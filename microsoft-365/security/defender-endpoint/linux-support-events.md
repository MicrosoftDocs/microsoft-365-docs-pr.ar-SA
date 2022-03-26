---
title: استكشاف مشاكل التنبيهات أو الأحداث المفقودة وإصلاحها ل Microsoft Defender for Endpoint على Linux
description: استكشاف الأخطاء المتعلقة بالأحداث أو التنبيهات المفقودة في Microsoft Defender for Endpoint على Linux وإصلاحها.
keywords: microsoft، defender، Microsoft Defender for Endpoint، linux، الأحداث
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5a17f94e3d26c08c0f6e0ca358778a65189cf6a5
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63570465"
---
# <a name="troubleshoot-missing-events-or-alerts-issues-for-microsoft-defender-for-endpoint-on-linux"></a>استكشاف مشاكل التنبيهات أو الأحداث المفقودة وإصلاحها ل Microsoft Defender for Endpoint على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender ل Endpoint على Linux](microsoft-defender-endpoint-linux.md)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

توفر هذه المقالة بعض الخطوات العامة للحد من الأحداث أو التنبيهات المفقودة <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">في Microsoft 365 Defender المدخل</a>.

بمجرد **تثبيت Microsoft Defender لنقطة** النهاية بشكل صحيح على جهاز، سيتم إنشاء صفحة جهاز  في المدخل. يمكنك مراجعة كل الأحداث المسجلة في علامة تبويب المخطط الزمني في صفحة الجهاز أو في صفحة الصيد المتقدمة. يشوه هذا القسم حالة بعض الأحداث المتوقعة أو كلها مفقودة.
على سبيل المثال، إذا كانت _كل أحداث CreatedFile_ مفقودة.

## <a name="missing-network-and-login-events"></a>أحداث تسجيل الدخول والشبكات المفقودة

يستخدم Microsoft Defender ل Endpoint إطار عمل `audit` من linux لتعقب نشاط الشبكة وتسجيل الدخول.

1. تأكد من عمل إطار عمل التدقيق.

    ```bash
    service auditd status
    ```

    الإخراج المتوقع:

    ```output
    ● auditd.service - Security Auditing Service
    Loaded: loaded (/usr/lib/systemd/system/auditd.service; enabled; vendor preset: enabled)
    Active: active (running) since Mon 2020-12-21 10:48:02 IST; 2 weeks 0 days ago
        Docs: man:auditd(8)
            https://github.com/linux-audit/audit-documentation
    Process: 16689 ExecStartPost=/sbin/augenrules --load (code=exited, status=1/FAILURE)
    Process: 16665 ExecStart=/sbin/auditd (code=exited, status=0/SUCCESS)
    Main PID: 16666 (auditd)
        Tasks: 25
    CGroup: /system.slice/auditd.service
            ├─16666 /sbin/auditd
            ├─16668 /sbin/audispd
            ├─16670 /usr/sbin/sedispatch
            └─16671 /opt/microsoft/mdatp/sbin/mdatp_audisp_plugin -d
    ```

2. إذا `auditd` تم وضع علامة كتوقف، فابدأه.

    ```bash
    service auditd start
    ```

**في أنظمة SLES** ، قد يكون تدقيق SYSCALL `auditd` في معطلا بشكل افتراضي ويمكن حسابه للأحداث المفقودة.

1. للتحقق من عدم تعطيل تدقيق SYSCALL، سرد قواعد التدقيق الحالية:

    ```bash
    sudo auditctl -l
    ```

    إذا كان السطر التالي موجودا، ف قم بإزالته أو تحريره لتمكين Microsoft Defender ل Endpoint من تعقب عناوين SYSCAL معينة.

    ```output
    -a task, never
    ```

    توجد قواعد التدقيق في `/etc/audit/rules.d/audit.rules`.

## <a name="missing-file-events"></a>أحداث الملفات المفقودة

يتم تجميع أحداث الملفات مع إطار `fanotify` عمل. في حالة فقدان بعض `fanotify` أحداث الملفات أو كلها، تأكد من تمكينه على الجهاز ومن دعم نظام [الملفات](microsoft-defender-endpoint-linux.md#system-requirements).

سرد ملفات الأنظمة على الجهاز ب:

```bash
df -Th
```
