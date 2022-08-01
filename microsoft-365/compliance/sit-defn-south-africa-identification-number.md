---
title: تعريف كيان رقم تعريف جنوب أفريقيا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف في جنوب أفريقيا.
ms.openlocfilehash: 95fbf2baa8842f1654881d0435a0328b5593242a
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944477"
---
# <a name="south-africa-identification-number"></a>رقم تعريف جنوب أفريقيا

### <a name="format"></a>تنسيق

13 رقما قد تحتوي على مسافات

## <a name="pattern"></a>نمط

13 رقما:

- ستة أرقام بالتنسيق YYMMDD، وهي تاريخ الميلاد
- أربعة أرقام
- مؤشر المواطنين المؤلف من رقم واحد
- الرقم "8" أو "9"
- رقم واحد، وهو رقم المجموع الاختباري

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_south_africa_identification_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_south_africa_identification_number` .
- يمر المجموع الاختباري.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- بطاقة الهوية
- المعرّف
- تحديد