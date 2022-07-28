---
title: تعريف كيان كلمة المرور العامة (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لكلمة المرور العامة.
ms.openlocfilehash: ea800d6798a2068eb90ff02e1550e48606e7b1ea
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944250"
---
# <a name="general-password-preview"></a>كلمة المرور العامة (معاينة)

## <a name="format"></a>تنسيق

مجموعة تصل إلى 20000 حرف من الأحرف والأرقام والأحرف الخاصة.

او

بيانات اعتماد تسجيل الدخول المستخدمة في سطور الأوامر

او

كلمة مرور النص العادي المستخدمة في قصاصات برمجية

او

كلمة مرور النص العادي المستخدمة في البرنامج النصي

او

كلمة مرور النص العادي المستخدمة في تكوين XML

او

مجموعة مكونة من 24 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

تركيبة مكونة من 32 حرفا تتكون من أحرف وأرقام.

او

مجموعة مكونة من 32 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

مجموعة مكونة من 44 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

مجموعة مكونة من 88 حرفا من الأحرف والأرقام والأحرف الخاصة.

## <a name="pattern"></a>نمط

أي تركيبة تصل إلى 20,000 حرف تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/) أو علامات الجمع (+)
- ما يصل إلى اثنين من علامات التساوي (=)

على سبيل المثال:

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

او

تنسيقات بيانات اعتماد تسجيل الدخول المختلفة لسطر الأوامر، على سبيل المثال: 

`-u username:********`

او

`-u username -p ********`

او

`/f ... /p ********`

او

`-Password ********`

او

`-U username%********`

او

`-secrets:********`

على سبيل المثال:

`zDbg.DataPuller.exe -secrets:eyJ`

او

تنسيقات كلمات المرور المختلفة في قصاصات برمجية، على سبيل المثال:

`new X509Certificates2(`

او

`ConvertTo-SecureString -String ********`

او

`password = "********"`

او

`"password" : "********"`

او

`UserPasswordCredential(`

على سبيل المثال:

`password = "ZYXWVU_1";`

او

تنسيقات كلمات المرور المختلفة في البرنامج النصي، على سبيل المثال:

`password = ********`

على سبيل المثال:

`password=ZYXWVU_1`

او

تنسيقات كلمات المرور المختلفة في XML، على سبيل المثال:

```xml
<secret>********</secret>
<password>********</password>
<setting name="password" value="********" >
<setting name="password">********</setting>
<setting name="password"><value>********</value></setting>
```

على سبيل المثال:

`<secret>ZYXWVU_1</secret>`

او

أي تركيبة مكونة من 22 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- أرقام أو خطوط مائلة للأمام أو علامات الجمع
- ينتهي بعلامةي التساوي (=)

على سبيل المثال:

`abcdefgh0123456789/+AB==`

او

أي تركيبة مكونة من 32 حرفا تتكون من:

- a-f أو A-F (حساس لحالة الأحرف) أو 0-9

على سبيل المثال:

`abcdef0123456789abcdef0123456789`

او

أي تركيبة مكونة من 32 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/) أو علامات الجمع (+)

على سبيل المثال:

`abcdefghijklmnopqr0123456789/+AB`

او

أي تركيبة مكونة من 43 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/) أو علامات الجمع (+)
- ينتهي بعلامة التساوي (=)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

او

أي تركيبة مكونة من 86 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/) أو علامات الجمع (+)
- ينتهي بعلامةي التساوي (=)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="description"></a>الوصف

تم تصميم SIT هذا لمطابقة معلومات الأمان مثل أسماء المستخدمين وكلمات المرور المستخدمة في [عملية تسجيل الدخول العامة لعملية تسجيل دخول المستخدم](/azure/key-vault/quick-create-portal). ويستخدم العديد من الموارد الأساسية:

- أنماط سلسلة Base64 المشفرة الحرفية.
- أنماط سياق كلمة المرور في سطر الأوامر.
- أنماط سياق كلمة المرور في التعليمات البرمجية.
- أنماط سياق كلمة المرور في البرنامج النصي.
- أنماط سياق كلمة المرور في XML.
- أنماط مفتاح 128 بت المتماثل المشفر ل Base64.
- أنماط سداسية مرمزة بمفتاح متماثل 128 بت.
- أنماط Base64 المشفرة بمفتاح متماثل 192 بت.
- أنماط مفتاح 256 بت المتماثل المشفر ل Base64.
- أنماط Base64 المشفرة بمفتاح متماثل 512 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName و ID و AccountName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس الكلمات المفردة.


تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral

- الوزاره

### <a name="keyword_passwordcontextincmdline"></a>Keyword_PasswordContextInCmdLine

- certutil
- zdbg
- السريه
- VSTS_TOKEN
- حليقه
- PowerShell
- ps1
- -u
- Smc
- Autologon
- Ldifde
- رنين
- --env
- SignTool
- winexe
- صافي

## <a name="keyword_passwordcontextincode"></a>Keyword_PasswordContextInCode

- مفتاح
- x509c
- بيانات الاعتماد
- كلمه المرور
- الاسبق
- سلسلة آمنة

### <a name="keyword_passwordcontextinscript"></a>Keyword_PasswordContextInScript

- السريه
- كلمه المرور
- الاسبق

### <a name="keyword_passwordcontextinxml"></a>Keyword_PasswordContextInXml

- userpass
- كلمه المرور
- الاسبق
- Connectionstring
- مفتاح
- بيانات الاعتماد
- الرمز المميز
- ساس
- السريه

### <a name="keyword_symmetrickey128"></a>Keyword_SymmetricKey128

- السريه
- مفتاح
- كلمه المرور
- الاسبق

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex

- dapi
- مفتاح
- السريه
- الرمز المميز
- كلمه المرور
- الاسبق

### <a name="keyword_symmetrickey192"></a>Keyword_SymmetricKey192

- كلمه المرور
- -p
- azurecr

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256

- SharedAccessKey
- مفتاح الحساب

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512

- SharedAccessKey
- مفتاح الحساب
