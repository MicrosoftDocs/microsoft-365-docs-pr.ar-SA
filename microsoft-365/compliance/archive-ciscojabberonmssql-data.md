---
title: إعداد موصل أرشفة Cisco Jabber على بيانات MS SQL في Microsoft 365
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
description: يمكن للمسؤولين إعداد موصل لاستيراد بيانات Cisco Jabber وأرشفتها على MS SQL من Veritas في Microsoft 365. يتيح لك هذا الموصل أرشفة البيانات من مصادر بيانات الجهات الخارجية في Microsoft 365. بعد أرشفتك لهذه البيانات، يمكنك استخدام ميزات التوافق مثل الاحتجاز القانوني والبحث في المحتوى ونهج الاستبقاء لإدارة بيانات الجهات الخارجية.
ms.openlocfilehash: ef9586c0e860db727bea53651d70777e7c606498
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099774"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>إعداد موصل أرشفة Cisco Jabber على بيانات MS SQL

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

استخدم موصل Veritas في مدخل توافق Microsoft Purview لاستيراد البيانات وأرشفتها من النظام الأساسي Cisco Jabber إلى علب بريد المستخدمين في مؤسستك Microsoft 365. يوفر لك Veritas موصل [Cisco Jabber](https://globanet.com/jabber/) الذي تم تكوينه لالتقاط العناصر من قاعدة بيانات MS SQL في Jabber، مثل رسائل الدردشة 1:1 والدردشات الجماعية ثم استيراد هذه العناصر إلى Microsoft 365. يسترد الموصل البيانات من قاعدة بيانات MS SQL ل Cisco Jabber، ويعالجها، ويحول المحتوى من حساب Cisco Jabber الخاص بالمستخدم إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Cisco Jabber في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل Cisco Jabber لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-cisco-jabber-data"></a>نظرة عامة على أرشفة بيانات Cisco Jabber

تشرح النظرة العامة التالية عملية استخدام موصل أرشفة Cisco Jabber على بيانات MS SQL في Microsoft 365.

![أرشفة سير العمل لبيانات Cisco Jabber.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. تعمل مؤسستك مع Cisco لإعداد وتكوين Cisco Jabber على MS SQL Database.

2. مرة واحدة كل 24 ساعة، يتم نسخ عناصر Cisco Jabber من MS SQL Database إلى موقع Veritas Merge1. يحول الموصل أيضا محتوى رسائل الدردشة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Cisco Jabber الذي تقوم بإنشائه في مدخل التوافق بموقع Veritas Merge1 كل يوم وينقل العناصر إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يقوم تعيين المستخدم التلقائي كموصل باستيراد العناصر إلى علب البريد الخاصة بمستخدمين محددين باستخدام قيمة خاصية *البريد الإلكتروني* للخطوة 3 الموضحة في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Cisco Jabber على MS SQL** في علب بريد المستخدمين، ويتم استيراد عناصر الرسالة إلى هذا المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر إليها باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر Cisco Jabber على هذه الخاصية، والتي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Veritas Merge1 لموصلات Microsoft. لإنشاء هذا الحساب، اتصل بدعم [عملاء Veritas](https://www.veritas.com/content/support/). ستقوم بتسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- قم بإعداد قاعدة بيانات MS SQL لاسترداد عناصر Jabber قبل إنشاء الموصل في الخطوة 1. ستحدد إعدادات الاتصال لقاعدة بيانات MS SQL عند تكوين موصل Cisco Jabber في الخطوة 2. لمزيد من المعلومات، راجع [دليل مستخدم موصلات الدمج1 لجهة خارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Cisco Jabber في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>الخطوة 1: إعداد موصل Cisco Jabber على MS SQL

الخطوة الأولى هي الوصول إلى **موصلات البيانات** في مدخل التوافق وإنشاء موصل ل Cisco Jabber على بيانات MS SQL.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/)**Data connectorsCisco** >  Jabber ثم انقر فوقه **على MS SQL**.

2. في صفحة **وصف منتج Cisco Jabber على MS SQL**، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين موصل Cisco Jabber على MS SQL على موقع Veritas Merge1

الخطوة الثانية هي تكوين Cisco Jabber على موصل MS SQL على موقع Veritas Merge1. للحصول على معلومات حول كيفية تكوين Cisco Jabber على موصل MS SQL، راجع [دليل مستخدم Merge1 Third-party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

بعد النقر فوق **"حفظ & إنهاء**"، يتم عرض صفحة **تعيين المستخدم** في معالج الموصل في مدخل التوافق.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال إعداد الموصل في مدخل التوافق، اتبع الخطوات التالية:

1. في **Map Cisco Jabber على MS SQL المستخدمين Microsoft 365 صفحة المستخدمين**، قم بتمكين تعيين المستخدم تلقائيا. تتضمن عناصر Cisco Jabber على MS SQL خاصية تسمى *"البريد الإلكتروني*"، والتي تحتوي على عناوين بريد إلكتروني للمستخدمين في مؤسستك. إذا كان بإمكان الموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر فوق **"التالي**"، وراجع الإعدادات، وانتقل إلى صفحة **"موصلات البيانات** " للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>الخطوة 4: مراقبة موصل Cisco Jabber

بعد إنشاء Cisco Jabber على موصل MS SQL، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com) **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **Connectors** ثم حدد **موصل Cisco Jabber على MS SQL** لعرض صفحة القائمة المنبثقة. تحتوي هذه الصفحة على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.
