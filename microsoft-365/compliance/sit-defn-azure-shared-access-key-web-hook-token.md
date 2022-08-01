---
title: تعريف كيان توقيع الرمز المميز ل Azure Shared Access / Web Hook (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح Azure Shared Access / رمز Web Hook المميز.
ms.openlocfilehash: 0ddb9585ba5bcec36785be8f722c484517254af0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944439"
---
# <a name="azure-shared-access-key--web-hook-token-preview"></a>مفتاح Azure Shared Access / رمز Web Hook المميز (معاينة) 

## <a name="format"></a>تنسيق

مجموعة مكونة من 44 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

تركيبة تصل إلى 76 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

أي تركيبة مكونة من 43 حرفا تتكون من:
 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- ينتهي بعلامة التساوي (=)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

او

مجموعة من 43 إلى 73 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- علامات النسبة المئوية (٪)
- ينتهي بلاحقة '٪3d' (غير حساسة لحالة الأحرف)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789%2F%2BABCDE%3D`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للوصول إلى [موارد Azure العامة ذات الإذن المقيد](/azure/notification-hubs/notification-hubs-push-notification-security). 

ويستخدم العديد من الموارد الأساسية:

- أنماط مفتاح 256 بت المتماثل المشفر ل Base64.
- أنماط مفتاح 256 بت المشفر ل URL المتماثل.
- أنماط CredentialName، CredentialFeatures، AccountIdentityName، AccountIdentityValue، ResourceType، ResourceName، المعرف.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات

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
