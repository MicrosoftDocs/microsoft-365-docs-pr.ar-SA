---
title: تعريف كيان رقم الحساب الطبي في أستراليا
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: تعريف كيان نوع المعلومات الحساسة لرقم الحساب الطبي في أستراليا.
ms.openlocfilehash: c17de71ef0c16b5c14ba118c66ae0d9274ce4468
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944383"
---
# <a name="australia-medical-account-number"></a>رقم الحساب الطبي في أستراليا

## <a name="format"></a>تنسيق

من 10 إلى 11 رقما

## <a name="pattern"></a>نمط

من 10 إلى 11 رقما:

- الرقم الأول في النطاق من 2 إلى 6
- الرقم التاسع هو خانة اختيار
- الرقم العاشر هو رقم المشكلة
- الرقم الحادي عشر (اختياري) هو الرقم الفردي

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_australian_medical_account_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_Australia_Medical_Account_Number.
- يمر المجموع الاختباري.

```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- تفاصيل الحساب البنكي
- دفعات medicare
- حساب رهن
- دفعات بنكية
- فرع المعلومات
- قرض بطاقة الائتمان
- قسم الخدمات البشرية
- الخدمة المحلية
- الرعايه الطبيه
