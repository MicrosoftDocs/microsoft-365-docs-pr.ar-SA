---
title: تعريف كيان مفتاح الوصول إلى Azure SignalR (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح الوصول إلى Azure SignalR.
ms.openlocfilehash: 0fab0ddee4052654d3b802f0df41e65825d9ff50
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944413"
---
# <a name="azure-signalr-access-key-preview"></a>مفتاح الوصول إلى Azure SignalR (معاينة)  

## <a name="format"></a>تنسيق

مجموعة مكونة من 43 حرفا تتكون من أحرف وأرقام وأحرف خاصة تنتهي بعلامة يساوي (=) لا تشكل جزءا من النمط.

## <a name="pattern"></a>نمط

تركيبة مكونة من 43 حرفا تتكون من:
 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لمصادقة عملاء [Azure SignalR](/azure/azure-signalr/signalr-howto-key-rotation) عند تقديم الطلبات إلى الخدمة.

ويستخدم العديد من الموارد الأساسية:

- أنماط مفتاح 256 بت المتماثل المشفر ل Base64.
- أنماط CredentialName، CredentialFeatures، AccountIdentityName، AccountIdentityValue، ResourceType، ResourceName، المعرف.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256:

- SharedAccessKey
- مفتاح الحساب
