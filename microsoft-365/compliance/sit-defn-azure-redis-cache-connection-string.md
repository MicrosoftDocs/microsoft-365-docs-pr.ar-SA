---
title: تعريف كيان سلسلة اتصال ذاكرة التخزين المؤقت ل Azure Redis
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
description: تعريف كيان نوع المعلومات الحساسة لسلسلة اتصال ذاكرة التخزين المؤقت ل Azure Redis.
ms.openlocfilehash: f195440c1f93ec1818bf10e1c57cf391085cb733
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944534"
---
# <a name="azure-redis-cache-connection-string"></a>سلسلة اتصال ذاكرة التخزين المؤقت لـ Azure Redis

## <a name="format"></a>تنسيق

السلسلة `redis.cache.windows.net` متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة `password` أو `pwd`.

## <a name="pattern"></a>نمط

- السلسلة `redis.cache.windows.net`
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة `password` أو `pwd`
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة مكونة من 43 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- علامة التساوي (=)

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_AzureRedisCacheConnectionString` العادي عن المحتوى الذي يطابق النمط.
- لا يعثر التعبير `CEP_CommonExampleKeywords` العادي على محتوى يطابق النمط.

```xml
<!--Azure Redis Cache Connection String-->
<Entity id="095a7e6c-efd8-46d5-af7b-5298d53a49fc" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureRedisCacheConnectionString" />
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
