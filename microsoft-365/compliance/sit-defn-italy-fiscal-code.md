---
title: تعريف كيان التعليمات البرمجية المالية في إيطاليا
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
description: تعريف كيان نوع المعلومات الحساسة للتعليمات البرمجية المالية في إيطاليا.
ms.openlocfilehash: 1a27af7f33aba799a37c64c37e53eef01555ec3c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944700"
---
# <a name="italy-fiscal-code"></a>الرمز المالي في إيطاليا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

تركيبة مكونة من 16 حرفا من الأحرف والأرقام في النمط المحدد

## <a name="pattern"></a>نمط

تركيبة مكونة من 16 حرفا من الأحرف والأرقام:

- ثلاثة أحرف تتوافق مع الأحرف الساكنة الثلاثة الأولى في اسم العائلة
- ثلاثة أحرف تتوافق مع الأحرف الساكنة الأولى والثالثة والرابعة في الاسم الأول
- رقمان يتوافقان مع الأرقام الأخيرة من سنة الميلاد
- حرف واحد يتوافق مع الحرف الخاص بشهر الميلاد— يتم استخدام الأحرف بترتيب أبجدي، ولكن يتم استخدام الأحرف من A إلى E، وH، وL، وM، وP، وR إلى T فقط (لذلك، يناير هو A و أكتوبر هو R)
- رقمان يتوافقان مع يوم شهر الميلاد من أجل التفريق بين الجنسين، يضاف 40 إلى يوم الميلاد بالنسبة إلى امرأة
- أربعة أرقام تتوافق مع رمز المنطقة الخاص بالمقيم حيث ولد الشخص (تستخدم الرموز على مستوى البلد للبلدان الخارجية)
- رقم تماثل واحد

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_italy_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_italy_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_italy_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Italy Fiscal Code -->
      <Entity id="4cd79172-8da9-4ff5-9188-98b1e7e2eca6" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
          <Match idRef="Keywords_italy_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice fiscal
- codice fiscale
- معرف codice personale
- codice personale
- التعليمات البرمجية المالية
- numero certificato personale
- numero di identific kazone fiscale
- numero id personale
- numero personale
- رقم الشهادة الشخصية
- رمز شخصي
- رمز المعرف الشخصي
- رقم المعرف الشخصي
- رمز شخصي #
- رمز الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الهوية الضريبية
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