---
title: تعريف كيان رقم التأمين الاجتماعي (SIN) في اليابان
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التأمين الاجتماعي (SIN) في اليابان.
ms.openlocfilehash: 27f812ec99c1ef7c2e4d3a913c039cab4fda65e7
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944432"
---
# <a name="japan-social-insurance-number-sin"></a>رقم التأمين الاجتماعي الياباني (SIN)

## <a name="format"></a>تنسيق

من 7 إلى 12 رقما

## <a name="pattern"></a>نمط

من 7 إلى 12 رقما:

- أربعة أرقام
- واصلة (اختيارية)
- ستة أرقام OR
- من 7 إلى 12 رقما متتاليا

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- محتوى الدالة `Func_jp_sin finds` الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_jp_sin` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_jp_sin_pre_1997` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_jp_sin` .

```xml
<!-- Japan Social Insurance Number -->
<Entity id="c840e719-0896-45bb-84fd-1ed5c95e45ff" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_jp_sin" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_sin_pre_1997" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- رقم التأمين الاجتماعي.
- رقم التأمين الاجتماعي
- رقم التأمين الاجتماعي
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 社会保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号