---
title: إدارة برنامج الحماية من الفيروسات من Microsoft Defender في شركتك
description: تعرف على كيفية استخدام نهج المجموعة ومدير التكوين و PowerShell و WMI و Intune و سطر الأوامر لإدارة Microsoft Defender AV
keywords: نهج المجموعة، gpo، إدارة المؤتمرات، sccm، scep، powershell، wmi، intune، defender، الحماية من الفيروسات، الحماية من البرامج الضارة، الأمان، الحماية
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 4c73936bd32381988a03ad527a83847497eab71d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63574252"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>إدارة برنامج الحماية من الفيروسات من Microsoft Defender في شركتك

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

يمكنك إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام الأدوات التالية:

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (الآن جزء من إدارة نقاط النهاية من Microsoft)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (الآن جزء من إدارة نقاط النهاية من Microsoft)
- [نهج المجموعة](./use-group-policy-microsoft-defender-antivirus.md)
- [PowerShell cmdlets](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Windows إدارة الأجهزة (WMI)](./use-wmi-microsoft-defender-antivirus.md)
- الأداة [المساعدة لخط](./command-line-arguments-microsoft-defender-antivirus.md) أوامر الحماية من البرامج الضارة من Microsoft (يشار إليها باسم الأداة *mpcmdrun.exe* البرامج الضارة

توفر المقالات التالية المزيد من المعلومات والربط والموارد لاستخدام هذه الأدوات لإدارة برنامج الحماية من الفيروسات من Microsoft Defender.

|مقالة|الوصف|
|:---|:---|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام Microsoft Intune Microsoft Endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|معلومات حول استخدام Intune و"إدارة التكوين" لنشر البيانات وإدارتها برنامج الحماية من الفيروسات من Microsoft Defender|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام إعدادات نهج المجموعة](use-group-policy-microsoft-defender-antivirus.md)|قائمة بكل إعدادات نهج المجموعة الموجودة في قوالب ADMX|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md)|إرشادات حول استخدام أوامر powerShell cmdlets لإدارة برنامج الحماية من الفيروسات من Microsoft Defender، بالإضافة إلى ارتباطات إلى الوثائق لكل أوامر cmdlets والمعلمات المسموح بها|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام Windows الإدارة (WMI)](use-wmi-microsoft-defender-antivirus.md)|إرشادات حول استخدام WMI لإدارة برنامج الحماية من الفيروسات من Microsoft Defender، بالإضافة إلى ارتباطات إلى وثائق واجهات برمجة التطبيقات WMIv2 (بما في ذلك كل الفئات والأساليب والخصائص)|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام MpCmdRun.exe سطر الأوامر](command-line-arguments-microsoft-defender-antivirus.md)|إرشادات حول استخدام أداة سطر الأوامر المخصصة لإدارة برنامج الحماية من الفيروسات من Microsoft Defender|
