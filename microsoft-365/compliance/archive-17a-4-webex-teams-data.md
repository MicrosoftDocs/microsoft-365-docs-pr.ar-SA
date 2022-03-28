---
title: إعداد موصل لأرشفة بيانات Cisco Webex في Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: تعرف على كيفية إعداد موصل Cisco Webex DataParser 17a-4 واستخدامه لاستيراد بيانات Cisco Webex وأرشفتها في Microsoft 365.
ms.openlocfilehash: fce025ab86b9c03e1200046750ebfc7f23830f43
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575563"
---
# <a name="set-up-a-connector-to-archive-cisco-webex-data"></a>إعداد موصل لأرشفة بيانات Cisco Webex

استخدم [Cisco Webex DataParser](https://www.17a-4.com/webex-dataparser/) من 17a-4 LLC لاستيراد البيانات وأرشفتها من النظام الأساسي Cisco Cisco Webex إلى علب بريد المستخدمين في Microsoft 365 مؤسستك. يتضمن DataParser موصل Cisco Webex الذي تم تكوينه لالتقاط العناصر من مصدر بيانات جهة خارجية واستيراد هذه العناصر Microsoft 365. يحول موصل Cisco Webex DataParser بيانات Cisco Webex إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علب بريد المستخدمين في Microsoft 365.

بعد تخزين بيانات Cisco Webex في علب بريد المستخدمين، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية و eDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل Cisco Webex لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="overview-of-archiving-cisco-webex-data"></a>نظرة عامة حول أرشفة بيانات Cisco Webex

تشرح النظرة العامة التالية عملية استخدام موصل بيانات لأرشفة بيانات Cisco Webex في Microsoft 365.

![أرشفة سير العمل لبيانات Cisco Webex من 17a-4.](../media/WebexTeamsDataParserConnectorWorkflow.png)

1. تعمل مؤسستك مع 17a-4 لإعداد Cisco Webex DataParser وتكوينه.

2. بشكل منتظم، يتم تجميع عناصر Cisco Webex بواسطة DataParser. يحول DataParser أيضا محتوى الرسالة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Cisco Webex DataParser الذي تقوم بإنشاءه في مركز التوافق في Microsoft 365 ب DataParser وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Cisco Webex DataParser** في علب بريد المستخدمين، كما يتم استيراد عناصر Cisco Webex إلى ذلك المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر لها باستخدام قيمة خاصية *البريد* الإلكتروني. يحتوي كل عنصر Cisco Webex على هذه الخاصية، التي يتم ملؤها عنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب DataParser لموصلات Microsoft. للقيام بذلك، اتصل [ب 17a-4 LLC](https://www.17a-4.com/contact/). يجب تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Cisco Webex DataParser في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يتوفر موصل البيانات 17a-4 هذا في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. قد تشتمل التطبيقات والخدمات التي تقدمها جهة خارجية على تخزين بيانات عملاء مؤسستك ونقلها وحمايتها على أنظمة أخرى تقع خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات التوافق وحماية البيانات Microsoft 365. لا تقدم Microsoft أي تمثيل يشير فيه استخدام هذا المنتج للاتصال إلى تطبيقات  الأطراف الخارجية إلى أن تلك التطبيقات التي تقدمها جهة خارجية متوافقة مع FEDRAMP.

## <a name="step-1-set-up-a-cisco-webex-dataparser-connector"></a>الخطوة 1: إعداد موصل Cisco Webex DataParser

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مركز التوافق في Microsoft 365 وإنشاء موصل 17a-4 لبيانات Cisco Webex.

1. انتقل إلى <https://compliance.microsoft.com> موصلات **البيانات** >  ثم انقر **فوقهاCisco Webex DataParser**.

2. في صفحة **وصف منتج Cisco Webex DataParser** ، انقر فوق **إضافة موصل**.

3. في صفحة **شروط الخدمة** ، انقر فوق **قبول**.

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **التالي**.

5. سجل الدخول إلى حسابك في 17a-4 وأكمل الخطوات في معالج اتصال Cisco Webex DataParser.

## <a name="step-2-configure-the-cisco-webex-dataparser-connector"></a>الخطوة 2: تكوين موصل Cisco Webex DataParser

استخدام دعم 17a-4 لتكوين موصل Cisco Webex DataParser.

## <a name="step-3-map-users"></a>الخطوة 3: تعيين المستخدمين

يقوم موصل Cisco Webex DataParser تلقائيا ب تعيين المستخدمين إلى عناوين بريدهم Microsoft 365 الإلكتروني قبل استيراد البيانات Microsoft 365.

## <a name="step-4-monitor-the-cisco-webex-dataparser-connector"></a>الخطوة 4: مراقبة موصل Cisco Webex DataParser

بعد إنشاء موصل Cisco Webex DataParser، يمكنك عرض حالة الموصل في مركز التوافق في Microsoft 365.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات البيانات وانقر** فوقها في التنقل الأيسر.

2. انقر فوق **علامة** التبويب موصلات، ثم حدد موصل بيانات Cisco Webex DataParser الذي أنشأته لعرض صفحة القائمة الإعلانية، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق الارتباط **تنزيل السجل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 مبايت. سيتوفر الدعم للعناصر الكبيرة في وقت لاحق.
