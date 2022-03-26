---
title: إنشاء قاموس كلمة أساسية
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
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: تعرف على الخطوات الأساسية لإنشاء قاموس كلمات أساسية في Office 365 الأمان & التوافق.
ms.openlocfilehash: ca88c57739c8734f9fcdb5d3356a44dc6a72faa5
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/29/2022
ms.locfileid: "63566295"
---
# <a name="create-a-keyword-dictionary"></a>إنشاء قاموس كلمة أساسية

يمكن لمنع فقدان البيانات (DLP) تحديد العناصر الحساسة ومراقبتها وحمايتها. يتطلب تحديد العناصر الحساسة في بعض الأحيان البحث عن كلمات أساسية، لا سيما عند تحديد محتوى عام (مثل الاتصالات ذات الصلة بالرعاية الصحية) أو لغة غير ملائمة أو صريحة. على الرغم من أنه يمكنك إنشاء قوائم الكلمات الأساسية في أنواع المعلومات الحساسة، إلا أن حجم قوائم الكلمات الأساسية محدود وتتطلب تعديل XML لإنشاءها أو تحريرها. توفر قواميس الكلمات الأساسية إدارة أبسط للكلمات الأساسية وعلى نطاق أوسع بكثير، حيث تدعم ما يصل إلى 1MB من المصطلحات (ضغط النشر) في القاموس وتدعم أي لغة. كما أن حد المستأجر هو 1 مبايت بعد الضغط. 1 مبايت من حد ضغط النشر يعني أن كل القواميس المجمعة عبر نطاق المستأجر يمكن أن يكون لها ما يقرب من مليون حرف.

## <a name="keyword-dictionary-limits"></a>حدود قاموس الكلمات الأساسية

يوجد حد أقصى لعدد 50 نوع معلومات حساسة مستندة إلى قاموس الكلمات الأساسية يمكن إنشاؤها لكل مستأجر. لمعرفة عدد قواميس الكلمات الأساسية لديك في المستأجر، اتصل باستخدام الإجراءات في الاتصال بمركز التوافق [في & PowerShell](/powershell/exchange/connect-to-scc-powershell) للاتصال ب المستأجر وتشغيل برنامج PowerShell النصي هذا.

```powershell
$rawFile = $env:TEMP + "\rule.xml"

$kd = Get-DlpKeywordDictionary
$ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
[System.IO.File]::WriteAllBytes((Resolve-Path $rawFile), $ruleCollections.SerializedClassificationRuleCollection)
$UnicodeEncoding = New-Object System.Text.UnicodeEncoding
$FileContent = [System.IO.File]::ReadAllText((Resolve-Path $rawFile), $unicodeEncoding)

if($kd.Count -gt 0)
{
$count = 0
$entities = $FileContent -split "Entity id"
for($j=1;$j -lt $entities.Count;$j++)
{
for($i=0;$i -lt $kd.Count;$i++)
{
$Matches = Select-String -InputObject $entities[$j] -Pattern $kd[$i].Identity -AllMatches
$count = $Matches.Matches.Count + $count
if($Matches.Matches.Count -gt 0) {break}
}
}

Write-Output "Total Keyword Dictionary SIT:"
$count
}
else
{
$Matches = Select-String -InputObject $FileContent -Pattern $kd.Identity -AllMatches
Write-Output "Total Keyword Dictionary SIT:"
$Matches.Matches.Count
}

Remove-Item $rawFile
```

## <a name="basic-steps-to-creating-a-keyword-dictionary"></a>الخطوات الأساسية لإنشاء قاموس الكلمات الأساسية

يمكن أن تأتي الكلمات الأساسية للقاموس من مصادر مختلفة، غالبا من ملف (مثل قائمة .csv أو .txt) تم استيرادها في الخدمة أو بواسطة PowerShell cmdlet، أو من قائمة تقوم بإدخالها مباشرة في أمر cmdlet في PowerShell، أو من قاموس موجود. عند إنشاء قاموس كلمة أساسية، ستتبع الخطوات الأساسية نفسها:

1. استخدم <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">*مركز التوافق في Microsoft 365</a> مركز **توافق &amp; الأمان PowerShell**.

