---
title: تعريف كيان رقم الحساب البنكي في أستراليا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الحساب البنكي في أستراليا.
ms.openlocfilehash: df46075da0b85f306a52b1971db7b15c6a13028b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944277"
---
# <a name="australia-bank-account-number"></a>رقم الحساب البنكي في أستراليا

## <a name="format"></a>تنسيق

من ستة إلى 10 أرقام مع رقم فرع ولاية بنكية أو بدونه

## <a name="pattern"></a>نمط

رقم الحساب من 6 إلى 10 أرقام.

رقم فرع ولاية أستراليا المصرفي:

- ثلاثة أرقام
- واصلة
- ثلاثة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_australia_bank_account_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_australia_bank_account_number.
- يبحث التعبير العادي Regex_australia_bank_account_number_bsb عن المحتوى الذي يطابق النمط.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_australia_bank_account_number عن المحتوى الذي يتطابق مع النمط.

- تم العثور على كلمة أساسية من Keyword_australia_bank_account_number.

```xml
<!-- Australia Bank Account Number -->
<Entity id="74a54de9-2a30-4aa0-a8aa-3d9327fc07c7" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
        <Match idRef="Regex_australia_bank_account_number_bsb" />
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
  </Pattern>
 </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- رمز بنك swift
- بنك
- العملة الأساسية
- حساب الولايات المتحدة الأمريكية
- عنوان حامل
- عنوان البنك
- حساب المعلومات
- عمليات تحويل الأموال
- الرسوم المصرفية
- تفاصيل البنك
- معلومات مصرفية
- الأسماء الكاملة
- الوكاله