---
title: تعريف كيان رقم الضمان الاجتماعي (SSN) في إسبانيا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضمان الاجتماعي (SSN) في إسبانيا.
ms.openlocfilehash: 4a531f0548aba2caa330423d493cf8e524c4ed73
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944539"
---
# <a name="spain-social-security-number-ssn"></a>رقم الضمان الاجتماعي الإسباني (SSN)

## <a name="format"></a>تنسيق

من 11 إلى 12 رقما

## <a name="pattern"></a>نمط

من 11 إلى 12 رقما:

- رقمين
- شرطة مائلة للأمام (اختيارية)
- من سبعة إلى ثمانية أرقام
- شرطة مائلة للأمام (اختيارية)
- رقمين

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_spanish_social_security_number` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.
    - تم العثور على كلمة أساسية منها `Keywords_spain_eu_ssn_or_equivalent` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_spanish_social_security_number` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- Spain SSN -->
    <Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85" relaxProximity="true" >
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spanish_social_security_number" />
          <Match idRef="Keywords_spain_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spanish_social_security_number" />
        </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- Ssn
- Ssn #
- الأمن الاجتماعي
- الضمان الاجتماعي لا
- رقم الضمان الاجتماعي
- número de la seguridad social