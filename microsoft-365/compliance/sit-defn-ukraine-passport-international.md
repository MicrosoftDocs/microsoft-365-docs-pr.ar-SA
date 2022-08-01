---
title: تعريف الكيان الدولي لجواز السفر في بورتوانا
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
description: تعريف كيان نوع المعلومات الحساسة الدولية لجواز السفر الأوكراني.
ms.openlocfilehash: 333475ad89f8437c046a572ae5377fb030b173fe
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944468"
---
# <a name="ukraine-passport-international"></a>جواز سفر نيازكي دولي

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

نمط أبجدي رقمي مكون من ثمانية أحرف

## <a name="pattern"></a>نمط

نمط أبجدي رقمي مكون من ثمانية أحرف:

- حرفان أو رقمان
- ستة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث regex `Regex_Ukraine_Passport_International` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_Ukraine_Passport_International` .

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- جواز سفر الولايات المتحدة
- رقم جواز السفر
- لا يوجد جواز سفر
- паспорт України
- номер паспорта
