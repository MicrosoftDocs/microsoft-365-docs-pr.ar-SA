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
ms.openlocfilehash: 0b7e9045ecc479c2da382979211caaa46e8a01d1
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683286"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>حساب Microsoft Defender for Identity Directory Services في Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة كيفية تكوين حساب [Microsoft Defender for Identity](/defender-for-identity) Directory [Services في Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

## <a name="configure-directory-services-account"></a>تكوين حساب خدمات الدليل

لتوصيل [المستشعر](sensor-health.md#add-a-sensor) بمجالات Active Directory، ستحتاج إلى تكوين حسابات خدمات الدليل.

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

    ![انتقل إلى الإعدادات، ثم الهويات.](../../media/defender-identity/settings-identities.png)

1. حدد **حسابات خدمة الدليل**. سترى الحسابات المقترنة بالمجالات.

    ![حسابات خدمة الدليل.](../../media/defender-identity/directory-service-accounts.png)

1. إذا قمت بتحديد حساب، سيتم فتح جزء مع إعدادات هذا الحساب.

    ![إعدادات الحساب.](../../media/defender-identity/account-settings.png)

1. لإضافة حساب جديد لخدمات الدليل، حدد **إنشاء حساب جديد** وملء اسم الحساب **والمجال وكلمة** **المرور**. يمكنك أيضا اختيار ما إذا كان حساب خدمة مدارة من قبل **المجموعة (** gMSA)، وإذا كان ينتمي إلى **مجال تسمية مفردة**.

    ![حساب خدمة الدليل الجديد.](../../media/defender-identity/new-directory-service-account.png)

1. حدد **حفظ**.

## <a name="see-also"></a>راجع أيضًا

- [حماية مستشعر الهوية وإعداداتها في Microsoft Defender](sensor-health.md)
