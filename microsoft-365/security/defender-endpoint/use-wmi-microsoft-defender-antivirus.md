---
title: تكوين برنامج الحماية من الفيروسات من Microsoft Defender WMI
description: تعرف على كيفية تكوين إعدادات برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها باستخدام برامج WMI النصية لاسترداد إعدادات Microsoft Defender لنقطة النهاية وتعديلها وتحديثها.
keywords: wmi، البرامج النصية، أدوات إدارة windows، التكوين
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
ms.openlocfilehash: c8057a971576d5511440ac009acd6eab55b302e9
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63575471"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>استخدم Windows أدوات الإدارة (WMI) لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Windows أدوات الإدارة (WMI) هي واجهة النصية التي تسمح لك باسترداد الإعدادات وتعديلها وتحديثها.

اقرأ المزيد حول WMI في [مكتبة إدارة نظام شبكة مطوري Microsoft](/windows/win32/wmisdk/wmi-start-page).

برنامج الحماية من الفيروسات من Microsoft Defender عدد من فئات WMI المحددة التي يمكن استخدامها لتنفيذ معظم الدالات نفسها مثل "نهج المجموعة" وأدوات الإدارة الأخرى. العديد من الفئات مماثلة ل [Defender for Cloud PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md).

[تسرد مكتبة مراجع Windows Defender WMIv2 فئات WMI](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) المتوفرة برنامج الحماية من الفيروسات من Microsoft Defender، وتتضمن برامج نصية على سبيل المثال.

ستؤثر التغييرات التي يتم إدخالها على WMI على الإعدادات المحلية في نقطة النهاية حيث يتم نشر التغييرات أو إجراءها. وهذا يعني أن عمليات نشر النهج باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو Microsoft Intune الكتابة فوق التغييرات التي يتم إدخالها باستخدام WMI. 

يمكنك [تكوين الإعدادات التي يمكن تجاوزها محليا باستخدام تجاوز النهج المحلي](configure-local-policy-overrides-microsoft-defender-antivirus.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [مواضيع مرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
