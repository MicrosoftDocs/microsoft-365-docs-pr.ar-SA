---
title: تعريف كيان رقم التأمين الاجتماعي في كندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التأمين الاجتماعي في كندا.
ms.openlocfilehash: 9af5cc026da5ac6bd414ebd80ded934efb90effb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944524"
---
# <a name="canada-social-insurance-number"></a>رقم التأمين الاجتماعي في كندا

## <a name="format"></a>تنسيق

تسعة أرقام مع واصلات اختيارية أو مسافات

## <a name="pattern"></a>نمط

تنسيق:

- ثلاثة أرقام
- واصلة أو مسافة
- ثلاثة أرقام
- واصلة أو مسافة
- ثلاثة أرقام

غير منسق: تسعة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_canadian_sin عن المحتوى الذي يتطابق مع النمط.
- على الأقل نمطان من الأنماط التالية:
    - تم العثور على كلمة أساسية منها `Keyword_sin` .
    - تم العثور على كلمة أساسية منها `Keyword_sin_collaborative` .
    - تبحث الدالة `Func_eu_date` عن تاريخ بتنسيق التاريخ الصحيح.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_unformatted_canadian_sin عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية منها `Keyword_sin` .
- يمر المجموع الاختباري.

```xml
<!-- Canada Social Insurance Number -->
<Entity id="a2f29c85-ecb8-4514-a610-364790c0773e" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_canadian_sin" />
        <Any minMatches="2">
          <Match idRef="Keyword_sin" />
          <Match idRef="Keyword_sin_collaborative" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_canadian_sin" />
        <Match idRef="Keyword_sin" />
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_sin"></a>Keyword_sin

- الخطيئه
- التأمين الاجتماعي
- numero d'assurance sociale
- الخطايا
- Ssn
- ssns
- الضمان الاجتماعي
- numero d'assurance social
- رقم التعريف الوطني
- المعرف الوطني
- الخطيئه #
- soc ins
- ins الاجتماعية

### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- رخصة القيادة
- رخصه
- رخصة القيادة
- رخصة القيادة
- دوب
- تاريخ الميلاد
- عيد ميلاد
- تاريخ الميلاد