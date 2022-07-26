---
title: تعريف كيان التعليمات البرمجية SWIFT
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
description: تعريف كيان نوع المعلومات الحساسة للتعليمات البرمجية SWIFT.
ms.openlocfilehash: b1bbadf8f2b56218a90eec1cfd2fac7d550efe0e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944230"
---
# <a name="swift-code"></a>رمز SWIFT

## <a name="format"></a>تنسيق

أربعة أحرف متبوعة ب 5-31 حرفا أو رقما

## <a name="pattern"></a>نمط

أربعة أحرف متبوعة ب 5-31 حرفا أو رقما:

- رمز بنكي مكون من أربعة أحرف (غير حساس لحالة الأحرف)
- مساحة اختيارية
- 4-28 حرفا أو رقما (رقم الحساب البنكي الأساسي (BBAN))
- مساحة اختيارية
- حرف أو ثلاثة أحرف (باقي BBAN)

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_swift` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_swift` .

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_swift"></a>Keyword_swift

- المنظمة الدولية لتوحيد المقاييس 9362
- iso 9362
- iso9362
- سويفت #
- swiftcode
- رقم سويفت
- رقم swiftrouting
- رمز swift
- رقم سريع #
- رقم التوجيه السريع
- رقم bic
- تعليمة bic البرمجية
- Bic #
- Bic #
- رمز معرف البنك
- المنظمة الدولية للتطبيع 9362
- سريع #
- رمز SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- \# BIC
- code identificateur de deque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT 番号
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード