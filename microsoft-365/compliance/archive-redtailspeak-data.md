---
title: إعداد موصل لأرشفة بيانات Red tail Speak في Microsoft 365
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
description: يمكن للمسؤولين إعداد موصل لاستيراد بيانات Red tail Speak وأرشفتها من Veritas Microsoft 365. يتيح لك هذا الموصل أرشفة البيانات من مصادر بيانات جهة خارجية في Microsoft 365. بعد أرشفة هذه البيانات، يمكنك استخدام ميزات التوافق مثل احتجاز قانوني والبحث في المحتوى ونهج الاستبقاء لإدارة بيانات جهة خارجية.
ms.openlocfilehash: 8c0e3c444bf285f951911a9de6e5ef3480eb6468
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575662"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>إعداد موصل لأرشفة بيانات Redtail Speak

استخدم موصل Veritas في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من علب بريد المستخدمين في Redtail Speak to user في Microsoft 365 الخاصة بك. يوفر لك Veritas موصل [Redtail Speak](https://globanet.com/redtail/) الذي تم تكوينه لالتقاط العناصر من خادم SFTP الخاص بالم المؤسسة حيث يتم تلقي العناصر من Redtail. يحول الموصل المحتوى من Redtail Speak إلى تنسيق رسالة بريد إلكتروني ثم يقوم باستيراد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Redtail Speak في علب بريد المستخدمين، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية و eDiscovery ونهج الاستبقاء وتسميات الاستبقاء. يمكن أن يساعد استخدام موصل Redtail Speak لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="overview-of-archiving-the-redtail-speak-data"></a>نظرة عامة حول أرشفة بيانات Redtail Speak

تشرح النظرة العامة التالية عملية استخدام موصل لأرشفة بيانات Redtail Speak في Microsoft 365.

![أرشفة سير العمل لبيانات Redtail Speak.](../media/RedtailSpeakConnectorWorkflow.png)

1. تعمل مؤسستك مع Redtail Speak لإعداد بوابة SMTP وتكوينها حيث يتم إعادة توجيه الرسائل من Redtail Speak إلى خادم SFTP الخاص بالم مؤسستك بشكل يومي.

2. مرة واحدة كل 24 ساعة، يتم نسخ عناصر Redtail Speak إلى موقع Veritas Merge1. يحول الموصل أيضا عناصر Redtail Speak إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Redtail Speak الذي تقوم مركز التوافق في Microsoft 365 به بموقع Veritas Merge1 كل يوم وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يقوم الموصل باستيراد عناصر Redtail Speak التي تم تحويلها إلى علب بريد مستخدمين معينين باستخدام قيمة خاصية البريد  الإلكتروني لتعيين المستخدم التلقائي كما هو موضح في الخطوة [3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Redtail Speak** في علب بريد المستخدمين، وتستورد العناصر إلى ذلك المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر لها باستخدام قيمة خاصية *البريد* الإلكتروني. يحتوي كل عنصر Redtail Speak على هذه الخاصية، التي يتم ملؤها عنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Veritas Merge1 لموصلات Microsoft. لإنشاء حساب، اتصل بدعم [عملاء Veritas](https://www.veritas.com/content/support/). يجب تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- في الخطوة 2، تحتاج إلى تحديد خادم SFTP الخاص مؤسستك. هذه الخطوة ضرورية لكي تتمكن Veritas Merge1 من الاتصال بها لتجميع بيانات Redtail Speak عبر SFTP.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Redtail Speak Importer في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يوجد موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. قد تشتمل التطبيقات والخدمات التي تقدمها جهة خارجية على تخزين بيانات عملاء مؤسستك ونقلها وحمايتها على أنظمة أخرى تقع خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات التوافق وحماية البيانات Microsoft 365. لا تقدم Microsoft أي تمثيل يشير فيه استخدام هذا المنتج للاتصال إلى تطبيقات  الأطراف الخارجية إلى أن تلك التطبيقات التي تقدمها جهة خارجية متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>الخطوة 1: إعداد موصل Redtail Speak

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مركز التوافق في Microsoft 365 وإنشاء موصل لبيانات Redtail Speak.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/) موصلات **البيانات وحدد** &gt; **Redtail Speak**.

2. في صفحة **وصف المنتج Redtail Speak** ، حدد **إضافة موصل جديد**.

3. في صفحة **شروط الخدمة** ، حدد **قبول**.

4. أدخل اسما فريدا يعرف الموصل، ثم حدد **التالي**.

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين موصل Redtail Speak على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل Redtail Speak على موقع Merge1. للحصول على معلومات حول كيفية تكوين موصل Redtail Speak، راجع [دمج1 دليل مستخدم الموصلات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf).

بعد تحديد **حفظ &،** يتم عرض صفحة تعيين المستخدم في  معالج الموصل في مركز التوافق في Microsoft 365.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

ل تعيين المستخدمين وإكمال إعداد الموصل، اتبع الخطوات التالية:

1. في صفحة **تعيين المستخدمين الذين يتحدثون Microsoft 365 المستخدمين**، يمكنك تعيين المستخدم تلقائيا. تتضمن عناصر Redtail Speak خاصية تسمى *البريد الإلكتروني*، والتي تحتوي على عناوين البريد الإلكتروني للمستخدمين في مؤسستك. إذا كان يمكن للموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. حدد **التالي**، وراجع الإعدادات، واذهب إلى صفحة  موصلات البيانات لرؤية تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>الخطوة 4: مراقبة موصل Redtail Speak

بعد إنشاء موصل Redtail Speak، يمكنك عرض حالة الموصل في مركز التوافق في Microsoft 365.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/) موصلات **البيانات** وحددها في التنقل الأيسر.

2. حدد علامة **التبويب موصلات** ثم حدد موصل **Redtail Speak** لعرض صفحة flyout. تعرض هذه الصفحة الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، حدد الارتباط **تنزيل السجل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 مبايت. سيتوفر الدعم للعناصر الكبيرة في وقت لاحق.