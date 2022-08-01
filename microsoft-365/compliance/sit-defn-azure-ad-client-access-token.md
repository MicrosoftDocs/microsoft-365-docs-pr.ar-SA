---
title: تعريف كيان الرمز المميز للوصول Azure AD العميل (معاينة)
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
description: Azure AD تعريف كيان نوع المعلومات الحساسة للرمز المميز للوصول إلى العميل.
ms.openlocfilehash: a59848511cde3778c373f55c18e794e81db1f80e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944380"
---
# <a name="azure-ad-client-access-token-preview"></a>Azure AD رمز وصول العميل (معاينة)

## <a name="format"></a>تنسيق

تركيبة تصل إلى 10000 حرف تتكون من أحرف وأرقام وأحرف خاصة.

او

سر العميل أو رمز التحديث المميز المستخدم في بروتوكول OAuth2.0.

او

مزيج من ما يصل إلى 1000 حرف يتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

أي تركيبة من:
 
- حتى 10000 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- حتى 2
- علامات التساوي (=)

على سبيل المثال:

`"VersionProfile": null, "TokenCache": { "CacheData": 
"AgAAAAIAAACZAWh0dHBzOi8vbG9naW4ubWljcm9zb2`

او

تنسيقات الرمز المميز أو تحديث سر العميل المتغير، على سبيل المثال. <br> 
`ClientSecret:********` <br>
`AppSecret=********` <br>
`ConsumerKey:=********` <br>
`Refresh_Token:********` <br>

او

3 أحرف: eyJ (حساس لحالة الأحرف)

و

تركيبة تصل إلى 1000 حرف تتكون من

- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرط (-)
- تسطير (_)
- أو النقاط (.)

على سبيل المثال:

`eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Ing0Nzh4eU9wbHNNMUg3TlhrN1N4MTd4MXVwYyIsImtpZCI6Ing0Nzh4`



## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان التي تحتوي على مطالبات يمكن استخدامها في [Azure Active Directory B2C](/azure/active-directory-b2c/active-directory-b2c-access-tokens) (Azure AD B2C) لتحديد الأذونات الممنوحة لموارد Azure. 

ويستخدم العديد من الموارد الأساسية:

- أنماط Azure PowerShell Token Cache
- أنماط سياق بيانات العميل السرية
- أنماط Json Web Token
- أنماط CredentialName، CredentialFeatures، AccountIdentityName، AccountIdentityValue، ResourceType، ResourceName
- أنماط قيم النماذج المحاكاة، والتنقيات، و العناصر النائبة
- قاموس من المفردات

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.



## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickeycontextinxml"></a>Keyword_SymmetricKeyContextInXml:

- رمز مميز

### <a name="keyword_clientsecretcontext"></a>Keyword_ClientSecretContext:

- السريه
- الرمز المميز
- المصادقه
- سلسلة آمنة
- مفتاح

### <a name="keyword_jsonwebtoken"></a>Keyword_JsonWebToken:

- eyJ

