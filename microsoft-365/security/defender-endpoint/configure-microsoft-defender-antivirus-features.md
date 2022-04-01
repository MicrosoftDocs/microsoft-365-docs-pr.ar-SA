---
title: تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender باستخدام Intune Microsoft Endpoint Configuration Manager و"نهج المجموعة" و PowerShell.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، مكافحة البرامج الضارة، الأمان، defender، تكوين، تكوين، إدارة المؤتمرات، Microsoft Endpoint Configuration Manager، SCCM، Intune، MDM، إدارة أجهزة المحمول، GP، نهج المجموعة، PowerShell
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
ms.openlocfilehash: 183fedefbbb56411674ff80a9feedc507cff0530
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63579543"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

يمكنك تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام عدد من الأدوات، مثل:

- إدارة نقاط النهاية من Microsoft (التي تتضمن Microsoft Intune Microsoft Endpoint Configuration Manager)
- نهج المجموعة
- PowerShell cmdlets
- Windows إدارة الأجهزة (WMI)
- [إرفاق المستأجر](/mem/configmgr/tenant-attach/)

يمكن تكوين الفئات العريضة التالية من الميزات:

- الحماية التي يتم تسليمها من السحابة. راجع [الحماية والحماية التي يتم توفيرها في السحابة برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- الحماية في الوقت الحقيقي دائما، بما في ذلك الحماية السلوكية، والحماية التحليلية، والحماية المستندة إلى التعلم الآلي. راجع [تكوين الحماية السلوكية، والحماية التحليلية، وفي الوقت الحقيقي](configure-protection-features-microsoft-defender-antivirus.md).

- كيفية تفاعل المستخدمين مع العميل على نقاط النهاية الفردية. راجع الموارد التالية:
  - [منع المستخدمين من رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [منع المستخدمين من تعديل إعدادات نهج برنامج الحماية من الفيروسات من Microsoft Defender محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> راجع [مواضيع المراجع الخاصة بأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md).
