---
title: تعريف كيان رقم الضمان الاجتماعي في المجر (TAJ)
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضمان الاجتماعي في المجر (TAJ).
ms.openlocfilehash: 52821cda4b997567a66e2527653ed0a1341a378e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944590"
---
# <a name="hungary-social-security-number-taj"></a>رقم الضمان الاجتماعي في المجر (TAJ)

## <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

## <a name="pattern"></a>نمط

تسعة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungary_eu_ssn_or_equivalent` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_hungary_eu_ssn_or_equivalent` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungary_eu_ssn_or_equivalent` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Hungarian Social Security Number (TAJ) -->
      <Entity id="0de78315-9537-47f5-95ab-b3e77eba3993" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_hungary_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- رقم الضمان الاجتماعي المجري
- رقم الضمان الاجتماعي
- رقم الأمان الاجتماعي #
- hssn #
- الأمان الاجتماعي غير متعلق
- hssn
- تاج
- تاج #
- Ssn
- Ssn #
- الضمان الاجتماعي لا
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám