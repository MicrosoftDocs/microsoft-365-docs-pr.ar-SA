---
title: تعريف كيان رمز تسجيل المحتوى الفريد (CURP) في المكسيك
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
description: تعريف كيان نوع المعلومات الحساسة لرمز تسجيل المحتوى الفريد (CURP) في المكسيك.
ms.openlocfilehash: 806f7e9b0d2dd797b17ad848d160c6f74c04e1e2
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988348"
---
# <a name="mexico-unique-population-registry-code-curp"></a>رمز سجل المحتوى الفريد في المكسيك (CURP)

## <a name="format"></a>تنسيق

نقش أبجدي رقمي من 18 حرفا

## <a name="pattern"></a>نمط

- أربعة أحرف (غير حساس لحالة الأحرف)
- ستة أرقام تشير إلى تاريخ صالح
- حرف - H/h أو M/m
- حرفان يشيران إلى تعليمة برمجية صحيحة لحالة المكسيك
- ثلاثة أحرف
- حرف واحد أو رقم واحد
- رقم واحد

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_mexico_population_registry_code` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_mexico_population_registry_code` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_mexico_population_registry_code` عن المحتوى الذي يطابق النمط.

```xml
    <!-- Mexico Unique Population Registry Code (CURP) -->
      <Entity id="e905ad4d-5a74-406d-bf36-b1efca798af4" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_mexico_population_registry_code" />
          <Match idRef="Keyword_mexico_population_registry_code" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_mexico_population_registry_code" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- رمز تسجيل المحتوى الفريد
- رمز محتوى فريد
- CURP
- المعرف الشخصي
- معرف فريد
- معرف شخصي
- رقم شخصي
- مفتاح فريد
- رقم فريد
- clave única
- احفظ unica
- clave personal Identidad
- Identidad Clave الشخصي
- ClaveÚnica
- claveunica
- clavepersonalIdentidad