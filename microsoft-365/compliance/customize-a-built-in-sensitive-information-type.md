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
description: تعرف على كيفية إنشاء نوع معلومات حساسة مخصص يسمح لك باستخدام القواعد التي تلبي احتياجات مؤسستك.
ms.openlocfilehash: 14fb645a4b7f58f609995bc71edae24090c83cc7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630974"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>تخصيص نوع معلومات حساسة مضمن

عند البحث عن معلومات حساسة في المحتوى، تحتاج إلى وصف تلك المعلومات في ما يسمى *بالقاعدة*. تتضمن تفادي فقدان البيانات في Microsoft Purview (DLP) قواعد لأنواع المعلومات الحساسة الأكثر شيوعا التي يمكنك استخدامها على الفور. لاستخدام هذه القواعد، يجب تضمينها في نهج. قد تجد أنك تريد ضبط هذه القواعد المضمنة لتلبية الاحتياجات الخاصة بالمؤسسة، ويمكنك القيام بذلك عن طريق إنشاء نوع معلومات حساسة مخصص. يوضح لك هذا الموضوع كيفية تخصيص ملف XML الذي يحتوي على مجموعة القواعد الموجودة للكشف عن نطاق أوسع من معلومات بطاقة الائتمان المحتملة.

يمكنك أخذ هذا المثال وتطبيقه على أنواع المعلومات الحساسة المضمنة الأخرى. للحصول على قائمة بأنواع المعلومات الحساسة الافتراضية وتعري تعريفات XML، راجع [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md).

## <a name="export-the-xml-file-of-the-current-rules"></a>تصدير ملف XML للقواعد الحالية

لتصدير XML، تحتاج إلى [الاتصال ب Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

1. في PowerShell، اكتب ما يلي لعرض قواعد مؤسستك على الشاشة. إذا لم تكن قد أنشأت قواعدك الخاصة، فسترى القواعد الافتراضية المضمنة فقط، المسماة "حزمة قواعد Microsoft".

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. قم بتخزين قواعد مؤسستك في متغير عن طريق كتابة ما يلي. تخزين شيء ما في متغير يجعلها متاحة بسهولة لاحقا بتنسيق يعمل مع أوامر PowerShell.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. قم بإنشاء ملف XML منسق مع كل تلك البيانات عن طريق كتابة ما يلي.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > تأكد من استخدام موقع الملف حيث يتم تخزين حزمة القواعد بالفعل. `C:\custompath\` هو عنصر نائب.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>البحث عن القاعدة التي تريد تعديلها في XML

تم تصدير cmdlets أعلاه *مجموعة القواعد* بأكملها، والتي تتضمن القواعد الافتراضية التي نقدمها. بعد ذلك، ستحتاج إلى البحث بشكل خاص عن قاعدة رقم بطاقة الائتمان التي تريد تعديلها.

1. استخدم محرر نص لفتح ملف XML الذي قمت بتصديره في المقطع السابق.

2. قم بالتمرير لأسفل وصولا إلى `<Rules>` العلامة، وهي بداية المقطع الذي يحتوي على قواعد DLP. نظرا لأن ملف XML هذا يحتوي على معلومات مجموعة القواعد بأكملها، فإنه يحتوي على معلومات أخرى في الأعلى تحتاج إلى تمريرها بعد ذلك للوصول إلى القواعد.

3. ابحث عن *Func_credit_card* للعثور على تعريف قاعدة رقم بطاقة الائتمان. في XML، لا يمكن أن تحتوي أسماء القواعد على مسافات، لذلك يتم استبدال المسافات عادة بتسطير أسفل السطر، ويتم أحيانا اختصار أسماء القواعد. ومن الأمثلة على ذلك قاعدة رقم الضمان الاجتماعي الأمريكية، وهي _SSN مختصرة_. يجب أن تبدو XML لقاعدة رقم بطاقة الائتمان مثل عينة التعليمات البرمجية التالية.

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

الآن بعد أن حددت تعريف قاعدة رقم بطاقة الائتمان في XML، يمكنك تخصيص XML الخاص بالقاعدة لتلبية احتياجاتك. للحصول على تحديث حول تعريفات XML، راجع [مسرد المصطلحات](#term-glossary) في نهاية هذا الموضوع.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>تعديل XML وإنشاء نوع معلومات حساسة جديد

أولا، تحتاج إلى إنشاء نوع معلومات حساسة جديد لأنه لا يمكنك تعديل القواعد الافتراضية مباشرة. يمكنك القيام بمجموعة متنوعة من الأشياء باستخدام أنواع المعلومات الحساسة المخصصة، والتي تم توضيحها في [إنشاء نوع معلومات حساسة مخصص في Security & Compliance PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md). على سبيل المثال، سنبقيه بسيطا ونزيل فقط الأدلة القاطعة ونضيف كلمات أساسية إلى قاعدة رقم بطاقة الائتمان.

يتم إنشاء كافة تعريفات قاعدة XML على القالب العام التالي. تحتاج إلى نسخ ولصق XML لتعريف رقم بطاقة الائتمان في القالب، وتعديل بعض القيم (لاحظ ". . ." العناصر النائبة في المثال التالي)، ثم قم بتحميل XML المعدل كقاعدة جديدة يمكن استخدامها في النهج.

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

الآن، لديك شيء يشبه XML التالي. نظرا إلى أن حزم القواعد وقواعدها يتم تعريفها بواسطة معرفات GUID الفريدة الخاصة بها، تحتاج إلى إنشاء اثنين من معرفات المستخدم الرسومية( GUIDs): واحدة لحزمة القواعد والأخرى لاستبدال GUID لقاعدة رقم بطاقة الائتمان. معرف GUID لمعرف الكيان في عينة التعليمات البرمجية التالية هو تعريف القاعدة المضمنة، والذي تحتاج إلى استبداله بتعريف جديد. هناك عدة طرق لإنشاء GUIDs، ولكن يمكنك القيام بذلك بسهولة في PowerShell عن طريق كتابة **[guid]::NewGuid()**.

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

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>إزالة متطلبات الأدلة غير المهيأة من نوع معلومات حساسة

الآن بعد أن أصبح لديك نوع معلومات حساسة جديد يمكنك تحميله إلى مدخل التوافق في Microsoft Purview، فإن الخطوة التالية هي جعل القاعدة أكثر تحديدا. قم بتعديل القاعدة بحيث لا تبحث إلا عن رقم مكون من 16 رقما يمرر المجموع الاختباري ولكنه لا يتطلب أدلة إضافية (خادعة)، مثل الكلمات الأساسية. للقيام بذلك، تحتاج إلى إزالة جزء XML الذي يبحث عن أدلة مضمنة. الأدلة الموثقة مفيدة جدا في الحد من النتائج الإيجابية الخاطئة. في هذه الحالة عادة ما تكون هناك كلمات أساسية معينة أو تاريخ انتهاء صلاحية بالقرب من رقم بطاقة الائتمان. إذا قمت بإزالة هذا الدليل، يجب عليك أيضا ضبط مدى ثقتك في أنك عثرت على رقم بطاقة ائتمان عن طريق خفض `confidenceLevel`، وهو 85 في المثال.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>البحث عن الكلمات الأساسية الخاصة بمؤسستك

قد تحتاج إلى الحصول على أدلة قاطعة ولكنك تريد كلمات أساسية مختلفة أو إضافية، وربما تريد تغيير مكان البحث عن هذا الدليل. يمكنك ضبط `patternsProximity` لتوسيع النافذة أو تقليصها للحصول على أدلة متوازة حول الرقم المكون من 16 رقما. لإضافة الكلمات الأساسية الخاصة بك، تحتاج إلى تعريف قائمة كلمات أساسية والإشارة إليها داخل القاعدة الخاصة بك. يضيف XML التالي الكلمات الأساسية "بطاقة الشركة" و"بطاقة Contoso" بحيث يتم تعريف أي رسالة تحتوي على هذه العبارات ضمن 150 حرفا من رقم بطاقة الائتمان كرقم بطاقة ائتمان.

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

## <a name="upload-your-rule"></a>تحميل القاعدة

لتحميل القاعدة، تحتاج إلى القيام بما يلي.

1. احفظه كملف .xml مع ترميز Unicode. هذا مهم لأن القاعدة لن تعمل إذا تم حفظ الملف مع ترميز مختلف.

2. [الاتصال ب Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

3. في PowerShell، اكتب ما يلي.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > تأكد من استخدام موقع الملف حيث يتم تخزين حزمة القواعد بالفعل. `C:\custompath\` هو عنصر نائب.

4. للتأكيد، اكتب Y، ثم اضغط على **مفتاح الإدخال Enter**.

5. تحقق من تحميل القاعدة الجديدة واسم العرض الخاص بها بكتابة:

   ```powershell
   Get-DlpSensitiveInformationType
   ```

لبدء استخدام القاعدة الجديدة للكشف عن المعلومات الحساسة، تحتاج إلى إضافة القاعدة إلى نهج DLP. لمعرفة كيفية إضافة القاعدة إلى نهج، راجع [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>مسرد المصطلحات

هذه هي تعريفات المصطلحات التي واجهتها أثناء هذا الإجراء.

<br>

****

|مصطلح|تعريف|
|---|---|
|الكيان|الكيانات هي ما نطلق عليه أنواع المعلومات الحساسة، مثل أرقام بطاقات الائتمان. يحتوي كل كيان على GUID فريد كمعرفه. إذا قمت بنسخ GUID والبحث عنه في XML، فستجد تعريف قاعدة XML وجميع الترجمات المترجمة لقاعدة XML هذه. يمكنك أيضا العثور على هذا التعريف عن طريق تحديد GUID للترجمة ثم البحث عن GUID هذا.|
|الدالات|مراجع ملف XML، وهي دالة في التعليمات `Func_credit_card`البرمجية المحولة برمجيا. يتم استخدام الدالات لتشغيل regexes المعقدة والتحقق من تطابق عمليات التحقق مع القواعد المضمنة لدينا.) لأن هذا يحدث في التعليمات البرمجية، لا تظهر بعض المتغيرات في ملف XML.|
|IdMatch|هذا هو المعرف الذي يحاول النمط مطابقته— على سبيل المثال، رقم بطاقة الائتمان.|
|قوائم الكلمات الأساسية|يشير ملف XML أيضا و `keyword_cc_verification` `keyword_cc_name`، وهي قوائم الكلمات الأساسية التي نبحث منها عن تطابقات داخل `patternsProximity` الكيان. لا يتم عرض هذه حاليا في XML.|
|نمط|يحتوي النمط على قائمة بما يبحث عنه النوع الحساس. يتضمن ذلك الكلمات الأساسية وrgexes والوظائف الداخلية، والتي تؤدي مهام مثل التحقق من الفحوصات. يمكن أن يكون لأنواع المعلومات الحساسة أنماط متعددة بثقة فريدة. وهذا مفيد عند إنشاء نوع معلومات حساسة يرجع ثقة عالية إذا تم العثور على دليل نافع وبثقة أقل إذا تم العثور على دليل بسيط أو معدوم.|
|مستوى الثقة بالنمط|هذا هو مستوى الثقة الذي وجده محرك DLP مطابقا. يقترن هذا المستوى من الثقة بمطابقة النمط إذا تم استيفاء متطلبات النمط. هذا هو مقياس الثقة الذي يجب مراعاته عند استخدام قواعد تدفق بريد Exchange (المعروفة أيضا بقواعد النقل).|
|patternsProximity|عندما نجد ما يبدو مثل نمط رقم بطاقة الائتمان، `patternsProximity` هو التقارب حول هذا الرقم حيث سنبحث عن أدلة التفافية.|
|recommendedConfidence|هذا هو مستوى الثقة الذي نوصي به لهذه القاعدة. وتنطبق الثقة الموصى بها على الكيانات والتقاربات. بالنسبة للكيانات، لا يتم تقييم هذا الرقم أبدا مقابل `confidenceLevel` النمط. إنه مجرد اقتراح لمساعدتك في اختيار مستوى ثقة إذا كنت تريد تطبيق مستوى ثقة. بالنسبة للترابط، `confidenceLevel` يجب أن يكون النمط أعلى من `recommendedConfidence` رقم إجراء قاعدة تدفق البريد المطلوب استدعاؤه. مستوى `recommendedConfidence` الثقة الافتراضي المستخدم في قواعد تدفق البريد الذي يستدعي إجراء. إذا أردت، يمكنك تغيير قاعدة تدفق البريد يدويا ليتم استدعاؤها استنادا إلى مستوى ثقة النمط، بدلا من ذلك.|
|

## <a name="for-more-information"></a>لمزيد من المعلومات

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [إنشاء نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type.md)
- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