2. **تعريف الكلمات الأساسية أو تحميلها من المصدر المقصود**. يقبل المعالج و cmdlet قائمة مفصولة بفواصل من الكلمات الأساسية لإنشاء قاموس كلمات أساسية مخصص، لذلك ستختلف هذه الخطوة قليلا استنادا إلى المكان الذي تأتي منه الكلمات الأساسية. بمجرد تحميلها، يتم ترميزها وتحويلها إلى صفيف بالييت قبل استيرادها.

3. **إنشاء القاموس**. اختر اسما ووصفا وأنشئ قاموسك.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>إنشاء قاموس كلمات أساسية باستخدام مركز & الأمان

استخدم الخطوات التالية لإنشاء الكلمات الأساسية واستيرادها لقاموس مخصص:

1. الاتصال إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a>.

2. انتقل إلى **التصنيفات > الحساسة**.

3. حدد **إنشاء** **وأدخل** اسما **ووصفا لنوع** المعلومات الحساسة، ثم حدد **التالي**

4. حدد **إضافة عنصر،** ثم حدد **القاموس (الكلمات الأساسية الكبيرة)** في القائمة المنسدل كشف **المحتوى الذي يحتوي** على.

5. حدد **إضافة قاموس**

6. ضمن عنصر التحكم بحث، حدد **يمكنك إنشاء قواميس كلمات أساسية جديدة هنا**.

7. أدخل **اسما** للقاموس المخصص.

8. حدد **استيراد**، وحدد **إما من النص** أو **من csv** استنادا إلى نوع ملف الكلمة الأساسية.

9. في مربع الحوار ملف، حدد ملف الكلمة الأساسية من الكمبيوتر المحلي أو مشاركة ملف الشبكة، ثم حدد **فتح**.

10. حدد **حفظ**، ثم حدد قاموسك المخصص من قائمة **قواميس** الكلمات الأساسية.

11. حدد **إضافة**، ثم حدد **التالي**.

12. راجع تحديدات نوع المعلومات الحساسة وأكملها، ثم حدد **إنهاء**.

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>إنشاء قاموس كلمة أساسية من ملف باستخدام PowerShell

في أغلب الأحيان، عندما تحتاج إلى إنشاء قاموس كبير، يجب استخدام كلمات أساسية من ملف أو قائمة تم تصديرها من مصدر آخر. في هذه الحالة، ستنشئ قاموس كلمات أساسية يحتوي على قائمة بلغات غير ملائمة للشاشة في بريد إلكتروني خارجي. يجب أولا الاتصال [إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

1. انسخ الكلمات الأساسية إلى ملف نصي وتأكد من أن كل كلمة أساسية على سطر منفصل.

2. احفظ الملف النصي باستخدام ترميز Unicode. في المفكرة \> **حفظ باسم** \> **ترميز** \> **Unicode**.

3. اقرأ الملف في متغير عن طريق تشغيل الأمر cmdlet هذا:

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. قم بإنشاء القاموس عن طريق تشغيل الأمر cmdlet هذا:

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>استخدام قواميس الكلمات الأساسية في أنواع المعلومات الحساسة المخصصة ونهج DLP

يمكن استخدام قواميس الكلمات الأساسية كجزء من متطلبات مطابقة نوع معلومات حساسة مخصص، أو كنوع معلومات حساسة نفسها. يتطلب كلا النوعين إنشاء [نوع معلومات مخصص حساس](create-a-custom-sensitive-information-type-in-scc-powershell.md). اتبع الإرشادات الواردة في المقالة المرتبطة لإنشاء نوع معلومات حساسة. بمجرد الحصول على XML، ستحتاج إلى معرف GUID لكي يستخدمه القاموس.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

للحصول على هوية القاموس، يمكنك تشغيل هذا الأمر ونسخ **قيمة خاصية** الهوية:

```powershell
Get-DlpKeywordDictionary -Name "Diseases"
```

يبدو إخراج الأمر كما يلي:

`RunspaceId        : 138e55e7-ea1e-4f7a-b824-79f2c4252255`
`Identity          : 8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f`
`Name              : Diseases`
`Description       : Names of diseases and injuries from ICD-10-CM lexicon`
`KeywordDictionary : aarskog's syndrome, abandonment, abasia, abderhalden-kaufmann-lignac, abdominalgia, abduction contracture, abetalipo` `proteinemia, abiotrophy, ablatio, ablation, ablepharia, abocclusion, abolition, aborter, abortion, abortus, aboulomania,`
                    `abrami's disease, abramo`
`IsValid           : True`
`ObjectState       : Unchanged`

قم بلصق الهوية في XML الخاص بنوع المعلومات الحساسة المخصصة وتحميلها. سيظهر القاموس الآن في قائمة أنواع المعلومات الحساسة، كما يمكنك استخدامه مباشرة في النهج، مع تحديد عدد الكلمات الأساسية المطلوبة لمطابقتها.

```xml
<Entity id="d333c6c2-5f4c-4131-9433-db3ef72a89e8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f" />
      </Pattern>
    </Entity>
    <LocalizedStrings>
      <Resource idRef="d333c6c2-5f4c-4131-9433-db3ef72a89e8">
        <Name default="true" langcode="en-us">Diseases</Name>
        <Description default="true" langcode="en-us">Detects various diseases</Description>
      </Resource>
    </LocalizedStrings>
```

> [!NOTE]
> Microsoft 365 "حماية المعلومات" لغات مجموعة أحرف مزدوجة القامة ل:
>
> - الصينية (المبسطة)
> - الصينية (التقليدية)
> - الكورية
> - اليابانية
>
> يتوفر هذا الدعم لأنواع المعلومات الحساسة. لمزيد من المعلومات، راجع دعم حماية المعلومات المجموعات المزدوجة من الأحرف [بالية ملاحظات الإصدار (](mip-dbcs-relnotes.md) معاينة).

> [!TIP]
> للكشف عن الأنماط التي تحتوي على أحرف صينية/يابانية وأحرف بالية مفردة أو للكشف عن الأنماط التي تحتوي على الصينية/اليابانية والإنجليزية، حدد متغيرين للكلمة الأساسية أو regex.
>
> - على سبيل المثال، للكشف عن كلمة أساسية مثل "机密的الكلمة الأساسية"، استخدم متغيرين للكلمة الأساسية؛ واحد مع مسافة بين النص الياباني والنص الإنجليزي وآخر بدون مسافة بين النص الياباني والنص الإنجليزي. وبالتالي، يجب أن تكون الكلمات الأساسية التي تريد إضافتها في SIT "机密的" و"机密的document". وبالمثل، للكشف عن عبارة "東京オリンピック2020"، يجب استخدام متغيرين؛ "東京オリンピック 2020" و"東京オリンピック2020".
>
> إلى جانب الأحرف الصينية/اليابانية/مزدوجة القاموس، إذا كانت قائمة الكلمات الأساسية/العبارات تحتوي أيضا على كلمات غير صينية/يابانية أيضا (مثل الإنجليزية فقط)، فمن المستحسن إنشاء قائمتين من القواميس/الكلمات الأساسية. واحدة للكلمات الأساسية التي تحتوي على أحرف صينية/يابانية/مزدوجة باليابانية وآخر للغة الإنجليزية فقط.
>
> - على سبيل المثال، إذا كنت تريد إنشاء قاموس/قائمة كلمات أساسية مع ثلاث عبارات "سري للغاية" و"機密性が高い" و"机密的document"، يجب إنشاء قائمتين للكلمة الأساسية.
>     1. سرية إلى حد كبير
>     2. 機密性が高い 机密的 المستند 机密的 المستند
>
> أثناء إنشاء regex باستخدام الوابل المزدوج من بايت أو نقطة مزدوجة بايت، تأكد من هروب كل من الأحرف مثل تلك التي قد تفلت من الوابلة أو الفترة الزمنية في regex. فيما يلي نموذج regex للمرجع:
>
> - `(?<!\d)([４][０-９]{3}[\-?\－\t]*[０-９]{4}`
>
> نوصي باستخدام تطابق سلسلة بدلا من تطابق كلمة في قائمة الكلمات الأساسية.
