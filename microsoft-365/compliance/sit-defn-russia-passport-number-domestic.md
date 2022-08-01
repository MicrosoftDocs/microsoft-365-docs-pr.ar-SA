---
title: تعريف الكيان المحلي لرقم جواز سفر روسيا
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
description: رقم جواز سفر روسيا تعريف كيان نوع المعلومات الحساسة المحلية.
ms.openlocfilehash: 0e74f6f8f268591cdf69148390e94e287f0e9686
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944421"
---
# <a name="russia-passport-number-domestic"></a>رقم جواز سفر روسيا محلياً

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

رقم مكون من 10 أرقام

## <a name="pattern"></a>نمط

رقم مكون من 10 أرقام:

- رقمين
- مسافة اختيارية أو واصلة اختيارية
- رقمين
- مساحة اختيارية
- ستة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث regex `Regex_Russian_Passport_Number_Domestic` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_Russian_Passport_Number` .

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

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