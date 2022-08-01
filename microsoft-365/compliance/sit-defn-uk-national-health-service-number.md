---
title: المملكة المتحدة تعريف كيان رقم الخدمة الصحية الوطنية
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
description: المملكة المتحدة تعريف كيان نوع المعلومات الحساسة لرقم خدمة الصحة الوطنية.
ms.openlocfilehash: d636be281b1652934fa7b4b83b3a4b5da7794a09
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944289"
---
# <a name="uk-national-health-service-number"></a>المملكة المتحدة رقم خدمة الصحة الوطنية

## <a name="format"></a>تنسيق

10-17 رقما مفصولة بمسافات

## <a name="pattern"></a>نمط

من 10 إلى 17 رقما:

- إما 3 أو 10 أرقام
- مساحة
- ثلاثة أرقام
- مساحة
- أربعة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_uk_nhs_number` عن المحتوى الذي يطابق النمط.
- أحد الإجراءات التالية صحيح:
    - تم العثور على كلمة أساسية منها `Keyword_uk_nhs_number` .
    - تم العثور على كلمة أساسية منها `Keyword_uk_nhs_number1` .
    - تم العثور على كلمة أساسية منها `Keyword_uk_nhs_number_dob` .
- يمر المجموع الاختباري.

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- خدمة الصحة الوطنية
- الصحي
- هيئة الخدمات الصحية
- هيئة الصحة

### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- معرف المريض
- تعريف المريض
- المريض لا
- رقم المريض

### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- دوب
- D.O.B
- تاريخ الميلاد
- تاريخ الميلاد