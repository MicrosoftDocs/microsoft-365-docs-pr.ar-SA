---
title: تعريف كيان بطاقة هوية المقترعين في الهند
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
description: تعريف كيان نوع المعلومات الحساسة لبطاقة هوية المقتراع الهندية.
ms.openlocfilehash: 4556824999f44f6407e996fbca7c82e79fe2cafc
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944399"
---
# <a name="india-voter-id-card"></a>بطاقة هوية المقترعين في الهند

## <a name="format"></a>تنسيق

نقش أبجدي رقمي من 10 أحرف

## <a name="pattern"></a>نمط

10 أحرف أو أرقام:

- ثلاثة أحرف
- سبعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_india_voter_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_india_voter_id_card` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_india_voter_id_card` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- India Voter Id Card  -->
        <Entity id="646d643f-5228-4408-acc8-f2e81a6df897" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
           <Pattern confidenceLevel="75">
             <IdMatch idRef="Regex_india_voter_id_card" />
             <Match idRef="Keyword_india_voter_id_card" />
            </Pattern>
           <Pattern confidenceLevel="65">
              <IdMatch idRef="Regex_india_voter_id_card" />
            </Pattern>
        </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- الناخبين
- معرف مصوت
- بطاقة التصويت
- بطاقة المصوت
- بطاقة هوية صورة
- ملحمه
- ECI
- فاصلة الانتخابات