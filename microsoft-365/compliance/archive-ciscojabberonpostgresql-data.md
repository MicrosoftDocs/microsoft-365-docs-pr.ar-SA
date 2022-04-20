---
title: إعداد موصل أرشفة Cisco Jabber على بيانات PostgreSQL في Microsoft 365
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: تعرف على كيفية إعداد موصل واستخدامه في مدخل توافق Microsoft Purview لاستيراد البيانات وأرشفتها من Cisco Jabber على PostgreSQL إلى Microsoft 365.
ms.openlocfilehash: 2e573bcc6c39e9188ec09f05190c124bd904ef98
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996317"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data"></a>إعداد موصل أرشفة Cisco Jabber على بيانات PostgreSQL

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

استخدم موصل Veritas في مدخل توافق Microsoft Purview لاستيراد البيانات وأرشفتها من النظام الأساسي Cisco Jabber إلى علب بريد المستخدمين في مؤسستك Microsoft 365. يوفر Veritas [Cisco Jabber على موصل PostgreSQL](https://www.veritas.com/insights/merge1/jabber) الذي تم تكوينه لالتقاط العناصر من مصدر بيانات الجهات الخارجية (بشكل منتظم) واستيراد هذه العناصر إلى Microsoft 365. يحول الموصل المحتوى مثل الرسائل والدردشات والمحتوى المشترك من Cisco Jabber على PostgreSQL إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Cisco Jabber على PostgreSQL في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء. يمكن أن يساعد استخدام Cisco Jabber على موصل PostgreSQL لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a>نظرة عامة على أرشفة Cisco Jabber على بيانات PostgreSQL

تشرح النظرة العامة التالية عملية استخدام موصل أرشفة Cisco Jabber على بيانات PostgreSQL في Microsoft 365.

![أرشفة سير العمل ل Cisco Jabber على بيانات PostgreSQL.](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. تعمل مؤسستك مع Cisco Jabber على PostgreSQL لإعداد وتكوين Cisco Jabber على موقع PostgreSQL.

2. مرة واحدة كل 24 ساعة، يتم نسخ Cisco Jabber على عناصر PostgreSQL إلى موقع Veritas Merge1. يحول الموصل أيضا Cisco Jabber على عناصر PostgreSQL إلى تنسيق رسالة بريد إلكتروني.

3. يتصل Cisco Jabber على موصل PostgreSQL الذي تقوم بإنشائه في مدخل التوافق بموقع Veritas Merge1 كل يوم، وينقل محتوى Jabber إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يستورد الموصل العناصر المحولة إلى علب بريد مستخدمين محددين باستخدام قيمة خاصية *البريد الإلكتروني* لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Cisco Jabber على PostgreSQL** في علب بريد المستخدمين، ويتم استيراد العناصر إلى هذا المجلد. يقوم الموصل بذلك باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر Jabber على هذه الخاصية، التي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Merge1 لموصلات Microsoft. للقيام بذلك، اتصل بدعم [عملاء Veritas](https://www.veritas.com/content/support/en_US). تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء Cisco Jabber على موصل PostgreSQL في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a>الخطوة 1: إعداد Cisco Jabber على موصل PostgreSQL

الخطوة الأولى هي الوصول إلى صفحة **موصلات البيانات** في مدخل التوافق وإنشاء موصل لبيانات Jabber.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات** &gt; البيانات ثم انقر فوق **Cisco Jabber على PostgreSQL**.

2. في **Cisco Jabber على صفحة وصف منتج PostgreSQL** ، انقر فوق **إضافة موصل**.

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين Cisco Jabber على PostgreSQL على موقع Veritas Merge1

الخطوة الثانية هي تكوين Cisco Jabber على موصل PostgreSQL على موقع Veritas Merge1. للحصول على معلومات حول كيفية تكوين Cisco Jabber على موصل PostgreSQL، راجع [دليل مستخدم Merge1 Third-party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf).

بعد النقر فوق **"حفظ & إنهاء**"، يتم عرض صفحة **تعيين المستخدم** في معالج الموصل في مدخل التوافق.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال إعداد الموصل في مدخل التوافق، اتبع الخطوات التالية:

1. في **Map Cisco Jabber على مستخدمي PostgreSQL Microsoft 365 صفحة المستخدمين**، قم بتمكين تعيين المستخدم تلقائيا. تتضمن عناصر Cisco Jabber على PostgreSQL خاصية تسمى *"البريد الإلكتروني*"، والتي تحتوي على عناوين بريد إلكتروني للمستخدمين في مؤسستك. إذا كان بإمكان الموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر فوق **"التالي**"، راجع الإعدادات، ثم انتقل إلى صفحة **"موصلات البيانات** " للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a>الخطوة 4: مراقبة Cisco Jabber على موصل PostgreSQL

بعد إنشاء Cisco Jabber على موصل PostgreSQL، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى <https://compliance.microsoft.com/> **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **Connectors** ثم حدد **Cisco Jabber على موصل PostgreSQL** لعرض صفحة القائمة المنبثقة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.
