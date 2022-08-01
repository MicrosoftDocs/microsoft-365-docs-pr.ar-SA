---
title: تعريف كيان رقم التعريف الموحد متعدد الأغراض في الفليبين
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الموحد متعدد الأغراض في الفليبين.
ms.openlocfilehash: d5e880ff8c021cdcee195077f419f3b7ab87ed36
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944676"
---
# <a name="philippines-unified-multi-purpose-identification-number"></a>رقم تعريف موحد متعدد الأغراض في الفليبين

## <a name="format"></a>تنسيق

12 رقما مفصولة بواصلات

## <a name="pattern"></a>نمط

12 رقما:

- أربعة أرقام
- واصلة
- سبعة أرقام
- واصلة
- رقم واحد

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_philippines_unified_id` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_philippines_id` .

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- معرف موحد متعدد الأغراض
- معرف UMID
- بطاقة الهوية
- معرف Pinag-isang Multi-Layunin