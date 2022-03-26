---
title: أجهزة macOS المجهزة للأجهزة التي تعمل باللوح واللوح في حلول التوافق Microsoft Intune Microsoft Defender لعملاء نقطة النهاية (معاينة)
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
description: تعرف على كيفية تشغيل أجهزة macOS أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام Microsoft Intune لعملاء MDE (معاينة)
ms.openlocfilehash: 6cc4362e924f291c6a8396bff342c6f628e33be3
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63570875"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview"></a>أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في حلول التوافق باستخدام Intune لعملاء نقطة النهاية ل Microsoft Defender (معاينة)

> [!IMPORTANT]
> استخدم هذا ***الإجراء إذا قمت*** بنشر Microsoft Defender لنقطة النهاية (MDE) على أجهزة macOS

**ينطبق على:**

- العملاء الذين نشروا MDE على أجهزة macOS الخاصة بهم.
- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>قبل البدء

- تأكد من أن [أجهزة macOS مجهزه في Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) ومسجلة [في Company Portal التطبيق](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- تأكد من إمكانية [الوصول إلى إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/#home)
- هذا يدعم إصدار macOS Catalina 10.15 والإصدارات الأحدث
- تثبيت مستعرض v95+ Edge على أجهزة macOS 

## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>أجهزة macOS المجهزة Microsoft 365 التوافق باستخدام Microsoft Intune

استخدم هذه الخطوات ل متن جهاز macOS في حلول التوافق إذا تم نشر MDE له بالفعل.

1. ستحتاج إلى هذه الملفات لهذا الإجراء.

|الملف المطلوب ل |المصدر |
|---------|---------|
|إمكانية وصول ذوي الاحتياجات الخاصة |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
الوصول الكامل إلى القرص     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> يمكنك تنزيل *ملفات .mobileconfig* بشكل فردي أو في [ملف واحد مدمج](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) يحتوي على:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> 
>
>إذا تم تحديث أي من هذه الملفات الفردية، ستحتاج إلى تنزيل الملف المدمج مرة أخرى أو الملف المحدث المفرد كل على حدة.

### <a name="create-system-configuration-profiles"></a>إنشاء ملفات تعريف تكوين النظام

1. افتح إدارة نقاط النهاية من Microsoft النملفات تعريف تكوين **في** **الوسط** >  > .

1. اختر: **إنشاء ملف تعريف**. 

1. اختر:
    1. **Platform = macOS**
    1. **نوع ملف التعريف = القوالب**
    1. **اسم القالب = مخصص**

1. اختر **إنشاء**

1. اختر اسما لملف التعريف، مثل *AccessibilityformacOS* في هذا المثال. اختر **التالي**.

1. اختر **ملف accessibility.mobileconfig** الذي قمت بتنزيلها في الخطوة 1 كملف ملف تعريف التكوين.

1. اختر **التالي**

1. على علامة **التبويب** الواجبات، أضف المجموعة التي تريد نشر هذه التكوينات لها واختر **التالي**.

1. راجع الإعدادات **واختر إنشاء** لنشر التكوين.

1. افتح **ملفات تعريف تكوين** >  **الأجهزة**، يجب أن ترى ملفات التعريف التي تم إنشاؤها هناك.

1. في الصفحة **ملفات تعريف** التكوين، اختر ملف التعريف الذي أنشأته للتو، في هذا المثال *AccessibilityformacOS* واختر حالة الجهاز  لرؤية قائمة الأجهزة حالة نشر ملف تعريف التكوين.

### <a name="update-configuration-profiles"></a>تحديث ملفات تعريف التكوين

1. قم بتحديث ملف تعريف الوصول الكامل الموجود باستخدام **ملف fulldisk.mobileconfig** .

1. تحديث ملف تعريف تفضيلات MDE الخارجية باستخدام هذه القيم
   
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
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.

1. في **إدارة نقاط النهاية من Microsoft،** افتح **ملفات تعريف تكوين** >  **الأجهزة**، يجب أن ترى ملفات التعريف التي تم إنشاؤها هناك.

2. في الصفحة **ملفات تعريف التكوين** ، اختر ملف تعريف تفضيلات MDE.

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