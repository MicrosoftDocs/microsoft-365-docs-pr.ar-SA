---
title: تعريف كيان المعرف الوطني ل فنلندا
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
description: تعريف كيان نوع المعلومات الحساسة لمعرف فنلندا الوطني.
ms.openlocfilehash: 7d196482051afb6a889d855c80616a4a15ce1df2
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944658"
---
# <a name="finland-national-id"></a>المعرف الوطني ل فنلندا

## <a name="format"></a>تنسيق

ستة أرقام بالإضافة إلى حرف يشير إلى قرن بالإضافة إلى ثلاثة أرقام بالإضافة إلى خانة اختيار

## <a name="pattern"></a>نمط

يجب أن يتضمن النمط كل ما يلي:

- ستة أرقام بتنسيق DD ولاي، وهي تاريخ الميلاد
- علامة القرن (إما '-' أو '+' أو 'a')
- رقم التعريف الشخصي المكون من ثلاثة أرقام
- رقم أو حرف (غير حساس لحالة الأحرف) وهو رقم اختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_finnish_national_id` عن المحتوى الذي يطابق النمط
- تم العثور على كلمة أساسية من `Keyword_finnish_national_id`
- تمريرات المجموع الاختباري

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_finnish_national_id` عن المحتوى الذي يطابق النمط
- تمريرات المجموع الاختباري

```xml
      <!-- Finnish National ID-->
      <Entity id="338FD995-4CB5-4F87-AD35-79BD1DD926C1" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finnish_national_id" />
          <Match idRef="Keyword_finnish_national_id" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_finnish_national_id" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

- تونوس henkilökohtainen
- تونوس henkilökohtainen
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- المعرف لا
- رقم المعرف
- رقم التعريف
- identiteetti numero
- رقم الهوية
- رقم المعرف
- kansallinen henkilötunnus
- kansallisen henkilökortin
- بطاقة المعرف الوطنية
- رقم المعرف الوطني.
- المعرف الشخصي
- رمز الهوية الشخصية
- رقم شخصي #
- اختيار شخص
- رقم الشخص
- رقم الضمان الاجتماعي
- sosiaaliturvatunnus
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
- tunnistenumero
- tunnus numero
- تونوسلالوكو
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus