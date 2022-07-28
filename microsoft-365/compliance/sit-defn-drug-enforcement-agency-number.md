---
title: تعريف كيان رقم وكالة إنفاذ مكافحة الأدوية (DEA)
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
description: تعريف كيان نوع المعلومات الحساسة لرقم وكالة إنفاذ مكافحة الأدوية (DEA).
ms.openlocfilehash: 7b1ade056621f619d8be0293708dd51cfc2e85dd
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944316"
---
# <a name="drug-enforcement-agency-dea-number"></a>رقم وكالة إنفاذ مكافحة الأدوية (DEA)

## <a name="format"></a>تنسيق

حرفان متبوعا بسبعة أرقام

## <a name="pattern"></a>نمط

يجب أن يتضمن النمط كل ما يلي:

- حرف واحد (غير حساس لحالة الأحرف) من هذه المجموعة من الأحرف المحتملة: A/B/F/G/M/P/R، وهو رمز مسجل
- حرف واحد (غير حساس لحالة الأحرف)، وهو الحرف الأول من اسم عائلة المسجل أو رقمه '9'
- سبعة أرقام، آخرها رقم الاختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_dea_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keyword_dea_number`
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_dea_number` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
    <!-- DEA Number -->
    <Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_dea_number" />
      </Pattern>
      <Version minEngineVersion="15.20.1207.000" maxEngineVersion="15.20.3134.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
        </Pattern>
      </Version>
      <Version minEngineVersion="15.20.3135.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
          <Match idRef="Keyword_dea_number" />
        </Pattern>
      </Version>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_dea_number"></a>Keyword_dea_number

- Dea
- Dea #
- إدارة إنفاذ مكافحة الأدوية
- وكالة إنفاذ مكافحة الأدوية