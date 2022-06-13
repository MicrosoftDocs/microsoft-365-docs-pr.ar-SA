---
title: مشكلات الأداء في Microsoft Defender لنقطة النهاية على Android
ms.reviewer: ''
description: يصف كيفية تثبيت Microsoft Defender لنقطة النهاية واستخدامها على Android
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، android، التثبيت، التوزيع، إلغاء التثبيت، intune
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8de6af6f04243a8481d116fe9a67f5420b536f6c
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016493"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>مشكلات الأداء في Microsoft Defender لنقطة النهاية على Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يصف هذا الموضوع كيفية تثبيت وتكوين وتحديث واستخدام Defender لنقطة النهاية على Android.

> [!CAUTION]
> من المحتمل أن يؤدي تشغيل منتجات حماية نقطة نهاية أخرى تابعة لجهة خارجية إلى جانب Defender لنقطة النهاية على Android إلى حدوث مشاكل في الأداء وأخطاء في النظام لا يمكن التنبؤ بها.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>كيفية تثبيت Microsoft Defender لنقطة النهاية على Android

### <a name="prerequisites"></a>المتطلبات الأساسية

- **للمستخدمين النهائيين**:
  - يجب تعيين ترخيص Microsoft Intune للمستخدم النهائي. لمزيد من المعلومات حول كيفية تعيين التراخيص، راجع [تعيين التراخيص للمستخدمين](/azure/active-directory/users-groups-roles/licensing-groups-assign).
  - يجب تعيين ترخيص Microsoft Defender لنقطة النهاية لمستخدمي التطبيق. لمزيد من المعلومات حول كيفية تعيين التراخيص، راجع [Microsoft Defender لنقطة النهاية متطلبات الترخيص](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).
  - يمكن تنزيل تطبيق Intune Company Portal من [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) وهو متوفر على جهاز Android.
  - بالإضافة إلى ذلك، يمكن [تسجيل](/mem/intune/user-help/enroll-device-android-company-portal) الأجهزة (الأجهزة) عبر تطبيق Intune Company Portal لفرض نهج توافق الأجهزة Intune. 

- **للمسؤولين**:
   - الوصول إلى مدخل Microsoft 365 Defender.
   - الوصول [إلى مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) من أجل:
     - نشر التطبيق لمجموعات المستخدمين المسجلين في مؤسستك.
     - تكوين إشارات مخاطر Microsoft Defender لنقطة النهاية في نهج حماية التطبيق.
  
    > [!NOTE]
    >
    > - Microsoft Defender لنقطة النهاية الآن توسيع الحماية إلى بيانات المؤسسة داخل تطبيق مدار (MAM) للأجهزة غير المسجلة باستخدام إدارة أجهزة المحمول (MDM)، ولكنها تستخدم Intune لإدارة تطبيقات الأجهزة المحمولة. كما أنه يوسع هذا الدعم للعملاء الذين يستخدمون حلول إدارة تنقل المؤسسات الأخرى، مع الاستمرار في استخدام Intune [لإدارة تطبيقات المحمول (MAM).](/mem/intune/apps/mam-faq)
    > - بالإضافة إلى ذلك، يدعم Microsoft Defender لنقطة النهاية بالفعل الأجهزة المسجلة باستخدام إدارة الأجهزة المحمولة Intune (MDM).

### <a name="network-requirements"></a>متطلبات الشبكة

- لكي يعمل Microsoft Defender لنقطة النهاية على Android عند الاتصال بشبكة، يجب تكوين جدار الحماية/الوكيل [لتمكين الوصول إلى عناوين URL للخدمة Microsoft Defender لنقطة النهاية](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

### <a name="system-requirements"></a>متطلبات النظام

- الهواتف المحمولة التي تعمل بنظام التشغيل Android 6.0 وما فوق. **الهواتف المحمولة التي تعمل بنظام التشغيل Android، وأجهزة الكمبيوتر اللوحي والأجهزة المحمولة الأخرى التي تعمل بنظام Android غير مدعومة حاليا.**
- يتم تنزيل تطبيق Intune Company Portal من [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) وتثبيته. تسجيل الجهاز مطلوب لفرض نهج توافق جهاز Intune.

### <a name="installation-instructions"></a>إرشادات التثبيت

يدعم Microsoft Defender لنقطة النهاية على Android التثبيت على كلا وضعي الأجهزة المسجلة - أوضاع مسؤول الأجهزة القديمة وAndroid Enterprise. **حاليا، يتم دعم الأجهزة المملوكة شخصيا مع ملف تعريف العمل وتسجيلات أجهزة المستخدم المدارة بالكامل المملوكة للشركة في Android Enterprise. سيتم الإعلان عن دعم أوضاع Android Enterprise الأخرى عندما تصبح جاهزا.**

- يتم نشر Microsoft Defender لنقطة النهاية على Android عبر Microsoft Intune (MDM). لمزيد من المعلومات، راجع [نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune](android-intune.md).
- تثبيت Microsoft Defender لنقطة النهاية على الأجهزة غير المسجلة باستخدام إدارة الأجهزة المحمولة Intune (MDM)، راجع [تكوين إشارات مخاطر Microsoft Defender لنقطة النهاية في نهج حماية التطبيقات (MAM).](android-configure-mam.md)

> [!NOTE]
> **يتوفر Microsoft Defender لنقطة النهاية على Android على [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx) الآن.**
>
> يمكنك الاتصال ب Google Play من Intune لنشر تطبيق Microsoft Defender لنقطة النهاية، عبر وضعي تسجيل مسؤول الجهاز وAndroid Enterprise.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>كيفية تكوين Microsoft Defender لنقطة النهاية على Android

تتوفر إرشادات حول كيفية تكوين Microsoft Defender لنقطة النهاية على ميزات Android في [تكوين Microsoft Defender لنقطة النهاية على ميزات Android](android-configure.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune](android-intune.md)
- [تكوين Microsoft Defender لنقطة النهاية على ميزات Android](android-configure.md)
- [أساسيات إدارة تطبيقات المحمول (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
