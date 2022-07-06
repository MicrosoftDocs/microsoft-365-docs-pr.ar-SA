---
title: إنشاء نوع معلومات حساسة مخصص باستخدام PowerShell
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
description: تعرف على كيفية إنشاء نوع معلومات حساسة مخصص واستيراده للنهج في مركز التوافق.
ms.openlocfilehash: b71893afad2d68f9820f23e60ae9c3b15531f976
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625578"
---
# <a name="create-a-custom-sensitive-information-type-using-powershell"></a>إنشاء نوع معلومات حساسة مخصص باستخدام PowerShell

توضح لك هذه المقالة كيفية إنشاء ملف *حزمة قاعدة* XML الذي يعرف [أنواع المعلومات الحساسة](sensitive-information-type-entity-definitions.md) المخصصة. تصف هذه المقالة نوع معلومات حساسة مخصص يعرف معرف الموظف. يمكنك استخدام نموذج XML في هذه المقالة كنقطة بداية لملف XML الخاص بك.

لمزيد من المعلومات حول أنواع المعلومات الحساسة، راجع [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md).

بعد إنشاء ملف XML بشكل جيد، يمكنك تحميله إلى Microsoft 365 باستخدام PowerShell. بعد ذلك، أنت مستعد لاستخدام نوع المعلومات الحساسة المخصصة في النهج. يمكنك اختبار فعاليتها في الكشف عن المعلومات الحساسة كما أردت.

> [!NOTE]
> إذا لم تكن بحاجة إلى عنصر التحكم الدقيق الذي يوفره PowerShell، يمكنك إنشاء أنواع معلومات حساسة مخصصة في مدخل التوافق في Microsoft Purview. لمزيد من المعلومات، راجع [إنشاء نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type.md).

## <a name="important-disclaimer"></a>إخلاء مسؤولية مهم

لا يمكن أن يساعدك دعم Microsoft في إنشاء تعريفات مطابقة المحتوى.

للتطوير والاختبار وتصحيح الأخطاء المخصصة لمطابقة المحتوى، ستحتاج إلى استخدام موارد تكنولوجيا المعلومات الداخلية الخاصة بك، أو استخدام الخدمات الاستشارية، مثل خدمات Microsoft Consulting Services (MCS). يمكن لمهندسي دعم Microsoft توفير دعم محدود لهذه الميزة، ولكن لا يمكنهم ضمان تلبية اقتراحات مطابقة المحتوى المخصصة لاحتياجاتك بشكل كامل.

يمكن أن توفر MCS تعبيرات منتظمة لأغراض الاختبار. يمكنهم أيضا تقديم المساعدة في استكشاف أخطاء نمط RegEx الموجود وإصلاحها الذي لا يعمل كما هو متوقع مع مثال محتوى محدد واحد.

راجع [مشاكل التحقق من الصحة المحتملة التي يجب أن تكون على علم بها في هذه المقالة](#potential-validation-issues-to-be-aware-of) .

لمزيد من المعلومات حول محرك Boost.RegEx (المعروف سابقا باسم RegEx++) المستخدم لمعالجة النص، راجع [Boost.Regex 5.1.3](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/).

> [!NOTE]
> إذا كنت تستخدم حرف علامة العطف (&) كجزء من كلمة أساسية في نوع المعلومات الحساسة المخصصة، فستحتاج إلى إضافة مصطلح إضافي يحتوي على مسافات حول الحرف. على سبيل المثال، _لا_ `L&P`تستخدم `L & P` .

## <a name="sample-xml-of-a-rule-package"></a>نموذج XML لحزمة قاعدة

فيما يلي نموذج XML لحزمة القواعد التي سنقوم بإنشائها في هذه المقالة. يتم شرح العناصر والسمات في الأقسام أدناه.

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

## <a name="what-are-your-key-requirements-rule-entity-pattern-elements"></a>ما هي متطلباتك الرئيسية؟ [القاعدة، الوحدة، عناصر النمط]

من المهم أن تفهم البنية الأساسية لمخطط XML لقاعدة. سيساعد فهمك للبنية نوع المعلومات الحساسة المخصصة على تحديد المحتوى الصحيح.

تعرف القاعدة كيانا واحدا أو أكثر (المعروف أيضا بأنواع المعلومات الحساسة). يحدد كل كيان نمطا واحدا أو أكثر. النمط هو ما يبحث عنه النهج عند تقييم المحتوى (على سبيل المثال، البريد الإلكتروني والمستندات).

في علامات XML، تعني "القواعد" الأنماط التي تحدد نوع المعلومات الحساسة. لا تربط المراجع بالقواعد الواردة في هذه المقالة ب "الشروط" أو "الإجراءات" الشائعة في ميزات Microsoft الأخرى.

### <a name="simplest-scenario-entity-with-one-pattern"></a>أبسط سيناريو: كيان بنمط واحد

إليك سيناريو بسيط: تريد أن يحدد نهجك المحتوى الذي يحتوي على معرفات الموظفين المكونة من تسعة أرقام المستخدمة في مؤسستك. يشير النمط إلى التعبير العادي في القاعدة التي تعرف الأرقام المكونة من تسعة أرقام. أي محتوى يحتوي على رقم مكون من تسعة أرقام يفي بالنمط.

![رسم تخطيطي للكيان بنمط واحد.](../media/4cc82dcf-068f-43ff-99b2-bac3892e9819.png)

ولكن، قد يحدد هذا النمط **أي** رقم مكون من تسعة أرقام، بما في ذلك أرقام أطول أو أنواع أخرى من الأرقام المكونة من تسعة أرقام ليست معرفات موظفين. يعرف هذا النوع من التطابق غير المرغوب فيه بأنه *إيجابي خطأ*.

### <a name="more-common-scenario-entity-with-multiple-patterns"></a>سيناريو أكثر شيوعا: كيان ذو أنماط متعددة

نظرا لاحتمال وجود إيجابيات خاطئة، عادة ما تستخدم أكثر من نمط واحد لتعريف كيان. توفر الأنماط المتعددة دليلا داعما للكيان المستهدف. على سبيل المثال، يمكن أن تساعد الكلمات الأساسية أو التواريخ أو النصوص الأخرى الإضافية في تحديد الكيان الأصلي (على سبيل المثال، رقم الموظف المكون من تسعة أرقام).

على سبيل المثال، لزيادة احتمالية تحديد المحتوى الذي يحتوي على معرف موظف، يمكنك تعريف أنماط أخرى للبحث عنها:

- نمط يحدد تاريخ التوظيف.
- نمط يحدد كل من تاريخ التوظيف والكلمة الأساسية "معرف الموظف".

![رسم تخطيطي للكيان بأنماط متعددة.](../media/c8dc2c9d-00c6-4ebc-889a-53b41a90024a.png)

هناك نقاط هامة يجب أخذها في الاعتبار لمطابقات الأنماط المتعددة:

- الأنماط التي تتطلب المزيد من الأدلة لها مستوى ثقة أعلى. استنادا إلى مستوى الثقة، يمكنك اتخاذ الإجراءات التالية:
  - استخدم إجراءات أكثر تقييدا (مثل محتوى الحظر) مع تطابقات ثقة أعلى.
  - استخدم إجراءات أقل تقييدا (مثل إرسال إعلامات) مع تطابقات أقل ثقة.

- يشير الدعم `IdMatch` والعناصر `Match` إلى RegExes والكلمات الأساسية التي هي في الواقع توابع للعنصر`Rule`، وليس .`Pattern` تتم الإشارة إلى هذه العناصر الداعمة `Pattern`بواسطة ، ولكن يتم تضمينها في `Rule`. يعني هذا السلوك أنه يمكن الرجوع إلى تعريف واحد لعنصر دعم، مثل تعبير عادي أو قائمة كلمات أساسية، بواسطة كيانات وأنماط متعددة.

## <a name="what-entity-do-you-need-to-identify-entity-element-id-attribute"></a>ما الكيان الذي تحتاج إلى تحديده؟ [عنصر الوحدة، سمة المعرف]

الكيان هو نوع معلومات حساسة، مثل رقم بطاقة الائتمان، الذي يحتوي على نمط محدد جيدا. يحتوي كل كيان على GUID فريد كمعرفه.

### <a name="name-the-entity-and-generate-its-guid"></a>تسمية الكيان وإنشاء GUID الخاص به

1. في محرر XML الذي تختاره، أضف العناصر `Rules` والعناصر `Entity` .
2. أضف تعليقا يحتوي على اسم الكيان المخصص، مثل معرف الموظف. لاحقا، ستضيف اسم الكيان إلى قسم السلاسل المترجمة، ويظهر هذا الاسم في مركز الإدارة عند إنشاء نهج.
3. إنشاء GUID فريد للكيان الخاص بك. على سبيل المثال، في Windows PowerShell، يمكنك تشغيل الأمر`[guid]::NewGuid()`. لاحقا، ستقوم أيضا بإضافة GUID إلى قسم السلاسل المترجمة للكيان.

![تظهر علامات XML عناصر القواعد والوحدة.](../media/c46c0209-0947-44e0-ac3a-8fd5209a81aa.png)

## <a name="what-pattern-do-you-want-to-match-pattern-element-idmatch-element-regex-element"></a>ما النمط الذي تريد مطابقته؟ [عنصر النمط، عنصر IdMatch، عنصر Regex]

يحتوي النمط على قائمة بما يبحث عنه نوع المعلومات الحساسة. يمكن أن يتضمن النمط RegExes والكلمات الأساسية والوظائف المضمنة. تقوم الدالات بمهمة مثل تشغيل RegExes للبحث عن التواريخ أو العناوين. يمكن أن يكون لأنواع المعلومات الحساسة أنماط متعددة بثقة فريدة.

في الرسم التخطيطي التالي، تشير كافة الأنماط إلى نفس التعبير العادي. يبحث RegEx هذا عن رقم `(\d{9})` مكون من تسعة أرقام محاطا بمسافة `(\s) ... (\s)`بيضاء. يشار إلى هذا التعبير العادي بواسطة `IdMatch` العنصر، وهو المتطلب الشائع لكافة الأنماط التي تبحث عن كيان معرف الموظف. `IdMatch` هو المعرف الذي يحاول النمط مطابقته. `Pattern` يجب أن يحتوي العنصر على عنصر واحد `IdMatch` بالضبط.

![تظهر علامات XML عناصر نمط متعددة تشير إلى عنصر Regex واحد.](../media/8f3f497b-3b8b-4bad-9c6a-d9abf0520854.png)

تقوم مطابقة النمط بالرضا بإرجاع مستوى عدد وثقة، والذي يمكنك استخدامه في الشروط في النهج الخاص بك. عند إضافة شرط للكشف عن نوع معلومات حساسة إلى نهج، يمكنك تحرير مستوى العدد والثقة كما هو موضح في الرسم التخطيطي التالي. يتم شرح مستوى الثقة (يسمى أيضا دقة المطابقة) لاحقا في هذه المقالة.

![عدد المثيلات وخيارات الدقة المطابقة.](../media/sit-confidence-level.png)

التعبيرات العادية قوية، لذلك هناك مشكلات تحتاج إلى معرفتها. على سبيل المثال، يمكن أن يؤثر RegEx الذي يحدد الكثير من المحتوى على الأداء. لمعرفة المزيد حول هذه المشاكل، راجع [مشاكل التحقق من الصحة المحتملة لكي تكون على علم بالمقطع](#potential-validation-issues-to-be-aware-of) لاحقا في هذه المقالة.

## <a name="do-you-want-to-require-additional-evidence-match-element-mincount-attribute"></a>هل تريد طلب أدلة إضافية؟ [عنصر المطابقة، سمة minCount]

بالإضافة إلى `IdMatch`ذلك، يمكن لنمط استخدام `Match` العنصر لطلب أدلة دعم إضافية، مثل كلمة أساسية أو RegEx أو تاريخ أو عنوان.

قد يتضمن A `Pattern` عناصر متعددة `Match` :

- مباشرة في `Pattern` العنصر.
- تم دمجها باستخدام `Any` العنصر.

`Match` يتم ربط العناصر بواسطة عامل تشغيل AND ضمني. بمعنى آخر، يجب أن تكون جميع `Match` العناصر راضية حتى يتطابق النمط.

يمكنك استخدام `Any` العنصر لتقديم عوامل تشغيل AND أو OR. يتم `Any` وصف العنصر لاحقا في هذه المقالة.

يمكنك استخدام السمة الاختيارية `minCount` لتحديد عدد مثيلات المطابقة التي يجب العثور عليها لكل `Match` عنصر. على سبيل المثال، يمكنك تحديد أن النمط مستوفي فقط عند العثور على كلمتين أساسيتين على الأقل من قائمة كلمات أساسية.

![تظهر علامات XML عنصر المطابقة مع السمة minOccurs.](../media/607f6b5e-2c7d-43a5-a131-a649f122e15a.png)

### <a name="keywords-keyword-group-and-term-elements-matchstyle-and-casesensitive-attributes"></a>الكلمات الأساسية [عناصر الكلمة الأساسية والمجموعة والمصطلحات، السمات المطابقة والسمات غير الحساسة لحالة الأحرف]

كما هو موضح سابقا، غالبا ما يتطلب تحديد المعلومات الحساسة كلمات أساسية إضافية كدليل مبدئي. على سبيل المثال، بالإضافة إلى مطابقة رقم مكون من تسعة أرقام، يمكنك البحث عن كلمات مثل "بطاقة" أو "شارة" أو "معرف" باستخدام عنصر الكلمة الأساسية. `Keyword` يحتوي العنصر على سمة `ID` يمكن الرجوع إليها بواسطة عناصر متعددة `Match` في أنماط أو كيانات متعددة.

يتم تضمين الكلمات الأساسية كلقائمة من `Term` العناصر في `Group` عنصر. يحتوي `Group` العنصر على سمة `matchStyle` بقيمتين محتملتين:

- **matchStyle="word"**: تحدد مطابقة الكلمة الكلمات بالكامل محاطة بمسافة بيضاء أو محددات أخرى. يجب عليك دائما استخدام **الكلمة** ما لم تكن بحاجة إلى مطابقة أجزاء من الكلمات أو الكلمات باللغات الآسيوية.

- **matchStyle="string"**: تحدد مطابقة السلسلة السلاسل بغض النظر عما تكون محاطة به. على سبيل المثال، سيتطابق "المعرف" مع "المزايدة" و"الفكرة". استخدم `string` فقط عندما تحتاج إلى مطابقة الكلمات الآسيوية أو إذا كانت الكلمة الأساسية الخاصة بك قد تكون مضمنة في سلاسل أخرى.

وأخيرا، يمكنك استخدام سمة `caseSensitive` `Term` العنصر لتحديد أن المحتوى يجب أن يتطابق تماما مع الكلمة الأساسية، بما في ذلك الأحرف الصغيرة والأحرف الكبيرة.

![تظهر علامات XML كلمات أساسية تشير إلى عناصر المطابقة.](../media/e729ba27-dec6-46f4-9242-584c6c12fd85.png)

### <a name="regular-expressions-regex-element"></a>التعبيرات العادية [عنصر Regex]

في هذا المثال، يستخدم `IdMatch` كيان الموظف `ID` العنصر بالفعل للإشارة إلى تعبير عادي للنمط: رقم مكون من تسعة أرقام محاط بمساحة بيضاء. بالإضافة إلى ذلك، يمكن للنمط استخدام `Match` عنصر للإشارة إلى عنصر إضافي `Regex` لتحديد الأدلة القاطعة، مثل رقم مكون من خمسة أرقام أو تسعة أرقام بتنسيق رمز بريدي أمريكي.

### <a name="additional-patterns-such-as-dates-or-addresses-built-in-functions"></a>أنماط إضافية مثل التواريخ أو العناوين [الدالات المضمنة]

يمكن لأنواع المعلومات الحساسة أيضا استخدام وظائف مضمنة لتحديد الأدلة الموثقة. على سبيل المثال، تاريخ الولايات المتحدة أو تاريخ الاتحاد الأوروبي أو تاريخ انتهاء الصلاحية أو عنوان الولايات المتحدة. لا يدعم Microsoft 365 تحميل وظائفك المخصصة. ولكن، عند إنشاء نوع معلومات حساسة مخصص، يمكن للكيان الخاص بك الرجوع إلى الوظائف المضمنة.

على سبيل المثال، تحتوي شارة معرف الموظف على تاريخ توظيف، بحيث يمكن لهذا الكيان المخصص استخدام الدالة المضمنة `Func_us_date` لتحديد تاريخ بالتنسيق المستخدم عادة في الولايات المتحدة.

لمزيد من المعلومات، راجع [دالات نوع المعلومات الحساسة](sit-functions.md).

![تظهر علامات XML عنصر المطابقة الذي يشير إلى الدالة المضمنة.](../media/dac6eae3-9c52-4537-b984-f9f127cc9c33.png)

## <a name="different-combinations-of-evidence-any-element-minmatches-and-maxmatches-attributes"></a>مجموعات مختلفة من الأدلة [أي عنصر وminMatches وسمات maxMatches]

في عنصر `Pattern` ما، يتم ضم كافة `IdMatch` العناصر والعناصر `Match` بواسطة عامل تشغيل AND ضمني. بمعنى آخر، يجب أن يتم استيفاء جميع التطابقات قبل أن يمكن استيفاء النمط.

يمكنك إنشاء منطق مطابق أكثر مرونة باستخدام `Any` العنصر لتجميع `Match` العناصر. على سبيل المثال، يمكنك استخدام `Any` العنصر لمطابقة الكل أو بلا أو مجموعة فرعية دقيقة من العناصر التابعة `Match` الخاصة به.

`Any` يحتوي العنصر على سمات اختيارية `minMatches` وسمات `maxMatches` يمكنك استخدامها لتحديد عدد العناصر التابعة `Match` التي يجب أن تكون راضية قبل مطابقة النمط. تحدد هذه السمات *عدد* `Match` العناصر، وليس عدد مثيلات الأدلة التي تم العثور عليها للتطابقات. لتعريف الحد الأدنى لعدد المثيلات لمطابقة معينة، مثل كلمتين أساسيتين من قائمة، استخدم السمة `minCount` لعنصر `Match` (انظر أعلاه).

### <a name="match-at-least-one-child-match-element"></a>مطابقة عنصر مطابقة تابع واحد على الأقل

لطلب الحد الأدنى من `Match` العناصر فقط، يمكنك استخدام السمة `minMatches` . في الواقع، يتم ربط هذه `Match` العناصر بواسطة عامل تشغيل OR ضمني. يتم استيفاء هذا `Any` العنصر إذا تم العثور على تاريخ منسق من قبل الولايات المتحدة أو كلمة أساسية من أي قائمة.

```xml
<Any minMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-an-exact-subset-of-any-children-match-elements"></a>مطابقة مجموعة فرعية دقيقة لأي عناصر مطابقة توابع

لطلب عدد محدد من `Match` العناصر، قم بتعيينها `minMatches` وإلى `maxMatches` نفس القيمة. يتم استيفاء هذا `Any` العنصر فقط إذا تم العثور على تاريخ أو كلمة أساسية واحدة بالضبط. إذا كان هناك أي تطابقات أخرى، فلن يتطابق النمط.

```xml
<Any minMatches="1" maxMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-none-of-children-match-elements"></a>عدم مطابقة أي عنصر من عناصر مطابقة التوابع

إذا كنت ترغب في المطالبة بغياب دليل محدد لنمط ما ليتم الوفاء به، يمكنك تعيين كل من minMatches وmaxMatches إلى 0. يمكن أن يكون هذا مفيدا إذا كان لديك قائمة كلمات أساسية أو أدلة أخرى من المحتمل أن تشير إلى إيجابية خاطئة.

على سبيل المثال، يبحث كيان معرف الموظف عن الكلمة الأساسية "بطاقة" لأنه قد يشير إلى "بطاقة المعرف". ومع ذلك، إذا ظهرت البطاقة فقط في عبارة "بطاقة الائتمان"، فمن غير المحتمل أن تعني "البطاقة" في هذا المحتوى "بطاقة المعرف". حتى تتمكن من إضافة "بطاقة الائتمان" ككلمة أساسية إلى قائمة المصطلحات التي تريد استبعادها من استيفاء النمط.

```xml
<Any minMatches="0" maxMatches="0" >
    <Match idRef="Keyword_false_positives_local" />
    <Match idRef="Keyword_false_positives_intl" />
</Any>
```

### <a name="match-a-number-of-unique-terms"></a>مطابقة عدد من المصطلحات الفريدة

إذا كنت تريد مطابقة عدد من المصطلحات الفريدة، فاستخدم المعلمة *uniqueResults* ، المعينة إلى *true*، كما هو موضح في المثال التالي:

```xml
<Pattern confidenceLevel="75">
    <IdMatch idRef="Salary_Revision_terms" />
    <Match idRef=" Salary_Revision_ID " minCount="3" uniqueResults="true" />
</Pattern>
```

في هذا المثال، يتم تعريف نمط لمراجعة الرواتب باستخدام ثلاث تطابقات فريدة على الأقل.

## <a name="how-close-to-the-entity-must-the-other-evidence-be-patternsproximity-attribute"></a>ما مدى قرب الكيان من الدليل الآخر؟ [السمة patternsProximity]

يبحث نوع المعلومات الحساسة عن نمط يمثل معرف الموظف، وكجزء من هذا النمط، فإنه يبحث أيضا عن أدلة برمجية مثل كلمة أساسية مثل "المعرف". من المنطقي أنه كلما اقتربت هذه الأدلة من بعضها البعض، كان النمط أكثر احتمالا أن يكون معرف موظف فعلي. يمكنك تحديد مدى قرب الأدلة الأخرى في النمط من الكيان باستخدام سمة الأنماط المطلوبة للعنصر Entity.

![علامات XML تظهر السمة patternsProximity.](../media/e97eb7dc-b897-4e11-9325-91c742d9839b.png)

لكل نمط في الكيان، تحدد قيمة السمة patternsProximity المسافة (بأحرف Unicode) من موقع IdMatch لكافة التطابقات الأخرى المحددة لهذا النمط. يتم إرساء نافذة التقارب بموقع IdMatch، مع امتداد النافذة إلى يسار IdMatch ويساره.

![رسم تخطيطي لنافذة التقارب.](../media/b593dfd1-5eef-4d79-8726-a28923f7c31e.png)

يوضح المثال أدناه كيفية تأثير نافذة التقارب على مطابقة النمط حيث يتطلب عنصر IdMatch للكيان المخصص لمعرف الموظف تطابقا واحدا على الأقل من الكلمات الأساسية أو التاريخ. يتطابق المعرف1 فقط لأنه بالنسبة إلى ID2 وID3، إما أنه لم يتم العثور على أي دليل جزئي أو دليل جزئي فقط داخل نافذة التقارب.

![Diagram of corroborative evidence and proximity window.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

لاحظ أنه بالنسبة للبريد الإلكتروني، يتم التعامل مع نص الرسالة وكل مرفق كعناصر منفصلة. وهذا يعني أن نافذة التقارب لا تمتد إلى ما بعد نهاية كل عنصر من هذه العناصر. لكل عنصر (مرفق أو نص)، يجب أن يتواجد كل من الدليل idMatch والدليل المعرفي في هذا العنصر.

## <a name="what-are-the-right-confidence-levels-for-different-patterns-confidencelevel-attribute-recommendedconfidence-attribute"></a>ما هي مستويات الثقة الصحيحة للأنماط المختلفة؟ [سمة confidenceLevel، السمة recommendedConfidence]

كلما زادت الأدلة التي يتطلبها النمط، زادت الثقة لديك في أنه تم تحديد كيان فعلي (مثل معرف الموظف) عند مطابقة النمط. على سبيل المثال، لديك ثقة في نمط يتطلب رقم معرف مكون من تسعة أرقام، وتاريخ توظيف، وكلمة أساسية قريبة، أكثر مما تفعل في نمط يتطلب رقم معرف مكون من تسعة أرقام فقط.

يحتوي عنصر النمط على سمة confidenceLevel مطلوبة. يمكنك التفكير في قيمة confidenceLevel (عدد صحيح بين 1 و100) كمعرف فريد لكل نمط في كيان — يجب أن يكون للأنماط في الكيان مستويات ثقة مختلفة تقوم بتعيينها. لا يهم القيمة الدقيقة للعدد الصحيح — ما عليك سوى اختيار الأرقام المنطقية لفريق التوافق. بعد تحميل نوع المعلومات الحساسة المخصصة ثم إنشاء نهج، يمكنك الرجوع إلى مستويات الثقة هذه في شروط القواعد التي تقوم بإنشائها.

![تظهر علامات XML عناصر النقش بقيم مختلفة للسمة confidenceLevel.](../media/sit-xml-markedup-2.png)

بالإضافة إلى confidenceLevel لكل نمط، تحتوي الوحدة على سمة موصى بها. يمكن اعتبار سمة الثقة الموصى بها على أنها مستوى الثقة الافتراضي للقاعدة. عند إنشاء قاعدة في نهج، إذا لم تحدد مستوى ثقة للقاعدة لاستخدامها، فستتطابق هذه القاعدة استنادا إلى مستوى الثقة الموصى به للكيان. يرجى ملاحظة أن السمة recommendedConfidence إلزامية لكل معرف وحدة في حزمة القواعد، إذا فقدت فلن تتمكن من حفظ النهج التي تستخدم نوع المعلومات الحساسة.

## <a name="do-you-want-to-support-other-languages-in-the-ui-of-the-compliance-center-localizedstrings-element"></a>هل تريد دعم لغات أخرى في واجهة مستخدم مركز التوافق؟ [عنصر LocalizedStrings]

إذا كان فريق التوافق يستخدم مدخل التوافق في Microsoft Purview لإنشاء نهج في لغات مختلفة وبغات مختلفة، يمكنك توفير إصدارات مترجمة لاسم ووصف نوع المعلومات الحساسة المخصص. عندما يستخدم فريق التوافق Microsoft 365 بلغة تدعمها، سيرى الاسم المترجم في واجهة المستخدم.

![عدد المثيلات ومطابقة تكوين الدقة.](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

يجب أن يحتوي عنصر القواعد على عنصر LocalizedStrings، والذي يحتوي على عنصر مورد يشير إلى المعرف الفريد العمومي للوحدة المخصصة. بدوره، يحتوي كل عنصر مورد على عنصر واحد أو أكثر من عناصر الاسم والوصف التي يستخدم كل منها سمة langcode لتوفير سلسلة مترجمة للغة معينة.

![تظهر علامات XML محتويات عنصر LocalizedStrings.](../media/a96fc34a-b93d-498f-8b92-285b16a7bbe6.png)

لاحظ أنك تستخدم السلاسل المترجمة فقط لكيفية ظهور نوع المعلومات الحساسة المخصصة في واجهة المستخدم الخاصة بمركز التوافق. لا يمكنك استخدام السلاسل المترجمة لتوفير إصدارات مترجمة مختلفة لقائمة كلمات أساسية أو تعبير عادي.

## <a name="other-rule-package-markup-rulepack-guid"></a>علامات حزمة قاعدة أخرى [RulePack GUID]

وأخيرا، تحتوي بداية كل RulePackage على بعض المعلومات العامة التي تحتاج إلى تعبئتها. يمكنك استخدام العلامات التالية كقالب واستبدال . . ." العناصر النائبة مع معلوماتك الخاصة.

والأهم من ذلك، ستحتاج إلى إنشاء GUID ل RulePack. أعلاه، قمت بإنشاء GUID للكيان؛ هذا GUID ثان ل RulePack. هناك عدة طرق لإنشاء GUIDs، ولكن يمكنك القيام بذلك بسهولة في PowerShell عن طريق كتابة [guid]::NewGuid().

عنصر الإصدار مهم أيضا. عند تحميل حزمة القواعد للمرة الأولى، يلاحظ Microsoft 365 رقم الإصدار. في وقت لاحق، إذا قمت بتحديث حزمة القواعد وتحميل إصدار جديد، فتأكد من تحديث رقم الإصدار أو لن يقوم Microsoft 365 بنشر حزمة القواعد.

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

عند الاكتمال، يجب أن يبدو عنصر RulePack كما يلي.

![علامات XML تظهر عنصر RulePack.](../media/fd0f31a7-c3ee-43cd-a71b-6a3813b21155.png)

## <a name="validators"></a>مدقق

يعرض Microsoft 365 معالجات الوظائف ل SITs شائعة الاستخدام كمدققات. فيما يلي قائمة بها.

### <a name="list-of-currently-available-validators"></a>قائمة بأجهزة التحقق من الصحة المتوفرة حاليا

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

يمنحك هذا القدرة على تحديد RegEx الخاص بك والتحقق من صحتها. لاستخدام المدققات، حدد RegEx الخاص بك واستخدم الخاصية `Validator` لإضافة معالج الوظائف الذي تختاره. بمجرد تحديدها، يمكنك استخدام RegEx هذا في SIT.

في المثال أدناه، يتم تعريف تعبير عادي - Regex_credit_card_AdditionalDelimiters لبطاقة الائتمان، والتي يتم بعد ذلك التحقق من صحتها باستخدام دالة المجموع الاختباري لبطاقة الائتمان باستخدام Func_credit_card كمدقق.

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

يوفر Microsoft 365 اثنين من المدققين العامين

### <a name="checksum-validator"></a>مدقق المجموع الاختباري

في هذا المثال، يتم تعريف مدقق المجموع الاختباري لمعرف الموظف للتحقق من صحة RegEx لمعرف الموظف.

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

### <a name="date-validator"></a>مدقق التاريخ

في هذا المثال، يتم تعريف مدقق التاريخ لجزء RegEx الذي يمثل التاريخ.

```xml
<Validators id="date_validator_1"> <Validator type="DateSimple"> <Param name="Pattern">DDMMYYYY</Param> <!—supported patterns DDMMYYYY, MMDDYYYY, YYYYDDMM, YYYYMMDD, DDMMYYYY, DDMMYY, MMDDYY, YYDDMM, YYMMDD --> </Validator> </Validators>
<Regex id="date_regex_1" validators="date_validator_1">\d{8}</Regex>
```

## <a name="changes-for-exchange-online"></a>تغييرات Exchange Online

في السابق، ربما استخدمت Exchange Online PowerShell لاستيراد أنواع المعلومات الحساسة المخصصة ل DLP. الآن يمكن استخدام أنواع المعلومات الحساسة المخصصة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">كل من مركز إدارة Exchange</a> ومركز التوافق. كجزء من هذا التحسين، يجب عليك استخدام Security & Compliance PowerShell لاستيراد أنواع المعلومات الحساسة المخصصة — لا يمكنك استيرادها من Exchange Online PowerShell بعد الآن. ستستمر أنواع المعلومات الحساسة المخصصة في العمل كما كان من قبل؛ ومع ذلك، قد يستغرق ظهور التغييرات التي تم إجراؤها على أنواع المعلومات الحساسة المخصصة في مركز التوافق في مركز إدارة Exchange ما يصل إلى ساعة واحدة.

لاحظ أنه في مركز التوافق، يمكنك استخدام **[New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage)** cmdlet لتحميل حزمة قاعدة. (سابقا، في مركز إدارة Exchange، استخدمت  **Cmdlet ل ClassificationRuleCollection**.)

## <a name="upload-your-rule-package"></a>تحميل حزمة القواعد

لتحميل حزمة القواعد، قم بالخطوات التالية:

1. احفظه كملف .xml مع ترميز Unicode.

2. [الاتصال ب Security & Compliance PowerShell](/powershell/exchange/exchange-online-powershell)

3. استخدم بناء الجملة التالي:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('PathToUnicodeXMLFile'))
   ```

   يقوم هذا المثال بتحميل ملف Unicode XML المسمى MyNewRulePack.xml من C:\My Documents.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\MyNewRulePack.xml'))
   ```

   للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage).

   > [!NOTE]
   > الحد الأقصى لعدد حزم القواعد المعتمدة هو 10، ولكن يمكن أن تحتوي كل حزمة على تعريف أنواع معلومات حساسة متعددة.

4. للتحقق من إنشاء نوع معلومات حساسة جديد بنجاح، قم بأي من الخطوات التالية:

   - قم بتشغيل [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet للتحقق من إدراج حزمة القواعد الجديدة:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - شغل [الأمر Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet للتحقق من إدراج نوع المعلومات الحساسة:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     بالنسبة لأنواع المعلومات الحساسة المخصصة، ستكون قيمة خاصية Publisher شيئا آخر غير Microsoft Corporation.

   - استبدال \<Name\> بقيمة الاسم لنوع المعلومات الحساسة (على سبيل المثال: معرف الموظف) وتشغيل [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="potential-validation-issues-to-be-aware-of"></a>مشاكل التحقق من الصحة المحتملة التي يجب أن تكون على علم بها

عند تحميل ملف XML لحزمة القواعد، يتحقق النظام من صحة XML ويتحقق من الأنماط السيئة المعروفة ومشكلات الأداء الواضحة. فيما يلي بعض المشكلات المعروفة التي يتحقق التحقق من صحتها — تعبير عادي:

- يجب أن تكون تأكيدات Lookbehind في التعبير العادي ذات طول ثابت فقط. ستؤدي تأكيدات طول المتغير إلى حدوث أخطاء.

  على سبيل المثال، `"(?<=^|\s|_)"` لن يتم تمرير التحقق من الصحة. النمط الأول (`^`) هو صفر طول، في حين أن النمطين التاليين (`\s` و `_`) لهما طول واحد. طريقة بديلة لكتابة هذا التعبير العادي هي `"(?:^|(?<=\s|_))"`.

- لا يمكن البدء أو الانتهاء بالتناوب `|`، الذي يطابق كل شيء لأنه يعتبر تطابقا فارغا.

  على سبيل المثال، `|a` أو `b|` لن يجتاز التحقق من الصحة.

- لا يمكن البدء أو الانتهاء بنمط `.{0,m}` ، والذي ليس له غرض وظيفي ولا يؤثر إلا على الأداء.

  على سبيل المثال، `.{0,50}ASDF` أو `ASDF.{0,50}` لن يجتاز التحقق من الصحة.

- لا يمكن أن يكون لديك `.{0,m}` أو `.{1,m}` في مجموعات، ولا يمكن أن يكون بها `.\*` أو `.+` في مجموعات.

  على سبيل المثال، `(.{0,50000})` لن يتم تمرير التحقق من الصحة.

- لا يمكن أن يكون لديك أي حرف مع `{0,m}` أو `{1,m}` معيدات في مجموعات.

  على سبيل المثال، `(a\*)` لن يتم تمرير التحقق من الصحة.

- لا يمكن البدء أو الانتهاء ب `.{1,m}`؛ بدلا من ذلك، استخدم `.`.

  على سبيل المثال، `.{1,m}asdf` لن يتم تمرير التحقق من الصحة. بدلا من ذلك، استخدم `.asdf`.

- لا يمكن أن يكون هناك مكرر غير منضم (مثل `*` أو `+`) في مجموعة.

  على سبيل المثال، `(xx)\*` `(xx)+` ولن يتم تمرير التحقق من الصحة.

- تحتوي الكلمات الأساسية على 50 حرفا بحد أقصى في الطول.  إذا كانت لديك كلمة أساسية داخل مجموعة تتجاوز ذلك، فإن الحل المقترح هو إنشاء مجموعة المصطلحات [كقاموس كلمات أساسية](./create-a-keyword-dictionary.md) والإشارة إلى المعرف الفريد العمومي (GUID) لقاموس الكلمات الأساسية ضمن بنية XML كجزء من Entity for Match أو idMatch في الملف.

- يمكن أن يحتوي كل نوع معلومات حساسة مخصص على إجمالي 2048 كلمة أساسية كحد أقصى.

- الحد الأقصى لحجم قواميس الكلمات الأساسية في مستأجر واحد هو 480 كيلوبايت مضغوط للامتثال لحدود مخطط AD. قم بالإشارة إلى نفس القاموس عدة مرات حسب الضرورة عند إنشاء أنواع معلومات حساسة مخصصة. ابدأ بإنشاء قوائم كلمات أساسية مخصصة في نوع المعلومات الحساسة واستخدم قواميس الكلمات الأساسية إذا كان لديك أكثر من 2048 كلمة أساسية في قائمة كلمات أساسية أو إذا كان طول الكلمة الأساسية أكبر من 50 حرفا.

- يسمح ب 50 نوعا من المعلومات الحساسة المستندة إلى قاموس الكلمات الأساسية كحد أقصى في المستأجر.

- تأكد من أن كل عنصر Entity يحتوي على سمةConfidence موصى بها.

- عند استخدام PowerShell Cmdlet، يوجد حد أقصى لحجم الإرجاع للبيانات غير المهيأة يبلغ حوالي 1 ميغابايت.   سيؤثر هذا على حجم ملف XML الخاص بحزمة القواعد. احتفظ بالملف الذي تم تحميله مقيدا بحد أقصى يبلغ 770 كيلوبايت كحد مقترح للحصول على نتائج متسقة دون خطأ عند المعالجة.

- لا تتطلب بنية XML أحرف تنسيق مثل المسافات أو علامات التبويب أو إدخالات أحرف الإرجاع/ملف الأسطر.  لاحظ هذا عند تحسين المساحة على التحميلات. توفر أدوات مثل Microsoft Visual Code ميزات خط الربط لضغط ملف XML.

إذا احتوى نوع معلومات حساسة مخصص على مشكلة قد تؤثر على الأداء، فلن يتم تحميله وقد ترى إحدى رسائل الخطأ هذه:

- `Generic quantifiers which match more content than expected (e.g., '+', '*')`

- `Lookaround assertions`

- `Complex grouping in conjunction with general quantifiers`

## <a name="recrawl-your-content-to-identify-the-sensitive-information"></a>إعادة تتبع ارتباطات المحتوى الخاص بك لتحديد المعلومات الحساسة

يستخدم Microsoft 365 متتبع ارتباطات البحث لتعريف المعلومات الحساسة وتصنيفها في محتوى الموقع. تتم إعادة تجميع المحتوى في SharePoint Online ومواقع OneDrive for Business تلقائيا كلما تم تحديثه. ولكن لتحديد نوع المعلومات الحساسة المخصص الجديد في كل المحتوى الموجود، يجب إعادة تتبع ارتباطات هذا المحتوى.

في Microsoft 365، لا يمكنك طلب إعادة تتبع ارتباطات لمؤسسة بأكملها يدويا، ولكن يمكنك طلب إعادة التسجيل يدويا لمجموعة مواقع مشتركة أو قائمة أو مكتبة. لمزيد من المعلومات، راجع [طلب تتبع الارتباطات يدويا وإعادة فهرسة موقع أو مكتبة أو قائمة](/sharepoint/crawl-site-content).

## <a name="reference-rule-package-xml-schema-definition"></a>المرجع: تعريف مخطط XML لحزمة القواعد

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

- [تعرف على تفادي فقدان البيانات في Microsoft Purview](dlp-learn-about-dlp.md)
- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [دالات نوع المعلومات الحساسة](sit-functions.md)
