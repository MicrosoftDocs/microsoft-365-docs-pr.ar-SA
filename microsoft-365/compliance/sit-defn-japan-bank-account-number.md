---
title: تعريف كيان رقم الحساب البنكي الياباني
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الحساب البنكي الياباني.
ms.openlocfilehash: 1e762a32654e6aa14e0b20d7e09ab5167cc330a5
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944450"
---
# <a name="japan-bank-account-number"></a>رقم الحساب البنكي الياباني

## <a name="format"></a>تنسيق

سبعة أو ثمانية أرقام

## <a name="pattern"></a>نمط

رقم الحساب البنكي:

- سبعة أو ثمانية أرقام
- رمز فرع الحساب البنكي:

- أربعة أرقام
- مسافة أو شرطة (اختياري)
- ثلاثة أرقام

المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_jp_bank_account` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_jp_bank_account` .
- أحد الإجراءات التالية صحيح:

- تبحث الدالة `Func_jp_bank_account_branch_code` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_jp_bank_branch_code` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_jp_bank_account` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_jp_bank_account` .

```xml
<!-- Japan Bank Account Number -->
<Entity id="d354f95b-96ee-4b80-80bc-4377312b55bc" patternsProximity="300" recommendedConfidence="75">
  <Version minEngineVersion="15.01.0131.000">
    <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_jp_bank_account" />
          <Match idRef="Keyword_jp_bank_account" />
          <Any minMatches="1">
            <Match idRef="Func_jp_bank_account_branch_code" />
            <Match idRef="Keyword_jp_bank_branch_code" />
          </Any>
      </Pattern>
  </Version>
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_bank_account" />
        <Match idRef="Keyword_jp_bank_account" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- التحقق من رقم الحساب
- تدقيق الحساب
- تدقيق الحساب #
- التحقق من رقم Acct
- التحقق من Acct #
- التحقق من رقم Acct.
- التحقق من رقم الحساب.
- رقم الحساب البنكي
- حساب بنكي
- حساب بنكي #
- رقم Acct البنكي
- Acct البنكي #
- رقم Acct البنكي.
- رقم الحساب البنكي.
- رقم حساب التوفير
- حساب التوفير
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
- 口座番号
- 銀行口座
- 銀行口座番号
- 総合口座
- 普通預金口座
- 普通口座
- 当座預金口座
- 当座口座
- 預金口座
- 振替口座
- 銀行
- バンク

### <a name="keyword_jp_bank_branch_code"></a>Keyword_jp_bank_branch_code

- 支店番号
- 支店コード
- 店番号