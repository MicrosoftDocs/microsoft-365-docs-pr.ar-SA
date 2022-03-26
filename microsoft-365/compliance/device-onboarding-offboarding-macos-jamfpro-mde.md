---
title: أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في حلول التوافق باستخدام JAMF Pro ل Microsoft Defender لعملاء نقطة النهاية (معاينة)
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
description: تعرف على كيفية تشغيل أجهزة macOS وإبقاف تشغيلها في Microsoft 365 التوافق باستخدام JAMF Pro لعملاء نقطة النهاية ل Microsoft Defender (معاينة)
ms.openlocfilehash: f260d901f8f02c2c02007b2cc0d49ab9ee57dafd
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716310"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview"></a>أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في حلول التوافق باستخدام JAMF Pro ل Microsoft Defender لعملاء نقطة النهاية (معاينة)

يمكنك استخدام JAMF Pro لتكدس أجهزة macOS في Microsoft 365 التوافق.

> [!IMPORTANT]
> استخدم هذا ***الإجراء إذا قمت*** بنشر Microsoft Defender لنقطة النهاية (MDE) على أجهزة macOS

**ينطبق على:**

- العملاء الذين نشروا MDE على أجهزة macOS الخاصة بهم.
- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>قبل البدء

- تأكد من إدارة أجهزة [macOS من خلال JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) ومقترنة بهوية (Azure AD انضم إلى UPN) من خلال JAMF الاتصال Intune.
- تثبيت مستعرض v95+ Edge على أجهزة macOS

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>الأجهزة المجهزة في Microsoft 365 التوافق باستخدام JAMF Pro

إن تشغيل جهاز macOS في حلول التوافق عملية متعددة المراحل.

### <a name="download-the-configuration-files"></a>تنزيل ملفات التكوين

1. ستحتاج إلى هذه الملفات لهذا الإجراء.

|الملف المطلوب ل |المصدر |
|---------|---------|
|إمكانية وصول ذوي الاحتياجات الخاصة |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
الوصول الكامل إلى القرص     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|تفضيل MDE |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> يمكنك تنزيل *ملفات .mobileconfig* بشكل فردي أو في [ملف واحد مدمج](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) يحتوي على:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
>
>إذا تم تحديث أي من هذه الملفات الفردية، ستحتاج إلى تنزيل الملف المدمج مرة أخرى أو الملف المحدث المفرد كل على حدة.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>تحديث ملف تعريف مجال تفضيلات MDE الموجود باستخدام وحدة تحكم JAMF PRO

1. قم بتحديث schema.xml التعريف **بالملف schema.json** الذي قمت بتنزيلها للتو.

1. ضمن **خصائص مجال تفضيلات MDE** ، اختر هذه الإعدادات
    - الميزات 
        - استخدام ملحقات النظام: `enabled` - مطلوب لملحقات الشبكة على كاتالينا
        - استخدام منع فقدان البيانات: `enabled`

1. اختر علامة **التبويب** نطاق.

1. اختر المجموعات لنشر ملف تعريف التكوين هذا لها.

1. اختر **حفظ**. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>تحديث ملف تعريف التكوين لمنح الوصول الكامل إلى القرص

1. قم بتحديث ملف تعريف الوصول الكامل الموجود باستخدام **ملف fulldisk.mobileconfig** .

1. Upload **ملف fulldisk.mobileconfig** إلى JAMF. راجع نشر [ملفات تعريف التكوين المخصصة باستخدام JAMF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>منح إمكانية وصول ذوي الاحتياجات الخاصة إلى DLP

1. استخدم ملف accessibility.mobileconfig الذي قمت بتنزيلها مسبقا.

1. Upload إلى JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصص باستخدام Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>التحقق من جهاز macOS 

1. أعد تشغيل جهاز macOS.

1. افتح **تفضيلات** **النظامProfiles** > .

1. من المفترض أن ترى:
    - Accessiblity
    - الوصول إلى القرص الكامل
    - ملف تعريف ملحق Kernel
    - MAU
    - MDATP Onboarding
    - تفضيلات MDE
    - ملف تعريف الإدارة
    - عامل تصفية الشبكة
    - الإعلامات
    - ملف تعريف ملحق النظام

## <a name="offboard-macos-devices-using-jamf-pro"></a>إيقاف تشغيل أجهزة macOS باستخدام JAMF Pro

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.

اغلق جهاز macOS، اتبع الخطوات التالية

 1. ضمن **خصائص مجال تفضيلات MDE** ، قم بإزالة القيم لهذه الإعدادات
    - الميزات 
        - استخدام ملحقات النظام
        - استخدام منع فقدان البيانات

1. اختر **حفظ**.
