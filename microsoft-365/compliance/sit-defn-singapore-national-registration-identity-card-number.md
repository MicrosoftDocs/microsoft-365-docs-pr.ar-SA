---
title: تعريف كيان رقم بطاقة هوية التسجيل الوطنية (NRIC) في سنغافورة
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة هوية التسجيل الوطنية في سنغافورة .
ms.openlocfilehash: b2dfa68f3d69134f7d4eca67648c64075b5d1c44
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944431"
---
# <a name="singapore-national-registration-identity-card-nric-number"></a>رقم بطاقة هوية التسجيل الوطنية في سنغافورة (NRIC)

## <a name="format"></a>تنسيق

تسعة أحرف وأرقام

## <a name="pattern"></a>نمط

- تسعة أحرف وأرقام:

- الحرف "F" أو "G" أو "M" أو "S" أو "T" (غير حساس لحالة الأحرف)
- سبعة أرقام
- رقم اختيار أبجدي

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_singapore_nric` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_singapore_nric` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_singapore_nric` العادي عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Singapore National Registration Identity Card (NRIC) Number -->
<Entity id="cead390a-dd83-4856-9751-fb6dc98c34da" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_singapore_nric"/>
     <Match idRef="Keyword_singapore_nric"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_singapore_nric"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- بطاقة هوية التسجيل الوطنية
- رقم بطاقة الهوية
- NRIC
- IC
- رقم التعريف الخارجي
- فنلندا
- 身份证
- 身份證