---
title: تعديل نوع معلومات حساسة مخصصة باستخدام PowerShell
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
description: تعرف على كيفية تعديل معلومات حساسة مخصصة باستخدام PowerShell.
ms.openlocfilehash: 2f1bc44dca9ec4a938c8cd3d4158163f9d5e2e2f
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/18/2022
ms.locfileid: "63583336"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>تعديل نوع معلومات حساسة مخصصة باستخدام PowerShell

في مركز التوافق PowerShell، يتطلب منك تعديل نوع معلومات مخصص حساس ما يلي:

1. تصدير حزمة القاعدة الموجودة التي تحتوي على نوع المعلومات الحساسة المخصصة إلى ملف XML (أو استخدم ملف XML الموجود إذا كان لديك).

2. قم بتعديل نوع المعلومات الحساسة المخصصة في ملف XML الذي تم تصديره.

3. استيراد ملف XML المحدث مرة أخرى إلى حزمة القواعد الموجودة.

للاتصال بمركز التوافق PowerShell، راجع الاتصال [مركز التوافق PowerShell](/powershell/exchange/exchange-online-powershell).

### <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>الخطوة 1: تصدير حزمة القاعدة الموجودة إلى ملف XML

> [!NOTE]
> إذا كان لديك نسخة من ملف XML (على سبيل المثال، قمت فقط بإنشاء الملف واستوردته)، يمكنك الانتقال إلى الخطوة التالية لتعديل ملف XML.

1. إذا لم تكن تعرف ذلك مسبقا، فدير [الأمر Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet للعثور على اسم حزمة القواعد المخصصة:

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > تسمى حزمة القواعد المضمنة التي تحتوي على أنواع المعلومات الحساسة المضمنة حزمة قاعدة Microsoft. تسمى حزمة القاعدة التي تحتوي على أنواع المعلومات الحساسة المخصصة التي أنشأتها في واجهة مستخدم مركز التوافق باسم Microsoft.SCCManaged.CustomRulePack.

2. استخدم [Cmdlet Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) لتخزين حزمة القواعد المخصصة إلى متغير:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   على سبيل المثال، إذا كان اسم حزمة القاعدة هو "حزمة قاعدة مخصصة لمعرف الموظف"، فدير أمر cmdlet التالي:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. استخدم بناء الجملة التالي لتصدير حزمة القواعد المخصصة إلى ملف XML:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   يصدر هذا المثال حزمة القاعدة إلى الملف المسمى ExportedRulePackage.xml في المجلد C:\My Documents.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

#### <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>الخطوة 2: تعديل نوع المعلومات الحساسة في ملف XML الذي تم تصديره

تم وصف أنواع المعلومات الحساسة في ملف XML والعناصر الأخرى في الملف سابقا في هذا الموضوع.

#### <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>الخطوة 3: استيراد ملف XML المحدث مرة أخرى إلى حزمة القواعد الموجودة

لاستيراد XML المحدث مرة أخرى إلى حزمة القواعد الموجودة، استخدم [cmdlet Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) cmdlet:

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>معلومات إضافية

- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [دالات نوع المعلومات الحساسة](sit-functions.md)
