---
title: تعريف كيان الرقم الوطني في بلجيكا
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
description: تعريف كيان نوع المعلومات الحساسة للرقم الوطني في بلجيكا.
ms.openlocfilehash: 5fc644a8dcb275cba2986139dfdd16444e47c218
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988344"
---
# <a name="belgium-national-number"></a>الرقم الوطني في بلجيكا

## <a name="format"></a>تنسيق

11 رقما بالإضافة إلى المحددات الاختيارية

## <a name="pattern"></a>نمط

11 رقما بالإضافة إلى المحددات:

- ستة أرقام وفترتان اختياريتان بالتنسيق YY. MM.DD لتاريخ الميلاد
- محدد اختياري من نقطة، شرطة، مسافة
- ثلاثة أرقام متتالية (فردية للذكور، حتى للإناث)
- محدد اختياري من نقطة، شرطة، مسافة
- خانتا اختيار رقميتان

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_belgium_national_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_belgium_national_number` .
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_belgium_national_number` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Belgium National Number -->
       <Entity id="fb969c9e-0fd1-4b18-8091-a2123c5e6a54" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_national_number" />
          <Match idRef="Keyword_belgium_national_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_belgium_national_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- مائل إلى الكسل
- bnn #
- bnn
- carte d'identité
- المعرف الوطني
- تعريفي #
- تحديد الفئة
- تحديد
- تعريف
- رقم معرف
- identifizierung
- الهويات
- هوية
- identiteitskaart
- الهويه
- النقش
- الرقم الوطني
- السجل الوطني
- رقم وطني #
- رقم وطني
- Nif #
- Nif
- numéro d'assuré
- numéro de registre national
- numéro de sécurité
- numéro d'identification
- numéro d'immatriculation
- numéro national
- رقمي #
- رقم المعرف الشخصي
- personalausweis
- رقم شخصي #
- تسجيل الصبر
- التسجيل
- رقم التسجيلات
- registrierung
- رقم الضمان الاجتماعي
- Ssn #
- Ssn
- رقم عمودي
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