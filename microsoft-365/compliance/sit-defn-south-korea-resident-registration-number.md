---
title: تعريف كيان رقم التسجيل المقيم في كوريا الجنوبية
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التسجيل المقيم في كوريا الجنوبية.
ms.openlocfilehash: 94de2ebb31e8bd7a0d9c175e318e166da691bbca
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944235"
---
# <a name="south-korea-resident-registration-number"></a>رقم التسجيل المقيم في كوريا الجنوبية

## <a name="format"></a>تنسيق

13 رقما تحتوي على واصلة

## <a name="pattern"></a>نمط

13 رقما:

- ستة أرقام بالتنسيق YYMMDD، وهي تاريخ الميلاد
- واصلة
- رقم واحد يحدده القرن والجنس
- رمز منطقة الميلاد المكون من أربعة أرقام
- رقم واحد يستخدم للتمييز بين الأشخاص الذين تتطابق الأرقام السابقة معهم
- خانة اختيار رقمية.

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_south_korea_resident_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_south_korea_resident_number` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_south_korea_resident_number` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- بطاقة المعرف الوطني
- رقم تسجيل المواطنين
- Jumin deungnok beonho
- RRN
- 주민등록번호