---
title: تعريف كيان الرمز المميز للوصول إلى Slack (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة للرمز المميز للوصول إلى Slack.
ms.openlocfilehash: 18e6654abe83bcbde40a832a74ec451c24f744b0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944545"
---
# <a name="slack-access-token-preview"></a>الرمز المميز للوصول إلى فترة السماح (معاينة)

## <a name="format"></a>تنسيق

تركيبة تصل إلى 34 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

بادئة الرمز المميز (حساسة لحالة الأحرف) "xoxp-" أو "xoxb-" أو "xoxa-" أو "xoxr-" أو "xoxo-" أو "xoxs-" أو "xoxe-"

تركيبة تصل إلى 29 حرفا:

- 29 a-z (غير حساس لحالة الأحرف)
- 0-9 أو واصلات (-)

على سبيل المثال:

`xoxp-abcdef-abcdef-abcdef-abcdef` 

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة للوصول إلى [وظائف النظام الأساسي Slack](https://api.slack.com/docs/token-type) (على سبيل المثال الرموز المميزة ل Bot والرموز المميزة للمستخدم والرموز المميزة على مستوى التطبيق). 

ويستخدم العديد من الموارد الأساسية:

- أنماط الرمز المميز لمستخدم/روبوت/مساحة عمل Slack.
- أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
- أنماط قيم المحاكاة، والتنقية، والعنصر النائب.

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_slacktokens"></a>Keyword_SlackTokens:

- Xox
