---
title: مراجعة نتائج عمليات برنامج الحماية من الفيروسات من Microsoft Defender ضوئية
description: مراجعة نتائج عمليات الفحص باستخدام Microsoft Endpoint Configuration Manager أو Microsoft Intune أو تطبيق أمن Windows
keywords: نتائج الفحص، المعالجة، الفحص الكامل، المسح السريع
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
ms.openlocfilehash: 8727baa9bb1935a1186907ca5f3d9d4f82dad6d4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473640"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>مراجعة برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

بعد اكتمال برنامج الحماية من الفيروسات من Microsoft Defender، سواء كان عند الطلب أو فحص مجدول، يتم [](run-scan-microsoft-defender-antivirus.md) تسجيل النتائج، كما [](scheduled-catch-up-scans-microsoft-defender-antivirus.md)يمكنك عرض النتائج. 


## <a name="use-configuration-manager-to-review-scan-results"></a>استخدام Configuration Manager لمراجعة نتائج الفحص

راجع [كيفية مراقبة حالة Endpoint Protection.](/configmgr/protect/deploy-use/monitor-endpoint-protection)

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>استخدام PowerShell cmdlets لمراجعة نتائج الفحص

سيرجع أمر cmdlet التالي كل عملية كشف على نقطة النهاية. إذا كانت هناك عمليات كشف متعددة لنفس الخطر، سيتم إدراج كل عملية كشف بشكل منفصل، استنادا إلى وقت كل عملية كشف:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="Cmdlets ومخرجات PowerShell" lightbox="../../media/wdav-get-mpthreatdetection.png":::

يمكنك تحديد الحد `-ThreatID` من الإخراج لإظهار الكشف عن خطر معين فقط.

إذا كنت تريد سرد الكشف عن المخاطر، ولكن دمج الكشف عن الخطر نفسه في عنصر واحد، يمكنك استخدام أمر cmdlet التالي:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="رمز PowerShell" lightbox="../../media/wdav-get-mpthreat.png":::

راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين الأمرين [cmdlets](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus وتشغيلها للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>استخدام Windows إدارة البيانات (WMI) لمراجعة نتائج الفحص

استخدم أسلوب [**الحصول** على MSFT_MpThreat والصفوف **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).


## <a name="related-articles"></a>المقالات ذات الصلة

- [تخصيص نتائج عمليات المسح برنامج الحماية من الفيروسات من Microsoft Defender والوساطة وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
