---
title: تعريف كيان بطاقة هوية النمسا
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
description: تعريف كيان نوع المعلومات الحساسة لبطاقة هوية النمسا.
ms.openlocfilehash: 5a7cae0eabfa179bda83a09dc6a70a3e6e5048a6
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944628"
---
# <a name="austria-identity-card"></a>بطاقة هوية النمسا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

مجموعة مكونة من 24 حرفا من الأحرف والأرقام والأحرف الخاصة

## <a name="pattern"></a>نمط

24 حرفا:

- 22 حرفا (غير حساسة لحالة الأحرف) أو أرقام أو خطوط مائلة عكسية أو شرطة مائلة للأمام أو علامات الجمع

- حرفان (غير حساسين لحالة الأحرف) أو أرقام أو شرطة مائلة عكسية أو شرطة مائلة للأمام أو علامات الجمع أو علامات التساوي

## <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_austria_eu_national_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_austria_eu_national_id_card` .

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- رقم الهوية
- المعرف الوطني
- personalausweis republik österreich