---
title: إنشاء بيانات دقيقة تتطابق مع نوع المعلومات الحساسة/حزمة القاعدة
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: إنشاء بيانات دقيقة تتطابق مع نوع المعلومات الحساسة/حزمة القاعدة
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e44d18bc1a779ace95fb2f64171ff0bf91de57ed
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63574690"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>إنشاء بيانات دقيقة تتطابق مع نوع المعلومات الحساسة/حزمة القاعدة

يمكنك إنشاء نوع معلومات حساسة مطابقة دقيقة للبيانات (EDM) (SIT) باستخدام معالج مخطط [EDM](#use-the-edm-schema-and-sit-wizard) و SIT في مركز التوافق أو إنشاء ملف حزمة القواعد XML [يدويا](#create-a-rule-package-manually). يمكنك أيضا دمج كليهما باستخدام أسلوب واحد لإنشاء المخطط وتحريره لاحقا باستخدام الأسلوب الآخر.

إذا لم تكن على دراية بتطبيقات SITS المستندة إلى EDM أو تنفيذها، يجب عليك التعرف على:

- [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [التعرف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [بدء استخدام أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>استخدام مخطط EDM ومعالج SIT

يمكنك استخدام هذا المعالج لإنشاء ملفات نوع المعلومات الحساسة (SIT) للمساعدة في تبسيط العملية.

يتكون نوع المعلومات الحساسة ل EDM من نمط واحد أو أكثر. يصف كل نمط مجموعة من الدلائل (الحقول من المخطط) التي سيتم استخدامها لتعريف المحتوى الحساس في مستند أو بريد إلكتروني.

## <a name="pre-requisites"></a>المتطلبات الأساسية

تنفيذ الخطوات في المقالات التالية:

1. [تصدير بيانات المصدر لنوع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [إنشاء المخطط لأنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [قم بتهش جدول مصدر المعلومات الحساس وتحميله للحصول على بيانات دقيقة تتطابق مع أنواع المعلومات الحساسة](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- سواء كنت ستنشئ نوع معلومات حساسة ل EDM باستخدام المعالج أو ملف حزمة القاعدة XML عبر PowerShell، يجب أن يكون لديك أذونات المسؤول العام أو مسؤول التوافق لإنشاء نوع معلومات حساسة مخصص واختباره ونشره من خلال واجهة المستخدم. راجع [حول أدوار المسؤولين في Office 365](/office365/admin/add-users/about-admin-roles).
- تحديد أحد أنواع المعلومات الحساسة للعناصر الأساسية لاستخدامها كنوع المعلومات الحساسة للعناصر الأساسية.
  - إذا لم يكن أي من أنواع المعلومات الحساسة المضمنة متطابقا مع البيانات الموجودة في العمود الذي حددته، فماذا يجب أن تقوم بإنشاء نوع معلومات حساسة مخصص يقوم بذلك.
  - إذا قمت بتحديد الخيار المحددات التي تم تجاهلها الخاصة عمود العنصر الأساسي في المخطط، فتأكد من أن SIT المخصص الذي تقوم بإنشاءه سيطابق البيانات مع المحددات المحددة وبدونها.
  - إذا كنت تستخدم مجموعة مضمنة في SIT، فتأكد من أنها ستكتشف تماما السلاسل التي تريد تحديدها، ولا تتضمن أي أحرف محيطة أو تستبعد أي جزء صحيح من السلسلة كما هو مخزن في جدول المعلومات الحساسة.

راجع [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) [وإنشاء أنواع معلومات حساسة مخصصة في مركز التوافق](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>استخدام مخطط مطابقة البيانات بدقة ومعالج نمط نوع المعلومات الحساسة

1. في Microsoft 365 التوافق للمستأجر، انتقل إلى **تصنيف** >  **البياناتتطابق البيانات**.

2. اختر **أنواع المعلومات الحساسة ل EDM** وإنشاء نوع معلومات **حساسة ل EDM** لفتح معالج تكوين نوع المعلومات الحساسة.

3. اختر **اختيار مخطط EDM** موجود واختر المخطط الذي أنشأته في إنشاء المخطط لأنواع المعلومات الحساسة المستندة إلى مطابقة البيانات [بدقة](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

4. اختر **التالي** واختر **إنشاء نمط**.

5. اختر مستوى **الثقة** و **العنصر الأساسي**. لمعرفة المزيد حول مستويات الثقة، راجع [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

6. اختر نوع **المعلومات الحساسة** للعناصر الأساسية لاقرانه بتعريف النص الذي سيتم مقارنته مع كل القيم في حقل العنصر الأساسي. راجع [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md) لمعرفة المزيد حول أنواع المعلومات الحساسة المتوفرة.

   > [!IMPORTANT]
   > حدد نوع معلومات حساسة يتطابق بشكل وثيق مع تنسيق المحتوى الذي تريد البحث فيه. قد يؤدي تحديد نوع معلومات حساسة يتطابق مع المحتوى غير الضروري، مثل ذلك النوع الذي يتطابق مع كل السلاسل النصية، أو كل الأرقام إلى تحميل زائد في النظام مما قد يؤدي إلى تفوية المعلومات الحساسة. راجع القسم أفضل الممارسات في المقالة مقدمة إلى مطابقة البيانات بدقة في هذه الوثائق للحصول على توصيات حول تحديد نوع معلومات حساسة لاستخدامه هنا.

7. اختر **عناصر الدعم والخيارات** المطابقة.

8. اختر **تم** **والتاية**.

9. اختر مستوى **الثقة المطلوب وتقارب الأحرف**. ستكون هذه هي القيمة الافتراضية لنوع المعلومات الحساسة ل EDM بكامله.

10. اختر **إنشاء نمط** إذا كنت تريد إنشاء أنماط إضافية لنوع المعلومات الحساسة ل EDM.

11. اختر **التالي** واملأ **الاسم** **والوصف للمسؤولين**.

12. راجع الأمر واختر **إرسال**.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>تحرير نمط نوع المعلومات الحساسة أو حذفه

1. فتح **مركز** **التوافقتصنيف** >  **البياناتتطابق** >  البيانات.

2. اختر **أنواع المعلومات الحساسة ل EDM**.

3. اختر EDM SIT الذي تريد تحريره.

4. اختر **تحرير نوع المعلومات الحساسة ل EDM** أو حذف نوع المعلومات الحساسة **ل EDM** من الصورة المنا البيانات.

## <a name="create-a-rule-package-manually"></a>إنشاء حزمة قاعدة يدويا

يوضح لك هذا الإجراء كيفية إنشاء ملف بتنسيق XML يسمى حزمة قاعدة (باستخدام ترميز Unicode)، ثم تحميله إلى Microsoft 365 باستخدام Cmdlets في مركز التوافق PowerShell.

> [!NOTE]
> إذا كان يمكن ل SIT الذي تريد تعيينه الكشف عن أدلة متعددة الكلمات، يمكن تعيين العناصر الثانوية التي تحددها في حزمة قواعد تم إنشاؤها يدويا إلى SIT. `John Smith` `John Smith` `Smith` `John` على سبيل المثال، لن يكون الاسم متطابقا كعنصر ثانوي لأننا نقارن المصطلح الذي تم تحميله في أحد الحقول ونعثر عليه في المحتوى بشكل منفصل، إذا لم يتم تعيين حقل الإثبات المقارن هذا إلى SIT يمكنه الكشف عن هذا النمط.
>
> هناك حد لعدد 10 حزم قواعد في Microsoft 365 المستأجر. بما أن حزمة القواعد قد تحتوي على عدد عشوائي من أنواع المعلومات الحساسة، يمكنك تجنب إنشاء حزمة قواعد جديدة في كل مرة تريد فيها تعريف نوع جديد من المعلومات الحساسة باستخدام هذا الأسلوب، بدلا من تصدير حزمة قواعد موجودة وإضافة أنواع المعلومات الحساسة إلى XML قبل إعادة تحميلها.

1. أنشئ حزمة قواعد بتنسيق XML (باستخدام ترميز Unicode)، تماما كما في المثال التالي. (يمكنك نسخ المثال وتعديله واستخدامه.)

   عند إعداد حزمة القاعدة، تأكد من الإشارة بشكل صحيح إلى ملف جدول مصدر المعلومات الحساسة وملف .csv أو tsv. أو pipe (|) المحدد وملفedm.xmlمخطط البيانات.**** يمكنك نسخ المثال وتعديله واستخدامه. في نموذج xml هذا، يجب تخصيص الحقول التالية لإنشاء نوع EDM الحساس:

   - **id rulePack & ExactMatch**: استخدم [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) لإنشاء GUID.

   - **Datastore**: يحدد هذا الحقل مخزن بيانات البحث ل EDM الذي سيتم استخدامه. يمكنك توفير اسم مصدر البيانات لم مخطط EDM الذي تم تكوينه.

   - **idMatch**: يشير هذا الحقل إلى العنصر الأساسي ل EDM.
   - **تطابقات**: يحدد الحقل الذي سيتم استخدامه في عملية البحث الدقيقة. يمكنك توفير اسم حقل قابل للبحث في مخطط EDM ل DataStore.
   - **التصنيف**: يحدد هذا الحقل نوع المعلومات الحساسة الذي يؤدي إلى تشغيل البحث في EDM. يمكنك استخدام اسم نوع معلومات مضمنة أو مخصصة حساسة موجودة أو GUID.

   > [!NOTE]
   > يجب الانتباه إلى أن أي سلسلة تطابق SIT التي تم توفيرها سيتم تفقيدها ومقارنتها مع كل إدخال في جدول مصدر المعلومات الحساس. لتجنب مشاكل الأداء إذا اخترت نظام SIT مخصصا عنصر التصنيف، فلا تستخدم واحدا يطابق نسبة مئوية كبيرة من المحتوى. على سبيل المثال، كلمة تطابق "أي رقم" أو "أي كلمة من خمسة حروف". يمكنك تمييزه عن طريق إضافة كلمات أساسية مدعمة أو تضمين تنسيق في تعريف التصنيف المخصص SIT.

   - **مطابقة**: يشير هذا الحقل إلى أدلة إضافية تم العثور عليها بالقرب من idMatch.
   - **تطابقات**: توفر أي اسم حقل في مخطط EDM ل DataStore.
   - **مورد idRef:** يحدد هذا القسم الاسم والوصف للنوع الحساس في لغات متعددة
     - أنت توفر GUID لمعيار ExactMatch.
     - **الاسم** &  **الوصف**: تخصيص كما هو مطلوب.

      ```xml
      <RulePackage xmlns="http://schemas.microsoft.com/office/2018/edm">
        <RulePack id="fd098e03-1796-41a5-8ab6-198c93c62b11">
          <Version build="0" major="2" minor="0" revision="0" />
          <Publisher id="eb553734-8306-44b4-9ad5-c388ad970528" />
          <Details defaultLangCode="en-us">
            <LocalizedDetails langcode="en-us">
              <PublisherName>IP DLP</PublisherName>
              <Name>Health Care EDM Rulepack</Name>
              <Description>This rule package contains the EDM sensitive type for health care sensitive types.</Description>
            </LocalizedDetails>
          </Details>
        </RulePack>
        <Rules>
          <ExactMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB371" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
            <Pattern confidenceLevel="65">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
            </Pattern>
            <Pattern confidenceLevel="75">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
              <Any minMatches ="3" maxMatches ="6">
                <match matches="PatientID" />
                <match matches="MRN"/>
                <match matches="FirstName"/>
                <match matches="LastName"/>
                <match matches="Phone"/>
                <match matches="DOB"/>
              </Any>
            </Pattern>
          </ExactMatch>
          <LocalizedStrings>
            <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB371">
              <Name default="true" langcode="en-us">Patient SSN Exact Match.</Name>
              <Description default="true" langcode="en-us">EDM Sensitive type for detecting Patient SSN.</Description>
            </Resource>
          </LocalizedStrings>
        </Rules>
      </RulePackage>
      ```

2. Upload حزمة القواعد عن طريق تشغيل الأمر PowerShell التالي:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('.\\rulepack.xml'))
   ```

> [!NOTE]
> إن بناء جملة ملف حزمة القاعدة هو نفسه بناء جملة أنواع المعلومات الحساسة الأخرى. للحصول على تفاصيل كاملة حول بناء جملة ملف حزمة القاعدة ولالخيارات الإضافية لتكوينها، ول للحصول على إرشادات حول تعديل أنواع المعلومات الحساسة وحذفها باستخدام PowerShell، أنشئ نوع معلومات حساسة مخصصا باستخدام [PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell).

## <a name="next-step"></a>الخطوة التالية

- [اختبار نوع معلومات دقيق يطابق المعلومات الحساسة](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
