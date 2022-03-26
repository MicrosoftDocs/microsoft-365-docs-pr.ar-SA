---
title: تشغيل اختبار الكشف على جهاز للتحقق من أنه تم ا متنه بشكل صحيح في Microsoft Defender لنقطة النهاية
description: يمكنك تشغيل البرنامج النصي لاختبار الكشف على جهاز تم تشغيله مؤخرا في خدمة Microsoft Defender for Endpoint للتحقق من إضافته بشكل صحيح.
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
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 41ba14fd2e4a9e3726e4ef4287812cf8d3ffb2d1
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63571511"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية الذي تم تشغيله حديثا

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- Windows 11
- الإصدارات Windows 10 المعتمدة
- Windows Server 2012 R2
- Windows Server 2016‏
- Windows Server، الإصدار 1803
- Windows Server 2019
- Windows Server 2022
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

عند إضافة جهاز إلى خدمة Microsoft Defender لنقطة النهاية للإدارة، يسمى ذلك أيضا أجهزة الالإضافة. تسمح التكاتف للأجهزة بالإشارة إلى حالة صحتها للخدمة.

إن التأكد من إضافة جهاز إلى الخدمة بنجاح، أو التحقق منه، خطوة هامة في عملية النشر بأكملها. وهو يضمن أنه يتم إدارة جميع الأجهزة المتوقعة. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>التحقق من توفر Microsoft Defender لنقطة النهاية على جهاز باستخدام اختبار الكشف عن PowerShell

يمكنك تشغيل البرنامج النصي التالي من PowerShell على جهاز تم إعداده حديثا للتحقق من أنه يتم إبلاغ خدمة Defender for Endpoint بشكل صحيح.

1. إنشاء مجلد: 'C:\test-MDATP-test'.
2. افتح موجه سطر أوامر مرتفعا على الجهاز و تشغيل البرنامج النصي:

   1. انتقل إلى **ابدأ** وا اكتب **cmd**.

   1. انقر ب زر الماوس الأيمن **فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

      ![نافذة قائمة البدء تشير إلى تشغيل كمسؤول.](images/run-as-admin.png)

3. في المطالبة، انسخ الأمر التالي وتشغيله:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

سيتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجح الأمر، سيظهر تنبيه جديد في مدخل الجهاز المحضر في غضون عشر دقائق تقريبا.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [أجهزة Windows](configure-endpoints.md)
- [خوادم على اللوحة](configure-server-endpoints.md)
- [استكشاف مشاكل تشغيل نقطة النهاية وإصلاحها في Microsoft Defender](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
