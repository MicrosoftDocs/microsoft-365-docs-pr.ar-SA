---
title: تعريف كيان سلسلة اتصال Azure SQL (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لسلسلة اتصال Azure SQL.
ms.openlocfilehash: 7091c50d96f22370358f5743a3992a10025ea29f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944412"
---
# <a name="azure-sql-connection-string-preview"></a>سلسلة اتصال Azure SQL (معاينة)

## <a name="format"></a>تنسيق

مجموعة تصل إلى 20000 حرف من الأحرف والأرقام والأحرف الخاصة.

او

زوج من اسم المستخدم وكلمة المرور المستخدمة في عملية المصادقة العامة.


## <a name="pattern"></a>نمط

أي تركيبة تصل إلى 20,000 حرف تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- خطوط مائلة للأمام (/)
- أو علامات الجمع (+)
- حتى 2
- علامات التساوي (=)

على سبيل المثال: 

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

او

تنسيقات اسم المستخدم وكلمة المرور المتغيرة، على سبيل المثال:

`username=...;password=********;` <br>
`user id=...;password=********;` <br>
`uid=...;pwd=********;` <br>
`DB_USER=...;DB_PASS=********;` <br>
`Service Account=...;Password=********;` <br>


## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للاتصال ب [Azure SQL Databases](/azure/sql-database/sql-database-aad-authentication-configure).

ويستخدم العديد من الموارد الأساسية:

- أنماط سلسلة Base64 المشفرة الحرفية.
- أنماط اسم المستخدم وكلمة المرور ذات النص العادي.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral:

- الوزاره

### <a name="keyword_logincredentials"></a>Keyword_LoginCredentials:

- كلمه المرور
- الاسبق
- DB_
