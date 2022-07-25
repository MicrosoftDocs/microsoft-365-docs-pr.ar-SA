---
title: تعريف كيان بطاقة المعرف الوطنية (CNI) في فرنسا
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
description: تعريف كيان نوع المعلومات الحساسة لبطاقة المعرف الوطنية (CNI) في فرنسا.
ms.openlocfilehash: 35a6481e657d20a83ed1b80a6d06ad8ebf1c9cdf
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988480"
---
# <a name="france-national-id-card-cni"></a>بطاقة المعرف الوطنية الفرنسية (CNI)

## <a name="format"></a>تنسيق

12 رقما

## <a name="pattern"></a>نمط

12 رقما

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_france_cni` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_france_eu_national_id_card` .

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- رقم البطاقة
- carte nationale d'identité
- carte nationale d'idenite no
- cni #
- cni
- compte bancaire
- رقم التعريف الوطني
- الهوية الوطنية
- nationalidno #
- numéro d'assurance maladie
- numéro de carte vitale