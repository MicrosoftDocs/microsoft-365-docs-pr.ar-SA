---
title: تعريف كيان رقم الحساب البنكي الأمريكي
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الحساب البنكي الأمريكي.
ms.openlocfilehash: 25b4c4018edc84e6bca4c1f24cea3def9a7adde8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944333"
---
# <a name="us-bank-account-number"></a>رقم الحساب البنكي الأمريكي

## <a name="format"></a>تنسيق

من 6 إلى 17 رقما

## <a name="pattern"></a>نمط

من 6 إلى 17 رقما متتاليا

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_usa_bank_account_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_usa_Bank_Account` .

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- التحقق من رقم الحساب
- تدقيق الحساب
- تدقيق الحساب #
- التحقق من رقم Acct
- التحقق من Acct #
- التحقق من رقم Acct.
- التحقق من رقم الحساب.
- رقم الحساب البنكي
- حساب بنكي #
- رقم Acct البنكي
- Acct البنكي #
- رقم Acct البنكي.
- رقم الحساب البنكي.
- رقم حساب التوفير
- حساب التوفير.
- حساب التوفير #
- رقم Acct للحفظ
- توفير Acct #
- Savings Acct No.
- رقم حساب التوفير.
- رقم حساب الخصم
- حساب الخصم
- حساب الخصم #
- رقم Acct للخصم
- أككت الخصم #
- رقم Acct للخصم.
- رقم حساب الخصم.