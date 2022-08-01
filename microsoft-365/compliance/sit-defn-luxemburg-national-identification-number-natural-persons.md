---
title: تعريف كيان رقم التعريف الوطني (الأشخاص الطبيعيين) في أوسمبورغ
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
description: تعريف كيان نوع المعلومات الحساسة ل Namemburg لرقم التعريف الوطني (الأشخاص الطبيعيين).
ms.openlocfilehash: d70052fdccfae70302a89069b5292c0daf5b8b2f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944726"
---
# <a name="luxemburg-national-identification-number-natural-persons"></a>رقم التعريف الوطني في لوسيمبورغ (الأشخاص الطبيعيون)

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

13 رقما بدون مسافات أو محددات

## <a name="pattern"></a>نمط

13 رقما:

- 11 رقما
- خانتا اختيار رقميتان

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_luxemburg_eu_tax_file_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_luxemburg_eu_national_id_card` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_luxemburg_eu_tax_file_number` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Luxemburg National Identification Number (Natural persons) -->
      <Entity id="aaf661ed-29ec-426d-8bf9-880cad298ebb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Match idRef="Keywords_luxemburg_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- معرف غير مهيئ
- معرف eindeutige-nummer
- eindeutigeid #
- معرف الموظفين
- idpersonnelle #
- idpersonnelle
- تعليمة برمجية فردية
- معرف فردي
- تعريف فردي
- الهوية الفردية
- موظفو تعريف numéro d'd'
- المعرف الشخصي
- التعريف الشخصي
- الهوية الشخصية
- personalidno #
- رقم شخصي #
- persönliche identifikationsnummer
- معرف فريد
- هوية فريدة
- مفتاح فريد #