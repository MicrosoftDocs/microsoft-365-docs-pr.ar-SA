---
title: استنساخ البحث في المحتوى
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: استخدم البرنامج النصي PowerShell في هذه المقالة لاستنساخ بحث محتوى موجود بسرعة في مدخل التوافق في Microsoft Purview في Microsoft 365.
ms.openlocfilehash: 806705202865d97136713dba4afb263b605ef0f8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628804"
---
# <a name="clone-a-content-search"></a>استنساخ البحث في المحتوى

قد يستغرق إنشاء "البحث في المحتوى" في مدخل التوافق في Microsoft Purview في Microsoft 365 الذي يبحث في العديد من علب البريد أو SharePoint ومواقع OneDrive for Business بعض الوقت. يمكن أيضا أن يكون تحديد المواقع المراد البحث فيها عرضة للأخطاء إذا أخطأت في كتابة عنوان URL. لتجنب هذه المشاكل، يمكنك استخدام البرنامج النصي Windows PowerShell في هذه المقالة لاستنساخ بحث محتوى موجود بسرعة. عند استنساخ بحث، يتم إنشاء بحث جديد (باسم مختلف) يحتوي على نفس الخصائص (مثل مواقع المحتوى واستعلام البحث) مثل البحث الأصلي. ثم يمكنك تحرير البحث الجديد عن طريق تغيير استعلام الكلمة الأساسية أو نطاق التاريخ وتشغيله.

لماذا استنساخ عمليات البحث في المحتوى؟

- لمقارنة نتائج استعلامات بحث الكلمات الأساسية المختلفة التي يتم تشغيلها على مواقع المحتوى نفسها.

- لحفظك من الاضطرار إلى إعادة إدخال عدد كبير من مواقع المحتويات عند إنشاء بحث جديد.

- لتقليل حجم نتائج البحث. على سبيل المثال، إذا كان لديك بحث يرجع نتائج كثيرة جدا لتصديرها، يمكنك نسخ البحث ثم إضافة شرط بحث استنادا إلى نطاق تاريخ لتقليل عدد نتائج البحث.

## <a name="script-information"></a>معلومات البرنامج النصي

- تحتاج إلى تثبيت الوحدة النمطية Exchange Online V2. للحصول على الإرشادات، راجع [تثبيت وحدة EXO V2 وصيانتها](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

- يجب أن تكون عضوا في مجموعة دور eDiscovery Manager في مدخل التوافق في Microsoft Purview لتشغيل البرنامج النصي الموضح في هذا الموضوع.

- يتضمن البرنامج النصي الحد الأدنى من معالجة الأخطاء. الغرض الأساسي من البرنامج النصي هو استنساخ بحث المحتوى بسرعة.

- يقوم البرنامج النصي بإنشاء بحث محتوى جديد، ولكنه لا يبدأه.

- يأخذ هذا البرنامج النصي في الاعتبار ما إذا كان البحث في المحتوى الذي تقوم بنسخه مقترنا بحالة eDiscovery. إذا كان البحث مقترنا بحالة، فسيتم أيضا إقران البحث الجديد بنفس الحالة. إذا لم يكن البحث الموجود مقترنا بحالة، فسيتم إدراج البحث الجديد في صفحة **البحث في المحتوى** في مدخل التوافق في Microsoft Purview.

- البرنامج النصي النموذجي المتوفر في هذا الموضوع غير معتمد ضمن أي برنامج دعم أو خدمة قياسية من Microsoft. يتم توفير نموذج البرنامج النصي AS IS دون ضمان من أي نوع. وتخلي Microsoft المزيد من المسؤولية عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية لقابلية تجارية أو للياقة لغرض معين. يبقى الخطر بأكمله الناشئ عن استخدام أو أداء نموذج البرنامج النصي والوثائق معك. لن تتحمل شركة Microsoft أو كتابها أو أي شخص آخر مشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها مسؤولية أي أضرار مهما كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن فقدان أرباح الأعمال أو انقطاع العمل أو فقدان معلومات العمل أو أي خسارة في المالية الأخرى) الناتجة عن استخدام نماذج البرامج النصية أو الوثائق أو عدم القدرة على استخدامها،  حتى إذا تم إعلام Microsoft باحتمال حدوث مثل هذه الأضرار.

## <a name="step-1-run-the-script-to-clone-a-search"></a>الخطوة 1: تشغيل البرنامج النصي لاستنساخ بحث

سيقوم البرنامج النصي في هذه الخطوة بإنشاء بحث محتوى جديد عن طريق نسخ بحث موجود. عند تشغيل هذا البرنامج النصي، ستتم مطالبتك بالمعلومات التالية:

- **بيانات اعتماد المستخدم -** سيستخدم البرنامج النصي بيانات الاعتماد الخاصة بك للاتصال ب Security & Compliance PowerShell. كما ذكر سابقا، يجب أن تكون عضوا في مجموعة دور eDiscovery Manager في مدخل التوافق في Microsoft Purview لتشغيل البرنامج النصي.

- **اسم البحث الموجود** - هذا هو البحث عن المحتوى الذي تريد نسخه.

- **اسم البحث الجديد الذي سيتم إنشاؤه** - إذا تركت هذه القيمة فارغة، فسينشئ البرنامج النصي اسما للبحث الجديد الذي يستند إلى اسم البحث الذي تقوم بنسخه.

لاستنساخ بحث:

1. احفظ النص التالي إلى ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `CloneSearch.ps1`.

   ```powershell
   # This PowerShell script clones an existing content search in Microsoft Purview compliance.

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

2. [الاتصال ب Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell). في نفس نافذة PowerShell، انتقل إلى المجلد حيث قمت بحفظ البرنامج النصي.

3. تشغيل البرنامج النصي؛ على سبيل المثال:

     ```powershell
     .\CloneSearch.ps1
     ```

4. أدخل المعلومات التالية عند مطالبتك من قبل البرنامج النصي. اكتب كل جزء من المعلومات ثم اضغط على **مفتاح الإدخال Enter**.

     - اسم البحث الموجود.
     - اسم البحث الجديد.

     ينشئ البرنامج النصي البحث عن المحتوى الجديد، ولكنه لا يبدأه. يمنحك هذا فرصة لتحرير البحث وتشغيله في الخطوة التالية. يمكنك عرض خصائص البحث الجديد عن طريق تشغيل **الأمر cmdlet Get-ComplianceSearch** أو بالانتقال إلى صفحة **البحث في المحتوى** أو **eDiscovery** في مدخل التوافق في Microsoft Purview، استنادا إلى ما إذا كان البحث الجديد مقترنا بحالة.

## <a name="step-2-edit-and-run-the-cloned-search-in-the-microsoft-purview-compliance-portal"></a>الخطوة 2: تحرير البحث المستنسخ وتشغيله في مدخل التوافق في Microsoft Purview

بعد تشغيل البرنامج النصي لاستنساخ بحث محتوى موجود، فإن الخطوة التالية هي الانتقال إلى مدخل التوافق في Microsoft Purview لتحرير البحث الجديد وتشغيله. كما ذكر سابقا، يمكنك تحرير بحث عن طريق تغيير استعلام البحث عن الكلمة الأساسية وإضافة شروط البحث أو إزالتها. لمزيد من المعلومات، اطلع على:

- [البحث عن المحتوى في Office 365](content-search.md)

- [استعلامات الكلمات الأساسية وشروط البحث في البحث عن المحتوى](keyword-queries-and-search-conditions.md)

- [حالات eDiscovery](./get-started-core-ediscovery.md)
