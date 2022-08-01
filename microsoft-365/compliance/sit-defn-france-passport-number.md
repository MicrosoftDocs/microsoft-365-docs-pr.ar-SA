---
title: تعريف كيان رقم جواز سفر فرنسا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز سفر فرنسا.
ms.openlocfilehash: f358edd8955b17e89354af536381327957eb38bc
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944688"
---
# <a name="france-passport-number"></a>رقم جواز سفر فرنسا

يتوفر هذا الكيان في نوع المعلومات الحساسة لرقم جواز سفر الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

## <a name="format"></a>تنسيق

تسعة أرقام وأحرف

## <a name="pattern"></a>نمط

تسعة أرقام وأحرف:

- رقمين
- حرفان (غير حساس لحالة الأحرف)
- خمسة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_fr_passport` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_france_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date3` العادي عن التاريخ بالتنسيق DD MM YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_fr_passport` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_france_eu_passport_number` تم العثور عليها.

```xml
    <!-- France Passport Number -->
    <Entity id="3008b884-8c8c-4cd8-a289-99f34fc7ff5d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

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

### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passeport
- passeport n °
- passeport غير
- منفذ المرور #
- منفذ المرور #
- passeportnon
- passeportn °
- passeport français
- passeport livre
- carte passeport
- numéro passeport
- منفذ المرور n°
- n° du passeport
- n° منفذ مرور

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية