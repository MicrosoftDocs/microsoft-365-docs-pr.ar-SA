---
title: تعريف الكيان الدولي لرقم جواز سفر روسيا
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
description: رقم جواز سفر روسيا تعريف كيان نوع المعلومات الحساسة الدولية.
ms.openlocfilehash: c4f36f4e8baac5aaf385ebe1a3ae0d9b33fdc365
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944419"
---
# <a name="russia-passport-number-international"></a>رقم جواز سفر روسيا الدولي

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

رقم مكون من تسعة أرقام

## <a name="pattern"></a>نمط

رقم مكون من تسعة أرقام:

- رقمين
- مسافة اختيارية أو واصلة اختيارية
- سبعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث regex `Regex_Russian_Passport_Number_International` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_Russian_Passport_Number` .

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- رقم جواز السفر
- لا يوجد جواز سفر
- جواز السفر #
- معرف جواز السفر
- جواز سفر #
- رقم جواز السفر #
- паспорт нет
- паспорт المعرف
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #