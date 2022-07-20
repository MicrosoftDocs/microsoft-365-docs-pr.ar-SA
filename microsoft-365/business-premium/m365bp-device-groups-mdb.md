---
title: العمل مع مجموعات الأجهزة في Microsoft 365 Business Premium
description: تعرف على مجموعات الأجهزة وكيفية تطبيق النهج مع Intune في Microsoft 365 Business Premium، وزيادة الحماية من الهجمات الإلكترونية.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: cde398c0ee13b7c06be3e0158b4f993476348b3d
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893934"
---
# <a name="device-groups-and-categories-in-microsoft-365-business-premium"></a>مجموعات الأجهزة وفئاتها في Microsoft 365 Business Premium

يتضمن Microsoft 365 Business Premium حماية نقطة النهاية من خلال Microsoft Defender for Business Microsoft Intune. يتم تطبيق نهج حماية الجهاز على الأجهزة من خلال مجموعات معينة تسمى مجموعات الأجهزة. في Intune، يتم تجميع الأجهزة في فئات الأجهزة كطريقة مختلفة لتنظيمها. 

تتضمن هذه المقالة الأقسام التالية:  

- [العمل مع مجموعات الأجهزة](#working-with-device-groups)
- [كيفية إنشاء مجموعة أجهزة جديدة](#create-a-device-group-in-the-microsoft-365-defender-portal)
- [كيفية إنشاء فئة جهاز جديدة في Intune](#create-a-device-category-in-intune)

## <a name="working-with-device-groups"></a>العمل مع مجموعات الأجهزة

مجموعة الأجهزة هي مجموعة من الأجهزة التي يتم تجميعها معا بسبب معايير معينة، مثل إصدار نظام التشغيل. يتم تضمين الأجهزة التي تفي بالمعايير في مجموعة الأجهزة هذه، إلا إذا قمت باستبعادها.

باستخدام Microsoft 365 Business Premium، لديك مجموعات أجهزة افتراضية يمكنك استخدامها. تتضمن مجموعات الأجهزة الافتراضية جميع الأجهزة التي تم إلحاقها ب Defender for Business. ومع ذلك، يمكنك أيضا إنشاء مجموعات أجهزة جديدة لتعيين نهج حماية الجهاز مع إعدادات معينة لأجهزة معينة.

يتم تخزين جميع مجموعات الأجهزة، بما في ذلك مجموعات الأجهزة الافتراضية وأي مجموعات أجهزة مخصصة تقوم بتعريفها، في [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-device-group-in-the-microsoft-365-defender-portal"></a>إنشاء مجموعة أجهزة في مدخل Microsoft 365 Defender

يمكنك إنشاء مجموعة أجهزة جديدة أثناء عملية إنشاء نهج حماية الجهاز أو تحريره.

1. انتقل إلى [مدخل Microsoft 365 Defender](https://security.microsoft.com) وسجل الدخول.

2. في جزء التنقل، اختر **تكوين الجهاز**.

3. اتخذ أحد الإجراءات التالية:

    1. حدد نهجا موجودا، ثم اختر **"تحرير**".

    2. اختر **+ إضافة** لإنشاء نهج جديد.

    > [!TIP]
    > للحصول على المساعدة في إنشاء نهج أو تحريره، راجع [عرض النهج أو تحريرها في Microsoft Defender for Business](m365bp-view-edit-create-mdb-policies.md).

4. في خطوة **المعلومات العامة** ، راجع المعلومات، وقم بالتحرير إذا لزم الأمر، ثم اختر **"التالي**".

5. اختر **إنشاء مجموعة جديدة**.

6. حدد اسما ووصفا لمجموعة الأجهزة، ثم اختر **"التالي**".

7. حدد الأجهزة المراد تضمينها في المجموعة، ثم اختر **"إنشاء مجموعة**".

8. في خطوة **مجموعات الأجهزة** ، راجع قائمة مجموعات الأجهزة للنهج. إذا لزم الأمر، قم بإزالة مجموعة من القائمة. ثم اختر **"التالي**".

9. في صفحة **إعدادات التكوين** ، راجع الإعدادات وتحريرها حسب الحاجة، ثم اختر **"التالي**". لمزيد من المعلومات حول هذه الإعدادات، راجع [فهم إعدادات تكوين الجيل التالي في Microsoft Defender for Business](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. في خطوة **مراجعة النهج،** راجع جميع الإعدادات، وأجر أي عمليات تحرير مطلوبة، ثم اختر **"إنشاء نهج** " أو **"تحديث النهج**".

## <a name="create-a-device-category-in-intune"></a>إنشاء فئة جهاز في Intune

إنشاء فئات الأجهزة في Intune التي يجب على المستخدمين الاختيار منها عند تسجيلهم لجهاز.

1. سجل الدخول إلى [مركز إدارة Microsoft إدارة نقاط النهاية](https://endpoint.microsoft.com).

2. اختر **فئات** >  أجهزة **الأجهزة** > **إنشاء فئة جهاز** لإضافة فئة جديدة.

3. في جزء **"Create device category** "، أدخل اسما للفئة الجديدة ووصفا اختياريا.

4. عند الانتهاء، حدد **"إنشاء**". يمكنك رؤية الفئة الجديدة في القائمة.

استخدم اسم فئة الجهاز عند إنشاء مجموعات أمان Azure Active Directory (Azure AD). عند تسجيل المستخدمين أجهزتهم، يتم تقديم قائمة بالفئات التي قمت بتكوينها في Intune. بعد اختيار فئة وإنهاء التسجيل، تتم إضافة جهازه إلى مجموعة أمان Active Directory المقترنة به.

## <a name="create-dynamic-device-groups-in-azure-active-directory"></a>إنشاء مجموعات أجهزة ديناميكية في Azure Active Directory

يمكنك أيضا إدخال مدخل Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) من مركز مسؤولي Microsoft 365. في مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com/))، اختر **جميع مراكز الإدارة**، ثم اختر **Azure Active Directory**.

في مدخل Azure AD، يمكنك إنشاء مجموعات ديناميكية استنادا إلى فئة الجهاز واسم فئة الجهاز. استخدم قواعد المجموعة الديناميكية لإضافة الأجهزة وإزالتها تلقائيا. إذا تغيرت سمات الجهاز، يبحث النظام في قواعد المجموعة الديناميكية للدليل لمعرفة ما إذا كان الجهاز يفي بمتطلبات القاعدة (تتم إضافته) أو لم يعد يفي بمتطلبات القواعد (تتم إزالته).

يمكنك إنشاء مجموعة ديناميكية لأي من الأجهزة أو المستخدمين، ولكن ليس لكليهما. لا يمكنك أيضا إنشاء مجموعة أجهزة استنادا إلى سمات مالكي الأجهزة. يمكن أن تشير قواعد عضوية الجهاز إلى إسنادات الجهاز فقط. 

## <a name="after-device-groups-are-created"></a>بعد إنشاء مجموعات الأجهزة

الآن بعد إنشاء الفئات ومجموعات الأجهزة، يقوم مستخدمو أجهزة iOS وAndroid بتسجيل أجهزتهم، وكما يفعلون ذلك، يجب عليهم اختيار فئة من قائمة الفئات التي تم تكوينها. يمكن لمستخدمي Windows استخدام موقع ويب Company Portal أو تطبيق Company Portal لتحديد فئة.

1. بعد تسجيل الجهاز، انتقل إلى [مدخل الشركة](https://portal.microsoft.com) واختر **"أجهزتي**".

2. حدد الجهاز المسجل من القائمة، ثم حدد فئة.

بعد اختيار فئة، تتم إضافة الجهاز تلقائيا إلى المجموعة المقابلة. إذا كان الجهاز مسجلا بالفعل قبل تكوين الفئات، يرى المستخدم إعلاما حول الجهاز على موقع ويب Company Portal. يتيح هذا للمستخدم معرفة تحديد فئة في المرة التالية التي يصل فيها إلى تطبيق Company Portal على iOS/iPadOS أو Android.

> [!NOTE]
> - يمكنك تحرير فئة جهاز في مدخل Microsoft Azure، ولكن يجب عليك تحديث أي مجموعات أمان Azure AD تشير إلى هذه الفئة يدويا.
> - إذا قمت بحذف فئة، فإن الأجهزة المعينة إليها تعرض اسم الفئة **غير معين**.

## <a name="view-the-categories-of-devices-that-you-manage"></a>عرض فئات الأجهزة التي تديرها

1. سجل الدخول إلى [مركز إدارة Microsoft إدارة نقاط النهاية](https://endpoint.microsoft.com)، واختر **الأجهزة** > **كافة الأجهزة**.

2. في قائمة الأجهزة، افحص عمود **فئة الجهاز** .

3. إذا لم يظهر عمود فئة الجهاز، فحدد "**تطبيق** **فئة** >  **الأعمدة** > ".

## <a name="change-the-category-of-a-device"></a>تغيير فئة الجهاز

1. سجل الدخول إلى [مركز إدارة Microsoft إدارة نقاط النهاية](https://endpoint.microsoft.com)، واختر **الأجهزة** > **كافة الأجهزة**. 

2. حدد الفئة التي تريدها من القائمة، لرؤية خصائصها.

## <a name="next-steps"></a>الخطوات التالية

الآن بعد أن أكملت بعثاتك الأساسية، خذ بعض الوقت لإعداد [فرق الاستجابة](m365bp-security-incident-management.md) [والحفاظ على بيئتك](m365bp-maintain-environment.md).
