---
title: تعريف كيان رقم الصحة في نيوزيلندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الصحة في نيوزيلندا.
ms.openlocfilehash: 62a7b181626d36930da36451ccd109ecc6d04812
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944683"
---
# <a name="new-zealand-ministry-of-health-number"></a>وزارة الصحة في نيوزيلندا

## <a name="format"></a>تنسيق

ثلاثة أحرف وأربعة أرقام

## <a name="pattern"></a>نمط

- ثلاثة أحرف (غير حساسة لحالة الأحرف) باستثناء 'I' و'O'
- أربعة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_new_zealand_ministry_of_health_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_nz_terms` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_new_zealand_ministry_of_health_number` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- New Zealand Health Number -->
    <Entity id="2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
          <Match idRef="Keyword_nz_terms" />
      </Pattern>
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
       </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- نيوزيلندا
- الفهرس الصحي الوطني
- NHI #
- الفهرس الصحي الوطني #