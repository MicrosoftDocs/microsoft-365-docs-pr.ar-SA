---
title: تعريف كيان كلمة المرور لإعداد نشر Azure
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
description: نشر تعريف كيان نوع المعلومات الحساسة لكلمة المرور في Azure.
ms.openlocfilehash: 9cbca08dc1414241f494a415cf3aafea9e505a6e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944337"
---
# <a name="azure-publish-setting-password"></a>كلمة مرور إعداد نشر Azure

### <a name="format"></a>تنسيق

السلسلة `userpwd=` متبوعة بسلسلة أبجدية رقمية.

### <a name="pattern"></a>نمط

- السلسلة `userpwd=`
- أي تركيبة من 60 حرفا صغيرا أو رقما
- علامة اقتباس (")

### <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_AzurePublishSettingPasswords` العادي عن المحتوى الذي يطابق النمط.
- لا يعثر التعبير `CEP_CommonExampleKeywords` العادي على محتوى يطابق النمط.

```xml
<!--Azure Publish Setting Password-->
<Entity id="75f4cc8a-a68e-49e5-89ce-fa8f03d286a5" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
       <IdMatch idRef="CEP_Regex_AzurePublishSettingPasswords" />
       <Any minMatches="0" maxMatches="0">
           <Match idRef="CEP_CommonExampleKeywords" />
       </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>الكلمات الرئيسيه

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

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
