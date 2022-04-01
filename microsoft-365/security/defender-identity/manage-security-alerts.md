---
title: Microsoft Defender for Identity تنبيهات الأمان في Microsoft 365 Defender
description: تعرف على كيفية إدارة تنبيهات الأمان الصادرة عن Microsoft Defender for Identity في Microsoft 365 Defender
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 3023dc05550aeee5a9d47bb7561eb221c6d1c588
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465806"
---
# <a name="defender-for-identity-security-alerts-in-microsoft-365-defender"></a>تنبيهات أمان Defender for Identity في Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة أساسيات كيفية استخدام تنبيهات [Microsoft Defender for Identity في Microsoft 365 Defender](/defender-for-identity)[.](/microsoft-365/security/defender/overview-security-center)

يتم دمج تنبيهات Defender for <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Identity</a> في Microsoft 365 Defender مع تنسيق صفحة تنبيه هوية مخصص. وهذا يمثل الخطوة الأولى في الرحلة لتقديم التجربة الكاملة Microsoft Defender for Identity [في Microsoft 365 Defender](/defender-for-identity/defender-for-identity-in-microsoft-365-defender).

توفر صفحة تنبيه الهوية الجديدة للعملاء Microsoft Defender for Identity قدرات أفضل لإثراء الإشارة عبر المجالات وإمكانيات استجابة تلقائية جديدة للهوية. يضمن لك الحفاظ على أمانك ويساعد على تحسين فعالية عمليات الأمان.

إحدى فوائد التحقق من التنبيهات من خلال Microsoft 365 Defender هي [](/microsoft-365/security/defender/microsoft-365-defender) أن Microsoft Defender for Identity التنبيهات مرتبطة بشكل أكبر بالمعلومات التي يتم الحصول عليها من كل من المنتجات الأخرى في المجموعة. هذه التنبيهات المحسنة متناسقة مع تنسيقات التنبيهات Microsoft 365 Defender الأخرى التي تنشأ من Microsoft Defender لـ Office 365 [Microsoft Defender لنقطة النهاية.](/microsoft-365/security/defender-endpoint)[](/microsoft-365/security/office-365-security) تلغي الصفحة الجديدة بشكل فعال الحاجة إلى الانتقال إلى مدخل منتج آخر للتحقق من التنبيهات المقترنة بالهوية.

يمكن للتنبيهات الصادرة من Defender for Identity الآن تشغيل قدرات Microsoft 365 Defender التلقائية الخاصة بالتحري والاستجابة [(AIR)،](/microsoft-365/security/defender/m365d-autoir) بما في ذلك تنبيهات المعالجة التلقائية وتخفيف الأدوات والعمليات التي يمكن أن تساهم في النشاط المريب.

> [!IMPORTANT]
> كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

## <a name="review-security-alerts"></a>مراجعة تنبيهات الأمان

يمكن الوصول إلى التنبيهات من مواقع متعددة، بما في ذلك  صفحة التنبيهات وصفحة  الأحداث وصفحات الأجهزة الفردية ومن صفحة **الصيد المتقدم.** في هذا المثال، سنقوم بمراجعة **صفحة التنبيهات**.

في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، انتقل إلى & **تنبيهات** ثم **إلى تنبيهات**.

:::image type="content" source="../../media/defender-identity/incidents-alerts.png" alt-text="عنصر القائمة &quot;تنبيهات&quot;" lightbox="../../media/defender-identity/incidents-alerts.png":::

لرؤية التنبيهات من Defender for Identity، في الجزء العلوي الأيمن حدد **عامل** التصفية، ثم ضمن **مصادر** الخدمة، حدد Microsoft Defender for Identity، وحدد **تطبيق**:

:::image type="content" source="../../media/defender-identity/filter-defender-for-identity.png" alt-text="عامل التصفية للأحداث &quot;Defender for Identity&quot;" lightbox="../../media/defender-identity/filter-defender-for-identity.png":::

يتم عرض التنبيهات بمعلومات في الأعمدة **التالية: اسم** التنبيه والعلامات والخطورة حالة التحقيق، الحالة، الفئة، مصدر الكشف، الأصول التي تم التأثير عليها، النشاط الأول، النشاط **الأخير**. 

:::image type="content" source="../../media/defender-identity/filtered-alerts.png" alt-text="أحداث Defender for Identity" lightbox="../../media/defender-identity/filtered-alerts.png":::

## <a name="manage-alerts"></a>إدارة التنبيهات

إذا نقرت فوق اسم **التنبيه** لأحد التنبيهات، فسوف تذهب إلى الصفحة مع تفاصيل حول التنبيه. في الجزء الأيسر، سترى ملخصا لما **حدث**:

:::image type="content" source="../../media/defender-identity/what-happened.png" alt-text="الجزء &quot;ماذا حدث&quot;" lightbox="../../media/defender-identity/what-happened.png":::

يوجد أعلى **المربع** ماذا حدث أزرار **للحسابات ومضيف** الوجهة  **ومضيف المصدر** للتنبيه. بالنسبة للتنبيهات الأخرى، قد ترى أزرارا للحصول على تفاصيل حول المزيد من المضيفين والحسابات وعناوين IP والمجالات ومجموعات الأمان. حدد أي منها للحصول على مزيد من التفاصيل حول الكيانات المعنية.

في الجزء الأيمن، سترى تفاصيل **التنبيه**. يمكنك هنا الاطلاع على مزيد من التفاصيل وأداء العديد من المهام:

- **تصنيف هذا التنبيه** - يمكنك هنا تعيين هذا التنبيه كتنبيه **True** أو **تنبيه خطأ**

    :::image type="content" source="../../media/defender-identity/classify-alert.png" alt-text="الصفحة التي يمكنك تصنيف تنبيه فيها" lightbox="../../media/defender-identity/classify-alert.png":::

- **حالة التنبيه** - في **Set تصنيف**، يمكنك تصنيف التنبيه على أنه **True** أو **False**. في **تعيين إلى**، يمكنك تعيين التنبيه إلى نفسك أو إلى عدم تعيينه.

    :::image type="content" source="../../media/defender-identity/alert-state.png" alt-text="جزء حالة التنبيه" lightbox="../../media/defender-identity/alert-state.png":::

- تفاصيل **التنبيه - ضمن** تفاصيل التنبيه، يمكنك العثور على مزيد من المعلومات حول التنبيه المحدد، واتبع ارتباطا إلى وثائق حول نوع التنبيه، وراجع ما هو الحادث المقترن بالتنبيه، وراجع أي تحقيق تلقائي مرتبط بنوع التنبيه هذا، وراجع الأجهزة والمستخدمين ذوي التأثير.

   :::image type="content" source="../../media/defender-identity/alert-details.png" alt-text="صفحة تفاصيل التنبيه" lightbox="../../media/defender-identity/alert-details.png":::

- **التعليقات & المحفوظات** - يمكنك هنا إضافة تعليقاتك إلى التنبيه، لمشاهدة محفوظات جميع الإجراءات المقترنة بالتنبيه.

    :::image type="content" source="../../media/defender-identity/comments-history.png" alt-text="صفحة محفوظات & التعليقات" lightbox="../../media/defender-identity/comments-history.png":::

- **إدارة التنبيه** - إذا حددت **إدارة** التنبيه، فسوف تذهب إلى جزء يسمح لك بتحرير:
  - **الحالة** - يمكنك اختيار **جديد** أو **تم الحل** أو **في تقدم**.
  - **التصنيف** - يمكنك اختيار **تنبيه True أو** **تنبيه خطأ**.
  - **تعليق** - يمكنك إضافة تعليق حول التنبيه.

    إذا حددت النقاط الثلاث إلى بجانب إدارة التنبيه، يمكنك استشارة خبير في التهديدات أو تصدير التنبيه إلى ملف  Excel آخر أو إنشاء **ارتباط إلى حادث آخر**.

    :::image type="content" source="../../media/defender-identity/manage-alert.png" alt-text="الخيار &quot;إدارة التنبيه&quot;" lightbox="../../media/defender-identity/manage-alert.png":::

    > [!NOTE]
    > في ملف Excel، لديك الآن ارتباطان **متوفران**: عرض Microsoft Defender for Identity وعرض **في Microsoft 365 Defender**. سيحضرك كل ارتباط إلى المدخل ذي الصلة، وسيوفر معلومات حول التنبيه هناك.

## <a name="see-also"></a>راجع أيضًا

- [التحقق من التنبيهات في Microsoft 365 Defender](../defender/investigate-alerts.md)
