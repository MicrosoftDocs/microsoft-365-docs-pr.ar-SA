---
title: تعريف الكيان المحلي لجواز السفر الأوكراني
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
description: تعريف كيان نوع المعلومات الحساسة المحلية لجواز السفر الأوكراني.
ms.openlocfilehash: 6ef59f90149b87a726377100f8dc4bf14f267ccf
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944469"
---
# <a name="ukraine-passport-domestic"></a>جواز سفر محلي في أوكرانيا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

تسعة أرقام

## <a name="pattern"></a>نمط

تسعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث regex `Regex_Ukraine_Passport_Domestic` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_Ukraine_Passport_Domestic` .

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- جواز سفر الولايات المتحدة
- رقم جواز السفر
- لا يوجد جواز سفر
- паспорт України
- номер паспорта
- персональний