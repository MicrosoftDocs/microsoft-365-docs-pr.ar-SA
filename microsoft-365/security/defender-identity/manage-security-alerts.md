---
title: تنبيهات أمان Microsoft Defender for Identity في Microsoft 365 Defender
description: تعرف على كيفية إدارة تنبيهات الأمان الصادرة عن Microsoft Defender for Identity ومراجعتها في Microsoft 365 Defender
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.openlocfilehash: 072654e8047989552d86f4030e420078e4ae1cc2
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/15/2021
ms.locfileid: "63583292"
---
# <a name="defender-for-identity-security-alerts-in-microsoft-365-defender"></a>تنبيهات أمان Defender for Identity في Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة أساسيات كيفية استخدام [تنبيهات أمان Microsoft Defender for Identity](/defender-for-identity) [في Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

يتم دمج تنبيهات Defender for <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Identity</a> في Microsoft 365 Defender مع تنسيق صفحة تنبيه هوية مخصص. يمثل ذلك الخطوة الأولى في الرحلة لتقديم تجربة [Microsoft Defender الكاملة للهوية في](/defender-for-identity/defender-for-identity-in-microsoft-365-defender) Microsoft 365 Defender.

تمنح صفحة تنبيه الهوية الجديدة عملاء Microsoft Defender for Identity قدرات أفضل لإثراء الإشارات عبر المجالات وإمكانيات استجابة تلقائية جديدة للهوية. يضمن لك الحفاظ على أمانك ويساعد على تحسين فعالية عمليات الأمان.

إحدى فوائد التحقق من التنبيهات من خلال Microsoft 365 Defender هي [](/microsoft-365/security/defender/microsoft-365-defender) ارتباط تنبيهات Microsoft Defender for Identity بشكل أكبر بالمعلومات التي يتم الحصول عليها من كل من المنتجات الأخرى في المجموعة. هذه التنبيهات المحسنة متناسقة مع تنسيقات التنبيهات Microsoft 365 Defender الأخرى التي تم Office 365 [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint).[](/microsoft-365/security/office-365-security) تلغي الصفحة الجديدة بشكل فعال الحاجة إلى الانتقال إلى مدخل منتج آخر للتحقق من التنبيهات المقترنة بالهوية.

يمكن للتنبيهات الصادرة من Defender for Identity الآن تشغيل قدرات Microsoft 365 Defender التلقائية الخاصة بالتحري والاستجابة [(AIR)،](/microsoft-365/security/defender/m365d-autoir) بما في ذلك تنبيهات المعالجة التلقائية وتخفيف الأدوات والعمليات التي يمكن أن تساهم في النشاط المريب.

> [!IMPORTANT]
> كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

## <a name="review-security-alerts"></a>مراجعة تنبيهات الأمان

يمكن الوصول إلى التنبيهات من مواقع متعددة، بما في ذلك  صفحة التنبيهات وصفحة  الأحداث وصفحات الأجهزة الفردية ومن صفحة **الصيد المتقدم.** في هذا المثال، سنقوم بمراجعة **صفحة التنبيهات**.

في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، انتقل إلى & **تنبيهات** ثم **إلى تنبيهات**.

![انتقل إلى الأحداث والتنبيهات، ثم التنبيهات.](../../media/defender-identity/incidents-alerts.png)

لرؤية التنبيهات من Defender for Identity، في الجزء العلوي الأيمن حدد **عامل** التصفية، ثم ضمن مصادر  الخدمة حدد **Microsoft Defender for Identity**، وحدد **تطبيق**:

![تصفية أحداث Defender for Identity.](../../media/defender-identity/filter-defender-for-identity.png)

يتم عرض التنبيهات بمعلومات في الأعمدة **التالية: اسم** التنبيه والعلامات والخطورة حالة التحقيق، الحالة، الفئة، مصدر الكشف، الأصول التي تم التأثير عليها، النشاط الأول، النشاط **الأخير**. 

![Defender for Identity events.](../../media/defender-identity/filtered-alerts.png)

## <a name="manage-alerts"></a>إدارة التنبيهات

إذا نقرت فوق اسم **التنبيه** لأحد التنبيهات، فسوف تذهب إلى الصفحة مع تفاصيل حول التنبيه. في الجزء الأيسر، سترى ملخصا لما **حدث**:

![ما حدث في التنبيه.](../../media/defender-identity/what-happened.png)

يوجد أعلى **المربع** ماذا حدث أزرار **للحسابات ومضيف** الوجهة  **ومضيف المصدر** للتنبيه. بالنسبة للتنبيهات الأخرى، قد ترى أزرارا للحصول على تفاصيل حول المزيد من المضيفين والحسابات وعناوين IP والمجالات ومجموعات الأمان. حدد أي منها للحصول على مزيد من التفاصيل حول الكيانات المعنية.

في الجزء الأيمن، سترى تفاصيل **التنبيه**. يمكنك هنا الاطلاع على مزيد من التفاصيل وأداء العديد من المهام:

- **تصنيف هذا التنبيه** - يمكنك هنا تعيين هذا التنبيه كتنبيه **True** أو **تنبيه خطأ**

    ![تنبيه تصنيف.](../../media/defender-identity/classify-alert.png)

- **حالة التنبيه** - في **Set تصنيف**، يمكنك تصنيف التنبيه على أنه **True** أو **False**. في **تعيين إلى**، يمكنك تعيين التنبيه إلى نفسك أو إلى عدم تعيينه.

    ![حالة التنبيه.](../../media/defender-identity/alert-state.png)

- تفاصيل **التنبيه - ضمن** تفاصيل التنبيه، يمكنك العثور على مزيد من المعلومات حول التنبيه المحدد، واتبع ارتباطا إلى وثائق حول نوع التنبيه، وراجع ما هو الحادث المقترن بالتنبيه، وراجع أي تحقيق تلقائي مرتبط بنوع التنبيه هذا، وراجع الأجهزة والمستخدمين ذوي التأثير.

    ![تفاصيل التنبيه.](../../media/defender-identity/alert-details.png)

- **التعليقات & المحفوظات** - يمكنك هنا إضافة تعليقاتك إلى التنبيه، لمشاهدة محفوظات جميع الإجراءات المقترنة بالتنبيه.

    ![التعليقات والمحفوظات.](../../media/defender-identity/comments-history.png)

- **إدارة التنبيه** - إذا حددت **إدارة** التنبيه، فسوف تذهب إلى جزء يسمح لك بتحرير:
  - **الحالة** - يمكنك اختيار **جديد** أو **تم الحل** أو **في تقدم**.
  - **التصنيف** - يمكنك اختيار **تنبيه True أو** **تنبيه خطأ**.
  - **تعليق** - يمكنك إضافة تعليق حول التنبيه.

    إذا حددت النقاط الثلاث إلى بجانب إدارة التنبيه، يمكنك استشارة خبير في التهديدات أو تصدير التنبيه إلى ملف  Excel آخر أو إنشاء **ارتباط إلى حادث آخر**.

    ![إدارة التنبيه.](../../media/defender-identity/manage-alert.png)

    > [!NOTE]
    > في ملف Excel، لديك الآن ارتباطان متوفران: عرض في **Microsoft Defender للهوية** وعرض **في** Microsoft 365 Defender. سيحضرك كل ارتباط إلى المدخل ذي الصلة، وسيوفر معلومات حول التنبيه هناك.

## <a name="see-also"></a>راجع أيضًا

- [التحقق من التنبيهات في Microsoft 365 Defender](../defender/investigate-alerts.md)
