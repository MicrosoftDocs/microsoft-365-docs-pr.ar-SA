---
title: إدارة Microsoft Defender لنقطة النهاية بعد الإعداد الأولي أو الترحيل
description: الآن بعد أن قمت بالتبديل إلى Microsoft Defender لنقطة النهاية، فإن خطوتك التالية هي إدارة ميزات الحماية من التهديدات
keywords: ما بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، Microsoft Defender لنقطة النهاية، edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: d00de67b52f521042d5595320346f875f8c89c9e
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607554"
---
# <a name="manage-microsoft-defender-for-endpoint-after-initial-setup-or-migration"></a>إدارة Microsoft Defender لنقطة النهاية بعد الإعداد الأولي أو الترحيل

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

بعد إعداد Microsoft Defender لنقطة النهاية وتكوينه، تكون خطوتك التالية هي إدارة ميزاتك وقدراتك. نوصي باستخدام [Microsoft إدارة نقاط النهاية](/mem/endpoint-manager-overview)، والتي تتضمن [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [ونقطة نهاية Microsoft Configuration Manager](/mem/configmgr/core/understand/introduction)، لإدارة أجهزة مؤسستك وإعدادات الأمان. ومع ذلك، يمكنك استخدام أدوات/أساليب أخرى، مثل [نهج المجموعة العناصر في azure خدمات مجال Active Directory](/azure/active-directory-domain-services/manage-group-policy).

يسرد الجدول التالي أدوات/أساليب مختلفة يمكنك استخدامها، مع ارتباطات لمعرفة المزيد.

|أداة/أسلوب|الوصف|
|---|---|
|**[رؤى لوحة معلومات إدارة المخاطر والثغرات الأمنية](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** في [مدخل Microsoft 365 Defender](https://security.microsoft.com/)|توفر لوحة معلومات إدارة الثغرات الأمنية & المخاطر معلومات قابلة للتنفيذ يمكن لفريق عمليات الأمان استخدامها لتقليل التعرض وتحسين وضع الأمان في مؤسستك. <br/><br/> راجع [إدارة الثغرات الأمنية & المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) [ونظرة عامة على Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (مستحسن)|يركز Microsoft Intune (Intune)، أحد مكونات [Microsoft إدارة نقاط النهاية](/mem/endpoint-manager-overview)، على إدارة أجهزة المحمول (MDM) وإدارة تطبيقات المحمول (MAM). باستخدام Intune، يمكنك التحكم في كيفية استخدام أجهزة مؤسستك، بما في ذلك الهواتف المحمولة وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر المحمولة. يمكنك أيضا تكوين نهج محددة للتحكم في التطبيقات. <br/><br/> راجع [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md).|
|**[Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)**|Microsoft إدارة نقاط النهاية (Configuration Manager)، المعروف سابقا باسم system Center Configuration Manager، هو أحد مكونات [Microsoft إدارة نقاط النهاية](/mem/endpoint-manager-overview). Configuration Manager هي أداة قوية لإدارة المستخدمين والأجهزة والبرامج. <br/><br/> راجع [إدارة Microsoft Defender لنقطة النهاية باستخدام Configuration Manager](manage-mde-post-migration-configuration-manager.md).|
|**[كائنات نهج المجموعة في Azure خدمات مجال Active Directory](/azure/active-directory-domain-services/manage-group-policy)**|يتضمن [Azure خدمات مجال Active Directory](/azure/active-directory-domain-services/overview) عناصر نهج المجموعة مضمنة للمستخدمين والأجهزة. يمكنك تخصيص كائنات نهج المجموعة المضمنة حسب الحاجة للبيئة الخاصة بك، بالإضافة إلى إنشاء كائنات نهج المجموعة مخصصة ووحدات تنظيمية (OUs). <br/><br/> راجع [إدارة Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة](manage-mde-post-migration-group-policy-objects.md).|
|**[PowerShell وWMI و MPCmdRun.exe](manage-mde-post-migration-other-tools.md)**|*نوصي باستخدام Microsoft إدارة نقاط النهاية (التي تتضمن Intune و Configuration Manager) لإدارة ميزات الحماية من التهديدات على أجهزة مؤسستك. ومع ذلك، يمكنك تكوين بعض الإعدادات، مثل إعدادات برنامج الحماية من الفيروسات من Microsoft Defender على الأجهزة الفردية (نقاط النهاية) باستخدام PowerShell أو WMI أو أداة MPCmdRun.exe.* <br/><br/> يمكنك استخدام PowerShell لإدارة برنامج الحماية من الفيروسات من Microsoft Defender وحماية الاستغلال وقواعد تقليل الأجزاء المعرضة للهجوم. راجع [تكوين Microsoft Defender لنقطة النهاية باستخدام PowerShell](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell). <br/><br/> يمكنك استخدام Windows Management Instrumentation (WMI) لإدارة برنامج الحماية من الفيروسات من Microsoft Defender والاستثناءات. راجع [تكوين Microsoft Defender لنقطة النهاية باستخدام WMI](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi). <br/><br/> يمكنك استخدام الأداة المساعدة Command-Line للحماية من البرامج الضارة من Microsoft (MPCmdRun.exe) لإدارة برنامج الحماية من الفيروسات من Microsoft Defender والاستثناءات، بالإضافة إلى التحقق من صحة الاتصالات بين شبكتك والسحابة. راجع [تكوين Microsoft Defender لنقطة النهاية باستخدام MPCmdRun.exe](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|


## <a name="see-also"></a>راجع أيضًا

- [معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)
