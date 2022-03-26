---
title: إنشاء نوع معلومات حساسة مخصصة باستخدام PowerShell
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: تعرف على كيفية إنشاء نوع معلومات مخصص حساس واستيراده لنهج في مركز التوافق.
ms.openlocfilehash: 89c215ca52b255a6e3aed72ff032cdd2475c0d87
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/18/2022
ms.locfileid: "63566701"
---
# <a name="create-a-custom-sensitive-information-type-using-powershell"></a>إنشاء نوع معلومات حساسة مخصصة باستخدام PowerShell

توضح لك هذه المقالة كيفية إنشاء ملف حزمة قاعدة *XML يعرف* أنواع المعلومات [الحساسة المخصصة](sensitive-information-type-entity-definitions.md). تصف هذه المقالة نوع معلومات مخصص حساس يعرف هوية الموظف. يمكنك استخدام نموذج XML في هذه المقالة كنقطة بداية لملف XML الخاص بك.

لمزيد من المعلومات حول أنواع المعلومات الحساسة، راجع [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md).

بعد إنشاء ملف XML تم تكوينه بشكل جيد، يمكنك تحميله إلى Microsoft 365 PowerShell. بعد ذلك، أنت جاهز لاستخدام نوع المعلومات الحساسة المخصصة في السياسات. يمكنك اختبار فعاليتها في الكشف عن المعلومات الحساسة كما أردت.

> [!NOTE]
> إذا لم تكن بحاجة إلى عنصر تحكم الحبوب الدقيقة الذي يوفره PowerShell، يمكنك إنشاء أنواع معلومات حساسة مخصصة في مركز التوافق في Microsoft 365. لمزيد من المعلومات، راجع [إنشاء نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type.md).

## <a name="important-disclaimer"></a>إخلاء المسؤولية المهم

لا يمكن أن يساعدك دعم Microsoft في إنشاء تعريفات مطابقة للمحتوى.

لتطوير مطابقة المحتوى المخصص واختباره وتصحيح الأخطاء فيه، ستحتاج إلى استخدام موارد تقنيات المعلومات الداخلية الخاصة بك، أو استخدام الخدمات الاستشارية، مثل Microsoft Consulting Services (MCS). يمكن لمهندسي دعم Microsoft توفير دعم محدود لهذه الميزة، ولكن لا يمكنهم ضمان تلبية الاقتراحات المخصصة لمطابقة المحتوى بشكل كامل لاحتياجاتك.

يمكن أن توفر MCS تعبيرات منتظمة لأغراض الاختبار. ويمكنهم أيضا توفير المساعدة في استكشاف الأخطاء وإصلاحها لنمط RegEx موجود لا يعمل كما هو متوقع مع مثال محتوى محدد واحد.

