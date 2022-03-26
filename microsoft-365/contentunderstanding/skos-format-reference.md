---
title: مرجع تنسيق SKOS SharePoint SKOS
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
ms.localizationpriority: high
description: مرجع تنسيق SKOS SharePoint SKOS
ms.openlocfilehash: 95183b64d76a70f69d08cd5a3c9dcf76f4e83bce
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/04/2021
ms.locfileid: "63568878"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>مرجع تنسيق SKOS SharePoint SKOS

تتضمن هذه المقالة مفردات RDF المستخدمة [لتمثيل SharePoint استنادا](/dotnet/api/microsoft.sharepoint.taxonomy) إلى [SKOS](https://www.w3.org/TR/skos-primer/). لتسلسل بناء جملة RDF هذا، استخدم RDF [TURTLE](https://www.w3.org/TR/turtle/).

يعرض الجدول التالي [مكافئات SKOS](https://www.w3.org/TR/skos-primer/) [لمصطلحات](/dotnet/api/microsoft.sharepoint.taxonomy) SharePoint الترتيب. SharePoint هذه القيم [قيم SKOS](https://www.w3.org/TR/skos-primer/) التي لا SharePoint مكافئة لها.

|SharePoint على|SKOS مكافئ|
|:-----------------|:--------------|
|sharepoint-taxonomy:Term|skos:Concept|
|sharepoint-taxonomy:TermSet|skos:ConceptScheme|
|sharepoint-taxonomy:inTermSet|skos:inScheme|
|sharepoint-taxonomy:hasTopLevelTerm|skos:hasTopConcept|
|sharepoint-taxonomy:topLevelTermOf|skos:topConceptOf|
|sharepoint-taxonomy:defaultLabel|skos:prefLabel|
|sharepoint-taxonomy:termSetName|skos:prefLabel|
|sharepoint-taxonomy:propertyName|skos:prefLabel|
|sharepoint-taxonomy:otherLabel|skos:altLabel|
|sharepoint-taxonomy:description|skos:definition|
|sharepoint-taxonomy:parent|skos:أوسع|
|sharepoint-taxonomy:child|skos:أضيق|

يعرض الجدول التالي كيانات SharePoint المفردات المشتقة من [OWL](https://www.w3.org/TR/owl2-primer/).

|SharePoint من مفردات SharePoint|مشتق من OWL|
|:-----------------------------|:----------------------|
|sharepoint-taxonomy:isAvailableForTagging|owl:datatypeproperty|
|sharepoint-taxonomy:SharedCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taxonomy:LocalCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taxonomy:CustomPropertyForTermSet|owl:ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>SharePoint من مفردات SharePoint

التصنيف هو نظام تصنيف رسمي. يقوم التصنيف بجماع الكلمات والتسميات والمصطلحات التي تصف شيئا ما، ثم يقوم بترتيب المجموعات في تسلسل هيكلي.

**sharepoint-taxonomy:Term**

يمثل مصطلحا أو كلمة أساسية في التسلسل الهيكلي لبيانات التعريف المدارة.

المصطلح [هو](/dotnet/api/microsoft.sharepoint.taxonomy.term) الوحدة ذرية SharePoint [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). ينتمي [كل](/dotnet/api/microsoft.sharepoint.taxonomy.term) مصطلح إلى [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) التي تنتمي إلى [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group).

بناء الجملة لتعريف [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) هو كما يلي:

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

يوجد [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) بشكل إجباري ضمن [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). DefaultLabel هو اسم [المصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) كما يظهر في التمثيل المرئي. تتضمن الحقول المطلوبة لتعريف [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) ما ما يلي:

- sharepoint-taxonomy:defaultLabel
- sharepoint-taxonomy:inTermSet

يمكن [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) ما:

- أن تكون مرتبطا بشكل هيكلي بمصطلح [آخر](/dotnet/api/microsoft.sharepoint.taxonomy.term) يتم توفيره [](/dotnet/api/microsoft.sharepoint.taxonomy.term) ينتمي كل من الشروط إلى [مجموعة الشروط نفسها](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- الحصول على شروط [متعددة للأطفال](/dotnet/api/microsoft.sharepoint.taxonomy.term)، ولكن فقط لمدة أصل [واحد](/dotnet/api/microsoft.sharepoint.taxonomy.term).
- ليس لديك مصطلح [أصل معرف](/dotnet/api/microsoft.sharepoint.taxonomy.term) ، إذا كان topLevelTermOf a [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- لديك واحد افتراضيLabel، لكل [لغة عمل TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .
- غير موجود إذا لم يحتوي على مصطلح [أصل](/dotnet/api/microsoft.sharepoint.taxonomy.term)، ولا هو topLevelTermOf a [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- لديك فقط افتراضي فريدLabel في المستوى الهرمي نفسه.

**sharepoint-taxonomy:TermSet**

يمثل مجموعة هرمية أو مسطحة من كائنات المصطلحات المعروفة ب "TermSet".

كما يقترح الاسم، TermSet عبارة عن مجموعة [من الشروط](/dotnet/api/microsoft.sharepoint.taxonomy.term). يجب [أن](/dotnet/api/microsoft.sharepoint.taxonomy.term) ينتمي [المصطلح في TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) إلى [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). لا [يمكن وجود](/dotnet/api/microsoft.sharepoint.taxonomy.term) أي مصطلح بشكل مستقل.

بناء الجملة لتعريف [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) هو:

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

[يتم تجميع TermSets](/dotnet/api/microsoft.sharepoint.taxonomy.termset) معا منطقيا في [TermGroups](/dotnet/api/microsoft.sharepoint.taxonomy.group). الحقل المطلوب لتعريف [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) هو:

- sharepoint-taxonomy:termSetName

في حالة المصطلحSetName الذي تم توفيره ليس فريدا ضمن [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group)، فإن SharePoint ي إلحاق رقم في نهاية الاسم للحفاظ على تفرد termSetName (المصطلحات).

**sharepoint-taxonomy:hasTopLevelTerm**

SharePoint هذه الخاصية في تعيين المصطلح الأعلى في [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset)، [](/dotnet/api/microsoft.sharepoint.taxonomy.term) وهو نقطة الإدخال إلى التسلسل الهيكلي للشروط في [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).[](/dotnet/api/microsoft.sharepoint.taxonomy.term) هذه علاقة معكوسة ل sharepoint-taxonomy:topLevelTermOf.

بناء الجملة لتعريف هذا هو:

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> لا يمكنك تحديد مدة المستوى [الأعلى](/dotnet/api/microsoft.sharepoint.taxonomy.term) لمصطلح [أصل](/dotnet/api/microsoft.sharepoint.taxonomy.term).

**sharepoint-taxonomy:topLevelTermOf**

Sharepoint-taxonomy:topLevelTermOf هو عكس sharepoint-taxonomy:hasTopLevelTerm

بناء الجملة لتعريف هذا هو:

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-taxonomy:inTermSet**

استخدم هذا الإعداد ل تعيين [مصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) إلى [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). يمكن [أن يتواجد](/dotnet/api/microsoft.sharepoint.taxonomy.term) المصطلح في مجموعة [شروط واحدة فقط](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint هذه الخاصية عند [تعريف مصطلح](https://github.com/MicrosoftDocs/microsoft-365-docs-pr/blob/3a3cd54dd076b18bdff1d43b3e342897f8704c23/microsoft-365/contentunderstanding/skos-format-reference.md#term).

## <a name="required-labels"></a>التسميات المطلوبة

قد ترغب مؤسستك في التخطيط بعناية قبل البدء في استخدام بيانات التعريف المدارة. يعتمد مقدار التخطيط الذي يجب عليك القيام به على مدى رسمية هذا التخطيط. يعتمد ذلك أيضا على مقدار عنصر التحكم الذي تريد فرضه على بيانات التعريف. في كل مستوى من مستويات التسلسل الهيكلي، تحتاج إلى تكوين التسميات المطلوبة لمصطلح أو مجموعة شروط.

يمكن أن يكون للمصطلحات تسمية واحدة أو أكثر باللغة الافتراضية، وصفر أو أكثر في اللغة غير الافتراضية. إذا كان المصطلح له تسميات بلغة، فيجب أن تكون إحدى التسميات هي التسمية الافتراضية.

**sharepoint-taxonomy:defaultLabel**

استخدم هذه التسمية الافتراضية المعجمية [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term) عبارة عن معلمة مطلوبة [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term). يتم استخدامها لتمثيل المصطلح [بشكل مرئي](/dotnet/api/microsoft.sharepoint.taxonomy.term).

بناء الجملة لتعريف defaultLabel هو:

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

يحتوي الإعداد الافتراضيLabel على جزأين له – السلسلة وعلامة اللغة. يجب أن تكون اللغة إحدى [لغات عمل TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . يجب أن يكون الإعداد الافتراضيLabel فريدا لجميع [الشروط](/dotnet/api/microsoft.sharepoint.taxonomy.term) في [نفس TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset)، على المستوى الهرمي نفسه.

**sharepoint-taxonomy:termSetName**

يحصل على اسم الكائن TermSet الحالي ويعيد تعيينه.

هذه التسمية المعجمية ل [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset)، بلغة [عمل TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . هذه معلمة مطلوبة ل [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). يتم استخدامها لتمثيل [TermSet بشكل مرئي](/dotnet/api/microsoft.sharepoint.taxonomy.termset).

بناء الجملة لتعريف المصطلحSetName هو:

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-taxonomy:propertyName**

يحصل على اسم الخاصية لكائن TermSet الحالي وي تعيينه.

هذه هي التسمية المعكوسة ل sharepoint-taxonomy:SharedCustomPropertyForTerm, sharepoint-taxonomy:LocalCustomPropertyForTerm و sharepoint-taxonomy:CustomPropertyForTermSet بلغة [عمل TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .

يتم التعامل مع sharepoint-taxonomy:propertyName كمفتاح CustomProperty.

بناء الجملة لتعريف propetyName هو:

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>تسميات اختيارية

يمكنك أيضا إضافة تسميات اختيارية إلى التصنيف.

**sharepoint-taxonomy:otherLabel**

هذه هي التسمية المعجمية البديلة [لمصطلح](/dotnet/api/microsoft.sharepoint.taxonomy.term).

بناء الجملة لتعريف آخرLabel هو:

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>العلاقات الدلالية

يكون للتسلسل الهيكلي في بعض الأحيان علاقة تقترن بسيطة "ذات صلة"، ولكن لدى بعضها "علاقات دلانية" أو علاقات تم إنشاؤها بشكل مخصص.

**sharepoint-taxonomy:parent**

ويربط هذا المصطلح بشكل هيكلي [مصطلحا](/dotnet/api/microsoft.sharepoint.taxonomy.term) بمصطلح [آخر](/dotnet/api/microsoft.sharepoint.taxonomy.term). قد [يكون](/dotnet/api/microsoft.sharepoint.taxonomy.term) المصطلح عبارة عن مصطلح من [](/dotnet/api/microsoft.sharepoint.taxonomy.term) المستوى الأعلى في [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset)، ولكن في حالة عدم وجوده يجب أن يكون له مصطلح [أصل](/dotnet/api/microsoft.sharepoint.taxonomy.term).

بناء الجملة لتعريف أصل هو:

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

وهذا يعني أن TermA هو الأصل و TermA هو الطفل.

**sharepoint-taxonomy:child**

يحتوي الكائن على مثيل واحد أو أكثر من أمثلة TermSet، ويمكن الوصول إليها من خلال الخاصية TermSets. توفر هذه الفئة أيضا أساليب لإنشاء كائنات TermSet فرعية جديدة. يتم تحديد الأذونات لتحرير مثيلات المصطلحات و TermSet الخاصة بالطفل في المجموعة.

ويربط هذا المصطلح بشكل هيكلي [مصطلحا](/dotnet/api/microsoft.sharepoint.taxonomy.term) بمصطلح [آخر](/dotnet/api/microsoft.sharepoint.taxonomy.term).

بناء الجملة لتعريف طفل هو:

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

وهذا يعني أن TermA هو الأصل و TermA هو الطفل.

## <a name="documentation-notes"></a>ملاحظات الوثائق

يتناول هذا القسم هذا النوع من المعلومات المفصلة في Microsoft. SharePoint. مساحة اسم للضريبة.

**sharepoint-taxonomy:description**

هذا شرح مفصل لأي SharePoint [مفردات](/dotnet/api/microsoft.sharepoint.taxonomy) في SharePoint.

بناء الجملة لإضافة وصف هو:

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>الخصائص المخصصة

يحصل على مجموعة من كائنات الخاصية المخصصة لكائن المصطلح الحالي من القاموس للقراءة فقط.

الخصائص المخصصة هي أزواج قيم أساسية يمكن تعريفها لمصطلح أو مجموعة شروط[](/dotnet/api/microsoft.sharepoint.taxonomy.term)، لمزيد من [](/dotnet/api/microsoft.sharepoint.taxonomy.termset)وصف المصطلح أو [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).[](/dotnet/api/microsoft.sharepoint.taxonomy.term) SharePoint إلى تحديد مفتاح الخاصية المخصصة بمساعدة الخاصيةName.

**sharepoint-taxonomy:CustomPropertyForTermSet**

بناء الجملة لتعريف هذا هو:

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**sharepoint-taxonomy:SharedCustomPropertyForTerm**

إذا كان يجب نقل الخاصية المخصصة لمصطلح مع المصطلح، عند إعادة استخدام [](/dotnet/api/microsoft.sharepoint.taxonomy.term)المصطلح في مكان آخر، يجب [](/dotnet/api/microsoft.sharepoint.taxonomy.term) تعريفه ضمن SharedCustomPropertyForTerm.[](/dotnet/api/microsoft.sharepoint.taxonomy.term)

بناء الجملة لتعريف هذا هو:

```SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**sharepoint-taxonomy:LocalCustomPropertyForTerm**

إذا لم تكن الخاصية المخصصة للمصطلح بحاجة إلى أن يتم حملها مع المصطلح، [](/dotnet/api/microsoft.sharepoint.taxonomy.term)عند إعادة استخدام المصطلح في مكان [](/dotnet/api/microsoft.sharepoint.taxonomy.term) آخر، يجب تعريفه ضمن LocalCustomPropertyForTerm.[](/dotnet/api/microsoft.sharepoint.taxonomy.term)

بناء الجملة لتعريف هذا هو:

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>خصائص البيانات

في كل مستوى من مستويات التسلسل الهيكلي، يمكنك تكوين خصائص بيانات معينة لمصطلح أو مجموعة شروط.

**sharepoint-taxonomy:isAvailableForTagging**

استخدم هذا لتحديد ما إذا كان [](/dotnet/api/microsoft.sharepoint.taxonomy.term) مصطلح أو [مجموعة](/dotnet/api/microsoft.sharepoint.taxonomy.termset) شروط متوفرة في SharePoint والمكتبات.

بناء الجملة لهذا هو:

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>المجال و النطاق

يصف الجدول أدناه المجال ومدى SharePoint المفردات في SharePoint.

|التكريس/الفعل|المعنى|المجال|النطاق|
|:--------------|:------|:-----|:----|
inTermSet|مجموعة المصطلحات|المدة|مجموعة المصطلحات|
inTermGroup|في مجموعة المصطلحات|TermSet|TermGroup|
topLevelTermOf|هو مصطلح المستوى الأعلى ل|المدة|TermSet|
hasTopLevelTerm|له مصطلح المستوى الأعلى|مجموعة المصطلحات|المدة|
termSetName|مجموعة المصطلحات لها اسم|المدة|حرف عادي|
defaultLabel|المصطلح له تسمية افتراضية|المدة|حرف عادي|
otherLabel|المصطلح له تسمية أخرى|المدة|حرف عادي|
propertyName|له تسمية الخاصية|SharedCustomPropertyForTerm, LocalCustomPropertyForTerm, CustomPropertyForTermSet |منطقي، سلسلة، عدد صحيح، عدد عشري، مزدوج|
|الوصف|له وصف|الكل|حرف عادي|
|الأصل|له أصل|المدة|المدة|
|طفل|له طفل|المدة|المدة|
|isAvailableForTagging|متوفر لوضع العلامات|المصطلح، مجموعة المصطلحات|منطقي|
|SharedCustomPropertyForTerm|لديه خاصية مخصصة مشتركة|المدة|منطقي، سلسلة، عدد صحيح، عشري، مزدوج|
|LocalCustomPropertyForTerm|لديه خاصية مخصصة محلية|المدة|منطقي، سلسلة، عدد صحيح، عدد عشري، مزدوج|
|CustomPropertyForTermSet|لديه خاصية مخصصة|TermSet|منطقي، سلسلة، عدد صحيح، عدد عشري، مزدوج|

[لا تسمح سيناريوهات SKOS](https://www.w3.org/TR/skos-primer/) [SharePoint التي لا](/dotnet/api/microsoft.sharepoint.taxonomy) تسمح بتوزيعها:

- التكرار الهرمي - يمكن إرفاق مفهوم [SKOS](https://www.w3.org/TR/skos-primer/) بعدة مفاهيم أوسع في الوقت نفسه، ولكن يمكن أن يكون ل sharepoint-taxonomy:Term فقط sharepoint-taxonomy:parent، وبالتالي تبعية دورية، الشروط غير مسموح بها أيضا.
- الشروط المعزولة غير مسموح بها في SharePoint. كل sharepoint-taxonomy:Term يجب أن يكون له sharepoint-taxonomy:parent أو يجب أن يكون sharepoint-taxonomy:topLevelTermOf a TermSet.
- SharePoint لا يدعم هذا SharePoint العلاقات المقترنة.
- SharePoint الترتيب نوعين فقط من العلاقات الهيكلية – sharepoint-taxonomy:parent و sharepoint-Taxonomy:child.
- بخلاف [SKOS](https://www.w3.org/TR/skos-primer/)، لا يمكن إنشاء SharePoint الهيكلية في مفردات SharePoint، إلا بمصطلحات ضمن نفس TermSet.

## <a name="see-also"></a>راجع أيضًا

[استيراد مجموعة مصطلحات باستخدام تنسيق مستند إلى SKOS](import-term-set-skos.md)