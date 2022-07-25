---
title: تعريف كيان رقم ترخيص برامج التشغيل السلوفينية
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
description: تعريف كيان نوع المعلومات الحساسة لرقم رخصة القيادة السلوفينية.
ms.openlocfilehash: 760972a7780ef6438b9e1c3109be26ddcba75dcb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988245"
---
# <a name="slovenia-drivers-license-number"></a>رقم ترخيص برامج التشغيل السلوفينية

## <a name="format"></a>تنسيق

تسعة أرقام بدون مسافات ومحددات

## <a name="pattern"></a>نمط

تسعة أرقام

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_slovenia_eu_driver's_license_number` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية من `Keywords_eu_driver's_license_number` أو `Keywords_slovenia_eu_driver's_license_number` تم العثور عليها.

```xml
      <!-- Slovenia Driver's License Number -->
      <Entity id="d5bc089a-f2ee-433d-a6b1-5c253051d6f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovenia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- برنامج تشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- lics برامج التشغيل
- ترخيص برنامج التشغيل
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- برامج التشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصه
- تراخيص برامج التشغيل
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- ترخيص القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- مقسم طريقة عرض برنامج التشغيل
- شرائح برنامج التشغيل
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- Dl #
- Dls #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- ترخيص برنامج التشغيل #
- تراخيص برامج التشغيل #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصه #
- تراخيص برامج التشغيل #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- ترخيص القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- مقسم طريقة عرض برنامج التشغيل #
- شرائح برنامج التشغيل #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة
- رخصة القيادة
- dlno #
- محرك lic
- القيادة الزهية
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل مسنن
- برامج التشغيل غير المهيملة
- رنين برنامج التشغيل
- محرك lic
- القيادة مدفوعة
- تراخيص القيادة
- رخصة القيادة
- تراخيص القيادة
- رخصة القيادة
- dl no
- dlno
- رقم dl

### <a name="keywords_slovenia_eu_drivers_license_number"></a>s_license_number Keywords_slovenia_eu_driver

- voznijeko dovoljenje
- ترخيص vozni دوليةka ztevilka
- vozniلفkih dovoljenj
- ztevilka voznijakega dovoljenja
- številke vozniških dovoljenj