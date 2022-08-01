---
title: تعريف كيان بطاقة المعرف الوطنية في اليونان
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
description: تعريف كيان نوع المعلومات الحساسة لبطاقة المعرف الوطنية في اليونان.
ms.openlocfilehash: 731adcfee8c2464bd45e9324e8305a4cc813d7eb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944245"
---
# <a name="greece-national-id-card"></a>بطاقة المعرف الوطنية في اليونان

## <a name="format"></a>تنسيق

تركيبة من 7-8 أحرف وأرقام بالإضافة إلى شرطة

## <a name="pattern"></a>نمط

سبعة أحرف وأرقام (تنسيق قديم):

- حرف واحد (أي حرف من الأبجدية اليونانية)
- شرطة
- ستة أرقام

ثمانية أحرف وأرقام (تنسيق جديد):

- حرفان يقع حرفهما العلوي في كل من الحروف الأبجدية اليونانية واللاتينية (ABEZHIKMNOPTYX)
- شرطة
- ستة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_greece_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_greece_id_card` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Regex_greece_id_card` العادي عن المحتوى الذي يطابق النمط.

```xml
      <!-- Greece National ID Card -->
      <Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_id_card" />
          <Match idRef="Keyword_greece_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_greece_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- المعرف اليوناني
- المعرف الوطني اليوناني
- بطاقة المعرف الشخصي اليونانية
- معرف الشرطة اليونانية
- بطاقة هوية
- tautotita
- ταυτότητα
- ταυτότητας