---
title: إلحاق أجهزة macOS وإلغاء إلحاقها بحلول التوافق باستخدام JAMF Pro ل Microsoft Defender لعملاء نقطة النهاية
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
description: تعرف على كيفية إلحاق أجهزة macOS وإلحاقها بحلول Microsoft Purview باستخدام JAMF Pro لعملاء Microsoft Defender لنقطة النهاية
ms.openlocfilehash: 97ab1dbccc28cd1f9d14635c2fa351d0295202c1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622910"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers"></a>إلحاق أجهزة macOS وإلغاء إلحاقها بحلول التوافق باستخدام JAMF Pro ل Microsoft Defender لعملاء نقطة النهاية

يمكنك استخدام JAMF Pro لإلحاق أجهزة macOS في حلول Microsoft Purview.

> [!IMPORTANT]
> استخدم هذا الإجراء ***إذا قمت*** بنشر Microsoft Defender لنقطة النهاية (MDE) على أجهزة macOS

**ينطبق على:**

- العملاء الذين تم نشر MDE على أجهزة macOS الخاصة بهم.
- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)


## <a name="before-you-begin"></a>قبل البدء

- تأكد من [إدارة أجهزة macOS من خلال JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) ومقترنة بهوية (Azure AD انضم إلى UPN) من خلال JAMF Connect أو Intune.
- تثبيت مستعرض v95+ Edge على أجهزة macOS

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>إلحاق الأجهزة في حلول Microsoft Purview باستخدام JAMF Pro

إعداد جهاز macOS في حلول التوافق هو عملية متعددة المراحل.

### <a name="download-the-configuration-files"></a>تنزيل ملفات التكوين

1. ستحتاج إلى هذه الملفات لهذا الإجراء.

|الملف المطلوب ل |مصدر |
|---------|---------|
|امكانيه الوصول |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
الوصول الكامل إلى القرص     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|تفضيل MDE |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> يمكنك تنزيل ملفات *.mobileconfig* بشكل فردي أو في [ملف واحد مدمج](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) يحتوي على:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
>
>إذا تم تحديث أي من هذه الملفات الفردية، فستحتاج إلى تنزيل الملف المدمج مرة أخرى أو الملف المحدث الفردي بشكل فردي.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>تحديث ملف تعريف مجال MDE Preference الموجود باستخدام وحدة تحكم JAMF PRO

1. تحديث ملف تعريف schema.xml مع ملف **schema.json** الذي قمت بتنزيله للتو.

1. ضمن **خصائص مجال تفضيلات MDE** اختر هذه الإعدادات
    - ميزات 
        - استخدام ملحقات النظام: `enabled` - مطلوب لملحقات الشبكة على Catalina
        - استخدام منع فقدان البيانات: `enabled`

1. اختر علامة التبويب **"نطاق** ".

1. اختر المجموعات التي تريد نشر ملف تعريف التكوين هذا إليها.

1. اختر **"حفظ**". 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>تحديث ملف تعريف التكوين لمنح حق الوصول الكامل إلى القرص

1. تحديث ملف تعريف الوصول إلى القرص الكامل الموجود مع ملف **fulldisk.mobileconfig** .

1. تحميل ملف **fulldisk.mobileconfig** إلى JAMF. راجع [نشر ملفات تعريف التكوين المخصصة باستخدام JAMF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>منح إمكانية وصول ذوي الاحتياجات الخاصة إلى DLP

1. استخدم ملف accessibility.mobileconfig الذي قمت بتنزيله مسبقا.

1. تحميل إلى JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصصة باستخدام Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>التحقق من جهاز macOS 

1. أعد تشغيل جهاز macOS.

1. افتح **ملفات تعريف** **تفضيلات** >  النظام.

1. يجب أن ترى:
    - إمكانية الوصول
    - الوصول إلى القرص الكامل
    - ملف تعريف ملحق Kernel
    - ماو
    - إلحاق MDATP
    - تفضيلات MDE
    - ملف تعريف الإدارة
    - عامل تصفية الشبكة
    - الاخطارات
    - ملف تعريف ملحق النظام

## <a name="offboard-macos-devices-using-jamf-pro"></a>إيقاف تشغيل أجهزة macOS باستخدام JAMF Pro

> [!IMPORTANT]
> يؤدي إلغاء الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات كان قد تم الاحتفاظ بها لمدة تصل إلى 6 أشهر.

لإلغاء إلحاق جهاز macOS، اتبع الخطوات التالية

 1. ضمن **خصائص مجال تفضيلات MDE** ، قم بإزالة قيم هذه الإعدادات
    - ميزات 
        - استخدام ملحقات النظام
        - استخدام منع فقدان البيانات

1. اختر **"حفظ**".
