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
description: تعرف على الخطوات الأساسية لإنشاء قاموس كلمات أساسية في Office 365 Security & Compliance Center.
ms.openlocfilehash: 64e431b5d2ef01e85eff55f39f4436786f45664b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758586"
---
# <a name="create-a-keyword-dictionary"></a>إنشاء قاموس كلمة أساسية

يمكن لمنع فقدان البيانات (DLP) تحديد العناصر الحساسة ومراقبتها وحمايتها. يتطلب تحديد العناصر الحساسة في بعض الأحيان البحث عن كلمات أساسية، خاصة عند تحديد محتوى عام (مثل الاتصال المتعلق بالرعاية الصحية) أو لغة غير ملائمة أو صريحة. على الرغم من أنه يمكنك إنشاء قوائم الكلمات الأساسية في أنواع المعلومات الحساسة، إلا أن حجم قوائم الكلمات الأساسية محدود وتتطلب تعديل XML لإنشائها أو تحريرها. توفر قواميس الكلمات الأساسية إدارة أبسط للكلمات الأساسية وعلى نطاق أكبر بكثير، حيث تدعم ما يصل إلى 1 ميغابايت من المصطلحات (ضغط النشر) في القاموس وتدعم أي لغة. حد المستأجر هو أيضا 1 ميغابايت بعد الضغط. 1 ميغابايت من حد ضغط ما بعد يعني أن جميع القواميس المدمجة عبر المستأجر يمكن أن تحتوي على ما يقرب من مليون حرف.

## <a name="keyword-dictionary-limits"></a>حدود قاموس الكلمات الأساسية

يوجد حد يبلغ 50 نوعا من المعلومات الحساسة المستندة إلى قاموس الكلمات الأساسية التي يمكن إنشاؤها لكل مستأجر. لمعرفة عدد قواميس الكلمات الأساسية لديك في المستأجر، قم بالاتصال باستخدام الإجراءات في [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) للاتصال بالمستأجر وتشغيل البرنامج النصي PowerShell هذا.

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

قد تأتي الكلمات الأساسية للقاموس من مصادر مختلفة، الأكثر شيوعا من ملف (مثل .csv أو قائمة .txt) تم استيراده في الخدمة أو بواسطة PowerShell cmdlet، أو من قائمة تدخلها مباشرة في PowerShell cmdlet، أو من قاموس موجود. عند إنشاء قاموس كلمات أساسية، يمكنك اتباع الخطوات الأساسية نفسها:

1. استخدم <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">*مركز التوافق في Microsoft 365</a> أو اتصل بمركز **التوافق الأمني &amp; PowerShell**.

2. **تعريف الكلمات الأساسية أو تحميلها من المصدر المقصود**. يقبل كل من المعالج و cmdlet قائمة مفصولة بفواصل من الكلمات الأساسية لإنشاء قاموس كلمات أساسية مخصص، لذلك ستختلف هذه الخطوة قليلا استنادا إلى المكان الذي تأتي منه الكلمات الأساسية. بمجرد تحميلها، يتم ترميزها وتحويلها إلى صفيف بايت قبل استيرادها.

3. **إنشاء القاموس الخاص بك**. اختر اسما ووصفا وقم بإنشاء القاموس.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>إنشاء قاموس كلمات أساسية باستخدام Security & Compliance Center

استخدم الخطوات التالية لإنشاء الكلمات الأساسية واستيرادها لقاموس مخصص:

1. الاتصال إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a>.

2. انتقل إلى **التصنيفات > أنواع المعلومات الحساسة**.

3. حدد **إنشاء** **اسم** **ووصف** لنوع المعلومات الحساسة وأدخله، ثم حدد **"التالي"**

4. حدد **"إضافة عنصر"**، ثم حدد **"القاموس" (الكلمات الأساسية الكبيرة)** في **"الكشف عن المحتوى" الذي يحتوي على** القائمة المنسدلة.

5. تحديد **إضافة قاموس**

6. ضمن عنصر تحكم "البحث"، حدد **"يمكنك إنشاء قواميس كلمات أساسية جديدة هنا**".

7. أدخل **اسما** للقاموس المخصص.

8. حدد **"استيراد**"، وحدد إما **"من النص"** أو **"من csv** " استنادا إلى نوع ملف الكلمة الأساسية.

9. في مربع حوار الملف، حدد ملف الكلمة الأساسية من مشاركة ملفات الكمبيوتر أو الشبكة المحلية، ثم حدد **"فتح**".

10. حدد **"حفظ"**، ثم حدد القاموس المخصص من قائمة **قواميس الكلمات الأساسية** .

11. حدد **"إضافة**"، ثم حدد **"التالي**".

12. راجع تحديدات نوع المعلومات الحساسة وقم بإنهاءها، ثم حدد **"إنهاء**".

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>إنشاء قاموس كلمات أساسية من ملف باستخدام PowerShell

في كثير من الأحيان عندما تحتاج إلى إنشاء قاموس كبير، يتم استخدام الكلمات الأساسية من ملف أو قائمة تم تصديرها من مصدر آخر. في هذه الحالة، ستقوم بإنشاء قاموس كلمات أساسية يحتوي على قائمة بلغة غير ملائمة لعرضها في البريد الإلكتروني الخارجي. يجب عليك أولا [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

1. انسخ الكلمات الأساسية إلى ملف نصي وتأكد من أن كل كلمة أساسية موجودة على سطر منفصل.

2. احفظ الملف النصي بترميز Unicode. في المفكرة \> **Save As** \> **Encoding** \> **Unicode**.

3. اقرأ الملف في متغير عن طريق تشغيل أمر cmdlet هذا:

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. إنشاء القاموس عن طريق تشغيل أمر cmdlet هذا:

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>استخدام قواميس الكلمات الأساسية في أنواع المعلومات الحساسة المخصصة ونهج DLP

يمكن استخدام قواميس الكلمات الأساسية كجزء من متطلبات المطابقة لنوع معلومات حساسة مخصص، أو كنوع معلومات حساسة بحد ذاته. كلاهما يتطلب منك إنشاء [نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type-in-scc-powershell.md). اتبع الإرشادات الواردة في المقالة المرتبطة لإنشاء نوع معلومات حساسة. بمجرد حصولك على XML، ستحتاج إلى معرف GUID للقاموس لاستخدامه.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

للحصول على هوية القاموس، قم بتشغيل هذا الأمر وانسخ قيمة خاصية **الهوية** :

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

الصق الهوية في XML الخاص بنوع المعلومات الحساسة المخصصة وقم بتحميلها. سيظهر القاموس الآن في قائمة أنواع المعلومات الحساسة ويمكنك استخدامه مباشرة في النهج الخاص بك، مع تحديد عدد الكلمات الأساسية المطلوبة لمطابقتها.

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
> يدعم Microsoft 365 حماية البيانات لغات مجموعة الأحرف مزدوجة البايت من أجل:
>
> - الصينية (المبسطة)
> - الصينية (التقليدية)
> - الكورية
> - اليابانية
>
> يتوفر هذا الدعم لأنواع المعلومات الحساسة. راجع [دعم حماية المعلومات لملاحظات إصدار مجموعات أحرف البايت المزدوجة (معاينة)](mip-dbcs-relnotes.md) لمزيد من المعلومات.

> [!TIP]
> للكشف عن الأنماط التي تحتوي على أحرف صينية/يابانية وأحرف بايت مفردة أو للكشف عن الأنماط التي تحتوي على الصينية/اليابانية والإنجليزية، حدد متغيرين من الكلمة الأساسية أو regex.
>
> - على سبيل المثال، للكشف عن كلمة أساسية مثل "机密的document"، استخدم متغيرين من الكلمة الأساسية؛ واحدة ذات مسافة بين النص الياباني والإنجليزي والأخرى بدون مسافة بين النص الياباني والإنجليزي. لذلك، يجب أن تكون الكلمات الأساسية المراد إضافتها في SIT "机密的 document" و"机密的document". وبالمثل، للكشف عن عبارة "東京オリンピック2020"، يجب استخدام متغيرين؛ "東京オリンピック 2020" "東京オリンピック2020".
>
> إلى جانب أحرف البايت الصينية/اليابانية/المزدوجة، إذا كانت قائمة الكلمات الأساسية/العبارات تحتوي أيضا على كلمات غير صينية/يابانية أيضا (مثل الإنجليزية فقط)، فمن المستحسن إنشاء قواميس/قوائم كلمات أساسية. واحدة للكلمات الأساسية التي تحتوي على أحرف البايت الصينية/اليابانية/المزدوجة والأخرى للغة الإنجليزية فقط.
>
> - على سبيل المثال، إذا كنت ترغب في إنشاء قاموس/قائمة كلمات أساسية بثلاث عبارات "سرية للغاية"، و"機密性が高い" و"机密的document"، يجب عليك إنشاء قائمتي كلمات أساسية.
>   1. سري للغاية
>   2. 機密性が高い، 机密的document و 机密的 المستند
>
> أثناء إنشاء regex باستخدام واصلة مزدوجة البايت أو فترة بايت مزدوجة، تأكد من إلغاء كل من الحروف مثل واحد قد يفلت من واصلة أو نقطة في regex. فيما يلي عينة regex للرجوع إليها:
>
> - `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> نوصي باستخدام مطابقة سلسلة بدلا من مطابقة كلمة في قائمة الكلمات الأساسية.
