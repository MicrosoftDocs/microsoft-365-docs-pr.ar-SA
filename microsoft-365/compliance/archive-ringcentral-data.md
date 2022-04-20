---
title: إعداد موصل أرشفة بيانات RingCentral في Microsoft 365
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
description: يمكن للمسؤولين إعداد موصل لاستيراد بيانات RingCentral وأرشفتها من Veritas إلى Microsoft 365. يتيح لك هذا الموصل أرشفة البيانات من مصادر بيانات الجهات الخارجية في Microsoft 365. بعد أرشفتك لهذه البيانات، يمكنك استخدام ميزات التوافق مثل الاحتجاز القانوني وeDiscovery ونهج الاستبقاء لإدارة بيانات الجهات الخارجية.
ms.openlocfilehash: 5b1186abdf842fcc2f66638258c20accb2b28980
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944052"
---
# <a name="set-up-a-connector-to-archive-ringcentral-data"></a>إعداد موصل أرشفة بيانات RingCentral

استخدم موصل Veritas في مدخل توافق Microsoft Purview لاستيراد البيانات وأرشفتها من النظام الأساسي RingCentral إلى علب بريد المستخدمين في مؤسسة Microsoft 365. يوفر Veritas موصل [RingCentral](https://www.veritas.com/insights/merge1/ringcentral) الذي تم تكوينه لالتقاط العناصر من مصدر بيانات الجهات الخارجية واستيراد هذه العناصر إلى Microsoft 365. يحول الموصل محتوى مثل الدردشات والمرفقات والمهام والملاحظات والمنشورات من RingCentral إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علب بريد المستخدمين في Microsoft 365.

بعد تخزين بيانات RingCentral في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء. يمكن أن يساعد استخدام موصل RingCentral لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-ringcentral-data"></a>نظرة عامة على أرشفة بيانات RingCentral

تشرح النظرة العامة التالية عملية استخدام موصل أرشفة بيانات RingCentral في Microsoft 365.

![أرشفة سير العمل لبيانات RingCentral.](../media/RingCentralConnectorWorkflow.png)

1. تعمل مؤسستك مع RingCentral لإعداد موقع RingCentral وتكوينه.

2. مرة واحدة كل 24 ساعة، يتم نسخ عناصر RingCentral إلى موقع Veritas Merge1. يحول الموصل أيضا عناصر RingCentral إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل RingCentral الذي تقوم بإنشائه في مدخل التوافق بموقع Veritas Merge1 كل يوم، وينقل محتوى RingCentral إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يستورد الموصل العناصر المحولة إلى علب بريد مستخدمين محددين باستخدام قيمة خاصية *البريد الإلكتروني* لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **RingCentral** في علب بريد المستخدمين، ويتم استيراد العناصر إلى هذا المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر إليها باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر RingCentral على هذه الخاصية، والتي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب Merge1 لموصلات Microsoft. لإنشاء هذا الحساب، اتصل بدعم [عملاء Veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact). تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- إنشاء تطبيق RingCentral لإحضار البيانات من حساب RingCentral الخاص بك. للحصول على إرشادات مفصلة خطوة بخطوة حول إنشاء التطبيق، راجع [دليل مستخدم موصلات الجهات الخارجية ل Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل RingCentral في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-ringcentral-connector"></a>الخطوة 1: إعداد موصل RingCentral

الخطوة الأولى هي الوصول إلى صفحة **موصلات البيانات** في مدخل التوافق وإنشاء موصل لبيانات RingCentral.

1. انتقل إلى <https://compliance.microsoft.com> Data **connectorsRingCentral** >  ثم انقر فوقها.

2. في صفحة وصف منتج **RingCentral** ، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-ringcentral-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين RingCentral على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل RingCentral على موقع Veritas Merge1. للحصول على معلومات حول كيفية تكوين موصل RingCentral، راجع [Merge1 دليل مستخدم موصلات الجهات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

بعد النقر فوق **"حفظ & إنهاء"،** يتم عرض صفحة **تعيين المستخدم** في معالج الموصل في مدخل التوافق.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال إعداد الموصل في مدخل التوافق، اتبع الخطوات التالية:

1. في صفحة **Map RingCentral Microsoft 365 المستخدمين**، قم بتمكين تعيين المستخدم تلقائيا. تتضمن عناصر RingCentral خاصية تسمى *"البريد الإلكتروني*"، والتي تحتوي على عناوين بريد إلكتروني للمستخدمين في مؤسستك. إذا كان بإمكان الموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر فوق **"التالي**"، راجع الإعدادات، ثم انتقل إلى صفحة **"موصلات البيانات** " للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-ringcentral-connector"></a>الخطوة 4: مراقبة موصل RingCentral

بعد إنشاء موصل RingCentral، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى <https://compliance.microsoft.com/> **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **"الموصلات** "، ثم حدد موصل **RingCentral** لعرض صفحة القائمة المنبثقة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.
