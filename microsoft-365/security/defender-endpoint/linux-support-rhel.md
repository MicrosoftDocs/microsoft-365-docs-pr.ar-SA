---
title: استكشاف مشاكل Microsoft Defender ل Endpoint على Linux RHEL6 وإصلاحها
ms.reviewer: ''
description: استكشاف مشاكل اتصال السحابة وإصلاحها ل Microsoft Defender لنقطة النهاية على Linux
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، السحابة، الاتصال، الاتصال
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 43a60d12883dc639c4ee5b831d305010cef58533
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63579951"
---
# <a name="troubleshoot-issues-for-microsoft-defender-for-endpoint-on-linux-rhel6"></a>استكشاف مشاكل Microsoft Defender ل Endpoint على Linux RHEL6 وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

توفر هذه المقالة إرشادات حول كيفية استكشاف المشاكل التي قد تواجهها مع Microsoft Defender for Linux وإصلاحها على Red Hat Linux 6 (RHEL 6) أو أعلى. 

بعد تثبيت الحزمة (mdatp_XXX.XX.XX.XX.x86_64.rpm)، اتخاذ الإجراءات التي تم توفيرها للتحقق من نجاح عملية التثبيت. 


## <a name="check-the-service-health"></a>التحقق من صحة الخدمة

استخدم الأمر التالي للتحقق من صحة الخدمة:

```bash
mdatp health 
```

## <a name="verify-that-the-service-is-running"></a>التحقق من تشغيل الخدمة

استخدم الأمر التالي للتحقق من تشغيل الخدمة:

```bash
service mdatp status 
```

الإخراج المتوقع: `mdatp start/running, process 4517`

## <a name="verify-the-distribution-and-kernel-version"></a>التحقق من التوزيع والإصدار kernel
يجب أن تكون إصدارات التوزيع وkernel في القائمة المعتمدة.

استخدم الأمر التالي للحصول على إصدار التوزيع:

```bash
cat /etc/redhat-release (or /etc/system-release) 
```

استخدم الأمر التالي للحصول على إصدار kernel:

```bash
uname -r
```
## <a name="check-if-mdatp-audisp-process-is-running"></a>التحقق مما إذا كانت عملية mdatp audisp قيد التشغيل 
الإخراج المتوقع هو أن العملية قيد التشغيل.

استخدم الأمر التالي للتحقق من:

```bash
pidof mdatp_audisp_plugin 
```

## <a name="check-talpa-modules"></a>التحقق من الوحدات النمطية ل TALPA
يجب أن يكون هناك تسع وحدات النمطية محملة. 

استخدم الأمر التالي للتحقق من:

```bash
lsmod | grep talpa
```

الإخراج المتوقع: تم التمكين

```bash
talpa_pedconnector       878  0 

talpa_pedevice          5189  2 talpa_pedconnector 

talpa_vfshook          32300  1 

talpa_vcdevice          4947  1 

talpa_syscall           9127  0 

talpa_core             90699  4 talpa_vfshook,talpa_vcdevice,talpa_syscall 

talpa_linux            29424  5 talpa_vfshook,talpa_vcdevice,talpa_syscall,talpa_core 

talpa_syscallhookprobe      882  0 

talpa_syscallhook      14987  2 talpa_vfshook,talpa_syscallhookprobe 
```


```bash
lsmod | grep talpa | wc -l 
```

الإخراج المتوقع: 9

## <a name="check-talpa-status"></a>التحقق من حالة TALPA

```bash
cat /proc/sys/talpa/interceptors/VFSHookInterceptor/status 
```

تصحيح ملفات سجل الأخطاء (بصرف النظر عن المجموعة "إنشاء تشخيص mdatp") 

```bash
/var/log/audit/audit.log 

/var/log/messages 

semanage fcontext -l > selinux.log 
```
 

الأداء والذاكرة 

```bash
top -p <wdavdaemon pid>      

pmap -x <wdavdaemon pid> 
```

أين `<wdavdaemon pid>` يمكن العثور عليه باستخدام `pidof wdavdaemon`.

