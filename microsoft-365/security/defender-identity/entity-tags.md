---
title: Microsoft Defender for Identity علامات الكيانات في Microsoft 365 Defender
description: تعرف على كيفية تطبيق علامات Microsoft Defender for Identity في Microsoft 365 Defender
ms.date: 06/08/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: c960f0cc1726155e733a0e88386fa7788cfc35e0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468050"
---
# <a name="defender-for-identity-entity-tags-in-microsoft-365-defender"></a>علامات كيان Defender for Identity في Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة [كيفية تطبيق علامات](/defender-for-identity) Microsoft Defender for Identity في [Microsoft 365 Defender.](/microsoft-365/security/defender/overview-security-center)

>[!IMPORTANT]
>كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

## <a name="entity-tags"></a>علامات الكيانات

في Microsoft 365 Defender، يمكنك تعيين ثلاثة أنواع من علامات كيان Defender for Identity **: العلامات** الحساسة والعلامات التي تم Exchange أو علامات **الخادم.**

لتعيين هذه العلامات، في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender، انتقل</a> **إلى الإعدادات** **ثم الهويات**.

:::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="الخيار &quot;الهويات&quot; ضمن العمود &quot;الاسم&quot; في الإعدادات &quot;" lightbox="../../media/defender-identity/settings-identities.png":::

ستظهر إعدادات العلامات ضمن **علامات الكيانات**.

:::image type="content" source="../../media/defender-identity/tag-settings.png" alt-text="جزء علامات الكيان" lightbox="../../media/defender-identity/tag-settings.png":::

لتعيين كل نوع من العلامات، اتبع الإرشادات أدناه.

## <a name="sensitive--tags"></a>العلامات الحساسة

يتم **استخدام العلامة الحساسة** لتحديد الأصول ذات القيمة العالية. يعتمد مسار الحركة اللاحقة أيضا على حالة حساسية كيان ما. تعتبر بعض الكيانات حساسة تلقائيا بواسطة Defender for Identity. للحصول على قائمة بهذه الأصول، راجع [الكيانات الحساسة](/defender-for-identity/manage-sensitive-honeytoken-accounts#sensitive-entities).

يمكنك أيضا وضع علامة على المستخدمين أو الأجهزة أو المجموعات يدويا على أنها حساسة.

1. حدد **حساسة**. سترى بعد ذلك المستخدمين **والأجهزة والمجموعات الحساسة** **الموجودة**.

   :::image type="content" source="../../media/defender-identity/sensitive-entities.png" alt-text="علامة التبويب &quot;الأجهزة&quot; في عنصر القائمة &quot;الوحدات الحساسة&quot;" lightbox="../../media/defender-identity/sensitive-entities.png":::

1. ضمن كل فئة، حدد **علامة...** لعلامة هذا النوع من الكيانات. على سبيل المثال، ضمن **مجموعات**، حدد **مجموعات العلامات.** سيتم فتح جزء مع المجموعات التي يمكنك تحديدها للعلامة. للبحث عن مجموعة، أدخل اسمها في مربع البحث.

   :::image type="content" source="../../media/defender-identity/add-groups.png" alt-text="خيار إضافة مجموعة" lightbox="../../media/defender-identity/add-groups.png":::

1. حدد المجموعة، وانقر **فوق إضافة تحديد.**

   :::image type="content" source="../../media/defender-identity/add-selection.png" alt-text="الخيار &quot;إضافة تحديد&quot;" lightbox="../../media/defender-identity/add-selection.png":::

## <a name="honeytoken-tags"></a>علامات Honeytoken

يتم استخدام الكيانات المتطفلة كشركات للممثلين الضارين. تؤدي أي مصادقة مقترنة بكيانات عسل هاته إلى تشغيل تنبيه.

يمكنك وضع علامة على المستخدمين أو الأجهزة باستخدام علامة **Honeytoken** بالطريقة نفسها التي تقوم بها بعلامة الحسابات الحساسة.

1. حدد **Honeytoken**. بعد ذلك، سترى أجهزة المستخدمين والأجهزة الموجودة التي تم  الوصول إلى **عسلها**.

    ![الوحدات المهزوم بهاني.](../../media/defender-identity/honeytoken-entities.png)

1. ضمن كل فئة، حدد **علامة...** لعلامة هذا النوع من الكيانات. على سبيل المثال، **ضمن المستخدمون**، حدد **وضع علامة على المستخدمين.** سيتم فتح جزء مع المجموعات التي يمكنك تحديدها للعلامة. للبحث عن مجموعة، أدخل اسمها في مربع البحث.

   :::image type="content" source="../../media/defender-identity/add-users.png" alt-text="خيار إضافة مستخدمين" lightbox="../../media/defender-identity/add-users.png":::

1. حدد المستخدم، وانقر **فوق إضافة تحديد.**

   :::image type="content" source="../../media/defender-identity/add-selected-user.png" alt-text="خيار إضافة مستخدم محدد" lightbox="../../media/defender-identity/add-selected-user.png":::

## <a name="exchange-server-tags"></a>Exchange علامات الخادم

يعتبر Defender for Identity Exchange الخوادم كموجودات ذات قيمة عالية ويقيمها **تلقائيا على أنها** حساسة. يمكنك أيضا وضع علامة يدويا على الأجهزة Exchange خوادم.

1. حدد **Exchange الخادم**. بعد ذلك، سترى الأجهزة الموجودة التي تسمى بعلامة Exchange **الخادم**.

   :::image type="content" source="../../media/defender-identity/exchange-servers.png" alt-text="عنصر Exchange الخادم" lightbox="../../media/defender-identity/exchange-servers.png":::

1. لعلامة جهاز كخادم Exchange، حدد **وضع علامة على الأجهزة**.  سيتم فتح جزء مع الأجهزة التي يمكنك تحديدها لعلامة. للبحث عن جهاز، أدخل اسمه في مربع البحث.

   :::image type="content" source="../../media/defender-identity/add-devices.png" alt-text="خيار إضافة جهاز" lightbox="../../media/defender-identity/add-devices.png":::

1. حدد جهازك، وانقر **فوق إضافة تحديد.**

   :::image type="content" source="../../media/defender-identity/select-device.png" alt-text="تحديد جهاز" lightbox="../../media/defender-identity/select-device.png":::

## <a name="see-also"></a>راجع أيضًا

- [إدارة تنبيهات أمان Defender for Identity](manage-security-alerts.md)
