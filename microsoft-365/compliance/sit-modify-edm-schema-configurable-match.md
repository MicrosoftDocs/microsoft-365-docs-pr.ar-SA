---
title: تعديل مخطط مطابقة البيانات الدقيق لاستخدام تطابق قابل للتكوين
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: تعرف على كيفية تعديل مخطط edm لاستخدام تطابق قابل للتكوين.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cf11e60f3fce46926d297c97a44c7d494942d556
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/29/2022
ms.locfileid: "63569757"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>تعديل مخطط مطابقة البيانات الدقيق لاستخدام تطابق قابل للتكوين

يمكنك التصنيف المستند إلى مطابقة البيانات الدقيقة (EDM) من إنشاء أنواع معلومات حساسة مخصصة تشير إلى القيم الدقيقة في قاعدة بيانات تتضمن معلومات حساسة. عندما تحتاج إلى السماح بمتغيرات سلسلة دقيقة، يمكنك استخدام تطابق قابل للتكوين Microsoft 365 تجاهل حالة الأحرف وبعض المحددات.

> [!IMPORTANT]
> استخدم هذا الإجراء لتعديل مخطط EDM وملف بيانات موجود.

1. قم ب إلغاء تثبيت **EdmUploadAgent.exeمن الكمبيوتر** الذي تستخدمه للاتصال Microsoft 365 مخطط EDM وأغراض تحميل ملف البيانات.

2. قم **بتنزيل ملفEdmUploadAgent.exe** المناسب لاشتراكك باستخدام الارتباطات أدناه:
    - [التجاري + سحابة القطاع الحكومي](https://go.microsoft.com/fwlink/?linkid=2088639) - يجب على معظم العملاء التجاريين استخدام هذا
    - [سحابة القطاع الحكومي-High](https://go.microsoft.com/fwlink/?linkid=2137521) - هذا خاص لمشتركي السحابة الحكومية عالية الأمان
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) - هذا خاص لعملاء السحابة في وزارة الدفاع الأمريكية

3. تخويل عامل Upload EDM وفتح نافذة موجه الأوامر (كمسؤول) وتشغيل الأمر التالي:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

4. إذا لم يكن لديك نسخة حالية من المخطط الحالي، ستحتاج إلى تنزيل نسخة من المخطط الموجود، قم بتشغيل هذا الأمر:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]
   ```

5. قم بتخصيص المخطط بحيث يستخدم كل عمود "caseInsensitive" و / أو "تم تجاهلDelimiters".  القيمة الافتراضية ل "caseInsensitive" هي "false" وبالنسبة إلى "تم تجاهلDelimiters"، فهي سلسلة فارغة.

    > [!NOTE]
    > يجب أن يدعم نوع المعلومات الحساسة المخصصة الأساسية أو نوع المعلومات الحساسة المضمن المستخدم للكشف عن نمط regex العام الكشف عن إدخالات التباينات المدرجة مع المعرف الذي تم تجاهله. على سبيل المثال، يمكن لنوع المعلومات الحساسة لرقم الضمان الاجتماعي (SSN) المضمن في الولايات المتحدة الكشف عن تباينات في البيانات التي تتضمن شرط أو مسافات أو عدم وجود مسافات بين الأرقام التي تم تجميعها التي تكون SSN. ونتيجة لذلك، فإن المواديل الوحيدة ذات الصلة التي يجب تضمينها في المهل التي تم تجاهلها في EDM لبيانات SSN هي: الشرطة والمساحة.

    إليك مخطط عينة يحاكي تطابق حالة غير متحسس عن طريق إنشاء أعمدة إضافية مطلوبة للتعرف على تباينات حالات الحالة في البيانات الحساسة.

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
               <Field name="PolicyNumber" searchable="true" />
               <Field name="PolicyNumberLowerCase" searchable="true" />
               <Field name="PolicyNumberUpperCase" searchable="true" />
               <Field name="PolicyNumberCapitalLetters" searchable="true" />
      </DataStore>
    </EdmSchema>
    ```

    في المثال أعلاه، لن `PolicyNumber` تحتاج بعد ذلك إلى تباينات العمود الأصلي إذا تم `caseInsensitive` `ignoredDelimiters` إضافة كل منهما.

    لتحديث هذا المخطط بحيث تستخدم EDM مطابقة قابلة للتكوين، استخدم `caseInsensitive` علامة و `ignoredDelimiters` .  إليك كيف يبدو ذلك:

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
             <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
      </DataStore>
    </EdmSchema>
    ```

    تدعم `ignoredDelimiters` العلامة أي حرف غير alphanumeric، فيما يلي بعض الأمثلة:
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

    لا `ignoredDelimiters` تدعم العلامة:
    - الأحرف من 0 إلى 9
    - A-Z
    - a-z
    - \"
    - \,

6. [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

    > [!NOTE]
    > إذا كانت مؤسستك قد قمت بإعداد ["مفتاح العميل"](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview) Microsoft 365 المستأجر (المعاينة العامة)، فإن تطابق البيانات الدقيق سيستخدم وظائف التشفير الخاصة به تلقائيا. يتوفر هذا فقط للمستأجرين المرخصين في E5 في السحابة التجارية.

7. قم بتحديث المخطط عن طريق تشغيل الأمر التالي:

   ```powershell
   Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
   ```

8. إذا لزم الأمر، قم بتحديث ملف البيانات لمطابقة إصدار المخطط الجديد.

    > [!TIP]
    > بشكل اختياري، يمكنك تشغيل التحقق من الصحة مقابل ملف csv قبل التحميل عن طريق تشغيل:
    >
    > `EdmUploadAgent.exe /ValidateData /DataFile [data file] [schema file]`
    >
    > لمزيد من المعلومات حول جميع EdmUploadAgent.exe المعتمدة، تشغيل
    >
    > `EdmUploadAgent.exe /?`

9. افتح نافذة موجه الأوامر (كمسؤول) ثم قم بتشغيل الأمر التالي لتفيش البيانات الحساسة وتحميلها:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]
   ```

## <a name="related-articles"></a>المقالات ذات الصلة

- [التعرف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [تعريفات نوع كيان المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [أنواع المعلومات الحساسة المخصصة](./sensitive-information-type-learn-about.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [Microsoft Defender لتطبيقات السحابة](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
