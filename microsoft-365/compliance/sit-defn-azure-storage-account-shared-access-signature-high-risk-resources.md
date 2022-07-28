---
title: توقيع الوصول المشترك لحساب Azure Storage لتعريف كيان الموارد عالية المخاطر (معاينة)
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
description: توقيع الوصول المشترك لحساب تخزين Azure لتعريف كيان نوع المعلومات الحساسة للموارد عالية المخاطر.
ms.openlocfilehash: 007016f38f0aa6409cd81c317653cb0acc71a881
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944409"
---
# <a name="azure-storage-account-shared-access-signature-for-high-risk-resources-preview"></a>توقيع الوصول المشترك لحساب تخزين Azure للموارد عالية المخاطر (معاينة)

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

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لمنح حقوق الوصول المقيدة لموارد [Azure Storage عالية المخاطر مثل الشهادات أو التكوينات أو حزم النشر](/rest/api/storageservices/delegate-access-with-shared-access-signature). 

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
