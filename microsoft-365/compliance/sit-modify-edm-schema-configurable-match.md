---
title: تعديل مخطط مطابقة البيانات الدقيقة لاستخدام مطابقة قابلة للتكوين
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
description: تعرف على كيفية تعديل مخطط edm لاستخدام مطابقة قابلة للتكوين.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a90f81136bf6aa78aa11d732deca19ecd1d59b9c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622052"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>تعديل مخطط مطابقة البيانات الدقيقة لاستخدام مطابقة قابلة للتكوين

يمكنك التصنيف المستند إلى مطابقة البيانات الدقيقة (EDM) من إنشاء أنواع معلومات حساسة مخصصة تشير إلى القيم الدقيقة في قاعدة بيانات المعلومات الحساسة. عندما تحتاج إلى السماح بمتغيرات سلسلة دقيقة، يمكنك استخدام *مطابقة قابلة للتكوين* لإخبار Microsoft Purview بتجاهل الحالة وبعض المحددات.

> [!IMPORTANT]
> استخدم هذا الإجراء لتعديل مخطط EDM وملف بيانات موجودين.

1. قم بإلغاء تثبيت **EdmUploadAgent.exe** من الكمبيوتر الذي تستخدمه للاتصال ب Microsoft 365 لمخطط EDM ولأغراض تحميل ملف البيانات.

2. قم بتنزيل ملف **EdmUploadAgent.exe** المناسب لاشتراكك باستخدام الارتباطات أدناه:
    - [التجاري + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) - يجب على معظم العملاء التجاريين استخدام هذا
    - [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) - هذا مخصص لمشتركي السحابة الحكومية ذات الأمان العالي
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) - هذا مخصص لعملاء السحابة في وزارة الدفاع الأمريكية

3. تخويل عامل تحميل EDM وفتح نافذة موجه الأوامر (كمسؤول) وتشغيل الأمر التالي:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

4. إذا لم يكن لديك نسخة حالية من المخطط الحالي، فستحتاج إلى تنزيل نسخة من المخطط الموجود، قم بتشغيل هذا الأمر:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]
   ```

5. تخصيص المخطط بحيث يستخدم كل عمود "caseInsensitive" و / أو "ignoredDelimiters".  القيمة الافتراضية ل "caseInsensitive" هي "false" وبالنسبة إلى "ignoredDelimiters"، فهي سلسلة فارغة.

    > [!NOTE]
    > يجب أن يدعم نوع المعلومات الحساسة المخصص الأساسي أو المضمن في نوع المعلومات الحساسة المستخدم للكشف عن نمط regex العام الكشف عن إدخالات التباينات المدرجة مع مدخلات تم تجاهلها. على سبيل المثال، يمكن لنوع المعلومات الحساسة لرقم الضمان الاجتماعي (SSN) المضمن في الولايات المتحدة اكتشاف الاختلافات في البيانات التي تتضمن شرطات أو مسافات أو نقص المسافات بين الأرقام المجمعة التي تشكل SSN. ونتيجة لذلك، فإن المحددات الوحيدة ذات الصلة التي يجب تضمينها في EDM's ignoredDelimiters لبيانات SSN هي: شرطة ومساحة.

    فيما يلي نموذج مخطط يحاكي التطابق غير الحساس لحالة الأحرف عن طريق إنشاء الأعمدة الإضافية اللازمة للتعرف على تباينات الحالة في البيانات الحساسة.

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

    في المثال أعلاه، لن تكون هناك حاجة إلى تباينات العمود الأصلي `PolicyNumber` إذا تمت إضافتها`caseInsensitive`.`ignoredDelimiters`

    لتحديث هذا المخطط بحيث يستخدم EDM مطابقة قابلة للتكوين، استخدم العلامات `caseInsensitive` والعلامات `ignoredDelimiters` .  إليك كيف يبدو ذلك:

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
             <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
      </DataStore>
    </EdmSchema>
    ```

    `ignoredDelimiters` تدعم العلامة أي حرف غير أبجدي رقمي، فيما يلي بعض الأمثلة:
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

6. [الاتصال ب Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

    > [!NOTE]
    > إذا قامت مؤسستك بإعداد [مفتاح العميل ل Microsoft 365 على مستوى المستأجر (معاينة عامة)،](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview) فستستفيد مطابقة البيانات الدقيقة من وظائف التشفير الخاصة بها تلقائيا. يتوفر هذا فقط للمستأجرين المرخصين E5 في السحابة التجارية.

7. حدث المخطط عن طريق تشغيل الأمر التالي:

   ```powershell
   Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
   ```

8. إذا لزم الأمر، قم بتحديث ملف البيانات لمطابقة إصدار المخطط الجديد.

    > [!TIP]
    > بشكل اختياري، يمكنك تشغيل التحقق من الصحة مقابل ملف csv قبل التحميل عن طريق تشغيل:
    >
    > `EdmUploadAgent.exe /ValidateData /DataFile [data file] [schema file]`
    >
    > لمزيد من المعلومات حول جميع المعلمات المدعومة EdmUploadAgent.exe، قم بتشغيل
    >
    > `EdmUploadAgent.exe /?`

9. افتح نافذة موجه الأوامر (كمسؤول) وقم بتشغيل الأمر التالي لتجزئة البيانات الحساسة وتحميلها:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]
   ```

## <a name="related-articles"></a>المقالات ذات الصلة

- [التعرّف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [تعريفات نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [أنواع المعلومات الحساسة المخصصة](./sensitive-information-type-learn-about.md)
- [تعرف على تفادي فقدان البيانات في Microsoft Purview](dlp-learn-about-dlp.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
