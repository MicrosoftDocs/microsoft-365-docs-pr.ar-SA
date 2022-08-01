---
title: Microsoft Defender for Identity في Microsoft 365 Defender
description: تعرف على التغييرات من Microsoft Defender for Identity إلى Microsoft 365 Defender
keywords: بدء استخدام Microsoft 365 Defender، Microsoft Defender for Identity، NDI
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dacurwin
author: dcurwin
manager: dansimp
ms.date: 07/06/2022
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 76044b7451014cc578800b6e1726556688d9db14
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67107272"
---
# <a name="microsoft-defender-for-identity-in-microsoft-365-defender"></a>Microsoft Defender for Identity في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender للهوية](/defender-for-identity/)

أصبح Microsoft Defender for Identity الآن جزءا من Microsoft 365 Defender. يسمح مدخل Microsoft 365 Defender لمسؤولي الأمان بتنفيذ مهام الأمان الخاصة بهم في موقع واحد. سيؤدي ذلك إلى تبسيط مهام سير العمل، وإضافة وظائف خدمات Microsoft 365 Defender الأخرى. ستكون Microsoft 365 Defender هي الصفحة الرئيسية لمراقبة الأمان وإدارته عبر هويات Microsoft وبياناتها وأجهزتها وتطبيقاتها وبنيتك الأساسية.

تساهم Microsoft Defender for Identity في المعلومات التي تركز على الهوية في الحوادث والتنبيهات التي يقدمها Microsoft 365 Defender. هذه المعلومات أساسية لتوفير السياق وربط التنبيهات من المنتجات الأخرى داخل Microsoft 365 Defender.

## <a name="quick-reference"></a>مرجع سريع

يسرد الجدول أدناه التغييرات في التنقل بين Microsoft Defender for Identity Microsoft 365 Defender.

