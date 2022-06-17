---
title: مرجع تنسيق SKOS للتصنيف SharePoint
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
ms.localizationpriority: high
description: مرجع تنسيق SKOS للتصنيف SharePoint
ms.openlocfilehash: c9dbaae4242155522eec2fff0f7fd4d721e697cc
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139662"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>مرجع تنسيق SKOS للتصنيف SharePoint

تتضمن هذه المقالة مفردات RDF المستخدمة لتمثيل [تصنيف SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy) ويستند إلى [SKOS](https://www.w3.org/TR/skos-primer/). لتسلسل بناء جملة RDF هذا، استخدم RDF [RUST](https://www.w3.org/TR/turtle/).

يعرض الجدول التالي مكافئات [SKOS](https://www.w3.org/TR/skos-primer/) لمفردات [التصنيف SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy). لا يدعم SharePoint قيم [SKOS](https://www.w3.org/TR/skos-primer/) التي ليس لها تصنيف SharePoint مكافئ.

|تصنيف SharePoint|مكافئ SKOS|
|:-----------------|:--------------|
|sharepoint-التصنيف:Term|skos:Concept|
|sharepoint-التصنيف:TermSet|skos:ConceptScheme|
|sharepoint-التصنيف:inTermSet|skos:inScheme|
|sharepoint-التصنيف:hasTopLevelTerm|skos:hasTopConcept|
|sharepoint-التصنيف:topLevelTermOf|skos:topConceptOf|
|sharepoint-التصنيف:defaultLabel|skos:prefLabel|
|sharepoint-التصنيف:termSetName|skos:prefLabel|
|sharepoint-التصنيف:propertyName|skos:prefLabel|
|sharepoint-التصنيف:otherLabel|skos:altLabel|
|sharepoint-التصنيف:description|skos:definition|
|sharepoint-التصنيف:parent|skos:broader|
|sharepoint-التصنيف:child|skos:narrower|

يعرض الجدول التالي كيانات مفردات التصنيف SharePoint المشتقة من [OWL](https://www.w3.org/TR/owl2-primer/).

|SharePoint مفردات التصنيف|مشتق من OWL|
|:-----------------------------|:----------------------|
|sharepoint-التصنيف:isAvailableForTagging|owl:datatypeproperty|
|sharepoint-التصنيف:SharedCustomPropertyForTerm|بومة:ObjectProperty|
|sharepoint-التصنيف:LocalCustomPropertyForTerm|بومة:ObjectProperty|
|sharepoint-التصنيف:CustomPropertyForTermSet|بومة:ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>SharePoint مفردات التصنيف

التصنيف هو نظام تصنيف رسمي. يجمع التصنيف الكلمات والتسميات والمصطلحات التي تصف شيئا ما، ثم يقوم بترتيب المجموعات في تسلسل هرمي.

**sharepoint-التصنيف:Term**

يمثل مصطلحا أو كلمة أساسية في التسلسل الهرمي لبيانات التعريف المدارة.

[المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) هو الوحدة الذرية SharePoint [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). ينتمي كل [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) إلى [مجموعة مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset) تنتمي إلى [مجموعة مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.group).

بناء الجملة لتعريف [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) هو كما يلي:

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

[يوجد مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) بشكل إلزامي داخل [مجموعة مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset). DefaultLabel هو اسم [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) كما يظهر في التمثيل المرئي. تتضمن الحقول المطلوبة لتعريف [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) ما ما:

- sharepoint-التصنيف:defaultLabel
- sharepoint-التصنيف:inTermSet

يمكن [أن يكون المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) :

- كن مرتبطا بشكل هرمي [بمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) آخر يتم توفيره لكل من [الشروط](/dotnet/api/microsoft.sharepoint.taxonomy.term) التي تنتمي إلى نفس [مجموعة المصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- لديك [عدة شروط](/dotnet/api/microsoft.sharepoint.taxonomy.term) تابعة، ولكن فقط [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) أصل واحد.
- لم يتم تعريف [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) أصل، إذا كان topLevelTermOf a [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- لديك defaultLabel واحدة، لكل لغة عمل [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .
- غير موجود إذا لم يكن يحتوي على [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) أصل، ولا هو topLevelTermOf a [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- لديك defaultLabel فريد فقط في نفس المستوى الهرمي.

**sharepoint-التصنيف:TermSet**

يمثل مجموعة هرمية أو مسطحة من كائنات المصطلح المعروفة باسم "مجموعة المصطلحات".

كما يوحي الاسم، مجموعة المصطلحات هي مجموعة من [الشروط](/dotnet/api/microsoft.sharepoint.taxonomy.term). يجب أن ينتمي [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) في [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) إلى [مجموعة مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset). لا يمكن أن يوجد [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) بشكل مستقل.

بناء الجملة لتعريف [مجموعة المصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset) هو:

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

يتم تجميع [مجموعات المصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset) بشكل منطقي معا في [TermGroups](/dotnet/api/microsoft.sharepoint.taxonomy.group). الحقل المطلوب لتعريف [مجموعة المصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset) هو:

- sharepoint-التصنيف:termSetName

في حالة أن termSetName المتوفر ليس فريدا داخل [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group)، SharePoint إلحاق رقم في نهاية الاسم للحفاظ على تفرد termSetName(s).

**sharepoint-التصنيف:hasTopLevelTerm**

تستخدم SharePoint هذه الخاصية [لتعيين المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) الأعلى في [مجموعة المصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset)، وهي نقطة الإدخال إلى التسلسل الهرمي [للمصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.term) في مجموعة [مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset). هذه علاقة عكسية ب sharepoint-التصنيف:topLevelTermOf.

بناء الجملة لتعريف هذا هو:

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> لا يمكنك تعريف [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) المستوى الأعلى [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) أصل.

**sharepoint-التصنيف:topLevelTermOf**

Sharepoint-التصنيف:topLevelTermOf هو عكس sharepoint-التصنيف:hasTopLevelTerm

بناء الجملة لتعريف هذا هو:

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-التصنيف:inTermSet**

استخدم هذا لتعيين [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) إلى مجموعة [مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset). يمكن أن يكون [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) موجودا فقط في مجموعة [مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset) واحدة. يتطلب SharePoint هذه [الخاصية عند تعريف مصطلح](#sharepoint-taxonomy-vocabulary).

## <a name="required-labels"></a>التسميات المطلوبة

قد ترغب مؤسستك في إجراء تخطيط دقيق قبل البدء في استخدام بيانات التعريف المدارة. يعتمد مقدار التخطيط الذي يجب عليك القيام به على مدى رسمية التصنيف الخاص بك. كما يعتمد ذلك على مقدار التحكم الذي تريد فرضه على بيانات التعريف. في كل مستوى من التدرج الهرمي، تحتاج إلى تكوين التسميات المطلوبة لمصطلح أو مجموعة مصطلحات.

يمكن أن يحتوي المصطلح على تسمية واحدة أو أكثر باللغة الافتراضية، وصفر أو أكثر من التسميات باللغة غير الافتراضية. إذا كان المصطلح يحتوي على تسميات بلغة، فيجب أن تكون إحدى التسميات هي التسمية الافتراضية.

**sharepoint-التصنيف:defaultLabel**

استخدم هذه التسمية المعجمية الافتراضية [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) يمثل معلمة مطلوبة [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term). يستخدم لتمثيل [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) بشكل مرئي.

بناء الجملة لتعريف defaultLabel هو:

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

يحتوي defaultLabel على جزأين له – السلسلة وعلامة اللغة. يجب أن تكون اللغة إحدى لغات عمل [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . يجب أن يكون defaultLabel فريدا لكافة [المصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.term) في نفس [مجموعة المصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset)، على المستوى الهرمي نفسه.

**sharepoint-التصنيف:termSetName**

الحصول على اسم كائن TermSet الحالي وتعيينه.

هذه التسمية المعجمية لمجموعة [مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset)، بلغة عمل [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . هذه معلمة مطلوبة لمجموعة [مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset). يستخدم لتمثيل [مجموعة مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset) بشكل مرئي.

بناء الجملة لتعريف termSetName هو:

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-التصنيف:propertyName**

الحصول على اسم الخاصية لكائن TermSet الحالي وتعيينه.

هذه هي التسمية المعجمية ل sharepoint-taxonomy:SharedCustomPropertyForTerm، sharepoint-taxonomy:LocalCustomPropertyForTerm وsharepoint-taxonomy:CustomPropertyForTermSet بلغة عمل [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .

يتم التعامل مع sharepoint-التصنيف:propertyName كمفتاح CustomProperty.

بناء الجملة لتعريف propetyName هو:

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>التسميات الاختيارية

يمكنك أيضا إضافة تسميات اختيارية إلى التصنيف الخاص بك.

**sharepoint-التصنيف:otherLabel**

هذه هي التسمية المعجمية البديلة [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term).

بناء الجملة لتعريف آخرLabel هو:

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>العلاقات الدلالية

تحتوي التصنيفات على علاقة ارتباط هرمية وأحيانا علاقة ارتباط بسيطة "ذات صلة"، ولكن بعضها له "علاقات دلالية" أو علاقات تم إنشاؤها خصيصا.

**sharepoint-التصنيف:parent**

يرتبط هذا بشكل هرمي [مصطلح بمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) آخر.[](/dotnet/api/microsoft.sharepoint.taxonomy.term) قد يكون [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) [مصطلحا](/dotnet/api/microsoft.sharepoint.taxonomy.term) من المستوى الأعلى لمجموعة [مصطلحات، ولكن](/dotnet/api/microsoft.sharepoint.taxonomy.termset) في حالة عدم وجوب أن يكون له [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) أصل.

بناء الجملة لتعريف أصل هو:

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

وهذا يعني أن TermA هو الأصل و TermA هو التابع.

**sharepoint-التصنيف:child**

يحتوي الكائن على مثيل واحد أو أكثر من مثيلات مجموعة المصطلحات التابعة، ويمكن الوصول إليها من خلال خاصية TermSets. توفر هذه الفئة أيضا أساليب لإنشاء كائنات مجموعة مصطلحات تابعة جديدة. يتم تحديد أذونات لتحرير مثيلات المصطلح التابع ومجموعة المصطلحات في المجموعة.

يرتبط هذا بشكل هرمي [مصطلح بمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) آخر.[](/dotnet/api/microsoft.sharepoint.taxonomy.term)

بناء الجملة لتعريف تابع هو:

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

وهذا يعني أن TermA هو الأصل و TermA هو التابع.

## <a name="documentation-notes"></a>ملاحظات الوثائق

يناقش هذا القسم التصنيف المفصل في Microsoft. SharePoint. مساحة اسم التصنيف.

**sharepoint-التصنيف:description**

هذا شرح مفصل لأي كيان [مفردات تصنيف SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy).

بناء الجملة لإضافة وصف هو:

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>خصائص مخصصة

يحصل على مجموعة كائنات الخصائص المخصصة لكائن المصطلح الحالي من القاموس للقراءة فقط.

الخصائص المخصصة هي أزواج قيم المفاتيح التي يمكن تعريفها [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) أو مجموعة [مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset)، لتعزيز وصف [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) أو مجموعة [المصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset). يحدد SharePoint مفتاح الخاصية المخصصة بمساعدة propertyName.

**sharepoint-التصنيف:CustomPropertyForTermSet**

بناء الجملة لتعريف هذا هو:

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**sharepoint-التصنيف:SharedCustomPropertyForTerm**

إذا كانت الخاصية المخصصة [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) تحتاج إلى أن يتم نقلها مع [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term)، عند إعادة استخدام [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) في مكان آخر، فأنت بحاجة إلى تعريفه ضمن SharedCustomPropertyForTerm.

بناء الجملة لتعريف هذا هو:

```SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**sharepoint-التصنيف:LocalCustomPropertyForTerm**

إذا كانت الخاصية المخصصة [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) لا تحتاج إلى أن يتم تنفيذها مع [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term)، عند إعادة استخدام [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) في مكان آخر، فأنت بحاجة إلى تعريفه ضمن LocalCustomPropertyForTerm.

بناء الجملة لتعريف هذا هو:

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>خصائص البيانات

في كل مستوى من التدرج الهرمي، يمكنك تكوين خصائص بيانات معينة لمصطلح أو مجموعة مصطلحات.

**sharepoint-التصنيف:isAvailableForTagging**

استخدم هذا لتحديد ما إذا كان [هناك مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) أو مجموعة [مصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy.termset) متوفرة في قوائم ومكتبات SharePoint.

بناء الجملة لهذا هو:

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>المجال والنطاق

يصف الجدول أدناه المجال ونطاق مفردات التصنيف SharePoint.

|دالات تقييم/فعل|معني|المجال|مجموعه|
|:--------------|:------|:-----|:----|
inTermSet|في مجموعة المصطلحات|مصطلح|مجموعة المصطلحات|
inTermGroup|في مجموعة المصطلحات|مجموعة المصطلحات|مجموعة المصطلحات|
topLevelTermOf|هو مصطلح المستوى الأعلى ل|مصطلح|مجموعة المصطلحات|
hasTopLevelTerm|يحتوي على مصطلح المستوى الأعلى|مجموعة المصطلحات|مصطلح|
termSetName|مجموعة المصطلحات لها اسم|مصطلح|القيمة الحرفية العادية|
DefaultLabel|المصطلح له تسمية افتراضية|مصطلح|القيمة الحرفية العادية|
غير ذلك من الLabel|المصطلح له تسمية أخرى|مصطلح|القيمة الحرفية العادية|
propertyName|له تسمية خاصية|SharedCustomPropertyForTerm، LocalCustomPropertyForTerm، CustomPropertyForTermSet |قيمة منطقية، سلسلة، عدد صحيح، عشري، مزدوج|
|وصف|يحتوي على وصف|الكل|القيمة الحرفية العادية|
|الاصل|له أصل|مصطلح|مصطلح|
|الطفل|له طفل|مصطلح|مصطلح|
|isAvailableForTagging|متوفر لوضع العلامات|مصطلح، مجموعة مصطلحات|منطقي|
|SharedCustomPropertyForTerm|يحتوي على خاصية مخصصة مشتركة|مصطلح|قيمة منطقية، سلسلة، عدد صحيح، عشري، مزدوج|
|LocalCustomPropertyForTerm|يحتوي على خاصية محلية مخصصة|مصطلح|قيمة منطقية، سلسلة، عدد صحيح، عشري، مزدوج|
|CustomPropertyForTermSet|يحتوي على خاصية مخصصة|مجموعة المصطلحات|قيمة منطقية، سلسلة، عدد صحيح، عشري، مزدوج|

لا تسمح سيناريوهات [SKOS](https://www.w3.org/TR/skos-primer/) الصالحة التي [SharePoint التصنيف](/dotnet/api/microsoft.sharepoint.taxonomy) بما يلي:

- التكرار الهرمي - يمكن إرفاق مفهوم [SKOS](https://www.w3.org/TR/skos-primer/) بالعديد من المفاهيم الأوسع في نفس الوقت، ولكن لا يسمح أيضا بالتبعية الدورية للمصطلحات: يمكن أن يكون للمصطلح تصنيف sharepoint-parent واحد فقط، ومن ثم التبعية الدورية.
- لا يسمح بالمصطلحات المعزولة في التصنيف SharePoint. كل sharepoint-التصنيف:يجب أن يكون للمصطلح إما sharepoint-التصنيف:parent أو يجب أن يكون sharepoint-taxonomy:topLevelTermOf a TermSet.
- لا يدعم التصنيف SharePoint العلاقات المرتبطة.
- SharePoint التصنيف يسمح فقط بنوعين من العلاقات الهرمية - sharepoint-التصنيف:parent وsharepoint-Taxonomy:child.
- على عكس [SKOS](https://www.w3.org/TR/skos-primer/)، لا يمكن إنشاء العلاقة الهرمية في مفردات التصنيف SharePoint إلا باستخدام المصطلحات ضمن مجموعة المصطلحات نفسها.

## <a name="see-also"></a>راجع أيضًا

[استيراد مجموعة مصطلحات باستخدام تنسيق يستند إلى SKOS](import-term-set-skos.md)
