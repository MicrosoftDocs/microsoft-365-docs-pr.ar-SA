---
title: تعديل قاموس كلمة أساسية
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية تعديل قاموس الكلمات الأساسية في Microsoft 365 التوافق.
ms.openlocfilehash: acdf8b24aced21ed2f576fd57a3c685ef14debea
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/29/2022
ms.locfileid: "63583295"
---
# <a name="modify-a-keyword-dictionary"></a>تعديل قاموس كلمة أساسية

قد تحتاج إلى تعديل الكلمات الأساسية في أحد قواميس الكلمات الأساسية، أو تعديل أحد القواميس المضمنة. يمكنك القيام بذلك من خلال PowerShell أو من خلال مركز التوافق.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>تعديل قاموس كلمة أساسية في مركز التوافق

يمكن استخدام قواميس الكلمات الأساسية كنقوش `Primary elements` `Supporting elements` نوع المعلومات الحساسة (SIT) أو في هذه الأنماط. يمكنك تحرير قاموس الكلمات الأساسية أثناء إنشاء SIT أو في SIT موجود. على سبيل المثال لتحرير قاموس كلمات أساسية موجود:

1. افتح النمط الذي به قاموس الكلمة الأساسية الذي تريد تحديثه.
2. ابحث عن قاموس الكلمة الأساسية الذي تريد تحديثه واختر تحرير.
3. قم بالتحرير باستخدام كلمة أساسية واحدة لكل سطر.

   ![لقطة شاشة لتحرير الكلمات الأساسية.](../media/edit-keyword-dictionary.png)

4. اختر `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>تعديل قاموس الكلمات الأساسية باستخدام PowerShell

على سبيل المثال، سنقوم بتعديل بعض الشروط في PowerShell، وحفظ الشروط محليا حيث يمكنك تعديلها في محرر، ثم تحديث الشروط السابقة في مكانها.

أولا، استرداد كائن القاموس:

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

سوف `$dict` تظهر الطباعة الخصائص المختلفة. يتم تخزين الكلمات `$dict.KeywordDictionary` الأساسية نفسها في كائن على الواجهة الخلفية، ولكنها تحتوي على تمثيل سلسلة لها، الذي سيتم استخدامه لتعديل القاموس.

قبل تعديل القاموس، ستحتاج إلى تحويل سلسلة المصطلحات مرة أخرى إلى صفيف باستخدام `.split(',')` الأسلوب. بعد ذلك، ستنظف `.trim()` المسافات غير المرغوب فيها بين الكلمات الأساسية باستخدام الأسلوب، مع ترك الكلمات الأساسية فقط للعمل عليها.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

الآن ستزيل بعض المصطلحات من القاموس. نظرا لأن المثال يحتوي على بضع كلمات أساسية فقط، يمكنك بسهولة التخطي إلى تصدير القاموس وتحريره في المفكرة، ولكن القواميس تحتوي بشكل عام على كمية كبيرة من النص، وبالتالي ستتعرف أولا على هذه الطريقة لتحريرها بسهولة في PowerShell.

في الخطوة الأخيرة، حفظت الكلمات الأساسية في صفيف. هناك عدة طرق لإزالة العناصر [](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10))من صفيف، ولكن من خلال نهج مباشر، ستنشئ صفيفا من المصطلحات التي تريد إزالتها من القاموس، ثم نسخ مصطلحات القاموس فقط إلى القاموس غير الموجودة في قائمة المصطلحات التي تريد إزالتها.

تشغيل الأمر `$terms` لإظهار قائمة المصطلحات الحالية. يبدو إخراج الأمر كما يلي:

```powershell
aarskog's syndrome
abandonment
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablatio
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

قم بتشغيل هذا الأمر لتحديد المصطلحات التي تريد إزالتها:

```powershell
$termsToRemove = @('abandonment','ablatio')
```

قم بتشغيل هذا الأمر لإزالة المصطلحات من القائمة فعليا:

```powershell
$updatedTerms = $terms | Where-Object {$_ -notin $termsToRemove}
```

تشغيل الأمر `$updatedTerms` لإظهار قائمة المصطلحات المحدثة. يبدو إخراج الأمر على هذا النحو (تمت إزالة المصطلحات المحددة):

```powershell
aarskog's syndrome
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

احفظ القاموس الآن محليا وأضف بعض المصطلحات الإضافية. يمكنك إضافة المصطلحات هنا في PowerShell، ولكنك ستحتاج إلى تصدير الملف محليا للتأكد من حفظه باستخدام ترميز Unicode ويحتوي على BOM.

احفظ القاموس محليا عن طريق تشغيل ما يلي:

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

افتح الآن الملف وأضف المصطلحات الأخرى واحفظه باستخدام ترميز Unicode (UTF-16). الآن سيتم تحميل المصطلحات المحدثة وتحديث القاموس في مكانه.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

تم الآن تحديث القاموس في مكانه. يأخذ `Identity` الحقل اسم القاموس. إذا أردت أيضا `Set-` تغيير اسم القاموس باستخدام الأمر cmdlet `-Name` ، فما عليك سوى إضافة المعلمة إلى ما هو أعلاه باستخدام اسم القاموس الجديد.

## <a name="see-also"></a>راجع أيضًا

- [إنشاء قاموس كلمة أساسية](create-a-keyword-dictionary.md)
- [إنشاء نوع معلومات حساسة مخصصة](create-a-custom-sensitive-information-type.md)
