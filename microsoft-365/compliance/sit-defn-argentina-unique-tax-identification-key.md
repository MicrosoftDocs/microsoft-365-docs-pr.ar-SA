---
title: تعريف كيان مفتاح التعريف الضريبي الفريد في الأرجنتين (CUIT/CUIL)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح التعريف الضريبي الفريد في الأرجنتين (CUIT/CUIL).
ms.openlocfilehash: d38cb0a972add240087c816399abf30d3d9ef670
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944577"
---
# <a name="argentina-unique-tax-identification-key-cuitcuil"></a>مفتاح التعريف الضريبي الفريد في الأرجنتين (CUIT/CUIL)

## <a name="format"></a>تنسيق

11 رقما بشرطة

## <a name="pattern"></a>نمط

11 رقما بشرطة:

- رقمان في 20 أو 23 أو 24 أو 27 أو 30 أو 33 أو 34
- واصلة (-)
- ثمانية أرقام
- واصلة (-)
- خانة اختيار واحدة

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_Argentina_Unique_Tax_Key` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_Argentina_Unique_Tax_Key` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_Argentina_Unique_Tax_Key` عن المحتوى الذي يطابق النمط.

```xml
    <!-- Argentina Unique Tax Identification Key (CUIT/CUIL) -->
      <Entity id="98da3da1-9199-4571-b7c4-b6522980b507" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
          <Match idRef="Keyword_Argentina_Unique_Tax_Key" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- تعليمة برمجية فريدة لتحديد هوية العمالة
- Clave Única de Identificación Tributaria
- رمز تعريف تعريف فريد للعمليات
- CUIL
- مفتاح تعريف الضريبة الفريد
- مفتاح تعريف فريد للعمليات
- مفتاح فريد لتحديد هوية العمالة
- رمز تعريف العمل الفريد
- رمز فريد لتعريف العمل
- مفتاح تعريف العمل الفريد
- مفتاح فريد لتعريف العمل
- رمز فريد لتعريف الضريبة
- مفتاح فريد لتعريف الضريبة
- رمز تعريف العمل الفريد
- رمز فريد لتعريف العمل
- مفتاح تعريف العمل الفريد
- مفتاح فريد لتعريف العمل
- معرف الضريبة
- معرف الضريبة #
- معرف الضريبة
- رقم سيارة أجرة
- رقم الضريبة
- رقم الضريبة
- الضريبيه #
- الضريبيه #
- معرف
- رقم/&
- لا
- دافعي الضرائب #
- دافعي الضرائب #
- الهوية الضريبية
- التعريف الضريبي
- Número de Identificación Fiscal
- número de contribuyente