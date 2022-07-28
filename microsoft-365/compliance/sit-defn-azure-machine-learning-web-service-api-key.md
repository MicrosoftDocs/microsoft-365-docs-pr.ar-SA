---
title: تعريف كيان مفتاح واجهة برمجة تطبيقات خدمة التعلم الآلي من Azure (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح واجهة برمجة تطبيقات خدمة التعلم الآلي من Azure.
ms.openlocfilehash: 99c99425fcba49f59adf7dcaf1baba88e13f0118
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944345"
---
# <a name="azure-machine-learning-web-service-api-key-preview"></a>مفتاح واجهة برمجة تطبيقات خدمة التعلم الآلي من Azure (معاينة) 

## <a name="format"></a>تنسيق

مجموعة مكونة من 88 حرفا تتكون من أحرف وأرقام وأحرف خاصة تنتهي بعلامةين متساويتين (==).

## <a name="pattern"></a>نمط

أي تركيبة مكونة من 86 حرفا:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للاتصال [بخدمات Azure Machine Learning Web](/azure/machine-learning/classic/consume-web-services). 

ويستخدم العديد من الموارد الأساسية:

- أنماط Base64 المشفرة بمفتاح متماثل 512 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName و Id و AccountName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512:

- SharedAccessKey
- مفتاح الحساب
