---
title: أدوات وأساليب الإلحاق للأجهزة Windows
description: إلحاق أجهزة Windows بحيث يمكنها إرسال بيانات المستشعر إلى أداة استشعار Microsoft Defender لنقطة النهاية
keywords: إلحاق أجهزة Windows، ونهج المجموعة، ومدير تكوين نقطة النهاية، وإدارة الأجهزة المحمولة، والبرامج النصية المحلية، وgp، وsccm، وmdm، وintune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: fbc5a0981a6318d767252e968e45874d889aee85
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949090"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>أدوات وأساليب الإلحاق للأجهزة Windows في Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [منع فقدان بيانات نقطة النهاية (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [إدارة المخاطر الداخلية](/microsoft-365/compliance/insider-risk-management)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يجب تكوين الأجهزة في مؤسستك بحيث يمكن لخدمة Defender for Endpoint الحصول على بيانات أداة الاستشعار منها. هناك العديد من الأساليب وأدوات النشر التي يمكنك استخدامها لتكوين الأجهزة في مؤسستك.

بشكل عام، ستحدد الجهاز Windows الذي تقوم بإلحاقه، ثم تتبع الأداة المقابلة المناسبة للجهاز أو البيئة الخاصة بك.

:::image type="content" source="images/onboarding-config-tools.png" alt-text="أدوات وأساليب الإلحاق" lightbox="images/onboarding-config-tools.png":::

## <a name="endpoint-onboarding-tools"></a>أدوات إلحاق نقطة النهاية

استنادا إلى نقطة النهاية Windows التي تريد إلحاقها، استخدم الأداة أو الأسلوب المطابق الموضح في الجدول التالي.

جهاز Windows | أداة أو أسلوب الإلحاق
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 و2019 و2022</li> <li>Windows Server 2012 R2 و2016<sup>[[1](#fn1)]<sup></li></ul>  |   [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md)<br>   [نهج المجموعة](configure-endpoints-gp.md)<br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [إدارة نقاط النهاية من Microsoft/ إدارة الجهاز الجوال (Intune)](configure-endpoints-mdm.md)<br>    [البرامج النصية ل VDI](configure-endpoints-vdi.md) <br><br> **ملاحظة**: البرنامج النصي المحلي مناسب لإثبات المفهوم ولكن لا ينبغي استخدامه لتوزيع الإنتاج. لنشر الإنتاج، نوصي باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو Intune.
|<ul><li> Windows Server 2008 R2 SP1 </li></ul>| [عامل مراقبة Microsoft (MMA)](onboard-downlevel.md) <br>[إلحاق الإصدارات السابقة من Windows](onboard-downlevel.md) أو [Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) <br><br> **ملاحظة**: عامل مراقبة Microsoft هو الآن عامل Azure Log Analytics. لمعرفة المزيد، راجع [نظرة عامة على عامل Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 SP1 </li> <li>  Windows 7 SP1 Pro </li> <li>  Windows 8.1 Pro </li> <li> Windows 8.1 Enterprise</li></ul>  | [عامل مراقبة Microsoft (MMA)](onboard-downlevel.md) <br><br> **ملاحظة**: عامل مراقبة Microsoft هو الآن عامل Azure Log Analytics. لمعرفة المزيد، راجع [نظرة عامة على عامل Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) يجب إلحاق Windows Server 2016 وخادم Windows 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

>[!IMPORTANT]
>لكي تكون مؤهلا لشراء Microsoft Defender لنقطة النهاية Server SKU، يجب أن تكون قد اشتريت بالفعل ما لا يقل عن أي مما يلي، Windows E5/A5 أو Microsoft 365 E5/A5 أو تراخيص اشتراك الأمان في Microsoft 365 E5.  لمزيد من المعلومات حول الترخيص، راجع [شروط المنتج](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

الموضوع|الوصف
:---|:---
[إلحاق الأجهزة باستخدام نهج المجموعة](configure-endpoints-gp.md)|استخدم نهج المجموعة لنشر حزمة التكوين على الأجهزة.
[إلحاق الأجهزة باستخدام Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|يمكنك استخدام الإصدار 1606 من إدارة نقاط النهاية من Microsoft (الفرع الحالي) أو الإصدار 1602 من إدارة نقاط النهاية من Microsoft (الفرع الحالي) أو إصدار سابق لنشر حزمة التكوين على الأجهزة.
[إلحاق الأجهزة باستخدام أدوات إدارة الجهاز الأجهزة المحمولة](configure-endpoints-mdm.md)|استخدم أدوات إدارة الجهاز الجوال أو Microsoft Intune لنشر حزمة التكوين على الجهاز.
[إلحاق الأجهزة باستخدام برنامج نصي محلي](configure-endpoints-script.md)|تعرف على كيفية استخدام البرنامج النصي المحلي لنشر حزمة التكوين على نقاط النهاية.
[أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)|تعرف على كيفية استخدام حزمة التكوين لتكوين أجهزة VDI.

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

بعد إلحاق الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أن الجهاز تم إلحاقه بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](run-detection-test.md).
