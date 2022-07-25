---
title: تعريف كيان رقم ترخيص برامج التشغيل الأمريكية
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
description: تعريف كيان نوع المعلومات الحساسة لرقم رخصة القيادة الأمريكية.
ms.openlocfilehash: d25de827c913781c0426d8c6262bcb9f421ee73e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988263"
---
# <a name="us-drivers-license-number"></a>رقم ترخيص برامج التشغيل الأمريكية

## <a name="format"></a>تنسيق

يعتمد على الحالة

## <a name="pattern"></a>نمط

يعتمد على الولاية - على سبيل المثال، نيويورك:

- ستتطابق تسعة أرقام منسقة مثل ddd ddd ddd.
- لن تتطابق تسعة أرقام مثل ddddddd.

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_new_york_drivers_license_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_[state_name]_drivers_license_name` .
- تم العثور على كلمة أساسية منها `Keyword_us_drivers_license` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_new_york_drivers_license_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_[state_name]_drivers_license_name` .
- تم العثور على كلمة أساسية منها `Keyword_us_drivers_license_abbreviations` .
- لم يتم العثور على كلمة أساسية منها `Keyword_us_drivers_license` .

```xml
<Entity id="dfeb356f-61cd-459e-bf0f-7c6d28b458c6 patternsProximity="300">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license" />
    </Pattern>
    <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license_abbreviations" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_us_drivers_license" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- المعرّف
- معرفات
- DL #
- DLS #
- CDL #
- CDLS #
- معرف #
- معرفات #
- رقم المعرف
- أرقام المعرف
- يسانس
- يسانس #
- DLN

### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- برنامج تشغيل
- برامج تشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- Lic برنامج التشغيل
- Lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- DriversLic
- DriversLics
- رخصة القيادة
- تراخيص برامج التشغيل
- Lic برامج التشغيل
- Lics برامج التشغيل
- رخصه
- تراخيص برامج التشغيل
- Lic للسائق
- Lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- Lic للسائق
- Lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- برنامج تشغيل sLic
- برامج التشغيل sLics
- رخصة القيادة
- تراخيص برامج التشغيل
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- تراخيص القيادة
- رقم التعريف
- أرقام التعريف
- تحديد #
- بطاقة المعرف
- بطاقات المعرف
- بطاقة التعريف
- بطاقات التعريف
- برنامج تشغيل #
- برامج تشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- Lic برنامج التشغيل #
- Lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- DriversLic #
- DriversLics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- Lic برامج التشغيل #
- Lics برامج التشغيل #
- رخصه #
- تراخيص برامج التشغيل #
- Lic للسائق #
- Lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- Lic للسائق #
- Lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- برنامج تشغيل sLic #
- برامج التشغيل sLics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- بطاقة المعرف #
- بطاقات المعرف #
- بطاقة التعريف #
- بطاقات التعريف #

### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- اختصار الحالة (على سبيل المثال، "NY")
- اسم الولاية (على سبيل المثال، "نيويورك")