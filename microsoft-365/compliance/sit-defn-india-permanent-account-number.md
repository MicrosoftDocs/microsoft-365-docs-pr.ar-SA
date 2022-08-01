---
title: تعريف كيان رقم الحساب الدائم (PAN) في الهند
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الحساب الدائم (PAN) في الهند.
ms.openlocfilehash: bf712e0949bba5f1e5396d61ff70f41b70ba579d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944303"
---
# <a name="india-permanent-account-number-pan"></a>رقم الحساب الدائم في الهند (PAN)

## <a name="format"></a>تنسيق

10 أحرف أو أرقام

## <a name="pattern"></a>نمط

10 أحرف أو أرقام:

- ثلاثة أحرف (غير حساسة لحالة الأحرف)
- حرف في C وP وH وF وA وT وB وL وJ وG (غير حساس لحالة الأحرف)
- رسالة
- أربعة أرقام
- حرف يمثل خانة اختيار أبجدية

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_india_permanent_account_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_india_permanent_account_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_india_permanent_account_number` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- India Permanent Account Number -->
      <Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_india_permanent_account_number" />
          <Match idRef="Keyword_india_permanent_account_number" />
        </Pattern>
        <Version minEngineVersion="15.20.3520.000">
          <Pattern confidenceLevel="65">
            <IdMatch idRef="Regex_india_permanent_account_number" />
          </Pattern>
        </Version>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- رقم الحساب الدائم
- عموم