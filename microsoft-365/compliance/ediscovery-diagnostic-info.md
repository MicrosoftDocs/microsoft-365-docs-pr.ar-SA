---
title: تجميع معلومات تشخيص eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: تعرف على كيفية تجميع معلومات eDiscovery التشخيصية عن حالة دعم Microsoft.
ms.openlocfilehash: cab21c71168119b27a478b99a19ad5693ffb678e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63570117"
---
# <a name="collect-ediscovery-diagnostic-information"></a>تجميع معلومات تشخيص eDiscovery

يحتاج مهندسو دعم Microsoft أحيانا إلى معلومات محددة حول المشكلة عند فتح حالة دعم ذات صلة ب Core eDiscovery أو Advanced eDiscovery. توفر هذه المقالة إرشادات حول كيفية تجميع المعلومات التشخيصية لمساعدة مهندسي الدعم على التحقق من المشاكل وحلها. لا تحتاج عادة إلى تجميع هذه المعلومات إلا عندما يطلب منك أحد مهندسي دعم Microsoft القيام بذلك.

> [!IMPORTANT]
> قد يتضمن إخراج cmdlets والمعلومات التشخيصية الموضحة في هذه المقالة معلومات حساسة حول الدعاوى القضائية أو التحريات الداخلية في مؤسستك. قبل إرسال المعلومات التشخيصية الأولية إلى دعم Microsoft، يجب مراجعة المعلومات وتحريض أي معلومات حساسة (مثل الأسماء أو معلومات أخرى حول الأطراف في الدعاوى القضائية أو التحقيق) عن طريق استبدالها ب `XXXXXXX`. سيشير استخدام هذا الأسلوب أيضا لمهندس دعم Microsoft إلى أنه تم إعادة تنشيط المعلومات.

## <a name="collect-diagnostic-information-for-core-ediscovery"></a>تجميع معلومات تشخيصية ل eDiscovery الأساسي

يعتمد تجميع المعلومات التشخيصية ل eDiscovery الأساسي على cmdlet، لذا يجب استخدام الأمان & مركز التوافق PowerShell. سيتم تشغيل cmdlets في أمثلة PowerShell التالية ثم حفظ الإخراج في ملف نصي محدد. في معظم حالات الدعم، يجب أن تحتاج فقط إلى تشغيل أحد هذه الأوامر.

لتشغيل cmdlets التالية، اتصل بمركز التوافق & [PowerShell</span>](/powershell/exchange/connect-to-scc-powershell). بعد الاتصال، يمكنك تشغيل أمر واحد أو أكثر من الأوامر التالية وتأكد من استبدال العنصر النائب بأسماء الكائنات الفعلية.

بعد مراجعة الملف النصي الذي تم إنشاؤه ومراجعة المعلومات الحساسة، أرسله إلى مهندس دعم Microsoft الذي يعمل على قضيتك.

> [!NOTE]
> يمكنك أيضا تشغيل الأوامر الواردة في هذا المقطع لتجميع المعلومات التشخيصية لعمليات البحث والتصدير المدرجة في صفحة البحث في المحتوى في مركز التوافق في Microsoft 365.

### <a name="collect-information-about-searches"></a>تجميع معلومات حول عمليات البحث

يجمع الأمر التالي المعلومات المفيدة عند التحقق من المشاكل المتعلقة بالبحث في المحتوى أو عملية بحث مقترنة بقضيه eDiscovery الأساسية.

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>تجميع معلومات حول إجراءات البحث

يجمع الأمر التالي المعلومات للتحقق من المشاكل المتعلقة بمعاينة نتائج بحث محتوى أو بحث مقترن بأو حالة eDiscovery أساسية أو تصديرها أو ازهاقها. يمكنك تحديد اسم إجراء البحث بالنقر فوق تصدير مدرج في علامة التبويب **عمليات** التصدير. لتحديد أسماء إجراءات المعاينة واحذفها، يمكنك تشغيل **الأمر Cmdlet Get-ComplianceSearchAction** لعرض قائمة بكل الإجراءات. يتم إنشاء تنسيق اسم إجراء `_Preview`البحث عن طريق تعليق أو `_Export`أو `_Purge` إلى اسم البحث المناظر.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>تجميع معلومات حول حاملات eDiscovery

عندما لا يعمل أحد أوامر eDiscovery المقترنة ب حالة eDiscovery الأساسية كما هو متوقع، يمكنك تشغيل الأمر التالي لتجميع معلومات حول "نهج الاستمرار في حالة القضيه" و"قاعدة الاستمرار حالة التكفير المقترنة" الخاصة ب eDiscovery. اسم *نهج الاستمرار حالة التكفير* في الأمر التالي هو نفس اسم الاستمرار eDiscovery. يمكنك تحديد هذا الاسم على علامات التبويب "علامات **تبويب** "، في حالة eDiscovery الأساسية.

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>تجميع كل معلومات الحالة

في بعض الأحيان، لا يكون واضحا المعلومات المطلوبة بواسطة دعم Microsoft للتحقق من المشكلة. في هذه الحالة، يمكنك تجميع كل معلومات التشخيص للحالة الأساسية eDiscovery. اسم *حالة eDiscovery* الأساسي في الأمر التالي هو نفس اسم حالة الحالة التي يتم عرضها على الصفحة **Core eDiscovery** في مركز التوافق في Microsoft 365.

```powershell
Get-ComplianceCase "<Core eDiscovery case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-advanced-ediscovery"></a>تجميع المعلومات التشخيصية Advanced eDiscovery

تتيح **الإعدادات** علامة التبويب "Advanced eDiscovery" نسخ المعلومات التشخيصية الخاصة بهذه الحالة بسرعة. يتم حفظ المعلومات التشخيصية في الحافظة بحيث يمكنك لصقها في ملف نصي وإرسالها إلى دعم Microsoft.

1. انتقل إلى مركز التوافق في Microsoft 365، وحدد **eDiscoveryAdvanced** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

2. حدد حالة، ثم انقر **فوق علامة التبويب** الإعدادات.

3. ضمن **معلومات حالة الاتصال،** انقر فوق **تحديد**.

4. على صفحة المعلومات، انقر فوق **معلومات** **دعم ActionsCopy** >  لنسخ المعلومات إلى الحافظة.

5. افتح ملفا نصيا (في المفكرة) ثم اللصق المعلومات في الملف النصي.

6. احفظ الملف النصي ثم احفظه باسم مثل `AeD Diagnostic Info YYYY.MM.DD` (على سبيل المثال، `AeD Diagnostic Info 2020.11.03`).

بعد مراجعة الملف ومراجعة المعلومات الحساسة، أرسلها إلى مهندس دعم Microsoft الذي يعمل على قضيتك.
