---
title: تعريف كيان رقم جواز سفر كندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم جواز سفر كندا.
ms.openlocfilehash: 5a645a71bd9cdb27727fd493bcd09ceca7340c22
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988259"
---
# <a name="canada-passport-number"></a>رقم جواز سفر كندا

## <a name="format"></a>تنسيق

حرفان من الأحرف الكبيرة متبوعا بستة أرقام

## <a name="pattern"></a>نمط

حرفان من الأحرف الكبيرة متبوعا بستة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_canada_passport_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keyword_canada_passport_number` أو `Keyword_passport` تم العثور عليها.

```xml
<!-- Canada Passport Number -->
<Entity id="14d0db8b-498a-43ed-9fca-f6097ae687eb" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_passport_number" />
          <Match idRef="Keyword_passport" />
        </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- المواطنين الكنديين
- جواز سفر كندا
- طلب جواز سفر
- صور جواز السفر
- مترجم معتمد
- المواطنين الكنديين
- أوقات المعالجة
- تطبيق التجديد

### <a name="keyword_passport"></a>Keyword_passport

- رقم جواز السفر
- رقم جواز السفر
- جواز السفر #
- جواز السفر #
- معرف جواز السفر
- Passportno
- رقم جواز السفر
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n °
- Passeport Non
- منفذ المرور #
- منفذ المرور #
- PasseportNon
- Passeportn °