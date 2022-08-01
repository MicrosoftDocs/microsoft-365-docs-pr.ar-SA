---
title: تعريف كيان رأس تخويل Http (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لرأس تخويل Http.
ms.openlocfilehash: b72934a88f85c0245320baa4b774d3c69196eb47
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944711"
---
# <a name="http-authorization-header-preview"></a>رأس تخويل Http (معاينة)

## <a name="format"></a>تنسيق

عنوان التخويل المستخدم في طلب HTTP.

## <a name="pattern"></a>نمط

تنسيقات عناوين المصادقة المختلفة على سبيل المثال:
 
`authorization: basic ********` <br>
`authorization: bearer ********` <br>
`authorization: digest ********` <br>
`authorization: negotiate ********` <br>

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة في رأس [طلب HTTP للمصادقة والتخويل.](/dotnet/api/system.net.http.headers.httprequestheaders.authorization?view=netframework-4.8) 

ويستخدم العديد من الموارد الأساسية:

- أنماط رأس تخويل Http.
- أنماط CredentialName و CredentialFeatures و ResourceType.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_httpauthorizationheader"></a>Keyword_HttpAuthorizationHeader:

- التخويل

