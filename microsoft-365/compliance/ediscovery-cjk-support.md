---
title: دعم CJK/Double Byte Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: تعرف على Advanced eDiscovery في Microsoft 365 اللغات الصينية واليابانية والكورية (CJK)، التي تستخدم مجموعة أحرف مزدوجة.
ms.openlocfilehash: 4c1871eb49754ba93d762989e3cff9c53950d2c6
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/09/2022
ms.locfileid: "63575418"
---
# <a name="cjk-language-support-for-advanced-ediscovery"></a>دعم لغة CJK Advanced eDiscovery

Advanced eDiscovery اللغات التي تستخدم مجموعة أحرف مزدوجة (تتضمن هذه اللغات الصينية المبسطة والصينية التقليدية واليابانية والكورية، والمعروفة بشكل جماعي بلغات *CJK*) للسيناريوهات المتقدمة التالية في مجموعة مراجعة:

- عند الاستعلام [عن البيانات في مجموعة مراجعة](review-set-search.md).

- عند وضع [علامة على المستندات في مجموعة مراجعة](tagging-documents.md).

- عند تحليل [بيانات الحالة في مجموعة مراجعة](analyzing-data-in-review-set.md) باستخدام الكشف المكرر تقريبا، وترابط البريد الإلكتروني، وتحليلات المحتوى.

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

**كيف يمكنني إنشاء بحث لتجميع العناصر التي تحتوي على أحرف CJK؟**

يمكنك استخدام أحرف CJK [للبحث عن](building-search-queries.md#keyword-searches) الكلمات الأساسية واستعلامات الكلمات الأساسية وشروط البحث عند البحث عن المحتوى في Advanced eDiscovery. [](keyword-queries-and-search-conditions.md) يتم أيضا دعم البحث عن أحرف CJK عند البحث عن محتوى في Core eDiscovery والبحث في المحتوى.

نحن نوفر دعم CJK لجميع عوامل [](keyword-queries-and-search-conditions.md#search-operators) تشغيل البحث وشروط [](keyword-queries-and-search-conditions.md#search-conditions)البحث، بما في ذلك عوامل التشغيل **منطقية AND** و **OR و** **NOT** و **NEAR**.

إذا كنت على يقين من أن مواقع المحتوى أو عناصره تحتوي على أحرف CJK، ولكن عمليات البحث لا تقوم بإرجاع أي نتائج، انقر فوق أيقونة لغة الاستعلام/البلد/المنطقة ![أيقونة اللغة/المنطقة للاستعلام في البحث في المحتوى.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) وحدد القيمة المقابلة لرمز ثقافة بلد اللغة للبحث. اللغة/المنطقة الافتراضية محايدة.

**هل يمكنني البحث عن لغات متعددة في وقت واحد؟**

يعتمد ذلك على سيناريو البحث.

- عند [استعلام البيانات في مجموعة مراجعة](review-set-search.md) في Advanced eDiscovery، يمكنك البحث عن لغات متعددة.

- عند إنشاء [بحث لتجميع البيانات](create-draft-collection.md)، قم بإنشاء مجموعات منفصلة لكل لغة تستهدفها. على سبيل المثال، إذا كنت تبحث عن مستند يحتوي على كل من الصينية والكورية، فحدد الصينية لمجموعتك الأولى وحدد الكورية لمجموعتك الثانية.

**لا يمكنني رؤية أيقونة اللغة/المنطقة للاستعلام لتحديد لغة للاستعلامات في مجموعة مراجعة. كيف يمكنني تحديد لغة استعلام في بحث مجموعة مراجعة؟**

لمراجعة استعلامات مجموعة المستندات، لست بحاجة إلى تحديد لغة مستند. Advanced eDiscovery تلقائيا عن لغات المستندات عند إضافة محتوى إلى مجموعة مراجعة. يساعدك ذلك على تحسين نتائج الاستعلام في مجموعة مراجعة.

**هل يمكنني رؤية اللغات التي تم الكشف عنها في [بيانات تعريف الملف](view-documents-in-review-set.md#file-metadata)؟**

لا، لا يمكنك رؤية اللغات التي تم الكشف عنها في بيانات تعريف الملف.

**هل يمكنني التصفية حسب لغات المستندات في مجموعة مراجعة**؟

لا، لا يمكنك التصفية أو الفرز أو البحث حسب لغات المستند في مجموعة مراجعة.

**هل سيؤثر إصدار CJK هذا لسيناريوهات مجموعة المراجعة على أي من مجموعات عمليات البحث والمراجعة الموجودة؟**

لا، لن تتغير أي من مجموعات عمليات البحث والمراجعة الموجودة. لست بحاجة إلى إعادة عرض البيانات الموجودة، وسوف تكون نتائج البحث عن نص باللغة الإنجليزية هي نفسها.

**كيف يمكنني تغيير لغة العرض إلى الصينية أو اليابانية أو الكورية؟**

للحصول على معلومات حول كيفية تغيير لغة العرض والمنطقة الزمنية، راجع كيفية تعيين إعدادات اللغة والمنطقة [Office 365.](/office365/troubleshoot/access-management/set-language-and-region)

## <a name="known-issues"></a>المشاكل المعروفة

- لا يدعم OCR أحرف CJK من ملفات الصور

- ملفات البريد الإلكتروني (مثل *.eml و*.msg) في [](view-documents-in-review-set.md#annotate-view) طريقة عرض التعليق التوضيحي غير معتمدة للغات CJK.

- تمييز نتائج البحث في [طريقة عرض](view-documents-in-review-set.md#text-view) النص غير معتمد للغات CJK.

- لا [تدعم الوحدة النمطية الصلة](using-relevance.md) المستخدمة لتحليل البيانات لغات CJK.

- [إن عمليات التحمس](managing-holds.md#manage-non-custodial-holds) المستندة إلى الاستعلام غير معتمدة للغات CJK.