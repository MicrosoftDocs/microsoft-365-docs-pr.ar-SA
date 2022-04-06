---
title: تكوين حساب خدمات الدليل في Microsoft Defender for Identity
description: تعرف على كيفية تكوين حساب Microsoft Defender for Identity Directory Services في Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e31c226037d5d9e945350ba73e1df9abc79571e9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469988"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Microsoft Defender for Identity خدمات الدليل في Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة كيفية تكوين [حساب Microsoft Defender for Identity](/defender-for-identity) Directory Services في [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

## <a name="configure-directory-services-account"></a>تكوين حساب خدمات الدليل

لتوصيل [المستشعر](sensor-health.md#add-a-sensor) بمجالات Active Directory، ستحتاج إلى تكوين حسابات خدمات الدليل.

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="الخيار &quot;الهويات&quot; في الإعدادات الصفحة" lightbox="../../media/defender-identity/settings-identities.png":::


1. حدد **حسابات خدمة الدليل**. سترى الحسابات المقترنة بالمجالات.

   :::image type="content" source="../../media/defender-identity/directory-service-accounts.png" alt-text="عنصر القائمة حسابات خدمة الدليل" lightbox="../../media/defender-identity/directory-service-accounts.png":::

1. إذا قمت بتحديد حساب، سيتم فتح جزء مع إعدادات هذا الحساب.

   :::image type="content" source="../../media/defender-identity/account-settings.png" alt-text="صفحة إعدادات الحساب" lightbox="../../media/defender-identity/account-settings.png":::

1. لإضافة حساب جديد لخدمات الدليل، حدد **إنشاء حساب جديد** وملء اسم الحساب **والمجال وكلمة** **المرور**. يمكنك أيضا اختيار ما إذا كان حساب خدمة مدارة من قبل **المجموعة (** gMSA)، وإذا كان ينتمي إلى **مجال تسمية مفردة**.

   :::image type="content" source="../../media/defender-identity/new-directory-service-account.png" alt-text="الخيار &quot;إنشاء حساب جديد&quot;" lightbox="../../media/defender-identity/new-directory-service-account.png":::

1. حدد **حفظ**.

## <a name="see-also"></a>راجع أيضًا

- [Microsoft Defender for Identity أدوات الاستشعار وإعداداتها](sensor-health.md)
