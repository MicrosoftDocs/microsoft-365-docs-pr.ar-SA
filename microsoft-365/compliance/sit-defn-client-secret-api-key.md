---
title: تعريف كيان مفتاح مفتاح العميل / سر واجهة برمجة التطبيقات (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح العميل / مفتاح واجهة برمجة التطبيقات.
ms.openlocfilehash: 25bd50de2193abaa926d09475cc9ff537432fc62
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988295"
---
# <a name="client-secret--api-key-preview"></a>سر العميل / مفتاح واجهة برمجة التطبيقات (معاينة)

## <a name="format"></a>تنسيق

سر عميل أو رمز مميز للتحديث المستخدم في بروتوكول OAuth 2.0.

او

مجموعة مكونة من 24 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

تركيبة مكونة من 32 حرفا تتكون من أحرف وأرقام.

او

مجموعة مكونة من 40 حرفا تتكون من أحرف وأرقام.

او

مجموعة مكونة من 44 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

تركيبة مكونة من 56 حرفا تتكون من أحرف وأرقام وأحرف خاصة

او

مجموعة مكونة من 88 حرفا تتكون من أحرف وأرقام وأحرف خاصة.


## <a name="pattern"></a>نمط

تنسيقات الرموز المميزة المختلفة لسرية العميل أو تحديثه على سبيل المثال:
 
`ClientSecret:********` <br>
`AppSecret=********` <br>
`ConsumerKey:=********` <br>
`Refresh_Token:********` <br>

او

تركيبة مكونة من 22 حرفا:
 
- a-z (غير حساس لحالة الأحرف)
- أرقام أو خطوط مائلة للأمام أو علامات الجمع
- ينتهي بعلامةي التساوي (=)

على سبيل المثال:

`abcdefgh0123456789/+AB==`

او

تركيبة مكونة من 32 حرفا:

- a-f أو A-F (حساس لحالة الأحرف)
- أو 0-9

على سبيل المثال:

`abcdef0123456789abcdef0123456789`

او

تركيبة مكونة من 40 حرفا:

- a-f أو A-F (حساس لحالة الأحرف)

او

- 0-9

على سبيل المثال:

`abcdef0123456789abcdef0123456789abcdef01`

او

تركيبة مكونة من 43 حرفا:
 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- ينتهي بعلامة التساوي (=)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

او

تركيبة مكونة من 54 حرفا:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/) أو علامات الجمع (+)
- ينتهي بعلامةي التساوي (==)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEFGHIJKLMNOP==`

او

تركيبة مكونة من 86 حرفا:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/) أو علامات الجمع (+)
- ينتهي بعلامةي التساوي (=)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`


## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المعروفة فقط [بتطبيق OAuth وخادم التخويل لتبادل](/azure/active-directory/develop/active-directory-how-applications-are-added) رمز مميز للوصول في وقت التشغيل. 

ويستخدم العديد من الموارد الأساسية:

- أنماط سياق العميل السري.
- أنماط Base64 المشفرة بمفتاح متماثل 128 بت.
- أنماط سداسية مرمزة بمفتاح متماثل 128 بت.
- أنماط سداسية مرمزة بمفتاح متماثل 160 بت.
- أنماط مفتاح 256 بت المتماثل المشفر ل Base64.
- أنماط مفتاح 320 بت المتماثل المشفر ل Base64.
- أنماط Base64 المشفرة بمفتاح متماثل 512 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName و Id و AccountName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_clientsecretcontext"></a>Keyword_ClientSecretContext:

- السريه
- الرمز المميز
- المصادقه
- سلسلة آمنة
- مفتاح

### <a name="keyword_symmetrickey128"></a>Keyword_SymmetricKey128:

- السريه
- مفتاح
- كلمه المرور
- الاسبق

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex:

- dapi
- مفتاح
- السريه
- الرمز المميز
- كلمه المرور
- الاسبق

### <a name="keyword_symmetrickey160hex"></a>Keyword_SymmetricKey160Hex:

- الرمز المميز

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256:

- SharedAccessKey
- مفتاح الحساب

### <a name="keyword_symmetrickey320"></a>Keyword_SymmetricKey320:

- التعليمات البرمجية=
- مفتاح

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512:

- SharedAccessKey
- مفتاح الحساب
