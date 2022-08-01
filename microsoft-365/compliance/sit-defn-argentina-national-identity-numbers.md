---
title: تعريف كيان رقم الهوية الوطنية للارجنتين (DNI)
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
description: تعريف كيان نوع المعلومات الحساسة للهوية الوطنية الأرجنتينية (DNI).
ms.openlocfilehash: f7a74b4f92cc23acf4c71320c06455fffcff378f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944584"
---
# <a name="argentina-national-identity-dni-number"></a>رقم الهوية الوطنية للارجنتين (DNI)

## <a name="format"></a>تنسيق

ثمانية أرقام بفترات زمنية أو بدونها

## <a name="pattern"></a>نمط

ثمانية أرقام:

- رقمين
- فترة اختيارية
- ثلاثة أرقام
- فترة اختيارية
- ثلاثة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_argentina_national_id عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_argentina_national_id.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- رقم الهوية الوطنية للارجنتين
- cedula
- cédula
- dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- rnp