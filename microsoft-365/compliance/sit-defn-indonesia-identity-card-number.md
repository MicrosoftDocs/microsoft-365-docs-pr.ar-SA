---
title: تعريف كيان رقم بطاقة هوية إندونيسيا (KTP)
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة هوية إندونيسيا (KTP).
ms.openlocfilehash: d70e6ca902c6246e6faa67a91c5b52ae65e4fd47
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944246"
---
# <a name="indonesia-identity-card-ktp-number"></a>رقم بطاقة هوية إندونيسيا (KTP)

## <a name="format"></a>تنسيق

16 رقما تحتوي على فترات اختيارية

## <a name="pattern"></a>نمط

16 رقما:

- رمز المقاطعة المكون من رقمين
- فترة زمنية (اختيارية)
- رمز المدينة أو رمز المدينة المكون من رقمين
- تعليمة برمجية فرعية مكونة من رقمين
- فترة زمنية (اختيارية)
- ستة أرقام بتنسيق DD ولاي، وهي تاريخ الميلاد
- فترة زمنية (اختيارية)
- أربعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_indonesia_id_card` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_indonesia_id_card` .

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- كارتو تاندا بيندوك
- Nomor Induk Kependudukan