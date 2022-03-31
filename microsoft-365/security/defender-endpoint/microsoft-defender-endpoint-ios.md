---
title: Microsoft Defender لنقطة النهاية على نظام التشغيل iOS
ms.reviewer: ''
description: يصف كيفية تثبيت Microsoft Defender لنقطة النهاية واستخدامه على نظام التشغيل iOS
keywords: microsoft، defender، Microsoft Defender ل Endpoint، ios، نظرة عامة، تثبيت، نشر، إزالة تثبيت، intune
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c144eb3cd0cec2d96f20294475618e7e9c49c816
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/17/2022
ms.locfileid: "63578090"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>Microsoft Defender لنقطة النهاية على نظام التشغيل iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**يوفر Microsoft Defender ل Endpoint على نظام التشغيل iOS** الحماية من التصيد الاحتيالي واتصالات الشبكة غير الآمنة من مواقع الويب ورسائل البريد الإلكتروني والتطبيقات. ستتوفر كل التنبيهات من خلال جزء واحد من الزجاج في Microsoft 365 Defender المدخل. يوفر المدخل لفرق الأمان طريقة عرض مركزية للتهديدات على أجهزة iOS إلى جانب الأنظمة الأساسية الأخرى.

> [!CAUTION]
> من المرجح أن يؤدي تشغيل منتجات أخرى لحماية نقاط النهاية من جهة خارجية إلى جانب Defender for Endpoint على نظام التشغيل iOS إلى حدوث مشاكل في الأداء وأخطاء في النظام لا يمكن التنبؤ بها.

## <a name="pre-requisites"></a>المتطلبات الأساسية

**للمستخدمين النهائيين**

- ترخيص Microsoft Defender لنقطة النهاية المعين إلى المستخدم (المستخدمين) النهائيين للتطبيق. راجع [متطلبات ترخيص نقطة النهاية ل Microsoft Defender](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **للأجهزة التي تم تسجيلها**:
    - يتم [تسجيل الجهاز (](/mem/intune/user-help/enroll-your-device-in-intune-ios)الأجهزة) عبر تطبيق Intune Company Portal لفرض سياسات توافق أجهزة Intune. يتطلب ذلك تعيين ترخيص Microsoft Intune للمستخدم.
    - Intune Company Portal التطبيق من [Apple App Store](https://apps.apple.com/us/app/intune-company-portal/id719171358).
    
    >[!NOTE]
    >لا تسمح Apple بإعادة توجيه المستخدمين لتنزيل تطبيقات أخرى من متجر التطبيقات، لذا يجب على المستخدم القيام بهذه الخطوة قبل التكوين في تطبيق Microsoft Defender for Endpoint.)
    
    - يتم تسجيل الجهاز (الأجهزة) مع Azure Active Directory. يتطلب ذلك من المستخدم تسجيل الدخول من [خلال Microsoft Authenticator التطبيق](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- **بالنسبة للأجهزة غير المسجلة**: يتم تسجيل الأجهزة (الأجهزة) باستخدام Azure Active Directory. يتطلب ذلك من المستخدم تسجيل الدخول من [خلال Microsoft Authenticator التطبيق](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- لمزيد من المعلومات حول كيفية تعيين التراخيص، راجع [تعيين التراخيص للمستخدمين](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**للمسؤولين**

- الوصول إلى Microsoft 365 Defender الإلكتروني.

- الوصول إلى [إدارة نقاط النهاية من Microsoft إدارة،](https://go.microsoft.com/fwlink/?linkid=2109431) إلى:
   - نشر التطبيق إلى مجموعات المستخدمين المسجلين في مؤسستك.
   - تكوين إشارات مخاطر نقطة النهاية ل Microsoft Defender في نهج حماية التطبيق (MAM)


    > [!NOTE]
    > - يعمل Microsoft Defender for Endpoint الآن على توسيع الحماية لبيانات المؤسسة ضمن تطبيق مدار لأولئك الذين لا يستخدمون إدارة أجهزة المحمول (MDM) ولكنهم يستخدمون Intune لإدارة تطبيقات الأجهزة المحمولة. كما أنه يوسع هذا الدعم ليشمل العملاء الذين يستخدمون حلولا أخرى لإدارة تنقل المؤسسات، مع استخدام Intune لإدارة تطبيقات الأجهزة المحمولة [(MAM).](/mem/intune/apps/mam-faq)
    > - بالإضافة إلى ذلك، يدعم Microsoft Defender for Endpoint بالفعل الأجهزة التي تم تسجيلها باستخدام إدارة أجهزة Intune المحمولة (MDM).  

**متطلبات النظام**

- جهاز iOS يعمل ب iOS 12.0 والأعلى. يتم أيضا دعم أجهزة iPad. *تجدر الإشارة إلى أنه بدءا من 31 مارس 2022، سيكون الحد الأدنى للإصدار المدعم من iOS من قبل Microsoft Defender ل Endpoint هو iOS 13.0.*

- يكون الجهاز إما مسجلا في Intune Company Portal [أو](https://apps.apple.com/us/app/intune-company-portal/id719171358) مسجلا مع Azure Active Directory من [خلال](https://apps.apple.com/app/microsoft-authenticator/id983156458) Microsoft Authenticator باستخدام الحساب نفسه.

## <a name="installation-instructions"></a>إرشادات التثبيت

يمكن نشر Microsoft Defender لنقطة النهاية على نظام التشغيل iOS عبر إدارة نقاط النهاية من Microsoft (MEM) كما يتم دعم الأجهزة غير المدعمة وغير المدعمة. يمكن للمستخدمين أيضا تثبيت التطبيق مباشرة من [متجر تطبيقات Apple](https://aka.ms/mdatpiosappstore).

- للحصول على معلومات حول النشر على الأجهزة إدارة نقاط النهاية من Microsoft أو Intune، راجع [نشر Microsoft Defender لنقطة النهاية على نظام التشغيل iOS](ios-install.md).
- للحصول على معلومات حول استخدام Defender for Endpoint في نهج حماية التطبيق (MAM)، راجع تكوين نهج حماية التطبيق لتضمين [إشارات خطر Defender for Endpoint (MAM)](ios-install-unmanaged.md)

## <a name="resources"></a>الموارد

- ابق على اطلاع على الإصدارات القادمة من خلال زيارة أحدث ما في [Microsoft Defender ل Endpoint على iOS](ios-whatsnew.md) أو [مدونتنا](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

- تقديم الملاحظات من خلال نظام الملاحظات داخل التطبيق أو من خلال [وحدة التحكم في الأمان الموحدة](https://security.microsoft.com)

## <a name="next-steps"></a>الخطوات التالية

- [نشر Microsoft Defender لنقطة النهاية على نظام التشغيل iOS من خلال Intune للأجهزة المسجلين](ios-install.md)
- [تكوين نهج حماية التطبيق لتضمين إشارات خطر Defender for Endpoint (MAM)](ios-install-unmanaged.md)
- [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)
- [تكوين نهج الوصول الشرطي استنادا إلى درجة مخاطر الجهاز من Microsoft Defender لنقطة النهاية](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [أساسيات إدارة تطبيقات الأجهزة المحمولة (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
