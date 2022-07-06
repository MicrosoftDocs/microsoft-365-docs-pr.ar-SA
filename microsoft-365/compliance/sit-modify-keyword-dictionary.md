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
description: تعرف على كيفية تعديل قاموس كلمات أساسية في مدخل التوافق في Microsoft Purview.
ms.openlocfilehash: 8b2f2256be506f0ba01dc059bf0ac54e84c481c9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621700"
---
# <a name="modify-a-keyword-dictionary"></a>تعديل قاموس كلمة أساسية

قد تحتاج إلى تعديل الكلمات الأساسية في أحد قواميس الكلمات الأساسية، أو تعديل أحد القواميس المضمنة. يمكنك القيام بذلك من خلال PowerShell أو من خلال مركز التوافق.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>تعديل قاموس كلمات أساسية في مركز التوافق

يمكن استخدام قواميس الكلمات الأساسية كأنماط `Primary elements` نوع المعلومات الحساسة (SIT) أو `Supporting elements` فيها. يمكنك تحرير قاموس كلمات أساسية أثناء إنشاء SIT أو في SIT موجود. على سبيل المثال لتحرير قاموس كلمات أساسية موجود:

1. افتح النمط الذي يحتوي على قاموس الكلمة الأساسية الذي تريد تحديثه.
2. ابحث عن قاموس الكلمات الأساسية الذي تريد تحديثه واختر تحرير.
3. قم بإجراء عمليات التحرير باستخدام كلمة أساسية واحدة لكل سطر.

   ![لقطة شاشة لتحرير الكلمات الأساسية.](../media/edit-keyword-dictionary.png)

4. اختر `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>تعديل قاموس الكلمات الأساسية باستخدام PowerShell

على سبيل المثال، سنقوم بتعديل بعض المصطلحات في PowerShell، وحفظ المصطلحات محليا حيث يمكنك تعديلها في محرر، ثم تحديث الشروط السابقة في مكانها.

أولا، استرداد كائن القاموس:

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

ستعرض الطباعة `$dict` الخصائص المختلفة. يتم تخزين الكلمات الأساسية نفسها في كائن على الواجهة الخلفية، ولكنها `$dict.KeywordDictionary` تحتوي على تمثيل سلسلة لها، والتي ستستخدمها لتعديل القاموس.

قبل تعديل القاموس، تحتاج إلى إعادة سلسلة المصطلحات إلى صفيف باستخدام `.split(',')` الأسلوب. ثم ستقوم بتنظيف المسافات غير المرغوب فيها بين الكلمات الأساسية باستخدام `.trim()` الأسلوب، مع ترك الكلمات الأساسية فقط للعمل معها.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

الآن ستقوم بإزالة بعض المصطلحات من القاموس. نظرا لأن القاموس المثال يحتوي على كلمات أساسية قليلة فقط، يمكنك بسهولة التخطي إلى تصدير القاموس وتحريره في المفكرة، ولكن القواميس تحتوي بشكل عام على كمية كبيرة من النص، لذلك ستتعلم أولا هذه الطريقة لتحريرها بسهولة في PowerShell.

في الخطوة الأخيرة، قمت بحفظ الكلمات الأساسية في صفيف. هناك عدة طرق [لإزالة العناصر من صفيف](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10))، ولكن كنهج مباشر، ستقوم بإنشاء صفيف من المصطلحات التي تريد إزالتها من القاموس، ثم نسخ مصطلحات القاموس فقط إليه غير الموجودة في قائمة المصطلحات لإزالتها.

قم بتشغيل الأمر `$terms` لإظهار قائمة المصطلحات الحالية. يبدو إخراج الأمر كما يلي:

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

قم بتشغيل هذا الأمر لإزالة المصطلحات من القائمة بالفعل:

```powershell
$updatedTerms = $terms | Where-Object {$_ -notin $termsToRemove}
```

قم بتشغيل الأمر `$updatedTerms` لإظهار قائمة المصطلحات المحدثة. يبدو إخراج الأمر كما يلي (تمت إزالة المصطلحات المحددة):

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

الآن احفظ القاموس محليا وأضف بعض المصطلحات الإضافية. يمكنك إضافة المصطلحات هنا في PowerShell، ولكن ستظل بحاجة إلى تصدير الملف محليا للتأكد من حفظه بترميز Unicode ويحتوي على BOM.

احفظ القاموس محليا عن طريق تشغيل ما يلي:

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

الآن افتح الملف، وأضف المصطلحات الأخرى، واحفظها بترميز Unicode (UTF-16). ستقوم الآن بتحميل المصطلحات المحدثة وتحديث القاموس في مكانه.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

الآن تم تحديث القاموس في مكانه. `Identity` يأخذ الحقل اسم القاموس. إذا أردت أيضا تغيير اسم القاموس باستخدام `Set-` cmdlet، فستحتاج فقط إلى إضافة `-Name` المعلمة إلى ما هو أعلاه باستخدام اسم القاموس الجديد.

## <a name="see-also"></a>راجع أيضًا

- [إنشاء قاموس كلمة أساسية](create-a-keyword-dictionary.md)
- [إنشاء نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type.md)
