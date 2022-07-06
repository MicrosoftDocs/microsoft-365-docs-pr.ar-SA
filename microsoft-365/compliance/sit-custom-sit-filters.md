---
title: مرجع عوامل تصفية نوع المعلومات الحساسة المخصصة
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: تقدم هذه المقالة قائمة بعوامل التصفية التي يمكن ترميزها في أنواع معلومات حساسة مخصصة.
ms.openlocfilehash: 79e4a2520ab922248f65adf1b0506219987fe832
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631948"
---
# <a name="custom-sensitive-information-type-filters-reference"></a>مرجع عوامل تصفية نوع المعلومات الحساسة المخصصة

في Microsoft، يمكنك تعريف عوامل التصفية أو عمليات التحقق الأخرى أثناء إنشاء أنواع معلومات حساسة مخصصة (SIT).

## <a name="list-of-supported-filters-and-use-cases"></a>قائمة بعوامل التصفية وحالات الاستخدام المدعومة

### <a name="alldigitssame-exclude"></a>استبعاد AllDigitsSame

الوصف: يسمح لك باستبعاد التطابقات التي تحتوي على كافة الأرقام كأرقام مكررة، مثل 111111111 أو 111-111-111

تعريف عوامل التصفية
```xml
<Filters id="ssn_filters">
    <Filter type="AllDigitsSameFilter"></Filter>
</Filters>
```

استخدامه في حزمة القواعد على مستوى الكيان
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85"  filters="ssn_filters">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

استخدامه في حزمة القواعد على مستوى النمط
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="ssn_filters">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

### <a name="textmatchfilter-startswith"></a>TextMatchFilter StartsWith 

الوصف: يسمح لك بتحديد أحرف البداية للكيان. يحتوي على متغيرين، تضمين واستبعاد.

على سبيل المثال لاستبعاد الأرقام بدءا من 0500، 91، 091، 010 في قائمة مثل هذا:

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

يمكنك استخدام xml التالي

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>
</Filters>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```
على سبيل المثال، لتضمين الأرقام بدءا من 0500، 91، 091، 0100 في قائمة مثل هذا: 

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

يمكنك استخدام xml التالي

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-endswith"></a>TextMatchFilter EndsWith 

الوصف: يسمح لك بتعريف أحرف النهاية للكيان. 

على سبيل المثال، لاستبعاد الأرقام التي تنتهي ب 0500,91,091، 0100 في قائمة مثل هذا:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

يمكنك استخدام xml التالي

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="EndsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```

على سبيل المثال، لتضمين الأرقام التي تنتهي ب 0500، 91، 091، 0100، في قائمة مثل هذا:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

يمكنك استخدام xml التالي

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction=" EndsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-full"></a>TextMatchFilter Full

الوصف: يسمح لك بحظر تطابقات معينة لمنعها من تشغيل القاعدة. على سبيل المثال، استبعاد 4111111111111111 من قائمة تطابقات بطاقة الائتمان الصالحة.

على سبيل المثال، لاستبعاد أرقام بطاقات الائتمان مثل 4111111111111111 3241891031113111 في قائمة مثل هذه:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

يمكنك استخدام xml التالي

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Full" logic="Exclude" textProcessorId="Keyword_false_positives_full">
</Filter>

  <Keyword id="Keyword_false_positives_full">
    <Group matchStyle="string">
      <Term>4111111111111111</Term>
      <Term>3241891031113111</Term>
    </Group>
  </Keyword>
```

على سبيل المثال، لتضمين أرقام بطاقات الائتمان مثل 4111111111111111 3241891031113111 في قائمة مثل هذه:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

يمكنك استخدام xml التالي

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_false_positives_full">
</Filter>
```

### <a name="textmatchfilter-prefix"></a>بادئة TextMatchFilter

الوصف: يسمح لك بتعريف الأحرف السابقة التي يجب تضمينها أو استبعادها دائما. على سبيل المثال، إذا كان رقم بطاقة الائتمان مسبوقا ب "معرف الطلب:" فقم بإزالة المطابقة من التطابقات الصحيحة.

على سبيل المثال، لاستبعاد تكرارات أرقام الهواتف التي تحتوي على **رقم الهاتف** والاتصال **بي في** سلاسل قبل رقم الهاتف، في قائمة مثل هذا:

- رقم الهاتف 091-8974-653278
- الهاتف 45-124576532-123
- 45-124576532-123

