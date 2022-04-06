---
title: أدوات وأساليب التكهين للأجهزة Windows الأجهزة
description: ألواح Windows الأجهزة بحيث يمكنها إرسال بيانات المستشعر إلى Microsoft Defender لنقطة النهاية المستشعر
keywords: أجهزة Windows، نهج المجموعة، إدارة تكوين نقطة النهاية، إدارة الأجهزة المحمولة، البرنامج النصي المحلي، gp، sccm، mdm، intune
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
ms.openlocfilehash: 035a47f904029e839e3fe19393e4b152515aa808
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471880"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>أدوات وأساليب التكوين للأجهزة Windows في Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Microsoft 365 إدارة مخاطر Insider](/microsoft-365/compliance/insider-risk-management)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يجب تكوين الأجهزة في مؤسستك بحيث تتمكن خدمة Defender for Endpoint من الحصول على بيانات المستشعر منها. هناك أساليب وأدوات نشر متنوعة يمكنك استخدامها لتكوين الأجهزة في مؤسستك.

بشكل عام، ستتعرف على Windows الذي تقوم بتركه، ثم تتبع الأداة المطابقة المناسبة للجهاز أو البيئة.

:::image type="content" source="images/onboarding-config-tools.png" alt-text="أدوات والأساليب الخاصة باللوح" lightbox="images/onboarding-config-tools.png":::

## <a name="endpoint-onboarding-tools"></a>أدوات تعيين نقطة النهاية

استنادا إلى Windows النهاية التي تريد استخدامها، استخدم الأداة أو الأسلوب المقابل الموضح في الجدول التالي.

Windows جديد | أداة أو أسلوب الboarding
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 و2019 و2022</li> <li>Windows Server 2012 R2 و2016<sup>[[1](#fn1)]<sup></li></ul>  |   [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md)<br>   [نهج المجموعة](configure-endpoints-gp.md)<br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [إدارة نقاط النهاية من Microsoft/ Mobile إدارة الجهاز (Intune)](configure-endpoints-mdm.md)<br>    [برامج VDI النصية](configure-endpoints-vdi.md) <br><br> **ملاحظة**: البرنامج النصي المحلي مناسب لإثبات المبدأ ولكن لا يجب استخدامه لنشر الإنتاج. لنشر الإنتاج، نوصي باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو Intune.
|<ul><li> Windows Server 2008 R2 SP1 </li></ul>| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br>[الإصدارات السابقة من](onboard-downlevel.md) Windows [أو Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) <br><br> **ملاحظة**: أصبح Microsoft Monitoring Agent الآن عامل Azure Log Analytics. لمعرفة المزيد، راجع [نظرة عامة حول عامل Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 SP1 </li> <li>  Windows 7 SP1 Pro </li> <li>  Windows 8.1 Pro </li> <li> Windows 8.1 Enterprise</li></ul>  | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **ملاحظة**: أصبح Microsoft Monitoring Agent الآن عامل Azure Log Analytics. لمعرفة المزيد، راجع [نظرة عامة حول عامل Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) Windows Server 2016 و Windows Server 2012 R2 إلى ال متنها باستخدام الإرشادات الموجودة في [خوادم Windows على اللوحة](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

>[!IMPORTANT]
>لكي تكون مؤهلا لشراء Microsoft Defender لنقطة النهاية Server SKU، يجب أن تكون قد اشتريت بالفعل حدا أدنى مدمجا لأي من تراخيص الاشتراك التالية أو Windows E5/A5 أو Microsoft 365 E5/A5 أو الأمان في Microsoft 365 E5 اشتراك.  لمزيد من المعلومات حول الترخيص، راجع [شروط المنتج](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

الموضوع|الوصف
:---|:---
[الأجهزة المجهزة باستخدام نهج المجموعة](configure-endpoints-gp.md)|استخدم نهج المجموعة لنشر حزمة التكوين على الأجهزة.
[الأجهزة المجهزة باستخدام Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|يمكنك استخدام إدارة نقاط النهاية من Microsoft (الفرع الحالي) الإصدار 1606 أو إدارة نقاط النهاية من Microsoft (الفرع الحالي) الإصدار 1602 أو إصدار سابق لنشر حزمة التكوين على الأجهزة.
[الأجهزة المجهزة باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول](configure-endpoints-mdm.md)|استخدم أدوات إدارة الجهاز أو Microsoft Intune المحمول لنشر حزمة التكوين على الجهاز.
[الأجهزة المجهزة باستخدام برنامج نصي محلي](configure-endpoints-script.md)|تعرف على كيفية استخدام البرنامج النصي المحلي لنشر حزمة التكوين على نقاط النهاية.
[أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)|تعرف على كيفية استخدام حزمة التكوين لتكوين أجهزة VDI.

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

بعد تشغيل الجهاز، يمكنك أن تختار تشغيل اختبار الكشف للتحقق من أن الجهاز مواد بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية جديد](run-detection-test.md).
