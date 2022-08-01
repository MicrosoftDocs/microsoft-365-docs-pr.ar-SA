---
title: تعريف كيان سلسلة اتصال Azure IoT (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لسلسلة اتصال Azure IoT.
ms.openlocfilehash: 89d2ab0170000285dc2c274f50ff9a5106b5bc59
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944696"
---
# <a name="azure-iot-connection-string-preview"></a>سلسلة اتصال Azure IoT (معاينة)

### <a name="format"></a>تنسيق

السلسلة `HostName` متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلاسل `azure-devices.net` و `SharedAccessKey`.

## <a name="pattern"></a>نمط

- السلسلة `HostName`
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة "azure-devices.<!--no-hyperlink-->net"
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة `SharedAccessKey`
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة من 43 حرفا صغيرا أو أحرفا كبيرة أو رقما أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- علامة التساوي (=)

## <a name="checksum"></a>المجموع الاختباري

لا

### <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_AzureIoTConnectionString` العادي عن المحتوى الذي يطابق النمط.
- لا يعثر التعبير `CEP_CommonExampleKeywords` العادي على محتوى يطابق النمط.

```xml
<!--Azure IoT Connection String-->
<Entity id="0b34bec3-d5d6-4974-b7b0-dcdb5c90c29d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureIoTConnectionString" />
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
