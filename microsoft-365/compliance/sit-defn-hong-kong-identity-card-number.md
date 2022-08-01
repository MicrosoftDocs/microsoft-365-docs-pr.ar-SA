---
title: تعريف كيان رقم بطاقة هوية هونغ كونغ (HKID)
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
description: تعريف كيان نوع المعلومات الحساسة لرقم هوية هونغ كونغ (HKID).
ms.openlocfilehash: 6d382d50334036aaa0a7ff8fce698246b1e5ccb0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944713"
---
# <a name="hong-kong-identity-card-hkid-number"></a>رقم بطاقة هوية هونغ كونغ (HKID)

## <a name="format"></a>تنسيق

تركيبة من 8-9 أحرف وأرقام بالإضافة إلى أقواس اختيارية حول الحرف النهائي

## <a name="pattern"></a>نمط

تركيبة من 8-9 أحرف:

- 1-2 حرف (غير حساس لحالة الأحرف)
- ستة أرقام
- مساحة اختيارية
- حرف اختيار (أي رقم أو الحرف A) المضمن اختياريا بين أقواس

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة متوسطة بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_hong_kong_id_card` عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_hong_kong_id_card` .
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_hong_kong_id_card` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Hong Kong Identity Card (HKID) number -->
<Entity id="e63c28a7-ad29-4c17-a41a-3d2a0b70fd9c" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_hong_kong_id_card"/>
     <Match idRef="Keyword_hong_kong_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Func_hong_kong_id_card"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- بطاقة هوية هونغ كونغ
- HKIDC
- بطاقة المعرف
- بطاقة هوية
- بطاقة هوية hk
- معرف هونغ كونغ
- 香港身份證
- 香港永久性居民身份證
- 身份證
- 身份証
- 身分證
- 身分証
- 香港身份証
- 香港身分證
- 香港身分証
- 香港身份證
- 香港居民身份證
- 香港居民身份証
- 香港居民身分證
- 香港居民身分証
- 香港永久性居民身份証
- 香港永久性居民身分證
- 香港永久性居民身分証
- 香港永久性居民身份證
- 香港非永久性居民身份證
- 香港非永久性居民身份証
- 香港非永久性居民身分證
- 香港非永久性居民身分証
- 香港特別行政區永久性居民身份證
- 香港特別行政區永久性居民身份証
- 香港特別行政區永久性居民身分證
- 香港特別行政區永久性居民身分証
- 香港特別行政區非永久性居民身份證
- 香港特別行政區非永久性居民身份証
- 香港特別行政區非永久性居民身分證
- 香港特別行政區非永久性居民身分証