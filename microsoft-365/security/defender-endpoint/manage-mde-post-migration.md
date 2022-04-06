---
title: إدارة Microsoft Defender ل ترحيل ما بعد نقطة النهاية
description: الآن وقد قمت بالتبديل إلى Microsoft Defender لنقطة النهاية، فإن الخطوة التالية هي إدارة ميزات الحماية من المخاطر
keywords: بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، و Microsoft Defender ل Endpoint، وedr
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
- m365solution-scenario
ms.topic: conceptual
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 2be934da8a87e02ead5c395097d90ccde46cb9d7
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/30/2021
ms.locfileid: "63583758"
---
# <a name="manage-microsoft-defender-for-endpoint-post-migration"></a>إدارة Microsoft Defender لنقطة النهاية، نشر الترحيل

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

بعد الانتقال من حل الحماية من الفيروسات وحماية نقطة النهاية السابق إلى Microsoft Defender ل Endpoint، تكون الخطوة التالية هي إدارة الميزات والإمكانات. نوصي باستخدام [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview)، التي تتضمن Microsoft Intune Microsoft Endpoint Configuration Manager، لإدارة [](/mem/intune/fundamentals/what-is-intune) أجهزة المؤسسة وإعدادات الأمان[](/mem/configmgr/core/understand/introduction). ومع ذلك، يمكنك استخدام أدوات/أساليب أخرى، مثل كائنات [نهج المجموعة في Azure Active Directory Domain Services](/azure/active-directory-domain-services/manage-group-policy).

يسرد الجدول التالي الأدوات/الأساليب المختلفة التي يمكنك استخدامها، مع ارتباطات لمعرفة المزيد.

<br/><br/>

|أداة/أسلوب|الوصف|
|---|---|
|**[معلومات إدارة الثغرات الأمنية المخاطر والخطر](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** في [مدخل](https://security.microsoft.com/) Microsoft 365 Defender|توفر لوحة & إدارة الثغرات الأمنية معلومات قابلة للتنفيذ يمكن لفريق عمليات الأمان استخدامها لتقليل التعرض وتحسين وضعية الأمان في مؤسستك. <br/><br/> راجع [المخاطر & إدارة الثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) نظرة [عامة حول Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (مستحسن)|Microsoft Intune (Intune)، أحد مكونات إدارة نقاط النهاية من Microsoft، على [](/mem/endpoint-manager-overview)إدارة أجهزة المحمول (MDM) وإدارة تطبيقات الأجهزة المحمولة (MAM). باستخدام Intune، يمكنك التحكم في كيفية استخدام أجهزة مؤسستك، بما في ذلك الهواتف المحمولة وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر المحمولة. يمكنك أيضا تكوين سياسات معينة للتحكم في التطبيقات. <br/><br/> راجع [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md).|
|**[Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)**|إدارة نقاط النهاية من Microsoft (إدارة التكوين)، المعروف سابقا ب System Center Configuration Manager، أحد [مكونات إدارة نقاط النهاية من Microsoft.](/mem/endpoint-manager-overview) إدارة التكوين هي أداة فعالة لإدارة المستخدمين والأجهزة والبرامج. <br/><br/> راجع [إدارة Microsoft Defender ل Endpoint باستخدام إدارة التكوين](manage-mde-post-migration-configuration-manager.md).|
|**[كائنات نهج المجموعة في Azure Active Directory Domain Services](/azure/active-directory-domain-services/manage-group-policy)**|[تتضمن خدمات مجال Azure Active Directory](/azure/active-directory-domain-services/overview) كائنات نهج المجموعة المضمنة للمستخدمين والأجهزة. يمكنك تخصيص كائنات نهج المجموعة المضمنة كما هو مطلوب لبيئة، بالإضافة إلى إنشاء كائنات نهج المجموعة المخصصة ووحدات تنظيمية (OUs). <br/><br/> راجع [إدارة Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة](manage-mde-post-migration-group-policy-objects.md).|
|**[PowerShell و WMI و MPCmdRun.exe](manage-mde-post-migration-other-tools.md)**|*نوصي باستخدام إدارة نقاط النهاية من Microsoft (التي تتضمن Intune ومدير التكوين) لإدارة ميزات الحماية من المخاطر على أجهزة مؤسستك. ومع ذلك، يمكنك تكوين بعض الإعدادات، مثل إعدادات برنامج الحماية من الفيروسات من Microsoft Defender الأجهزة الفردية (نقاط النهاية) باستخدام PowerShell أو WMI أو أداة MPCmdRun.exe.* <br/><br/> يمكنك استخدام PowerShell لإدارة برنامج الحماية من الفيروسات من Microsoft Defender والحماية من الهجمات وقواعد الحد من الهجمات. راجع [تكوين Microsoft Defender ل Endpoint باستخدام PowerShell](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell). <br/><br/> يمكنك استخدام Windows إدارة الأدوات (WMI) لإدارة برنامج الحماية من الفيروسات من Microsoft Defender والاستثناءات. راجع [تكوين Microsoft Defender لنقطة النهاية باستخدام WMI](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi). <br/><br/> يمكنك استخدام الأداة المساعدة للحماية من البرامج الضارة Command-Line Microsoft (MPCmdRun.exe) لإدارة برنامج الحماية من الفيروسات من Microsoft Defender والاستثناءات، بالإضافة إلى التحقق من صحة الاتصالات بين الشبكة والسحابة. راجع [تكوين Microsoft Defender لنقطة النهاية باستخدام MPCmdRun.exe](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|


## <a name="see-also"></a>راجع أيضًا

- [معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)
