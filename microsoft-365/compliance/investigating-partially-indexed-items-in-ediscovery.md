---
title: التحقق من العناصر المفهرسة جزئيا في eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 4e8ff113-6361-41e2-915a-6338a7e2a1ed
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية إدارة العناصر المفهرسة جزئيا (تسمى أيضا العناصر غير المفهرسة) من Exchange SharePoint OneDrive for Business داخل مؤسستك.
ms.openlocfilehash: 308b99b8bcb8d11c53759700d43651e521987948
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63566506"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>التحقق من العناصر المفهرسة جزئيا في eDiscovery

يتضمن بحث eDiscovery الذي تقوم بتشغيله من مركز التوافق في Microsoft 365 تلقائيا عناصر مفهرسة جزئيا في نتائج البحث المقدرة عند تشغيل عملية بحث. العناصر المفهرسة جزئيا Exchange عناصر علبة البريد والمستندات على SharePoint ومواقع OneDrive for Business التي لم تكن مفهرسة بالكامل للبحث لسبب ما. يتم فهرسة معظم رسائل البريد الإلكتروني ومستندات الموقع بنجاح لأنها تقع ضمن حدود [الفهرسة لرسائل البريد الإلكتروني](limits-for-content-search.md#indexing-limits-for-email-messages). ومع ذلك، قد تتجاوز بعض العناصر حدود الفهرسة هذه، وستفهرس جزئيا. فيما يلي أسباب أخرى وراء عدم فهرسة العناصر للبحث وإعادتها كعنصر مفهرس جزئيا عند تشغيل بحث eDiscovery:
  
- رسائل البريد الإلكتروني بها ملف مرفق لا يمكن فتحه، مثل ملفات الصور؛ هذا هو السبب الأكثر شيوعا لعناصر البريد الإلكتروني المفهرسة جزئيا.

- عدد كبير جدا من الملفات المرفقة برسالة بريد إلكتروني.

- الملف المرفق برسالة بريد إلكتروني كبير جدا.

- يتم دعم نوع الملف للفهرسة ولكن حدث خطأ في الفهرسة لملف معين.

وعلى الرغم من أنه يختلف، فإن معظم المؤسسات التي لديها عملاء أقل من 1٪ من المحتوى حسب الحجم وأقل من 12٪ من المحتوى حسب الحجم المفهرس جزئيا. والسبب في الفرق بين الحجم والحجم هو أن الملفات الأكبر حجما لديها احتمال أكبر باحتواء محتوى لا يمكن فهرسته بالكامل.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>لماذا يتغير عدد العناصر المفهرسة جزئيا للبحث؟

بعد تشغيل عملية بحث eDiscovery، يتم سرد العدد الإجمالي للعناصر المفهرسة جزئيا وحجمها في المواقع التي تم البحث عنها في إحصائيات نتائج البحث التي يتم عرضها في الإحصائيات المفصلة للبحث. تجدر الإشارة إلى أن هذه العناصر تسمى عناصر  *غير*  موجودة في إحصائيات البحث. فيما يلي بعض الأمور التي ستؤثر على عدد العناصر المفهرسة جزئيا التي يتم إرجاعها في نتائج البحث:
  
- إذا تم فهرسة عنصر ما جزئيا وكان يتطابق مع استعلام البحث، يتم تضمينه في كل من عدد (وحجم) عناصر نتائج البحث والعناصر المفهرسة جزئيا. ومع ذلك، عند تصدير نتائج البحث نفسه، يتم تضمين العنصر مع مجموعة نتائج البحث فقط؛ ولا يتم تضمينه كعنصر مفهرس جزئيا.

- لا يتم تضمين العناصر المفهرسة جزئيا الموجودة في SharePoint ومواقع OneDrive في تقدير العناصر المفهرسة  جزئيا التي يتم عرضها في الإحصائيات المفصلة للبحث. ومع ذلك، يمكن تصدير العناصر المفهرسة جزئيا عند تصدير نتائج عملية بحث eDiscovery. على سبيل المثال، إذا كنت تبحث في المواقع فقط، فإن العدد المقدر للعناصر المفهرسة جزئيا سيكون صفرا.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>حساب نسبة العناصر المفهرسة جزئيا في مؤسستك

لفهم تعرض مؤسستك للعناصر المفهرسة جزئيا، يمكنك تشغيل بحث عن كل المحتوى في كل علب البريد (باستخدام استعلام كلمة أساسية فارغ). في المثال التالي، يوجد 1629904 (146.46 غيغابايت) عناصر مفهرسة بالكامل و10025 (10.27 غيغابايت) عناصر مفهرسة جزئيا.
  
![مثال على إحصائيات البحث التي تعرض عناصر مفهرسة جزئيا.](../media/PartiallyIndexedItemsTest.png)
  
يمكنك تحديد النسبة المئوية للعناصر المفهرسة جزئيا باستخدام العمليات الحسابية التالية.
  
 **لحساب نسبة العناصر المفهرسة جزئيا في مؤسستك:**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

باستخدام نتائج البحث من المثال السابق، يتم فهرسة 0,62٪ من كل عناصر علب البريد جزئيا.
  
 **لحساب النسبة المئوية لحجم العناصر المفهرسة جزئيا في مؤسستك:**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

وبالتالي، في المثال السابق، فإن 7٪ من إجمالي حجم عناصر علبة البريد من عناصر مفهرسة جزئيا. وكما ذكر سابقا، فإن معظم المؤسسات التي لديها عملاء أقل من 1٪ من المحتوى من حيث الحجم وأقل من 12٪ من المحتوى حسب الحجم المفهرس جزئيا.

## <a name="working-with-partially-indexed-items"></a>العمل مع عناصر مفهرسة جزئيا

في الحالات التي تحتاج فيها إلى فحص العناصر المفهرسة جزئيا للتحقق من أنها لا تحتوي على معلومات ذات صلة، يمكنك تصدير تقرير البحث في [](export-a-content-search-report.md) المحتوى الذي يحتوي على معلومات حول العناصر المفهرسة جزئيا. عند تصدير تقرير البحث في المحتوى، تأكد من اختيار أحد خيارات التصدير التي تتضمن عناصر مفهرسة جزئيا.
  
![اختر الخيار الثاني أو الثالث لتصدير العناصر المفهرسة جزئيا.](../media/PartiallyIndexedItemsExportOptions.png)
  
عند تصدير نتائج بحث eDiscovery أو تقرير بحث باستخدام أحد هذه الخيارات، يتضمن التصدير تقريرا يسمى Unindexed Items.csv. يتضمن هذا التقرير معظم المعلومات نفسها التي يتضمنها ملف ResultsLog.csv؛ ومع ذلك، يتضمن ملف unindexed Items.csv أيضا حقلين مرتبطين بالعناصر المفهرسة **جزئيا: علامات** الخطأ **وخصائص الخطأ**. تحتوي هذه الحقول على معلومات حول خطأ الفهرسة لكل عنصر مفهرس جزئيا. يمكن أن يساعدك استخدام المعلومات في هذين الحقلين في تحديد ما إذا كان خطأ الفهرسة لخطأ معين يؤثر على التحقيق أم لا. 

> [!NOTE]
> يحتوي ملف "Items.csv Unindexed" أيضا على حقول تسمى "نوع **الخطأ** " و" **رسالة الخطأ**". هذه هي الحقول القديمة التي تحتوي على معلومات مشابهة للمعلومات في الحقلين علامات الخطأ وخصائص  الخطأ، ولكن مع  معلومات أقل تفصيلا. يمكنك تجاهل هذه الحقول القديمة بأمان.
  
## <a name="errors-related-to-partially-indexed-items"></a>الأخطاء المتعلقة بالعناصر المفهرسة جزئيا

ت تطبع علامات الخطأ اثنتين من المعلومات، الخطأ ونوع الملف. على سبيل المثال، في هذا الزوج من نوع الملف/الخطأ:

```text
 parseroutputsize_xls
```

 `parseroutputsize` هو الخطأ وهو `xls` نوع الملف للملف الذي حدث فيه الخطأ. في الحالات التي `noformat` لم يتم فيها التعرف على نوع الملف أو عدم تطبيق نوع الملف على الخطأ، سترى القيمة مكان نوع الملف.
  
فيما يلي قائمة تتضمن أخطاء الفهرسة ووصفا للسبب المحتمل للخطأ.
  
| علامة الخطأ | الوصف |
|:-----|:-----|
| `attachmentcount` <br/> |كانت رسالة البريد الإلكتروني بها مرفقات كثيرة جدا، ولم تتم معالجة بعض هذه المرفقات.  <br/> |
| `attachmentdepth` <br/> |عثر مسترد المحتوى ومقفر المستندات على عدد كبير جدا من مستويات المرفقات المتداخلة داخل مرفقات أخرى. لم تتم معالجة بعض هذه المرفقات.  <br/> |
| `attachmentrms` <br/> |فشل فك تشفير المرفق لأنه محمي ب RMS.  <br/> |
| `attachmentsize` <br/> |كان الملف المرفق برسالة بريد إلكتروني كبيرا جدا ولا يمكن معالجته.  <br/> |
| `indexingtruncated` <br/> |عند كتابة رسالة البريد الإلكتروني المعالجة إلى الفهرس، كانت إحدى الخصائص القابلة للفهرسة كبيرة جدا وقد تم اقتطاعها. يتم سرد الخصائص الم اقتطاع في الحقل خصائص الخطأ.  <br/> |
| `invalidunicode` <br/> |تحتوي رسالة بريد إلكتروني على نص لا يمكن معالجته ك Unicode صالح. قد تكون الفهرسة لهذا العنصر غير مكتملة.  <br/> |
| `parserencrypted` <br/> |يتم تشفير محتوى المرفق أو رسالة البريد الإلكتروني، Microsoft 365 فك ترميز المحتوى.  <br/> |
| `parsererror` <br/> |حدث خطأ غير معروف أثناء عملية تحليل. ينتج ذلك عادة عن خطأ في البرنامج أو تعطل في الخدمة.  <br/> |
| `parserinputsize` <br/> |كان حجم المرفق كبيرا جدا حتى يمكن لمعالجه، ولم يتم تحليل هذا المرفق أو لم يتم إكماله.  <br/> |
| `parsermalformed` <br/> |تم تشوه المرفق و كان من غير المسهل معالجة من قبل الناص. يمكن أن يعود سبب هذه النتيجة إلى تنسيقات الملفات القديمة أو الملفات التي تم إنشاؤها بواسطة برامج غير متوافقة أو فيروسات تزعم أنها غير مدعية.  <br/> |
| `parseroutputsize` <br/> |كان الناتج من تحليل المرفق كبيرا جدا وكان يجب اقتطاعه.  <br/> |
| `parserunknowntype` <br/> |يحتوي المرفق على نوع ملف Microsoft 365 بالكشف.  <br/> |
| `parserunsupportedtype` <br/> |يحتوي المرفق على نوع ملف Office 365 كشفه، ولكن تحليل نوع الملف هذا غير معتمد.  <br/> |
| `propertytoobig` <br/> |كانت قيمة خاصية البريد الإلكتروني في Exchange أكبر من اللازم لا يمكن استردادها ولا يمكن معالجة الرسالة. يحدث هذا عادة فقط للممتلكات الأصلية لرسالة بريد إلكتروني.  <br/> |
| `retrieverrms` <br/> |فشل استرداد المحتوى في فك ترميز رسالة محمية ب RMS.  <br/> |
| `wordbreakertruncated` <br/> |تم تحديد عدد كبير جدا من الكلمات في المستند أثناء الفهرسة. توقفت معالجة الخاصية عند بلوغ الحد، في حين يتم اقتطاع الخاصية.  <br/> |

تصف حقول الخطأ الحقول المتأثرة بخطأ المعالجة المدرج في الحقل علامات الخطأ. إذا كنت تبحث عن  `subject`  `participants`خاصية مثل أو ، فلن تؤثر الأخطاء في نص الرسالة على نتائج البحث. قد يكون هذا الأمر مفيدا عند تحديد العناصر المفهرسة جزئيا التي قد تحتاج إلى إجراء المزيد من التحقق منها.
  
## <a name="using-a-powershell-script-to-determine-your-organizations-exposure-to-partially-indexed-email-items"></a>استخدام برنامج PowerShell النصي لتحديد تعرض مؤسستك لعناصر البريد الإلكتروني المفهرسة جزئيا

تظهر لك الخطوات التالية كيفية تشغيل برنامج PowerShell النصي الذي يبحث عن كل العناصر في كل علب بريد Exchange، ثم ينشئ تقريرا حول نسبة عناصر البريد الإلكتروني المفهرسة جزئيا في مؤسستك (حسب العدد والحجم) ويعرض عدد العناصر (ونوع الملف الخاص بها) لكل خطأ فهرسة يحدث. استخدم أوصاف علامة الخطأ في المقطع السابق لتحديد خطأ الفهرسة.
  
1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `PartiallyIndexedItems.ps1`.

   ```powershell
     write-host "**************************************************"
     write-host "     Security & Compliance Center PowerShell      " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "   eDiscovery Partially Indexed Item Statistics   " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "**************************************************"
     " " 
     # Create a search with Error Tags Refinders enabled
     Remove-ComplianceSearch "RefinerTest" -Confirm:$false -ErrorAction 'SilentlyContinue'
     New-ComplianceSearch -Name "RefinerTest" -ContentMatchQuery "size>0" -RefinerNames ErrorTags -ExchangeLocation ALL
     Start-ComplianceSearch "RefinerTest"
     # Loop while search is in progress
     do{
         Write-host "Waiting for search to complete..."
         Start-Sleep -s 5
         $complianceSearch = Get-ComplianceSearch "RefinerTest"
     }while ($complianceSearch.Status -ne 'Completed')
     $refiners = $complianceSearch.Refiners | ConvertFrom-Json
     $errorTagProperties = $refiners.Entries | Get-Member -MemberType NoteProperty
     $partiallyIndexedRatio = $complianceSearch.UnindexedItems / $complianceSearch.Items
     $partiallyIndexedSizeRatio = $complianceSearch.UnindexedSize / $complianceSearch.Size
     " "
     "===== Partially indexed items ====="
     "         Total          Ratio"
     "Count    {0:N0}{1:P2}" -f $complianceSearch.Items.ToString("N0").PadRight(15, " "), $partiallyIndexedRatio
     "Size(GB) {0:N2}{1:P2}" -f ($complianceSearch.Size / 1GB).ToString("N2").PadRight(15, " "), $partiallyIndexedSizeRatio
     " "
     Write-Host ===== Reasons for partially indexed items =====
     foreach($errorTagProperty in $errorTagProperties)
     {
         $name = $refiners.Entries.($errorTagProperty.Name).Name
         $count = $refiners.Entries.($errorTagProperty.Name).TotalCount
         $frag = $name.Split("{_}")
         $errorTag = $frag[0]
         $fileType = $frag[1]
         if ($errorTag -ne $lastErrorTag)
         {
             $errorTag
         }
         "    " + $fileType + " => " + $count
         $lastErrorTag = $errorTag
     }
   ```

2. [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/exchange-online-powershell).

3. في Security & Compliance Center PowerShell، انتقل إلى المجلد حيث حفظت البرنامج النصي في الخطوة 1، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

فيما يلي مثال على الإخراج الذي يتم إرجاعه بواسطة البرنامج النصي.
  
![مثال للإخراج من البرنامج النصي الذي ينشئ تقريرا حول تعرض مؤسستك لعناصر البريد الإلكتروني المفهرسة جزئيا.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> لاحظ ما يلي:
>  
> - العدد الإجمالي لعناصر البريد الإلكتروني وحجمها ونسبة مؤسستك لعناصر البريد الإلكتروني المفهرسة جزئيا (حسب العدد والحجم).
> 
> - علامات خطأ قائمة وأنواع الملفات المطابقة التي حدث الخطأ فيها.
  
## <a name="see-also"></a>راجع أيضًا

[العناصر المفهرسة جزئيا في eDiscovery](partially-indexed-items-in-content-search.md)
