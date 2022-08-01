---
title: سلسلة اتصال قاعدة بيانات Azure IAAS وتعريف كيان سلسلة اتصال Azure SQL
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
description: سلسلة اتصال قاعدة بيانات Azure IAAS وتعريف نوع وحدة نوع المعلومات الحساسة لسلسلة اتصال Azure SQL.
ms.openlocfilehash: 894a849c318ad15ab9baac8343192428d633ce1b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944444"
---
# <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>سلسلة اتصال قاعدة بيانات Azure IAAS وسلسلة اتصال Azure SQL

## <a name="format"></a>تنسيق

السلسلة `Server`، `server`أو `data source` متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة `cloudapp.azure.com` أو `cloudapp.azure.net` `database.windows.net`، والسلسلة `Password` أو `password` `pwd`.

## <a name="pattern"></a>نمط

- السلسلة `Server`، `server`أو `data source`
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "cloudapp.azure.<!--no-hyperlink-->com"، "cloudapp.azure.<!--no-hyperlink-->net"، أو "database.windows.<!--no-hyperlink-->net"
- أي تركيبة بين 1-300 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة `Password`، `password`أو `pwd`
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- حرف واحد أو أكثر ليس فاصلة منقوطة (;) أو علامة اقتباس (") أو فاصلة فاصلة أحادية (')
- فاصلة منقوطة (;) أو علامة اقتباس (") أو فاصلة فاصلة أحادية (')

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_AzureConnectionString` العادي عن المحتوى الذي يطابق النمط.
- لا يعثر التعبير `CEP_CommonExampleKeywords` العادي على محتوى يطابق النمط.

```xml
<!--Azure IAAS Database Connection String and Azure SQL Connection String-->
<Entity id="ce1a126d-186f-4700-8c0c-486157b953fd" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

يعرف نوع المعلومات الحساسة هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي
