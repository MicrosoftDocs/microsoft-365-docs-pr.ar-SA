---
title: تعريف كيان مفتاح حساب تخزين Azure (عام)
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
description: تعريف كيان نوع المعلومات الحساسة لمفتاح حساب تخزين Azure (عام).
ms.openlocfilehash: 88139dfe26e654e664d74e8543ea791fd171da63
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944436"
---
# <a name="azure-storage-account-key-generic"></a>مفتاح حساب Azure دنن(عام)

## <a name="format"></a>تنسيق

أي تركيبة مكونة من 86 حرفا صغيرا أو أحرفا كبيرة أو رقما أو شرطة مائلة للأمام (/) أو علامة الجمع (+)، مسبوقة أو متبوعة بالأحرف الموضحة في النمط أدناه.

## <a name="pattern"></a>نمط

- من صفر إلى واحد من الرمز الأكبر (>) أو علامة اقتباس أحادية (') أو علامة التساوي (=) أو علامة الاقتباس (") أو علامة الرقم (#)
- أي تركيبة مكونة من 86 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو شرطة مائلة للأمام (/) أو علامة الجمع (+)
- اثنين من علامات التساوي (=)

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_AzureStorageAccountKeyGeneric` العادي عن المحتوى الذي يطابق النمط.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```