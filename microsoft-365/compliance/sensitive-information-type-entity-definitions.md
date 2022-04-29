---
title: تعريفات كيان نوع المعلومات الحساسة
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: هناك العديد من أنواع المعلومات الحساسة الجاهزة للاستخدام في نهج DLP. تسرد هذه المقالة كل أنواع المعلومات الحساسة هذه وتعرض ما يبحث عنه نهج DLP عند اكتشاف كل نوع.
ms.openlocfilehash: af2cbd03de426aa34b9db82691a22684c4c1df0b
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130791"
---
# <a name="sensitive-information-type-entity-definitions"></a>تعريفات كيان نوع المعلومات الحساسة

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تسرد هذه المقالة كافة تعريفات كيان نوع المعلومات الحساسة. يوضح كل تعريف ما يبحث عنه نهج DLP للكشف عن كل نوع. لمعرفة المزيد حول أنواع المعلومات الحساسة، راجع [أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md)

> [!NOTE]
> تعيين مستوى الثقة (مرتفع/متوسط/منخفض) برقم دقة (قيمة رقمية من 1 إلى 100)
>
> - ثقة منخفضة: 65 أو أقل
> - الثقة المتوسطة: 75
> - ثقة عالية: 85

## <a name="aba-routing-number"></a>رقم توجيه ABA

### <a name="format"></a>تنسيق

تسعة أرقام قد تكون في نقش منسق أو غير منسق

### <a name="pattern"></a>نمط

- رقمان في النطاقات 00-12 أو 21-32 أو 61-72 أو 80
- رقمين
- واصلة اختيارية
- أربعة أرقام
- واصلة اختيارية
- رقم

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع النهج بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، في حدود 300 حرف:

- تبحث الدالة Func_aba_routing عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_ABA_Routing.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_aba_routing عن المحتوى الذي يتطابق مع النمط.

```xml
    <!-- ABA Routing Number -->
    <Entity id="cb353f78-2b72-4c3c-8827-92ebe4f69fdf" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_aba_routing" />
        <Match idRef="Keyword_ABA_Routing" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_aba_routing" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- رقم aba
- ابا #
- ابا
- شريط شريطي #
- abaroutingnumber
- americanbankassociationrouting #
- رقم الأرقام في americanbankassociationrouting
- توجيه بنكي #
- رقم الجدولة البنكية
- التوجيه #
- لا يتم التوجيه
- رقم التوجيه
- توجيه رقم النقل
- التوجيه #
- RTN

## <a name="all-full-names"></a>كافة الأسماء الكاملة

جميع الأسماء الكاملة هي كيان مسمى مجمع. يكشف عن الأسماء الكاملة للأشخاص من جميع البلدان/المناطق المدعومة، والتي تشمل أستراليا والصين واليابان والولايات المتحدة والبلدان في الاتحاد الأوروبي. استخدم SIT هذا للكشف عن كافة التطابقات المحتملة للأسماء الكاملة.

### <a name="format"></a>تنسيق

مختلف.

### <a name="pattern"></a>نمط

مختلف.

### <a name="checksum"></a>المجموع الاختباري

لا.

### <a name="description"></a>الوصف

يطابق هذا الكيان المسمى SIT الأسماء الشخصية التي قد يحددها الإنسان كاسم بثقة عالية. على سبيل المثال، إذا تم العثور على سلسلة تتكون من اسم معين وتبعها اسم عائلة، فسيتم إجراء تطابق بثقة عالية. ويستخدم ثلاثة موارد أساسية:

- قاموس للأسماء المحددة.
- قاموس بأسماء العائلة.
- أنماط كيفية تشكيل الأسماء.

تختلف الموارد الثلاثة لكل بلد.  ستؤدي السلاسل *UnityVia إلى* إجراء تطابق. تمنح أسماء العائلة/الأسماء المعطاة الشائعة ثقة أعلى من الأسماء النادرة. ومع ذلك، يسمح النمط أيضا بالتطابقات الجزئية. إذا تم العثور على اسم معين من القاموس متبوعا باسم عائلة غير موجود في القاموس، فسيتم تشغيل تطابق جزئي. على سبيل المثال، قد يؤدي *جمعاء ريشارد إلى* إجراء تطابق جزئي. تمنح التطابقات الجزئية ثقة أقل.

بالإضافة إلى ذلك، تتطابق أيضا الأنماط التي يراها الإنسان على أنها تدل على الأسماء مع الثقة المناسبة. مثل *O.Anda*, *O.P.Anda*, *Dr. O. P.Anda,Anda**, O.P.* أو *سيكون T. Richard, Jr.* مطابقين.

### <a name="supported-languages"></a>اللغات المدعومة

- الإنجليزية
- البلغارية
- الصينية
- الكرواتية
- التشيكية
- الدانمركية
- الإستونية
- الفنلندية
- الفرنسية
- الألمانية
- المجرية
- الأيسلندية
- الأيرلندية
- الإيطالية
- اليابانية
- اللاتفية
- الليتوانية
- المالطية
- الهولندية
- النرويجية
- البولندية
- البرتغالية
- الرومانية
- السلوفاكية
- السلوفينية
- الإسبانية
- السويدية
- التركية

## <a name="all-medical-terms-and-conditions"></a>جميع الشروط والأحكام الطبية

جميع الشروط والأحكام الطبية هي كيان مسمى مجمع يكشف عن الشروط الطبية والحالات الطبية. يكشف عن مصطلحات اللغة الإنجليزية فقط. استخدم SIT هذا للكشف عن جميع التطابقات المحتملة للشروط والأحكام الطبية.

### <a name="format"></a>تنسيق

القاموس

### <a name="pattern"></a>نمط

القاموس

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="description"></a>الوصف

يتطابق هذا الكيان المسمى المجمع مع النص الذي يشير إلى الحالات الطبية الموجودة في قواميس منسقة. هناك قاموس واحد تم تنسيقه لكل لغة معتمدة. القواميس من العديد من الموارد الطبية الدولية. تتضمن القواميس أكبر عدد ممكن من الحالات الطبية دون المخاطرة بعدد كبير من الإيجابيات الخاطئة. يحتوي كل إدخال على النماذج المختلفة التي تتم كتابة شرط واحد بها بشكل شائع لضمان التغطية، على سبيل المثال:

- *السل*
- *السل*
- *phthisis*

### <a name="contains"></a>يحتوي

يحتوي هذا الكيان المسمى المجمع SIT على SITs الفردية هذه.

- مصطلحات اختبار الدم
- أنواع الأدوية
- الامراض
- أسماء الأدوية العامة
- الإعاقات المدرجة في تقييم الإعاقة في الولايات المتحدة ضمن الضمان الاجتماعي
- مصطلحات الاختبار المعملي
- أنماط الحياة التي تتعلق بالظروف الطبية
- التخصصات الطبية
- الإجراءات الجراحية
- أسماء أدوية العلامة التجارية

## <a name="all-physical-addresses"></a>كافة العناوين الفعلية

جميع العناوين المادية هي كيان مجمع SIT، والذي يكتشف الأنماط المتعلقة بالعناوين المادية من جميع البلدان/المناطق المدعومة.

### <a name="format"></a>تنسيق

مختلف

### <a name="pattern"></a>نمط

مختلف

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="description"></a>الوصف

تم تصميم مطابقة عناوين الشارع لمطابقة السلاسل التي قد يحددها الإنسان كعنوان شارع. للقيام بذلك، فإنه يستخدم العديد من الموارد الأساسية:

- قاموس للمناطق والتجمعات والتجمعات.
- قاموس للاحقات الشارع، مثل الطريق أو الشارع أو الشارع.
- أنماط الرموز البريدية.
- أنماط تنسيقات العناوين.

تختلف الموارد لكل بلد. الموارد الأساسية هي أنماط تنسيقات العناوين المستخدمة في بلد معين. يتم اختيار تنسيقات مختلفة للتأكد من مطابقة أكبر عدد ممكن من العناوين. تسمح هذه التنسيقات بالمرونة، على سبيل المثال، قد يحذف العنوان الرمز البريدي أو يحذف اسم بلدة أو يحتوي على شارع بدون لاحقة شارع. في جميع الحالات، يتم استخدام هذه التطابقات لزيادة ثقة المطابقة.

تم تصميم الأنماط لمطابقة العناوين الفردية، وليس المواقع العامة. لذلك لن تتطابق سلاسل مثل *Redmond أو WA 98052* أو *Main Street أو Albuquerque* .

### <a name="contains"></a>يحتوي

يحتوي هذا الكيان المجمع المسمى SIT على SITs الفردية هذه:

- العناوين المادية في أستراليا
- العناوين المادية في النمسا
- عناوين فعلية لبلكيا
- العناوين المادية في البرازيل
- العناوين المادية لبلغاريا
- العناوين الفعلية لكندا
- عناوين مادية لكرواتيا
- العناوين المادية للسينية
- العناوين المادية للتشيك
- عناوين الدانمارك المادية
- العناوين المادية في  الإستونية
- عناوين فنلندا المادية
- عناوين فرنسا الفعلية
- عناوين ألمانيا الفعلية
- عناوين مادية في اليونان
- العناوين المادية في المجر
- عناوين آيسلندا المادية
- عناوين أيرلندا المادية
- العناوين الفعلية في إيطاليا
- عناوين لاتفيا المادية
- عناوين ليشتاندا المادية
- عناوين ليتوانية فعلية
- عناوين لكسمبورج المادية
- عناوين مادية في  الاحتياجات الخاصة
- العناوين المادية في هولندا
- العناوين المادية في نيوزيلندا
- العناوين المادية في النرويج
- العناوين المادية لبولاندا
- العناوين المادية البرتغالية
- عناوين مادية في رومانيا
- العناوين المادية ل لمزوفا
- العناوين المادية السلوفينية
- العناوين الفعلية في أسبانيا
- عناوين فعلية في السويد
- العناوين المادية في سويسرا
- العناوين المادية لتركيا
- العناوين الفعلية في المملكة المتحدة
- العناوين الفعلية للولايات المتحدة

### <a name="supported-languages"></a>اللغات المدعومة

- الإنجليزية
- البلغارية
- الصينية
- الكرواتية
- التشيكية
- الدانمركية
- الإستونية
- الفنلندية
- الفرنسية
- الألمانية
- المجرية
- الأيسلندية
- الأيرلندية
- الإيطالية
- اليابانية
- اللاتفية
- الليتوانية
- المالطية
- الهولندية
- النرويجية
- البولندية
- البرتغالية
- الرومانية
- السلوفاكية
- السلوفينية
- الإسبانية
- السويدية
- التركية

## <a name="argentina-national-identity-dni-number"></a>رقم الهوية الوطنية للارجنتين (DNI)

### <a name="format"></a>تنسيق

ثمانية أرقام بفترات زمنية أو بدونها

### <a name="pattern"></a>نمط

ثمانية أرقام:

- رقمين
- فترة اختيارية
- ثلاثة أرقام
- فترة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_argentina_national_id عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_argentina_national_id.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- رقم الهوية الوطنية للارجنتين
- cedula
- cédula
- dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- rnp

## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>مفتاح التعريف الضريبي الفريد في الأرجنتين (CUIT/CUIL)

### <a name="format"></a>تنسيق

11 رقما بشرطة

### <a name="pattern"></a>نمط

11 رقما بشرطة:

- رقمان في 20 أو 23 أو 24 أو 27 أو 30 أو 33 أو 34
- واصلة (-)
- ثمانية أرقام
- واصلة (-)
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_Argentina_Unique_Tax_Key` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_Argentina_Unique_Tax_Key` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_Argentina_Unique_Tax_Key` عن المحتوى الذي يطابق النمط.

```xml
    <!-- Argentina Unique Tax Identification Key (CUIT/CUIL) -->
      <Entity id="98da3da1-9199-4571-b7c4-b6522980b507" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
          <Match idRef="Keyword_Argentina_Unique_Tax_Key" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- تعليمة برمجية فريدة لتحديد هوية العمالة
- Clave Única de Identificación Tributaria
- رمز تعريف تعريف فريد للعمليات
- CUIL
- مفتاح تعريف الضريبة الفريد
- مفتاح تعريف فريد للعمليات
- مفتاح فريد لتحديد هوية العمالة
- رمز تعريف العمل الفريد
- رمز فريد لتعريف العمل
- مفتاح تعريف العمل الفريد
- مفتاح فريد لتعريف العمل
- رمز فريد لتعريف الضريبة
- مفتاح فريد لتعريف الضريبة
- رمز تعريف العمل الفريد
- رمز فريد لتعريف العمل
- مفتاح تعريف العمل الفريد
- مفتاح فريد لتعريف العمل
- معرف الضريبة
- معرف الضريبة #
- معرف الضريبة
- رقم سيارة أجرة
- رقم الضريبة
- رقم الضريبة
- الضريبيه #
- الضريبيه #
- معرف
- رقم/&
- لا
- دافعي الضرائب #
- دافعي الضرائب #
- الهوية الضريبية
- التعريف الضريبي
- Número de Identificación Fiscal
- número de contribuyente

## <a name="australia-bank-account-number"></a>رقم الحساب البنكي في أستراليا

### <a name="format"></a>تنسيق

من ستة إلى 10 أرقام مع رقم فرع ولاية بنكية أو بدونه

### <a name="pattern"></a>نمط

رقم الحساب من 6 إلى 10 أرقام.

رقم فرع ولاية أستراليا المصرفي:

- ثلاثة أرقام
- واصلة
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_australia_bank_account_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_australia_bank_account_number.
- يبحث التعبير العادي Regex_australia_bank_account_number_bsb عن المحتوى الذي يطابق النمط.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_australia_bank_account_number عن المحتوى الذي يتطابق مع النمط.

- تم العثور على كلمة أساسية من Keyword_australia_bank_account_number.

```xml
<!-- Australia Bank Account Number -->
<Entity id="74a54de9-2a30-4aa0-a8aa-3d9327fc07c7" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
        <Match idRef="Regex_australia_bank_account_number_bsb" />
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
  </Pattern>
 </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- رمز بنك swift
- بنك
- العملة الأساسية
- حساب الولايات المتحدة الأمريكية
- عنوان حامل
- عنوان البنك
- حساب المعلومات
- عمليات تحويل الأموال
- الرسوم المصرفية
- تفاصيل البنك
- معلومات مصرفية
- الأسماء الكاملة
- الوكاله

## <a name="australia-business-number"></a>رقم العمل في أستراليا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

11 رقما مع محددات اختيارية

### <a name="pattern"></a>نمط

11 رقما مع محددات اختيارية:

- رقمين
- واصلة أو مسافة اختيارية
- ثلاثة أرقام
- واصلة أو مسافة اختيارية
- ثلاثة أرقام
- واصلة أو مسافة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_australian_business_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_australian_business_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_australian_business_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Australia Business Number -->
      <Entity id="76e83b3b-01ee-4530-aced-e667a6609f49" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_australian_business_number" />
          <Match idRef="Keywords_australian_business_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_australian_business_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- رقم الأعمال في أستراليا
- رقم العمل
- ايه #
- معرف الأعمال #
- معرف العمل
- ايه
- رجل أعمال #

## <a name="australia-company-number"></a>رقم شركة أستراليا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

تسعة أرقام مع المحددات

### <a name="pattern"></a>نمط

تسعة أرقام مع المحددات:

- ثلاثة أرقام
- مساحة
- ثلاثة أرقام
- مساحة
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Australian_Company_Number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_Australian_Company_Number.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_Australian_Company_Number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Australia Company Number -->
      <Entity id="b1fba4f7-7b3e-4bb9-8f9a-9366df604dbb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Australian_Company_Number" />
          <Match idRef="Keyword_Australian_Company_Number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_Australian_Company_Number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- Cna
- رقم شركة أستراليا
- رقم شركة أستراليا #
- رقم شركة أستراليا
- لا للشركة الأسترالية
- لا للشركة الأسترالية #
- رقم الشركة الأسترالية

## <a name="australia-drivers-license-number"></a>رقم رخصة القيادة في أستراليا

### <a name="format"></a>تنسيق

تسعة أحرف وأرقام

### <a name="pattern"></a>نمط

تسعة أحرف وأرقام:

- رقمان أو حرفان (غير حساس لحالة الأحرف)
- رقمين
- خمسة أرقام أو أحرف (غير حساسة لحالة الأحرف)

او

- حرف إلى حرفين اختياريين (غير حساس لحالة الأحرف)
- من أربعة إلى تسعة أرقام

او

