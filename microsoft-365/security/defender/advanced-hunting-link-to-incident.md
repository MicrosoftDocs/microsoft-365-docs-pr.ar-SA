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
ms.openlocfilehash: c81b0b0850686242c675629cf99fa2c4b3a18496
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755496"
---
# <a name="link-query-results-to-an-incident"></a>ربط نتائج الاستعلام بحادث

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

يمكنك استخدام الارتباط إلى ميزة الحادث لإضافة نتائج استعلام بحث متقدمة إلى حادث جديد أو موجود قيد التحقيق. تساعدك هذه الميزة على تسجيل السجلات بسهولة من أنشطة الصيد المتقدمة، التي تمكنك من إنشاء مخطط زمني أو سياق أحداث أكثر غنى فيما يتعلق بحادث ما. 

## <a name="link-results-to-new-or-existing-incidents"></a>ربط النتائج بالحوادث الجديدة أو الموجودة

1. في صفحة استعلام البحث المتقدم، أدخل الاستعلام أولا في حقل الاستعلام الذي تم توفيره ثم حدد **تشغيل الاستعلام** للحصول على النتائج.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="صفحة الاستعلام في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-1.png":::

2. في صفحة النتائج، حدد الأحداث أو السجلات المرتبطة بتحريات جديدة أو حالية تعمل عليها، ثم حدد **ارتباط بالحادث**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="الخيار &quot;ارتباط بحادث&quot; من علامة التبويب &quot;نتائج&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-1b.png":::

3. ابحث عن **المقطع تفاصيل** التنبيه في الجزء ارتباط بحادث، ثم حدد إنشاء حدث جديد  لتحويل الأحداث إلى تنبيهات و تجميعها إلى حادث جديد:

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="المقطع &quot;تفاصيل التنبيه&quot; في الجزء &quot;ارتباط بحادث&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    أو حدد **ارتباط إلى حادث موجود** لإضافة السجلات المحددة إلى سجل موجود. اختر الحادث المرتبط من القائمة المنسدلة للحوادث الموجودة. يمكنك أيضا إدخال الأحرف القليلة الأولى من اسم الحادث أو المعرف للعثور على الحادث الموجود. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="مقطع تفاصيل التنبيه في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-3-link-to-existing.png":::

4. لأي من التحديدين، قم بتوفير التفاصيل التالية، ثم حدد **التالي**:
      - **عنوان التنبيه** - توفير عنوان وصفي للنتائج التي يمكن لمستجيبي الأحداث فهمها. يصبح هذا العنوان الوصفي عنوان التنبيه.
      - **الخطورة** - اختر الخطورة المطبقة على مجموعة التنبيهات.
      - **الفئة** - اختر فئة التهديدات المناسبة للتنبيهات.
      - **الوصف** - امنح وصفا مفيدا للتنبيهات التي تم تجميعها.
      - **الإجراءات الموصى بها** - توفير إجراءات المعالجة.

5. في القسم **الكيانات المتأثرة** ، حدد الكيان الرئيسي المتأثر أو المتأثر. تظهر الكيانات القابلة للتطبيق استنادا إلى نتائج الاستعلام فقط في هذا القسم. في مثالنا، استخدمنا استعلاما للعثور على أحداث ذات صلة بحادث محتمل لطرح البريد الإلكتروني، وبالتالي فإن المرسل هو الكيان المتأثير. إذا كان هناك أربعة مرسلين مختلفين، على سبيل المثال، يتم إنشاء أربعة تنبيهات وربطها بالحادث الذي تم اختياره.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="الكيان المتأثّر في المقطع &quot;ارتباط بحادث&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. حدد **التالي**.
1. راجع التفاصيل التي قدمتها في **القسم ملخص** .
   :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="صفحة النتائج في المقطع ارتباط إلى حادث في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. حدد **تم**.

## <a name="view-linked-records-in-the-incident"></a>عرض السجلات المرتبطة في الحادث

يمكنك تحديد اسم الحدث لعرض الحدث الذي ترتبط به الأحداث.
:::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="شاشة تفاصيل الحدث في علامة التبويب &quot;ملخص&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-6-incident-pg.png":::

في مثالنا، تم ربط التنبيهات الأربعة، التي تمثل الأحداث الأربعة المحددة، بحادث جديد بنجاح. 

في كل صفحة من صفحات التنبيه، يمكنك العثور على المعلومات الكاملة حول الحدث أو الأحداث في طريقة عرض المخطط الزمني (إذا كانت متوفرة) وعرض نتائج الاستعلام.
:::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="التفاصيل الكاملة لحدث ما في علامة التبويب &quot;المخطط الزمني&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-7-alert-story.png":::

يمكنك أيضا تحديد الحدث لفتح الجزء **فحص** السجل.
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="فحص تفاصيل سجل حدث ما في علامة التبويب &quot;المخطط الزمني&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>التصفية للأحداث التي تمت إضافتها باستخدام الصيد المتقدم
يمكنك عرض التنبيهات التي تم إنشاؤها من عمليات البحث المتقدمة من خلال تصفية قائمة انتظار "الأحداث" و"قائمة انتظار التنبيهات" حسب **مصدر** الكشف اليدوي.

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="التصفية اليدوية لصفات الأحداث والتنبيهات في صفحة عوامل التصفية في مدخل Microsoft 365 Defender" lightbox="../../media/link-to-incident-8-filter.png":::
