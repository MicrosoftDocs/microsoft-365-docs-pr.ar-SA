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
description: هناك العديد من أنواع المعلومات الحساسة الجاهزة لاستخدامها في سياسات DLP. تسرد هذه المقالة كل أنواع المعلومات الحساسة هذه، كما تعرض ما تبحث عنه نهج DLP عند الكشف عن كل نوع.
ms.openlocfilehash: a3d2592af6b7692b5a5e634947deb811412b5650
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/18/2022
ms.locfileid: "63568291"
---
# <a name="sensitive-information-type-entity-definitions"></a>تعريفات كيان نوع المعلومات الحساسة

تسرد هذه المقالة كل تعريفات كيان نوع المعلومات الحساسة. يعرض كل تعريف ما تبحث عنه نهج DLP للكشف عن كل نوع. لمعرفة المزيد حول أنواع المعلومات الحساسة، راجع [أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md)

> [!NOTE]
> تعيين مستوى الثقة (عال/متوسط/منخفض) مع رقم دقة (قيمة رقمية من 1 إلى 100)
> - الثقة المنخفضة: 65 أو أقل
> - الثقة المتوسطة: 75
> - الثقة العالية: 85


## <a name="aba-routing-number"></a>رقم توجيه ABA

### <a name="format"></a>تنسيق

تسعة أرقام قد تكون في نمط تم تنسيقه أو غير تنسيقه

### <a name="pattern"></a>النمط

- رقمان في النطاقات 00-12 أو 21-32 أو 61-72 أو 80
- رقمان
- الوابلة الاختيارية
- أربعة أرقام
- الوابلة الاختيارية
- رقم


### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

يكون النهج لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا، ضمن تقارب 300 حرف:
- تعثر الدالة Func_aba_routing المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_ABA_Routing كلمة أساسية.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_aba_routing المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- رقم aba
- aba #
- aba
- شريطي #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- توجيه بنكي #
- bankroutingnumber
- التوجيه #
- التوجيه لا
- رقم التوجيه
- توجيه رقم النقل العام
- التوجيه #
- RTN


## <a name="all-full-names"></a>كل الأسماء الكاملة

جميع الأسماء الكاملة هي كيان مسمى مجمع. يكشف عن الأسماء الكاملة للأشخاص من جميع البلدان/المناطق المدعومة، بما في ذلك أستراليا والصين واليابان والولايات المتحدة والبلدان في الاتحاد الأوروبي. استخدم SIT هذا للكشف عن كل تطابقات الأسماء الكاملة المحتملة.

### <a name="format"></a>تنسيق

متنوعة.

### <a name="pattern"></a>النمط

متنوعة.

### <a name="checksum"></a>الاختبارات

لا.

### <a name="description"></a>الوصف

يتطابق هذا الكيان المسمى SIT مع الأسماء الشخصية التي يمكن أن يحددها الإنسان على أنها اسم بثقة عالية. على سبيل المثال، إذا تم العثور على سلسلة تتكون من اسم معين ويتبعها اسم عائلة، في هذه المرحلة يتم وضع تطابق بثقة عالية. وهي تستخدم ثلاثة موارد أساسية:

-   قاموس بأسماء معينة.
-   قاموس أسماء العائلة.
-   أنماط كيفية تشكيل الأسماء.

تختلف الموارد الثلاثة لكل بلد.  ستشغل السلاسل *أوليفيا ولسون* تطابقا. يتم منح أسماء العائلة/الأسماء الشائعة ثقة أعلى من الأسماء النادرة. ومع ذلك، يسمح النمط أيضا بتطابقات جزئية. إذا تم العثور على اسم معين من القاموس متبوع باسم عائلة غير في القاموس، يتم تشغيل تطابق جزئي. على سبيل المثال *، قد يؤدي توماس باريشاد* إلى تشغيل تطابق جزئي. يتم منح تطابقات جزئية ثقة أقل.

بالإضافة إلى ذلك، فإن الأنماط التي قد يراها الإنسان كتكاتف للأسماء تتطابق أيضا مع الثقة المناسبة. مثل *س. ولسون*، *أوب. ولسون*، د *. س. ب. ولسون**، ع.ب.* أو *T. ريشنا، ي.* سيكون تطابقا.

### <a name="supported-languages"></a>اللغات المعتمدة

- الإنكليزية
- البلغارية
- الصينية
- الكرواتية
- التشيكية
- الدانماركية
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
- النرويجية ‏
- البولندية
- البرتغالية
- الرومانية
- السلوفاكية
- السلوفينية
- الإسبانية
- السويدية
- التركية


## <a name="all-medical-terms-and-conditions"></a>كل الشروط والأحكام الطبية

جميع الشروط والأحكام الطبية عبارة عن كيان مسمى مجمع يكشف عن الشروط الطبية والأحكام الطبية. يكشف عن المصطلحات الإنجليزية فقط. استخدم SIT هذا للكشف عن جميع تطابقات الشروط والأحكام الطبية المحتملة.

### <a name="format"></a>تنسيق

القاموس

### <a name="pattern"></a>النمط

القاموس

### <a name="checksum"></a>الاختبارات

لا

### <a name="description"></a>الوصف

يتطابق هذا الكيان المسمى المجمع مع النص الذي يذكر الحالات الطبية الموجودة في القواميس التي تم تجميعها. يوجد قاموس واحد منتدي لكل لغة معتمدة. القواميس من العديد من الموارد الطبية الدولية. تتضمن القواميس أكبر عدد ممكن من الحالات الطبية دون المخاطرة بعدد كبير من الإيجابيات الخاطئة. يحتوي كل إدخال على نماذج مختلفة تكتب فيها عادة شرط واحد لضمان تغطية، على سبيل المثال:

- *TB*
- <bpt id="p1">*</bpt>tuberculosis<ept id="p1">*</ept>
- *phthisis phthisis.*

### <a name="contains"></a>يحتوي على

يحتوي هذا الكيان المسمى المجمع SIT على كيانات SITs الفردية هذه.

- شروط اختبار الدم 
- أنواع الأدوية
- مواد داء
- أسماء الأدوية العامة
- الإعاقة المدرجة في تقييم الإعاقة في الولايات المتحدة ضمن الضمان الاجتماعي
- شروط الاختبار المعملي
- أنماط الحياة المتعلقة بالشروط الطبية
- التخصصات الطبية
- الإجراءات المهينة
- أسماء الأدوية ذات العلامة التجارية


## <a name="all-physical-addresses"></a>كل العناوين الفعلية

كل العناوين الفعلية هي وحدة SIT مجمعة، تكتشف الأنماط ذات الصلة والعناوين الفعلية من كل البلدان/المناطق المعتمدة.

### <a name="format"></a>تنسيق

متنوعة

### <a name="pattern"></a>النمط

متنوعة

### <a name="checksum"></a>الاختبارات

لا

### <a name="description"></a>الوصف

تم تصميم مطابقة عناوين الشارع بحيث تتطابق مع السلاسل التي يمكن أن يحددها الإنسان كعناوين الشارع. للقيام بذلك، يستخدم موارد أساسية متعددة:

-   قاموس للتسويات والمقاطعات والمناطق.
-   قاموس لاحقات الشارع، مثل الطريق أو الشارع أو شارع.
-   أنماط الرموز البريدية.
-   أنماط تنسيقات العنوان.

تختلف الموارد لكل بلد. الموارد الأساسية هي أنماط تنسيقات العنوان المستخدمة في بلد معين. يتم اختيار تنسيقات مختلفة للتأكد من تطابق أكبر عدد ممكن من العناوين. تسمح هذه التنسيقات بالمرونة، على سبيل المثال، قد يحذف العنوان الرمز البريدي أو يحذف اسم مدينة أو أن يكون له شارع بدون لاحقة شارع. في جميع الحالات، يتم استخدام مثل هذه المطابقات لزيادة ثقة المطابقة.

تم تصميم الأنماط بحيث تتطابق مع العناوين الفردية، وليس المواقع العامة. وبالتالي لن تتم مطابقة *سلاسل مثل Redmond أو WA 98052* أو *Main Street أو Albuquerque* .

### <a name="contains"></a>يحتوي على

يحتوي هذا الكيان المسمى المجمع SIT على كيانات SITs الفردية هذه:

- العناوين الفعلية في أستراليا
- عناوين النمسا الفعلية
- العناوين الفعلية في بلجيكا
- العناوين الفعلية للبرازيل
- العناوين الفعلية لبلغاريا
- العناوين الفعلية في كندا
- العناوين الفعلية لكرواتيا
- العناوين الفعلية لقبرص
- العناوين الفعلية جمهورية التشيك
- العناوين الفعلية في الدانمرك
- العناوين الفعلية لإستونيا
- العناوين الفعلية لفنلندا
- عناوين فرنسا الفعلية
- عناوين ألمانيا الفعلية
- العناوين الفعلية في اليونان
- العناوين الفعلية للمجر
- العناوين الفعلية في آيسلندا
- عناوين أيرلندا الفعلية
- عناوين إيطاليا الفعلية
- العناوين الفعلية في لاتفيا
- عناوين ليشتنشتاين الفعلية
- العناوين الفعلية في ليتوانيا
- العناوين الفعلية في لكسمبورغ
- العناوين الفعلية المالطية
- العناوين الفعلية لهولندا
- العناوين الفعلية في نيوزيلندا
- العناوين الفعلية في النرويج
- العناوين الفعلية في بولندا
- العناوين الفعلية للبرتغال
- العناوين الفعلية لرومانيا
- العناوين الفعلية في سلوفاكيا
- العناوين الفعلية لسلوفينيا
- العناوين الفعلية لإسبانيا
- العناوين الفعلية في السويد
- العناوين الفعلية في سويسرا
- عناوين تركيا الفعلية
- العناوين الفعلية للمملكة المتحدة
- العناوين الفعلية للولايات المتحدة

### <a name="supported-languages"></a>اللغات المعتمدة

- الإنكليزية
- البلغارية
- الصينية
- الكرواتية
- التشيكية
- الدانماركية
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
- النرويجية ‏
- البولندية
- البرتغالية
- الرومانية
- السلوفاكية
- السلوفينية
- الإسبانية
- السويدية
- التركية


## <a name="argentina-national-identity-dni-number"></a>رقم الهوية الوطنية (DNI) في الأرجنتين

### <a name="format"></a>تنسيق

ثمانية أرقام بفترات زمنية أو بدونها

### <a name="pattern"></a>النمط

ثمانية أرقام:
- رقمان
- فترة اختيارية
- ثلاثة أرقام
- فترة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_argentina_national_id العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_argentina_national_id كلمة أساسية.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- رقم الهوية الوطنية في الأرجنتين
- cedula
- cédula
- dni
- documento nacional de identidad
- documento número
- documento numero
- o nacional de las personas
- rnp


## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>مفتاح التعريف الضريبي الفريد في الأرجنتين (CUIT/CUIL)

### <a name="format"></a>تنسيق

11 رقما مع شرطة

### <a name="pattern"></a>النمط

11 رقما مع شرطة:
- رقمان في 20 أو 23 أو 24 أو 27 أو 30 أو 33 أو 34
- الفوسمة (-)
- ثمانية أرقام
- الفوسمة (-)
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_Argentina_Unique_Tax_Key` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_Argentina_Unique_Tax_Key` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_Argentina_Unique_Tax_Key` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- رمز فريد لتحديد هوية العاملين 
- Clave Única de Identificación Tributaria
- رمز تعريف فريد للميزات المهينة
- CUIL
- مفتاح تعريف ضريبي فريد
- مفتاح تعريف فريد لمهى العمل
- مفتاح فريد لتحديد هوية العاملين
- رمز تعريف عمل فريد
- التعليمات البرمجية الفريدة لتحديد هوية العمل
- مفتاح تعريف عمل فريد
- المفتاح الفريد لتحديد هوية العمل
- رمز تعريف الضريبة الفريد
- المفتاح الفريد لتحديد الضريبة
- رمز تعريف العمل الفريد
- التعليمات البرمجية الفريدة لتحديد هوية العمل
- مفتاح تعريف فريد للعمل
- مفتاح فريد لتحديد هوية العمل
- المايود الضريبي
- taxID #
- taxId
- number
- رقم الضريبة
- لا للضريبة
- الضريبة #
- الضريبة #
- "الممول"
- رقم الممول
- الممول لا
- الممول #
- الممول #
- الهوية الضريبية
- تعريف الضريبة
- Número de Identificación Fiscal
- número de contribuyente


## <a name="australia-bank-account-number"></a>رقم الحساب البنكي في أستراليا

### <a name="format"></a>تنسيق

ستة إلى 10 أرقام مع رقم فرع ولاية بنكية أو بدونه

### <a name="pattern"></a>النمط

رقم الحساب من 6 إلى 10 أرقام.

رقم فرع ولاية أستراليا البنكية:
- ثلاثة أرقام
- الواهة
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_australia_bank_account_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_australia_bank_account_number كلمة أساسية.
- يعثر التعبير Regex_australia_bank_account_number_bsb العادي على المحتوى الذي يتطابق مع النمط.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_australia_bank_account_number العادي على المحتوى الذي يتطابق مع النمط.

- تم العثور على كلمة أساسية Keyword_australia_bank_account_number كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- رمز swift البنكي
- bank
- العملة الأساسية
- حساب الولايات المتحدة الأمريكية
- عنوان حامل
- عنوان بنكي
- حساب المعلومات
- تحويلات الأموال
- الرسوم المصرفية
- تفاصيل البنك
- المعلومات المصرفية
- الأسماء الكاملة
- إلى


## <a name="australia-business-number"></a>رقم الأعمال في أستراليا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:

- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

11 رقما بمواد اختيارية

### <a name="pattern"></a>النمط

11 رقما بمواد اختيارية:

- رقمان
- وفاتمة اختيارية أو مسافة اختيارية
- ثلاثة أرقام
- وفاتمة اختيارية أو مسافة اختيارية
- ثلاثة أرقام
- وفاتمة اختيارية أو مسافة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_australian_business_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_australian_business_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_australian_business_number المحتوى الذي يتطابق مع النمط.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- australia business no
- رقم العمل
- abn #
- businessid #
- معرّف العمل
- abn
- businessno #


## <a name="australia-company-number"></a>رقم الشركة الأسترالية

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:

- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

تسعة أرقام مع مواريخ

### <a name="pattern"></a>النمط

تسعة أرقام مع المفهاة:

- ثلاثة أرقام
- مسافة
- ثلاثة أرقام
- مسافة
- ثلاثة أرقام


### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_Australian_Company_Number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Australian_Company_Number كلمة أساسية.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_Australian_Company_Number المحتوى الذي يتطابق مع النمط.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- يمكن
- australia company no
- australia company no #
- رقم الشركة في أستراليا
- لا للشركة الأسترالية
- لا للشركة الأسترالية #
- رقم الشركة الأسترالية


## <a name="australia-drivers-license-number"></a>رقم ترخيص القيادة في أستراليا

### <a name="format"></a>تنسيق

تسعة أحرف ورقم

### <a name="pattern"></a>النمط

تسعة أحرف ورقمية:

- رقمان أو حرفان (لا يتحسس حالة الأحرف)
- رقمان
- خمسة أرقام أو أحرف (لا تتحسس حالة الأحرف)

OR

- حرف واحد إلى حرفين اختيارين (لا يتحسس حالة الأحرف)
- أربعة إلى تسعة أرقام

OR

- تسعة أرقام أو أحرف (لا تتحسس حالة الأحرف)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر Regex_australia_drivers_license_number العادي على محتوى يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_australia_drivers_license_number كلمة أساسية.
- لم يتم العثور على Keyword_australia_drivers_license_number_exclusions كلمة أساسية من هذه الكلمات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- تراخيص القيادة الدولية
- اتحاد السيارات الأسترالية
- رخصة القيادة الدولية
- DriverLicence
- DriverLicences
- برنامج التشغيل Lic
- ترخيص القيادة
- تراخيص القيادة
- DriversLic
- DriversLicence
- DriversLicences
- برامج التشغيل Lic
- برامج التشغيل Lics
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- برنامج التشغيل Lic
- Lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- Lic الخاص ب برنامج التشغيل
- Lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج التشغيل Lic
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- Lic الخاص ب برنامج التشغيل
- Lics الخاصة ب برنامج التشغيل
- ترخيص القيادة
- تراخيص القيادة
- DriverLic #
- DriverLics #
- DriverLicence #
- DriverLicences #
- برنامج التشغيل Lic #
- برنامج التشغيل Lics #
- ترخيص القيادة #
- تراخيص القيادة #
- DriversLic #
- DriversLics #
- DriversLicence #
- DriversLicences #
- برامج التشغيل Lic #
- برامج التشغيل Lics #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- برنامج التشغيل Lic #
- Lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- Lic الخاص ب برنامج التشغيل #
- Lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- برنامج التشغيل Lic #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- Lic الخاص ب برنامج التشغيل #
- Lics الخاصة ب برنامج التشغيل #
- ترخيص القيادة #
- تراخيص القيادة #

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- aaa
- DriverLicense
- DriverLicenses
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- DriversLicense
- DriversLicenses
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- SLicense الخاص ب برنامج التشغيل
- اطباق برنامج التشغيل
- ترخيص القيادة
- تراخيص القيادة
- DriverLicense #
- DriverLicenses #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- DriversLicense #
- DriversLicenses #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- SLicense الخاص ب برنامج التشغيل #
- اطباق برنامج التشغيل #
- ترخيص القيادة #
- تراخيص القيادة #


## <a name="australia-medical-account-number"></a>رقم الحساب الطبي في أستراليا

### <a name="format"></a>تنسيق

10-11 رقما

### <a name="pattern"></a>النمط

10-11 رقما:
- الرقم الأول في النطاق من 2 إلى 6
- الرقم التاسع هو خانة الاختيار
- الرقم العاشر هو رقم المشكلة
- الرقم 11 (اختياري) هو الرقم الفردي

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_australian_medical_account_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Australia_Medical_Account_Number كلمة أساسية.
- يتم تمرير الاختبارات.


```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- تفاصيل الحساب البنكي
- مدفوعات واهية
- حساب رهن
- دفعات بنكية
- فرع المعلومات
- قرض بطاقة الائتمان
- قسم الخدمات البشرية
- الخدمة المحلية
- فريسة


## <a name="australia-passport-number"></a>رقم جواز سفر أستراليا

### <a name="format"></a>تنسيق

ثمانية أحرف أو تسعة أحرف ألفا رقمية

### <a name="pattern"></a>النمط

- حرف واحد (N، E، D، F، A، C، U، X) متبوع بسبعة أرقام أو
- حرفان (PA و PB و PC و PD و PE و PF و PU و PW و PX و PZ) متبوعين بسبعة أرقام.

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_australia_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_australia_passport_number` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- يعثر التعبير `Regex_australia_passport_number` العادي على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر
- تفاصيل جواز السفر
- والمواطنة
- من أستراليا
- قسم الشرطة
- بطاقة الهوية الوطنية
- مستند السفر
- مرجع إصدار


## <a name="australia-physical-addresses"></a>العناوين الفعلية في أستراليا 

كيان مسمى غير مرتبط، يكشف عن أنماط ذات صلة بالمعالجة الفعلية من أستراليا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة
متوسط


## <a name="australia-tax-file-number"></a>رقم الملف الضريبي في أستراليا

### <a name="format"></a>تنسيق

من ثمانية إلى تسعة أرقام

### <a name="pattern"></a>النمط

عادة ما يتم تقديم المسافات بين ثمانية وتسعة أرقام على النحو التالي:
- ثلاثة أرقام
- مسافة اختيارية
- ثلاثة أرقام
- مسافة اختيارية
- رقمان إلى ثلاثة أرقام حيث الرقم الأخير هو خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_australian_tax_file_number المحتوى الذي يتطابق مع النمط.
- لم يتم العثور على Keyword_Australia_Tax_File_Number أو Keyword_number_exclusions كلمة أساسية.
- يتم تمرير الاختبارات.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- رقم الأعمال الأسترالي
- معدل الضريبة
- الرعاية الصحية
- رقم ملف المشاريع
- الخدمة المخضرة
- الضريبة المقتطاعة
- عائدات ضريبية فردية
- رقم ملف الضريبة
- tfn


## <a name="austria-drivers-license-number"></a>رقم ترخيص القيادة في النمسا

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- يعثر التعبير  `Regex_austria_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_austria_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver لا s_license_number

- fuhrerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern


## <a name="austria-identity-card"></a>بطاقة هوية النمسا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

مجموعة من 24 حرفا من الأحرف والأرقام والأحرف الخاصة

### <a name="pattern"></a>النمط

24 حرفا:

-  22 حرفا (لا تتحسس حالة الأحرف) أو أرقاما أو خطا مائلا مائلا للخلف أو شرط مائلة للأمام أو علامات زائد

- حرفان (لا يتحسسان حالة الأحرف) أو رقما أو خطا مائلا مائلا للخلف أو شرط مائلة للأمام أو علامات زائد أو علامات المساواة

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- يعثر التعبير  `Regex_austria_eu_national_id_card` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_austria_eu_national_id_card` من.

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- رقم الهوية
- الم id الوطنية
- personalausweis republik österreich


## <a name="austria-passport-number"></a>رقم جواز سفر النمسا

### <a name="format"></a>تنسيق

حرف واحد متبوع بمساحة اختيارية وسبعة أرقام

### <a name="pattern"></a>النمط

تركيبة من حرف واحد، سبعة أرقام، ومساحة واحدة:

- حرف واحد (لا يتحسس حالة الحروف)
- مسافة واحدة (اختياري)
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_austria_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_austria_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_austria_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_austria_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_austria_eu_passport_number"></a>Keywords_austria_eu_passport_number

- reisepassnummer
- reisepasse
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="austria-physical-addresses"></a>عناوين النمسا الفعلية

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من النمسا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="austria-social-security-number"></a>رقم الضمان الاجتماعي في النمسا

### <a name="format"></a>تنسيق

10 أرقام في التنسيق المحدد

### <a name="pattern"></a>النمط

10 أرقام:

- ثلاثة أرقام تتطابق مع رقم تسلسلي
- رقم خانة واحدة
- ستة أرقام تتطابق مع تاريخ الميلاد (DDMMYY)

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_austria_eu_ssn_or_equivalent` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_austria_eu_ssn_or_equivalent` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_austria_eu_ssn_or_equivalent` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- ssn نمساوي
- رقم ehic
- ehic no
- رمز التأمين
- رمز التأمين #
- رقم التأمين
- رقم التأمين
- krankenkasennummer
- krankenversicherung
- socialsecurityno
- socialsecurityno #
- لا الضمان الاجتماعي
- رقم الضمان الاجتماعي
- رمز الضمان الاجتماعي
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- ssn #
- ssn
- versicherungscode
- versicherungsnummer
- zdravstveno zavarovanje


## <a name="austria-tax-identification-number"></a>رقم تعريف الضريبة في النمسا

### <a name="format"></a>تنسيق

تسعة أرقام ذات الوابل الاختياري والائلة المائلة للأمام

### <a name="pattern"></a>النمط

تسعة أرقام ذات الوابل الاختياري والائلة المائلة للأمام:

- رقمان
- الوابلة (اختيارية)
- ثلاثة أرقام
- الشرطة المائلة للأمام (اختيارية)
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_austria_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_austria_eu_tax_file_number` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر  `Func_austria_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- österreich
- st.nr.
- steuernummer
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- رقم الضريبة


## <a name="austria-value-added-tax"></a>ضريبة القيمة المضافة في النمسا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

نمط alphanumeric من 11 حرفا

### <a name="pattern"></a>النمط

النمط alphanumeric من 11 حرفا:

- أ أو
- T أو t
- مسافة اختيارية
- U أو u
- مسافة اختيارية
- رقمان أو ثلاثة أرقام
- مسافة اختيارية
- أربعة أرقام
- مسافة اختيارية
- رقم أو رقمين

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_Austria_Value_Added_Tax على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Austria_Value_Added_Tax كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_Austria_Value_Added_Tax على المحتوى الذي يتطابق مع النمط.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة #
- رقم ضريبة القيمة المضافة في النمسا
- لا لضريبة القيمة المضافة.
- vatno #
- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة (vat) في النمسا
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- رقم تعريف ضريبة القيمة المضافة
- رقم atu
- رقم uid


