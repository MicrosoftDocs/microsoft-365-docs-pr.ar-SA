---
title: أحدث الميزات في Microsoft Defender لنقطة النهاية على Android
description: تعرف على التغييرات الرئيسية للإصدارات السابقة من Microsoft Defender لنقطة النهاية على Android.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، macos، whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 95c4d77014e31c748cc4bd6662a148810c01f79a
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825179"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>أحدث الميزات في Microsoft Defender لنقطة النهاية على Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

>[!NOTE]
>لم يعد Microsoft Defender مدعوما للإصدارات التي تقل عن 1.0.3011.0302. يطلب من المستخدمين الترقية إلى أحدث الإصدارات للحفاظ على أمان أجهزتهم.
للتحديث، يمكن للمستخدمين استخدام الخطوات التالية:
>1. في ملف تعريف العمل، انتقل إلى متجر التشغيل المدار.
>2. اضغط على أيقونة ملف التعريف في الزاوية العلوية اليسرى وحدد "إدارة التطبيقات والجهاز".
>3. حدد موقع MDE ضمن التحديثات المتوفرة وحدد التحديث.
>
>إذا واجهت أي مشاكل، [أرسل ملاحظات داخل التطبيق](/security/defender-endpoint/android-support-signin#send-in-app-feedback).

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-play-store"></a>Microsoft Defender لنقطة النهاية أصبح الآن Microsoft Defender في متجر Play

Microsoft Defender لنقطة النهاية متوفر الآن في **Microsoft Defender** في متجر التشغيل. مع هذا التحديث، سيكون التطبيق متوفرا كمعاينة **للمستهلكين في منطقة الولايات المتحدة** - استنادا إلى كيفية تسجيل الدخول إلى التطبيق باستخدام حساب العمل أو الحساب الشخصي الخاص بك، سيكون لديك حق الوصول إلى ميزات Microsoft Defender لنقطة النهاية أو ميزات Microsoft Defender للأفراد. الرجاء مراجعة [هذه المدونة](https://www.microsoft.com/microsoft-365/microsoft-defender-for-individuals) للحصول على مزيد من التفاصيل.

## <a name="threat-and-vulnerability-management"></a>إدارة المخاطر والثغرات الأمنية

في 25 يناير 2022، أعلنا عن التوفر العام لإدارة المخاطر والثغرات الأمنية على Android وiOS. لمزيد من التفاصيل، راجع [منشور «techcommunity» هنا](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>تغييرات الأذونات القادمة Microsoft Defender لنقطة النهاية تشغيل Android 11 أو إصدار أحدث (نوفمبر 2021)

إصدار الإصدار: 1.0.3501.0301 شهر الإصدار: إصدار نوفمبر 2021 Microsoft Defender لنقطة النهاية أصدر هذا التحديث الذي تطلبه [Google](https://developer.android.com/distribute/play-policies#APILevel30) للترقية إلى Android API 30. سيطالب هذا التغيير المستخدمين بالوصول إلى [إذن تخزين جديد](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play)، للأجهزة التي تعمل بنظام التشغيل Android 11 أو الإصدارات الأحدث. سيحتاج المستخدمون إلى قبول إذن التخزين الجديد هذا بمجرد تحديث تطبيق Defender بإصدار الإصدار 1.0.3501.0301 أو إصدار أحدث. سيضمن ذلك أن يعمل Defender for Endpoint's app security feature دون أي تعطيل. لمزيد من المعلومات، راجع الأقسام التالية.

**كيف سيؤثر ذلك على مؤسستك:** ستدخل هذه التغييرات حيز التنفيذ إذا كنت تستخدم Microsoft Defender لنقطة النهاية على الأجهزة التي تعمل بنظام التشغيل Android 11 أو الإصدارات الأحدث والمحدثة من Defender لنقطة النهاية لإصدار الإصدار 1.0.3501.0301 أو إصدار أحدث.

> [!NOTE]
> يتعذر على المسؤول تكوين أذونات التخزين الجديدة ل "الموافقة التلقائية" من خلال إدارة نقاط النهاية من Microsoft. سيحتاج المستخدم إلى اتخاذ إجراء لتوفير الوصول إلى هذا الإذن.

- **تجربة المستخدم:** سيتلقى المستخدمون إعلاما يشير إلى إذن مفقود لأمان التطبيق. إذا رفض المستخدم هذا الإذن، فسيتم إيقاف تشغيل وظيفة "أمان التطبيق" على الجهاز. إذا لم يقبل المستخدم الإذن أو يرفضه، فسيستمر في تلقي المطالبة عند إلغاء تأمين جهازه أو فتح التطبيق، حتى تتم الموافقة عليه.

> [!NOTE]
> إذا كانت مؤسستك تقوم بمعاينة ميزة "الحماية من العبث" وإذا لم يمنح المستخدم أذونات التخزين الجديدة في غضون 7 أيام من التحديث إلى الإصدار الأخير، فقد يفقد المستخدم إمكانية الوصول إلى موارد الشركة.

**ما تحتاج إلى القيام به للتحضير:**

قم بإعلام المستخدمين ومساعدتك (حسب الاقتضاء) بأن المستخدمين سيحتاجون إلى قبول الأذونات الجديدة عند مطالبتك بعد تحديث Defender لنقطة النهاية لإنشاء الإصدار 1.0.3501.0301 أو إصدار أحدث. لقبول الأذونات، يجب على المستخدمين:

1. اضغط على إعلام Defender لنقطة النهاية داخل التطبيق أو افتح تطبيق Defender لنقطة النهاية. سيرى المستخدمون شاشة تسرد الأذونات المطلوبة. ستفقد علامة اختيار خضراء بجوار إذن التخزين.

2. اضغط على **"ابدأ**".

3. اضغط على زر التبديل **للسماح بالوصول لإدارة كافة الملفات.**

4. الجهاز محمي الآن.

  > [!NOTE]
  > يسمح هذا الإذن Microsoft Defender لنقطة النهاية بالوصول إلى التخزين على جهاز المستخدم، مما يساعد على اكتشاف التطبيقات الضارة وغير المرغوب فيها وإزالتها. Microsoft Defender لنقطة النهاية الوصول إلى/فحص ملف حزمة تطبيق Android (.apk) فقط. على الأجهزة التي تحتوي على ملف تعريف العمل، يقوم Defender لنقطة النهاية بفحص الملفات المتعلقة بالعمل فقط.
