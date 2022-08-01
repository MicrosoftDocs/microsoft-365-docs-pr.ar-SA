---
title: تعريف كيان التصنيف الدولي الأمراض (ICD-10-CM)
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
description: تعريف كيان نوع المعلومات الحساسة للتصنيف الدولي الأمراض (ICD-10-CM).
ms.openlocfilehash: 414ad224f32a6eecb1fe244bdefde12afdc4b006
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944398"
---
# <a name="international-classification-of-diseases-icd-10-cm"></a>التصنيف الدولي الأمراض (ICD-10-CM)

## <a name="format"></a>تنسيق

القاموس

## <a name="pattern"></a>نمط

الكلمه الاساسيه

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تم العثور على كلمة أساسية منها `Dictionary_icd_10_updated` .
- تم العثور على كلمة أساسية منها `Dictionary_icd_10_codes` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تم العثور على كلمة أساسية منها `Dictionary_icd_10_ updated` .

```xml
      <!-- ICD-10 CM -->
      <Entity id="3356946c-6bb7-449b-b253-6ffa419c0ce7" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_10_updated" />
          <Match idRef="Dictionary_icd_10_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_10_updated" />
        </Pattern>

```

## <a name="keywords"></a>الكلمات الرئيسيه

أي مصطلح من `Dictionary_icd_10_updated` قاموس الكلمات الأساسية، والذي يستند إلى [التصنيف الدولي للمرضى، المراجعة العاشرة، التعديل الإكلينيكي (ICD-10-CM).](https://icd10cmtool.cdc.gov/) يبحث هذا النوع عن المصطلح فقط، وليس رموز التأمين.

أي مصطلح من `Dictionary_icd_10_codes` قاموس الكلمات الأساسية، والذي يستند إلى [التصنيف الدولي للمرضى، المراجعة العاشرة، التعديل الإكلينيكي (ICD-10-CM).](https://icd10cmtool.cdc.gov/) يبحث هذا النوع عن رموز التأمين فقط، وليس الوصف.