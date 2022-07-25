---
title: تعريف الكيان الضريبي للقيمة المضافة في النمسا
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
description: تعريف كيان نوع المعلومات الحساسة للضريبة للقيمة المضافة في النمسا.
ms.openlocfilehash: b4d6841e857d81c42255eec1184e51623f78059f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988313"
---
# <a name="austria-value-added-tax"></a>ضريبة القيمة المضافة في النمسا

يتوفر نوع المعلومات الحساسة هذا للاستخدام فقط في:

- نهج منع فقدان البيانات
- نهج التوافق مع الاتصالات
- إدارة دورة حياة البيانات
- إدارة السجلات
- Microsoft Defender for Cloud Apps

## <a name="format"></a>تنسيق

نقش أبجدي رقمي مكون من 11 حرفا

## <a name="pattern"></a>نمط

نمط أبجدي رقمي مكون من 11 حرفا:

- A أو a
- T أو t
- مساحة اختيارية
- U أو u
- مساحة اختيارية
- رقمان أو ثلاثة أرقام
- مساحة اختيارية
- أربعة أرقام
- مساحة اختيارية
- رقم واحد أو رقمين

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Austria_Value_Added_Tax عن المحتوى الذي يتطابق مع النمط.
- تم العثور على كلمة أساسية من Keyword_Austria_Value_Added_Tax.

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة Func_Austria_Value_Added_Tax عن المحتوى الذي يتطابق مع النمط.

```xml
      <!-- Austria Value Added Tax -->
      <Entity id="b6a3eda2-c56c-4b69-a5f7-dca34db00f48" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
          <Match idRef="Keyword_Austria_Value_Added_Tax" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- رقم ضريبة القيمة المضافة
- ضريبه القيمه المضافه #
- رقم ضريبة القيمة المضافة في الولايات المتحدة الأمريكية
- رقم ضريبة القيمة المضافة.
- vatno #
- رقم ضريبة القيمة المضافة
- ضريبة القيمة المضافة في الولايات المتحدة الأمريكية
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- رقم تعريف ضريبة القيمة المضافة
- رقم عمودي
- رقم uid