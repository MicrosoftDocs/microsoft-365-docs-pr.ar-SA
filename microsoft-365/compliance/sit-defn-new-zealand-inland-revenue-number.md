---
title: تعريف كيان رقم الإيرادات الداخلية في نيوزيلندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الإيرادات الداخلية في نيوزيلندا.
ms.openlocfilehash: 26604014771674a2177f3fee6c062e3bfcee4175
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988333"
---
# <a name="new-zealand-inland-revenue-number"></a>رقم إيرادات نيوزيلندا الداخلية

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

ثمانية أو تسعة أرقام مع محددات اختيارية

## <a name="pattern"></a>نمط

ثمانية أو تسعة أرقام مع محددات اختيارية

- رقمان أو ثلاثة أرقام
- مسافة اختيارية أو واصلة اختيارية
- ثلاثة أرقام
- مسافة اختيارية أو واصلة اختيارية
- ثلاثة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_new_zealand_inland_revenue_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_new_zealand_inland_revenue_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_new_zealand_inland_revenue_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- New Zealand Inland Revenue Number -->
      <Entity id="dd0fe2bc-7bcf-455f-bac1-83b1e3eb25fd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
          <Match idRef="Keywords_new_zealand_inland_revenue_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- رقم ird.
- ird no #
- nz ird
- /&ة نيوزيلندا
- رقم ird
- رقم الإيرادات الداخلية