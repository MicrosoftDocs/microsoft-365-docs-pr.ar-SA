---
title: تعريف كيان رقم ترخيص برامج التشغيل في كندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم رخصة القيادة في كندا.
ms.openlocfilehash: a42af206eef8508bd971fad60d213c15f131e2b2
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944722"
---
# <a name="canada-drivers-license-number"></a>رقم ترخيص برامج التشغيل في كندا

## <a name="format"></a>تنسيق

يختلف حسب المقاطعة

## <a name="pattern"></a>نمط

أنماط مختلفة تغطي:

- البرتا
- مقاطعة بريتامبيا البريطانية
- مانيتوبا
- بروناسويك جديد
- نيوفاوندلاند/لابرادور
- نوفا سكوتيا
- اونتاريو
- جزيرة أدوارد الاميرة
- كيبيك
- ساسكاتشوان

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_[province_name]_drivers_license_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_[province_name]_drivers_license_name` .
- تم العثور على كلمة أساسية منها `Keyword_canada_drivers_license` .

```xml
<!-- Canada Driver's License Number -->
    <Entity id="37186abb-8e48-4800-ad3c-e3d1610b3db0" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_alberta_drivers_license_number" />
        <Match idRef="Keyword_alberta_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_british_columbia_drivers_license_number" />
        <Match idRef="Keyword_british_columbia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_manitoba_drivers_license_number" />
        <Match idRef="Keyword_manitoba_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_brunswick_drivers_license_number" />
        <Match idRef="Keyword_new_brunswick_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_newfoundland_labrador_drivers_license_number" />
        <Match idRef="Keyword_newfoundland_labrador_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_nova_scotia_drivers_license_number" />
        <Match idRef="Keyword_nova_scotia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_ontario_drivers_license_number" />
        <Match idRef="Keyword_ontario_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_prince_edward_island_drivers_license_number" />
        <Match idRef="Keyword_prince_edward_island_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_quebec_drivers_license_number" />
        <Match idRef="Keyword_quebec_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_saskatchewan_drivers_license_number" />
        <Match idRef="Keyword_saskatchewan_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- اختصار المقاطعة، على سبيل المثال AB
- اسم المقاطعة، على سبيل المثال،"ألبيرا"

### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- برنامج تشغيل
- برامج تشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- DriverLicence
- DriverLicences
- Lic برنامج التشغيل
- Lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- رخص القيادة
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- رخصة القيادة
- تراخيص برامج التشغيل
- Lic برامج التشغيل
- Lics برامج التشغيل
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- رخص القيادة
- Lic للسائق
- Lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Lic للسائق
- Lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- رخص القيادة
- برنامج تشغيل sLic
- برامج التشغيل sLics
- رخصة القيادة
- تراخيص برامج التشغيل
- SLicence للسائق
- برامج التشغيل sLicences
- Lic للسائق
- Lics للسائق
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- رخص القيادة
- Permis de Conduire
- id
- معرفات
- رقم بطاقة idcard
- أرقام بطاقات idcard
- بطاقة idcard #
- #s بطاقة idcard
- بطاقة بطاقة idcard
- بطاقات بطاقة idcard
- بطاقة idcard
- رقم التعريف
- أرقام التعريف
- تحديد #
- #s التعريف
- بطاقة التعريف
- بطاقات التعريف
- تحديد
- DL #
- DLS #
- CDL #
- CDLS #
- برنامج تشغيل #
- برامج تشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- DriverLicence #
- DriverLicences #
- Lic برنامج التشغيل #
- Lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- ترخيص برنامج التشغيل #
- رخص القيادة #
- DriversLic #
- DriversLics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- DriversLicence #
- DriversLicences #
- Lic برامج التشغيل #
- Lics برامج التشغيل #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- رخص القيادة #
- Lic للسائق #
- Lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- Lic للسائق #
- Lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- رخص القيادة #
- برنامج تشغيل sLic #
- برامج التشغيل sLics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- SLicence للسائق #
- برامج التشغيل sLicences #
- Lic للسائق #
- Lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- رخص القيادة #
- Permis de Conduire #
- معرف #
- معرفات #
- بطاقة بطاقة idcard #
- بطاقات بطاقة idcard #
- بطاقة idcard #
- بطاقة التعريف #
- بطاقات التعريف #
- تحديد #