---
title: تعريف كيان رقم بطاقة هوية تشيلي
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة هوية تشيلي.
ms.openlocfilehash: 1ec3b90d52d5404bf49a343cba7fb2c7f5464870
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944470"
---
# <a name="chile-identity-card-number"></a>رقم بطاقة هوية تشيلي

## <a name="format"></a>تنسيق

من سبعة إلى ثمانية أرقام بالإضافة إلى تحديد خانة اختيار أو حرف

## <a name="pattern"></a>نمط

من سبعة إلى ثمانية أرقام بالإضافة إلى المحددات:

- رقم إلى رقمين
- فترة اختيارية
- ثلاثة أرقام
- فترة اختيارية
- ثلاثة أرقام
- شرطة
- رقم واحد أو حرف واحد (غير حساس لحالة الأحرف) وهو رقم اختيار

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_chile_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_chile_id_card` .
- يمر المجموع الاختباري.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_chile_id_card` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Chile Identity Card Number -->
<Entity id="4e979794-49a0-407e-a0b9-2c536937b925" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_chile_id_card"/>
     <Match idRef="Keyword_chile_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_chile_id_card"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- التعريف الوطني
- رقم التعريف الوطني
- المعرف الوطني
- número de identificación nacional
- rol único nacional
- rol único tributario
- تشغيل
- شبق
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- تشغيل #
- شبق #
- nationaluniqueroleID #
- معرف nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad numero
- رقم الهوية الزكية.
- رقم الهوية الزيلية
- الهوية الزيلية #
- سجل الضريبة الفريد
- دور الفرز الفريد
- دور الضريبة الفريد
- رقم الفرز الفريد
- رقم وطني فريد
- دور وطني فريد
- الدور الفريد الوطني
- رقم هوية تشيلي.
- رقم هوية تشيلي
- هوية تشيلي #
- R.U.T
- R.U.N