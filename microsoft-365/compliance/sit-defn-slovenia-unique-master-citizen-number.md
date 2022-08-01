---
title: تعريف كيان رقم المواطنين الرئيسي الفريد لسلوفانيا
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
description: تعريف كيان نوع المعلومات الحساسة ل "رقم المواطنين الرئيسي الفريد" في سلوفانيا.
ms.openlocfilehash: 23c484946c8e73e7f21b251aa35935dba37b110b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944460"
---
# <a name="slovenia-unique-master-citizen-number"></a>رقم المواطن الرئيسي الفريد في سلوفينيا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

13 رقما بدون مسافات أو محددات

## <a name="pattern"></a>نمط

13 رقما في النمط المحدد:

- سبعة أرقام تتوافق مع تاريخ الميلاد (DDMMLLL) حيث تتوافق "LLL" مع الأرقام الثلاثة الأخيرة من سنة الميلاد
- رقمان يتوافقان مع منطقة الميلاد "50"
- ثلاثة أرقام تتوافق مع مجموعة من الجنس والرقم التسلسلي للأشخاص الذين ولدوا في نفس اليوم. 000-499 للذكر و500-999 للإناث.
- خانة اختيار واحدة

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_slovenia_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_slovenia_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_slovenia_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Slovenia Unique Master Citizen Number -->
      <Entity id="68948b27-803d-41e4-adf1-13e05eb541bb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
          <Match idRef="Keywords_slovenia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena ütevilka gvilnega drjaavljana
- رمز المشاعر
- enotna maticna riftevilka obcana
- بطاقة المعرف
- رقم التعريف
- identifikacijska ذتيvilka
- بطاقة هوية
- معرف nacionalna
- قائمة nacionalni potni
- المعرف الوطني
- osebna izkaznica
- osebni koda
- osebni ne
- osebni ذتيvilka
- رمز شخصي
- رقم شخصي
- رمز رقمي شخصي
- ütevilka drjaavljana
- رقم مواطن فريد
- رقم المعرف الفريد
- رقم هوية فريد
- رقم مواطن رئيسي فريد
- رقم تسجيل فريد
- uniqueidentityno #
- uniqueidentityno #