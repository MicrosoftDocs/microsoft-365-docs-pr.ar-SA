---
title: تعريف كيان مفتاح واجهة برمجة تطبيقات Google (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح واجهة برمجة تطبيقات Google.
ms.openlocfilehash: 5aef61e28dee6624620d1f254434fb860f28f1af
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944465"
---
# <a name="google-api-key-preview"></a>مفتاح واجهة برمجة تطبيقات Google (معاينة)

## <a name="format"></a>تنسيق

مجموعة مكونة من 39 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

بادئة الرمز المميز (حساسة لحالة الأحرف) "أيزا"

تركيبة مكونة من 35 حرفا:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرط (-)
- تسطير (_) أو خطوط مائلة للخلف (\)

على سبيل المثال:

`AIzaefgh0123456789_-ABCDEFGHIJKLMNOPQRS`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة كسلسلة مشفرة بسيطة تحدد [عميل واجهة برمجة تطبيقات Google REST](https://cloud.google.com/docs/authentication/api-keys) دون أي كيان يستخدم لربط طلبات واجهة برمجة التطبيقات بمشروعك للحصة النسبية والفوترة. 

ويستخدم العديد من الموارد الأساسية:

- أنماط Base64 المشفرة بمفتاح متماثل 210 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey210"></a>Keyword_SymmetricKey210:

- أيزا
