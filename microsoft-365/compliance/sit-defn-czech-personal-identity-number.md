---
title: تعريف كيان رقم الهوية الشخصية التشيكية
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
description: تعريف كيان نوع المعلومات الحساسة لرقم الهوية الشخصية التشيكية.
ms.openlocfilehash: a5c6156a2f84ff96025c3f73cf20dcbd201e90d3
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944716"
---
# <a name="czech-personal-identity-number"></a>رقم الهوية الشخصية التشيكية

## <a name="format"></a>تنسيق

تسعة أرقام مع شرطة مائلة للأمام اختيارية (تنسيق قديم)

10 أرقام مع شرطة مائلة للأمام اختيارية (تنسيق جديد)

## <a name="pattern"></a>نمط

تسعة أرقام (تنسيق قديم):

- ستة أرقام تمثل تاريخ الميلاد
- شرطة مائلة للأمام اختيارية
- ثلاثة أرقام

10 أرقام (تنسيق جديد):

- ستة أرقام تمثل تاريخ الميلاد
- شرطة مائلة للأمام اختيارية
- أربعة أرقام حيث الرقم الأخير هو خانة اختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_czech_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_czech_id_card` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_czech_id_card_new_format` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Czech Personal Identity Number -->
      <!-- Czech Personal Identity Number -->
      <Entity id="60c0725a-4eb6-455b-9dda-05d8a7396497" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_czech_id_card" />
          <Match idRef="Keyword_czech_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.3000.000">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Func_czech_id_card_new_format" />
          </Pattern>
        </Version>
      </Entity>
```
## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- رقم الميلاد
- معرف جمهورية تشيكيا
- تشيكيدنو #
- daňové îíslo
- identifikaíní ííslo
- لا هوية
- رقم الهوية
- identityno #
- identityno
- رقم التأمين
- رقم التعريف الوطني
- رقم وطني #
- الرقم الوطني
- osobní ííslo
- رقم شخصي #
- رقم المعرف الشخصي
- رقم التعريف الشخصي
- رقم شخصي
- Pid #
- Pid
- pojiîtění îíslo
- rč
- rodne cislo
- rodné ííslo
- Ssn
- Ssn #
- رقم الضمان الاجتماعي
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
- رقم تعريف فريد