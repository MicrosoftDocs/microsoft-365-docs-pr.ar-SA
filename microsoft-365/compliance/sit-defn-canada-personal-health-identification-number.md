---
title: تعريف كيان رقم التعريف الصحي الشخصي (PHIN) في كندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الصحي الشخصي (PHIN) في كندا.
ms.openlocfilehash: 0d2ac2f8deeb4cb9139d0ab66cb02bbd4bccd7c8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988251"
---
# <a name="canada-personal-health-identification-number-phin"></a>رقم التعريف الصحي الشخصي لكندا (PHIN)

## <a name="format"></a>تنسيق

تسعة أرقام

## <a name="pattern"></a>نمط

تسعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_canada_phin` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمتين أساسيتين على الأقل من `Keyword_canada_phin` أو `Keyword_canada_provinces` تم العثور عليها.

```xml
<!-- Canada PHIN -->
<Entity id="722e12ac-c89a-4ec8-a1b7-fea3469f89db" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_phin" />
        <Any minMatches="2">
          <Match idRef="Keyword_canada_phin" />
          <Match idRef="Keyword_canada_provinces" />
        </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- رقم التأمين الاجتماعي
- قانون المعلومات الصحية
- معلومات ضريبة الدخل
- صحة مانيتوبا
- التسجيل الصحي
- مشتريات وصفة طبية
- الأهلية للاستفادة
- الصحة الشخصية
- قوة الوكيل
- رقم التسجيل
- رقم الحماية الشخصية
- إحالة ممارس
- محترف الكفاءة
- إحالة المريض
- الصحة والصحة

### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- نونافوت
- كيبيك
- المناطق الشمالية الغربية
- اونتاريو
- مقاطعة بريتامبيا البريطانية
- البرتا
- ساسكاتشوان
- مانيتوبا
- يوكون
- نيوفاوندلاند ولابرادور
- بروناسويك جديد
- نوفا سكوتيا
- جزيرة أدوارد الاميرة
- كندا