---
title: Microsoft Defender لنقطة النهاية - الدفاع عن تهديدات الأجهزة المحمولة
ms.reviewer: ''
description: نظرة عامة حول "الدفاع عن تهديدات الأجهزة المحمولة" في Microsoft Defender لنقطة النهاية
keywords: mobile, defender, Microsoft Defender for Endpoint, ios, mtd, android, security
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 07cd42d1ab1c6b945525b1e9ed4b463ee76376e1
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/14/2022
ms.locfileid: "63574657"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Microsoft Defender لنقطة النهاية - الدفاع عن تهديدات الأجهزة المحمولة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender ل Endpoint على نظامي التشغيل Android و iOS هو حل الدفاع ضد المخاطر على الأجهزة **المحمولة (MTD).** عادة ما تكون الشركات استباقية في حماية أجهزة الكمبيوتر الشخصية من نقاط الضعف والهجمة بينما غالبا ما تكون الأجهزة المحمولة غير محمية وغير محمية. حيث توفر حماية مضمنة للهواتف المحمولة مثل عزل التطبيقات ومخازن تطبيقات المستهلكين التي تم حمايتها، تبقى هذه الأنظمة الأساسية عرضة للهجمات المستندة إلى الويب أو الهجمات المتطورة الأخرى. مع استخدام المزيد من الموظفين للأجهزة للعمل والوصول إلى المعلومات الحساسة، من الضروري أن تنشر الشركات حل MTD لحماية الأجهزة ومواردك من الهجمات المعقدة بشكل متزايد على الهواتف المحمولة.

## <a name="key-capabilities"></a>الإمكانات الأساسية

يوفر Microsoft Defender ل Endpoint على نظامي التشغيل Android و iOS الإمكانات الأساسية أدناه، للحصول على معلومات حول أحدث الميزات والفوائد، اقرأ [إعلاناتنا](https://aka.ms/mdeblog).

<br>

|الإمكانية|الوصف|
|---|---|
|حماية ويب|مكافحة التصيد الاحتيالي وحظر اتصالات الشبكة غير الآمنة ودعم المؤشرات المخصصة.|
|الحماية من البرامج الضارة (Android-only)|المسح بحثا عن التطبيقات الضارة.|
|الكشف عن الكسر (iOS-only)|الكشف عن الأجهزة التي تم إلغاء تشغيلها.|
|إدارة المخاطر والنقاط الضعف (TVM) |تقييم نقاط الضعف للأجهزة المحمولة المجهزة. تفضل بزيارة [هذه الصفحة](next-gen-threat-and-vuln-mgt.md) لمعرفة المزيد حول إدارة المخاطر والثغرات الأمنية في Microsoft Defender ل Endpoint. *تجدر الإشارة إلى أن نقاط الضعف في نظام التشغيل iOS فقط معتمدة في هذه المعاينة.*|
|التنبيه الموحد|تنبيهات من كل الأنظمة الأساسية في وحدة تحكم أمان M365 الموحدة|
|الوصول الشرطي، تشغيل شرطي|منع الأجهزة المحكة من الوصول إلى موارد الشركة. يمكن أيضا إضافة Defender للإشارات إلى مخاطر نقطة النهاية إلى سياسات حماية التطبيق (MAM)|
|عناصر تحكم الخصوصية. في المعاينة (راجع الملاحظة أدناه)|قم بتكوين الخصوصية في تقارير التهديدات من خلال التحكم في البيانات المرسلة بواسطة Microsoft Defender لنقطة النهاية. *تجدر الإشارة إلى أن عناصر التحكم بالخصوصية متوفرة حاليا للأجهزة المسجلين فقط. سيتم إضافة عناصر التحكم للأجهزة غير الخاصة في وقت لاحق*|
|التكامل مع Microsoft فينال|يمكن التكامل مع Microsoft، حل بوابة VPN لتمكين الأمان والاتصال في تطبيق واحد. متوفر فقط على Android حاليا|

تتوفر كل هذه الإمكانات لحاملي تراخيص نقطة النهاية من Microsoft Defender. لمزيد من المعلومات، راجع [متطلبات الترخيص](minimum-requirements.md#licensing-requirements).


## <a name="overview-and-deploy"></a>نظرة عامة ونشر

يمكن نشر Microsoft Defender لنقطة النهاية على الأجهزة المحمولة عبر إدارة نقاط النهاية من Microsoft (MEM). شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول إمكانات MTD ونشرها:

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

### <a name="deploy"></a>نشر

يلخص الجدول التالي كيفية نشر Microsoft Defender ل Endpoint على نظامي التشغيل Android و iOS. للحصول على وثائق مفصلة، راجع 
- [نظرة عامة حول Microsoft Defender لنقطة النهاية على نظام التشغيل Android](microsoft-defender-endpoint-android.md)، و
- [نظرة عامة حول Microsoft Defender لنقطة النهاية على نظام التشغيل iOS](microsoft-defender-endpoint-ios.md)

**Android**

|نوع التسجيل     |التفاصيل      |
|--------------------|-------------|
|Android Enterprise مع Intune Unified إدارة نقاط النهاية (إدارة نقاط النهاية من Microsoft)|[النشر على الأجهزة التي تم تسجيلها في Android Enterprise](android-intune.md#deploy-on-android-enterprise-enrolled-devices)|
|مسؤول الجهاز مع Intune Unified إدارة نقاط النهاية (إدارة نقاط النهاية من Microsoft)|[النشر على الأجهزة التي تم تسجيلها في "مسؤول الجهاز"](android-intune.md#deploy-on-device-administrator-enrolled-devices)|
|أجهزة BYOD OR غير المدارة التي يديرها مديرو نقاط النهاية الموحدون / نهج حماية تطبيق الإعداد (MAM)|[تكوين إشارات مخاطر Defender في نهج حماية التطبيق (MAM)](android-configure-mam.md)|

**iOS**

|نوع التسجيل     |التفاصيل      |
|--------------------|-------------|
|الأجهزة التي تم التعامل معها باستخدام Intune Unified إدارة نقاط النهاية (إدارة نقاط النهاية من Microsoft)|1. [نشر تطبيق متجر iOS](ios-install.md)<br/>2. [إعداد حماية ويب بدون VPN للأجهزة التي تعمل ب iOS](ios-install.md#complete-deployment-for-supervised-devices)|
|الأجهزة غير المجهزة (BYOD) والمسجلة مع Intune UEM (إدارة نقاط النهاية من Microsoft)|[نشر تطبيق متجر iOS](ios-install.md)|
|أجهزة BYOD OR غير المدارة المدارة بواسطة نهج حماية تطبيق UEMs /Setup (MAM)|[تكوين إشارات مخاطر Defender في نهج حماية التطبيق (MAM)](ios-install-unmanaged.md)|

### <a name="end-user-onboarding"></a>ا متنبها للمستخدم النهائي

- [تكوين اللوحة](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview) التي تعمل باللمس الصفري للأجهزة التي تم تسجيلها في iOS: يمكن للمسؤولين تكوين تثبيت بدون لمس لتركيب Microsoft Defender لنقطة النهاية بصمت على أجهزة iOS المسجله دون مطالبة المستخدم بفتح التطبيق. 

- [تكوين الوصول الشرطي](android-configure.md#conditional-access-with-defender-for-endpoint-on-android) لفرض تهيئة المستخدمين: يمكن تطبيق ذلك لضمان وصول المستخدمين النهائيين إلى تطبيق Microsoft Defender for Endpoint بعد النشر. شاهد هذا الفيديو للحصول على عرض توضيحي سريع حول تكوين الوصول الشرطي باستخدام إشارات خطر Defender for Endpoint. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>تبسيط الboarding

- [iOS - Zero-Touch Onboard](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview)
- [Android Enterprise - الإعداد دائما على VPN](android-intune.md#auto-setup-of-always-on-vpn).
- [iOS - الإعداد التلقائي لملف تعريف VPN](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="pilot-evaluation"></a>تقييم تجريبي

أثناء تقييم الدفاع عن تهديدات الأجهزة المحمولة باستخدام Microsoft Defender ل Endpoint، يمكنك التحقق من تحقيق معايير معينة قبل المتابعة لنشر الخدمة على مجموعة أكبر من الأجهزة. يمكنك تحديد معايير الخروج والتأكد من أنها راضية قبل النشر على نطاق واسع.

يساعد ذلك على تقليل المشاكل المحتملة التي قد تنشأ أثناء طرح الخدمة. فيما يلي بعض الاختبارات ومعايير الخروج التي قد تساعدك:

- تظهر الأجهزة في قائمة مخزون الأجهزة: بعد نجاح تشغيل Defender for Endpoint على الجهاز المحمول، تحقق من إدراج الجهاز في "مخزون الجهاز" في وحدة [التحكم في الأمان](https://security.microsoft.com).

- تشغيل اختبار الكشف عن البرامج الضارة على جهاز يعمل بنظام التشغيل Android: قم بتثبيت أي تطبيق اختباري للفيروسات من متجر Google play وتحقق من اكتشافه بواسطة Microsoft Defender لنقطة النهاية. فيما يلي مثال للتطبيق الذي يمكن استخدامه لهذا الاختبار: [اختبار الفيروسات](https://play.google.com/store/apps/details?id=com.androidantivirus.testvirus). تجدر الإشارة إلى أنه على Android Enterprise مع ملف تعريف العمل، يتم دعم ملف تعريف العمل فقط.

- تشغيل اختبار التصيد الاحتيالي: استعرض https://smartscreentestratings2.net بحثا عن Microsoft Defender لنقطة النهاية وتحقق من حظره. تجدر الإشارة إلى أنه على Android Enterprise مع ملف تعريف العمل، يتم دعم ملف تعريف العمل فقط.

- تظهر التنبيهات في لوحة المعلومات: تحقق من ظهور التنبيهات لاختبارات الكشف أعلاه على [وحدة التحكم في الأمان](https://security.microsoft.com).

## <a name="configure"></a>تكوين

- [تكوين ميزات Android](android-configure.md)
- [تكوين ميزات iOS](ios-configure-features.md)
- [تكوين حماية ويب بدون VPN للأجهزة التي تعمل ب iOS](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="resources"></a>الموارد

- [Microsoft Defender لنقطة النهاية على نظام التشغيل Android](microsoft-defender-endpoint-android.md)
- [Microsoft Defender لنقطة النهاية على نظام التشغيل iOS](microsoft-defender-endpoint-ios.md)
- ابق على اطلاع على الإصدارات القادمة من خلال قراءة [إعلاناتنا](https://aka.ms/mdeblog).

