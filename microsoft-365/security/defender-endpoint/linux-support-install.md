---
title: استكشاف مشاكل تثبيت Microsoft Defender ل Endpoint على Linux وإصلاحها
ms.reviewer: ''
description: استكشاف مشاكل تثبيت Microsoft Defender ل Endpoint على Linux وإصلاحها
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، التثبيت
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a0b2a571be5f78818279a343d253709e05814908
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63573346"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-linux"></a>استكشاف مشاكل تثبيت Microsoft Defender ل Endpoint على Linux وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="verify-that-the-installation-succeeded"></a>التحقق من نجاح عملية التثبيت

قد ينتج عن خطأ في التثبيت أو لا ينتج عنه رسالة خطأ ذات معنى من قبل مدير الحزمة. للتحقق مما إذا نجح التثبيت، احصل على سجلات التثبيت وتحقق منها باستخدام:

```bash
 sudo journalctl --no-pager|grep 'microsoft-mdatp' > installation.log
```

```bash
 grep 'postinstall end' installation.log
```

```Output
 microsoft-mdatp-installer[102243]: postinstall end [2020-03-26 07:04:43OURCE +0000] 102216
```

يشير الإخراج من الأمر السابق مع التاريخ والوقت الصحيحين للثبيت إلى النجاح.

تحقق أيضا من [تكوين العميل](linux-install-manually.md#client-configuration) للتحقق من صحة المنتج والكشف عن الملف النصي EICAR.

## <a name="make-sure-you-have-the-correct-package"></a>تأكد من أن لديك الحزمة الصحيحة

تحقق من تطابق الحزمة التي تقوم بتثبيتها مع توزيع المضيف والإصدار.

<br>

****

|حزمة|توزيع|
|---|---|
|mdatp-rhel8. Linux.x86_64.rpm|Oracle و RHEL و CentOS 8.x|
|mdatp-sles12. Linux.x86_64.rpm|SUSE Linux Enterprise Server 12.x|
|mdatp-sles15. Linux.x86_64.rpm|SUSE Linux Enterprise Server 15.x|
|mdatp. Linux.x86_64.rpm|Oracle و RHEL و CentOS 7.x|
|mdatp. Linux.x86_64.deb|Debian وUbuntu 16.04 و18.04 و20.04|
|

للنشر [اليدوي](linux-install-manually.md)، تأكد من اختيار الإصدار والإصدار الصحيحين.

## <a name="installation-failed"></a>فشل التثبيت

تحقق مما إذا كانت خدمة Defender for Endpoint قيد التشغيل:

```bash
service mdatp status
```

```Output
 ● mdatp.service - Microsoft Defender for Endpoint
   Loaded: loaded (/lib/systemd/system/mdatp.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-03-26 10:37:30 IST; 23h ago
 Main PID: 1966 (wdavdaemon)
    Tasks: 105 (limit: 4915)
   CGroup: /system.slice/mdatp.service
           ├─1966 /opt/microsoft/mdatp/sbin/wdavdaemon
           ├─1967 /opt/microsoft/mdatp/sbin/wdavdaemon
           └─1968 /opt/microsoft/mdatp/sbin/wdavdaemon
 ```

## <a name="steps-to-troubleshoot-if-the-mdatp-service-isnt-running"></a>خطوات استكشاف الأخطاء وإصلاحها إذا لم تكن خدمة mdatp قيد التشغيل

1. تحقق مما إذا كان مستخدم "mdatp" موجودا:

    ```bash
    id "mdatp"
    ```

    إذا لم يكن هناك إخراج، ف

    ```bash
    sudo useradd --system --no-create-home --user-group --shell /usr/sbin/nologin mdatp
    ```

2. حاول تمكين الخدمة وإعادة تشغيلها باستخدام:

    ```bash
    sudo service mdatp start
    ```

    ```bash
    sudo service mdatp restart
    ```

3. إذا لم يتم العثور على mdatp.service عند تشغيل الأمر السابق، فقم بتشغيل:

    ```bash
    sudo cp /opt/microsoft/mdatp/conf/mdatp.service <systemd_path> 
    ```

    أين `<systemd_path>` هو لتوزيعات `/lib/systemd/system` Ubuntu وDbian و/usr/lib/systemd/system' لرهيل و CentOS و Oracle و SLES. ثم قم ب إعادة تشغيل الخطوة 2.

4. إذا لم تنجح الخطوات المذكورة أعلاه، فتحقق مما إذا كان SELinux مثبتا وفي وضع فرض التشغيل. إذا كان الأمر كذلك، فحاول تعيينه إلى وضع مستحسن أو وضع معطل. يمكن القيام بذلك من خلال تعيين `SELINUX` المعلمة إلى "مفجب" أو "معطل" `/etc/selinux/config` في الملف، متبوع إعادة التشغيل. تحقق من صفحة رجل من selinux للحصول على مزيد من التفاصيل.
حاول الآن إعادة تشغيل خدمة mdatp باستخدام الخطوة 2. يمكنك إعادة تغيير التكوين على الفور لأسباب تتعلق والأمان بعد تجربة ذلك ثم إعادة التشغيل.

5. إذا `/opt` كان الدليل هو ارتباط رمزي، ف قم بإنشاء مجموعة ربط ل `/opt/microsoft`.

6. تأكد من أن ال daemon لديها إذن قابل للتنفيذ.

    ```bash
    ls -l /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    ```Output
    -rwxr-xr-x 2 root root 15502160 Mar  3 04:47 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    إذا لم يكن للدهمة أذونات قابلة للتنفيذ، فجعلها قابلة للتنفيذ باستخدام:

    ```bash
    sudo chmod 0755 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    ثم إعادة محاولة تشغيل الخطوة 2.

7. تأكد من عدم تثبيت نظام الملفات الذي يحتوي على wdavdaemon ب "noexec".

## <a name="if-the-defender-for-endpoint-service-is-running-but-the-eicar-text-file-detection-doesnt-work"></a>إذا كانت خدمة Defender for Endpoint قيد التشغيل، ولكن الكشف عن ملف EICAR النصي لا يعمل

1. تحقق من نوع نظام الملفات باستخدام:

    ```bash
    findmnt -T <path_of_EICAR_file>
    ```

    يتم سرد أنظمة الملفات المعتمدة حاليا للنشاط عند الوصول [هنا](microsoft-defender-endpoint-linux.md#system-requirements). لن يتم فحص أي ملفات خارج أنظمة الملفات هذه.

## <a name="command-line-tool-mdatp-isnt-working"></a>أداة سطر الأوامر "mdatp" لا تعمل

1. إذا كان تشغيل أداة سطر الأوامر `mdatp` يعطي خطأ `command not found`، ف تشغيل الأمر التالي:

    ```bash
    sudo ln -sf /opt/microsoft/mdatp/sbin/wdavdaemonclient /usr/bin/mdatp
    ```

    وحاول مرة أخرى.

    إذا لم تساعدك أي من الخطوات المذكورة أعلاه، فجمع سجلات التشخيص:

    ```bash
    sudo mdatp diagnostic create
    ```

    ```Output
    Diagnostic file created: <path to file>
    ```

    سيتم عرض مسار ملف zip يحتوي على السجلات كمخرج. التواصل مع دعم العملاء باستخدام هذه السجلات.