- تسعة أرقام أو أحرف (غير حساسة لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_australia_drivers_license_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_australia_drivers_license_number.
- لم يتم العثور على كلمة أساسية من Keyword_australia_drivers_license_number_exclusions.

```xml
<!-- Australia Drivers License Number -->
<Entity id="1cbbc8f5-9216-4392-9eb5-5ac2298d1356" patternsProximity="300" recommendedConfidence="75">
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_drivers_license_number" />
        <Match idRef="Keyword_australia_drivers_license_number" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_australia_drivers_license_number_exclusions" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- تراخيص القيادة الدولية
- اتحاد السيارات الأسترالية
- رخصة القيادة الدولية
- DriverLicence
- DriverLicences
- Lic برنامج التشغيل
- رخصة القيادة
- رخص القيادة
- DriversLic
- DriversLicence
- DriversLicences
- Lic برامج التشغيل
- Lics برامج التشغيل
- رخصة القيادة
- رخص القيادة
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- تراخيص القيادة
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- رخص القيادة
- برنامج تشغيل sLic
- برامج التشغيل sLics
- SLicence للسائق
- برامج التشغيل sLicences
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- رخص القيادة
- برنامج تشغيل #
- برامج تشغيل #
- DriverLicence #
- DriverLicences #
- Lic برنامج التشغيل #
- Lics برامج التشغيل #
- رخصة القيادة #
- رخص القيادة #
- DriversLic #
- DriversLics #
- DriversLicence #
- DriversLicences #
- Lic برامج التشغيل #
- Lics برامج التشغيل #
- رخصة القيادة #
- رخص القيادة #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- رخص القيادة #
- برنامج تشغيل sLic #
- برامج التشغيل sLics #
- SLicence للسائق #
- برامج التشغيل sLicences #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- رخص القيادة #

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- Aaa
- رخصة القيادة
- تراخيص برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- رخصه
- تراخيص برامج التشغيل
- ترخيص القيادة
- تراخيص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة #
- تراخيص برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- رخصه #
- تراخيص برامج التشغيل #
- ترخيص القيادة #
- تراخيص القيادة #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #

## <a name="australia-medical-account-number"></a>رقم الحساب الطبي في أستراليا

### <a name="format"></a>تنسيق

من 10 إلى 11 رقما

### <a name="pattern"></a>نمط

من 10 إلى 11 رقما:

- الرقم الأول في النطاق من 2 إلى 6
- الرقم التاسع هو خانة اختيار
- الرقم العاشر هو رقم المشكلة
- الرقم الحادي عشر (اختياري) هو الرقم الفردي

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_australian_medical_account_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_Australia_Medical_Account_Number.
- يمر المجموع الاختباري.

```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- تفاصيل الحساب البنكي
- دفعات medicare
- حساب رهن
- دفعات بنكية
- فرع المعلومات
- قرض بطاقة الائتمان
- قسم الخدمات البشرية
- الخدمة المحلية
- الرعايه الطبيه

## <a name="australia-passport-number"></a>رقم جواز سفر أستراليا

### <a name="format"></a>تنسيق

ثمانية أو تسعة أحرف أبجدية رقمية

### <a name="pattern"></a>نمط

- حرف واحد (N، E، D، F، A، C، U، X) متبوعا بسبعة أرقام أو
- حرفان (PA، PB، PC، PD، PE، PF، PU، PW، PX، PZ) متبوعا بسبعة أرقام.

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_australia_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_australia_passport_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_australia_passport_number` العادي عن المحتوى الذي يطابق النمط.

```xml
    <!-- Australia Passport Number -->
    <Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Match idRef="Keyword_australia_passport_number" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_australia_passport_number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر
- تفاصيل جواز السفر
- وجنسية
- من أستراليا
- قسم الشؤون الخارجية
- بطاقة الهوية الوطنية
- مستند السفر
- الجهة المصدرة

## <a name="australia-physical-addresses"></a>العناوين المادية في أستراليا

الكشف عن الأنماط المتعلقة بالعنوان الفعلي من أستراليا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة
المتوسطه

## <a name="australia-tax-file-number"></a>رقم ملف الضريبة في أستراليا

### <a name="format"></a>تنسيق

من ثمانية إلى تسعة أرقام

### <a name="pattern"></a>نمط

عادة ما يتم عرض الأرقام من ثمانية إلى تسعة مع مسافات كما يلي:

- ثلاثة أرقام
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- رقمان إلى ثلاثة أرقام حيث الرقم الأخير هو خانة اختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_australian_tax_file_number عن المحتوى الذي يتطابق مع النمط.
- لم يتم العثور على كلمة أساسية من Keyword_Australia_Tax_File_Number أو Keyword_number_exclusions.
- يمر المجموع الاختباري.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- رقم العمل الأسترالي
- معدل الضريبة الهامشية
- الرعاية الصحية الأساسية
- رقم قائمة المشاريع
- المخضرمين في الخدمة
- خصم الضريبة
- الإرجاع الضريبي الفردي
- رقم ملف الضريبة
- tfn

## <a name="austria-drivers-license-number"></a>رقم رخصة القيادة في النمسا

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_austria_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_austria_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Austria Driver's License Number -->
      <Entity id="682f18ce-44eb-482b-8198-2bcb96a0761e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_austria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_austria_eu_drivers_license_number"></a>s_license_number Keywords_austria_eu_driver

- فهررشين
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern

## <a name="austria-identity-card"></a>بطاقة هوية النمسا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

مجموعة مكونة من 24 حرفا من الأحرف والأرقام والأحرف الخاصة

### <a name="pattern"></a>نمط

24 حرفا:

- 22 حرفا (غير حساسة لحالة الأحرف) أو أرقام أو خطوط مائلة عكسية أو شرطة مائلة للأمام أو علامات الجمع

- حرفان (غير حساسين لحالة الأحرف) أو أرقام أو شرطة مائلة عكسية أو شرطة مائلة للأمام أو علامات الجمع أو علامات التساوي

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_austria_eu_national_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_austria_eu_national_id_card` .

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- رقم الهوية
- المعرف الوطني
- personalausweis republik österreich

## <a name="austria-passport-number"></a>رقم جواز سفر النمسا

### <a name="format"></a>تنسيق

حرف واحد متبوعا بمسافة اختيارية وسبعة أرقام

### <a name="pattern"></a>نمط

تركيبة مكونة من حرف واحد وسبعة أرقام ومسافة واحدة:

- حرف واحد (غير حساس لحالة الأحرف)
- مسافة واحدة (اختياري)
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_austria_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_austria_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_austria_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_austria_eu_passport_number` تم العثور عليها.

```xml
      <!-- Austria Passport Number -->
      <Entity id="1c96ae4e-303b-447d-86c7-77113ac266bf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_austria_eu_passport_number"></a>Keywords_austria_eu_passport_number

- reisepassnummer
- إعادة الدفع
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- رقم المرور
- reisepässe

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="austria-physical-addresses"></a>العناوين المادية في النمسا

يكشف هذا الكيان المسمى غير الملغى عن الأنماط المتعلقة بالعنوان الفعلي من النمسا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="austria-social-security-number"></a>رقم الضمان الاجتماعي في النمسا

### <a name="format"></a>تنسيق

10 أرقام بالتنسيق المحدد

### <a name="pattern"></a>نمط

10 أرقام:

- ثلاثة أرقام تتوافق مع رقم تسلسلي
- خانة اختيار واحدة
- ستة أرقام تتوافق مع تاريخ الميلاد (DDNAMY)

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_austria_eu_ssn_or_equivalent` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_austria_eu_ssn_or_equivalent` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_austria_eu_ssn_or_equivalent` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Austria Social Security Number -->
      <Entity id="6896a906-86c9-4d19-a2da-6e43ccd19b7b" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_austria_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_austria_eu_telephone_number" />
            <Match idRef="Keywords_austria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- ssn في
- رقم ehic
- ehic no
- رمز التأمين
- رمز التأمين #
- رقم التأمين
- لا يوجد تأمين
- كرينكينكاسينومر
- كرينكينفيرسيشيرونغ
- الأمن الاجتماعي
- الأمن الاجتماعي #
- الضمان الاجتماعي لا
- رقم الضمان الاجتماعي
- رمز الضمان الاجتماعي
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- Ssn #
- Ssn
- versicherungscode
- versicherungsnummer
- zdveno zavarovanje

## <a name="austria-tax-identification-number"></a>رقم التعريف الضريبي في النمسا

### <a name="format"></a>تنسيق

تسعة أرقام مع واصلة اختيارية وشرطة مائلة للأمام

### <a name="pattern"></a>نمط

تسعة أرقام مع واصلة اختيارية ومائلة للأمام:

- رقمين
- واصلة (اختيارية)
- ثلاثة أرقام
- شرطة مائلة للأمام (اختيارية)
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_austria_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_austria_eu_tax_file_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_austria_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Austria Tax Identification Number -->
      <Entity id="4fd58d22-af28-4451-b18a-6f722430a56d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
          <Match idRef="Keywords_austria_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- österreich
- st.nr.
- رقم عمودي
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- رقم الضريبة

## <a name="austria-value-added-tax"></a>ضريبة القيمة المضافة في النمسا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نقش أبجدي رقمي مكون من 11 حرفا

### <a name="pattern"></a>نمط

نمط أبجدي رقمي مكون من 11 حرفا:

- A أو a
- T أو t
- مساحة اختيارية
- U أو u
- مساحة اختيارية
- رقمان أو ثلاثة أرقام
- مساحة اختيارية
- أربعة أرقام
- مساحة اختيارية
- رقم واحد أو رقمين

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Austria_Value_Added_Tax عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_Austria_Value_Added_Tax.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Austria_Value_Added_Tax عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Austria Value Added Tax -->
      <Entity id="b6a3eda2-c56c-4b69-a5f7-dca34db00f48" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
          <Match idRef="Keyword_Austria_Value_Added_Tax" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- رقم ضريبة القيمة المضافة
- ضريبه القيمه المضافه #
- رقم ضريبة القيمة المضافة في الولايات المتحدة الأمريكية
- رقم ضريبة القيمة المضافة.
- vatno #
- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة في الولايات المتحدة الأمريكية
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- رقم تعريف ضريبة القيمة المضافة
- رقم عمودي
- رقم uid

## <a name="azure-documentdb-auth-key"></a>مفتاح مصادقة Azure DocumentDB

### <a name="format"></a>تنسيق

السلسلة "DocumentDb" متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه.

### <a name="pattern"></a>نمط

- السلسلة "DocumentDb"
- أي تركيبة بين 3-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- رمز أكبر من (>) أو علامة التساوي (=) أو علامة اقتباس (") أو علامة اقتباس أحادية (')
- أي تركيبة من 86 حرفا صغيرا أو أحرفا كبيرة أو رقما أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- اثنين من علامات التساوي (=)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzureDocumentDBAuthKey عن المحتوى الذي يتطابق مع النمط.
- لا يعثر التعبير العادي CEP_CommonExampleKeywords على محتوى يطابق النمط.

```xml
<!-- Azure Document DB Auth Key -->
<Entity id="0f587d92-eb28-44a9-bd1c-90f2892b47aa" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureDocumentDBAuthKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
          </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(من الناحية الفنية، يعرف نوع المعلومات الحساسة هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي

## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>سلسلة اتصال قاعدة بيانات Azure IAAS وسلسلة اتصال azure SQL

### <a name="format"></a>تنسيق

السلسلة "Server" أو "server" أو "data source" متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة "cloudapp.azure.<!--no-hyperlink-->com" أو "cloudapp.azure.<!--no-hyperlink-->net" أو "database.windows.<!--no-hyperlink-->net"، والسلسلة "Password" أو "password" أو "pwd".

### <a name="pattern"></a>نمط

- السلسلة "Server" أو "server" أو "data source"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "cloudapp.azure.<!--no-hyperlink-->com"، "cloudapp.azure.<!--no-hyperlink-->net"، أو "database.windows.<!--no-hyperlink-->net"
- أي تركيبة بين 1-300 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "Password" أو "password" أو "pwd"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- حرف واحد أو أكثر ليس فاصلة منقوطة (;) أو علامة اقتباس (") أو فاصلة فاصلة أحادية (')
- فاصلة منقوطة (;) أو علامة اقتباس (") أو فاصلة فاصلة أحادية (')

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzureConnectionString عن المحتوى الذي يتطابق مع النمط.
- لا يعثر التعبير العادي CEP_CommonExampleKeywords على محتوى يطابق النمط.

```xml
<!--Azure IAAS Database Connection String and Azure SQL Connection String-->
<Entity id="ce1a126d-186f-4700-8c0c-486157b953fd" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(من الناحية الفنية، يعرف نوع المعلومات الحساسة هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي

## <a name="azure-iot-connection-string"></a>سلسلة اتصال Azure IoT

### <a name="format"></a>تنسيق

السلسلة "HostName" متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلاسل "azure-devices.<!--no-hyperlink-->net" و"SharedAccessKey".

### <a name="pattern"></a>نمط

- السلسلة "HostName"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "azure-devices.<!--no-hyperlink-->net"
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "SharedAccessKey"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة من 43 حرفا صغيرا أو أحرفا كبيرة أو رقما أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- علامة التساوي (=)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzureIoTConnectionString عن المحتوى الذي يتطابق مع النمط.
- لا يعثر التعبير العادي CEP_CommonExampleKeywords على محتوى يطابق النمط.

```xml
<!--Azure IoT Connection String-->
<Entity id="0b34bec3-d5d6-4974-b7b0-dcdb5c90c29d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureIoTConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

يعرف نوع المعلومات الحساسة هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي

## <a name="azure-publish-setting-password"></a>كلمة مرور إعداد نشر Azure

### <a name="format"></a>تنسيق

السلسلة "userpwd=" متبوعة بسلسلة أبجدية رقمية.

### <a name="pattern"></a>نمط

- السلسلة "userpwd="
- أي تركيبة من 60 حرفا صغيرا أو رقما
- علامة اقتباس (")

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzurePublishSettingPasswords عن المحتوى الذي يتطابق مع النمط.
- لا يعثر التعبير العادي CEP_CommonExampleKeywords على محتوى يطابق النمط.

```xml
<!--Azure Publish Setting Password-->
<Entity id="75f4cc8a-a68e-49e5-89ce-fa8f03d286a5" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
       <IdMatch idRef="CEP_Regex_AzurePublishSettingPasswords" />
       <Any minMatches="0" maxMatches="0">
           <Match idRef="CEP_CommonExampleKeywords" />
       </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

يعرف نوع المعلومات الحساسة هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي

## <a name="azure-redis-cache-connection-string"></a>سلسلة اتصال ذاكرة التخزين المؤقت ل Azure Redis

### <a name="format"></a>تنسيق

السلسلة "redis.cache.windows.<!--no-hyperlink-->net" متبوعا بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة "password" أو "pwd".

### <a name="pattern"></a>نمط

- السلسلة "redis.cache.windows.<!--no-hyperlink-->net"
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "password" أو "pwd"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة مكونة من 43 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- علامة التساوي (=)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzureRedisCacheConnectionString عن المحتوى الذي يتطابق مع النمط.
- لا يعثر التعبير العادي CEP_CommonExampleKeywords على محتوى يطابق النمط.

```xml
<!--Azure Redis Cache Connection String-->
<Entity id="095a7e6c-efd8-46d5-af7b-5298d53a49fc" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureRedisCacheConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(من الناحية الفنية، يعرف نوع المعلومات الحساسة هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي

## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>تنسيق

السلسلة "sig" متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه.

### <a name="pattern"></a>نمط

- السلسلة "sig"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 43-53 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو علامة النسبة المئوية (٪)
- السلسلة "٪3d"
- أي حرف ليس حرفا أو رقما أو رقما أو علامة النسبة المئوية (٪)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzureSAS عن المحتوى الذي يتطابق مع النمط.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>سلسلة اتصال ناقل خدمة Azure

### <a name="format"></a>تنسيق

السلسلة "EndPoint" متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلاسل "servicebus.windows.<!--no-hyperlink-->net" و"SharedAccesKey".

### <a name="pattern"></a>نمط

- السلسلة "نقطة النهاية"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "servicebus.windows.<!--no-hyperlink-->net"
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "SharedAccessKey"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة مكونة من 43 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- علامة التساوي (=)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzureServiceBusConnectionString عن المحتوى الذي يتطابق مع النمط.
- لا يعثر التعبير العادي CEP_CommonExampleKeywords على محتوى يطابق النمط.

```xml
<!--Azure Service Bus Connection String-->
<Entity id="b9a6578f-a83f-4fcd-bf44-2130bae49a6f" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureServiceBusConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(من الناحية الفنية، يعرف نوع المعلومات الحساسة هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي

## <a name="azure-storage-account-key"></a>مفتاح حساب تخزين Azure

### <a name="format"></a>تنسيق

السلسلة "DefaultEndpointsProtocol" متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة "AccountKey".

### <a name="pattern"></a>نمط

- السلسلة "DefaultEndpointsProtocol"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "AccountKey"
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة مكونة من 86 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- اثنين من علامات التساوي (=)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzureStorageAccountKey عن المحتوى الذي يتطابق مع النمط.
- لا يعثر التعبير العادي CEP_AzureEmulatorStorageAccountFilter على محتوى يطابق النمط.
- لا يعثر التعبير العادي CEP_CommonExampleKeywords على محتوى يطابق النمط.

```xml
<!--Azure Storage Account Key-->
<Entity id="c7bc98e8-551a-4c35-a92d-d2c8cda714a7" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_AzureEmulatorStorageAccountFilter" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

(من الناحية الفنية، يعرف نوع المعلومات الحساسة هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(من الناحية الفنية، يعرف نوع المعلومات الحساسة هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي

## <a name="azure-storage-account-key-generic"></a>مفتاح حساب Azure Storage (عام)

### <a name="format"></a>تنسيق

أي تركيبة مكونة من 86 حرفا صغيرا أو أحرفا كبيرة أو رقما أو شرطة مائلة للأمام (/) أو علامة الجمع (+)، مسبوقة أو متبوعة بالأحرف الموضحة في النمط أدناه.

### <a name="pattern"></a>نمط

- من صفر إلى واحد من الرمز الأكبر (>) أو علامة اقتباس أحادية (') أو علامة التساوي (=) أو علامة الاقتباس (") أو علامة الرقم (#)
- أي تركيبة مكونة من 86 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- اثنين من علامات التساوي (=)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_AzureStorageAccountKeyGeneric عن المحتوى الذي يتطابق مع النمط.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```

## <a name="belgium-drivers-license-number"></a>رقم رخصة القيادة في بلجيكا

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

10 أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_belgium_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_belgium_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Belgium Driver's License Number -->
      <Entity id="d89fd329-9324-433c-b687-2c37bd5166f3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_belgium_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_belgium_eu_drivers_license_number"></a>s_license_number Keywords_belgium_eu_driver

- rijbewijs
- rijbewijsnummer
- führerschein
- führerscheinnummer
- füehrerscheinnummer
- فهررشين
- fuehrerschein
- عدد الفوهررساتشيين
- fuehrerscheinnummer
- permis de conduire
- numéro permis conduire

## <a name="belgium-national-number"></a>الرقم الوطني في بلجيكا

### <a name="format"></a>تنسيق

11 رقما بالإضافة إلى المحددات الاختيارية

### <a name="pattern"></a>نمط

11 رقما بالإضافة إلى المحددات:

- ستة أرقام وفترتان اختياريتان بالتنسيق YY. MM.DD لتاريخ الميلاد
- محدد اختياري من نقطة، شرطة، مسافة
- ثلاثة أرقام متتالية (فردية للذكور، حتى للإناث)
- محدد اختياري من نقطة، شرطة، مسافة
- خانتا اختيار رقميتان

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_belgium_national_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_belgium_national_number.
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_belgium_national_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Belgium National Number -->
       <Entity id="fb969c9e-0fd1-4b18-8091-a2123c5e6a54" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_national_number" />
          <Match idRef="Keyword_belgium_national_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_belgium_national_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- مائل إلى الكسل
- bnn #
- bnn
- carte d'identité
- المعرف الوطني
- تعريفي #
- تحديد الفئة
- تحديد
- تعريف
- رقم معرف
- identifizierung
- الهويات
- هوية
- identiteitskaart
- الهويه
- النقش
- الرقم الوطني
- السجل الوطني
- رقم وطني #
- رقم وطني
- Nif #
- Nif
- numéro d'assuré
- numéro de registre national
- numéro de sécurité
- numéro d'identification
- numéro d'immatriculation
- numéro national
- رقمي #
- رقم المعرف الشخصي
- personalausweis
- رقم شخصي #
- تسجيل الصبر
- التسجيل
- رقم التسجيلات
- registrierung
- رقم الضمان الاجتماعي
- Ssn #
- Ssn
- رقم عمودي
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="belgium-passport-number"></a>رقم جواز سفر بلجيكا

### <a name="format"></a>تنسيق

حرفان متبوعا بستة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرفان متبوعا بستة أرقام

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

 يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_belgium_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_belgium_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date2` العادي عن التاريخ بالتنسيق DD MM YY أو كلمة أساسية من `Keywords_eu_passport_date` أو `Keywords_belgium_eu_passport_number` تم العثور عليها

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_belgium_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_belgium_eu_passport_number` تم العثور عليها.

```xml
      <!-- Belgium Passport Number -->
      <Entity id="d7b1315b-21ca-4774-a32a-596010ff78fd" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
            <Match idRef="Keywords_belgium_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- كارتة منفذ المرور
- Passeport livre
- Pass-Nr
- رقم المرور
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="belgium-physical-addresses"></a>عناوين فعلية لبلكيا

يكتشف هذا الكيان المسمى غير الملغى الأنماط المتعلقة بالعناوين الفعلية من بلجيكا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="belgium-value-added-tax-number"></a>رقم الضريبة للقيمة المضافة في بلجيكا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نقش أبجدي رقمي مكون من 12 حرفا

### <a name="pattern"></a>نمط

نمط أبجدي رقمي مكون من 12 حرفا:

- حرف B أو b
- حرف E أو e
- رقم 0
- رقم من 1 إلى 9
- نقطة اختيارية أو واصلة أو مسافة
- أربعة أرقام
- نقطة اختيارية أو واصلة أو مسافة
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_belgium_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_belgium_value_added_tax_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_belgium_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Belgium Value Added Tax Number -->
      <Entity id="85b5b3c3-f2de-4ae8-ac46-fd3cb38bf9ed" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
          <Match idRef="Keywords_belgium_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
        </Pattern>
      </Entity>
    </Version>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nلاين tva
- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- Btw
- Btw #
- ضريبه القيمه المضافه #

## <a name="blood-test-terms"></a>مصطلحات اختبار الدم

يكشف هذا الكيان المسمى غير المفكك عن المصطلحات المتعلقة باختبارات الدم، مثل *hCG*. وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="brand-medication-names"></a>أسماء أدوية العلامة التجارية

يكشف هذا الكيان المسمى غير المكتظ بأسماء أدوية العلامة التجارية، مثل *Tylenol*. وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="brazil-cpf-number"></a>رقم CPF في البرازيل

### <a name="format"></a>تنسيق

11 رقما تتضمن خانة اختيار ويمكن تنسيقها أو عدم تنسيقها

### <a name="pattern"></a>نمط

تنسيق:

- ثلاثة أرقام
- فترة زمنية
- ثلاثة أرقام
- فترة زمنية
- ثلاثة أرقام
- واصلة
- رقمان يتم التحقق من رقمين

منسق:

- 11 رقما يتم فيها التحقق من الرقمين الأخيرين

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_brazil_cpf عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_brazil_cpf.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_brazil_cpf عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Brazil CPF Number -->
<Entity id="78e09124-f2c3-4656-b32a-c1a132cd2711" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cpf"/>
     <Match idRef="Keyword_brazil_cpf"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cpf"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- الشراكه
- تحديد
- التسجيل
- الايرادات
- Cadastro de Pessoas Físicas
- منتحل إلى
- Identificação
- Inscrição
- Receita

## <a name="brazil-legal-entity-number-cnpj"></a>رقم الكيان القانوني البرازيلي (CNPJ)

### <a name="format"></a>تنسيق

14 رقما تتضمن رقم تسجيل ورقم فرع وخانات اختيار، بالإضافة إلى المحددات

### <a name="pattern"></a>نمط

14 رقما، بالإضافة إلى المحددات:

- رقمين
- فترة زمنية
- ثلاثة أرقام
- فترة زمنية
- ثلاثة أرقام (أول ثمانية أرقام هي رقم التسجيل)
- شرطة مائلة للأمام
- رقم الفرع المكون من أربعة أرقام
- واصلة
- رقمان يتم التحقق من رقمين

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_brazil_cnpj عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_brazil_cnpj.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_brazil_cnpj عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Brazil Legal Entity Number (CNPJ) -->
<Entity id="9b58b5cd-5e90-4df6-b34f-1ebcc88ceae4" recommendedConfidence="85" patternsProximity="300">
   <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cnpj"/>
     <Match idRef="Keyword_brazil_cnpj"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cnpj"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- السجل الوطني للكيانات القانونية
- سجل مهى
- كيان قانوني
- الكيانات القانونية
- حالة التسجيل
- Business
- الشركه
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- CadastroGeral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação cadascad
- Inscrição
- Empresa

## <a name="brazil-national-identification-card-rg"></a>بطاقة تعريف البرازيل الوطنية (RG)

### <a name="format"></a>تنسيق

Registro غيرال (تنسيق قديم): تسعة أرقام

Registro de Identidade (RIC) (تنسيق جديد): 11 رقما

### <a name="pattern"></a>نمط

Registro غيرال (تنسيق قديم):

- رقمين
- فترة زمنية
- ثلاثة أرقام
- فترة زمنية
- ثلاثة أرقام
- واصلة
- رقم واحد هو خانة اختيار

Registro de Identidade (RIC) (تنسيق جديد):

- 10 أرقام
- واصلة
- رقم واحد هو خانة اختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_brazil_rg عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_brazil_rg.
- يمر المجموع الاختباري.

```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- بطاقة هوية
- المعرف الوطني
- número de rregistro
- registro de Iidentidade
- registrogeral
- RG (هذه الكلمة الأساسية حساسة لحالة الأحرف)
- RIC (هذه الكلمة الأساسية حساسة لحالة الأحرف)

## <a name="brazil-physical-addresses"></a>العناوين المادية في البرازيل

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من البرازيل. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="bulgaria-drivers-license-number"></a>رقم رخصة القيادة في بلغاريا

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_bulgaria_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_bulgaria_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Bulgaria Driver's License Number -->
      <Entity id="66d39258-94c2-43b2-804b-aa312258e54b" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_bulgaria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>s_license_number Keywords_bulgaria_eu_driver

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки

## <a name="bulgaria-passport-number"></a>رقم جواز سفر بلغاريا

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_bulgaria_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_bulgaria_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_bulgaria_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_bulgaria_eu_passport_number` تم العثور عليها.

```xml
      <!-- Bulgaria Passport Number -->
      <Entity id="f7172b82-c588-4216-845e-4e54e397f29a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт لا

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="bulgaria-physical-addresses"></a>العناوين المادية لبلغاريا

يكشف هذا الكيان المسمى غير الملغى عن الأنماط المتعلقة بالعنوان الفعلي من بلغاريا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="bulgaria-uniform-civil-number"></a>الرقم المدني الموحد لبلغاريا
يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

10 أرقام بدون مسافات ومحددات

- ستة أرقام تتوافق مع تاريخ الميلاد (YYMMDD)
- رقمان يتوافقان مع أمر الميلاد
- رقم واحد يتوافق مع الجنس: رقم زوجي للذكر ورقم فردي للإناث
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_bulgaria_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_bulgaria_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_bulgaria_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Bulgaria Uniform Civil Number -->
      <Entity id="100d58b1-0a35-4fb1-aa89-e4a86fb53fcc" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Match idRef="Keywords_bulgaria_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_bulgaria_eu_telephone_number" />
            <Match idRef="Keywords_bulgaria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn #
- bnn
- bucn #
- bucn
- edinendanski nomer
- egn #
- egn
- رقم التعريف
- المعرف الوطني
- الرقم الوطني
- رقم وطني #
- رقم وطني
- المعرف الشخصي
- لا شخصي
- رقم شخصي
- رقم شخصي #
- رقم الضمان الاجتماعي
- Ssn #
- Ssn
- معرف مدني موحد
- لا يوجد زي مدني
- رقم مدني موحد
- زيسلنو #
- زيسلنو
- رقم موحد #
- رقم موحد
- رقم جنس فريد
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- униформ المعرف
- униформ граждански id
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #

## <a name="canada-bank-account-number"></a>رقم الحساب البنكي في كندا

### <a name="format"></a>تنسيق

7 أرقام أو 12 رقما

### <a name="pattern"></a>نمط

رقم الحساب البنكي في كندا هو 7 أو 12 رقما.

رقم النقل لحساب كندا البنكي هو:

- خمسة أرقام
- واصلة
- ثلاثة أرقام OR
- صفر "0"
- ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_canada_bank_account_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_canada_bank_account_number.
- يبحث التعبير العادي Regex_canada_bank_account_transit_number عن المحتوى الذي يتطابق مع النمط.

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_canada_bank_account_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_canada_bank_account_number.

```xml
<!-- Canada Bank Account Number -->
<Entity id="552e814c-cb50-4d94-bbaa-bb1d1ffb34de" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
        <Match idRef="Regex_canada_bank_account_transit_number" />
   </Pattern>
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
   </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- مدخرات كندا
- وكالة الإيرادات في كندا
- المؤسسة المالية الكندية
- نموذج الإيداع المباشر
- مواطن أمريكي
- ممثل قانوني
- عام للكاتم
- المفوض لليمين
- ميزة رعاية الأطفال
- الرعاية الشاملة للأطفال
- ميزة ضريبة الأطفال في كندا
- ميزة ضريبة الدخل
- ضريبة المبيعات الموزعة
- رقم التأمين الاجتماعي
- استرداد ضريبة الدخل
- ميزة ضريبة الأطفال
- دفعات/ة
- رقم المؤسسة
- طلب إيداع
- معلومات مصرفية
- الإيداع المباشر

## <a name="canada-drivers-license-number"></a>رقم رخصة القيادة في كندا

### <a name="format"></a>تنسيق

يختلف حسب المقاطعة

### <a name="pattern"></a>نمط

أنماط مختلفة تغطي:

- البرتا
- مقاطعة بريتامبيا البريطانية
- مانيتوبا
- بروناسويك جديد
- نيوفاوندلاند/لابرادور
- نوفا سكوتيا
- اونتاريو
- جزيرة أدوارد الاميرة
- كيبيك
- ساسكاتشوان

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_[province_name]_drivers_license_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_[province_name]_drivers_license_name.
- تم العثور على كلمة أساسية من Keyword_canada_drivers_license.

```xml
<!-- Canada Driver's License Number -->
    <Entity id="37186abb-8e48-4800-ad3c-e3d1610b3db0" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_alberta_drivers_license_number" />
        <Match idRef="Keyword_alberta_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_british_columbia_drivers_license_number" />
        <Match idRef="Keyword_british_columbia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_manitoba_drivers_license_number" />
        <Match idRef="Keyword_manitoba_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_brunswick_drivers_license_number" />
        <Match idRef="Keyword_new_brunswick_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_newfoundland_labrador_drivers_license_number" />
        <Match idRef="Keyword_newfoundland_labrador_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_nova_scotia_drivers_license_number" />
        <Match idRef="Keyword_nova_scotia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_ontario_drivers_license_number" />
        <Match idRef="Keyword_ontario_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_prince_edward_island_drivers_license_number" />
        <Match idRef="Keyword_prince_edward_island_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_quebec_drivers_license_number" />
        <Match idRef="Keyword_quebec_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_saskatchewan_drivers_license_number" />
        <Match idRef="Keyword_saskatchewan_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- اختصار المقاطعة، على سبيل المثال AB
- اسم المقاطعة، على سبيل المثال،"ألبيرا"

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- برنامج تشغيل
- برامج تشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- DriverLicence
- DriverLicences
- Lic برنامج التشغيل
- Lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- رخص القيادة
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- رخصة القيادة
- تراخيص برامج التشغيل
- Lic برامج التشغيل
- Lics برامج التشغيل
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- رخص القيادة
- Lic للسائق
- Lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Lic للسائق
- Lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- رخص القيادة
- برنامج تشغيل sLic
- برامج التشغيل sLics
- رخصة القيادة
- تراخيص برامج التشغيل
- SLicence للسائق
- برامج التشغيل sLicences
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- رخص القيادة
- Permis de Conduire
- id
- معرفات
- رقم بطاقة idcard
- أرقام بطاقات idcard
- بطاقة idcard #
- #s بطاقة idcard
- بطاقة بطاقة idcard
- بطاقات بطاقة idcard
- بطاقة idcard
- رقم التعريف
- أرقام التعريف
- تحديد #
- #s التعريف
- بطاقة التعريف
- بطاقات التعريف
- تحديد
- DL #
- DLS #
- CDL #
- CDLS #
- برنامج تشغيل #
- برامج تشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- DriverLicence #
- DriverLicences #
- Lic برنامج التشغيل #
- Lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برنامج التشغيل #
- رخص القيادة #
- DriversLic #
- DriversLics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- DriversLicence #
- DriversLicences #
- Lic برامج التشغيل #
- Lics برامج التشغيل #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- رخص القيادة #
- Lic للسائق #
- Lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- Lic للسائق #
- Lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- رخص القيادة #
- برنامج تشغيل sLic #
- برامج التشغيل sLics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- SLicence للسائق #
- برامج التشغيل sLicences #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- رخص القيادة #
- Permis de Conduire #
- معرف #
- معرفات #
- بطاقة بطاقة idcard #
- بطاقات بطاقة idcard #
- بطاقة idcard #
- بطاقة التعريف #
- بطاقات التعريف #
- تحديد #

## <a name="canada-health-service-number"></a>رقم خدمة الصحة في كندا

### <a name="format"></a>تنسيق

 10 أرقام

### <a name="pattern"></a>نمط

10 أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_canada_health_service_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_canada_health_service_number.

```xml
<!-- Canada Health Service Number -->
<Entity id="59c0bf39-7fab-482c-af25-00faa4384c94" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_health_service_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_health_service_number" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- رقم الحماية الشخصية
- معلومات المريض
- الخدمات الصحية
- خدمات التخصص
- حادث سيارة
- مستشفى المرضى
- طبيب نفسي
- تعويض العمال
- الاعاقه

## <a name="canada-passport-number"></a>رقم جواز سفر كندا

### <a name="format"></a>تنسيق

حرفان من الأحرف الكبيرة متبوعا بستة أرقام

### <a name="pattern"></a>نمط

حرفان من الأحرف الكبيرة متبوعا بستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_canada_passport_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_canada_passport_number أو Keyword_passport.

```xml
<!-- Canada Passport Number -->
<Entity id="14d0db8b-498a-43ed-9fca-f6097ae687eb" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_passport_number" />
          <Match idRef="Keyword_passport" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- المواطنين الكنديين
- جواز سفر كندا
- طلب جواز سفر
- صور جواز السفر
- مترجم معتمد
- المواطنين الكنديين
- أوقات المعالجة
- تطبيق التجديد

#### <a name="keyword_passport"></a>Keyword_passport

- رقم جواز السفر
- رقم جواز السفر
- جواز السفر #
- جواز السفر #
- معرف جواز السفر
- Passportno
- رقم جواز السفر
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n °
- Passeport Non
- منفذ المرور #
- منفذ المرور #
- PasseportNon
- Passeportn °

## <a name="canada-personal-health-identification-number-phin"></a>رقم التعريف الصحي الشخصي لكندا (PHIN)

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_canada_phin عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمتين أساسيتين على الأقل من Keyword_canada_phin أو Keyword_canada_provinces.

```xml
<!-- Canada PHIN -->
<Entity id="722e12ac-c89a-4ec8-a1b7-fea3469f89db" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_phin" />
        <Any minMatches="2">
          <Match idRef="Keyword_canada_phin" />
          <Match idRef="Keyword_canada_provinces" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- رقم التأمين الاجتماعي
- قانون المعلومات الصحية
- معلومات ضريبة الدخل
- صحة مانيتوبا
- التسجيل الصحي
- مشتريات وصفة طبية
- الأهلية للاستفادة
- الصحة الشخصية
- قوة الوكيل
- رقم التسجيل
- رقم الحماية الشخصية
- إحالة ممارس
- محترف الكفاءة
- إحالة المريض
- الصحة والصحة

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- نونافوت
- كيبيك
- المناطق الشمالية الغربية
- اونتاريو
- مقاطعة بريتامبيا البريطانية
- البرتا
- ساسكاتشوان
- مانيتوبا
- يوكون
- نيوفاوندلاند ولابرادور
- بروناسويك جديد
- نوفا سكوتيا
- جزيرة أدوارد الاميرة
- كندا

## <a name="canada-physical-addresses"></a>العناوين الفعلية لكندا

يكشف هذا الكيان المسمى غير المضني عن الأنماط المتعلقة بالعنوان الفعلي من كندا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="canada-social-insurance-number"></a>رقم التأمين الاجتماعي في كندا

### <a name="format"></a>تنسيق

تسعة أرقام مع واصلات اختيارية أو مسافات

### <a name="pattern"></a>نمط

تنسيق:

- ثلاثة أرقام
- واصلة أو مسافة
- ثلاثة أرقام
- واصلة أو مسافة
- ثلاثة أرقام

غير منسق: تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_canadian_sin عن المحتوى الذي يتطابق مع النمط.
- على الأقل نمطان من الأنماط التالية:
    - تم العثور على كلمة أساسية من Keyword_sin.
    - تم العثور على كلمة أساسية من Keyword_sin_collaborative.
    - تبحث الدالة Func_eu_date عن تاريخ بتنسيق التاريخ الصحيح.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_unformatted_canadian_sin عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_sin.
- يمر المجموع الاختباري.

```xml
<!-- Canada Social Insurance Number -->
<Entity id="a2f29c85-ecb8-4514-a610-364790c0773e" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_canadian_sin" />
        <Any minMatches="2">
          <Match idRef="Keyword_sin" />
          <Match idRef="Keyword_sin_collaborative" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_canadian_sin" />
        <Match idRef="Keyword_sin" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_sin"></a>Keyword_sin

- الخطيئه
- التأمين الاجتماعي
- numero d'assurance sociale
- الخطايا
- Ssn
- ssns
- الضمان الاجتماعي
- numero d'assurance social
- رقم التعريف الوطني
- المعرف الوطني
- الخطيئه #
- soc ins
- ins الاجتماعية

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- رخصة القيادة
- رخصه
- رخصة القيادة
- رخصة القيادة
- دوب
- تاريخ الميلاد
- عيد ميلاد
- تاريخ الميلاد

## <a name="chile-identity-card-number"></a>رقم بطاقة هوية تشيلي

### <a name="format"></a>تنسيق

من سبعة إلى ثمانية أرقام بالإضافة إلى تحديد خانة اختيار أو حرف

### <a name="pattern"></a>نمط

من سبعة إلى ثمانية أرقام بالإضافة إلى المحددات:

- رقم إلى رقمين
- فترة اختيارية
- ثلاثة أرقام
- فترة اختيارية
- ثلاثة أرقام
- شرطة
- رقم واحد أو حرف واحد (غير حساس لحالة الأحرف) وهو رقم اختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_chile_id_card عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_chile_id_card.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_chile_id_card عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Chile Identity Card Number -->
<Entity id="4e979794-49a0-407e-a0b9-2c536937b925" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_chile_id_card"/>
     <Match idRef="Keyword_chile_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_chile_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- التعريف الوطني
- رقم التعريف الوطني
- المعرف الوطني
- número de identificación nacional
- rol único nacional
- rol único tributario
- تشغيل
- شبق
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- تشغيل #
- شبق #
- nationaluniqueroleID #
- معرف nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad numero
- رقم الهوية الزكية.
- رقم الهوية الزيلية
- الهوية الزيلية #
- سجل الضريبة الفريد
- دور الفرز الفريد
- دور الضريبة الفريد
- رقم الفرز الفريد
- رقم وطني فريد
- دور وطني فريد
- الدور الفريد الوطني
- رقم هوية تشيلي.
- رقم هوية تشيلي
- هوية تشيلي #
- R.U.T
- R.U.N

## <a name="china-resident-identity-card-prc-number"></a>رقم بطاقة هوية مقيمة في الصين (PRC)

### <a name="format"></a>تنسيق

18 رقما

### <a name="pattern"></a>نمط

18 رقما:

- ستة أرقام هي رمز عنوان
- ثمانية أرقام في نموذج YYYYMMDD، وهي تاريخ الميلاد
- ثلاثة أرقام هي رمز طلب
- رقم واحد هو خانة اختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_china_resident_id عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_china_resident_id.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_china_resident_id عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- China Resident Identity Card (PRC) Number -->
<Entity id="c92daa86-2d16-4871-901f-816b3f554fc1" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_china_resident_id"/>
     <Match idRef="Keyword_china_resident_id"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_china_resident_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- بطاقة هوية مقيمة
- PRC
- بطاقة التعريف الوطنية
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定

## <a name="credit-card-number"></a>رقم بطاقة الائتمان

### <a name="format"></a>تنسيق

من 14 إلى 19 رقما يمكن تنسيقها أو عدم تنسيقها (ddddddddd) والتي يجب أن تجتاز اختبار Luhn.

### <a name="pattern"></a>نمط

الكشف عن البطاقات من جميع العلامات التجارية الرئيسية في جميع أنحاء العالم، بما في ذلك فيز، و MasterCard، وD discover Card، وJCB، و American Express، وبطاقات الهدايا، وبطاقات diner، و Rupay و China UnionPay.

### <a name="checksum"></a>المجموع الاختباري

نعم، التحقق من Luhn

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_credit_card عن المحتوى الذي يتطابق مع النمط.
- أحد الشروط التالية صحيح:
  - تم العثور على كلمة أساسية من Keyword_cc_verification.
  - تم العثور على كلمة أساسية من Keyword_cc_name.
  - تبحث الدالة Func_expiration_date عن تاريخ بتنسيق التاريخ الصحيح.
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_credit_card عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Credit Card Number -->
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_credit_card" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- التحقق من البطاقة
- رقم تعريف البطاقة
- cvn
- سيد
- cvc2
- cvv2
- كتلة تثبيت
- رمز الأمان
- رقم الأمان
- رقم الأمان
- رقم المشكلة
- المشكلة رقم
- صورة مشفرة
- numéro de sécurité
- numero de securite
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- prufziffer
- sicherheits Kode
- sicherheitscode
- رقم sicherheits
- verfalldatum
- codice di verifica
- القد. sicurezza
- cod sicurezza
- n autorizzzzzzone
- código
- الكدقل
- القد. ثواني
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- القد. seguranca
- القد. segurança
- cód. seguranca
- cód segurança
- cod seguranca
- cod segurança
- cód seguranca
- número de verificação
- numero de verificaero
- ablauf
- gültig bis
- gültigkeitsdatum
- gultig bis
- gultigkeitsdatum
- scadenza
- scad البيانات
- fecha de expiracion
- fecha de venc
- vencimiento
- válido hasta
- valido hasta
- vto
- data de expiração
- data de expira تاريخ انتهاء الصلاحية
- انتهاء صلاحية البيانات em que
- صالح
- بساله
- vencimento
- المعاملات
- رقم المعاملة
- رقم المرجع
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- اميكس
- american express
- americanexpress
- americano espresso
- فيزا
- ماستركارد
- البطاقة الرئيسية
- Mc
- بطاقات رئيسية
- البطاقات الرئيسية
- نادي العشاء
- نادي diners
- dinersclub
- اكتشاف
- اكتشاف البطاقة
- بطاقة الاكتشاف
- اكتشاف البطاقات
- JCB
- علامة تجارية
- مكتب البطاقات اليابانية
- كرونة دوارة
- الذبذبة
- بطاقة ائتمان
- Cc #
- نسخة#:

- تاريخ انتهاء الصلاحية
- تاريخ exp
- تاريخ انتهاء الصلاحية
- تاريخ انتهاء الصلاحية
- تاريخ الا exp
- انتهاء صلاحية التاريخ
- بطاقة بنكية
- بانككارد
- رقم البطاقة
- رقم البطاقة
- رقم البطاقة
- أرقام البطاقات
- أرقام البطاقات
- بطاقة ائتمان
- بطاقات الائتمان
- بطاقات الائتمان
- نسخة من نسخة
- حامل البطاقة
- حامل البطاقه
- حاملو البطاقات
- حاملو البطاقات
- التحقق من البطاقة
- بطاقة اختيار
- التحقق من البطاقات
- بطاقات اختيار
- بانككارد
- بطاقة خصم
- بطاقات الخصم
- بطاقات الخصم
- بطاقة جهاز atm
- بطاقة atmcard
- بطاقات ال atm
- بطاقات atmcard
- enroute
- طريقها
- نوع البطاقة
- Cardmember Acct
- حساب cardmember
- Cardno
- بطاقة الشركة
- بطاقات الشركة
- نوع البطاقة
- رقم حساب البطاقة
- حساب عضو البطاقة
- Cardmember Acct.
- رقم البطاقة.
- رقم البطاقة
- رقم البطاقة
- قافزة دوارة
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nانهارس دي لا كارت
- nاصفة من نوع carte
- kreditkarte
- الكارتي
- karteninhaber
- كارتينهارس
- kreditkartenin fisherer
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr
- كرتنمر
- kreditkartennummer
- kreditkarten-nummer
- carta di credito
- carta credito
- ن. كارتا
- n carta
- Nr. كارتا
- nr carta
- numero carta
- numero della carta
- numero di carta
- tarjeta credito
- tarjeta de credito
- tarjeta crédito
- tarjeta de crédito
- tarjeta de atm
- أجهزة atm في tarjeta
- tarjeta debito
- tarjeta de debito
- tarjeta débito
- tarjeta de débito
- nاصفة de tarjeta
- لا. de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjetahabiente
- cartão de crédito
- cartão de credito
- cartao de crédito
- cartao de credito
- cartão de débito
- cartao de débito
- cartão de debito
- cartao de debito
- débito automático
- الدينو تلقائي
- número do cartão
- numero do cartão
- número do cartao
- numero do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nلاسم do cartão
- nلاهي do cartao
- nلاين. do cartão
- no do cartão
- لا يوجد قرطاو
- لا. do cartão
- لا. do cartao
- rupay
- الدفع الموحد
- الدفع الموحد
- diner's
- داينرز
- クレジットカード番号
- クレジットカードナンバー
- クレジットカード＃
- クレジットカード
- クレジット
- クレカ
- カード番号
- カードナンバー
- カード＃
- アメックス
- アメリカンエクスプレス
- アメリカン エクスプレス
- الفيزاカード
- الفيزا カード
- マスターカード
- マスター カード
- マスター
- ダイナースクラブ
- ダイナース クラブ
- ダイナース
- 有効期限
- 期限
- キャッシュカード
- キャッシュ カード
- カード名義人
- カードの名義人
- カードの名義
- デビット カード
- デビットカード
- 中国银联
- 银联

## <a name="croatia-drivers-license-number"></a>رقم رخصة القيادة في كرواتيا

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_croatia_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_croatia_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Croatia Driver's License Number -->
      <Entity id="005b3ef1-47dd-4e68-bb02-c6db484d00f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_croatia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_croatia_eu_drivers_license_number"></a>s_license_number Keywords_croatia_eu_driver

- vozaصka dozvola
- voza rangke dozvole

## <a name="croatia-identity-card-number"></a>رقم بطاقة هوية كرواتية

يتم تضمين هذا الكيان في نوع المعلومات الحساسة لرقم التعريف الوطني للاتحاد الأوروبي. وهي متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>نمط

تسعة أرقام متتالية

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_croatia_id_card عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_croatia_id_card.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj građana
- رقم مواطن رئيسي
- nacionalni identifikacijski broj
- رقم التعريف الوطني
- oib #
- oib
- osobna iskaznica
- معرف osobni
- osobni identifikacijski broj
- رقم التعريف الشخصي
- بوارياني بروج
- porezni identifikacijski broj
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="croatia-passport-number"></a>رقم جواز سفر بورتواني

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_croatia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_croatia_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_croatia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_croatia_eu_passport_number` تم العثور عليها.

```xml
      <!-- Croatia Passport Number -->
      <Entity id="7d7a729d-32d8-4204-8d01-d5e6a6c25581" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- فرع. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>رقم التعريف الشخصي لكرواتيا (OIB)

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>نمط

11 رقما:

- 10 أرقام
- الرقم الأخير هو خانة اختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_croatia_oib_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_croatia_eu_tax_file_number.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_croatia_oib_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
      <!-- Croatia Personal Identification (OIB) Number -->
      <Entity id="31983b6d-db95-4eb2-a630-b44bd091968d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_croatia_oib_number" />
          <Match idRef="Keywords_croatia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_croatia_oib_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstorski broj građana
- رقم مواطن رئيسي
- nacionalni identifikacijski broj
- رقم التعريف الوطني
- oib #
- oib
- osobna iskaznica
- معرف osobni
- osobni identifikacijski broj
- رقم التعريف الشخصي
- بوارياني بروج
- porezni identifikacijski broj
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="croatia-physical-addresses"></a>عناوين مادية لكرواتيا

يكشف هذا الكيان المسمى غير المحمل عنايات عن الأنماط المتعلقة بالعنوان الفعلي من كرواتيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="cyprus-drivers-license-number"></a>رقم ترخيص برامج التشغيل في البرنامج الرئيسي

### <a name="format"></a>تنسيق

12 رقما بدون مسافات ومحددات

### <a name="pattern"></a>نمط

12 رقما

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_cyprus_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_cyprus_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Cyprus Driver's License Number -->
      <Entity id="356fa104-f9ac-4aff-a0e4-2e6e65ea06c4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_cyprus_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>s_license_number Keywords_cyprus_eu_driver

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης

## <a name="cyprus-identity-card"></a>بطاقة هوية للسينية

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

10 أرقام

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_cyprus_eu_national_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_cyprus_eu_national_id_card` .

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- رقم بطاقة المعرف
- رقم بطاقة الهوية
- kimlik karti
- رقم التعريف الوطني
- رقم المعرف الشخصي
- ταυτοτητασ

## <a name="cyprus-passport-number"></a>رقم جواز سفر سفر قبطي

### <a name="format"></a>تنسيق

حرف واحد متبوعا ب 6-8 أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرف واحد متبوعا بستة إلى ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_cyprus_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_cyprus_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_cyprus_eu_passport_date` العادي عن التاريخ بالتنسيق DD/MM/YYYY أو تم العثور على كلمة أساسية منه `Keywords_cyprus_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_cyprus_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_cyprus_eu_passport_number` تم العثور عليها.

```xml
      <!-- Cyprus Passport Number -->
      <Entity id="9193e2e8-7f8c-43c1-a274-ac40d651936f" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_cyprus_eu_passport_date" />
            <Match idRef="Keywords_cyprus_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- pandaportu
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- Pandaport Kimlii
- pandaport numarası
- رقم Pwaport.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- تنتهي الصلاحية في
- تم الإصدار في

## <a name="cyprus-physical-addresses"></a>العناوين المادية للسينية

يكشف هذا الكيان المسمى غير الملغى عن الأنماط المتعلقة بالعنوان الفعلي من أداة «المعالجة الفعلية». كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="cyprus-tax-identification-number"></a>رقم التعريف الضريبي للسريبة

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

ثمانية أرقام وحرف واحد في النمط المحدد

### <a name="pattern"></a>نمط

ثمانية أرقام وحرف واحد:

- a "0" أو "9"
- سبعة أرقام
- حرف واحد (غير حساس لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_cyprus_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_cyprus_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_cyprus_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Cyprus Tax Identification Number -->
      <Entity id="40e64bd9-55f3-4a09-9bd6-1db18dced9dd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
          <Match idRef="Keywords_cyprus_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- معرف الضريبة
- رمز التعريف الضريبي
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- عره #
- عره
- معرف الصفيح
- رقم الصفيح
- القصدير #
- vergi kimlik kodu
- vergi kimlik numarası
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού

## <a name="czech-drivers-license-number"></a>رقم رخصة القيادة التشيكية

### <a name="format"></a>تنسيق

حرفان متبوعا بستة أرقام

### <a name="pattern"></a>نمط

ثمانية أحرف وأرقام:

- الحرف 'E' (غير حساس لحالة الأحرف)
- رسالة
- مسافة (اختياري)
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_czech_republic_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_czech_republic_eu_driver's_license_number` تم العثور عليها.

```xml
      <Entity id="86b40d3b-d8ea-4c36-aab0-ef9416a6769c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_czech_republic_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>s_license_number Keywords_czech_republic_eu_driver

- řidiîsk  prúkaz
- řidiîské průkazy
- îíslo řidiîského průkazu
- îísla řidiskůkazů

## <a name="czech-passport-number"></a>رقم جواز السفر التشيكي

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

ثمانية أرقام بدون مسافات أو محددات

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_czech_republic_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_czech_republic_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_czech_republic_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_czech_republic_eu_passport_number` تم العثور عليها.

```xml
      <!-- Czech Republic Passport Number -->
      <Entity id="7bcd8ce8-5e92-4bbe-bc92-fa669f0369fa" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cestovní pas
- ííslo pasu
- cestovní pasu
- لا يوجد منفذ مرور
- íísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="czech-personal-identity-number"></a>رقم الهوية الشخصية التشيكية

### <a name="format"></a>تنسيق

تسعة أرقام مع شرطة مائلة للأمام اختيارية (تنسيق قديم)

10 أرقام مع شرطة مائلة للأمام اختيارية (تنسيق جديد)

### <a name="pattern"></a>نمط

تسعة أرقام (تنسيق قديم):

- ستة أرقام تمثل تاريخ الميلاد
- شرطة مائلة للأمام اختيارية
- ثلاثة أرقام

10 أرقام (تنسيق جديد):

- ستة أرقام تمثل تاريخ الميلاد
- شرطة مائلة للأمام اختيارية
- أربعة أرقام حيث الرقم الأخير هو خانة اختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_czech_id_card عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_czech_id_card.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_czech_id_card_new_format عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Czech Personal Identity Number -->
      <!-- Czech Personal Identity Number -->
      <Entity id="60c0725a-4eb6-455b-9dda-05d8a7396497" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_czech_id_card" />
          <Match idRef="Keyword_czech_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.3000.000">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Func_czech_id_card_new_format" />
          </Pattern>
        </Version>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- رقم الميلاد
- معرف جمهورية تشيكيا
- تشيكيدنو #
- daňové îíslo
- identifikaíní ííslo
- لا هوية
- رقم الهوية
- identityno #
- identityno
- رقم التأمين
- رقم التعريف الوطني
- رقم وطني #
- الرقم الوطني
- osobní ííslo
- رقم شخصي #
- رقم المعرف الشخصي
- رقم التعريف الشخصي
- رقم شخصي
- Pid #
- Pid
- pojiîtění îíslo
- rč
- rodne cislo
- rodné ííslo
- Ssn
- Ssn #
- رقم الضمان الاجتماعي
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- رقم تعريف فريد

## <a name="czech-republic-physical-addresses"></a>العناوين المادية للتشيك

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من جمهورية تشيكيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="denmark-drivers-license-number"></a>رقم رخصة القيادة في الدانمارك

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_denmark_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_denmark_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Denmark Driver's License Number -->
      <Entity id="98a95812-6203-451a-a220-d39870ebef0e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_denmark_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_denmark_eu_drivers_license_number"></a>s_license_number Keywords_denmark_eu_driver

- kørekort
- kørekortnummer

## <a name="denmark-passport-number"></a>رقم جواز سفر الدانمارك

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_denmark_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_denmark_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date2` العادي عن التاريخ بالتنسيق DD MM YY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_denmark_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_denmark_eu_passport_number` تم العثور عليها.

```xml
      <!-- Denmark Passport Number -->
      <Entity id="25e8c47e-e6fe-4884-a211-74898f8c0196" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- رقم pasnummer
- Passeport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="denmark-personal-identification-number"></a>رقم التعريف الشخصي للدانمرك

### <a name="format"></a>تنسيق

10 أرقام تحتوي على واصلة

### <a name="pattern"></a>نمط

10 أرقام:

- ستة أرقام بتنسيق DD ولاي، وهي تاريخ الميلاد
- مسافة اختيارية أو واصلة اختيارية
- أربعة أرقام حيث الرقم النهائي هو خانة اختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Func_denmark_eu_tax_file_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_denmark_id.
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير العادي Func_denmark_eu_tax_file_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Denmark Personal Identification Number -->
    <!-- Denmark Personal Identification Number -->
      <Entity id="6c4f2fef-56e1-4c00-8093-88d7a01cf460" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
          <Match idRef="Keyword_denmark_id" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- مسجل شخصية مركزي
- نظام تسجيل السجل المدني
- Cpr
- Cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- بطاقة صحية
- رقم بطاقة التأمين الصحي
- رقم التأمين الصحي
- رقم التعريف
- رقم معرف
- رقم معرف #
- رقم الهوية
- كرينكينكاسينومر
- معرف وطني #
- رقم وطني #
- الرقم الوطني
- رقم شخصي #
- كيان شخصي #
- رقم المعرف الشخصي
- رقم الشخص
- رقم الشخص #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- Ssn
- Ssn #
- معرف skat
- skat kode
- nummer للتزلج
- skattenummer
- رقم الضمان الاجتماعي
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- رمز الضريبة
- بطاقة التأمين الصحي السفر
- uniqueidentityno #
- رقم الضريبة
- رقم التسجيل الضريبي
- معرف الضريبة
- رقم التعريف الضريبي
- سيارة أجرة #
- رقم الضريبة #
- رقم الضريبة
- الضريبة #
- رقم الضريبة
- رقم التعريف الضريبي
- القصدير #
- سيارة أجرة #
- رقم سيارة أجرة #
- رقم الضريبة #
- معرف الصفيح
- رقم الصفيح
- cpr.nr
- cprnr
- cprnummer
- شخص
- تسجيل شخص
- sygesikringsbevis
- sygesikringsbevisnr
- sygesikringsbevisnummer
- sygesikringskort
- sygesikringskortnr
- sygesikringskortnummer
- sygesikringsnr
- sygesikringsnummer

## <a name="denmark-physical-addresses"></a>عناوين الدانمارك المادية

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من الدانمارك. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="diseases"></a>الامراض

يكشف هذا الكيان المسمى غير الملغى عن النص الذي يطابق أسماء الأمراض، مثل *مرض السكري*. وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="drug-enforcement-agency-dea-number"></a>رقم وكالة إنفاذ مكافحة الأدوية (DEA)

### <a name="format"></a>تنسيق

حرفان متبوعا بسبعة أرقام

### <a name="pattern"></a>نمط

يجب أن يتضمن النمط كل ما يلي:

- حرف واحد (غير حساس لحالة الأحرف) من هذه المجموعة من الأحرف المحتملة: A/B/F/G/M/P/R، وهو رمز مسجل
- حرف واحد (غير حساس لحالة الأحرف)، وهو الحرف الأول من اسم عائلة المسجل أو رقمه '9'
- سبعة أرقام، آخرها رقم الاختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_dea_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من `Keyword_dea_number`
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_dea_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
    <!-- DEA Number -->
    <Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_dea_number" />
      </Pattern>
      <Version minEngineVersion="15.20.1207.000" maxEngineVersion="15.20.3134.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
        </Pattern>
      </Version>
      <Version minEngineVersion="15.20.3135.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
          <Match idRef="Keyword_dea_number" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- Dea
- Dea #
- إدارة إنفاذ مكافحة الأدوية
- وكالة إنفاذ مكافحة الأدوية

## <a name="estonia-drivers-license-number"></a>رقم رخصة القيادة الإستونية

### <a name="format"></a>تنسيق

حرفان متبوعا بستة أرقام

### <a name="pattern"></a>نمط

حرفان وستة أرقام:

- الأحرف "ET" (غير حساسة لحالة الأحرف)
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_estonia_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_estonia_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Estonia Driver's License Number -->
      <Entity id="51da8171-da70-4cc1-9d65-055a59ca4f83" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_estonia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_estonia_eu_drivers_license_number"></a>s_license_number Keywords_estonia_eu_driver

- permis de conduire
- jutainubade numbrid
- رقم juhiloa
- جهوبوبا

## <a name="estonia-passport-number"></a>رقم جواز السفر الإستوني

### <a name="format"></a>تنسيق

حرف واحد متبوعا بسبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرف واحد متبوعا بسبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_estonia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_estonia_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_estonia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_estonia_eu_passport_number` تم العثور عليها.

```xml
      <!-- Estonia Passport Number -->
      <Entity id="61f7073a-509e-425b-a754-bc01bb5d5b8c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passinumbrid document number document document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="estonia-personal-identification-code"></a>رمز التعريف الشخصي الإستوني

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

11 رقما بدون مسافات ومحددات

### <a name="pattern"></a>نمط

11 رقما:

- رقم واحد يتوافق مع الجنس وقرن الميلاد (رقم فردي ذكر، حتى رقم أنثى؛ 1-2: القرن التاسع عشر؛ 3-4: القرن العشرين؛ 5-6: القرن الحادي والعشرون)
- ستة أرقام تتوافق مع تاريخ الميلاد (YYMMDD)
- ثلاثة أرقام تتوافق مع رقم تسلسلي يفصل بين الأشخاص الذين ولدوا في نفس التاريخ
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_estonia_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_estonia_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_estonia_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Estonia Personal Identification Code -->
      <Entity id="bfb26de6-dad5-4d48-ab72-4789cdd0654c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Match idRef="Keywords_estonia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_estonia_eu_telephone_number" />
            <Match idRef="Keywords_estonia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- ايك
- isikukood #
- isikukood
- معرف maksu
- maksukohustuslase identifitseerimisnumber
- maksunumber
- رقم التعريف الوطني
- الرقم الوطني
- رمز شخصي
- رقم المعرف الشخصي
- رمز التعريف الشخصي
- رقم التعريف الشخصي
- رقم شخصي #
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="estonia-physical-addresses"></a>العناوين المادية في  الإستونية

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من استونيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="eu-debit-card-number"></a>رقم بطاقة خصم الاتحاد الأوروبي

### <a name="format"></a>تنسيق

16 رقما

### <a name="pattern"></a>نمط

نمط معقد وقوي

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_eu_debit_card عن المحتوى الذي يتطابق مع النمط.
- واحد على الأقل مما يلي صحيح:
    - تم العثور على كلمة أساسية من Keyword_eu_debit_card.
    - تم العثور على كلمة أساسية من Keyword_card_terms_dict.
    - تم العثور على كلمة أساسية من Keyword_card_security_terms_dict.
    - تم العثور على كلمة أساسية من Keyword_card_expiration_terms_dict.
    - تبحث الدالة Func_expiration_date عن تاريخ بتنسيق التاريخ الصحيح.
- يمر المجموع الاختباري.

```xml
    <!-- EU Debit Card Number -->
    <Entity id="0e9b3178-9678-47dd-a509-37222ca96b42" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_eu_debit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_eu_debit_card" />
          <Match idRef="Keyword_card_terms_dict" />
          <Match idRef="Keyword_card_security_terms_dict" />
          <Match idRef="Keyword_card_expiration_terms_dict" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- رقم الحساب
- رقم البطاقة
- رقم البطاقة.
- رقم الأمان
- Cc #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr
- رقم acct
- acct no
- american express
- americanexpress
- americano espresso
- اميكس
- بطاقة جهاز atm
- بطاقات ال atm
- atm kaart
- بطاقة atmcard
- بطاقات atmcard
- قالب atmkaart
- atmkaarten
- بانكوتاكت
- بطاقة بنكية
- رسم بنكي
- حامل البطاقة
- حاملو البطاقات
- رقم البطاقة
- رقم البطاقة
- أرقام البطاقات
- نوع البطاقة
- cardano numerico
- حامل البطاقه
- حاملو البطاقات
- رقم البطاقة
- أرقام البطاقات
- كارتا بيانكا
- carta credito
- carta di credito
- cartao de credito
- cartao de crédito
- cartao de debito
- cartao de débito
- قافزة دوارة
- كرونة دوارة
- bleue للكارت
- carte de credit
- carte de crédit
- carte di credito
- الذبذبة
- cartão de credito
- cartão de crédito
- cartão de debito
- cartão de débito
- Cb
- نسخة من نسخة
- التحقق من البطاقة
- التحقق من البطاقات
- بطاقة اختيار
- بطاقات اختيار
- chequekaart
- المعلاق
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- بطاقة ائتمان
- بطاقات الائتمان
- بطاقة ائتمان
- بطاقات الائتمان
- debetkaart
- debetkaarten
- بانككارد
- بطاقات الخصم
- بطاقة خصم
- بطاقات الخصم
- الدينو تلقائي
- نادي diners
- dinersclub
- اكتشاف
- اكتشاف البطاقة
- اكتشاف البطاقات
- بطاقة الاكتشاف
- بطاقات الاكتشاف
- débito automático
- Edc
- eigentümername
- بطاقة الخصم الأوروبي
- hoofdkaart
- hoofdkaarten
- في الفياجية
- مكتب البطاقات اليابانية
- kaartdienst في اليابان
- Jcb
- kaart
- kaart num
- kaartaantal
- kaartaantallen
- kaarthouder
- kaarthouders
- الكارتي
- karteninhaber
- كارتينهارس
- kartennr
- كرتنمر
- kreditkarte
- kreditkarten-nummer
- kreditkartenin fisherer
- kreditkarteninstitut
- kreditkartennummer
- kreditkartentyp
- مايسترو
- البطاقة الرئيسية
- البطاقات الرئيسية
- ماستركارد
- بطاقات رئيسية
- Mc
- نقدية غير مهيئة
- n carta
- كارتا
- no de tarjeta
- لا يوجد قرطاو
- no do cartão
- لا. de tarjeta
- لا. do cartao
- لا. do cartão
- nr carta
- Nr. كارتا
- numeri di scheda
- numero carta
- numero de cartao
- numero de carte
- numero de cartão
- numero de tarjeta
- numero della carta
- numero di carta
- numero di scheda
- numero do cartao
- numero do cartão
- numéro de carte
- كارتا nوو
- nاصفة من نوع carte
- nانهارس دي لا كارت
- nاصفة de tarjeta
- nلاهي do cartao
- nلاسم do cartão
- nلاين. do cartão
- número de cartao
- número de cartão
- número de tarjeta
- número do cartao
- scheda dell'assegno
- scheda dell'atmosfera
- scheda dell'atmosfera
- scheda della بانكا
- scheda di controllo
- scheda di debito
- مصفوفة scheda
- schede'atmosfera
- schede di controllo
- schede di debito
- schede matrici
- scoprono la scheda
- scoprono le schede
- منفردا
- supporti di scheda
- supporto di scheda
- التبديل
- أجهزة atm في tarjeta
- tarjeta credito
- tarjeta de atm
- tarjeta de credito
- tarjeta de debito
- tarjeta debito
- tarjeta no
- tarjetahabiente
- tipo della scheda
- ufficio giapponese della
- scheda
- v pay
- v-pay
- فيزا
- علامة الجمع
- إلكترون
- visto
- visum
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- رقم تعريف البطاقة
- التحقق من البطاقة
- cardi la verifica
- سيد
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- القد. ثواني
- القد. seguranca
- القد. segurança
- القد. sicurezza
- codice di sicurezza
- codice di verifica
- الكدقل
- codigo de seguranca
- codigo de segurança
- مخطط تخطيطي
- التشفير
- صورة مشفرة
- cv2
- وسي
- cvc2
- cvn
- Cvv
- cvv2
- cód seguranca
- cód segurança
- cód. seguranca
- cód. segurança
- código
- código de seguranca
- código de segurança
- de kaart controle
- geeft nr uit
- المشكلة رقم
- رقم المشكلة
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- لا. edizione
- لا. di sicurezza
- numero de securite
- numero de verificaero
- numero dev'edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero van veiligheid
- numéro de sécurité
- nالاستراد التلقائي
- número de verificação
- perno il
- كتلة تثبيت
- prufziffer
- prüfziffer
- رمز الأمان
- رقم الأمان
- رقم الأمان
- sicherheits kode
- sicherheitscode
- رقم sicherheits
- sblok sblok
- veiligheid nr
- veiligheidsaantal
- veiligheidscode
- veiligheidsnummer
- verfalldatum

#### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

- ablauf
- data de expira تاريخ انتهاء الصلاحية
- data de expiração
- data del exp
- data di exp
- data di scadenza
- انتهاء صلاحية البيانات em que
- scad البيانات
- بيانات scadenza
- تاريخ الصلاحية
- datum afloop
- datum van exp
- de afloop
- espira
- espira
- تاريخ exp
- exp datum
- انتهاء الصلاحيه
- تنتهي
- تنتهي
- انتهاء
- fecha de expiracion
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- قابل للتقييم
- صالح
- valido hasta
- بساله
- venc
- vencimento
- vencimiento
- verloopt
- ذرى
- vervaldatum
- vto
- válido hasta

## <a name="eu-drivers-license-number"></a>رقم رخصة القيادة في الاتحاد الأوروبي

هذه الكيانات موجودة في رقم رخصة القيادة في الاتحاد الأوروبي وهي أنواع معلومات حساسة.

- [النمسا](#austria-drivers-license-number)
- [بلجيكا](#belgium-drivers-license-number)
- [بلغاريا](#bulgaria-drivers-license-number)
- [جمهورية كرواتيا](#croatia-drivers-license-number)
- [قبرص](#cyprus-drivers-license-number)
- [التشيكية](#czech-drivers-license-number)
- [الدانمارك](#denmark-drivers-license-number)
- [جمهورية إستونيا](#estonia-drivers-license-number)
- [جمهورية فنلندا](#finland-drivers-license-number)
- [فرنسا](#france-drivers-license-number)
- [ألمانيا](#germany-drivers-license-number)
- [اليونان](#greece-drivers-license-number)
- [هنغاريا](#hungary-drivers-license-number)
- [أيرلندا](#ireland-drivers-license-number)
- [إيطاليا](#italy-drivers-license-number)
- [جمهورية لاتفيا](#latvia-drivers-license-number)
- [جمهورية ليتوانيا](#lithuania-drivers-license-number)
- [لوكسمبورغ](#luxemburg-drivers-license-number)
- [جمهورية مالطا](#malta-drivers-license-number)
- [هولندا](#netherlands-drivers-license-number)
- [بولندا](#poland-drivers-license-number)
- [البرتغال](#portugal-drivers-license-number)
- [رومانيا](#romania-drivers-license-number)
- [سلوفاكيا](#slovakia-drivers-license-number)
- [سلوفينيا](#slovenia-drivers-license-number)
- [إسبانيا](#spain-drivers-license-number)
- [السويد](#sweden-drivers-license-number)
- [بريطانيا.](#uk-drivers-license-number)

## <a name="eu-national-identification-number"></a>رقم التعريف الوطني للاتحاد الأوروبي

هذه الكيانات موجودة في رقم التعريف الوطني للاتحاد الأوروبي وهي أنواع معلومات حساسة.

- [النمسا](#austria-identity-card)
- [بلجيكا](#belgium-national-number)
- [بلغاريا](#bulgaria-uniform-civil-number)
- [جمهورية كرواتيا](#croatia-identity-card-number)
- [قبرص](#cyprus-identity-card)
- [التشيكية](#czech-personal-identity-number)
- [الدانمارك](#denmark-personal-identification-number)
- [جمهورية إستونيا](#estonia-personal-identification-code)
- [جمهورية فنلندا](#finland-national-id)
- [فرنسا](#france-national-id-card-cni)
- [ألمانيا](#germany-identity-card-number)
- [اليونان](#greece-national-id-card)
- [هنغاريا](#hungary-personal-identification-number)
- [أيرلندا](#ireland-personal-public-service-pps-number)
- [إيطاليا](#italy-fiscal-code)
- [جمهورية لاتفيا](#latvia-personal-code)
- [جمهورية ليتوانيا](#lithuania-personal-code)
- [لوكسمبورغ](#luxemburg-national-identification-number-natural-persons)
- [جمهورية مالطا](#malta-identity-card-number)
- [هولندا](#netherlands-citizens-service-bsn-number)
- [بولندا](#poland-national-id-pesel)
- [البرتغال](#portugal-citizen-card-number)
- [رومانيا](#romania-personal-numeric-code-cnp)
- [سلوفاكيا](#slovakia-personal-number)
- [سلوفينيا](#slovenia-unique-master-citizen-number)
- [إسبانيا](#spain-dni)
- [بريطانيا.](#uk-national-insurance-number-nino)

## <a name="eu-passport-number"></a>رقم جواز سفر الاتحاد الأوروبي

هذه الكيانات موجودة في رقم جواز سفر الاتحاد الأوروبي وهي أنواع معلومات حساسة. هذه الكيانات موجودة في حزمة رقم جواز سفر الاتحاد الأوروبي.

- [النمسا](#austria-passport-number)
- [بلجيكا](#belgium-passport-number)
- [بلغاريا](#bulgaria-passport-number)
- [جمهورية كرواتيا](#croatia-passport-number)
- [قبرص](#cyprus-passport-number)
- [التشيكية](#czech-passport-number)
- [الدانمارك](#denmark-passport-number)
- [جمهورية إستونيا](#estonia-passport-number)
- [جمهورية فنلندا](#finland-passport-number)
- [فرنسا](#france-passport-number)
- [ألمانيا](#germany-passport-number)
- [اليونان](#greece-passport-number)
- [هنغاريا](#hungary-passport-number)
- [أيرلندا](#ireland-passport-number)
- [إيطاليا](#italy-passport-number)
- [جمهورية لاتفيا](#latvia-passport-number)
- [جمهورية ليتوانيا](#lithuania-passport-number)
- [لوكسمبورغ](#luxemburg-passport-number)
- [جمهورية مالطا](#malta-passport-number)
- [هولندا](#netherlands-passport-number)
- [بولندا](#poland-passport-number)
- [البرتغال](#portugal-passport-number)
- [رومانيا](#romania-passport-number)
- [سلوفاكيا](#slovakia-passport-number)
- [سلوفينيا](#slovenia-passport-number)
- [إسبانيا](#spain-passport-number)
- [السويد](#sweden-passport-number)
- [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](#usuk-passport-number)

## <a name="eu-social-security-number-or-equivalent-identification"></a>رقم الضمان الاجتماعي في الاتحاد الأوروبي أو التعريف المكافئ

هذه الكيانات موجودة في رقم الضمان الاجتماعي للاتحاد الأوروبي أو تعريف مكافئ وهي أنواع معلومات حساسة.

- [النمسا](#austria-social-security-number)
- [بلجيكا](#belgium-national-number)
- [جمهورية كرواتيا](#croatia-personal-identification-oib-number)
- [التشيكية](#czech-personal-identity-number)
- [الدانمارك](#denmark-personal-identification-number)
- [جمهورية فنلندا](#finland-national-id)
- [فرنسا](#france-social-security-number-insee)
- [ألمانيا](#germany-identity-card-number)
- [اليونان](#greece-national-id-card)
- [هنغاريا](#hungary-social-security-number-taj)
- [البرتغال](#portugal-citizen-card-number)
- [إسبانيا](#spain-social-security-number-ssn)
- [السويد](#sweden-national-id)

## <a name="eu-tax-identification-number"></a>رقم التعريف الضريبي للاتحاد الأوروبي

هذه الكيانات في نوع المعلومات الحساسة لرقم التعريف الضريبي في الاتحاد الأوروبي.

- [النمسا](#austria-tax-identification-number)
- [بلجيكا](#belgium-national-number)
- [بلغاريا](#bulgaria-uniform-civil-number)
- [جمهورية كرواتيا](#croatia-identity-card-number)
- [قبرص](#cyprus-tax-identification-number)
- [التشيكية](#czech-personal-identity-number)
- [الدانمارك](#denmark-personal-identification-number)
- [جمهورية إستونيا](#estonia-personal-identification-code)
- [جمهورية فنلندا](#finland-national-id)
- [فرنسا](#france-tax-identification-number)
- [ألمانيا](#germany-tax-identification-number)
- [اليونان](#greece-tax-identification-number)
- [هنغاريا](#hungary-tax-identification-number)
- [أيرلندا](#ireland-personal-public-service-pps-number)
- [إيطاليا](#italy-fiscal-code)
- [جمهورية لاتفيا](#latvia-personal-code)
- [جمهورية ليتوانيا](#lithuania-personal-code)
- [لوكسمبورغ](#luxemburg-national-identification-number-non-natural-persons)
- [جمهورية مالطا](#malta-tax-identification-number)
- [هولندا](#netherlands-tax-identification-number)
- [بولندا](#poland-tax-identification-number)
- [البرتغال](#portugal-tax-identification-number)
- [رومانيا](#romania-personal-numeric-code-cnp)
- [سلوفاكيا](#slovakia-personal-number)
- [سلوفينيا](#slovenia-tax-identification-number)
- [إسبانيا](#spain-tax-identification-number)
- [السويد](#sweden-tax-identification-number)
- [بريطانيا.](#uk-unique-taxpayer-reference-number)

## <a name="finland-drivers-license-number"></a>رقم رخصة القيادة في فنلندا

### <a name="format"></a>تنسيق

10 أرقام تحتوي على واصلة

### <a name="pattern"></a>نمط

10 أرقام تحتوي على واصلة:

- ستة أرقام
- واصلة
- ثلاثة أرقام
- رقم أو حرف

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_finland_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_finland_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Finland Driver's License Number -->
      <Entity id="bb3b27a3-79bd-4ac4-81a7-f9fca3c7d1a7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_finland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_finland_eu_drivers_license_number"></a>s_license_number Keywords_finland_eu_driver

- ajokortti
- permis de conduire
- ajokortin numero
- kulj consoleja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot

## <a name="finland-european-health-insurance-number"></a>رقم التأمين الصحي الأوروبي ل فنلندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

رقم مكون من 20 رقما

### <a name="pattern"></a>نمط

رقم مكون من 20 رقما:

- 10 أرقام - 8024680246
- مسافة اختيارية أو واصلة اختيارية
- 10 أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث Regex_Finland_European_Health_Insurance_Number regex عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_Finland_European_Health_Insurance_Number.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- ehic #
- ehic
- رقم/> #
- finska sjukförsäkringskort
- بطاقة صحية
- بطاقة التأمين الصحي
- رقم التأمين الصحي
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti

## <a name="finland-national-id"></a>المعرف الوطني ل فنلندا

### <a name="format"></a>تنسيق

ستة أرقام بالإضافة إلى حرف يشير إلى قرن بالإضافة إلى ثلاثة أرقام بالإضافة إلى خانة اختيار

### <a name="pattern"></a>نمط

يجب أن يتضمن النمط كل ما يلي:

- ستة أرقام بتنسيق DD ولاي، وهي تاريخ الميلاد
- علامة القرن (إما '-' أو '+' أو 'a')
- رقم التعريف الشخصي المكون من ثلاثة أرقام
- رقم أو حرف (غير حساس لحالة الأحرف) وهو رقم اختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_finnish_national_id عن المحتوى الذي يطابق النمط
- تم العثور على كلمة أساسية من Keyword_finnish_national_id
- تمريرات المجموع الاختباري

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_finnish_national_id عن المحتوى الذي يطابق النمط
- تمريرات المجموع الاختباري

```xml
      <!-- Finnish National ID-->
      <Entity id="338FD995-4CB5-4F87-AD35-79BD1DD926C1" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finnish_national_id" />
          <Match idRef="Keyword_finnish_national_id" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_finnish_national_id" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

- تونوس henkilökohtainen
- تونوس henkilökohtainen
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- المعرف لا
- رقم المعرف
- رقم التعريف
- identiteetti numero
- رقم الهوية
- رقم المعرف
- kansallinen henkilötunnus
- kansallisen henkilökortin
- بطاقة المعرف الوطنية
- رقم المعرف الوطني.
- المعرف الشخصي
- رمز الهوية الشخصية
- رقم شخصي #
- اختيار شخص
- رقم الشخص
- رقم الضمان الاجتماعي
- sosiaaliturvatunnus
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- tunnistenumero
- tunnus numero
- تونوسلالوكو
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus

## <a name="finland-passport-number"></a>رقم جواز سفر فنلندا

يتوفر هذا الكيان في نوع المعلومات الحساسة "رقم جواز سفر الاتحاد الأوروبي" ويتوفر ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق
تركيبة من تسعة أحرف وأرقام

### <a name="pattern"></a>نمط

تركيبة من تسعة أحرف وأرقام:

- حرفان (غير حساس لحالة الأحرف)
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_finland_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_finland_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_finland_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_finland_passport_number` تم العثور عليها.

```xml
      <!-- Finland Passport Number -->
      <Entity id="d1685ac3-1d3a-40f8-8198-32ef5669c7a5" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomalainen passi
- passin numero
- passin numero. #
- passin numero #
- passin numero.
- passi #
- رقم المرور

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="finland-physical-addresses"></a>عناوين فنلندا المادية

يكتشف هذا الكيان المسمى غير الملغى الأنماط المتعلقة بالعنوان الفعلي من فنلندا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="france-drivers-license-number"></a>رقم رخصة القيادة في فرنسا

يتوفر هذا الكيان في نوع المعلومات الحساسة لرقم رخصة القيادة في الاتحاد الأوروبي ويتوفر ككيان نوع معلومات حساسة مستقل.

### <a name="format"></a>تنسيق

12 رقما

### <a name="pattern"></a>نمط

12 رقما مع التحقق من الصحة لخصم أنماط مماثلة مثل أرقام الهواتف الفرنسية

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_french_drivers_license عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_french_drivers_license.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl
- permis de conduire
- رقم الترخيص
- رقم الترخيص
- أرقام التراخيص
- أرقام التراخيص
- numéros de licence

## <a name="france-health-insurance-number"></a>رقم التأمين الصحي في فرنسا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

رقم مكون من 21 رقما

### <a name="pattern"></a>نمط

رقم مكون من 21 رقما:

- 10 أرقام
- مساحة اختيارية
- 10 أرقام
- مساحة اختيارية
- رقم

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث Regex_France_Health_Insurance_Number regex عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_France_Health_Insurance_Number.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- بطاقة التأمين
- carte vitale
- carte d'assuré social

## <a name="france-national-id-card-cni"></a>بطاقة المعرف الوطنية الفرنسية (CNI)

### <a name="format"></a>تنسيق

12 رقما

### <a name="pattern"></a>نمط

12 رقما

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير العادي Regex_france_cni عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_france_eu_national_id_card.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- رقم البطاقة
- carte nationale d'identité
- carte nationale d'idenite no
- cni #
- cni
- compte bancaire
- رقم التعريف الوطني
- الهوية الوطنية
- nationalidno #
- numéro d'assurance maladie
- numéro de carte vitale

## <a name="france-passport-number"></a>رقم جواز سفر فرنسا

يتوفر هذا الكيان في نوع المعلومات الحساسة لرقم جواز سفر الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

تسعة أرقام وأحرف

### <a name="pattern"></a>نمط

تسعة أرقام وأحرف:

- رقمين
- حرفان (غير حساس لحالة الأحرف)
- خمسة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_fr_passport` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_france_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date3` العادي عن التاريخ بالتنسيق DD MM YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_fr_passport` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_france_eu_passport_number` تم العثور عليها.

```xml
    <!-- France Passport Number -->
    <Entity id="3008b884-8c8c-4cd8-a289-99f34fc7ff5d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passeport
- passeport n °
- passeport غير
- منفذ المرور #
- منفذ المرور #
- passeportnon
- passeportn °
- passeport français
- passeport livre
- carte passeport
- numéro passeport
- منفذ المرور n°
- n° du passeport
- n° منفذ مرور

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="france-physical-addresses"></a>عناوين فرنسا الفعلية

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من فرنسا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="france-social-security-number-insee"></a>رقم الضمان الاجتماعي (INSEE) في فرنسا

### <a name="format"></a>تنسيق

15 رقما

### <a name="pattern"></a>نمط

يجب أن تتطابق مع أحد النمطين:

- 13 رقما متبوعا بمسافة متبوعة برقمين

  او

- 15 رقما متتاليا

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_french_insee` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_fr_insee.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_french_insee أو Func_fr_insee عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
    <!-- France INSEE -->
    <Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Keyword_fr_insee" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- تعليمة برمجية sécu
- d'identité nationale
- insee
- fssn #
- le numéro d'identification nationale
- le code de la sécurité sociale
- المعرف الوطني
- التعريف الوطني
- لا يوجد هوية
- لا. هوية d'identité
- ضمان numéro d'assurance
- numéro d'identité
- numero d'identite
- numéro de sécu
- numéro de sécurité sociale
- لا توجد هوية
- لا. هوية d'd
- Ssn
- Ssn #
- sécurité sociale
- securité sociale
- securite sociale
- رقم الأمان الاجتماعي
- رقم الضمان الاجتماعي
- رمز الضمان الاجتماعي
- رقم التأمين الاجتماعي

## <a name="france-tax-identification-number"></a>رقم التعريف الضريبي في فرنسا

### <a name="format"></a>تنسيق

13 رقما

### <a name="pattern"></a>نمط

13 رقما

- رقم واحد يجب أن يكون 0 أو 1 أو 2 أو 3
- رقم واحد
- مسافة (اختياري)
- رقمين
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة خانات اختيار رقمية

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_france_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_france_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_france_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- France Tax Identification Number (numéro SPI.) -->
      <Entity id="ed59e77e-171d-442c-9ec1-88e2ebcb5b0a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Match idRef="Keywords_france_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_france_eu_telephone_number" />
            <Match idRef="Keywords_france_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d'identification fiscale
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="france-value-added-tax-number"></a>رقم الضريبة للقيمة المضافة في فرنسا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 13 حرفا

### <a name="pattern"></a>نمط

13 حرفا أبجديا رقميا:

- حرفان - FR (غير حساس لحالة الأحرف)
- مسافة اختيارية أو واصلة اختيارية
- حرفان أو رقمان
- مسافة اختيارية أو نقطة أو واصلة أو فاصلة
- ثلاثة أرقام
- مسافة اختيارية أو نقطة أو واصلة أو فاصلة
- ثلاثة أرقام
- مسافة اختيارية أو نقطة أو واصلة أو فاصلة
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_france_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_france_value_added_tax_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_france_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- France Value Added Tax Number -->
      <Entity id="949121e6-ad9f-4379-8731-710342baea78" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_value_added_tax_number" />
          <Match idRef="Keywords_france_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- ضريبه القيمه المضافه #
- ضريبة القيمة المضافة
- تعريف numéro d'identification taxe sur ajoutée
- تقييم الضرائب ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification en

## <a name="generic-medication-names"></a>أسماء الأدوية العامة

يكتشف هذا الكيان المسمى غير المحمل باسم أسماء الأدوية المعممة، مثل *الأكيتمينوفين*. وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="germany-drivers-license-number"></a>رقم رخصة القيادة في ألمانيا

يتم تضمين كيان نوع المعلومات الحساسة هذا في نوع المعلومات الحساسة لرقم رخصة القيادة في الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

تركيبة مكونة من 11 رقما وحرفا

### <a name="pattern"></a>نمط

11 رقما وحرفا (غير حساس لحالة الأحرف):

- رقم أو حرف
- رقمين
- ستة أرقام أو أحرف
- رقم
- رقم أو حرف

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_german_drivers_license عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_german_drivers_license_number.
- يمر المجموع الاختباري.

```xml
    <!-- German Driver's License Number -->
    <Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Match idRef="Keyword_german_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_german_drivers_license_number"></a>Keyword_german_drivers_license_number

- ausstellungsdatum
- ausstellungsort
- ausstellende behöde
- ausstellende behorde
- ausstellende behoerde
- führerschein
- فهررشين
- fuehrerschein
- führerscheinnummer
- عدد الفوهررساتشيين
- fuehrerscheinnummer
- führerschein-
- fuhrerschein-
- fuehrerschein-
- führerscheinnummernr
- fuhrerscheinnummernr
- fuehrerscheinnummernr
- führerscheinnummerklasse
- fuhrerscheinnummerklasse
- fuehrerscheinnummerklasse
- nr-führerschein
- nr-fuhrerschein
- nr-fuehrerschein
- no-führerschein
- لا يوجد أي أجهزة غير مهيقة
- لا يوجد أي أجهزة غير أجهزة
- n-führerschein
- n-fuhrerschein
- n-fuehrerschein
- permis de conduire
- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dlno

## <a name="germany-identity-card-number"></a>رقم بطاقة الهوية في ألمانيا

### <a name="format"></a>تنسيق

منذ 1 نوفمبر 2010: من تسعة إلى 11 حرفا ورقما

من 1 أبريل 1987 حتى 31 أكتوبر 2010: 10 أرقام

### <a name="pattern"></a>نمط

منذ 1 نوفمبر 2010: 9 إلى 11 حرفا من النمط الأبجدي الرقمي
- واحد L، M، N، P، R، T، V، W، X، Y (غير حساس لحالة الأحرف)
- ثمانية أرقام أو أحرف في C وF وG وH وJ وK وL وM وN وP وR وT وV وW وX وY وZ (غير حساس لحالة الأحرف)
- خانة اختيار رقمية
- d/D اختياري

من 1 أبريل 1987 حتى 31 أكتوبر 2010:

- 10 أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_german_id_card_with_check` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_germany_id_card` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي عن `Regex_germany_id_card` المحتوى الذي يطابق النمط (9 أحرف بدون خانة اختيار تم إصدارها قبل 2010 أو 10 أرقام تم إصدارها في 2010).
- تم العثور على كلمة أساسية من Keyword_germany_id_card.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_german_id_card_with_check` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
      <!-- Germany Identity Card Number -->
      <Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
         <IdMatch idRef="Regex_germany_id_card" />
         <Match idRef="Keyword_germany_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.4545.000">
          <Pattern confidenceLevel="85">
           <IdMatch idRef="Func_german_id_card_with_check" />
            <Match idRef="Keyword_germany_id_card" />
          </Pattern>
          <Pattern confidenceLevel="65">
           <IdMatch idRef="Func_german_id_card_with_check" />
          </Pattern>
        </Version>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- تحديد
- تعريف
- identifizierungsnummer
- بطاقة هوية
- رقم الهوية
- id-nummer
- المعرف الشخصي
- personalausweis
- رقم معرف persönliche
- persönliche identifikationsnummer
- persönliche-id-nummer

## <a name="germany-passport-number"></a>رقم جواز سفر ألمانيا

### <a name="format"></a>تنسيق

من 9 إلى 11 حرفا

### <a name="pattern"></a>نمط

- حرف واحد في C وF وG وH وJ وK (غير حساس لحالة الأحرف)
- ثمانية أرقام أو أحرف في C وF وG وH وJ وK وL وM وN وP وR وT وV وW وX وY وZ (غير حساس لحالة الأحرف)
- خانة اختيار رقمية
- d/D اختياري

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_german_passport_checksum` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keyword_german_passport` أو `Keywords_eu_passport_number_common` تم العثور عليها.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_german_passport` عن المحتوى الذي يتطابق مع نمط الأحرف التسعة (بدون خانة اختيار الرقم والاختياري d/D).
- تم العثور على كلمة أساسية من `Keyword_german_passport` أو `Keywords_eu_passport_number_common` تم العثور عليها.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_german_passport_checksum` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- German Passport Number -->
    <Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keywords_eu_passport_number_common" />
        </Any>
      </Pattern>
      <Version minEngineVersion="15.20.4570.0">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_german_passport_checksum" />
          <Any minMatches="1">
            <Match idRef="Keyword_german_passport" />
            <Match idRef="Keywords_eu_passport_number_common" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_german_passport_checksum" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- إعادة الدفع
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- رقم المرور
- reisepässe
- passeport no.
- لا يوجد منفذ مرور

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

## <a name="germany-physical-addresses"></a>عناوين ألمانيا الفعلية

يكتشف هذا الكيان المسمى غير الملغى الأنماط المتعلقة بالعنوان الفعلي من ألمانيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="germany-tax-identification-number"></a>رقم التعريف الضريبي في ألمانيا

### <a name="format"></a>تنسيق

11 رقما بدون مسافات ومحددات

### <a name="pattern"></a>نمط

11 رقما

- رقمين
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- رقمين
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_germany_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_germany_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_germany_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Germany Tax Identification Number -->
      <Entity id="43316a89-9880-40cf-b980-04bc7eefcec5" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
          <Match idRef="Keywords_germany_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- رقم معرف
- معرف steuer
- steueridentifikationsnummer
- رقم عمودي
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- زين #
- زين
- zinnnummer

## <a name="germany-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في ألمانيا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 11 حرفا

### <a name="pattern"></a>نمط

نمط أبجدي رقمي مكون من 11 حرفا:

- حرف D أو d
- حرف E أو e
- مساحة اختيارية
- ثلاثة أرقام
- مسافة أو فاصلة اختيارية
- ثلاثة أرقام
- مسافة أو فاصلة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_germany_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_germany_value_added_tax_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_germany_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Germany Value Added Tax Number -->
      <Entity id="db177eb2-8811-4842-bffc-128c14aa219f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
          <Match idRef="Keywords_germany_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- ضريبه القيمه المضافه #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer

## <a name="greece-drivers-license-number"></a>رقم رخصة القيادة في اليونان

يتم تضمين هذا الكيان في نوع المعلومات الحساسة لرقم رخصة القيادة في الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_greece_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_greece_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Greece Driver's License Number -->
      <Entity id="7a2200b5-aacf-4e3c-ab36-136d3e68b7da" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_greece_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_greece_eu_drivers_license_number"></a>s_license_number Keywords_greece_eu_driver

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης

## <a name="greece-national-id-card"></a>بطاقة المعرف الوطنية في اليونان

### <a name="format"></a>تنسيق

تركيبة من 7-8 أحرف وأرقام بالإضافة إلى شرطة

### <a name="pattern"></a>نمط

سبعة أحرف وأرقام (تنسيق قديم):

- حرف واحد (أي حرف من الأبجدية اليونانية)
- شرطة
- ستة أرقام

ثمانية أحرف وأرقام (تنسيق جديد):

- حرفان يقع حرفهما العلوي في كل من الحروف الأبجدية اليونانية واللاتينية (ABEZHIKMNOPTYX)
- شرطة
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_greece_id_card عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_greece_id_card.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير العادي Regex_greece_id_card عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Greece National ID Card -->
      <Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_id_card" />
          <Match idRef="Keyword_greece_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_greece_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- المعرف اليوناني
- المعرف الوطني اليوناني
- بطاقة المعرف الشخصي اليونانية
- معرف الشرطة اليونانية
- بطاقة هوية
- tautotita
- ταυτότητα
- ταυτότητας

## <a name="greece-passport-number"></a>رقم جواز سفر اليونان

### <a name="format"></a>تنسيق

حرفان متبوعا بسبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرفان متبوعا بسبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_greece_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_greece_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_greece_eu_passport_date` العادي عن التاريخ بالتنسيق DD MMM YY (مثال - 28 أغسطس 19) أو تم العثور على كلمة أساسية منه `Keywords_greece_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_greece_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_greece_eu_passport_number` تم العثور عليها.

```xml
      <!-- Greece Passport Number -->
      <Entity id="7e65eb47-cdf9-4f52-8f90-2a27d5ee67e3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_greece_eu_passport_date" />
            <Match idRef="Keywords_greece_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο

## <a name="greece-physical-addresses"></a>عناوين مادية في اليونان

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من اليونان. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="greece-social-security-number-amka"></a>رقم الضمان الاجتماعي في اليونان (AMKA)

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

11 رقما بدون مسافات ومحددات

### <a name="pattern"></a>نمط

- ستة أرقام كتواريخ ميلاد YYMMDD
- أربعة أرقام
- خانة اختيار رقمية

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_greece_eu_ssn` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_greece_eu_ssn_or_equivalent` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_greece_eu_ssn` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Greece Social Security Number (AMKA) -->
      <Entity id="e39b03f4-50ea-41ae-af7a-a4b9539596ad" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_greece_eu_ssn" />
          <Match idRef="Keywords_greece_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_greece_eu_ssn" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- Ssn
- Ssn #
- الضمان الاجتماعي لا
- الأمن الاجتماعي #
- رقم الضمان الاجتماعي
- amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης

## <a name="greece-tax-identification-number"></a>رقم التعريف الضريبي في اليونان

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_greece_eu_tax_file_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_greece_eu_tax_file_number` .

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- فؤاد #
- فؤاد
- a◂μ|aφμ ριθμός
- aφμ
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- لا يوجد سجل ضريبي
- رقم السجل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- taxregistryno #
- معرف الصفيح
- رقم الصفيح
- القصدير #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο

## <a name="hong-kong-identity-card-hkid-number"></a>رقم بطاقة هوية هونغ كونغ (HKID)

### <a name="format"></a>تنسيق

تركيبة من 8-9 أحرف وأرقام بالإضافة إلى أقواس اختيارية حول الحرف النهائي

### <a name="pattern"></a>نمط

تركيبة من 8-9 أحرف:

- 1-2 حرف (غير حساس لحالة الأحرف)
- ستة أرقام
- مساحة اختيارية
- حرف اختيار (أي رقم أو الحرف A) المضمن اختياريا بين أقواس

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_hong_kong_id_card عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_hong_kong_id_card.
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_hong_kong_id_card عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Hong Kong Identity Card (HKID) number -->
<Entity id="e63c28a7-ad29-4c17-a41a-3d2a0b70fd9c" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_hong_kong_id_card"/>
     <Match idRef="Keyword_hong_kong_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Func_hong_kong_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- بطاقة هوية هونغ كونغ
- HKIDC
- بطاقة المعرف
- بطاقة هوية
- بطاقة هوية hk
- معرف هونغ كونغ
- 香港身份證
- 香港永久性居民身份證
- 身份證
- 身份証
- 身分證
- 身分証
- 香港身份証
- 香港身分證
- 香港身分証
- 香港身份證
- 香港居民身份證
- 香港居民身份証
- 香港居民身分證
- 香港居民身分証
- 香港永久性居民身份証
- 香港永久性居民身分證
- 香港永久性居民身分証
- 香港永久性居民身份證
- 香港非永久性居民身份證
- 香港非永久性居民身份証
- 香港非永久性居民身分證
- 香港非永久性居民身分証
- 香港特別行政區永久性居民身份證
- 香港特別行政區永久性居民身份証
- 香港特別行政區永久性居民身分證
- 香港特別行政區永久性居民身分証
- 香港特別行政區非永久性居民身份證
- 香港特別行政區非永久性居民身份証
- 香港特別行政區非永久性居民身分證
- 香港特別行政區非永久性居民身分証

## <a name="hungary-drivers-license-number"></a>رقم رخصة القيادة في المجر

### <a name="format"></a>تنسيق

حرفان متبوعا بستة أرقام

### <a name="pattern"></a>نمط

حرفان وستة أرقام:

- حرفان (غير حساس لحالة الأحرف)
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_hungary_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_hungary_eu_driver's_license_number` تم العثور عليها.

```xml
      <Entity id="9d31c46b-6e6b-444c-aeb1-6dd7e604bb24" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_hungary_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_hungary_eu_drivers_license_number"></a>s_license_number Keywords_hungary_eu_driver

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek

## <a name="hungary-passport-number"></a>رقم جواز سفر المجر

### <a name="format"></a>تنسيق

حرفان متبوعا بستة أرقام أو سبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرفان متبوعا بستة أرقام أو سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_hungary_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_hungary_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_hungary_eu_passport_date` العادي عن التاريخ بالتنسيق DD MMM/MMM YY (مثال - 01 MÁR/MAR 12) أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_hungary_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_hungary_eu_passport_number` تم العثور عليها.

```xml
      <!-- Hungary Passport Number -->
      <Entity id="5b483910-9aa7-4c99-9917-f4001464bda7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_hungary_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="hungary-personal-identification-number"></a>رقم التعريف الشخصي في المجر

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>نمط

11 رقما:

- رقم واحد يتوافق مع الجنس، 1 للذكر، 2 للإناث. وهناك أعداد أخرى ممكنة أيضا بالنسبة إلى المواطنين الذين ولدوا قبل عام 1900 أو المواطنين ذوي المواطنين المزدوجين.
- ستة أرقام تتوافق مع تاريخ الميلاد (YYMMDD)
- ثلاثة أرقام تتوافق مع رقم تسلسلي
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungary_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_hungary_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungary_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Hungary Personal Identification Number -->
      <Entity id="7b5cc218-7046-47d9-80c9-f325b50896ca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Match idRef="Keywords_hungary_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- رقم المعرف
- رقم التعريف
- sz ig
- Sz. Ig.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány

## <a name="hungary-physical-addresses"></a>العناوين المادية في المجر

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من المجر. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="hungary-social-security-number-taj"></a>رقم الضمان الاجتماعي في المجر (TAJ)

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungary_eu_ssn_or_equivalent` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_hungary_eu_ssn_or_equivalent` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungary_eu_ssn_or_equivalent` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Hungarian Social Security Number (TAJ) -->
      <Entity id="0de78315-9537-47f5-95ab-b3e77eba3993" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_hungary_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- رقم الضمان الاجتماعي المجري
- رقم الضمان الاجتماعي
- رقم الأمان الاجتماعي #
- hssn #
- الأمان الاجتماعي غير متعلق
- hssn
- تاج
- تاج #
- Ssn
- Ssn #
- الضمان الاجتماعي لا
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám

## <a name="hungary-tax-identification-number"></a>رقم التعريف الضريبي في المجر

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

10 أرقام:

- رقم واحد يجب أن يكون "8"
- ثمانية أرقام
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungary_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_hungary_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungary_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Hungary Tax Identification Number -->
      <Entity id="ede42eb4-59d9-49eb-9603-d7853fbda91d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Match idRef="Keywords_hungary_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- علب المجرية
- معلقة #
- لا يوجد سلطة ضريبية
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- رقم ضريبة القيمة المضافة

## <a name="hungary-value-added-tax-number"></a>رقم الضريبة للقيمة المضافة في المجر

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 10 أحرف

### <a name="pattern"></a>نمط

نقش أبجدي رقمي من 10 أحرف:

- حرفان - HU أو hu
- مساحة اختيارية
- ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_hungarian_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_hungarian_value_added_tax_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_hungarian_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Hungarian Value Added Tax Number -->
      <Entity id="976349a0-683b-477a-90f8-ff0a220d5592" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
          <Match idRef="Keywords_hungarian_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- ضريبه القيمه المضافه
- رقم ضريبة القيمة المضافة
- ضريبه القيمه المضافه #
- vatno #
- المجريةvatno #
- رقم الضريبة.
- ضريبة القيمة المضافة áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám

## <a name="iceland-physical-addresses"></a>عناوين آيسلندا المادية

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من أيسلندا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>الإعاقات المدرجة في تقييم الإعاقة في الولايات المتحدة ضمن الضمان الاجتماعي

يكشف هذا الكيان المسمى غير المضمن عن أسماء الإعاقات المدرجة في تقييم الإعاقة في الولايات المتحدة ضمن الضمان الاجتماعي، مثل *عسر القراءة*. وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="india-drivers-license-number"></a>رقم رخصة القيادة في الهند

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 15 حرفا

### <a name="pattern"></a>نمط

15 حرفا أو رقما:

- حرفان يشيران إلى رمز الحالة
- مسافة اختيارية أو شرطة اختيارية
- رقمان يشيران إلى رمز المدينة
- مسافة اختيارية أو شرطة اختيارية
- أربعة أرقام تشير إلى سنة المشكلة
- مسافة اختيارية أو شرطة اختيارية
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_india_driving_license` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_eu_driver's_license_number_common` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_india_driving_license` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- India Driver's License Number -->
        <Entity id="680788a3-53b6-455a-b891-c38cd76dc917" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_india_driving_license" />
            <Match idRef="Keywords_eu_driver's_license_number_common" />
          </Pattern>
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Regex_india_driving_license" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number_common"></a>s_license_number_common Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

## <a name="india-gst-number"></a>رقم GST في الهند

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 15 حرفا

### <a name="pattern"></a>نمط

15 حرفا أو رقما:

- رقمان يمثلان رمز حالة صالح
- مسافة اختيارية أو شرطة اختيارية
- عشرة أحرف تمثل رقم الحساب الدائم (PAN)
- حرف واحد أو رقم واحد
- مسافة اختيارية أو شرطة اختيارية
- حرف واحد 'z' أو 'Z'
- مسافة اختيارية أو شرطة اختيارية
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_india_gst_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_india_gst_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_india_gst_number` عن المحتوى الذي يطابق النمط.

```xml
    <!-- India GST number  -->
      <Entity id="9f5a721c-2fd2-446a-a27e-0c02fbe4630c" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_india_gst_number" />
          <Match idRef="Keyword_india_gst_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_india_gst_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- Gst
- gstin
- ضريبة السلع والخدمات
- ضريبة السلع والخدمات

## <a name="india-permanent-account-number-pan"></a>رقم الحساب الدائم في الهند (PAN)

### <a name="format"></a>تنسيق

10 أحرف أو أرقام

### <a name="pattern"></a>نمط

10 أحرف أو أرقام:

- ثلاثة أحرف (غير حساسة لحالة الأحرف)
- حرف في C وP وH وF وA وT وB وL وJ وG (غير حساس لحالة الأحرف)
- رسالة
- أربعة أرقام
- حرف يمثل خانة اختيار أبجدية

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_india_permanent_account_number عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_india_permanent_account_number.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير العادي Regex_india_permanent_account_number عن المحتوى الذي يطابق النمط.

```xml
      <!-- India Permanent Account Number -->
      <Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_india_permanent_account_number" />
          <Match idRef="Keyword_india_permanent_account_number" />
        </Pattern>
        <Version minEngineVersion="15.20.3520.000">
          <Pattern confidenceLevel="65">
            <IdMatch idRef="Regex_india_permanent_account_number" />
          </Pattern>
        </Version>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- رقم الحساب الدائم
- عموم

## <a name="india-unique-identification-aadhaar-number"></a>رقم التعريف الفريد (Aadhaar) في الهند

### <a name="format"></a>تنسيق

12 رقما تحتوي على مسافات أو شرط اختيارية

### <a name="pattern"></a>نمط

12 رقما:

- رقم ليس 0 أو 1
- ثلاثة أرقام
- مسافة اختيارية أو شرطة اختيارية
- أربعة أرقام
- مسافة اختيارية أو شرطة اختيارية
- الرقم الأخير، وهو خانة الاختيار

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_india_aadhaar عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_india_aadhar.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_india_aadhaar عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- India Unique Identification (Aadhaar) number -->
<Entity id="1ca46b29-76f5-4f46-9383-cfa15e91048f" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_india_aadhaar"/>
     <Match idRef="Keyword_india_aadhar"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_india_aadhaar"/>
  </Pattern>
</Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- aadhar
- aadhar #
- Uid
- आधार
- uidai

## <a name="india-voter-id-card"></a>بطاقة هوية المقترعين في الهند

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 10 أحرف

### <a name="pattern"></a>نمط

10 أحرف أو أرقام:

- ثلاثة أحرف
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_india_voter_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_india_voter_id_card` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_india_voter_id_card` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- India Voter Id Card  -->
        <Entity id="646d643f-5228-4408-acc8-f2e81a6df897" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
           <Pattern confidenceLevel="75">
             <IdMatch idRef="Regex_india_voter_id_card" />
             <Match idRef="Keyword_india_voter_id_card" />
            </Pattern>
           <Pattern confidenceLevel="65">
              <IdMatch idRef="Regex_india_voter_id_card" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- الناخبين
- معرف مصوت
- بطاقة التصويت
- بطاقة المصوت
- بطاقة هوية صورة
- ملحمه
- ECI
- فاصلة الانتخابات

## <a name="indonesia-identity-card-ktp-number"></a>رقم بطاقة هوية إندونيسيا (KTP)

### <a name="format"></a>تنسيق

16 رقما تحتوي على فترات اختيارية

### <a name="pattern"></a>نمط

16 رقما:

- رمز المقاطعة المكون من رقمين
- فترة زمنية (اختيارية)
- رمز المدينة أو رمز المدينة المكون من رقمين
- تعليمة برمجية فرعية مكونة من رقمين
- فترة زمنية (اختيارية)
- ستة أرقام بتنسيق DD ولاي، وهي تاريخ الميلاد
- فترة زمنية (اختيارية)
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_indonesia_id_card عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_indonesia_id_card.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- كارتو تاندا بيندوك
- Nomor Induk Kependudukan

## <a name="international-banking-account-number-iban"></a>رقم الحساب المصرفي الدولي (IBAN)

### <a name="format"></a>تنسيق

رمز البلد (حرفان) بالإضافة إلى خانات الاختيار (رقمين) بالإضافة إلى رقم bban (حتى 30 حرفا)

### <a name="pattern"></a>نمط

يجب أن يتضمن النمط كل ما يلي:

- رمز البلد المكون من حرفين
- رقمان للتحقق (متبوعا بمسافة اختيارية)
- 1-7 مجموعات مكونة من أربعة أحرف أو أرقام (يمكن فصلها بمسافات)
- أحرف أو أرقام من 1 إلى 3

يختلف تنسيق كل بلد قليلا. يغطي نوع المعلومات الحساسة ل IBAN هذه البلدان ال 60:

- الاعلان
- Ae
- al
- في
- Az
- بكالوريوس
- be
- bg
- الهرسك
- الفصل
- Cr
- قبرصي
- تشيكوسلوفاكيا
- de
- Dk
- القيام بذلك
- Ee
- es
- fi
- fo
- fr
- غيغابايت
- جنرال الكتريك
- غي
- gl
- غرام
- hr
- hu
- اي
- ايل
- is
- it
- كيلوواط
- Kz
- رطل
- لي
- lt
- لو
- lv
- Mc
- Md
- أنا
- عضو الكنيست
- السيد
- طن متري
- مو
- nl
- no
- pl
- pt
- ro
- Rs
- Sa
- حد ذاته
- سي
- sk
- ن خ
- تينيسي
- tr
- Vg

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_iban عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

None

## <a name="international-classification-of-diseases-icd-10-cm"></a>التصنيف الدولي الأمراض (ICD-10-CM)

### <a name="format"></a>تنسيق

القاموس

### <a name="pattern"></a>نمط

الكلمه الاساسيه

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تم العثور على كلمة أساسية من Dictionary_icd_10_updated.
- تم العثور على كلمة أساسية من Dictionary_icd_10_codes.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تم العثور على كلمة أساسية من Dictionary_icd_10_ محدثة.

```xml
      <!-- ICD-10 CM -->
      <Entity id="3356946c-6bb7-449b-b253-6ffa419c0ce7" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_10_updated" />
          <Match idRef="Dictionary_icd_10_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_10_updated" />
        </Pattern>

```

### <a name="keywords"></a>الكلمات الرئيسيه

Any term from the Dictionary_icd_10_updated keyword dictionary, which is based on the [International Classification of Diseases, Tenth Revision, Clinical Modification (ICD-10-CM)](https://icd10cmtool.cdc.gov/). يبحث هذا النوع عن المصطلح فقط، وليس رموز التأمين.

أي مصطلح من قاموس الكلمات الأساسية Dictionary_icd_10_codes، والذي يستند إلى [التصنيف الدولي للمرضى، المراجعة العاشرة، التعديل الإكلينيكي (ICD-10-CM).](https://icd10cmtool.cdc.gov/) يبحث هذا النوع عن رموز التأمين فقط، وليس الوصف.

## <a name="international-classification-of-diseases-icd-9-cm"></a>التصنيف الدولي الأمراض (ICD-9-CM)

### <a name="format"></a>تنسيق

القاموس

### <a name="pattern"></a>نمط

الكلمه الاساسيه

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تم العثور على كلمة أساسية من Dictionary_icd_9_updated.
- تم العثور على كلمة أساسية من Dictionary_icd_9_codes.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تم العثور على كلمة أساسية من Dictionary_icd_9_updated.

```xml
    <Entity id="fa3f9c74-ee07-4c52-b5f2-085d6b2c0ec4" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_9_updated" />
          <Match idRef="Dictionary_icd_9_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_9_updated" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

Any term from the Dictionary_icd_9_updated keyword dictionary, which is based on the [International Classification of Diseases,Ninth Revision, Clinical Modification (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). يبحث هذا النوع عن المصطلح فقط، وليس رموز التأمين.

Any term from the Dictionary_icd_9_codes keyword dictionary, which is based on the [International Classification of Diseases,Ninth Revision, Clinical Modification (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). يبحث هذا النوع عن رموز التأمين فقط، وليس الوصف.

## <a name="ip-address"></a>عنوان IP

### <a name="format"></a>تنسيق

#### <a name="ipv4"></a>IPv4:
النمط المعقد الذي يمثل إصدارات عناوين IPv4 المنسقة (الفترات) وغير المنسقة (بدون نقاط)

#### <a name="ipv6"></a>IPv6:
النمط المعقد الذي يمثل أرقام IPv6 المنسقة (التي تتضمن نقطتين)

### <a name="pattern"></a>نمط

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

بالنسبة إلى IPv6، يتمتع نهج DLP بثقة عالية بأنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_ipv6_address عن المحتوى الذي يتطابق مع النمط.
- لم يتم العثور على كلمة أساسية من Keyword_ipaddress.

بالنسبة إلى IPv4، يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_ipv4_address عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_ipaddress.

بالنسبة إلى IPv6، يتمتع نهج DLP بثقة عالية بأنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_ipv6_address عن المحتوى الذي يتطابق مع النمط.
- لم يتم العثور على كلمة أساسية من Keyword_ipaddress.

```xml
    <!-- IP Address -->
    <Entity id="1daa4ad5-e2dd-4ca4-a788-54722c09efb2" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv4_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (هذه الكلمة الأساسية حساسة لحالة الأحرف)
- عنوان ip
- عناوين ip
- بروتوكول الإنترنت
- IP-כתובת ה

## <a name="ip-address-v4"></a>عنوان IP v4

### <a name="format"></a>تنسيق

النمط المعقد الذي يمثل إصدارات عناوين IPv4 المنسقة (الفترات) وغير المنسقة (بدون نقاط)

### <a name="pattern"></a>نمط

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ipv4_address` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ipaddress` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ipv4_address` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- IP Address v4-->
      <Entity id="a7dd5e5f-e7f9-4626-a2c6-86a8cb6830d2" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv4_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv4_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (حساس لحالة الأحرف)
- عنوان ip
- عناوين ip
- بروتوكول الإنترنت
- IP-כתובת ה

## <a name="ip-address-v6"></a>عنوان IP v6

### <a name="format"></a>تنسيق

النمط المعقد الذي يمثل أرقام IPv6 المنسقة (التي تتضمن نقطتين)

### <a name="pattern"></a>نمط

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ipv6_address` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ipaddress` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ipv6_address` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- IP Address v6-->
      <Entity id="3f691089-7413-4926-ab3b-3c5ea8a1c17e" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv6_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv6_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (حساس لحالة الأحرف)
- عنوان ip
- عناوين ip
- بروتوكول الإنترنت
- IP-כתובת ה

## <a name="ireland-drivers-license-number"></a>رقم رخصة القيادة في أيرلندا

### <a name="format"></a>تنسيق

ستة أرقام متبوعة بأربعة أحرف

### <a name="pattern"></a>نمط

ستة أرقام وأربعة أحرف:

- ستة أرقام
- أربعة أحرف (غير حساسة لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ireland_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_ireland_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Ireland Driver's License Number -->
      <Entity id="e01bccd9-eb4d-414f-ace1-e9b6a4c4a2ca" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_ireland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_ireland_eu_drivers_license_number"></a>s_license_number Keywords_ireland_eu_driver

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>رقم جواز سفر أيرلندا

### <a name="format"></a>تنسيق

حرفان أو رقمان متبوعا بسبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرفان أو رقمان متبوعا بسبعة أرقام:

- رقمان أو حرفان (غير حساس لحالة الأحرف)
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ireland_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_ireland_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_ireland_eu_passport_date` العادي عن التاريخ بالتنسيق DD MMM/MMM YYYY (مثال - 01 BEA/MAY 1988) أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ireland_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_ireland_eu_passport_number` تم العثور عليها.

```xml
      <!-- Ireland Passport Number -->
      <Entity id="a2130f27-9ee2-4103-84f9-a6b1ee7d0cbf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_ireland_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha pasanna
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cárta
- uimhir chárta

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="ireland-personal-public-service-pps-number"></a>رقم الخدمة العامة الشخصية (PPS) في أيرلندا

### <a name="format"></a>تنسيق

التنسيق القديم (حتى 31 ديسمبر 2012):

- سبعة أرقام متبوعة بأحرف من 1 إلى 2

تنسيق جديد (1 يناير 2013 وبعده):

- سبعة أرقام متبوعة بحرفين

### <a name="pattern"></a>نمط

التنسيق القديم (حتى 31 ديسمبر 2012):

- سبعة أرقام
- حرف إلى حرفين (غير حساس لحالة الأحرف)

تنسيق جديد (1 يناير 2013 وبعده):

- سبعة أرقام
- حرف (غير حساس لحالة الأحرف) وهو رقم فحص أبجدي
- حرف اختياري في النطاق A-I أو "W"

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_ireland_pps عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_ireland_eu_national_id_card.
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_ireland_pps عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
      <!-- Ireland Personal Public Service (PPS) Number -->
      <Entity id="1cdb674d-c19a-4fcf-9f4b-7f56cc87345a" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_ireland_pps" />
          <Match idRef="Keywords_ireland_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_ireland_pps" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- خدمة هوية العميل
- رقم التعريف
- رقم المعرف الشخصي
- رقم الخدمة العامة الشخصية
- الخدمة الشخصية لا
- phearsanta seirbhíse poiblí
- pps no
- رقم pps
- pps num
- pps service no
- ppsn
- ppsno #
- ppsno
- Psp
- الخدمة العامة لا
- الخدمة العامة #
- الخدمة العامة
- رقم الإيرادات والتأمين الاجتماعي
- rsi no
- رقم rsi
- rsin
- عميل seirbhís aitheantais
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="ireland-physical-addresses"></a>عناوين أيرلندا المادية

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من أيرلندا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="israel-bank-account-number"></a>رقم الحساب البنكي في إسرائيل

### <a name="format"></a>تنسيق

13 رقما

### <a name="pattern"></a>نمط

تنسيق:

- رقمين
- شرطة
- ثلاثة أرقام
- شرطة
- ثمانية أرقام

منسق:

- 13 رقما متتاليا

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_israel_bank_account_number عن محتوى يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_israel_bank_account_number.

```xml
<!-- Israel Bank Account Number -->
<Entity id="7d08b2ff-a0b9-437f-957c-aeddbf9b2b25" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_israel_bank_account_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_israel_bank_account_number" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- رقم الحساب البنكي
- حساب بنكي
- رقم الحساب
- מספר חשבון בנק

## <a name="israel-national-identification-number"></a>رقم التعريف الوطني في إسرائيل

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>نمط

تسعة أرقام متتالية

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_israeli_national_id_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_Israel_National_ID.
- يمر المجموع الاختباري.

```xml
<!-- Israel National ID Number -->
<Entity id="e05881f5-1db1-418c-89aa-a3ac5c5277ee" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_israeli_national_id_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_Israel_National_ID" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

- מספר זהות
- מספר זיה וי
- מספר זיהוי ישר אלי
- זהותישר אלית
- هو ية اسرائيل ية عدد
- هوية إسرائ يلية
- رقم الهوية
- عدد هوية فريدة من نوعها
- رقم المعرف #
- رقم المعرف
- لا هوية
- رقم الهوية #
- رقم الهوية
- israeliidentitynumber
- المعرف الشخصي
- معرف فريد

## <a name="italy-drivers-license-number"></a>رقم رخصة القيادة في إيطاليا

يتم تضمين كيان النوع هذا في نوع المعلومات الحساسة لرقم رخصة القيادة في الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

مزيج من 10 أحرف وأرقام

### <a name="pattern"></a>نمط

تركيبة مكونة من 10 أحرف وأرقام:

- حرف واحد (غير حساس لحالة الأحرف)
- الحرف "A" أو "V" (غير حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد (غير حساس لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_italy_drivers_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keyword_italy_drivers_license_number` تم العثور عليها.

```xml
    <!-- Italy Driver's license Number -->
    <Entity id="97d6244f-9157-41bd-8e0c-9d669a5c4d71" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_italy_drivers_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keyword_italy_drivers_license_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- numero di patente
- patente di guida
- guida للبراءة
- patenti di guida
- guida للبراءة

## <a name="italy-fiscal-code"></a>الرمز المالي في إيطاليا
يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

تركيبة مكونة من 16 حرفا من الأحرف والأرقام في النمط المحدد

### <a name="pattern"></a>نمط

تركيبة مكونة من 16 حرفا من الأحرف والأرقام:

- ثلاثة أحرف تتوافق مع الأحرف الساكنة الثلاثة الأولى في اسم العائلة
- ثلاثة أحرف تتوافق مع الأحرف الساكنة الأولى والثالثة والرابعة في الاسم الأول
- رقمان يتوافقان مع الأرقام الأخيرة من سنة الميلاد
- حرف واحد يتوافق مع الحرف الخاص بشهر الميلاد— يتم استخدام الأحرف بترتيب أبجدي، ولكن يتم استخدام الأحرف من A إلى E، وH، وL، وM، وP، وR إلى T فقط (لذلك، يناير هو A و أكتوبر هو R)
- رقمان يتوافقان مع يوم شهر الميلاد من أجل التفريق بين الجنسين، يضاف 40 إلى يوم الميلاد بالنسبة إلى امرأة
- أربعة أرقام تتوافق مع رمز المنطقة الخاص بالمقيم حيث ولد الشخص (تستخدم الرموز على مستوى البلد للبلدان الخارجية)
- رقم تماثل واحد

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_italy_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_italy_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_italy_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Italy Fiscal Code -->
      <Entity id="4cd79172-8da9-4ff5-9188-98b1e7e2eca6" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
          <Match idRef="Keywords_italy_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice fiscal
- codice fiscale
- معرف codice personale
- codice personale
- التعليمات البرمجية المالية
- numero certificato personale
- numero di identific kazone fiscale
- numero id personale
- numero personale
- رقم الشهادة الشخصية
- رمز شخصي
- رمز المعرف الشخصي
- رقم المعرف الشخصي
- رمز شخصي #
- رمز الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الهوية الضريبية
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="italy-passport-number"></a>رقم جواز سفر إيطاليا

### <a name="format"></a>تنسيق

حرفان أو رقمان متبوعا بسبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرفان أو رقمان متبوعا بسبعة أرقام:

- رقمان أو حرفان (غير حساس لحالة الأحرف)
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_italy_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_italy_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_italy_eu_passport_date` العادي عن التاريخ بالتنسيق DD MMM/MMM YYYY (مثال - 01 GEN/JAN 1988) أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_italy_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_italy_eu_passport_number` تم العثور عليها.

```xml
      <!-- Italy Passport Number -->
      <Entity id="39811019-4750-445f-b26d-4c0e6c431544" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_italy_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto numero
- numéro passeport
- numero di passaporto
- numeri del passaporto
- passeport italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="italy-physical-addresses"></a>العناوين الفعلية في إيطاليا

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من إيطاليا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="italy-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في إيطاليا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 13 حرفا مع محددات اختيارية

### <a name="pattern"></a>نمط

نمط أبجدي رقمي من 13 حرفا مع محددات اختيارية:

- I أو i
- T أو t
- مساحة اختيارية أو نقطة أو واصلة أو فاصلة
- 11 رقما

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_italy_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_italy_value_added_tax_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_italy_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Italy Value Added Tax -->
      <Entity id="26a8cc07-2283-4a2a-ab1d-4ab643c4c67f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
          <Match idRef="Keywords_italy_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- ضريبه القيمه المضافه #
- Iva
- Iva #

## <a name="japan-bank-account-number"></a>رقم الحساب البنكي الياباني

### <a name="format"></a>تنسيق

سبعة أو ثمانية أرقام

### <a name="pattern"></a>نمط

رقم الحساب البنكي:

- سبعة أو ثمانية أرقام
- رمز فرع الحساب البنكي:

- أربعة أرقام
- مسافة أو شرطة (اختياري)
- ثلاثة أرقام

المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_jp_bank_account عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_bank_account.
- أحد الإجراءات التالية صحيح:

- تبحث الدالة Func_jp_bank_account_branch_code عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_bank_branch_code.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_jp_bank_account عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_bank_account.

```xml
<!-- Japan Bank Account Number -->
<Entity id="d354f95b-96ee-4b80-80bc-4377312b55bc" patternsProximity="300" recommendedConfidence="75">
  <Version minEngineVersion="15.01.0131.000">
    <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_jp_bank_account" />
          <Match idRef="Keyword_jp_bank_account" />
          <Any minMatches="1">
            <Match idRef="Func_jp_bank_account_branch_code" />
            <Match idRef="Keyword_jp_bank_branch_code" />
          </Any>
      </Pattern>
  </Version>
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_bank_account" />
        <Match idRef="Keyword_jp_bank_account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- التحقق من رقم الحساب
- تدقيق الحساب
- تدقيق الحساب #
- التحقق من رقم Acct
- التحقق من Acct #
- التحقق من رقم Acct.
- التحقق من رقم الحساب.
- رقم الحساب البنكي
- حساب بنكي
- حساب بنكي #
- رقم Acct البنكي
- Acct البنكي #
- رقم Acct البنكي.
- رقم الحساب البنكي.
- رقم حساب التوفير
- حساب التوفير
- حساب التوفير #
- رقم Acct للحفظ
- توفير Acct #
- Savings Acct No.
- رقم حساب التوفير.
- رقم حساب الخصم
- حساب الخصم
- حساب الخصم #
- رقم Acct للخصم
- أككت الخصم #
- رقم Acct للخصم.
- رقم حساب الخصم.
- 口座番号
- 銀行口座
- 銀行口座番号
- 総合口座
- 普通預金口座
- 普通口座
- 当座預金口座
- 当座口座
- 預金口座
- 振替口座
- 銀行
- バンク

#### <a name="keyword_jp_bank_branch_code"></a>Keyword_jp_bank_branch_code

- 支店番号
- 支店コード
- 店番号

## <a name="japan-drivers-license-number"></a>رقم رخصة القيادة اليابانية

### <a name="format"></a>تنسيق

12 رقما

### <a name="pattern"></a>نمط

12 رقما متتاليا

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_jp_drivers_license_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_drivers_license_number.

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- رخصة القيادة
- رخصة القيادة
- مقسم طريقة عرض برنامج التشغيل
- تراخيص برامج التشغيل
- شرائح برنامج التشغيل
- تراخيص برامج التشغيل
- Dl #
- Dls #
- يسانس #
- lics #
- 運転免許証
- 運転免許
- 免許証
- 免許
- 運転免許証番号
- 運転免許番号
- 免許証番号
- 免許番号
- 運転免許証ナンバー
- 運転免許ナンバー
- 免許証ナンバー
- 運転免許証no
- 運転免許no
- 免許証no
- 免許no
- 運転経歴証明書番号
- 運転経歴証明書
- 運転免許証No.
- 運転免許No.
- 免許証No.
- 免許No.
- 運転免許証 #
- 運転免許 #
- 免許証 #
- 免許 #

## <a name="japan-my-number---corporate"></a>رقم هاتفي في اليابان - الشركة

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

رقم مكون من 13 رقما

### <a name="pattern"></a>نمط

رقم مكون من 13 رقما:

- رقم واحد من واحد إلى تسعة
- 12 رقما

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_japanese_my_number_corporate عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_japanese_my_number_corporate.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_japanese_my_number_corporate عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Japanese My Number – Corporate -->
      <Entity id="9e0eaf79-ff20-4ffb-b3e4-e7368d5db6ff" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
          <Match idRef="Keywords_japanese_my_number_corporate" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_japan_my_number_corporate"></a>Keyword_japan_my_number_corporate

- رقم الشركة
- マイナンバー
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 法人番号
- 指定通知書

## <a name="japan-my-number---personal"></a>رقم هاتفي في اليابان - شخصي

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

رقم مكون من 12 رقما

### <a name="pattern"></a>نمط

رقم مكون من 12 رقما:

- أربعة أرقام
- مسافة أو نقطة أو واصلة اختيارية
- أربعة أرقام
- مسافة أو نقطة أو واصلة اختيارية
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_japanese_my_number_personal عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_japanese_my_number_personal.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_japanese_my_number_personal عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Japanese My Number – Personal -->
      <Entity id="98da8e66-7299-4ebd-9f82-c871ab37d3ef" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_personal" />
          <Match idRef="Keywords_japanese_my_number_personal" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_japanese_my_number_personal" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_japan_my_number_personal"></a>Keyword_japan_my_number_personal

- رقمي
- マイナンバー
- 個人番号
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 通知カード

## <a name="japan-passport-number"></a>رقم جواز سفر اليابان

### <a name="format"></a>تنسيق

حرفان متبوعا بسبعة أرقام

### <a name="pattern"></a>نمط

حرفان (غير حساسين لحالة الأحرف) متبوعا بسبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_jp_passport عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_passport.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- جواز السفر
- رقم جواز السفر
- رقم جواز السفر.
- جواز السفر #
- パスポート
- パスポート番号
- パスポートナンバー
- パスポート＃
- パスポート #
- パスポートNo.
- 旅券番号
- 旅券番号＃
- 旅券番号♯
- 旅券ナンバー

## <a name="japan-residence-card-number"></a>رقم بطاقة الإقامة في اليابان

### <a name="format"></a>تنسيق

12 حرفا ورقما

### <a name="pattern"></a>نمط

12 حرفا ورقما:

- حرفان (غير حساس لحالة الأحرف)
- ثمانية أرقام
- حرفان (غير حساس لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_jp_residence_card_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_residence_card_number.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- رقم بطاقة الإقامة
- رقم بطاقة الإقامة
- بطاقة الإقامة #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>رقم التسجيل المقيم في اليابان

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>نمط

11 رقما متتاليا

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_jp_resident_registration_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_resident_registration_number.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- رقم التسجيل المقيم
- رقم السجل الأساسي للمقيمين
- رقم تسجيل المقيم.
- رقم السجل المقيم.
- رقم السجل الأساسي للمقيمين.
- رقم السجل المقيم الأساسي.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証

## <a name="japan-social-insurance-number-sin"></a>رقم التأمين الاجتماعي الياباني (SIN)

### <a name="format"></a>تنسيق

من 7 إلى 12 رقما

### <a name="pattern"></a>نمط

من 7 إلى 12 رقما:

- أربعة أرقام
- واصلة (اختيارية)
- ستة أرقام OR
- من 7 إلى 12 رقما متتاليا

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_jp_sin عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_sin.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_jp_sin_pre_1997 عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_jp_sin.

```xml
<!-- Japan Social Insurance Number -->
<Entity id="c840e719-0896-45bb-84fd-1ed5c95e45ff" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_jp_sin" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_sin_pre_1997" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- رقم التأمين الاجتماعي.
- رقم التأمين الاجتماعي
- رقم التأمين الاجتماعي
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 社会保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号

## <a name="lab-test-terms"></a>مصطلحات الاختبار المعملي

يكشف هذا الكيان المسمى غير المملوء عن المصطلحات المتعلقة باختبارات المعمل، مثل *أداة مكافحة الاختراق C-peptide*. وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="latvia-drivers-license-number"></a>رقم رخصة القيادة في لاتفيا

### <a name="format"></a>تنسيق

ثلاثة أحرف متبوعة بستة أرقام

### <a name="pattern"></a>نمط

ثلاثة أحرف وستة أرقام:

- ثلاثة أحرف (غير حساسة لحالة الأحرف)
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_latvia_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_latvia_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Latvia Driver's License Number -->
      <Entity id="ec996de0-30f2-46b1-b192-4d2ff8805fa7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_latvia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_latvia_eu_drivers_license_number"></a>s_license_number Keywords_latvia_eu_driver

- autovadjatja apliecultba
- autovadjatja apliecultbas
- vad predictionja apliecja

## <a name="latvia-passport-number"></a>رقم جواز سفر لاتفيا

### <a name="format"></a>تنسيق

حرفان أو رقمان متبوعا بسبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرفان أو رقمان متبوعا بسبعة أرقام:

- رقمان أو حرفان (غير حساس لحالة الأحرف)
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_latvia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_latvia_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_latvia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_latvia_eu_passport_number` تم العثور عليها.

```xml
      <!-- Latvia Passport Number -->
      <Entity id="23ae25ec-cc28-421b-b77a-3054eadf1ede" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase nununus
- pase nununu
- pases numuri
- pases nr
- لا يوجد منفذ مرور
- n° du Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="latvia-personal-code"></a>رمز لاتفيا الشخصي

### <a name="format"></a>تنسيق

11 رقما وواصلة اختيارية

### <a name="pattern"></a>نمط

التنسيق القديم

11 رقما وواصلة:

- ستة أرقام تتوافق مع تاريخ الميلاد (DDNAMY)
- واصلة
- رقم واحد يتوافق مع قرن الميلاد ("0" في القرن التاسع عشر، و"1" في القرن العشرين، و"2" في القرن الحادي والعشرين)
- أربعة أرقام، تم إنشاؤها عشوائيا

تنسيق جديد

11 رقما

- رقمان "32"
- تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_latvia_eu_national_id_card` أو regex `Regex_latvia_eu_national_id_card_new_format` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_latvia_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_latvia_eu_national_id_card` أو regex `Regex_latvia_eu_national_id_card_new_format` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Latvia Personal Code -->
      <Entity id="03fcf763-27c2-49ed-9422-2641c6c895c9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- رقم إداري
- alvas nē
- رقم الميلاد
- رقم المواطنين
- الرقم المدني
- رقم التعداد الإلكتروني
- رقم إلكتروني
- التعليمات البرمجية المالية
- رقم مستخدم الرعاية الصحية
- معرف #
- رمز المعرف
- رقم التعريف
- identifikjas nunus
- رقم المعرف
- رقم فردي
- latvija alva
- معرف nacionakalais
- المعرف الوطني
- رقم تعريف وطني
- رقم الهوية الوطنية
- رقم التأمين الوطني
- رقم السجل الوطني
- nodokļa nunus
- معرف nodokļu
- nodokļu identifikîcija nununus
- رقم الشهادة الشخصية
- رمز شخصي
- رمز المعرف الشخصي
- رقم المعرف الشخصي
- رمز التعريف الشخصي
- المعرف الشخصي
- رقم الهوية الشخصية
- رقم شخصي
- رمز رقمي شخصي
- رمز شخصي #
- personas kods
- رمز تعريف المحتوى
- رقم الخدمة العامة
- رقم التسجيل
- رقم الإيرادات
- رقم التأمين الاجتماعي
- رقم الضمان الاجتماعي
- رمز ضريبة الحالة
- رقم ملف الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- رقم المصوت

## <a name="latvia-physical-addresses"></a>عناوين لاتفيا المادية

يكتشف هذا الكيان المسمى غير المفكك الأنماط المتعلقة بالعنوان الفعلي من لاتفيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="liechtenstein-physical-addresses"></a>عناوين ليشتاندا المادية

يكشف هذا الكيان المسمى غير المكتظ بالأنماط المتعلقة بالعنوان الفعلي من ليشتاندا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="lifestyles-that-relate-to-medical-conditions"></a>أنماط الحياة التي تتعلق بالظروف الطبية

يكشف هذا الكيان المسمى غير الملصق عن المصطلحات المتعلقة بأنماط الحياة التي قد تؤدي إلى حالة طبية، مثل *التدخين*. وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="lithuania-drivers-license-number"></a>رقم رخصة القيادة في ليتوانا

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_lithuania_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_lithuania_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Lithuania Driver's License Number -->
      <Entity id="86f7628b-e0f4-4dc3-9fbc-e4300e4c7d78" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_lithuania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_lithuania_eu_drivers_license_number"></a>s_license_number Keywords_lithuania_eu_driver

- vairuotojo paėjimas
- vairuotojo paėjimo numeris
- vairuotojo paėjimo numeriai

## <a name="lithuania-personal-code"></a>رمز ليتواني الشخصي

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

11 رقما بدون مسافات ومحددات

### <a name="pattern"></a>نمط

11 رقما بدون مسافات ومحددات:

- رقم واحد (1-6) يتوافق مع نوع الشخص وقرن ميلاده
- ستة أرقام تتوافق مع تاريخ الميلاد (YYMMDD)
- ثلاثة أرقام تتوافق مع الرقم التسلسلي لتاريخ الميلاد
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_lithuania_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_lithuania_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_lithuania_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Lithuania Personal Code -->
      <Entity id="cd6d3786-8ec3-4524-a2cf-1e0095379171" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Match idRef="Keywords_lithuania_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_lithuania_eu_telephone_number" />
            <Match idRef="Keywords_lithuania_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- رقم خدمة المواطنين
- معرف mokesîių
- mokesîių identifikavimas numeris
- mokesîių identifikavimo numeris
- mokesîių numeris
- رقم التعريف الوطني
- رمز شخصي
- رمز رقمي شخصي
- أرقام piliepiio paslaugos
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- رقم تعريف فريد
- رقم هوية فريد
- uniqueidentityno #

## <a name="lithuania-physical-addresses"></a>عناوين ليتوانية فعلية

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من ليتوانا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="lithuania-passport-number"></a>رقم جواز سفر ليتوانا

### <a name="format"></a>تنسيق

ثمانية أرقام أو أحرف بدون مسافات أو محددات

### <a name="pattern"></a>نمط

ثمانية أرقام أو أحرف (غير حساسة لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_lithuania_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_lithuania_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date3` العادي عن التاريخ بالتنسيق DD MM YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_lithuania_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_lithuania_eu_passport_number` تم العثور عليها.

```xml
      <!-- Lithuania Passport Number -->
      <Entity id="1b79900f-047b-4c3f-846f-7d73b5534bce" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- أرقام paso
- paso numeriai
- paso nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="luxemburg-drivers-license-number"></a>رقم رخصة القيادة في أوسمبورغ

### <a name="format"></a>تنسيق

ستة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_luxemburg_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_luxemburg_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Luxemburg Driver's License Number -->
      <Entity id="89daf717-1544-4860-9a2e-fc9166dd8852" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_luxemburg_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>s_license_number Keywords_luxemburg_eu_driver

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>رقم التعريف الوطني في أوسيمبورغ (الأشخاص الطبيعيون)

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

13 رقما بدون مسافات أو محددات

### <a name="pattern"></a>نمط

13 رقما:

- 11 رقما
- خانتا اختيار رقميتان

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_luxemburg_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_luxemburg_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_luxemburg_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Luxemburg National Identification Number (Natural persons) -->
      <Entity id="aaf661ed-29ec-426d-8bf9-880cad298ebb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Match idRef="Keywords_luxemburg_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- معرف غير مهيئ
- معرف eindeutige-nummer
- eindeutigeid #
- معرف الموظفين
- idpersonnelle #
- idpersonnelle
- تعليمة برمجية فردية
- معرف فردي
- تعريف فردي
- الهوية الفردية
- موظفو تعريف numéro d'd'
- المعرف الشخصي
- التعريف الشخصي
- الهوية الشخصية
- personalidno #
- رقم شخصي #
- persönliche identifikationsnummer
- معرف فريد
- هوية فريدة
- مفتاح فريد #

## <a name="luxemburg-national-identification-number-non-natural-persons"></a>رقم التعريف الوطني في أوسمبيرغ (أشخاص غير طبيعيين)

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>نمط

11 رقما

- رقمين
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- رقمين
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_luxemburg_eu_tax_file_number_non_natural` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_luxemburg_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_luxemburg_eu_tax_file_number_non_natural` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Luxemburg National Identification Number (Non-natural persons) -->
      <Entity id="84bffa3a-d805-4788-a613-b1e4df3804cf" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Match idRef="Keywords_luxemburg_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- étain غير
- étain #
- المعرف d'imp imp t
- معرف الضريبة في لكسمر لكسمر
- numéro d'étain
- numéro d'identification fiscal لكسمبورجية
- numéro d'identification fiscale
- الضمان الاجتماعي
- sozialunterstützung
- sozialversécherung
- sozialversicherungsausweis
- معرف steier
- steier identifikatiounsnummer
- steier nummer
- معرف steuer
- steueridentifikationsnummer
- رقم عمودي
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- زين #
- زين
- zinnzahl

## <a name="luxemburg-passport-number"></a>رقم جواز سفر Unityemburg

### <a name="format"></a>تنسيق

ثمانية أرقام أو أحرف بدون مسافات أو محددات

### <a name="pattern"></a>نمط

ثمانية أرقام أو أحرف (غير حساسة لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_luxemburg_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_luxemburg_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date3` العادي عن التاريخ بالتنسيق DD MM YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_luxemburg_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_luxemburg_eu_passport_number` تم العثور عليها.

```xml
      <!-- Luxemburg Passport Number -->
      <Entity id="81d5c027-bed9-4421-91a0-3b2e55b3eb85" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- تمرير لكسمبورج
- منفذ مرور لكسمبورج
- جواز سفر لكسمبورج
- no de passeport
- عدم إعادة التسهيب
- nr-reisepass
- numéro de passeport
- شبكة تمرير
- تمرير nr
- رقم المرور
- passeport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="luxemburg-physical-addresses"></a>عناوين Unityemburg المادية

يكشف هذا الكيان المسمى غير المختلط عن الأنماط المتعلقة بالعنوان الفعلي من Unityemburg. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="malaysia-identification-card-number"></a>رقم بطاقة تعريف ماليزيا

### <a name="format"></a>تنسيق

12 رقما تحتوي على واصلات اختيارية

### <a name="pattern"></a>نمط

12 رقما:

- ستة أرقام بالتنسيق YYMMDD، وهي تاريخ الميلاد
- شرطة (اختياري)
- رمز مكان الميلاد المكون من حرفين
- شرطة (اختياري)
- ثلاثة أرقام عشوائية
- رمز الجنس المكون من رقم واحد

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_malaysia_id_card_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_malaysia_id_card_number.

```xml
<!-- Malaysia ID Card Number -->
</Entity>
      <Entity id="7f0e921c-9677-435b-aba2-bb8f1013c749" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_malaysia_id_card_number" />
            <Match idRef="Keyword_malaysia_id_card_number" />
        </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- بطاقة تطبيق رقمية
- i/c
- i/c no
- Ic
- ic no
- بطاقة المعرف
- بطاقة التعريف
- بطاقة هوية
- k/p
- k/p no
- kad akiri diri
- kad aplikasi digital
- kad pengenalan malaysia
- Kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- بطاقة هوية ماليزيا
- بطاقة هوية
- nric
- بطاقة التعريف الشخصية

## <a name="malta-drivers-license-number"></a>رقم رخصة القيادة للمتجر

### <a name="format"></a>تنسيق

تركيبة مكونة من حرفين وستة أرقام في النمط المحدد

### <a name="pattern"></a>نمط

تركيبة مكونة من حرفين وستة أرقام:

- حرفان (أرقام أو أحرف، غير حساسة لحالة الأحرف)
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_malta_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_malta_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Malta Driver's License Number -->
      <Entity id="a3bdaa4a-8371-4735-8fa5-56ee0fb4afc4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_malta_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_malta_eu_drivers_license_number"></a>s_license_number Keywords_malta_eu_driver

- liċenzja tas-radiqan
- liċenzji tas-azurewieq

## <a name="malta-identity-card-number"></a>رقم بطاقة هوية الهويات في مالطا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

سبعة أرقام متبوعة بحرف واحد

### <a name="pattern"></a>نمط

سبعة أرقام متبوعة بحرف واحد:

- سبعة أرقام
- حرف واحد في "M، G، A، P، L، H، B، Z" (غير حساس لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_malta_eu_national_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_malta_eu_national_id_card` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_malta_eu_national_id_card` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- Malta Identity Card Number -->
      <Entity id="854b36b3-a388-4ac8-a4ec-677c2b5e4356" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
          <Match idRef="Keywords_malta_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- رقم خدمة المواطنين
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- رمز رقمي شخصي
- رقم تعريف فريد
- رقم هوية فريد
- uniqueidentityno #

## <a name="malta-passport-number"></a>رقم جواز سفر الحيوانات

### <a name="format"></a>تنسيق

سبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_malta_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_malta_eu_passport_number` تم العثور عليها.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_malta_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_malta_eu_passport_number` تم العثور عليها.

```xml
      <!-- Malta Passport Number -->
      <Entity id="b2b21198-48f9-4d13-b2a5-03969bff0fb8" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
          <Match idRef="Keywords_eu_passport_date" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- منفذ numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="malta-physical-addresses"></a>عناوين مادية في  الاحتياجات الخاصة

يكشف هذا الكيان المسمى غير الملغى عن الأنماط المتعلقة بالعنوان الفعلي من أداة معالجة الرسومات. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="malta-tax-identification-number"></a>رقم التعريف الضريبي في دائرة الضرائب

### <a name="format"></a>تنسيق

بالنسبة إلى المواطنين المالطيين:

- سبعة أرقام وحرف واحد في النمط المحدد

المواطنين غير المالطيين والكيانات المالطية:

- تسعة أرقام

### <a name="pattern"></a>نمط

المواطنين المالطيين: سبعة أرقام وحرف واحد

- سبعة أرقام
- حرف واحد (غير حساس لحالة الأحرف)

المواطنين غير المالطيين والكيانات المالطية: تسعة أرقام

- تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- regex `Regex_malta_eu_tax_file_number`  أو `Regex_malta_eu_tax_file_number_non_maltese_national` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_malta_eu_tax_file_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- regex `Regex_malta_eu_tax_file_number` أو `Regex_malta_eu_tax_file_number_non_maltese_national` البحث عن المحتوى الذي يطابق النمط.

```xml
      <!-- Malta Tax ID Number -->
      <Entity id="ec830c63-65f4-45d0-9d8c-910dc8334b20" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- رقم خدمة المواطنين
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- رمز رقمي شخصي
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- رقم تعريف فريد
- رقم هوية فريد
- uniqueidentityno #

## <a name="medical-specialities"></a>التخصصات الطبية

يكشف هذا الكيان المسمى غير المفكك عن المصطلحات المتعلقة بالتخصصات الطبية، مثل *طب الأطباء*.  وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="medicare-beneficiary-identifier-mbi-card"></a>بطاقة معرف Medicare للمستفيد (MBI)

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 11 حرفا

### <a name="pattern"></a>نمط

- رقم واحد بين 1 إلى 9
- حرف واحد باستثناء S وL وO وI وB وZ
- رقم واحد أو حرف واحد باستثناء S وL وO وI وB وZ
- رقم واحد
- واصلة اختيارية
- حرف واحد باستثناء S وL وO وI وB وZ
- رقم واحد أو حرف واحد باستثناء S وL وO وI وB وZ
- رقم واحد
- واصلة اختيارية
- حرفان باستثناء S وL وO وI وB وZ
- رقمين

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_mbi_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_mbi_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_mbi_card` العادي عن المحتوى الذي يطابق النمط.

```xml
    <!-- Medicare Beneficiary Identifier (MBI) card -->
      <Entity id="f753a286-f5cc-47e6-a592-4be25fd02591" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_mbi_card" />
          <Match idRef="Keyword_mbi_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_mbi_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- mbi
- mbi #
- الرعاية الصحية غير المستفيدة #
- معرف medicare للمستفيد
- medicare غير مستحق
- رقم الرعاية المستفيدة من medicare
- الرعاية الصحية غير المستفيدة #

## <a name="mexico-unique-population-registry-code-curp"></a>رمز سجل المحتوى الفريد في المكسيك (CURP)

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 18 حرفا

### <a name="pattern"></a>نمط

- أربعة أحرف (غير حساس لحالة الأحرف)
- ستة أرقام تشير إلى تاريخ صالح
- حرف - H/h أو M/m
- حرفان يشيران إلى تعليمة برمجية صحيحة لحالة المكسيك
- ثلاثة أحرف
- حرف واحد أو رقم واحد
- رقم واحد

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_mexico_population_registry_code` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_mexico_population_registry_code` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_mexico_population_registry_code` عن المحتوى الذي يطابق النمط.

```xml
    <!-- Mexico Unique Population Registry Code (CURP) -->
      <Entity id="e905ad4d-5a74-406d-bf36-b1efca798af4" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_mexico_population_registry_code" />
          <Match idRef="Keyword_mexico_population_registry_code" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_mexico_population_registry_code" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- رمز تسجيل المحتوى الفريد
- رمز محتوى فريد
- CURP
- المعرف الشخصي
- معرف فريد
- معرف شخصي
- رقم شخصي
- مفتاح فريد
- رقم فريد
- clave única
- احفظ unica
- clave personal Identidad
- Identidad Clave الشخصي
- ClaveÚnica
- claveunica
- clavepersonalIdentidad

## <a name="netherlands-citizens-service-bsn-number"></a>رقم خدمة المواطنين الهولنديين (BSN)

### <a name="format"></a>تنسيق

ثمانية أو تسعة أرقام تحتوي على مسافات اختيارية

### <a name="pattern"></a>نمط

ثمانية تسعة أرقام:

- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- رقمان مكونان من ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_netherlands_bsn عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_netherlands_bsn.
- يمر المجموع الاختباري.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- Bsn #
- Bsn
- عدد الخوادم
- رقم خدمة المواطنين
- رقم الشخص
- رقم شخصي
- رمز رقمي شخصي
- رقم ذو صلة بالشخص
- رقم persoonlijk
- رمز رقمي persoonlijke
- persoonsgebonden
- عدد الأعصار
- nummer sociaal-fiscaal
- الرقم الاجتماعي -المالي
- صوفي
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- رقم تعريف فريد
- رقم هوية فريد
- uniqueidentityno #

## <a name="netherlands-drivers-license-number"></a>رقم رخصة القيادة في هولندا

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

10 أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_netherlands_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_netherlands_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Netherlands Driver's License Number -->
      <Entity id="6247fbea-ab80-4be5-8233-308b7c031401" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_netherlands_eu_driver's_license_number" />
            </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_netherlands_eu_drivers_license_number"></a>s_license_number Keywords_netherlands_eu_driver

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- عدد rijbewijs

## <a name="netherlands-passport-number"></a>رقم جواز سفر هولندا

### <a name="format"></a>تنسيق

تسعة أحرف أو أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

تسعة أحرف أو أرقام

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_netherlands_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_netherlands_eu_passport_number` تم العثور عليها.
- يبحث التعبير العادي عن `Regex_netherlands_eu_passport_date` التاريخ بالتنسيق DD MMM/MMM YYYY (مثال - 26 MAA/MAR 2012)

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_netherlands_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_netherlands_eu_passport_number` تم العثور عليها.

```xml
      <!-- Netherlands Passport Number -->
      <Entity id="61786727-bafd-45f6-94d9-888d815e228e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Match idRef="Regex_netherlands_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- رقم paspoort
- paspoortnummers
- paspoortnummer
- paspoort nr

## <a name="netherlands-physical-addresses"></a>العناوين المادية في هولندا

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من هولندا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="netherlands-tax-identification-number"></a>رقم التعريف الضريبي في هولندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_netherlands_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_netherlands_eu_tax_file_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_netherlands_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Netherlands Tax Identification Number -->
      <Entity id="01f42a64-eba7-4892-a67b-398237e4ade2" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
          <Match idRef="Keywords_netherlands_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- التعريف الضريبي hollânske
- رقم معرف hulandes impuesto
- تحديد هولاندز impuesto
- تحديد هوية الكتاليوم
- تحديد هوية van belasting
- رقم التعريف impuesto
- رقم مرتجل
- رقم معرف nederlands المائل
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- التعريف الضريبي لهولندا
- التعريف الضريبي لهولندا
- صفيح هولندا
- صفيح هولندا
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- إجمالي التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- إجمالي الضريبة
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="netherlands-value-added-tax-number"></a>رقم الضريبة للقيمة المضافة في هولندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نقش أبجدي رقمي من 14 حرفا

### <a name="pattern"></a>نمط

نمط أبجدي رقمي مكون من 14 حرفا:

- N أو n
- L أو l
- مساحة أو نقطة أو واصلة اختيارية
- تسعة أرقام
- مساحة أو نقطة أو واصلة اختيارية
- B أو b
- رقمين

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_netherlands_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_netherlands_value_added_tax_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_netherlands_value_added_tax_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Netherlands Value Added Tax Number -->
      <Entity id="4f320d9b-4972-41ae-b337-88d499bb1ade" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
          <Match idRef="Keywords_netherlands_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- ضريبه القيمه المضافه #
- الحصول على الضريبة التي تم ارتداؤها
- btw nûmer
- btw-nummer

## <a name="new-zealand-bank-account-number"></a>رقم الحساب البنكي في نيوزيلندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نمط من 14 رقما إلى 16 رقما مع محدد اختياري

### <a name="pattern"></a>نمط

نمط مكون من 14 رقما إلى 16 رقما مع محدد اختياري:

- رقمين
- واصلة أو مسافة اختيارية
- ثلاثة إلى أربعة أرقام
- واصلة أو مسافة اختيارية
- سبعة أرقام
- واصلة أو مسافة اختيارية
- رقمان إلى ثلاثة أرقام
- واصلة خيارات أو مسافة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_new_zealand_bank_account_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_new_zealand_bank_account_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_new_zealand_bank_account_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- New Zealand Bank Account Number -->
      <Entity id="1a97fc2b-dd2f-48f1-bc4e-2ddf25813956" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
          <Match idRef="Keywords_new_zFealand_bank_account_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- رقم الحساب
- حساب بنكي
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr

## <a name="new-zealand-drivers-license-number"></a>رقم رخصة القيادة في نيوزيلندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نقش أبجدي رقمي لثمانية أحرف

### <a name="pattern"></a>نمط

نقش أبجدي رقمي لثمانية أحرف

- حرفان
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_newzealand_driver_license_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_newzealand_driver_license_number.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_newzealand_driver_license_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- New Zealand Driver License Number -->
      <Entity id="1924b377-d287-49c9-a737-cfe7a8a2615a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
          <Match idRef="Keywords_newzealand_driver_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل #
- برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة الدولية
- تراخيص القيادة الدولية
- اتحاد السيارات nz
- اتحاد السيارات في نيوزيلندا

## <a name="new-zealand-inland-revenue-number"></a>رقم إيرادات نيوزيلندا الداخلية

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

ثمانية أو تسعة أرقام مع محددات اختيارية

### <a name="pattern"></a>نمط

ثمانية أو تسعة أرقام مع محددات اختيارية

- رقمان أو ثلاثة أرقام
- مسافة اختيارية أو واصلة اختيارية
- ثلاثة أرقام
- مسافة اختيارية أو واصلة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_new_zealand_inland_revenue_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_new_zealand_inland_revenue_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_new_zealand_inland_revenue_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- New Zealand Inland Revenue Number -->
      <Entity id="dd0fe2bc-7bcf-455f-bac1-83b1e3eb25fd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
          <Match idRef="Keywords_new_zealand_inland_revenue_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- رقم ird.
- ird no #
- nz ird
- /&ة نيوزيلندا
- رقم ird
- رقم الإيرادات الداخلية

## <a name="new-zealand-ministry-of-health-number"></a>وزارة الصحة في نيوزيلندا

### <a name="format"></a>تنسيق

ثلاثة أحرف وأربعة أرقام

### <a name="pattern"></a>نمط

- ثلاثة أحرف (غير حساسة لحالة الأحرف) باستثناء 'I' و'O'
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_new_zealand_ministry_of_health_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_nz_terms.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_new_zealand_ministry_of_health_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
    <!-- New Zealand Health Number -->
    <Entity id="2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
          <Match idRef="Keyword_nz_terms" />
      </Pattern>
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
       </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- نيوزيلندا
- الفهرس الصحي الوطني
- NHI #
- الفهرس الصحي الوطني #

## <a name="new-zealand-physical-addresses"></a>العناوين المادية في نيوزيلندا

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من نيوزيلندا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="new-zealand-social-welfare-number"></a>رقم الرعاية الاجتماعية في نيوزيلندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>نمط

تسعة أرقام

- ثلاثة أرقام
- واصلة اختيارية
- ثلاثة أرقام
- واصلة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_newzealand_social_welfare_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_newzealand_social_welfare_number.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_newzealand_social_welfare_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Newzealand Social Welfare Number -->
      <Entity id="20f3c48d-4ac1-4cd2-86bd-34ecc1826e9d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
          <Match idRef="Keywords_newzealand_social_welfare_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- الرعاية الاجتماعية #
- الرعاية الاجتماعية #
- رقم الرعاية الاجتماعية.
- رقم الرعاية الاجتماعية
- swn #

## <a name="norway-identification-number"></a>رقم تعريف النرويج

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>نمط

11 رقما:

- ستة أرقام بتنسيق DD ولاي، وهي تاريخ الميلاد
- رقم فردي مكون من ثلاثة أرقام
- خانتا اختيار رقميتان

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_norway_id_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_norway_id_number.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_norway_id_numbe عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Norway Identification Number -->
<Entity id="d4c8a798-e9f2-4bd3-9652-500d24080fc3" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_norway_id_number"/>
     <Match idRef="Keyword_norway_id_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_norway_id_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- رقم التعريف الشخصي
- رقم المعرف النرويجي
- رقم المعرف
- تحديد
- رقم الشخص
- Fødselsnummer

## <a name="norway-physical-addresses"></a>العناوين المادية في النرويج

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من النرويج. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="philippines-unified-multi-purpose-identification-number"></a>رقم تعريف موحد متعدد الأغراض في الفليبين

### <a name="format"></a>تنسيق

12 رقما مفصولة بواصلات

### <a name="pattern"></a>نمط

12 رقما:

- أربعة أرقام
- واصلة
- سبعة أرقام
- واصلة
- رقم واحد

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_philippines_unified_id عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_philippines_id.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- معرف موحد متعدد الأغراض
- معرف UMID
- بطاقة الهوية
- معرف Pinag-isang Multi-Layunin

## <a name="poland-drivers-license-number"></a>رقم رخصة القيادة في بولندا

### <a name="format"></a>تنسيق

14 رقما تحتوي على شرطتين مائلتين للأمام

### <a name="pattern"></a>نمط

14 رقما واثنين من الشرطة المائلة للأمام:

- خمسة أرقام
- شرطة مائلة للأمام
- رقمين
- شرطة مائلة للأمام
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_poland_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_poland_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Poland Driver's License Number -->
      <Entity id="24d51f99-ee9e-4060-a077-cae58cab1ee4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_poland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_poland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_poland_eu_drivers_license_number"></a>s_license_number Keywords_poland_eu_driver

- prawo jazdy
- prawa jazdy

## <a name="poland-identity-card"></a>بطاقة هوية في بولندا

### <a name="format"></a>تنسيق

ثلاثة أحرف وستة أرقام

### <a name="pattern"></a>نمط

ثلاثة أحرف (غير حساسة لحالة الأحرف) متبوعة بستة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_polish_national_id عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_polish_national_id_passport_number.
- يمر المجموع الاختباري.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa i nr dowodu tożsamości
- Dowód Tożsamości
- داو. Os.

## <a name="poland-national-id-pesel"></a>المعرف الوطني في بولندا (PESEL)

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>نمط

- ستة أرقام تمثل تاريخ الميلاد بالتنسيق YYMMDD
- أربعة أرقام
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_pesel_identification_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_pesel_identification_number.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_pesel_identification_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
      <!-- Poland National ID (PESEL) -->
      <Entity id="E3AAF206-4297-412F-9E06-BA8487E22456" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_pesel_identification_number" />
          <Match idRef="Keyword_pesel_identification_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_pesel_identification_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osobisty
- dowódosobisty
- رقم niepowtarzalny
- رقم niepowtarzalny
- nr.-pesel
- nr-pesel
- رقم identyfikacyjny
- البسل
- tożsamości narodowej

## <a name="poland-passport-number"></a>رقم جواز سفر بولندا

يتم تضمين كيان نوع المعلومات الحساسة هذا في نوع المعلومات الحساسة لرقم جواز سفر الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

حرفان وسبعة أرقام

### <a name="pattern"></a>نمط

حرفان (غير حساسين لحالة الأحرف) متبوعا بسبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_polish_passport_number_v2` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_polish_national_passport_number` تم العثور عليها.
- تم العثور على كلمة أساسية منها `Keywords_eu_passport_date` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_polish_passport_number_v2` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_polish_national_passport_number` تم العثور عليها.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_polish_passport_number_v2` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
      <!-- Poland Passport Number -->
      <Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_passport_number_v2" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- عدد paszportu
- paszportów رقمي
- paszportowe رقمي
- nr paszportu
- Nr. paszportu
- nr paszportów
- n° منفذ مرور
- منفذ المرور n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="poland-physical-addresses"></a>العناوين المادية لبولاندا

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من بولندا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="poland-regon-number"></a>رقم REGON في بولندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

رقم مكون من 9 أرقام أو 14 رقما

### <a name="pattern"></a>نمط

تسعة أرقام أو 14 رقما:

- تسعة أرقام أو
- تسعة أرقام
- واصله
- خمسة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_polish_regon_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_polish_regon_number.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_polish_regon_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Polish REGON Number  -->
      <Entity id="fc87b421-f437-4f8b-b739-29a735ead0d9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_regon_number" />
          <Match idRef="Keywords_polish_regon_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_regon_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- معرف regon
- رقم إحصائي
- المعرف الإحصائي
- لا إحصائية
- رقم المضلع
- regonid #
- regonno #
- معرف الشركة
- معرف الشركة #
- companyidno #
- numer statystyczny
- إعادة بناء الأرقام
- numerstatystyczny #
- رقم #

## <a name="poland-tax-identification-number"></a>رقم التعريف الضريبي في بولندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

11 رقما بدون مسافات أو محددات

### <a name="pattern"></a>نمط

11 رقما

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_poland_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_poland_eu_tax_file_number` .

```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- خطه التنفيذ الوطنيه #
- خطه التنفيذ الوطنيه
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- معرف ضريبة القيمة المضافة #
- معرف ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- رقم ضريبة القيمة المضافة
- vatid #
- vatid
- vatno #

## <a name="portugal-citizen-card-number"></a>رقم بطاقة المواطنين البرتغاليين

### <a name="format"></a>تنسيق

ثمانية أرقام

### <a name="pattern"></a>نمط

ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_portugal_citizen_card عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_portugal_citizen_card.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- ʖ>>>>>>
- cartão de cidadão
- بطاقة مواطن
- رقم المستند
- documento de identificação
- رقم المعرف
- لا يوجد تعريف
- رقم التعريف
- رقم بطاقة الهوية
- رقم بطاقة الهوية
- بطاقة المعرف الوطنية
- Nic
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- رقم bi في البرتغال

## <a name="portugal-drivers-license-number"></a>رقم رخصة القيادة البرتغالية

### <a name="format"></a>تنسيق

نمطان - حرفان متبوعا ب 5-8 أرقام بأحرف خاصة

### <a name="pattern"></a>نمط

النمط 1: حرفان متبوعا ب 5/6 بأحرف خاصة:

- حرفان (غير حساس لحالة الأحرف)
- واصلة
- خمسة أرقام أو ستة أرقام
- مساحة
- رقم واحد

النمط 2: حرف واحد متبوعا ب 6/8 أرقام بأحرف خاصة:

- حرف واحد (غير حساس لحالة الأحرف)
- واصلة
- ستة أو ثمانية أرقام
- مساحة
- رقم واحد

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_portugal_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_portugal_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Portugal Driver's License Number -->
      <Entity id="977f1e5a-2c33-4bcc-b516-95bb275cff23" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_portugal_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_portugal_eu_drivers_license_number"></a>s_license_number Keywords_portugal_eu_driver

- carteira de motorista
- carteira motorista
- carteira de habilitação
- carteira habilitação
- número de pança
- número pança
- permissão de condução
- permissão condução
- ترخيص Condução Portugal
- carta de condução

## <a name="portugal-passport-number"></a>رقم جواز سفر البرتغال

### <a name="format"></a>تنسيق

حرف واحد متبوعا بستة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرف واحد متبوعا بستة أرقام:

- حرف واحد (غير حساس لحالة الأحرف)
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_portugal_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_portugal_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_portugal_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_portugal_eu_passport_number` تم العثور عليها.

```xml
      <!-- Portugal Passport Number -->
      <Entity id="080a52fd-a7bc-431e-b54d-51f08f59db11" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do passaporte
- جواز سفر برتغالي
- منفذ المرور البرتغالي
- منفذ المرور البرتغالي
- passaporte nلاين
- passeport n والنواة
- números de passaporte
- جواز سفر البرتغالية
- número passaporte
- números passaporte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="portugal-physical-addresses"></a>العناوين المادية البرتغالية

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من البرتغال. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="portugal-tax-identification-number"></a>رقم التعريف الضريبي في البرتغال

### <a name="format"></a>تنسيق

تسعة أرقام ذات مسافات اختيارية

### <a name="pattern"></a>نمط

- ثلاثة أرقام
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_portugal_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_portugal_eu_tax_file_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_portugal_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Portugal Tax Identification Number -->
      <Entity id="65372402-3131-4f1e-9983-4439841d1f15" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
          <Match idRef="Keywords_portugal_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- الشراكه #
- الشراكه
- Nif #
- Nif
- número de identificação fisca
- numero fiscal
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="romania-drivers-license-number"></a>رقم رخصة القيادة في رومانيا

### <a name="format"></a>تنسيق

حرف واحد متبوعا بثمانية أرقام

### <a name="pattern"></a>نمط

حرف واحد متبوعا بثمانية أرقام:

- حرف واحد (غير حساس لحالة الأحرف) أو رقم
- ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_romania_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_romania_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Romania Driver's License Number -->
      <Entity id="b5511ace-2fd8-4ae4-b6fc-c7c6e4689e3c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_romania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_romania_eu_drivers_license_number"></a>s_license_number Keywords_romania_eu_driver

- permis de de deere
- permisnani de deere
- permisؤدي أداة مساعدة
- permisele de deere
- permisele أداة المساعدة
- permis أداة المساعدة

## <a name="romania-passport-number"></a>رقم جواز سفر رومانيا

### <a name="format"></a>تنسيق

ثمانية أو تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

ثمانية أو تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_romania_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_romania_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_romania_eu_passport_date` العادي عن التاريخ بالتنسيق DD MMM/MMM YY (مثال- 01 فبراير/فبراير 10) أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_romania_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_romania_eu_passport_number` تم العثور عليها.

```xml
      <!-- Romania Passport Number -->
      <Entity id="5d31b90c-7fe2-4a76-a14b-767b8fd19d6c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_romania_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numărul pașaportporti numarul pandaportporti numerele pașaportporti Pașaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="romania-personal-numeric-code-cnp"></a>تعليمة برمجية رقمية شخصية في رومانيا (CNP)

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

13 رقما بدون مسافات ومحددات

### <a name="pattern"></a>نمط

- رقم واحد من 1 إلى 9
- ستة أرقام تمثل تاريخ الميلاد (YYMMDD)
- رقمان، يمكن أن يكونا 01-52 أو 99
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_romania_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_romania_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_romania_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Romania Personal Numerical Code (CNP) -->
      <Entity id="eb5fa399-fe28-4c67-8188-d63a616ed89c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
          <Match idRef="Keywords_romania_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- cnp #
- cnp
- cod identificare personal
- cod numeric personal
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscală nr #
- id-ul taxei
- رقم التأمين
- رقم التأمين #
- المعرف الوطني #
- المعرف الوطني
- رقم التعريف الوطني
- număr identificare personal
- هوية număr
- număr personal unic
- număridentitate #
- număridentitate
- numărpersonalunic #
- numărpersonalunic
- număru de identificare fiscală
- numărul de identificare fiscală
- رمز رقمي شخصي
- دبوس #
- دبوس
- ملف الضريبة لا
- رقم ملف الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- رقم تعريف فريد
- رقم هوية فريد
- uniqueidentityno #
- uniqueidentityno

## <a name="romania-physical-addresses"></a>عناوين مادية في رومانيا

يكشف هذا الكيان المسمى غير الملغى عن الأنماط المتعلقة بالعنوان الفعلي من رومانيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="russia-passport-number-domestic"></a>رقم جواز سفر روسيا محليا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

رقم مكون من 10 أرقام

### <a name="pattern"></a>نمط

رقم مكون من 10 أرقام:

- رقمين
- مسافة اختيارية أو واصلة اختيارية
- رقمين
- مساحة اختيارية
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث Regex_Russian_Passport_Number_Domestic regex عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_Russian_Passport_Number.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- رقم جواز السفر
- لا يوجد جواز سفر
- جواز السفر #
- معرف جواز السفر
- جواز سفر #
- رقم جواز السفر #
- паспорт нет
- паспорт المعرف
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #

## <a name="russia-passport-number-international"></a>رقم جواز سفر روسيا الدولي

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

رقم مكون من تسعة أرقام

### <a name="pattern"></a>نمط

رقم مكون من تسعة أرقام:

- رقمين
- مسافة اختيارية أو واصلة اختيارية
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث Regex_Russian_Passport_Number_International regex عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_Russian_Passport_Number.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- رقم جواز السفر
- لا يوجد جواز سفر
- جواز السفر #
- معرف جواز السفر
- جواز سفر #
- رقم جواز السفر #
- паспорт нет
- паспорт المعرف
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #

## <a name="saudi-arabia-national-id"></a>المعرف الوطني للسعودية

### <a name="format"></a>تنسيق

10 أرقام

### <a name="pattern"></a>نمط

10 أرقام متتالية

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_saudi_arabia_national_id عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_saudi_arabia_national_id.

```xml
<!-- Saudi Arabia National ID -->
<Entity id="8c5a0ba8-404a-41a3-8871-746aa21ee6c0" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_saudi_arabia_national_id" />
        <Any minMatches="1">
          <Match idRef="Keyword_saudi_arabia_national_id" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- بطاقة التعريف
- رقم البطاقة
- رقم المعرف
- الوطنية الهوية بطاقة رقم

## <a name="singapore-national-registration-identity-card-nric-number"></a>رقم بطاقة هوية التسجيل الوطنية في سنغافورة (NRIC)

### <a name="format"></a>تنسيق

تسعة أحرف وأرقام

### <a name="pattern"></a>نمط

- تسعة أحرف وأرقام:

- الحرف "F" أو "G" أو "M" أو "S" أو "T" (غير حساس لحالة الأحرف)
- سبعة أرقام
- رقم اختيار أبجدي

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_singapore_nric عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_singapore_nric.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_singapore_nric عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Singapore National Registration Identity Card (NRIC) Number -->
<Entity id="cead390a-dd83-4856-9751-fb6dc98c34da" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_singapore_nric"/>
     <Match idRef="Keyword_singapore_nric"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_singapore_nric"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- بطاقة هوية التسجيل الوطنية
- رقم بطاقة الهوية
- NRIC
- IC
- رقم التعريف الخارجي
- فنلندا
- 身份证
- 身份證

## <a name="slovakia-drivers-license-number"></a>رقم رخصة القيادة السلوفاكية

### <a name="format"></a>تنسيق

حرف واحد متبوعا بسبعة أرقام

### <a name="pattern"></a>نمط

حرف واحد متبوعا بسبعة أرقام

- حرف واحد (غير حساس لحالة الأحرف) أو رقم
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovakia_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_slovakia_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Slovakia Driver's License Number -->
      <Entity id="14240c22-b6de-4ce5-a90b-137f74252513" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovakia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver s_license_number

- vodisksksk preukaz
- vodiské preukazy
- vodiského preukazu
- vodiskskskch preukazov

## <a name="slovakia-passport-number"></a>رقم جواز سفر بورتوفا

### <a name="format"></a>تنسيق

نقش أبجدي رقمي لثمانية أو تسعة أحرف

### <a name="pattern"></a>نمط

حرف واحد (غير حساس لحالة الأحرف) متبوعا بسبعة أرقام أو حرفين (غير حساس لحالة الأحرف) متبوعا بستة أو سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovakia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_slovakia_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovakia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_slovakia_eu_passport_number` تم العثور عليها.

```xml
      <!-- Slovakia Passport Number -->
      <Entity id="238e1f08-d80e-4793-af33-9b57918335b7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- ííslo pasu
- íísla pasov
- pas  أذونات.
- Passeport n°
- n° Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="slovakia-personal-number"></a>الرقم الشخصي ل لمزوفا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

تسعة أرقام أو 10 أرقام تحتوي على مائلة عكسية اختيارية

### <a name="pattern"></a>نمط

- ستة أرقام تمثل تاريخ الميلاد
- شرطة مائلة اختيارية (/)
- ثلاثة أرقام
- رقم اختيار واحد اختياري

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_slovakia_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_slovakia_eu_national_id_card` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_slovakia_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Slovakia Personal Number -->
      <Entity id="951c26b7-3b35-4f73-924b-15dd599cb9ab" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
          <Match idRef="Keywords_slovakia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- رقم الميلاد
- ííslo národnej identifikanej karty
- ííslo obíianského preukazu
- daňové îíslo
- رقم المعرف
- لا يوجد تعريف
- رقم التعريف
- identifikaáná كارتا  ه
- identifikaíné ííslo
- رقم بطاقة الهوية
- رقم بطاقة الهوية
- národná identifikaáná zna ak á
- الرقم الوطني
- رقم وطني #
- nemzeti személyazonosító igazolvány
- رقم شخصي #
- rč
- rodne cislo
- rodné ííslo
- رقم الضمان الاجتماعي
- Ssn #
- Ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyzolvány szám
- ملف الضريبة لا
- رقم ملف الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="slovakia-physical-addresses"></a>العناوين المادية ل لمزوفا

يكشف هذا الكيان المسمى غير الملغى عن الأنماط المتعلقة بالعنوان الفعلي من تلقائيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="slovenia-drivers-license-number"></a>رقم رخصة القيادة السلوفينية

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovenia_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_slovenia_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Slovenia Driver's License Number -->
      <Entity id="d5bc089a-f2ee-433d-a6b1-5c253051d6f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovenia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_slovenia_eu_drivers_license_number"></a>s_license_number Keywords_slovenia_eu_driver

- voznijeko dovoljenje
- ترخيص vozni دوليةka ztevilka
- vozniلفkih dovoljenj
- ztevilka voznijakega dovoljenja
- številke vozniških dovoljenj

## <a name="slovenia-passport-number"></a>رقم جواز السفر السلوفيني

### <a name="format"></a>تنسيق

حرفان متبوعا بسبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرفان متبوعا بسبعة أرقام:

- الحرف "P"
- حرف واحد من الأحرف الكبيرة
- سبعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovenia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_slovenia_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovenia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_slovenia_eu_passport_number` تم العثور عليها.

```xml
      <!-- Slovenia Passport Number -->
      <Entity id="235b7976-7bbe-4df5-bb40-08678e749d1a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- wtevilka potnega lista
- potek veljavnosti
- قائمة potni #
- datum rojstva
- قائمة potni
- ovtevilke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="slovenia-physical-addresses"></a>العناوين المادية السلوفينية

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من  السلوفينية. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="slovenia-tax-identification-number"></a>رقم التعريف الضريبي السلوفيني

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

- رقم واحد من 1 إلى 9
- ستة أرقام
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_slovenia_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_slovenia_eu_tax_file_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_slovenia_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Slovenia Tax Identification Number -->
      <Entity id="e47b071e-c352-4d70-8241-8c215ad65505" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
          <Match idRef="Keywords_slovenia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- dav jarna ذتيvilka
- identifikacijska ذtevilka davka
- edtevilka davذne datoteke
- ملف الضريبة لا
- رقم ملف الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="slovenia-unique-master-citizen-number"></a>رقم مواطن رئيسي فريد في  السلوفينية

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

13 رقما بدون مسافات أو محددات

### <a name="pattern"></a>نمط

13 رقما في النمط المحدد:

- سبعة أرقام تتوافق مع تاريخ الميلاد (DDMMLLL) حيث تتوافق "LLL" مع الأرقام الثلاثة الأخيرة من سنة الميلاد
- رقمان يتوافقان مع منطقة الميلاد "50"
- ثلاثة أرقام تتوافق مع مجموعة من الجنس والرقم التسلسلي للأشخاص الذين ولدوا في نفس اليوم. 000-499 للذكر و500-999 للإناث.
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_slovenia_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_slovenia_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_slovenia_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Slovenia Unique Master Citizen Number -->
      <Entity id="68948b27-803d-41e4-adf1-13e05eb541bb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
          <Match idRef="Keywords_slovenia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena ütevilka gvilnega drjaavljana
- رمز المشاعر
- enotna maticna riftevilka obcana
- بطاقة المعرف
- رقم التعريف
- identifikacijska ذتيvilka
- بطاقة هوية
- معرف nacionalna
- قائمة nacionalni potni
- المعرف الوطني
- osebna izkaznica
- osebni koda
- osebni ne
- osebni ذتيvilka
- رمز شخصي
- رقم شخصي
- رمز رقمي شخصي
- ütevilka drjaavljana
- رقم مواطن فريد
- رقم المعرف الفريد
- رقم هوية فريد
- رقم مواطن رئيسي فريد
- رقم تسجيل فريد
- uniqueidentityno #
- uniqueidentityno #

## <a name="south-africa-identification-number"></a>رقم تعريف جنوب أفريقيا

### <a name="format"></a>تنسيق

13 رقما قد تحتوي على مسافات

### <a name="pattern"></a>نمط

13 رقما:

- ستة أرقام بالتنسيق YYMMDD، وهي تاريخ الميلاد
- أربعة أرقام
- مؤشر المواطنين المؤلف من رقم واحد
- الرقم "8" أو "9"
- رقم واحد، وهو رقم المجموع الاختباري

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_south_africa_identification_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_south_africa_identification_number.
- يمر المجموع الاختباري.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- بطاقة الهوية
- المعرّف
- تحديد

## <a name="south-korea-resident-registration-number"></a>رقم التسجيل المقيم في كوريا الجنوبية

### <a name="format"></a>تنسيق

13 رقما تحتوي على واصلة

### <a name="pattern"></a>نمط

13 رقما:

- ستة أرقام بالتنسيق YYMMDD، وهي تاريخ الميلاد
- واصلة
- رقم واحد يحدده القرن والجنس
- رمز منطقة الميلاد المكون من أربعة أرقام
- رقم واحد يستخدم للتمييز بين الأشخاص الذين تتطابق الأرقام السابقة معهم
- خانة اختيار رقمية.

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_south_korea_resident_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_south_korea_resident_number.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_south_korea_resident_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- بطاقة المعرف الوطني
- رقم تسجيل المواطنين
- Jumin deungnok beonho
- RRN
- 주민등록번호

## <a name="spain-dni"></a>DNI أسبانيا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

ثمانية أرقام متبوعة بحرف واحد

### <a name="pattern"></a>نمط

سبعة أرقام متبوعة بحرف واحد

- ثمانية أرقام
- مسافة اختيارية أو واصلة اختيارية
- حرف اختيار واحد (غير حساس لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_spain_eu_national_id_card"` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` البحث عن المحتوى الذي يطابق النمط.

```xml
      <!-- Spain DNI -->
      <Entity id="8e6251b9-47b4-40e8-a42b-0f80876be192" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- dni #
- dni
- dninúmero #
- documento nacional de identidad
- identidad único
- identidadúnico #
- رقم التأمين
- رقم التعريف الوطني
- الهوية الوطنية
- معرف وطني #
- nationalidno #
- نيه #
- نيه
- nienúmero #
- número de identificación
- número nacional identidad
- رقم التعريف الشخصي
- الهوية الشخصية لا
- رقم هوية فريد
- معرف فريد #

## <a name="spain-drivers-license-number"></a>رقم رخصة القيادة الإسبانية

### <a name="format"></a>تنسيق

ثمانية أرقام متبوعة بحرف واحد

### <a name="pattern"></a>نمط

ثمانية أرقام متبوعة بحرف واحد:

- ثمانية أرقام
- رقم واحد أو حرف واحد (غير حساس لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_spain_eu_driver's_license_number` تم العثور عليها.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` البحث عن المحتوى الذي يطابق النمط.

```xml
      <!-- Spain Driver's License Number -->
      <Entity id="d5a82922-b501-4f40-8868-341321146aa2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_spain_eu_drivers_license_number"></a>s_license_number Keywords_spain_eu_driver

- permiso de deción
- permisoón
- de de de
- ناسيا سهى
- permiso
- permiso de deir
- permisos de deir
- permisos
- carnet
- carnet de
- />صفحة/>
- رنينسيا مانيخو

## <a name="spain-passport-number"></a>رقم جواز سفر إسبانيا

### <a name="format"></a>تنسيق

مجموعة مكونة من ثمانية أو تسعة أحرف من الأحرف والأرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

مجموعة مكونة من ثمانية أو تسعة أحرف من الأحرف والأرقام:

- رقمان أو حرفان
- رقم واحد أو حرف واحد (اختياري)
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_spain_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_spain_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_spain_eu_passport_date` العادي عن التاريخ بالتنسيق DD-MM-YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_spain_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_spain_eu_passport_number` تم العثور عليها.

```xml
      <!-- Spain Passport Number -->
      <Entity id="d17a57de-9fa5-4e9f-85d3-85c26d89686e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_spain_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta pandaporte
- número pandaporte
- españa pandaporte
- números de pandaporte
- número de pandaporte
- números pandaporte
- pandaporte no
- Passeport n°
- n° Passeport
- pwaporte no.
- pandaporte n°
- جواز سفر إسبانيا

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="spain-physical-addresses"></a>العناوين الفعلية في أسبانيا

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من إسبانيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="spain-social-security-number-ssn"></a>رقم الضمان الاجتماعي الإسباني (SSN)

### <a name="format"></a>تنسيق

من 11 إلى 12 رقما

### <a name="pattern"></a>نمط

من 11 إلى 12 رقما:

- رقمين
- شرطة مائلة للأمام (اختيارية)
- من سبعة إلى ثمانية أرقام
- شرطة مائلة للأمام (اختيارية)
- رقمين

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_spanish_social_security_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.
- - تم العثور على كلمة أساسية منها `Keywords_spain_eu_ssn_or_equivalent` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_spanish_social_security_number عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
    <!-- Spain SSN -->
    <Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85" relaxProximity="true" >
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spanish_social_security_number" />
          <Match idRef="Keywords_spain_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spanish_social_security_number" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- Ssn
- Ssn #
- الأمن الاجتماعي
- الضمان الاجتماعي لا
- رقم الضمان الاجتماعي
- número de la seguridad social

## <a name="spain-tax-identification-number"></a>رقم التعريف الضريبي الإسباني

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

سبعة أو ثمانية أرقام وحرف واحد أو حرفان في النمط المحدد

### <a name="pattern"></a>نمط

الأشخاص الطبيعيون الأسبانيون مع بطاقة هوية وطنية أسبانيا:

- ثمانية أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

أسبان غير مقيمين بدون بطاقة هوية وطنية أسبانيا

- حرف واحد من الأحرف الكبيرة "L" (حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

الإسبانيون المقيمون الذين تقل أعمارهم عن 14 سنة بدون بطاقة هوية وطنية في إسبانيا:

- حرف واحد من الأحرف الكبيرة "K" (حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

مهى مع رقم تعريف المقيمين

- حرف واحد من الأحرف الكبيرة يكون "X" أو "Y" أو "Z" (حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

أجهزة نواة بدون رقم تعريف نافل

- حرف واحد من الأحرف الكبيرة يكون "M" (حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_tax_file_number` أو `Func_spain_eu_DL_and_NI_number_citizen` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_spain_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_tax_file_number` أو `Func_spain_eu_DL_and_NI_number_citizen` البحث عن المحتوى الذي يطابق النمط.

```xml
      <!-- Spain Tax Identification Number -->
      <Entity id="10f0d113-b0e1-47dc-872a-a4f45b9376a3" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- Cif
- مقتباس #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- ملف الضريبة لا
- رقم ملف الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="sql-server-connection-string"></a>سلسلة اتصال SQL Server

### <a name="format"></a>تنسيق

السلسلة "معرف المستخدم" أو "معرف المستخدم" أو "uid" أو "UserId" متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه.

### <a name="pattern"></a>نمط

- السلسلة "معرف المستخدم" أو "معرف المستخدم" أو "uid" أو "UserId"
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "Password" أو "pwd" حيث لا يسبق "pwd" حرف صغير
- علامة التساوي (=)
- أي حرف ليس علامة الدولار ($) أو رمز النسبة المئوية (٪)، أو أكبر من الرمز (>)، أو عند الرمز (@)، أو علامة الاقتباس (")، أو فاصلة منقوطة (;)، أو قوس أيسر([)، أو قوس أيسر ({)
- أي تركيبة من 7 إلى 128 حرفا ليست فاصلة منقوطة (;) أو شرطة مائلة للأمام (/) أو علامة اقتباس (")
- فاصلة منقوطة (;) أو علامة الاقتباس (")

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي CEP_Regex_SQLServerConnectionString عن المحتوى الذي يتطابق مع النمط.
- لم يتم العثور على كلمة أساسية من CEP_GlobalFilter.
- لا يعثر التعبير العادي CEP_PasswordPlaceHolder على محتوى يطابق النمط.
- لا يعثر التعبير العادي CEP_CommonExampleKeywords على محتوى يطابق النمط.

```sql
<!---SQL Server Connection String>
<Entity id="e76b6205-d3cb-46f2-bd63-c90153f2f97d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_SQLServerConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_GlobalFilter" />
            <Match idRef="CEP_PasswordPlaceHolder" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- بعض كلمات المرور
- somepassword
- secretPassword
- عينه

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

يعرف نوع المعلومات الحساسة هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- كلمة المرور أو pwd متبوعة بمسافات 0-2، وعلامة التساوي (=)، ومسافات 0-2، وعلامة نجمية (*) -OR-
- كلمة المرور أو pwd متبوعة ب:
    - علامة التساوي (=)
    - أقل من رمز (<)
    - أي تركيبة من 1-200 حرف عبارة عن أحرف كبيرة أو صغيرة أو أرقام أو علامة نجمية (*) أو واصلة (-) أو تسطير (_) أو حرف مسافة بيضاء
    - رمز أكبر من (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

يعرف نوع المعلومات الحساسة هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي

## <a name="surgical-procedures"></a>الإجراءات الجراحية

يكشف هذا الكيان المسمى غير المكتظ بالمصطلحات المتعلقة بالإجراءات الطبية، مثل *الإلحاق*.  وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="sweden-drivers-license-number"></a>رقم رخصة القيادة في السويد

### <a name="format"></a>تنسيق

10 أرقام تحتوي على واصلة

### <a name="pattern"></a>نمط

10 أرقام تحتوي على واصلة:

- ستة أرقام
- واصلة
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_sweden_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_sweden_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Sweden Driver's License Number -->
      <Entity id="70088720-90dd-47f5-805e-5525f3567391" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_sweden_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_sweden_eu_drivers_license_number"></a>s_license_number Keywords_sweden_eu_driver

- ajokortti
- permis de de deere
- ajokortin numero
- lic kulj consolejat.
- lic برنامج التشغيل.
- körkort
- numărul permisnani de أداة إزالة الأدبر
- שאָפער דערלויבעניש נומער
- förare lic.
- דריווערס דערלויבעניש
- körkortsnummer

## <a name="sweden-national-id"></a>المعرف الوطني للسويد

### <a name="format"></a>تنسيق

10 أو 12 رقما ومحدد اختياري

### <a name="pattern"></a>نمط

10 أو 12 رقما ومحدد اختياري:

- رقمان (اختياري)
- ستة أرقام بتنسيق التاريخ YYMMDD
- محدد "-" أو "+" (اختياري)
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_swedish_national_identifier` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_swedish_national_identifier`
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_swedish_national_identifier` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- Sweden National ID -->
    <Entity id="f69aaf40-79be-4fac-8f05-fd1910d272c8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_swedish_national_identifier" />
        <Match idRef="Keywords_swedish_national_identifier" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_swedish_national_identifier" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- المعرف لا
- رقم المعرف
- معرف #
- لا يوجد تعريف
- رقم التعريف
- identifikationsnumret #
- identifikationsnumret
- التعامل مع الهويات
- مستند هوية
- لا هوية
- رقم الهوية
- id-nummer
- المعرف الشخصي
- رقم الشخص #
- رقم الشخص
- skatteidentifikationsnummer

## <a name="sweden-passport-number"></a>رقم جواز سفر السويد

### <a name="format"></a>تنسيق

ثمانية أرقام

### <a name="pattern"></a>نمط

ثمانية أرقام متتالية

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_sweden_passport_number عن المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_sweden_passport` تم العثور عليها.
- يبحث التعبير `Regex_sweden_eu_passport_date` العادي عن تاريخ بتنسيق DD MMM/MMM YY (01 JAN/JAN 12) أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_sweden_passport_number عن المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_sweden_passport` تم العثور عليها.

```xml
    <!-- Sweden Passport Number -->
    <Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_sweden_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- بطاقة تسجيل الأشخاص الذين تم تسجيلهم
- رسوم معالجة g3
- إدخال متعدد
- Numéro de passeport
- passeport n °
- passeport غير
- منفذ المرور #
- منفذ المرور #
- passeportnon
- passeportn °
- رقم المرور
- تمرير nr
- تأشيرة الشينجن
- تواشير الشينجن
- إدخال واحد
- تمرير sverige
- متطلبات طلب الحصول على
- معالجة الملفات
- نوع

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية

## <a name="sweden-physical-addresses"></a>عناوين فعلية في السويد

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من السويد. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="sweden-tax-identification-number"></a>رقم التعريف الضريبي في السويد

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

10 أرقام رمزا في النمط المحدد

### <a name="pattern"></a>نمط

10 أرقام رمز:

- ستة أرقام تتوافق مع تاريخ الميلاد (YYMMDD)
- علامة الجمع أو علامة الطرح
- ثلاثة أرقام تجعل رقم التعريف فريدا حيث:
  - بالنسبة للأرقام التي تم إصدارها قبل عام 1990، يحدد الرقم السابع والرقم الثامن مقاطعة الميلاد أو الأشخاص الذين يولدون في الخارج
  - الرقم في الموضع التاسع يشير إلى نوع الجنس حسب الأرقام الفردية للذكور أو حتى للإناث
- خانة اختيار واحدة

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_sweden_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_sweden_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_sweden_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Sweden Tax Identification Number -->
      <Entity id="139acba0-a5bc-4fbb-876d-f7a493ae8a40" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Match idRef="Keywords_sweden_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_sweden_eu_telephone_number" />
            <Match idRef="Keywords_sweden_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- رقم المعرف الشخصي
- رقم الشخص
- رقم معرف skatt
- تعريف skatt
- skattebetalarens identifikationsnummer
- صفيح sverige
- ملف الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="swift-code"></a>رمز SWIFT

### <a name="format"></a>تنسيق

أربعة أحرف متبوعة ب 5-31 حرفا أو رقما

### <a name="pattern"></a>نمط

أربعة أحرف متبوعة ب 5-31 حرفا أو رقما:

- رمز بنكي مكون من أربعة أحرف (غير حساس لحالة الأحرف)
- مساحة اختيارية
- 4-28 حرفا أو رقما (رقم الحساب البنكي الأساسي (BBAN))
- مساحة اختيارية
- حرف أو ثلاثة أحرف (باقي BBAN)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_swift عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_swift.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_swift"></a>Keyword_swift

- المنظمة الدولية لتوحيد المقاييس 9362
- iso 9362
- iso9362
- سويفت #
- swiftcode
- رقم سويفت
- رقم swiftrouting
- رمز swift
- رقم سريع #
- رقم التوجيه السريع
- رقم bic
- تعليمة bic البرمجية
- Bic #
- Bic #
- رمز معرف البنك
- المنظمة الدولية للتطبيع 9362
- سريع #
- رمز SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- \# BIC
- code identificateur de deque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT 番号
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード

## <a name="switzerland-physical-addresses"></a>العناوين المادية في سويسرا

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من سويسرا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="switzerland-ssn-ahv-number"></a>رقم SSN AHV في سويسرا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

رقم مكون من 13 رقما

### <a name="pattern"></a>نمط

رقم مكون من 13 رقما:

- ثلاثة أرقام - 756
- نقطة اختيارية
- أربعة أرقام
- نقطة اختيارية
- أربعة أرقام
- نقطة اختيارية
- رقمين

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_swiss_social_security_number_ahv عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_swiss_social_security_number_ahv.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_swiss_social_security_number_ahv عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Swiss SSN AHV Number -->
      <Entity id="277cfa4b-6eaa-4a1b-9492-099dec849971" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
          <Match idRef="Keywords_swiss_social_security_number_ahv" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- ahv
- Ssn
- Pid
- رقم التأمين
- personalidno #
- رقم الضمان الاجتماعي
- رقم المعرف الشخصي
- رقم التعريف الشخصي.
- تأمين #
- uniqueidno #
- رقم التعريف الفريد.
- رقم avs
- الهوية الشخصية بلا رقم versicherungsnummer
- رقم معرف
- niczigartige identität niه
- sozialversicherungsnummer
- معرف تعريف الموظفين
- numéro de sécurité sociale

## <a name="taiwan-national-identification-number"></a>رقم التعريف الوطني التايواني

### <a name="format"></a>تنسيق

حرف واحد (باللغة الإنجليزية) متبوعا بتسعة أرقام

### <a name="pattern"></a>نمط

حرف واحد (باللغة الإنجليزية) متبوعا بتسعة أرقام:

- حرف واحد (باللغة الإنجليزية، غير حساس لحالة الأحرف)
- الرقم "1" أو "2"
- ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_taiwanese_national_id عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_taiwanese_national_id.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_taiwanese_national_id عن المحتوى الذي يتطابق مع النمط.
- يمر المجموع الاختباري.

```xml
<!-- Taiwanese National ID -->
<Entity id="4C7BFC34-8DD1-421D-8FB7-6C6182C2AF03" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_taiwanese_national_id" />
          <Match idRef="Keyword_taiwanese_national_id" />
      </Pattern>
       <Pattern confidenceLevel="75">
         <IdMatch idRef="Func_taiwanese_national_id" />
       </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_taiwan_national_id"></a>Keyword_taiwan_national_id

- 身份證字號
- 身份證
- 身份證號碼
- 身份證號
- 身分證字號
- 身分證
- 身分證號碼
- 身份證號
- 身分證統一編號
- 國民身分證統一編號
- 簽名
- 蓋章
- 簽名或蓋章
- 簽章

## <a name="taiwan-passport-number"></a>رقم جواز سفر تايوان

### <a name="format"></a>تنسيق

- رقم جواز السفر البيومتري: تسعة أرقام
- رقم جواز سفر غير قياسي: تسعة أرقام

### <a name="pattern"></a>نمط
رقم جواز السفر البيومتري:

- الحرف "3"
- ثمانية أرقام

رقم جواز السفر غير البيومتري:

- تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_taiwan_passport عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_taiwan_passport.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- رقم جواز سفر ROC
- رقم جواز السفر
- لا يوجد جواز سفر
- رقم جواز السفر
- جواز السفر #
- 护照
- 中華民國護照
- Zhînghuá Mínguó hùzhào

## <a name="taiwan-resident-certificate-arctarc-number"></a>رقم الشهادة المقيمة في تايوان (ARC/TARC)

### <a name="format"></a>تنسيق

10 أحرف ورقم

### <a name="pattern"></a>نمط

10 أحرف ورقم:

- حرفان (غير حساس لحالة الأحرف)
- ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_taiwan_resident_certificate عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_taiwan_resident_certificate.

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- شهادة مقيمة
- شهادة مقيمة
- شهادة مقيمة.
- بطاقة التعريف
- شهادة مقيمة في البلد
- قوس
- شهادة مقيمة في منطقة تايوان
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證

## <a name="thai-population-identification-code"></a>رمز تعريف السكان التايلاندي

### <a name="format"></a>تنسيق

13 رقما

### <a name="pattern"></a>نمط

13 رقما:

- الرقم الأول ليس صفرا أو تسعة
- 12 رقما

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Thai_Citizen_Id عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_Thai_Citizen_Id.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Thai_Citizen_Id عن المحتوى الذي يتطابق مع النمط.

```xml
<!-- Thai Citizen ID -->
-<Entity id="44ca9e86-ead7-4c5d-884a-e2eaa401515e" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
      <Match idRef="Keyword_Thai_Citizen_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- رقم المعرف
- رقم التعريف
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkey-national-identification-number"></a>رقم التعريف الوطني لتركيا

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>نمط

11 رقما

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Turkish_National_Id عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_Turkish_National_Id.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Turkish_National_Id عن المحتوى الذي يتطابق مع النمط.

```xml
<!-- Turkish National Identity -->
-<Entity id="fb621f20-3876-4cfc-acec-8c8e73ca32c7" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Turkish_National_Id"/>
      <Match idRef="Keyword_Turkish_National_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Turkish_National_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik numarası
- Vatandaılık numarası
- Vatandaılık no

## <a name="turkey-physical-addresses"></a>العناوين المادية لتركيا

يكشف هذا الكيان المسمى غير المفكك عن الأنماط المتعلقة بالعنوان الفعلي من تركيا. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="types-of-medication"></a>أنواع الأدوية

يكشف هذا الكيان المسمى غير المكتظ بأسماء الأدوية، مثل *الأدوية.*  وهو يدعم مصطلحات اللغة الإنجليزية فقط. كما أنها مضمنة في [جميع الشروط والأحكام الطبية](#all-medical-terms-and-conditions) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

عاليه

## <a name="uk-drivers-license-number"></a>بريطانيا. رقم رخصة القيادة

### <a name="format"></a>تنسيق

تركيبة من 18 حرفا ورقما بالتنسيق المحدد

### <a name="pattern"></a>نمط

18 حرفا ورقما:

- خمسة أحرف (غير حساسة لحالة الأحرف) أو الرقم "9" بدلا من حرف.
- رقم واحد.
- خمسة أرقام بتنسيق التاريخ MMDDY لتاريخ الميلاد. يتم زيادة الحرف السابع بمقدار 50 إذا كان برنامج التشغيل أنثى؛ على سبيل المثال، من 51 إلى 62 بدلا من 01 إلى 12.
- حرفان (غير حساسين لحالة الأحرف) أو الرقم "9" بدلا من حرف.
- خمسة أرقام.

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_uk_drivers_license` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_eu_driver's_license_number` .
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_uk_drivers_license` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- U.K. Driver's License Number -->
    <Entity id="f93de4be-d94c-40df-a8be-461738047551" patternsProximity="300" recommendedConfidence="75" relaxProximity="true" >
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_uk_drivers_license" />
          <Match idRef="Keywords_eu_driver's_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_uk_drivers_license" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

## <a name="uk-electoral-roll-number"></a>بريطانيا. رقم لفة

### <a name="format"></a>تنسيق

حرفان متبوعا بأرقام من 1 إلى 4

### <a name="pattern"></a>نمط

حرفان (غير حساسين لحالة الأحرف) متبوعا بأرقام من 1 إلى 4

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_uk_electoral عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_uk_electoral.

```xml
<!-- U.K. Electoral Number -->
<Entity id="a3eea206-dc0c-4f06-9e22-aa1be3059963" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_uk_electoral" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_electoral" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- رئيس مجلس الشورى
- نموذج التزكية
- سجل السجلات
- لفة

## <a name="uk-national-health-service-number"></a>بريطانيا. رقم خدمة الصحة الوطنية

### <a name="format"></a>تنسيق

10-17 رقما مفصولة بمسافات

### <a name="pattern"></a>نمط

من 10 إلى 17 رقما:

- إما 3 أو 10 أرقام
- مساحة
- ثلاثة أرقام
- مساحة
- أربعة أرقام

### <a name="checksum"></a>المجموع الاختباري

نعم

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_uk_nhs_number عن المحتوى الذي يتطابق مع النمط.
- أحد الإجراءات التالية صحيح:
    - تم العثور على كلمة أساسية من Keyword_uk_nhs_number.
    - تم العثور على كلمة أساسية من Keyword_uk_nhs_number1.
    - تم العثور على كلمة أساسية من Keyword_uk_nhs_number_dob.
- يمر المجموع الاختباري.

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- خدمة الصحة الوطنية
- الصحي
- هيئة الخدمات الصحية
- هيئة الصحة

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- معرف المريض
- تعريف المريض
- المريض لا
- رقم المريض

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- دوب
- D.O.B
- تاريخ الميلاد
- تاريخ الميلاد

## <a name="uk-national-insurance-number-nino"></a>بريطانيا. رقم التأمين الوطني (NINO)

يتم تضمين كيان نوع المعلومات الحساسة هذا في نوع المعلومات الحساسة لرقم التعريف الوطني للاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

سبعة أحرف أو تسعة أحرف مفصولة بمسافات أو شرط

### <a name="pattern"></a>نمط

نمطان محتملان:

- حرفان (تستخدم NINOs الصالحة أحرفا معينة فقط في هذه البادئة، والتي يقوم هذا النمط بالتحقق من صحتها؛ غير حساسة لحالة الأحرف)
- ستة أرقام
- إما 'A' أو 'B' أو 'C' أو 'D' (مثل البادئة، يتم السماح بأحرف معينة فقط في اللاحقة؛ غير حساسة لحالة الأحرف)

او

- حرفان
- مسافة أو شرطة
- رقمين
- مسافة أو شرطة
- رقمين
- مسافة أو شرطة
- رقمين
- مسافة أو شرطة
- إما 'A' أو 'B' أو 'C' أو 'D'

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_uk_nino عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_uk_nino.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_uk_nino عن المحتوى الذي يتطابق مع النمط.

```xml
    <!-- U.K. NINO -->
    <Entity id="16c07343-c26f-49d2-a987-3daf717e94cc" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nino" />
        <Match idRef="Keyword_uk_nino" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_nino" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- رقم التأمين الوطني
- مساهمات التأمين الوطنية
- قانون الحماية
- التامين
- رقم الضمان الاجتماعي
- تطبيق التأمين
- تطبيق طبي
- التأمين الاجتماعي
- العناية الطبية
- الضمان الاجتماعي
- الولايات المتحدة العظمى
- رقم NI
- رقم NI.
- ني #
- ني #
- التامين #
- رقم التأمين
- الطمأنينة الوطنية #
- رقم الأرقام الوطنية

## <a name="uk-physical-addresses"></a>بريطانيا. العناوين الفعلية

يكشف هذا الكيان المسمى غير الملغى عن الأنماط المتعلقة بالعنوان الفعلي من المملكة المتحدة. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="uk-unique-taxpayer-reference-number"></a>بريطانيا. رقم مرجع فريد ل "مرجع ما بعد الإسناد"

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومحددات

### <a name="pattern"></a>نمط

10 أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_uk_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_uk_eu_tax_file_number` .

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- رقم الضريبة
- ملف الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #

## <a name="us-bank-account-number"></a>رقم الحساب البنكي الأمريكي

### <a name="format"></a>تنسيق

من 6 إلى 17 رقما

### <a name="pattern"></a>نمط

من 6 إلى 17 رقما متتاليا

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_usa_bank_account_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_usa_Bank_Account.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- التحقق من رقم الحساب
- تدقيق الحساب
- تدقيق الحساب #
- التحقق من رقم Acct
- التحقق من Acct #
- التحقق من رقم Acct.
- التحقق من رقم الحساب.
- رقم الحساب البنكي
- حساب بنكي #
- رقم Acct البنكي
- Acct البنكي #
- رقم Acct البنكي.
- رقم الحساب البنكي.
- رقم حساب التوفير
- حساب التوفير.
- حساب التوفير #
- رقم Acct للحفظ
- توفير Acct #
- Savings Acct No.
- رقم حساب التوفير.
- رقم حساب الخصم
- حساب الخصم
- حساب الخصم #
- رقم Acct للخصم
- أككت الخصم #
- رقم Acct للخصم.
- رقم حساب الخصم.

## <a name="us-drivers-license-number"></a>رقم رخصة القيادة الأمريكية

### <a name="format"></a>تنسيق

يعتمد على الحالة

### <a name="pattern"></a>نمط

يعتمد على الولاية - على سبيل المثال، نيويورك:

- ستتطابق تسعة أرقام منسقة مثل ddd ddd ddd.
- لن تتطابق تسعة أرقام مثل ddddddd.

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_new_york_drivers_license_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_[state_name]_drivers_license_name.
- تم العثور على كلمة أساسية من Keyword_us_drivers_license.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_new_york_drivers_license_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_[state_name]_drivers_license_name.
- تم العثور على كلمة أساسية من Keyword_us_drivers_license_abbreviations.
- لم يتم العثور على كلمة أساسية من Keyword_us_drivers_license.

```xml
<Entity id="dfeb356f-61cd-459e-bf0f-7c6d28b458c6 patternsProximity="300">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license" />
    </Pattern>
    <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license_abbreviations" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_us_drivers_license" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- المعرّف
- معرفات
- DL #
- DLS #
- CDL #
- CDLS #
- معرف #
- معرفات #
- رقم المعرف
- أرقام المعرف
- يسانس
- يسانس #
- DLN

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- برنامج تشغيل
- برامج تشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- Lic برنامج التشغيل
- Lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- DriversLic
- DriversLics
- رخصة القيادة
- تراخيص برامج التشغيل
- Lic برامج التشغيل
- Lics برامج التشغيل
- رخصه
- تراخيص برامج التشغيل
- Lic للسائق
- Lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- Lic للسائق
- Lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- برنامج تشغيل sLic
- برامج التشغيل sLics
- رخصة القيادة
- تراخيص برامج التشغيل
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- تراخيص القيادة
- رقم التعريف
- أرقام التعريف
- تحديد #
- بطاقة المعرف
- بطاقات المعرف
- بطاقة التعريف
- بطاقات التعريف
- برنامج تشغيل #
- برامج تشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- Lic برنامج التشغيل #
- Lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- DriversLic #
- DriversLics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- Lic برامج التشغيل #
- Lics برامج التشغيل #
- رخصه #
- تراخيص برامج التشغيل #
- Lic للسائق #
- Lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- Lic للسائق #
- Lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- برنامج تشغيل sLic #
- برامج التشغيل sLics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- بطاقة المعرف #
- بطاقات المعرف #
- بطاقة التعريف #
- بطاقات التعريف #

#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- اختصار الحالة (على سبيل المثال، "NY")
- اسم الولاية (على سبيل المثال، "نيويورك")

## <a name="us-individual-taxpayer-identification-number-itin"></a>رقم التعريف الفردي للولايات المتحدة (ITIN)

### <a name="format"></a>تنسيق

تسعة أرقام تبدأ ب "9" وتحتوي على "7" أو "8" كرقم الرابع، ويتم تنسيقها اختياريا بمسافات أو شرط

### <a name="pattern"></a>نمط

تنسيق:

- الرقم "9"
- رقمين
- مسافة أو شرطة
- a "7" أو "8"
- رقم
- مسافة أو شرطة
- أربعة أرقام

منسق:

- الرقم "9"
- رقمين
- a "7" أو "8"
- خمسة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_formatted_itin عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_itin.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_unformatted_itin عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_itin.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_formatted_itin أو Func_unformatted_itin عن المحتوى الذي يتطابق مع النمط.

```xml
    <!-- U.S. Individual Taxpayer Identification Number (ITIN) -->
    <Entity id="e55e2a32-f92d-4985-a35d-a0b269eb687b" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_formatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_formatted_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_unformatted_itin" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_itin"></a>Keyword_itin

- دافعي الضرائب
- معرف الضريبة
- التعريف الضريبي
- itin
- i.t.i.n.
- Ssn
- القصدير
- الضمان الاجتماعي
- مدفع الضريبة
- تثبيتات
- سيارة أجرة
- أجهزة فردية

## <a name="us-physical-addresses"></a>العناوين الفعلية في الولايات المتحدة

يكشف هذا الكيان المسمى غير الملغى عن الأنماط المتعلقة بالعنوان الفعلي من الولايات المتحدة. كما أنها مضمنة في [كافة العناوين المادية](#all-physical-addresses) المجمعة المسماة ENTITY SIT.

### <a name="confidence-level"></a>مستوى الثقة

المتوسطه

## <a name="us-social-security-number-ssn"></a>رقم الضمان الاجتماعي (SSN) في الولايات المتحدة

### <a name="format"></a>تنسيق

تسعة أرقام، والتي قد تكون في نمط منسق أو غير منسق

> [!NOTE]
> إذا تم إصداره قبل منتصف عام 2011، فإن SSN لديه تنسيق قوي حيث يجب أن تقع أجزاء معينة من الرقم ضمن نطاقات معينة لتكون صالحة (ولكن لا يوجد مجموعة تدقيق).

### <a name="pattern"></a>نمط

تبحث أربع دالات عن SSNs في أربعة أنماط مختلفة:

- Func_ssn البحث عن شبكات SSN ذات تنسيق قوي ما قبل 2011 تم تنسيقها بشرطات أو مسافات (ddd-dddd OR ddd ddd)
- Func_unformatted_ssn البحث عن شبكات SSN ذات تنسيق قوي ما قبل 2011 غير منسقة كتسع أرقام متتالية (dddddddd)
- Func_randomized_formatted_ssn البحث عن SSNs ما بعد 2011 التي تم تنسيقها بشرطات أو مسافات (ddd-dddd OR ddd dddd)
- Func_randomized_unformatted_ssn البحث عن شبكات SSN لما بعد 2011 غير المنسقة كتسع أرقام متتالية (ddddddd)

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_ssn` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ssn` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_unformatted_ssn' عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ssn` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- الدالة `Func_randomized_formatted_ssn` أو `Func_randomized_unformatted_ssn` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ssn` .

```xml
<!-- U.S. Social Security Number (SSN) -->
  <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_randomized_formatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="55">
        <IdMatch idRef="Func_randomized_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
  </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_ssn"></a>Keyword_ssn

- رقم SSA
- رقم الضمان الاجتماعي
- الضمان الاجتماعي #
- الضمان الاجتماعي #
- الضمان الاجتماعي لا
- الضمان الاجتماعي #
- Soc Sec
- SSN
- SSNS
- SSN #
- SS #
- SSID

## <a name="usuk-passport-number"></a>الولايات المتحدة/المملكة المتحدة رقم جواز السفر

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>نمط

- حرف واحد أو رقم واحد
- ثمانية أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_usa_uk_passport عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_uk_eu_passport_number` تم العثور عليها.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_usa_uk_passport عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_uk_eu_passport_number` تم العثور عليها.

```xml
    <!-- U.S. / U.K. Passport Number -->
    <Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
       <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- جواز سفر بريطاني
- جواز سفر المملكة المتحدة

## <a name="ukraine-passport-domestic"></a>جواز سفر محلي في بورتوانا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>نمط

تسعة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث Regex_Ukraine_Passport_Domestic regex عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_Ukraine_Passport_Domestic.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- جواز سفر الولايات المتحدة
- رقم جواز السفر
- لا يوجد جواز سفر
- паспорт України
- номер паспорта
- персональний

## <a name="ukraine-passport-international"></a>جواز سفر نيازكي دولي

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

### <a name="format"></a>تنسيق

نمط أبجدي رقمي مكون من ثمانية أحرف

### <a name="pattern"></a>نمط

نمط أبجدي رقمي مكون من ثمانية أحرف:

- حرفان أو رقمان
- ستة أرقام

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث Regex_Ukraine_Passport_International regex عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من Keyword_Ukraine_Passport_International.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- جواز سفر الولايات المتحدة
- رقم جواز السفر
- لا يوجد جواز سفر
- паспорт України
- номер паспорта
