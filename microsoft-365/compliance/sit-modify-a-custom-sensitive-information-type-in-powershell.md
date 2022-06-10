---
title: تعديل نوع معلومات حساسة مخصص باستخدام PowerShell
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
ms.openlocfilehash: deb50679702cec69187392337511b4dde2d1ceb3
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014377"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>تعديل نوع معلومات حساسة مخصص باستخدام PowerShell

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

في Security & Compliance PowerShell، يتطلب منك تعديل نوع معلومات حساسة مخصص:

1. قم بتصدير حزمة القواعد الموجودة التي تحتوي على نوع المعلومات الحساسة المخصصة إلى ملف XML (أو استخدم ملف XML الموجود إذا كان لديك).

2. تعديل نوع المعلومات الحساسة المخصصة في ملف XML الذي تم تصديره.

3. قم باستيراد ملف XML المحدث مرة أخرى إلى حزمة القواعد الموجودة.

للاتصال ب Security & Compliance PowerShell، راجع [Security & Compliance PowerShell](/powershell/exchange/exchange-online-powershell).

## <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>الخطوة 1: تصدير حزمة القواعد الموجودة إلى ملف XML

> [!NOTE]
> إذا كان لديك نسخة من ملف XML (على سبيل المثال، قمت بإنشائه واستيراده للتو)، يمكنك الانتقال إلى الخطوة التالية لتعديل ملف XML.

1. إذا لم تكن تعرف ذلك بالفعل، فشغل [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet للعثور على اسم حزمة القواعد المخصصة:

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > تسمى حزمة القواعد المضمنة التي تحتوي على أنواع المعلومات الحساسة المضمنة بحزمة قاعدة Microsoft. حزمة القواعد التي تحتوي على أنواع المعلومات الحساسة المخصصة التي قمت بإنشائها في واجهة مستخدم مركز التوافق تسمى Microsoft.SCCManaged.CustomRulePack.

2. استخدم [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet لتخزين حزمة القواعد المخصصة إلى متغير:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   على سبيل المثال، إذا كان اسم حزمة القاعدة هو "Employee ID Custom Rule Pack"، فشغل cmdlet التالي:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. استخدم بناء الجملة التالي لتصدير حزمة القاعدة المخصصة إلى ملف XML:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   يقوم هذا المثال بتصدير حزمة القواعد إلى الملف المسمى ExportedRulePackage.xml في المجلد C:\My Documents.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

## <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>الخطوة 2: تعديل نوع المعلومات الحساسة في ملف XML الذي تم تصديره

يتم وصف أنواع المعلومات الحساسة في ملف XML والعناصر الأخرى في الملف سابقا في هذا الموضوع.

## <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>الخطوة 3: استيراد ملف XML المحدث مرة أخرى إلى حزمة القواعد الموجودة

لاستيراد XML المحدث مرة أخرى إلى حزمة القواعد الموجودة، استخدم [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) cmdlet:

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>معلومات إضافية

- [تعرف على منع فقدان بيانات Microsoft Purview](dlp-learn-about-dlp.md)
- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [دالات نوع المعلومات الحساسة](sit-functions.md)
