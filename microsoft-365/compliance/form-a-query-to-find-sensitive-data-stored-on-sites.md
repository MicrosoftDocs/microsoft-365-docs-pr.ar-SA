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
ms.openlocfilehash: af1ca8f28f80d58c0f366e1a002181e23db3d552
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566108"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>تشكيل استعلام للعثور على البيانات الحساسة المخزنة على المواقع

غالبا ما يخزن المستخدمون البيانات الحساسة، مثل أرقام بطاقات الائتمان أو أرقام الضمان الاجتماعي أو الشخصية، على مواقعهم، ومع مرور الوقت، قد يعرض ذلك المؤسسة لخطر كبير بفقدان البيانات. يمكن مشاركة المستندات المخزنة على المواقع، بما في ذلك OneDrive for Business المواقع، مع أشخاص من خارج المؤسسة لا يجب أن يكون لديهم حق الوصول إلى المعلومات. باستخدام منع فقدان البيانات (DLP) في SharePoint Online، يمكنك اكتشاف المستندات التي تحتوي على بيانات حساسة في جميع أنحاء المستأجر. بعد اكتشاف المستندات، يمكنك العمل مع مالكي المستندات لحماية البيانات. يمكن أن يساعدك هذا الموضوع في تكوين استعلام للبحث عن البيانات الحساسة.

