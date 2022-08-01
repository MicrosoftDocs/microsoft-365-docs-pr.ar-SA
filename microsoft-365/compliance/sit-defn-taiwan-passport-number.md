---
title: تعريف كيان رقم جواز سفر تايوان
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز سفر تايوان.
ms.openlocfilehash: b899fbe560ea6cba19c66bafea819c769ece2634
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944537"
---
# <a name="taiwan-passport-number"></a>رقم جواز سفر تايوان

## <a name="format"></a>تنسيق

- رقم جواز السفر البيومتري: تسعة أرقام
- رقم جواز سفر غير قياسي: تسعة أرقام

## <a name="pattern"></a>نمط

رقم جواز السفر البيومتري:

- الحرف "3"
- ثمانية أرقام

رقم جواز السفر غير البيومتري:

- تسعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_taiwan_passport` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_taiwan_passport` .

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- رقم جواز سفر ROC
- رقم جواز السفر
- لا يوجد جواز سفر
- رقم جواز السفر
- جواز السفر #
- 护照
- 中華民國護照
- Zhînghuá Mínguó hùzhào