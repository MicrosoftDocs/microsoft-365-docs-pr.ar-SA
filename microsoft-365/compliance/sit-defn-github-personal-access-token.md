---
title: تعريف كيان رمز الوصول الشخصي GitHub (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لرمز الوصول الشخصي GitHub.
ms.openlocfilehash: e1da4eaf09ef480ad29928d8066dc91612cf779e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944472"
---
# <a name="github-personal-access-token-preview"></a>الرمز المميز للوصول الشخصي إلى GitHub (معاينة)

## <a name="format"></a>تنسيق

مجموعة مكونة من 40 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

اسم المستخدم المقترن وكلمة المرور المستخدمة في URL.

او

مجموعة مكونة من 40 حرفا تتكون من أحرف وأرقام.

## <a name="pattern"></a>نمط

- بادئة الرمز المميز (حساسة لحالة الأحرف) 'ghp_' أو 'gho_' أو 'ghu_' أو 'ghs_' أو 'ghr_'
- أي تركيبة من 36 
- a-z (غير حساس لحالة الأحرف) أو 0-9

على سبيل المثال:

`ghp_abcdefghijklmnopqrstuvwxyzABCD012345`

او

تنسيقات اسم المستخدم وكلمة المرور المختلفة ل URL على سبيل المثال:
 
`https://username:********@contoso.com/` <br>

`ftp://username:********@contoso.com:20/`<br>


او

تركيبة مكونة من 40 حرفا:

- a-f أو A-F (حساس لحالة الأحرف) أو 0-9

على سبيل المثال:

`abcdef0123456789abcdef0123456789abcdef01`

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة ككلمة مرور بديلة للمصادقة إلى GitHub عند استخدام [واجهة برمجة تطبيقات GitHub أو سطر الأوامر](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token). 

ويستخدم العديد من الموارد الأساسية:

- أنماط GitHub PAT القابلة للتحديث.
- أنماط بيانات اعتماد تسجيل دخول المستخدم في عنوان URL.
- أنماط سداسية مرمزة بمفتاح متماثل 160 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_githubpatidentifiablesecret"></a>Keyword_GitHubPatIdentifiableSecret:

- gh_

### <a name="keyword_logincredentialsinurl"></a>Keyword_LoginCredentialsInUrl:

- ://

### <a name="keyword_symmetrickey160hex"></a>Keyword_SymmetricKey160Hex:

- الرمز المميز
