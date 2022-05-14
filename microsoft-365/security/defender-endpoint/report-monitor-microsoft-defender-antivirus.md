---
title: مراقبة الحماية برنامج الحماية من الفيروسات من Microsoft Defender وإعداد تقرير بشأنها
description: استخدم Configuration Manager أو أدوات إدارة معلومات الأمان والأحداث (SIEM) لاستهلاك التقارير ومراقبة Microsoft Defender AV باستخدام PowerShell وWMI.
keywords: siem, monitor, report, Microsoft Defender AV
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
ms.openlocfilehash: c36902d6c636c726a42292d7a6e4f0cdec60edb7
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415096"
---
# <a name="report-on-microsoft-defender-antivirus"></a>الإبلاغ عن برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

تم تضمين برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10 و Windows 11 و Windows Server 2019 و Windows Server 2022 و Windows Server 2016. برنامج الحماية من الفيروسات من Microsoft Defender هو من الجيل التالي من الحماية في Microsoft Defender لنقطة النهاية. تساعد الحماية من الجيل التالي على حماية أجهزتك من تهديدات البرامج مثل الفيروسات والبرامج الضارة وبرامج التجسس عبر البريد الإلكتروني والتطبيقات والسحابة والويب.

مع برنامج الحماية من الفيروسات من Microsoft Defender، لديك العديد من الخيارات لمراجعة حالة الحماية والتنبيهات. يمكنك استخدام إدارة نقاط النهاية من Microsoft [لمراقبة برنامج الحماية من الفيروسات من Microsoft Defender](/configmgr/protect/deploy-use/monitor-endpoint-protection) أو [إنشاء تنبيهات البريد الإلكتروني](/configmgr/protect/deploy-use/endpoint-configure-alerts). أو يمكنك مراقبة الحماية باستخدام [Microsoft Intune](/intune/introduction-intune).

إذا كان لديك خادم معلومات أمان وإدارة أحداث (SIEM) تابع لجهة خارجية، يمكنك أيضا استهلاك [Windows أحداث عميل Defender](/windows/win32/events/windows-events).

تتضمن أحداث Windows العديد من مصادر أحداث الأمان، بما في ذلك أحداث Security Account Manager (SAM) ([المحسنة Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511)، راجع أيضا موضوع [تدقيق الأمان](/windows/device-security/auditing/security-auditing-overview)) [وأحداث Windows Defender](troubleshoot-microsoft-defender-antivirus.md).

يمكن تجميع هذه الأحداث مركزيا باستخدام [مجمع أحداث Windows](/windows/win32/wec/windows-event-collector). غالبا ما تحتوي خوادم SIEM على موصلات لأحداث Windows، مما يسمح لك بربط جميع أحداث الأمان في خادم SIEM.

يمكنك أيضا [مراقبة أحداث البرامج الضارة باستخدام حل تقييم البرامج الضارة في Log Analytics](/azure/log-analytics/log-analytics-malware).

لمراقبة الحالة أو تحديدها باستخدام PowerShell أو WMI أو Microsoft Azure، راجع [(جدول خيارات النشر والإدارة وإعداد التقارير)](deploy-manage-report-microsoft-defender-antivirus.md#ref2).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
