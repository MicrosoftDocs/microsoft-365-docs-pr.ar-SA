---
title: إنشاء المخطط لأنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة
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
description: إنشاء المخطط لأنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9eb4e69aa833e8a355115115e1c965e57d65716c
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435270"
---
# <a name="create-the-schema-for-exact-data-match-based-sensitive-information-types"></a>إنشاء المخطط لأنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يمكنك إنشاء المخطط وEDM SIT باستخدام [مخطط مطابقة البيانات الدقيق ومعالج نمط المعلومات الحساسة](#use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard) أو [يدويا](#create-exact-data-match-schema-manually-and-upload). يمكنك أيضا دمج كل من استخدام أسلوب واحد لإنشاء المخطط وتحريره لاحقا باستخدام الأسلوب الآخر.

إذا لم تكن على دراية ب SITS المستندة إلى EDM أو تنفيذها، يجب أن تتعرف على:

- [التعرّف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [التعرّف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [بدء استخدام أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

يمكن استخدام مخطط EDM واحد في أنواع معلومات حساسة متعددة تستخدم نفس جدول البيانات الحساسة. يمكنك إنشاء ما يصل إلى 10 مخططات مختلفة ل EDM في مستأجر Microsoft 365.



## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-wizard"></a>استخدام "مخطط مطابقة البيانات الدقيقة" ومعالج نوع المعلومات الحساسة

يمكنك استخدام هذا المعالج للمساعدة في تبسيط عملية إنشاء ملف المخطط.

## <a name="pre-requisites"></a>المتطلبات الأساسية

- تنفيذ الخطوات في [تصدير البيانات المصدر لنوع المعلومات الحساسة المستندة إلى مطابقة البيانات الدقيقة](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type).

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>استخدام مخطط مطابقة البيانات الدقيق ومعالج نمط نوع المعلومات الحساسة

1. في مدخل التوافق في Microsoft Purview للمستأجر الخاص بك انتقل إلى **بيانات Data classificationExact** >  **تتطابق** >  مع **مخططاتEDM**.

2. اختر **إنشاء مخطط EDM** لفتح القائمة المنبثقة لتكوين معالج المخطط.

   ![القائمة المنبثقة لتكوين معالج إنشاء مخطط EDM.](../media/edm-schema-wizard-1.png)

3. املأ **الاسم** **والوصف** المناسبين.

4. اختر **تجاهل المحددات وعلامات الترقيم لكافة حقول المخطط** إذا كنت تريد هذا السلوك للمخطط بأكمله. لمعرفة المزيد حول تكوين EDM لتجاهل الحالة أو المحددات، راجع [استخدام حقول caseInsensitive وتجاهلDelimiters](#using-the-caseinsensitive-and-ignoreddelimiters-fields) للحصول على مزيد من التفاصيل حول هذه الميزة.

5. املأ القيم المطلوبة **لحقل المخطط رقم 1** وأضف المزيد من الحقول حسب الحاجة. يجب أن يكون كل حقل مخطط مطابقا لرؤوس الأعمدة في ملف مصدر المعلومات الحساسة.

6. إذا أردت، فقم بتعيين قيم كل حقل ل:
    1. **الحقل قابل للبحث**
    1. **الحقل غير حساس لحالة الأحرف**
    1. **اختيار المحددات وعلامات الترقيم لتجاهلها لهذا الحقل**
    1. **أدخل المحددات المخصصة وعلامات الترقيم لهذا الحقل**

   > [!IMPORTANT]
   > يجب تعيين حقل واحد على الأقل، ولكن يجب تعيين خمسة حقول من حقول المخطط على أنها قابلة للبحث.

7. اختر **"حفظ**". سيتم الآن إدراج المخطط الخاص بك وسيتوفر للاستخدام.

   > [!IMPORTANT]
   > إذا كنت تريد إزالة مخطط، وكان مقترنا بالفعل بنوع معلومات حساسة ل EDM، يجب أولا حذف نوع المعلومات الحساسة ل EDM، ثم يمكنك حذف المخطط. يؤدي حذف مخطط يحتوي على مخزن بيانات مقترن به أيضا إلى حذف مخزن البيانات في غضون 24 ساعة.

## <a name="export-of-the-edm-schema-file-in-xml-format"></a>تصدير ملف مخطط EDM بتنسيق XML

إذا قمت بإنشاء مخطط EDM في معالج مخطط EDM، يجب تصدير ملف مخطط EDM بتنسيق XML. ستحتاج إليها في [تجزئة وتحميل جدول مصدر المعلومات الحساسة لمرحلة أنواع المعلومات الحساسة المطابقة تماما للبيانات](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) .

1. [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. لتصدير ملف مخطط EDM، استخدم بناء الجملة هذا:

   ```powershell
   $Schema = Get-DlpEdmSchema -Identity "[your EDM Schema name]"
   Set-Content -Path ".\Schemafile.xml" -Value $Schema.EdmSchemaXML
   ```

3. احفظ هذا الملف لاستخدامه لاحقا.

## <a name="create-exact-data-match-schema-manually-and-upload"></a>إنشاء مخطط مطابقة البيانات بشكل يدوي وتحميله

في ملف المخطط، قم بتكوين إدخال لكل عمود في جدول مصدر المعلومات الحساسة، باستخدام بناء الجملة:

```xml
<Field name="FieldName" searchable="true/false" caseInsensitive="true/false" ignoredDelimiters="delimiter characters" />
```

### <a name="using-the-caseinsensitive-and-ignoreddelimiters-fields"></a>استخدام حقول caseInsensitive and ignoredDelimiters

يستخدم نموذج XML للمخطط التالي حقول *caseInsensitive* *وDelimiters التي تم تجاهلها* .

عند تضمين حقل *caseInsensitive* المعين إلى قيمة `true` في تعريف المخطط الخاص بك، لن يستثني EDM عنصرا استنادا إلى اختلافات الحالة. على سبيل المثال، سترى EDM القيم **FOO-1234** **وfOo-1234** متطابقة للحقل `PatientID` .

عند تضمين حقل *IgnoreedDelimiters* مع أحرف معتمدة، سيتجاهل EDM هذه الأحرف. لذلك سيشاهد EDM القيم **FOO-1234** و **FOO#1234** على أنها متطابقة للحقل `PatienID` .

في هذا المثال، حيث يتم استخدام كليهما `caseInsensitive` `ignoredDelimiters` ، قد ترى EDM **أن FOO-1234** **وfOo#1234** متطابقان وتصنف العنصر كنوع معلومات حساسة لسجل المريض.

يتم استخدام كلتا المعلمتين على أساس كل حقل.

> [!IMPORTANT]
> إذا قمت بتكوين *مسافات* ليتم تجاهلها، فسيكون ذلك فعالا فقط لأعمدة الحقول الأساسية ويتم تعريف نوع معلومات حساسة يمكنه الكشف عن سلاسل متعددة الكلمات. وإلا فسيتم إجراء المقارنة مقابل كل كلمة فردية في المحتوى الذي يتم تحليله.

تدعم *علامةDelimiters التي تم تجاهلها* أي حرف غير أبجدي رقمي، فيما يلي بعض الأمثلة:

- \.
- \-
- \/
- \_
- \*
- \^
- \#
- \!
- \?
- \[
- \]
- \{
- \}
- \\
- \~
- \;

`ignoredDelimiters` لا تدعم العلامة ما يلي:

- الأحرف من 0 إلى 9
- A-Z
- a-z
- \"
- \,

> [!IMPORTANT]
> عند تعريف نوع المعلومات الحساسة ل EDM، لن يؤثر *ignoreDelimiters* على كيفية تعريف نوع المعلومات الحساسة للتصنيف المقترن بالعنصر الأساسي في نمط EDM للمحتوى في عنصر. لذلك إذا قمت بتكوين *ignoreDelimiters* لحقل قابل للبحث، فستحتاج إلى التأكد من أن نوع المعلومات الحساسة المستخدمة لعنصر أساسي يستند إلى هذا الحقل سيختار السلاسل مع وجود هذه الأحرف وبدونها.
>
> يجب أن يتطابق عدد الأعمدة في جدول مصدر المعلومات الحساسة وعدد الحقول في المخطط، لا يهم الترتيب.

1. حدد المخطط بتنسيق XML (على غرار المثال أدناه). قم بتسمية ملف المخطط هذا **edm.xml**، وقم بتكوينه بحيث يوجد سطر يستخدم بناء الجملة لكل عمود في جدول مصدر المعلومات الحساسة:

      `\<Field name="" searchable=""/\>`.

      - استخدام أسماء الأعمدة لقيم *اسم الحقل* .
      - استخدم *searchable="true"* للحقول التي تريد أن تكون قابلة للبحث والحقول الأساسية بحد أقصى 5 حقول. يجب أن يكون حقل واحد على الأقل قابلا للبحث.

      على سبيل المثال، يحدد ملف XML التالي مخطط قاعدة بيانات سجلات المرضى، مع خمسة حقول محددة على أنها قابلة للبحث: *PatientID* و *MRN* *وSSN* *الهاتف* و *DOB*.

      (يمكنك نسخ المثال وتعديله واستخدامه.)

      ```xml
      <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
            <DataStore name="PatientRecords" description="Schema for patient records" version="1">
                  <Field name="PatientID" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
                  <Field name="MRN" searchable="true" />
                  <Field name="FirstName" />
                  <Field name="LastName" />
                  <Field name="SSN" searchable="true" />
                  <Field name="Phone" searchable="true" />
                  <Field name="DOB" searchable="true" />
                  <Field name="Gender" />
                  <Field name="Address" />
            </DataStore>
      </EdmSchema>
      ```

   بمجرد إنشاء ملف مخطط EDM بتنسيق XML، يجب عليك تحميله إلى خدمة السحابة.

2. [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

3. لتحميل مخطط قاعدة البيانات، قم بتشغيل الأمر التالي:

      ```powershell
      New-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      ستتم مطالبتك بالتأكيد، كما يلي:

      > تاكيد
      >
      > هل تريد بالتأكيد تنفيذ هذا الإجراء؟
      >
      > سيتم استيراد مخطط EDM الجديد لمخزن البيانات "patientrecords".
      >
      > \[Y نعم نعم للكل \[N\] No \[L\] No للكل\[؟\]\] \[\] التعليمات (الإعداد الافتراضي هو "Y"):

   > [!TIP]
   > إذا كنت تريد إجراء التغييرات بدون تأكيد، فلا تستخدمها `-Confirm:$true` في الخطوة 3.

> [!NOTE]
> قد يستغرق تحديث EDMSchema بالإضافات ما بين 10 إلى 60 دقيقة. يجب أن يكتمل التحديث قبل تنفيذ الخطوات التي تستخدم الإضافات.

## <a name="next-step"></a>الخطوة التالية

- [تجزئة وتحميل جدول مصدر المعلومات الحساسة للحصول على بيانات مطابقة تماماً لأنواع المعلومات الحساسة](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)
