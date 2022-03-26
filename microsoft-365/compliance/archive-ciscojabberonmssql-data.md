---
title: إعداد موصل لأرشفة Cisco Jabber على بيانات MS SQL في Microsoft 365
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
description: يمكن للمسؤولين إعداد موصل لاستيراد Cisco Jabber وأرشفته على MS SQL من Veritas في Microsoft 365. يتيح لك هذا الموصل أرشفة البيانات من مصادر بيانات جهة خارجية في Microsoft 365. بعد أرشفة هذه البيانات، يمكنك استخدام ميزات التوافق مثل احتجاز قانوني والبحث في المحتوى ونهج الاستبقاء لإدارة بيانات جهة خارجية.
ms.openlocfilehash: 66f09f2fafcd33d8bc73bdaed61b41354e9633f7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569715"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>إعداد موصل لأرشفة Cisco Jabber على بيانات MS SQL

استخدم موصل Veritas في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من النظام الأساسي Cisco Jabber إلى علب بريد المستخدمين في Microsoft 365 الخاصة بك. يوفر لك Veritas موصل [Cisco Jabber](https://globanet.com/jabber/) الذي تم تكوينه لالتقاط العناصر من قاعدة بيانات MS SQL الخاصة بجابر، مثل رسائل الدردشة 1:1 والمحادثات الجماعية ثم استيراد هذه العناصر إلى Microsoft 365. يسترد الموصل البيانات من قاعدة بيانات MS SQL الخاصة ب Cisco Jabber، ويحول المحتوى من حساب Cisco Jabber الخاص بالمستخدم إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Cisco Jabber في علب بريد المستخدمين، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية و eDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل Cisco Jabber لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="overview-of-archiving-cisco-jabber-data"></a>نظرة عامة حول أرشفة بيانات Cisco Jabber

تشرح النظرة العامة التالية عملية استخدام موصل لأرشفة Cisco Jabber على MS SQL بيانات في Microsoft 365.

![سير عمل الأرشفة لبيانات Cisco Jabber.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. تعمل مؤسستك مع Cisco لإعداد Cisco Jabber وتكوينه على MS SQL Database.

2. مرة واحدة كل 24 ساعة، يتم نسخ عناصر Cisco Jabber من قاعدة بيانات MS SQL إلى موقع Veritas Merge1. يحول الموصل أيضا محتوى رسائل الدردشة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Cisco Jabber الذي تقوم مركز التوافق في Microsoft 365 به بموقع Veritas Merge1 كل يوم وينقل العناصر إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يقوم التعيين التلقائي للمستخدم كموصل باستيراد العناصر إلى علب بريد مستخدمين معينين باستخدام قيمة خاصية البريد الإلكتروني الخاصة  ب كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد **باسم Cisco Jabber على MS SQL** في علب بريد المستخدمين، كما يتم استيراد عناصر الرسالة إلى ذلك المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر لها باستخدام قيمة خاصية *البريد* الإلكتروني. يحتوي كل عنصر Cisco Jabber على هذه الخاصية، التي يتم ملؤها عنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Veritas Merge1 لموصلات Microsoft. لإنشاء هذا الحساب، اتصل ب [دعم عملاء Veritas](https://www.veritas.com/content/support/). سيتم تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- قم بإعداد قاعدة بيانات MS SQL لاسترداد عناصر Jabber من قبل إنشاء الموصل في الخطوة 1. ستحدد إعدادات الاتصال لقاعدة بيانات MS SQL عند تكوين موصل Cisco Jabber في الخطوة 2. للحصول على مزيد من المعلومات، راجع [دليل المستخدم Merge1 Connectors الخاص ب جهة خارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي ينشئ موصل Cisco Jabber في الخطوة 1 (ويكمله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يوجد موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. قد تشتمل التطبيقات والخدمات التي تقدمها جهة خارجية على تخزين بيانات عملاء مؤسستك ونقلها وحمايتها على أنظمة أخرى تقع خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات التوافق وحماية البيانات Microsoft 365. لا تقدم Microsoft أي تمثيل يشير فيه استخدام هذا المنتج للاتصال إلى تطبيقات  الأطراف الخارجية إلى أن تلك التطبيقات التي تقدمها جهة خارجية متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>الخطوة 1: إعداد Cisco Jabber على MS SQL موصل

الخطوة الأولى هي الوصول إلى موصلات  البيانات في مركز التوافق في Microsoft 365 وإنشاء موصل ل Cisco Jabber على بيانات MS SQL.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com/)موصلات **البيانات** >  ثم انقر **فوقهاCisco Jabber على MS SQL**.

2. في الصفحة **Cisco Jabber على MS SQL** وصف المنتج، انقر فوق **إضافة موصل**.

3. في صفحة **شروط الخدمة** ، انقر فوق **قبول**.

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **التالي**.

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين موصل Cisco Jabber على MS SQL على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل Cisco Jabber على MS SQL على موقع Veritas Merge1. للحصول على معلومات حول كيفية تكوين Cisco Jabber على MS SQL موصل، راجع [دمج1 دليل مستخدم الموصلات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

بعد النقر **فوق & إنهاء**، يتم عرض صفحة تعيين المستخدم  في معالج الموصل في مركز التوافق في Microsoft 365.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال الموصل الذي تم إعداده في مركز التوافق في Microsoft 365، اتبع الخطوات التالية:

1. في الصفحة **Map Cisco Jabber على MS SQL للمستخدمين** Microsoft 365 المستخدمين، يمكنك تعيين المستخدم تلقائيا. تتضمن عناصر Cisco Jabber SQL MS خاصية تسمى البريد الإلكتروني، والتي تحتوي على عناوين البريد الإلكتروني للمستخدمين في مؤسستك. إذا كان يمكن للموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر **فوق** التالي، وراجع الإعدادات، واذهب إلى  صفحة موصلات البيانات للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>الخطوة 4: مراقبة موصل Cisco Jabber

بعد إنشاء Cisco Jabber على موصل MS SQL، يمكنك عرض حالة الموصل في مركز التوافق في Microsoft 365.

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com) **موصلات البيانات وانقر** فوقها في التنقل الأيسر.

2. انقر فوق **علامة التبويب موصلات**، ثم حدد **Cisco Jabber على MS** SQL لعرض صفحة flyout. تحتوي هذه الصفحة على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق الارتباط **تنزيل السجل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 مبايت. سيتوفر الدعم للعناصر الكبيرة في وقت لاحق.
