---
title: تشغيل اختبار الكشف على جهاز للتحقق من أنه تم االلوح بشكل صحيح Microsoft Defender لنقطة النهاية
description: تشغيل البرنامج النصي لاختبار الكشف على جهاز تم تشغيله مؤخرا Microsoft Defender لنقطة النهاية الخدمة للتحقق من إضافتها بشكل صحيح.
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
ms.openlocfilehash: 1d8459633d00d759fda1584e0084cd8ed4e12633
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477248"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>تشغيل اختبار الكشف على جهاز تم Microsoft Defender لنقطة النهاية جديد

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- Windows 11
- الإصدارات Windows 10 المعتمدة
- Windows Server 2012 R2
- Windows Server 2016‏
- Windows Server، الإصدار 1803
- Windows Server 2019
- Windows Server 2022
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

عند إضافة جهاز إلى الخدمة Microsoft Defender لنقطة النهاية الإدارة، يسمى ذلك أيضا أجهزة الالإضافة. تسمح التكاتف للأجهزة بالإشارة إلى حالة صحتها للخدمة.

إن التأكد من إضافة جهاز إلى الخدمة بنجاح، أو التحقق منه، خطوة هامة في عملية النشر بأكملها. وهو يضمن أنه يتم إدارة جميع الأجهزة المتوقعة. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>التحقق من Microsoft Defender لنقطة النهاية على جهاز باستخدام اختبار الكشف عن PowerShell

يمكنك تشغيل البرنامج النصي التالي من PowerShell على جهاز تم إعداده حديثا للتحقق من أنه يتم إبلاغ خدمة Defender for Endpoint بشكل صحيح.

1. إنشاء مجلد: 'C:\test-MDATP-test'.
2. افتح موجه سطر أوامر مرتفعا على الجهاز و تشغيل البرنامج النصي:

   1. انتقل إلى **ابدأ** وا اكتب **cmd**.

   1. انقر ب زر الماوس الأيمن **فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

      :::image type="content" source="images/run-as-admin.png" alt-text="يشير قائمة البدء إلى تشغيل كمسؤول" lightbox="images/run-as-admin.png":::
    
3. في المطالبة، انسخ الأمر التالي وتشغيله:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

سيتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجح الأمر، سيظهر تنبيه جديد في مدخل الجهاز المحضر في غضون عشر دقائق تقريبا.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [أجهزة Windows](configure-endpoints.md)
- [خوادم على اللوحة](configure-server-endpoints.md)
- [استكشاف مشاكل Microsoft Defender لنقطة النهاية في الحافظة وإصلاحها](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
