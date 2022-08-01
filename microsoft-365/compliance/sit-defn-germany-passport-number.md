---
title: تعريف كيان رقم جواز سفر ألمانيا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز سفر ألمانيا.
ms.openlocfilehash: 3e58ded04d1507903c890598a7f2c7d892ac45e7
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944523"
---
# <a name="germany-passport-number"></a>رقم جواز سفر ألمانيا

## <a name="format"></a>تنسيق

من 9 إلى 11 حرفا

## <a name="pattern"></a>نمط

- حرف واحد في C وF وG وH وJ وK (غير حساس لحالة الأحرف)
- ثمانية أرقام أو أحرف في C وF وG وH وJ وK وL وM وN وP وR وT وV وW وX وY وZ (غير حساس لحالة الأحرف)
- خانة اختيار رقمية
- d/D اختياري

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_german_passport_checksum` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keyword_german_passport` أو `Keywords_eu_passport_number_common` تم العثور عليها.
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_german_passport` عن المحتوى الذي يتطابق مع نمط الأحرف التسعة (بدون خانة اختيار الرقم والاختياري d/D).
- تم العثور على كلمة أساسية من `Keyword_german_passport` أو `Keywords_eu_passport_number_common` تم العثور عليها.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_german_passport_checksum` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- German Passport Number -->
    <Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keywords_eu_passport_number_common" />
        </Any>
      </Pattern>
      <Version minEngineVersion="15.20.4570.0">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_german_passport_checksum" />
          <Any minMatches="1">
            <Match idRef="Keyword_german_passport" />
            <Match idRef="Keywords_eu_passport_number_common" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_german_passport_checksum" />
        </Pattern>
      </Version>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_german_passport"></a>Keyword_german_passport

- إعادة الدفع
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- رقم المرور
- reisepässe
- passeport no.
- لا يوجد منفذ مرور

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