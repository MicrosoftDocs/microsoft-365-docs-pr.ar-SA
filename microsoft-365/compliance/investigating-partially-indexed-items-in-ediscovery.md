---
title: التحقق من العناصر المفهرسة جزئيا في eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
ms.openlocfilehash: 03d68a02765a85066e41ba2b4dee54441d971190
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077915"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>التحقق من العناصر المفهرسة جزئيا في eDiscovery

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يتضمن بحث eDiscovery الذي تقوم بتشغيله من مدخل توافق Microsoft Purview تلقائيا عناصر مفهرسة جزئيا في نتائج البحث المقدرة عند تشغيل عملية بحث. العناصر المفهرسة جزئيا هي Exchange عناصر علبة البريد والمستندات على SharePoint ومواقع OneDrive for Business التي لم تتم فهرستها بشكل كامل للبحث لسبب ما. تمت فهرسة معظم رسائل البريد الإلكتروني ومستندات الموقع بنجاح لأنها تقع ضمن [حدود الفهرسة لرسائل البريد الإلكتروني](limits-for-content-search.md#indexing-limits-for-email-messages). ومع ذلك، قد تتجاوز بعض العناصر حدود الفهرسة هذه، وسيتم فهرستها جزئيا. فيما يلي أسباب أخرى لعدم إمكانية فهرسة العناصر للبحث وإرجاعها كعناصر مفهرسة جزئيا عند تشغيل بحث eDiscovery:
  
- تحتوي رسائل البريد الإلكتروني على ملف مرفق لا يمكن فتحه، مثل ملفات الصور؛ هذا هو السبب الأكثر شيوعا لعناصر البريد الإلكتروني المفهرسة جزئيا.

- عدد الملفات المرفقة برسالة بريد إلكتروني كبير جدا.

- ملف مرفق برسالة بريد إلكتروني كبير جدا.

- نوع الملف معتمد للفهرسة ولكن حدث خطأ فهرسة لملف معين.

على الرغم من اختلافه، فإن معظم عملاء المؤسسات لديهم أقل من 1٪ من المحتوى حسب وحدة التخزين وأقل من 12٪ من المحتوى حسب الحجم الذي تتم فهرسته جزئيا. السبب في الفرق بين وحدة التخزين مقابل الحجم هو أن الملفات الكبيرة لديها احتمال أعلى لاحتواء محتوى لا يمكن فهرسته بالكامل.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>لماذا يتغير عدد العناصر المفهرسة جزئيا للبحث؟

بعد تشغيل بحث eDiscovery، يتم سرد العدد الإجمالي للعناصر المفهرسة جزئيا وحجمها في المواقع التي تم البحث فيها في إحصائيات نتائج البحث التي يتم عرضها في الإحصائيات المفصلة للبحث. لاحظ أن هذه العناصر تسمى  *العناصر غير المفهرسة*  في إحصائيات البحث. فيما يلي بعض الأشياء التي ستؤثر على عدد العناصر المفهرسة جزئيا التي يتم إرجاعها في نتائج البحث:
  
- إذا تمت فهرسة عنصر ما جزئيا وتطابق استعلام البحث، يتم تضمينه في كل من عدد (وحجم) عناصر نتائج البحث والعناصر المفهرسة جزئيا. ومع ذلك، عند تصدير نتائج البحث نفسه، يتم تضمين العنصر فقط مع مجموعة من نتائج البحث؛ لا يتم تضمينه كعنصر مفهرس جزئيا.

- *لا يتم* تضمين العناصر المفهرسة جزئيا الموجودة في مواقع SharePoint OneDrive في تقدير العناصر المفهرسة جزئيا التي يتم عرضها في الإحصائيات المفصلة للبحث. ومع ذلك، يمكن تصدير العناصر المفهرسة جزئيا عند تصدير نتائج بحث eDiscovery. على سبيل المثال، إذا قمت بالبحث في المواقع فقط، فسيكون العدد المقدر للعناصر المفهرسة جزئيا صفرا.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>حساب نسبة العناصر المفهرسة جزئيا في مؤسستك

لفهم تعرض مؤسستك للعناصر المفهرسة جزئيا، يمكنك تشغيل بحث عن كل المحتوى في كل علب البريد (باستخدام استعلام كلمة أساسية فارغ). في المثال التالي، هناك 1629904 (146.46 غيغابايت) عناصر مفهرسة بالكامل و10025 (10.27 غيغابايت) عناصر مفهرسة جزئيا.
  
![مثال على إحصائيات البحث التي تعرض عناصر مفهرسة جزئيا.](../media/PartiallyIndexedItemsTest.png)
  
يمكنك تحديد النسبة المئوية للعناصر المفهرسة جزئيا باستخدام العمليات الحسابية التالية.
  
 **لحساب نسبة العناصر المفهرسة جزئيا في مؤسستك:**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

باستخدام نتائج البحث من المثال السابق، تتم فهرسة 0.62٪ من كافة عناصر علب البريد بشكل جزئي.
  
 **لحساب النسبة المئوية لحجم العناصر المفهرسة جزئيا في مؤسستك:**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

لذلك في المثال السابق، 7٪ من الحجم الإجمالي لعناصر علبة البريد من عناصر مفهرسة جزئيا. كما ذكر سابقا، فإن معظم عملاء المؤسسات لديهم أقل من 1٪ من المحتوى حسب وحدة التخزين وأقل من 12٪ من المحتوى حسب الحجم الذي تتم فهرسته جزئيا.

## <a name="working-with-partially-indexed-items"></a>العمل مع عناصر مفهرسة جزئيا

في الحالات التي تحتاج فيها إلى فحص العناصر المفهرسة جزئيا للتحقق من أنها لا تحتوي على معلومات ذات صلة، يمكنك [تصدير تقرير بحث محتوى](export-a-content-search-report.md) يحتوي على معلومات حول العناصر المفهرسة جزئيا. عند تصدير تقرير البحث في المحتوى، تأكد من اختيار أحد خيارات التصدير التي تتضمن عناصر مفهرسة جزئيا.
  
![اختر الخيار الثاني أو الثالث لتصدير العناصر المفهرسة جزئيا.](../media/PartiallyIndexedItemsExportOptions.png)
  
عند تصدير نتائج بحث eDiscovery أو تقرير بحث باستخدام أحد هذه الخيارات، يتضمن التصدير تقريرا يسمى Unindexed Items.csv. يتضمن هذا التقرير معظم المعلومات نفسها التي يتضمنها ملف ResultsLog.csv؛ ومع ذلك، يتضمن ملف Items.csv Unindexed أيضا حقلين مرتبطين بالعناصر المفهرسة جزئيا: **علامات الخطأ** **وخصائص الخطأ**. تحتوي هذه الحقول على معلومات حول خطأ الفهرسة لكل عنصر مفهرس جزئيا. يمكن أن يساعدك استخدام المعلومات الموجودة في هذين الحقلين في تحديد ما إذا كان خطأ الفهرسة لجهة معينة يؤثر على التحقيق أم لا. 

> [!NOTE]
> يحتوي ملف Items.csv Unindexed أيضا على حقول تسمى **نوع الخطأ** **ورسالة الخطأ**. هذه هي الحقول القديمة التي تحتوي على معلومات مشابهة للمعلومات الموجودة في **الحقلين "علامات الخطأ"** و **"خصائص الخطأ** "، ولكن مع معلومات أقل تفصيلا. يمكنك تجاهل هذه الحقول القديمة بأمان.
  
## <a name="errors-related-to-partially-indexed-items"></a>الأخطاء المتعلقة بالعناصر المفهرسة جزئيا

تتكون علامات الخطأ من قطعتين من المعلومات، الخطأ ونوع الملف. على سبيل المثال، في زوج نوع الملف/الخطأ هذا:

```text
 parseroutputsize_xls
```

 `parseroutputsize` هو الخطأ وهو `xls` نوع ملف الملف الذي حدث فيه الخطأ. في الحالات التي لم يتم فيها التعرف على نوع الملف أو لم يتم تطبيق نوع الملف على الخطأ، سترى القيمة `noformat` بدلا من نوع الملف.
  
فيما يلي قائمة بأخطاء الفهرسة ووصف للسبب المحتمل للخطأ.
  
| علامة الخطأ | الوصف |
|:-----|:-----|
| `attachmentcount` <br/> |تحتوي رسالة البريد الإلكتروني على عدد كبير جدا من المرفقات، ولم تتم معالجة بعض هذه المرفقات.  <br/> |
| `attachmentdepth` <br/> |عثر مسترد المحتوى وموزع المستند على مستويات كثيرة جدا من المرفقات المتداخلة داخل مرفقات أخرى. لم تتم معالجة بعض هذه المرفقات.  <br/> |
| `attachmentrms` <br/> |فشل فك ترميز المرفق لأنه كان محميا بواسطة RMS.  <br/> |
| `attachmentsize` <br/> |ملف مرفق برسالة بريد إلكتروني كبير جدا ويتعذر معالجته.  <br/> |
| `indexingtruncated` <br/> |عند كتابة رسالة البريد الإلكتروني التي تمت معالجتها إلى الفهرس، كانت إحدى الخصائص القابلة للفهرسة كبيرة جدا وتم اقتطاعها. يتم سرد الخصائص التي تم اقتطاعها في الحقل "خصائص الخطأ".  <br/> |
| `invalidunicode` <br/> |تحتوي رسالة بريد إلكتروني على نص تعذرت معالجته ك Unicode صالح. قد تكون الفهرسة لهذا العنصر غير مكتملة.  <br/> |
| `parserencrypted` <br/> |يتم تشفير محتوى المرفق أو رسالة البريد الإلكتروني، ويتعذر على Microsoft 365 فك ترميز المحتوى.  <br/> |
| `parsererror` <br/> |حدث خطأ غير معروف أثناء التوزيع. ينتج هذا عادة عن خطأ في البرنامج أو تعطل الخدمة.  <br/> |
| `parserinputsize` <br/> |كان المرفق كبيرا جدا بحيث يتعذر على المحلل التعامل معه، ولم يتم تحليل هذا المرفق أو لم يكتمل.  <br/> |
| `parsermalformed` <br/> |تم تكوين مرفق بشكل غير صحيح وتعذرت معالجته بواسطة المحلل. يمكن أن تكون هذه النتيجة بسبب تنسيقات الملفات القديمة أو الملفات التي تم إنشاؤها بواسطة برامج غير متوافقة أو فيروسات تتظاهر بأنها شيء آخر غير المطالب به.  <br/> |
| `parseroutputsize` <br/> |كان الإخراج من تحليل مرفق كبيرا جدا ويجب اقتطاعه.  <br/> |
| `parserunknowntype` <br/> |يتضمن المرفق نوع ملف لم يتمكن Microsoft 365 من اكتشافه.  <br/> |
| `parserunsupportedtype` <br/> |يحتوي المرفق على نوع ملف يمكن Office 365 اكتشافه، ولكن تحليل نوع الملف هذا غير معتمد.  <br/> |
| `propertytoobig` <br/> |كانت قيمة خاصية البريد الإلكتروني في Exchange Store كبيرة جدا بحيث يتعذر استردادها وتعذرت معالجة الرسالة. يحدث هذا عادة فقط لخاصية النص الأساسي لرسالة بريد إلكتروني.  <br/> |
| `retrieverrms` <br/> |فشل مسترد المحتوى في فك ترميز رسالة محمية بواسطة RMS.  <br/> |
| `wordbreakertruncated` <br/> |تم تحديد عدد كبير جدا من الكلمات في المستند أثناء الفهرسة. توقفت معالجة الخاصية عند الوصول إلى الحد، ويتم اقتطاع الخاصية.  <br/> |

تصف حقول الخطأ الحقول المتأثرة بخطأ المعالجة المدرج في الحقل "علامات الخطأ". إذا كنت تبحث عن خاصية مثل  `subject` أو  `participants`، فلن تؤثر الأخطاء في النص الأساسي للرسالة على نتائج البحث. يمكن أن يكون هذا مفيدا عند تحديد العناصر المفهرسة جزئيا التي قد تحتاج إلى مزيد من التحقيق.
  
## <a name="using-a-powershell-script-to-determine-your-organizations-exposure-to-partially-indexed-email-items"></a>استخدام برنامج نصي PowerShell لتحديد تعرض مؤسستك لعناصر البريد الإلكتروني المفهرسة جزئيا

توضح لك الخطوات التالية كيفية تشغيل برنامج نصي PowerShell يبحث عن كافة العناصر في كل علب بريد Exchange، ثم ينشئ تقريرا حول نسبة عناصر البريد الإلكتروني المفهرسة جزئيا في مؤسستك (حسب العدد والحجم) ويعرض عدد العناصر (ونوع الملف الخاص بها) لكل خطأ فهرسة يحدث. استخدم أوصاف علامة الخطأ في القسم السابق لتحديد خطأ الفهرسة.
  
1. احفظ النص التالي إلى ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `PartiallyIndexedItems.ps1`.

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

2. [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/exchange-online-powershell).

3. في Security & Compliance Center PowerShell، انتقل إلى المجلد حيث قمت بحفظ البرنامج النصي في الخطوة 1، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

فيما يلي مثال على الإخراج الذي تم إرجاعه بواسطة البرنامج النصي.
  
![مثال على الإخراج من البرنامج النصي الذي ينشئ تقريرا حول تعرض مؤسستك لعناصر البريد الإلكتروني المفهرسة جزئيا.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> لاحظ ما يلي:
>  
> - العدد الإجمالي لعناصر البريد الإلكتروني وحجمها ونسبة عناصر البريد الإلكتروني المفهرسة جزئيا في مؤسستك (حسب العدد والحجم).
> 
> - علامات خطأ قائمة وأنواع الملفات المقابلة التي حدث فيها الخطأ.
  
## <a name="see-also"></a>راجع أيضًا

[العناصر المفهرسة جزئيا في eDiscovery](partially-indexed-items-in-content-search.md)
