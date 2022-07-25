---
title: تعريف كيان رقم التسجيل المقيم في اليابان
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
description: تعريف كيان نوع المعلومات الحساسة لرقم التسجيل المقيم في اليابان.
ms.openlocfilehash: 2cdff586ac9fe92e66a5844eae824f7df335eb31
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988278"
---
# <a name="japan-resident-registration-number"></a>رقم التسجيل المقيم في اليابان

## <a name="format"></a>تنسيق

11 رقما

## <a name="pattern"></a>نمط

11 رقما متتاليا

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_jp_resident_registration_number` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_jp_resident_registration_number` .

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- رقم التسجيل المقيم
- رقم السجل الأساسي للمقيمين
- رقم تسجيل المقيم.
- رقم السجل المقيم.
- رقم السجل الأساسي للمقيمين.
- رقم السجل المقيم الأساسي.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証