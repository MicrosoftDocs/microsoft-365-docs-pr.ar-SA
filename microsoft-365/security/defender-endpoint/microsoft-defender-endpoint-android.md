---
title: Microsoft Defender لنقطة النهاية على نظام التشغيل Android
ms.reviewer: ''
description: يصف كيفية تثبيت Microsoft Defender لنقطة النهاية واستخدامه على نظام التشغيل Android
keywords: microsoft، defender، Microsoft Defender ل Endpoint، android، التثبيت، النشر، إزالة التثبيت، intune
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
ms.openlocfilehash: 7d4e553e89f83f9b641367bb4037b4eb7da21f8b
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63571595"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender لنقطة النهاية على نظام التشغيل Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يصف هذا الموضوع كيفية تثبيت Defender لنقطة النهاية وتكوينه وتحديثه واستخدامه على Android.

> [!CAUTION]
> من المرجح أن يؤدي تشغيل منتجات حماية نقاط نهاية أخرى من جهة خارجية إلى جانب Defender for Endpoint على Android إلى حدوث مشاكل في الأداء وأخطاء في النظام لا يمكن التنبؤ بها.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>كيفية تثبيت Microsoft Defender لنقطة النهاية على نظام التشغيل Android

### <a name="prerequisites"></a>المتطلبات الأساسية

- **بالنسبة للمستخدمين النهائيين**:
  - ترخيص Microsoft Defender لنقطة النهاية المعين إلى المستخدم (المستخدمين) النهائيين للتطبيق. راجع [متطلبات ترخيص نقطة النهاية ل Microsoft Defender](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)
  - Intune Company Portal التطبيق من [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) وهو متوفر على جهاز Android.
  - بالإضافة إلى ذلك، يمكن تسجيل الجهاز (الأجهزة[](/mem/intune/user-help/enroll-device-android-company-portal)) عبر تطبيق Intune Company Portal لفرض سياسات توافق أجهزة Intune. يتطلب ذلك تعيين ترخيص Microsoft Intune للمستخدم.
  - لمزيد من المعلومات حول كيفية تعيين التراخيص، راجع [تعيين التراخيص للمستخدمين](/azure/active-directory/users-groups-roles/licensing-groups-assign).

- **للمسؤولين**
   - الوصول إلى Microsoft 365 Defender الإلكتروني.
   - الوصول [إدارة نقاط النهاية من Microsoft مركز الإدارة إلى](https://go.microsoft.com/fwlink/?linkid=2109431)
       - نشر التطبيق إلى مجموعات المستخدمين المسجلين في مؤسستك.
       - تكوين إشارات مخاطر نقطة النهاية ل Microsoft Defender في نهج حماية التطبيق.
  
    > [!NOTE]
    > - يعمل Microsoft Defender ل Endpoint الآن على توسيع الحماية إلى بيانات المؤسسة ضمن تطبيق مدار (MAM) للأجهزة غير المسجلين باستخدام إدارة أجهزة المحمول (MDM)، ولكنها تستخدم Intune لإدارة تطبيقات الأجهزة المحمولة. كما أنه يوسع هذا الدعم ليشمل العملاء الذين يستخدمون حلولا أخرى لإدارة تنقل المؤسسات، مع استخدام Intune لإدارة تطبيقات الأجهزة المحمولة [(MAM).](/mem/intune/apps/mam-faq)
    > - بالإضافة إلى ذلك، يدعم Microsoft Defender for Endpoint بالفعل الأجهزة التي تم تسجيلها باستخدام إدارة أجهزة Intune المحمولة (MDM).


### <a name="network-requirements"></a>متطلبات الشبكة

- لكي يعمل Microsoft Defender ل Endpoint على نظام التشغيل Android عند الاتصال بشبكة، يجب تكوين جدار الحماية/الوكيل لتمكين الوصول إلى عناوين URL لخدمة [Microsoft Defender لنقطة النهاية](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

### <a name="system-requirements"></a>متطلبات النظام

- الهواتف المحمولة التي تعمل بنظام التشغيل Android 6.0 وال إصدار أعلى. **الهواتف المحمولة التي تعمل بنظام التشغيل Android، وأجهزة الكمبيوتر اللوحي، والأجهزة المحمولة الأخرى التي تعمل بنظام Android غير معتمدة حاليا.**
- Intune Company Portal التطبيق من [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) وتثبيته. يلزم تسجيل الجهاز لكي يتم فرض سياسات توافق أجهزة Intune.

### <a name="installation-instructions"></a>إرشادات التثبيت

يدعم Microsoft Defender ل Endpoint على Android التثبيت على كلا وضعي الأجهزة المسجلين - الأوضاع القديمة "مسؤول الجهاز" و"Android Enterprise". **حاليا، يتم دعم الأجهزة المملوكة شخصيا مع ملف تعريف العمل والتسجيلات التي تملكها الشركة بشكل كامل لأجهزة المستخدم المدارة بالكامل في Android Enterprise. سيتم الإعلان عن دعم أوضاع Android Enterprise الأخرى عندما تكون جاهزا.**

- يتم نشر Microsoft Defender لنقطة النهاية على Android عبر Microsoft Intune (MDM). لمزيد من المعلومات، راجع [نشر Microsoft Defender ل Endpoint على Android باستخدام Microsoft Intune](android-intune.md).
- تثبيت Microsoft Defender لنقطة النهاية على الأجهزة التي لم يتم تسجيلها باستخدام إدارة أجهزة Intune للأجهزة المحمولة (MDM)، راجع تكوين إشارات مخاطر نقطة النهاية ل Microsoft Defender في نهج حماية التطبيق [(MAM).](android-configure-mam.md)

> [!NOTE]
> **يتوفر Microsoft Defender ل Endpoint على Android على [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx) الآن.**
>
> يمكنك الاتصال ب Google Play من Intune لنشر تطبيق Microsoft Defender for Endpoint، عبر أوضاع الإدخال في مسؤول الجهاز وAndroid Enterprise.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>كيفية تكوين Microsoft Defender لنقطة النهاية على نظام التشغيل Android

تتوفر إرشادات حول كيفية تكوين Microsoft Defender لنقطة النهاية على ميزات Android في [تكوين Microsoft Defender لنقطة النهاية على ميزات Android](android-configure.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نشر Microsoft Defender ل Endpoint على Android باستخدام Microsoft Intune](android-intune.md)
- [تكوين Microsoft Defender لنقطة النهاية على ميزات Android](android-configure.md)
- [أساسيات إدارة تطبيقات الأجهزة المحمولة (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
