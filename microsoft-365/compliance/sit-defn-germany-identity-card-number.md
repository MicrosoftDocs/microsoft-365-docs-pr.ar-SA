---
title: تعريف كيان رقم بطاقة الهوية في ألمانيا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة الهوية في ألمانيا.
ms.openlocfilehash: 961dec17e4f68a1650cd0c4360ccf5244bef0062
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944402"
---
# <a name="germany-identity-card-number"></a>رقم بطاقة الهوية في ألمانيا

## <a name="format"></a>تنسيق

منذ 1 نوفمبر 2010: من تسعة إلى 11 حرفا ورقما

من 1 أبريل 1987 حتى 31 أكتوبر 2010: 10 أرقام

## <a name="pattern"></a>نمط

منذ 1 نوفمبر 2010: 9 إلى 11 حرفا من النمط الأبجدي الرقمي
- واحد L، M، N، P، R، T، V، W، X، Y (غير حساس لحالة الأحرف)
- ثمانية أرقام أو أحرف في C وF وG وH وJ وK وL وM وN وP وR وT وV وW وX وY وZ (غير حساس لحالة الأحرف)
- خانة اختيار رقمية
- d/D اختياري

من 1 أبريل 1987 حتى 31 أكتوبر 2010:

- 10 أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_german_id_card_with_check` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_germany_id_card` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي عن `Regex_germany_id_card` المحتوى الذي يطابق النمط (9 أحرف بدون خانة اختيار تم إصدارها قبل 2010 أو 10 أرقام تم إصدارها في 2010).
- تم العثور على كلمة أساسية منها `Keyword_germany_id_card` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_german_id_card_with_check` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
      <!-- Germany Identity Card Number -->
      <Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
         <IdMatch idRef="Regex_germany_id_card" />
         <Match idRef="Keyword_germany_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.4545.000">
          <Pattern confidenceLevel="85">
           <IdMatch idRef="Func_german_id_card_with_check" />
            <Match idRef="Keyword_germany_id_card" />
          </Pattern>
          <Pattern confidenceLevel="65">
           <IdMatch idRef="Func_german_id_card_with_check" />
          </Pattern>
        </Version>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- تحديد
- تعريف
- identifizierungsnummer
- بطاقة هوية
- رقم الهوية
- id-nummer
- المعرف الشخصي
- personalausweis
- رقم معرف persönliche
- persönliche identifikationsnummer
- persönliche-id-nummer