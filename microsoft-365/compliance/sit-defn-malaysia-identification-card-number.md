---
title: تعريف كيان رقم بطاقة تعريف ماليزيا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة تعريف ماليزيا.
ms.openlocfilehash: ed233a9aa91c1c178644c4468271ee6839c55268
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944548"
---
# <a name="malaysia-identification-card-number"></a>رقم بطاقة تعريف ماليزيا

## <a name="format"></a>تنسيق

12 رقما تحتوي على واصلات اختيارية

## <a name="pattern"></a>نمط

12 رقما:

- ستة أرقام بالتنسيق YYMMDD، وهي تاريخ الميلاد
- شرطة (اختياري)
- رمز مكان الميلاد المكون من حرفين
- شرطة (اختياري)
- ثلاثة أرقام عشوائية
- رمز الجنس المكون من رقم واحد

## <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_malaysia_id_card_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_malaysia_id_card_number` .

```xml
<!-- Malaysia ID Card Number -->
</Entity>
      <Entity id="7f0e921c-9677-435b-aba2-bb8f1013c749" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_malaysia_id_card_number" />
            <Match idRef="Keyword_malaysia_id_card_number" />
        </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- بطاقة تطبيق رقمية
- i/c
- i/c no
- Ic
- ic no
- بطاقة المعرف
- بطاقة التعريف
- بطاقة هوية
- k/p
- k/p no
- kad akiri diri
- kad aplikasi digital
- kad pengenalan malaysia
- Kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- بطاقة هوية ماليزيا
- بطاقة هوية
- nric
- بطاقة التعريف الشخصية