---
title: تعريف كيان AZURE SAS
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
description: تعريف كيان نوع المعلومات الحساسة ل Azure SAS.
ms.openlocfilehash: c7d63497a94204b77f83c5b357700311bf332e8c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944533"
---
# <a name="azure-sas"></a>Azure SAS

## <a name="format"></a>تنسيق

السلسلة `sig` متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه.

## <a name="pattern"></a>نمط

- السلسلة `sig`
- من صفر إلى حرفين من أحرف المسافة البيضاء
- علامة التساوي (=)
- من صفر إلى حرفين من أحرف المسافة البيضاء
- أي تركيبة بين 43-53 حرفا من أحرف صغيرة أو كبيرة أو أرقام أو علامة النسبة المئوية (٪)
- السلسلة `%3d`
- أي حرف ليس حرفا أو رقما أو رقما أو علامة النسبة المئوية (٪)

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_AzureSAS` العادي عن المحتوى الذي يطابق النمط.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```
