---
title: إزالة نوع معلومات حساسة مخصص باستخدام PowerShell
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
ms.openlocfilehash: ba29c2f20133b94d87c14f527d454980c41373c9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621678"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>إزالة نوع معلومات حساسة مخصص باستخدام PowerShell

في Security & Compliance PowerShell، هناك طريقتان لإزالة أنواع المعلومات الحساسة المخصصة:

- **إزالة أنواع المعلومات الحساسة المخصصة الفردية**: استخدم الأسلوب الموثق في [تعديل نوع معلومات حساسة مخصص باستخدام PowerShell](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell). يمكنك تصدير حزمة القواعد المخصصة التي تحتوي على نوع المعلومات الحساسة المخصصة، وإزالة نوع المعلومات الحساسة من ملف XML، واستيراد ملف XML المحدث مرة أخرى إلى حزمة القواعد المخصصة الموجودة.

- **إزالة حزمة قاعدة مخصصة وكافة أنواع المعلومات الحساسة المخصصة التي تحتوي عليها**: تم توثيق هذا الأسلوب في هذا المقطع.

> [!NOTE]
> قبل إزالة نوع معلومات حساسة مخصص، تحقق من عدم وجود نهج DLP أو قواعد تدفق بريد Exchange (المعروفة أيضا باسم قواعد النقل) لا تزال تشير إلى نوع المعلومات الحساسة.

1. [Security & Compliance PowerShell](/powershell/exchange/exchange-online-powershell)

2. لإزالة حزمة قاعدة مخصصة، استخدم [الأمر Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) cmdlet:

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   يمكنك استخدام قيمة الاسم (لأي لغة) أو `RulePack id` قيمة (GUID) لتعريف حزمة القاعدة.

   يزيل هذا المثال حزمة القاعدة المسماة "Employee ID Custom Rule Pack".

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. للتحقق من إزالة نوع معلومات حساسة مخصص بنجاح، قم بأي من الخطوات التالية:

   - قم بتشغيل [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet وتحقق من أن حزمة القواعد لم تعد مدرجة:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - قم بتشغيل [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet للتحقق من أن أنواع المعلومات الحساسة في حزمة القواعد التي تمت إزالتها لم تعد مدرجة:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     بالنسبة لأنواع المعلومات الحساسة المخصصة، ستكون قيمة خاصية Publisher شيئا آخر غير Microsoft Corporation.

   - استبدل \<Name\> بقيمة الاسم لنوع المعلومات الحساسة (على سبيل المثال، معرف الموظف) وقم بتشغيل [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet للتحقق من أن نوع المعلومات الحساسة لم يعد مدرجا:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>معلومات إضافية

- [تعرف على تفادي فقدان البيانات في Microsoft Purview](dlp-learn-about-dlp.md)

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)

- [دالات نوع المعلومات الحساسة](sit-functions.md)
