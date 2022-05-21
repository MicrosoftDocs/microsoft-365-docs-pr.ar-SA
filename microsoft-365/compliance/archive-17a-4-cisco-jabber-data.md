---
title: إعداد موصل أرشفة بيانات Cisco Jabber في Microsoft 365
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
description: تعرف على كيفية إعداد موصل Cisco Jabber DataParser 17a-4 واستخدامه لاستيراد بيانات Cisco Jabber وأرشفتها في Microsoft 365.
ms.openlocfilehash: 3cc3fc0642b40bfd16f7e8b42fa3d68a98e7bca9
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622180"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-data"></a>إعداد موصل أرشفة بيانات Cisco Jabber

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

استخدم [Cisco Jabber DataParser](https://www.17a-4.com/jabber-dataparser/) من 17a-4 LLC لاستيراد البيانات وأرشفتها من Cisco Jabber إلى علب بريد المستخدمين في مؤسستك Microsoft 365. يتضمن DataParser موصل Cisco Jabber الذي تم تكوينه لالتقاط العناصر من مصدر بيانات تابع لجهة خارجية واستيراد هذه العناصر إلى Microsoft 365. يحول موصل Cisco Jabber DataParser بيانات Cisco Jabber إلى تنسيق رسالة بريد إلكتروني ثم يستورد هذه العناصر إلى علب بريد المستخدمين في Microsoft 365.

بعد تخزين بيانات Cisco Jabber في علب بريد المستخدمين، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. يمكن أن يساعد استخدام موصل Cisco Jabber لاستيراد البيانات وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="overview-of-archiving-cisco-jabber-data"></a>نظرة عامة على أرشفة بيانات Cisco Jabber

تشرح النظرة العامة التالية عملية استخدام موصل بيانات أرشفة بيانات Cisco Jabber في Microsoft 365.

![أرشفة سير العمل لبيانات Cisco Jabber من 17a-4.](../media/CiscoJabberDataParserConnectorWorkflow.png)

1. تعمل مؤسستك مع 17a-4 لإعداد وتكوين Cisco Jabber DataParser.

2. بشكل منتظم، يتم تجميع عناصر Cisco Jabber بواسطة DataParser. يقوم DataParser أيضا بتحويل محتوى رسالة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل موصل Cisco Jabber DataParser الذي تقوم بإنشائه في مدخل التوافق في Microsoft Purview ب DataParser وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يتم إنشاء مجلد فرعي في مجلد علبة الوارد يسمى **Cisco Jabber DataParser** في علب بريد المستخدمين، ويتم استيراد عناصر Cisco Jabber إلى هذا المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر إليها باستخدام قيمة خاصية *"البريد الإلكتروني* ". يحتوي كل عنصر Cisco Jabber على هذه الخاصية، والتي يتم ملؤها بعنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب DataParser لموصلات Microsoft. للقيام بذلك، اتصل [ب 17a-4 LLC](https://www.17a-4.com/contact/). تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإنشاء موصل Cisco Jabber DataParser في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة أدوار مخصصة" في ["الأذونات" في مدخل التوافق في Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يتوفر موصل البيانات 17a-4 هذا في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. قد تتضمن تطبيقات وخدمات الجهات الخارجية تخزين بيانات العملاء الخاصة بمؤسستك وإرسالها ومعالجتها على أنظمة تابعة لجهات خارجية خارج البنية الأساسية Microsoft 365 وبالتالي لا تغطيها التزامات Microsoft Purview وحماية البيانات. لا تقدم Microsoft أي تمثيل يشير إلى أن استخدام هذا المنتج للاتصال بتطبيقات الجهات الخارجية يعني أن تطبيقات الجهات الخارجية هذه متوافقة مع FEDRAMP.

## <a name="step-1-set-up-a-cisco-jabber-dataparser-connector"></a>الخطوة 1: إعداد موصل Cisco Jabber DataParser

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مدخل التوافق وإنشاء موصل 17a-4 لبيانات Cisco Jabber.

1. انتقل إلى <https://compliance.microsoft.com> **Data connectorsCisco** >  **Jabber DataParser ثم انقر فوقها**.

2. في صفحة وصف منتج **Cisco Jabber DataParser** ، انقر فوق **"إضافة موصل**".

3. في صفحة **"شروط الخدمة** "، انقر فوق **"قبول**".

4. أدخل اسما فريدا يعرف الموصل ثم انقر فوق **"التالي**".

5. سجل الدخول إلى حساب 17a-4 الخاص بك وأكمل الخطوات في معالج اتصال Cisco Jabber DataParser.

## <a name="step-2-configure-the-cisco-jabber-dataparser-connector"></a>الخطوة 2: تكوين موصل Cisco Jabber DataParser

العمل مع دعم 17a-4 لتكوين موصل Cisco Jabber DataParser.

## <a name="step-3-map-users"></a>الخطوة 3: تعيين المستخدمين

سيقوم موصل Cisco Jabber DataParser تلقائيا بتعيين المستخدمين إلى عناوين بريدهم الإلكتروني Microsoft 365 قبل استيراد البيانات إلى Microsoft 365.

## <a name="step-4-monitor-the-cisco-jabber-dataparser-connector"></a>الخطوة 4: مراقبة موصل Cisco Jabber DataParser

بعد إنشاء موصل Cisco Jabber DataParser، يمكنك عرض حالة الموصل في مدخل التوافق.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات البيانات وانقر فوقها** في جزء التنقل الأيمن.

2. انقر فوق علامة التبويب **"Connectors** "، ثم حدد موصل Cisco Jabber DataParser الذي أنشأته لعرض صفحة القائمة المنبثقة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق ارتباط **سجل التنزيل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على معلومات حول البيانات التي تم استيرادها إلى سحابة Microsoft. لمزيد من المعلومات، راجع [عرض سجلات المسؤول لموصلات البيانات](data-connector-admin-logs.md).

## <a name="known-issues"></a>المشاكل المعروفة

في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 ميغابايت. سيتوفر دعم العناصر الأكبر حجما في وقت لاحق.
