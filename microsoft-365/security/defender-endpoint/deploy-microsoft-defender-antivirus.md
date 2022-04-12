---
title: نشر برنامج الحماية من الفيروسات من Microsoft Defender
description: نشر برنامج الحماية من الفيروسات من Microsoft Defender لحماية نقاط النهاية باستخدام Microsoft Intune، Microsoft Endpoint Configuration Manager، نهج المجموعة، PowerShell cmdlets أو WMI.
keywords: نشر، تمكين، برنامج الحماية من الفيروسات من Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: fe84fa4df958ea42304531defc4810edf332b3a3
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790515"
---
# <a name="deploy-and-enable-microsoft-defender-antivirus"></a>نشر برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

اعتمادا على أداة الإدارة التي تستخدمها، قد تحتاج إلى تمكين حماية برنامج الحماية من الفيروسات من Microsoft Defender أو تكوينها على وجه التحديد. 

راجع الجدول في ["Deploy" و"manage" و"report on برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md#ref2)" للحصول على إرشادات حول كيفية تمكين الحماية باستخدام Microsoft Intune، Microsoft Endpoint Configuration Manager، نهج المجموعة وActive Directory وMicrosoft Azure وPowerShell cmdlets وتعليمات إدارة Windows (WMI).

تتطلب بعض السيناريوهات المزيد من الإرشادات حول كيفية نشر حماية برنامج الحماية من الفيروسات من Microsoft Defender أو تكوينها بنجاح، مثل بيئات البنية الأساسية لسطح المكتب الظاهري (VDI).

توفر المقالة المتبقية في هذا القسم المشورة الشاملة وأفضل الممارسات [لإعداد برنامج الحماية من الفيروسات من Microsoft Defender على الأجهزة الظاهرية (VMs) في بيئة VDI أو خدمات سطح المكتب البعيد (RDS](deployment-vdi-microsoft-defender-antivirus.md)).

## <a name="related-articles"></a>المقالات ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [نشر التحديثات وإدارتها وإعداد تقرير عن برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [دليل النشر برنامج الحماية من الفيروسات من Microsoft Defender في بيئة البنية الأساسية لسطح المكتب الظاهري (VDI)](deployment-vdi-microsoft-defender-antivirus.md)

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)