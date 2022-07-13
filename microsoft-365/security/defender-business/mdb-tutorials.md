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
ms.openlocfilehash: 029be738b8c916ec4eb16970ae2d2ff3c460f639
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66771963"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>البرامج التعليمية والمحاكاة في Microsoft Defender for Business

تصف هذه المقالة بعض السيناريوهات التي يجب تجربتها والعديد من البرامج التعليمية والمحاكاة المتوفرة ل Defender for Business. توضح هذه الموارد كيف يمكن أن يعمل Defender for Business لشركتك.


## <a name="try-these-scenarios"></a>جرب هذه السيناريوهات

يلخص الجدول التالي العديد من السيناريوهات التي يجب تجربتها باستخدام Defender for Business.

| السيناريو  | الوصف  |
|---------|---------|
| إلحاق الأجهزة باستخدام برنامج نصي محلي     | في Defender for Business، يمكنك إلحاق أجهزة Windows وMac باستخدام برنامج نصي تقوم بتنزيله وتشغيله على كل جهاز. ينشئ البرنامج النصي ثقة مع Azure Active Directory (Azure AD)، إذا لم تكن هذه الثقة موجودة بالفعل؛ يسجل الجهاز مع Microsoft Intune، إذا كان لديك Intune؛ ويلحق الجهاز ب Defender for Business. لمعرفة المزيد، راجع [إلحاق الأجهزة ب Defender for Business](mdb-onboard-devices.md).         |
| إلحاق الأجهزة باستخدام مركز إدارة Microsoft إدارة نقاط النهاية     | إذا كنت تستخدم Intune بالفعل قبل الحصول على Defender for Business، يمكنك الاستمرار في استخدام مركز إدارة إدارة نقاط النهاية لإلحاق الأجهزة. حاول إلحاق أجهزة Windows وMac وiOS وAndroid باستخدام Microsoft Intune. لمعرفة المزيد، راجع [تسجيل الجهاز في Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| تحرير نهج الأمان     | إذا كنت تدير نهج الأمان في Defender for Business، فاستخدم صفحة **تكوين الجهاز** لعرض النهج وتحريرها. يأتي Defender for Business مزودا بنهج افتراضية تستخدم الإعدادات الموصى بها لتأمين أجهزة شركتك بمجرد إلحاقها. يمكنك الاحتفاظ بالنهج الافتراضية وتحريرها وتحديد النهج الخاصة بك لتناسب احتياجات عملك. لمعرفة المزيد، راجع [عرض النهج أو تحريرها في Defender for Business](mdb-view-edit-policies.md).        |
| تشغيل هجوم محاكاة   | تتوفر العديد من البرامج التعليمية والمحاكاة في Defender for Business. توضح هذه البرامج التعليمية والمحاكاة كيفية عمل ميزات الحماية من التهديدات في Defender for Business لشركتك. يمكنك أيضا استخدام هجوم محاكاة كتمرين تدريبي لفريقك. لتجربة البرامج التعليمية، راجع [البرامج التعليمية الموصى بها ل Defender for Business](#recommended-tutorials-for-defender-for-business).         |
| عرض الحوادث في Microsoft 365 Lighthouse     | إذا كنت [موفر حلول سحابة Microsoft](/partner-center/enrolling-in-the-csp-program) باستخدام Microsoft 365 Lighthouse، يمكنك عرض الحوادث عبر مستأجري عملائك في مدخل Microsoft 365 Lighthouse. لمعرفة المزيد، راجع [Microsoft 365 Lighthouse و Defender for Business](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>البرامج التعليمية الموصى بها ل Defender for Business

يصف الجدول التالي البرامج التعليمية الموصى بها لعملاء Defender for Business.

| تعليمي  | الوصف  |
|---------|---------|
| **المستند المنسدلة الخلفية**     | محاكاة هجوم يقدم برامج ضارة مستندة إلى الملفات على جهاز اختبار. يصف البرنامج التعليمي كيفية استخدام ملف المحاكاة وما يجب مراقبته في مدخل Microsoft 365 Defender. <p>يتطلب هذا البرنامج التعليمي تثبيت Microsoft Word على جهاز الاختبار.   |
| **الاستجابة المباشرة**     | تعرف على كيفية استخدام الأوامر الأساسية والمتقدمة مع Live Response. تعرف على كيفية تحديد موقع ملف مريب، ومعالجة الملف، وجمع المعلومات على جهاز.   |
| **إدارة الثغرات الأمنية & المخاطر (السيناريوهات الأساسية)**     | تعرف على إدارة المخاطر والثغرات الأمنية من خلال ثلاثة سيناريوهات:<ol><li>تقليل تعرض شركتك للمخاطر والثغرات الأمنية.</li><li>طلب معالجة.</li><li>إنشاء استثناء لتوصيات الأمان.</li></ol> <p> تستخدم إدارة الثغرات الأمنية & المخاطر نهجا يستند إلى المخاطر لاكتشاف الثغرات الأمنية في نقاط النهاية والتكوينات الخاطئة وتحديد أولوياتها ومعالجتها.      |

يتضمن كل برنامج تعليمي مستندا إرشاديا يشرح السيناريو وكيفية عمله وما يجب فعله.

> [!TIP]
> سترى مراجع Microsoft Defender لنقطة النهاية في مستندات المعاينة. يمكن استخدام البرامج التعليمية المذكورة في هذه المقالة إما مع Defender لنقطة النهاية أو Defender for Business.

## <a name="how-to-access-the-tutorials"></a>كيفية الوصول إلى البرامج التعليمية

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، ضمن **نقاط النهاية**، اختر **البرامج التعليمية**.

3. اختر أحد البرامج التعليمية التالية:

   - **المستند المنسدلة الخلفية**
   - **الاستجابة المباشرة**
   - **إدارة الثغرات الأمنية & المخاطر (السيناريوهات الأساسية)**

## <a name="next-steps"></a>الخطوات التالية

- [إدارة الأجهزة في Defender for Business](mdb-manage-devices.md)
- [عرض الحوادث وإدارتها في Defender for Business](mdb-view-manage-incidents.md)
- [الاستجابة للتهديدات وتخفيفها في Defender for Business](mdb-respond-mitigate-threats.md)
- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)