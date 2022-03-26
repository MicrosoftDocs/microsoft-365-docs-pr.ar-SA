---
title: الأجهزة المجهزة بدون اتصال بالإنترنت إلى Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: الأجهزة المجهزة بدون اتصال بالإنترنت بحيث يمكنها إرسال بيانات المستشعر إلى مستشعر نقطة النهاية ل Microsoft Defender
keywords: onboard, servers, vm, on-premises, oms gateway, log analytics, azure log analytics, mma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 83f0f53e2d2376975f853d826531e749732416b7
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754325"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>الأجهزة المجهزة بدون اتصال بالإنترنت إلى Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


للأجهزة المجهزة بدون اتصال بالإنترنت، ستحتاج إلى اتخاذ الخطوات العامة التالية:

> [!IMPORTANT] 
> تنطبق الخطوات التالية فقط على الأجهزة التي تعمل بالإصدارات السابقة من Windows باستخدام الحل المستند إلى MMA. لمزيد من المعلومات، راجع [Windows إلى خدمة Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

> [!NOTE]
> - لا يمكن استخدام خادم بوابة OMS كوكيل للأجهزة Windows أو Windows غير المتصلة عند تكوينها عبر سجل 'TelemetryProxyServer' أو GPO.
> - بالنسبة Windows أو Windows Server - بينما يمكنك استخدام TelemetryProxyServer، يجب أن يشير إلى جهاز وكيل قياسي أو جهاز.
> - بالإضافة إلى Windows أو Windows أن يتمكن الخادم في البيئات غير المتصلة من تحديث قوائم الثقة بالشهادات دون اتصال عبر ملف داخلي أو خادم ويب.
> - لمزيد من المعلومات حول تحديث عناوين CTLs دون اتصال، راجع تكوين ملف أو خادم [ويب لتنزيل ملفات CTL](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files).

للحصول على مزيد من المعلومات حول أساليب الboard، راجع المقالات التالية:
- [الإصدارات السابقة من Windows](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [خوادم على لوحة لخدمة Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)
- [تكوين إعدادات اتصال الإنترنت ووكيل الجهاز](/microsoft-365/security/defender-endpoint/configure-proxy-internet#configure-the-proxy-server-manually-using-a-registry-based-static-proxy)

## <a name="devices-running-the-previous-mma-based-solution"></a>الأجهزة التي تقوم بتشغيل الحل السابق المستند إلى MMA

- إعداد Azure Log Analytics (المعروف سابقا باسم بوابة OMS) للعمل كوكيل أو مركز:
  - [وكيل Azure Log Analytics](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [تثبيت عامل مراقبة Microsoft (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) وتكوينه يشير إلى مفتاح Defender for Endpoint Workspace & ID

[الإصدارات السابقة من Windows](onboard-downlevel.md)

- الأجهزة غير المتصلة في شبكة Azure Log Analytics نفسها
  - تكوين MMA لتشير إلى:
    - Azure Log Analytics IP كوكيل
    - Defender لمفتاح مساحة عمل نقطة النهاية & ID

### <a name="azure-virtual-machines"></a>أجهزة Azure الظاهرية

- بالنسبة للأجهزة التي تقوم بتشغيل الحل السابق المستند إلى MMA، قم بإعداد Azure Log Analytics Gateway (المعروف سابقا ببوابة OMS) للعمل كوكيل أو مركز:
    - [بوابة تحليلات سجل Azure](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
    - [تثبيت عامل مراقبة Microsoft (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) وتكوينه يشير إلى مفتاح Defender for Endpoint Workspace & ID
- أجهزة VMs Azure غير المتصلة في نفس شبكة بوابة OMS
    - تكوين Azure Log Analytics IP كوكيل
    - مفتاح مساحة عمل Azure Log Analytics & ID
- Microsoft Defender for Cloud
    - [مساحة عمل تحليلات \> سجل نهج الأمان](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)
    - [الكشف عن المخاطر \> السماح ل Defender لنقطة النهاية بالوصول إلى بياناتي](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)

    لمزيد من المعلومات، راجع [استخدام سياسات الأمان](/azure/security-center/tutorial-security-policy).
