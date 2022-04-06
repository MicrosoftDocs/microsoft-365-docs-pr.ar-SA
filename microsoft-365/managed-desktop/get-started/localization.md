---
title: تعريف تجربة المستخدم
description: كيفية تهويد الأجهزة للمستخدمين
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: c429a072d6ceb2d5d1472533649e30d1fc1a0078
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63583216"
---
# <a name="localize-the-user-experience"></a>تعريف تجربة المستخدم

يمكن لمستخدمي أجهزة سطح المكتب المدارة من Microsoft تحديد اللغة التي يختارونها إما أثناء عملية الإعداد ("تجربة خارج الصندوق") أو بعد ذلك.

## <a name="during-setup-the-out-of-box-experience"></a>أثناء الإعداد (تجربة "خارج المربع")

أثناء الإعداد، يمكن للمستخدمين تحديد اللغة التي يختارها المستخدمون. يؤثر هذا التحديد على السمات:

| السمة | الوصف |
| ------ | ------ |
| Windows 10 اللغات | <ul><li>لغة العرض</li><li>لغة لوحة المفاتيح</li><li>الميزات ذات الصلة باللغة عند الطلب</li><ul> |
| Microsoft 365 Apps لميزات لغة المؤسسة | <ul><li>لغة العرض</li><li>أدوات التدقيق والتأليف</li></ul> |

> [!NOTE]
> يمكن للمستخدمين الحصول على الميزات ذات الصلة باللغة عند الطلب فقط عن طريق تحديد اللغة أثناء عملية الإعداد.

## <a name="after-completing-setup"></a>بعد إكمال الإعداد

يمكن للمستخدمين تحديد اللغة التي يختارها Windows 10، Microsoft 365 Apps للمؤسسة في أي وقت بعد اكتمال عملية الإعداد. بشكل خاص:

| الميزة | الوصف |
| ------ | ------ |
| Windows 10 اللغات | <ul><li>لغة العرض</li><li>لغة لوحة المفاتيح</li><ul> |
| Microsoft 365 Apps لميزات لغة المؤسسة | <ul><li>لغة العرض</li><li>أدوات التدقيق والتأليف</li></ul> |

## <a name="install-more-languages"></a>تثبيت المزيد من اللغات

> [!NOTE]
> في 16 مارس 2022، سنلغى مجموعة Modern Workplace-Office-Language_Packs التي تسمح لك بإضافة لغات إلى Microsoft Office. سيتم إكمال الانتقال إلى الأسلوب الجديد (انظر أدناه) في أبريل 2022. إذا كانت لديك أي مشاكل أثناء فترة الانتقال هذه، فالرجاء [التواصل مع الدعم](../working-with-managed-desktop/admin-support.md).

بشكل افتراضي، Microsoft Office المستخدمين بأن يكونوا المسؤولين. يقوم Microsoft Managed Desktop بنشر نهج Office لتمكين المستخدمين القياسيين من تثبيت حزم ملحقات اللغة مباشرة من تطبيقات Office الخاصة بهم. لمزيد من المعلومات، راجع [السماح للمستخدمين غير المسؤولين بتثبيت لغات إضافية](/deployoffice/overview-deploying-languages-microsoft-365-apps#allow-users-who-arent-admins-to-install-additional-languages).

## <a name="supported-languages"></a>اللغات المعتمدة

بالنسبة للأجهزة الجديدة، يجب على الشركة المصنعة توفير صور الأجهزة التي تتضمن اللغات التي تحتاج إليها. إذا تضمنت صورة الشركة المصنعة لغات غير مضمنة في قائمة اللغات المعتمدة، فإن الخدمة لا تزال تدعم الجهاز.

إذا كنت تقوم ب إعادة استخدام الأجهزة الموجودة، فقد تحتاج إلى العمل مع ممثل حساب Microsoft للحصول على الصور المناسبة. لمزيد من المعلومات، راجع [صور الجهاز](../service-description/device-images.md).

تتضمن [الصورة العامة التي](../service-description/device-images.md#universal-image) يوفرها Microsoft Managed Desktop هذه اللغات Windows 10:

- العربية
- البلغارية
- الصينية المبسطة
- الصينية التقليدية
- الكرواتية
- التشيكية
- الدانماركية  
- الهولندية  
- الإنجليزية (الولايات المتحدة، GB، AU، CA، IN)
- الإستونية
- الفنلندية
- الفرنسية (فرنسا، كندا)
- الألمانية
- اليونانية
- العبرية
- المجرية
- الإندونيسية
- الإيطالية
- اليابانية
- الكورية
- اللاتفية
- الليتوانية
- النرويجية (بوكمل)
- البولندية
- البرتغالية (البرازيل)
- البرتغالية (البرتغال)
- الرومانية
- الروسية
- الصربية (الأبجدية اللاتينية)
- السلوفاكية
- السلوفينية
- الإسبانية (إسبانيا، المكسيك)
- السويدية
- التايلندية
- التركية
- الأوكرانية
- الفيتنامية

> [!NOTE]
> Microsoft 365 Apps ل Enterprise قائمة مختلفة بعض الوقت.

إذا كان المستخدمون بحاجة إلى لغة أخرى غير تلك المذكورة هنا، فلف طلب [دعم](../working-with-managed-desktop/admin-support.md) باستخدام [مدخل المسؤول](access-admin-portal.md).

## <a name="languages-for-support-and-operations"></a>لغات الدعم والعمليات

### <a name="admin-support-and-operations"></a>دعم المسؤول وعملياته

يوفر Microsoft Managed Desktop دعم المسؤول باللغة الإنجليزية فقط. يتضمن هذا الدعم مدخل المسؤول وجميع الاتصالات مع عمليات سطح المكتب المدارة من Microsoft. يجب أن تفترض أن كل التفاعلات والواجهات ذات الصلة بالمسؤول ستكون باللغة الإنجليزية، ما لم يتم تحديد خلاف ذلك.
