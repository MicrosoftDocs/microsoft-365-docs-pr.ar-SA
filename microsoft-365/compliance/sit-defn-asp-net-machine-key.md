---
title: تعريف كيان مفتاح الجهاز ASP.NET (معاينة)
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
description: ASP.NET تعريف كيان نوع المعلومات الحساسة لمفتاح الجهاز.
ms.openlocfilehash: 23dc07febc51425fb9b7f79d851848e00d5d974d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944575"
---
# <a name="aspnet-machine-key-preview"></a>مفتاح الجهاز ASP.NET (معاينة)

## <a name="format"></a>تنسيق

مفاتيح متماثلة في تكوين XML.

## <a name="pattern"></a>نمط

تنسيقات المفاتيح المتماثلة المختلفة في XML، على سبيل المثال:

```xml
<machineKey decryptionKey="******** </br> 
<machineKey validationKey="********
```
## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف


تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لتشفير البيانات أو تجزئةها في [ASP.NET](/dotnet/api/system.web.security.machinekey?view=netframework-4.8) نماذج المصادقة وعرض الحالة. 

ويستخدم العديد من الموارد الأساسية:

- أنماط سياق المفتاح المتماثل في ملفات xml.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.


## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickeycontextinxml"></a>Keyword_SymmetricKeyContextInXml:

- كلمه المرور
- مفتاح
- Connectionstring

