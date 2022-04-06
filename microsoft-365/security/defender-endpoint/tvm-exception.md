---
title: إنشاء استثناءات لتوصيات الأمان وعرضها - إدارة المخاطر والثغرات الأمنية
description: إنشاء استثناءات لتوصيات الأمان ومراقبتها في إدارة المخاطر والثغرات الأمنية.
keywords: Microsoft Defender لنقطة النهاية، Microsoft Defender لنقطة النهاية tvm، إدارة المخاطر والثغرات الأمنية، & إدارة الثغرات الأمنية، & إدارة الثغرات الأمنية المعالجة، المعالجة بالتلفزيون intune، sccm المعالجة بالتلفزيون
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 00d7afd9daec71a14d4b789d1d6dcfe5eaf07d83
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477182"
---
# <a name="create-and-view-exceptions-for-security-recommendations---threat-and-vulnerability-management"></a>إنشاء استثناءات لتوصيات الأمان وعرضها - إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

كبديل لطلب المعالجة عندما لا تكون التوصية ذات صلة في الوقت الحالي، يمكنك إنشاء استثناءات لالتوصيات. إذا كانت مؤسستك لديها مجموعات أجهزة، يمكنك تحديد نطاق الاستثناء لمجموعات أجهزة معينة. يمكن إنشاء استثناءات لمجموعات الأجهزة المحددة أو لكل مجموعات الأجهزة السابقة والحاضرة.

عند إنشاء استثناء لتوصية، لن تكون التوصية نشطة حتى نهاية مدة الاستثناء. ستتغير حالة التوصية إلى **استثناء كامل** أو **استثناء جزئي** (حسب مجموعة الأجهزة).

## <a name="permissions"></a>الأذونات

يمكن للمستخدمين الذين لديهم أذونات "التعامل مع الاستثناءات" فقط إدارة الاستثناءات (بما في ذلك إنشاء أو إلغاء). [تعرف على المزيد حول أدوار RBAC](user-roles.md).

:::image type="content" source="images/tvm-exception-permissions.png" alt-text="إذن معالجة الاستثناء" lightbox="images/tvm-exception-permissions.png":::

## <a name="create-an-exception"></a>إنشاء استثناء

حدد توصية أمان تريد إنشاء استثناء لها، ثم حدد **خيارات الاستثناء** وملء النموذج.

:::image type="content" source="images/tvm-exception-options.png" alt-text="موقع الزر &quot;خيارات الاستثناء&quot; في منتحل توصيات الأمان" lightbox="images/tvm-exception-options.png":::

### <a name="exception-by-device-group"></a>استثناء حسب مجموعة الأجهزة

تطبيق الاستثناء على كل مجموعات الأجهزة الحالية أو اختيار مجموعات أجهزة معينة. لن يتم تضمين مجموعات الأجهزة المستقبلية في الاستثناء. لن يتم عرض مجموعات الأجهزة التي لديها استثناء بالفعل في القائمة. إذا حددت مجموعات أجهزة معينة فقط، ستتغير حالة التوصية من "نشط" إلى "استثناء جزئي". ستتغير الحالة إلى "استثناء كامل" إذا حددت كل مجموعات الأجهزة.

:::image type="content" source="images/tvm-exception-device-group-500.png" alt-text="المجموعة المنسدلة &quot;الجهاز&quot;" lightbox="images/tvm-exception-device-group-500.png":::

#### <a name="filtered-views"></a>طرق العرض التي تمت تصفيتها

إذا قمت بالتصفية حسب مجموعة الأجهزة على أي من إدارة المخاطر والثغرات الأمنية الصفحات، ستظهر مجموعات الأجهزة التي تمت تصفيتها فقط كالخيارات.

هذا هو الزر الذي تريد تصفيته حسب مجموعة الأجهزة على أي من صفحات إدارة المخاطر والثغرات الأمنية:

:::image type="content" source="images/tvm-selected-device-groups.png" alt-text="عامل تصفية مجموعات الأجهزة المحددة" lightbox="images/tvm-selected-device-groups.png":::

طريقة عرض الاستثناء مع مجموعات الأجهزة التي تمت تصفيتها:

:::image type="content" source="images/tvm-exception-device-filter500.png" alt-text="القائمة المنسدلة لمجموعة الأجهزة التي تمت تصفيتها" lightbox="images/tvm-exception-device-filter500.png":::

#### <a name="large-number-of-device-groups"></a>عدد كبير من مجموعات الأجهزة

إذا كانت مؤسستك لديها أكثر من 20 مجموعة أجهزة، فحدد **تحرير** بجانب خيار مجموعة الأجهزة التي تمت تصفيتها.

:::image type="content" source="images/tvm-exception-edit-groups.png" alt-text="إجراء تحرير أعداد كبيرة من المجموعات" lightbox="images/tvm-exception-edit-groups.png":::

ستظهر القائمة من خلال القائمة التي يمكنك البحث فيها واختيار مجموعات الأجهزة التي تريد تضمينها. حدد أيقونة علامة الاختيار أسفل بحث لتحديد/إلغاء تحديد الكل.

:::image type="content" source="images/tvm-exception-device-group-flyout-400.png" alt-text="مجموعة الأجهزة الكبيرة" lightbox="images/tvm-exception-device-group-flyout-400.png":::

### <a name="global-exceptions"></a>الاستثناءات العالمية

إذا كانت لديك أذونات المسؤول العام، يمكنك إنشاء استثناء عام وإلغائه. يؤثر ذلك **على** كل مجموعات الأجهزة الحالية والمستقبلية في مؤسستك، ولن يتمكن من تغييره سوى المستخدم الذي له إذن مماثل. ستتغير حالة التوصية من "نشط" إلى "استثناء كامل".

:::image type="content" source="images/tvm-exception-global.png" alt-text="خيار الاستثناء العام" lightbox="images/tvm-exception-global.png":::

بعض الأمور التي يجب تذكرها:

- إذا كانت هناك توصية ضمن استثناء عام، سيتم تعليق الاستثناءات التي تم إنشاؤها حديثا لمجموعات الأجهزة حتى انتهاء صلاحية الاستثناء العام أو إلغاؤه. بعد هذه النقطة، ستدخل استثناءات مجموعة الأجهزة الجديدة حيز التنفيذ حتى انتهاء صلاحيتها.
- إذا كانت هناك توصية لها استثناءات لمجموعات أجهزة معينة، وكان هناك استثناء عام تم إنشاؤه، سيتم إيقاف استثناء مجموعة الأجهزة مؤقتا حتى انتهاء صلاحيته أو يتم إلغاء الاستثناء العام قبل انتهاء صلاحيته.

### <a name="justification"></a>التبرير

حدد مبرر الاستثناء الذي تحتاج إلى تقديمه بدلا من معالجة توصية الأمان المعنية. املأ سياق التبرير، ثم قم بتعيين مدة الاستثناء.

تفصيل القائمة التالية التبريرات وراء خيارات الاستثناءات:

- **عنصر تحكم جهة خارجية** - يتناول منتج أو برنامج من جهة خارجية هذه التوصية بالفعل - يؤدي اختيار نوع التبرير هذا إلى خفض درجة التعرض وزيادة نقاطك الآمنة بسبب تقليل المخاطر
- **تخفيف بديل** - تعالج أداة داخلية هذه التوصية بالفعل - يؤدي اختيار نوع التبرير هذا إلى خفض درجة التعرض وزيادة نقاطك الآمنة بسبب تقليل المخاطر
- **قبول المخاطر** - المخاطر المنخفضة و/أو تنفيذ التوصية مكلفة جدا
- **المعالجة المخطط لها (نعمة)** - تم التخطيط لها بالفعل ولكن بانتظار التنفيذ أو التفويض

## <a name="view-all-exceptions"></a>عرض كل الاستثناءات

انتقل إلى **علامة التبويب استثناءات** في **صفحة المعالجة** . يمكنك التصفية حسب التبرير والنوع الحالة.

 حدد استثناء لفتح منزه مع مزيد من التفاصيل. ستضم مجموعة الاستثناءات لكل جهاز قائمة بكل مجموعة أجهزة يغطيها الاستثناء، والتي يمكنك تصديرها. يمكنك أيضا عرض التوصية ذات الصلة أو إلغاء الاستثناء.

:::image type="content" source="images/tvm-exception-view.png" alt-text="علامة التبويب &quot;استثناءات&quot; في صفحة &quot;المعالجة&quot;" lightbox="images/tvm-exception-view.png":::

## <a name="how-to-cancel-an-exception"></a>كيفية إلغاء استثناء

لإلغاء استثناء، انتقل إلى علامة **التبويب استثناءات** في **صفحة المعالجة** . حدد الاستثناء.

لإلغاء الاستثناء لكل مجموعات الأجهزة أو استثناء عام، حدد الزر إلغاء **الاستثناء لكل مجموعات** الأجهزة. لن تتمكن من إلغاء الاستثناءات إلا لمجموعات الأجهزة التي تملك أذونات لها.

:::image type="content" source="images/tvm-exception-cancel.png" alt-text="الزر &quot;إلغاء الأمر&quot;" lightbox="images/tvm-exception-cancel.png":::

### <a name="cancel-the-exception-for-a-specific-device-group"></a>إلغاء الاستثناء لمجموعة أجهزة معينة

حدد مجموعة الأجهزة المحددة لإلغاء الاستثناء الخاص بها. ستظهر من خلال منير لمجموعة الأجهزة، كما يمكنك تحديد **إلغاء الاستثناء**.

:::image type="content" source="images/tvm-exception-device-group-hover.png" alt-text="إجراء تحديد مجموعة أجهزة معينة" lightbox="images/tvm-exception-device-group-hover.png":::

## <a name="view-impact-after-exceptions-are-applied"></a>عرض التأثير بعد تطبيق الاستثناءات

في صفحة الأمان التوصيات، حدد تخصيص **الأعمدة** وحدد المربعات للأجهزة المعرضة **(** بعد الاستثناءات) والتأثير **(بعد الاستثناءات)**.

:::image type="content" source="images/tvm-after-exceptions.png" alt-text="خيارات تخصيص الأعمدة" lightbox="images/tvm-after-exceptions.png":::

يعرض عمود الأجهزة المعرضة (بعد الاستثناءات) الأجهزة المتبقية التي لا تزال عرضة لنقاط الضعف بعد تطبيق الاستثناءات. تتضمن مبررات الاستثناءات التي تؤثر على التعرض 'التحكم من جهة خارجية' و'تخفيف بديل'. لا تقلل التبريرات الأخرى من التعرض لجهاز، ولا تزال تعتبر مكشوفة.

يظهر التأثير (بعد الاستثناءات) التأثير المتبقي على درجة التعرض للضوء أو الدرجة الآمنة بعد تطبيق الاستثناءات. تتضمن مبررات الاستثناءات التي تؤثر على النقاط "تحكم جهة خارجية" و"تخفيف بديل". لا تقلل التبريرات الأخرى من التعرض لجهاز، وبالتالي لا تتغير درجة التعرض للضوء والنتيجة الآمنة.

:::image type="content" source="images/tvm-after-exceptions-table.png" alt-text="الأعمدة في الجدول" lightbox="images/tvm-after-exceptions-table.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [إصلاح الثغرات](tvm-remediation.md)
- [توصيات الأمان](tvm-security-recommendation.md)
- [درجة التعرض للضوء](tvm-exposure-score.md)
- [Microsoft Secure Score للأجهزة](tvm-microsoft-secure-score-devices.md)
