---
title: تعريف كيان رقم التعريف الشخصي في الدانمارك
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التعريف الشخصي في الدانمارك.
ms.openlocfilehash: 8fbdd3fc2bd273b34fcf3625fa9f021d1f948358
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944531"
---
# <a name="denmark-personal-identification-number"></a>رقم التعريف الشخصي للدانمرك

## <a name="format"></a>تنسيق

10 أرقام تحتوي على واصلة

## <a name="pattern"></a>نمط

10 أرقام:

- ستة أرقام بتنسيق DD ولاي، وهي تاريخ الميلاد
- مسافة اختيارية أو واصلة اختيارية
- أربعة أرقام حيث الرقم النهائي هو خانة اختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Func_denmark_eu_tax_file_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_denmark_id` .
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- يبحث التعبير `Func_denmark_eu_tax_file_number` العادي عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Denmark Personal Identification Number -->
    <!-- Denmark Personal Identification Number -->
      <Entity id="6c4f2fef-56e1-4c00-8093-88d7a01cf460" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
          <Match idRef="Keyword_denmark_id" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- مسجل شخصية مركزي
- نظام تسجيل السجل المدني
- Cpr
- Cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- بطاقة صحية
- رقم بطاقة التأمين الصحي
- رقم التأمين الصحي
- رقم التعريف
- رقم معرف
- رقم معرف #
- رقم الهوية
- كرينكينكاسينومر
- معرف وطني #
- رقم وطني #
- الرقم الوطني
- رقم شخصي #
- كيان شخصي #
- رقم المعرف الشخصي
- رقم الشخص
- رقم الشخص #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- Ssn
- Ssn #
- معرف skat
- skat kode
- nummer للتزلج
- skattenummer
- رقم الضمان الاجتماعي
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- رمز الضريبة
- بطاقة التأمين الصحي السفر
- uniqueidentityno #
- رقم الضريبة
- رقم التسجيل الضريبي
- معرف الضريبة
- رقم التعريف الضريبي
- سيارة أجرة #
- رقم الضريبة #
- رقم الضريبة
- الضريبة #
- رقم الضريبة
- رقم التعريف الضريبي
- القصدير #
- سيارة أجرة #
- رقم سيارة أجرة #
- رقم الضريبة #
- معرف الصفيح
- رقم الصفيح
- cpr.nr
- cprnr
- cprnummer
- شخص
- تسجيل شخص
- sygesikringsbevis
- sygesikringsbevisnr
- sygesikringsbevisnummer
- sygesikringskort
- sygesikringskortnr
- sygesikringskortnummer
- sygesikringsnr
- sygesikringsnummer