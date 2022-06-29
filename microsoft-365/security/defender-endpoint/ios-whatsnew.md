---
title: أحدث الميزات في Microsoft Defender لنقطة النهاية على iOS
description: تعرف على التغييرات الرئيسية للإصدارات السابقة من Microsoft Defender لنقطة النهاية على iOS.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، macos، whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: sunasing
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: b94c52feb88703ac28f9cd72267d7fa8c952a741
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489958"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>أحدث الميزات في Microsoft Defender لنقطة النهاية على iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="network-protection"></a>حماية الشبكة
حماية الشبكة على Microsoft Defender لنقطة النهاية الآن في المعاينة العامة. توفر حماية الشبكة الحماية من التهديدات Wi-Fi المحتالة ذات الصلة، والأجهزة المحتالة مثل أجهزة الأناناس وإعلام المستخدم إذا تم الكشف عن تهديد ذي صلة. سيرى المستخدمون أيضا تجربة موجهة للاتصال بشبكات آمنة وتغيير الشبكات عند الاتصال باتصال غير آمن.

يتضمن العديد من عناصر تحكم المسؤول لتوفير المرونة، مثل القدرة على تكوين الميزة من داخل مركز إدارة نقاط النهاية مسؤول Microsoft. يمكن للمسؤولين أيضا تمكين عناصر التحكم في الخصوصية لتكوين البيانات التي يتم إرسالها بواسطة Defender لنقطة النهاية من أجهزة iOS. لمزيد من المعلومات، اقرأ [تكوين حماية الشبكة](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-network-protection).

تم تمكين حماية الشبكة لنظام التشغيل iOS بالفعل للمستأجر الخاص بك. يمكن للمستخدمين النهائيين الذين يختبرون ميزة حماية الشبكة تثبيت إصدار المعاينة من التطبيق عبر TestFlight. استعرض وصولا إلى https://aka.ms/mdeiospp جهاز iOS. سيطالبك هذا بتثبيت تطبيق TestFlight على جهازك أو فتح TestFlight في حالة تثبيته بالفعل. في تطبيق TestFlight، اتبع الإرشادات التي تظهر على الشاشة لتثبيت نقطة نهاية Microsoft Defender. الرجاء التحقق من أن رقم إصدار MDE هو 1.1.29270104.

## <a name="integration-with-tunnel"></a>التكامل مع النفق
يمكن Microsoft Defender لنقطة النهاية على iOS الآن التكامل مع Microsoft Tunnel، وهو حل بوابة VPN لتمكين الأمان والاتصال في تطبيق واحد.  يوفر التكامل مع Tunnel تجربة VPN أبسط وآمنة على iOS مع تطبيق واحد فقط. كانت هذه الميزة متوفرة مسبقا على Android فقط. لمزيد من التفاصيل، [راجع منشور «techcommunity» هنا](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995)

## <a name="improved-experience-on-supervised-ios-devices"></a>تجربة محسنة على أجهزة iOS الخاضعة للإشراف

يتمتع Microsoft Defender لنقطة النهاية على iOS الآن بقدرة متخصصة على أجهزة iOS/iPadOS الخاضعة للإشراف، نظرا إلى زيادة قدرات الإدارة التي يوفرها النظام الأساسي على هذه الأنواع من الأجهزة. كما يمكن أن توفر حماية الويب **دون إعداد VPN محلي على الجهاز**. وهذا يعطي المستخدمين النهائيين تجربة سلسة مع استمرار حمايتهم من التصيد الاحتيالي والهجمات الأخرى المستندة إلى الويب. للحصول على التفاصيل، تفضل بزيارة [هذه الوثائق](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Microsoft Defender لنقطة النهاية أصبح الآن Microsoft Defender في متجر التطبيقات

يتوفر Microsoft Defender لنقطة النهاية الآن ك **Microsoft Defender** في متجر التطبيقات. مع هذا التحديث، سيكون التطبيق متوفرا كمعاينة **للمستهلكين في منطقة الولايات المتحدة**. استنادا إلى كيفية تسجيل الدخول إلى التطبيق باستخدام حساب العمل أو الحساب الشخصي، سيكون لديك حق الوصول إلى ميزات Microsoft Defender لنقطة النهاية أو ميزات Microsoft Defender للأفراد. لمزيد من المعلومات، راجع [هذه المدونة](https://www.microsoft.com/microsoft-365/microsoft-defender-for-individuals).

## <a name="threat-and-vulnerability-management"></a>إدارة المخاطر والثغرات الأمنية

في 25 يناير 2022، أعلنا عن التوفر العام لإدارة المخاطر والثغرات الأمنية على Android وiOS. لمزيد من التفاصيل، راجع [منشور «techcommunity» هنا](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="1128250101"></a>1.1.28250101
- **التكامل مع Tunnel** - يمكن Microsoft Defender لنقطة النهاية على iOS الآن التكامل مع Microsoft Tunnel، وهو حل بوابة VPN لتمكين الأمان والاتصال في تطبيق واحد. لمزيد من المعلومات، راجع [نظرة عامة على نفق Microsoft](/mem/intune/protect/microsoft-tunnel-overview).
- يتوفر **الإعداد بدون لمس لأجهزة iOS المسجلة** من خلال Microsoft إدارة نقاط النهاية (Intune) بشكل عام. لمزيد من المعلومات، راجع [عدم إلحاق Microsoft Defender لنقطة النهاية باللمس](/microsoft-365/security/defender-endpoint/ios-install#zero-touch-onboarding-of-microsoft-defender-for-endpoint).
- إصلاحات الأخطاء.


## <a name="1124210103"></a>1.1.24210103

- تم حل مشكلات الاتصال بالإنترنت على الأجهزة الخاضعة للإشراف. لمزيد من المعلومات، راجع [Deploy Defender لنقطة النهاية على أجهزة iOS المسجلة](ios-install.md).
- إصلاحات الأخطاء.

## <a name="1123250104"></a>1.1.23250104

- تحسينات الأداء - اختبار أداء البطارية باستخدام هذا الإصدار وإعلامنا بملاحظاتك.
- **إعداد بدون لمس لأجهزة iOS المسجلة** - مع هذا الإصدار، تمت إضافة معاينة تشغيل Zero-touch للأجهزة المسجلة من خلال Microsoft إدارة نقاط النهاية (Intune). لمزيد من المعلومات، راجع هذه [الوثائق](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint) للحصول على مزيد من التفاصيل حول الإعداد والتكوين.
- **عناصر التحكم في الخصوصية** - تكوين عناصر التحكم في الخصوصية لتقرير تنبيه التصيد الاحتيالي. لمزيد من المعلومات، راجع [تكوين ميزات iOS](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- إصلاحات الأخطاء وتحسينات الأداء 
  - تم إجراء تحسينات الأداء في هذا الإصدار. اختبر أداء البطارية باستخدام هذا الإصدار وأخبرنا بملاحظاتك.

## <a name="1120240103"></a>1.1.20240103
- بطاقة Device Health - تقوم بطاقة Device Health بإعلام المستخدمين النهائيين بأي تحديثات برامج معلقة.
- تحسينات قابلية الاستخدام - يمكن للمستخدمين النهائيين الآن تعطيل Defender لنقطة النهاية VPN من تطبيق Microsoft Defender نفسه. قبل هذا التحديث، كان على المستخدمين النهائيين تعطيل VPN فقط من تطبيق الإعدادات.
- إصلاحات الأخطاء.

## <a name="1120020101"></a>1.1.20020101
- تحسينات أسلوب عمل المستخدم - Microsoft Defender لنقطة النهاية له مظهر جديد.
- إصلاحات الأخطاء.

## <a name="1117240101"></a>1.1.17240101
- يتوفر دعم إدارة تطبيقات المحمول (MAM) عبر Intune بشكل عام مع هذا الإصدار. لمزيد من المعلومات، راجع [إشارات المخاطر Microsoft Defender لنقطة النهاية المتوفرة لنهج حماية التطبيقات](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **الكشف عن الكسر من التهيؤ** متاح بشكل عام. لمزيد من المعلومات، راجع [إعداد نهج الوصول المشروط استنادا إلى إشارات مخاطر الجهاز](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- يتوفر **الإعداد التلقائي لملف تعريف VPN** للأجهزة المسجلة عبر Microsoft إدارة نقاط النهاية (Intune) بشكل عام. لمزيد من المعلومات، راجع [ملف تعريف VPN للإعداد التلقائي لأجهزة iOS المسجلة](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- إصلاحات الأخطاء.

## <a name="1115140101"></a>1.1.15140101

- **الكشف عن المقاطعة** قيد المعاينة. لمزيد من المعلومات، راجع [إعداد نهج الوصول المشروط استنادا إلى إشارات مخاطر الجهاز](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **الإعداد التلقائي لملف تعريف VPN** قيد المعاينة للأجهزة المسجلة عبر Microsoft إدارة نقاط النهاية (Intune). لمزيد من المعلومات، راجع [ملف تعريف VPN للإعداد التلقائي لأجهزة iOS المسجلة](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- تم الآن تحديث اسم منتج Microsoft Defender ATP إلى Microsoft Defender لنقطة النهاية في متجر التطبيقات.
- تجربة تسجيل الدخول المحسنة.
- إصلاحات الأخطاء.

## <a name="1115010101"></a>1.1.15010101

- مع هذا الإصدار، نعلن عن دعم أجهزة iPadOS/iPad.
- إصلاحات الأخطاء.
