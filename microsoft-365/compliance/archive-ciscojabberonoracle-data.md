---
title: إعداد موصل لأرشفة Cisco Jabber على بيانات Oracle في Microsoft 365
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
description: تعرف على كيفية إعداد موصل واستخدامه في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من Cisco Jabber على Oracle Microsoft 365.
ms.openlocfilehash: d58d015e94050bc82b427ba450314b7bb447d4d1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63573897"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-oracle-data"></a>إعداد موصل لأرشفة Cisco Jabber على بيانات Oracle

استخدم موصل Veritas في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من النظام الأساسي Cisco Jabber على Oracle إلى علب بريد المستخدمين في Microsoft 365 الخاصة بك. يوفر Veritas [Cisco Jabber](https://www.veritas.com/insights/merge1/jabber) على موصل Oracle الذي تم تكوينه لالتقاط العناصر من مصدر بيانات جهة خارجية (بشكل منتظم) واستيراد هذه العناصر إلى Microsoft 365. يحول الموصل المحتوى مثل الملفات وعمليات الملفات والتعليقات والمحتوى المشترك من Cisco Jabber على Oracle إلى تنسيق رسالة بريد إلكتروني، ثم يقوم باستيراد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين بيانات Cisco Jabber على Oracle في علب بريد المستخدمين، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية و eDiscovery ونهج الاستبقاء وتسميات الاستبقاء. يمكن أن يساعد استخدام Cisco Jabber على موصل Oracle لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="overview-of-archiving-cisco-jabber-on-oracle-data"></a>نظرة عامة حول أرشفة Cisco Jabber على بيانات Oracle

تشرح النظرة العامة التالية عملية استخدام موصل لأرشفة Cisco Jabber على بيانات Oracle في Microsoft 365.

![أرشفة سير العمل ل Cisco Jabber على بيانات Oracle.](../media/CiscoJabberOnOracleConnectorWorkflow.png)

1. تعمل مؤسستك مع Cisco Jabber على Oracle لإعداد Cisco Jabber وتكوينه على موقع Oracle.

2. مرة واحدة كل 24 ساعة، يتم نسخ Cisco Jabber على عناصر Oracle إلى موقع Veritas Merge1. يحول الموصل أيضا Cisco Jabber على عناصر Oracle إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Cisco Jabber على Oracle الذي تقوم بإنشاءه في مركز التوافق في Microsoft 365 بموقع Veritas Merge1 كل يوم وينقل محتوى جابر إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يقوم الموصل باستيراد العناصر التي تم تحويلها إلى علب بريد مستخدمين معينين باستخدام قيمة خاصية البريد  الإلكتروني لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Cisco Jabber على Oracle** في علب بريد المستخدمين، كما يتم استيراد العناصر إلى ذلك المجلد. يقوم الموصل بذلك باستخدام قيمة الخاصية *البريد* الإلكتروني. يحتوي كل عنصر من عناصر "جببر" على هذه الخاصية، التي يتم ملؤها عنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Merge1 لموصلات Microsoft. للقيام بذلك، اتصل بدعم [عملاء Veritas](https://www.veritas.com/content/support/en_US). يجب تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي ينشئ Cisco Jabber على موصل Oracle في الخطوة 1 (ويكمله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يوجد موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. قد تشتمل التطبيقات والخدمات التي تقدمها جهة خارجية على تخزين بيانات عملاء مؤسستك ونقلها وحمايتها على أنظمة أخرى تقع خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات التوافق وحماية البيانات Microsoft 365. لا تقدم Microsoft أي تمثيل يشير فيه استخدام هذا المنتج للاتصال إلى تطبيقات  الأطراف الخارجية إلى أن تلك التطبيقات التي تقدمها جهة خارجية متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-oracle-connector"></a>الخطوة 1: إعداد Cisco Jabber على موصل Oracle

الخطوة الأولى هي الوصول إلى صفحة "موصلات البيانات" في مركز التوافق في Microsoft 365 وإنشاء موصل لبيانات "جابر".

1. انتقل إلى <https://compliance.microsoft.com> موصلات **البيانات** >  ثم انقر **فوقهاCisco Jabber على Oracle**.

2. في الصفحة **Cisco Jabber على وصف منتج Oracle** ، انقر **فوق إضافة موصل**.

3. في صفحة **شروط الخدمة** ، انقر فوق **قبول**.

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **التالي**.

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-cisco-jabber-on-oracle-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين Cisco Jabber على Oracle على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل Cisco Jabber على Oracle على موقع Veritas Merge1. للحصول على معلومات حول كيفية تكوين Cisco Jabber على موصل Oracle، راجع [دمج1 دليل مستخدم الموصلات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20Oracle%20User%20Guide.pdf).

بعد النقر **فوق & إنهاء**، يتم عرض صفحة تعيين المستخدم  في معالج الموصل في مركز التوافق في Microsoft 365.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

ل تعيين المستخدمين وإكمال إعداد الموصل في مركز التوافق في Microsoft 365، اتبع الخطوات التالية:

1. في صفحة **Map Cisco Jabber على مستخدمي Oracle Microsoft 365 المستخدمين**، يمكنك تعيين المستخدم تلقائيا. تتضمن عناصر Cisco Jabber على Oracle خاصية تسمى *البريد الإلكتروني*، والتي تحتوي على عناوين البريد الإلكتروني للمستخدمين في مؤسستك. إذا كان يمكن للموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر **فوق** التالي، وراجع الإعدادات، ثم انتقل إلى صفحة  موصلات البيانات للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-cisco-jabber-on-oracle-connector"></a>الخطوة 4: مراقبة Cisco Jabber على موصل Oracle

بعد إنشاء Cisco Jabber على موصل Oracle، يمكنك عرض حالة الموصل في مركز التوافق في Microsoft 365.

1. انتقل إلى <https://compliance.microsoft.com/> **موصلات البيانات وانقر** فوقها في التنقل الأيسر.

2. انقر فوق **علامة التبويب موصلات** ، ثم حدد **موصل Cisco Jabber على Oracle** لعرض صفحة القائمة المطيرة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق الارتباط **تنزيل السجل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 مبايت. سيتوفر الدعم للعناصر الكبيرة في وقت لاحق.
