---
title: سيناريوهات وضع استكشاف الأخطاء وإصلاحها في Microsoft Defender لنقطة النهاية
description: استخدم وضع استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية لمعالجة مشكلات مكافحة الفيروسات المختلفة.
keywords: مكافحة الفيروسات، واستكشاف الأخطاء وإصلاحها، ووضع استكشاف الأخطاء وإصلاحها، والحماية من العبث، والتوافق
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c4824c603fda14d95487abdbc4f3b4949fdf0e97
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/17/2022
ms.locfileid: "66857407"
---
# <a name="troubleshooting-mode-scenarios-in-microsoft-defender-for-endpoint"></a>سيناريوهات وضع استكشاف الأخطاء وإصلاحها في Microsoft Defender لنقطة النهاية 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

يسمح لك وضع استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية باستكشاف أخطاء ميزات Microsoft Defender Antivirus المختلفة وإصلاحها من خلال تمكينها من الجهاز واختبار سيناريوهات مختلفة، حتى لو كان يتم التحكم فيها بواسطة نهج المؤسسة. يتم تعطيل وضع استكشاف الأخطاء وإصلاحها بشكل افتراضي ويتطلب منك تشغيله لجهاز (و/أو مجموعة من الأجهزة) لفترة محدودة. لاحظ أن هذه ميزة خاصة بالمؤسسات فقط، وتتطلب الوصول Microsoft 365 Defender.

## <a name="scenario-1-unable-to-install-application"></a>السيناريو 1: تعذر تثبيت التطبيق

إذا كنت تريد تثبيت تطبيق ولكنك تلقيت رسالة خطأ تفيد بأن برنامج الحماية من الفيروسات والحماية من العبث ب Microsoft Defender قيد التشغيل، فاتبع الخطوات أدناه لاستكشاف المشكلة وإصلاحها.

1. اطلب من مسؤول الأمان تشغيل وضع استكشاف الأخطاء وإصلاحها. ستتلقى إعلاما أمن Windows بمجرد بدء تشغيل وضع استكشاف الأخطاء وإصلاحها.  

2. الاتصال بالجهاز (باستخدام خدمات المحطة الطرفية على سبيل المثال) باستخدام أذونات المسؤول المحلي.  

3. بدء مراقبة العمليات (ProcMon). راجع الخطوات الموضحة في [استكشاف مشكلات الأداء المتعلقة بالحماية في الوقت الحقيقي وإصلاحها](troubleshoot-performance-issues.md).  

4. انتقل إلى Windows security  > **Threat & virus protection** > **Manage settings** > **Protection** > **Off**.  

5. تشغيل موجه أوامر PowerShell غير مقيد، وتبديل RTP. 

    - تشغيل `Get-MpComputerStatus` للتحقق من حالة RealTimeProtection.
    - تشغيل `Set-mppreference -DisableRealtimeMonitoring $true` لإيقاف تشغيل RTP.
    - تشغيل `Get-MpComputerStatus` مرة أخرى للتحقق من حالة RealTimeProtection.

6. حاول تثبيت التطبيق.

## <a name="scenario-2-high-cpu-usage-due-to-windows-defender-msmpengexe"></a>السيناريو 2: ارتفاع استخدام وحدة المعالجة المركزية بسبب Windows Defender (MsMpEng.exe)

في بعض الأحيان أثناء الفحص المجدول، يمكن أن تستهلك MsMpEng.exe وحدة المعالجة المركزية عالية.

1. انتقل إلى علامة التبويب **"تفاصيل** **إدارة** >  المهام" للتأكد من أن MsMpEng.exe هو السبب وراء ارتفاع استخدام وحدة المعالجة المركزية. تحقق أيضا لمعرفة ما إذا كان الفحص المجدول قيد التنفيذ حاليا.

2. قم بتشغيل ProcMon أثناء ارتفاع وحدة المعالجة المركزية لمدة 5 دقائق تقريبا، ثم راجع سجل ProcMon للحصول على أدلة. 

3. بمجرد تحديد السبب الجذري، قم بتشغيل وضع استكشاف الأخطاء وإصلاحها. 

4. سجل الدخول إلى الجهاز وابدأ تشغيل موجه أوامر PowerShell غير مقيد. 

5. إضافة استثناءات العملية/الملف/المجلد/الملحق استنادا إلى نتائج ProcMon باستخدام أحد الأوامر التالية (المسار والملحق واستثناءات العملية المذكورة أدناه هي أمثلة فقط): 

    - `Set-mppreference -ExclusionPath` (على سبيل المثال، C:\DB\DataFiles) 
    
    - `Set-mppreference –ExclusionExtension` (على سبيل المثال، .dbx) 
    
    - `Set-mppreference –ExclusionProcess` (على سبيل المثال، C:\DB\Bin\Convertdb.exe) 

