---
title: تعريف كيان رقم الضريبة المضافة في ألمانيا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضريبة للقيمة المضافة في ألمانيا.
ms.openlocfilehash: 831b38ea1fcc7fe952ed28dc595e1d4a471ed505
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944407"
---
# <a name="germany-value-added-tax-number"></a>رقم ضريبة القيمة المضافة في ألمانيا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

نقش أبجدي رقمي من 11 حرفا

## <a name="pattern"></a>نمط

نمط أبجدي رقمي مكون من 11 حرفا:

- حرف D أو d
- حرف E أو e
- مساحة اختيارية
- ثلاثة أرقام
- مسافة أو فاصلة اختيارية
- ثلاثة أرقام
- مسافة أو فاصلة اختيارية
- ثلاثة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_germany_value_added_tax_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_germany_value_added_tax_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_germany_value_added_tax_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Germany Value Added Tax Number -->
      <Entity id="db177eb2-8811-4842-bffc-128c14aa219f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
          <Match idRef="Keywords_germany_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- ضريبه القيمه المضافه #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer