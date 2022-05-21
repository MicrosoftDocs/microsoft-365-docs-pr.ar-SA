---
title: استكشاف المشكلات وإصلاحها عند التبديل إلى Microsoft Defender لنقطة النهاية
description: تعرف على كيفية استكشاف المشكلات وإصلاحها عند التبديل إلى Microsoft Defender لنقطة النهاية.
keywords: الترحيل، windows defender، حماية متقدمة لنقطة النهاية، مكافحة الفيروسات، مكافحة البرامج الضارة، الوضع السلبي، الوضع النشط، استكشاف الأخطاء وإصلاحها
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
ms.date: 05/20/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 9a1a95c927c4f659510c587d2bbc81ad4b9c1264
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621646"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>استكشاف المشكلات وإصلاحها عند التبديل إلى Microsoft Defender لنقطة النهاية

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

توفر هذه المقالة معلومات استكشاف الأخطاء وإصلاحها لمسؤولي الأمان الذين يواجهون مشاكل عند التبديل من حل حماية نقطة النهاية غير التابع ل Microsoft إلى Microsoft Defender لنقطة النهاية.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>يتم إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows

عند التبديل إلى Defender لنقطة النهاية، تبدأ بالحماية من الفيروسات/الحماية من البرامج الضارة غير التابعة ل Microsoft في الوضع النشط. كجزء من عملية الإعداد، يمكنك تكوين برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. في بعض الأحيان، قد يمنع حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft برنامج الحماية من الفيروسات من Microsoft Defender من العمل على Windows Server. في الواقع، يمكن أن يبدو وكأنه تمت إزالة برنامج الحماية من الفيروسات من Microsoft Defender من Windows Server.

لحل هذه المشكلة، اتبع الخطوات التالية:

1. [إضافة Microsoft Defender لنقطة النهاية إلى قائمة الاستبعاد](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
2. [تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي يدويا](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>إضافة Microsoft Defender لنقطة النهاية إلى قائمة الاستبعاد

يجب تعريف بعض الاستثناءات ل Defender لنقطة النهاية في حل حماية نقطة النهاية غير التابعة ل Microsoft. تأكد من إضافة الاستثناءات التالية:

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي يدويا

في Windows Server 2019 أو Windows Server أو الإصدار 1803 أو أحدث أو Windows Server 2016 أو Windows Server 2012 R2، يجب تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع الخامل يدويا. يساعد هذا الإجراء على منع المشاكل الناتجة عن تثبيت منتجات الحماية من الفيروسات المتعددة على خادم. يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي باستخدام PowerShell أو نهج المجموعة أو مفتاح التسجيل.

يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي عن طريق تعيين مفتاح التسجيل التالي:

مسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

الاسم: `ForceDefenderPassiveMode`

نوع: `REG_DWORD`

قيمه: `1`

> [!NOTE]
> لكي يعمل الوضع السلبي على نقاط النهاية التي تعمل Windows Server 2016 وخادم Windows 2012 R2، يجب إلحاق نقاط النهاية هذه باستخدام الإرشادات الموجودة في [خوادم Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

لمزيد من المعلومات، راجع [برنامج الحماية من الفيروسات من Microsoft Defender في Windows](microsoft-defender-antivirus-windows.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>يبدو أن برنامج الحماية من الفيروسات من Microsoft Defender عالق في الوضع السلبي

إذا كانت برنامج الحماية من الفيروسات من Microsoft Defender عالقة في الوضع السلبي، فقم بتعيينها إلى الوضع النشط يدويا باتباع الخطوات التالية:

1. على جهازك Windows، افتح "محرر السجل" كمسؤول.

2. الانتقال إل `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

3. تعيين إدخال **REG_DWORD** يسمى `ForceDefenderPassiveMode`، وتعيين قيمته إلى `0`.

4. إعادة تشغيل الجهاز.

> [!IMPORTANT]
> إذا كنت لا تزال تواجه مشكلة في إعداد برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع النشط بعد اتباع هذا الإجراء، [فاتصل بالدعم](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>أواجه مشكلة في إعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016

إذا كنت تستخدم حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft على Windows Server 2016، فقد يتطلب الحل الحالي برنامج الحماية من الفيروسات من Microsoft Defender ليتم تعطيله أو إلغاء تثبيته. يمكنك استخدام[ الأداة المساعدة Command-Line للحماية من البرامج الضارة](command-line-arguments-microsoft-defender-antivirus.md) لإعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016.

1. كمسؤول محلي على الخادم، افتح موجه الأوامر.

2. تشغيل الأمر التالي: `MpCmdRun.exe -wdenable`

3. أعد تشغيل الجهاز.

## <a name="see-also"></a>راجع أيضًا

- [التوافق برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md)

- [أدوات وأساليب الإلحاق للأجهزة Windows في Defender لنقطة النهاية](configure-endpoints.md) 