6. بعد إضافة الاستبعاد، تحقق لمعرفة ما إذا كان استخدام وحدة المعالجة المركزية قد انخفض. 

لمزيد من المعلومات حول Set-MpPreference تفضيلات تكوين cmdlet لإجراء عمليات الفحص والتحديثات Windows Defender، راجع [Set-MpPreference](/powershell/module/defender/set-mppreference). 

## <a name="scenario-3-application-taking-longer-to-perform-an-action"></a>السيناريو 3: يستغرق التطبيق وقتا أطول لتنفيذ إجراء

عند تشغيل حماية Microsoft Defender Antivirus في الوقت الحقيقي، يستغرق التطبيق وقتا طويلا لتنفيذ المهام الأساسية. لإيقاف تشغيل الحماية في الوقت الحقيقي واستكشاف المشكلة وإصلاحها، اتبع الخطوات أدناه. 

1. اطلب من مسؤول الأمان تشغيل وضع استكشاف الأخطاء وإصلاحها على الجهاز. 

2. لتعطيل RTP لهذا السيناريو، قم أولا بإيقاف تشغيل الحماية من العبث. لمزيد من المعلومات، راجع [حماية إعدادات الأمان باستخدام الحماية من العبث بالبيانات](prevent-changes-to-security-settings-with-tamper-protection.md). 

3. بمجرد تعطيل الحماية من العبث، سجل الدخول إلى الجهاز. 

4. تشغيل موجه أوامر PowerShell غير مقيد. 

    - `Set-mppreference -DisableRealtimeMonitoring $true` 

5. بعد تعطيل RTP، تحقق لمعرفة ما إذا كان التطبيق بطيئا. 

## <a name="scenario-4-microsoft-office-plugin-blocked-by-attack-surface-reduction"></a>السيناريو 4: تم حظر المكون الإضافي Microsoft Office بواسطة تقليل الأجزاء المعرضة للهجوم

لا يسمح تقليل الأجزاء المعرضة للهجوم (ASR) بالعمل بشكل صحيح لأن **حظر جميع تطبيقات Office من إنشاء عمليات تابعة** تم تعيينه إلى وضع الحظر. 

1. قم بتشغيل وضع استكشاف الأخطاء وإصلاحها، وسجل الدخول إلى الجهاز. 

2. تشغيل موجه أوامر PowerShell غير مقيد. 

    - `Set-MpPreference -AttackSurfaceReductionRules_Ids D4F940AB-401B-4EFC-AADC-AD5F3C50688A -AttackSurfaceReductionRules_Actions Disabled` 

3. بعد تعطيل قاعدة ASR، تأكد من أن المكون الإضافي Microsoft Office يعمل الآن.

لمزيد من المعلومات، راجع [نظرة عامة على تقليل الأجزاء المعرضة للهجوم](overview-attack-surface-reduction.md). 

## <a name="scenario-5-domain-blocked-by-network-protection"></a>السيناريو 5: المجال المحظور بواسطة Network Protection

تقوم Network Protection بحظر مجال Microsoft، مما يمنع المستخدمين من الوصول إليه. 

1. قم بتشغيل وضع استكشاف الأخطاء وإصلاحها، وسجل الدخول إلى الجهاز. 

2. تشغيل موجه أوامر PowerShell غير مقيد. 

    - `Set-MpPreference -EnableNetworkProtection Disabled` 

3. بعد تعطيل Network Protection، تحقق لمعرفة ما إذا كان المجال مسموحا به الآن. 

لمزيد من المعلومات، راجع [استخدام حماية الشبكة للمساعدة في منع الاتصالات بالمواقع غير الصالحة](network-protection.md). 

## <a name="related-topics"></a>المواضيع ذات الصلة

- [تمكين وضع استكشاف الأخطاء وإصلاحها](enable-troubleshooting-mode.md)
- [حماية إعدادات الأمان باستخدام الحماية من العبث](prevent-changes-to-security-settings-with-tamper-protection.md)
- [Set-MpPreference](/powershell/module/defender/set-mppreference)
- [حماية الشبكة](network-protection.md)
- [نظرة عامة على تقليل الأجزاء المعرضة للهجوم](overview-attack-surface-reduction.md)
- [الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [الحصول على نظرة عامة على Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/)
- [معاً بشكل أفضل: برنامج الحماية من الفيروسات من Microsoft Defender Microsoft Defender لنقطة النهاية](why-use-microsoft-defender-antivirus.md)
