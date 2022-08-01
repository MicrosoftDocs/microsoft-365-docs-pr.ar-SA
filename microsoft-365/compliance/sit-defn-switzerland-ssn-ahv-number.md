---
title: تعريف كيان رقم SSN AHV في سويسرا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم SSN AHV في سويسرا.
ms.openlocfilehash: e06ef00d0d8c919f4506d829899b0f6150394854
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944591"
---
# <a name="switzerland-ssn-ahv-number"></a>رقم SSN AHV في سويسرا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

رقم مكون من 13 رقما

## <a name="pattern"></a>نمط

رقم مكون من 13 رقما:

- ثلاثة أرقام - 756
- نقطة اختيارية
- أربعة أرقام
- نقطة اختيارية
- أربعة أرقام
- نقطة اختيارية
- رقمين

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_swiss_social_security_number_ahv` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_swiss_social_security_number_ahv` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_swiss_social_security_number_ahv` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Swiss SSN AHV Number -->
      <Entity id="277cfa4b-6eaa-4a1b-9492-099dec849971" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
          <Match idRef="Keywords_swiss_social_security_number_ahv" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- ahv
- Ssn
- Pid
- رقم التأمين
- personalidno #
- رقم الضمان الاجتماعي
- رقم المعرف الشخصي
- رقم التعريف الشخصي.
- تأمين #
- uniqueidno #
- رقم التعريف الفريد.
- رقم avs
- الهوية الشخصية بلا رقم versicherungsnummer
- رقم معرف
- niczigartige identität niه
- sozialversicherungsnummer
- معرف تعريف الموظفين
- numéro de sécurité sociale