---
title: Azure AD تعريف الكيان السري للعميل (معاينة)
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
description: Azure AD تعريف كيان نوع المعلومات الحساسة السرية للعميل.
ms.openlocfilehash: ea597fc5493db6b6f919d907dcb61af115299ea1
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944378"
---
# <a name="azure-ad-client-secret-preview"></a>Azure AD سر العميل (معاينة)

## <a name="format"></a>تنسيق

تركيبة تصل إلى 40 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

تركيبة تصل إلى 40 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرط (-)
- تسطير (_)
- النقاط (.) 
- أو تشكيلات التلدة (~)

على سبيل المثال:

`abc7Q~defghijklmnopqrs0t123456789-_.~`

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لتأمين [أساسيات خدمة Azure Active Directory](/azure/active-directory/fundamentals/service-accounts-principal). 

ويستخدم العديد من الموارد الأساسية:

- أنماط سر العميل بتنسيق معين.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_appsecret"></a>Keyword_AppSecret:

- السريه
- كلمة المرور
- مفتاح

