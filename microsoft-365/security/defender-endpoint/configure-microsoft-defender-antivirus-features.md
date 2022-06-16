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
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 8271f6d0fcc58ce5a7e1ce08f6034a8a90afab48
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115444"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender


**ينطبق على:**

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
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
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)
