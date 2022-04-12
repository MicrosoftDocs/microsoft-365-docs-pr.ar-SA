---
title: مراجعة نتائج عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender
description: مراجعة نتائج عمليات الفحص باستخدام Microsoft Endpoint Configuration Manager أو Microsoft Intune أو تطبيق أمن Windows
keywords: مسح النتائج، والمعالجة، والمسح الضوئي الكامل، والمسح الضوئي السريع
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
ms.openlocfilehash: 9ffe10560bb36c8fc1311061510f35396934e3b8
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790625"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>مراجعة نتائج فحص برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

بعد اكتمال فحص برنامج الحماية من الفيروسات من Microsoft Defender، سواء كان فحصا [حسب الطلب](run-scan-microsoft-defender-antivirus.md) أو [مجدولا](scheduled-catch-up-scans-microsoft-defender-antivirus.md)، يتم تسجيل النتائج ويمكنك عرض النتائج. 


## <a name="use-configuration-manager-to-review-scan-results"></a>استخدام Configuration Manager لمراجعة نتائج الفحص

راجع [كيفية مراقبة حالة Endpoint Protection](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>استخدام PowerShell cmdlets لمراجعة نتائج الفحص

سيعيد cmdlet التالي كل اكتشاف على نقطة النهاية. إذا كانت هناك عمليات كشف متعددة لنفس التهديد، فسيتم سرد كل عملية كشف بشكل منفصل، استنادا إلى وقت كل عملية كشف:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="أوامر PowerShell cmdlets ومخرجاتها" lightbox="../../media/wdav-get-mpthreatdetection.png":::

يمكنك تحديد `-ThreatID` الحد من الإخراج لإظهار عمليات الكشف عن تهديد معين فقط.

إذا كنت ترغب في سرد عمليات الكشف عن التهديدات، ولكن مع دمج عمليات الكشف عن نفس التهديد في عنصر واحد، يمكنك استخدام cmdlet التالي:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="التعليمات البرمجية ل PowerShell" lightbox="../../media/wdav-get-mpthreat.png":::

راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets لبرنامج الحماية من الفيروسات](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>استخدام تعليمات إدارة Windows (WMI) لمراجعة نتائج الفحص

استخدم [أسلوب **Get** للفئات **MSFT_MpThreat** وفئات **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)


## <a name="related-articles"></a>المقالات ذات الصلة

- [تخصيص نتائج عمليات الفحص والمعالجة برنامج الحماية من الفيروسات من Microsoft Defender وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
