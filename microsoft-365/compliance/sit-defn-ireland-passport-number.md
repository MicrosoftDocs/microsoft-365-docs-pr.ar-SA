---
title: تعريف كيان رقم جواز سفر أيرلندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز سفر أيرلندا.
ms.openlocfilehash: 5924b689096896e6d09cecca0c022c05972dedef
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944565"
---
# <a name="ireland-passport-number"></a>رقم جواز سفر أيرلندا

## <a name="format"></a>تنسيق

حرفان أو رقمان متبوعا بسبعة أرقام بدون مسافات أو محددات

### <a name="pattern"></a>نمط

حرفان أو رقمان متبوعا بسبعة أرقام:

- رقمان أو حرفان (غير حساس لحالة الأحرف)
- سبعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ireland_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_ireland_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_ireland_eu_passport_date` العادي عن التاريخ بالتنسيق DD MMM/MMM YYYY (مثال - 01 BEA/MAY 1988) أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ireland_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_ireland_eu_passport_number` تم العثور عليها.

```xml
      <!-- Ireland Passport Number -->
      <Entity id="a2130f27-9ee2-4103-84f9-a6b1ee7d0cbf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_ireland_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- جواز السفر #
- جواز السفر #
- معرف جواز سفر
- جوازات السفر
- جواز سفر
- لا يوجد جواز سفر
- رقم جواز السفر
- رقم جواز السفر
- رقم جواز سفر
- أرقام جواز السفر

### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha pasanna
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cárta
- uimhir chárta

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية