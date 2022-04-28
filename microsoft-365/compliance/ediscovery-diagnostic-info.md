---
title: تجميع معلومات تشخيص eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: تعرف على كيفية جمع معلومات تشخيص eDiscovery لحالة دعم Microsoft.
ms.openlocfilehash: 2759156a3948339629ea7d988eaaa5464da197fa
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095873"
---
# <a name="collect-ediscovery-diagnostic-information"></a>تجميع معلومات تشخيص eDiscovery

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يحتاج مهندسو دعم Microsoft أحيانا إلى معلومات محددة حول مشكلتك عند فتح حالة دعم متعلقة ب Microsoft Purview eDiscovery (قياسي) أو Microsoft Purview eDiscovery (Premium). توفر هذه المقالة إرشادات حول كيفية جمع معلومات التشخيص لمساعدة المهندسين على التحقق من المشاكل وحلها. عادة، لا تحتاج إلى جمع هذه المعلومات حتى يطلب منك مهندس دعم Microsoft القيام بذلك.

> [!IMPORTANT]
> قد تتضمن المخرجات من cmdlets والمعلومات التشخيصية الموضحة في هذه المقالة معلومات حساسة حول التقاضي أو التحقيقات الداخلية في مؤسستك. قبل إرسال معلومات التشخيص الأولية إلى دعم Microsoft، يجب عليك مراجعة المعلومات وتصعيد أي معلومات حساسة (مثل الأسماء أو معلومات أخرى حول أطراف التقاضي أو التحقيق) عن طريق استبدالها.`XXXXXXX` سيؤدي استخدام هذا الأسلوب أيضا إلى الإشارة إلى مهندس دعم Microsoft أنه تم تنقيح المعلومات.

## <a name="collect-diagnostic-information-for-ediscovery-standard"></a>تجميع معلومات تشخيصية ل eDiscovery (قياسي)

يستند تجميع المعلومات التشخيصية ل eDiscovery (Standard) إلى cmdlet، لذلك سيتعين عليك استخدام Security & Compliance Center PowerShell. ستقوم أمثلة PowerShell التالية بتشغيل cmdlets ثم حفظ الإخراج إلى ملف نصي محدد. في معظم حالات الدعم، يجب عليك تشغيل أحد هذه الأوامر فقط.

لتشغيل cmdlets التالية، [اتصل ب Security & Compliance Center PowerShell</span>](/powershell/exchange/connect-to-scc-powershell). بعد الاتصال، قم بتشغيل أمر واحد أو أكثر من الأوامر التالية وتأكد من استبدال العناصر النائبة بأسماء العناصر الفعلية.

بعد مراجعة الملف النصي الذي تم إنشاؤه وتكرار المعلومات الحساسة، أرسله إلى مهندس دعم Microsoft الذي يعمل على حالتك.

> [!NOTE]
> يمكنك أيضا تشغيل الأوامر في هذا القسم لجمع معلومات تشخيصية لعمليات البحث والتصدير المدرجة في صفحة **البحث في المحتوى** في مدخل توافق Microsoft Purview.

### <a name="collect-information-about-searches"></a>تجميع معلومات حول عمليات البحث

يجمع الأمر التالي معلومات مفيدة عند التحقق من المشاكل المتعلقة بالبحث في المحتوى أو البحث المقترن بحالة eDiscovery (قياسي).

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>تجميع معلومات حول إجراءات البحث

يجمع الأمر التالي معلومات للتحقيق في المشاكل المتعلقة بمعاينة نتائج البحث في المحتوى أو البحث المقترن بحالة eDiscovery (قياسي) أو تصديرها أو إزالتها. يمكنك تحديد اسم إجراء البحث بالنقر فوق تصدير مدرج في علامة التبويب " **تصديرات** ". لتحديد أسماء إجراءات المعاينة والإزالة، يمكنك تشغيل **Get-ComplianceSearchAction** cmdlet لعرض قائمة بجميع الإجراءات. يتم إنشاء تنسيق اسم إجراء البحث بواسطة إلحاق `_Preview`أو `_Export``_Purge` اسم البحث المطابق.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>تجميع معلومات حول قوائم احتجاز eDiscovery

عندما لا تعمل قائمة احتجاز eDiscovery المقترنة بحالة eDiscovery (Standard) كما هو متوقع، قم بتشغيل الأمر التالي لجمع معلومات حول نهج احتجاز الحالة وقاعدة احتجاز الحالة المقترنة للاحتفاظ ب eDiscovery. *اسم نهج احتجاز الحالة* في الأمر التالي هو نفس اسم قائمة احتجاز eDiscovery. يمكنك تحديد هذا الاسم على علامات التبويب **"احتجاز** " في حالة eDiscovery (قياسي).

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>تجميع كافة معلومات الحالة

في بعض الأحيان، لا يكون من الواضح المعلومات المطلوبة من قبل دعم Microsoft للتحقيق في مشكلتك. في هذه الحالة، يمكنك جمع كافة معلومات التشخيص لحالة eDiscovery (قياسي). *اسم حالة eDiscovery (قياسي)* في الأمر التالي هو نفس اسم حالة يتم عرضها على صفحة **eDiscovery (قياسي)** في مدخل التوافق.

```powershell
Get-ComplianceCase "<eDiscovery (Standard) case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-ediscovery-premium"></a>جمع معلومات تشخيصية ل eDiscovery (Premium)

تتيح لك علامة التبويب **الإعدادات** في حالة eDiscovery (Premium) نسخ معلومات التشخيص للحالة بسرعة. يتم حفظ معلومات التشخيص في الحافظة حتى تتمكن من لصقها في ملف نصي وإرسالها إلى دعم Microsoft.

1. انتقل إلى مدخل التوافق، وحدد **eDiscoveryAdvanced** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

2. حدد حالة ثم انقر فوق علامة التبويب **الإعدادات**.

3. ضمن **"معلومات الحالة**"، انقر فوق **"تحديد**".

4. في صفحة القائمة المنبثقة، انقر فوق **معلومات دعم ActionsCopy**  >  لنسخ المعلومات إلى الحافظة.

5. افتح ملفا نصيا (في المفكرة) ثم الصق المعلومات في الملف النصي.

6. احفظ الملف النصي وقم بتسمية شيء مثل `AeD Diagnostic Info YYYY.MM.DD` (على سبيل المثال، `AeD Diagnostic Info 2020.11.03`).

بعد مراجعة الملف وتصعيد المعلومات الحساسة، أرسله إلى مهندس دعم Microsoft الذي يعمل على حالتك.
