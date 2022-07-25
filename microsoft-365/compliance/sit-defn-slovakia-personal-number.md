---
title: تعريف كيان الرقم الشخصي لسلوفاك
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
description: تعريف كيان نوع المعلومات الحساسة للرقم الشخصي السلوفاكي.
ms.openlocfilehash: 4f923c714cf94543828d184164631d5e0c60e9e8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988248"
---
# <a name="slovakia-personal-number"></a>الرقم الشخصي سلوفاكيا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

تسعة أرقام أو 10 أرقام تحتوي على مائلة عكسية اختيارية

## <a name="pattern"></a>نمط

- ستة أرقام تمثل تاريخ الميلاد
- شرطة مائلة اختيارية (/)
- ثلاثة أرقام
- رقم اختيار واحد اختياري

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_slovakia_eu_national_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_slovakia_eu_national_id_card` .

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_slovakia_eu_national_id_card` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Slovakia Personal Number -->
      <Entity id="951c26b7-3b35-4f73-924b-15dd599cb9ab" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
          <Match idRef="Keywords_slovakia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
        </Pattern>
      </Entity>
    </Version>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- رقم الميلاد
- ííslo národnej identifikanej karty
- ííslo obíianského preukazu
- daňové îíslo
- رقم المعرف
- لا يوجد تعريف
- رقم التعريف
- identifikaáná كارتا  ه
- identifikaíné ííslo
- رقم بطاقة الهوية
- رقم بطاقة الهوية
- národná identifikaáná zna ak á
- الرقم الوطني
- رقم وطني #
- nemzeti személyazonosító igazolvány
- رقم شخصي #
- rč
- rodne cislo
- rodné ííslo
- رقم الضمان الاجتماعي
- Ssn #
- Ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyzolvány szám
- ملف الضريبة لا
- رقم ملف الضريبة
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