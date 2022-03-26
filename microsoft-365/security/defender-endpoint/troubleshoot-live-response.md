---
title: استكشاف مشاكل الاستجابة المباشرة ل Microsoft Defender ل Endpoint وإصلاحها
description: استكشاف المشاكل التي قد تنشأ عند استخدام الاستجابة المباشرة في Microsoft Defender لنقطة النهاية وإصلاحها
keywords: استكشاف الأخطاء في الاستجابة المباشرة وال مباشرة والاستجابة ومقفلة وملف وإصلاحها
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 4a3bab27a4e2efd6b196167754303f35d5553de6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570196"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-live-response-issues"></a>استكشاف مشاكل الاستجابة المباشرة ل Microsoft Defender ل Endpoint وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

توفر هذه الصفحة خطوات مفصلة لاستعلام مشاكل الاستجابة المباشرة وإصلاحها.

## <a name="file-cannot-be-accessed-during-live-response-sessions"></a>لا يمكن الوصول إلى الملف أثناء جلسات الاستجابة المباشرة

إذا واجهت رسالة خطأ أثناء محاولة اتخاذ إجراء أثناء جلسة استجابة مباشرة تفيد بأنه لا يمكن الوصول إلى الملف، ستحتاج إلى استخدام الخطوات أدناه لمعالجة المشكلة.

1. انسخ قصاصة التعليمات البرمجية البرنامج النصي التالية واحفظها كملف PS1:

    ```powershell
    $copied_file_path=$args[0]
    $action=Copy-Item $copied_file_path -Destination $env:TEMP -PassThru -ErrorAction silentlyContinue

    if ($action){
         Write-Host "You copied the file specified in $copied_file_path to $env:TEMP Succesfully"
    }

    else{
        Write-Output "Error occoured while trying to copy a file, details:"
        Write-Output  $error[0].exception.message

    }
    ```

2. أضف البرنامج النصي إلى مكتبة الاستجابة المباشرة.
3. تشغيل البرنامج النصي بمعلمة واحدة: مسار الملف للملف الذي سيتم نسخه.
4. انتقل إلى مجلد TEMP.
5. تشغيل الإجراء الذي تريد اتخاذه على الملف المنسوخ.

## <a name="slow-live-response-sessions-or-delays-during-initial-connections"></a>إبطاء جلسات الاستجابة المباشرة أو التأخيرات أثناء الاتصالات الأولية

تعمل الاستجابة المباشرة على تحسين تسجيل استشعار Defender لنقطة النهاية مع خدمة WNS في Windows. إذا كنت تواجه مشاكل في الاتصال مع الاستجابة المباشرة، فتأكد من التفاصيل التالية:

1. `notify.windows.com` غير المحظورة في بيئتك. لمزيد من المعلومات، راجع تكوين إعدادات اتصال الإنترنت ووكيل [الجهاز](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).
2. لا يتم تعطيل WpnService (Windows خدمة نظام الإعلامات).

راجع المقالات أدناه لفهم سلوك خدمة WpnService ومتطلباتها بشكل كامل:

- [Windows نظرة عامة حول خدمات الإعلامات (WNS)](/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)
- [جدار حماية المؤسسة وتكوينات الوكيل لدعم حركة مرور WNS](/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)
- [نطاقات IP العامة لخدمة الإعلامات من Microsoft (MPNS)](https://www.microsoft.com/download/details.aspx?id=44535)
