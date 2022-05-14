---
title: استعادة الملفات المعزولة في برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك استعادة الملفات والمجلدات التي تم عزلها بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/19/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 52e83cf75385b36f87efbe72df9c865415f15452
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417337"
---
# <a name="restore-quarantined-files-in-microsoft-defender-antivirus"></a>استعادة الملفات المعزولة في برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

إذا تم تكوين برنامج الحماية من الفيروسات من Microsoft Defender للكشف عن التهديدات على جهازك ومعالجتها، برنامج الحماية من الفيروسات من Microsoft Defender عزل الملفات المشبوهة. إذا كنت متأكدا من أن الملف المعزول ليس تهديدا، يمكنك استعادته.

1. افتح **أمن Windows**.
2. حدد **الحماية من الفيروسات & ثم** انقر فوق **محفوظات الحماية**.
3. في قائمة كافة العناصر الأخيرة، قم بالتصفية حسب **العناصر المعزولة**.
4. حدد عنصرا تريد الاحتفاظ به، واتخذ إجراء، مثل الاستعادة.

> [!TIP]
> يمكن أيضا استعادة ملف من العزل باستخدام موجه الأوامر. راجع [استعادة ملف من العزل](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts#restore-file-from-quarantine). 

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [تكوين المعالجة لإجراء عمليات الفحص](configure-remediation-microsoft-defender-antivirus.md)
- [مراجعة نتائج الفحص](review-scan-results-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى اسم الملف والملحق وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات للملفات التي يتم فتحها بواسطة العمليات والتحقق من صحتها](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين استثناءات برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows](configure-server-exclusions-microsoft-defender-antivirus.md)