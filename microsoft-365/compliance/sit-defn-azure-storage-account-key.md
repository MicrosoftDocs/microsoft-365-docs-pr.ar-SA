---
title: تعريف كيان مفتاح حساب تخزين Azure
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح تخزين Azure.
ms.openlocfilehash: 6cea53a555a03fa1007e20b89078e02bd612bfc9
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988316"
---
# <a name="azure-storage-account-key"></a>مفتاح حساب تخزين Azure

## <a name="format"></a>تنسيق

السلسلة `DefaultEndpointsProtocol` متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه، بما في ذلك السلسلة `AccountKey`.

## <a name="pattern"></a>نمط

- السلسلة `DefaultEndpointsProtocol`
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة `AccountKey`
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة مكونة من 86 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- اثنين من علامات التساوي (=)

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_AzureStorageAccountKey` العادي عن المحتوى الذي يطابق النمط.
- لا يعثر التعبير `CEP_AzureEmulatorStorageAccountFilter` العادي على محتوى يطابق النمط.
- لا يعثر التعبير `CEP_CommonExampleKeywords` العادي على محتوى يطابق النمط.

```xml
<!--Azure Storage Account Key-->
<Entity id="c7bc98e8-551a-4c35-a92d-d2c8cda714a7" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_AzureEmulatorStorageAccountFilter" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

يعرف نوع المعلومات الحساسة هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

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