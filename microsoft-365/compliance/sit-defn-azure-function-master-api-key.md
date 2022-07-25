---
title: تعريف كيان مفتاح Azure Function Master / API (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح Azure Function Master / API.
ms.openlocfilehash: 3a2fd12125d220bb0de3d0f4217ca6e11f58ea56
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988332"
---
# <a name="azure-function-master--api-key-preview"></a>مفتاح Azure Function Master / API (معاينة)  

## <a name="format"></a>تنسيق

مجموعة مكونة من 56 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

او

تركيبة تصل إلى 90 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

أي تركيبة مكونة من 54 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- ينتهي بعلامةي التساوي (=)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEFGHIJKLMNOP==`

او

مجموعة من 54 إلى 84 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- أو علامات النسبة المئوية (٪)
- ينتهي بلاحقة '٪3d٪3d' (غير حساسة لحالة الأحرف)

على سبيل المثال:

abcdefghijklmnopqrstuvwxyz0123456789٪2F٪2BABCDEF0123456789٪3D٪3D


## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لطلب [واجهة برمجة تطبيقات Azure Function](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=portal) عند تعيين مستوى التخويل الخاص بها بقيمة أخرى غير المجهولة. 

ويستخدم العديد من الموارد الأساسية:

- أنماط مفتاح 320 بت المتماثل المشفر ل Base64.
- أنماط مفتاح 320 بت المشفر ل URL المتماثل.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.


## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey320"></a>Keyword_SymmetricKey320:

- التعليمات البرمجية=
- مفتاح

### <a name="keyword_symmetrickey320urlencoded"></a>Keyword_SymmetricKey320UrlEncoded:

- التعليمات البرمجية=
- مفتاح
