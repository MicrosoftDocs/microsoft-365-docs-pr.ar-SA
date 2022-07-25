---
title: المملكة المتحدة تعريف كيان رقم التأمين الوطني (NINO)
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
description: المملكة المتحدة تعريف كيان نوع المعلومات الحساسة لرقم التأمين الوطني (NINO).
ms.openlocfilehash: 44b41cf2c19d001e142ff527b431990ebd3c80c6
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988283"
---
# <a name="uk-national-insurance-number-nino"></a>المملكة المتحدة رقم التأمين الوطني (NINO)

يتم تضمين كيان نوع المعلومات الحساسة هذا في نوع المعلومات الحساسة لرقم التعريف الوطني للاتحاد الأوروبي. كما أنها متوفرة ككيان مستقل لنوع المعلومات الحساسة.

## <a name="format"></a>تنسيق

سبعة أحرف أو تسعة أحرف مفصولة بمسافات أو شرط

## <a name="pattern"></a>نمط

نمطان محتملان:

- حرفان (تستخدم NINOs الصالحة أحرفا معينة فقط في هذه البادئة، والتي يقوم هذا النمط بالتحقق من صحتها؛ غير حساسة لحالة الأحرف)
- ستة أرقام
- إما 'A' أو 'B' أو 'C' أو 'D' (مثل البادئة، يتم السماح بأحرف معينة فقط في اللاحقة؛ غير حساسة لحالة الأحرف)

او

- حرفان
- مسافة أو شرطة
- رقمين
- مسافة أو شرطة
- رقمين
- مسافة أو شرطة
- رقمين
- مسافة أو شرطة
- إما 'A' أو 'B' أو 'C' أو 'D'

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_uk_nino` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_uk_nino` .

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_uk_nino` عن المحتوى الذي يطابق النمط.

```xml
    <!-- U.K. NINO -->
    <Entity id="16c07343-c26f-49d2-a987-3daf717e94cc" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nino" />
        <Match idRef="Keyword_uk_nino" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_nino" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- رقم التأمين الوطني
- مساهمات التأمين الوطنية
- قانون الحماية
- التامين
- رقم الضمان الاجتماعي
- تطبيق التأمين
- تطبيق طبي
- التأمين الاجتماعي
- العناية الطبية
- الضمان الاجتماعي
- الولايات المتحدة العظمى
- رقم NI
- رقم NI.
- ني #
- ني #
- التامين #
- رقم التأمين
- الطمأنينة الوطنية #
- رقم الأرقام الوطنية