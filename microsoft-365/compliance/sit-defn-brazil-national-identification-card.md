---
title: تعريف كيان بطاقة التعريف الوطنية (RG) في البرازيل
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
description: تعريف كيان نوع المعلومات الحساسة لبطاقة التعريف الوطنية البرازيلية (RG).
ms.openlocfilehash: 7f4fe7a0eda911639c0c7650d4ac71f07dfe4f3a
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944266"
---
# <a name="brazil-national-identification-card-rg"></a>بطاقة تعريف البرازيل الوطنية (RG)

## <a name="format"></a>تنسيق

Registro غيرال (تنسيق قديم): تسعة أرقام

Registro de Identidade (RIC) (تنسيق جديد): 11 رقما

### <a name="pattern"></a>نمط

Registro غيرال (تنسيق قديم):

- رقمين
- فترة زمنية
- ثلاثة أرقام
- فترة زمنية
- ثلاثة أرقام
- واصلة
- رقم واحد هو خانة اختيار

Registro de Identidade (RIC) (تنسيق جديد):

- 10 أرقام
- واصلة
- رقم واحد هو خانة اختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_brazil_rg` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_brazil_rg` .
- يمر المجموع الاختباري.

```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- بطاقة هوية
- المعرف الوطني
- número de rregistro
- registro de Iidentidade
- registrogeral
- RG (هذه الكلمة الأساسية حساسة لحالة الأحرف)
- RIC (هذه الكلمة الأساسية حساسة لحالة الأحرف)