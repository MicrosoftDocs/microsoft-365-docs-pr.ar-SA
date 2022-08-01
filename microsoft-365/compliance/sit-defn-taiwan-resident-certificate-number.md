---
title: تعريف كيان رقم الشهادة المقيمة في تايوان (ARC/TARC)
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
description: تعريف كيان نوع المعلومات الحساسة لشهادة مقيمة في تايوان (ARC/TARC).
ms.openlocfilehash: 26719642f5cc937909c7357302f660a5a8610189
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944462"
---
# <a name="taiwan-resident-certificate-arctarc-number"></a>رقم الشهادة المقيمة في تايوان (ARC/TARC)

## <a name="format"></a>تنسيق

10 أحرف ورقم

## <a name="pattern"></a>نمط

10 أحرف ورقم:

- حرفان (غير حساس لحالة الأحرف)
- ثمانية أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_taiwan_resident_certificate` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_taiwan_resident_certificate` .

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- شهادة مقيمة
- شهادة مقيمة
- شهادة مقيمة.
- بطاقة التعريف
- شهادة مقيمة في البلد
- قوس
- شهادة مقيمة في منطقة تايوان
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證