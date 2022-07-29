---
title: مقارنة ميزات الأمان في خطط Microsoft 365 للشركات الصغيرة والمتوسطة الحجم
description: كيف يقارن Defender for Business ب Defender لنقطة النهاية Microsoft 365 Business Premium؟ اطلع على ما هو مضمن في كل خطة حتى تتمكن من اتخاذ قرار أكثر استنارة لشركتك.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: 87abc4dd3369a61ce5a50697035b3ce566a97746
ms.sourcegitcommit: 61df6377a6185a8b55e668cfb81adbd8462a9cce
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/29/2022
ms.locfileid: "67071558"
---
# <a name="compare-security-features-in-microsoft-365-plans-for-small-and-medium-sized-businesses"></a>مقارنة ميزات الأمان في خطط Microsoft 365 للشركات الصغيرة والمتوسطة الحجم

تقدم Microsoft مجموعة متنوعة من الحلول والخدمات السحابية، بما في ذلك خطط للشركات الصغيرة والمتوسطة الحجم. على سبيل المثال، [تتضمن Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) إمكانات الأمان وإدارة الأجهزة، بالإضافة إلى ميزات الإنتاجية مثل تطبيقات Office. تصف هذه المقالة ميزات الأمان في Microsoft 365 Business Premium [Microsoft Defender for Business Microsoft Defender لنقطة النهاية.](../defender-endpoint/microsoft-defender-endpoint.md)


**استخدم هذه المقالة ل**:

