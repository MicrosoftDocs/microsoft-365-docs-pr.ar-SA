---
title: تعريف كيان رقم توجيه ABA
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
description: تعريف كيان نوع المعلومات الحساسة لرقم توجيه ABA.
ms.openlocfilehash: 5efc835b5d5dced7fbfe9a0b1ce7c59b89b60ac0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944453"
---
# <a name="aba-routing-number"></a>رقم توجيه ABA

## <a name="format"></a>تنسيق

تسعة أرقام قد تكون في نقش منسق أو غير منسق

## <a name="pattern"></a>نمط

- رقمان في النطاقات 00-12 أو 21-32 أو 61-72 أو 80
- رقمين
- واصلة اختيارية
- أربعة أرقام
- واصلة اختيارية
- رقم

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع النهج بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، في حدود 300 حرف:

- تبحث الدالة Func_aba_routing عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_ABA_Routing.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة Func_aba_routing عن المحتوى الذي يتطابق مع النمط.

```xml
    <!-- ABA Routing Number -->
    <Entity id="cb353f78-2b72-4c3c-8827-92ebe4f69fdf" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_aba_routing" />
        <Match idRef="Keyword_ABA_Routing" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_aba_routing" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- رقم aba
- ابا #
- ابا
- شريط شريطي #
- abaroutingnumber
- americanbankassociationrouting #
- رقم الأرقام في americanbankassociationrouting
- توجيه بنكي #
- رقم الجدولة البنكية
- التوجيه #
- لا يتم التوجيه
- رقم التوجيه
- توجيه رقم النقل
- التوجيه #
- RTN
