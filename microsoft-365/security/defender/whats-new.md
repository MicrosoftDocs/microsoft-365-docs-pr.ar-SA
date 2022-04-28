---
title: الجديد في Microsoft 365 Defender
description: سرد الميزات والوظائف الجديدة في Microsoft 365 Defender
keywords: أحدث الميزات في Microsoft 365 Defender، و ga، والمتاحة بشكل عام، والقدرات، والمتاحة، والجديدة
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 56e22e0525324c59d2d62adaf2325edc3317ccd6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096039"
---
# <a name="whats-new-in-microsoft-365-defender"></a>الجديد في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

>الميزات التالية في المعاينة أو متوفرة بشكل عام (GA) في أحدث إصدار من Microsoft 365 Defender.

موجز RSS: يتم إعلامك عند تحديث هذه الصفحة عن طريق نسخ عنوان URL التالي ولصقه في قارئ الموجز:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

لمزيد من المعلومات حول أحدث الميزات في منتجات أمان Microsoft Defender الأخرى، راجع:

- [أحدث الميزات في Microsoft Defender لـ Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [ما الجديد في Microsoft Defender لنقطة النهاية](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [ما الجديد في Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [ما الجديد في Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

يمكنك أيضا الحصول على تحديثات المنتج والإعلامات المهمة من خلال [مركز الرسائل](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 


## <a name="april-2022"></a>أبريل 2022
- (معاينة) يمكن الآن اتخاذ [إجراءات](advanced-hunting-take-action.md) على رسائل البريد الإلكتروني مباشرة من نتائج استعلام التتبع. يمكن نقل رسائل البريد الإلكتروني إلى مجلدات أخرى أو حذفها بشكل دائم. 

## <a name="march-2022"></a>مارس 2022

- (معاينة) تم تحسين قائمة انتظار الحوادث باستخدام العديد من الميزات المصممة لمساعدة التحقيقات الخاصة بك. تتضمن التحسينات قدرات مثل القدرة على البحث عن الحوادث حسب المعرف أو الاسم، وتحديد نطاق زمني مخصص، وغيرها.


## <a name="december-2021"></a>ديسمبر 2021

- (GA) `DeviceTvmSoftwareEvidenceBeta` تمت إضافة الجدول على أساس قصير الأجل في التتبع المتقدم للسماح لك بعرض دليل على مكان اكتشاف برنامج معين على جهاز.

## <a name="november-2021"></a>نوفمبر 2021

- (معاينة) تتوفر الآن ميزة الوظيفة الإضافية لإدارة التطبيقات إلى Defender for Cloud Apps في Microsoft 365 Defender. توفر إدارة التطبيقات إمكانية إدارة الأمان والنهج المصممة للتطبيقات التي تدعم OAuth والتي يمكنها الوصول إلى بيانات Microsoft 365 من خلال واجهات برمجة تطبيقات Microsoft Graph. توفر حوكمة التطبيقات الرؤية الكاملة والمعالجة والحوكمة في كيفية وصول هذه التطبيقات ومستخدميها إلى بياناتك الحساسة المخزنة في Microsoft 365 واستخدامها ومشاركتها من خلال رؤى قابلة للتنفيذ وتنبيهات وإجراءات نهج تلقائية. [تعرف على المزيد حول حوكمة التطبيق](/cloud-app-security/app-governance-manage-app-governance).
- (معاينة) تحتوي صفحة [التتبع المتقدمة](advanced-hunting-overview.md) الآن على دعم متعدد المستويات، والتمرير الذكي، وعلامات تبويب المخطط المبسطة، وخيارات التحرير السريع للاستعلامات، ومؤشر استخدام موارد الاستعلام، والتحسينات الأخرى لجعل الاستعلام أكثر سلاسة وأسهل في ضبطه.
- (معاينة) يمكنك الآن استخدام [الارتباط إلى ميزة الحدث](advanced-hunting-link-to-incident.md) لتضمين الأحداث أو السجلات من نتائج استعلام التتبع المتقدمة مباشرة في حادث جديد أو موجود تقوم بالتحقيق فيه.

## <a name="october-2021"></a>أكتوبر 2021

- (GA) في التتبع المتقدم، تمت إضافة المزيد من الأعمدة في جدول [CloudAppEvents](advanced-hunting-cloudappevents-table.md) . يمكنك الآن تضمين `AccountType`استعلاماتك `IsExternalUser`، و، `IsImpersonated`و، `IPTags`و، و، `IPCategory`و `UserAgentTags` .

## <a name="september-2021"></a>سبتمبر 2021

- (GA) تتوفر Microsoft Defender لـ Office 365 بيانات الحدث في واجهة برمجة تطبيقات دفق الأحداث Microsoft 365 Defender. يمكنك الاطلاع على توفر أنواع الأحداث وحالتها في [أنواع أحداث Microsoft 365 Defender المعتمدة في واجهة برمجة تطبيقات الدفق](supported-event-types.md).
- (GA) Microsoft Defender لـ Office 365 البيانات المتاحة في التتبع المتقدم متاحة الآن بشكل عام.
- (GA) تعيين الحوادث والتنبيهات لحسابات المستخدمين

  يمكنك تعيين حدث، وكافة التنبيهات المقترنة به، إلى حساب مستخدم من **"تعيين" إلى:** في جزء **"إدارة الحادث** " لحدث أو جزء **"إدارة التنبيه** " في تنبيه.

## <a name="august-2021"></a>أغسطس 2021

- (معاينة) Microsoft Defender لـ Office 365 البيانات المتوفرة في التتبع المتقدم

  يمكن أن توفر الأعمدة الجديدة في جداول البريد الإلكتروني مزيدا من التفاصيل حول التهديدات المستندة إلى البريد الإلكتروني لإجراء تحقيقات أكثر شمولا باستخدام التتبع المتقدم. يمكنك الآن تضمين `AuthenticationDetails` العمود في [EmailEvents](./advanced-hunting-emailevents-table.md) وفي `FileSize` [EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md) وفي `ThreatTypes` `DetectionMethods` جداول [EmailPostDeliveryEvents](./advanced-hunting-emailpostdeliveryevents-table.md) .

- (معاينة) رسم بياني للحوادث

  تظهر علامة تبويب **Graph** جديدة على علامة تبويب **الملخص** لأحد الحوادث النطاق الكامل للهجوم، وكيفية انتشار الهجوم عبر شبكتك بمرور الوقت، ومكان بدائه، والمدى الذي ذهب إليه المهاجم.

## <a name="july-2021"></a>يوليو 2021

- [كتالوج الخدمات الاحترافية](https://sip.security.microsoft.com/interoperability/professional_services)

  تعزيز قدرات الكشف والتحقيق والتحلي بالتهديدات للنظام الأساسي باستخدام اتصالات الشريك المدعومة.

## <a name="june-2021"></a>يونيو 2021

- (معاينة) [عرض التقارير لكل علامات التهديد](threat-analytics.md#view-reports-per-threat-tags)

  تساعدك علامات التهديد على التركيز على فئات مخاطر معينة ومراجعة التقارير الأكثر صلة.

- (معاينة) [واجهة برمجة تطبيقات الدفق](../defender-endpoint/raw-data-export.md)

  يدعم Microsoft 365 Defender دفق جميع الأحداث المتوفرة من خلال Advanced Hunting إلى Event Hubs و/أو حساب تخزين Azure.

- (معاينة) [اتخاذ إجراء في التتبع المتقدم](advanced-hunting-take-action.md)

  تحتوي بسرعة على تهديدات أو تعالج الأصول المخترقة التي [تجدها في التتبع المتقدم](advanced-hunting-overview.md).

- (معاينة) [مرجع مخطط المدخل](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  احصل على معلومات حول جداول مخطط التتبع المتقدمة مباشرة في مركز الأمان. بالإضافة إلى أوصاف الجدول والأعمدة، يتضمن هذا المرجع أنواع الأحداث المعتمدة (`ActionType` القيم) والاستعلامات النموذجية.

- (معاينة) [DeviceFromIP() (الدالة DeviceFromIP)](advanced-hunting-devicefromip-function.md)

  احصل على معلومات حول الأجهزة التي تم تعيين عنوان IP محدد لها أو عناوينها في نطاق زمني معين.

## <a name="may-2021"></a>مايو 2021

- [صفحة تنبيه جديدة في مدخل Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  يوفر معلومات محسنة للسياق في هجوم. يمكنك معرفة التنبيه المشغل الآخر الذي تسبب في التنبيه الحالي وجميع الكيانات والأنشطة المتأثرة التي ينطوي عليها الهجوم، بما في ذلك الملفات والمستخدمين وعلب البريد. راجع [التحقيق في التنبيهات](/microsoft-365/security/defender/investigate-alerts) للحصول على مزيد من المعلومات.

- [رسم بياني للاتجاه للحوادث والتنبيهات في مدخل Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  حدد ما إذا كانت هناك عدة تنبيهات لحادث واحد أو أن مؤسستك تتعرض للهجوم بعدة حوادث مختلفة. راجع [تحديد أولويات الحوادث](/microsoft-365/security/defender/incident-queue) للحصول على مزيد من المعلومات.

## <a name="april-2021"></a>2021 ابريل

- Microsoft 365 Defender

  يتوفر الآن مدخل [Microsoft 365 Defender](https://security.microsoft.com) المحسن. تجمع هذه التجربة الجديدة بين Defender for Endpoint و Defender لـ Office 365 و Defender for Identity والمزيد في مدخل واحد. هذا هو المنزل الجديد لإدارة عناصر التحكم في الأمان. [تعرف على أحدث الميزات](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender تقرير تحليلات التهديدات](threat-analytics.md)

  تساعدك تحليلات التهديدات على الاستجابة إلى تأثير الهجمات النشطة وتقليله. يمكنك أيضا التعرف على محاولات الهجوم التي تمنعها حلول Microsoft 365 Defender واتخاذ إجراءات وقائية تخفف من مخاطر التعرض بشكل أكبر وتزيد من المرونة. كجزء من تجربة الأمان الموحدة، تتوفر الآن تحليلات التهديدات ل Microsoft Defender لنقطة النهاية وMicrosoft Defender لحاملي تراخيص E5 Office.

## <a name="march-2021"></a>مارس 2021

- [جدول CloudAppEvents](advanced-hunting-cloudappevents-table.md)

  ابحث عن معلومات حول الأحداث في العديد من التطبيقات والخدمات السحابية التي تغطيها Microsoft Cloud App Security. يتضمن هذا الجدول أيضا معلومات متوفرة مسبقا في `AppFileEvents` الجدول.

