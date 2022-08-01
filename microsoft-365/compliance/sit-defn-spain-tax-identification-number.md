---
title: تعريف كيان رقم التعريف الضريبي في إسبانيا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الضريبي في إسبانيا.
ms.openlocfilehash: de7075c6ff81c97537b9f7145fd269a671b8e1dc
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944596"
---
# <a name="spain-tax-identification-number"></a>رقم التعريف الضريبي الإسباني

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

سبعة أو ثمانية أرقام وحرف واحد أو حرفان في النمط المحدد

## <a name="pattern"></a>نمط

الأشخاص الطبيعيون الأسبانيون مع بطاقة هوية وطنية أسبانيا:

- ثمانية أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

أسبان غير مقيمين بدون بطاقة هوية وطنية أسبانيا

- حرف واحد من الأحرف الكبيرة "L" (حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

الإسبانيون المقيمون الذين تقل أعمارهم عن 14 سنة بدون بطاقة هوية وطنية في إسبانيا:

- حرف واحد من الأحرف الكبيرة "K" (حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

مهى مع رقم تعريف المقيمين

- حرف واحد من الأحرف الكبيرة يكون "X" أو "Y" أو "Z" (حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

أجهزة نواة بدون رقم تعريف نافل

- حرف واحد من الأحرف الكبيرة يكون "M" (حساس لحالة الأحرف)
- سبعة أرقام
- حرف واحد من الأحرف الكبيرة (حساس لحالة الأحرف)

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_tax_file_number` أو `Func_spain_eu_DL_and_NI_number_citizen` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_spain_eu_tax_file_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_tax_file_number` أو `Func_spain_eu_DL_and_NI_number_citizen` البحث عن المحتوى الذي يطابق النمط.

```xml
      <!-- Spain Tax Identification Number -->
      <Entity id="10f0d113-b0e1-47dc-872a-a4f45b9376a3" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- Cif
- مقتباس #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- ملف الضريبة لا
- رقم ملف الضريبة
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