---
title: تعريف كيان تعريف التعريف الفردي للولايات المتحدة (ITIN)
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الفردي للولايات المتحدة (ITIN).
ms.openlocfilehash: c99635c29bb5b720ecc2d70577fe66d508ce9d9c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944647"
---
# <a name="us-individual-taxpayer-identification-number-itin"></a>رقم التعريف الفردي للولايات المتحدة (ITIN)

## <a name="format"></a>تنسيق

تسعة أرقام تبدأ ب "9" وتحتوي على "7" أو "8" كرقم الرابع، ويتم تنسيقها اختياريا بمسافات أو شرط

## <a name="pattern"></a>نمط

تنسيق:

- الرقم "9"
- رقمين
- مسافة أو شرطة
- a "7" أو "8"
- رقم
- مسافة أو شرطة
- أربعة أرقام

منسق:

- الرقم "9"
- رقمين
- a "7" أو "8"
- خمسة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_formatted_itin` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_itin` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_unformatted_itin` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_itin` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- الدالة `Func_formatted_itin` أو `Func_unformatted_itin` البحث عن المحتوى الذي يطابق النمط.

```xml
    <!-- U.S. Individual Taxpayer Identification Number (ITIN) -->
    <Entity id="e55e2a32-f92d-4985-a35d-a0b269eb687b" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_formatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_formatted_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_unformatted_itin" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_itin"></a>Keyword_itin

- دافعي الضرائب
- معرف الضريبة
- التعريف الضريبي
- itin
- i.t.i.n.
- Ssn
- القصدير
- الضمان الاجتماعي
- مدفع الضريبة
- تثبيتات
- سيارة أجرة
- أجهزة فردية