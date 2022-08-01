---
title: تعريف كيان توقيع الوصول المشترك لناقل خدمة Azure (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لتوقيع الوصول المشترك في ناقل خدمة Azure.
ms.openlocfilehash: f9464bb2700bc4e4e186d33e451a2b286acca54f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944415"
---
# <a name="azure-service-bus-shared-access-signature-preview"></a>توقيع الوصول المشترك لناقل خدمة Azure (معاينة)

## <a name="format"></a>تنسيق

مجموعة مكونة من 44 حرفا تتكون من أحرف وأرقام وأحرف خاصة تنتهي بعلامة يساوي (=) ليست جزءا من النمط.

او

تركيبة مكونة من ما يصل إلى 76 حرفا تتكون من أحرف وأرقام وأحرف خاصة تنتهي بعلامة يساوي (=) ليست جزءا من النمط.

## <a name="pattern"></a>نمط

أي تركيبة مكونة من 43 حرفا تتكون من:
 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- ينتهي بعلامة التساوي (=) التي ليست جزءا من النمط

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

او

أي تركيبة من 43 إلى 73 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- أو علامات النسبة المئوية (٪)
- ينتهي بلاحقة '٪3d' (غير حساسة لحالة الأحرف)

على سبيل المثال: 

`abcdefghijklmnopqrstuvwxyz0123456789%2F%2BABCDE%3D`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لمنح المستخدم حق الوصول إلى [موارد ناقل خدمة Azure](/azure/service-bus-messaging/service-bus-authentication-and-authorization) ذات حقوق محددة.

ويستخدم العديد من الموارد الأساسية:

- أنماط مفتاح 256 بت المتماثل المشفر ل Base64.
- أنماط مفتاح 256 بت المشفر ل URL المتماثل.
- أنماط CredentialName، CredentialFeatures، AccountIdentityName، AccountIdentityValue، ResourceType، ResourceName، المعرف.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256:

- SharedAccessKey
- مفتاح الحساب

### <a name="keyword_symmetrickey256urlencoded"></a>Keyword_SymmetricKey256UrlEncoded:

- sig=
- مفتاح
- الرمز المميز
- السريه
- كلمه المرور
