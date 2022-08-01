---
title: تعريف كيان رقم الضريبة المضافة في فرنسا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضريبة المضافة في فرنسا.
ms.openlocfilehash: 782030e563b59540b721ecfd40ee7470a2aaaa87
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944480"
---
# <a name="france-value-added-tax-number"></a>رقم الضريبة للقيمة المضافة في فرنسا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

نقش أبجدي رقمي من 13 حرفا

## <a name="pattern"></a>نمط

13 حرفا أبجديا رقميا:

- حرفان - FR (غير حساس لحالة الأحرف)
- مسافة اختيارية أو واصلة اختيارية
- حرفان أو رقمان
- مسافة اختيارية أو نقطة أو واصلة أو فاصلة
- ثلاثة أرقام
- مسافة اختيارية أو نقطة أو واصلة أو فاصلة
- ثلاثة أرقام
- مسافة اختيارية أو نقطة أو واصلة أو فاصلة
- ثلاثة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_france_value_added_tax_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_france_value_added_tax_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_france_value_added_tax_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- France Value Added Tax Number -->
      <Entity id="949121e6-ad9f-4379-8731-710342baea78" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_value_added_tax_number" />
          <Match idRef="Keywords_france_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_value_added_tax_number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- ضريبه القيمه المضافه #
- ضريبة القيمة المضافة
- تعريف numéro d'identification taxe sur ajoutée
- تقييم الضرائب ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification en