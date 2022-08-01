---
title: تعريف كيان بيانات اعتماد تسجيل دخول المستخدم (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لبيانات اعتماد تسجيل دخول المستخدم.
ms.openlocfilehash: d75fcb7069e8393b5b03ce08071057ff503a4bfb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944251"
---
# <a name="user-login-credentials-preview"></a>بيانات اعتماد تسجيل دخول المستخدم (معاينة)

## <a name="format"></a>تنسيق

اسم مستخدم مقترن وكلمة مرور مستخدمان في عملية المصادقة العامة.

او

اسم مستخدم مقترن وكلمة مرور مستخدمان في إدارة اتصال PuTTY.

او

كلمة مرور النص العادي المستخدمة في قصاصات برمجية.

او

مجموعة مكونة من 88 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

تنسيقات اسم المستخدم وكلمة المرور المختلفة، على سبيل المثال:
 
`username=...;password=********;` <br>
`user id=...;password=********;` <br>
`uid=...;pwd=********;` <br>
`DB_USER=...;DB_PASS=********;` <br>
`Service Account=...;Password=********;` <br>

او

```xml
An XML element <login>
An embeded XML element <login>
Inner XML content
An embeded XML element </login>
An embeded XML element <password>
Inner XML content
An embeded XML element </password>
An XML element </login>
```

على سبيل المثال

`<login> <login>ZYXWVU_1</login> <password>ZY…`

او

تنسيقات كلمات المرور المختلفة في قصاصات برمجية، على سبيل المثال:

`new X509Certificates2(` <br>
`ConvertTo-SecureString -String ********` <br>
`password = "********"` <br>
`"password" : "********"`<br>
`UserPasswordCredential(` <br>

او

تركيبة مكونة من 86 حرفا:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- ينتهي بعلامةي التساوي (=)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة في [عملية تسجيل دخول المستخدم](/azure/key-vault/quick-create-portal) العامة. 

ويستخدم العديد من الموارد الأساسية:

- أنماط اسم المستخدم وكلمة المرور ذات النص العادي.
- أنماط اسم المستخدم وكلمة المرور ذات النص العادي في ملف قاعدة بيانات PuTTYcm.
- أنماط سياق كلمة المرور في التعليمات البرمجية.
- أنماط Base64 المشفرة بمفتاح متماثل 512 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName و Id و AccountName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_logincredentials"></a>Keyword_LoginCredentials:

- كلمه المرور
- الاسبق
- DB_

### <a name="keyword_logincredentialsputty"></a>Keyword_LoginCredentialsPutty:

- تسجيل الدخول

### <a name="keyword_passwordcontextincode"></a>Keyword_PasswordContextInCode:

- مفتاح
- x509c
- بيانات الاعتماد
- كلمه المرور
- الاسبق
- سلسلة آمنة

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512:

- SharedAccessKey
- مفتاح الحساب
