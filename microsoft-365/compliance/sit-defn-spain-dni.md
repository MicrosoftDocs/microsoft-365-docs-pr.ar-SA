---
title: تعريف كيان DNI في إسبانيا
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
description: تعريف كيان نوع المعلومات الحساسة DNI في إسبانيا.
ms.openlocfilehash: e18fbfdcaad30e94d9f8fbd239026c25bee04d78
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944387"
---
# <a name="spain-dni"></a>بطاقة الهوية الوطنية (DNI) الإسبانية

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

ثمانية أرقام متبوعة بحرف واحد

## <a name="pattern"></a>نمط

سبعة أرقام متبوعة بحرف واحد

- ثمانية أرقام
- مسافة اختيارية أو واصلة اختيارية
- حرف اختيار واحد (غير حساس لحالة الأحرف)

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` البحث عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_spain_eu_national_id_card"` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- الدالة `Func_spain_eu_DL_and_NI_number_citizen` أو `Func_spain_eu_DL_and_NI_number_foreigner` البحث عن المحتوى الذي يطابق النمط.

```xml
      <!-- Spain DNI -->
      <Entity id="8e6251b9-47b4-40e8-a42b-0f80876be192" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- dni #
- dni
- dninúmero #
- documento nacional de identidad
- identidad único
- identidadúnico #
- رقم التأمين
- رقم التعريف الوطني
- الهوية الوطنية
- معرف وطني #
- nationalidno #
- نيه #
- نيه
- nienúmero #
- número de identificación
- número nacional identidad
- رقم التعريف الشخصي
- الهوية الشخصية لا
- رقم هوية فريد
- معرف فريد #