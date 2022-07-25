---
title: تعريف كيان رقم CPF في البرازيل
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
description: تعريف كيان نوع المعلومات الحساسة لرقم CPF في البرازيل.
ms.openlocfilehash: b8164d44f20237b5eb74d45369f3bffbe1dc07e3
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988268"
---
# <a name="brazil-cpf-number"></a>رقم CPF في البرازيل

## <a name="format"></a>تنسيق

11 رقما تتضمن خانة اختيار ويمكن تنسيقها أو عدم تنسيقها

## <a name="pattern"></a>نمط

تنسيق:

- ثلاثة أرقام
- فترة زمنية
- ثلاثة أرقام
- فترة زمنية
- ثلاثة أرقام
- واصلة
- رقمان يتم التحقق من رقمين

منسق:

- 11 رقما يتم فيها التحقق من الرقمين الأخيرين

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_brazil_cpf` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_brazil_cpf` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_brazil_cpf` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Brazil CPF Number -->
<Entity id="78e09124-f2c3-4656-b32a-c1a132cd2711" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cpf"/>
     <Match idRef="Keyword_brazil_cpf"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cpf"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- الشراكه
- تحديد
- التسجيل
- الايرادات
- Cadastro de Pessoas Físicas
- منتحل إلى
- Identificação
- Inscrição
- Receita