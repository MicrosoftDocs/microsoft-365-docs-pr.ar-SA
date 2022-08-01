---
title: تعريف كيان رقم التأمين الصحي في فرنسا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التأمين الصحي في فرنسا.
ms.openlocfilehash: c62a50553c985bbe6a4e4f8c640772902f7b4bd0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944435"
---
# <a name="france-health-insurance-number"></a>رقم التأمين الصحي في فرنسا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

رقم مكون من 21 رقما

## <a name="pattern"></a>نمط

رقم مكون من 21 رقما:

- 10 أرقام
- مساحة اختيارية
- 10 أرقام
- مساحة اختيارية
- رقم

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث regex `Regex_France_Health_Insurance_Number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_France_Health_Insurance_Number` .

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- بطاقة التأمين
- carte vitale
- carte d'assuré social