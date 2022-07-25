---
title: تعريف كيان رقم التعريف الضريبي السلوفيني
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الضريبي السلوفيني.
ms.openlocfilehash: baf6cef29b98b2963a4d3286e68c4d10008c415c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988244"
---
# <a name="slovenia-tax-identification-number"></a>رقم التعريف الضريبي السلوفيني

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

ثمانية أرقام بدون مسافات أو محددات

## <a name="pattern"></a>نمط

- رقم واحد من 1 إلى 9
- ستة أرقام
- خانة اختيار واحدة

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_slovenia_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_slovenia_eu_tax_file_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_slovenia_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Slovenia Tax Identification Number -->
      <Entity id="e47b071e-c352-4d70-8241-8c215ad65505" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
          <Match idRef="Keywords_slovenia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- dav jarna ذتيvilka
- identifikacijska ذtevilka davka
- edtevilka davذne datoteke
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