---
title: تعريف كيان رقم ترخيص برامج التشغيل في أستراليا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم رخصة القيادة في أستراليا.
ms.openlocfilehash: 100bc203f5e3df7445e4067db286f31257b2df9b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944382"
---
# <a name="australia-drivers-license-number"></a>رقم ترخيص برامج التشغيل في أستراليا

## <a name="format"></a>تنسيق

تسعة أحرف وأرقام

## <a name="pattern"></a>نمط

تسعة أحرف وأرقام:

- رقمان أو حرفان (غير حساس لحالة الأحرف)
- رقمين
- خمسة أرقام أو أحرف (غير حساسة لحالة الأحرف)

او

- حرف إلى حرفين اختياريين (غير حساس لحالة الأحرف)
- من أربعة إلى تسعة أرقام

او

- تسعة أرقام أو أحرف (غير حساسة لحالة الأحرف)

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير العادي Regex_australia_drivers_license_number عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_australia_drivers_license_number.
- لم يتم العثور على كلمة أساسية من Keyword_australia_drivers_license_number_exclusions.

```xml
<!-- Australia Drivers License Number -->
<Entity id="1cbbc8f5-9216-4392-9eb5-5ac2298d1356" patternsProximity="300" recommendedConfidence="75">
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_drivers_license_number" />
        <Match idRef="Keyword_australia_drivers_license_number" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_australia_drivers_license_number_exclusions" />
        </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- تراخيص القيادة الدولية
- اتحاد السيارات الأسترالية
- رخصة القيادة الدولية
- DriverLicence
- DriverLicences
- Lic برنامج التشغيل
- رخصة القيادة
- رخص القيادة
- DriversLic
- DriversLicence
- DriversLicences
- Lic برامج التشغيل
- Lics برامج التشغيل
- رخصة القيادة
- رخص القيادة
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- تراخيص القيادة
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- رخص القيادة
- برنامج تشغيل sLic
- برامج التشغيل sLics
- SLicence للسائق
- برامج التشغيل sLicences
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- رخص القيادة
- برنامج تشغيل #
- برامج تشغيل #
- DriverLicence #
- DriverLicences #
- Lic برنامج التشغيل #
- Lics برامج التشغيل #
- رخصة القيادة #
- رخص القيادة #
- DriversLic #
- DriversLics #
- DriversLicence #
- DriversLicences #
- Lic برامج التشغيل #
- Lics برامج التشغيل #
- رخصة القيادة #
- رخص القيادة #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- رخص القيادة #
- برنامج تشغيل sLic #
- برامج التشغيل sLics #
- SLicence للسائق #
- برامج التشغيل sLicences #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- رخص القيادة #

### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- Aaa
- رخصة القيادة
- تراخيص برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- رخصه
- تراخيص برامج التشغيل
- ترخيص القيادة
- تراخيص القيادة
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة #
- تراخيص برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- رخصه #
- تراخيص برامج التشغيل #
- ترخيص القيادة #
- تراخيص القيادة #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