راجع [مشاكل التحقق من الصحة المحتملة التي يجب أن تكون على علم بها](#potential-validation-issues-to-be-aware-of) في هذه المقالة.

لمزيد من المعلومات حول محرك Boost.RegEx (المعروف سابقا باسم RegEx++) المستخدم لمعالجة النص، راجع [Boost.Regex 5.1.3](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/).

> [!NOTE]
> إذا كنت تستخدم حرفا (&) كجزء من كلمة أساسية في نوع المعلومات الحساسة المخصص، ستحتاج إلى إضافة مصطلح إضافي مع مسافات حول الحرف. على سبيل المثال، لا تستخدم `L & P` _._ `L&P`

## <a name="sample-xml-of-a-rule-package"></a>نموذج XML لحزمة قاعدة

إليك نموذج XML لحزمة القواعد التي سننشئها في هذه المقالة. يتم شرح العناصر والصفات في الأقسام أدناه.

```xml
<?xml version="1.0" encoding="UTF-16"?>
<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
<RulePack id="DAD86A92-AB18-43BB-AB35-96F7C594ADAA">
  <Version build="0" major="1" minor="0" revision="0"/>
  <Publisher id="619DD8C3-7B80-4998-A312-4DF0402BAC04"/>
  <Details defaultLangCode="en-us">
    <LocalizedDetails langcode="en-us">
      <PublisherName>Contoso</PublisherName>
      <Name>Employee ID Custom Rule Pack</Name>
      <Description>
      This rule package contains the custom Employee ID entity.
      </Description>
    </LocalizedDetails>
  </Details>
</RulePack>
<Rules>
<!-- Employee ID -->
  <Entity id="E1CC861E-3FE9-4A58-82DF-4BD259EAB378" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="65">
      <IdMatch idRef="Regex_employee_id"/>
    </Pattern>
    <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_employee_id"/>
      <Match idRef="Func_us_date"/>
    </Pattern>
    <Pattern confidenceLevel="85">
      <IdMatch idRef="Regex_employee_id"/>
      <Match idRef="Func_us_date"/>
      <Any minMatches="1">
        <Match idRef="Keyword_badge" minCount="2"/>
        <Match idRef="Keyword_employee"/>
      </Any>
      <Any minMatches="0" maxMatches="0">
        <Match idRef="Keyword_false_positives_local"/>
        <Match idRef="Keyword_false_positives_intl"/>
      </Any>
    </Pattern>
  </Entity>
  <Regex id="Regex_employee_id">(\s)(\d{9})(\s)</Regex>
  <Keyword id="Keyword_employee">
    <Group matchStyle="word">
      <Term>Identification</Term>
      <Term>Contoso Employee</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_badge">
    <Group matchStyle="string">
      <Term>card</Term>
      <Term>badge</Term>
      <Term caseSensitive="true">ID</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_false_positives_local">
    <Group matchStyle="word">
      <Term>credit card</Term>
      <Term>national ID</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_false_positives_intl">
    <Group matchStyle="word">
      <Term>identity card</Term>
      <Term>national ID</Term>
      <Term>EU debit card</Term>
    </Group>
  </Keyword>
  <LocalizedStrings>
    <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB378">
      <Name default="true" langcode="en-us">Employee ID</Name>
      <Description default="true" langcode="en-us">
      A custom classification for detecting Employee IDs.
      </Description>
      <Description default="false" langcode="de-de">
      Description for German locale.
      </Description>
    </Resource>
  </LocalizedStrings>
</Rules>
</RulePackage>
```

## <a name="what-are-your-key-requirements-rule-entity-pattern-elements"></a>ما هي متطلباتك الأساسية؟ [القاعدة، الكيان، عناصر النمط]

من المهم أن تفهم البنية الأساسية لم المخطط XML للقاعدة. سيساعد فهمك للبنية نوع المعلومات الحساسة المخصصة لتحديد المحتوى المناسب.

تعرف القاعدة كيانا واحدا أو أكثر (يعرف أيضا بأنواع المعلومات الحساسة). يعرف كل كيان نمطا واحدا أو أكثر. النمط هو ما تبحث عنه النهج عند تقييمه للمحتوى (على سبيل المثال، البريد الإلكتروني والمستندات).

في علامة XML، تعني "القواعد" الأنماط التي تحدد نوع المعلومات الحساسة. لا تشرك المراجع إلى القواعد في هذه المقالة ب "الشروط" أو "الإجراءات" الشائعة في ميزات Microsoft الأخرى.

### <a name="simplest-scenario-entity-with-one-pattern"></a>السيناريو الأبسط: كيان مع نمط واحد

إليك سيناريو بسيط: تريد أن يحدد النهج الخاص بك المحتوى الذي يحتوي على هويات الموظفين المكونة من تسعة أرقام المستخدمة في مؤسستك. يشير النمط إلى التعبير العادي في القاعدة الذي يحدد الأرقام المكونة من تسعة أرقام. أي محتوى يحتوي على رقم من تسعة أرقام يلبي النمط.

![رسم تخطيطي لكيان مع نمط واحد.](../media/4cc82dcf-068f-43ff-99b2-bac3892e9819.png)

ولكن، قد يحدد هذا النمط أي رقم **من تسعة أرقام** ، بما في ذلك أرقام أطول أو أنواع أخرى من الأرقام المكونة من تسعة أرقام ليست من هويات الموظفين. يعرف هذا النوع من المطابقات غير المرغوب فيها *بالإيجابية الخاطئة*.

### <a name="more-common-scenario-entity-with-multiple-patterns"></a>سيناريو أكثر شيوعا: كيان مع أنماط متعددة

نظرا لاحتمال وجود إيجابيات خاطئة، تستخدم عادة أكثر من نمط واحد لتعريف كيان. توفر الأنماط المتعددة إثباتات دعم للكيان الهدف. على سبيل المثال، يمكن أن تساعد الكلمات الأساسية أو التواريخ أو النصوص الأخرى الإضافية في تحديد الكيان الأصلي (على سبيل المثال، رقم الموظف المكون من تسعة أرقام).

على سبيل المثال، لزيادة احتمالية تحديد المحتوى الذي يحتوي على "هوية الموظف"، يمكنك تحديد أنماط أخرى للبحث عن:

- نمط يحدد تاريخ التوظيف.
- نمط يحدد كل من تاريخ التوظيف والكلمة الأساسية "هوية الموظف".

![رسم تخطيطي لكيان مع أنماط متعددة.](../media/c8dc2c9d-00c6-4ebc-889a-53b41a90024a.png)

هناك نقاط هامة يجب التفكير فيها لمطابقات الأنماط المتعددة:

- والأنماط التي تتطلب المزيد من الدلائل لديها مستوى ثقة أعلى. استنادا إلى مستوى الثقة، يمكنك اتخاذ الإجراءات التالية:
  - استخدم إجراءات أكثر تقييدا (مثل حظر المحتوى) مع تطابقات عالية الثقة.
  - استخدم إجراءات أقل تقييدا (مثل إرسال الإعلامات) مع تطابقات أقل ثقة.

- تشير عناصر الدعم `IdMatch` `Match` والعناصر إلى RegExes والكلمات `Rule` الأساسية التي تكون في الواقع من عناصر العنصر، وليس .`Pattern` يتم الإشارة إلى عناصر الدعم هذه بواسطة `Pattern`، ولكن يتم تضمينها في `Rule`. يعني هذا السلوك أنه يمكن الإشارة إلى تعريف واحد لعنصر دعم، مثل تعبير عادي أو قائمة كلمات أساسية، بواسطة وحدات وأنماط متعددة.

## <a name="what-entity-do-you-need-to-identify-entity-element-id-attribute"></a>ما هو الكيان الذي تحتاج إلى تحديده؟ [عنصر كيان، سمة المرجع]

الكيان هو نوع معلومات حساس، مثل رقم بطاقة الائتمان، له نمط محدد جيدا. يحتوي كل كيان على GUID فريد كم ID الخاص به.

### <a name="name-the-entity-and-generate-its-guid"></a>تسمية الكيان وإنشاء GUID الخاص به

1. في محرر XML الذي تختاره، أضف `Rules` العنصرين و `Entity` .
2. أضف تعليقا يحتوي على اسم الكيان المخصص، مثل "عرف الموظف". في وقت لاحق،  تضيف اسم الكيان إلى مقطع السلاسل المعرف، وسيظهر هذا الاسم في مركز الإدارة عند إنشاء نهج.
3. إنشاء GUID فريد لكيانك. على سبيل المثال، في Windows PowerShell، يمكنك تشغيل الأمر `[guid]::NewGuid()`. وفي وقت لاحق،  تضيف أيضا GUID إلى مقطع السلاسل المعرف في الكيان.

![تعرض علامات XML عناصر "القواعد" و"الكيان".](../media/c46c0209-0947-44e0-ac3a-8fd5209a81aa.png)

## <a name="what-pattern-do-you-want-to-match-pattern-element-idmatch-element-regex-element"></a>ما النمط الذي تريد مطابقته؟ [عنصر النمط، عنصر IdMatch، عنصر Regex]

يحتوي النمط على قائمة بنوع المعلومات الحساسة الذي يبحث عنه. يمكن أن يتضمن النمط RegExes والكلمات الأساسية والوظائف المضمنة. تقوم الدالات بمهمة مثل تشغيل RegExes للعثور على التواريخ أو العناوين. يمكن أن يكون لأنواع المعلومات الحساسة أنماط متعددة ذات ثقة فريدة.

في الرسم التخطيطي التالي، تشير كل الأنماط إلى التعبير العادي نفسه. تبحث RegEx هذه عن رقم من تسعة أرقام `(\d{9})` محاط بمساحة بيضاء `(\s) ... (\s)`. يشير العنصر إلى هذا `IdMatch` التعبير العادي، وهو المتطلب الشائع لكل الأنماط التي تبحث عن كيان "المرجع الموظف". `IdMatch` هو المعرف الذي يحاول النمط مطابقته. يجب `Pattern` أن يكون العنصر عنصرا واحدا `IdMatch` بالضبط.

![تعرض علامات XML عناصر نقش متعددة تشير إلى عنصر Regex واحد.](../media/8f3f497b-3b8b-4bad-9c6a-d9abf0520854.png)

ترجع مطابقة النمط المقتنع مستوى للعد والثقة، يمكنك استخدامه في الشروط في النهج. عند إضافة شرط للكشف عن نوع معلومات حساسة إلى نهج، يمكنك تحرير مستوى العدد والثقة كما هو موضح في الرسم التخطيطي التالي. يتم شرح مستوى الثقة (يسمى أيضا دقة مطابقة) لاحقا في هذه المقالة.

![عدد المثيلات ومطابقة خيارات الدقة.](../media/sit-confidence-level.png)

التعبيرات العادية فعالة، لذلك هناك مشاكل تحتاج إلى معرفتها. على سبيل المثال، يمكن أن تؤثر RegEx التي تعرف الكثير من المحتوى على الأداء. لمعرفة المزيد حول هذه المشاكل، راجع مشاكل التحقق من الصحة المحتملة التي يجب أن تكون على [علم بها](#potential-validation-issues-to-be-aware-of) لاحقا في هذه المقالة.

## <a name="do-you-want-to-require-additional-evidence-match-element-mincount-attribute"></a>هل تريد طلب دليل إضافي؟ [عنصر مطابقة، سمة minCount]

بالإضافة إلى `IdMatch`، يمكن أن `Match` يستخدم النمط العنصر لتطلب إثبات دعم إضافي، مثل كلمة أساسية أو RegEx أو تاريخ أو عنوان.

قد `Pattern` تتضمن عناصر `Match` متعددة:

- مباشرة في `Pattern` العنصر.
- يتم دمجها باستخدام `Any` العنصر.

`Match` يتم ضم العناصر بواسطة عامل تشغيل AND ضمني. بعبارة أخرى، يجب `Match` أن تكون كل العناصر راضية عن النمط الذي يجب مطابقته.

يمكنك استخدام العنصر لتقديم `Any` عوامل تشغيل AND أو OR. يتم `Any` وصف العنصر لاحقا في هذه المقالة.

يمكنك استخدام السمة `minCount` الاختيارية لتحديد عدد مثيلات مطابقة يجب العثور عليها لكل `Match` عنصر. على سبيل المثال، يمكنك تحديد أن النمط راض فقط عند العثور على كلمتين أساسية على الأقل من قائمة الكلمات الأساسية.

![تعرض علامات XML عنصر مطابقة مع سمة minOccurs.](../media/607f6b5e-2c7d-43a5-a131-a649f122e15a.png)

### <a name="keywords-keyword-group-and-term-elements-matchstyle-and-casesensitive-attributes"></a>الكلمات الأساسية [عناصر الكلمة الأساسية والمجموعة والمصطلحات، تطابقالسمات والوسيمات الحساسة]

كما هو موضح سابقا، يتطلب تحديد المعلومات الحساسة في أغلب الأحيان كلمات أساسية إضافية كدليل منسدل. على سبيل المثال، بالإضافة إلى مطابقة رقم من تسعة أرقام، يمكنك البحث عن كلمات مثل "بطاقة" أو "شارة" أو "هوية" باستخدام عنصر الكلمة الأساسية. العنصر `Keyword` له سمة `ID` يمكن `Match` الإشارة إليها بواسطة عناصر متعددة في عدة أنماط أو وحدات.

يتم تضمين الكلمات الأساسية ك قائمة بالعناصر `Term` في `Group` عنصر. العنصر `Group` له سمة مع `matchStyle` قيمتين محتملتين:

- **matchStyle="word"**: تعرف كلمة مطابقة الكلمات بالكامل محاطة بمساحة بيضاء أو بمحددات أخرى. يجب عليك دائما استخدام **الكلمة** ما لم تكن بحاجة إلى مطابقة أجزاء من الكلمات أو الكلمات باللغات الآسيوية.

- **matchStyle="string"**: تعرف مطابقة السلسلة السلاسل بغض النظر عما يحيط بها. على سبيل المثال، تتطابق "المعروض" مع "العرض" و"الفكرة". استخدم `string` فقط عندما تحتاج إلى مطابقة الكلمات الآسيوية أو إذا كانت الكلمة الأساسية مضمنة في سلاسل أخرى.

وأخيرا، يمكنك `caseSensitive` `Term` استخدام سمة العنصر لتحديد أن المحتوى يجب أن يكون متطابقا تماما مع الكلمة الأساسية، بما في ذلك الأحرف ذات الأحرف السفلية والأحرف الكبيرة.

![تعرض علامات XML تطابق العناصر التي تشير إلى الكلمات الأساسية.](../media/e729ba27-dec6-46f4-9242-584c6c12fd85.png)

### <a name="regular-expressions-regex-element"></a>التعبيرات العادية [عنصر Regex]

في هذا المثال، يستخدم `ID` `IdMatch` كيان الموظف العنصر بالفعل لالإشارة إلى تعبير عادي للنقش: رقم من تسعة أرقام محاط بمساحة بيضاء. بالإضافة إلى ذلك `Match` `Regex` ، يمكن أن يستخدم النمط عنصرا لالإشارة إلى عنصر إضافي لتحديد الدليل المرجعي، مثل رقم من خمسة أرقام أو تسعة أرقام بتنسيق رمز بريدي في الولايات المتحدة.

### <a name="additional-patterns-such-as-dates-or-addresses-built-in-functions"></a>أنماط إضافية مثل التواريخ أو العناوين [الدالات المضمنة]

يمكن لأنواع المعلومات الحساسة أيضا استخدام الدالات المضمنة لتحديد إثباتات إثبات التكاتف. على سبيل المثال، تاريخ الولايات المتحدة أو تاريخ الاتحاد الأوروبي أو تاريخ انتهاء الصلاحية أو عنوان الولايات المتحدة. Microsoft 365 لا تدعم تحميل الدالات المخصصة الخاصة بك. ولكن، عندما تنشئ نوع معلومات حساسة مخصصا، يمكن للكيان الإشارة إلى دالات مضمنة.

على سبيل `Func_us_date` المثال، تتضمن شارة هوية الموظف تاريخ توظيف، بحيث يمكن لهذا الكيان المخصص استخدام الدالة المضمنة لتحديد تاريخ بتنسيق شائع الاستخدام في الولايات المتحدة.

لمزيد من المعلومات، راجع [دالات نوع المعلومات الحساسة](sit-functions.md).

![علامات XML تعرض مطابقة العنصر للإشارة إلى الدالة المضمنة.](../media/dac6eae3-9c52-4537-b984-f9f127cc9c33.png)

## <a name="different-combinations-of-evidence-any-element-minmatches-and-maxmatches-attributes"></a>مجموعات مختلفة من الدلائل [أي عنصر وسمات minMatches و maxMatches]

في عنصر `Pattern` ما، يتم `IdMatch` `Match` ضم كل العناصر وعامل تشغيل AND ضمني. بعبارة أخرى، يجب أن تكون جميع المطابقات راضية قبل أن يكون النمط راضيا.

يمكنك إنشاء منطق مطابقة أكثر مرونة باستخدام العنصر `Any` في تجميع `Match` العناصر. على سبيل المثال، يمكنك استخدام العنصر `Any` لمطابقة الكل أو بلا أو مجموعة فرعية دقيقة من العناصر `Match` الفرعية الخاصة به.

يكون `Any` العنصر اختياريا `minMatches` وسمات `maxMatches` `Match` يمكنك استخدامها لتحديد عدد العناصر الطفلة التي يجب أن يتم تلبيتها قبل مطابقة النمط. تعرف هذه السمات *عدد* `Match` العناصر، وليس عدد مثيلات الإثباتات التي تم العثور عليها للمطابقات. لتحديد الحد الأدنى لعدد المثيلات لمطابقة معينة، مثل كلمتين أساسيتين `minCount` `Match` من قائمة، استخدم السمة الخاصة بعنصر (انظر أعلاه).

### <a name="match-at-least-one-child-match-element"></a>مطابقة عنصر واحد على الأقل من عناصر مطابقة الأطفال

لتطلب حدا أدنى من العناصر `Match` فقط، يمكنك استخدام السمة `minMatches` . في الواقع، يتم `Match` ضم هذه العناصر بواسطة عامل تشغيل OR ضمني. يكون `Any` هذا العنصر راضيا إذا تم العثور على تاريخ بتنسيق الولايات المتحدة أو كلمة أساسية من أي قائمة.

```xml
<Any minMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-an-exact-subset-of-any-children-match-elements"></a>مطابقة مجموعة فرعية دقيقة لأي عناصر مطابقة للأطفال

ولطلب عدد محدد من `Match` العناصر، قم بتعيين `minMatches` القيمة `maxMatches` نفسها ونهاية لها. يتم `Any` رضا هذا العنصر فقط إذا تم العثور على تاريخ أو كلمة أساسية واحدة بالضبط. إذا كان هناك أي تطابقات أخرى، لن يكون النمط متطابقا.

```xml
<Any minMatches="1" maxMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-none-of-children-match-elements"></a>مطابقة أي من الأطفال مع العناصر متطابقة

إذا كنت تريد طلب عدم وجود دليل محدد لارضاء النمط، يمكنك تعيين كل من minMatches و maxMatches إلى 0. قد يكون هذا مفيدا إذا كان لديك قائمة كلمات أساسية أو أدلة أخرى من المرجح أن تشير إلى خطأ موجب.

على سبيل المثال، تبحث كيان "هوية الموظف" عن الكلمة الأساسية "البطاقة" لأنها قد تشير إلى "بطاقة الم ID". ومع ذلك، إذا كانت البطاقة تظهر فقط في عبارة "بطاقة الائتمان"، فمن غير المحتمل أن تعني "البطاقة" في هذا المحتوى "بطاقة الم الهوية". حتى تتمكن من إضافة "بطاقة ائتمان" ككلمة أساسية إلى قائمة الشروط التي تريد استبعادها من تلبية النمط.

```xml
<Any minMatches="0" maxMatches="0" >
    <Match idRef="Keyword_false_positives_local" />
    <Match idRef="Keyword_false_positives_intl" />
</Any>
```

### <a name="match-a-number-of-unique-terms"></a>مطابقة عدد من المصطلحات الفريدة

إذا كنت تريد مطابقة عدد من المصطلحات الفريدة، فاستخدم المعلمة *UniqueResults* ، التي تم تعيينها إلى *true*، كما هو موضح في المثال التالي:

```xml
<Pattern confidenceLevel="75">
    <IdMatch idRef="Salary_Revision_terms" />
    <Match idRef=" Salary_Revision_ID " minCount="3" uniqueResults="true" />
</Pattern>
```

في هذا المثال، يتم تعريف نمط لمراجعة الرواتب باستخدام ثلاث تطابقات فريدة على الأقل.

## <a name="how-close-to-the-entity-must-the-other-evidence-be-patternsproximity-attribute"></a>ما مدى قرب الكيان من الدليل الآخر؟ [patternsProximity attribute]

يبحث نوع المعلومات الحساسة عن نمط يمثل "معرِّف الموظف"، وكجزء من هذا النمط، يبحث أيضا عن أدلة معززة مثل كلمة أساسية مثل "الم ID". من المنطقي أنه كلما اقترب هذا الدليل من بعضهما البعض، فمن المرجح أن يكون النمط هو الملهم الفعلي للموظف. يمكنك تحديد مدى قرب الدليل الآخر في النمط للكيان باستخدام السمة النقوش المطلوبة الخاصة بProximity الخاصة العنصر كيان.

![علامات XML تعرض النقوش سمةProximity.](../media/e97eb7dc-b897-4e11-9325-91c742d9839b.png)

لكل نمط في الكيان، تحدد قيمة سمة النقوشProximity المسافة (في أحرف Unicode) من موقع IdMatch لكل التطابقات الأخرى المحددة لهذا النمط. يتم إرساء نافذة التقارب بواسطة موقع IdMatch، مع توسيع النافذة إلى يسار IdMatch ويساره.

![رسم تخطيطي للنافذة القريبة.](../media/b593dfd1-5eef-4d79-8726-a28923f7c31e.png)

يوضح المثال أدناه كيفية تأثير نافذة التقارب على النمط المطابق حيث يتطلب عنصر IdMatch للكيان المخصص لمعرف الموظف تطابقا واحدا على الأقل للكلمة الأساسية أو التاريخ. يتطابق الم ID1 فقط لأنه بالنسبة ل ID2 و ID3، لا يمكن العثور على أي من إثباتات التكاتف الجزئية أو فقط ضمن نافذة التقارب.

![رسم تخطيطي للدلليل المتكاتف ونافذة التقارب.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

لاحظ أنه بالنسبة للبريد الإلكتروني، يتم التعامل مع نص الرسالة وكل مرفق كعنصرين منفصلين. وهذا يعني أن نافذة التقارب لا تمتد إلى ما بعد نهاية كل عنصر من هذه العناصر. لكل عنصر (مرفق أو هيئة)، يجب أن يتواجد كل من idMatch ودلليل الإثبات في ذلك العنصر.

## <a name="what-are-the-right-confidence-levels-for-different-patterns-confidencelevel-attribute-recommendedconfidence-attribute"></a>ما هي مستويات الثقة الصحيحة للأنماط المختلفة؟ [confidenceLevel سمة، سمةConfidence الموصى بها]

كلما كان النمط يتطلب المزيد من الأدلة، كانت الثقة أكبر في تحديد كيان فعلي (مثل معرف الموظف) عند تطابق النمط. على سبيل المثال، لديك ثقة أكبر في نمط يتطلب رقما من تسعة أرقام للمعين وتاريخ توظيف وكلمة أساسية في مكان قريب، أكثر مما هو عليه في نمط يتطلب رقما من تسعة أرقام فقط.

عنصر النمط له سمة الثقة المطلوبة يمكنك التفكير في قيمة confidenceLevel (وهي عدد صحيح بين 1 و100) كمعريف فريد لكل نمط في كيان — يجب أن يكون للأنماط في كيان مستويات ثقة مختلفة تقوم بتعيينها. لا تهم القيمة الدقيقة للقيمة العدد صحيح ، ما عليك سوى اختيار الأرقام التي تكون ذات معنى لفريق التوافق. بعد تحميل نوع المعلومات الحساسة المخصص ثم إنشاء نهج، يمكنك الإشارة إلى مستويات الثقة هذه في شروط القواعد التي تنشئها.

![علامات XML تعرض عناصر النمط مع قيم مختلفة للنسبة confidenceLevel.](../media/sit-xml-markedup-2.png)

بالإضافة إلى confidenceLevel لكل نمط، يحتوي الكيان على سمةConfidence موصى بها. يمكن التفكير في سمة الثقة الموصى بها كمستوى الثقة الافتراضي للقاعدة. عند إنشاء قاعدة في نهج، إذا لم تحدد مستوى ثقة للقاعدة لاستخدامها، ستتطابق هذه القاعدة استنادا إلى مستوى الثقة الموصى به للكيان. تجدر الإشارة إلى أن السمة "Confidence" الموصى بها إلزامية لكل "المرجع الكياني" في "حزمة القواعد"، إذا لم تكن مفقودة، فلن تتمكن من حفظ النهج التي تستخدم نوع المعلومات الحساسة.

## <a name="do-you-want-to-support-other-languages-in-the-ui-of-the-compliance-center-localizedstrings-element"></a>هل تريد دعم لغات أخرى في واجهة مستخدم مركز التوافق؟ [عنصر LocalizedStrings]

إذا كان فريق التوافق يستخدم Microsoft 365 التوافق لإنشاء سياسات بلغات محلية مختلفة ولغات مختلفة، يمكنك توفير إصدارات محلية من اسم ووصف نوع المعلومات الحساسة المخصص. عندما يستخدم فريق التوافق Microsoft 365 بلغة تدعمها، سيشاهدون الاسم المعرف في واجهة المستخدم.

![عدد المثيلات ومطابقة تكوين الدقة.](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

يجب أن يحتوي عنصر القواعد على عنصر LocalizedStrings، الذي يحتوي على عنصر Resource يشير إلى GUID للكيان المخصص. في المقابل، يحتوي كل عنصر مورد على عنصر واحد أو أكثر من عناصر الاسم والوصف التي يستخدم كل منها السمة langcode لتوفير سلسلة معرَّمة للغة معينة.

![علامات XML تعرض محتويات عنصر LocalizedStrings.](../media/a96fc34a-b93d-498f-8b92-285b16a7bbe6.png)

تجدر الإشارة إلى أنك تستخدم السلاسل المعرفه فقط لكيفية ظهور نوع المعلومات الحساسة المخصصة في واجهة المستخدم الخاصة بمركز التوافق. لا يمكنك استخدام السلاسل المحلية لتوفير إصدارات مختلفة معنيه من قائمة الكلمات الأساسية أو التعبير العادي.

## <a name="other-rule-package-markup-rulepack-guid"></a>علامات حزمة قواعد أخرى [RulePack GUID]

وأخيرا، تحتوي بداية كل RulePackage على بعض المعلومات العامة التي تحتاج إلى تعبئتها. يمكنك استخدام العلامات التالية كقالب واستبدال . . ." عنصر نائب مع معلوماتك الخاصة.

والأهم من ذلك، ستحتاج إلى إنشاء GUID ل RulePack. أعلاه، قمت بتوليد GUID للكيان؛ هذا هو GUID ثان ل RulePack. هناك عدة طرق لإنشاء GUIDs، ولكن يمكنك القيام بذلك بسهولة في PowerShell عن طريق كتابة [guid]::NewGuid().

عنصر الإصدار مهم أيضا. عند تحميل حزمة القواعد للمرة الأولى، Microsoft 365 على رقم الإصدار. في وقت لاحق، إذا قمت بتحديث حزمة القواعد وتحميل إصدار جديد، فتأكد من تحديث رقم الإصدار أو Microsoft 365 لن تنشر حزمة القاعدة.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
  <RulePack id=". . .">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id=". . ." />
    <Details defaultLangCode=". . .">
      <LocalizedDetails langcode=" . . . ">
         <PublisherName>. . .</PublisherName>
         <Name>. . .</Name>
         <Description>. . .</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
  . . .
 </Rules>
</RulePackage>
```

عند الانتهاء، يجب أن يبدو عنصر RulePack كما هو.

![علامات XML تعرض عنصر RulePack.](../media/fd0f31a7-c3ee-43cd-a71b-6a3813b21155.png)

## <a name="validators"></a>مثبتات

Microsoft 365 المعالجات الدالة ل SITs شائعة استخدامها كتحقق من صحة. إليك قائمة بها.

### <a name="list-of-currently-available-validators"></a>قائمة بالتحقق من صحة المعلومات المتوفرة حاليا

- `Func_credit_card`
- `Func_ssn`
- `Func_unformatted_ssn`
- `Func_randomized_formatted_ssn`
- `Func_randomized_unformatted_ssn`
- `Func_aba_routing`
- `Func_south_africa_identification_number`
- `Func_brazil_cpf`
- `Func_iban`
- `Func_brazil_cnpj`
- `Func_swedish_national_identifier`
- `Func_india_aadhaar`
- `Func_uk_nhs_number`
- `Func_Turkish_National_Id`
- `Func_australian_tax_file_number`
- `Func_usa_uk_passport`
- `Func_canadian_sin`
- `Func_formatted_itin`
- `Func_unformatted_itin`
- `Func_dea_number_v2`
- `Func_dea_number`
- `Func_japanese_my_number_personal`
- `Func_japanese_my_number_corporate`

يمنحك ذلك القدرة على تعريف RegEx الخاص بك والتحقق من صحتها. لاستخدام مثبتات التحقق من صحة، حدد RegEx الخاص بك ثم استخدم `Validator` الخاصية لإضافة معالج الدالة الذي تختاره. بمجرد تعريفه، يمكنك استخدام RegEx هذا في SIT.

في المثال أدناه، تعبير عادي - Regex_credit_card_AdditionalDelimiters بطاقة الائتمان، التي يتم التحقق من صحتها بعد ذلك باستخدام دالة الاختبارات لبطاقة الائتمان باستخدام Func_credit_card كتحقق من صحة.

```xml
<Regex id="Regex_credit_card_AdditionalDelimiters" validators="Func_credit_card"> (?:^|[\s,;\:\(\)\[\]"'])([0-9]{4}[ -_][0-9]{4}[ -_][0-9]{4}[ -_][0-9]{4})(?:$|[\s,;\:\(\)\[\]"'])</Regex>
<Entity id="675634eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
<Pattern confidenceLevel="85">
<IdMatch idRef="Regex_credit_card_AdditionalDelimiters" />
<Any minMatches="1">
<Match idRef="Keyword_cc_verification" />
<Match idRef="Keyword_cc_name" />
<Match idRef="Func_expiration_date" />
</Any>
</Pattern>
</Entity>
```

Microsoft 365 اثنين من التحقق من صحة عامة

### <a name="checksum-validator"></a>أداة التحقق من صحة الاختبارات

في هذا المثال، يتم تعريف أداة التحقق من صحة التحقق لمعرف الموظف للتحقق من صحة RegEx for EmployeeID.

```xml
<Validators id="EmployeeIDChecksumValidator">
<Validator type="Checksum">
<Param name="Weights">2, 2, 2, 2, 2, 1</Param>
<Param name="Mod">28</Param>
<Param name="CheckDigit">2</Param> <!-- Check 2nd digit -->
<Param name="AllowAlphabets">1</Param> <!— 0 if no Alphabets -->
</Validator>
</Validators>
<Regex id="Regex_EmployeeID" validators="ChecksumValidator">(\d{5}[A-Z])</Regex>
<Entity id="675634eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
<Pattern confidenceLevel="85">
<IdMatch idRef="Regex_EmployeeID"/>
</Pattern>
</Entity>
```

### <a name="date-validator"></a>مثبت التاريخ

في هذا المثال، يتم تعريف أداة التحقق من صحة التاريخ لجزء RegEx الذي هو تاريخ.

```xml
<Validators id="date_validator_1"> <Validator type="DateSimple"> <Param name="Pattern">DDMMYYYY</Param> <!—supported patterns DDMMYYYY, MMDDYYYY, YYYYDDMM, YYYYMMDD, DDMMYYYY, DDMMYY, MMDDYY, YYDDMM, YYMMDD --> </Validator> </Validators>
<Regex id="date_regex_1" validators="date_validator_1">\d{8}</Regex>
```

## <a name="changes-for-exchange-online"></a>التغييرات Exchange Online

في السابق، ربما استخدمت Exchange Online PowerShell لاستيراد أنواع المعلومات الحساسة المخصصة ل DLP. يمكن الآن استخدام أنواع المعلومات الحساسة المخصصة في كل من Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز</a> الإدارة ومركز التوافق. كجزء من هذا التحسين، يجب استخدام مركز التوافق PowerShell لاستيراد أنواع المعلومات الحساسة المخصصة — لا يمكنك استيرادها من Exchange PowerShell بعد الآن. ستستمر أنواع المعلومات الحساسة المخصصة في العمل كما كان من قبل؛ ومع ذلك، قد يستغرق ظهور التغييرات التي تم إدخالها على أنواع المعلومات الحساسة المخصصة في مركز التوافق في مركز إدارة Exchange ما يصل إلى ساعة واحدة.

تجدر الإشارة إلى أنك تستخدم في مركز التوافق **[الأمر cmdlet New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage)** لتحميل حزمة قاعدة. (سابقا، في مركز إدارة Exchange، كنت تستخدم **cmdlet الخاص ب ClassificationRuleCollection**.)

## <a name="upload-your-rule-package"></a>Upload حزمة القواعد

لتحميل حزمة القواعد، قم بالخطوات التالية:

1. احفظه كملف .xml ترميز Unicode.

2. [الاتصال مركز التوافق في PowerShell](/powershell/exchange/exchange-online-powershell)

3. استخدم بناء الجملة التالي:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('PathToUnicodeXMLFile'))
   ```

   يحمل هذا المثال ملف Unicode XML MyNewRulePack.xml من C:\My Documents.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\MyNewRulePack.xml'))
   ```

   للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage).

   > [!NOTE]
   > إن الحد الأقصى لعدد حزم القواعد المعتمدة هو 10 حزم، ولكن يمكن أن تحتوي كل حزمة على تعريف لأنواع معلومات حساسة متعددة.

4. للتحقق من أنك قمت بإنشاء نوع معلومات حساس جديد بنجاح، قم بأي من الخطوات التالية:

   - تشغيل [الأمر cmdlet Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) للتحقق من إدراج حزمة القاعدة الجديدة:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - تشغيل [الأمر Cmdlet Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) للتحقق من إدراج نوع المعلومات الحساسة:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     بالنسبة لأنواع المعلومات الحساسة المخصصة، ستكون Publisher الخاصية شيء آخر غير Microsoft Corporation.

   - استبدل \<Name\> بقيمة الاسم لنوع المعلومات الحساسة (على سبيل المثال: "معلومات الموظف") ثم ابدل [cmdlet Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) :

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="potential-validation-issues-to-be-aware-of"></a>مشاكل التحقق من الصحة المحتملة التي يجب أن تكون على علم بها

عند تحميل ملف XML لحزمة القواعد، يتحقق النظام من صحة XML ويتحقق من الأنماط السيئة المعروفة وملفات الأداء الواضحة. فيما يلي بعض المشاكل المعروفة التي يتحقق منها التحقق من الصحة — تعبير عادي:

- يجب أن تكون تأكيدات Lookbehind في التعبير العادي ذات طول ثابت فقط. ستنتج عن تأكيدات الطول المتغير أخطاء.

  على سبيل المثال، `"(?<=^|\s|_)"` لن يجتاز التحقق من الصحة. النمط الأول (`^`) هو طول صفري، بينما يكون طول النمطين التاليين ( `_``\s` و ) واحدا. هناك طريقة بديلة لكتابة هذا التعبير العادي وهي `"(?:^|(?<=\s|_))"`.

- لا يمكن البدء أو الانتهاء بالمبدل `|`، الذي يتطابق مع كل شيء لأنه يعتبر تطابقا فارغا.

  على سبيل المثال، `|a` أو `b|` لن يجتاز التحقق من الصحة.

- لا يمكن أن يبدأ نمطا `.{0,m}` أو ينتهي به، وليس له أي غرض وظيفي ويضعف الأداء فقط.

  على سبيل المثال، `.{0,50}ASDF` أو `ASDF.{0,50}` لن يجتاز التحقق من الصحة.

- لا يمكن أن `.{0,m}` يكون لديك أو `.{1,m}` في مجموعات، ولا يمكن أن يكون لها `.\*` أو `.+` في مجموعات.

  على سبيل المثال، `(.{0,50000})` لن يجتاز التحقق من الصحة.

- لا يمكن أن يكون هناك أي حرف مع `{0,m}` أو `{1,m}` مكررات في المجموعات.

  على سبيل المثال، `(a\*)` لن يجتاز التحقق من الصحة.

- لا يمكن أن يبدأ أو ينتهي ب `.{1,m}`; بدلا من ذلك، استخدم `.`.

  على سبيل المثال، `.{1,m}asdf` لن يجتاز التحقق من الصحة. بدلا من ذلك، استخدم `.asdf`.

- لا يمكن أن يكون هناك مكرر غير منضم (مثل `*` أو `+`) في مجموعة.

  على سبيل المثال، `(xx)\*` ولن `(xx)+` يجتاز التحقق من الصحة.

- الكلمات الأساسية بحد أقصى 50 حرفا في الطول.  إذا كانت لديك كلمة أساسية ضمن مجموعة تتجاوز هذه الكلمة، فإن الحل المقترح هو إنشاء مجموعة المصطلحات كقاموس الكلمة الأساسية والإشارة إلى GUID الخاص بقاموس الكلمات الأساسية ضمن بنية XML كجزء من كيان مطابقة أو idMatch في الملف.[](./create-a-keyword-dictionary.md)

- يمكن أن يحتوي كل نوع من أنواع المعلومات الحساسة المخصصة على إجمالي 2048 كلمة أساسية كحد أقصى.

- الحد الأقصى لحجم قواميس الكلمات الأساسية في مستأجر واحد هو 480 كيلوB مضغوطة لتتوافق مع حدود مخطط AD. ارجع إلى القاموس نفسه قدر ما يلزم عند إنشاء أنواع معلومات حساسة مخصصة. ابدأ بإنشاء قوائم الكلمات الأساسية المخصصة في نوع المعلومات الحساسة واستخدام قواميس الكلمات الأساسية إذا كان لديك أكثر من 2048 كلمة أساسية في قائمة الكلمات الأساسية أو إذا كان طول كلمة أساسية أكبر من 50 حرفا.

- يسمح للمستأجر ب 50 نوعا من أنواع المعلومات الحساسة المستندة إلى قاموس الكلمات الأساسية كحد أقصى.

- تأكد من أن كل عنصر كيان يحتوي على سمةConfidence موصى بها.

- عند استخدام الأمر PowerShell Cmdlet، يوجد حد أقصى لحجم إرجاع البيانات غير المهينة التي تبلغ 1 ميغابايت تقريبا.   سيؤثر ذلك على حجم ملف XML لحزمة القواعد. احتفظ بالملف الذي تم تحميله بحد أقصى 770 كيلوبايت كحد اقتراح للحصول على نتائج متناسقة دون أخطاء عند المعالجة.

- لا تتطلب بنية XML أحرف تنسيق مثل المسافات أو علامات التبويب أو إدخالات أحرف الإرجاع/السطر.  لاحظ ذلك عند تحسين المساحة على عمليات التحميل. توفر أدوات مثل Microsoft Visual Code ميزات خط الضم لضغط ملف XML.

إذا احتوى نوع معلومات مخصص حساس على مشكلة قد تؤثر على الأداء، فلن يتم تحميله وقد ترى إحدى رسائل الخطأ هذه:

- `Generic quantifiers which match more content than expected (e.g., '+', '*')`

- `Lookaround assertions`

- `Complex grouping in conjunction with general quantifiers`

## <a name="recrawl-your-content-to-identify-the-sensitive-information"></a>إعادة تعيين المحتوى لتحديد المعلومات الحساسة

Microsoft 365 متتبع ارتباطات البحث لتعريف المعلومات الحساسة وتصنيفها في محتوى الموقع. يتم إعادة SharePoint مواقع الويب OneDrive for Business أو الإنترنت تلقائيا كلما تم تحديثها. ولكن لتحديد نوع المعلومات الحساسة المخصص الجديد في كل المحتويات الموجودة، يجب إعادة تعيين هذا المحتوى.

في Microsoft 365، لا يمكنك طلب إعادة تجميع مؤسسة بأكملها يدويا، ولكن يمكنك طلب إعادة فرز مجموعة مواقع أو قائمة أو مكتبة يدويا. لمزيد من المعلومات، راجع طلب تتبع ارتباطات موقع أو مكتبة أو [قائمة وإعادة ترابطها يدويا](/sharepoint/crawl-site-content).

## <a name="reference-rule-package-xml-schema-definition"></a>المرجع: تعريف مخطط XML لحزمة القاعدة

يمكنك نسخ هذه العلامات وحفظها كملف XSD واستخدامها للتحقق من صحة ملف XML لحزمة القواعد.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:mce="http://schemas.microsoft.com/office/2011/mce"
           targetNamespace="http://schemas.microsoft.com/office/2011/mce"
           xmlns:xs="https://www.w3.org/2001/XMLSchema"
           elementFormDefault="qualified"
           attributeFormDefault="unqualified"
           id="RulePackageSchema">
  <!-- Use include if this schema has the same target namespace as the schema being referenced, otherwise use import -->
  <xs:element name="RulePackage" type="mce:RulePackageType"/>
  <xs:simpleType name="LangType">
    <xs:union memberTypes="xs:language">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value=""/>
        </xs:restriction>
      </xs:simpleType>
    </xs:union>
  </xs:simpleType>
  <xs:simpleType name="GuidType" final="#all">
    <xs:restriction base="xs:token">
      <xs:pattern value="[0-9a-fA-F]{8}\-([0-9a-fA-F]{4}\-){3}[0-9a-fA-F]{12}"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="RulePackageType">
    <xs:sequence>
      <xs:element name="RulePack" type="mce:RulePackType"/>
      <xs:element name="Rules" type="mce:RulesType">
        <xs:key name="UniqueRuleId">
          <xs:selector xpath="mce:Entity|mce:Affinity|mce:Version/mce:Entity|mce:Version/mce:Affinity"/>
          <xs:field xpath="@id"/>
        </xs:key>
        <xs:key name="UniqueProcessorId">
          <xs:selector xpath="mce:Regex|mce:Keyword|mce:Fingerprint"></xs:selector>
          <xs:field xpath="@id"/>
        </xs:key>
        <xs:key name="UniqueResourceIdRef">
          <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
          <xs:field xpath="@idRef"/>
        </xs:key>
        <xs:keyref name="ReferencedRuleMustExist" refer="mce:UniqueRuleId">
          <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
          <xs:field xpath="@idRef"/>
        </xs:keyref>
        <xs:keyref name="RuleMustHaveResource" refer="mce:UniqueResourceIdRef">
          <xs:selector xpath="mce:Entity|mce:Affinity|mce:Version/mce:Entity|mce:Version/mce:Affinity"/>
          <xs:field xpath="@id"/>
        </xs:keyref>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="RulePackType">
    <xs:sequence>
      <xs:element name="Version" type="mce:VersionType"/>
      <xs:element name="Publisher" type="mce:PublisherType"/>
      <xs:element name="Details" type="mce:DetailsType">
        <xs:key name="UniqueLangCodeInLocalizedDetails">
          <xs:selector xpath="mce:LocalizedDetails"/>
          <xs:field xpath="@langcode"/>
        </xs:key>
        <xs:keyref name="DefaultLangCodeMustExist" refer="mce:UniqueLangCodeInLocalizedDetails">
          <xs:selector xpath="."/>
          <xs:field xpath="@defaultLangCode"/>
        </xs:keyref>
      </xs:element>
      <xs:element name="Encryption" type="mce:EncryptionType" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="VersionType">
    <xs:attribute name="major" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="minor" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="build" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="revision" type="xs:unsignedShort" use="required"/>
  </xs:complexType>
  <xs:complexType name="PublisherType">
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="LocalizedDetailsType">
    <xs:sequence>
      <xs:element name="PublisherName" type="mce:NameType"/>
      <xs:element name="Name" type="mce:RulePackNameType"/>
      <xs:element name="Description" type="mce:OptionalNameType"/>
    </xs:sequence>
    <xs:attribute name="langcode" type="mce:LangType" use="required"/>
  </xs:complexType>
  <xs:complexType name="DetailsType">
    <xs:sequence>
      <xs:element name="LocalizedDetails" type="mce:LocalizedDetailsType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="defaultLangCode" type="mce:LangType" use="required"/>
  </xs:complexType>
  <xs:complexType name="EncryptionType">
    <xs:sequence>
      <xs:element name="Key" type="xs:normalizedString"/>
      <xs:element name="IV" type="xs:normalizedString"/>
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="RulePackNameType">
    <xs:restriction base="xs:token">
      <xs:minLength value="1"/>
      <xs:maxLength value="64"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="NameType">
    <xs:restriction base="xs:normalizedString">
      <xs:minLength value="1"/>
      <xs:maxLength value="256"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="OptionalNameType">
    <xs:restriction base="xs:normalizedString">
      <xs:minLength value="0"/>
      <xs:maxLength value="256"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="RestrictedTermType">
    <xs:restriction base="xs:string">
      <xs:minLength value="1"/>
      <xs:maxLength value="100"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="RulesType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Entity" type="mce:EntityType"/>
        <xs:element name="Affinity" type="mce:AffinityType"/>
        <xs:element name="Version" type="mce:VersionedRuleType"/>
      </xs:choice>
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Regex" type="mce:RegexType"/>
        <xs:element name="Keyword" type="mce:KeywordType"/>
        <xs:element name="Fingerprint" type="mce:FingerprintType"/>
        <xs:element name="ExtendedKeyword" type="mce:ExtendedKeywordType"/>
      </xs:choice>
      <xs:element name="LocalizedStrings" type="mce:LocalizedStringsType"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="EntityType">
    <xs:sequence>
      <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
      <xs:element name="Version" type="mce:VersionedPatternType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
    <xs:attribute name="patternsProximity" type="mce:ProximityType" use="required"/>
    <xs:attribute name="recommendedConfidence" type="mce:ProbabilityType"/>
    <xs:attribute name="workload" type="mce:WorkloadType"/>
  </xs:complexType>
  <xs:complexType name="PatternType">
    <xs:sequence>
      <xs:element name="IdMatch" type="mce:IdMatchType"/>
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
  </xs:complexType>
  <xs:complexType name="AffinityType">
    <xs:sequence>
      <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
      <xs:element name="Version" type="mce:VersionedEvidenceType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
    <xs:attribute name="evidencesProximity" type="mce:ProximityType" use="required"/>
    <xs:attribute name="thresholdConfidenceLevel" type="mce:ProbabilityType" use="required"/>
    <xs:attribute name="workload" type="mce:WorkloadType"/>
  </xs:complexType>
  <xs:complexType name="EvidenceType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
  </xs:complexType>
  <xs:complexType name="IdMatchType">
    <xs:attribute name="idRef" type="xs:string" use="required"/>
  </xs:complexType>
  <xs:complexType name="MatchType">
    <xs:attribute name="idRef" type="xs:string" use="required"/>
    <xs:attribute name="minCount" type="xs:positiveInteger" use="optional"/>
    <xs:attribute name="uniqueResults" type="xs:boolean" use="optional"/>
  </xs:complexType>
  <xs:complexType name="AnyType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="minMatches" type="xs:nonNegativeInteger" default="1"/>
    <xs:attribute name="maxMatches" type="xs:nonNegativeInteger" use="optional"/>
  </xs:complexType>
  <xs:simpleType name="ProximityType">
    <xs:union>
      <xs:simpleType>
        <xs:restriction base='xs:string'>
          <xs:enumeration value="unlimited"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType>
        <xs:restriction base="xs:positiveInteger">
          <xs:minInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:union>
  </xs:simpleType>
  <xs:simpleType name="ProbabilityType">
    <xs:restriction base="xs:integer">
      <xs:minInclusive value="1"/>
      <xs:maxInclusive value="100"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="WorkloadType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Exchange"/>
      <xs:enumeration value="Outlook"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="EngineVersionType">
    <xs:restriction base="xs:token">
      <xs:pattern value="^\d{2}\.01?\.\d{3,4}\.\d{1,3}$"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="VersionedRuleType">
    <xs:choice maxOccurs="unbounded">
      <xs:element name="Entity" type="mce:EntityType"/>
      <xs:element name="Affinity" type="mce:AffinityType"/>
    </xs:choice>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:complexType name="VersionedPatternType">
    <xs:sequence>
      <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:complexType name="VersionedEvidenceType">
    <xs:sequence>
      <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:simpleType name="FingerprintValueType">
    <xs:restriction base="xs:string">
      <xs:minLength value="2732"/>
      <xs:maxLength value="2732"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FingerprintType">
    <xs:simpleContent>
      <xs:extension base="mce:FingerprintValueType">
        <xs:attribute name="id" type="xs:token" use="required"/>
        <xs:attribute name="threshold" type="mce:ProbabilityType" use="required"/>
        <xs:attribute name="shingleCount" type="xs:positiveInteger" use="required"/>
        <xs:attribute name="description" type="xs:string" use="optional"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="RegexType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="KeywordType">
    <xs:sequence>
      <xs:element name="Group" type="mce:GroupType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="id" type="xs:token" use="required"/>
  </xs:complexType>
  <xs:complexType name="GroupType">
    <xs:sequence>
      <xs:choice>
        <xs:element name="Term" type="mce:TermType" maxOccurs="unbounded"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="matchStyle" default="word">
      <xs:simpleType>
        <xs:restriction base="xs:NMTOKEN">
          <xs:enumeration value="word"/>
          <xs:enumeration value="string"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
  <xs:complexType name="TermType">
    <xs:simpleContent>
      <xs:extension base="mce:RestrictedTermType">
        <xs:attribute name="caseSensitive" type="xs:boolean" default="false"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="ExtendedKeywordType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="LocalizedStringsType">
    <xs:sequence>
      <xs:element name="Resource" type="mce:ResourceType" maxOccurs="unbounded">
      <xs:key name="UniqueLangCodeUsedInNamePerResource">
        <xs:selector xpath="mce:Name"/>
        <xs:field xpath="@langcode"/>
      </xs:key>
      <xs:key name="UniqueLangCodeUsedInDescriptionPerResource">
        <xs:selector xpath="mce:Description"/>
        <xs:field xpath="@langcode"/>
      </xs:key>
    </xs:element>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="ResourceType">
    <xs:sequence>
      <xs:element name="Name" type="mce:ResourceNameType" maxOccurs="unbounded"/>
      <xs:element name="Description" type="mce:DescriptionType" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="idRef" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="ResourceNameType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="default" type="xs:boolean" default="false"/>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="DescriptionType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="default" type="xs:boolean" default="false"/>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
</xs:schema>
```

## <a name="more-information"></a>معلومات إضافية

- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [دالات نوع المعلومات الحساسة](sit-functions.md)