| **Defender ل** الهوية  | **Microsoft 365 Defender**                                   |
| -------------------------- | ------------------------------------------------------------ |
| مخطط زمني                   | قائمة انتظار Microsoft 365 Defender Alerts/Incidents                |
| التقارير                    | سيبقى في مدخل [Defender for Identity الكلاسيكي](/defender-for-identity/classic-workspace-portal). <br> يمكن إنشاء تقارير مخصصة في مدخل Microsoft 365 Defender باستخدام [التتبع المتقدم](#advanced-hunting-new).               |
| صفحة المستخدم                  | صفحة مستخدم Microsoft 365 Defender                             |
| صفحة الجهاز                | صفحة جهاز Microsoft 365 Defender                           |
| صفحة المجموعة                 | الجزء الجانبي لمجموعات Microsoft 365 Defender                      |
| صفحة التنبيه                 | صفحة تنبيه Microsoft 365 Defender                            |
| بحث                     | Microsoft 365 Defender البحث                                |
| مركز الرعاية الصحية              | الإعدادات -> Identities -> Sensors                            |
| أنشطة الكيان          | الصيد المتقدم                                             |
| الإعدادات                   | الإعدادات -> الهويات                                       |
| المستخدمون والحسابات         | الأصول -> الهويات                                         |
| وضع أمان الهوية  | [تقييمات الوضع الأمني Microsoft Defender for Identity](/defender-for-identity/security-assessment) |
| إعداد مساحة عمل جديدة | الإعدادات -> الهويات (تلقائيا)                       |

## <a name="whats-changed"></a>ما الذي تم تغييره

### <a name="defender-for-identity-settings"></a>إعدادات Defender for Identity

للوصول إلى إعدادات تكوين Microsoft Defender for Identity، في [Microsoft 365 Defender](https://security.microsoft.com)، انتقل إلى **الإعدادات** ثم **الهويات**.

### <a name="defender-for-identity-security-posture"></a>وضع أمان Defender for Identity

تتوفر الآن جميع تقييمات إدارة وضع أمان الهوية التي كان يمكن الوصول إليها سابقا في Defender for Cloud Apps في Microsoft Secure Score، والتي يمكن العثور عليها في <https://security.microsoft.com/securescore> [مدخل Microsoft 365 Defender](https://security.microsoft.com). لمزيد من المعلومات، راجع [تقييمات الوضع الأمني Microsoft Defender for Identity](/defender-for-identity/security-assessment).

### <a name="global-search"></a>البحث العمومي

يسمح البحث العام في Microsoft 365 Defender (باستخدام شريط البحث في أعلى الصفحة) لفرق الأمان بالبحث عن أي كيان تراقبه Microsoft 365 Defender، مثل الهوية ونقطة النهاية وبيانات Office 365 والمزيد. يمكن التفاعل مع النتائج مباشرة من القائمة المنسدلة للبحث، أو يمكن لفرق الأمان اختيار تحديد **كافة المستخدمين** أو **كافة الأجهزة**  لرؤية جميع الكيانات المقترنة بمصطلح البحث هذا.

### <a name="onboarding-and-administration"></a>الإلحاق والإدارة

عملية الإلحاق تلقائية الآن للعملاء الجدد، دون الحاجة إلى تكوين مساحة عمل يدويا. بالإضافة إلى ذلك، تتوفر جميع ميزات المسؤول ضمن قائمة **الهويات** في إعدادات Microsoft 365 Defender.

### <a name="alerting-and-incident-correlation"></a>ارتباط التنبيه والحوادث

يتم الآن تضمين تنبيهات Defender for Identity في قائمة انتظار تنبيه Microsoft 365 Defender، ما يجعلها متاحة لميزة ارتباط الحدث التلقائي. وهذا يضمن أن جميع التنبيهات متوفرة في مكان واحد، وأن نطاق الخرق يمكن تحديده بشكل أسرع من ذي قبل. لمزيد من المعلومات، راجع [تنبيهات أمان Defender for Identity في Microsoft 365 Defender](/defender-for-identity/manage-security-alerts).

### <a name="advanced-hunting-new"></a>التتبع المتقدم (جديد)

يمكنك الآن البحث بشكل استباقي عن التهديدات والنشاط الضار باستخدام استعلامات التتبع المتقدمة. يمكن استخدام هذه الاستعلامات القوية لتحديد موقع مؤشرات التهديد والكيانات ومراجعتها لكل من التهديدات المعروفة والمحتملة.

يمكن إنشاء قواعد الكشف المخصصة من استعلامات التتبع المتقدمة لمساعدتك على مشاهدة الأحداث التي قد تشير إلى نشاط الاختراق والأجهزة التي تم تكوينها بشكل خاطئ بشكل استباقي. لمزيد من المعلومات، راجع [البحث بشكل استباقي عن التهديدات مع التتبع المتقدم في Microsoft 365 Defender](advanced-hunting-overview.md).

### <a name="alert-exclusions-updated"></a>استثناءات التنبيه (محدثة)

واجهة التنبيه أكثر سهولة في الاستخدام، بما في ذلك إضافة دالة بحث مفيدة. بالإضافة إلى ذلك، فإنه يتضمن الآن استثناءات عمومية. وهذا يعني أنه يمكن استبعاد أي كيان من جميع التنبيهات التي تم إنشاؤها بواسطة Defender for Identity، مما يساعد في أي سيناريوهات اختبار قد تكون لديك. لمزيد من المعلومات، راجع [تكوين استثناءات الكشف عن الهوية ل Defender في Microsoft 365 Defender](/defender-for-identity/exclusions).

### <a name="entity-profiles"></a>ملفات تعريف الكيان

يتم الآن تضمين بيانات Defender for Identity في ملفات تعريف كيان Microsoft 365 User و Device.

### <a name="remediation-actions-new"></a>إجراءات المعالجة (جديدة)

يمكن الآن أخذ إجراءات معالجة Defender for Identity، مثل تعطيل الحسابات أو طلب إعادة تعيين كلمة المرور، من صفحة المستخدم Microsoft 365 Defender. لمزيد من المعلومات، راجع [إجراءات المعالجة في Microsoft Defender for Identity](/defender-for-identity/remediation-actions).

### <a name="lateral-movement-paths"></a>مسارات الحركة الجانبية

بالإضافة إلى علامة تبويب **مسارات الحركة الجانبية** على صفحة المستخدم، يمكن أيضا اكتشاف مسارات الحركة الجانبية عبر ميزة **التتبع المتقدمة** وتقييم الأمان لمسارات الحركة الجانبية. لمزيد من المعلومات، راجع [Microsoft Defender for Identity مسارات الحركة الجانبية (LMPs).](/defender-for-identity/understand-lateral-movement-paths)

## <a name="related-videos"></a>مقاطع فيديو ذات صلة

- [جديد ل Microsoft Defender for Identity](https://www.microsoft.com/videoplayer/embed/RE4HcEU)

## <a name="related-information"></a>المعلومات ذات الصلة

- [Microsoft 365 Defender](microsoft-365-defender.md)
