---
title: إعداد موصل لأرشفة بيانات ICE الاتصال الدردشة في Microsoft 365
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
description: تعرف على كيفية إعداد موصل ICE 17a-4 ICE الاتصال Chat DataParser واستخدامه لاستيراد بيانات ICE الاتصال في Microsoft 365.
ms.openlocfilehash: fa6b440f77b0c7836de5bf94f108eaffaa12d2fa
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575567"
---
# <a name="set-up-a-connector-to-archive-ice-connect-chat-data"></a>إعداد موصل لأرشفة بيانات ICE الاتصال الدردشة

استخدم [ICE DataParser](https://www.17a-4.com/ice-dataparser/) من 17a-4 LLC لاستيراد البيانات وأرشفتها من ICE الاتصال إلى علب بريد المستخدمين في Microsoft 365 الخاصة بك. يتضمن DataParser موصل ICE Chat الذي تم تكوينه لالتقاط العناصر من مصدر بيانات جهة خارجية واستيراد هذه العناصر Microsoft 365. يحول موصل ICE DataParser بيانات الاتصال ICE إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علب بريد المستخدمين في Microsoft 365.

بعد الاتصال بيانات الدردشة في علب بريد المستخدمين، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية و eDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل ICE DataParser لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="overview-of-archiving-ice-chat-data"></a>نظرة عامة حول أرشفة بيانات ICE Chat

تشرح النظرة العامة التالية عملية استخدام موصل بيانات لأرشفة ICE الاتصال بيانات الدردشة في Microsoft 365.

![أرشفة سير العمل ل ICE الاتصال بيانات الدردشة من 17a-4.](../media/ICEChatDataParserConnectorWorkflow.png)

1. تعمل مؤسستك مع 17a-4 لإعداد ICE DataParser وتكوينه.

2. بشكل منتظم، يتم الاتصال ICE عناصر الدردشة بواسطة DataParser. يحول DataParser أيضا محتوى الرسالة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل ICE DataParser الذي تقوم مركز التوافق في Microsoft 365 ب DataParser وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **ICE DataParser** في علب بريد المستخدمين، كما يتم استيراد عناصر الاتصال ICE إلى ذلك المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر لها باستخدام قيمة خاصية *البريد* الإلكتروني. يحتوي كل عنصر الاتصال ICE على هذه الخاصية، التي يتم ملؤها عنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب DataParser لموصلات Microsoft. للقيام بذلك، اتصل [ب 17a-4 LLC](https://www.17a-4.com/contact/). يجب تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي ينشئ موصل بيانات ICEParser في الخطوة 1 (ويكمله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يتوفر موصل البيانات 17a-4 هذا في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. قد تشتمل التطبيقات والخدمات التي تقدمها جهة خارجية على تخزين بيانات عملاء مؤسستك ونقلها وحمايتها على أنظمة أخرى تقع خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات التوافق وحماية البيانات Microsoft 365. لا تقدم Microsoft أي تمثيل يشير فيه استخدام هذا المنتج للاتصال إلى تطبيقات  الأطراف الخارجية إلى أن تلك التطبيقات التي تقدمها جهة خارجية متوافقة مع FEDRAMP.

## <a name="step-1-set-up-an-ice-dataparser-connector"></a>الخطوة 1: إعداد موصل ICE DataParser

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مركز التوافق في Microsoft 365 وإنشاء موصل 17a-4 لبيانات ICE الاتصال Chat.

1. انتقل إلى <https://compliance.microsoft.com> ثم انقر فوق **Data connectorsICE** >  **DataParser**.

2. في صفحة **وصف منتج ICE DataParser** ، انقر فوق **إضافة موصل**.

3. في صفحة **شروط الخدمة** ، انقر فوق **قبول**.

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **التالي**.

5. سجل الدخول إلى حسابك في 17a-4 وأكمل الخطوات في معالج اتصال ICE DataParser.

## <a name="step-2-configure-the-ice-dataparser-connector"></a>الخطوة 2: تكوين موصل ICE DataParser

استخدام الدعم 17a-4 لتكوين موصل ICE DataParser.

## <a name="step-3-map-users"></a>الخطوة 3: تعيين المستخدمين

يقوم موصل ICE DataParser تلقائيا ب تعيين المستخدمين إلى عناوين بريدهم Microsoft 365 الإلكتروني قبل استيراد البيانات Microsoft 365.

## <a name="step-4-monitor-the-ice-dataparser-connector"></a>الخطوة 4: مراقبة موصل ICE DataParser

بعد إنشاء موصل ICE DataParser، يمكنك عرض حالة الموصل في مركز التوافق في Microsoft 365.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات البيانات وانقر** فوقها في التنقل الأيسر.

2. انقر فوق **علامة التبويب** موصلات، ثم حدد موصل ICE DataParser الذي أنشأته لعرض صفحة القائمة الإعلانية، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق الارتباط **تنزيل السجل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 مبايت. سيتوفر الدعم للعناصر الكبيرة في وقت لاحق.
