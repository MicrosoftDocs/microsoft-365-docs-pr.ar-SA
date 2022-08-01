---
title: تعريف كيان رقم جواز سفر السويد
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز سفر السويد.
ms.openlocfilehash: 497965aea803a162fc97bb64fa456191f8788aab
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944233"
---
# <a name="sweden-passport-number"></a>رقم جواز سفر السويد

## <a name="format"></a>تنسيق

ثمانية أرقام

## <a name="pattern"></a>نمط

ثمانية أرقام متتالية

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_sweden_passport_number عن المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_sweden_passport` تم العثور عليها.
- يبحث التعبير `Regex_sweden_eu_passport_date` العادي عن تاريخ بتنسيق DD MMM/MMM YY (01 JAN/JAN 12) أو تم العثور على كلمة أساسية منه `Keywords_eu_passport_date` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_sweden_passport_number عن المحتوى الذي يتطابق مع النمط.
- كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_sweden_passport` تم العثور عليها.

```xml
    <!-- Sweden Passport Number -->
    <Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_sweden_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
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

### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- بطاقة تسجيل الأشخاص الذين تم تسجيلهم
- رسوم معالجة g3
- إدخال متعدد
- Numéro de passeport
- passeport n °
- passeport غير
- منفذ المرور #
- منفذ المرور #
- passeportnon
- passeportn °
- رقم المرور
- تمرير nr
- تأشيرة الشينجن
- تواشير الشينجن
- إدخال واحد
- تمرير sverige
- متطلبات طلب الحصول على
- معالجة الملفات
- نوع

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية