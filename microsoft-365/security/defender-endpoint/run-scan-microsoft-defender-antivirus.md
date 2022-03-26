---
title: تشغيل عمليات الفحص عند الطلب وتخصيصها في برنامج الحماية من الفيروسات من Microsoft Defender
description: تشغيل عمليات الفحص عند الطلب وتكوينها باستخدام PowerShell أو Windows Management Instrumentation أو بشكل فردي على نقاط النهاية باستخدام أمن Windows التطبيق
keywords: المسح الضوئي، عند الطلب، dos، intune، المسح السريع
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/22/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 1f82fe410634ab92f7b403a30bcbcdf9a61634ba
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63575472"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>تكوين عمليات فحص عند برنامج الحماية من الفيروسات من Microsoft Defender عند الطلب

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

يمكنك تشغيل فحص عند الطلب على نقاط النهاية الفردية. ستبدأ عمليات الفحص هذه على الفور، كما يمكنك تعريف معلمات الفحص، مثل الموقع أو النوع. عند تشغيل عملية فحص، يمكنك الاختيار من بين ثلاثة أنواع: الفحص السريع والمسح الكامل والفحص المخصص. في معظم الحالات، استخدم فحصا سريعا. تتفحص عملية المسح السريع كل المواقع التي يمكن أن يكون فيها برنامج ضار مسجلا للبدء باستخدام النظام، مثل مفاتيح التسجيل ومجلدات بدء التشغيل المعروفة Windows بدء التشغيل.

يساعد إجراء مسح سريع على توفير حماية قوية من البرامج الضارة التي تبدأ من النظام والبرامج الضارة على مستوى النواة، وذلك إذا تم دمجها مع الحماية دائما في الوقت الحقيقي، والتي تراجع الملفات عند فتحها أو إغلاقها، وكلما انتقل مستخدم إلى مجلد. في معظم الحالات، يكون الفحص السريع كافيا وهو الخيار الموصى به للفحص المجدول أو عند الطلب. [تعرف على المزيد حول أنواع الفحص](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).

> [!IMPORTANT]
> برنامج الحماية من الفيروسات من Microsoft Defender في سياق [حساب LocalSystem](/windows/win32/services/localsystem-account) عند إجراء فحص محلي. أما بالنسبة إلى عمليات فحص الشبكة، فهي تستخدم سياق حساب الجهاز. إذا لم يكن حساب جهاز المجال لديه الأذونات المناسبة للوصول إلى المشاركة، فلن يعمل الفحص. تأكد من أن الجهاز لديه أذونات لمشاركة شبكة الوصول.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>استخدام إدارة نقاط النهاية من Microsoft لتشغيل عملية فحص

1. انتقل إلى إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) وسجل الدخول.

2. اختر **الحماية من الفيروسات لنقطة** \> **النهاية**.

3. في قائمة علامات التبويب **، حدد Windows 10** نقاط نهاية غير Windows 11 **نقاط نهاية غير صحية**.

4. من قائمة الإجراءات المتوفرة، حدد **فحص سريع** (مستحسن) أو **فحص كامل**.

   [![خيارات الفحص على علامة التبويب Windows 10 نقاط النهاية غير الصحية.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> لمزيد من المعلومات حول استخدام إدارة نقاط النهاية من Microsoft لتشغيل عملية فحص، راجع مهام الحماية من البرامج الضارة وجدار [الحماية: كيفية إجراء فحص عند الطلب](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers).

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>استخدام الأداة mpcmdrun.exe سطر الأوامر لتشغيل عملية فحص

استخدم المعلمة `-scan` التالية:

```console
mpcmdrun.exe -scan -scantype 1
```

لمزيد من المعلومات حول كيفية استخدام الأداة والمعلمات الإضافية، بما في ذلك بدء فحص كامل أو تحديد المسارات، راجع استخدام أداة سطر الأوامر [mpcmdrun.exe](command-line-arguments-microsoft-defender-antivirus.md) لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="use-microsoft-intune-to-run-a-scan"></a>استخدام Microsoft Intune لتشغيل عملية فحص

1. انتقل إلى إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) وسجل الدخول.

2. من على الجانب، حدد **الأجهزة** \> **كافة الأجهزة** واختر الجهاز الذي تريد فحصه.

3. حدد **... المزيد**. من الخيارات، حدد **فحص سريع** (مستحسن) أو **فحص كامل**.

## <a name="use-the-windows-security-app-to-run-a-scan"></a>استخدام تطبيق أمن Windows لتشغيل عملية فحص

راجع [تشغيل فحص في تطبيق أمن Windows للحصول](microsoft-defender-security-center-antivirus.md) على إرشادات حول تشغيل الفحص على نقاط النهاية الفردية.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>استخدام PowerShell cmdlets لتشغيل عملية فحص

استخدم cmdlet التالي:

```PowerShell
Start-MpScan
```

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع استخدام [الأمرين cmdlets في PowerShell لتكوين](use-powershell-cmdlets-microsoft-defender-antivirus.md) برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets و Defender Antivirus وتشغيلها](/powershell/module/defender/).

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>استخدام Windows إدارة البيانات (WMI) لتشغيل عملية فحص

استخدم أسلوب [**البدء**](/previous-versions/windows/desktop/defender/start-msft-mpscan) **للفئة** MSFT_MpScan.

لمزيد من المعلومات حول المعلمات المسموح بها، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)
