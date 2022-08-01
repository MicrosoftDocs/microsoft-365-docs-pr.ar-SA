---
title: تعريف وحدة كلمة مرور سلسلة اتصال ذاكرة التخزين المؤقت ل Azure Redis (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لسلسلة اتصال ذاكرة التخزين المؤقت ل Azure Redis.
ms.openlocfilehash: 04d79512c7740401e81ba5089b57734d7f8f1961
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944336"
---
# <a name="azure-redis-cache-connection-string-password-preview"></a>كلمة مرور سلسلة اتصال ذاكرة التخزين المؤقت ل Azure Redis (معاينة)

## <a name="format"></a>تنسيق

تركيبة مكونة من ما يصل إلى 20000 حرف تتكون من أحرف وأرقام وأحرف خاصة.

او

مجموعة مكونة من 44 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

أي تركيبة تصل إلى 20,000 حرف تتكون من: 
 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- حتى 2
- علامات التساوي (=)

على سبيل المثال: 

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

او

أي تركيبة مكونة من 43 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- ينتهي بعلامة التساوي (=)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للاتصال [بذاكرة التخزين المؤقت Azure لخوادم Redis](/azure/azure-cache-for-redis/). 

ويستخدم العديد من الموارد الأساسية:

- أنماط سلسلة Base64 المشفرة الحرفية.
- أنماط مفتاح 256 بت المتماثل المشفر ل Base64.
- أنماط CredentialName، CredentialFeatures، AccountIdentityName، AccountIdentityValue، ResourceType، ResourceName، المعرف.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral:

- الوزاره

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256:

- SharedAccessKey
- مفتاح الحساب
