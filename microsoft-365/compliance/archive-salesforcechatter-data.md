---
title: إعداد موصل أرشفة بيانات Salesforce Chatter في Microsoft 365
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
description: يمكن للمسؤولين إعداد موصل لاستيراد بيانات Salesforce Chatter وأرشفتها من Veritas إلى Microsoft 365. يتيح لك هذا الموصل أرشفة البيانات من مصادر بيانات الجهات الخارجية في Microsoft 365. بعد أرشفتك لهذه البيانات، يمكنك استخدام ميزات التوافق مثل الاحتجاز القانوني والبحث في المحتوى ونهج الاستبقاء لإدارة بيانات الجهات الخارجية.
ms.openlocfilehash: cc13f8c7c3b82839883053b07c97b03c5a0bc492
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417073"
---
# <a name="set-up-a-connector-to-archive-salesforce-chatter-data"></a>إعداد موصل أرشفة بيانات Salesforce Chatter

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

استخدم موصل Veritas في مدخل التوافق في Microsoft Purview لاستيراد البيانات وأرشفتها من النظام الأساسي Salesforce Chatter إلى علب بريد المستخدمين في مؤسستك Microsoft 365. يوفر Veritas موصل [Salesforce Chatter](http://globanet.com/chatter/) الذي يلتقط العناصر من مصدر بيانات الجهات الخارجية ويستورد هذه العناصر إلى Microsoft 365. يحول الموصل المحتوى مثل الدردشات والمرفقات والمنشورات من Salesforce Chater إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Salesforce Chatter في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء. يمكن أن يساعد استخدام موصل Salesforce Chatter لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-salesforce-chatter-data"></a>نظرة عامة على أرشفة بيانات Salesforce Chatter

تشرح النظرة العامة التالية عملية استخدام موصل أرشفة بيانات Salesforce Chatter في Microsoft 365.

![أرشفة سير العمل لبيانات Salesforce Chatter.](../media/SalesforceChatterConnectorWorkflow.png)

1. تعمل مؤسستك مع Salesforce Chatter لإعداد موقع Salesforce Chatter وتكوينه.

2. مرة واحدة كل 24 ساعة، يتم نسخ عناصر Salesforce Chatter إلى موقع Veritas Merge1. الموصل أيضا عناصر Salesforce Chatter بتنسيق رسالة بريد إلكتروني.

3. يتصل موصل Salesforce Chatter الذي تقوم بإنشائه في مدخل التوافق بموقع Veritas Merge1 كل يوم وينقل محتوى الدردشة إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يستورد الموصل العناصر المحولة إلى علب بريد مستخدمين محددين باستخدام قيمة خاصية *البريد الإلكتروني* لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Salesforce Chatter** في علب بريد المستخدمين، ويتم استيراد العناصر إلى هذا المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر إليها باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر "محادثة" على هذه الخاصية، التي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Merge1 لموصلات Microsoft. لإنشاء حساب، اتصل بدعم [عملاء Veritas](https://www.veritas.com/content/support/). تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- إنشاء تطبيق Salesforce والحصول على رمز مميز في [https://salesforce.com](https://salesforce.com). ستحتاج إلى تسجيل الدخول إلى حساب Salesforce كمسؤول والحصول على رمز مميز شخصي للمستخدم لاستيراد البيانات. يجب أيضا نشر المشغلات على موقع الدردشة لالتقاط التحديثات والحذف والتحرير. ستنشئ هذه المشغلات منشورا على قناة، وستلتقط Merge1 المعلومات من القناة. للحصول على إرشادات خطوة بخطوة حول كيفية إنشاء التطبيق والحصول على الرمز المميز، راجع [Merge1 دليل مستخدم موصلات الجهات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Salesforce Chatter في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة أدوار مخصصة" في ["الأذونات" في مدخل التوافق في Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء الخاصة بمؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-salesforce-chatter-connector"></a>الخطوة 1: إعداد موصل Salesforce Chatter

الخطوة الأولى هي الوصول إلى صفحة **"موصلات البيانات** " في مدخل التوافق وإنشاء موصل لبيانات "الدردشة".

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/) Data **connectorsSalesforce** >  Chatter ثم انقر فوقها.

2. في صفحة وصف منتج **Salesforce Chatter** ، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-salesforce-chatter-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين Salesforce Chatter على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل Salesforce Chatter على موقع Veritas Merge1. للحصول على معلومات حول كيفية تكوين موصل Salesforce Chatter، راجع [Merge1 دليل مستخدم موصلات الجهات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

بعد النقر فوق **"حفظ & إنهاء"،** يتم عرض صفحة **تعيين المستخدم** في معالج الموصل في مدخل التوافق.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال إعداد الموصل في مدخل التوافق، اتبع الخطوات التالية:

1. في صفحة **Map Salesforce Chatter Microsoft 365 المستخدمين**، قم بتمكين تعيين المستخدم تلقائيا. تتضمن عناصر Salesforce Chatter خاصية تسمى *"البريد الإلكتروني*"، والتي تحتوي على عناوين بريد إلكتروني للمستخدمين في مؤسستك. إذا كان بإمكان الموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر فوق **"التالي**"، راجع الإعدادات، ثم انتقل إلى صفحة **"موصلات البيانات** " للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-salesforce-chatter-connector"></a>الخطوة 4: مراقبة موصل Salesforce Chatter

بعد إنشاء موصل Salesforce Chatter، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/) **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **"الموصلات** " ثم انقر فوق موصل **Salesforce Chatter** لعرض صفحة القائمة المنبثقة التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.
