---
title: إعداد موصل وأرشفة بيانات Skype for Business Server في Microsoft 365
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
description: تعرف على كيفية إعداد موصل 17a-4 Skype for Business Server DataParser واستخدامه لاستيراد بيانات Skype for Business Server وأرشفتها في Microsoft 365.
ms.openlocfilehash: d1daedd7be239fa29746d51b625a633952461d09
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092514"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-server-data"></a>إعداد موصل وأرشفة بيانات Skype for Business Server

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

استخدم [Skype Server DataParser](https://www.17a-4.com/skype-server-dataparser/) من 17a-4 LLC لاستيراد البيانات وأرشفتها من Skype for Business Server إلى علب بريد المستخدمين في مؤسسة Microsoft 365. يتضمن DataParser موصلا Skype for Business تم تكوينه لالتقاط العناصر من مصدر بيانات تابع لجهة خارجية واستيراد هذه العناصر إلى Microsoft 365. يقوم موصل Skype for Business Server DataParser بتحويل بيانات Skype for Business Server إلى تنسيق رسالة بريد إلكتروني ثم استيراد هذه العناصر إلى علب بريد المستخدمين في Microsoft 365.

بعد تخزين البيانات Skype for Business Server في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل Skype for Business Server لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-skype-for-business-server-data"></a>نظرة عامة على أرشفة بيانات Skype for Business Server

تشرح النظرة العامة التالية عملية استخدام موصل بيانات أرشفة البيانات Skype for Business Server في Microsoft 365.

![أرشفة سير العمل لبيانات Skype for Business Server من 17a-4.](../media/SkypeServerDataParserConnectorWorkflow.png)

1. تعمل مؤسستك مع 17a-4 لإعداد Skype for Business Server DataParser وتكوينه.

2. بشكل منتظم، يتم جمع Skype for Business Server العناصر بواسطة DataParser. يقوم DataParser أيضا بتحويل محتوى رسالة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Skype for Business Server DataParser الذي تقوم بإنشائه في مدخل توافق Microsoft Purview ب DataParser وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يتم إنشاء مجلد فرعي في مجلد علبة الوارد المسمى **Skype for Business Server DataParser** في علب بريد المستخدمين، ويتم استيراد عناصر Skype for Business Server إلى هذا المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر إليها باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر Skype for Business Server على هذه الخاصية، التي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب DataParser لموصلات Microsoft. للقيام بذلك، اتصل [ب 17a-4 LLC](https://www.17a-4.com/contact/). تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Skype for Business Server DataParser في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يتوفر موصل البيانات 17a-4 هذا في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-a-skype-for-business-server-dataparser-connector"></a>الخطوة 1: إعداد موصل dataParser Skype for Business Server

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مدخل التوافق وإنشاء موصل 17a-4 لبيانات Skype for Business Server.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات البيانات** ثم انقر فوقها  > **Skype for Business Server DataParser**.

2. في صفحة وصف منتج **Skype for Business Server DataParser**، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حسابك في 17a-4 وأكمل الخطوات الواردة في معالج اتصال Skype for Business Server DataParser.

## <a name="step-2-configure-the-skype-for-business-server-dataparser-connector"></a>الخطوة 2: تكوين موصل Skype for Business Server DataParser

العمل مع دعم 17a-4 لتكوين موصل dataParser Skype for Business Server.

## <a name="step-3-map-users"></a>الخطوة 3: تعيين المستخدمين

سيقوم موصل Skype for Business Server DataParser تلقائيا بتعيين المستخدمين إلى عناوين بريدهم الإلكتروني Microsoft 365 قبل استيراد البيانات إلى Microsoft 365.

## <a name="step-4-monitor-the-skype-for-business-server-dataparser-connector"></a>الخطوة 4: مراقبة موصل Skype for Business Server DataParser

بعد إنشاء موصل Skype for Business Server DataParser، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **"الموصلات**"، ثم حدد موصل Skype for Business Server DataParser الذي قمت بإنشائه لعرض صفحة القائمة المنبثقة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.
