---
title: تعريف وحدة المعرِّف الوطني بالمملكة العربية السعودية
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
description: تعريف وحدة نوع المعلومات الحساسة للمعرَّف الوطني بالمملكة العربية السعودية.
ms.openlocfilehash: c5bfa2560959caa0aa6115f4e25e8d09c8dffb5e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944417"
---
# <a name="saudi-arabia-national-id"></a>بطاقة الهوية الوطنية في المملكة العربية السعودية

## <a name="format"></a>التنسيق

10 أرقام

## <a name="pattern"></a>نمط

10 أرقام متتالية

## <a name="checksum"></a>مجموع اختباري

لا

## <a name="definition"></a>التعريف

يتمتع نهج DLP بثقة متوسطة، حيث إنه اكتشف هذا النوع من المعلومات الحساسة، مع وجود مقربة من 300 حرف:

- يبحث التعبير العادي `Regex_saudi_arabia_national_id` عن محتوى يتطابق مع النمط.
- تم العثور على كلمة أساسية من `Keyword_saudi_arabia_national_id`.

```xml
<!-- Saudi Arabia National ID -->
<Entity id="8c5a0ba8-404a-41a3-8871-746aa21ee6c0" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_saudi_arabia_national_id" />
        <Any minMatches="1">
          <Match idRef="Keyword_saudi_arabia_national_id" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>كلمات أساسية

### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- بطاقة التعريف
- رقم بطاقة المًصدِر
- رقم المعرّف
- الوطنية الهوية بطاقة رقم