---
title: تعريف كيان رقم بطاقة المواطنين البرتغاليين
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة المواطنين البرتغاليين.
ms.openlocfilehash: 95aa6f824de748dfc513ef5d509b6ae5e1c58119
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988317"
---
# <a name="portugal-citizen-card-number"></a>رقم بطاقة المواطنين البرتغاليين

## <a name="format"></a>تنسيق

ثمانية أرقام

## <a name="pattern"></a>نمط

ثمانية أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_portugal_citizen_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_portugal_citizen_card` .

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- ʖ>>>>>>
- cartão de cidadão
- بطاقة مواطن
- رقم المستند
- documento de identificação
- رقم المعرف
- لا يوجد تعريف
- رقم التعريف
- رقم بطاقة الهوية
- رقم بطاقة الهوية
- بطاقة المعرف الوطنية
- Nic
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- رقم bi في البرتغال