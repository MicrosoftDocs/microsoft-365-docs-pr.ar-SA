---
title: إزالة نوع معلومات حساسة مخصصة باستخدام PowerShell
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: تعرف على كيفية إزالة نوع معلومات حساسة مخصص باستخدام PowerShell
ms.openlocfilehash: 852f9987b072f05dcf4f322f600bed23bcce7ef2
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/18/2022
ms.locfileid: "63579651"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>إزالة نوع معلومات حساسة مخصصة باستخدام PowerShell

في مركز التوافق PowerShell، هناك طريقتان لإزالة أنواع المعلومات الحساسة المخصصة:

- **إزالة أنواع المعلومات الحساسة المخصصة** الفردية: استخدم الأسلوب الموثق في [تعديل نوع معلومات حساسة مخصصة باستخدام PowerShell](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell). يمكنك تصدير حزمة القاعدة المخصصة التي تحتوي على نوع المعلومات الحساسة المخصصة، وإزالة نوع المعلومات الحساسة من ملف XML، واستيراد ملف XML المحدث مرة أخرى إلى حزمة القواعد المخصصة الموجودة.

- **إزالة حزمة قاعدة مخصصة وكل أنواع المعلومات الحساسة** المخصصة التي تحتوي عليها: تم توثيق هذا الأسلوب في هذا المقطع.

> [!NOTE]
> قبل إزالة نوع معلومات حساسة مخصص، تحقق من عدم وجود أي Exchange DLP أو قواعد تدفق بريد إلكتروني (تعرف أيضا بقواعد النقل) تشير إلى نوع المعلومات الحساسة.

1. [الاتصال مركز التوافق في PowerShell](/powershell/exchange/exchange-online-powershell)

2. لإزالة حزمة قاعدة مخصصة، استخدم [cmdlet Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) cmdlet:

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   يمكنك استخدام قيمة الاسم (لأي لغة) أو `RulePack id` القيمة (GUID) لتحديد حزمة القاعدة.

   يزيل هذا المثال حزمة القاعدة المسماة "حزمة قواعد مخصصة لمعرف الموظف".

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. للتحقق من أنك قمت بإزالة نوع معلومات حساسة مخصص بنجاح، يمكنك تنفيذ أي من الخطوات التالية:

   - تشغيل [أمر cmdlet Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) والتحقق من أن حزمة القاعدة لم تعد مدرجة:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - تشغيل [الأمر Cmdlet Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) للتحقق من أن أنواع المعلومات الحساسة في حزمة القواعد التي تمت إزالتها لم تعد مدرجة:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     بالنسبة لأنواع المعلومات الحساسة المخصصة، ستكون Publisher الخاصية شيء آخر غير Microsoft Corporation.

   - استبدل \<Name\> بقيمة الاسم لنوع المعلومات الحساسة (على سبيل المثال، "اسم الموظف") ثم ابدل أمر cmdlet [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) للتحقق من أن نوع المعلومات الحساسة لم يعد مدرجا:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>معلومات إضافية

- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)

- [دالات نوع المعلومات الحساسة](sit-functions.md)
