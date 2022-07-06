---
title: إعداد موصل أرشفة Cisco Jabber على بيانات Oracle في Microsoft 365
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
description: تعرف على كيفية إعداد موصل واستخدامه في مدخل التوافق في Microsoft Purview لاستيراد البيانات وأرشفتها من Cisco Jabber على Oracle إلى Microsoft 365.
ms.openlocfilehash: 9920ade2b025824fe7308142ac033872a656ff7a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636844"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-oracle-data"></a>إعداد موصل أرشفة Cisco Jabber على بيانات Oracle

استخدم موصل Veritas في مدخل التوافق في Microsoft Purview لاستيراد البيانات وأرشفتها من Cisco Jabber على نظام Oracle الأساسي إلى علب بريد المستخدمين في مؤسسة Microsoft 365. يوفر Veritas [Cisco Jabber على](https://www.veritas.com/insights/merge1/jabber) موصل Oracle الذي تم تكوينه لالتقاط العناصر من مصدر بيانات الجهات الخارجية (بشكل منتظم) واستيراد هذه العناصر إلى Microsoft 365. يحول الموصل المحتوى مثل الملفات وعمليات الملفات والتعليقات والمحتوى المشترك من Cisco Jabber على Oracle إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد تخزين Cisco Jabber على بيانات Oracle في علب بريد المستخدم، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء. يمكن أن يساعد استخدام Cisco Jabber على موصل Oracle لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-cisco-jabber-on-oracle-data"></a>نظرة عامة على أرشفة Cisco Jabber على بيانات Oracle

تشرح النظرة العامة التالية عملية استخدام موصل أرشفة Cisco Jabber على بيانات Oracle في Microsoft 365.

![أرشفة سير عمل Cisco Jabber على بيانات Oracle.](../media/CiscoJabberOnOracleConnectorWorkflow.png)

1. تعمل مؤسستك مع Cisco Jabber على Oracle لإعداد وتكوين Cisco Jabber على موقع Oracle.

2. مرة واحدة كل 24 ساعة، يتم نسخ Cisco Jabber على عناصر Oracle إلى موقع Veritas Merge1. يحول الموصل أيضا Cisco Jabber على عناصر Oracle إلى تنسيق رسالة بريد إلكتروني.

3. يتصل Cisco Jabber على موصل Oracle الذي تقوم بإنشائه في مدخل التوافق بموقع Veritas Merge1 كل يوم وينقل محتوى Jabber إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يستورد الموصل العناصر المحولة إلى علب بريد مستخدمين محددين باستخدام قيمة خاصية *البريد الإلكتروني* لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Cisco Jabber على Oracle** في علب بريد المستخدم، ويتم استيراد العناصر إلى هذا المجلد. يقوم الموصل بذلك باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر Jabber على هذه الخاصية، التي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-begin"></a>قبل البدء

- إنشاء حساب Merge1 لموصلات Microsoft. للقيام بذلك، اتصل بدعم [عملاء Veritas](https://www.veritas.com/content/support/en_US). تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور موصل البيانات مسؤول للمستخدم الذي يقوم بإنشاء Cisco Jabber على موصل Oracle في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور موصل البيانات مسؤول، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة أدوار مخصصة" في ["الأذونات" في مدخل التوافق في Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- موصل بيانات Veritas هذا في المعاينة العامة في بيئات GCC في سحابة Microsoft 365 US Government. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء في مؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-oracle-connector"></a>الخطوة 1: إعداد Cisco Jabber على موصل Oracle

الخطوة الأولى هي الوصول إلى صفحة **موصلات البيانات** في مدخل التوافق وإنشاء موصل لبيانات Jabber.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات** >  البيانات **ثم انقر فوقها Cisco Jabber على Oracle**.

2. في صفحة **وصف منتج Oracle في Cisco Jabber** ، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-cisco-jabber-on-oracle-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين Cisco Jabber على Oracle على موقع Veritas Merge1

الخطوة الثانية هي تكوين Cisco Jabber على موصل Oracle على موقع Veritas Merge1. للحصول على معلومات حول كيفية تكوين Cisco Jabber على موصل Oracle، راجع [Merge1 دليل مستخدم موصلات الجهات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20Oracle%20User%20Guide.pdf).

بعد النقر فوق **"حفظ & إنهاء**"، يتم عرض صفحة **تعيين المستخدم** في معالج الموصل في مدخل التوافق.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

لتعيين المستخدمين وإكمال إعداد الموصل في مدخل التوافق، اتبع الخطوات التالية:

1. في صفحة **Map Cisco Jabber على مستخدمي Oracle لمستخدمي Microsoft 365** ، قم بتمكين تعيين المستخدم التلقائي. يتضمن Cisco Jabber على عناصر Oracle خاصية تسمى *"البريد الإلكتروني*"، والتي تحتوي على عناوين بريد إلكتروني للمستخدمين في مؤسستك. إذا كان بإمكان الموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر فوق **"التالي**"، راجع الإعدادات، ثم انتقل إلى صفحة **"موصلات البيانات** " للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-cisco-jabber-on-oracle-connector"></a>الخطوة 4: مراقبة Cisco Jabber على موصل Oracle

بعد إنشاء Cisco Jabber على موصل Oracle، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى <https://compliance.microsoft.com/> **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **Connectors** ثم حدد **Cisco Jabber على** موصل Oracle لعرض صفحة القائمة المنبثقة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على معلومات حول البيانات التي تم استيرادها إلى سحابة Microsoft. لمزيد من المعلومات، راجع [عرض سجلات المسؤول لموصلات البيانات](data-connector-admin-logs.md).

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.
