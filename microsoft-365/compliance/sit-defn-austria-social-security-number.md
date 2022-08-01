---
title: تعريف كيان رقم الضمان الاجتماعي في النمسا
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الضمان الاجتماعي في النمسا.
ms.openlocfilehash: 24b909e2b45bce3db5c4b4cfd1e0d3cf3d74296c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944467"
---
# <a name="austria-social-security-number"></a>رقم الضمان الاجتماعي في النمسا

## <a name="format"></a>تنسيق

10 أرقام بالتنسيق المحدد

## <a name="pattern"></a>نمط

10 أرقام:

- ثلاثة أرقام تتوافق مع رقم تسلسلي
- خانة اختيار واحدة
- ستة أرقام تتوافق مع تاريخ الميلاد (DDNAMY)

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_austria_eu_ssn_or_equivalent` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keywords_austria_eu_ssn_or_equivalent` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_austria_eu_ssn_or_equivalent` عن المحتوى الذي يطابق النمط.

```xml
      <!-- Austria Social Security Number -->
      <Entity id="6896a906-86c9-4d19-a2da-6e43ccd19b7b" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_austria_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_austria_eu_telephone_number" />
            <Match idRef="Keywords_austria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- ssn في
- رقم ehic
- ehic no
- رمز التأمين
- رمز التأمين #
- رقم التأمين
- لا يوجد تأمين
- كرينكينكاسينومر
- كرينكينفيرسيشيرونغ
- الأمن الاجتماعي
- الأمن الاجتماعي #
- الضمان الاجتماعي لا
- رقم الضمان الاجتماعي
- رمز الضمان الاجتماعي
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- Ssn #
- Ssn
- versicherungscode
- versicherungsnummer
- zdveno zavarovanje