---
title: استخدام مجموعات الأجهزة في Microsoft 365 Business Premium
description: تعرف على مجموعات الأجهزة في Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 2cc874580dad24e1b3d5349d6075956a9e518704
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634636"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>مجموعات الأجهزة في Microsoft 365 Business Premium

Microsoft 365 Business Premium حماية نقطة النهاية من خلال Microsoft Defender for Business. يتم تطبيق سياسات حماية الجهاز على الأجهزة من خلال مجموعات معينة تسمى مجموعات الأجهزة. 

**تصف هذه المقالة**:  

- [ما هي مجموعات الأجهزة](#whats-a-device-group)
- [كيفية إنشاء مجموعة أجهزة جديدة](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>ما هي مجموعة الأجهزة؟

إن مجموعة الأجهزة عبارة عن مجموعة من الأجهزة التي يتم تجميعها معا بسبب معايير محددة معينة، مثل إصدار نظام التشغيل. يتم تضمين الأجهزة التي تفي بالمعايير في مجموعة الأجهزة هذه، إلا إذا قمت باستبعادها. 

باستخدام اشتراكك، لديك مجموعات أجهزة افتراضية يمكنك استخدامها. تتضمن مجموعات الأجهزة الافتراضية جميع الأجهزة التي تم تشغيلها في Defender for Business. ومع ذلك، يمكنك أيضا إنشاء مجموعات أجهزة جديدة لتعيين سياسات حماية الجهاز بإعدادات معينة إلى أجهزة معينة. 

يتم تخزين كل مجموعات الأجهزة، بما في ذلك مجموعات الأجهزة الافتراضية وأي مجموعات أجهزة مخصصة تحددها، في [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="how-do-i-create-a-new-device-group"></a>كيف أعمل إنشاء مجموعة أجهزة جديدة؟

يمكنك إنشاء مجموعة أجهزة جديدة أثناء عملية إنشاء نهج حماية الجهاز أو تحريره. 

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. في جزء التنقل، اختر **تكوين الجهاز**. 

3. اتخاذ أحد الإجراءات التالية:

    1. حدد نهج موجود، ثم اختر **تحرير**.
    
    2. اختر **+ إضافة** لإنشاء نهج جديد.

    > [!TIP]
    > للحصول على المساعدة في إنشاء نهج أو تحريره، راجع [عرض النهج أو تحريرها في Microsoft Defender for Business](m365bp-view-edit-create-mdb-policies.md).

4. في الخطوة **معلومات عامة** ، راجع المعلومات، ثم قم بالتحرير إذا لزم الأمر، ثم اختر **التالي**.

5. اختر **+ إنشاء مجموعة جديدة**. 

6. حدد اسما ووصفا لمجموعة الأجهزة، ثم اختر **التالي**.

7. حدد الأجهزة التي تريد تضمينها في المجموعة، ثم اختر **إنشاء مجموعة**.

8. على الخطوة **مجموعات الأجهزة** ، راجع قائمة مجموعات الأجهزة للحصول على النهج. إذا لزم الأمر، قم بإزالة مجموعة من القائمة. ثم اختر **التالي**.

9. في صفحة **إعدادات التكوين** ، راجع الإعدادات وتحريرها حسب الحاجة، ثم اختر **التالي**. لمزيد من المعلومات حول هذه الإعدادات، راجع [فهم](../security/defender-business/mdb-next-gen-configuration-settings.md) إعدادات تكوين الجيل التالي في Microsoft Defender for Business.

10. في الخطوة **مراجعة النهج** ، راجع كل الإعدادات، وأنشئ أي عمليات تحرير مطلوبة، ثم اختر **إنشاء نهج** أو **نهج تحديث**.


