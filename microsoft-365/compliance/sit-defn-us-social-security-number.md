---
title: تعريف كيان رقم الضمان الاجتماعي (SSN) في الولايات المتحدة
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضمان الاجتماعي (SSN) في الولايات المتحدة.
ms.openlocfilehash: 2644ff5be51d8316007d20ec3c8918ce0e2003c1
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988282"
---
# <a name="us-social-security-number-ssn"></a>رقم الضمان الاجتماعي (SSN) في الولايات المتحدة

## <a name="format"></a>تنسيق

تسعة أرقام، والتي قد تكون في نمط منسق أو غير منسق

> [!NOTE]
> إذا تم إصداره قبل منتصف عام 2011، فإن SSN لديه تنسيق قوي حيث يجب أن تقع أجزاء معينة من الرقم ضمن نطاقات معينة لتكون صالحة (ولكن لا يوجد مجموعة تدقيق).

## <a name="pattern"></a>نمط

تبحث أربع دالات عن SSNs في أربعة أنماط مختلفة:

- `Func_ssn` البحث عن شبكات SSN ذات تنسيق قوي قبل 2011 تم تنسيقه بشرطات أو مسافات (ddd-dddd OR ddd ddd ddd)
- `Func_unformatted_ssn` البحث عن شبكات SSN ذات تنسيق قوي ما قبل 2011 غير منسق كتسع أرقام متتالية (ddddddd)
- `Func_randomized_formatted_ssn` البحث عن SSNs ما بعد 2011 التي تم تنسيقها بشرطات أو مسافات (ddd-dddd OR ddd ddd)
- `Func_randomized_unformatted_ssn` البحث عن شبكات SSN لما بعد 2011 غير المنسقة كتسع أرقام متتالية (dddddddd)

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_ssn` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ssn` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_unformatted_ssn` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ssn` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- الدالة `Func_randomized_formatted_ssn` أو `Func_randomized_unformatted_ssn` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ssn` .

```xml
<!-- U.S. Social Security Number (SSN) -->
  <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_randomized_formatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="55">
        <IdMatch idRef="Func_randomized_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
  </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_ssn"></a>Keyword_ssn

- رقم SSA
- رقم الضمان الاجتماعي
- الضمان الاجتماعي #
- الضمان الاجتماعي #
- الضمان الاجتماعي لا
- الضمان الاجتماعي #
- Soc Sec
- SSN
- SSNS
- SSN #
- SS #
- SSID