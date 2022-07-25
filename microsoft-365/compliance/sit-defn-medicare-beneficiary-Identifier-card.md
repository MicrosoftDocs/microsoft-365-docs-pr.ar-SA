---
title: تعريف كيان بطاقة Medicare
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
description: Medicare Beneficiary Identifier (MBI) card sensitive information type entity definition.
ms.openlocfilehash: 601c34adcb0f9b19ab2c23a3df7d1c574cdd5031
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988349"
---
# <a name="medicare-beneficiary-identifier-mbi-card"></a>بطاقة معرف Medicare للمستفيد (MBI)

## <a name="format"></a>تنسيق

نقش أبجدي رقمي من 11 حرفا

## <a name="pattern"></a>نمط

- رقم واحد بين 1 إلى 9
- حرف واحد باستثناء S وL وO وI وB وZ
- رقم واحد أو حرف واحد باستثناء S وL وO وI وB وZ
- رقم واحد
- واصلة اختيارية
- حرف واحد باستثناء S وL وO وI وB وZ
- رقم واحد أو حرف واحد باستثناء S وL وO وI وB وZ
- رقم واحد
- واصلة اختيارية
- حرفان باستثناء S وL وO وI وB وZ
- رقمين

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_mbi_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_mbi_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_mbi_card` العادي عن المحتوى الذي يطابق النمط.

```xml
    <!-- Medicare Beneficiary Identifier (MBI) card -->
      <Entity id="f753a286-f5cc-47e6-a592-4be25fd02591" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_mbi_card" />
          <Match idRef="Keyword_mbi_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_mbi_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- mbi
- mbi #
- الرعاية الصحية غير المستفيدة #
- معرف medicare للمستفيد
- medicare غير مستحق
- رقم الرعاية المستفيدة من medicare
- الرعاية الصحية غير المستفيدة #