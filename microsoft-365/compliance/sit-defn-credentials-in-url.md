---
title: Crednetial في URL
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
description: بيانات الاعتماد في تعريف كيان نوع المعلومات الحساسة ل URL.
ms.openlocfilehash: f7a363539ec9bdd7fa0ddaab30ac7e2d20afb69b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944451"
---
# <a name="credentials-in-url"></a>بيانات الاعتماد في URL

## <a name="format"></a>تنسيق

اسم المستخدم المقترن وكلمة المرور المستخدمة في URL

او

كلمة مرور النص العادي المستخدمة في البرنامج النصي

## <a name="pattern"></a>نمط

تنسيقات اسم المستخدم وكلمة المرور المختلفة ل URL، على سبيل المثال: 

`https://username:********@contoso.com/...`
`ftp://username:********@contoso.com:20/...`

على سبيل المثال: `https://myuser:mypassword@localhost`

او

تنسيقات كلمات المرور المختلفة في البرنامج النصي، على سبيل المثال: 

`password = ********...`

على سبيل المثال:

`password=ZYXWVU_1`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="description"></a>الوصف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة كرمز مميز في URL لإجراء عملية التحقق من صحة العميل أو [تسجيل دخول المستخدم](/azure/key-vault/quick-create-portal) التعريفي. ويستخدم العديد من الموارد الأساسية:

- أنماط بيانات اعتماد تسجيل دخول المستخدم في عنوان URL.
- أنماط سياق كلمة المرور في البرنامج النصي.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_logincredentialsinurl"></a>Keyword_LoginCredentialsInUrl

- ://

### <a name="keyword_passwordcontextinscript"></a>Keyword_PasswordContextInScript

- السريه
- كلمه المرور
- الاسبق
