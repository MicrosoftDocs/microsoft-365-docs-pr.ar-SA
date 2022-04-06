---
title: كيفية جدولة عمليات الفحص باستخدام Microsoft Defender ل Endpoint على macOS
description: تعرف على كيفية جدولة وقت فحص تلقائي ل Microsoft Defender لنقطة النهاية في macOS لحماية أصول مؤسستك بشكل أفضل.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، عمليات المسح الضوئي، برنامج الحماية من الفيروسات
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
ms.openlocfilehash: 629db5fc343d100913d631f59a680fc9160713ed
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63583215"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>جدولة عمليات الفحص باستخدام Microsoft Defender ل Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

على الرغم من أنه يمكنك بدء فحص التهديدات في أي وقت باستخدام Microsoft Defender ل Endpoint، قد تستفيد المؤسسة من عمليات الفحص المجدولة أو التي تم تحديد موعدها. على سبيل المثال، يمكنك جدولة فحص لتشغيله في بداية كل يوم عمل أو أسبوع. 

## <a name="schedule-a-scan-with-launchd"></a>جدولة عملية فحص *مع بدء تشغيلها*

يمكنك إنشاء جدول مسح ضوئي *باستخدام daemon* الذي تم تشغيله على جهاز macOS.

لمزيد من المعلومات حول *تنسيق ملف plist.* المستخدم هنا، راجع حول ملفات قائمة خاصية [المعلومات](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) في موقع مطور Apple الرسمي على الويب.

### <a name="schedule-a-quick-scan"></a>جدولة فحص سريع

توضح التعليمة البرمجية التالية المخطط الذي تحتاج إلى استخدامه لجدولة فحص سريع. 

1. افتح محرر نص واستخدم هذا المثال كدليل لملف الفحص المجدول الخاص بك.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedquickscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan quick</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>0</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. احفظ الملف *ك com.microsoft.wdav.schedquickscan.plist*.

### <a name="schedule-a-full-scan"></a>جدولة فحص كامل

1. افتح محرر نص واستخدم هذا المثال لمسح كامل.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedfullscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan full</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>50</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. احفظ الملف *ك com.microsoft.wdav.schedfullscan.plist*.
 
### <a name="load-your-file"></a>تحميل الملف

1. افتح **المحطة الطرفية**.
2. أدخل الأوامر التالية لتحميل الملف:

    ```bash
    launchctl load /Library/LaunchDaemons/<your file name.plist>
    launchctl start <your file name>
    ```

3. سيتم تشغيل الفحص المجدول في التاريخ والوقت والتكرد الذي حددته في قائمة p. في الأمثلة السابقة، يتم تشغيل الفحص في الساعة 2:50 صباحا كل جمعة. 

    - قيمة `Weekday` استخدام `StartCalendarInterval` عدد صحيح للإشارة إلى اليوم الخامس من الأسبوع أو يوم الجمعة. يتراوح النطاق بين 0 و7 مع 7 تمثل الأحد.
    - قيمة `Day` استخدام `StartCalendarInterval` عدد صحيح للإشارة إلى اليوم الثالث من الشهر. يتراوح النطاق بين 1 و31.
    - تستخدم `Hour` قيمة `StartCalendarInterval` عدد صحيح للإشارة إلى الساعة الثانية من اليوم. يتراوح النطاق بين 0 و24.
    قيمة `Minute` استخدام `StartCalendarInterval` عدد صحيح للإشارة إلى خمسون دقيقة من الساعة. يتراوح النطاق بين 0 و59.
    
    
 > [!IMPORTANT]
 > لن يتم تشغيل *الوكلاء الذين* تم تنفيذهم مع التشغيل في الوقت المجدول أثناء وضع الجهاز في وضع النوم. سيتم تشغيلها بدلا من ذلك بمجرد استئناف الجهاز من وضع السكون.
 >
 > إذا تم إيقاف تشغيل الجهاز، سيتم تشغيل الفحص في وقت الفحص المجدول التالي.

## <a name="schedule-a-scan-with-intune"></a>جدولة فحص باستخدام Intune

يمكنك أيضا جدولة عمليات الفحص باستخدام Microsoft Intune. سوف [runMDATPQuickScan.sh](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP#runmdatpquickscansh) البرنامج النصي shell المتوفر في [البرامج النصية ل Microsoft Defender ل Endpoint](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP) عند استئناف الجهاز من وضع السكون. 

راجع [استخدام البرامج النصية shell على أجهزة macOS في Intune](/mem/intune/apps/macos-shell-scripts) للحصول على إرشادات أكثر تفصيلا حول كيفية استخدام هذا البرنامج النصي في المؤسسة.
