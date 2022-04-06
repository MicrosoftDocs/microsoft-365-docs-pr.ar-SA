---
title: معالجة الأخطاء في البحث المتقدم Microsoft 365 Defender
description: فهم الأخطاء المعروضة عند استخدام الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و المخطط، و kusto، و المهلة، و الموارد، و الأخطاء، و الأخطاء غير المعروفة، و الحدود، والحصة النسبية، والمعلمة، والتخصيص
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 8bd7d4b5191ff88fe2bd958c87e930b91f64dd5e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/03/2021
ms.locfileid: "63583157"
---
# <a name="handle-advanced-hunting-errors"></a>معالجة أخطاء الصيد المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية


يعرض الصيد المتقدم أخطاء لإعلامك عن أخطاء بناء الجملة وكلما تم تحديد الحصص النسبية ومعايير [الاستخدام المحددة مسبقا للاستعلامات](advanced-hunting-limits.md). راجع الجدول أدناه للحصول على تلميحات حول كيفية حل الأخطاء أو تجنبها.

| نوع الخطأ | السبب | الدقة | أمثلة على رسائل الخطأ |
|--|--|--|--|
| أخطاء بناء الجملة | يحتوي الاستعلام على أسماء غير مفصول بها، بما في ذلك مراجع إلى عوامل تشغيل أو أعمدة أو دالات أو جداول غير موجودة. | تأكد من صحة [المراجع إلى دالات و عوامل تشغيل Kusto](/azure/data-explorer/kusto/query/) . تحقق [من المخطط للحصول](advanced-hunting-schema-tables.md) على الأعمدة والوظائف والجداول المتقدمة الصحيحة. إحاطة السلاسل المتغيرة بين علامات اقتباس بحيث يتم التعرف عليها. أثناء كتابة الاستعلامات، استخدم اقتراحات الإبهار التلقائي من IntelliSense. | `A recognition error occurred.` |
| الأخطاء الدلالية | في حين يستخدم الاستعلام أسماء عامل تشغيل أو عمود أو دالة أو جدول صالحة، توجد أخطاء في بنيته والمنطق الناتج. في بعض الحالات، يحدد الصيد المتقدم عامل التشغيل المحدد الذي تسبب في الخطأ. | تحقق من وجود أخطاء في بنية الاستعلام. راجع [وثائق Kusto](/azure/data-explorer/kusto/query/) للحصول على الإرشادات. أثناء كتابة الاستعلامات، استخدم اقتراحات الإبهار التلقائي من IntelliSense. |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| 2010 | يمكن تشغيل الاستعلام خلال [فترة زمنية محددة فقط قبل توقيت الخروج](advanced-hunting-limits.md). قد يحدث هذا الخطأ بشكل متكرر أكثر عند تشغيل الاستعلامات المعقدة. | [تحسين الاستعلام](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| تدويل وحدة المعالجة المركزية (CPU) | تجاوزت الاستعلامات في نفس المستأجر موارد [CPU](advanced-hunting-limits.md) التي تم تخصيصها استنادا إلى حجم المستأجر. | تحقق الخدمة من استخدام موارد CPU كل 15 دقيقة يوميا وتعرض التحذيرات بعد أن يتجاوز الاستخدام 10٪ من الحصة النسبية المخصصة. إذا وصلت إلى الاستخدام بنسبة 100٪، فإن الخدمة تمنع الاستعلامات حتى بعد الدورة اليومية التالية أو 15 دقيقة. [تحسين الاستعلامات لتجنب الضغط على الحصص النسبية لوحدة المعالجة المركزية (CPU)](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| تم تجاوز حد حجم النتيجة  | تجاوز الحجم التجميعي مجموعة النتائج للاستعلام الحد الأقصى للحجم. يمكن أن يحدث هذا الخطأ إذا كانت مجموعة النتائج كبيرة جدا بحيث لا يمكن أن يؤدي الاقجام عند حد 10000 سجل إلى تقليله إلى حجم مقبول. من المحتمل أن تكون النتائج التي لها أعمدة متعددة ذات محتوى كبير متأثّر بهذا الخطأ. | [تحسين الاستعلام](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| الاستهلاك المفرط للموارد | استهلك الاستعلام كميات زائدة من الموارد وتوقف عن الإكمال. في بعض الحالات، يحدد الصيد المتقدم عامل التشغيل المحدد الذي لم يتم تحسينه. | [تحسين الاستعلام](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| أخطاء غير معروفة | فشل الاستعلام بسبب سبب غير معروف. | حاول تشغيل الاستعلام مرة أخرى. اتصل ب Microsoft عبر المدخل إذا استمرت الاستعلامات في إرجاع أخطاء غير معروفة. | `An unexpected error occurred during query execution. Please try again in a few minutes.`



## <a name="related-topics"></a>المواضيع ذات الصلة
- [أفضل الممارسات المتقدمة للصيد](advanced-hunting-best-practices.md)
- [معلمات الاستخدام والحصص النسبية](advanced-hunting-limits.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [نظرة عامة على لغة الاستعلام في Kusto](/azure/data-explorer/kusto/query/)