---
title: تشكيل استعلام للعثور على البيانات الحساسة المخزنة على المواقع
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: استخدم منع فقدان البيانات (DLP) في SharePoint Online لاكتشاف المستندات التي تحتوي على بيانات حساسة عبر المستأجر.
ms.openlocfilehash: 1bb3ed0286f719f9ea9210b4952044081213914f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638312"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>تشكيل استعلام للعثور على البيانات الحساسة المخزنة على المواقع

غالبا ما يقوم المستخدمون بتخزين البيانات الحساسة، مثل أرقام بطاقات الائتمان أو أرقام الضمان الاجتماعي أو الشخصية، على مواقعهم، ومع مرور الوقت يمكن أن يعرض هذا المؤسسة لخطر كبير من فقدان البيانات. يمكن مشاركة المستندات المخزنة على المواقع، بما في ذلك مواقع OneDrive for Business، مع أشخاص من خارج المؤسسة لا ينبغي أن يتوفر لديهم حق الوصول إلى المعلومات. باستخدام تفادي فقدان البيانات في Microsoft Purview (DLP) في SharePoint Online، يمكنك اكتشاف المستندات التي تحتوي على بيانات حساسة في جميع أنحاء المستأجر. بعد اكتشاف المستندات، يمكنك العمل مع مالكي المستندات لحماية البيانات. يمكن أن يساعدك هذا الموضوع في تشكيل استعلام للبحث عن البيانات الحساسة.

> [!NOTE]
> الاكتشاف الإلكتروني أو eDiscovery وDLP هما من الميزات المتميزة التي تتطلب [خطة SharePoint Online 2](https://go.microsoft.com/fwlink/?LinkId=510080).

## <a name="forming-a-basic-dlp-query"></a>تشكيل استعلام DLP أساسي

هناك ثلاثة أجزاء تشكل استعلام DLP أساسيا: SensitiveType ونطاق العدد ونطاق الثقة. كما هو موضح في الرسم التالي، **SensitiveType:"\<type\>"** مطلوب، وكلاهما **|\<count range\>** **|\<confidence range\>** اختياري.

![استعلام مثال مقسم إلى مطلوب واختياري.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>نوع حساس - مطلوب

فما هو كل جزء؟ تبدأ استعلامات DLP في SharePoint عادة بالخاصية  `SensitiveType:"` واسم نوع المعلومات من [مخزون أنواع المعلومات الحساسة](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help)، وتنتهي ب  `"`. يمكنك أيضا استخدام اسم [نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type.md) قمت بإنشائه لمؤسستك. على سبيل المثال، قد تبحث عن المستندات التي تحتوي على أرقام بطاقات الائتمان. في مثل هذا المثيل، يمكنك استخدام التنسيق التالي:  `SensitiveType:"Credit Card Number"`. نظرا لأنك لم تقم بتضمين نطاق العد أو نطاق الثقة، يقوم الاستعلام بإرجاع كل مستند يتم فيه الكشف عن رقم بطاقة ائتمان. هذا هو أبسط استعلام يمكنك تشغيله، ويرجع معظم النتائج. ضع في اعتبارك أن التدقيق الإملائي والتباعد للنوع الحساس مهم.

### <a name="ranges---optional"></a>النطاقات - اختيارية

كلا الجزأين التاليين هما النطاقات، لذلك دعونا نفحص بسرعة كيف يبدو النطاق. في استعلامات DLP في SharePoint، يتم تمثيل نطاق أساسي برقمين مفصولين بفترتين، والتي تبدو كما يلي:  `[number]..[number]`. على سبيل المثال، إذا  `10..20` تم استخدامه، فسيسجل هذا النطاق الأرقام من 10 إلى 20. هناك العديد من مجموعات النطاقات المختلفة ويتم تناول العديد منها في هذا الموضوع.

دعونا نضيف نطاق عدد إلى الاستعلام. يمكنك استخدام نطاق العد لتعريف عدد تكرارات المعلومات الحساسة التي يجب أن يحتوي عليها المستند قبل تضمينه في نتائج الاستعلام. على سبيل المثال، إذا كنت تريد أن يقوم الاستعلام بإرجاع المستندات التي تحتوي على خمسة أرقام بطاقات ائتمان بالضبط، فاستخدم ما يلي:  `SensitiveType:"Credit Card Number|5"`. يمكن أن يساعدك نطاق العد أيضا في تحديد المستندات التي تشكل درجات عالية من المخاطر. على سبيل المثال، قد تعتبر مؤسستك المستندات التي تحتوي على خمسة أرقام أو أكثر من أرقام بطاقات الائتمان خطرا كبيرا. للعثور على مستندات مناسبة لهذا المعيار، يمكنك استخدام هذا الاستعلام:  `SensitiveType:"Credit Card Number|5.."`. بدلا من ذلك، يمكنك العثور على مستندات تتضمن خمسة أرقام أو أقل من أرقام بطاقات الائتمان باستخدام هذا الاستعلام:  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>نطاق الثقة

وأخيرا، نطاق الثقة هو مستوى الثقة بأن النوع الحساس المكتشف هو في الواقع تطابق. تعمل قيم نطاق الثقة بشكل مماثل لنطاق العد. يمكنك تشكيل استعلام دون تضمين نطاق عدد. على سبيل المثال، للبحث عن المستندات التي تحتوي على أي عدد من أرقام بطاقات الائتمان - طالما أن نطاق الثقة هو 85 بالمئة أو أعلى - يمكنك استخدام هذا الاستعلام:  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> العلامة النجمية ( `*` ) هي حرف بدل يعني أن أي قيمة تعمل. يمكنك استخدام حرف البدل ( `*` ) إما في نطاق العد أو في نطاق الثقة، ولكن ليس في نوع حساس.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>خصائص الاستعلام الإضافية وعوامل تشغيل البحث المتوفرة في مركز eDiscovery

يقدم DLP في SharePoint أيضا خاصية LastSensitiveContentScan، والتي يمكن أن تساعدك في البحث عن الملفات التي تم مسحها ضوئيا ضمن إطار زمني معين. للحصول على أمثلة الاستعلام مع الخاصية  `LastSensitiveContentScan` ، راجع [أمثلة الاستعلامات المعقدة](#examples-of-complex-queries) في القسم التالي.

لا يمكنك استخدام الخصائص الخاصة ب DLP فقط لإنشاء استعلام، ولكن أيضا خصائص بحث SharePoint eDiscovery القياسية مثل  `Author` أو  `FileExtension`. يمكنك استخدام عوامل التشغيل لإنشاء استعلامات معقدة. للحصول على قائمة بالخصائص وعوامل التشغيل المتوفرة، راجع ["استخدام خصائص البحث وعوامل التشغيل" مع نشر مدونة eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) .

## <a name="examples-of-complex-queries"></a>أمثلة على الاستعلامات المعقدة

تستخدم الأمثلة التالية أنواعا وخصائص وعوامل تشغيل حساسة مختلفة لتوضيح كيفية تحسين الاستعلامات للعثور على ما تبحث عنه بالضبط.

<br>

****

|الاستعلام|تفسير|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|قد يبدو الاسم غريب لأنه طويل جدا، ولكنه الاسم الصحيح لهذا النوع الحساس. تأكد من استخدام الأسماء الدقيقة من [مخزون أنواع المعلومات الحساسة](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help). يمكنك أيضا استخدام اسم [نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type.md) قمت بإنشائه لمؤسستك.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|يؤدي ذلك إلى إرجاع مستندات ذات تطابق واحد على الأقل للنوع الحساس "رقم بطاقة الائتمان". قيم كل نطاق هي الحد الأدنى والحد الأقصى للقيم. طريقة أبسط لكتابة هذا الاستعلام هي  `SensitiveType:"Credit Card Number"`، ولكن أين يوجد المرح في ذلك؟|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|يؤدي ذلك إلى إرجاع المستندات ذات أرقام بطاقات الائتمان من 5 إلى 25 التي تم مسحها ضوئيا من 11 أغسطس 2018 إلى 13 أغسطس 2018.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|يؤدي ذلك إلى إرجاع المستندات ذات أرقام بطاقات الائتمان من 5 إلى 25 التي تم مسحها ضوئيا من 11 أغسطس 2018 إلى 13 أغسطس 2018. لا يتم تضمين الملفات ذات ملحق XLSX في نتائج الاستعلام.  `FileExtension` هي واحدة من العديد من الخصائص التي يمكنك تضمينها في استعلام. لمزيد من المعلومات، راجع [استخدام خصائص البحث وعوامل التشغيل مع eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|يؤدي ذلك إلى إرجاع المستندات التي تحتوي على رقم بطاقة ائتمان أو رقم ضمان اجتماعي.|
|

## <a name="examples-of-queries-to-avoid"></a>أمثلة على الاستعلامات التي يجب تجنبها

لا يتم إنشاء كافة الاستعلامات متساوية. يقدم الجدول التالي أمثلة على الاستعلامات التي لا تعمل مع DLP في SharePoint ويصف السبب.

<br>

****

|استعلام غير معتمد|السبب|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|يجب إضافة رقم واحد على الأقل.|
|`SensitiveType:"NotARule"`|"NotARule" ليس اسم نوع حساس صحيح. تعمل الأسماء الموجودة في [أنواع المعلومات الحساسة](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) فقط في استعلامات DLP.|
|`SensitiveType:"Credit Card Number|0"`|الصفر غير صالح إما كقيمة الحد الأدنى أو الحد الأقصى للقيمة في نطاق.|
|`SensitiveType:"Credit Card Number"`|قد يكون من الصعب رؤيتها، ولكن هناك مسافة بيضاء إضافية بين "الرصيد" و"البطاقة" التي تجعل الاستعلام غير صالح. استخدم أسماء الأنواع الحساسة بالضبط من [مخزون أنواع المعلومات الحساسة](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help).|
|`SensitiveType:"Credit Card Number|1. .3"`|لا ينبغي فصل الجزء المكون من فترتين بمسافة.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|هناك عدد كبير جدا من محددات الأنابيب (\|). اتبع هذا التنسيق بدلا من ذلك: `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|نظرا لأن قيم الثقة تمثل نسبة مئوية، فلا يمكن أن تتجاوز 100. اختر رقما من 1 إلى 100 بدلا من ذلك.|
|

## <a name="for-more-information"></a>لمزيد من المعلومات

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [تشغيل البحث في المحتوى](content-search.md)
- [استعلامات الكلمات الأساسية وشروط البحث في البحث عن المحتوى](keyword-queries-and-search-conditions.md)
