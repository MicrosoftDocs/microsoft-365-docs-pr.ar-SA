---
title: Microsoft Defender for Identity الكشف في Microsoft 365 Defender
description: تعرف على كيفية تكوين استثناءات الكشف Microsoft Defender for Identity في Microsoft 365 Defender.
ms.date: 11/02/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e2df92e44b323bd0555407d72ebd48a7e050c9a5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473904"
---
# <a name="configure-defender-for-identity-detection-exclusions-in-microsoft-365-defender"></a>تكوين استثناءات الكشف عن الهوية ل Defender for Identity في Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة كيفية تكوين استثناءات [](/defender-for-identity) الكشف Microsoft Defender for Identity في [Microsoft 365 Defender.](/microsoft-365/security/defender/overview-security-center)

> [!IMPORTANT]
> كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

[!INCLUDE [Product long](includes/product-long.md)] تمكين استثناء عناوين IP أو أجهزة الكمبيوتر أو المجالات أو المستخدمين المعينين من عدد من الاكتشافات.

على سبيل المثال، يمكن تشغيل **تنبيه استطلاع DNS** بواسطة ماسح أمان يستخدم DNS كآلية فحص. يساعد إنشاء استثناء Defender for Identity على تجاهل مثل هذه الماسحات الضوئية وتقليل الإيجابيات الخاطئة.

>[!NOTE]
>من المجالات الأكثر شيوعا التي يتم فيها فتح الاتصالات المريبة عبر [تنبيهات DNS](/defender-for-identity/exfiltration-alerts#suspicious-communication-over-dns-external-id-2031) عليها، لاحظنا المجالات التي استثناها العملاء بشكل أكبر من التنبيه. تضاف هذه المجالات إلى قائمة الاستثناءات بشكل افتراضي، ولكن لديك خيار لإزالتها بسهولة.

## <a name="how-to-add-detection-exclusions"></a>كيفية إضافة استثناءات الكشف

1. في [Microsoft 365 Defender](https://security.microsoft.com/)، **انتقل إلى الإعدادات** ثم **الهويات**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="الخيار &quot;الهويات&quot; في العمود &quot;الاسم&quot;" lightbox="../../media/defender-identity/settings-identities.png":::

1. سترى بعد ذلك الوحدات **المستبعدة** في القائمة اليمنى.

   :::image type="content" source="../../media/defender-identity/excluded-entities.png" alt-text="جزء الكيانات المستبعدة" lightbox="../../media/defender-identity/excluded-entities.png":::

يمكنك بعد ذلك تعيين الاستثناءات باستخدام طريقتين: الاستثناءات **بواسطة قاعدة الكشف** **والكيانات المستبعدة العامة**.

## <a name="exclusions-by-detection-rule"></a>الاستثناءات حسب قاعدة الكشف

1. في القائمة اليمنى، حدد **الاستثناءات حسب قاعدة الكشف**. سترى قائمة بقواعد الكشف.

   :::image type="content" source="../../media/defender-identity/exclusions-by-detection-rule.png" alt-text="خيار قاعدة الاستثناءات حسب الكشف في عنصر الكيانات المستبعدة في الجزء الأيسر" lightbox="../../media/defender-identity/exclusions-by-detection-rule.png":::

1. لكل عملية كشف تريد تكوينها، قم بالخطوات التالية:

    1. حدد القاعدة. يمكنك البحث عن عمليات الكشف باستخدام شريط البحث. بمجرد تحديده، سيتم فتح جزء مع تفاصيل قاعدة الكشف.

       :::image type="content" source="../../media/defender-identity/detection-rule-details.png" alt-text="تفاصيل قاعدة الكشف" lightbox="../../media/defender-identity/detection-rule-details.png":::

    1. لإضافة استثناء، حدد الزر **الوحدات المستبعدة** ، ثم اختر نوع الاستثناء. تتوفر كيانات مستبعدة مختلفة لكل قاعدة. وهي تتضمن المستخدمين والأجهزة والمجالات وعناوين IP. في هذا المثال، الخيارات هي **استبعاد الأجهزة** واستبعاد **عناوين IP**.

       :::image type="content" source="../../media/defender-identity/exclude-devices-or-ip-addresses.png" alt-text="خيار استثناء الأجهزة أو عناوين IP" lightbox="../../media/defender-identity/exclude-devices-or-ip-addresses.png":::

    1. بعد اختيار نوع الاستثناء، يمكنك إضافة الاستثناء. في الجزء الذي يفتح، حدد **+** الزر لإضافة الاستثناء.

       :::image type="content" source="../../media/defender-identity/add-exclusion.png" alt-text="خيار إضافة استثناء" lightbox="../../media/defender-identity/add-exclusion.png":::

    1. ثم أضف الكيان الذي سيتم استبعاده. حدد **+ إضافة** لإضافة الكيان إلى القائمة.

       :::image type="content" source="../../media/defender-identity/add-excluded-entity.png" alt-text="خيار إضافة كيان سيتم استبعاده" lightbox="../../media/defender-identity/add-excluded-entity.png":::

    1. ثم حدد **استبعاد عناوين IP** (في هذا المثال) لإكمال الاستثناء.

       :::image type="content" source="../../media/defender-identity/exclude-ip-addresses.png" alt-text="خيار استبعاد عناوين IP" lightbox="../../media/defender-identity/exclude-ip-addresses.png":::

    1. بعد إضافة الاستثناءات، يمكنك تصدير القائمة أو إزالة الاستثناءات من خلال العودة إلى الزر **الكيانات المستبعدة** . في هذا المثال، لقد قمنا بعودة إلى **استبعاد الأجهزة**. لتصدير القائمة، حدد زر السهم لأسفل.

       :::image type="content" source="../../media/defender-identity/return-to-exclude-devices.png" alt-text="الخيار &quot;العودة إلى استبعاد الأجهزة&quot;" lightbox="../../media/defender-identity/return-to-exclude-devices.png":::

    1. لحذف استثناء، حدد الاستثناء وحدد أيقونة سلة المهملات.

       :::image type="content" source="../../media/defender-identity/delete-exclusion.png" alt-text="الخيار &quot;حذف استثناء&quot;" lightbox="../../media/defender-identity/delete-exclusion.png":::

## <a name="global-excluded-entities"></a>الكيانات المستثناة العامة

يمكنك الآن أيضا تكوين الاستثناءات بواسطة **الكيانات المستبعدة العامة**. تتيح لك الاستثناءات العامة تحديد بعض الكيانات (عناوين IP أو الشبكة الفرعية أو الأجهزة أو المجالات) التي سيتم استبعادها عبر كل الاكتشافات التي تم الحصول عليها من Defender for Identity. على سبيل المثال، إذا قمت باستبعاد جهاز، سيتم تطبيقه فقط على تلك الاكتشافات التي لها تعريف الجهاز كجزء من عملية الكشف.

1. في القائمة اليمنى، حدد **الكيانات المستبعدة العامة**. سترى فئات الكيانات التي يمكنك استبعادها.

   :::image type="content" source="../../media/defender-identity/global-excluded-entities.png" alt-text="عنصر القائمة الفرعية للكيانات المستبعدة العامة" lightbox="../../media/defender-identity/global-excluded-entities.png":::

1. اختر نوع استثناء. في هذا المثال، حددنا **استبعاد المجالات**.

   :::image type="content" source="../../media/defender-identity/exclude-domains.png" alt-text="علامة التبويب &quot;المجالات&quot;" lightbox="../../media/defender-identity/exclude-domains.png":::

1. سيتم فتح جزء حيث يمكنك إضافة مجال لتستبعده. أضف المجال الذي تريد استبعاده.

   :::image type="content" source="../../media/defender-identity/add-excluded-domain.png" alt-text="خيار إضافة مجال لاستثناءه" lightbox="../../media/defender-identity/add-excluded-domain.png":::

1. سيضاف المجال إلى القائمة. حدد **استبعاد المجالات** لإكمال الاستثناء.

   :::image type="content" source="../../media/defender-identity/select-exclude-domains.png" alt-text="خيار تحديد المجالات التي سيتم استبعادها" lightbox="../../media/defender-identity/select-exclude-domains.png":::

1. سترى بعد ذلك المجال في قائمة الكيانات التي سيتم استبعادها من كل قواعد الكشف. يمكنك تصدير القائمة أو إزالة الكيانات عن طريق تحديدها والنقر فوق **الزر** إزالة.

   :::image type="content" source="../../media/defender-identity/global-excluded-entries-list.png" alt-text="قائمة الإدخالات المستبعدة العامة" lightbox="../../media/defender-identity/global-excluded-entries-list.png":::

## <a name="see-also"></a>راجع أيضًا

- [إدارة تنبيهات أمان Defender for Identity](manage-security-alerts.md)
