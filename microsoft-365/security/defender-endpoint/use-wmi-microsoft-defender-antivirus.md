---
title: تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام WMI
description: تعرف على كيفية تكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام البرامج النصية WMI لاسترداد الإعدادات وتعديلها وتحديثها في Microsoft Defender لنقطة النهاية.
keywords: wmi، والبرامج النصية، وأدوات إدارة Windows، والتكوين
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 8ef8355afe3019c2a179f59d83faddac4aa5792a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418991"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>استخدم Windows Management Instrumentation (WMI) لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

Windows Management Instrumentation (WMI) هي واجهة برمجة نصية تسمح لك باسترداد إعدادات وتعديلها وتحديثها.

اقرأ المزيد حول WMI في [مكتبة إدارة نظام شبكة مطوري Microsoft](/windows/win32/wmisdk/wmi-start-page).

يحتوي برنامج الحماية من الفيروسات من Microsoft Defender على عدد من فئات WMI المحددة التي يمكن استخدامها لتنفيذ معظم الوظائف نفسها مثل نهج المجموعة وأدوات الإدارة الأخرى. العديد من الفئات مماثلة [ل Defender for Cloud PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md).

تسرد [مكتبة مرجع موفر MSDN Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) فئات WMI المتوفرة برنامج الحماية من الفيروسات من Microsoft Defender، وتتضمن أمثلة على البرامج النصية.

ستؤثر التغييرات التي تم إجراؤها باستخدام WMI على الإعدادات المحلية على نقطة النهاية حيث يتم نشر التغييرات أو إجراؤها. وهذا يعني أن عمليات نشر النهج باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو Microsoft Intune يمكن الكتابة فوق التغييرات التي تم إجراؤها باستخدام WMI. 

يمكنك [تكوين الإعدادات التي يمكن تجاوزها محليا مع تجاوز النهج المحلي](configure-local-policy-overrides-microsoft-defender-antivirus.md).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [مواضيع مرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
