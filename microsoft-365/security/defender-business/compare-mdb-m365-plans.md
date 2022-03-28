---
title: مقارنة ميزات الأمان في Microsoft 365 للشركات الصغيرة والمتوسطة الحجم
description: فهم الاختلافات بين Defender for Business و Defender for Endpoint. يمكن أن تساعدك معرفة ما هو مضمن في كل خطة على اتخاذ قرار مخبر للشركة.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: 793c078621424bca89ccc4c6d88c79054ab059cd
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575178"
---
# <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>مقارنة Microsoft Defender for Business Microsoft 365 Business Premium

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يكون Defender for Business باشتراك مستقل في وضع المعاينة، وسوف يتم طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا لطلبه.[](https://aka.ms/mdb-preview) تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

تقدم Microsoft مجموعة واسعة من الحلول والخدمات السحابية، بما في ذلك العديد من الخطط المختلفة للشركات الصغيرة والمتوسطة الحجم. على سبيل [المثال Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) تتضمن هذه Microsoft 365 Business Premium الأمان وإمكانيات إدارة الأجهزة، إلى جانب ميزات الإنتاجية، مثل Office التطبيق. تم تصميم هذه المقالة للمساعدة في توضيح ميزات الأمان، مثل حماية الجهاز، المضمنة في Microsoft 365 Business Premium و Microsoft Defender for Business و Microsoft Defender ل Endpoint.

يتوفر Microsoft Defender for Business كعرض مستقل أو كجزء من Microsoft 365 Business Premium (بداية من 1 مارس 2022).

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

**استخدم هذه المقالة ل**:

- [مقارنة Microsoft Defender for Business (مستقل) Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [مقارنة Defender for Business (مستقل) مع عروض مؤسسة Microsoft Defender for Endpoint](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)

**لست بحاجة إلى اشتراك Microsoft 365 لشراء Microsoft Defender for Business واستخدامه.** يتم تضمين Microsoft Defender for Business في Microsoft 365 Business Premium، وهو متوفر كحل أمان مستقل للشركات الصغيرة والمتوسطة الحجم. إذا كان لديك Microsoft 365 Business Basic أو قياسي، فنظر في إضافة إما Microsoft 365 Business Premium أو إضافة Microsoft Defender for Business للحصول على المزيد من قدرات الحماية من المخاطر. 

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>مقارنة ميزات الأمان في Microsoft Defender for Business Microsoft 365 Business Premium

> [!NOTE]
> تهدف هذه المقالة إلى توفير نظرة عامة عالية المستوى حول ميزات الحماية من المخاطر المضمنة في Microsoft Defender for Business (كخطة مستقلة) Microsoft 365 Business Premium (التي تتضمن Defender for Business). لا تهدف هذه المقالة إلى العمل كمستند عقد ترخيص أو وصف الخدمة. لمزيد من المعلومات، [راجع Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

**بدءا من 1 مارس 2022، سيبدأ طرح Defender for Business كجزء من Microsoft 365 Business Premium. لا يزال Defender for Business كعرض مستقل في وضع المعاينة.**

يقارن الجدول التالي بين ميزات الأمان وإمكانياته في Defender for Business (مستقل) Microsoft 365 Business Premium. 

 <br/><br/>

| الميزة/الإمكانية | [Microsoft Defender for Business](mdb-overview.md)<br/>(مستقل؛ حاليا في وضع المعاينة) | [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md)<br/>(بما في ذلك Defender for Business) |
|:---|:---|:---|
| حماية البريد الإلكتروني | نعم <br/>- [مسح البريد الإلكتروني باستخدام برنامج الحماية من الفيروسات من Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) | نعم <br/>- [Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) <br/>- [مسح البريد الإلكتروني باستخدام برنامج الحماية من الفيروسات من Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| الحماية منspam | نعم <br/>- للأجهزة | نعم <br/>- للأجهزة<br/>- للحصول Microsoft 365 البريد الإلكتروني، مثل الرسائل والمرفقات |
| الحماية من البرامج الضارة | نعم<br/>- للأجهزة | نعم <br/>- للأجهزة<br/>- للحصول Microsoft 365 البريد الإلكتروني، مثل الرسائل والمرفقات |
| [حماية الجيل التالي](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (الحماية من الفيروسات والحماية من البرامج الضارة) | نعم<br/>- برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10 واللاحقة  | نعم <br/>- برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10 واللاحقة<br/>- سياسات حماية الجيل التالي للأجهزة المجهزة |
| [الحد من سطح الهجوم](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(قواعد ASR في Windows 10 أو لاحقا وحماية جدار الحماية) | نعم  | نعم  |
| [الكشف عن نقطة النهاية والاستجابة لها](../defender-endpoint/overview-endpoint-detection-response.md) <br/>(إجراءات الكشف والاستجابة اليدوية المستندة إلى السلوك) | نعم | نعم |
| [إجراء عمليات التحقيق والاستجابة التلقائية](../defender-endpoint/automated-investigations.md) | نعم | نعم |
| [التهديدات & إدارة الثغرات الأمنية](../defender-endpoint/tvm-dashboard-insights.md) | نعم | نعم |
| الإدارة المركزية وإعداد التقارير  | نعم  | نعم  |
| [واجهات برمجة التطبيقات](../defender-endpoint/apis-intro.md) <br/>(للتكامل مع التطبيقات المخصصة أو حلول التقارير)  | نعم | نعم |


## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>مقارنة Microsoft Defender for Business ب Microsoft Defender لخطط نقطة النهاية 1 و2

يجمع Defender for Business قدرات على مستوى المؤسسة من Defender لنقطة النهاية للشركات الصغيرة والمتوسطة الحجم. 

يقارن الجدول التالي بين ميزات الأمان وإمكانياته في Defender for Business و Microsoft Defender لخطتي نقطة النهاية 1 و2. <br/><br/>

| الميزة/الإمكانية | [Defender for Business](mdb-overview.md) (معاينة) | [Defender for Endpoint Plan 1](../defender-endpoint/defender-endpoint-plan-1.md) | [Defender for Endpoint Plan 2](../defender-endpoint/microsoft-defender-endpoint.md) |
|:---|:---|:---|
| [الإدارة المركزية](../defender-endpoint/manage-atp-post-migration.md) <sup>[[1](#fn1)]</sup> | نعم | نعم | نعم |
| [تكوين عميل مبسط](mdb-simplified-configuration.md) | نعم | لا | لا |
| [التهديدات & إدارة الثغرات الأمنية](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) | نعم | لا | نعم |
| [إمكانات الحد من سطح الهجوم](../defender-endpoint/overview-attack-surface-reduction.md) | نعم | نعم | نعم |
| [حماية الجيل التالي](../defender-endpoint/next-generation-protection.md) | نعم | نعم | نعم |
| [الكشف عن نقطة النهاية والاستجابة لها](../defender-endpoint/overview-endpoint-detection-response.md) | نعم <sup>[[2](#fn2)]</sup> | لا | نعم |
| [إجراء عمليات التحقيق والاستجابة التلقائية](../defender-endpoint/automated-investigations.md) | نعم <sup>[[2](#fn2)]</sup> | لا | نعم |
| [البحث عن تهديدات](../defender-endpoint/advanced-hunting-overview.md) واستبقاء البيانات لمدة ستة أشهر | لا | لا | نعم |
| [تحليل المخاطر](../defender-endpoint/threat-analytics.md) | نعم <sup>[[2](#fn2)]</sup> | لا | نعم |
| [دعم عبر الأنظمة الأساسية](../defender-endpoint/minimum-requirements.md) <br/>(Windows و macOS و iOS و Android OS) | نعم <sup>[[3](#fn3)]</sup> | نعم | نعم |
| [خبراء المخاطر في Microsoft](../defender-endpoint/microsoft-threat-experts.md) | لا | لا | نعم |
| واجهات برمجة التطبيقات الشريكة | نعم | نعم | نعم |
| [Microsoft 365 المنارة](../../lighthouse/m365-lighthouse-overview.md) <br/>(لعرض أحداث الأمان عبر مستأجري العملاء) | نعم | لا | لا |

(<a id="fn1">1</a>) اداخل الأجهزة وإدارتها في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) أو باستخدام أداة أخرى، مثل إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) تم تحسين هذه الإمكانات للشركات الصغيرة والمتوسطة الحجم.

(<a id="fn3">3</a>) أثناء برنامج المعاينة، Windows الأجهزة العميلة المعتمدة في Microsoft 365 Defender المدخل ([https://security.microsoft.com](https://security.microsoft.com)).

## <a name="next-steps"></a>الخطوات التالية

- [الاطلاع على متطلبات Microsoft Defender for Business](mdb-requirements.md)

- [الحصول على Microsoft Defender for Business](get-defender-business.md)

- [تعرف على كيفية إعداد Microsoft Defender for Business وتكوينه](mdb-setup-configuration.md) 