> [!NOTE]
> الاكتشاف الإلكتروني أو eDiscovery وDLP هي ميزات متميزة تتطلب SharePoint [عبر الإنترنت 2](https://go.microsoft.com/fwlink/?LinkId=510080).

## <a name="forming-a-basic-dlp-query"></a>تشكيل استعلام DLP أساسي

هناك ثلاثة أجزاء تكون استعلام DLP أساسي: SensitiveType، نطاق العدد، نطاق الثقة. كما هو موضح في الرسم التالي، **SensitiveType:"\<type\>"** مطلوب **|\<count range\>** ، وكل منهما اختياري **|\<confidence range\>** .

![مثال استعلام مقسم إلى مطلوب واختياري.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>النوع الحساس - مطلوب

فما هو كل جزء؟ SharePoint عادة ما تبدأ استعلامات DLP `SensitiveType:"` بالممتلكات واسم نوع المعلومات من مخزون أنواع المعلومات الحساسة[](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help)، وتنتهي ب `"`. يمكنك أيضا استخدام اسم نوع معلومات مخصص حساس [](create-a-custom-sensitive-information-type.md) أنشأته لمنظمتك. على سبيل المثال، قد تبحث عن مستندات تحتوي على أرقام بطاقات ائتمان. في مثل هذا المثيل، يمكنك استخدام التنسيق التالي:  `SensitiveType:"Credit Card Number"`. نظرا لعدم تضمين نطاق العدد أو نطاق الثقة، يرجع الاستعلام كل مستند يتم فيه الكشف عن رقم بطاقة ائتمان. هذا هو أبسط استعلام يمكنك تشغيله، وهو يرجع معظم النتائج. ضع في اعتبارك أن التدقيق الإملائي والتباعد للنوع الحساس مهم.

### <a name="ranges---optional"></a>النطاقات - اختيارية

كلا الجزأين التاليين نطاقات، لذا دعنا نفحص شكل النطاق بسرعة. في SharePoint DLP، يتم تمثيل النطاق الأساسي بعددين مفصولين بفترتين، مما يبدو كما يلي: `[number]..[number]`. على سبيل المثال، إذا  `10..20` تم استخدامه، فإن هذا النطاق سيلتقط أرقاما من 10 إلى 20. هناك العديد من مجموعات النطاقات المختلفة والعديد من المجموعات التي تم تناولها في هذا الموضوع.

دعنا نضيف نطاق عدد إلى الاستعلام. يمكنك استخدام نطاق العدد لتعريف عدد تكرارات المعلومات الحساسة التي يحتاج المستند إلى احتوائها قبل تضمينه في نتائج الاستعلام. على سبيل المثال، إذا كنت تريد أن يرجع الاستعلام المستندات التي تحتوي على خمسة أرقام بطاقات ائتمان فقط، فاستخدم ما يلي:  `SensitiveType:"Credit Card Number|5"`. يمكن أن يساعدك نطاق العدد أيضا على تحديد المستندات التي تشكل درجات عالية من المخاطر. على سبيل المثال، قد تعتبر مؤسستك المستندات ذات خمسة أرقام أو أكثر من أرقام بطاقات الائتمان من المخاطر العالية. للعثور على المستندات التي تلائم هذا المعيار، يمكنك استخدام هذا الاستعلام:  `SensitiveType:"Credit Card Number|5.."`. بدلا من ذلك، يمكنك العثور على مستندات ذات خمسة أرقام بطاقات ائتمان أو أقل باستخدام هذا الاستعلام:  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>نطاق الثقة

وأخيرا، نطاق الثقة هو مستوى الثقة بأن النوع الحساس الذي تم اكتشافه متطابق في الواقع. تعمل قيم نطاق الثقة بطريقة مماثلة لنطاق العدد. يمكنك إنشاء استعلام دون أن يتضمن نطاق عدد. على سبيل المثال، للبحث عن مستندات تتضمن أي عدد من أرقام بطاقات الائتمان، طالما أن نطاق الثقة هو 85 بالمائة أو أكثر، يمكنك استخدام هذا الاستعلام:  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> إن النجمة ( `*` ) هي حرف بدل يعني أن أي قيمة تعمل. يمكنك استخدام حرف البدل ( `*` ) إما في نطاق العدد أو في نطاق الثقة، ولكن ليس في نوع حساس.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>خصائص الاستعلام الإضافية و عوامل البحث المتوفرة في مركز eDiscovery

تقدم أيضا DLP في SharePoint الخاصية LastSensitiveContentScan، التي يمكن أن تساعدك في البحث عن الملفات الممسوحة ضوئيا ضمن إطار زمني معين. للحصول على أمثلة الاستعلام مع الخاصية  `LastSensitiveContentScan` ، راجع أمثلة [الاستعلامات](#examples-of-complex-queries) المعقدة في المقطع التالي.

لا يمكنك استخدام الخصائص الخاصة ب DLP فقط لإنشاء استعلام، ولكن أيضا خصائص البحث القياسية SharePoint eDiscovery مثل `Author` أو `FileExtension`. يمكنك استخدام عوامل التشغيل لإنشاء استعلامات معقدة. للحصول على قائمة الخصائص و عوامل التشغيل المتوفرة، راجع استخدام خصائص البحث و عوامل [التشغيل مع منشور مدونة eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) .

## <a name="examples-of-complex-queries"></a>أمثلة للاستعلامات المعقدة

تستخدم الأمثلة التالية الأنواع والخصائص و عوامل التشغيل الحساسة المختلفة لتوضيح كيفية تحسين الاستعلامات للعثور على ما تبحث عنه بالضبط.

<br>

****

|استعلام|شرح|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|قد يبدو الاسم غريبا لأنه طويل جدا، ولكنه الاسم الصحيح لهذا النوع الحساس. تأكد من استخدام الأسماء الدقيقة من مخزون [أنواع المعلومات الحساسة](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help). يمكنك أيضا استخدام اسم نوع معلومات مخصص حساس [](create-a-custom-sensitive-information-type.md) أنشأته لمنظمتك.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|يرجع ذلك المستندات ذات مطابقة واحدة على الأقل للنوع الحساس "رقم بطاقة الائتمان". القيم الخاصة بكل نطاق هي الحد الأدنى والحد الأقصى للقيم الخاصة بها. هناك طريقة أكثر بساطة لكتابة هذا الاستعلام وهي  `SensitiveType:"Credit Card Number"`، ولكن أين المتعة في ذلك؟|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|يرجع ذلك المستندات التي بها أرقام بطاقات ائتمان من 5 إلى 25 تم فحصها من 11 أغسطس 2018 إلى 13 أغسطس 2018.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|يرجع ذلك المستندات التي بها أرقام بطاقات ائتمان من 5 إلى 25 تم فحصها من 11 أغسطس 2018 إلى 13 أغسطس 2018. لا يتم تضمين الملفات ذات الملحق XLSX في نتائج الاستعلام.  `FileExtension` هي إحدى الخصائص العديدة التي يمكنك تضمينها في استعلام. لمزيد من المعلومات، راجع [استخدام خصائص البحث و عوامل التشغيل مع eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|يرجع ذلك المستندات التي تحتوي على رقم بطاقة ائتمان أو رقم الضمان الاجتماعي.|
|

## <a name="examples-of-queries-to-avoid"></a>أمثلة للاستعلامات التي يجب تجنبها

لا يتم إنشاء كل الاستعلامات بالتساوي. يوفر الجدول التالي أمثلة للاستعلامات التي لا تعمل مع DLP في SharePoint ويصف السبب.

<br>

****

|استعلام غير معتمد|السبب|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|يجب إضافة رقم واحد على الأقل.|
|`SensitiveType:"NotARule"`|"NotARule" ليس اسم نوع حساس صالح. تعمل الأسماء فقط في [أنواع المعلومات الحساسة في](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) استعلامات DLP.|
|`SensitiveType:"Credit Card Number|0"`|لا يعد الصفر صالحا كقيمة الحد الأدنى أو الحد الأقصى للقيمة في نطاق.|
|`SensitiveType:"Credit Card Number"`|قد يكون من الصعب رؤية ذلك، ولكن هناك مسافة بيضاء إضافية بين "الائتمان" و"البطاقة" تجعل الاستعلام غير صالح. استخدم أسماء الأنواع الحساسة الدقيقة من [مخزون أنواع المعلومات الحساسة](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help).|
|`SensitiveType:"Credit Card Number|1. .3"`|يجب عدم الفصل بين جزء الفترتين بمساحة.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|هناك عدد كبير جدا من مواسير الانابيب (\|). اتبع هذا التنسيق بدلا من ذلك: `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|وبما أن قيم الثقة تمثل نسبة مئوية، لا يمكن أن تتجاوز 100. اختر رقما من 1 إلى 100 بدلا من ذلك.|
|

## <a name="for-more-information"></a>لمزيد من المعلومات

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [تشغيل البحث في المحتوى](content-search.md)
- [استعلامات الكلمات الأساسية وشروط البحث في البحث في المحتوى](keyword-queries-and-search-conditions.md)
