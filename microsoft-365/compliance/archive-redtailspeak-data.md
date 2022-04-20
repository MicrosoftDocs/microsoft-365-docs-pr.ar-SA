---
title: إعداد موصل أرشفة بيانات Red tail Speak في Microsoft 365
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
description: يمكن للمسؤولين إعداد موصل لاستيراد بيانات Red tail Speak وأرشفتها من Veritas إلى Microsoft 365. يتيح لك هذا الموصل أرشفة البيانات من مصادر بيانات الجهات الخارجية في Microsoft 365. بعد أرشفتك لهذه البيانات، يمكنك استخدام ميزات التوافق مثل الاحتجاز القانوني والبحث في المحتوى ونهج الاستبقاء لإدارة بيانات الجهات الخارجية.
ms.openlocfilehash: af568495cd7ee8b1bf003da71a4582462fbd5c4c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64950622"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>إعداد موصل أرشفة بيانات Redtail Speak

استخدم موصل Veritas في مدخل توافق Microsoft Purview لاستيراد البيانات وأرشفتها من Redtail Speak إلى علب بريد المستخدمين في مؤسسة Microsoft 365. يوفر لك Veritas موصل [Redtail Speak](https://globanet.com/redtail/) الذي تم تكوينه لالتقاط العناصر من خادم SFTP الخاص بمؤسستك حيث يتم تلقي العناصر من Redtail. يحول الموصل المحتوى من Redtail Speak إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Redtail Speak في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء. يمكن أن يساعد استخدام موصل Redtail Speak لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-the-redtail-speak-data"></a>نظرة عامة على أرشفة بيانات Redtail Speak

تشرح النظرة العامة التالية عملية استخدام موصل أرشفة بيانات Redtail Speak في Microsoft 365.

![أرشفة سير العمل لبيانات Redtail Speak.](../media/RedtailSpeakConnectorWorkflow.png)

1. تعمل مؤسستك مع Redtail Speak لإعداد بوابة SMTP وتكوينها حيث تتم إعادة توجيه الرسائل من Redtail Speak إلى خادم SFTP الخاص بمؤسستك بشكل يومي.

2. مرة واحدة كل 24 ساعة، يتم نسخ عناصر Redtail Speak إلى موقع Veritas Merge1. يقوم الموصل أيضا بتحويل عناصر Redtail Speak إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Redtail Speak الذي تقوم بإنشائه في مدخل التوافق بموقع Veritas Merge1 كل يوم وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يستورد الموصل عناصر Redtail Speak المحولة إلى علب بريد مستخدمين محددين باستخدام قيمة خاصية *"البريد الإلكتروني* " لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Redtail Speak** في علب بريد المستخدمين، ويتم استيراد العناصر إلى هذا المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر إليها باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر Redtail Speak على هذه الخاصية، والتي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Veritas Merge1 لموصلات Microsoft. لإنشاء حساب، اتصل بدعم [عملاء Veritas](https://www.veritas.com/content/support/). تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- في الخطوة 2، تحتاج إلى تحديد خادم SFTP الخاص بالمؤسسة. هذه الخطوة ضرورية بحيث يمكن ل Veritas Merge1 الاتصال بها لجمع بيانات Redtail Speak عبر SFTP.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Redtail Speak Importer في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>الخطوة 1: إعداد موصل Redtail Speak

الخطوة الأولى هي الوصول إلى صفحة **موصلات البيانات** في مدخل التوافق وإنشاء موصل لبيانات Redtail Speak.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/) **موصلات** &gt; البيانات وحدد **"Redtail Speak**".

2. في صفحة وصف منتج **Redtail Speak** ، حدد **إضافة موصل جديد**.

3. في صفحة **"شروط الخدمة** "، حدد **"قبول**".

4. أدخل اسما فريدا يعرف الموصل، ثم حدد **"التالي**".

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين موصل Redtail Speak على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل Redtail Speak على موقع Merge1. للحصول على معلومات حول كيفية تكوين موصل Redtail Speak، راجع [Merge1 دليل مستخدم موصلات الجهات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf).

بعد تحديد **"حفظ & إنهاء**"، يتم عرض صفحة **تعيين المستخدم** في معالج الموصل في مدخل التوافق.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال إعداد الموصل، اتبع الخطوات التالية:

1. في **خريطة Redtail Speak users Microsoft 365 صفحة المستخدمين**، قم بتمكين تعيين المستخدم تلقائيا. تتضمن عناصر Redtail Speak خاصية تسمى *"البريد الإلكتروني*"، والتي تحتوي على عناوين بريد إلكتروني للمستخدمين في مؤسستك. إذا كان بإمكان الموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. حدد **"التالي**"، راجع الإعدادات، وانتقل إلى صفحة **"موصلات البيانات** " للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>الخطوة 4: مراقبة موصل Redtail Speak

بعد إنشاء موصل Redtail Speak، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/) **موصلات البيانات وحددها** في جزء التنقل الأيمن.

2. حدد علامة التبويب **Connectors** ثم حدد موصل **Redtail Speak** لعرض صفحة القائمة المنبثقة. تعرض هذه الصفحة الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، حدد ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.