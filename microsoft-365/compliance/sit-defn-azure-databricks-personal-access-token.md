---
title: تعريف كيان رمز الوصول الشخصي في Azure Databricks (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لرمز الوصول الشخصي الخاص ب Azure Databricks.
ms.openlocfilehash: 9dfe6cb2616cc389cd122b4430c717bd099900f0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944355"
---
# <a name="azure-databricks-personal-access-token-preview"></a>الرمز المميز للوصول الشخصي إلى Azure Databricks (معاينة) 

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

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للمصادقة إلى [Azure Databricks REST API](/azure/databricks/administration-guide/access-control/tokens). 

ويستخدم العديد من الموارد الأساسية:

- أنماط سداسية مرمزة بمفتاح متماثل 128 بت.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.


## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex:

كلمة مرور الرمز المميز السري لمفتاح dapi pw
