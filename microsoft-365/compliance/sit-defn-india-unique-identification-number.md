---
title: تعريف كيان رقم التعريف الفريد (Aadhaar) في الهند
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الفريد في الهند (Aadhaar).
ms.openlocfilehash: 37f0182050e4602ebeda9d9e5376df18b7971571
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944571"
---
# <a name="india-unique-identification-aadhaar-number"></a>رقم التعريف الفريد (Aadhaar) في الهند

## <a name="format"></a>تنسيق

12 رقما تحتوي على مسافات أو شرط اختيارية

## <a name="pattern"></a>نمط

12 رقما:

- رقم ليس 0 أو 1
- ثلاثة أرقام
- مسافة اختيارية أو شرطة اختيارية
- أربعة أرقام
- مسافة اختيارية أو شرطة اختيارية
- الرقم الأخير، وهو خانة الاختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_india_aadhaar` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_india_aadhar` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_india_aadhaar` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- India Unique Identification (Aadhaar) number -->
<Entity id="1ca46b29-76f5-4f46-9383-cfa15e91048f" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_india_aadhaar"/>
     <Match idRef="Keyword_india_aadhar"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_india_aadhaar"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar

- aadhaar
- aadhar
- aadhar #
- Uid
- आधार
- uidai