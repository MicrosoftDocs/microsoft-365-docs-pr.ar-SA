---
title: تعريف كيان رقم التعريف الوطني في  لاسيمبيرغ (الأشخاص غير الطبيعيين)
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
description: تعريف كيان نوع المعلومات الحساسة ل Namemburg لرقم التعريف الوطني (الأشخاص غير الطبيعيين).
ms.openlocfilehash: 0e5a82862c51aafcc6d3033fccb1a8ec1b561671
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988351"
---
# <a name="luxemburg-national-identification-number-non-natural-persons"></a>رقم التعريف الوطني في لوسمبيرغ (أشخاص غير طبيعيين)

## <a name="format"></a>تنسيق

11 رقما

## <a name="pattern"></a>نمط

11 رقما

- رقمين
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- رقمين
- خانة اختيار واحدة

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_luxemburg_eu_tax_file_number_non_natural` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_luxemburg_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_luxemburg_eu_tax_file_number_non_natural` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Luxemburg National Identification Number (Non-natural persons) -->
      <Entity id="84bffa3a-d805-4788-a613-b1e4df3804cf" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Match idRef="Keywords_luxemburg_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- étain غير
- étain #
- المعرف d'imp imp t
- معرف الضريبة في لكسمر لكسمر
- numéro d'étain
- numéro d'identification fiscal لكسمبورجية
- numéro d'identification fiscale
- الضمان الاجتماعي
- sozialunterstützung
- sozialversécherung
- sozialversicherungsausweis
- معرف steier
- steier identifikatiounsnummer
- steier nummer
- معرف steuer
- steueridentifikationsnummer
- رقم عمودي
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
- زين #
- زين
- zinnzahl