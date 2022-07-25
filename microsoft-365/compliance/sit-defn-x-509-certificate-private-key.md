---
title: تعريف كيان المفتاح الخاص لشهادة X.509 (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة للمفتاح الخاص لشهادة X.509.
ms.openlocfilehash: bdf6666060e62312ecfaa260ea2521161e2db7a6
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988280"
---
# <a name="x509-certificate-private-key-preview"></a>مفتاح خاص لشهادة X.509 (معاينة)

## <a name="format"></a>تنسيق

تركيبة تصل إلى 20000 حرف تتكون من أحرف وأرقام وأحرف خاصة.

او

تركيبة تصل إلى 40 حرفا تتكون من أحرف كبيرة ومساحة وشرطات.

## <a name="pattern"></a>نمط

تركيبة تصل إلى 20,000 حرف:
 
- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)

ما يصل إلى اثنين من علامات التساوي (==)

على سبيل المثال:

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

او

5 شرط (-)

ومزيج يصل إلى 30 حرفا:

- A-Z (حساس لحالة الأحرف) 
- كل الاماكن
- 5 شرط (-)

على سبيل المثال:

`-----BEGIN PRIVATE KEY-----`


## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة كمكون خاص في [شهادات SSL.](/azure/key-vault/certificate-scenarios) 

ويستخدم العديد من الموارد الأساسية:

- أنماط سلسلة Base64 المشفرة الحرفية.
- أنماط رأس المفتاح الخاص للشهادة.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
- قاموس من المفردات.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral:

- الوزاره

### <a name="keyword_certificateprivatekeyheader"></a>Keyword_CertificatePrivateKeyHeader:

- مفتاح
