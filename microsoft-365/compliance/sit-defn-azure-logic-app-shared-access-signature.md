---
title: تعريف كيان توقيع الوصول المشترك ل Azure Logic App (معاينة)
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
description: تعريف كيان نوع المعلومات الحساسة لتوقيع الوصول المشترك لتوقيع Azure Logic App.
ms.openlocfilehash: ff777170f9c9cc7ea3865a4a01e794c20137f7db
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944346"
---
# <a name="azure-logic-app-shared-access-signature-preview"></a>توقيع الوصول المشترك ل Azure Logic App (معاينة) 

## <a name="format"></a>تنسيق

تركيبة تصل إلى 76 حرفا تتكون من أحرف وأرقام وأحرف خاصة.

## <a name="pattern"></a>نمط

أي تركيبة من 43 إلى 73 حرفا تتكون من:

- a-z (غير حساس لحالة الأحرف)
- 0-9
- أو علامات النسبة المئوية (٪)
- ينتهي بلاحقة '٪3d' (غير حساسة لحالة الأحرف)

على سبيل المثال:

`abcdefghijklmnopqrstuvwxyz0123456789%2F%2BABCDE%3D`

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

تم تصميم SIT هذا لمطابقة معلومات الأمان المستخدمة لمنح حق الوصول إلى نقطة نهاية الطلب على [Azure Logic Apps.](/azure/logic-apps/logic-apps-securing-a-logic-app?tabs=azure-portal) 

ويستخدم العديد من الموارد الأساسية:

أنماط مفتاح 256 بت المشفر ل URL المتماثل.
أنماط CredentialName و CredentialFeatures و AccountIdentityName و AccountIdentityValue و ResourceType و ResourceName.
أنماط قيم المحاكاة، والتنقية، والعنصر النائب.
قاموس من المفردات

تم تصميم الأنماط لمطابقة بيانات الاعتماد الفعلية بثقة معقولة. لا تتطابق الأنماط مع بيانات الاعتماد المنسقة كأمثلة. قيم المحاكاة والقيم المكررة والعنصر النائب، مثل نوع بيانات الاعتماد أو أوصاف الاستخدام، في الموضع حيث يجب عدم مطابقة القيمة السرية الفعلية.


## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_symmetrickey256urlencoded"></a>Keyword_SymmetricKey256UrlEncoded:

- sig=
- مفتاح
- الرمز المميز
- السريه
- كلمه المرور
