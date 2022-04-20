---
title: مقارنة ميزات الأمان في خطط Microsoft 365 للشركات الصغيرة والمتوسطة الحجم
description: فهم الاختلافات بين Defender for Business و Defender لنقطة النهاية. يمكن أن تساعدك معرفة ما هو مضمن في كل خطة على اتخاذ قرار مستنير لشركتك.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 04/18/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: e32018f52f3a45624fcf07ae03e44c662a594297
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916304"
---
# <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>مقارنة Microsoft Defender for Business ب Microsoft 365 Business Premium

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business [للعملاء Microsoft 365 Business Premium](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم معاينة Defender for Business باعتباره اشتراكا مستقلا، وسيتم طرحه تدريجيا للعملاء وشركاء تكنولوجيا المعلومات الذين [يسجلون هنا](https://aka.ms/mdb-preview) لطلب ذلك. تتضمن المعاينة [مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بانتظام.
>
> تتعلق بعض المعلومات الواردة في هذه المقالة بالنواتج/الخدمات التي تم إصدارها مسبقا والتي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المقدمة هنا.

تقدم Microsoft مجموعة متنوعة من الحلول والخدمات السحابية، بما في ذلك العديد من الخطط المختلفة للشركات الصغيرة والمتوسطة الحجم. على سبيل المثال، [تتضمن Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) قدرات الأمان وإدارة الأجهزة، بالإضافة إلى ميزات الإنتاجية، مثل تطبيقات Office. تم تصميم هذه المقالة للمساعدة في توضيح ميزات الأمان، مثل حماية الجهاز، المضمنة في Microsoft 365 Business Premium Microsoft Defender for Business Microsoft Defender لنقطة النهاية.

يتوفر Microsoft Defender for Business كعرض مستقل أو كجزء من Microsoft 365 Business Premium (بداية من 1 مارس 2022).

>
> **هل لديك دقيقة؟**
> يرجى أخذ <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاعنا القصير حول الأمان</a>. يسعدنا أن نستمع إليك!
>

**استخدم هذه المقالة ل**:

- [مقارنة Microsoft Defender for Business (مستقل) مع Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [مقارنة Defender for Business (مستقل) بعروض المؤسسة Microsoft Defender لنقطة النهاية](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)

**ليس عليك أن يكون لديك اشتراك Microsoft 365 لشراء Microsoft Defender for Business واستخدامها.** يتم تضمين Microsoft Defender for Business في Microsoft 365 Business Premium، وهي متوفرة كحل أمني مستقل للشركات الصغيرة والمتوسطة الحجم. إذا كان لديك بالفعل Microsoft 365 Business Basic أو قياسي، ففكر في إضافة إما الترقية إلى Microsoft 365 Business Premium أو إضافة Microsoft Defender for Business للحصول على المزيد من قدرات الحماية من التهديدات.

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>مقارنة ميزات الأمان في Microsoft Defender for Business مع Microsoft 365 Business Premium

> [!NOTE]
> تهدف هذه المقالة إلى تقديم نظرة عامة عالية المستوى حول ميزات الحماية من التهديدات المضمنة في Microsoft Defender for Business (كخطط مستقلة) Microsoft 365 Business Premium (والتي تتضمن Defender for Business). لا تهدف هذه المقالة إلى أن تكون بمثابة وصف للخدمة أو مستند عقد الترخيص. لمزيد من المعلومات، راجع [إرشادات الترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

**بداية من 1 مارس 2022، سيبدأ Defender for Business في الطرح كجزء من Microsoft 365 Business Premium. لا يزال Defender for Business كعرض مستقل قيد المعاينة.**

يقارن الجدول التالي ميزات الأمان وإمكانياته في Defender for Business (مستقل) مع Microsoft 365 Business Premium.

|الميزة/القدرة|[Microsoft Defender for Business](mdb-overview.md)<br/>(مستقل؛ قيد المعاينة حاليا)|[Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md)<br/>(بما في ذلك Defender for Business)|
|---|---|---|
|حماية البريد الإلكتروني|نعم <br/>- [مسح البريد الإلكتروني باستخدام برنامج الحماية من الفيروسات من Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md)|نعم <br/>- [Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) <br/>- [مسح البريد الإلكتروني باستخدام برنامج الحماية من الفيروسات من Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|حماية Antispam|نعم <br/>- للأجهزة|نعم <br/>- للأجهزة<br/>- لمحتوى البريد الإلكتروني Microsoft 365، مثل الرسائل والمرفقات|
|الحماية من البرامج الضارة|نعم<br/>- للأجهزة|نعم <br/>- للأجهزة<br/>- لمحتوى البريد الإلكتروني Microsoft 365، مثل الرسائل والمرفقات|
|[حماية الجيل التالي](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (الحماية من الفيروسات والحماية من البرامج الضارة)|نعم<br/>- يتم تضمين برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10 والإي وقت لاحق|نعم <br/>- يتم تضمين برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10 والإي وقت لاحق<br/>- نهج الحماية من الجيل التالي للأجهزة التي تم إلحاقها|
|[قواعد تقليل الأجزاء المعرضة للهجوم](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(قواعد ASR في Windows 10 أو الأحدث وحماية جدار الحماية)|نعم|نعم|
|[الكشف عن نقطة النهاية والاستجابة لها](../defender-endpoint/overview-endpoint-detection-response.md) <br/>(إجراءات الكشف والاستجابة اليدوية المستندة إلى السلوك)|نعم|نعم|
|[التحقيق التلقائي والاستجابة (AIR)](../defender-endpoint/automated-investigations.md)|نعم|نعم|
|[التهديدات وإدارة الثغرات الأمنية](../defender-endpoint/tvm-dashboard-insights.md)|نعم|نعم|
|الإدارة المركزية وإعداد التقارير|نعم|نعم|
|[واجهات برمجه التطبيقات](../defender-endpoint/apis-intro.md) <br/>(للتكامل مع التطبيقات المخصصة أو حلول التقارير)|نعم|نعم|

## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>مقارنة Microsoft Defender for Business بالخطط Microsoft Defender لنقطة النهاية 1 و2

يوفر Defender for Business قدرات على مستوى المؤسسة من Defender لنقطة النهاية للشركات الصغيرة والمتوسطة الحجم.

يقارن الجدول التالي ميزات الأمان وإمكانياته في Defender for Business بعروض المؤسسة، Microsoft Defender لنقطة النهاية الخطط 1 و2.

|الميزة/القدرة|[Defender for Business](mdb-overview.md)<br/>(مستقل؛ قيد المعاينة حاليا)|[Defender for Endpoint الخطة 1](../defender-endpoint/defender-endpoint-plan-1.md)<br/>(لعملاء المؤسسات) |[Defender لنقطة النهاية الخطة 2](../defender-endpoint/microsoft-defender-endpoint.md)<br/>(لعملاء المؤسسات) |
|---|---|---|---|
|[الإدارة المركزية](../defender-endpoint/manage-atp-post-migration.md) |نعم <sup>[[1](#fn1)]</sup>|نعم|نعم|
|[تكوين العميل المبسط](mdb-simplified-configuration.md)|نعم|لا|لا|
|[التهديدات وإدارة الثغرات الأمنية](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)|نعم|لا|نعم|
|[قدرات تقليل الأجزاء المعرضة للهجوم](../defender-endpoint/overview-attack-surface-reduction.md)|نعم|نعم|نعم|
|[حماية الجيل التالي](../defender-endpoint/next-generation-protection.md)|نعم|نعم|نعم|
|[الكشف عن نقطة النهاية والاستجابة لها](../defender-endpoint/overview-endpoint-detection-response.md)|نعم <sup>[[2](#fn2)]</sup>|لا|نعم|
|[التحقيق التلقائي والاستجابة (AIR)](../defender-endpoint/automated-investigations.md)|نعم <sup>[[3](#fn3)]</sup>|لا|نعم|
|[تتبع التهديدات](../defender-endpoint/advanced-hunting-overview.md) واستبقاء البيانات لمدة ستة أشهر |لا <sup>[[4](#fn4)]</sup>|لا|نعم|
|[تحليلات المخاطر](../defender-endpoint/threat-analytics.md)|نعم <sup>[[5](#fn5)]</sup>|لا|نعم|
|[دعم عبر الأنظمة الأساسية](../defender-endpoint/minimum-requirements.md) <br/>(Windows وmacOS وiOS وAndroid OS)|نعم <sup>[[6](#fn6)]</sup>|نعم|نعم|
|[خبراء المخاطر في Microsoft](../defender-endpoint/microsoft-threat-experts.md)|لا|لا|نعم|
|واجهات برمجة التطبيقات الخاصة بالشركاء|نعم|نعم|نعم|
|[تكامل Microsoft 365 Lighthouse](../../lighthouse/m365-lighthouse-overview.md) <br/>(لعرض حوادث الأمان عبر مستأجري العملاء)|نعم|لا|لا|

(<a id="fn1">1</a>) إلحاق الأجهزة وإدارتها في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) أو باستخدام إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) تتضمن قدرات الكشف عن نقاط النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في Defender for Business الكشف المستند إلى السلوك والأنواع الأربعة التالية من إجراءات الاستجابة اليدوية: 
- تشغيل مسح الحماية من الفيروسات
- عزل الجهاز
- إيقاف ملف وعزله
- إضافة مؤشر لحظر ملف أو السماح به

(<a id="fn3">3</a>) في Defender for Business، يتم تشغيل التحقيق التلقائي والاستجابة بشكل افتراضي، على نطاق المستأجر. إذا أوقفت تشغيل التحقيق التلقائي والاستجابة، فإنه يؤثر على الحماية في الوقت الحقيقي. راجع [إعدادات المراجعة للميزات المتقدمة](mdb-configure-security-settings.md#review-settings-for-advanced-features).  

(<a id="fn4">4</a>) لا توجد طريقة عرض للمخطط الزمني في Defender for Business.

(<a id="fn5">5</a>) في Defender for Business، يتم تحسين تحليلات التهديدات للشركات الصغيرة والمتوسطة الحجم.

(<a id="fn6">6</a>) أثناء برنامج المعاينة، يتم دعم Windows أجهزة العميل للإلحاق في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). يمكنك استخدام أسلوب البرنامج النصي المحلي. راجع [الأجهزة الملحقة Microsoft Defender for Business](mdb-onboard-devices.md).

## <a name="next-steps"></a>الخطوات التالية

- [راجع متطلبات Microsoft Defender for Business](mdb-requirements.md)
- [الحصول على Microsoft Defender for Business](get-defender-business.md)
- [تعرف على كيفية إعداد Microsoft Defender for Business وتكوينها](mdb-setup-configuration.md)
