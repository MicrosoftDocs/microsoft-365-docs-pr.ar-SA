---
title: تعريف كيان رقم جواز سفر أستراليا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز السفر في أستراليا.
ms.openlocfilehash: 9f879dc2f071398f7c3ba49b7fcded8be220e07b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944381"
---
# <a name="australia-passport-number"></a>رقم جواز سفر أستراليا

## <a name="format"></a>تنسيق

ثمانية أو تسعة أحرف أبجدية رقمية

## <a name="pattern"></a>نمط

- حرف واحد (N، E، D، F، A، C، U، X) متبوعا بسبعة أرقام أو
- حرفان (PA، PB، PC، PD، PE، PF، PU، PW، PX، PZ) متبوعا بسبعة أرقام.

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_australia_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_australia_passport_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_australia_passport_number` العادي عن المحتوى الذي يطابق النمط.

```xml
    <!-- Australia Passport Number -->
    <Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Match idRef="Keyword_australia_passport_number" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_australia_passport_number" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

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
- تفاصيل جواز السفر
- وجنسية
- من أستراليا
- قسم الشؤون الخارجية
- بطاقة الهوية الوطنية
- مستند السفر
- الجهة المصدرة