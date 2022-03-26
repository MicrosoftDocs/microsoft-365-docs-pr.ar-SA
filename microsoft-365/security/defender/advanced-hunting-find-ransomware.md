---
title: البحث عن برامج الفدية الضارة مع الصيد المتقدم
description: استخدم الصيد المتقدم لتحديد موقع الأجهزة التي قد تتأثر بفيروسات الفدية الضارة.
keywords: الصيد المتقدم، برامج الفدية الضارة، البحث عن التهديدات عبر الإنترنت، البحث، الاستعلام، بيانات Microsoft 365، Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-ransomware
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 79dee9b6750e21d9b2482d4a0482d87d7fc7434b
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/30/2021
ms.locfileid: "63571578"
---
# <a name="hunt-for-ransomware"></a>البحث عن برامج الفدية الضارة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

لقد تطور برنامج الفدية الضارة بسرعة من البرامج الضارة البسيطة التي تؤثر على مستخدمي الكمبيوتر الفرديين إلى خطر المؤسسة الذي يؤثر بشكل كبير على الصناعات والمؤسسات الحكومية. في [Microsoft 365 Defender](microsoft-365-defender.md) توفر هذه Microsoft 365 Defender العديد من الإمكانات التي تكشف عن برامج الفدية الضارة وأنشطة التسلل المرتبطة بها وحظرها، فإن إجراء عمليات فحص استباقية للكشف عن علامات اختراق قد يساعد على الحفاظ على حماية الشبكة.

