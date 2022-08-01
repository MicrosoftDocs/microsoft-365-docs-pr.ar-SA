---
title: تعريف كيان رقم الكيان القانوني (CNPJ) في البرازيل
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الكيان القانوني البرازيلي (CNPJ).
ms.openlocfilehash: a8cf09eb283cea08e72a5858e7bfd4752486a01e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944646"
---
# <a name="brazil-legal-entity-number-cnpj"></a>رقم الكيان القانوني البرازيلي (CNPJ)

## <a name="format"></a>تنسيق

14 رقما تتضمن رقم تسجيل ورقم فرع وخانات اختيار، بالإضافة إلى المحددات

## <a name="pattern"></a>نمط

14 رقما، بالإضافة إلى المحددات:

- رقمين
- فترة زمنية
- ثلاثة أرقام
- فترة زمنية
- ثلاثة أرقام (أول ثمانية أرقام هي رقم التسجيل)
- شرطة مائلة للأمام
- رقم الفرع المكون من أربعة أرقام
- واصلة
- رقمان يتم التحقق من رقمين

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_brazil_cnpj` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_brazil_cnpj` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_brazil_cnpj` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Brazil Legal Entity Number (CNPJ) -->
<Entity id="9b58b5cd-5e90-4df6-b34f-1ebcc88ceae4" recommendedConfidence="85" patternsProximity="300">
   <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cnpj"/>
     <Match idRef="Keyword_brazil_cnpj"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cnpj"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- السجل الوطني للكيانات القانونية
- سجل مهى
- كيان قانوني
- الكيانات القانونية
- حالة التسجيل
- Business
- الشركه
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- CadastroGeral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação cadascad
- Inscrição
- Empresa