---
title: نسخ بحث في المحتوى
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 4/26/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 7b40eeaa-544c-4534-b89b-9f79998e374c
ms.custom:
- seo-marvel-apr2020
description: استخدم البرنامج النصي PowerShell في هذه المقالة لاستنساخ بحث محتوى موجود في مركز التوافق في Office 365 أو Microsoft 365.
ms.openlocfilehash: 763bd6ac49841e5b55bbbc187631ef74426d9d0a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568546"
---
# <a name="clone-a-content-search"></a>نسخ بحث في المحتوى

قد يستغرق إنشاء "البحث في المحتوى" في مركز التوافق Office 365 أو Microsoft 365 الذي يبحث في العديد من علب البريد أو SharePoint OneDrive for Business المواقع بعض الوقت. قد يكون تحديد المواقع التي تريد البحث عنها عرضة للأخطاء أيضا إذا أخطأت في استخدام عنوان URL. لتجنب هذه المشاكل، يمكنك استخدام البرنامج النصي Windows PowerShell في هذه المقالة لاستنساخ بحث محتوى موجود بسرعة. عند نسخ عملية بحث، يتم إنشاء بحث جديد (باسم مختلف) يحتوي على الخصائص نفسها (مثل مواقع المحتوى واستعلام البحث) كالبحث الأصلي. بعد ذلك، يمكنك تحرير البحث الجديد عن طريق تغيير استعلام الكلمة الأساسية أو نطاق التاريخ وتشغيله.
  
لماذا تستنسخ عمليات البحث في المحتوى؟
  
- لمقارنة نتائج استعلامات بحث الكلمات الأساسية المختلفة التي يتم تشغيلها على مواقع المحتوى نفسها.
    
- لحفظك من الحاجة إلى إعادة استخدام عدد كبير من مواقع المحتوى عند إنشاء بحث جديد.
    
- لتقليل حجم نتائج البحث. على سبيل المثال، إذا كان لديك بحث يرجع نتائج كثيرة جدا لتصديرها، يمكنك نسخ البحث ثم إضافة شرط بحث استنادا إلى نطاق تاريخ لتقليل عدد نتائج البحث.
  
## <a name="script-information"></a>معلومات البرنامج النصي

- يجب أن تكون عضوا في مجموعة دور مدير eDiscovery في مركز التوافق في Microsoft 365 لتشغيل البرنامج النصي الموضح في هذا الموضوع.
    
- يتضمن البرنامج النصي الحد الأدنى من معالجة الأخطاء. الغرض الأساسي من البرنامج النصي هو نسخ عملية البحث في المحتوى بسرعة.
    
- ينشئ البرنامج النصي "بحث محتوى" جديد، ولكنه لا يبدأه.
    
- يأخذ هذا البرنامج النصي في الاعتبار ما إذا كان البحث في المحتوى الذي تقوم باستخدامه مقترن مع حالة eDiscovery. إذا كان البحث مقترن بقضيه، سيتم أيضا إقترن البحث الجديد بنفس الحالة. إذا لم يكن البحث الموجود مقترن بأحراج، سيتم إدراج البحث الجديد في صفحة البحث في المحتوى  في مركز التوافق. 
    
- البرنامج النصي النموذجي الموفر في هذا الموضوع غير معتمد ضمن أي برنامج أو خدمة دعم قياسية من Microsoft. يتم توفير البرنامج النصي النموذجي AS IS بدون ضمان من أي نوع. وتنقر Microsoft أيضا عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية ل قابلية الاستخدام أو اللياقة لغرض معين. يبقى الخطر بأكمله الناتج عن استخدام أو أداء البرنامج النصي النموذجي والوثائق معك. لا تتحمل Microsoft بأي حال من الأحوال، أو كتابها، أو أي شخص آخر يشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها المسؤولية عن أي أضرار أيا كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن خسارة أرباح الأعمال أو انقطاع الأعمال أو فقدان معلومات العمل أو أي خسارة مادية أخرى) الناشئة عن استخدام البرامج النصية أو الوثائق العينة أو عدم القدرة على استخدامها،  حتى لو تم نصح Microsoft بإمكانية حدوث مثل هذه الأضرار.
  
## <a name="step-1-run-the-script-to-clone-a-search"></a>الخطوة 1: تشغيل البرنامج النصي لاستنساخ عملية بحث

سينشئ البرنامج النصي في هذه الخطوة "بحث محتوى" جديد عن طريق استعمار بحث موجود. عند تشغيل هذا البرنامج النصي، سيطلب منك الحصول على المعلومات التالية:
  
- **بيانات اعتماد المستخدم** - سيستخدم البرنامج النصي بيانات الاعتماد للاتصال بمركز & التوافق PowerShell. كما ذكرنا سابقا، يجب أن تكون عضوا في مجموعة دور مدير eDiscovery في مركز & compliance لتشغيل البرنامج النصي. 
    
- **اسم البحث الموجود** - هذا هو بحث المحتوى الذي تريد نسخه. 
    
- اسم البحث الجديد الذي سيتم **إنشاؤه - إذا** تركت هذه القيمة فارغة، سينشئ البرنامج النصي اسما للبحث الجديد الذي يستند إلى اسم البحث الذي تقوم به. 
    
لاستنساخ عملية بحث:
  
1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `CloneSearch.ps1`.
    
  ```powershell
  # This PowerShell script clones an existing content search in the Security &amp; Compliance Center.
  # Get login credentials from the user
  if(!$UserCredential)
  {
      $UserCredential = Get-Credential
      $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
      if (!$Session)
      {
          Write-Error "Couldn't create a remote PowerShell session."
          return
      }
      Import-PSSession $Session -AllowClobber -DisableNameChecking
      $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Security & Compliance Center)"
  }
  # Ask for the name of the search you want to clone
  $searchName = Read-Host 'Enter the name of the search that you want to clone'
  # Ask for the name of the new search
  $newSearchName = Read-Host 'Enter a name for the new search [leave blank to automatically generate a name]'
  $originalSearch = Get-ComplianceSearch $searchName -EA SilentlyContinue
  # Make sure we have a valid search before continuing
  if(!$originalSearch)
  {
      Write-Error "Couldn't find search: $searchName"
      return
  }
  $searchNameCounter = 1
  # Find a suitable name for the new search
  while(!$newSearchName)
  {
      $newSearchName = $originalSearch.Name + "_" + $searchNameCounter
      $tempSearch = Get-ComplianceSearch $newSearchName -EA SilentlyContinue
      if ($tempSearch)
      {
          $newSearchName = $null
          $searchNameCounter++
      }
  }
  $caseName
  # Determine if the search is part of a case; if so get the case name
  if ($originalSearch.CaseId)
  {
      $searchCase = Get-ComplianceCase $originalSearch.CaseId
      $caseName = $searchCase.Name
  }
  # Need to cast this value as a Boolean the old fashion way
  $allowNotFoundExchangeLocationsEnabled = $false
  if ($originalSearch.AllowNotFoundExchangeLocationsEnabled)
  {
      $allowNotFoundExchangeLocationsEnabled = $true
  }
  $newSearch = New-ComplianceSearch -Name $newSearchName -AllowNotFoundExchangeLocationsEnabled $allowNotFoundExchangeLocationsEnabled -Case $caseName -ContentMatchQuery $originalSearch.ContentMatchQuery -Description $originalSearch.Description -ExchangeLocation $originalSearch.ExchangeLocation -ExchangeLocationExclusion $originalSearch.ExchangeLocationExclusion -Language $originalSearch.Language -SharePointLocation $originalSearch.SharePointLocation -SharePointLocationExclusion $originalSearch.SharePointLocationExclusion -PublicFolderLocation $originalSearch.PublicFolderLocation
  if ($newSearch)
  {
      Write-Host $newSearch.Name "was successfully created" -ForegroundColor Yellow
  }
  ```

2. افتح Windows PowerShell واذهب إلى المجلد حيث حفظت البرنامج النصي.
    
3. تشغيل البرنامج النصي؛ على سبيل المثال:
    
    ```powershell
    .\CloneSearch.ps1
    ```

4. عند مطالبتك بإدخال بيانات الاعتماد، أدخل عنوان البريد الإلكتروني وكلمة المرور، ثم انقر فوق **موافق**.
    
5. أدخل المعلومات التالية عند مطالبتك بها بواسطة البرنامج النصي. اكتب كل معلومة، ثم اضغط على **Enter**.
    
    - اسم البحث الموجود.
    
    - اسم البحث الجديد.
    
    ينشئ البرنامج النصي "البحث في المحتوى" الجديد، ولكنه لا يبدأه. يمنحك هذا الأمر فرصة لتحرير البحث وتشغيله في الخطوة التالية. يمكنك عرض خصائص البحث الجديد عن طريق تشغيل **الأمر Cmdlet البحث عن Get-ComplianceSearch** أو عن طريق الذهاب إلى صفحة  بحث المحتوى أو **eDiscovery** في مركز التوافق، استنادا إلى ما إذا كان البحث الجديد مقترن بقضية ما. 
  
## <a name="step-2-edit-and-run-the-cloned-search-in-the-compliance-center"></a>الخطوة 2: تحرير البحث المستنسخ وتشغيله في مركز التوافق

بعد تشغيل البرنامج النصي لاستنساخ بحث محتوى موجود، تكون الخطوة التالية هي الانتقال إلى مركز التوافق لتحرير البحث الجديد وتشغيله. كما ذكر سابقا، يمكنك تحرير بحث عن طريق تغيير استعلام البحث عن الكلمات الأساسية وإضافة شروط البحث أو إزالتها. لمزيد من المعلومات، اطلع على:
  
- [البحث في المحتوى في Office 365](content-search.md)
    
- [استعلامات الكلمات الأساسية وشروط البحث في البحث في المحتوى](keyword-queries-and-search-conditions.md)
    
- [حالات eDiscovery](./get-started-core-ediscovery.md)