يمكنك استخدام xml التالي

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_prefix">
</Filter>
  <Keyword id="Keyword_false_positives_prefix">
    <Group matchStyle="string">
      <Term>phone number</Term>
      <Term>call me at</Term>
    </Group>
  </Keyword>
```

على سبيل المثال، لتضمين التكرارات التي تحتوي على **سلاسل** **# بطاقة الائتمان والبطاقة** قبل رقم بطاقة الائتمان، في قائمة مثل هذا:

- بطاقة الائتمان 45-124576532-123 
- 45-124576532-123 (الذي قد يكون رقم الهاتف)

يمكنك استخدام xml التالي

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_prefix">
</Filter>

  <Keyword id="Keyword_true_positives_prefix">
    <Group matchStyle="string">
      <Term>credit card</Term>
      <Term>card #</Term>
    </Group>
  </Keyword
```

### <a name="textmatchfilter-suffix"></a>لاحقة TextMatchFilter

الوصف: يسمح لك بتعريف الأحرف التالية التي يجب تضمينها أو استبعادها دائما. على سبيل المثال، إذا كان رقم بطاقة الائتمان متبوعا ب '/xuid'، فقم بإزالة المطابقة من التطابقات الصحيحة.

على سبيل المثال، استبعاد التكرارات العليا إذا كان هناك خمسة مثيلات أخرى من أربعة أرقام كلاحقة في قائمة مثل هذا:

- 1234-5678-9321 4500 9870 6321 48925566
- 1234-5678-9321

يمكنك استخدام xml التالي

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Regex_false_positives_suffix">
</Filter>

  <Regexid="Regex_false_positives_suffix">(\d{4}){5,}</Regex>
```
على سبيل المثال، لاستبعاد التكرارات إذا كانت متبوعة ب **/xuidsuffix**، مثل واحدة في هذه القائمة:

- 1234-5678-9321 /xuid
- 1234-5678-9321

يمكنك استخدام xml هذا

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_suffix">
</Filter>

  <Keyword id="Keyword_false_positives_suffix">
    <Group matchStyle="string">
      <Term>/xuid</Term>
    </Group>
  </Keyword>
```

على سبيل المثال، لتضمين تكرار فقط إذا كان متبوعا **ب cvv** أو **انتهت صلاحيته**، مثل اثنين في هذه القائمة:

- 45-124576532-123 
- 45-124576532-123 cvv 966
- 45-124576532-123 تنتهي صلاحيتها في 03/23

يمكنك استخدام xml هذا

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_suffix">
</Filter>

  <Keyword id="Keyword_true_positives_suffix">
    <Group matchStyle="string">
      <Term>cvv</Term>
      <Term>expires</Term>
    </Group>
  </Keyword>
```

## <a name="using-filters-in-rule-packages"></a>استخدام عوامل التصفية في حزم القواعد

يمكن تعريف عوامل التصفية على SIT بأكملها أو على نمط. فيما يلي بعض أمثلة أجزاء التعليمات البرمجية. 

### <a name="at-sensitive-information-type-level"></a>على مستوى نوع المعلومات الحساسة

عوامل التصفية في الوحدة - سوف تغطي جميع الأنماط التابعة

سيتم تطبيق عوامل التصفية على **جميع** المثيلات المصنفة حسب أي من الأنماط في هذا الكيان / النوع الحساس

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
```

### <a name="at-the-individual-pattern-of-the-sensitive-information-type-level"></a>على النمط الفردي لمستوى نوع المعلومات الحساسة

عوامل التصفية على مستوى النقش فقط.

سيتم تطبيق عامل التصفية على المثيلات المطابقة للنمط.

```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Keyword_cc_verification" />
      </Pattern>
</Entity>
```


### <a name="at-sensitive-information-type-level-and-an-additional-filter-on-some-of-the-patterns-of-that-entity"></a>على مستوى نوع المعلومات الحساسة وعامل تصفية إضافي على بعض أنماط هذا الكيان

عوامل التصفية في الوحدة + النمط

سيتم تطبيق عوامل التصفية على **جميع** المثيلات المصنفة حسب أي من الأنماط في هذا الكيان / النوع الحساس. سيقوم عامل تصفية مستوى النمط بتصفية المثيلات المطابقة لهذا النمط.

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85" filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
``` 

 

## <a name="more-information"></a>معلومات إضافية

- [تعرف على تفادي فقدان البيانات في Microsoft Purview](dlp-learn-about-dlp.md)

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)

- [دالات نوع المعلومات الحساسة](sit-functions.md)
