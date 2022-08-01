---
title: تعريف كيان رقم الخدمة العامة الشخصية (PPS) في أيرلندا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الخدمة العامة الشخصية (PPS) في أيرلندا.
ms.openlocfilehash: 9473886085fe3ae5630becdeeb69efb82f428edd
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944557"
---
# <a name="ireland-personal-public-service-pps-number"></a>رقم الخدمة العامة الشخصية (PPS) في أيرلندا

## <a name="format"></a>تنسيق

التنسيق القديم (حتى 31 ديسمبر 2012):

- سبعة أرقام متبوعة بأحرف من 1 إلى 2

تنسيق جديد (1 يناير 2013 وبعده):

- سبعة أرقام متبوعة بحرفين

## <a name="pattern"></a>نمط

التنسيق القديم (حتى 31 ديسمبر 2012):

- سبعة أرقام
- حرف إلى حرفين (غير حساس لحالة الأحرف)

تنسيق جديد (1 يناير 2013 وبعده):

- سبعة أرقام
- حرف (غير حساس لحالة الأحرف) وهو رقم فحص أبجدي
- حرف اختياري في النطاق A-I أو "W"

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- محتوى الدالة `Func_ireland_pps finds` الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_ireland_eu_national_id_card` .
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_ireland_pps` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
      <!-- Ireland Personal Public Service (PPS) Number -->
      <Entity id="1cdb674d-c19a-4fcf-9f4b-7f56cc87345a" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_ireland_pps" />
          <Match idRef="Keywords_ireland_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_ireland_pps" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- خدمة هوية العميل
- رقم التعريف
- رقم المعرف الشخصي
- رقم الخدمة العامة الشخصية
- الخدمة الشخصية لا
- phearsanta seirbhíse poiblí
- pps no
- رقم pps
- pps num
- pps service no
- ppsn
- ppsno #
- ppsno
- Psp
- الخدمة العامة لا
- الخدمة العامة #
- الخدمة العامة
- رقم الإيرادات والتأمين الاجتماعي
- rsi no
- رقم rsi
- rsin
- عميل seirbhís aitheantais
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
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