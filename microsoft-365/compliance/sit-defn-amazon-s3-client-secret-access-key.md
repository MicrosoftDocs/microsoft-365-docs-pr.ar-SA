---
title: تعريف كيان مفتاح الوصول السري لعميل Amazon S3 (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح الوصول السري لعميل Amazon S3.
ms.openlocfilehash: c3026beae856097e221063732f65b805a3fd05c2
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944320"
---
# <a name="amazon-s3-client-secret-access-key-preview"></a>مفتاح الوصول السري لعميل Amazon S3 (معاينة)

## <a name="format"></a>تنسيق

مجموعة مكونة من 40 حرفا تتكون من أحرف وأرقام وأحرف خاصة. 

## <a name="pattern"></a>نمط

رقم مكون من 13 رقما:

تركيبة مكونة من 40 حرفا تتكون من: 

- a-z (غير حساس لحالة الأحرف) 
- 0-9 
- شرطة مائلة للأمام (/) أو علامة الجمع (+) 

على سبيل المثال: 

`abcdefghijklmnopqrst0123456789/+ABCDEFGH`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للوصول إلى [Amazon Web Services.](/toolkit-for-eclipse/v1/user-guide/setup-credentials.html)


ويستخدم العديد من الموارد الأساسية: 
 
- أنماط مفتاح 240 بت المتماثل المشفر ل Base64. 
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName. 
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب. 
- قاموس الكلمات المفردة.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية. 

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey240"></a>Keyword_SymmetricKey240: 

- السريه 
- مفتاح 