---
title: تعريف كيان رقم تعريف النرويج
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
description: تعريف كيان نوع المعلومات الحساسة لرقم تعريف النرويج.
ms.openlocfilehash: 9edce24b1fef475ce30b50d3703214d4388a1338
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944680"
---
# <a name="norway-identification-number"></a>رقم تعريف النرويج

## <a name="format"></a>تنسيق

11 رقما

## <a name="pattern"></a>نمط

11 رقما:

- ستة أرقام بتنسيق DD ولاي، وهي تاريخ الميلاد
- رقم فردي مكون من ثلاثة أرقام
- خانتا اختيار رقميتان

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_norway_id_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_norway_id_number` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_norway_id_number` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Norway Identification Number -->
<Entity id="d4c8a798-e9f2-4bd3-9652-500d24080fc3" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_norway_id_number"/>
     <Match idRef="Keyword_norway_id_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_norway_id_number"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- رقم التعريف الشخصي
- رقم المعرف النرويجي
- رقم المعرف
- تحديد
- رقم الشخص
- Fødselsnummer