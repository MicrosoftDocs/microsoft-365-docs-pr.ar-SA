---
title: إلحاق الأجهزة بدون الوصول إلى الإنترنت إلى Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: إلحاق الأجهزة دون الوصول إلى الإنترنت بحيث يمكنها إرسال بيانات جهاز الاستشعار إلى أداة استشعار Microsoft Defender لنقطة النهاية
keywords: إلحاق، خوادم، جهاز ظاهري، محلي، بوابة oms، تحليلات السجل، تحليلات سجل azure، mma
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
ms.openlocfilehash: 33b539018f479c1b023a656ab056ca892d27e526
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822170"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>إلحاق الأجهزة بدون الوصول إلى الإنترنت إلى Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

بالنسبة للأجهزة التي لا يوجد بها اتصال مباشر بالإنترنت، فإن استخدام حل الوكيل هو النهج الموصى به. بالنسبة إلى أجهزة Windows القديمة التي تم إلحاقها باستخدام الحل السابق المستند إلى MMA، يوفر استخدام حل بوابة OMS نهجا بديلا. لمزيد من المعلومات حول أساليب الإلحاق، راجع المقالات التالية:
- [الإصدارات السابقة من Windows](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [إلحاق الخوادم بخدمة Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)

> [!IMPORTANT]
> - يجب أن يكون Windows أو Windows Server في البيئات غير المتصلة قادرا على تحديث قوائم توثيق الشهادات دون اتصال عبر ملف داخلي أو خادم ويب.
> - لمزيد من المعلومات حول تحديث CTLs دون اتصال، راجع [تكوين ملف أو خادم ويب لتنزيل ملفات CTL](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files).

## <a name="devices-running-windows-10-or-later-windows-server-2012-r2-or-later-linux-and-macos"></a>الأجهزة التي تعمل Windows 10 أو أحدث، Windows Server 2012 R2 أو أحدث، Linux وmacOS

اعتمادا على نظام التشغيل، يمكن تكوين الوكيل الذي سيتم استخدامه Microsoft Defender لنقطة النهاية تلقائيا، عادة من خلال استخدام الكشف التلقائي أو ملف تكوين تلقائي، أو خاص بشكل ثابت بخدمات Defender لنقطة النهاية التي تعمل على الجهاز.

- بالنسبة لأجهزة Windows، يرجى الرجوع إلى [إعدادات تكوين وكيل الجهاز والاتصال بالإنترنت](/microsoft-365/security/defender-endpoint/configure-proxy-internet)
- بالنسبة لأجهزة Linux، يرجى الرجوع إلى [تكوين Microsoft Defender لنقطة النهاية على Linux لاكتشاف الوكيل الثابت](/microsoft-365/security/defender-endpoint/linux-static-proxy-configuration)
- بالنسبة لأجهزة macOS، يرجى الرجوع [إلى Microsoft Defender لنقطة النهاية على Mac](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac#network-connections)

## <a name="windows-devices-running-the-previous-mma-based-solution"></a>أجهزة Windows التي تقوم بتشغيل الحل السابق المستند إلى MMA

> [!NOTE]
> - لا يمكن استخدام خادم بوابة OMS كوكيل لأجهزة Windows أو Windows Server غير المتصلة عند تكوينه عبر سجل "TelemetryProxyServer" أو عنصر نهج المجموعة.
> - بالنسبة إلى Windows أو Windows Server - بينما يمكنك استخدام TelemetryProxyServer، فإنه يجب أن يشير إلى جهاز وكيل قياسي أو جهاز.

- إعداد Azure Log Analytics (المعروف سابقا باسم بوابة OMS) للعمل كوكيل أو مركز:
  - [عامل Azure Log Analytics](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [تثبيت نقطة عامل مراقبة Microsoft (MMA) وتكوينها](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) إلى مفتاح مساحة عمل Defender لنقطة النهاية & معرف

[الإصدارات السابقة من Windows](onboard-downlevel.md)

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender للسحابة

- راجع قسم المتطلبات الأساسية في [حماية نقاط النهاية باستخدام حل EDR المتكامل ل Defender for Cloud: Microsoft Defender لنقطة النهاية](/azure/defender-for-cloud/integration-defender-for-endpoint?tabs=windows#prerequisites)
