---
title: البرامج التعليمية والمحاكاة في Microsoft Defender for Business
description: تعرف على العديد من البرامج التعليمية لمساعدتك على بدء استخدام Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: e491e6d093396e54983e96eb1ca96c5e713565ba
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089165"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>البرامج التعليمية والمحاكاة في Microsoft Defender for Business

إذا انتهيت للتو من إعداد Microsoft Defender for Business، فقد تتساءل من أين تبدأ في التعرف على كيفية عمل Defender for Business. تصف هذه المقالة بعض السيناريوهات التي يجب تجربتها، والعديد من البرامج التعليمية والمحاكاة المتوفرة ل Defender for Business. تم تصميم هذه الموارد لمساعدتك على معرفة كيف يمكن أن يعمل Defender for Business لشركتك.


## <a name="try-these-scenarios"></a>جرب هذه السيناريوهات

يلخص الجدول التالي العديد من السيناريوهات التي يجب تجربتها باستخدام Defender for Business:

| السيناريو  | الوصف  |
|---------|---------|
| إلحاق الأجهزة باستخدام برنامج نصي محلي     | في Defender for Business، يمكنك إلحاق الأجهزة Windows macOS باستخدام برنامج نصي تقوم بتنزيله وتشغيله على كل جهاز. ينشئ البرنامج النصي ثقة مع Azure Active Directory (Azure AD) (إذا لم تكن هذه الثقة موجودة بالفعل)، ويسجل الجهاز مع Microsoft Intune (إذا كان لديك Intune)، ويلحق الجهاز ب Defender for Business. لمعرفة المزيد، راجع [إلحاق الأجهزة Microsoft Defender for Business](mdb-onboard-devices.md).         |
| إلحاق الأجهزة باستخدام مركز إدارة إدارة نقاط النهاية من Microsoft     | إذا كنت تستخدم Intune بالفعل قبل الحصول على Defender for Business، يمكنك الاستمرار في استخدام مركز إدارة إدارة نقاط النهاية لإلحاق الأجهزة. حاول إلحاق أجهزة Windows macOS وiOS وAndroid باستخدام Microsoft Intune. لمعرفة المزيد، راجع [تسجيل الجهاز في Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| تحرير نهج الأمان     | إذا كنت تدير نهج الأمان في Defender for Business، فاستخدم صفحة **تكوين الجهاز** لعرض النهج وتحريرها، إذا لزم الأمر. يأتي Defender for Business مزودا بنهج افتراضية تستخدم الإعدادات الموصى بها لتأمين أجهزة شركتك بمجرد إلحاقها. يمكنك الاحتفاظ بنهجك الافتراضية وتحريرها وتحديد نهجك الخاص ليناسب احتياجات عملك. لمعرفة المزيد، راجع [عرض النهج أو تحريرها في Microsoft Defender for Business](mdb-view-edit-policies.md).        |
| تشغيل هجوم محاكاة   | تتوفر العديد من البرامج التعليمية والمحاكاة في Defender for Business. تم تصميم هذه البرامج التعليمية والمحاكاة لتوضح لك مباشرة كيف يمكن أن تعمل ميزات الحماية من التهديدات في Defender for Business لشركتك. يمكنك أيضا استخدام هجوم محاكاة كتمرين تدريبي لفريقك. لتجربة برنامج تعليمي واحد أو أكثر، راجع [البرامج التعليمية الموصى بها Microsoft Defender for Business](#recommended-tutorials-for-defender-for-business).         |
| عرض الحوادث في Microsoft 365 Lighthouse     | إذا كنت [موفر حلول الحوسبة السحابية من Microsoft](/partner-center/enrolling-in-the-csp-program) باستخدام Microsoft 365 Lighthouse، فستتمكن من عرض الحوادث عبر مستأجري عملائك في مدخل Microsoft 365 Lighthouse. لمعرفة المزيد، راجع [Microsoft 365 Lighthouse و Microsoft Defender for Business](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>البرامج التعليمية الموصى بها ل Defender for Business

يصف الجدول التالي البرامج التعليمية الموصى بها لعملاء Defender for Business:

| تعليمي  | الوصف  |
|---------|---------|
| **القائمة الخلفية لإفلات المستند**     | محاكاة هجوم يقدم برامج ضارة مستندة إلى الملفات على جهاز اختبار. يصف البرنامج التعليمي كيفية الحصول على ملف المحاكاة واستخدامه، وما يجب مراقبته في مدخل Microsoft 365 Defender. <br/><br/>يتطلب هذا البرنامج التعليمي تثبيت Microsoft Word على جهاز الاختبار الخاص بك.   |
| **البرنامج التعليمي للاستجابة المباشرة**     | تعرف على كيفية استخدام الأوامر الأساسية والمتقدمة مع Live Response. تعرف على كيفية تحديد موقع ملف مريب، ومعالجة الملف، وجمع المعلومات على جهاز.   |
| **إدارة الثغرات الأمنية & المخاطر (السيناريوهات الأساسية)**     | تعرف على إدارة المخاطر والثغرات الأمنية من خلال ثلاثة سيناريوهات: <br/><br/>1. تقليل تعرض شركتك للمخاطر والثغرات الأمنية. <br/>2. طلب معالجة. <br/>3. إنشاء استثناء لتوصيات الأمان. <br/><br/> يستخدم التهديد إدارة الثغرات الأمنية نهجا يستند إلى المخاطر لاكتشاف نقاط الضعف والتكوينات الخاطئة وتحديد أولوياتها ومعالجتها.      |

يتضمن كل برنامج تعليمي مستندا إرشاديا يشرح السيناريو وكيفية عمله وما يجب فعله.

> [!TIP]
> سترى مراجع Microsoft Defender لنقطة النهاية في مستندات المعاينة. يمكن استخدام البرامج التعليمية المذكورة في هذه المقالة إما مع Defender لنقطة النهاية أو Defender for Business.

## <a name="how-to-access-the-tutorials"></a>كيفية الوصول إلى البرامج التعليمية

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، ضمن **نقاط النهاية**، اختر **البرامج التعليمية**.

3. اختر أحد البرامج التعليمية التالية:

   - **القائمة الخلفية لإفلات المستند**
   - **البرنامج التعليمي للاستجابة المباشرة**
   - **إدارة الثغرات الأمنية & المخاطر (السيناريوهات الأساسية)**

## <a name="next-steps"></a>الخطوات التالية

- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)
- [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)
- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)
- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)