---
title: مشكلات الأداء في Microsoft Defender لنقطة النهاية على iOS
ms.reviewer: ''
description: يصف كيفية تثبيت Microsoft Defender لنقطة النهاية واستخدامها على iOS
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، ios، نظرة عامة، تثبيت، توزيع، إلغاء تثبيت، intune
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
ms.openlocfilehash: ac2c34359686da45998fab1076b7501357651318
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/09/2022
ms.locfileid: "66695846"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>مشكلات الأداء في Microsoft Defender لنقطة النهاية على iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**يوفر Microsoft Defender لنقطة النهاية على iOS** الحماية من التصيد الاحتيالي واتصالات الشبكة غير الآمنة من مواقع الويب ورسائل البريد الإلكتروني والتطبيقات. ستتوفر جميع التنبيهات من خلال جزء واحد من الزجاج في مدخل Microsoft 365 Defender. يمنح المدخل فرق الأمان عرضا مركزيا للتهديدات على أجهزة iOS جنبا إلى جنب مع الأنظمة الأساسية الأخرى.

> [!CAUTION]
> من المحتمل أن يؤدي تشغيل منتجات حماية نقطة نهاية أخرى تابعة لجهة خارجية إلى جانب Defender لنقطة النهاية على iOS إلى حدوث مشاكل في الأداء وأخطاء في النظام لا يمكن التنبؤ بها.

## <a name="prerequisites"></a>المتطلبات الأساسية

**للمستخدمين النهائيين**

- Microsoft Defender لنقطة النهاية الترخيص المعين للمستخدم (المستخدمين) النهائيين للتطبيق. راجع [متطلبات الترخيص Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **للأجهزة المسجلة**:
    - [يتم تسجيل](/mem/intune/user-help/enroll-your-device-in-intune-ios) الأجهزة عبر تطبيق Intune Company Portal لفرض نهج توافق جهاز Intune. يتطلب هذا تعيين ترخيص Microsoft Intune للمستخدم النهائي.
    - يمكن تنزيل تطبيق Intune Company Portal من [App Store Apple](https://apps.apple.com/us/app/intune-company-portal/id719171358).
    
    >[!NOTE]
    >لا تسمح Apple بإعادة توجيه المستخدمين لتنزيل تطبيقات أخرى من متجر التطبيقات لذلك يجب أن يقوم المستخدم بتنفيذ هذه الخطوة قبل إلحاقه بتطبيق Microsoft Defender لنقطة النهاية.)


    - يتم تسجيل الأجهزة (الأجهزة) مع Azure Active Directory. يتطلب ذلك تسجيل دخول المستخدم النهائي من خلال [تطبيق Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- **للأجهزة غير المسجلة**: يتم تسجيل الجهاز (الأجهزة) مع Azure Active Directory. يتطلب ذلك تسجيل دخول المستخدم النهائي من خلال [تطبيق Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- لمزيد من المعلومات حول كيفية تعيين التراخيص، راجع [تعيين التراخيص للمستخدمين](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**للمسؤولين**

- الوصول إلى مدخل Microsoft 365 Defender.

- الوصول إلى [مركز إدارة Microsoft إدارة نقاط النهاية](https://go.microsoft.com/fwlink/?linkid=2109431)، من أجل:
   - نشر التطبيق لمجموعات المستخدمين المسجلين في مؤسستك.
   - تكوين إشارات مخاطر Microsoft Defender لنقطة النهاية في نهج حماية التطبيقات (MAM)


    > [!NOTE]
    > - Microsoft Defender لنقطة النهاية الآن توسيع الحماية إلى بيانات المؤسسة داخل تطبيق مدار لأولئك الذين لا يستخدمون إدارة أجهزة المحمول (MDM) ولكنهم يستخدمون Intune لإدارة تطبيقات الأجهزة المحمولة. كما أنه يوسع هذا الدعم للعملاء الذين يستخدمون حلول إدارة تنقل المؤسسات الأخرى، مع الاستمرار في استخدام Intune [لإدارة تطبيقات المحمول (MAM).](/mem/intune/apps/mam-faq)
    > - بالإضافة إلى ذلك، يدعم Microsoft Defender لنقطة النهاية بالفعل الأجهزة المسجلة باستخدام إدارة الأجهزة المحمولة Intune (MDM).  

**متطلبات النظام**

- جهاز iOS يعمل بنظام التشغيل iOS 12.0 وما فوق. يتم دعم أجهزة iPad أيضا. *لاحظ أنه بدءا من 31 مارس-2022، سيكون الحد الأدنى من إصدار iOS المدعوم بواسطة Microsoft Defender لنقطة النهاية هو iOS 13.0.*

- إما أن يكون الجهاز مسجلا في [تطبيق Intune Company Portal](https://apps.apple.com/us/app/intune-company-portal/id719171358) أو مسجلا مع Azure Active Directory من خلال [Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458) بنفس الحساب.

 > [!NOTE]
 > Microsoft Defender لنقطة النهاية على iOS غير مدعوم حاليا أثناء استخدام تسجيل مستخدم iOS.

## <a name="installation-instructions"></a>إرشادات التثبيت

يمكن نشر Microsoft Defender لنقطة النهاية على iOS عبر Microsoft إدارة نقاط النهاية (MEM) ويتم دعم كل من الأجهزة الخاضعة للإشراف وغير الخاضعة للإشراف. يمكن للمستخدمين النهائيين أيضا تثبيت التطبيق مباشرة من [متجر تطبيقات Apple](https://aka.ms/mdatpiosappstore).

- للحصول على معلومات حول النشر على الأجهزة المسجلة من خلال Microsoft إدارة نقاط النهاية أو Intune، راجع [نشر Microsoft Defender لنقطة النهاية على iOS](ios-install.md).
- للحصول على معلومات حول استخدام Defender لنقطة النهاية في نهج حماية التطبيقات (MAM)، راجع [تكوين نهج حماية التطبيق لتضمين إشارات مخاطر Defender لنقطة النهاية (MAM)](ios-install-unmanaged.md)

## <a name="resources"></a>الموارد

- ابق على اطلاع على الإصدارات القادمة من خلال زيارة أحدث [الميزات في Microsoft Defender لنقطة النهاية على iOS](ios-whatsnew.md) أو [مدونتنا](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

- تقديم الملاحظات من خلال نظام الملاحظات داخل التطبيق أو من خلال [وحدة تحكم الأمان الموحدة](https://security.microsoft.com)

## <a name="next-steps"></a>الخطوات التالية

- [نشر Microsoft Defender لنقطة النهاية على iOS من خلال Intune للأجهزة المسجلة](ios-install.md)
- [تكوين نهج حماية التطبيق لتضمين إشارات مخاطر Defender لنقطة النهاية (MAM)](ios-install-unmanaged.md)
- [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)
- [تكوين نهج الوصول المشروط استنادا إلى درجة مخاطر الجهاز من Microsoft Defender لنقطة النهاية](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [أساسيات إدارة تطبيقات المحمول (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
