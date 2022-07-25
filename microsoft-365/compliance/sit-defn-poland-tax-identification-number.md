---
title: تعريف كيان رقم التعريف الضريبي في بولندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الضريبي في بولندا.
ms.openlocfilehash: 793fbb9d82a94a9328adb665792768f051cf927f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988342"
---
# <a name="poland-tax-identification-number"></a>رقم التعريف الضريبي في بولندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

11 رقما بدون مسافات أو محددات

## <a name="pattern"></a>نمط

11 رقما

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_poland_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_poland_eu_tax_file_number` .

```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- خطه التنفيذ الوطنيه #
- خطه التنفيذ الوطنيه
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
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
- معرف ضريبة القيمة المضافة #
- معرف ضريبة القيمة المضافة
- ضريبة القيمة المضافة لا
- رقم ضريبة القيمة المضافة
- vatid #
- vatid
- vatno #