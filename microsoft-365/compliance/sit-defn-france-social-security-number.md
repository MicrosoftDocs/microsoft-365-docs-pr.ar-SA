---
title: تعريف كيان رقم الضمان الاجتماعي في فرنسا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضمان الاجتماعي (INSEE) في فرنسا.
ms.openlocfilehash: 3378b452e8136e5ca62fe49932ba23949eb6a85d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988478"
---
# <a name="france-social-security-number-insee"></a>رقم الضمان الاجتماعي (INSEE) في فرنسا

## <a name="format"></a>تنسيق

15 رقما

## <a name="pattern"></a>نمط

يجب أن تتطابق مع أحد النمطين:

- 13 رقما متبوعا بمسافة متبوعة برقمين

  او

- 15 رقما متتاليا

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_french_insee` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_fr_insee` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_french_insee` أو `Func_fr_insee` البحث عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- France INSEE -->
    <Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Keyword_fr_insee" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- تعليمة برمجية sécu
- d'identité nationale
- insee
- fssn #
- le numéro d'identification nationale
- le code de la sécurité sociale
- المعرف الوطني
- التعريف الوطني
- لا يوجد هوية
- لا. هوية d'identité
- ضمان numéro d'assurance
- numéro d'identité
- numero d'identite
- numéro de sécu
- numéro de sécurité sociale
- لا توجد هوية
- لا. هوية d'd
- Ssn
- Ssn #
- sécurité sociale
- securité sociale
- securite sociale
- رقم الأمان الاجتماعي
- رقم الضمان الاجتماعي
- رمز الضمان الاجتماعي
- رقم التأمين الاجتماعي