---
title: تجميع سجلات الدعم في Microsoft Defender لنقطة النهاية باستخدام الاستجابة المباشرة
description: تعرف على كيفية تجميع السجلات باستخدام الاستجابة المباشرة لا استكشاف Microsoft Defender لنقطة النهاية وإصلاحها
keywords: الدعم، السجل، تجميع، استكشاف الأخطاء وإصلاحها، الاستجابة المباشرة، liveanalyzer، محلل، مباشر، استجابة
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
ms.openlocfilehash: 138b532e7786a3d142c3cbbe68f668a4b0e05591
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472562"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>تجميع سجلات الدعم في Microsoft Defender لنقطة النهاية باستخدام الاستجابة المباشرة


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


عند الاتصال بالدعم، قد يطلب منك توفير حزمة إخراج أداة Microsoft Defender لنقطة النهاية العميل.

يوفر هذا الموضوع إرشادات حول كيفية تشغيل الأداة عبر Live Response.

1. قم بتنزيل البرامج النصية المطلوبة المتوفرة من داخل الدليل الفرعي "أدوات" في Microsoft Defender لنقطة النهاية [العميل](https://aka.ms/BetaMDEAnalyzer). <br>
على سبيل المثال، للحصول على المستشعر الأساسي وسجلات صحة الجهاز، قم بإحضار ".. \Tools\MDELiveAnalyzer.ps1".<br>
إذا كنت تحتاج أيضا إلى سجلات دعم Defender Antivirus (MpSupportFiles.cab)، فإحضار ".. \Tools\MDELiveAnalyzerAV.ps1" 

2. ابدأ جلسة [استجابة مباشرة](live-response.md#initiate-a-live-response-session-on-a-device) على الجهاز الذي تحتاج إلى التحقق منه.

3. حدد **Upload الملف إلى المكتبة**.

   :::image type="content" source="images/upload-file.png" alt-text="ملف التحميل" lightbox="images/upload-file.png":::

4. حدد **اختيار ملف**.

   :::image type="content" source="images/choose-file.png" alt-text="الزر &quot;اختيار ملف&quot;-1" lightbox="images/choose-file.png":::

5. حدد الملف الذي تم تنزيله MDELiveAnalyzer.ps1 ثم انقر فوق **تأكيد**

   :::image type="content" source="images/analyzer-file.png" alt-text="الزر &quot;اختيار ملف-2&quot;" lightbox="images/analyzer-file.png":::

6. أثناء وجودك في جلسة LiveResponse، استخدم الأوامر أدناه لتشغيل المحلل وجمع ملف النتيجة:

    ```console
    Run MDELiveAnalyzer.ps1
    GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
    ```

    [![صورة الأوامر.](images/analyzer-commands.png)](images/analyzer-commands.png#lightbox)

> [!NOTE]
>
> - يمكن تنزيل أحدث إصدار معاينة من MDEClientAnalyzer هنا: [https://aka.ms/Betamdeanalyzer](https://aka.ms/Betamdeanalyzer).
>
> - ينزيل البرنامج النصي LiveAnalyzer حزمة استكشاف الأخطاء وإصلاحها على الجهاز الوجهة من: https://mdatpclientanalyzer.blob.core.windows.net.
>
>   إذا لم تتمكن من السماح للجهاز بالوصول إلى عنوان URL أعلاه، MDEClientAnalyzerPreview.zip الملف إلى المكتبة قبل تشغيل البرنامج النصي LiveAnalyzer:
>
>   ```console
>   PutFile MDEClientAnalyzerPreview.zip -overwrite
>   Run MDELiveAnalyzer.ps1
>   GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
>   ```
>
> - لمزيد من المعلومات حول تجميع البيانات محليا على جهاز في حال لم يكن الجهاز على اتصال مع خدمات سحابة Microsoft Defender لنقطة النهاية، أو لم يظهر في مدخل Microsoft Defender لنقطة النهاية كما هو متوقع، راجع التحقق من اتصال العميل ب [ Microsoft Defender لنقطة النهاية URL للخدمة](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls).
> 
> - كما هو موضح في [](live-response-command-examples.md)أمثلة أوامر الاستجابة المباشرة، قد تحتاج إلى استخدام الرمز "&" في نهاية الأمر لتجميع السجلات ك إجراء في الخلفية:
>   ```console
>   Run MDELiveAnalyzer.ps1&
>   ```


## <a name="see-also"></a>راجع أيضًا
- [نظرة عامة حول محلل العميل](overview-client-analyzer.md)
- [تنزيل محلل العميل وتشغيله](download-client-analyzer.md)
- [تشغيل محلل العميل على Windows](run-analyzer-windows.md)
- [تشغيل محلل العميل على macOS أو Linux](run-analyzer-macos-linux.md)
- [تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows](data-collection-analyzer.md)
- [فهم تقرير HTML الخاص ب المحلل](analyzer-report.md)
