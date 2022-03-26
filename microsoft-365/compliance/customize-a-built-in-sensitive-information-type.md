---
title: تخصيص نوع معلومات حساسة مضمن
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية إنشاء نوع معلومات مخصص حساس يسمح لك باستخدام القواعد التي تلبي احتياجات مؤسستك.
ms.openlocfilehash: 8393da8e2b2607692983010783d9ae110f268f4c
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/29/2022
ms.locfileid: "63566091"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>تخصيص نوع معلومات حساسة مضمن

عند البحث عن معلومات حساسة في المحتوى، تحتاج إلى وصف هذه المعلومات في ما يسمى *بالقاعدة*. تتضمن عملية منع فقدان البيانات (DLP) قواعد لأنواع المعلومات الحساسة الأكثر شيوعا التي يمكنك استخدامها على الفور. لاستخدام هذه القواعد، يجب تضمينها في نهج. قد تجد أنك تريد ضبط هذه القواعد المضمنة لتلبية الاحتياجات الخاصة لمنظمتك، كما يمكنك القيام بذلك عن طريق إنشاء نوع معلومات مخصص حساس. يوضح لك هذا الموضوع كيفية تخصيص ملف XML الذي يحتوي على مجموعة القواعد الموجودة للكشف عن نطاق أوسع من معلومات بطاقة الائتمان المحتملة.

يمكنك أخذ هذا المثال وتطبيقه على أنواع المعلومات الحساسة المضمنة الأخرى. للحصول على قائمة بأنواع المعلومات الحساسة الافتراضية وتعريفات XML، راجع تعريفات [كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md).

## <a name="export-the-xml-file-of-the-current-rules"></a>تصدير ملف XML للقواعد الحالية

لتصدير XML، تحتاج إلى الاتصال بمركز الأمان [والتوافق عبر Remote PowerShell.](/powershell/exchange/connect-to-scc-powershell).

1. في PowerShell، اكتب ما يلي لعرض قواعد مؤسستك على الشاشة. إذا لم تكن قد أنشأت قاعدة خاصة بك، فسوف ترى القواعد الافتراضية المضمنة فقط، التي تسمى "حزمة قاعدة Microsoft".

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. قم بتخزين قواعد مؤسستك في متغير عن طريق كتابة ما يلي. تخزين شيء ما في متغير يجعلها متوفرة بسهولة في وقت لاحق بتنسيق يعمل مع أوامر PowerShell البعيدة.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. قم بصنع ملف XML تم تنسيقه مع كل هذه البيانات عن طريق كتابة ما يلي.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > تأكد من استخدام موقع الملف حيث يتم تخزين حزمة القواعد فعليا. `C:\custompath\` هو عنصر نائب.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>البحث عن القاعدة التي تريد تعديلها في XML

تم تصدير cmdlets أعلاه مجموعة القواعد *بأكملها*، التي تتضمن القواعد الافتراضية التي نوفرها. بعد ذلك، ستحتاج إلى البحث بشكل خاص عن قاعدة رقم بطاقة الائتمان التي تريد تعديلها.

1. استخدم محرر نص لفتح ملف XML الذي قمت بتصديره في المقطع السابق.

2. قم بالتمرير لأسفل `<Rules>` وصولا إلى العلامة، وهي بداية المقطع الذي يحتوي على قواعد DLP. بما أن ملف XML هذا يحتوي على معلومات مجموعة القواعد بأكملها، فهو يحتوي على معلومات أخرى في الأعلى تحتاج إلى التمرير عبرها للوصول إلى القواعد.

3. ابحث عن *Func_credit_card* للعثور على تعريف قاعدة رقم بطاقة الائتمان. في XML، لا يمكن لأسماء القواعد أن تحتوي على مسافات، لذلك يتم استبدال المسافات عادة بسمات تحتية، وفي بعض الأحيان يتم اختصار أسماء القواعد. مثال على ذلك هو قاعدة رقم الضمان الاجتماعي في الولايات المتحدة، _والمختصرة SSN_. يجب أن تبدو قاعدة رقم بطاقة الائتمان XML كنموذج التعليمات البرمجية التالية.

   ```xml
   <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085"
          patternsProximity="300" recommendedConfidence="85">
         <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_credit_card" />
           <Any minMatches="1">
             <Match idRef="Keyword_cc_verification" />
             <Match idRef="Keyword_cc_name" />
             <Match idRef="Func_expiration_date" />
           </Any>
         </Pattern>
       </Entity>
   ```

الآن بعد تحديد موقع تعريف قاعدة رقم بطاقة الائتمان في XML، يمكنك تخصيص XML للقاعدة لتلبية احتياجاتك. للحصول على تحديث حول تعريفات XML، راجع مصطلحات [المصطلحات في](#term-glossary) نهاية هذا الموضوع.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>تعديل XML وإنشاء نوع جديد من المعلومات الحساسة

أولا، تحتاج إلى إنشاء نوع جديد من المعلومات الحساسة لأنه لا يمكنك تعديل القواعد الافتراضية مباشرة. يمكنك القيام بمجموعة واسعة من الأشياء باستخدام أنواع المعلومات الحساسة المخصصة، الموضحة في إنشاء نوع معلومات مخصص حساس في [مركز & التوافق PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md). في هذا المثال، سنبقيه بسيطا ولن نقوم سوى بإزالة الدليل المانع وإضافة كلمات أساسية إلى قاعدة رقم بطاقة الائتمان.

يتم إنشاء كل تعريفات قواعد XML على القالب العام التالي. تحتاج إلى نسخ تعريف رقم بطاقة الائتمان XML ولصقه في القالب، وتعديل بعض القيم (لاحظ أن ". . ." في المثال التالي)، ثم قم بتحميل XML المعدل كقاعدة جديدة يمكن استخدامها في السياسات.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
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
   <!-- Paste the Credit Card Number rule definition here.-->
      <LocalizedStrings>
         <Resource idRef=". . .">
           <Name default="true" langcode=" . . . ">. . .</Name>
           <Description default="true" langcode=". . ."> . . .</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

الآن، لديك شيء يبدو مشابها ل XML التالي. نظرا لأنه يتم تعريف حزم القواعد والقواعد بواسطة معرفات GUID الفريدة الخاصة بها، ستحتاج إلى إنشاء معرفين: أحدهما لحزمة القواعد والرابع لاستبدال GUID لقاعدة رقم بطاقة الائتمان. إن GUID لم ID للكيان في عينة التعليمات البرمجية التالية هو التعريف الخاص بتعريف القاعدة المضمن، الذي تحتاج إلى استبداله بتعريف قاعدة جديد. هناك عدة طرق لإنشاء GUIDs، ولكن يمكنك القيام بذلك بسهولة في PowerShell عن طريق كتابة **[guid]::NewGuid()**.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id="8aac8390-e99f-4487-8d16-7f0cdee8defc">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="8d34806e-cd65-4178-ba0e-5d7d712e5b66" />
    <Details defaultLangCode="en">
      <LocalizedDetails langcode="en">
        <PublisherName>Contoso Ltd.</PublisherName>
        <Name>Financial Information</Name>
        <Description>Modified versions of the Microsoft rule package</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f"
       patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
      <LocalizedStrings>
         <Resource idRef="db80b3da-0056-436e-b0ca-1f4cf7080d1f">
<!-- This is the GUID for the preceding Credit Card Number entity because the following text is for that Entity. -->
           <Name default="true" langcode="en-us">Modified Credit Card Number</Name>
           <Description default="true" langcode="en-us">Credit Card Number that looks for additional keywords, and another version of Credit Card Number that doesn't require keywords (but has a lower confidence level)</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>إزالة متطلب الإثبات المانع من نوع معلومات حساسة

الآن وقد أصبح لديك نوع &amp; جديد من المعلومات الحساسة التي يمكنك تحميلها إلى مركز توافق الأمان، فإن الخطوة التالية هي جعل القاعدة أكثر تحديدا. قم بتعديل القاعدة بحيث تبحث عن رقم من 16 رقما فقط يمرر الاختبارات ولكنه لا يتطلب إثباتا إضافيا (معاكسا)، مثل الكلمات الأساسية. للقيام بذلك، تحتاج إلى إزالة جزء XML الذي تبحث عن أدلة معززة. إن الإثباتات المتعاونة مفيدة جدا في تقليل الإيجابيات الخاطئة. في هذه الحالة توجد عادة كلمات أساسية معينة أو تاريخ انتهاء صلاحية بالقرب من رقم بطاقة الائتمان. إذا قمت بإزالة هذا `confidenceLevel`الدليل، يجب أيضا ضبط مدى ثقتك في العثور على رقم بطاقة ائتمان عن طريق تخفيض ، وهو 85 في المثال.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>البحث عن الكلمات الأساسية الخاصة لمنظمتك

قد تحتاج إلى الحصول على إثباتات معززة ولكنك تريد كلمات أساسية مختلفة أو إضافية، وربما تريد تغيير مكان البحث عن هذا الدليل. يمكنك ضبط لتوسيع `patternsProximity` النافذة أو تقليصها للحصول على أدلة إثباتية حول الرقم المكون من 16 رقما. لإضافة كلمات أساسية خاصة بك، تحتاج إلى تعريف قائمة كلمات أساسية والإشارة إليها ضمن القاعدة. تضيف XML التالية الكلمات الأساسية "بطاقة الشركة" و"بطاقة Contoso" بحيث يتم تعريف أي رسالة تحتوي على هذه العبارات ضمن 150 حرفا من رقم بطاقة الائتمان على أنها رقم بطاقة ائتمان.

```xml
<Rules>
<! -- Modify the patternsProximity to be "150" rather than "300." -->
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="150" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
<!-- Add the following XML, which references the keywords at the end of the XML sample. -->
          <Match idRef="My_Additional_Keywords" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
<!-- Add the following XML, and update the information inside the <Term> tags with the keywords that you want to detect. -->
    <Keyword id="My_Additional_Keywords">
      <Group matchStyle="word">
        <Term caseSensitive="false">company card</Term>
        <Term caseSensitive="false">Contoso card</Term>
      </Group>
    </Keyword>
