---
title: إعداد موصل لبيانات Webex Teams في Microsoft 365
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
description: يمكن للمسؤولين إعداد موصل لاستيراد البيانات وأرشفتها من موصل Webex Teams الخاص ب Veritas في Microsoft 365. يتيح لك هذا الموصل أرشفة البيانات من مصادر بيانات الجهات الخارجية في Microsoft 365 حتى تتمكن من استخدام ميزات التوافق مثل الاحتجاز القانوني والبحث في المحتوى ونهج الاستبقاء لإدارة بيانات الجهات الخارجية لمؤسستك.
ms.openlocfilehash: 1a1823c4928ac310aa3bbfe7b5c6e0a26408f964
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621260"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>إعداد موصل أرشفة بيانات Webex Teams

استخدم موصل Veritas في مدخل التوافق في Microsoft Purview لاستيراد البيانات وأرشفتها من Webex Teams إلى علب بريد المستخدمين في مؤسسة Microsoft 365. يوفر Veritas موصل [Webex Teams](https://globanet.com/webex-teams/) الذي تم تكوينه لالتقاط عناصر اتصال Webex Teams واستيرادها إلى Microsoft 365. يحول الموصل المحتوى من Webex Teams، مثل الدردشات 1:1 ومحادثات المجموعة ومحادثات القناة والمرفقات من حساب Webex Teams الخاص بمؤسستك، إلى تنسيق رسالة بريد إلكتروني ثم استيراد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Webex Teams في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل Webex Teams لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-webex-teams-data"></a>نظرة عامة على أرشفة بيانات Webex Teams

تشرح النظرة العامة التالية عملية استخدام موصل أرشفة بيانات Webex Teams في Microsoft 365.

![أرشفة سير العمل لبيانات Webex Teams.](../media/WebexTeamsConnectorWorkflow.png)

1. تعمل مؤسستك مع Webex Teams لإعداد موقع Webex Teams وتكوينه.

2. مرة واحدة كل 24 ساعة، يتم نسخ عناصر Webex Teams إلى موقع Veritas Merge1. يقوم الموصل أيضا بتحويل عناصر Webex Teams إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Webex Teams الذي تقوم بإنشائه في مدخل التوافق ب Veritas Merge1 كل يوم، وينقل عناصر Webex Teams إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يستورد الموصل العناصر إلى علب بريد مستخدمين محددين باستخدام قيمة خاصية *"البريد الإلكتروني* " لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Webex Teams** في علب بريد المستخدمين، ويتم استيراد العناصر إلى هذا المجلد. يقوم الموصل بذلك باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر من عناصر Webex Teams على هذه الخاصية، التي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Veritas Merge1 لموصلات Microsoft. لإنشاء هذا الحساب، اتصل بدعم [عملاء Veritas](https://globanet.com/ms-connectors-contact). ستقوم بتسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- أنشئ تطبيقا [https://developer.webex.com/](https://developer.webex.com) لإحضار البيانات من حساب Webex Teams الخاص بك. للحصول على إرشادات مفصلة خطوة بخطوة حول إنشاء التطبيق، راجع [دليل مستخدم موصلات الدمج1 لجهة خارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   عند إنشاء هذا التطبيق، ينشئ النظام الأساسي Webex مجموعة من بيانات الاعتماد الفريدة. يتم استخدام بيانات الاعتماد هذه في الخطوة 2 عند تكوين موصل Webex Teams على موقع Global Merge1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Webex Teams في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور موصل البيانات مسؤول، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة أدوار مخصصة" في ["الأذونات" في مدخل التوافق في Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- موصل بيانات Veritas هذا في المعاينة العامة في بيئات GCC في سحابة Microsoft 365 US Government. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-webex-teams-connector"></a>الخطوة 1: إعداد موصل Webex Teams

الخطوة الأولى هي الوصول إلى **موصلات البيانات** وإعداد موصل [Webex Teams](https://globanet.com/webex-teams/) .

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/) **Data connectors** > **Webex Teams ثم انقر فوقها**.

2. في صفحة وصف منتج **Webex Teams** ، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين موصل Webex Teams على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل Webex Teams على موقع Merge1. للحصول على معلومات حول كيفية تكوين موصل Webex Teams، راجع [Merge1 دليل مستخدم موصلات الجهات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

بعد النقر فوق **"حفظ & إنهاء**"، يتم عرض صفحة **تعيين المستخدم** في معالج الموصل في مدخل التوافق.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال إعداد الموصل في مدخل التوافق، اتبع الخطوات التالية:

1. في صفحة **مستخدمي Map Webex Teams لمستخدمي Microsoft 365** ، قم بتمكين تعيين المستخدم تلقائيا. تتضمن عناصر Webex Teams خاصية تسمى *"البريد الإلكتروني*"، والتي تحتوي على عناوين بريد إلكتروني للمستخدمين في مؤسستك. إذا كان بإمكان الموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر فوق **"التالي**"، راجع الإعدادات، ثم انتقل إلى صفحة **"موصلات البيانات** " للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-webex-teams-connector"></a>الخطوة 4: مراقبة موصل Webex Teams

بعد إنشاء موصل Webex Teams، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com) **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **"الموصلات** "، ثم حدد موصل **Webex Teams** لعرض صفحة القائمة المنبثقة. تحتوي هذه الصفحة على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على معلومات حول البيانات التي تم استيرادها إلى سحابة Microsoft. لمزيد من المعلومات، راجع [عرض سجلات المسؤول لموصلات البيانات](data-connector-admin-logs.md).

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.