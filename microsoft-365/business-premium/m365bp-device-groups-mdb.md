---
title: العمل مع مجموعات الأجهزة في Microsoft 365 Business Premium
description: التعرف على مجموعات الأجهزة في Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/16/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: ee73b5a83a669653087bf787061e8ad59b23ed18
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095201"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>مجموعات الأجهزة في Microsoft 365 Business Premium

تتضمن Microsoft 365 Business Premium حماية نقطة النهاية من خلال Microsoft Defender for Business. يتم تطبيق نهج حماية الجهاز على الأجهزة من خلال مجموعات معينة تسمى مجموعات الأجهزة. 

**يصف هذا الإرشاد ما يلي**:  

- [ما هي مجموعات الأجهزة](#whats-a-device-group)
- [كيفية إنشاء مجموعة أجهزة جديدة](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>ما هي مجموعة الأجهزة؟

مجموعة الأجهزة هي مجموعة من الأجهزة التي يتم تجميعها معا بسبب معايير معينة، مثل إصدار نظام التشغيل. يتم تضمين الأجهزة التي تفي بالمعايير في مجموعة الأجهزة هذه، إلا إذا قمت باستبعادها. 

مع اشتراكك، لديك مجموعات أجهزة افتراضية يمكنك استخدامها. تتضمن مجموعات الأجهزة الافتراضية جميع الأجهزة التي تم إلحاقها ب Defender for Business. ومع ذلك، يمكنك أيضا إنشاء مجموعات أجهزة جديدة لتعيين نهج حماية الجهاز مع إعدادات معينة لأجهزة معينة. 

يتم تخزين جميع مجموعات الأجهزة، بما في ذلك مجموعات الأجهزة الافتراضية وأي مجموعات أجهزة مخصصة تقوم بتعريفها، في [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="how-do-i-create-a-new-device-group"></a>كيف أعمل إنشاء مجموعة أجهزة جديدة؟

يمكنك إنشاء مجموعة أجهزة جديدة أثناء عملية إنشاء نهج حماية الجهاز أو تحريره. 

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **تكوين الجهاز**. 

3. اتخذ أحد الإجراءات التالية:

    1. حدد نهجا موجودا، ثم اختر **"تحرير**".
    
    2. اختر **+ إضافة** لإنشاء نهج جديد.

    > [!TIP]
    > للحصول على المساعدة في إنشاء نهج أو تحريره، راجع [عرض النهج أو تحريرها في Microsoft Defender for Business](m365bp-view-edit-create-mdb-policies.md).

4. في خطوة **المعلومات العامة** ، راجع المعلومات، وقم بالتحرير إذا لزم الأمر، ثم اختر **"التالي**".

5. اختر **+ إنشاء مجموعة جديدة**. 

6. حدد اسما ووصفا لمجموعة الأجهزة، ثم اختر **"التالي**".

7. حدد الأجهزة المراد تضمينها في المجموعة، ثم اختر **"إنشاء مجموعة**".

8. في خطوة **مجموعات الأجهزة** ، راجع قائمة مجموعات الأجهزة للنهج. إذا لزم الأمر، قم بإزالة مجموعة من القائمة. ثم اختر **"التالي**".

9. في صفحة **إعدادات التكوين** ، راجع الإعدادات وتحريرها حسب الحاجة، ثم اختر **"التالي**". لمزيد من المعلومات حول هذه الإعدادات، راجع [فهم إعدادات تكوين الجيل التالي في Microsoft Defender for Business](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. في خطوة **مراجعة النهج،** راجع جميع الإعدادات، وأجر أي عمليات تحرير مطلوبة، ثم اختر **"إنشاء نهج** " أو **"تحديث النهج**".

الآن بعد أن أكملت بعثاتك الأساسية، قم بإعداد [فرق الاستجابة](m365bp-security-incident-management.md) الخاصة بك [والحفاظ على بيئتك](m365bp-maintain-environment.md).

