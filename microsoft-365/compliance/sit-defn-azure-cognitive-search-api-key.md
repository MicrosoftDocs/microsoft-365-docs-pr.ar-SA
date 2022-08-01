---
title: تعريف كيان مفتاح واجهة برمجة تطبيقات البحث المعرفي من Azure (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح واجهة برمجة تطبيقات البحث المعرفي من Azure.
ms.openlocfilehash: 8d4b5ca6c968468c5d084e6adb44eaf921553e21
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944363"
---
# <a name="azure-cognitive-search-api-key-preview"></a>مفتاح واجهة برمجة تطبيقات البحث المعرفي من Azure (معاينة) 

## <a name="format"></a>تنسيق

تركيبة مكونة من 32 حرفا تتكون من أحرف وأرقام.

## <a name="pattern"></a>نمط

تركيبة مكونة من 32 حرفا تتكون من:

- a-f أو A-F (حساس لحالة الأحرف)
- أو 0-9

على سبيل المثال:

`abcdef0123456789abcdef0123456789`


## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لمصادقة الطلبات الواردة إلى [واجهات برمجة تطبيقات البحث المعرفي من Azure.](/azure/search/search-security-api-keys) 

ويستخدم العديد من الموارد الأساسية:

أنماط سداسية مرمزة بمفتاح متماثل 128 بت.
أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex:

- dapi
- مفتاح
- السريه
- الرمز المميز
- كلمه المرور
- الاسبق
