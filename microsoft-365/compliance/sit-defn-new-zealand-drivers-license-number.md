---
title: تعريف كيان رقم ترخيص برامج تشغيل نيوزيلندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم رخصة القيادة في نيوزيلندا.
ms.openlocfilehash: 56ca27a23cf328978dfc56628a0a5740c8f0ab6e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944334"
---
# <a name="new-zealand-drivers-license-number"></a>رقم ترخيص برامج تشغيل نيوزيلندا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

نقش أبجدي رقمي لثمانية أحرف

## <a name="pattern"></a>نمط

نقش أبجدي رقمي لثمانية أحرف

- حرفان
- ستة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_newzealand_driver_license_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_newzealand_driver_license_number` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_newzealand_driver_license_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- New Zealand Driver License Number -->
      <Entity id="1924b377-d287-49c9-a737-cfe7a8a2615a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
          <Match idRef="Keywords_newzealand_driver_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- برنامج التشغيل
- برامج التشغيل
- lic برنامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل
- تكرار برامج التشغيل
- برامج التشغيل
- lic برامج التشغيل
- برامج التشغيل lics
- رخصة القيادة
- تراخيص برامج التشغيل
- lic للسائق
- lics للسائق
- رخصة القيادة
- تراخيص القيادة
- lic للسائق
- lics للسائق
- رخصة القيادة
- تراخيص القيادة
- محرك اللص
- محركات الشرائح
- شريحة برنامج التشغيل
- مقسمات طريقة عرض برنامج التشغيل
- lic الخاص ببرنامج التشغيل
- lics برامج التشغيل
- رخصة القيادة
- تراخيص القيادة
- برنامج تشغيل #
- برامج التشغيل #
- برنامج التشغيل #
- برامج التشغيل #
- lic برنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- برنامج تشغيل #
- برامج التشغيل #
- تكرار برامج التشغيل #
- برامج التشغيل #
- lic برامج التشغيل #
- برامج التشغيل lics #
- رخصة القيادة #
- تراخيص برامج التشغيل #
- lic للسائق #
- lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- lic للسائق #
- lics للسائق #
- رخصة القيادة #
- تراخيص القيادة #
- محرك اللص #
- محركات الشرائح #
- شريحة برنامج التشغيل #
- مقسمات طريقة عرض برنامج التشغيل #
- lic الخاص ببرنامج التشغيل #
- lics برامج التشغيل #
- رخصة القيادة #
- تراخيص القيادة #
- رخصة القيادة الدولية
- تراخيص القيادة الدولية
- اتحاد السيارات nz
- اتحاد السيارات في نيوزيلندا