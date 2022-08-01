---
title: تعريف كيان رقم جواز السفر في بولندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز سفر بولندا.
ms.openlocfilehash: 910084a1c4a2c97256a2045e25ac436c248899fd
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944670"
---
# <a name="poland-passport-number"></a>رقم جواز سفر بولندا

يتم تضمين كيان نوع المعلومات الحساسة هذا في نوع المعلومات الحساسة لرقم جواز سفر الاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

## <a name="format"></a>تنسيق

حرفان وسبعة أرقام

## <a name="pattern"></a>نمط

حرفان (غير حساسين لحالة الأحرف) متبوعا بسبعة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_polish_passport_number_v2` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_polish_national_passport_number` تم العثور عليها.
- تم العثور على كلمة أساسية منها `Keywords_eu_passport_date` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_polish_passport_number_v2` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.
- تم العثور على كلمة أساسية من `Keywords_eu_passport_number` أو `Keyword_polish_national_passport_number` تم العثور عليها.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_polish_passport_number_v2` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
      <!-- Poland Passport Number -->
      <Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_passport_number_v2" />
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

### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- عدد paszportu
- paszportów رقمي
- paszportowe رقمي
- nr paszportu
- Nr. paszportu
- nr paszportów
- n° منفذ مرور
- منفذ المرور n°

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- تاريخ المشكلة
- تاريخ انتهاء الصلاحية