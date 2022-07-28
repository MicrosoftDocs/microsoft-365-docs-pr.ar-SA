---
title: تعريف كيان شهادة إدارة اشتراك Azure (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لشهادة إدارة اشتراك Azure.
ms.openlocfilehash: 7ce7b09fdeae6f9622a3aac4f92beb446715f8df
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944287"
---
# <a name="azure-subscription-management-certificate-preview"></a>شهادة إدارة اشتراك Azure (معاينة)

## <a name="format"></a>تنسيق

تركيبة تصل إلى 20000 حرف تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

تركيبة تصل إلى 20,000 حرف:
 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- شرطة مائلة للأمام (/) أو علامة الجمع (+)
- ما يصل إلى اثنين من علامات التساوي (==)

على سبيل المثال:

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للمصادقة مع [نموذج النشر الكلاسيكي](/azure/azure-resource-manager/management/deployment-models) الذي توفره Azure. تستخدم العديد من البرامج والأدوات، مثل Visual Studio أو Azure SDK، هذه الشهادات لأتمتة تكوين [ونشر خدمات Azure](/azure/azure-api-management-certs) المختلفة. 

ويستخدم العديد من الموارد الأساسية:

- أنماط سلسلة Base64 المشفرة الحرفية.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral:

- الوزاره
