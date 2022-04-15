---
title: مجموعات الأجهزة في Microsoft Defender for Business
description: التعرف على مجموعات الأجهزة في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 6c02a92132f7f5249f2ba67ca2841902b889d52b
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861719"
---
# <a name="device-groups-in-microsoft-defender-for-business"></a>مجموعات الأجهزة في Microsoft Defender for Business

> [!NOTE]
> تم تضمين Microsoft Defender for Business الآن في [Microsoft 365 Business Premium](../../business-premium/index.md). 

في Microsoft Defender for Business، يتم تطبيق النهج على الأجهزة من خلال مجموعات معينة تسمى مجموعات الأجهزة. 

**تصف هذه المقالة**:  

- [ما هي مجموعات الأجهزة](#what-is-a-device-group)   
- [كيفية إنشاء مجموعات الأجهزة في Defender for Business](#create-a-new-device-group)
- [كيفية عرض مجموعة أجهزة موجودة](#view-an-existing-device-group)
- [وظيفة الخيار "إضافة كافة الأجهزة"](#what-does-the-add-all-devices-option-do)

>
> **هل لديك دقيقة؟**
> يرجى أخذ <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاعنا القصير حول الأمان</a>. يسعدنا أن نستمع إليك!
>

## <a name="what-is-a-device-group"></a>ما هي مجموعة الأجهزة؟

مجموعة الأجهزة هي مجموعة من الأجهزة التي يتم تجميعها معا بسبب معايير معينة، مثل إصدار نظام التشغيل. يتم تضمين الأجهزة التي تفي بالمعايير في مجموعة الأجهزة هذه، إلا إذا قمت باستبعادها. في Microsoft Defender for Business، يتم تطبيق النهج على الأجهزة باستخدام مجموعات الأجهزة.

يتضمن Defender for Business مجموعات الأجهزة الافتراضية التي يمكنك استخدامها. تتضمن مجموعات الأجهزة الافتراضية جميع الأجهزة التي تم إلحاقها ب Defender for Business. على سبيل المثال، هناك مجموعة أجهزة افتراضية للأجهزة Windows. كلما قمت بإلحاق أجهزة Windows، تتم إضافتها إلى مجموعة الأجهزة الافتراضية تلقائيا.

يمكنك أيضا إنشاء مجموعات أجهزة جديدة لتعيين نهج ذات إعدادات معينة إلى أجهزة معينة. على سبيل المثال، قد يكون لديك نهج جدار حماية معين لمجموعة واحدة من أجهزة Windows، ونهج جدار حماية مختلف معين لمجموعة أخرى من أجهزة Windows. يمكنك تعريف مجموعات أجهزة معينة لاستخدامها مع النهج الخاصة بك.

> [!NOTE]
> أثناء إنشاء نهج في Defender for Business، يتم تعيين ترتيب الأولوية. إذا قمت بتطبيق نهج متعددة على مجموعة معينة من الأجهزة، فستتلقى هذه الأجهزة النهج المطبق الأول فقط. لمزيد من المعلومات، راجع [فهم ترتيب النهج في Microsoft Defender for Business](mdb-policy-order.md).

يتم تخزين جميع مجموعات الأجهزة، بما في ذلك مجموعات الأجهزة الافتراضية وأي مجموعات أجهزة مخصصة تقوم بتعريفها، في [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-new-device-group"></a>إنشاء مجموعة أجهزة جديدة

حاليا، في Defender for Business، يمكنك إنشاء مجموعة أجهزة جديدة أثناء عملية إنشاء نهج أو تحريره، كما هو موضح في الإجراء التالي: 

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **تكوين الجهاز**. 

3. اتخذ أحد الإجراءات التالية:

    1. حدد نهجا موجودا، ثم اختر **"تحرير**".
    2. اختر **+ إضافة** لإنشاء نهج جديد.

    > [!TIP]
    > للحصول على المساعدة في إنشاء نهج أو تحريره، راجع [عرض النهج أو تحريرها في Microsoft Defender for Business](mdb-view-edit-policies.md).

4. في خطوة **المعلومات العامة** ، راجع المعلومات، وقم بالتحرير إذا لزم الأمر، ثم اختر **"التالي**".

5. اختر **+ إنشاء مجموعة جديدة**. 

6. حدد اسما ووصفا لمجموعة الأجهزة، ثم اختر **"التالي**".

7. حدد الأجهزة المراد تضمينها في المجموعة، ثم اختر **"إنشاء مجموعة**".

8. في خطوة **مجموعات الأجهزة** ، راجع قائمة مجموعات الأجهزة للنهج. إذا لزم الأمر، قم بإزالة مجموعة من القائمة. ثم اختر **"التالي**".

9. في صفحة **إعدادات التكوين** ، راجع الإعدادات وتحريرها حسب الحاجة، ثم اختر **"التالي**". لمزيد من المعلومات حول هذه الإعدادات، راجع [إعدادات التكوين](mdb-next-gen-configuration-settings.md).

10. في خطوة **مراجعة النهج،** راجع جميع الإعدادات، وأجر أي عمليات تحرير مطلوبة، ثم اختر **"إنشاء نهج** " أو **"تحديث النهج**".

## <a name="view-an-existing-device-group"></a>عرض مجموعة أجهزة موجودة

حاليا، في Defender for Business، يمكنك عرض مجموعات الأجهزة الموجودة أثناء عملية إنشاء نهج أو تحريره، كما هو موضح في الإجراء التالي: 

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **تكوين الجهاز**. 

3. اتخذ أحد الإجراءات التالية:

    1. حدد نهجا موجودا، ثم اختر **"تحرير**".
    2. اختر **+ إضافة** لإنشاء نهج جديد.

    > [!TIP]
    > للحصول على المساعدة في إنشاء نهج أو تحريره، راجع [عرض النهج أو تحريرها في Microsoft Defender for Business](mdb-view-edit-policies.md).

4. في خطوة **المعلومات العامة** ، راجع المعلومات، وقم بالتحرير إذا لزم الأمر، ثم اختر **"التالي**".

5. اختر **"استخدام مجموعة موجودة**". يتم فتح قائمة منبثقة وعرض مجموعات الأجهزة. إذا لم يكن لديك أي مجموعات أجهزة بعد، فستتم مطالبتك بإنشاء مجموعة أجهزة جديدة.

## <a name="what-does-the-add-all-devices-option-do"></a>ماذا يفعل الخيار "إضافة كافة الأجهزة"؟

عند إنشاء نهج أو تحريره، قد يظهر الخيار **"إضافة كافة الأجهزة** ".

:::image type="content" source="media/add-all-devices-option.png" alt-text="Screenshot of the Add All Devices option.":::

إذا حددت هذا الخيار، فستتلقى جميع الأجهزة المسجلة في إدارة نقاط النهاية من Microsoft (والتي تتضمن Microsoft Intune) النهج الذي تقوم بإنشائه أو تحريره بشكل افتراضي. 

## <a name="next-steps"></a>الخطوات التالية

اختر مهمة واحدة أو أكثر من المهام التالية:

- [عرض النهج أو تحريرها](mdb-view-edit-policies.md)
- [إنشاء نهج جديد](mdb-create-new-policy.md)
- [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)
- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)
- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)