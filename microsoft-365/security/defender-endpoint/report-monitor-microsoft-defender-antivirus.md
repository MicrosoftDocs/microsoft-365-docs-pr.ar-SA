---
title: مراقبة البيانات برنامج الحماية من الفيروسات من Microsoft Defender الحماية
description: استخدم إدارة التكوين أو أدوات إدارة معلومات الأمان والأحداث (SIEM) لاستخدام التقارير، وراقب Microsoft Defender AV مع PowerShell و WMI.
keywords: siem، جهاز عرض، تقرير، Microsoft Defender AV
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
ms.openlocfilehash: 8d801daed1ae9884d10d6a4eec7059096333ec6f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63583237"
---
# <a name="report-on-microsoft-defender-antivirus"></a>الإبلاغ عن برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10 و Windows 11 و Windows Server 2019 و Windows Server 2022 و Windows Server 2016. برنامج الحماية من الفيروسات من Microsoft Defender هو من حماية الجيل التالي في Microsoft Defender ل Endpoint. تساعد حماية الجيل التالي على حماية أجهزتك من تهديدات البرامج مثل الفيروسات والبرامج الضارة وبرامج التجسس عبر البريد الإلكتروني والتطبيقات والسحابة وال web.

باستخدام برنامج الحماية من الفيروسات من Microsoft Defender، لديك العديد من الخيارات لمراجعة حالة الحماية والتنبيهات. يمكنك استخدام إدارة نقاط النهاية من Microsoft [لمراقبة برنامج الحماية من الفيروسات من Microsoft Defender](/configmgr/protect/deploy-use/monitor-endpoint-protection) [أو إنشاء تنبيهات البريد الإلكتروني](/configmgr/protect/deploy-use/endpoint-configure-alerts). أو، يمكنك مراقبة [الحماية باستخدام Microsoft Intune](/intune/introduction-intune).

إذا كان لديك خادم معلومات أمان وإدارة أحداث (SIEM) جهة خارجية، يمكنك أيضا استخدام Windows [عميل Defender](/windows/win32/events/windows-events).

Windows الأحداث العديد من مصادر أحداث الأمان، بما في ذلك أحداث إدارة حسابات الأمان (SAM) (محسنة ل [Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511)، راجع أيضا موضوع تدقيق الأمان) [Windows Defender](troubleshoot-microsoft-defender-antivirus.md).[](/windows/device-security/auditing/security-auditing-overview)

يمكن تجميع هذه الأحداث مركزيا باستخدام Windows [الحدث](/windows/win32/wec/windows-event-collector). غالبا ما يكون لدى خوادم SIEM موصلات Windows الأحداث، مما يسمح لك بربط كل أحداث الأمان في خادم SIEM.

يمكنك أيضا مراقبة [أحداث البرامج الضارة باستخدام حل تقييم البرامج الضارة في Log Analytics](/azure/log-analytics/log-analytics-malware).

لمراقبة الحالة أو تحديدها باستخدام PowerShell أو WMI أو Microsoft Azure، راجع (جدول خيارات النشر والإدارة [وإعداد التقارير)](deploy-manage-report-microsoft-defender-antivirus.md#ref2).

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