- [مقارنة Microsoft Defender for Business ب Microsoft 365 Business Premium](#compare-microsoft-defender-for-business-to-microsoft-365-business-premium).
- [قارن Defender for Business (مستقل) بعروض مؤسسة Defender for Endpoint](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> [!TIP]
> يتوفر Defender for Business كحل أمني مستقل للشركات الصغيرة والمتوسطة الحجم. تم تضمين Defender for Business الآن في Microsoft 365 Business Premium. إذا كان لديك بالفعل Microsoft 365 Business Basic أو قياسي، ففكر في الترقية إلى Microsoft 365 Business Premium أو إضافة Defender for Business إلى اشتراكك الحالي للحصول على المزيد من قدرات الحماية من التهديدات لأجهزتك.

## <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>مقارنة Microsoft Defender for Business ب Microsoft 365 Business Premium

> [!NOTE]
> توفر هذه المقالة نظرة عامة عالية المستوى حول الميزات والقدرات المضمنة في Microsoft Defender for Business (كخطط مستقلة) Microsoft 365 Business Premium (والتي تتضمن Defender for Business). ليس المقصود منه أن يكون وصفا للخدمة أو مستند عقد ترخيص. لمزيد من المعلومات التفصيلية، راجع [إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

| Microsoft Defender for Business (مستقل) | Microsoft 365 Business Premium |
|:---|:---|
| تتضمن قدرات الحماية من الفيروسات والبرامج الضارة والحماية من برامج الفدية الضارة للأجهزة ما يلي: <ul><li>[حماية الجيل التالي](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) (الحماية من الفيروسات/الحماية من البرامج الضارة على الأجهزة جنبا إلى جنب مع حماية السحابة)</li><li>[تقليل الأجزاء المعرضة للهجوم](../defender-endpoint/overview-attack-surface-reduction.md) (حماية الشبكة وجدار الحماية وقواعد تقليل الأجزاء <sup>[المعرضة](#fna) للهجوم) [a]</sup></li><li>[الكشف عن نقطة النهاية والاستجابة](../defender-endpoint/overview-endpoint-detection-response.md) لها (إجراءات الكشف والاستجابة اليدوية المستندة إلى السلوك)</li><li>[التحقيق التلقائي والاستجابة](../defender/m365d-autoir.md) (مع الإصلاح الذاتي للتهديدات المكتشفة)</li><li>[إدارة المخاطر والثغرات الأمنية](mdb-view-tvm-dashboard.md) (عرض الأجهزة والتوصيات المكشوفة)</li><li>[دعم عبر الأنظمة الأساسية للأجهزة](mdb-onboard-devices.md) (Windows وMac وiOS وAndroid) <sup>[[b](#fnb)]</sup></li><li>[الإدارة المركزية وإعداد التقارير](mdb-get-started.md) (مدخل Microsoft 365 Defender)</li><li>[واجهات برمجة التطبيقات للتكامل](../defender-endpoint/management-apis.md) (لشركاء Microsoft أو الأدوات والتطبيقات المخصصة)</li></ul><br/><br/><br/><br/><br/><br/><br/> | تتضمن قدرات الإنتاجية والأمان ما يلي:<ul><li>[Microsoft 365 Business Standard](../../admin/admin-overview/what-is-microsoft-365-for-business.md) (تطبيقات وخدمات Office وMicrosoft Teams)</li><li>[تنشيط الكمبيوتر المشترك](/deployoffice/overview-shared-computer-activation) (لنشر Microsoft 365 Apps)</li><li>[Windows 10/11 Business](../../business-premium/m365bp-upgrade-windows-10-pro.md) (الترقية من الإصدارات السابقة من Windows Pro)</li><li>[Windows Autopilot](/mem/autopilot/windows-autopilot) (لإعداد أجهزة Windows وتكوينها)</li><li>[Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) (مكافحة الفيش، ومكافحة الspam، ومكافحة البرامج الضارة، والانتحال الذكي للبريد الإلكتروني)</li><li>[Defender for Business](mdb-overview.md) (كل شيء مدرج في العمود "Defender for Business (مستقل)" </li><li>[Microsoft Defender لـ Office 365 الخطة 1](../office-365-security/overview.md) (مكافحة الكتابة المتقدمة، والكشف في الوقت الحقيقي، والمرفقات الآمنة، والارتباطات الآمنة)</li><li>[التوسيع التلقائي لأرشفة](../../compliance/autoexpanding-archiving.md) (للبريد الإلكتروني)</li><li>[الخطة 1 من Azure Active Directory Premium](/azure/active-directory/fundamentals/active-directory-whatis) (إدارة الهوية)</li><li>[Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (إلحاق الجهاز وإدارته)</li><li>[Azure حماية البيانات الخطة 1 المتميزة](/azure/information-protection/what-is-information-protection) (حماية المعلومات الحساسة)</li><li>[Azure Virtual Desktop](/azure/virtual-desktop/overview) (الأجهزة الظاهرية الآمنة المدارة مركزيا في السحابة)</li></ul> |

(<a id="fna">أ</a>) Microsoft Intune مطلوب لتعديل قواعد تقليل الأجزاء المعرضة للهجوم أو تخصيصها. يتم تضمين Intune في Microsoft 365 Business Premium.

(<a id="fnb">ب</a>) Microsoft Intune مطلوب لإلحاق أجهزة iOS وAndroid. راجع [الأجهزة الملحقة Microsoft Defender for Business](mdb-onboard-devices.md).

## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>مقارنة Microsoft Defender for Business بالخطط Microsoft Defender لنقطة النهاية 1 و2

يوفر Defender for Business قدرات على مستوى المؤسسة من Defender لنقطة النهاية للشركات الصغيرة والمتوسطة الحجم. يقارن الجدول التالي ميزات الأمان وإمكانياته في Defender for Business بعروض المؤسسة، Microsoft Defender لنقطة النهاية الخطط 1 و2.

|الميزة/القدرة|[Defender for Business](mdb-overview.md)<br/>(مستقل)|[Defender for Endpoint الخطة 1](../defender-endpoint/defender-endpoint-plan-1.md)<br/>(لعملاء المؤسسات) |[Defender لنقطة النهاية الخطة 2](../defender-endpoint/microsoft-defender-endpoint.md)<br/>(لعملاء المؤسسات) |
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
|[دعم عبر الأنظمة الأساسية](../defender-endpoint/minimum-requirements.md) <br/>(Windows وMac وiOS وAndroid OS)|نعم <sup>[[6](#fn6)]</sup>|نعم|نعم|
|[خبراء المخاطر في Microsoft](../defender-endpoint/microsoft-threat-experts.md)|لا|لا|نعم|
|واجهات برمجة التطبيقات الخاصة بالشركاء|نعم|نعم|نعم|
|[تكامل Microsoft 365 Lighthouse](../../lighthouse/m365-lighthouse-overview.md) <br/>(لعرض حوادث الأمان عبر مستأجري العملاء)|نعم |نعم <sup>[[7](#fn7)]</sup>|نعم <sup>[[7](#fn7)]</sup>|

(<a id="fn1">1</a>) إلحاق الأجهزة وإدارتها في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) أو باستخدام Microsoft Intune، تتم إدارتها في مركز إدارة Microsoft إدارة نقاط النهاية ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) تتضمن قدرات الكشف عن نقاط النهاية والاستجابة لها (EDR) في Defender for Business الكشف المستند إلى السلوك وإجراءات الاستجابة اليدوية التالية: 
- تشغيل مسح الحماية من الفيروسات
- عزل الجهاز
- إيقاف ملف وعزله
- إضافة مؤشر لحظر ملف أو السماح به

(<a id="fn3">3</a>) في Defender for Business، يتم تشغيل التحقيق التلقائي والاستجابة بشكل افتراضي، على نطاق المستأجر. إذا أوقفت تشغيل التحقيق التلقائي والاستجابة، فإن ذلك يؤثر على الحماية في الوقت الحقيقي. راجع [إعدادات المراجعة للميزات المتقدمة](mdb-configure-security-settings.md#review-settings-for-advanced-features).  

(<a id="fn4">4</a>) لا توجد طريقة عرض للمخطط الزمني في Defender for Business.

(<a id="fn5">5</a>) في Defender for Business، يتم تحسين تحليلات التهديدات للشركات الصغيرة والمتوسطة الحجم.

(<a id="fn6">6</a>) راجع [الأجهزة الملحقة Microsoft Defender for Business](mdb-onboard-devices.md).

(<a id="fn7">7</a>) القدرة على عرض الحوادث عبر المستأجرين باستخدام Defender لنقطة النهاية جديدة!

راجع أيضا [مقارنة خطط أمان نقطة نهاية Microsoft](../defender-endpoint/defender-endpoint-plan-1-2.md).

## <a name="next-steps"></a>الخطوات التالية

- [راجع متطلبات Microsoft Defender for Business](mdb-requirements.md)
- [الحصول على Microsoft Defender for Business](get-defender-business.md)
- [تعرف على كيفية إعداد Microsoft Defender for Business وتكوينها](mdb-setup-configuration.md)
