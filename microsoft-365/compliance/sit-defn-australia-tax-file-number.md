---
title: تعريف كيان رقم الملف الضريبي في أستراليا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضريبة في أستراليا.
ms.openlocfilehash: 155bdbd2142d0c6c097907b0ab651ff74cfac46d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944631"
---
# <a name="australia-tax-file-number"></a>رقم ملف الضريبة في أستراليا

## <a name="format"></a>تنسيق

من ثمانية إلى تسعة أرقام

## <a name="pattern"></a>نمط

عادة ما يتم عرض الأرقام من ثمانية إلى تسعة مع مسافات كما يلي:

- ثلاثة أرقام
- مساحة اختيارية
- ثلاثة أرقام
- مساحة اختيارية
- رقمان إلى ثلاثة أرقام حيث الرقم الأخير هو خانة اختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_australian_tax_file_number عن المحتوى الذي يتطابق مع النمط.
- لم يتم العثور على كلمة أساسية من Keyword_Australia_Tax_File_Number أو Keyword_number_exclusions.
- يمر المجموع الاختباري.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- رقم العمل الأسترالي
- معدل الضريبة الهامشية
- الرعاية الصحية الأساسية
- رقم قائمة المشاريع
- المخضرمين في الخدمة
- خصم الضريبة
- الإرجاع الضريبي الفردي
- رقم ملف الضريبة
- tfn
