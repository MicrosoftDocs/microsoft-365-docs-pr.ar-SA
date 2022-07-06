---
title: إعداد موصل أرشفة بيانات BlackBerry في Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: تعرف على كيفية إعداد موصل BlackBerry DataParser 17a-4 واستخدامه لاستيراد بيانات BlackBerry وأرشفتها في Microsoft 365.
ms.openlocfilehash: 9736ee81c5fc01a4e2e47d5c57585bee7533165d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640215"
---
# <a name="set-up-a-connector-to-archive-blackberry-data"></a>إعداد موصل أرشفة بيانات BlackBerry

استخدم [BlackBerry DataParser](https://www.17a-4.com/BlackBerry-dataparser/) من 17a-4 LLC لاستيراد بيانات مؤسسة BlackBerry وأرشفتها إلى علب بريد المستخدمين في مؤسسة Microsoft 365. يتضمن DataParser موصل BlackBerry الذي تم تكوينه لالتقاط العناصر من مصدر بيانات تابع لجهة خارجية واستيراد هذه العناصر إلى Microsoft 365. يحول موصل BlackBerry DataParser بيانات BlackBerry إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علب بريد المستخدمين في Microsoft 365.

بعد تخزين بيانات BlackBerry في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل BlackBerry لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-blackberry-data"></a>نظرة عامة على أرشفة بيانات BlackBerry

تشرح النظرة العامة التالية عملية استخدام موصل بيانات أرشفة بيانات BlackBerry في Microsoft 365.

![أرشفة سير العمل لبيانات BlackBerry من 17a-4.](../media/BlackBerryDataParserConnectorWorkflow.png)

1. تعمل مؤسستك مع 17a-4 لإعداد BlackBerry DataParser وتكوينه.

2. بشكل منتظم، يتم تجميع عناصر BlackBerry بواسطة DataParser. يقوم DataParser أيضا بتحويل محتوى رسالة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل BlackBerry DataParser الذي تقوم بإنشائه في مدخل التوافق في Microsoft Purview ب DataParser وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **BlackBerry DataParser** في علب بريد المستخدمين، ويتم استيراد عناصر BlackBerry إلى هذا المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر إليها باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر BlackBerry على هذه الخاصية، والتي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب DataParser لموصلات Microsoft. للقيام بذلك، اتصل [ب 17a-4 LLC](https://www.17a-4.com/contact/). تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل BlackBerry DataParser في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور موصل البيانات مسؤول، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل التوافق](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يتوفر موصل البيانات 17a-4 هذا في بيئات GCC في سحابة Microsoft 365 US Government. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-a-blackberry-dataparser-connector"></a>الخطوة 1: إعداد موصل BlackBerry DataParser

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مدخل التوافق وإنشاء موصل 17a-4 لبيانات BlackBerry.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات** >  البيانات ثم انقر فوق **BlackBerry DataParser**.

2. في صفحة وصف منتج **BlackBerry DataParser** ، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب 17a-4 الخاص بك وأكمل الخطوات الواردة في معالج اتصال BlackBerry DataParser.

## <a name="step-2-configure-the-blackberry-dataparser-connector"></a>الخطوة 2: تكوين موصل BlackBerry DataParser

العمل مع دعم 17a-4 لتكوين موصل BlackBerry DataParser.

## <a name="step-3-map-users"></a>الخطوة 3: تعيين المستخدمين

سيقوم موصل BlackBerry DataParser تلقائيا بتعيين المستخدمين إلى عناوين بريدهم الإلكتروني في Microsoft 365 قبل استيراد البيانات إلى Microsoft 365.

## <a name="step-4-monitor-the-blackberry-dataparser-connector"></a>الخطوة 4: مراقبة موصل BlackBerry DataParser

بعد إنشاء موصل BlackBerry DataParser، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **"الموصلات** "، ثم حدد موصل BlackBerry DataParser الذي أنشأته لعرض صفحة القائمة المنبثقة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على معلومات حول البيانات التي تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.