> [اقرأ حول برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

باستخدام [البحث المتقدم في](advanced-hunting-overview.md) Microsoft 365 Defender، يمكنك إنشاء استعلامات لتحديد موقع التحف الفردية المقترنة بنشاط برامج الفدية الضارة. يمكنك أيضا تشغيل استعلامات أكثر تعقيدا يمكنها البحث عن علامات النشاط وتوازن هذه العلامات للعثور على الأجهزة التي تتطلب انتباها فوريا.

## <a name="signs-of-ransomware-activity"></a>علامات نشاط برامج الفدية الضارة
لاحظ الباحثون في مجال الأمان في Microsoft العديد من عمليات التحف الشائعة والمتقنة في العديد من حملات برامج الفدية الضارة التي أطلقها متطفلون متطورون. تشتمل هذه العلامات في معظمها على استخدام أدوات النظام للتحضير للتشفير ومنع الكشف ومسح الأدلة الجنائية.

| نشاط برامج الفدية الضارة | الأدوات الشائعة | الهدف |
|--|--|--|
| إيقاف العمليات | _taskkill.exe_، _و net stop_ | تأكد من أن الملفات المستهدفة للتشفير غير مؤمنة بواسطة تطبيقات مختلفة. |
| إيقاف تشغيل الخدمات | _sc.exe_ | - تأكد من عدم تأمين الملفات المستهدفة للتشفير بواسطة تطبيقات مختلفة.<br>- منع برامج الأمان من تعطيل التشفير وغيرها من أنشطة برامج الفدية الضارة.<br>- منع برنامج النسخ الاحتياطي من إنشاء نسخ قابلة لاستردادها.  |
| حذف السجلات والملفات | _cipher.exe_، _wevtutil_، _fsutil.exe_ | إزالة أدلة التحليل الطبي الشرعي. |
| حذف نسخ الظل  | _vsadmin.exe_، _wmic.exe_ | قم بإزالة نسخ ظل محرك الأقراص التي يمكن استخدامها لاسترداد الملفات المشفرة. |
| حذف النسخ الاحتياطية أو إيقافها | _wbadmin.exe_ | احذف النسخ الاحتياطية الموجودة وأوقف مهام النسخ الاحتياطي المجدولة، مما يمنع الاسترداد بعد التشفير. |
| تعديل إعدادات التشغيل | _bcdedit.exe_ | إيقاف تشغيل التحذيرات والإصلاحات التلقائية بعد حالات فشل التشغيل التي يمكن أن تسببها عملية التشفير. |
| إيقاف تشغيل أدوات الاسترداد | _schtasks.exe_، _regedit.exe_، | إيقاف تشغيل استعادة النظام وخيارات استرداد النظام الأخرى. |

## <a name="check-for-individual-signs-of-ransomware-activity"></a>التحقق من وجود علامات فردية لنشاط برامج الفدية الضارة
يمكن أن تكون العديد من الأنشطة التي تشكل سلوك برامج الفدية الضارة، بما في ذلك الأنشطة الموضحة في المقطع السابق، أنشطة غير مهينة. عند استخدام الاستعلامات التالية لتحديد موقع برامج الفدية الضارة، قم بتشغيل أكثر من استعلام واحد للتحقق مما إذا كانت الأجهزة نفسها تعرض علامات مختلفة لنشاط برامج الفدية الضارة المحتملة.

### <a name="stopping-multiple-processes-using-_taskkillexe_"></a>إيقاف عمليات متعددة _باستخدام_ taskkill.exe
يتحقق هذا الاستعلام من محاولات إيقاف 10 عمليات منفصلة على الأقل _باستخدام الأداةtaskkill.exe_ المساعدة. [تشغيل الاستعلام](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RS2vCUBCFz7rgfwiuIkit3eumVSgtpYvuS9SLDTY2eLUvxN_eb8YHKlFkyNzJzDkn505aailRX7mmGlFlmhNBhUrOSGeuT3L0s6QqNaMagolEcMyCbApjx2e8TYhcH8Q1mB-emq50z_lF39gvBzo9-gEF-6Yhlyh9653ejCfRK6zCsaZfuJOu-x2jkqqN-0Yls-8-gp6dZ52OVuT6Sad1plulyN0KIkMt15_zt7zHDe8OBwv3btoJToa7Tnp0T8Ou9WzfT761gPOm3_FQ16Zxp2qcCdg33_rlyokG-iXv7_4BRNMnhkortmvTW6rqnZ7bgP2Vtm70D3d9wcFaAgAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using taskkill.exe
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10
```
  
### <a name="stopping-processes-using-_net-stop_"></a>إيقاف العمليات باستخدام _net stop_
يتحقق هذا الاستعلام من محاولات إيقاف 10 عمليات منفصلة على الأقل باستخدام أمر _التوقف_ الصافي. [تشغيل الاستعلام](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RQUvDUBCE5yz0P4ScUijWereXVkGQIti7aA1pqakhL7VVxN_ebzc1NBChPLJv2Z2ZN5sdaqhId1ppozeyF1WcVLkK7kCl0gcx-F2QFSrJFmACJ3XMlmgKGfmGWnXC6OlCU2qfIIz12OLfUk_h2FuG_IG505JayRdpDit3bIW33B2M3WeGSqIRrvudTJvpnWzmPKvc6JcYHx1eEvd8savV07e9TchzTt198AlNZ0kluNLfjHHjIPAvak4J_tvx9XtPR6ypbn1icxShvGgqyVkO-hrAm7VUrRcaTWOs6T_7hs7XjfSqL-Lpvu5BDLxjqKRjI9a9Juvew__T2x5HutIB3T1qt4QCAAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using net stop
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10
```
### <a name="deletion-of-data-on-multiple-drives-using-_cipherexe_"></a>حذف البيانات على محركات أقراص _متعددة باستخدامcipher.exe_
يتحقق هذا الاستعلام من محاولات حذف البيانات على محركات أقراص متعددة _باستخدامcipher.exe_. يتم هذا النشاط عادة بواسطة برامج الفدية الضارة لمنع استرداد البيانات بعد التشفير. [تشغيل الاستعلام](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI1SXUvDQBCcZ8H_cOQpgWLoD7AvVUEo4oPvElO1pblUcmn9QPztzk6TEuEsIdzdZndndm73cuRwWGDLb0PrhWfDs8Qab1jhmX8X3D-4HJbcK66W0Rqv8hT8K4RsiPW0PHbMasVQdbiGf3vaAec4wxWtPT0lz3vhSsUCrpVVE33I_Cb6vdNhTA9EeeVaVc8KDjOugmq2SDFlrSyKvCHS1NwJZ55L_HBPondNGDGWXP2JdyMnv927UnXHWwf6l4MunupXTOPfXszVT8_smriFOCxrRU-QclOQDLgCNRwQ1u8vZc8H2o1xp-7a7U1NefSko6pnmKjakNVi4chpiA39j-rGeF6HJ3xyH76NW2ZMFLGsNDJ9i05pZSPmVdDfq-jncfqtOuU5zSuQz6Zq92w7Hfbm-9cUm-d_vZ9J9S81O2KIfAMAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for cipher.exe deleting data from multiple drives
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine),
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1
```

### <a name="clearing-of-forensic-evidence-from-event-logs-using-_wevtutil_"></a>مسح الأدلة الجنائية من سجلات الأحداث _باستخدام wevtutil_
يتحقق هذا الاستعلام من محاولات مسح ما لا يقل عن 10 إدخالات سجلات من سجلات الأحداث _باستخدام wevtutil_. [تشغيل الاستعلام](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWRTU_CQBCG37OJ_2HDqSQkwMGjXgoHEg4cUI-m2hUaqGu6BaPxx_vsEFCTxmA225nOvB_tzFBDOc0VOBuyZ2JD3CnKEwMVpzfyPbVWlba8t9Sdnsi9CsPXdLfWf7Wq4xm0QuVSF5oYv4LhtQAfLIucKXWvF5gH5Ke5rak1prKEVRu2xalG3emGW6AdlGmsUv1O5m-fnLzmFHiV_G9FTKg1lUjs6Z5vucPvljsD0TOXhP6_Vm7841dFZnPAN2A_DDu36eSnCSbNnc3B6Zpb4nasZGf59zWA963orZdcEiKelBNvQ_fBNny-utOj3nn-3OUMxMA6CZV1bCt1r8i6d_TXFNKWxxrpC48hm8miAgAA&runQuery=true&timeRangeId=week)

```kusto
// Look for use of wevtutil to clear multiple logs
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10
```

### <a name="turning-off-services-using-_scexe_"></a>إيقاف تشغيل _الخدمات باستخدامsc.exe_
يتحقق هذا الاستعلام من محاولات إيقاف تشغيل 10 خدمات موجودة على الأقل _باستخدام_ sc.exe. [تشغيل الاستعلام](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAKWST2vCQBDF31nodwg5RZCqhx7bi3ooeCjovaQxraIxxfU_fvj-ZoiiEIqlhM3Ozrz3ZnZm22or0lAl3xzrk33FHpTpUbn2rEgTzfCk-tACa6kvR-Qgt5wzrKAHNdTHOnveiJZVLGiAP4e5rpAnFHaauoZlGMMqHLsmT6FvfC-slFylEnWpoVnLvM3Twy74UnJNuJdVa6gpnsAe-81iVzbE3_kZiCV9mlHZf3Sue5pzii-3C9pU3BWYo_NGKPdvGJZh4x2N9Owzyi6e5K5qmmrVKg_9dNY11hzvu0_8fu0ItQP_6zfxCqLlEUMlNVO36BNW_ax_74K9l646-gFts39I1AIAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for sc.exe disabling services
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10
```

### <a name="turning-off-system-restore"></a>إيقاف تشغيل استعادة النظام
يحدد هذا الاستعلام محاولات إيقاف استعادة النظام ومنع النظام من إنشاء نقاط استعادة، والتي يمكن استخدامها لاسترداد البيانات المشفرة بواسطة برامج الفدية الضارة. [تشغيل الاستعلام](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAK2S3UrDQBCFz7XgO6y9id4o6HWvrIVCkaJPENOYFNumZGO1ID673w4xJA1isbJMZnZ-zpzM7EiptlooQc9UqjDLc-7wp1qrwj7Via44MzK35FTotTI5PXMr0aVe8cy15NzoGo-zqg_0m3KQSsRpQtbC6uMGpdt3jHeJfU_GymqG-uQb9XpcEn1HIuvmGpZT0Aq99Dim4G3ousNO8K04sSE6EEN22kL6jvzO-LaDNW2QzqxLmGBsPo9vUMt_oA8Na3DQv3vwcmPiifpmds48jkhut8T2FLikxm_T4bI_m_6uQt-wrXO28lPPSBcdziOqPFlP9RYy47tDKtuZM07hVtSvaJ_HYRPL63-NyMgtmtWv5684jy2WDx2O0ZEM562ZBLQvURxur6gDAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
//Pivoting for rundll32  
| where InitiatingProcessFileName =~ 'rundll32.exe'   
//Looking for empty command line   
and InitiatingProcessCommandLine !contains " " and InitiatingProcessCommandLine != ""  
//Looking for schtasks.exe as the created process  
and FileName in~ ('schtasks.exe')  
//Disabling system restore   
and ProcessCommandLine has 'Change' and ProcessCommandLine has 'SystemRestore' 
and ProcessCommandLine has 'disable'
```

### <a name="backup-deletion"></a>حذف النسخة الاحتياطية
يحدد هذا الاستعلام استخدام _wmic.exeلحذف_ لقطات النسخ الظلية قبل التشفير. [تشغيل الاستعلام](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWS2wqCQBCG_-ugd5CupTfoqgMIEV70AqFLGp5QyYLo2fsavEjxwlhWZ7-df2Z2dndyuitVxD9UrdKshrGHOxVqsZda6CVPnRJYzfR0QJVhnXRRbmSjN98VXrlFXEMfzNWkfphti50zLmSMdURfmFcCaSxqY3aMX4eqVKUn1OsV_8eLWX_rbwcVVhblBovY8bT76U-AxoedWeeWp7WzV0YDMqSQFNZavuuopnHH_Iku-lbJnLPMyxnYDTp4bZ5P9M5uNpsZIWSn7l_CuNoPSggb4z4CAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
| where FileName =~ "wmic.exe"
| where ProcessCommandLine has "shadowcopy" and ProcessCommandLine has "delete"
| project DeviceId, Timestamp, InitiatingProcessFileName, FileName,
ProcessCommandLine, InitiatingProcessIntegrityLevel, InitiatingProcessParentFileName
```

## <a name="check-for-multiple-signs-of-ransomware-activity"></a>التحقق من وجود علامات متعددة لنشاط برامج الفدية الضارة
بدلا من تشغيل عدة استعلامات بشكل منفصل، يمكنك أيضا استخدام استعلام شامل يتحقق من وجود علامات متعددة لنشاط برامج الفدية الضارة لتحديد الأجهزة المتأثرة. الاستعلام المجمع التالي:
- البحث عن علامات ملموسة وخفية نسبيا لنشاط برامج الفدية الضارة
- تقييم وجود هذه العلامات
- تحديد الأجهزة ذات فرص أكبر في أن تكون أهداف برامج الفدية الضارة 

عند التشغيل، يرجع هذا الاستعلام المجمع قائمة بالأجهزة التي تعرض علامات هجوم متعددة. يتم أيضا عرض عدد كل نوع من أنواع أنشطة برامج الفدية الضارة. لتشغيل هذا الاستعلام المجمع، انسخه مباشرة إلى [محرر استعلام البحث المتقدم](https://security.microsoft.com/advanced-hunting). 

```kusto
// Find attempts to stop processes using taskkill.exe
let taskKill = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10;
// Find attempts to stop processes using net stop
let netStop = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10;
// Look for cipher.exe deleting data from multiple drives
let cipher = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine), 
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1;
// Look for use of wevtutil to clear multiple logs
let wevtutilClear = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10;
// Look for sc.exe disabling services
let scDisable = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10;
// Main query for counting and aggregating evidence
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "vssadmin.exe" and ProcessCommandLine has_any("list shadows", "delete shadows")
or FileName =~ "fsutil.exe" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal"
or ProcessCommandLine has("bcdedit") and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures")
or ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup")
or (ProcessCommandLine has "wevtutil" and ProcessCommandLine has "cl") 
or (ProcessCommandLine has "wmic" and ProcessCommandLine has "shadowcopy delete")
or (ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled")
| extend Bcdedit = iff(ProcessCommandLine has "bcdedit" and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures"), 1, 0)
| extend ShadowCopyDelete = iff (ProcessCommandLine has "shadowcopy delete", 1, 0)
| extend VssAdminShadows = iff(ProcessCommandLine has "vssadmin" and ProcessCommandLine has_any("list shadows", "delete shadows"), 1, 0)
| extend Wbadmin = iff(ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup"), 1,0)
| extend Fsutil = iff(ProcessCommandLine has "fsutil" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal", 1, 0)
| summarize FirstActivity = min(Timestamp), ReportId = any(ReportId), Commands = make_set(ProcessCommandLine) by DeviceId, Fsutil, Wbadmin, ShadowCopyDelete, Bcdedit, VssAdminShadows, bin(Timestamp, 6h)
// Joining extra evidence
| join kind=leftouter (wevtutilClear) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (cipher) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (netStop) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (taskKill) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (scDisable) on $left.DeviceId == $right.DeviceId
| extend WevtutilUse = iff(LogClearCount > 10, 1, 0)
| extend CipherUse = iff(CipherCount > 1, 1, 0)
| extend NetStopUse = iff(netStopCount > 10, 1, 0)
| extend TaskkillUse = iff(taskKillCount > 10, 1, 0)
| extend ScDisableUse = iff(ScDisableCount > 10, 1, 0)
// Adding up all evidence
| mv-expand CommandList = NetStopList, TaskKillList, ClearedLogList, CipherList, Commands, ScDisableList
// Format results
| summarize BcdEdit = iff(make_set(Bcdedit) contains "1" , 1, 0), NetStop10PlusCommands = iff(make_set(NetStopUse) contains "1", 1, 0), Wevtutil10PlusLogsCleared = iff(make_set(WevtutilUse) contains "1", 1, 0),
CipherMultipleDrives = iff(make_set(CipherUse) contains "1", 1, 0), Fsutil = iff(make_set(Fsutil) contains "1", 1, 0), ShadowCopyDelete = iff(make_set(ShadowCopyDelete) contains "1", 1, 0),
Wbadmin = iff(make_set(Wbadmin) contains "1", 1, 0), TaskKill10PlusCommand = iff(make_set(TaskkillUse) contains "1", 1, 0), VssAdminShadow = iff(make_set(VssAdminShadows) contains "1", 1, 0), 
ScDisable = iff(make_set(ScDisableUse) contains "1", 1, 0), TotalEvidenceCount = count(CommandList), EvidenceList = make_set(Commands), StartofBehavior = min(FirstActivity) by DeviceId, bin(Timestamp, 1d)
| extend UniqueEvidenceCount = BcdEdit + NetStop10PlusCommands + Wevtutil10PlusLogsCleared + CipherMultipleDrives + Wbadmin + Fsutil + TaskKill10PlusCommand + VssAdminShadow + ScDisable + ShadowCopyDelete
| where UniqueEvidenceCount > 2
```
### <a name="understand-and-tweak-the-query-results"></a>فهم نتائج الاستعلام وتعديلها
يرجع الاستعلام المجمع النتائج التالية:

- **DeviceId** —يحدد الجهاز المتأثر 
- **TimeStamp** —للمرة الأولى التي يتم فيها ملاحظة أي علامة لنشاط برامج الفدية الضارة على الجهاز
- **علامات معينة للنشاط**— العدد لكل علامة تظهر في أعمدة متعددة، مثل _BcdEdit_ أو _FsUtil_
- **TotalEvidenceCount** —عدد العلامات التي تم ملاحظتها
- **UniqueEvidenceCount** —عدد أنواع العلامات التي تم ملاحظتها

:::image type="content" source="../../media/advanced-hunting-ransomware-query.png" alt-text="مثال لاستعلام مدمج لنشاط برامج الفدية الضارة في مدخل Microsoft 365 Defender":::

*تظهر نتائج الاستعلام الأجهزة المتأثرة وعدد مختلف علامات نشاط برامج الفدية الضارة*

بشكل افتراضي، تسرد نتيجة الاستعلام الأجهزة التي لديها أكثر من نوعين من أنشطة برامج الفدية الضارة فقط. لرؤية جميع الأجهزة التي بها أي علامة لنشاط برامج الفدية الضارة، قم بتعديل `where` عامل التشغيل التالي ثم قم بتعيين الرقم إلى صفر (0). لرؤية عدد أقل من الأجهزة، قم بتعيين رقم أعلى. 

```kusto
| where UniqueEvidenceCount > 2
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)

## <a name="additional-ransomware-resources"></a>موارد برامج الفدية الضارة الإضافية

المعلومات الأساسية من Microsoft:

- [التهديدات المتزايدة التي تشكلها برامج الفدية الضارة](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/)، نشر مدونة Microsoft حول المشاكل في 20 يوليو 2021
- [برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان](/security/compass/human-operated-ransomware)
- [الحماية السريعة من برامج الفدية الضارة وافيروسات الفدية الضارة](/security/compass/protect-against-ransomware)
- [تقرير الدفاع الرقمي ل Microsoft 2021](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (راجع الصفحات من 10 إلى 19)
- [برامج الفدية الضارة: تقرير](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) تحليل التهديدات المستمرة والمستمرة في مدخل Microsoft 365 Defender

Microsoft 365:

- [نشر الحماية من برامج الفدية الضارة لمستأجر Microsoft 365 الخاص بك](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [زيادة مرونة برامج الفدية الضارة باستخدام Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [الاستعادة من هجوم برامج الفدية الضارة](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [الحماية من البرامج الضارة وفيروسات الفدية الضارة](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [حماية الكمبيوتر الشخصي Windows من برامج الفدية الضارة](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [التعامل مع برامج الفدية الضارة في SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [تقارير تحليلات المخاطر الخاصة بفيروسات الفدية](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) الضارة في مدخل Microsoft 365 Defender

Microsoft Azure:

- [هجوم Azure Defenses for Ransomware](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [زيادة مرونة برامج الفدية الضارة باستخدام Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [خطة النسخ الاحتياطي والاستعادة للحماية من برامج الفدية الضارة](/security/compass/backup-plan-to-protect-against-ransomware)
- [المساعدة في الحماية من برامج الفدية الضارة باستخدام Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (فيديو لمدة 26 دقيقة)
- [الاستعادة من اختراق الهوية المهينة](/azure/security/fundamentals/recover-from-identity-compromise)
- [الكشف المتقدم عن الهجمات متعددة الكواليس في Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [الكشف عن الفدية الضارة في Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender لتطبيقات السحابة:

-  [إنشاء سياسات الكشف عن الشذوذ في Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

منشورات مدونة فريق أمان Microsoft:

- [3 خطوات لمنع برامج الفدية الضارة واستردادها (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [دليل لمكافحة برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: الجزء 1 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  الخطوات الأساسية حول كيفية إدارة فريق الكشف والاستجابة (DART) من Microsoft لإجراء عمليات التحقيق في أحداث برامج الفدية الضارة.

- [دليل لمكافحة برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: الجزء 2 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  التوصيات وأفضل الممارسات.

- [أن تصبح مرنا من خلال فهم مخاطر الأمن الإلكتروني: الجزء 4 — التنقل عبر التهديدات الحالية (مايو 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  راجع قسم **برامج الفدية** الضارة.

- [هجمات برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: كارثة يمكن تفاديها (مارس 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  يتضمن تحليلات سلسلة الهجمات للهجمات الفعلية.

- [استجابة برامج الفدية الضارة - للدفع أو عدم الدفع؟ (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [تستجيب Norsk Hydro لهجمات برامج الفدية الضارة بشفافية (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
