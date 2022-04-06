---
title: مجموعات الأجهزة في Microsoft Defender for Business
description: التعرف على مجموعات الأجهزة في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 340d696d2fbc6b698821c54962d04502d6781701
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63583768"
---
# <a name="device-groups-in-microsoft-defender-for-business"></a>مجموعات الأجهزة في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

في Microsoft Defender for Business، يتم تطبيق سياسات على الأجهزة من خلال مجموعات معينة تسمى مجموعات الأجهزة. 

**تصف هذه المقالة**:  

- [ما هي مجموعات الأجهزة](#what-is-a-device-group)   
- [كيفية إنشاء مجموعات الأجهزة في Defender for Business](#create-a-new-device-group)

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="what-is-a-device-group"></a>ما هي مجموعة الأجهزة؟

إن مجموعة الأجهزة عبارة عن مجموعة من الأجهزة التي يتم تجميعها معا بسبب معايير محددة معينة، مثل إصدار نظام التشغيل. يتم تضمين الأجهزة التي تفي بالمعايير في مجموعة الأجهزة هذه، إلا إذا قمت باستبعادها. في Microsoft Defender for Business، يتم تطبيق سياسات على الأجهزة باستخدام مجموعات الأجهزة. 

يتضمن Defender for Business مجموعات الأجهزة الافتراضية التي يمكنك استخدامها. تتضمن مجموعات الأجهزة الافتراضية جميع الأجهزة التي تم تشغيلها في Defender for Business. ومع ذلك، يمكنك أيضا إنشاء مجموعات أجهزة جديدة لتعيين سياسات ذات إعدادات معينة إلى أجهزة معينة. 

يتم تخزين كل مجموعات الأجهزة، بما في ذلك مجموعات الأجهزة الافتراضية وأي مجموعات أجهزة مخصصة تحددها، في [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-new-device-group"></a>إنشاء مجموعة أجهزة جديدة

حاليا، في Defender for Business، يمكنك إنشاء مجموعة أجهزة جديدة أثناء عملية إنشاء نهج أو تحريره، كما هو موضح في الإجراء التالي: 

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. في جزء التنقل، اختر **تكوين الجهاز**. 

3. اتخاذ أحد الإجراءات التالية:

    1. حدد نهج موجود، ثم اختر **تحرير**.
    2. اختر **+ إضافة** لإنشاء نهج جديد.

    > [!TIP]
    > للحصول على المساعدة في إنشاء نهج أو تحريره، راجع عرض النهج أو تحريرها [في Microsoft Defender for Business](mdb-view-edit-policies.md).

4. في الخطوة **معلومات عامة** ، راجع المعلومات، ثم قم بالتحرير إذا لزم الأمر، ثم اختر **التالي**.

5. اختر **+ إنشاء مجموعة جديدة**. 

6. حدد اسما ووصفا لمجموعة الأجهزة، ثم اختر **التالي**.

7. حدد الأجهزة التي تريد تضمينها في المجموعة، ثم اختر **إنشاء مجموعة**.

8. على الخطوة **مجموعات الأجهزة** ، راجع قائمة مجموعات الأجهزة للحصول على النهج. إذا لزم الأمر، قم بإزالة مجموعة من القائمة. ثم اختر **التالي**.

9. في صفحة **إعدادات التكوين** ، راجع الإعدادات وتحريرها حسب الحاجة، ثم اختر **التالي**. لمزيد من المعلومات حول هذه الإعدادات، راجع [إعدادات التكوين](mdb-next-gen-configuration-settings.md).

10. في الخطوة **مراجعة النهج** ، راجع كل الإعدادات، وأنشئ أي عمليات تحرير مطلوبة، ثم اختر **إنشاء نهج** أو **نهج تحديث**.

## <a name="next-steps"></a>الخطوات التالية

اختر واحدة أو أكثر من المهام التالية:

- [عرض أو تحرير السياسات](mdb-view-edit-policies.md)

- [إنشاء نهج جديد](mdb-create-new-policy.md)

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md)