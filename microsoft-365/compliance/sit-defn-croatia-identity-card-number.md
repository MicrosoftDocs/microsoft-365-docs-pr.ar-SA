---
title: تعريف كيان رقم بطاقة هوية كرواتية
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة الهوية الكرواتية.
ms.openlocfilehash: c1a281af470557623e649f29c98594992848779d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944609"
---
# <a name="croatia-identity-card-number"></a>رقم بطاقة هوية كرواتية

يتم تضمين هذا الكيان في نوع المعلومات الحساسة لرقم التعريف الوطني للاتحاد الأوروبي. وهي متوفرة ككيان مستقل لنوع المعلومات الحساسة.

## <a name="format"></a>تنسيق

تسعة أرقام

## <a name="pattern"></a>نمط

تسعة أرقام متتالية

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_croatia_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_croatia_id_card` .

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj građana
- رقم مواطن رئيسي
- nacionalni identifikacijski broj
- رقم التعريف الوطني
- oib #
- oib
- osobna iskaznica
- معرف osobni
- osobni identifikacijski broj
- رقم التعريف الشخصي
- بوارياني بروج
- porezni identifikacijski broj
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #