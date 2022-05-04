---
title: Microsoft Defender لنقطة النهاية - الدفاع عن تهديدات الجوال
ms.reviewer: ''
description: نظرة عامة على الدفاع عن تهديدات الأجهزة المحمولة في Microsoft Defender لنقطة النهاية
keywords: الأجهزة المحمولة، و defender، Microsoft Defender لنقطة النهاية، وios، و mtd، وandroid، والأمان
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
ms.openlocfilehash: 83da2034a04da85849383700204174110ceffa57
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188515"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Microsoft Defender لنقطة النهاية - الدفاع عن تهديدات الجوال

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender لنقطة النهاية على Android وiOS هو **حل الدفاع عن تهديدات الأجهزة المحمولة (MTD).** عادة ما تكون الشركات استباقية في حماية أجهزة الكمبيوتر الشخصية من الثغرات الأمنية والهجمات بينما غالبا ما تكون الأجهزة المحمولة غير مراقبة وغير محمية. حيث تتمتع الأنظمة الأساسية للأجهزة المحمولة بحماية مضمنة مثل عزل التطبيقات ومخازن تطبيقات المستهلكين المدققة، تظل هذه الأنظمة الأساسية عرضة للهجمات المستندة إلى الويب أو غيرها من الهجمات المتطورة. مع استخدام المزيد من الموظفين للأجهزة للعمل والوصول إلى المعلومات الحساسة، من الضروري أن تقوم الشركات بنشر حل MTD لحماية الأجهزة ومواردك من الهجمات المتطورة بشكل متزايد على الأجهزة المحمولة.

## <a name="key-capabilities"></a>القدرات الرئيسية

يوفر Microsoft Defender لنقطة النهاية على Android وiOS القدرات الرئيسية أدناه، للحصول على معلومات حول أحدث الميزات والفوائد، اقرأ [إعلاناتنا](https://aka.ms/mdeblog).

<br>

|القدره|الوصف|
|---|---|
|حماية الويب|مكافحة التصيد الاحتيالي، وحظر اتصالات الشبكة غير الآمنة، ودعم المؤشرات المخصصة.|
|الحماية من البرامج الضارة (Android فقط)|المسح بحثا عن تطبيقات ضارة.|
|الكشف عن المقاطعة (iOS فقط)|الكشف عن الأجهزة التي تم خرقها.|
|إدارة المخاطر والثغرات الأمنية (TVM) |تقييم الثغرات الأمنية للأجهزة المحمولة التي تم إلحاقها. تفضل بزيارة هذه [الصفحة](next-gen-threat-and-vuln-mgt.md) لمعرفة المزيد حول إدارة المخاطر والثغرات الأمنية في Microsoft Defender لنقطة النهاية. *لاحظ أنه على نظام التشغيل iOS يتم دعم الثغرات الأمنية في نظام التشغيل فقط في هذه المعاينة.*|
|تنبيه موحد|تنبيهات من جميع الأنظمة الأساسية في وحدة تحكم أمان M365 الموحدة|
|الوصول المشروط، التشغيل الشرطي|حظر الأجهزة المحفوفة بالمخاطر من الوصول إلى موارد الشركة. يمكن أيضا إضافة إشارات مخاطر Defender لنقطة النهاية إلى نهج حماية التطبيقات (MAM)|
|عناصر التحكم في الخصوصية. في المعاينة (راجع الملاحظة أدناه)|تكوين الخصوصية في تقارير التهديدات عن طريق التحكم في البيانات المرسلة من قبل Microsoft Defender لنقطة النهاية. *لاحظ أن عناصر التحكم في الخصوصية متوفرة حاليا فقط للأجهزة المسجلة. ستتم إضافة عناصر التحكم للأجهزة غير المسجلة لاحقا*|
|التكامل مع Microsoft Tunnel|يمكن التكامل مع Microsoft Tunnel، وهو حل بوابة VPN لتمكين الأمان والاتصال في تطبيق واحد. متوفر على Android وهو متوفر الآن بشكل عام على نظام التشغيل iOS أيضا.|

تتوفر جميع هذه الإمكانات لحاملي التراخيص Microsoft Defender لنقطة النهاية. لمزيد من المعلومات، راجع [متطلبات الترخيص](minimum-requirements.md#licensing-requirements).


## <a name="overview-and-deploy"></a>نظرة عامة ونشر

يمكن نشر Microsoft Defender لنقطة النهاية على الهاتف المحمول عبر إدارة نقاط النهاية من Microsoft (MEM). شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول قدرات MTD والنشر:

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

### <a name="deploy"></a>النشر

يلخص الجدول التالي كيفية نشر Microsoft Defender لنقطة النهاية على Android وiOS. للحصول على وثائق مفصلة، راجع 
- [نظرة عامة على Microsoft Defender لنقطة النهاية على Android](microsoft-defender-endpoint-android.md)، و
- [نظرة عامة Microsoft Defender لنقطة النهاية على iOS](microsoft-defender-endpoint-ios.md)

**الروبوت**

|نوع التسجيل     |التفاصيل      |
|--------------------|-------------|
|Android Enterprise مع إدارة نقاط النهاية موحدة Intune (إدارة نقاط النهاية من Microsoft)|[النشر على الأجهزة المسجلة في Android Enterprise](android-intune.md#deploy-on-android-enterprise-enrolled-devices)|
|مسؤول الجهاز مع إدارة نقاط النهاية موحدة Intune (إدارة نقاط النهاية من Microsoft)|[النشر على الأجهزة المسجلة في مسؤول الجهاز](android-intune.md#deploy-on-device-administrator-enrolled-devices)|
|أجهزة BYOD OR غير المدارة التي يديرها مديرو نقاط النهاية الموحدة / نهج حماية تطبيق الإعداد (MAM)|[تكوين إشارات مخاطر Defender في نهج حماية التطبيقات (MAM)](android-configure-mam.md)|

**دائره الرقابه الداخليه**

|نوع التسجيل     |التفاصيل      |
|--------------------|-------------|
|الأجهزة الخاضعة للإشراف مع إدارة نقاط النهاية الموحدة Intune (إدارة نقاط النهاية من Microsoft)|1. [النشر كتطبيق متجر iOS](ios-install.md)<br/>2. [إعداد حماية الويب بدون VPN لأجهزة iOS الخاضعة للإشراف](ios-install.md#complete-deployment-for-supervised-devices)|
|الأجهزة غير الخاضعة للإشراف (BYOD) المسجلة مع Intune UEM (إدارة نقاط النهاية من Microsoft)|[النشر كتطبيق متجر iOS](ios-install.md)|
|أجهزة BYOD OR غير المدارة التي تديرها UEMs / إعداد نهج حماية التطبيق (MAM)|[تكوين إشارات مخاطر Defender في نهج حماية التطبيقات (MAM)](ios-install-unmanaged.md)|

### <a name="end-user-onboarding"></a>إلحاق المستخدم النهائي

- [تكوين إعداد بدون لمس للأجهزة المسجلة في iOS](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint): يمكن للمسؤولين تكوين تثبيت بدون لمس لإلحاق Microsoft Defender لنقطة النهاية بصمت على أجهزة iOS المسجلة دون مطالبة المستخدم بفتح التطبيق. 

- [تكوين الوصول المشروط لفرض إلحاق المستخدم](android-configure.md#conditional-access-with-defender-for-endpoint-on-android): يمكن تطبيق هذا لضمان إلحاق المستخدمين النهائيين بتطبيق Microsoft Defender لنقطة النهاية بعد النشر. شاهد هذا الفيديو للحصول على عرض توضيحي سريع حول تكوين الوصول المشروط باستخدام إشارات مخاطر Defender لنقطة النهاية. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>تبسيط الإلحاق

- [iOS - Zero-Touch Onboard](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint)
- [Android Enterprise - إعداد VPN دائما.](android-intune.md#auto-setup-of-always-on-vpn)
- [iOS - الإعداد التلقائي لملف تعريف VPN](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="pilot-evaluation"></a>التقييم التجريبي

في أثناء تقييم الدفاع عن تهديدات الأجهزة المحمولة باستخدام Microsoft Defender لنقطة النهاية، يمكنك التحقق من استيفاء معايير معينة قبل المتابعة لنشر الخدمة على مجموعة أكبر من الأجهزة. يمكنك تحديد معايير الخروج والتأكد من أنها مستوفية قبل النشر على نطاق واسع.

يساعد ذلك على تقليل المشكلات المحتملة التي قد تنشأ أثناء طرح الخدمة. فيما يلي بعض الاختبارات ومعايير الخروج التي قد تساعد:

- تظهر الأجهزة في قائمة مخزون الأجهزة: بعد نجاح عملية إلحاق Defender لنقطة النهاية على الجهاز المحمول، تحقق من أن الجهاز مدرج في "مخزون الجهاز" في [وحدة تحكم الأمان](https://security.microsoft.com).

- قم بتشغيل اختبار الكشف عن البرامج الضارة على جهاز يعمل بنظام Android: قم بتثبيت أي تطبيق فيروسات اختبار من متجر Google play وتحقق من اكتشافه بواسطة Microsoft Defender لنقطة النهاية. فيما يلي مثال على التطبيق الذي يمكن استخدامه لهذا الاختبار: [اختبار الفيروسات](https://play.google.com/store/apps/details?id=com.androidantivirus.testvirus). لاحظ أنه على Android Enterprise مع ملف تعريف العمل، يتم دعم ملف تعريف العمل فقط.

- تشغيل اختبار التصيد الاحتيالي: استعرض وتحقق https://smartscreentestratings2.net من حظره من قبل Microsoft Defender لنقطة النهاية. لاحظ أنه على Android Enterprise مع ملف تعريف العمل، يتم دعم ملف تعريف العمل فقط.

- تظهر التنبيهات في لوحة المعلومات: تحقق من ظهور التنبيهات لاختبارات الكشف أعلاه على [وحدة تحكم الأمان](https://security.microsoft.com).

## <a name="configure"></a>تكوين

- [تكوين ميزات Android](android-configure.md)
- [تكوين ميزات iOS](ios-configure-features.md)
- [تكوين حماية الويب بدون VPN لأجهزة iOS الخاضعة للإشراف](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="resources"></a>الموارد

- [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Android](microsoft-defender-endpoint-android.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية على iOS](microsoft-defender-endpoint-ios.md)
- ابق على اطلاع على الإصدارات القادمة من خلال قراءة [إعلاناتنا](https://aka.ms/mdeblog).

