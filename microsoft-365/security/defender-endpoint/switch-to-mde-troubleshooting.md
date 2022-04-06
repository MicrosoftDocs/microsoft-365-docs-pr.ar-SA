---
title: استكشاف الأخطاء وإصلاحها عند التبديل إلى Microsoft Defender لنقطة النهاية
description: تعرف على كيفية استكشاف المشاكل وإصلاحها عند التبديل إلى Microsoft Defender لنقطة النهاية.
keywords: الترحيل، windows defender، حماية نقاط النهاية المتقدمة، الحماية من الفيروسات، الحماية من البرامج الضارة، الوضع السلبي، الوضع النشط، استكشاف الأخطاء وإصلاحها
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 03/28/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 30218ea9b3b5ecbec20fdbc3364546d25c80bcab
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507503"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>استكشاف الأخطاء وإصلاحها عند التبديل إلى Microsoft Defender لنقطة النهاية

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

توفر هذه المقالة معلومات حول استكشاف الأخطاء وإصلاحها لمسؤولي الأمان الذين يعانون من مشاكل عند التبديل من حل حماية نقطة نهاية غير Microsoft إلى حل Microsoft Defender لنقطة النهاية.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>برنامج الحماية من الفيروسات من Microsoft Defender يتم إلغاء تثبيته على Windows Server

عندما تقوم بالتبديل إلى Defender for Endpoint، تبدأ بحماية برامج الحماية من الفيروسات/البرامج الضارة غير من Microsoft في الوضع النشط. كجزء من عملية الإعداد، يمكنك تكوين برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. في بعض الأحيان، قد يمنع حل مكافحة الفيروسات/مكافحة البرامج الضارة غير التابع ل Microsoft برنامج الحماية من الفيروسات من Microsoft Defender تشغيل على Windows Server. في الواقع، قد يبدو برنامج الحماية من الفيروسات من Microsoft Defender تمت إزالته من Windows Server.

لحل هذه المشكلة، اتبع الخطوات التالية:

1. [قم بتعيين مفتاح التسجيل DisableAntiSpyware إلى false](#set-the-disableantispyware-registry-key-to-false).
2. [أضف Microsoft Defender لنقطة النهاية إلى قائمة الاستثناء](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
3. [تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي يدويا](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="set-the-disableantispyware-registry-key-to-false"></a>تعيين مفتاح تسجيل DisableAntiSpyware إلى خطأ

تم [استخدام مفتاح تسجيل DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) في الماضي لتعطيل برنامج الحماية من الفيروسات من Microsoft Defender، ونشر منتج آخر من برامج الحماية من الفيروسات، مثل McAfee أو Symantec أو غيرها. **بشكل عام**`DisableAntiSpyware`، يجب ألا يكون لديك مفتاح التسجيل هذا على أجهزة Windows ونقاط النهاية؛ ومع ذلك، إذا قمت بتكوينها، فيما يلي كيفية تعيين قيمتها إلى خطأ:

1. على جهاز Windows، افتح محرر السجل.

2. انتقل إلى `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. في هذا المجلد، ابحث عن إدخال DWORD يسمى **DisableAntiSpyware**.
   - إذا لم تشاهد هذا الإدخال، تكون قد تم تعيينه.
   - إذا رأيت **DisableAntiSpyware**، فاتابع إلى الخطوة 4.

4. انقر ب الماوس الأيمن فوق DisableAntiSpyware DWORD، ثم اختر **تعديل**.

5. قم بتعيين القيمة إلى `0`. (يحدد هذا الإجراء قيمة مفتاح التسجيل إلى *خطأ*.)

> [!TIP]
> لمعرفة المزيد حول مفتاح التسجيل هذا، راجع [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>إضافة Microsoft Defender لنقطة النهاية إلى قائمة الاستثناء

يجب تعريف بعض الاستثناءات ل Defender لنقطة النهاية في حل الحماية الحالي غير الخاص بنقطة نهاية Microsoft. تأكد من إضافة الاستثناءات التالية:

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي يدويا

على Windows Server 2019 أو Windows Server أو الإصدار 1803 أو الأحدث أو Windows Server 2016 أو Windows Server 2012 R2، يجب تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي يدويا. يساعد هذا الإجراء على منع حدوث مشاكل بسبب تثبيت منتجات الحماية من الفيروسات المتعددة على خادم. يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي باستخدام PowerShell أو نهج المجموعة أو مفتاح تسجيل.

يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي عن طريق تعيين مفتاح التسجيل التالي:

المسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

الاسم: `ForceDefenderPassiveMode`

اكتب: `REG_DWORD`

القيمة: `1`

> [!NOTE]
> لكي يعمل الوضع السلبي على نقاط النهاية التي تعمل Windows Server 2016 و Windows Server 2012 R2، يجب أن يتم تشغيل نقاط النهاية هذه باستخدام الإرشادات الموجودة في خوادم Windows[.](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016)

لمزيد من المعلومات، راجع برنامج الحماية من الفيروسات من Microsoft Defender [على Windows Server](microsoft-defender-antivirus-on-windows-server.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>برنامج الحماية من الفيروسات من Microsoft Defender تبدو عالقة في الوضع غير النشط

إذا برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، ف قم بتعيينه إلى الوضع النشط يدويا باتباع الخطوات التالية:

1. على جهاز Windows، افتح "محرر السجل" كمسؤول.

2. انتقل إلى `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

3. قم بتعيين أو **تعريف REG_DWORD** يسمى `ForceDefenderPassiveMode`، ثم قم بتعيين قيمته إلى `0`.

4. إعادة تشغيل الجهاز.

> [!IMPORTANT]
> إذا كنت لا تزال تواجه مشكلة في برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع النشط بعد اتباع هذا الإجراء، [فاتصل بالدعم](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>أواجه مشكلة في إعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016

إذا كنت تستخدم حلا غير Microsoft antivirus/antimalware على Windows Server 2016، فقد يتطلب الحل الحالي برنامج الحماية من الفيروسات من Microsoft Defender تعطيل أو إلغاء تثبيته. يمكنك استخدام الأداة المساعدة Command-Line[ الحماية](command-line-arguments-microsoft-defender-antivirus.md) من البرامج الضارة لإعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016.

1. كمسؤول محلي على الخادم، افتح موجه الأوامر.

2. تشغيل الأمر التالي: `MpCmdRun.exe -wdenable`

3. أعد تشغيل الجهاز.

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender التوافق مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md)

- [أدوات وأساليب التكوين للأجهزة Windows في Defender for Endpoint](configure-endpoints.md) 
