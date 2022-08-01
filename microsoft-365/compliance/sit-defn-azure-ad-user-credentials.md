---
title: تعريف كيان بيانات اعتماد المستخدم Azure AD (معاينة)
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
description: Azure AD تعريف كيان نوع المعلومات الحساسة لبيانات اعتماد المستخدم.
ms.openlocfilehash: 5b27f2a5c700770df65be74f0cebb23351de77bc
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944376"
---
# <a name="azure-ad-user-credentials-preview"></a>بيانات اعتماد المستخدم Azure AD (معاينة)

## <a name="format"></a>تنسيق

اسم مستخدم مقترن وكلمة مرور مرتبطة بمجال *.onmicrosoft.com.

او

كلمة مرور النص العادي المستخدمة في قصاصات التعليمات البرمجية.

او

كلمة مرور النص العادي المستخدمة في تكوين XML.

## <a name="pattern"></a>نمط

تنسيقات اسم المستخدم وكلمة المرور المختلفة، على سبيل المثال:

`username=...password=********` <br>
`/user:.../pass:********` <br>
`SharePointOnlineAuthenticatedContext` <br>
`sign_in`<br>


او

تنسيقات كلمات المرور المختلفة في قصاصات برمجية، على سبيل المثال:

`new X509Certificates2( ...` <br>
`ConvertTo-SecureString -String ********...`<br>
`password = "********"...` <br>
`"password" : "********"...` <br>
`UserPasswordCredential( ...` <br>

او

تنسيقات كلمات المرور المختلفة في XML، على سبيل المثال:


```xml
... <secret>********</secret> ...
... <password>********</password> ...
... <setting name="password" value="********" > ... 
... <setting name="password">********</setting> ... 
... <setting name="password"><value>********</value></setting> ... 
```


## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة كلمات مرور مستخدم فردية للمصادقة مقابل [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-reset-password-azure-portal). 

ويستخدم العديد من الموارد الأساسية:

- أنماط اسم المستخدم وكلمة المرور للنص العادي لمستأجر Azure AD.
- أنماط سياق كلمة المرور في التعليمات البرمجية.
- أنماط سياق كلمة المرور في XML.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.


## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_azureactivedirectorylogincredentials"></a>Keyword_AzureActiveDirectoryLoginCredentials:

- كلمه المرور
- الاسبق
- userpass
- وثائق التفويض
- cmdkey
- أوثينتي
- sign_in

### <a name="keyword_passwordcontextincode"></a>Keyword_PasswordContextInCode:

- مفتاح
- x509c
- بيانات الاعتماد
- كلمه المرور
- الاسبق
- سلسلة آمنة

### <a name="keyword_passwordcontextinxml"></a>Keyword_PasswordContextInXml:

- userpass
- كلمه المرور
- الاسبق
- Connectionstring
- مفتاح
- بيانات الاعتماد
- الرمز المميز
- ساس
- السريه

