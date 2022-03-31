---
title: ما الجديد في Microsoft Defender ل Endpoint على نظام التشغيل Android
description: تعرف على التغييرات الرئيسية للإصدارات السابقة من Microsoft Defender ل Endpoint على Android.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، التثبيت، macos، whatsnew
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
ms.openlocfilehash: d250fefbdcc2c268563b6321ee7d91eca4881063
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63578536"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>ما الجديد في Microsoft Defender ل Endpoint على نظام التشغيل Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-play-store"></a>أصبح Microsoft Defender for Endpoint الآن Microsoft Defender في متجر Play

يتوفر الآن Microsoft Defender ل Endpoint ك **Microsoft Defender** في متجر play. باستخدام هذا التحديث، سيكون التطبيق متوفرا كمعاينة للمستهلكين في منطقة الولايات **المتحدة - استنادا** إلى كيفية تسجيل الدخول إلى التطبيق باستخدام حساب العمل أو الحساب الشخصي، سيكون لديك حق الوصول إلى ميزات Microsoft Defender ل Endpoint أو إلى ميزات Microsoft Defender للأفراد. الرجاء الاطلاع [على هذه المدونة](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals) للحصول على مزيد من التفاصيل.

## <a name="threat-and-vulnerability-management"></a>إدارة المخاطر والنقاط الضعف

في 25 يناير 2022، أعلنا عن التوفر العام لإدارة المخاطر والضعف على نظامي التشغيل Android و iOS. لمزيد من التفاصيل، راجع [منشور techcommunity هنا](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>تغييرات الأذونات القادمة ل Microsoft Defender ل Endpoint الذي يعمل بنظام التشغيل Android 11 أو إصدار لاحق (نوفمبر 2021)

إصدار الإصدار: 1.0.3501.0301 شهر الإصدار: إصدار نوفمبر 2021 Microsoft Defender لنقطة النهاية هذا التحديث الذي تطلبه [Google](https://developer.android.com/distribute/play-policies#APILevel30) للترقية إلى Android API 30. سيطالب هذا التغيير المستخدمين الذين يسعون للوصول إلى [إذن تخزين](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play) جديد، للأجهزة التي تعمل بنظام Android 11 أو إصدار لاحق. يجب على المستخدمين قبول إذن التخزين الجديد هذا بمجرد تحديثهم لتطبيق Defender باستخدام إصدار الإصدار 1.0.3501.0301 أو الإصدارات اللاحقة. سيضمن ذلك عمل ميزة أمان تطبيق Defender for Endpoint دون أي انقطاع. لمزيد من المعلومات، راجع المقاطع التالية.

**كيف سيؤثر ذلك على مؤسستك:** ستتخذ هذه التغييرات حيز التنفيذ إذا كنت تستخدم Microsoft Defender لنقطة النهاية على الأجهزة التي تعمل بنظام التشغيل Android 11 أو إصدار أحدث ومحدثة ل Defender for Endpoint الإصدار 1.0.3501.0301 أو إصدار أحدث.

> [!NOTE]
> يتعذر على المسؤول تكوين أذونات التخزين الجديدة ل "الموافقة التلقائية" من خلال إدارة نقاط النهاية من Microsoft. يجب على المستخدم اتخاذ إجراء لتوفير حق الوصول إلى هذا الإذن.

- **تجربة المستخدم:** سيتلقى المستخدمون إعلاما يشير إلى وجود إذن مفقود لأمن التطبيق. إذا قام المستخدم برفض هذا الإذن، سيتم إيقاف تشغيل وظيفة "أمان التطبيق" على الجهاز. إذا لم يقبل المستخدم الإذن أو يرفضه، سيستمر في تلقي المطالبة عند إلغاء تأمين جهازه أو فتح التطبيق، حتى يتم الموافقة عليه.

> [!NOTE]
> إذا كانت مؤسستك تقوم بمعاينة ميزة 'الحماية من العبث' وإذا لم يمنح المستخدم أذونات التخزين الجديدة في غضون 7 أيام من التحديث إلى الإصدار الأخير، فقد يفقد المستخدم إمكانية الوصول إلى موارد الشركة.

**ما يجب فعله للتحضير:**

قم بإعلام المستخدمين ومساعديك (حسب الاقتضاء) بأنه يجب على المستخدمين قبول الأذونات الجديدة عند مطالبتك بذلك بعد تحديث Defender for Endpoint للإصدار 1.0.3501.0301 أو الإصدارات الأحدث. لقبول الأذونات، يجب على المستخدمين:

1. اضغط على إعلام Defender for Endpoint داخل التطبيق أو افتح تطبيق Defender for Endpoint. سيشاهد المستخدمون شاشة تسرد الأذونات المطلوبة. ستفقد علامة الاختيار الخضراء بجانب إذن التخزين.

2. اضغط **على بدء**.

3. اضغط على زر تبديل السماح **بالوصول لإدارة كل الملفات.**

4. الجهاز محمي الآن.

  > [!NOTE]
  > يسمح هذا الإذن ل Microsoft Defender لنقطة النهاية بالوصول إلى مساحة التخزين على جهاز المستخدم، مما يساعد على الكشف عن التطبيقات الضارة وغير المرغوب فيها وإزالتها. يقوم Microsoft Defender for Endpoint بالوصول/المسح الضوئي لملف حزمة تطبيق Android (apk.) فقط. على الأجهزة التي بها ملف تعريف العمل، يقوم Defender for Endpoint بفحص الملفات ذات الصلة بالعمل فقط.
