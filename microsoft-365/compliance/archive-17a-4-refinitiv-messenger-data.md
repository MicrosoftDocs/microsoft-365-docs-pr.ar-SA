---
title: إعداد موصل أرشفة بيانات Refinitiv Eikon Messenger في Microsoft 365
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
description: تعرف على كيفية إعداد موصل 17a-4 Refinitiv Eikon Messenger DataParser واستخدامه لاستيراد هذه البيانات وأرشفتها في Microsoft 365.
ms.openlocfilehash: 2cba39d30bf83646023b457866605f37352eb478
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077513"
---
# <a name="set-up-a-connector-to-archive-refinitiv-eikon-messenger-data"></a>إعداد موصل أرشفة بيانات Refinitiv Eikon Messenger

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

استخدم [Refinitiv Eikon Messenger DataParser](https://www.17a-4.com/refinitiv-messenger-dataparser/) من 17a-4 LLC لاستيراد البيانات وأرشفتها من Refinitiv Eikon Messenger إلى علب بريد المستخدمين في مؤسستك Microsoft 365. يتضمن DataParser موصل Refinitiv Eikon Messenger الذي تم تكوينه لالتقاط العناصر من مصدر بيانات تابع لجهة خارجية واستيراد هذه العناصر إلى Microsoft 365. يحول موصل Refinitiv Eikon Messenger DataParser بيانات Refinitiv Eikon Messenger إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علب بريد المستخدمين في Microsoft 365.

بعد تخزين بيانات Refinitiv Eikon Messenger في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل Refinitiv Eikon Messenger لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-refinitiv-eikon-messenger-data"></a>نظرة عامة على أرشفة بيانات Refinitiv Eikon Messenger

تشرح النظرة العامة التالية عملية استخدام موصل بيانات أرشفة بيانات Refinitiv Eikon Messenger في Microsoft 365.

![أرشفة سير العمل لبيانات Refinitiv Eikon Messenger من 17a-4.](../media/RefinitivMessengerDataParserConnectorWorkflow.png)

1. تعمل مؤسستك مع 17a-4 لإعداد وتكوين Refinitiv Eikon Messenger DataParser.

2. بشكل منتظم، يتم تجميع عناصر Refinitiv Eikon Messenger بواسطة DataParser. يقوم DataParser أيضا بتحويل محتوى رسالة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Refinitiv Eikon Messenger DataParser الذي تقوم بإنشائه في مدخل توافق Microsoft Purview ب DataParser وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Refinitiv Eikon Messenger DataParser** في علب بريد المستخدمين، ويتم استيراد عناصر Refinitiv Eikon Messenger إلى هذا المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر إليها باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر من عناصر Refinitiv Eikon Messenger على هذه الخاصية، والتي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب DataParser لموصلات Microsoft. لإنشاء حساب، اتصل [ب 17a-4 LLC](https://www.17a-4.com/contact/). ستحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Refinitiv Eikon Messenger DataParser في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يتوفر موصل البيانات 17a-4 هذا في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-a-refinitiv-eikon-messenger-dataparser-connector"></a>الخطوة 1: إعداد موصل Refinitiv Eikon Messenger DataParser

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مدخل التوافق وإنشاء موصل 17a-4 لبيانات Refinitiv Eikon Messenger.

1. انتقل إلى <https://compliance.microsoft.com> **Data connectorsRefinitiv** >  **Eikon Messenger DataParser ثم انقر فوقها**.

2. في صفحة وصف منتج **Refinitiv Eikon Messenger DataParser** ، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حسابك في 17a-4 وأكمل الخطوات الواردة في معالج اتصال Refinitiv Eikon Messenger DataParser.

## <a name="step-2-configure-the-refinitiv-eikon-messenger-dataparser-connector"></a>الخطوة 2: تكوين موصل Refinitiv Eikon Messenger DataParser

العمل مع دعم 17a-4 لتكوين موصل Refinitiv Eikon Messenger DataParser.

## <a name="step-3-map-users"></a>الخطوة 3: تعيين المستخدمين

سيقوم موصل Refinitiv Eikon Messenger DataParser تلقائيا بتعيين المستخدمين إلى عناوين بريدهم الإلكتروني Microsoft 365 قبل استيراد البيانات إلى Microsoft 365.

## <a name="step-4-monitor-the-refinitiv-eikon-messenger-dataparser-connector"></a>الخطوة 4: مراقبة موصل Refinitiv Eikon Messenger DataParser

بعد إنشاء موصل Refinitiv Eikon Messenger DataParser، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **"Connectors** "، ثم حدد موصل Refinitiv Eikon Messenger DataParser الذي أنشأته لعرض صفحة القائمة المنبثقة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.