```

## <a name="upload-your-rule"></a>Upload القاعدة

لتحميل القاعدة، تحتاج إلى القيام بما يلي.

1. احفظه كملف .xml ترميز Unicode. وهذا أمر مهم لأن القاعدة لن تعمل إذا تم حفظ الملف باستخدام ترميز مختلف.

2. [الاتصال إلى مركز الأمان والتوافق عبر Remote PowerShell.](/powershell/exchange/connect-to-scc-powershell)

3. في PowerShell، اكتب ما يلي.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > تأكد من استخدام موقع الملف حيث يتم تخزين حزمة القواعد فعليا. `C:\custompath\` هو عنصر نائب.

4. لتأكيد ذلك، اكتب Y، ثم اضغط على **Enter**.

5. تحقق من تحميل القاعدة الجديدة واسم العرض الخاص بها عن طريق كتابة:

   ```powershell
   Get-DlpSensitiveInformationType
   ```

لبدء استخدام القاعدة الجديدة للكشف عن المعلومات الحساسة، ستحتاج إلى إضافة القاعدة إلى نهج DLP. لمعرفة كيفية إضافة القاعدة إلى نهج، راجع [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>مصطلحات المصطلحات

هذه هي تعريفات المصطلحات التي صادفتها أثناء هذا الإجراء.

<br>

****

|المدة|التعريف|
|---|---|
|كيان|الكيانات هي ما نطلق عليه أنواع المعلومات الحساسة، مثل أرقام بطاقات الائتمان. يحتوي كل كيان على GUID فريد كم ID الخاص به. إذا نسخت GUID وابحثت عنه في XML، فتعثر على تعريف قاعدة XML وكل الترجمات المترجمة لقاعدة XML هذه. يمكنك أيضا العثور على هذا التعريف عن طريق تحديد موقع GUID للترجمة ثم البحث عن GUID هذا.|
|الدالات|مراجع ملفات XML `Func_credit_card`، وهي دالة في التعليمات البرمجية المجمعة. يتم استخدام الدالات لتشغيل regexes معقدة والتحقق من تطابق الاختبارات للقواعد المضمنة.) ونظرا لحدث ذلك في التعليمة البرمجية، لا تظهر بعض المتغيرات في ملف XML.|
|IdMatch|هذا هو المعرف الذي يحاول النمط مطابقته، على سبيل المثال، رقم بطاقة الائتمان.|
|قوائم الكلمات الأساسية|يشير ملف XML `keyword_cc_verification` `keyword_cc_name`أيضا إلى و ، `patternsProximity` وهي قوائم الكلمات الأساسية التي نبحث عن تطابقات ضمن للكيان. لا يتم عرضها حاليا في XML.|
|النمط|يحتوي النمط على قائمة بالنوع الحساس الذي يبحث عنه. يشمل ذلك الكلمات الأساسية وregexes والوظائف الداخلية، التي تقوم بتنفيذ مهام مثل التحقق من الاختبارات. يمكن أن يكون لأنواع المعلومات الحساسة أنماط متعددة ذات ثقة فريدة. يعد هذا الأمر مفيدا عند إنشاء نوع معلومات حساس يرجع ثقة عالية في حالة العثور على دليل إثباتي وثقة أقل في حالة العثور على القليل من الدلائل المرجعية أو عدم العثور عليها.|
|نقش confidenceLevel|هذا هو مستوى الثقة الذي وجده محرك DLP متطابقا. يقترن هذا المستوى من الثقة بمطابقة النمط إذا تم تلبية متطلبات النمط. هذا هو مقياس الثقة الذي يجب أن تفكر فيه عند Exchange قواعد تدفق البريد الإلكتروني (المعروفة أيضا بقواعد النقل).|
|الأنماطProximity|عندما نعثر على ما `patternsProximity` يبدو على شكل نمط رقم بطاقة الائتمان، يكون التقارب حول هذا الرقم حيث سنبحث عن أدلة معززة.|
|RecommendedConfidence|هذا هو مستوى الثقة الذي نوصي به لهذه القاعدة. تنطبق الثقة الموصى بها على الكيانات والتقاربات. بالنسبة للكيانات، لا يتم تقييم هذا الرقم أبدا مقابل النمط `confidenceLevel` . إنه مجرد اقتراح لمساعدتك على اختيار مستوى الثقة إذا كنت تريد تطبيق أحدها. بالنسبة إلى التشابهات `confidenceLevel` `recommendedConfidence` ، يجب أن يكون النمط أعلى من رقم إجراء قاعدة تدفق البريد الذي يجب استدعاءه. هو `recommendedConfidence` مستوى الثقة الافتراضي المستخدم في قواعد تدفق البريد الذي تستدعي إجراء ما. يمكنك تغيير قاعدة تدفق البريد يدويا، إذا أردت ذلك، لكي يتم استدعاها استنادا إلى مستوى ثقة النمط، بدلا من ذلك.|
|

## <a name="for-more-information"></a>لمزيد من المعلومات

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [إنشاء نوع معلومات حساسة مخصصة](create-a-custom-sensitive-information-type.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
