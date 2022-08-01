---
title: تعريف كيان رقم GST في الهند
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
description: تعريف كيان نوع المعلومات الحساسة لرقم GST في الهند.
ms.openlocfilehash: 19d51294b8ff53b53bceba1a047976802359f09e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944304"
---
# <a name="india-gst-number"></a>رقم GST في الهند

## <a name="format"></a>تنسيق

نقش أبجدي رقمي من 15 حرفا

## <a name="pattern"></a>نمط

15 حرفا أو رقما:

- رقمان يمثلان رمز حالة صالح
- مسافة اختيارية أو شرطة اختيارية
- عشرة أحرف تمثل رقم الحساب الدائم (PAN)
- حرف واحد أو رقم واحد
- مسافة اختيارية أو شرطة اختيارية
- حرف واحد 'z' أو 'Z'
- مسافة اختيارية أو شرطة اختيارية
- خانة اختيار واحدة

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_india_gst_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_india_gst_number` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_india_gst_number` عن المحتوى الذي يطابق النمط.

```xml
    <!-- India GST number  -->
      <Entity id="9f5a721c-2fd2-446a-a27e-0c02fbe4630c" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_india_gst_number" />
          <Match idRef="Keyword_india_gst_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_india_gst_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- Gst
- gstin
- ضريبة السلع والخدمات
- ضريبة السلع والخدمات