---
title: تعريف كيان رقم الحساب البنكي في نيوزيلندا
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
description: تعريف كيان نوع المعلومات الحساسة لحساب بنك نيوزيلندا.
ms.openlocfilehash: b33eeb1e83f5efc9dd805c9ea036c6f30de600a0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944388"
---
# <a name="new-zealand-bank-account-number"></a>رقم الحساب المصرفي النيوزيلندي

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

نمط من 14 رقما إلى 16 رقما مع محدد اختياري

## <a name="pattern"></a>نمط

نمط مكون من 14 رقما إلى 16 رقما مع محدد اختياري:

- رقمين
- واصلة أو مسافة اختيارية
- ثلاثة إلى أربعة أرقام
- واصلة أو مسافة اختيارية
- سبعة أرقام
- واصلة أو مسافة اختيارية
- رقمان إلى ثلاثة أرقام
- واصلة خيارات أو مسافة

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_new_zealand_bank_account_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_new_zealand_bank_account_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_new_zealand_bank_account_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- New Zealand Bank Account Number -->
      <Entity id="1a97fc2b-dd2f-48f1-bc4e-2ddf25813956" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
          <Match idRef="Keywords_new_zFealand_bank_account_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- رقم الحساب
- حساب بنكي
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr