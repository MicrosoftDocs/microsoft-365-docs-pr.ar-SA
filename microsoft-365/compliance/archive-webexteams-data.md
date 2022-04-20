---
title: إعداد موصل إلى بيانات Teams Webex في Microsoft 365
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
description: يمكن للمسؤولين إعداد موصل لاستيراد البيانات وأرشفتها من موصل Teams Webex في Veritas في Microsoft 365. يتيح لك هذا الموصل أرشفة البيانات من مصادر بيانات الجهات الخارجية في Microsoft 365 حتى تتمكن من استخدام ميزات التوافق مثل الاحتجاز القانوني والبحث في المحتوى ونهج الاستبقاء لإدارة بيانات الجهات الخارجية لمؤسستك.
ms.openlocfilehash: 1aa1a0ddd94aa2308c4884921138b12b0c152bab
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942854"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>إعداد موصل إلى أرشفة بيانات Teams Webex

استخدم موصل Veritas في مدخل توافق Microsoft Purview لاستيراد البيانات وأرشفتها من Teams Webex إلى علب بريد المستخدمين في مؤسستك Microsoft 365. يوفر Veritas موصل [Teams Webex](https://globanet.com/webex-teams/) الذي تم تكوينه لالتقاط عناصر اتصال Teams Webex واستيرادها إلى Microsoft 365. يحول الموصل المحتوى من Teams Webex، مثل الدردشات 1:1 ومحادثات المجموعة ومحادثات القناة والمرفقات من حساب Teams Webex الخاص بمؤسستك، إلى تنسيق رسالة بريد إلكتروني ثم استيراد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Teams Webex في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل Teams Webex لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-webex-teams-data"></a>نظرة عامة على أرشفة بيانات Teams Webex

تشرح النظرة العامة التالية عملية استخدام موصل أرشفة بيانات Teams Webex في Microsoft 365.

![أرشفة سير العمل لبيانات Teams Webex.](../media/WebexTeamsConnectorWorkflow.png)

1. تعمل مؤسستك مع Teams Webex لإعداد موقع Teams Webex وتكوينه.

2. مرة واحدة كل 24 ساعة، يتم نسخ عناصر Teams Webex إلى موقع Veritas Merge1. يقوم الموصل أيضا بتحويل عناصر Teams Webex إلى تنسيق رسالة بريد إلكتروني.

3. يتصل Webex Teams الموصل الذي تقوم بإنشائه في مدخل التوافق ب Veritas Merge1 كل يوم، وينقل عناصر Teams Webex إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يستورد الموصل العناصر إلى علب بريد مستخدمين محددين باستخدام قيمة خاصية *"البريد الإلكتروني* " لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Webex Teams** في علب بريد المستخدمين، ويتم استيراد العناصر إلى هذا المجلد. يقوم الموصل بذلك باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر Teams Webex على هذه الخاصية، والتي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Veritas Merge1 لموصلات Microsoft. لإنشاء هذا الحساب، اتصل بدعم [عملاء Veritas](https://globanet.com/ms-connectors-contact). ستقوم بتسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- أنشئ تطبيقا [https://developer.webex.com/](https://developer.webex.com) لإحضار البيانات من حساب Teams Webex. للحصول على إرشادات مفصلة خطوة بخطوة حول إنشاء التطبيق، راجع [دليل مستخدم موصلات الدمج1 لجهة خارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   عند إنشاء هذا التطبيق، ينشئ النظام الأساسي Webex مجموعة من بيانات الاعتماد الفريدة. يتم استخدام بيانات الاعتماد هذه في الخطوة 2 عند تكوين موصل Teams Webex على موقع "الدمج العمومي1".

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Webex Teams في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-webex-teams-connector"></a>الخطوة 1: إعداد موصل Teams Webex

الخطوة الأولى هي الوصول إلى **موصلات البيانات** وإعداد موصل [Teams Webex](https://globanet.com/webex-teams/).

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/) **موصلات Data** **connectorsWebex** >  Teams ثم انقر فوقها.

2. في صفحة وصف المنتج **Teams Webex**، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين موصل Webex Teams على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل webex Teams على موقع Merge1. للحصول على معلومات حول كيفية تكوين موصل Teams Webex، راجع [دليل مستخدم Merge1 لجهات خارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

بعد النقر فوق **"حفظ & إنهاء**"، يتم عرض صفحة **تعيين المستخدم** في معالج الموصل في مدخل التوافق.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال إعداد الموصل في مدخل التوافق، اتبع الخطوات التالية:

1. في **Map Webex Teams المستخدمين Microsoft 365 صفحة المستخدمين**، قم بتمكين تعيين المستخدم تلقائيا. تتضمن عناصر Teams Webex خاصية تسمى *"البريد الإلكتروني*"، والتي تحتوي على عناوين بريد إلكتروني للمستخدمين في مؤسستك. إذا كان بإمكان الموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر فوق **"التالي**"، راجع الإعدادات، ثم انتقل إلى صفحة **"موصلات البيانات** " للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-webex-teams-connector"></a>الخطوة 4: مراقبة موصل Teams Webex

بعد إنشاء موصل Teams Webex، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com) **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **"الموصلات**"، ثم حدد موصل **Teams Webex** لعرض صفحة القائمة المنبثقة. تحتوي هذه الصفحة على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على معلومات حول البيانات التي تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.