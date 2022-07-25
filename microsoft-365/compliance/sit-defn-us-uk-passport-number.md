---
title: الولايات المتحدة/المملكة المتحدة تعريف كيان رقم جواز السفر
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
description: الولايات المتحدة/المملكة المتحدة تعريف كيان نوع المعلومات الحساسة لرقم جواز السفر.
ms.openlocfilehash: 88caf63983d6f459f5ff201ae695f909489569cb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988300"
---
# <a name="usuk-passport-number"></a>الولايات المتحدة/المملكة المتحدة رقم جواز السفر

## <a name="format"></a>تنسيق

تسعة أرقام

## <a name="pattern"></a>نمط

- حرف واحد أو رقم واحد
- ثمانية أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_usa_uk_passport` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_uk_eu_passport_number` تم العثور عليها.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_date`

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_usa_uk_passport` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keywords_uk_eu_passport_number` تم العثور عليها.

```xml
    <!-- U.S. / U.K. Passport Number -->
    <Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
       <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
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

### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- جواز سفر بريطاني
- جواز سفر المملكة المتحدة