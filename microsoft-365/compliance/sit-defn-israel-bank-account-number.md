---
title: تعريف كيان رقم الحساب البنكي في إسرائيل
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الحساب البنكي في إسرائيل.
ms.openlocfilehash: a68f90cd92432778d89d3f8494522a5ab2822d07
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944703"
---
# <a name="israel-bank-account-number"></a>رقم الحساب البنكي في إسرائيل

## <a name="format"></a>تنسيق

13 رقما

## <a name="pattern"></a>نمط

تنسيق:

- رقمين
- شرطة
- ثلاثة أرقام
- شرطة
- ثمانية أرقام

منسق:

- 13 رقما متتاليا

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_israel_bank_account_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_israel_bank_account_number` .

```xml
<!-- Israel Bank Account Number -->
<Entity id="7d08b2ff-a0b9-437f-957c-aeddbf9b2b25" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_israel_bank_account_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_israel_bank_account_number" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- رقم الحساب البنكي
- حساب بنكي
- رقم الحساب
- מספר חשבון בנק