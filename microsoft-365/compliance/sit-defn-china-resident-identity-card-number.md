---
title: تعريف كيان رقم بطاقة هوية مقيمة في الصين (PRC)
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة الهوية المقيمة في الصين .
ms.openlocfilehash: 9ab0f1af6de2c8ffdcb835824e1559ab1a574718
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944332"
---
# <a name="china-resident-identity-card-prc-number"></a>رقم بطاقة هوية مقيمة في الصين (PRC)

## <a name="format"></a>تنسيق

18 رقما

## <a name="pattern"></a>نمط

18 رقما:

- ستة أرقام هي رمز عنوان
- ثمانية أرقام في نموذج YYYYMMDD، وهي تاريخ الميلاد
- ثلاثة أرقام هي رمز طلب
- رقم واحد هو خانة اختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_china_resident_id` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_china_resident_id` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_china_resident_id` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- China Resident Identity Card (PRC) Number -->
<Entity id="c92daa86-2d16-4871-901f-816b3f554fc1" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_china_resident_id"/>
     <Match idRef="Keyword_china_resident_id"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_china_resident_id"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

## <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- بطاقة هوية مقيمة
- PRC
- بطاقة التعريف الوطنية
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定