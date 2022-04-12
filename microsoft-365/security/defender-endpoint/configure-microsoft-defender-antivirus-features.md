---
title: تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender باستخدام Intune، Microsoft Endpoint Configuration Manager، نهج المجموعة، وPowerShell.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، ومكافحة البرامج الضارة، والأمان، وDimer، والتكوين، والتكوين، و Config Manager، Microsoft Endpoint Configuration Manager، وSCCM، وIntune، وMDM، وإدارة أجهزة المحمول، وGP، ونهج المجموعة، وPowerShell
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/14/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 8a1aa78a153e11f1a36fe9f7dcbd85322e6f258d
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787941"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

يمكنك تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام عدد من الأدوات، مثل:

- إدارة نقاط النهاية من Microsoft (التي تتضمن Microsoft Intune Microsoft Endpoint Configuration Manager)
- نهج المجموعة
- PowerShell cmdlets
- Windows Management Instrumentation (WMI)
- [إرفاق المستأجر](/mem/configmgr/tenant-attach/)

يمكن تكوين الفئات العامة التالية من الميزات:

- الحماية التي توفرها السحابة. راجع [الحماية المقدمة من السحابة برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- الحماية في الوقت الحقيقي دائما، بما في ذلك الحماية السلوكية والاستعلائية والمستندة إلى التعلم الآلي. راجع [تكوين الحماية السلوكية والاستيائية والحماية في الوقت الحقيقي](configure-protection-features-microsoft-defender-antivirus.md).

- كيفية تفاعل المستخدمين النهائيين مع العميل على نقاط النهاية الفردية. راجع الموارد التالية:
  - [منع المستخدمين من رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [منع المستخدمين أو السماح لهم بتعديل إعدادات نهج برنامج الحماية من الفيروسات من Microsoft Defender محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> مراجعة [المواضيع المرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)