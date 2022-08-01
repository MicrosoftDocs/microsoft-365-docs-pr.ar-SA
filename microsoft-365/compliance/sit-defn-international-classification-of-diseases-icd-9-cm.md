---
title: تعريف كيان التصنيف الدولي الأمراض (ICD-9-CM)
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
description: تعريف كيان نوع المعلومات الحساسة للتصنيف الدولي الأمراض (ICD-9-CM).
ms.openlocfilehash: 1aceb3864638f2fa8658d4c88dc47812910dd588
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944530"
---
# <a name="international-classification-of-diseases-icd-9-cm"></a>التصنيف الدولي الأمراض (ICD-9-CM)

## <a name="format"></a>تنسيق

القاموس

## <a name="pattern"></a>نمط

الكلمه الاساسيه

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تم العثور على كلمة أساسية منها `Dictionary_icd_9_updated` .
- تم العثور على كلمة أساسية منها `Dictionary_icd_9_codes` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تم العثور على كلمة أساسية منها `Dictionary_icd_9_updated` .

```xml
    <Entity id="fa3f9c74-ee07-4c52-b5f2-085d6b2c0ec4" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_9_updated" />
          <Match idRef="Dictionary_icd_9_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_9_updated" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

أي مصطلح من `Dictionary_icd_9_updated` قاموس الكلمة الأساسية، الذي يستند إلى [التصنيف الدولي للمرضى، المراجعة التاسعة، التعديل الإكلينيكي (ICD-9-CM).](https://go.microsoft.com/fwlink/?linkid=852605) يبحث هذا النوع عن المصطلح فقط، وليس رموز التأمين.

أي مصطلح من `Dictionary_icd_9_codes` قاموس الكلمة الأساسية، الذي يستند إلى [التصنيف الدولي للمرضى، المراجعة التاسعة، التعديل الإكلينيكي (ICD-9-CM).](https://go.microsoft.com/fwlink/?linkid=852605) يبحث هذا النوع عن رموز التأمين فقط، وليس الوصف.