---
title: تعريف كيان المفتاح السري ل Azure Bot Framework (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح Azure Bot Framework السري.
ms.openlocfilehash: c436436b00dda8a5273939665920ef709ff164c5
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944366"
---
# <a name="azure-bot-framework-secret-key-preview"></a>المفتاح السري ل Azure Bot Framework (معاينة)

## <a name="format"></a>تنسيق

مجموعة مكونة من 55 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

مجموعة مكونة من 63 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

تركيبة مكونة من 55 حرفا:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- تسطير (_)
- أو النقاط (.)


`abcdefghijklmnopqrstuvwxyz.0123456789_ABCDEabcdefghijkl`

أو للأحرف ال 63

تركيبة مكونة من 11 حرفا:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرط (-)
- أو تسطير (_)
- نقطة

تركيبة مكونة من 3 أحرف:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرط (-)
- أو تسطير (_)
- نقطة

تركيبة مكونة من 3 أحرف:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرط (-)
- أو تسطير (_)
- نقطة

تركيبة مكونة من 43 حرفا

- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرط (-)
- أو تسطير (_)

على سبيل المثال:

`abcdefghijk.lmn.opq.rstuvwxyz0123456789-_ABCDEFGHIJKLMNOPQRSTUV`


## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للاتصال [بقنوات WebChat من خدمات Azure Bot.](/azure/bot-service/bot-service-channel-connect-webchat?view=azure-bot-service-4.0) 

ويستخدم العديد من الموارد الأساسية:

- أنماط عنوان URL Base64 المرمز بمفتاح متماثل 328 بت.
- أنماط عنوان URL Base64 المرمز بمفتاح متماثل 360 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey328url"></a>Keyword_SymmetricKey328Url:

- botframework
- مفتاح

### <a name="keyword_symmetrickey360url"></a>Keyword_SymmetricKey360Url:

- botframework
- مفتاح
