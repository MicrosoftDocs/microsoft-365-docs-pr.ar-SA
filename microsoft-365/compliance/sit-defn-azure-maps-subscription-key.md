---
title: تعريف كيان مفتاح الاشتراك خرائط Azure (معاينة)
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
description: خرائط Azure تعريف كيان نوع المعلومات الحساسة لمفتاح الاشتراك.
ms.openlocfilehash: f1ebfe0018fac9bd792dc102df39bb0aada84fdf
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944339"
---
# <a name="azure-maps-subscription-key-preview"></a>مفتاح اشتراك خرائط Azure (معاينة)

## <a name="format"></a>تنسيق

مجموعة مكونة من 43 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

أي تركيبة مكونة من 43 حرفا تتكون من:
 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرط (-)
- أو تسطير (_)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789-_ABCDE`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للوصول إلى الموارد في [حسابات خرائط Azure](/azure/azure-maps/how-to-manage-authentication). 

ويستخدم العديد من الموارد الأساسية:

- أنماط عنوان URL Base64 المرمز بمفتاح متماثل 256 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey256url"></a>Keyword_SymmetricKey256Url:

- مفتاح
- microsoft.maps
