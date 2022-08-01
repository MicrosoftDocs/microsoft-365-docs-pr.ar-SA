---
title: تعريف كيان رقم بطاقة هوية تابعة لسلة الهوية
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة الهوية اللفحة.
ms.openlocfilehash: b9f728930b14bb14954e45473c1c327ad36f0aa0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944461"
---
# <a name="malta-identity-card-number"></a>رقم بطاقة هوية الهويات في مالطا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

سبعة أرقام متبوعة بحرف واحد

## <a name="pattern"></a>نمط

سبعة أرقام متبوعة بحرف واحد:

- سبعة أرقام
- حرف واحد في "M، G، A، P، L، H، B، Z" (غير حساس لحالة الأحرف)

## <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_malta_eu_national_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_malta_eu_national_id_card` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_malta_eu_national_id_card` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- Malta Identity Card Number -->
      <Entity id="854b36b3-a388-4ac8-a4ec-677c2b5e4356" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
          <Match idRef="Keywords_malta_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- رقم خدمة المواطنين
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- رمز رقمي شخصي
- رقم تعريف فريد
- رقم هوية فريد
- uniqueidentityno #