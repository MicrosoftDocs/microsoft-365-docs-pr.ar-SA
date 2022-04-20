---
title: إلحاق أجهزة macOS وإلحاقها بحلول التوافق باستخدام Microsoft Intune لعملاء Microsoft Defender لنقطة النهاية
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: تعرف على كيفية إلحاق أجهزة macOS وإلحاقها بحلول Microsoft Purview باستخدام Microsoft Intune لعملاء MDE
ms.openlocfilehash: c6b374ad3c35ba3441e82412d9897132006d0559
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952831"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers"></a>إلحاق أجهزة macOS وإلحاقها في حلول التوافق باستخدام Intune لعملاء Microsoft Defender لنقطة النهاية

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!IMPORTANT]
> استخدم هذا الإجراء ***إذا قمت*** بنشر Microsoft Defender لنقطة النهاية (MDE) على أجهزة macOS

**ينطبق على:**

- العملاء الذين تم نشر MDE على أجهزة macOS الخاصة بهم.
- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)


## <a name="before-you-begin"></a>قبل البدء

- تأكد من [إلحاق أجهزة macOS في Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) وتسجيلها في [تطبيق Company Portal](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- تأكد من أن لديك حق الوصول إلى [مركز إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/#home)
- هذا يدعم إصدار macOS Catalina 10.15 والإصدارات الأحدث
- تثبيت مستعرض v95+ Edge على أجهزة macOS 

## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>إلحاق أجهزة macOS في حلول Microsoft Purview باستخدام Microsoft Intune

استخدم هذه الخطوات لإلحاق جهاز macOS في حلول التوافق إذا كان قد تم نشر MDE عليه بالفعل.

1. ستحتاج إلى هذه الملفات لهذا الإجراء.

|الملف المطلوب ل |مصدر |
|---------|---------|
|امكانيه الوصول |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
الوصول الكامل إلى القرص     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> يمكنك تنزيل ملفات *.mobileconfig* بشكل فردي أو في [ملف واحد مدمج](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) يحتوي على:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> 
>
>إذا تم تحديث أي من هذه الملفات الفردية، فستحتاج إلى تنزيل الملف المدمج مرة أخرى أو الملف المحدث الفردي بشكل فردي.

### <a name="create-system-configuration-profiles"></a>إنشاء ملفات تعريف تكوين النظام

1. افتح **ملفات تعريف إدارة نقاط النهاية من Microsoft** **centerDevicesConfiguration** >  > .

1. اختر: **إنشاء ملف تعريف**. 

1. اختيار:
    1. **النظام الأساسي = macOS**
    1. **نوع ملف التعريف = قوالب**
    1. **اسم القالب = مخصص**

1. اختر **"إنشاء"**

1. اختر اسما لملف التعريف، مثل *AccessibilityformacOS* في هذا المثال. اختر **"التالي**".

1. اختر ملف **accessibility.mobileconfig** الذي قمت بتنزيله في الخطوة 1 كملف ملف تعريف التكوين.

1. اختر **"التالي"**

1. في علامة التبويب **"الواجبات"** ، أضف المجموعة التي تريد توزيع هذه التكوينات إليها واختر **"التالي**".

1. راجع الإعدادات واختر **"إنشاء** " لنشر التكوين.

1. افتح **ملفات تعريف DevicesConfiguration** > ، يجب أن تشاهد ملفات التعريف التي تم إنشاؤها هناك.

1. في صفحة **ملفات تعريف التكوين** ، اختر ملف التعريف الذي أنشأته للتو، في هذا المثال *AccessibilityformacOS* واختر **حالة الجهاز** لعرض قائمة بالأجهزة وحالة نشر ملف تعريف التكوين.

### <a name="update-configuration-profiles"></a>تحديث ملفات تعريف التكوين

1. تحديث ملف تعريف الوصول إلى القرص الكامل الموجود مع ملف **fulldisk.mobileconfig** .

1. تحديث ملف تعريف تفضيلات MDE مع هذه القيم
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```

## <a name="offboard-macos-devices-using-intune"></a>إيقاف تشغيل أجهزة macOS باستخدام Intune

> [!IMPORTANT]
> يؤدي إلغاء الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات كان قد تم الاحتفاظ بها لمدة تصل إلى 6 أشهر.

1. في **مركز إدارة نقاط النهاية من Microsoft**، افتح **ملفات تعريف DevicesConfiguration** > ، يجب أن تشاهد ملفات التعريف التي تم إنشاؤها هناك.

2. في صفحة **ملفات تعريف التكوين** ، اختر ملف تعريف تفضيلات MDE.

1. إزالة هذه الإعدادات:
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```
3. **حفظ**.
