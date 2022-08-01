---
title: تعريف كيان رقم التعريف الضريبي لسلفاين
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الضريبي لسلسلة التعريف الضريبية.
ms.openlocfilehash: 5f77f6755ff69bf200a3999e684901bf39bdf6d9
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944396"
---
# <a name="malta-tax-identification-number"></a>رقم التعريف الضريبي في دائرة الضرائب

## <a name="format"></a>تنسيق

بالنسبة إلى المواطنين المالطيين:

- سبعة أرقام وحرف واحد في النمط المحدد

المواطنين غير المالطيين والكيانات المالطية:

- تسعة أرقام

## <a name="pattern"></a>نمط

المواطنين المالطيين: سبعة أرقام وحرف واحد

- سبعة أرقام
- حرف واحد (غير حساس لحالة الأحرف)

المواطنين غير المالطيين والكيانات المالطية: تسعة أرقام

- تسعة أرقام

## <a name="checksum"></a>المجموع الاختباري

غير قابل للتطبيق

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- regex `Regex_malta_eu_tax_file_number`  أو `Regex_malta_eu_tax_file_number_non_maltese_national` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_malta_eu_tax_file_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- regex `Regex_malta_eu_tax_file_number` أو `Regex_malta_eu_tax_file_number_non_maltese_national` البحث عن المحتوى الذي يطابق النمط.

```xml
      <!-- Malta Tax ID Number -->
      <Entity id="ec830c63-65f4-45d0-9d8c-910dc8334b20" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- رقم خدمة المواطنين
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- رمز رقمي شخصي
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- رقم تعريف فريد
- رقم هوية فريد
- uniqueidentityno #