## <a name="azure-documentdb-auth-key"></a>مفتاح توثيق Azure DocumentDB

### <a name="format"></a>تنسيق

السلسلة "DocumentDb" متبوعه بالحروف السلاسل الموضحة في النمط أدناه.

### <a name="pattern"></a>النمط

- السلسلة "DocumentDb"
- أي تركيبة بين 3-200 أحرف صغيرة أو كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- رمز أكبر من (>) أو علامة المساواة (=) أو علامة اقتباس (") أو علامة اقتباس (')
- أي تركيبة من 86 حرفا أو رقما أو خطا مائلا للأمام (/) أو علامة الجمع (+)
- علامة المساواة (=)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير العادي CEP_Regex_AzureDocumentDBAuthKey على المحتوى الذي يتطابق مع النمط.
- لا يعثر CEP_CommonExampleKeywords العادي على محتوى يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(تقنيا، يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- contoso
- fabrikam
- northwind
- الحماية
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>سلسلة اتصال قاعدة بيانات Azure IAAS وسلسلة SQL Azure

### <a name="format"></a>تنسيق

السلسلة "Server" أو "server" أو "مصدر البيانات" متبوعا بالحروف السلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة "cloudapp.azure.<!--no-hyperlink-->com" أو "cloudapp.azure.<!--no-hyperlink-->net" أو "database.windows.<!--no-hyperlink-->net"، والسلسلة "كلمة المرور" أو "كلمة المرور" أو "pwd".

### <a name="pattern"></a>النمط

- السلسلة "Server" أو "server" أو "data source"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة تتراوح بين 1-200 حرف أو أحرف كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "cloudapp.azure.<!--no-hyperlink-->com", "cloudapp.azure.<!--no-hyperlink-->net"، أو "database.windows.<!--no-hyperlink-->net"
- أي تركيبة تتراوح بين 1-300 حرف أو أحرف صغيرة أو كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "كلمة المرور" أو "كلمة المرور" أو "pwd"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- حرف واحد أو أكثر ليس بعلامة منقوصة (;) أو علامة اقتباس (") أو علامة اقتباس (')
- فقامت بعلامة ;) أو علامة اقتباس (") أو علامة اقتباس (')

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير CEP_Regex_AzureConnectionString العادي على المحتوى الذي يتطابق مع النمط.
- لا يعثر CEP_CommonExampleKeywords العادي على محتوى يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(تقنيا، يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- contoso
- fabrikam
- northwind
- الحماية
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-iot-connection-string"></a>سلسلة اتصال Azure IoT

### <a name="format"></a>تنسيق

السلسلة "HostName" متبوعا بالحروف السلاسل الموضحة في النمط أدناه، بما في ذلك السلاسل "azure-devices.<!--no-hyperlink-->net" و"SharedAccessKey".

### <a name="pattern"></a>النمط

- السلسلة "HostName"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة تتراوح بين 1-200 حرف أو أحرف كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "azure-devices.<!--no-hyperlink-->net"
- أي تركيبة تتراوح بين 1-200 حرف أو أحرف كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "SharedAccessKey"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة من 43 حرفا أو حرفا أو رقما أو الشرطة المائلة للأمام (/) أو علامة الجمع (+)
- علامة المساواة (=)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير CEP_Regex_AzureIoTConnectionString العادي على المحتوى الذي يتطابق مع النمط.
- لا يعثر CEP_CommonExampleKeywords العادي على محتوى يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- contoso
- fabrikam
- northwind
- الحماية
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-publish-setting-password"></a>كلمة مرور إعداد نشر Azure

### <a name="format"></a>تنسيق

السلسلة "userpwd=" متبوع بسلسلة alphanumeric.

### <a name="pattern"></a>النمط

- السلسلة "userpwd="
- أي تركيبة من 60 حرفا أو رقما
- علامة اقتباس (")

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير CEP_Regex_AzurePublishSettingPasswords العادي على المحتوى الذي يتطابق مع النمط.
- لا يعثر CEP_CommonExampleKeywords العادي على محتوى يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- contoso
- fabrikam
- northwind
- الحماية
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-redis-cache-connection-string"></a>سلسلة اتصال ذاكرة التخزين المؤقت ل Azure Redis

### <a name="format"></a>تنسيق

السلسلة "redis.cache.windows.<!--no-hyperlink-->net" متبوع بالحروف السلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة "كلمة المرور" أو "pwd".

### <a name="pattern"></a>النمط

- السلسلة "redis.cache.windows.<!--no-hyperlink-->net"
- أي تركيبة تتراوح بين 1-200 حرف أو أحرف كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "كلمة المرور" أو "pwd"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة من 43 حرفا ذات أحرف صغيرة أو كبيرة أو أرقام أو الشرطة المائلة للأمام (/) أو علامة الجمع (+)
- علامة المساواة (=)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير CEP_Regex_AzureRedisCacheConnectionString العادي على المحتوى الذي يتطابق مع النمط.
- لا يعثر CEP_CommonExampleKeywords العادي على محتوى يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(تقنيا، يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- contoso
- fabrikam
- northwind
- الحماية
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>تنسيق

السلسلة "sig" متبوعه بالحروف السلاسل الموضحة في النمط أدناه.

### <a name="pattern"></a>النمط

- السلسلة "sig"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة تتراوح بين 43-53 حرفا ذات أحرف صغيرة أو كبيرة أو أرقام أو علامة النسبة المئوية (٪)
- السلسلة "٪3d"
- أي حرف ليس حرفا أحرفا صغيرة أو أحرفا صغيرة أو رقما أو علامة النسبة المئوية (٪)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير CEP_Regex_AzureSAS العادي على المحتوى الذي يتطابق مع النمط.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>سلسلة اتصال بحافلة خدمة Azure

### <a name="format"></a>تنسيق

السلسلة "EndPoint" متبوعه بالحروف السلاسل الموضحة في النمط أدناه، بما في ذلك السلاسل "servicebus.windows.<!--no-hyperlink-->net" و"SharedAccesKey".

### <a name="pattern"></a>النمط

- السلسلة "EndPoint"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة تتراوح بين 1-200 حرف أو أحرف كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "servicebus.windows.<!--no-hyperlink-->net"
- أي تركيبة تتراوح بين 1-200 حرف أو أحرف كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "SharedAccessKey"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة من 43 حرفا ذات أحرف صغيرة أو كبيرة أو أرقام أو الشرطة المائلة للأمام (/) أو علامة الجمع (+)
- علامة المساواة (=)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير CEP_Regex_AzureServiceBusConnectionString العادي على المحتوى الذي يتطابق مع النمط.
- لا يعثر CEP_CommonExampleKeywords العادي على محتوى يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(تقنيا، يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- contoso
- fabrikam
- northwind
- الحماية
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-storage-account-key"></a>مفتاح حساب تخزين Azure

### <a name="format"></a>تنسيق

السلسلة "DefaultEndpointsProtocol" متبوع بالحروف السلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة "AccountKey".

### <a name="pattern"></a>النمط

- السلسلة "DefaultEndpointsProtocol"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة تتراوح بين 1-200 حرف أو أحرف كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "AccountKey"
- من صفر إلى حرفين من مساحة بيضاء
- علامة المساواة (=)
- من صفر إلى حرفين من مساحة بيضاء
- أي تركيبة من 86 حرفا ذات أحرف صغيرة أو كبيرة أو أرقام أو الشرطة المائلة للأمام (/) أو علامة الجمع (+)
- علامة المساواة (=)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير العادي CEP_Regex_AzureStorageAccountKey على المحتوى الذي يتطابق مع النمط.
- لا تعثر CEP_AzureEmulatorStorageAccountFilter العادية على محتوى يتطابق مع النمط.
- لا يعثر CEP_CommonExampleKeywords العادي على محتوى يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

(تقنيا، يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- Eby8vdM02xNOcqFlqUWJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(تقنيا، يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.)

- contoso
- fabrikam
- northwind
- الحماية
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-storage-account-key-generic"></a>مفتاح حساب Azure Storage (generic)

### <a name="format"></a>تنسيق

أي تركيبة من 86 حرفا أو رقما أو أحرفا صغيرة أو كبيرة أو الشرطة المائلة للأمام (/) أو علامة الجمع (+) تسبق الأحرف الموضحة في النمط أدناه أو تليها.

### <a name="pattern"></a>النمط

- صفر إلى أحد الرموز الأكبر من (>) أو علامة اقتباس (') أو علامة المساواة (=) أو علامة الاقتباس (") أو علامة الرقم (#)
- أي تركيبة من 86 حرفا ذات أحرف صغيرة أو كبيرة أو أرقام أو الشرطة المائلة للأمام (/) أو علامة الجمع (+)
- علامة المساواة (=)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير CEP_Regex_AzureStorageAccountKeyGeneric العادي على المحتوى الذي يتطابق مع النمط.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```


## <a name="belgium-drivers-license-number"></a>رقم ترخيص القيادة في بلجيكا

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

10 أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_belgium_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_belgium_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver لا s_license_number

- rijbewijs
- rijbewijsnummer
- führerschein
- führerscheinnummer
- füehrerscheinnummer
- fuhrerschein
- fuehrerschein
- fuhrerscheinnummer
- fuehrerscheinnummer
- permis de conduire
- numéro permis conduire


## <a name="belgium-national-number"></a>الرقم الوطني لبلجيكا

### <a name="format"></a>تنسيق

11 رقما بالإضافة إلى المواريخ الاختيارية

### <a name="pattern"></a>النمط

11 رقما بالإضافة إلى المواريخ:
- ستة أرقام وفترتين اختيارتين بتنسيق YY. MM.DD بتاريخ الميلاد
- أحد المواقع الاختيارية من نقطة أو شرطة أو مسافة
- ثلاثة أرقام تسلسلية (فردية للذكور، حتى لأنثى)
- أحد المواقع الاختيارية من نقطة أو شرطة أو مسافة
- رقمان للتحقق

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_belgium_national_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_belgium_national_number كلمة أساسية.
- يتم تمرير الاختبارات.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_belgium_national_number المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- تكبل aantal
- bnn #
- bnn
- carte d'identité
- identifiant national
- identifiantnational #
- identificatie
- تعريف
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- الهوية
- كتابة
- الرقم الوطني
- السجل الوطني
- nationalnumber #
- nationalnumber
- nif #
- nif
- numéro d'assuré
- numéro de registre national
- numéro de sécurité
- numéro d'identification
- numéro d'immatriculation
- numéro national
- numéronational #
- رقم الم id الشخصي
- personalausweis
- personalidnumber #
- registratie
- التسجيل
- registrationsnumme
- riierung
- رقم الضمان الاجتماعي
- ssn #
- ssn
- steuernummer
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="belgium-passport-number"></a>رقم جواز سفر بلجيكا

### <a name="format"></a>تنسيق

حرفان متبوعان بستة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرفان متبوعان بستة أرقام

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

 إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_belgium_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_belgium_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date2` على التاريخ بتنسيق DD MM YY أو كلمة أساسية من `Keywords_eu_passport_date` أو `Keywords_belgium_eu_passport_number` يتم العثور عليه

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_belgium_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_belgium_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- منفذ مرور numéro
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- كارت النقل العام لتمرير المرور
- Passeport livre
- Pass-Nr
- Passnummer
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="belgium-physical-addresses"></a>العناوين الفعلية في بلجيكا

يكشف هذا الكيان المسمى الذي لم يتم تكتم صلته عن الأنماط المرتبطة والعناوين الفعلية من بلجيكا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="belgium-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في بلجيكا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 12 حرفا

### <a name="pattern"></a>النمط

النمط alphanumeric من 12 حرفا:

- حرف B أو b
- حرف E أو e
- رقم 0
- رقم من 1 إلى 9
- نقطة اختيارية أو وفاتة أو مسافة
- أربعة أرقام
- نقطة اختيارية أو وفاتة أو مسافة
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_belgium_value_added_tax_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_belgium_value_added_tax_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_belgium_value_added_tax_number على المحتوى الذي يتطابق مع النمط.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- رقم ضريبة القيمة المضافة
- لا لضريبة القيمة المضافة
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- btw
- btw #
- ضريبة القيمة المضافة #


## <a name="blood-test-terms"></a>شروط اختبار الدم

يكشف هذا الكيان المسمى الذي لم يتم حله عن المصطلحات ذات الصلة باختبارات الدم، مثل *hCG*. فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال

## <a name="brand-medication-names"></a>أسماء الأدوية ذات العلامة التجارية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن أسماء الأدوية التي تحمل علامة تجارية، مثل *Tylenol*. فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال


## <a name="brazil-cpf-number"></a>رقم CPF في البرازيل

### <a name="format"></a>تنسيق

11 رقما تتضمن خانة اختيار ويمكن تنسيقها أو إلغاء تنسيقها

### <a name="pattern"></a>النمط

تم التنسيق:
- ثلاثة أرقام
- فترة
- ثلاثة أرقام
- فترة
- ثلاثة أرقام
- الواهة
- رقمان خانتان

غير مهيى:
- 11 رقما حيث الرقمان الأخيران خانات رقمية

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_brazil_cpf المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_brazil_cpf كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_brazil_cpf المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- تحديد الهوية
- التسجيل
- الإيرادات
- Cadastro de Pessoas Físicas
- Imposto
- Identificação
- Inscrição
- Receita


## <a name="brazil-legal-entity-number-cnpj"></a>رقم كيان قانوني في البرازيل (CNPJ)

### <a name="format"></a>تنسيق

14 رقما تتضمن رقم التسجيل ورقم الفرع والأرقام التي تم فحصها، بالإضافة إلى خانات الاختيار

### <a name="pattern"></a>النمط

14 رقما، بالإضافة إلى المواريخ:

- رقمان
- فترة
- ثلاثة أرقام
- فترة
- ثلاثة أرقام (أول ثمانية أرقام هي رقم التسجيل)
- الشرطة المائلة للأمام
- رقم الفرع المكون من أربعة أرقام
- الواهة
- رقمان خانتان

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_brazil_cnpj الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_brazil_cnpj كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_brazil_cnpj الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- السجل الوطني للكيانات القانونية
- سجل الممولين
- كيان قانوني
- الكيانات القانونية
- حالة التسجيل
- Business
- الشركة
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- Cadastro Geral de Contribuintes
- CGC
- بيزووا جوريكا
- Pessoas jurídicas
- Situação cadastral
- Inscrição
- Empresa


## <a name="brazil-national-identification-card-rg"></a>بطاقة تعريف البرازيل الوطنية (RG)

### <a name="format"></a>تنسيق

سجل باريال (تنسيق قديم): تسعة أرقام

Digito de Identidade (RIC) (تنسيق جديد): 11 رقما

### <a name="pattern"></a>النمط

باكو باريال (تنسيق قديم):
- رقمان
- فترة
- ثلاثة أرقام
- فترة
- ثلاثة أرقام
- الواهة
- رقم واحد خانة الاختيار

وسجلو de Identidade (RIC) (تنسيق جديد):
- 10 أرقام
- الواهة
- رقم واحد خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_brazil_rg الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_brazil_rg كلمة أساسية.
- يتم تمرير الاختبارات.


```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- بطاقة الهوية
- الم id الوطنية
- número de rregistro
- entidade
- دونو باريال
- RG (تتحسس هذه الكلمة الأساسية حالة التحسس)
- RIC (تتحسس هذه الكلمة الأساسية حالة التحسس)


## <a name="brazil-physical-addresses"></a>العناوين الفعلية للبرازيل

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من البرازيل. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط

## <a name="bulgaria-drivers-license-number"></a>رقم ترخيص القيادة في بلغاريا

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_bulgaria_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_bulgaria_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver لا s_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки


## <a name="bulgaria-passport-number"></a>رقم جواز سفر بلغاريا

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_bulgaria_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_bulgaria_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_bulgaria_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_bulgaria_eu_passport_number` تم العثور عليها.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- пасрорт No

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="bulgaria-physical-addresses"></a>العناوين الفعلية لبلغاريا

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من بلغاريا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط

## <a name="bulgaria-uniform-civil-number"></a>الرقم المدني الرسمي لبلغاريا
يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

10 أرقام بدون مسافات ومواريخ

- ستة أرقام تتطابق مع تاريخ الميلاد (YYMMDD)
- رقمان يتطابقان مع ترتيب الميلاد
- رقم واحد يتطابق مع الجنس: رقم رقمي للذكر ورقم فردي لأنثى
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_bulgaria_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_bulgaria_eu_national_id_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_bulgaria_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn #
- bnn
- bucn #
- bucn
- edinendanski nomer
- egn #
- egn
- رقم التعريف
- الم id الوطنية
- الرقم الوطني
- nationalnumber #
- nationalnumber
- الم id الشخصي
- شخصي لا
- الرقم الشخصي
- personalidnumber #
- رقم الضمان الاجتماعي
- ssn #
- ssn
- الم id مدني موحد
- رقم مدني موحد
- رقم مدني موحد
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- رقم فريد من نوع "المواطنة"
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- униформ الما بعد
- униформ граждански الما بعد
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #


## <a name="canada-bank-account-number"></a>رقم الحساب البنكي في كندا

### <a name="format"></a>تنسيق

7 أو 12 رقما

### <a name="pattern"></a>النمط

رقم الحساب البنكي في كندا هو 7 أو 12 رقما.

رقم النقل العام لحساب بنك كندا هو:
- خمسة أرقام
- الواهة
- OR المكون من ثلاثة أرقام
- صفر "0"
- ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير العادي Regex_canada_bank_account_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_canada_bank_account_number كلمة أساسية.
- يعثر Regex_canada_bank_account_transit_number العادي على محتوى يتطابق مع النمط.

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير العادي Regex_canada_bank_account_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_canada_bank_account_number كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- الشركات الموفرة في كندا
- وكالة الإيرادات في كندا
- المؤسسة المالية الكندية
- نموذج الإيداع المباشر
- كندا
- ممثل قانوني
- Notary public
- مفوض اليمين
- فائدة رعاية الطفل
- الرعاية الشاملة للأطفال
- الإفادة الضريبية للأطفال في كندا
- فائدة ضريبة الدخل
- ضريبة المبيعات التي تم فرضها
- رقم التأمين الاجتماعي
- استرداد ضريبة الدخل
- الإفادة الضريبية للأطفال
- مدفوعات المدفوعات
- رقم المؤسسة
- طلب الإيداع
- المعلومات المصرفية
- الإيداع المباشر


## <a name="canada-drivers-license-number"></a>رقم ترخيص القيادة في كندا

### <a name="format"></a>تنسيق

تختلف حسب المقاطعة

### <a name="pattern"></a>النمط

تغطي الأنماط المختلفة:
- ألبيرتا
- كولومبيا البريطانية
- مانيتوبا
- نيو برونزويك
- نيوفاوندلاند/لابرادور
- نوفا سكوشيا
- أونتاريو
- جزيرة برنس إدوارد
- كيبيك
- ساسكاتشوان

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعمل الدالة Func_[province_name]_drivers_license_number البحث عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_[province_name]_drivers_license_name.
- تم العثور على كلمة أساسية Keyword_canada_drivers_license كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- اختصار المقاطعة، على سبيل المثال AB
- اسم المقاطعة، على سبيل المثال ألبيرتا

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- DriverLicence
- DriverLicences
- برنامج التشغيل Lic
- برنامج التشغيل Lics
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص القيادة
- تراخيص القيادة
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- برامج التشغيل Lic
- برامج التشغيل Lics
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- برنامج التشغيل Lic
- Lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Lic الخاص ب برنامج التشغيل
- Lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج التشغيل Lic
- اطباق برنامج التشغيل
- SLicense الخاص ب برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- Lic الخاص ب برنامج التشغيل
- Lics الخاصة ب برنامج التشغيل
- ترخيص القيادة
- تراخيص القيادة
- ترخيص القيادة
- تراخيص القيادة
- Permis de Conduire
- الم id
- الم ids
- رقم بطاقة idcard
- أرقام بطاقات idcard
- idcard #
- بطاقة idcard #s
- بطاقة idcard
- بطاقات idcard
- idcard
- رقم التعريف
- أرقام التعريف
- تعريف #
- تعريف #s
- بطاقة التعريف
- بطاقات التعريف
- تعريف
- DL #
- DLS #
- CDL #
- CDLS #
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- DriverLicence #
- DriverLicences #
- برنامج التشغيل Lic #
- برنامج التشغيل Lics #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- DriversLicence #
- DriversLicences #
- برامج التشغيل Lic #
- برامج التشغيل Lics #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- برنامج التشغيل Lic #
- Lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- Lic الخاص ب برنامج التشغيل #
- Lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- برنامج التشغيل Lic #
- اطباق برنامج التشغيل #
- SLicense الخاص ب برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- Lic الخاص ب برنامج التشغيل #
- Lics الخاصة ب برنامج التشغيل #
- ترخيص القيادة #
- تراخيص القيادة #
- ترخيص القيادة #
- تراخيص القيادة #
- Permis de Conduire #
- الم id #
- الم ids #
- بطاقة idcard #
- بطاقات idcard #
- idcard #
- بطاقة التعريف #
- بطاقات التعريف #
- تعريف #


## <a name="canada-health-service-number"></a>رقم خدمة الصحة في كندا

### <a name="format"></a>تنسيق

 10 أرقام

### <a name="pattern"></a>النمط

10 أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- ويعثر التعبير Regex_canada_health_service_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_canada_health_service_number كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- رقم الصحة الشخصية
- معلومات المريض
- الخدمات الصحية
- خدمات التخصص
- حادث سيارة
- مستشفى المريض
- psychiatrist
- تعويض العاملين
- الإعاقة


## <a name="canada-passport-number"></a>رقم جواز سفر كندا

### <a name="format"></a>تنسيق

حرفان كبيرة متبوعان بستة أرقام

### <a name="pattern"></a>النمط

حرفان كبيرة متبوعان بستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_canada_passport_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة Keyword_canada_passport_number أو Keyword_passport كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- الكندية
- جواز السفر الكندي
- طلب جواز السفر
- صور جواز السفر
- مترجم معتمد
- الكنديون
- أوقات المعالجة
- تجديد التطبيق

#### <a name="keyword_passport"></a>Keyword_passport

- رقم جواز السفر
- رقم جواز السفر
- جواز السفر #
- جواز السفر #
- PassportID
- Passportno
- passportnumber
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


## <a name="canada-personal-health-identification-number-phin"></a>رقم تعريف الصحة الشخصية (PHIN) في كندا

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_canada_phin العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمتين Keyword_canada_phin أو Keyword_canada_provinces على الأقل.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- رقم التأمين الاجتماعي
- قانون المعلومات الصحية
- معلومات ضريبة الدخل
- صحة manitoba
- تسجيل الصحة
- عمليات الشراء بالوصفات الطبية
- الأهلية للإفادة
- الصحة الشخصية
- توكيل
- رقم التسجيل
- رقم الصحة الشخصية
- مرجع ممارس
- wellness professional
- مرجع المريض
- الصحة و الصحة

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- نوافوت
- كيبيك
- الأقاليم الشمالية الغربية
- أونتاريو
- كولومبيا البريطانية
- ألبيرتا
- ساسكاتشوان
- مانيتوبا
- يوكون
- نيوفاوندلاند ولابرادور
- نيو برونزويك
- نوفا سكوشيا
- جزيرة برنس إدوارد
- كندا


## <a name="canada-physical-addresses"></a>العناوين الفعلية في كندا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من كندا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="canada-social-insurance-number"></a>رقم التأمين الاجتماعي في كندا

### <a name="format"></a>تنسيق

تسعة أرقام مع الوافات أو المسافات الاختيارية

### <a name="pattern"></a>النمط

تم التنسيق:
- ثلاثة أرقام
- وفاتة أو مسافة
- ثلاثة أرقام
- وفاتة أو مسافة
- ثلاثة أرقام

غير مهيّز: تسعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_canadian_sin الدالة على المحتوى الذي يتطابق مع النمط.
- نمطان على الأقل من النمطين التاليين:
    - تم العثور على كلمة أساسية من Keyword_sin.
    - تم العثور على كلمة أساسية Keyword_sin_collaborative كلمة أساسية.
    - تعثر Func_eu_date الدالة على تاريخ بتنسيق التاريخ المناسب.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_unformatted_canadian_sin المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_sin.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_sin"></a>Keyword_sin

- خطيئة
- التأمين الاجتماعي
- numero d'assurance sociale
- الخطايا
- ssn
- ssns
- الضمان الاجتماعي
- numero d'assurance social
- رقم التعريف الوطني
- الم id الوطنية
- خطيئة #
- soc ins
- ins الاجتماعية

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- ترخيص برنامج التشغيل
- ترخيص برامج التشغيل
- رخصة القيادة
- ترخيص برامج التشغيل
- DOB
- تاريخ الميلاد
- تاريخ الميلاد
- تاريخ الميلاد


## <a name="chile-identity-card-number"></a>رقم بطاقة هوية تشيلي

### <a name="format"></a>تنسيق

من سبعة إلى ثمانية أرقام بالإضافة إلى خانة الاختيار أو الحرف

### <a name="pattern"></a>النمط

من سبعة إلى ثمانية أرقام بالإضافة إلى المواريخ:
- رقم واحد إلى رقمين
- فترة اختيارية
- ثلاثة أرقام
- فترة اختيارية
- ثلاثة أرقام
- شرطة
- رقم واحد أو حرف (وليس حساسا للقضية) وهو رقم خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_chile_id_card على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_chile_id_card كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_chile_id_card على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- التعريف الوطني
- رقم التعريف الوطني
- الم id الوطنية
- número de identificación nacional
- rol único nacional
- rol único tributario
- RUN
- RUT
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- RUN #
- RUT #
- nationaluniqueroleID #
- identidad nacional
- número identificación
- identidad número
- numero identificacion
- identidad numero
- الهوية التشيلية لا.
- رقم الهوية التشيلية
- الهوية التشيلية #
- سجل ضريبي فريد
- دور رافد فريد
- دور الضريبة الفريد
- رقم رافد فريد
- رقم قومي فريد
- الدور الوطني الفريد
- الدور الفريد الوطني
- تشيلي الهوية لا.
- رقم هوية تشيلي
- هوية تشيلي #
- R.U.T
- R.U.N


## <a name="china-resident-identity-card-prc-number"></a>رقم بطاقة الهوية المقيمة في الصين (PRC)

### <a name="format"></a>تنسيق

18 رقما

### <a name="pattern"></a>النمط

18 رقما:
- ستة أرقام هي رمز عنوان
- ثمانية أرقام في النموذج YYYYMMDD، وهي تاريخ الميلاد
- ثلاثة أرقام هي رمز طلب
- رقم واحد خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_china_resident_id على المحتوى الذي يتطابق مع النمط.
- تم العثور على Keyword_china_resident_id كلمة أساسية من Keyword_china_resident_id.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_china_resident_id على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- بطاقة هوية المقيم
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

من 14 إلى 19 رقما يمكن تنسيقها أو عدم تنسيقها (ddddddd) ويجب أن تجتاز اختبار Luhn.

### <a name="pattern"></a>النمط

الكشف عن البطاقات من جميع العلامات التجارية الرئيسية حول العالم، بما في ذلك Visa و MasterCard و Discover Card و JCB و American Express وبطاقات الهدايا وبطاقات diner و Rupay و China UnionPay.

### <a name="checksum"></a>الاختبارات

نعم، خانة الاختيار Luhn

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_credit_card المحتوى الذي يتطابق مع النمط.
- يكون أحد ما يلي صحيحا:
    - تم العثور على كلمة أساسية Keyword_cc_verification كلمة أساسية.
    - تم العثور على كلمة أساسية Keyword_cc_name كلمة أساسية.
    - تعثر Func_expiration_date الدالة على تاريخ بتنسيق التاريخ الصحيح.
- يتم تمرير الاختبارات.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_credit_card المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- التحقق من البطاقة
- رقم تعريف البطاقة
- cvn
- cid
- cvc2
- cvv2
- تثبيت الكتلة
- رمز الأمان
- رقم الأمان
- الأمان لا
- رقم المشكلة
- المشكلة لا
- cryptogramme
- numéro de sécurité
- numero de securite
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- prufziffer
- sicherheits Kode
- sicherheitscode
- sicherheitsnummer
- verfalldatum
- codice di verifica
- cod. sicurezza
- cod sicurezza
- n autorizzazione
- código
- codigo
- cod. seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- cod. seguranca
- cod. segurança
- cód. seguranca
- cód segurança
- cod seguranca
- cod segurança
- cód seguranca
- número de verificação
- numero de verificacao
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
- data de expiracao
- data em que expira
- validade
- valor
- vencimento
- معاملة
- رقم المعاملة
- رقم المرجع
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- amex
- american express
- americanexpress
- americano espresso
- Visa
- بطاقة رئيسية
- البطاقة الرئيسية
- mc
- بطاقات رئيسية
- البطاقات الرئيسية
- diner's Club
- نادي diners
- dinersclub
- اكتشاف
- بطاقة الاكتشاف
- بطاقة الاكتشاف
- اكتشاف البطاقات
- JCB
- BrandSmart
- مكتب البطاقات اليابانية
- carte blanche
- carteblanche
- بطاقة الائتمان
- نسخة #
- نسخة#:
- تاريخ انتهاء الصلاحية
- تاريخ exp
- تاريخ انتهاء الصلاحية
- تاريخ انتهاء الصلاحية
- تاريخ d'exp
- انتهاء صلاحية التاريخ
- بطاقة بنكية
- بطاقة بنكية
- رقم البطاقة
- بطاقة num
- cardnumber
- cardnumbers
- أرقام البطاقات
- بطاقة الائتمان
- بطاقات الائتمان
- بطاقات الائتمان
- ccn
- حامل البطاقة
- عنصر البطاقة
- حاملو البطاقات
- حاملو البطاقات
- بطاقة الاختيار
- بطاقة الاختيار
- التحقق من البطاقات
- بطاقات الاختيار
- بطاقة خصم
- بطاقة الخصم
- بطاقات الخصم
- بطاقات الخصم
- بطاقة atm
- atmcard
- بطاقات atm
- atmcards
- enroute
- en route
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
- لا.
- البطاقة لا
- رقم البطاقة
- carte bancaire
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nº de la carte
- nº de carte
- kreditkarte
- karte
- karteninhaber
- karteninhabers
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr
- kartennummer
- kreditkartennummer
- kreditkarten-nummer
- carta di credito
- carta credito
- n. كارتا
- n carta
- nr. كارتا
- nr carta
- numero carta
- numero della carta
- numero di carta
- tarjeta credito
- tarjeta de credito
- tarjeta crédito
- tarjeta de crédito
- tarjeta de atm
- tarjeta atm
- tarjeta debito
- tarjeta de debito
- tarjeta débito
- tarjeta de débito
- nº de tarjeta
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
- debito automatico
- número do cartão
- numero do cartão
- número do cartao
- numero do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nº do cartão
- nº do cartao
- nº. do cartão
- no do cartão
- no do cartao
- لا. do cartão
- لا. do cartao
- rupay
- دفع اتحادي
- unionpay
- diner's
- diners
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
- Visaカード
- Visa カード
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


## <a name="croatia-drivers-license-number"></a>رقم ترخيص القيادة في كرواتيا

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- يعثر التعبير  `Regex_croatia_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_croatia_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_croatia_eu_drivers_license_number"></a>Keywords_croatia_eu_driver لا s_license_number

- vozačka dozvola
- vozačke dozvole


## <a name="croatia-identity-card-number"></a>رقم بطاقة هوية كرواتيا
يتم تضمين هذا الكيان في نوع المعلومات الحساسة ل رقم التعريف الوطنية في الاتحاد الأوروبي. وهي متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>النمط

تسعة أرقام متتالية

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_croatia_id_card المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_croatia_id_card كلمة أساسية.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj graana
- رقم المهى الرئيسي
- nacionalni identifikacijski broj
- رقم التعريف الوطني
- oib #
- oib
- osobna iskaznica
- osobni id
- osobni identifikacijski broj
- رقم التعريف الشخصي
- porezni broj
- porezni identifikacijski broj
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="croatia-passport-number"></a>رقم جواز سفر كرواتيا

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_croatia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_croatia_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_croatia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_croatia_eu_passport_number` تم العثور عليها.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- br. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>رقم التعريف الشخصي (OIB) في كرواتيا

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>النمط

11 رقما:
- 10 أرقام
- الرقم النهائي هو خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_croatia_oib_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_croatia_eu_tax_file_number كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_croatia_oib_number المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstorski broj graana
- رقم المهى الرئيسي
- nacionalni identifikacijski broj
- رقم التعريف الوطني
- oib #
- oib
- osobna iskaznica
- osobni id
- osobni identifikacijski broj
- رقم التعريف الشخصي
- porezni broj
- porezni identifikacijski broj
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="croatia-physical-addresses"></a>العناوين الفعلية لكرواتيا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من كرواتيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="cyprus-drivers-license-number"></a>رقم ترخيص القيادة في قبرص

### <a name="format"></a>تنسيق

12 رقما بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

12 رقما

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_cyprus_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_cyprus_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver لا s_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης


## <a name="cyprus-identity-card"></a>بطاقة هوية قبرص

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

10 أرقام

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_cyprus_eu_national_id_card` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_cyprus_eu_national_id_card` من.

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- رقم بطاقة الم id
- رقم بطاقة الهوية
- kimlik karti
- رقم التعريف الوطني
- رقم الم id الشخصي
- ταυτοτητασ


## <a name="cyprus-passport-number"></a>رقم جواز السفر الخاص بقبرص

### <a name="format"></a>تنسيق

حرف واحد متبوع ب 6 إلى 8 أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرف واحد متبوع بستة إلى ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_cyprus_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_cyprus_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_cyprus_eu_passport_date` على التاريخ بتنسيق العثور على DD/MM/YYYY أو كلمة أساسية من `Keywords_cyprus_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_cyprus_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_cyprus_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- pasaportu
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- Pasaport Kimliوي
- pasaport nuasası
- Pasaport no.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- تنتهي الصلاحية في
- تم إصداره في


## <a name="cyprus-physical-addresses"></a>العناوين الفعلية لقبرص

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من قبرص. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط

## <a name="cyprus-tax-identification-number"></a>رقم التعريف الضريبي لقبرص
يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

ثمانية أرقام ورسالة واحدة في النمط المحدد

### <a name="pattern"></a>النمط

ثمانية أرقام ورسالة واحدة:

- "0" أو "9"
- سبعة أرقام
- حرف واحد (لا يتحسس حالة الحروف)

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_cyprus_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_cyprus_eu_tax_file_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_cyprus_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- الم id الضريبة
- رمز تعريف الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- tic #
- tic
- "معرف الصفيح"
- tin no
- صفيحة #
- vergi kimlik kodu
- vergi kimlik nuهاsı
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού


## <a name="czech-drivers-license-number"></a>رقم ترخيص القيادة التشيكية

### <a name="format"></a>تنسيق

حرفان متبوعان بستة أرقام

### <a name="pattern"></a>النمط

ثمانية أحرف ورقم:

- حرف 'E' (لا يتحسس حالة الحروف)
- رسالة
- مسافة (اختياري)
- ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_czech_republic_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_czech_republic_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver لا s_license_number

- تينكسكه prúkaz
- ، průkazy
- číslo íidičského průkazu
- čísla íidičskích průkazů


## <a name="czech-passport-number"></a>رقم جواز السفر التشيكي

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

ثمانية أرقام بدون مسافات أو مواريخ

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_czech_republic_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_czech_republic_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_czech_republic_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_czech_republic_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cestovní pas
- číslo pasu
- cestovní pasu
- passeport no
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="czech-personal-identity-number"></a>رقم الهوية الشخصية التشيكية

### <a name="format"></a>تنسيق

تسعة أرقام مع الشرطة المائلة للأمام الاختيارية (تنسيق قديم) 10 أرقام مع الشرطة المائلة للأمام الاختيارية (تنسيق جديد)

### <a name="pattern"></a>النمط

تسعة أرقام (تنسيق قديم):
- ستة أرقام تمثل تاريخ الميلاد
- الشرطة المائلة للأمام الاختيارية
- ثلاثة أرقام

10 أرقام (تنسيق جديد):
- ستة أرقام تمثل تاريخ الميلاد
- الشرطة المائلة للأمام الاختيارية
- أربعة أرقام حيث الرقم الأخير هو خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر Func_czech_id_card الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_czech_id_card كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر الدالة Func_czech_id_card_new_format المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- رقم الميلاد
- id جمهورية التشيك
- czechidno #
- daňové číslo
- identifikační číslo
- الهوية لا
- رقم الهوية
- identityno #
- identityno
- رقم التأمين
- رقم التعريف الوطني
- nationalnumber #
- الرقم الوطني
- osobní číslo
- personalidnumber #
- رقم الم id الشخصي
- رقم التعريف الشخصي
- الرقم الشخصي
- pid #
- pid
- pojištšní číslo
- rč
- cislo
- روني číslo
- ssn
- ssn #
- رقم الضمان الاجتماعي
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- رقم تعريف فريد


## <a name="czech-republic-physical-addresses"></a>العناوين الفعلية جمهورية التشيك

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من جمهورية التشيك. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط

## <a name="denmark-drivers-license-number"></a>رقم ترخيص القيادة في الدانمرك

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_denmark_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_denmark_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver لا s_license_number

- kørekort
- kørekortnummer


## <a name="denmark-passport-number"></a>رقم جواز سفر الدانمارك

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_denmark_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_denmark_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date2` على التاريخ بتنسيق العثور على DD MM YY أو كلمة أساسية `Keywords_eu_passport_date` من

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_denmark_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_denmark_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="denmark-personal-identification-number"></a>رقم التعريف الشخصي في الدانمرك

### <a name="format"></a>تنسيق

10 أرقام تحتوي على الفوسفات

### <a name="pattern"></a>النمط

10 أرقام:
- ستة أرقام بتنسيق DDMMYY، وهو تاريخ الميلاد
- مسافة اختيارية أو الوابلة الاختيارية
- أربعة أرقام حيث الرقم النهائي هو خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Func_denmark_eu_tax_file_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_denmark_id كلمة أساسية.
- يتم تمرير الاختبارات.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- يعثر التعبير Func_denmark_eu_tax_file_number العادي على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilt rieringssystem
- cpr
- cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- بطاقة صحية
- رقم بطاقة التأمين الصحي
- رقم التأمين الصحي
- رقم التعريف
- identifikationsnummer
- identifikationsnummer #
- رقم الهوية
- krankenkasennummer
- nationalid #
- nationalnumber #
- الرقم الوطني
- personalidnumber #
- personalidentityno #
- رقم الم id الشخصي
- personnummer
- personnummer #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- ssn
- ssn #
- skat id
- skat kode
- skat nummer
- skattenummer
- رقم الضمان الاجتماعي
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- رمز الضريبة
- بطاقة التأمين الصحي للسفر
- uniqueidentityno #
- رقم الضريبة
- رقم التسجيل الضريبي
- الم id الضريبة
- رقم تعريف الضريبة
- #
- taxnumber #
- لا للضريبة
- taxno #
- taxnumber
- تعريف الضريبة لا
- صفيحة #
- no #
- number #
- لا للضريبة #
- "معرف الصفيح"
- tin no
- cpr.nr
- cprnr
- cprnummer
- personnr
- personregister
- sygesikringsbevis
- sygesikringsbevisnr
- sygesikringsbevisnummer
- sygesikringskort
- sygesikringskortnr
- sygesikringskortnummer
- sygesikringsnr
- sygesikringsnummer


## <a name="denmark-physical-addresses"></a>العناوين الفعلية في الدانمرك

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من الدانمرك. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="diseases"></a>مواد داء

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن النص الذي يتطابق مع أسماء الداء، مثل *ا.* فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال


## <a name="drug-enforcement-agency-dea-number"></a>رقم وكالة مكافحة المخدرات (DEA)

### <a name="format"></a>تنسيق

حرفان متبوعان بسبعة أرقام

### <a name="pattern"></a>النمط

يجب أن يتضمن النمط كل ما يلي:
- حرف واحد (لا يتحسس حالة الأحرف) من مجموعة الأحرف المحتملة هذه: abcdefghjklmnprstux، وهو رمز مسجل
- حرف واحد (ليس حساسا للقضية)، وهو الحرف الأول من اسم العائلة أو الرقم '9' للمسجل
- سبعة أرقام، آخرها خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_dea_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من `Keyword_dea_number`
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_dea_number المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- dea
- dea #
- إدارة مكافحة المخدرات
- وكالة مكافحة المخدرات


## <a name="estonia-drivers-license-number"></a>رقم ترخيص القيادة الإستونية

### <a name="format"></a>تنسيق

حرفان متبوعان بستة أرقام

### <a name="pattern"></a>النمط

حرفان وستة أرقام:

- الأحرف "ET" (لا تتحسس حالة الأحرف)
- ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_estonia_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_estonia_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver لا s_license_number

- permis de conduire
- juhilubade numbrid
- رقم juhiloa
- juhiluba


## <a name="estonia-passport-number"></a>رقم جواز سفر إستونيا

### <a name="format"></a>تنسيق

حرف واحد متبوع بسبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرف واحد متبوع بسبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_estonia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_estonia_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_estonia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_estonia_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passinumbrid document number document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="estonia-personal-identification-code"></a>رمز التعريف الشخصي لإستونيا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

11 رقما بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

11 رقما:

- رقم واحد يتطابق مع الجنس و قرن الميلاد (رقم فردي ذكر، رقم أنثى؛ من 1 إلى 2: القرن التاسع عشر؛ 3-4: القرن العشرين؛ 5-6: القرن 21)
- ستة أرقام تتطابق مع تاريخ الميلاد (YYMMDD)
- ثلاثة أرقام تتطابق مع رقم تسلسلي يفصل بين الأشخاص الذين تم ولادتهم في التاريخ نفسه
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_estonia_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_estonia_eu_national_id_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_estonia_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- ik
- isikukood #
- isikukood
- maksu id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- رقم التعريف الوطني
- الرقم الوطني
- الرمز الشخصي
- رقم الم id الشخصي
- رمز التعريف الشخصي
- رقم التعريف الشخصي
- personalidnumber #
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="estonia-physical-addresses"></a>العناوين الفعلية لإستونيا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من إستونيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="eu-debit-card-number"></a>رقم بطاقة خصم الاتحاد الأوروبي

### <a name="format"></a>تنسيق

16 رقما

### <a name="pattern"></a>النمط

نمط معقد وقوي

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_eu_debit_card المحتوى الذي يتطابق مع النمط.
- يكون أحد ما يلي على الأقل صحيحا:
    - تم العثور على كلمة أساسية من Keyword_eu_debit_card.
    - تم العثور على كلمة أساسية Keyword_card_terms_dict كلمة أساسية.
    - تم العثور على كلمة أساسية Keyword_card_security_terms_dict كلمة أساسية.
    - تم العثور على كلمة أساسية Keyword_card_expiration_terms_dict كلمة أساسية.
    - تعثر Func_expiration_date الدالة على تاريخ بتنسيق التاريخ الصحيح.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- رقم الحساب
- رقم البطاقة
- لا.
- رقم الأمان
- نسخة #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr
- acct num
- acct no
- american express
- americanexpress
- americano espresso
- amex
- بطاقة atm
- بطاقات atm
- atm kaart
- atmcard
- atmcards
- atmkaart
- atmkaarten
- bancontact
- بطاقة بنكية
- bankkaart
- حامل البطاقة
- حاملو البطاقات
- بطاقة num
- رقم البطاقة
- أرقام البطاقات
- نوع البطاقة
- cardano numerico
- عنصر البطاقة
- حاملو البطاقات
- cardnumber
- cardnumbers
- carta bianca
- carta credito
- carta di credito
- cartao de credito
- cartao de crédito
- cartao de debito
- cartao de débito
- carte bancaire
- carte blanche
- carte bleue
- carte de credit
- carte de crédit
- carte di credito
- carteblanche
- cartão de credito
- cartão de crédito
- cartão de debito
- cartão de débito
- cb
- ccn
- بطاقة الاختيار
- التحقق من البطاقات
- بطاقة الاختيار
- بطاقات الاختيار
- art
- cirrus
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- بطاقة الائتمان
- بطاقات الائتمان
- بطاقة الائتمان
- بطاقات الائتمان
- debetkaart
- debetkaarten
- بطاقة خصم
- بطاقات الخصم
- بطاقة الخصم
- بطاقات الخصم
- debito automatico
- نادي diners
- dinersclub
- اكتشاف
- بطاقة الاكتشاف
- اكتشاف البطاقات
- بطاقة الاكتشاف
- بطاقات الاكتشاف
- débito automático
- edc
- eigentümername
- بطاقة خصم أوروبية
- hoofdkaart
- hoofdkaarten
- في viaggio
- مكتب البطاقات اليابانية
- japanse kaartdienst
- jcb
- kaart
- kaart num
- kaartaantal
- kaartaantallen
- kaarthouder
- kaarthouders
- karte
- karteninhaber
- karteninhabers
- kartennr
- kartennummer
- kreditkarte
- kreditkarten-nummer
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartennummer
- kreditkartentyp
- maestro
- البطاقة الرئيسية
- البطاقات الرئيسية
- بطاقة رئيسية
- بطاقات رئيسية
- mc
- mister cash
- n carta
- كارتا
- no de tarjeta
- no do cartao
- no do cartão
- لا. de tarjeta
- لا. do cartao
- لا. do cartão
- nr carta
- nr. كارتا
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
- nº carta
- nº de carte
- nº de la carte
- nº de tarjeta
- nº do cartao
- nº do cartão
- nº. do cartão
- número de cartao
- número de cartão
- número de tarjeta
- número do cartao
- scheda dell'assegno
- scheda dell'atmosfera
- scheda dell'atmosfera
- scheda della banca
- scheda di controllo
- scheda di debito
- scheda matrice
- schede dell'atmosfera
- schede di controllo
- schede di debito
- schede matrici
- scoprono la scheda
- scoprono le schede
- solo
- supporti di scheda
- supporto di scheda
- التبديل
- tarjeta atm
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
- visa plus
- فيزا إلكترون
- visto
- visum
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- رقم تعريف البطاقة
- التحقق من البطاقة
- cardi la verifica
- cid
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- cod. seg
- cod. seguranca
- cod. segurança
- cod. sicurezza
- codice di sicurezza
- codice di verifica
- codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- التشفير
- cryptogramme
- cv2
- cvc
- cvc2
- cvn
- cvv
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
- المشكلة لا
- رقم المشكلة
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- لا. dell'edizione
- لا. di sicurezza
- numero de securite
- numero de verificacao
- numero dell'edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero vanheidigheid
- numéro de sécurité
- nº autorizzazione
- número de verificação
- perno ilهمco
- تثبيت الكتلة
- prufziffer
- prüfziffer
- رمز الأمان
- الأمان لا
- رقم الأمان
- sicherheits kode
- sicherheitscode
- sicherheitsnummer
- speldblok
- r
- heidsaantal
- code
- heidsnummer
- verfalldatum

#### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

- ablauf
- data de expiracao
- data de expiração
- data del exp
- data di exp
- data di scadenza
- data em que expira
- scad البيانات
- بيانات scadenza
- date de validité
- datum afloop
- datum van exp
- de afloop
- espira
- espira
- تاريخ exp
- exp datum
- انتهاء الصلاحية
- تنتهي الصلاحية
- تنتهي الصلاحية
- انتهاء الصلاحية
- fecha de expiracion
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- valable
- validade
- valido hasta
- valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta


## <a name="eu-drivers-license-number"></a>رقم ترخيص القيادة في الاتحاد الأوروبي

توجد هذه الكيانات في "رقم ترخيص برنامج تشغيل الاتحاد الأوروبي" وهي أنواع معلومات حساسة.

- [النمسا](#austria-drivers-license-number)
- [بلجيكا](#belgium-drivers-license-number)
- [بلغاريا](#bulgaria-drivers-license-number)
- [كرواتيا](#croatia-drivers-license-number)
- [قبرص](#cyprus-drivers-license-number)
- [التشيكية](#czech-drivers-license-number)
- [الدانمارك](#denmark-drivers-license-number)
- [إستونيا](#estonia-drivers-license-number)
- [فنلندا](#finland-drivers-license-number)
- [فرنسا](#france-drivers-license-number)
- [ألمانيا](#germany-drivers-license-number)
- [اليونان](#greece-drivers-license-number)
- [المجر](#hungary-drivers-license-number)
- [أيرلندا](#ireland-drivers-license-number)
- [إيطاليا](#italy-drivers-license-number)
- [لاتفيا](#latvia-drivers-license-number)
- [لتوانيا](#lithuania-drivers-license-number)
- [Luxemburg](#luxemburg-drivers-license-number)
- [مالطا](#malta-drivers-license-number)
- [هولندا](#netherlands-drivers-license-number)
- [بولندا](#poland-drivers-license-number)
- [البرتغال](#portugal-drivers-license-number)
- [رومانيا](#romania-drivers-license-number)
- [سلوفاكيا](#slovakia-drivers-license-number)
- [سلوفينيا](#slovenia-drivers-license-number)
- [إسبانيا](#spain-drivers-license-number)
- [السويد](#sweden-drivers-license-number)
- [المملكة المتحدة](#uk-drivers-license-number)


## <a name="eu-national-identification-number"></a>رقم التعريف الوطني في الاتحاد الأوروبي

توجد هذه الكيانات في رقم التعريف الوطني للاتحاد الأوروبي وهي أنواع معلومات حساسة.

- [النمسا](#austria-identity-card)
- [بلجيكا](#belgium-national-number)
- [بلغاريا](#bulgaria-uniform-civil-number)
- [كرواتيا](#croatia-identity-card-number)
- [قبرص](#cyprus-identity-card)
- [التشيكية](#czech-personal-identity-number)
- [الدانمارك](#denmark-personal-identification-number)
- [إستونيا](#estonia-personal-identification-code)
- [فنلندا](#finland-national-id)
- [فرنسا](#france-national-id-card-cni)
- [ألمانيا](#germany-identity-card-number)
- [اليونان](#greece-national-id-card)
- [المجر](#hungary-personal-identification-number)
- [أيرلندا](#ireland-personal-public-service-pps-number)
- [إيطاليا](#italy-fiscal-code)
- [لاتفيا](#latvia-personal-code)
- [لتوانيا](#lithuania-personal-code)
- [Luxemburg](#luxemburg-national-identification-number-natural-persons)
- [مالطا](#malta-identity-card-number)
- [هولندا](#netherlands-citizens-service-bsn-number)
- [بولندا](#poland-national-id-pesel)
- [البرتغال](#portugal-citizen-card-number)
- [رومانيا](#romania-personal-numeric-code-cnp)
- [سلوفاكيا](#slovakia-personal-number)
- [سلوفينيا](#slovenia-unique-master-citizen-number)
- [إسبانيا](#spain-dni)
- [المملكة المتحدة](#uk-national-insurance-number-nino)


## <a name="eu-passport-number"></a>رقم جواز سفر الاتحاد الأوروبي

توجد هذه الكيانات في رقم جواز سفر الاتحاد الأوروبي وهي أنواع معلومات حساسة. توجد هذه الكيانات في مجموعة أرقام جواز سفر الاتحاد الأوروبي.

- [النمسا](#austria-passport-number)
- [بلجيكا](#belgium-passport-number)
- [بلغاريا](#bulgaria-passport-number)
- [كرواتيا](#croatia-passport-number)
- [قبرص](#cyprus-passport-number)
- [التشيكية](#czech-passport-number)
- [الدانمارك](#denmark-passport-number)
- [إستونيا](#estonia-passport-number)
- [فنلندا](#finland-passport-number)
- [فرنسا](#france-passport-number)
- [ألمانيا](#germany-passport-number)
- [اليونان](#greece-passport-number)
- [المجر](#hungary-passport-number)
- [أيرلندا](#ireland-passport-number)
- [إيطاليا](#italy-passport-number)
- [لاتفيا](#latvia-passport-number)
- [لتوانيا](#lithuania-passport-number)
- [Luxemburg](#luxemburg-passport-number)
- [مالطا](#malta-passport-number)
- [هولندا](#netherlands-passport-number)
- [بولندا](#poland-passport-number)
- [البرتغال](#portugal-passport-number)
- [رومانيا](#romania-passport-number)
- [سلوفاكيا](#slovakia-passport-number)
- [سلوفينيا](#slovenia-passport-number)
- [إسبانيا](#spain-passport-number)
- [السويد](#sweden-passport-number)
- [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](#usuk-passport-number)


## <a name="eu-social-security-number-or-equivalent-identification"></a>رقم الضمان الاجتماعي أو تعريف مكافئ في الاتحاد الأوروبي

هذه هي الكيانات التي توجد في رقم الضمان الاجتماعي في الاتحاد الأوروبي أو تعريف مكافئ لها وهي أنواع معلومات حساسة.

- [النمسا](#austria-social-security-number)
- [بلجيكا](#belgium-national-number)
- [كرواتيا](#croatia-personal-identification-oib-number)
- [التشيكية](#czech-personal-identity-number)
- [الدانمارك](#denmark-personal-identification-number)
- [فنلندا](#finland-national-id)
- [فرنسا](#france-social-security-number-insee)
- [ألمانيا](#germany-identity-card-number)
- [اليونان](#greece-national-id-card)
- [المجر](#hungary-social-security-number-taj)
- [البرتغال](#portugal-citizen-card-number)
- [إسبانيا](#spain-social-security-number-ssn)
- [السويد](#sweden-national-id)


## <a name="eu-tax-identification-number"></a>رقم تعريف الضريبة في الاتحاد الأوروبي

توجد هذه الكيانات في نوع المعلومات الحساسة ل رقم تعريف الضريبة في الاتحاد الأوروبي.

- [النمسا](#austria-tax-identification-number)
- [بلجيكا](#belgium-national-number)
- [بلغاريا](#bulgaria-uniform-civil-number)
- [كرواتيا](#croatia-identity-card-number)
- [قبرص](#cyprus-tax-identification-number)
- [التشيكية](#czech-personal-identity-number)
- [الدانمارك](#denmark-personal-identification-number)
- [إستونيا](#estonia-personal-identification-code)
- [فنلندا](#finland-national-id)
- [فرنسا](#france-tax-identification-number)
- [ألمانيا](#germany-tax-identification-number)
- [اليونان](#greece-tax-identification-number)
- [المجر](#hungary-tax-identification-number)
- [أيرلندا](#ireland-personal-public-service-pps-number)
- [إيطاليا](#italy-fiscal-code)
- [لاتفيا](#latvia-personal-code)
- [لتوانيا](#lithuania-personal-code)
- [Luxemburg](#luxemburg-national-identification-number-non-natural-persons)
- [مالطا](#malta-tax-identification-number)
- [هولندا](#netherlands-tax-identification-number)
- [بولندا](#poland-tax-identification-number)
- [البرتغال](#portugal-tax-identification-number)
- [رومانيا](#romania-personal-numeric-code-cnp)
- [سلوفاكيا](#slovakia-personal-number)
- [سلوفينيا](#slovenia-tax-identification-number)
- [إسبانيا](#spain-tax-identification-number)
- [السويد](#sweden-tax-identification-number)
- [المملكة المتحدة](#uk-unique-taxpayer-reference-number)


## <a name="finland-drivers-license-number"></a>رقم ترخيص القيادة في فنلندا

### <a name="format"></a>تنسيق

10 أرقام تحتوي على الفوسفات

### <a name="pattern"></a>النمط

10 أرقام تحتوي على الوامة:

- ستة أرقام
- الواهة
- ثلاثة أرقام
- رقم أو حرف

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_finland_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_finland_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver لا s_license_number

- ajokortti
- permis de conduire
- ajokortin numero
- kuljja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot


## <a name="finland-european-health-insurance-number"></a>رقم التأمين الصحي الأوروبي لفنلندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

رقم من 20 رقما

### <a name="pattern"></a>النمط

رقم من 20 رقما:

- 10 أرقام - 8024680246
- مسافة اختيارية أو الوابلة الاختيارية
- 10 أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر Regex_Finland_European_Health_Insurance_Number regex على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Finland_European_Health_Insurance_Number كلمة أساسية.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- ehic #
- ehic
- finlandehicnumber #
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


## <a name="finland-national-id"></a>الم ID الوطنية لفنلندا

### <a name="format"></a>تنسيق

ستة أرقام بالإضافة إلى حرف يشير إلى قرن بالإضافة إلى ثلاثة أرقام بالإضافة إلى خانة الاختيار

### <a name="pattern"></a>النمط

يجب أن يتضمن النمط كل ما يلي:
- ستة أرقام بتنسيق DDMMYY، وهو تاريخ الميلاد
- علامة القرن (إما '-' أو '+' أو 'a')
- رقم التعريف الشخصي المكون من ثلاثة أرقام
- رقم أو حرف (حالة غير حساسة) وهو رقم خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة Func_finnish_national_id البحث عن المحتوى الذي يتطابق مع النمط
- تم العثور على Keyword_finnish_national_id كلمة أساسية من
- تمريرات الاختبارات

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة Func_finnish_national_id البحث عن المحتوى الذي يتطابق مع النمط
- تمريرات الاختبارات

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

### <a name="keywords"></a>الكلمات الأساسية

- ainutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- الم id no
- رقم الم id
- رقم التعريف
- identiteetti numero
- رقم الهوية
- idnumber
- kansallinen henkilötunnus
- kansallisen henkilökortin
- بطاقة الهوية الوطنية
- رقم الم id الوطنية.
- الم id الشخصي
- رمز الهوية الشخصية
- personalidnumber #
- personbeteckning
- personnummer
- رقم الضمان الاجتماعي
- sosiaaliturvatunnus
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- tunnistenumero
- tunnus numero
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus


## <a name="finland-passport-number"></a>رقم جواز سفر فنلندا

يتوفر هذا الكيان في نوع المعلومات الحساسة ل رقم جواز السفر في الاتحاد الأوروبي وهو متوفر ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق
تركيبة من تسعة أحرف ورقم

### <a name="pattern"></a>النمط
تركيبة من تسعة أحرف ورقمية:
- حرفان (لا يتحسس حالة الأحرف)
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_finland_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_finland_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_finland_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_finland_passport_number` تم العثور عليها.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
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


## <a name="finland-physical-addresses"></a>العناوين الفعلية لفنلندا

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من فنلندا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="france-drivers-license-number"></a>رقم ترخيص القيادة في فرنسا

يتوفر هذا الكيان في نوع المعلومات الحساسة ل رقم ترخيص القيادة في الاتحاد الأوروبي، كما يتوفر ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

12 رقما

### <a name="pattern"></a>النمط

12 رقما مع التحقق من الصحة للخصم من أنماط مماثلة مثل أرقام الهواتف الفرنسية

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة Func_french_drivers_license البحث عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة Keyword_french_drivers_license كلمة أساسية.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
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

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

رقم من 21 رقما

### <a name="pattern"></a>النمط

رقم من 21 رقما:

- 10 أرقام
- مسافة اختيارية
- 10 أرقام
- مسافة اختيارية
- رقم


### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر Regex_France_Health_Insurance_Number regex على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_France_Health_Insurance_Number كلمة أساسية.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- بطاقة التأمين
- carte vitale
- carte d'assuré social


## <a name="france-national-id-card-cni"></a>بطاقة الهوية الوطنية الفرنسية (CNI)

### <a name="format"></a>تنسيق

12 رقما

### <a name="pattern"></a>النمط

12 رقما

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- يعثر التعبير Regex_france_cni العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على Keywords_france_eu_national_id_card كلمة أساسية من Keywords_france_eu_national_id_card.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

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

يتوفر هذا الكيان في نوع المعلومات الحساسة ل رقم جواز السفر في الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

تسعة أرقام وأحرف

### <a name="pattern"></a>النمط

تسعة أرقام وأحرف:
- رقمان
- حرفان (لا يتحسس حالة الأحرف)
- خمسة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_fr_passport` الدالة على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_france_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date3` على التاريخ بتنسيق العثور على DD MM YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_fr_passport` الدالة على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_france_eu_passport_number` تم العثور عليها.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passeport
- passeport n °
- passeport non
- منفذ التمرير #
- منفذ التمرير #
- passeportnon
- passeportn °
- passeport français
- passeport livre
- carte في منفذ التمرير
- منفذ مرور numéro
- passeport n°
- n° du passeport
- منفذ مرور n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="france-physical-addresses"></a>عناوين فرنسا الفعلية

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من فرنسا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="france-social-security-number-insee"></a>رقم الضمان الاجتماعي في فرنسا (INSEE)

### <a name="format"></a>تنسيق

15 رقما

### <a name="pattern"></a>النمط

يجب أن تتطابق مع أحد النمطين:
- 13 رقما متبوع مسافة متبوع برقمين<br/>
أو
- 15 رقما متتاليا

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_french_insee` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_fr_insee كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_french_insee أو Func_fr_insee المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- code sécu
- d'identité nationale
- insee
- fssn #
- le numéro d'identification nationale
- le code de la sécurité sociale
- الم id الوطنية
- التعريف الوطني
- no d'identité
- لا. d'identité
- numéro d'assurance
- numéro d'identité
- numero d'identite
- numéro de sécu
- numéro de sécurité sociale
- no d'identite
- لا. d'identite
- ssn
- ssn #
- sécurité sociale
- securité sociale
- securite sociale
- socialsecuritynumber
- رقم الضمان الاجتماعي
- رمز الضمان الاجتماعي
- رقم التأمين الاجتماعي


## <a name="france-tax-identification-number"></a>رقم تعريف الضريبة في فرنسا

### <a name="format"></a>تنسيق

13 رقما

### <a name="pattern"></a>النمط

13 رقما

- رقم واحد يجب أن يكون 0 أو 1 أو 2 أو 3
- رقم واحد
- مسافة (اختياري)
- رقمان
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة أرقام للتحقق


### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_france_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_france_eu_tax_file_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_france_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d'identification fiscale
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="france-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في فرنسا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

النمط alphanumeric الذي يكون 13 حرفا

### <a name="pattern"></a>النمط

النمط alphanumeric 13 حرفا:

- حرفان - FR (حالة غير حساسة)
- مسافة اختيارية أو الوابلة الاختيارية
- حرفان أو رقمان
- مسافة اختيارية أو نقطة أو الواسمة أو الفاصلة
- ثلاثة أرقام
- مسافة اختيارية أو نقطة أو الواسمة أو الفاصلة
- ثلاثة أرقام
- مسافة اختيارية أو نقطة أو الواسمة أو الفاصلة
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_france_value_added_tax_number الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_france_value_added_tax_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_france_value_added_tax_number الدالة على المحتوى الذي يتطابق مع النمط.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- رقم ضريبة القيمة المضافة
- لا لضريبة القيمة المضافة
- ضريبة القيمة المضافة #
- ضريبة القيمة المضافة
- تعريف صفيف بدون numéro d'identificatione taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification


## <a name="generic-medication-names"></a>أسماء الأدوية العامة

يكشف هذا الكيان المسمى الذي لم يتم ثنيه عن أسماء الأدوية العامة، مثل *acetaminophen*. فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال


## <a name="germany-drivers-license-number"></a>رقم ترخيص القيادة في ألمانيا

يتم تضمين كيان نوع المعلومات الحساس هذا في نوع المعلومات الحساسة ل رقم ترخيص برنامج تشغيل الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

تركيبة من 11 رقما وخطا

### <a name="pattern"></a>النمط

11 رقما وخطا (لا تتحسس حالة الأحرف):
- رقم أو حرف
- رقمان
- ستة أرقام أو أحرف
- رقم
- رقم أو حرف

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_german_drivers_license المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_german_drivers_license_number كلمة أساسية.
- يتم تمرير الاختبارات.

```xml
    <!-- German Driver's License Number -->
    <Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Match idRef="Keyword_german_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_german_drivers_license_number"></a>Keyword_german_drivers_license_number

- ausstellungsdatum
- ausstellungsort
- ausstellende behöde
- ausstellende behorde
- ausstellende behoerde
- führerschein
- fuhrerschein
- fuehrerschein
- führerscheinnummer
- fuhrerscheinnummer
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
- no-fuhrerschein
- no-fuehrerschein
- n-führerschein
- n-fuhrerschein
- n-fuehrerschein
- permis de conduire
- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dlno


## <a name="germany-identity-card-number"></a>رقم بطاقة هوية ألمانيا

### <a name="format"></a>تنسيق

منذ 1 نوفمبر 2010: من تسعة إلى أحد عشر حرفا ورقما

من 1 أبريل 1987 إلى 31 أكتوبر 2010: 10 أرقام

### <a name="pattern"></a>النمط

منذ 1 نوفمبر 2010: نمط alphanumeric من 9 إلى 11 حرفا
- واحد L، M، N، P، R، T، V، W، X، Y (حالة غير حساسة)
- ثمانية أرقام أو أحرف في C و F و G و H و J و K و L و M و N و P و R و T و V و W و X و Y و Z (حالة غير حساسة)
- خانة اختيارية
- اختياري d/D

من 1 أبريل 1987 إلى 31 أكتوبر 2010:
- 10 أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_german_id_card_with_check` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_germany_id_card` من.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_germany_id_card` العادي على المحتوى الذي يتطابق مع النمط (9 أحرف بدون خانة رقمية تم إصدارها قبل 2010 أو 10 أرقام تم إصدارها من posy 2010).
- تم العثور على كلمة أساسية Keyword_germany_id_card كلمة أساسية.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر `Func_german_id_card_with_check` الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- تعريف
- identifikation
- identifizierungsnummer
- بطاقة الهوية
- رقم الهوية
- id-nummer
- الم id الشخصي
- personalausweis
- persönliche id nummer
- persönliche identifikationsnummer
- persönliche-id-nummer


## <a name="germany-passport-number"></a>رقم جواز السفر الألماني

### <a name="format"></a>تنسيق

من 9 إلى 11 حرفا

### <a name="pattern"></a>النمط

- حرف واحد في C، F، G، H، J، K (حالة غير حساسة)
- ثمانية أرقام أو أحرف في C و F و G و H و J و K و L و M و N و P و R و T و V و W و X و Y و Z (حالة غير حساسة)
- خانة اختيارية
- اختياري d/D

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_german_passport_checksum` الدالة على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keyword_german_passport` أو `Keywords_eu_passport_number_common` تم العثور عليها.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة `Func_german_passport` على المحتوى الذي يتطابق مع نمط الأحرف التسعة (بدون خانة رقمية و d/D اختياري).
- كلمة أساسية من `Keyword_german_passport` أو `Keywords_eu_passport_number_common` تم العثور عليها.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر `Func_german_passport_checksum` الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- passeport no.
- passeport no

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر


## <a name="germany-physical-addresses"></a>عناوين ألمانيا الفعلية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من ألمانيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="germany-tax-identification-number"></a>رقم تعريف الضريبة في ألمانيا

### <a name="format"></a>تنسيق

11 رقما بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

11 رقما

- رقمان
- مسافة اختيارية
- ثلاثة أرقام
- مسافة اختيارية
- ثلاثة أرقام
- مسافة اختيارية
- رقمان
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_germany_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_germany_eu_tax_file_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_germany_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- id steuer
- steueridentifikationsnummer
- steuernummer
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- zinn #
- zinn
- بعض الوقت


## <a name="germany-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في ألمانيا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 11 حرفا

### <a name="pattern"></a>النمط

النمط alphanumeric من 11 حرفا:

- حرف D أو d
- حرف E أو e
- مسافة اختيارية
- ثلاثة أرقام
- مسافة اختيارية أو فاصلة اختيارية
- ثلاثة أرقام
- مسافة اختيارية أو فاصلة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_germany_value_added_tax_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_germany_value_added_tax_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_germany_value_added_tax_number على المحتوى الذي يتطابق مع النمط.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- رقم ضريبة القيمة المضافة
- لا لضريبة القيمة المضافة
- ضريبة القيمة المضافة #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer


## <a name="greece-drivers-license-number"></a>رقم ترخيص القيادة في اليونان

يتم تضمين هذا الكيان في نوع المعلومات الحساسة ل رقم ترخيص القيادة في الاتحاد الأوروبي. كما أنه متوفر ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_greece_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_greece_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_greece_eu_drivers_license_number"></a>Keywords_greece_eu_driver لا s_license_number

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης


## <a name="greece-national-id-card"></a>بطاقة الم ID الوطنية في اليونان

### <a name="format"></a>تنسيق

تركيبة من 7 إلى 8 أحرف و أرقام بالإضافة إلى شرطة

### <a name="pattern"></a>النمط

سبعة أحرف و أرقام (تنسيق قديم):
- حرف واحد (أي حرف من الأحرف الأبجدية اليونانية)
- شرطة
- ستة أرقام

ثمانية أحرف و أرقام (تنسيق جديد):
- حرفان حرفان أحرف كبيرة في كل من الحروف الأبجدية اليونانية واللاتينية (ABEZHIKMNOPTYX)
- شرطة
- ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_greece_id_card العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_greece_id_card كلمة أساسية.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- يعثر التعبير Regex_greece_id_card العادي على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- الم id اليونانية
- الم id الوطنية اليونانية
- بطاقة الهوية الشخصية اليونانية
- id الشرطة اليونانية
- بطاقة الهوية
- tautotita
- ταυτότητα
- ταυτότητας


## <a name="greece-passport-number"></a>رقم جواز سفر اليونان

### <a name="format"></a>تنسيق

حرفان متبوعان بسبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرفان متبوعان بسبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_greece_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_greece_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_greece_eu_passport_date` على التاريخ بتنسيق DD MMM YY (مثال - 28 أغسطس 19) `Keywords_greece_eu_passport_date` أو تم العثور على كلمة أساسية من

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_greece_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_greece_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο


## <a name="greece-physical-addresses"></a>العناوين الفعلية في اليونان

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من اليونان. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط

## <a name="greece-social-security-number-amka"></a>رقم الضمان الاجتماعي في اليونان (AMKA)

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

11 رقما بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

- ستة أرقام ك تاريخ الميلاد YYMMDD
- أربعة أرقام
- خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_greece_eu_ssn` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_greece_eu_ssn_or_equivalent` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_greece_eu_ssn` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- ssn
- ssn #
- لا الضمان الاجتماعي
- socialsecurityno #
- رقم الضمان الاجتماعي
- amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης


## <a name="greece-tax-identification-number"></a>رقم تعريف الضريبة في اليونان

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- يعثر التعبير  `Regex_greece_eu_tax_file_number` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_greece_eu_tax_file_number` من.

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- afm #
- afm
- aпμ|aμ αριθμός
- aпμ
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سجل الضرائب لا
- رقم السجل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- taxregistryno #
- "معرف الصفيح"
- tin no
- صفيحة #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο


## <a name="hong-kong-identity-card-hkid-number"></a>رقم بطاقة هوية هونج كونج (HKID)

### <a name="format"></a>تنسيق

تركيبة من 8 إلى 9 أحرف و أرقام بالإضافة إلى  الوالدين الاختياريين حول الحرف النهائي

### <a name="pattern"></a>النمط

تركيبة من 8 إلى 9 أحرف:
- حرف واحد إلى حرفين (لا يتحسس حالة الأحرف)
- ستة أرقام
- الحرف النهائي (أي رقم أو الحرف A)، وهو خانة الاختيار ومحاطة بشكل اختياري بين طوقين.

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_hong_kong_id_card المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_hong_kong_id_card كلمة أساسية.
- يتم تمرير الاختبارات.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_hong_kong_id_card المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- بطاقة هوية هونغ كونغ
- HKIDC
- بطاقة الم id
- بطاقة الهوية
- بطاقة هوية hk
- الهونغ كونغ
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


## <a name="hungary-drivers-license-number"></a>رقم ترخيص القيادة في هنغاريا

### <a name="format"></a>تنسيق

حرفان متبوعان بستة أرقام

### <a name="pattern"></a>النمط

حرفان وستة أرقام:

- حرفان (لا يتحسس حالة الأحرف)
- ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- يعثر التعبير  `Regex_hungary_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_hungary_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver لا s_license_number

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek


## <a name="hungary-passport-number"></a>رقم جواز السفر المجري

### <a name="format"></a>تنسيق

حرفان متبوعان بستة أو سبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرفان متبوعان بستة أو سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_hungary_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_hungary_eu_passport_number` تم العثور عليها.
- يعثر التعبير `Regex_hungary_eu_passport_date` العادي على التاريخ بتنسيق DD MMM/MMM YY (مثال - 01 MÁR/MAR 12) `Keywords_eu_passport_date` أو تم العثور على كلمة أساسية منها

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_hungary_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_hungary_eu_passport_number` تم العثور عليها.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="hungary-personal-identification-number"></a>رقم التعريف الشخصي في هنغاريا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>النمط

11 رقما:

- رقم واحد يتطابق مع الجنس، و1 للذكر، و2 للأنثى. يمكن أيضا الحصول على أرقام أخرى من قبل مواليد 1900 أو من ذوي المواطين المزدوجين.
- ستة أرقام تتطابق مع تاريخ الميلاد (YYMMDD)
- ثلاثة أرقام تتطابق مع رقم تسلسلي
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر  `Func_hungary_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_hungary_eu_national_id_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر  `Func_hungary_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- رقم الم id
- رقم التعريف
- sz ig
- sz. ig.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány


## <a name="hungary-physical-addresses"></a>العناوين الفعلية للمجر

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من هنغاريا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="hungary-social-security-number-taj"></a>رقم الضمان الاجتماعي في هنغاريا (TAJ)

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر  `Func_hungary_eu_ssn_or_equivalent` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_hungary_eu_ssn_or_equivalent` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر  `Func_hungary_eu_ssn_or_equivalent` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- رقم الضمان الاجتماعي المجري
- رقم الضمان الاجتماعي
- socialsecuritynumber #
- hssn #
- socialsecuritynno
- hssn
- تاج
- تاج #
- ssn
- ssn #
- لا الضمان الاجتماعي
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám


## <a name="hungary-tax-identification-number"></a>رقم تعريف الضريبة في هنغاريا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

10 أرقام:

- رقم واحد يجب أن يكون "8"
- ثمانية أرقام
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر  `Func_hungary_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_hungary_eu_tax_file_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر  `Func_hungary_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- صفيحة هنغارية
- hungatiantin #
- هيئة الضرائب لا
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- رقم ضريبة القيمة المضافة


## <a name="hungary-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في هنغاريا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 10 أحرف

### <a name="pattern"></a>النمط

النمط alphanumeric من 10 أحرف:

- حرفان - HU أو hu
- مسافة اختيارية
- ثمانية أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر الدالة Func_hungarian_value_added_tax_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_hungarian_value_added_tax_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر الدالة Func_hungarian_value_added_tax_number المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- ضريبة القيمة المضافة
- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة #
- vatno #
- hungarianvatno #
- رقم الضريبة.
- ضريبة القيمة المضافة áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám


## <a name="iceland-physical-addresses"></a>العناوين الفعلية في آيسلندا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من آيسلندا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>الإعاقة المدرجة في تقييم الإعاقة في الولايات المتحدة ضمن الضمان الاجتماعي

يكشف هذا الكيان المسمى الذي لم يتم تكديسه أسماء الإعاقة المدرجة في تقييم الإعاقة في الولايات المتحدة ضمن الضمان الاجتماعي، مثل ضمور *العضلي*. فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال


## <a name="india-drivers-license-number"></a>رقم ترخيص برنامج تشغيل الهند

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 15 حرفا

### <a name="pattern"></a>النمط

15 حرفا أو رقما:
- حرفان يشيران إلى رمز الولاية
- مسافة اختيارية أو شرطة اختيارية
- رقمان يشيران إلى رمز المدينة
- مسافة اختيارية أو شرطة اختيارية
- أربعة أرقام تشير إلى سنة المشكلة
- مسافة اختيارية أو شرطة اختيارية
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_india_driving_license` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keywords_eu_driver's_license_number_common` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_india_driving_license` العادي على المحتوى الذي يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver لا s_license_number_common

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl



## <a name="india-gst-number"></a>رقم GST في الهند

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 15 حرفا

### <a name="pattern"></a>النمط

15 حرفا أو رقما:
- رقمان يمثلان رمز الحالة الصالح
- مسافة اختيارية أو شرطة اختيارية
- عشرة أحرف تمثل رقم الحساب الدائم (PAN) 
- حرف واحد أو رقم واحد
- مسافة اختيارية أو شرطة اختيارية
- حرف واحد 'z' أو 'Z'
- مسافة اختيارية أو شرطة اختيارية
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_india_gst_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_india_gst_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_india_gst_number` الدالة على المحتوى الذي يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- gst
- gstin
- ضريبة السلع والخدمات
- ضريبة السلع والخدمات


## <a name="india-permanent-account-number-pan"></a>رقم الحساب الدائم للهند (PAN)

### <a name="format"></a>تنسيق

10 أحرف أو أرقام

### <a name="pattern"></a>النمط

10 أحرف أو أرقام:
- ثلاثة أحرف (لا تتحسس حالة الأحرف)
- حرف في C و P و H و F و A و T و B و L و J و G (لا يتحسس حالة الحروف)
- رسالة
- أربعة أرقام
- حرف هو خانة الاختيار الأبجدية

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_india_permanent_account_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_india_permanent_account_number كلمة أساسية.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- يعثر التعبير Regex_india_permanent_account_number العادي على المحتوى الذي يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- رقم الحساب الدائم
- PAN

## <a name="india-unique-identification-aadhaar-number"></a>رقم التعريف الفريد (Aadhaar) في الهند

### <a name="format"></a>تنسيق

12 رقما تحتوي على مسافات أو شرط اختيارية

### <a name="pattern"></a>النمط

12 رقما:
- رقم ليس 0 أو 1
- ثلاثة أرقام
- مسافة اختيارية أو شرطة اختيارية
- أربعة أرقام
- مسافة اختيارية أو شرطة اختيارية
- الرقم النهائي، وهو خانة الاختيار

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_india_aadhaar الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_india_aadhar كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر Func_india_aadhaar الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- aadhar
- aadhar #
- uid
- आधार
- uidai


## <a name="india-voter-id-card"></a>بطاقة هوية الرابية الهندية

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 10 أحرف

### <a name="pattern"></a>النمط

10 أحرف أو أرقام:
- ثلاثة أحرف
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_india_voter_id_card` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_india_voter_id_card` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- يعثر التعبير `Regex_india_voter_id_card` العادي على المحتوى الذي يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- voter
- voterid
- بطاقة البدل
- بطاقة الرتبة الخاصة
- بطاقة هوية صورة
- EPIC
- ECI
- commmision


## <a name="indonesia-identity-card-ktp-number"></a>رقم بطاقة هوية إندونيسيا (KTP)

### <a name="format"></a>تنسيق

16 رقما تحتوي على فترات اختيارية

### <a name="pattern"></a>النمط

16 رقما:
- رمز المقاطعة المكون من رقمين
- فترة زمنية (اختيارية)
- رمز مدينة أو وكالة من رقمين
- التعليمات البرمجية الفرعية المكونة من رقمين
- فترة زمنية (اختيارية)
- ستة أرقام بتنسيق DDMMYY، وهو تاريخ الميلاد
- فترة زمنية (اختيارية)
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- يعثر التعبير Regex_indonesia_id_card العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_indonesia_id_card كلمة أساسية.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk
- Nomor Induk Kependukan

## <a name="international-banking-account-number-iban"></a>رقم حساب الخدمات المصرفية الدولية (IBAN)

### <a name="format"></a>تنسيق

رمز البلد (حرفان) بالإضافة إلى خانات الاختيار (رقمان) بالإضافة إلى رقم bban (ما يصل إلى 30 حرفا)

### <a name="pattern"></a>النمط

يجب أن يتضمن النمط كل ما يلي:

- رمز البلد من حرفين
- رقمان للتحقق (متبوعان بمساحة اختيارية)
- مجموعات من 1 إلى 7 من أربعة أحرف أو أرقام (يمكن فصلها بمساحات)
- 1-3 أحرف أو أرقام

يختلف التنسيق لكل بلد اختلافا طفيفا. يغطي نوع المعلومات الحساسة ل IBAN هذه البلدان ال 60:

- ad
- ae
- al
- في
- az
- ba
- تكون
- bg
- bh
- ch
- cr
- cy
- cz
- de
- dk
- do
- ee
- es
- fi
- fo
- fr
- غيغابايت
- ge
- gi
- gl
- gr
- hr
- hu
- ie
- il
- is
- إنه
- kw
- kz
- lb
- li
- lt
- lu
- lv
- mc
- md
- أنا
- mk
- mr
- mt
- mu
- nl
- لا
- pl
- pt
- ro
- rs
- sa
- se
- si
- sk
- sm
- tn
- tr
- vg

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- تعثر الدالة Func_iban المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

بلا


## <a name="international-classification-of-diseases-icd-10-cm"></a>التصنيف الدولي لداءات (ICD-10-CM)

### <a name="format"></a>تنسيق

القاموس

### <a name="pattern"></a>النمط

الكلمة الأساسية

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تم العثور على كلمة أساسية Dictionary_icd_10_updated كلمة أساسية.
- تم العثور على كلمة أساسية Dictionary_icd_10_codes كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تم العثور على كلمة أساسية Dictionary_icd_10_ تم تحديثها.

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

### <a name="keywords"></a>الكلمات الأساسية

أي مصطلح من قاموس Dictionary_icd_10_updated الأساسية، الذي يستند إلى التصنيف الدولي للشروط المرضية، المراجعة العاشرة، التعديل الإكلينيكي [(ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604) . هذا النوع للبحث عن المصطلح فقط، وليس رموز التأمين.

أي مصطلح من قاموس Dictionary_icd_10_codes الأساسية، الذي يستند إلى التصنيف الدولي للشروط المرضية، المراجعة العاشرة، التعديل الإكلينيكي [(ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604). هذا النوع للبحث عن رموز التأمين فقط، وليس الوصف.


## <a name="international-classification-of-diseases-icd-9-cm"></a>التصنيف الدولي لداءات (ICD-9-CM)

### <a name="format"></a>تنسيق

القاموس

### <a name="pattern"></a>النمط

الكلمة الأساسية

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تم العثور على كلمة أساسية Dictionary_icd_9_updated كلمة أساسية.
- تم العثور على كلمة أساسية Dictionary_icd_9_codes كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تم العثور على كلمة أساسية Dictionary_icd_9_updated كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

أي مصطلح من قاموس Dictionary_icd_9_updated الأساسية، الذي يستند إلى التصنيف الدولي للشروط المرضية، المراجعة التاسع، التعديل الإكلينيكي [(ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). هذا النوع للبحث عن المصطلح فقط، وليس رموز التأمين.

أي مصطلح من قاموس Dictionary_icd_9_codes الأساسية، الذي يستند إلى التصنيف الدولي للشروط المرضية، المراجعة التاسع، التعديل الإكلينيكي [(ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605) . هذا النوع للبحث عن رموز التأمين فقط، وليس الوصف.

## <a name="ip-address"></a>عنوان IP

### <a name="format"></a>تنسيق

#### <a name="ipv4"></a>IPv4:
النمط المركب الذي يتم حسابه للإصدارات (الفترات) وغير المنسقة (بدون فترات) من عناوين IPv4

#### <a name="ipv6"></a>IPv6:
النمط المركب الذي يمثل أرقام IPv6 التي تم تنسيقها (والتي تتضمن النقطتين)

### <a name="pattern"></a>النمط

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

بالنسبة إلى IPv6، يكون نهج DLP على ثقة عالية بأنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، ضمن تقارب 300 حرف:
- يعثر التعبير Regex_ipv6_address العادي على المحتوى الذي يتطابق مع النمط.
- لم يتم العثور على كلمة Keyword_ipaddress كلمة أساسية.

بالنسبة ل IPv4، فإن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا، ضمن تقارب 300 حرف:
- يعثر التعبير Regex_ipv4_address العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_ipaddress كلمة أساسية.

بالنسبة إلى IPv6، يكون نهج DLP على ثقة عالية بأنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، ضمن تقارب 300 حرف:
- يعثر التعبير Regex_ipv6_address العادي على المحتوى الذي يتطابق مع النمط.
- لم يتم العثور على كلمة Keyword_ipaddress كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (تتحسس هذه الكلمة الأساسية حالة التحسس)
- عنوان ip
- عناوين ip
- بروتوكول الإنترنت
- IP-כתובת 3


## <a name="ip-address-v4"></a>عنوان IP v4

### <a name="format"></a>تنسيق

النمط المركب الذي يتم حسابه للإصدارات (الفترات) وغير المنسقة (بدون فترات) من عناوين IPv4

### <a name="pattern"></a>النمط


### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_ipv4_address` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_ipaddress` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_ipv4_address` العادي على المحتوى الذي يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (حساس لل حالة التحسس)
- عنوان ip
- عناوين ip
- بروتوكول الإنترنت
- IP-כתובת 3


## <a name="ip-address-v6"></a>عنوان IP v6

### <a name="format"></a>تنسيق

النمط المركب الذي يمثل أرقام IPv6 التي تم تنسيقها (والتي تتضمن النقطتين)

### <a name="pattern"></a>النمط


### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_ipv6_address` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_ipaddress` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_ipv6_address` العادي على المحتوى الذي يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (حساس لل حالة التحسس)
- عنوان ip
- عناوين ip
- بروتوكول الإنترنت
- IP-כתובת 3


## <a name="ireland-drivers-license-number"></a>رقم ترخيص القيادة في أيرلندا

### <a name="format"></a>تنسيق

ستة أرقام متبوع بأربعة أحرف

### <a name="pattern"></a>النمط

ستة أرقام وأربعة أحرف:

- ستة أرقام
- أربعة أحرف (لا تتحسس حالة الأحرف)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:

- يعثر التعبير  `Regex_ireland_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_ireland_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver لا s_license_number

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>رقم جواز سفر أيرلندا

### <a name="format"></a>تنسيق

حرفان أو رقمان متبوعان بسبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرفان أو رقمان متبوعان بسبعة أرقام:

- رقمان أو حرفان (لا يتحسس حالة الأحرف)
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_ireland_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_ireland_eu_passport_number` تم العثور عليها.
- يعثر التعبير `Regex_ireland_eu_passport_date` العادي على التاريخ بتنسيق DD MMM/MMM YYYY (مثال - 01 BEA/مايو 1988) `Keywords_eu_passport_date` أو تم العثور على كلمة أساسية من

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_ireland_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_ireland_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- numero في منفذ التمرير
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
- سبعة أرقام متبوع بحروف من 1 إلى 2

تنسيق جديد (1 يناير 2013 وما بعده):
- سبعة أرقام متبوعتان برقمين

### <a name="pattern"></a>النمط

التنسيق القديم (حتى 31 ديسمبر 2012):
- سبعة أرقام
- حرف إلى حرفين (لا يتحسس حالة الأحرف)

تنسيق جديد (1 يناير 2013 وما بعده):
- سبعة أرقام
- حرف (لا يتحسس حالة الأحرف) وهو رقم خانة الاختيار الأبجدية
- حرف اختياري في النطاق A-I أو "W"

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_ireland_pps المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_ireland_eu_national_id_card كلمة أساسية.
- يتم تمرير الاختبارات.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_ireland_pps المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- خدمة هوية العميل
- رقم التعريف
- رقم الم id الشخصي
- رقم الخدمة العامة الشخصية
- الخدمة الشخصية لا
- phearsanta seirbhíse poiblí
- pps no
- رقم pps
- pps num
- خدمة pps لا
- ppsn
- ppsno #
- ppsno
- psp
- الخدمة العامة لا
- publicserviceno #
- publicserviceno
- رقم التأمين الاجتماعي والإيرادات
- rsi no
- rsi number
- rsin
- seirbhís aitheantais client
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="ireland-physical-addresses"></a>عناوين أيرلندا الفعلية

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من أيرلندا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="israel-bank-account-number"></a>رقم الحساب البنكي في إسرائيل

### <a name="format"></a>تنسيق

13 رقما

### <a name="pattern"></a>النمط

تم التنسيق:
- رقمان
- شرطة
- ثلاثة أرقام
- شرطة
- ثمانية أرقام

غير مهيى:
- 13 رقما متتاليا

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_israel_bank_account_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_israel_bank_account_number كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- رقم الحساب البنكي
- الحساب البنكي
- رقم الحساب
- מספר חשבון בנק


## <a name="israel-national-identification-number"></a>رقم التعريف الوطني في إسرائيل

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>النمط

تسعة أرقام متتالية

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_israeli_national_id_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Israel_National_ID كلمة أساسية.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

-   מספר זהות
-   מספר זיה וי
-   מספר זיהוי ישר אלי      
-   זהותישר אלית
-   هو ية اسرائيل ية عدد
-   هوية إسرائ يلية
-   رقم الهوية
-   عدد هوية فريدة من نوعها
-   idnumber #
-   رقم الم id
-   الهوية لا        
-   identitynumber #
-   رقم الهوية
-   israeliidentitynumber       
-   الم id الشخصي
-   الم id الفريد  


## <a name="italy-drivers-license-number"></a>رقم ترخيص القيادة في إيطاليا

يتم تضمين هذا الكيان من النوع في نوع المعلومات الحساسة ل رقم ترخيص القيادة في الاتحاد الأوروبي. كما أنه متوفر ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

مجموعة من 10 أحرف ورقم

### <a name="pattern"></a>النمط

مجموعة من 10 أحرف ورقم:
- حرف واحد (لا يتحسس حالة الحروف)
- الحرف "A" أو "V" (لا يتحسس حالة الحروف)
- سبعة أرقام
- حرف واحد (لا يتحسس حالة الحروف)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير `Regex_italy_drivers_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keyword_italy_drivers_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
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
- براءة اختراع guida
- patenti di guida
- patenti guida


## <a name="italy-fiscal-code"></a>رمز إيطاليا المالي
يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

تركيبة من 16 حرفا من الأحرف والأرقام في النمط المحدد

### <a name="pattern"></a>النمط

مجموعة من 16 حرفا من الأحرف والأرقام:
- ثلاثة أحرف تتوافق مع الأحرف الساكنة الثلاثة الأولى في اسم العائلة
- ثلاثة أحرف تتوافق مع الأحرف الساكنة الأولى والثالثة والرابعة في الاسم الأول
- رقمان يتطابقان مع الأرقام الأخيرة من سنة الميلاد
- حرف واحد يتطابق مع الحرف لشهر الميلاد— يتم استخدام الأحرف بالترتيب الأبجدي، ولكن يتم استخدام الأحرف فقط من أ إلى E، H، L، M، P، R إلى T (لذلك، شهر يناير هو أ وأكتوبر هو R)
- رقمان يتطابقان مع يوم من شهر الميلاد من أجل التمييز بين  الجنس، تتم إضافة 40 إلى يوم ميلاد النساء
- أربعة أرقام تتوافق مع رمز المنطقة الخاص للبلدية التي وُلد فيها الشخص (تستخدم الرموز على مستوى البلد للبلدان الأجنبية)
- رقم واحد للاتقاء

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_italy_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_italy_eu_national_id_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_italy_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice Fiscal
- codice Fiscale
- codice idice id personale
- codice personale
- التعليمات البرمجية المالية
- numero certificato personale
- numero di identificazione fiscale
- numero id personale
- numero personale
- رقم الشهادة الشخصية
- الرمز الشخصي
- رمز الم id الشخصي
- رقم الم id الشخصي
- personalcodeno #
- رمز الضريبة
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- رقم الهوية الضريبية
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="italy-passport-number"></a>رقم جواز سفر إيطاليا

### <a name="format"></a>تنسيق

حرفان أو رقمان متبوعة بسبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرفان أو رقمان متبوعان بسبعة أرقام:

- رقمان أو حرفان (لا يتحسس حالة الأحرف)
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_italy_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_italy_eu_passport_number` تم العثور عليها.
- يعثر التعبير `Regex_italy_eu_passport_date` العادي على التاريخ بتنسيق DD MMM/MMM YYYY (مثال - 01 GEN/JAN 1988) `Keywords_eu_passport_date` أو تم العثور على كلمة أساسية منها

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_italy_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_italy_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto numero
- منفذ مرور numéro
- numero di passaporto
- numeri del passaporto
- passeport italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="italy-physical-addresses"></a>عناوين إيطاليا الفعلية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من إيطاليا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="italy-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في إيطاليا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 13 حرفا مع معينات اختيارية

### <a name="pattern"></a>النمط

نمط ألفا رقمي من 13 حرفا مع معينات اختيارية:

- I أو i
- T أو t
- مسافة اختيارية أو نقطة أو الواسمة أو الفاصلة
- 11 رقما

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_italy_value_added_tax_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_italy_value_added_tax_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_italy_value_added_tax_number المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- رقم ضريبة القيمة المضافة
- لا لضريبة القيمة المضافة
- ضريبة القيمة المضافة #
- iva
- iva #


## <a name="japan-bank-account-number"></a>رقم الحساب البنكي الياباني

### <a name="format"></a>تنسيق

سبعة أو ثمانية أرقام

### <a name="pattern"></a>النمط

رقم الحساب البنكي:
- سبعة أو ثمانية أرقام
- رمز فرعي للحساب البنكي:
- أربعة أرقام
- مسافة أو شرطة (اختياري)
- ثلاثة أرقام

الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_jp_bank_account المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_jp_bank_account كلمة أساسية.
- يكون أحد ما يلي صحيحا:
- تعثر Func_jp_bank_account_branch_code الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_jp_bank_branch_code كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_jp_bank_account المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_jp_bank_account كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- التحقق من رقم الحساب
- التحقق من الحساب
- التحقق من الحساب #
- التحقق من رقم Acct
- التحقق من Acct #
- التحقق من Acct No.
- التحقق من رقم الحساب.
- رقم الحساب البنكي
- الحساب البنكي
- الحساب البنكي #
- رقم Bank Acct
- Bank Acct #
- Bank Acct No.
- رقم الحساب البنكي
- رقم حساب التوفير
- حساب التوفير
- حساب التوفير #
- رقم Acct للادخار
- Savings Acct #
- حفظ Acct No.
- رقم حساب التوفير.
- رقم حساب المدين
- حساب المدين
- حساب المدين #
- رقم الخصم Acct
- خصم Acct #
- خصم Acct No.
- رقم حساب المدين.
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

## <a name="japan-drivers-license-number"></a>رقم ترخيص القيادة في اليابان

### <a name="format"></a>تنسيق

12 رقما

### <a name="pattern"></a>النمط

12 رقما متتاليا

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_jp_drivers_license_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_jp_drivers_license_number كلمة أساسية.

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- driverlicense
- driverslicense
- اطباق برنامج التشغيل
- driverslicenses
- م الشرائح الخاصة ب برنامج التشغيل
- driverlicenses
- dl #
- dls #
- lic #
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


## <a name="japan-my-number---corporate"></a>اليابان رقمي - الشركة

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

رقم من 13 رقما

### <a name="pattern"></a>النمط

الرقم المكون من 13 رقما:

- رقم واحد من رقم واحد إلى تسعة
- 12 رقما

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_japanese_my_number_corporate المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_japanese_my_number_corporate.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_japanese_my_number_corporate المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

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


## <a name="japan-my-number---personal"></a>اليابان رقمي - شخصي

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

رقم من 12 رقما

### <a name="pattern"></a>النمط

الرقم المكون من 12 رقما:

- أربعة أرقام
- مسافة اختيارية أو نقطة أو الوابلة
- أربعة أرقام
- مسافة اختيارية أو نقطة أو الوابلة
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_japanese_my_number_personal المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_japanese_my_number_personal كلمة أساسية.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_japanese_my_number_personal المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

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


## <a name="japan-passport-number"></a>رقم جواز السفر الياباني

### <a name="format"></a>تنسيق

حرفان متبوعان بسبعة أرقام

### <a name="pattern"></a>النمط

حرفان (لا يتحسسان حالة الأحرف) متبوعين بسبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_jp_passport المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_jp_passport كلمة أساسية.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

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

### <a name="pattern"></a>النمط

12 حرفا ورقما:
- حرفان (لا يتحسس حالة الأحرف)
- ثمانية أرقام
- حرفان (لا يتحسس حالة الأحرف)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_jp_residence_card_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على Keyword_jp_residence_card_number كلمة أساسية من Keyword_jp_residence_card_number.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- رقم بطاقة الإقامة
- بطاقة الإقامة لا
- بطاقة الإقامة #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>رقم التسجيل المقيم في اليابان

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>النمط

11 رقما متتاليا

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_jp_resident_registration_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_jp_resident_registration_number كلمة أساسية.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- رقم تسجيل المقيمين
- رقم السجل الأساسي للمقيمين
- رقم تسجيل المقيمين.
- رقم التسجيل المقيم
- رقم السجل الأساسي للمقيمين.
- رقم تسجيل المقيم الأساسي.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証


## <a name="japan-social-insurance-number-sin"></a>رقم التأمين الاجتماعي الياباني (SIN)

### <a name="format"></a>تنسيق

7 إلى 12 رقما

### <a name="pattern"></a>النمط

7-12 رقما:
- أربعة أرقام
- الوابلة (اختيارية)
- OR المكون من ستة أرقام
- 7-12 رقما متتاليا

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_jp_sin الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_jp_sin كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_jp_sin_pre_1997 المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_jp_sin كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- رقم التأمين الاجتماعي
- التأمين الاجتماعي Num
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


## <a name="lab-test-terms"></a>شروط الاختبار المعملي

يكشف هذا الكيان المسمى الذي لم يتم حله عن المصطلحات ذات الصلة باختبارات المعمل، مثل *"تينك C-بيبتييد*". فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال


## <a name="latvia-drivers-license-number"></a>رقم ترخيص القيادة في لاتفيا

### <a name="format"></a>تنسيق

ثلاثة أحرف متبوع بستة أرقام

### <a name="pattern"></a>النمط

ثلاثة أحرف وستة أرقام:

- ثلاثة أحرف (لا تتحسس حالة الأحرف)
- ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_latvia_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_latvia_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_latvia_eu_drivers_license_number"></a>Keywords_latvia_eu_driver لا s_license_number

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība


## <a name="latvia-passport-number"></a>رقم جواز سفر لاتفيا

### <a name="format"></a>تنسيق

حرفان أو رقمان متبوعة بسبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرفان أو رقمان متبوعان بسبعة أرقام:

- رقمان أو حرفان (لا يتحسس حالة الأحرف)
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_latvia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_latvia_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_latvia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_latvia_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- نوادر بايز
- نونمور بايز
- pases numuri
- pases nr
- passeport no
- n° du Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="latvia-personal-code"></a>رمز لاتفيا الشخصي

### <a name="format"></a>تنسيق

11 رقما ووابل اختياري

### <a name="pattern"></a>النمط

التنسيق القديم

11 رقما وفاتمة:

- ستة أرقام تتطابق مع تاريخ الميلاد (DDMMYY)
- الواهة
- رقم واحد يتطابق مع قرن الميلاد ("0" في القرن التاسع عشر و"1" في القرن العشرين و"2" في القرن الواحد والعشرين)
- أربعة أرقام، تم إنشاؤها عشوائيا

تنسيق جديد

11 رقما

- رقمان "32"
- تسعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_latvia_eu_national_id_card` الدالة أو regex `Regex_latvia_eu_national_id_card_new_format` على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_latvia_eu_national_id_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_latvia_eu_national_id_card` الدالة أو regex `Regex_latvia_eu_national_id_card_new_format` على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- رقم إداري
- alvas n،
- رقم الميلاد
- رقم هاتف
- رقم مدني
- رقم الإحصاء الإلكتروني
- رقم إلكتروني
- التعليمات البرمجية المالية
- رقم مستخدم الرعاية الصحية
- الم id #
- رمز id
- رقم التعريف
- identifikācijas numurs
- رقم الم id
- رقم فردي
- latvija alva
- nacionālais id
- الم id الوطنية
- رقم التعريف الوطنية
- رقم الهوية الوطنية
- رقم التأمين الوطني
- رقم السجل الوطني
- nodokļa نواة
- nodokļu الما بعد
- nodokļu identifikācija numurs
- رقم الشهادة الشخصية
- الرمز الشخصي
- رمز الم id الشخصي
- رقم الم id الشخصي
- رمز التعريف الشخصي
- المعرف الشخصي
- رقم الهوية الشخصية
- الرقم الشخصي
- رمز رقمي شخصي
- personalcodeno #
- personas kods
- رمز تعريف عدد السكان
- رقم الخدمة العامة
- رقم التسجيل
- رقم الإيرادات
- رقم التأمين الاجتماعي
- رقم الضمان الاجتماعي
- رمز ضريبة الولاية
- رقم ملف الضريبة
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- رقم


## <a name="latvia-physical-addresses"></a>العناوين الفعلية في لاتفيا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من لاتفيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="liechtenstein-physical-addresses"></a>عناوين ليشتنشتاين الفعلية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من ليشتنشتاين. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT. 

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="lifestyles-that-relate-to-medical-conditions"></a>أنماط الحياة المتعلقة بالشروط الطبية

يكشف هذا الكيان المسمى غير المفبرك عن المصطلحات المتعلقة بأنماط الحياة التي قد تؤدي إلى حالة طبية، مثل *التبغ*. فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال


## <a name="lithuania-drivers-license-number"></a>رقم ترخيص القيادة في ليتوانيا

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_lithuania_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_lithuania_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver لا s_license_number

- vairuotojo pažym،jimas
- الأرقام vairuotojo pažym،jimo
- vairuotojo pažymموجjimo numeriai


## <a name="lithuania-personal-code"></a>الرمز الشخصي لليتوانيا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

11 رقما بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

11 رقما بدون مسافات ومواريخ:

- رقم واحد (1-6) يتطابق مع نوع الشخص و قرن ميلاده
- ستة أرقام تتطابق مع تاريخ الميلاد (YYMMDD)
- ثلاثة أرقام تتطابق مع الرقم التسلسلي من تاريخ الميلاد
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_lithuania_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_lithuania_eu_tax_file_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_lithuania_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- رقم خدمة العملاء
- mokesčių الما بعد
- mokesčių identifikavimas
- mokesčių identifikavimo numeris
- mokesčių الأرقام
- رقم التعريف الوطني
- الرمز الشخصي
- رمز رقمي شخصي
- piliečio paslaugos numeris
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- unikalus identifikavimo kodas
- الأرقام unikalus identifikavimo
- رقم تعريف فريد
- رقم الهوية الفريدة
- uniqueidentityno #


## <a name="lithuania-physical-addresses"></a>العناوين الفعلية في ليتوانيا

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من ليتوانيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="lithuania-passport-number"></a>رقم جواز السفر الليتواني

### <a name="format"></a>تنسيق

ثمانية أرقام أو أحرف بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

ثمانية أرقام أو أحرف (لا تتحسس حالة الأحرف)

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_lithuania_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_lithuania_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date3` على التاريخ بتنسيق العثور على DD MM YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_lithuania_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_lithuania_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- الأرقام paso
- paso numeriai
- paso nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="luxemburg-drivers-license-number"></a>رقم ترخيص برنامج تشغيل Luxemburg

### <a name="format"></a>تنسيق

ستة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_luxemburg_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_luxemburg_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver لا s_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>رقم التعريف الوطني ل Luxemburg (الأشخاص الطبيعيون)

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

13 رقما بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

13 رقما:

- 11 رقما
- رقمان للتحقق

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_luxemburg_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_luxemburg_eu_national_id_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_luxemburg_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- eindeutige id
- eindeutige id-nummer
- eindeutigeid #
- id personnelle
- idpersonnelle #
- idpersonnelle
- التعليمات البرمجية الفردية
- الم id الفردي
- تعريف فردي
- هوية فردية
- numéro d'identification الموظفين
- الم id الشخصي
- التعريف الشخصي
- الهوية الشخصية
- personalidno #
- personalidnumber #
- persönliche identifikationsnummer
- الم id الفريد
- هوية فريدة
- uniqueidkey #


## <a name="luxemburg-national-identification-number-non-natural-persons"></a>رقم التعريف الوطني ل Luxemburg (الأشخاص غير الطبيعيين)

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>النمط

11 رقما

- رقمان
- مسافة اختيارية
- ثلاثة أرقام
- مسافة اختيارية
- ثلاثة أرقام
- مسافة اختيارية
- رقمان
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_luxemburg_eu_tax_file_number_non_natural` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_luxemburg_eu_tax_file_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_luxemburg_eu_tax_file_number_non_natural` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- étain non
- étain #
- identifiant d'impôt
- تعريف ضريبة luxembourgkatiounsnummer
- numéro d'étain
- numéro d'identification fiscal luxembourgeois
- numéro d'identification fiscale
- الضمان الاجتماعي
- sozialunterstützung
- sozialversécherung
- sozialversicherungsausweis
- steier id
- steier identifikatiounsnummer
- steier nummer
- id steuer
- steueridentifikationsnummer
- steuernummer
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- zinn #
- zinn
- zinnzahl


## <a name="luxemburg-passport-number"></a>رقم جواز سفر للوكسمبورج

### <a name="format"></a>تنسيق

ثمانية أرقام أو أحرف بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

ثمانية أرقام أو أحرف (لا تتحسس حالة الأحرف)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_luxemburg_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_luxemburg_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date3` على التاريخ بتنسيق العثور على DD MM YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_luxemburg_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_luxemburg_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- luxembourg pass
- منفذ مرور لكسمبورغ
- جواز سفر لكسمبورغ
- no de passeport
- no-reisepass
- nr-reisepass
- numéro de passeport
- pass net
- تمرير nr
- passnummer
- passeport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="luxemburg-physical-addresses"></a>عناوين Luxemburg الفعلية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من Luxemburg. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="malaysia-identification-card-number"></a>رقم بطاقة تعريف ماليزيا

### <a name="format"></a>تنسيق

12 رقما تحتوي على الوافات الاختيارية

### <a name="pattern"></a>النمط

12 رقما:
- ستة أرقام بتنسيق YYMMDD، وهو تاريخ الميلاد
- شرطة (اختياري)
- رمز مكان الميلاد من حرفين
- شرطة (اختياري)
- ثلاثة أرقام عشوائية
- رمز الجنس المكون من رقم واحد

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_malaysia_id_card_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_malaysia_id_card_number كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- بطاقة تطبيق رقمية
- i/c
- i/c no
- ic
- ic no
- بطاقة الم id
- بطاقة التعريف
- بطاقة الهوية
- k/p
- k/p no
- kad akوا diri
- kad aplikasi digital
- kad pengenalan malaysia
- kp
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


## <a name="malta-drivers-license-number"></a>رقم ترخيص القيادة المالطية

### <a name="format"></a>تنسيق

تركيبة من حرفين وستة أرقام في النمط المحدد

### <a name="pattern"></a>النمط

تركيبة من حرفين وستة أرقام:

- حرفان (رقمان أو أحرف، وليسا حساسين للقضية)
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_malta_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_malta_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver لا s_license_number

- liċenzja tas-liċenzja
- liċenzji tas-eq


## <a name="malta-identity-card-number"></a>رقم بطاقة هوية مالطا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

سبعة أرقام متبوع حرف واحد

### <a name="pattern"></a>النمط

سبعة أرقام متبوع ب حرف واحد:

- سبعة أرقام
- حرف واحد في "M، G، A، P، L، H، B، Z" (حالة غير حساسة)

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_malta_eu_national_id_card` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_malta_eu_national_id_card` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- يعثر التعبير  `Regex_malta_eu_national_id_card` العادي على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- رقم خدمة العملاء
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi رقمية personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- رمز رقمي شخصي
- رقم تعريف فريد
- رقم الهوية الفريدة
- uniqueidentityno #


## <a name="malta-passport-number"></a>رقم جواز السفر المالطية

### <a name="format"></a>تنسيق

سبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_malta_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_malta_eu_passport_number` تم العثور عليها.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_malta_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_malta_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="malta-physical-addresses"></a>العناوين الفعلية المالطية

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من مالطا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="malta-tax-identification-number"></a>رقم تعريف الضريبة المالطية

### <a name="format"></a>تنسيق

بالنسبة إلى المالطية:
- سبعة أرقام ورسالة واحدة في النمط المحدد

غير المالطية والكيانات المالطية:
- تسعة أرقام

### <a name="pattern"></a>النمط

الوطنية المالطية: سبعة أرقام ورسالة واحدة

- سبعة أرقام
- حرف واحد (لا يتحسس حالة الحروف)

الكيانات المالطية وغير المالطية: تسعة أرقام

- تسعة أرقام

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- regex  `Regex_malta_eu_tax_file_number`  أو `Regex_malta_eu_tax_file_number_non_maltese_national` البحث عن محتوى يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_malta_eu_tax_file_number` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- regex  `Regex_malta_eu_tax_file_number` أو `Regex_malta_eu_tax_file_number_non_maltese_national` البحث عن محتوى يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- رقم خدمة العملاء
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi رقمية personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- رمز رقمي شخصي
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- رقم تعريف فريد
- رقم الهوية الفريدة
- uniqueidentityno #

## <a name="medical-specialities"></a>التخصصات الطبية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن المصطلحات ذات الصلة بالتخصصات الطبية، مثل *علم الأدمة*.  فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال

## <a name="medicare-beneficiary-identifier-mbi-card"></a>بطاقة معرف المستفيد من الرعاية الصحية (MBI)

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 11 حرفا

### <a name="pattern"></a>النمط

- رقم واحد بين 1 إلى 9
- حرف واحد باستثناء S و L و O و I و B و Z
- رقم واحد أو حرف باستثناء S و L و O و I و B و Z
- رقم واحد
- الوابل الاختياري
- حرف واحد باستثناء S و L و O و I و B و Z
- رقم واحد أو حرف باستثناء S و L و O و I و B و Z
- رقم واحد
- الوابل الاختياري
- حرفان باستثناء S و L و O و I و B و Z
- رقمان

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_mbi_card` العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keyword_mbi_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_mbi_card` العادي على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- mbi
- mbi #
- منتفعة من برنامج العمل #
- معرف برنامج الرعاية الصحية للمستفيدين
- الرعاية الصحية غير المنتفعة
- رقم المستفيد من الرعاية الصحية
- منتفعة من برنامج العمل #


## <a name="mexico-unique-population-registry-code-curp"></a>رمز السجل الفريد للسكان (CURP) في المكسيك

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 18 حرفا

### <a name="pattern"></a>النمط

- أربعة أحرف (حالة غير حساسة)
- ستة أرقام تشير إلى تاريخ صحيح
- حرف - H/h أو M/m
- حرفان يشيران إلى رمز ولاية مكسيكية صالح
- ثلاثة أحرف
- حرف واحد أو رقم واحد
- رقم واحد

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_mexico_population_registry_code` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keyword_mexico_population_registry_code` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_mexico_population_registry_code` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- كلافي Única de كارتومينو دي Población
- Clave Unica de Registro de Poblacion
- رمز تسجيل عدد السكان الفريد 
- رمز عدد السكان الفريد
- CURP
- الم ID الشخصي
- الم ID فريد
- personalid
- personalidnumber
- uniqueidkey
- uniqueidnumber
- clave única
- التصفيق unica
- clave Personal Identidad
- Identidad Clave الشخصي
- ClaveÚnica
- claveunica
- clavepersonalIdentidad


## <a name="netherlands-citizens-service-bsn-number"></a>رقم خدمة شركة هولندا (BSN)

### <a name="format"></a>تنسيق

ثمانية أو تسعة أرقام تحتوي على مسافات اختيارية

### <a name="pattern"></a>النمط

ثمانية تسعة أرقام:
- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- رقمان وثلاثة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_netherlands_bsn المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_netherlands_bsn كلمة أساسية.
- يتم تمرير الاختبارات.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- bsn #
- bsn
- icenummer
- رقم خدمة العملاء
- رقم الشخص
- الرقم الشخصي
- رمز رقمي شخصي
- رقم مرتبط بالشخص
- persoonlijk nummer
- persoonlijke numerieke code
- persoonsgebonden
- persoonsnummer
- sociaal-fiscaal nummer
- رقم اجتماعي-مالي
- sofi
- sofinummer
- معرف uniekcatienummer
- uniek identiteitsnummer
- رقم تعريف فريد
- رقم الهوية الفريدة
- uniqueidentityno #


## <a name="netherlands-drivers-license-number"></a>رقم ترخيص القيادة في هولندا

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

10 أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_netherlands_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_netherlands_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver لا s_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers


## <a name="netherlands-passport-number"></a>رقم جواز السفر الهولندي

### <a name="format"></a>تنسيق

تسعة أحرف أو أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

تسعة أحرف أو أرقام

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_netherlands_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_netherlands_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_netherlands_eu_passport_date` على التاريخ بتنسيق DD MMM/MMM YYYY (مثال - 26 MAA/MAR 2012)

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_netherlands_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_netherlands_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- paspoort nummer
- paspoortnummers
- paspoortnummer
- paspoort nr


## <a name="netherlands-physical-addresses"></a>العناوين الفعلية لهولندا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من هولندا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="netherlands-tax-identification-number"></a>رقم تعريف الضريبة في هولندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_netherlands_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_netherlands_eu_tax_file_number` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر  `Func_netherlands_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- تعريف ضريبة hollânske
- hulandes impuesto id number
- hulandes impuesto identification
- تحديد المكبس identificatienummer
- identificatienummer van belasting
- رقم التعريف الخاص بالدفع
- رقم الاتحل
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- تعريف الضريبة في هولندا
- تعريف الضريبة في هولندا
- تين هولندا
- علبة تين الهولندية
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- tal لتحديد الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- الضريبة tal
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="netherlands-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في هولندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

نمط ألفا رقمي من 14 حرفا

### <a name="pattern"></a>النمط

النمط alphanumeric من 14 حرفا:

- N أو n
- L أو l
- مسافة اختيارية أو نقطة أو الوابلة
- تسعة أرقام
- مسافة اختيارية أو نقطة أو الوابلة
- B أو b
- رقمان

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_netherlands_value_added_tax_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_netherlands_value_added_tax_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_netherlands_value_added_tax_number المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- رقم ضريبة القيمة المضافة
- لا لضريبة القيمة المضافة
- ضريبة القيمة المضافة #
- ضريبة wearde tafoege
- btw nûmer
- btw-nummer


## <a name="new-zealand-bank-account-number"></a>رقم الحساب البنكي في نيوزيلندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

نمط من 14 رقما إلى 16 رقما مع معين اختياري

### <a name="pattern"></a>النمط

نمط من 14 رقما إلى 16 رقما مع معين اختياري:

- رقمان
- وفاتمة اختيارية أو مسافة اختيارية
- من ثلاثة إلى أربعة أرقام
- وفاتمة اختيارية أو مسافة اختيارية
- سبعة أرقام
- وفاتمة اختيارية أو مسافة اختيارية
- رقمان إلى ثلاثة أرقام
- الفاتة خيارات أو مسافة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_new_zealand_bank_account_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_new_zealand_bank_account_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_new_zealand_bank_account_number المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- رقم الحساب
- حساب بنكي
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr


## <a name="new-zealand-drivers-license-number"></a>رقم ترخيص القيادة في نيوزيلندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

النمط alphanumeric لثمانية أحرف

### <a name="pattern"></a>النمط

النمط alphanumeric لثمانية أحرف

- حرفان
- ستة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_newzealand_driver_license_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_newzealand_driver_license_number كلمة أساسية.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_newzealand_driver_license_number المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslicence
- driverslicences
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- driverlic #
- driverlics #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج تشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة الدولية
- تراخيص القيادة الدولية
- nz اقتران السيارات
- اتحاد السيارات في نيوزيلندا


## <a name="new-zealand-inland-revenue-number"></a>رقم الإيرادات الداخلية في نيوزيلندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

ثمانية أو تسعة أرقام بمواد اختيارية

### <a name="pattern"></a>النمط

ثمانية أو تسعة أرقام بمواد اختيارية

- رقمان أو ثلاثة أرقام
- مسافة اختيارية أو الوابلة الاختيارية
- ثلاثة أرقام
- مسافة اختيارية أو الوابلة الاختيارية
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_new_zealand_inland_revenue_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_new_zealand_inland_revenue_number كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_new_zealand_inland_revenue_number المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- ird no.
- ird no #
- nz ird
- ird في نيوزيلندا
- رقم ird
- رقم الإيرادات الداخلية


## <a name="new-zealand-ministry-of-health-number"></a>رقم وزارة الصحة في نيوزيلندا

### <a name="format"></a>تنسيق

ثلاثة أحرف وأربعة أرقام

### <a name="pattern"></a>النمط

- ثلاثة أحرف (لا تتحسس حالة الأحرف) باستثناء "I" و"O"
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_new_zealand_ministry_of_health_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_nz_terms كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_new_zealand_ministry_of_health_number المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- نيوزيلندا
- مؤشر الصحة الوطنية
- NHI #
- مؤشر الصحة الوطنية #


## <a name="new-zealand-physical-addresses"></a>العناوين الفعلية في نيوزيلندا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من نيوزيلندا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="new-zealand-social-welfare-number"></a>رقم الرعاية الاجتماعية في نيوزيلندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>النمط

تسعة أرقام

- ثلاثة أرقام
- الوابلة الاختيارية
- ثلاثة أرقام
- الوابلة الاختيارية
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_newzealand_social_welfare_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_newzealand_social_welfare_number.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_newzealand_social_welfare_number على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- الرعاية الاجتماعية #
- الرعاية الاجتماعية #
- رقم الرعاية الاجتماعية.
- رقم الرعاية الاجتماعية
- swn #


## <a name="norway-identification-number"></a>رقم تعريف النرويج

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>النمط

11 رقما:
- ستة أرقام بتنسيق DDMMYY، وهو تاريخ الميلاد
- رقم فردي من ثلاثة أرقام
- رقمان للتحقق

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_norway_id_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_norway_id_number كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_norway_id_numbe المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- رقم التعريف الشخصي
- رقم الم ID النرويجي
- رقم الم ID
- تحديد الهوية
- Personnummer
- Fødselsnummer


## <a name="norway-physical-addresses"></a>العناوين الفعلية في النرويج

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من النرويج. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="philippines-unified-multi-purpose-identification-number"></a>رقم تعريف متعدد الأغراض موحد للفلبين

### <a name="format"></a>تنسيق

12 رقما مفصولة بالفاتفات

### <a name="pattern"></a>النمط

12 رقما:
- أربعة أرقام
- الواهة
- سبعة أرقام
- الواهة
- رقم واحد

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_philippines_unified_id العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_philippines_id كلمة أساسية.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- الم ID الموحد متعدد الأغراض
- UMID
- بطاقة الهوية
- Pinag-isang Multi-Layunin ID


## <a name="poland-drivers-license-number"></a>رقم ترخيص القيادة في بولندا

### <a name="format"></a>تنسيق

14 رقما تحتوي على شرطتين مائلتين للأمام

### <a name="pattern"></a>النمط

14 رقما ومائلين للأمام:

- خمسة أرقام
- الشرطة المائلة للأمام
- رقمان
- الشرطة المائلة للأمام
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_poland_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_poland_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver لا s_license_number

- prawo jazdy
- prawa jazdy


## <a name="poland-identity-card"></a>بطاقة هوية بولندا

### <a name="format"></a>تنسيق

ثلاثة أحرف وستة أرقام

### <a name="pattern"></a>النمط

ثلاثة أحرف (لا تتحسس حالة الأحرف) متبوع بستة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_polish_national_id على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_polish_national_id_passport_number كلمة أساسية.
- يتم تمرير الاختبارات.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa i nr dowodu tośsamości
- Dowód Tośsamości
- dow. os.


## <a name="poland-national-id-pesel"></a>الم ID الوطنية البولندية (PESEL)

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>النمط

- ستة أرقام تمثل تاريخ الميلاد بتنسيق YYMMDD
- أربعة أرقام
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_pesel_identification_number على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_pesel_identification_number كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_pesel_identification_number على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osobisty
- dowódosobisty
- niepowtarzalny numer
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- رقم identyfikacyjny
- pesel
- tośsamości narodowej


## <a name="poland-passport-number"></a>رقم جواز السفر البولندي

يتم تضمين كيان نوع المعلومات الحساس هذا في نوع المعلومات الحساسة لرقم جواز السفر في الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

حرفان وسبعة أرقام

### <a name="pattern"></a>النمط

حرفان (لا يتحسسان حالة الأحرف) متبوعين بسبعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_polish_passport_number_v2` الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_polish_national_passport_number` تم العثور عليها.
- تم العثور على كلمة أساسية `Keywords_eu_passport_date` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_polish_passport_number_v2` الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_polish_national_passport_number` تم العثور عليها.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر `Func_polish_passport_number_v2` الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- numer paszportu
- numery paszportów
- numery paszportowe
- nr paszportu
- nr. paszportu
- nr paszportów
- منفذ مرور n°
- passeport n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="poland-physical-addresses"></a>العناوين الفعلية في بولندا

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من بولندا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="poland-regon-number"></a>رقم REGON في بولندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

رقم من 9 أرقام أو 14 رقما

### <a name="pattern"></a>النمط

رقم من تسعة أرقام أو 14 رقما:

- تسعة أرقام أو
- تسعة أرقام
- الواف
- خمسة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_polish_regon_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_polish_regon_number.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر الدالة Func_polish_regon_number المحتوى الذي يتطابق مع النمط.

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
### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- regon id
- رقم إحصائي
- الم id الإحصائي
- لا إحصائي
- رقم إعادة
- regonid #
- regonno #
- اسم الشركة
- companyid #
- companyidno #
- numer statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #


## <a name="poland-tax-identification-number"></a>رقم تعريف الضريبة في بولندا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

11 رقما بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

11 رقما

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_poland_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_poland_eu_tax_file_number` من.


```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- nip #
- nip
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- معرّف ضريبة القيمة المضافة #
- معرّف ضريبة القيمة المضافة
- لا لضريبة القيمة المضافة
- رقم ضريبة القيمة المضافة
- vatid #
- vatid
- vatno #


## <a name="portugal-citizen-card-number"></a>رقم بطاقة المهى البرتغالية

### <a name="format"></a>تنسيق

ثمانية أرقام

### <a name="pattern"></a>النمط

ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير العادي Regex_portugal_citizen_card على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_portugal_citizen_card كلمة أساسية.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilhete de identidade
- cartão de cidadão
- بطاقة العمل
- رقم المستند
- documento de identificação
- رقم الم id
- تحديد لا
- رقم التعريف
- بطاقة الهوية لا
- رقم بطاقة الهوية
- بطاقة الهوية الوطنية
- nic
- número bi de portugal
- número de identificação civil
- número de identificação Fiscal
- número do documento
- الرقم bi للبرتغال


## <a name="portugal-drivers-license-number"></a>رقم ترخيص القيادة في البرتغال

### <a name="format"></a>تنسيق

نمطان - حرفان متبوعان بأحرف خاصة من 5 إلى 8 أرقام

### <a name="pattern"></a>النمط

النمط 1: حرفان متبوعان ب 5/6 بأحرف خاصة:
- حرفان (لا يتحسس حالة الأحرف)
- الواهة
- خمسة أو ستة أرقام
- مسافة
- رقم واحد

النمط 2: حرف واحد متبوع ب 6/8 أرقام بأحرف خاصة:
- حرف واحد (لا يتحسس حالة الحروف)
- الواهة
- ستة أو ثمانية أرقام
- مسافة
- رقم واحد


### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_portugal_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_portugal_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver لا s_license_number

- carteira de motorista
- carteira motorista
- carteira de habilitação
- carteira habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugal
- carta de condução


## <a name="portugal-passport-number"></a>رقم جواز سفر البرتغال

### <a name="format"></a>تنسيق

حرف واحد متبوع بستة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرف واحد متبوع بستة أرقام:

- حرف واحد (لا يتحسس حالة الحروف)
- ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_portugal_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_portugal_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_portugal_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_portugal_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do passaporte
- جواز سفر برتغالي
- منفذ المرور البرتغالي
- البرتغالية passaporte
- passaporte nº
- passeport nº
- números de passaporte
- البرتغالية
- número passaporte
- números passaporte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="portugal-physical-addresses"></a>العناوين الفعلية للبرتغال

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من البرتغال. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="portugal-tax-identification-number"></a>رقم تعريف الضريبة في البرتغال

### <a name="format"></a>تنسيق

تسعة أرقام مع مسافات اختيارية

### <a name="pattern"></a>النمط

- ثلاثة أرقام
- مسافة اختيارية
- ثلاثة أرقام
- مسافة اختيارية
- ثلاثة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_portugal_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_portugal_eu_tax_file_number` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر  `Func_portugal_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- cpf #
- cpf
- nif #
- nif
- número de identificação fisca
- numero Fiscal
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="romania-drivers-license-number"></a>رقم ترخيص القيادة في رومانيا

### <a name="format"></a>تنسيق

حرف واحد متبوع بثمانية أرقام

### <a name="pattern"></a>النمط

حرف واحد متبوع بثمانية أرقام:
- حرف واحد (لا يتحسس حالة الحروف) أو رقم
- ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_romania_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_romania_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver لا s_license_number

- permis deهم
- permisului deهمة
- permisuluiهمة
- permisele deهمة
- permiseleهمية
- permisهمي


## <a name="romania-passport-number"></a>رقم جواز سفر رومانيا

### <a name="format"></a>تنسيق

ثمانية أو تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

ثمانية أو تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_romania_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_romania_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_romania_eu_passport_date` على التاريخ بتنسيق DD MMM/MMM YY (مثال- 01 فبراير/فبراير 10) `Keywords_eu_passport_date` أو تم العثور على كلمة أساسية من

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_romania_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_romania_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numهمrul pașaportului numarul pasaportului numerele pașaportului Pașaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="romania-personal-numeric-code-cnp"></a>رمز رومانيا الشخصي (CNP)

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

13 رقما بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

- رقم واحد من 1-9
- ستة أرقام تمثل تاريخ الميلاد (YYMMDD)
- رقمان، يمكن أن يكونا 01-52 أو 99
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_romania_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_romania_eu_national_id_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_romania_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- cnp #
- cnp
- cod identificare personal
- cod رقمية شخصية
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscalراز nr #
- id-ul taxei
- رقم التأمين
- التأمينر #
- الم id الوطنية #
- الم id الوطنية
- رقم التعريف الوطني
- numهمr identificare personal
- هوية număr
- număr personal unic
- număridentitate #
- număridentitate
- numهمrpersonalunic #
- numهمrpersonalunic
- numضرو de identificare fiscalراز
- numهمrul de identificare fiscalراز
- رمز رقمي شخصي
- تثبيت #
- تثبيت
- ملف الضريبة لا
- رقم ملف الضريبة
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #
- رقم تعريف فريد
- رقم الهوية الفريدة
- uniqueidentityno #
- uniqueidentityno


## <a name="romania-physical-addresses"></a>العناوين الفعلية لرومانيا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من رومانيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="russia-passport-number-domestic"></a>رقم جواز السفر الروسي المحلي

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

رقم من 10 أرقام

### <a name="pattern"></a>النمط

رقم من 10 أرقام:

- رقمان
- مسافة اختيارية أو الوابلة الاختيارية
- رقمان
- مسافة اختيارية
- ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر Regex_Russian_Passport_Number_Domestic regex على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Russian_Passport_Number كلمة أساسية.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- رقم جواز السفر
- جواز السفر لا
- جواز السفر #
- رقم جواز السفر
- passportno #
- passportnumber #
- паспорт нет
- пасрорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- пасрортid #
- номер паспорта
- номерпаспорта #


## <a name="russia-passport-number-international"></a>رقم جواز سفر روسيا دولي

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

رقم من تسعة أرقام

### <a name="pattern"></a>النمط

رقم من تسعة أرقام:

- رقمان
- مسافة اختيارية أو الوابلة الاختيارية
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر Regex_Russian_Passport_Number_International regex على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Russian_Passport_Number كلمة أساسية.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- رقم جواز السفر
- جواز السفر لا
- جواز السفر #
- رقم جواز السفر
- passportno #
- passportnumber #
- паспорт нет
- пасрорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- пасрортid #
- номер паспорта
- номерпаспорта #


## <a name="saudi-arabia-national-id"></a>الم ID الوطنية للمملكة العربية السعودية

### <a name="format"></a>تنسيق

10 أرقام

### <a name="pattern"></a>النمط

10 أرقام متتالية

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_saudi_arabia_national_id العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_saudi_arabia_national_id كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- بطاقة التعريف
- رقم بطاقة I
- رقم الم ID
- الوطنية الهوية بطاقة رقم


## <a name="singapore-national-registration-identity-card-nric-number"></a>رقم بطاقة هوية التسجيل الوطنية (NRIC) في سنغافورة

### <a name="format"></a>تنسيق

تسعة أحرف ورقم

### <a name="pattern"></a>النمط

- تسعة أحرف ورقمية:
- الحرف "F" أو "G" أو "S" أو "T" (ليس حساسا للقضية)
- سبعة أرقام
- خانة الاختيار الأبجدية

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_singapore_nric العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_singapore_nric كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_singapore_nric العادي على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- بطاقة هوية التسجيل الوطنية
- رقم بطاقة الهوية
- NRIC
- IC
- رقم التعريف الخارجي
- FIN
- 身份证
- 身份證


## <a name="slovakia-drivers-license-number"></a>رقم ترخيص القيادة في سلوفاكيا

### <a name="format"></a>تنسيق

حرف واحد متبوع بسبعة أرقام

### <a name="pattern"></a>النمط

حرف واحد متبوع بسبعة أرقام

- حرف واحد (لا يتحسس حالة الحروف) أو رقم
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_slovakia_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_slovakia_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver لا s_license_number

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičských preukazov


## <a name="slovakia-passport-number"></a>رقم جواز السفر السلوفاكي

### <a name="format"></a>تنسيق

رقم واحد أو حرف متبوع بسبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

رقم واحد أو حرف (لا يتحسس حالة الحروف) متبوع بسبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_slovakia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_slovakia_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_slovakia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_slovakia_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- číslo pasu
- čísla pasov
- pas č.
- Passeport n°
- n° Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="slovakia-personal-number"></a>الرقم الشخصي في سلوفاكيا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

تسعة أو 10 أرقام تحتوي على مبللة اختيارية

### <a name="pattern"></a>النمط

- ستة أرقام تمثل تاريخ الميلاد
- الشرطة المائلة الاختيارية (/)
- ثلاثة أرقام
- خانة اختيارية واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_slovakia_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_slovakia_eu_national_id_card` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر  `Func_slovakia_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- رقم الميلاد
- číslo národnej identifikačnej karty
- číslo občianského preukazu
- daňové číslo
- رقم الم id
- تحديد لا
- رقم التعريف
- identifikačná karta č
- identifikačné číslo
- بطاقة الهوية لا
- رقم بطاقة الهوية
- národná identifikačná značka č
- الرقم الوطني
- nationalnumber #
- nemzeti személyazonosító igazolvány
- personalidnumber #
- rč
- cislo
- روني číslo
- رقم الضمان الاجتماعي
- ssn #
- ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyázolvány szám
- ملف الضريبة لا
- رقم ملف الضريبة
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="slovakia-physical-addresses"></a>العناوين الفعلية في سلوفاكيا

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من سلوفاكيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="slovenia-drivers-license-number"></a>رقم ترخيص القيادة في سلوفينيا

### <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومواريخ

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_slovenia_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_slovenia_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver لا s_license_number

- vozniško dovoljenje
- ترخيص vozniška številka
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj


## <a name="slovenia-passport-number"></a>رقم جواز سفر سلوفينيا

### <a name="format"></a>تنسيق

حرفان متبوعان بسبعة أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

حرفان متبوعان بسبعة أرقام:

- الحرف "P"
- حرف واحد حرف علوي
- سبعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_slovenia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_slovenia_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_eu_passport_date1` على التاريخ بتنسيق يتم العثور على DD.MM.YYYY أو كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_slovenia_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_slovenia_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- قائمة potni #
- datum rojstva
- قائمة potni
- številke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="slovenia-physical-addresses"></a>العناوين الفعلية لسلوفينيا

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من سلوفينيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="slovenia-tax-identification-number"></a>رقم تعريف الضريبة في سلوفينيا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

- رقم واحد من 1-9
- ستة أرقام
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_slovenia_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_slovenia_eu_tax_file_number` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر  `Func_slovenia_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- davčna številka
- identifikacijska številka davka
- številka davčne datoteke
- ملف الضريبة لا
- رقم ملف الضريبة
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="slovenia-unique-master-citizen-number"></a>رقم سلوفينيا الرئيسي الفريد

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

13 رقما بدون مسافات أو مواريخ

### <a name="pattern"></a>النمط

13 رقما في النمط المحدد:

- سبعة أرقام تتطابق مع تاريخ الميلاد (DDMMLLL) حيث تتطابق "LLL" مع الأرقام الثلاثة الأخيرة من سنة الميلاد
- رقمان يتطابقان مع منطقة الميلاد "50"
- ثلاثة أرقام تتوافق مع مجموعة من الجنس والرقم التسلسلي للأشخاص الذين يولدون في نفس اليوم. 000-499 للذكر و500-999 للأنثى.
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_slovenia_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_slovenia_eu_national_id_card` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_slovenia_eu_national_id_card` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka gavnega dršavljana
- emšo
- enotna maticna številka obcana
- بطاقة الم id
- رقم التعريف
- identifikacijska številka
- بطاقة الهوية
- nacionalna id
- قائمة nacionalni potni
- الم id الوطنية
- osebna izkaznica
- osebni koda
- osebni ne
- osebni številka
- الرمز الشخصي
- الرقم الشخصي
- رمز رقمي شخصي
- številka dršavljana
- رقم فريد لمهة العمل
- رقم الم id الفريد
- رقم الهوية الفريدة
- رقم المهى الرئيسي الفريد
- رقم التسجيل الفريد
- uniqueidentityno #
- uniqueidentityno #


## <a name="south-africa-identification-number"></a>رقم تعريف جنوب أفريقيا

### <a name="format"></a>تنسيق

13 رقما قد تحتوي على مسافات

### <a name="pattern"></a>النمط

13 رقما:
- ستة أرقام بتنسيق YYMMDD، وهو تاريخ الميلاد
- أربعة أرقام
- مؤشر مواطنة من رقم واحد
- الرقم "8" أو "9"
- رقم واحد، وهو رقم شيكوم

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_south_africa_identification_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_south_africa_identification_number كلمة أساسية.
- يتم تمرير الاختبارات.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- بطاقة الهوية
- الم ID
- تحديد الهوية


## <a name="south-korea-resident-registration-number"></a>رقم التسجيل المقيم في كوريا الجنوبية

### <a name="format"></a>تنسيق

13 رقما تحتوي على الفوسفات

### <a name="pattern"></a>النمط

13 رقما:
- ستة أرقام بتنسيق YYMMDD، وهو تاريخ الميلاد
- الواهة
- رقم واحد يحدده القرن والجنس
- رمز منطقة الميلاد المكون من أربعة أرقام
- رقم واحد يستخدم للتمييز بين الأشخاص الذين تتطابق الأرقام السابقة معهم
- رقم خانة الاختيار.

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_south_korea_resident_number المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_south_korea_resident_number كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_south_korea_resident_number المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- بطاقة الهوية الوطنية
- رقم تسجيل المهى
- Jumin deungnok beonho
- RRN
- 주민등록번호


## <a name="spain-dni"></a>أسبانيا DNI

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

ثمانية أرقام متبوع ب حرف واحد

### <a name="pattern"></a>النمط

سبعة أرقام متبوع ب حرف واحد

- ثمانية أرقام
- مسافة اختيارية أو الفاتف
- حرف شيك واحد (لا يتحسس حالة الحروف)

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة  `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` تعثر على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_spain_eu_national_id_card"` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة  `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` تعثر على المحتوى الذي يتطابق مع النمط.


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

### <a name="keywords"></a>الكلمات الأساسية

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
- nationalid #
- nationalidno #
- nie #
- nie
- nienúmero #
- número de identificación
- número nacional identidad
- رقم التعريف الشخصي
- الهوية الشخصية لا
- رقم الهوية الفريدة
- فريد #


## <a name="spain-drivers-license-number"></a>رقم ترخيص القيادة في إسبانيا

### <a name="format"></a>تنسيق

ثمانية أرقام متبوع ب حرف واحد

### <a name="pattern"></a>النمط

ثمانية أرقام متبوع ب حرف واحد:

- ثمانية أرقام
- رقم واحد أو حرف واحد (لا يتحسس حالة الحروف)

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة  `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` تعثر على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_spain_eu_driver's_license_number` تم العثور عليها.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة  `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` تعثر على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver لا s_license_number

- permiso deóción
- permisoón
- licencia deciair
- licencia
- permiso
- permiso de
- permisos deهم
- permisos
- carnet
- carnet de
- licencia de manejo
- licencia manejo


## <a name="spain-passport-number"></a>رقم جواز سفر إسبانيا

### <a name="format"></a>تنسيق

تركيبة من ثمانية أو تسعة أحرف من الأحرف و الأرقام بدون مسافات أو معادلات

### <a name="pattern"></a>النمط

تركيبة من ثمانية أو تسعة أحرف من الأحرف و الأرقام:

- رقمان أو حرفان
- رقم واحد أو حرف (اختياري)
- ستة أرقام

### <a name="checksum"></a>الاختبارات

غير قابل للتطبيق

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_spain_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_spain_eu_passport_number` تم العثور عليها.
- يعثر التعبير العادي `Regex_spain_eu_passport_date` على التاريخ بتنسيق العثور على DD-MM-YYYY أو كلمة أساسية `Keywords_eu_passport_date` من

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_spain_eu_passport_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_passport_number` أو `Keywords_spain_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta pasaporte
- número pasaporte
- españa pasaporte
- números de pasaporte
- número de pasaporte
- números pasaporte
- pasaporte no
- Passeport n°
- n° Passeport
- pasaporte no.
- pasaporte n°
- جواز سفر إسبانيا

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="spain-physical-addresses"></a>العناوين الفعلية لإسبانيا

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن الأنماط ذات الصلة بالمعالجة الفعلية من أسبانيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="spain-social-security-number-ssn"></a>رقم الضمان الاجتماعي (SSN) في إسبانيا


### <a name="format"></a>تنسيق

11-12 رقما

### <a name="pattern"></a>النمط

11-12 رقما:
- رقمان
- الشرطة المائلة للأمام (اختيارية)
- من سبعة إلى ثمانية أرقام
- الشرطة المائلة للأمام (اختيارية)
- رقمان

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_spanish_social_security_number المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.
- - تم العثور على كلمة أساسية  `Keywords_spain_eu_ssn_or_equivalent` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_spanish_social_security_number المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- ssn
- ssn #
- socialsecurityno
- لا الضمان الاجتماعي
- رقم الضمان الاجتماعي
- número de la seguridad social


## <a name="spain-tax-identification-number"></a>رقم تعريف الضريبة في إسبانيا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

سبعة أو ثمانية أرقام ورقم واحد أو حرفين في النمط المحدد

### <a name="pattern"></a>النمط

الأشخاص الطبيعيون الأسبانيون الذين معهم بطاقة هوية وطنية لإسبانيا:

- ثمانية أرقام
- حرف واحد حرف علوي (يتحسس حالة الحروف)

الإسبان غير المقيمين بدون بطاقة هوية وطنية لإسبانيا

- حرف واحد حرف علوي "L" (يتحسس حالة الحروف)
- سبعة أرقام
- حرف واحد حرف علوي (يتحسس حالة الحروف)

الإسبان المقيمون دون سن 14 سنة بدون بطاقة هوية وطنية لإسبانيا:

- حرف واحد حرف "K" (يتحسس حالة الحروف)
- سبعة أرقام
- حرف واحد حرف علوي (يتحسس حالة الحروف)

المقيمين في مكان ما باستخدام رقم تعريف "ناهز"

- حرف واحد حرف علوي هو "X" أو "Y" أو "Z" (مع حساسية حالة الحروف)
- سبعة أرقام
- حرف واحد حرف علوي (يتحسس حالة الحروف)

المقيمين بدون رقم تعريف "ناهز"

- حرف واحد حرف علوي هو "M" (مع حساسية حالة الحروف)
- سبعة أرقام
- حرف واحد حرف علوي (يتحسس حالة الحروف)

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة  `Func_spain_eu_tax_file_number` أو `Func_spain_eu_DL_and_NI_number_citizen` تعثر على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_spain_eu_tax_file_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- الدالة  `Func_spain_eu_tax_file_number` أو `Func_spain_eu_DL_and_NI_number_citizen` تعثر على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- cif
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación Fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- ملف الضريبة لا
- رقم ملف الضريبة
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="sql-server-connection-string"></a>SQL Server الاتصال

### <a name="format"></a>تنسيق

السلسلة "User Id" أو "User ID" أو "uid" أو "UserId" متبوع بالحروف السلاسل الموضحة في النمط أدناه.

### <a name="pattern"></a>النمط

- السلسلة "User Id" أو "User ID" أو "uid" أو "UserId"
- أي تركيبة تتراوح بين 1-200 حرف أو أحرف كبيرة أو أرقام أو رموز أو أحرف خاصة أو مسافات
- السلسلة "كلمة المرور" أو "pwd" حيث لا يسبق الحرف "pwd" حرفا صغيرة
- علامة المساواة (=)
- أي حرف ليس علامة دولار ($) أو رمز النسبة المئوية (٪)، أو أكبر من الرمز (>)، أو عند الرمز (@)، أو علامة الاقتباس (")، أو الفاتنقوة (;)، أو قوس كبير أيسار([)، أو قوس أيسار ({)
- أي تركيبة من 7 إلى 128 حرفا ليست فاتحه منقوصه (;) الشرطة المائلة للأمام (/) أو علامة الاقتباس (")
- فقامت بلعبة من ;) أو علامة اقتباس (")

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير CEP_Regex_SQLServerConnectionString العادي على المحتوى الذي يتطابق مع النمط.
- لم يتم العثور CEP_GlobalFilter كلمة أساسية من هذه الكلمة الأساسية.
- لا يعثر CEP_PasswordPlaceHolder العادي على محتوى يتطابق مع النمط.
- لا يعثر CEP_CommonExampleKeywords العادي على محتوى يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- بعض كلمة المرور
- somepassword
- secretPassword
- نموذج

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- كلمة المرور أو pwd متبوعة بمساحات من 0 إلى 2، وشارة المساواة (=)، ومساحات من 0 إلى 2، و علامة النجمة (*) -OR-
- كلمة المرور أو pwd متبوع ب:
    - علامة المساواة (=)
    - رمز أقل من (<)
    - أي تركيبة من 1-200 حرفا تكون أحرفا كبيرة أو صغيرة أو رقما أو شكلا من الرموز النجمية (*) أو اليسرى (-) أو التسطير (_) أو حرف whitespace
    - أكبر من الرمز (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

يعرف نوع المعلومات الحساس هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- contoso
- fabrikam
- northwind
- الحماية
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="surgical-procedures"></a>الإجراءات المهينة

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن المصطلحات ذات الصلة بالإجراءات العملية، مثل *ال إلحاق.*  فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال


## <a name="sweden-drivers-license-number"></a>رقم ترخيص القيادة في السويد

### <a name="format"></a>تنسيق

10 أرقام تحتوي على الفوسفات

### <a name="pattern"></a>النمط

10 أرقام تحتوي على الوامة:

- ستة أرقام
- الواهة
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير  `Regex_sweden_eu_driver's_license_number` العادي على المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من  `Keywords_eu_driver's_license_number` أو `Keywords_sweden_eu_driver's_license_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver لا s_license_number

- ajokortti
- permis deهم
- ajokortin numero
- kuljjat lic.
- drivere lic.
- körkort
- numهمrul permisului deهمة
-  שאָפער דערלויבעניש נומער
- förare lic.
-  דריווערס דערלויבעניש
- körkortsnummer


## <a name="sweden-national-id"></a>الم ID الوطنية في السويد

### <a name="format"></a>تنسيق

10 أو 12 رقما وماخر اختياري

### <a name="pattern"></a>النمط

10 أو 12 رقما وماخر اختياري:
- رقمان (اختياري)
- ستة أرقام بتنسيق التاريخ YYMMDD
- delimiter of "-" or "+" (اختياري)
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_swedish_national_identifier` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من `Keywords_swedish_national_identifier`
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_swedish_national_identifier` الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- الم id no
- رقم الم id
- الم id #
- تحديد لا
- رقم التعريف
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- مستند الهوية
- الهوية لا
- رقم الهوية
- id-nummer
- الم id الشخصي
- personnummer #
- personnummer
- skatteidentifikationsnummer


## <a name="sweden-passport-number"></a>رقم جواز سفر السويد

### <a name="format"></a>تنسيق

ثمانية أرقام

### <a name="pattern"></a>النمط

ثمانية أرقام متتالية

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- التعبير العادي Regex_sweden_passport_number البحث عن المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_sweden_passport` تم العثور عليها.
- يعثر التعبير العادي `Regex_sweden_eu_passport_date` على تاريخ بتنسيق DD MMM/MMM YY (01 يناير/يناير 12) `Keywords_eu_passport_date` أو يتم العثور على كلمة أساسية منه.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- التعبير العادي Regex_sweden_passport_number البحث عن المحتوى الذي يتطابق مع النمط.
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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- بطاقة تسجيل من قبل
- رسوم معالجة g3
- إدخال متعدد
- Numéro de passeport
- passeport n °
- passeport non
- منفذ التمرير #
- منفذ التمرير #
- passeportnon
- passeportn °
- passnummer
- تمرير nr
- sهمة فيزا
- تاشيرات s،
- إدخال واحد
- sverige pass
- متطلبات التأشيرات
- معالجة التأشيرات
- نوع التأشيرات

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية


## <a name="sweden-physical-addresses"></a>العناوين الفعلية في السويد

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من السويد. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="sweden-tax-identification-number"></a>رقم تعريف الضريبة في السويد

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

10 أرقام ورمز في النمط المحدد

### <a name="pattern"></a>النمط

10 أرقام ورمز:

- ستة أرقام تتطابق مع تاريخ الميلاد (YYMMDD)
- علامة ضافة أو علامة طرح
- ثلاثة أرقام تجعل رقم التعريف فريدا حيث:
  - بالنسبة إلى الأرقام التي تم إصدارها قبل عام 1990، يحدد الرقمان السابع والثامن مقاطعة الميلاد أو الأشخاص الذين يولدون في اجانب
  - يشير الرقم في الموضع التاسع إلى الجنس حسب فردي للذكر أو حتى للأنثى
- رقم خانة واحدة

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_sweden_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_sweden_eu_tax_file_number` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_sweden_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- رقم الم id الشخصي
- personnummer
- skatt id nummer
- تعريف skatt
- skattebetalarens identifikationsnummer
- sverige tin
- ملف الضريبة
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="swift-code"></a>رمز SWIFT

### <a name="format"></a>تنسيق

أربعة أحرف متبوعه ب 5-31 حرفا أو رقما

### <a name="pattern"></a>النمط

أربعة أحرف متبوعه ب 5-31 حرفا أو رقما:
- رمز بنكي من أربعة حرف (لا يتحسس حالة الحروف)
- مسافة اختيارية
- 4-28 حرفا أو رقما (رقم الحساب البنكي الأساسي (BBAN))
- مسافة اختيارية
- من حرف إلى ثلاثة أرقام (باقي BBAN)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_swift العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_swift كلمة أساسية.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_swift"></a>Keyword_swift

- مؤسسة دولية ل التوحيد القياسي 9362
- iso 9362
- iso9362
- swift #
- رمز swiftcode
- swiftnumber
- swiftroutingnumber
- رمز swift
- رقم swift #
- رقم التوجيه السريع
- رقم bic
- رمز bic
- bic #
- bic #
- رمز معرف البنك
- Internationale de normalisation 9362
- rapide #
- رمز SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- # <a name="bic"></a>BIC
- code identificateur de banque
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


## <a name="switzerland-physical-addresses"></a>العناوين الفعلية في سويسرا

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من سويسرا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="switzerland-ssn-ahv-number"></a>رقم SSN AHV في سويسرا

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

رقم من 13 رقما

### <a name="pattern"></a>النمط

الرقم المكون من 13 رقما:

- ثلاثة أرقام - 756
- نقطة اختيارية
- أربعة أرقام
- نقطة اختيارية
- أربعة أرقام
- نقطة اختيارية
- رقمان

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_swiss_social_security_number_ahv الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keywords_swiss_social_security_number_ahv كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_swiss_social_security_number_ahv الدالة على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- ahv
- ssn
- pid
- رقم التأمين
- personalidno #
- رقم الضمان الاجتماعي
- رقم الم id الشخصي
- رقم التعريف الشخصي.
- التأمين #
- uniqueidno #
- رقم التعريف الفريد.
- avs number
- الهوية الشخصية بدون versicherungsnummer
- identifikationsnummer
- einzigartige identität nicht
- sozialversicherungsnummer
- تعريف هوية العاملين
- numéro de sécurité sociale


## <a name="taiwan-national-identification-number"></a>رقم التعريف الوطني التايواني

### <a name="format"></a>تنسيق

حرف واحد (باللغة الإنجليزية) متبوع بتسعة أرقام

### <a name="pattern"></a>النمط

حرف واحد (باللغة الإنجليزية) متبوع بتسعة أرقام:
- حرف واحد (باللغة الإنجليزية، وليس حساسا للقضية)
- الرقم "1" أو "2"
- ثمانية أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_taiwanese_national_id المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_taiwanese_national_id كلمة أساسية.
- يتم تمرير الاختبارات.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_taiwanese_national_id المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

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


## <a name="taiwan-passport-number"></a>رقم جواز السفر التايواني

### <a name="format"></a>تنسيق

- رقم جواز السفر البيومتري: تسعة أرقام
- رقم جواز سفر غير حيوي: تسعة أرقام

### <a name="pattern"></a>النمط
رقم جواز السفر البيومتري:
- الحرف "3"
- ثمانية أرقام

رقم جواز السفر غير البيومتري:
- تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_taiwan_passport العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_taiwan_passport كلمة أساسية.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- رقم جواز سفر ROC
- رقم جواز السفر
- جواز السفر لا
- جواز السفر Num
- جواز السفر #
- 护照
- 中華民國護照
- Zhōnghuá Mínguó hùzhào


## <a name="taiwan-resident-certificate-arctarc-number"></a>رقم الشهادة المقيمة في تايوان (ARC/TARC)

### <a name="format"></a>تنسيق

10 أحرف ورقم

### <a name="pattern"></a>النمط

10 أحرف ورقم:
- حرفان (لا يتحسس حالة الأحرف)
- ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير العادي Regex_taiwan_resident_certificate على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_taiwan_resident_certificate كلمة أساسية.

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- شهادة المقيم
- المقيمة Cert
- المقيمة Cert.
- بطاقة التعريف
- شهادة مقيم في المنطقة
- ARC
- شهادة مقيم في منطقة تايوان
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證


## <a name="thai-population-identification-code"></a>رمز تحديد عدد السكان التايلاندية

### <a name="format"></a>تنسيق

13 رقما

### <a name="pattern"></a>النمط

13 رقما:
- الرقم الأول ليس صفرا أو تسعة
- 12 رقما

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_Thai_Citizen_Id المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Thai_Citizen_Id كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_Thai_Citizen_Id المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- رقم الم ID
- رقم التعريف
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkey-national-identification-number"></a>رقم التعريف الوطني تركيا

### <a name="format"></a>تنسيق

11 رقما

### <a name="pattern"></a>النمط

11 رقما

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_Turkish_National_Id المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Turkish_National_Id كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_Turkish_National_Id المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik numarası
- Vatandaşlık nuهاsı
- Vatandaşlık no


## <a name="turkey-physical-addresses"></a>عناوين تركيا الفعلية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن أنماط ذات صلة بالمعالجة الفعلية من تركيا. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="types-of-medication"></a>أنواع الأدوية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن أسماء الأدوية، مثل الفيروسات *المخصبة*.  فهو يدعم المصطلحات الإنجليزية فقط. كما أنها مضمنة في [جميع](#all-medical-terms-and-conditions) الشروط والأحكام الطبية المجمعة المسماة كيان SIT.

### <a name="confidence-level"></a>مستوى الثقة

عال


## <a name="uk-drivers-license-number"></a>المملكة المتحدة رقم ترخيص برنامج التشغيل

### <a name="format"></a>تنسيق

تركيبة من 18 حرفا ورقما في التنسيق المحدد

### <a name="pattern"></a>النمط

18 حرفا ورقما:
- خمسة أحرف (لا تتحسس حالة الأحرف) أو الرقم "9" مكان الحرف.
- رقم واحد.
- خمسة أرقام بتنسيق التاريخ MMDDY بتاريخ الميلاد. يتم زيادة الحرف السابع ب 50 إذا كان برنامج التشغيل أنثى؛ على سبيل المثال، من 51 إلى 62 بدلا من 01 إلى 12.
- حرفان (لا يتحسسان حالة الأحرف) أو الرقم "9" مكان الحرف.
- خمسة أرقام.

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_uk_drivers_license` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keywords_eu_driver's_license_number` من.
- يتم تمرير الاختبارات.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر `Func_uk_drivers_license` الدالة على المحتوى الذي يتطابق مع النمط.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver لا s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- برنامج تشغيل
- driverlicences
- lic برنامج التشغيل
- lics في برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- ترخيص برنامج تشغيل
- تراخيص برنامج التشغيل
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- lic برامج التشغيل
- lics برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- رخصة القيادة
- تراخيص برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- اطباق برنامج التشغيل
- م الشرائح الخاصة ب برنامج التشغيل
- شريحة برنامج التشغيل
- شرائح برنامج التشغيل
- lic الخاص ب برنامج التشغيل
- lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- برنامج تشغيل #
- driverlicences #
- lic برنامج التشغيل #
- lics في برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- lic برامج التشغيل #
- lics برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- رخصة القيادة #
- تراخيص برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- اطباق برنامج التشغيل #
- م الشرائح الخاصة ب برنامج التشغيل #
- شريحة برنامج التشغيل #
- شرائح برنامج التشغيل #
- lic الخاص ب برنامج التشغيل #
- lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة 
- ترخيص القيادة
- dlno #
- lic القيادة
- رخص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- licen برنامج التشغيل
- برامج التشغيل licen
- رقائق برنامج التشغيل
- lic القيادة
- دفع الين
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl


## <a name="uk-electoral-roll-number"></a>المملكة المتحدة رقم لفة العمل

### <a name="format"></a>تنسيق

حرفان متبوعان برقم واحد إلى 4 أرقام

### <a name="pattern"></a>النمط

حرفان (لا يتحسسان حالة الأحرف) متبوعين ب 1-4 أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_uk_electoral العادي على المحتوى الذي يتطابق مع النمط.
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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- مجلس العمل
- نموذج
- سجل التهي
- roll


## <a name="uk-national-health-service-number"></a>المملكة المتحدة رقم خدمة الصحة الوطنية

### <a name="format"></a>تنسيق

10 إلى 17 رقما مفصولة بمساحات

### <a name="pattern"></a>النمط

من 10 إلى 17 رقما:
- إما 3 أو 10 أرقام
- مسافة
- ثلاثة أرقام
- مسافة
- أربعة أرقام

### <a name="checksum"></a>الاختبارات

نعم

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_uk_nhs_number المحتوى الذي يتطابق مع النمط.
- يكون أحد ما يلي صحيحا:
    - تم العثور على كلمة أساسية Keyword_uk_nhs_number كلمة أساسية.
    - تم العثور على كلمة أساسية Keyword_uk_nhs_number1 كلمة أساسية.
    - تم العثور على كلمة أساسية من Keyword_uk_nhs_number_dob.
- يتم تمرير الاختبارات.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- خدمة الصحة الوطنية
- nhs
- هيئة الخدمات الصحية
- هيئة الصحة

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- الم id المريض
- تحديد هوية المريض
- المريض لا
- رقم المريض

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.O.B
- تاريخ الميلاد
- تاريخ الميلاد


## <a name="uk-national-insurance-number-nino"></a>المملكة المتحدة رقم التأمين الوطني (NINO)

يتم تضمين كيان نوع المعلومات الحساس هذا في نوع المعلومات الحساسة لرقم التعريف الوطنية في الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

### <a name="format"></a>تنسيق

سبعة أحرف أو تسعة أحرف مفصولة بمساحات أو شرطات

### <a name="pattern"></a>النمط

نمطان محتملان:

- حرفان (تستخدم "نينوس" صالحة أحرفا معينة فقط في هذه البادئه، والتي يتم التحقق من صحة هذا النمط؛ وليس حساسة للحالة)
- ستة أرقام
- إما 'A' أو 'B' أو 'C' أو 'D' (كالبادرة، يتم السماح ببعض الأحرف فقط في اللاحقة؛ غير حساسة للقضية)

OR

- حرفان
- مسافة أو شرطة
- رقمان
- مسافة أو شرطة
- رقمان
- مسافة أو شرطة
- رقمان
- مسافة أو شرطة
- إما 'A' أو 'B' أو 'C' أو 'D'

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_uk_nino المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_uk_nino كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_uk_nino المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- رقم التأمين الوطني
- اشتراكات التأمين الوطنية
- قانون الحماية
- التأمين
- رقم الضمان الاجتماعي
- تطبيق التأمين
- تطبيق طبي
- التأمين الاجتماعي
- العناية الطبية
- الضمان الاجتماعي
- بريطانيا العظمى
- رقم NI
- NI No.
- NI #
- NI #
- التأمين #
- التأمينر
- nationalinsurance #
- nationalinsهمnumber


## <a name="uk-physical-addresses"></a>المملكة المتحدة العناوين الفعلية

يكشف هذا الكيان المسمى الذي لم يتم تكبله عن أنماط ذات صلة با عنوان فعلي من المملكة المتحدة. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط



## <a name="uk-unique-taxpayer-reference-number"></a>المملكة المتحدة رقم مرجع الممول الفريد

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

10 أرقام بدون مسافات ومواريخ


### <a name="pattern"></a>النمط

10 أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر  `Func_uk_eu_tax_file_number` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية  `Keywords_uk_eu_tax_file_number` من.

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- رقم الضريبة
- ملف الضريبة
- الم id الضريبة
- تعريف الضريبة لا
- رقم تعريف الضريبة
- لا للضريبة #
- لا للضريبة
- رقم التسجيل الضريبي
- #
- no #
- number #
- taxno #
- taxnumber #
- taxnumber
- "معرف الصفيح"
- tin no
- صفيحة #


## <a name="us-bank-account-number"></a>رقم الحساب البنكي الأميركي

### <a name="format"></a>تنسيق

6 إلى 17 رقما

### <a name="pattern"></a>النمط

6-17 رقما متتاليا

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر التعبير Regex_usa_bank_account_number العادي على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_usa_Bank_Account كلمة أساسية.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- التحقق من رقم الحساب
- التحقق من الحساب
- التحقق من الحساب #
- التحقق من رقم Acct
- التحقق من Acct #
- التحقق من Acct No.
- التحقق من رقم الحساب.
- رقم الحساب البنكي
- الحساب البنكي #
- رقم Bank Acct
- Bank Acct #
- Bank Acct No.
- رقم الحساب البنكي
- رقم حساب التوفير
- حساب التوفير.
- حساب التوفير #
- رقم Acct للادخار
- Savings Acct #
- حفظ Acct No.
- رقم حساب التوفير.
- رقم حساب المدين
- حساب المدين
- حساب المدين #
- رقم الخصم Acct
- خصم Acct #
- خصم Acct No.
- رقم حساب المدين.


## <a name="us-drivers-license-number"></a>رقم ترخيص القيادة الأمريكية

### <a name="format"></a>تنسيق

يعتمد على الحالة

### <a name="pattern"></a>النمط

يعتمد على الولاية - على سبيل المثال، نيويورك:
- ستتطابق تسعة أرقام تم تنسيقها مثل dddd ddd.
- لن تتطابق تسعة أرقام مثل dddddddd.

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_new_york_drivers_license_number الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_[state_name]_drivers_license_name الكلمة الأساسية.
- تم العثور على كلمة أساسية من Keyword_us_drivers_license.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر Func_new_york_drivers_license_number الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_[state_name]_drivers_license_name الكلمة الأساسية.
- تم العثور على كلمة أساسية Keyword_us_drivers_license_abbreviations كلمة أساسية.
- لم يتم العثور على كلمة Keyword_us_drivers_license كلمة أساسية.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- الم ID
- الم IDS
- DL #
- DLS #
- CDL #
- CDLS #
- الم ID #
- الم IDS #
- رقم الم ID
- أرقام الم ID
- LIC
- LIC #

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- برنامج التشغيل Lic
- برنامج التشغيل Lics
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- DriversLic
- DriversLics
- DriversLicense
- DriversLicenses
- برامج التشغيل Lic
- برامج التشغيل Lics
- ترخيص برامج التشغيل
- تراخيص برامج التشغيل
- برنامج التشغيل Lic
- Lics الخاصة ب برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- Lic الخاص ب برنامج التشغيل
- Lics الخاصة ب برنامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برنامج التشغيل
- برنامج التشغيل Lic
- اطباق برنامج التشغيل
- SLicense الخاص ب برنامج التشغيل
- اطباق برنامج التشغيل
- Lic الخاص ب برنامج التشغيل
- Lics الخاصة ب برنامج التشغيل
- ترخيص القيادة
- تراخيص القيادة
- رقم التعريف
- أرقام التعريف
- تعريف #
- بطاقة الم id
- بطاقات الم id
- بطاقة التعريف
- بطاقات التعريف
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- برنامج التشغيل Lic #
- برنامج التشغيل Lics #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- برامج التشغيل Lic #
- برامج التشغيل Lics #
- ترخيص برامج التشغيل #
- تراخيص برامج التشغيل #
- برنامج التشغيل Lic #
- Lics الخاصة ب برنامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- Lic الخاص ب برنامج التشغيل #
- Lics الخاصة ب برنامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برنامج التشغيل #
- برنامج التشغيل Lic #
- اطباق برنامج التشغيل #
- SLicense الخاص ب برنامج التشغيل #
- اطباق برنامج التشغيل #
- Lic الخاص ب برنامج التشغيل #
- Lics الخاصة ب برنامج التشغيل #
- ترخيص القيادة #
- تراخيص القيادة #
- بطاقة الم id #
- بطاقات الم id #
- بطاقة التعريف #
- بطاقات التعريف #


#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- اختصار الحالة (على سبيل المثال، "NY")
- اسم الولاية (على سبيل المثال، "نيويورك")


## <a name="us-individual-taxpayer-identification-number-itin"></a>رقم تعريف الممول الفردي (ITIN)

### <a name="format"></a>تنسيق

تسعة أرقام تبدأ ب "9" وتحتوي على "7" أو "8" كالرقم الرابع، تم تنسيقها بشكل اختياري باستخدام المسافات أو الشرطة

### <a name="pattern"></a>النمط

تم تنسيقه:
- الرقم "9"
- رقمان
- مسافة أو شرطة
- "7" أو "8"
- رقم
- مسافة أو شرطة
- أربعة أرقام

غير منتضد:
- الرقم "9"
- رقمان
- "7" أو "8"
- خمسة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_formatted_itin المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_itin كلمة أساسية.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_unformatted_itin على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_itin كلمة أساسية.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- تعثر Func_formatted_itin أو Func_unformatted_itin على المحتوى الذي يتطابق مع النمط.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_itin"></a>Keyword_itin

- الممول
- الم id الضريبة
- تعريف الضريبة
- itin
- i.t.i.n.
- ssn
- صفيحة
- الضمان الاجتماعي
- مسدد الضرائب
- itins
- taxid
- الممول الفردي


## <a name="us-physical-addresses"></a>العناوين الفعلية في الولايات المتحدة

يكشف هذا الكيان المسمى الذي لم يتم حله عن الأنماط ذات الصلة بالمعالجة الفعلية من الولايات المتحدة. كما أنه مضمن في [كل](#all-physical-addresses) العناوين الفعلية المجمعة المسماة SIT.

### <a name="confidence-level"></a>مستوى الثقة

متوسط


## <a name="us-social-security-number-ssn"></a>رقم الضمان الاجتماعي (SSN) في الولايات المتحدة

### <a name="format"></a>تنسيق

تسعة أرقام، والتي قد تكون في نمط تم تنسيقه أو غير تنسيقه

> [!NOTE]
> إذا تم إصداره قبل منتصف 2011، فإن SSN له تنسيق قوي حيث يجب أن تقع أجزاء معينة من الرقم ضمن نطاقات معينة لتكون صالحة (ولكن لا يوجد شيك).

### <a name="pattern"></a>النمط

تبحث أربع دالات عن SSN في أربعة أنماط مختلفة:
- Func_ssn البحث عن SSN بتنسيق قوي قبل 2011 تم تنسيقه باستخدام شرط أو مسافات (ddd-dddd أو ddd ddd ddddd)
- Func_unformatted_ssn البحث عن SSN بتنسيق قوي قبل 2011 غير منسق بتسعة أرقام متتالية (dddddddddd)
- Func_randomized_formatted_ssn البحث عن SSN بعد عام 2011 التي تم تنسيقها باستخدام شرط أو مسافات (ddd-ddddD OR ddd ddddd)
- Func_randomized_unformatted_ssn البحث عن SSN بعد عام 2011 التي لم يتم فرزها بتسعة أرقام متتالية (ddddddddd)

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر `Func_ssn` الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_ssn` من.

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر Func_unformatted_ssn الدالة على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_ssn` من.

يكون نهج DLP منخفض الثقة في الكشف عن هذا النوع من المعلومات الحساسة إذا كان، ضمن تقارب 300 حرف:
- الدالة `Func_randomized_formatted_ssn` أو `Func_randomized_unformatted_ssn` تعثر على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية `Keyword_ssn` من.


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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_ssn"></a>Keyword_ssn

- رقم SSA
- رقم الضمان الاجتماعي
- الضمان الاجتماعي #
- الضمان الاجتماعي #
- لا الضمان الاجتماعي
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

### <a name="pattern"></a>النمط

- حرف واحد أو رقم واحد
- ثمانية أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة عالية في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_usa_uk_passport المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_uk_eu_passport_number` تم العثور عليها.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_date`

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- تعثر الدالة Func_usa_uk_passport المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_uk_eu_passport_number` تم العثور عليها.

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

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- جواز السفر #
- جواز السفر #
- جواز سفر
- passports
- passportno
- جواز السفر لا
- passportnumber
- رقم جواز السفر
- passportnumbers
- أرقام جواز السفر

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- جواز السفر البريطاني
- جواز سفر المملكة المتحدة


## <a name="ukraine-passport-domestic"></a>جواز سفر أوكرانيا محلي

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

تسعة أرقام

### <a name="pattern"></a>النمط

تسعة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر Regex_Ukraine_Passport_Domestic regex على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Ukraine_Passport_Domestic كلمة أساسية.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- جواز سفر أوكرانيا
- رقم جواز السفر
- جواز السفر لا
- паспорт України
- номер паспорта
- персональний


## <a name="ukraine-passport-international"></a>جواز سفر أوكرانيا دولي

يتوفر نوع المعلومات الحساس هذا فقط للاستخدام في:
- سياسات منع فقدان البيانات
- سياسات التوافق مع الاتصالات
- إدارة المعلومات
- إدارة السجلات
- Microsoft Defender لتطبيقات السحابة

### <a name="format"></a>تنسيق

نمط alphanumeric من ثمانية أحرف

### <a name="pattern"></a>النمط

النمط alphanumeric من ثمانية أحرف:
- حرفان أو رقمان
- ستة أرقام

### <a name="checksum"></a>الاختبارات

لا

### <a name="definition"></a>التعريف

إن نهج DLP لديه ثقة متوسطة في أنه اكتشف هذا النوع من المعلومات الحساسة إذا كان في تقارب 300 حرف:
- يعثر Regex_Ukraine_Passport_International regex على المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية Keyword_Ukraine_Passport_International كلمة أساسية.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>الكلمات الأساسية

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- جواز سفر أوكرانيا
- رقم جواز السفر
- جواز السفر لا
- паспорт України
- номер паспорта


