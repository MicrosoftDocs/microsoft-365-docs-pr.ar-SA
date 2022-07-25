---
title: تعريف كيان رقم خدمة المواطنين الهولنديين (BSN)
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
description: تعريف كيان نوع المعلومات الحساسة لخدمة المواطنين الهولنديين (BSN).
ms.openlocfilehash: 4a5ca70bbbffe2d89b2dd05bd51e3dcda525e6a3
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988346"
---
# <a name="netherlands-citizens-service-bsn-number"></a>رقم خدمة المواطنين الهولنديين (BSN)

## <a name="format"></a>تنسيق

ثمانية أو تسعة أرقام تحتوي على مسافات اختيارية

## <a name="pattern"></a>نمط

ثمانية تسعة أرقام:

- ثلاثة أرقام
- مسافة (اختياري)
- ثلاثة أرقام
- مسافة (اختياري)
- رقمان مكونان من ثلاثة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- محتوى الدالة `Func_netherlands_bsn finds` الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_netherlands_bsn` .
- يمر المجموع الاختباري.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- Bsn #
- Bsn
- عدد الخوادم
- رقم خدمة المواطنين
- رقم الشخص
- رقم شخصي
- رمز رقمي شخصي
- رقم ذو صلة بالشخص
- رقم persoonlijk
- رمز رقمي persoonlijke
- persoonsgebonden
- عدد الأعصار
- nummer sociaal-fiscaal
- الرقم الاجتماعي -المالي
- صوفي
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- رقم تعريف فريد
- رقم هوية فريد
- uniqueidentityno #