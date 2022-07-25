---
title: Microsoft Bing يعين تعريف الكيان الرئيسي (معاينة)
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
description: يعين Microsoft Bing تعريف كيان نوع المعلومات الحساسة الرئيسية.
ms.openlocfilehash: 6f25ec9716be33a0e2bbe404f12742dddad89250
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988347"
---
# <a name="microsoft-bing-maps-key-preview"></a>مفتاح خرائط Microsoft Bing (معاينة)

## <a name="format"></a>تنسيق

مجموعة مكونة من 64 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

تركيبة مكونة من 64 حرفا:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- تسطير (_) أو واصلات (-)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789-_ABCDEabcdefghijklmnopqrstu`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لاستدعاء [واجهة برمجة تطبيقات خرائط Bing.](/bingmaps/getting-started/bing-maps-dev-center-help/getting-a-bing-maps-key) 

ويستخدم العديد من الموارد الأساسية:

- أنماط عنوان URL Base64 المشفر بمفتاح متماثل 384 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey384url"></a>Keyword_SymmetricKey384Url:

- الواجهة الظاهرية
- واجهة برمجة التطبيقات/الخرائط
- مفتاح
