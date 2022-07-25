---
title: تعريف كيان رقم الضريبة المضافة للقيمة المضافة في المجر
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضريبة المضافة لقيمة المجر.
ms.openlocfilehash: 3ebc5921e0fd09fb98b1e86699aa3941bd214b96
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988291"
---
# <a name="hungary-value-added-tax-number"></a>رقم الضريبة للقيمة المضافة في المجر

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

نقش أبجدي رقمي من 10 أحرف

## <a name="pattern"></a>نمط

نقش أبجدي رقمي من 10 أحرف:

- حرفان - HU أو hu
- مساحة اختيارية
- ثمانية أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungarian_value_added_tax_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_hungarian_value_added_tax_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hungarian_value_added_tax_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Hungarian Value Added Tax Number -->
      <Entity id="976349a0-683b-477a-90f8-ff0a220d5592" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
          <Match idRef="Keywords_hungarian_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- ضريبه القيمه المضافه
- رقم ضريبة القيمة المضافة
- ضريبه القيمه المضافه #
- vatno #
- المجريةvatno #
- رقم الضريبة.
- ضريبة القيمة المضافة áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám