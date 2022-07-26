---
title: تعريف كيان التعليمات البرمجية الشخصية اللاتفية
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
description: تعريف كيان نوع المعلومات الحساسة للتعليمات البرمجية الشخصية اللاتفية.
ms.openlocfilehash: 16e736220fa402df6ebcb87e947e75090b4a0f57
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944231"
---
# <a name="latvia-personal-code"></a>رمز لاتفيا الشخصي

## <a name="format"></a>تنسيق

11 رقما وواصلة اختيارية

## <a name="pattern"></a>نمط

التنسيق القديم

11 رقما وواصلة:

- ستة أرقام تتوافق مع تاريخ الميلاد (DDNAMY)
- واصلة
- رقم واحد يتوافق مع قرن الميلاد ("0" في القرن التاسع عشر، و"1" في القرن العشرين، و"2" في القرن الحادي والعشرين)
- أربعة أرقام، تم إنشاؤها عشوائيا

تنسيق جديد

11 رقما

- رقمان "32"
- تسعة أرقام

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_latvia_eu_national_id_card` أو regex `Regex_latvia_eu_national_id_card_new_format` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_latvia_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_latvia_eu_national_id_card` أو regex `Regex_latvia_eu_national_id_card_new_format` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Latvia Personal Code -->
      <Entity id="03fcf763-27c2-49ed-9422-2641c6c895c9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- رقم إداري
- alvas nē
- رقم الميلاد
- رقم المواطنين
- الرقم المدني
- رقم التعداد الإلكتروني
- رقم إلكتروني
- التعليمات البرمجية المالية
- رقم مستخدم الرعاية الصحية
- معرف #
- رمز المعرف
- رقم التعريف
- identifikjas nunus
- رقم المعرف
- رقم فردي
- latvija alva
- معرف nacionakalais
- المعرف الوطني
- رقم تعريف وطني
- رقم الهوية الوطنية
- رقم التأمين الوطني
- رقم السجل الوطني
- nodokļa nunus
- معرف nodokļu
- nodokļu identifikîcija nununus
- رقم الشهادة الشخصية
- رمز شخصي
- رمز المعرف الشخصي
- رقم المعرف الشخصي
- رمز التعريف الشخصي
- المعرف الشخصي
- رقم الهوية الشخصية
- رقم شخصي
- رمز رقمي شخصي
- رمز شخصي #
- personas kods
- رمز تعريف المحتوى
- رقم الخدمة العامة
- رقم التسجيل
- رقم الإيرادات
- رقم التأمين الاجتماعي
- رقم الضمان الاجتماعي
- رمز ضريبة الحالة
- رقم ملف الضريبة
- معرف الضريبة
- رقم التعريف الضريبي
- رقم التعريف الضريبي
- رقم الضريبة #
- رقم الضريبة
- رقم الضريبة
- سيارة أجرة #
- سيارة أجرة #
- رقم سيارة أجرة #
- الضريبة #
- رقم الضريبة #
- رقم الضريبة
- معرف الصفيح
- رقم الصفيح
- القصدير #
- رقم المصوت