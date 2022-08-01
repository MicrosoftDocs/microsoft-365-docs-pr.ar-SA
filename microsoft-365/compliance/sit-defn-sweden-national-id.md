---
title: تعريف كيان المعرف الوطني في السويد
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
description: تعريف كيان نوع المعلومات الحساسة لمعرف السويد.
ms.openlocfilehash: 77d0fd72a4293bdc8cae0aa806899b30baa21ed8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944645"
---
# <a name="sweden-national-id"></a>المعرف الوطني للسويد

## <a name="format"></a>تنسيق

10 أو 12 رقما ومحدد اختياري

## <a name="pattern"></a>نمط

10 أو 12 رقما ومحدد اختياري:

- رقمان (اختياري)
- ستة أرقام بتنسيق التاريخ YYMMDD
- محدد "-" أو "+" (اختياري)
- أربعة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_swedish_national_identifier` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_swedish_national_identifier`
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_swedish_national_identifier` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- Sweden National ID -->
    <Entity id="f69aaf40-79be-4fac-8f05-fd1910d272c8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_swedish_national_identifier" />
        <Match idRef="Keywords_swedish_national_identifier" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_swedish_national_identifier" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- المعرف لا
- رقم المعرف
- معرف #
- لا يوجد تعريف
- رقم التعريف
- identifikationsnumret #
- identifikationsnumret
- التعامل مع الهويات
- مستند هوية
- لا هوية
- رقم الهوية
- id-nummer
- المعرف الشخصي
- رقم الشخص #
- رقم الشخص
- skatteidentifikationsnummer