---
title: ربط نتائج الاستعلام بحادث
description: ربط نتائج الاستعلام بحادث
keywords: الصيد المتقدم، والحادث، وال pivot، والكيانات، والصيد، والأحداث ذات الصلة، وصيد التهديدات عبر الإنترنت، والبحث، والاستعلام، والتعقب، Microsoft 365، Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 8a1b8e11d16f0bf0d20739af8ff5699eb150c6f7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63583729"
---
# <a name="link-query-results-to-an-incident"></a>ربط نتائج الاستعلام بحادث

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

يتيح لك الارتباط بميزة الحادث إضافة نتائج استعلام بحث متقدمة إلى حادث جديد أو موجود قيد التحقيق. تساعدك هذه الميزة على تسجيل السجلات بسهولة من أنشطة الصيد المتقدمة حتى تتمكن من إنشاء مخطط زمني أو سياق أحداث أكثر ثرية تتعلق بحادث ما. 

## <a name="link-results-to-new-or-existing-incidents"></a>ربط النتائج بالحوادث الجديدة أو الموجودة

1. في صفحة استعلام البحث المتقدم، أدخل الاستعلام أولا في حقل الاستعلام الذي تم توفيره ثم حدد **تشغيل الاستعلام** للحصول على النتائج.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="مثال على صفحة **استعلام** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-1.png":::

2. في صفحة النتائج، حدد الأحداث أو السجلات المرتبطة بتحريات جديدة أو حالية تعمل عليها، ثم حدد **ارتباط بالحادث**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="الخيار **ارتباط إلى الحادث** ل علامة التبويب **النتائج** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-1b.png":::

3. ابحث عن **المقطع تفاصيل** التنبيه في الجزء ارتباط بحادث، ثم حدد إنشاء حدث جديد  لتحويل الأحداث إلى تنبيهات و تجميعها إلى حادث جديد:

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="مثال على المقطع **تفاصيل التنبيه** في الجزء **ارتباط بالحادث** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    أو حدد **ارتباط إلى حادث موجود** لإضافة السجلات المحددة إلى سجل موجود. اختر الحادث المرتبط من القائمة المنسدلة للحوادث الموجودة. يمكنك أيضا إدخال الأحرف القليلة الأولى من اسم الحادث أو المعرف للعثور على الحادث الموجود. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="مثال على مقطع **تفاصيل التنبيه** في الجزء **ارتباط بالحادث** في مدخل Microsoft 365 Defender":::

4. لأي من التحديدين، قم بتوفير التفاصيل التالية، ثم حدد **التالي**:
      - **عنوان التنبيه** - توفير عنوان وصفي للنتائج التي يمكن لمستجيبي الأحداث فهمها. ويصبح هذا العنوان عنوان التنبيه.
      - **الخطورة** - اختر الخطورة المطبقة على مجموعة التنبيهات.
      - **الفئة** - اختر فئة التهديدات المناسبة للتنبيهات.
      - **الوصف** - امنح وصفا مفيدا للتنبيهات التي تم تجميعها.
      - **الإجراءات الموصى بها** - توفير إجراءات المعالجة.

5. في القسم **الكيانات المتأثرة** ، حدد الكيان الرئيسي المتأثر أو المتأثر. تظهر الكيانات القابلة للتطبيق استنادا إلى نتائج الاستعلام فقط في هذا القسم. في مثالنا، استخدمنا استعلاما للعثور على أحداث ذات صلة بحادث محتمل لطرح البريد الإلكتروني، وبالتالي فإن المرسل هو الكيان المتأثير. إذا كان هناك أربعة مرسلين مختلفين، على سبيل المثال، يتم إنشاء أربعة تنبيهات وربطها بالحادث الذي تم اختياره.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="مثال على كيان متأثّر في المقطع **ارتباط إلى حادث** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. حدد **التالي**.
1. راجع التفاصيل التي قدمتها في **القسم ملخص** .
     :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="مثال لصفحة النتائج في المقطع **ارتباط بالحادث** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. حدد **تم**.

## <a name="view-linked-records-in-the-incident"></a>عرض السجلات المرتبطة في الحادث

يمكنك تحديد اسم الحدث لعرض الحدث الذي ترتبط به الأحداث.
     :::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="مثال على شاشة تفاصيل الحدث في علامة التبويب **ملخص** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-6-incident-pg.png":::

في مثالنا، تم ربط التنبيهات الأربعة، التي تمثل الأحداث الأربعة المحددة، بحادث جديد بنجاح. 

في كل صفحة من صفحات التنبيه، يمكنك العثور على المعلومات الكاملة حول الحدث أو الأحداث في طريقة عرض المخطط الزمني (إذا كانت متوفرة) وعرض نتائج الاستعلام.
     :::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="مثال على التفاصيل الكاملة لحدث ما في علامة التبويب **المخطط الزمني** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-7-alert-story.png":::

يمكنك أيضا تحديد الحدث لفتح الجزء **فحص** السجل.
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="مثال لفحص تفاصيل سجل حدث في علامة التبويب **اليوميات** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>التصفية للأحداث التي تمت إضافتها باستخدام الصيد المتقدم
يمكنك عرض التنبيهات التي تم إنشاؤها من عمليات البحث المتقدمة من خلال تصفية قائمة انتظار "الأحداث" و"قائمة انتظار التنبيهات" حسب **مصدر** الكشف اليدوي.

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="مثال على التصفية اليدوية لحوادث وتنبيهات في صفحة **عوامل التصفية** في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-8-filter.png":::
