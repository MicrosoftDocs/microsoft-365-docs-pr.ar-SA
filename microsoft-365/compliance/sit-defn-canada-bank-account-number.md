---
title: تعريف كيان رقم الحساب البنكي في كندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الحساب البنكي في كندا.
ms.openlocfilehash: c7008b17ff532a55dfefc079a07fc8e95f789b04
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944516"
---
# <a name="canada-bank-account-number"></a>رقم الحساب البنكي في كندا

## <a name="format"></a>تنسيق

7 أرقام أو 12 رقما

## <a name="pattern"></a>نمط

رقم الحساب البنكي في كندا هو 7 أو 12 رقما.

رقم النقل لحساب كندا البنكي هو:

- خمسة أرقام
- واصلة
- ثلاثة أرقام OR
- صفر "0"
- ثمانية أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_canada_bank_account_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_canada_bank_account_number` .
- يبحث التعبير `Regex_canada_bank_account_transit_number` العادي عن المحتوى الذي يطابق النمط.

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_canada_bank_account_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_canada_bank_account_number` .

```xml
<!-- Canada Bank Account Number -->
<Entity id="552e814c-cb50-4d94-bbaa-bb1d1ffb34de" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
        <Match idRef="Regex_canada_bank_account_transit_number" />
   </Pattern>
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
   </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- مدخرات كندا
- وكالة الإيرادات في كندا
- المؤسسة المالية الكندية
- نموذج الإيداع المباشر
- مواطن أمريكي
- ممثل قانوني
- عام للكاتم
- المفوض لليمين
- ميزة رعاية الأطفال
- الرعاية الشاملة للأطفال
- ميزة ضريبة الأطفال في كندا
- ميزة ضريبة الدخل
- ضريبة المبيعات الموزعة
- رقم التأمين الاجتماعي
- استرداد ضريبة الدخل
- ميزة ضريبة الأطفال
- دفعات/ة
- رقم المؤسسة
- طلب إيداع
- معلومات مصرفية
- الإيداع المباشر