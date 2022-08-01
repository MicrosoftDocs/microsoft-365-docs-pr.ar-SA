---
title: تعريف كيان رقم الحساب المصرفي الدولي (IBAN)
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الحساب المصرفي الدولي (IBAN).
ms.openlocfilehash: 739c0a1fd90da1da817f46019cd1023be8ab27a3
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944522"
---
# <a name="international-banking-account-number-iban"></a>رقم الحساب المصرفي الدولي (IBAN)

## <a name="format"></a>تنسيق

رمز البلد (حرفان) بالإضافة إلى خانات الاختيار (رقمين) بالإضافة إلى رقم bban (حتى 30 حرفا)

## <a name="pattern"></a>نمط

يجب أن يتضمن النمط كل ما يلي:

- رمز البلد المكون من حرفين
- رقمان للتحقق (متبوعا بمسافة اختيارية)
- 1-7 مجموعات مكونة من أربعة أحرف أو أرقام (يمكن فصلها بمسافات)
- أحرف أو أرقام من 1 إلى 3

يختلف تنسيق كل بلد قليلا. يغطي نوع المعلومات الحساسة ل IBAN هذه البلدان ال 60:

- الاعلان
- Ae
- al
- في
- Az
- بكالوريوس
- be
- bg
- الهرسك
- الفصل
- Cr
- قبرصي
- تشيكوسلوفاكيا
- de
- Dk
- القيام بذلك
- Ee
- es
- fi
- fo
- fr
- غيغابايت
- جنرال الكتريك
- غي
- gl
- غرام
- hr
- hu
- اي
- ايل
- is
- it
- كيلوواط
- Kz
- رطل
- لي
- lt
- لو
- lv
- Mc
- Md
- أنا
- عضو الكنيست
- السيد
- طن متري
- مو
- nl
- no
- pl
- pt
- ro
- Rs
- Sa
- حد ذاته
- سي
- sk
- ن خ
- تينيسي
- tr
- Vg

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_iban` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

None