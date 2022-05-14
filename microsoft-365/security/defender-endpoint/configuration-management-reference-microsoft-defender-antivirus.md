---
title: إدارة برنامج الحماية من الفيروسات من Microsoft Defender في شركتك
description: تعرف على كيفية استخدام نهج المجموعة Configuration Manager وPowerShell وWMI وIntune وسطر الأوامر لإدارة Microsoft Defender AV
keywords: نهج المجموعة، gpo، مدير التكوين، sccm، scep، powershell، wmi، intune، defender، antivirus، antimalware، الأمان، الحماية
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
ms.openlocfilehash: 760c3b7ca646b02813b5d14086f5d94fc9aec72c
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418643"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>إدارة برنامج الحماية من الفيروسات من Microsoft Defender في شركتك

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يمكنك إدارة برنامج الحماية من الفيروسات من Microsoft Defender وتكوينها باستخدام الأدوات التالية:

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (الآن جزء من إدارة نقاط النهاية من Microsoft)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (الآن جزء من إدارة نقاط النهاية من Microsoft)
- [نهج المجموعة](./use-group-policy-microsoft-defender-antivirus.md)
- [PowerShell cmdlets](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Windows Management Instrumentation (WMI)](./use-wmi-microsoft-defender-antivirus.md)
- [الأداة المساعدة لسطر أوامر حماية البرامج الضارة من Microsoft](./command-line-arguments-microsoft-defender-antivirus.md) (يشار إليها باسم الأداة المساعدة *mpcmdrun.exe*

توفر المقالات التالية مزيدا من المعلومات والارتباطات والموارد لاستخدام هذه الأدوات لإدارة برنامج الحماية من الفيروسات من Microsoft Defender وتكوينها.

|مقالة|الوصف|
|:---|:---|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام Microsoft Intune Microsoft Endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|معلومات حول استخدام Intune و Configuration Manager لنشر وإدارة والإبلاغ وتكوين برنامج الحماية من الفيروسات من Microsoft Defender|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام إعدادات نهج المجموعة](use-group-policy-microsoft-defender-antivirus.md)|قائمة بكافة إعدادات نهج المجموعة الموجودة في قوالب ADMX|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md)|إرشادات استخدام أوامر cmdlets PowerShell لإدارة برنامج الحماية من الفيروسات من Microsoft Defender، بالإضافة إلى ارتباطات إلى وثائق لكافة أوامر cmdlets والمعلمات المسموح بها|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام Windows Management Instrumentation (WMI)](use-wmi-microsoft-defender-antivirus.md)|إرشادات استخدام WMI لإدارة برنامج الحماية من الفيروسات من Microsoft Defender، بالإضافة إلى ارتباطات لوثائق واجهات برمجة تطبيقات WMIv2 (بما في ذلك جميع الفئات والأساليب والخصائص)|
|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام أداة سطر الأوامر MpCmdRun.exe](command-line-arguments-microsoft-defender-antivirus.md)|إرشادات حول استخدام أداة سطر الأوامر المخصصة لإدارة برنامج الحماية من الفيروسات من Microsoft Defender واستخدامها|

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)