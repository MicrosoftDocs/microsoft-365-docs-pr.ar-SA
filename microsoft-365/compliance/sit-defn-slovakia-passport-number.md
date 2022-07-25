---
title: تعريف كيان رقم جواز السفر السلوفاكي
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز السفر السلوفاكي.
ms.openlocfilehash: d0bba50015395d0783d604779d7259244b881118
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988247"
---
# <a name="slovakia-passport-number"></a>رقم جواز سفر سلوفاكيا

## <a name="format"></a>تنسيق

نقش أبجدي رقمي لثمانية أو تسعة أحرف

## <a name="pattern"></a>نمط

حرف واحد (غير حساس لحالة الأحرف) متبوعا بسبعة أرقام أو حرفين (غير حساس لحالة الأحرف) متبوعا بستة أو سبعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovakia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_slovakia_eu_passport_number` تم العثور عليها.
- يبحث التعبير `Regex_eu_passport_date1` العادي عن التاريخ بالتنسيق DD.MM.YYYY أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovakia_eu_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_slovakia_eu_passport_number` تم العثور عليها.

```xml
      <!-- Slovakia Passport Number -->
      <Entity id="238e1f08-d80e-4793-af33-9b57918335b7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
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

### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- ííslo pasu
- íísla pasov
- pas  أذونات.
- Passeport n°
- n° Passeport

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية