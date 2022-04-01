---
title: التقنيات في المخطط الزمني للجهاز
description: فهم المخطط الزمني للجهاز في Microsoft Defender لنقطة النهاية
keywords: مخطط زمني للجهاز ونقطة النهاية و MITRE و MITRE ATT&CK والتقنيات والالأساليب
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d724b7663bd4484c630e97362eb5766490e1fa8e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465894"
---
# <a name="techniques-in-the-device-timeline"></a>التقنيات في المخطط الزمني للجهاز

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

يمكنك الحصول على مزيد من المعرفة في التحقيق من خلال تحليل الأحداث التي حدثت على جهاز معين. أولا، حدد الجهاز الذي يهمك من [قائمة الأجهزة](machines-view-overview.md). على صفحة الجهاز، يمكنك تحديد علامة **التبويب المخطط الزمني** لعرض كل الأحداث التي وقعت على الجهاز.

## <a name="understand-techniques-in-the-timeline"></a>فهم التقنيات في المخطط الزمني

> [!IMPORTANT]
> تتعلق بعض المعلومات بميزة منتج تم إصدارها مسبقا في المعاينة العامة والتي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

في Microsoft Defender لنقطة النهاية **، التقنيات** هي نوع بيانات إضافي في المخطط الزمني للحدث. توفر التقنيات معرفة أكثر حول الأنشطة المقترنة ب [MITRE ATT&تقنيات أو تقنيات CK](https://attack.mitre.org/) الفرعية.

تبسط هذه الميزة تجربة التحقيق من خلال مساعدة المحللين على فهم الأنشطة التي تم ملاحظتها على جهاز. يمكن للمحللين عندئذ أن يقرروا إجراء المزيد من التحقيق.

للمعاينة العامة، تتوفر التقنيات بشكل افتراضي، كما تظهر مع الأحداث عند عرض المخطط الزمني للجهاز.

:::image type="content" source="images/device-timeline-2.png" alt-text="التقنيات في المخطط الزمني للجهاز" lightbox="images/device-timeline-2.png":::

يتم تمييز التقنيات بنص غامق، كما تظهر مع أيقونة زرقاء على اليمين. يظهر أيضا اسم أسلوب&MITRE ATT&CK ID واسم التقنية كعلامات ضمن معلومات إضافية.

تتوفر خيارات البحث والتصدير أيضا لتقنيات.

## <a name="investigate-using-the-side-pane"></a>التحقق من استخدام الجزء الجانبي

حدد تقنية لفتح الجزء الجانبي المناظر لها. يمكنك هنا الاطلاع على معلومات ورؤى إضافية مثل&ATT ذات الصلة وتقنيات CK والأساليب والأوصاف.

حدد أسلوب *الهجوم المحدد* لفتح صفحة تقنية ATT&CK ذات الصلة حيث يمكنك العثور على مزيد من المعلومات حولها.

يمكنك نسخ تفاصيل كيان عندما ترى أيقونة زرقاء على الجانب الأيمن. على سبيل المثال، لنسخ SHA1 ملف ذي صلة، حدد أيقونة الصفحة الزرقاء.

:::image type="content" source="images/techniques-side-pane-clickable.png" alt-text="تفاصيل الكيان لنسخ" lightbox="images/techniques-side-pane-clickable.png":::

يمكنك القيام بالشيء نفسه لخطوط الأوامر.

:::image type="content" source="images/techniques-side-pane-command.png" alt-text="خيار نسخ سطر الأوامر" lightbox="images/techniques-side-pane-command.png":::

## <a name="investigate-related-events"></a>التحقق من الأحداث ذات الصلة

لاستخدام البحث [المتقدم](advanced-hunting-overview.md) للبحث عن الأحداث المرتبطة بالتقنية المحددة، حدد **البحث عن الأحداث ذات الصلة**. يؤدي ذلك إلى صفحة الصيد المتقدمة مع استعلام للعثور على الأحداث ذات الصلة بالتقنية.

:::image type="content" source="images/techniques-hunt-for-related-events.png" alt-text="الخيار &quot;البحث عن الأحداث ذات الصلة&quot;" lightbox="images/techniques-hunt-for-related-events.png":::

> [!NOTE]
> يؤدي الاستعلام باستخدام الزر **البحث** عن الأحداث ذات الصلة من الجزء الجانبي تقنية إلى عرض كل الأحداث ذات الصلة بالتقنية المحددة ولكنه لا يتضمن التقنية نفسها في نتائج الاستعلام.

## <a name="customize-your-device-timeline"></a>تخصيص المخطط الزمني للجهاز

على الجانب العلوي الأيسر من المخطط الزمني للجهاز، يمكنك اختيار نطاق تاريخ للحد من عدد الأحداث والتقنيات في المخطط الزمني.

يمكنك تخصيص الأعمدة التي تريد عرضها. يمكنك أيضا التصفية للأحداث التي تم وضع علامة عليها حسب نوع البيانات أو حسب مجموعة الأحداث.

### <a name="choose-columns-to-expose"></a>اختيار أعمدة لكشفها

يمكنك اختيار الأعمدة التي تريد عرضها في المخطط الزمني عن طريق تحديد **الزر اختيار** أعمدة.

:::image type="content" source="images/filter-customize-columns.png" alt-text="الجزء الذي يمكنك تخصيص الأعمدة فيه" lightbox="images/filter-customize-columns.png":::


من هناك، يمكنك تحديد المعلومات التي تم تعيينها لتضمينها.

### <a name="filter-to-view-techniques-or-events-only"></a>التصفية لعرض التقنيات أو الأحداث فقط

لعرض الأحداث أو التقنيات فقط، حدد **عوامل التصفية** من المخطط الزمني للجهاز واختر نوع البيانات المفضل لديك لعرضه.

:::image type="content" source="images/device-timeline-filters.png" alt-text="جزء عوامل التصفية" lightbox="images/device-timeline-filters.png":::

## <a name="see-also"></a>راجع أيضًا

- [عرض قائمة الأجهزة وتنظيمها](machines-view-overview.md)
- [Microsoft Defender لنقطة النهاية أحداث المخطط الزمني للجهاز](device-timeline-event-flag.md)
