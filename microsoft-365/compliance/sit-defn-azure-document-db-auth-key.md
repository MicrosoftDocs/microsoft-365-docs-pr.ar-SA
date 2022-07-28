---
title: تعريف كيان مفتاح مصادقة Azure DocumentDB
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح مصادقة Azure DocumentDB.
ms.openlocfilehash: e499d185b0a1752960f71f659a212aa0422154f4
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944349"
---
# <a name="azure-documentdb-auth-key"></a>مفتاح مصادقة Azure DocumentDB

## <a name="format"></a>تنسيق

السلسلة `DocumentDb` متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه.

## <a name="pattern"></a>نمط

- السلسلة `DocumentDb`
- أي تركيبة بين 3-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- رمز أكبر من (>) أو علامة التساوي (=) أو علامة اقتباس (") أو علامة اقتباس أحادية (')
- أي تركيبة من 86 حرفا صغيرا أو أحرفا كبيرة أو رقما أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- اثنين من علامات التساوي (=)

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_AzureDocumentDBAuthKey` العادي عن المحتوى الذي يطابق النمط.
- لا يعثر التعبير `CEP_CommonExampleKeywords` العادي على محتوى يطابق النمط.

```xml
<!-- Azure Document DB Auth Key -->
<Entity id="0f587d92-eb28-44a9-bd1c-90f2892b47aa" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureDocumentDBAuthKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
          </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

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
