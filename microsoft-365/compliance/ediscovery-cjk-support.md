---
title: دعم CJK/Double Byte ل eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: تعرف على كيفية دعم Microsoft Purview eDiscovery (Premium) في Microsoft 365 للغات الصينية واليابانية والكورية (CJK)، التي تستخدم مجموعة أحرف مزدوجة البايت.
ms.openlocfilehash: e6399136713ff7be4b3c065de05b587a3f942b01
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095895"
---
# <a name="cjk-language-support-for-ediscovery-premium"></a>دعم لغة CJK ل eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يدعم Microsoft Purview eDiscovery (Premium) لغات مجموعة الأحرف مزدوجة البايت (بما في ذلك الصينية المبسطة والصينية التقليدية واليابانية والكورية، والتي تعرف مجتمعة بلغات *CJK*) للسيناريوهات المتقدمة التالية في مجموعة مراجعة:

- عند [الاستعلام عن البيانات في مجموعة مراجعة](review-set-search.md).

- عند [وضع علامة على المستندات في مجموعة مراجعة](tagging-documents.md).

- عند [تحليل بيانات الحالة في مجموعة مراجعة](analyzing-data-in-review-set.md) باستخدام الكشف شبه المكرر ومؤشرات ترابط البريد الإلكتروني وتحليلات النسق.

## <a name="frequently-asked-questions"></a>الأسئلة الشائعة

**كيف أعمل إنشاء بحث لتجميع العناصر التي تحتوي على أحرف CJK؟**

يمكنك استخدام أحرف CJK [لعمليات البحث عن الكلمات الأساسية](building-search-queries.md#keyword-searches) [واستعلامات الكلمات الأساسية وشروط البحث](keyword-queries-and-search-conditions.md) عند البحث عن المحتوى في eDiscovery (Premium). يتم أيضا دعم البحث عن أحرف CJK عند البحث عن محتوى في Microsoft Purview eDiscovery (قياسي) والبحث عن المحتوى.

نحن نقدم دعم CJK لكافة [عوامل البحث](keyword-queries-and-search-conditions.md#search-operators) [وشروط البحث](keyword-queries-and-search-conditions.md#search-conditions)، بما في ذلك عوامل التشغيل المنطقية **AND** **وOR** و **NOT** و **Near**.

إذا كنت متأكدا من أن مواقع المحتويات أو العناصر تحتوي على أحرف CJK، ولكن عمليات البحث لا ترجع أي نتائج، فانقر فوق أيقونة لغة/منطقة الاستعلام ![استعلام عن أيقونة اللغة-البلد/المنطقة في البحث في المحتوى.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) وحدد قيمة التعليمات البرمجية لثقافة بلد اللغة المطابقة للبحث. اللغة/المنطقة الافتراضية محايدة.

**هل يمكنني البحث عن لغات متعددة في وقت واحد؟**

يعتمد ذلك على سيناريو البحث.

- عند [الاستعلام عن البيانات في مجموعة مراجعة](review-set-search.md) في eDiscovery (Premium)، يمكنك البحث عن لغات متعددة.

- عند [إنشاء عملية بحث لجمع البيانات](create-draft-collection.md)، قم بإنشاء مجموعات منفصلة لكل لغة تستهدفها. على سبيل المثال، إذا كنت تبحث عن مستند يحتوي على كل من الصينية والكورية، فحدد الصينية لمجموعتك الأولى وحدد الكورية لمجموعتك الثانية.

**لا أرى أيقونة لغة/منطقة الاستعلام لتحديد لغة للاستعلامات في مجموعة مراجعة. كيف يمكنني تحديد لغة استعلام في بحث مجموعة المراجعة؟**

بالنسبة إلى استعلامات مجموعة المراجعة، لا تحتاج إلى تحديد لغة مستند. يكشف eDiscovery (Premium) تلقائيا عن لغات المستندات عند إضافة محتوى إلى مجموعة مراجعة. يساعدك هذا على تحسين نتائج الاستعلام في مجموعة مراجعة.

**هل يمكنني رؤية اللغات المكتشفة في [بيانات تعريف الملفات](view-documents-in-review-set.md#file-metadata)؟**

لا، لا يمكنك رؤية اللغات المكتشفة في بيانات تعريف الملفات.

**هل يمكنني التصفية حسب لغات المستند في مجموعة مراجعة**؟

لا، لا يمكنك التصفية أو الفرز أو البحث حسب لغات المستند في مجموعة مراجعة.

**هل سيؤثر إصدار CJK هذا لسيناريوهات مجموعة المراجعة على أي من عمليات البحث الحالية ومجموعات المراجعة؟**

لا، لن تتغير أي من عمليات البحث ومجموعات المراجعة الموجودة. لا تحتاج إلى إعادة فهرسة البيانات الموجودة، وستكون نتائج البحث عن نص باللغة الإنجليزية هي نفسها.

**كيف أعمل تغيير لغة العرض إلى الصينية أو اليابانية أو الكورية؟**

للحصول على معلومات حول كيفية تغيير لغة العرض والمنطقة الزمنية، راجع [كيفية تعيين إعدادات اللغة والمنطقة Office 365](/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>المشاكل المعروفة

- لا يدعم التعرف البصري على الحروف أحرف CJK من ملفات الصور

- ملفات البريد الإلكتروني (مثل *.eml و*.msg) في [طريقة عرض التعليقات التوضيحية](view-documents-in-review-set.md#annotate-view) غير معتمدة للغات CJK.

- تمييز البحث في [طريقة عرض النص](view-documents-in-review-set.md#text-view) غير معتمد للغات CJK.

- لا تدعم [وحدة الصلة](using-relevance.md) المستخدمة لتحليل البيانات لغات CJK.

- عمليات [الاحتجاز المستندة إلى الاستعلام](managing-holds.md#manage-non-custodial-holds) غير معتمدة للغات CJK.