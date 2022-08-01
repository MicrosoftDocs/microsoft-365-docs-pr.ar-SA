---
title: تعريف كيان رقم العمل في أستراليا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الأعمال في أستراليا.
ms.openlocfilehash: 5d3b238dc631086be26399e3adf6c4fa2ef0cf99
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944278"
---
# <a name="australia-business-number"></a>رقم العمل في أستراليا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

11 رقما مع محددات اختيارية

## <a name="pattern"></a>نمط

11 رقما مع محددات اختيارية:

- رقمين
- واصلة أو مسافة اختيارية
- ثلاثة أرقام
- واصلة أو مسافة اختيارية
- ثلاثة أرقام
- واصلة أو مسافة اختيارية
- ثلاثة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_australian_business_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keywords_australian_business_number.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_australian_business_number عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Australia Business Number -->
      <Entity id="76e83b3b-01ee-4530-aced-e667a6609f49" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_australian_business_number" />
          <Match idRef="Keywords_australian_business_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_australian_business_number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- رقم الأعمال في أستراليا
- رقم العمل
- ايه #
- معرف الأعمال #
- معرف العمل
- ايه
- رجل أعمال #