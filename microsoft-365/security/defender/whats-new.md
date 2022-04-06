---
title: ما الجديد في Microsoft 365 Defender
description: تسرد الميزات والوظائف الجديدة في Microsoft 365 Defender
keywords: ما الجديد في Microsoft 365 Defender، ga، متوفر بشكل عام، إمكانات، متوفر، جديد
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
ms.openlocfilehash: aebf7a82a886540374176c06535e9f0097e73a03
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499804"
---
# <a name="whats-new-in-microsoft-365-defender"></a>ما الجديد في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> هل تريد تجربة Microsoft 365 Defender؟ يمكنك [تقييمه في بيئة معملية](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) أو [تشغيل مشروعك التجريبي في الإنتاج](m365d-pilot.md?ocid=cx-evalpilot).

تتوفر الميزات التالية في المعاينة أو تتوفر بشكل عام (GA) في أحدث إصدار من Microsoft 365 Defender.

موجز RSS: يتم إعلامك عند تحديث هذه الصفحة عن طريق نسخ عنوان URL التالي ولصقه في قارئ الموجز:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

لمزيد من المعلومات حول أحدث ما في منتجات أمان Microsoft Defender الأخرى، راجع:

- [ما الجديد في Microsoft Defender لـ Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [ما الجديد في Microsoft Defender لنقطة النهاية](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [ما الجديد في Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [ما الجديد في Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

يمكنك أيضا الحصول على تحديثات المنتجات والإعلامات المهمة من خلال [مركز الرسائل](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 



## <a name="march-2022"></a>مارس 2022

- (Preview) تم تحسين قائمة انتظار الأحداث باستخدام العديد من الميزات المصممة لمساعدتك على إجراء التحريات. تتضمن التحسينات قدرات مثل القدرة على البحث عن الأحداث حسب المعرف أو الاسم، وتحديد نطاق وقت مخصص، وغيرها.

## <a name="december-2021"></a>ديسمبر 2021

- (GA) لقد `DeviceTvmSoftwareEvidenceBeta` تم إضافة الجدول على المدى القصير في عملية البحث المتقدم للسماح لك لعرض دليل على مكان اكتشاف برنامج معين على جهاز.

## <a name="november-2021"></a>نوفمبر 2021

- (Preview) تتوفر الآن ميزة الوظائف الإضافية لإدارة التطبيق ل Defender for Cloud Apps في Microsoft 365 Defender. يوفر حوكمة التطبيق إمكانية لإدارة الأمان والسياسات تم تصميمها للتطبيقات التي تم تمكين OAuth Microsoft 365 البيانات من خلال Microsoft Graph واجهات برمجة التطبيقات. توفر إدارة التطبيق إمكانية الرؤية الكاملة والوساطة والحوكمة في كيفية وصول هذه التطبيقات والمستخدمين إليها إلى بياناتك الحساسة المخزنة في Microsoft 365 واستخدامها ومشاركتها من خلال نتائج تحليلات قابلة للتنفيذ وتنبيهات النهج والإجراءات التلقائية. [تعرف على المزيد حول إدارة التطبيق](/cloud-app-security/app-governance-manage-app-governance).
- (Preview) تحتوي [](advanced-hunting-overview.md) صفحة الصيد المتقدمة الآن على دعم متعدد الbb، والتمرير الذكي، و علامات تبويب المخططات المبسطة، وخيارات التحرير السريع للاستعلامات، ومؤشر استخدام موارد الاستعلام، وتحسينات أخرى لجعل الاستعلامات أكثر سلاسة وأسهل لضبطها.
- (Preview) يمكنك الآن استخدام الارتباط إلى [](advanced-hunting-link-to-incident.md) ميزة الحدث لتضمين أحداث أو سجلات من نتائج استعلام البحث المتقدم مباشرة في حادث جديد أو موجود تقوم بالتحري فيه.

## <a name="october-2021"></a>أكتوبر 2021

- (GA) في الصيد المتقدم، تم إضافة المزيد من الأعمدة في [جدول CloudAppEvents](advanced-hunting-cloudappevents-table.md) . يمكنك الآن تضمين `AccountType`و `IsExternalUser`و `IsImpersonated`و `IPTags`و `IPCategory`و إلى `UserAgentTags` الاستعلامات الخاصة بك.

## <a name="september-2021"></a>سبتمبر 2021

- (GA) Microsoft Defender لـ Office 365 بيانات الحدث المتوفرة في Microsoft 365 Defender الأحداث المتدفقة. يمكنك الاطلاع على توفر أنواع الأحداث ووضعها في أنواع Microsoft 365 Defender [في دفق API](supported-event-types.md).
- (GA) Microsoft Defender لـ Office 365 البيانات المتوفرة في الصيد المتقدم متوفرة الآن بشكل عام.
- (GA) تعيين الأحداث والتنبيهات إلى حسابات المستخدمين

  يمكنك تعيين حادث، وجميع التنبيهات المقترنة به، إلى حساب مستخدم من تعيين إلى **:** في الجزء إدارة الحادث لحادث أو جزء  إدارة التنبيه من تنبيه.

## <a name="august-2021"></a>أغسطس 2021

- (Preview) Microsoft Defender لـ Office 365 البيانات المتوفرة في البحث المتقدم

  يمكن أن توفر الأعمدة الجديدة في جداول البريد الإلكتروني مزيدا من المعرفة حول التهديدات المستندة إلى البريد الإلكتروني من أجل إجراء المزيد من التحريات المعمقة باستخدام الصيد المتقدم. يمكنك الآن تضمين العمود `AuthenticationDetails` في [EmailEvents](./advanced-hunting-emailevents-table.md)`FileSize` وفي [EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md)`ThreatTypes` `DetectionMethods` وفي [EmailPostDeliveryEvents](./advanced-hunting-emailpostdeliveryevents-table.md) الجداول.

- (Preview) رسم بياني للحوادث

  تظهر علامة  تبويب Graph جديدة على علامة  التبويب ملخص لحادث ما النطاق الكامل للهجوم، وكيفية انتشار الهجوم عبر شبكتك مع مرور الوقت، ومن أين بدأ، والمدى الذي ذهب منه المهاجم.

## <a name="july-2021"></a>يوليو 2021

- [كتالوج الخدمات الاحترافية](https://sip.security.microsoft.com/interoperability/professional_services)

  تحسين قدرات الكشف والتحري والخطر في النظام الأساسي باستخدام اتصالات الشركاء المعتمدة.

## <a name="june-2021"></a>يونيو 2021

- (Preview) [عرض التقارير وفقا لعلامات التهديدات](threat-analytics.md#view-reports-per-threat-tags)

  تساعدك علامات التهديدات على التركيز على فئات تهديدات معينة ومراجعة التقارير الأكثر صلة.

- (Preview) [برمجة تطبيقات النقل المتدفق](../defender-endpoint/raw-data-export.md)

  Microsoft 365 Defender دفق كل الأحداث المتوفرة من خلال "البحث المتقدم" إلى مركز الأحداث و/أو حساب تخزين Azure.

- (Preview) [اتخاذ إجراء في مجال البحث المتقدم](advanced-hunting-take-action.md)

  تحتوي بسرعة على تهديدات أو تعالج الأصول التي تم اختراقها التي تعثر عليها في [عملية البحث المتقدمة](advanced-hunting-overview.md).

- (Preview) [مرجع مخطط داخل المدخل](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  احصل على معلومات حول جداول مخطط الصيد المتقدم مباشرة في مركز الأمان. بالإضافة إلى أوصاف الأعمدة والأعمدة، يتضمن هذا المرجع أنواع أحداث معتمدة (`ActionType` قيم) واستعلامات نموذجية.

- (Preview) [DeviceFromIP() (الدالة DeviceFromIP()](advanced-hunting-devicefromip-function.md)

  احصل على معلومات حول الأجهزة التي تم تعيين عنوان IP أو عناوين لها في نطاق وقت معين.

## <a name="may-2021"></a>مايو 2021

- [صفحة تنبيه جديدة في مدخل Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  توفير معلومات محسنة للسياقات في هجوم. يمكنك معرفة التنبيه المشغل الآخر الذي تسبب في التنبيه الحالي وجميع الكيانات والأنشطة المتأثرة بالهجوم، بما في ذلك الملفات والمستخدمين علب البريد. راجع [التحقق من التنبيهات](/microsoft-365/security/defender/investigate-alerts) للحصول على مزيد من المعلومات.

- [رسم بياني للاتجاهات للحوادث والتنبيهات في مدخل Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  تحديد ما إذا كان هناك عدة تنبيهات لحادث واحد أو أن مؤسستك قد تم هجومها بعدة أحداث مختلفة. راجع [تحديد أولوية الأحداث](/microsoft-365/security/defender/incident-queue) للحصول على مزيد من المعلومات.

## <a name="april-2021"></a>2021 ابريل

- Microsoft 365 Defender

  يتوفر الآن [Microsoft 365 Defender](https://security.microsoft.com) المدخل المحسن. تجمع هذه التجربة الجديدة بين Defender for Endpoint Defender لـ Office 365 و Defender for Identity والمزيد في مدخل واحد. هذا هو المنزل الجديد لإدارة عناصر التحكم في الأمان. [تعرف على الجديد](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender تحليل المخاطر](threat-analytics.md)

  تساعدك تحليلات المخاطر على الاستجابة للهجمات النشطة وتقليل تأثيرها. يمكنك أيضا التعرف على محاولات الهجمات التي حظرتها الحلول Microsoft 365 Defender واتخاذ إجراءات وقائية تخفف من خطر التعرض للضوء بشكل أكبر وتزيد من مرونة. كجزء من تجربة الأمان الموحدة، تتوفر الآن تحليلات المخاطر Microsoft Defender لنقطة النهاية و Microsoft Defender Office تراخيص E5.

## <a name="march-2021"></a>مارس 2021

- [جدول CloudAppEvents](advanced-hunting-cloudappevents-table.md)

  يمكنك العثور على معلومات حول الأحداث في تطبيقات وخدمات سحابية متنوعة تغطيها Microsoft Cloud App Security. يتضمن هذا الجدول أيضا المعلومات المتوفرة مسبقا في `AppFileEvents` الجدول.

