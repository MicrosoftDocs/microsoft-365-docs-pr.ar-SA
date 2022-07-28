---
title: تعريف كيان رمز التعريف الشخصي الإستوني
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
description: تعريف كيان نوع المعلومات الحساسة لرمز التعريف الشخصي الإستوني.
ms.openlocfilehash: 866c78a871f0d402cab49783b43e770328b32b1d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944308"
---
# <a name="estonia-personal-identification-code"></a>رمز التعريف الشخصي الإستوني

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

11 رقما بدون مسافات ومحددات

## <a name="pattern"></a>نمط

11 رقما:

- رقم واحد يتوافق مع الجنس وقرن الميلاد (رقم فردي ذكر، حتى رقم أنثى؛ 1-2: القرن التاسع عشر؛ 3-4: القرن العشرين؛ 5-6: القرن الحادي والعشرون)
- ستة أرقام تتوافق مع تاريخ الميلاد (YYMMDD)
- ثلاثة أرقام تتوافق مع رقم تسلسلي يفصل بين الأشخاص الذين ولدوا في نفس التاريخ
- خانة اختيار واحدة

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_estonia_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_estonia_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_estonia_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Estonia Personal Identification Code -->
      <Entity id="bfb26de6-dad5-4d48-ab72-4789cdd0654c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Match idRef="Keywords_estonia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_estonia_eu_telephone_number" />
            <Match idRef="Keywords_estonia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- ايك
- isikukood #
- isikukood
- معرف maksu
- maksukohustuslase identifitseerimisnumber
- maksunumber
- رقم التعريف الوطني
- الرقم الوطني
- رمز شخصي
- رقم المعرف الشخصي
- رمز التعريف الشخصي
- رقم التعريف الشخصي
- رقم شخصي #
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- رقم التسجيل الضريبي
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #