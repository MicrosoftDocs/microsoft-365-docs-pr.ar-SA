---
title: مراجعة متطلبات البنية وإطار العمل التقني ل Microsoft Defender for Identity
description: سيساعدك الرسم التخطيطي التقني ل Microsoft Defender for Identity Microsoft 365 Defender على فهم الهوية في Microsoft 365 قبل إنشاء المعمل التجريبي أو بيئة الإصدار التجريبي.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e534211008ea560642ba306844b9223170ac0140
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579677"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-identity"></a>مراجعة متطلبات البنية والمفاهيم الأساسية ل Microsoft Defender for Identity


**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 1 من 3](eval-defender-identity-overview.md) في عملية إعداد بيئة التقييم ل Microsoft Defender for Identity. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-identity-overview.md).

قبل تمكين Microsoft Defender for Identity، تأكد من فهم البنية ويمكنها تلبية المتطلبات.

يستخدم Microsoft Defender for Identity التحليلات السلوكية والتعلم الآلي لتحديد الهجمات عبر شبكتك المحلية إلى جانب الكشف عن مخاطر تسجيل الدخول من قبل المستخدمين المقترنة بالهويات السحابية ومنعها بشكل استباقي. لمزيد من المعلومات، [راجع ما هو Microsoft Defender for Identity؟](/defender-for-identity/what-is)

يحمي Defender for Identity مستخدمي Active Directory المحلي و/أو المستخدمين الذين متزامنوا مع Azure Active Directory (Azure AD). لحماية بيئة تكون من مستخدمي Azure AD فقط، راجع [حماية هوية Azure AD](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="understand-the-architecture"></a>فهم البنية

يوضح الرسم التخطيطي التالي بنية الأساس ل Defender for Identity. 

![هندسة Microsoft Defender for Identity.](../../media/defender/m365-defender-identity-architecture.png)

في هذا الرسم التوضيحي:
- تقوم أدوات الاستشعار المثبتة على وحدات التحكم في مجال AD بتحليل السجلات وازدحام الشبكة وإرسالها إلى Microsoft Defender for Identity لتحليلها وإعداد التقارير بشأنها.
-  يمكن أن تقوم أدوات الاستشعار أيضا تحليل خدمات اتحاد Active Directory (AD FS) عند تكوين Azure AD لاستخدام المصادقة المتحدة (الخط المنقطة في الرسم التوضيحي). 
- يشارك Microsoft Defender for Identity الإشارات Microsoft 365 Defender للكشف والاستجابة الموسعة (XDR).


يمكن تثبيت Defender for Identity sensors مباشرة على الخوادم التالية:

- وحدات التحكم بالمجال: يراقب المستشعر بشكل مباشر حركة مرور وحدة التحكم بالمجال، دون الحاجة إلى خادم مخصص، أو تكوين انعكاس المنفذ.
- AD FS: يراقب المستشعر مباشرة أحداث حركة مرور الشبكة والمصادقة.

للحصول على نظرة أعمق على بنية Defender for Identity، بما في ذلك التكامل مع Defender for Cloud Apps، راجع [هندسة Microsoft Defender for Identity](/defender-for-identity/architecture).


## <a name="understand-key-concepts"></a>فهم المفاهيم الأساسية

حدد الجدول التالي المفاهيم الأساسية التي من المهم فهمها عند تقييم Microsoft Defender for Identity وتكوينه ونشره.


|المفهوم  |الوصف |معلومات إضافية  |
|---------|---------|---------|
| الأنشطة التي يتم مراقبتها | يراقب Defender for Identity الإشارات التي يتم إنشاؤها من داخل مؤسستك للكشف عن نشاط مريب أو ضار ويساعدك على تحديد مدى صلاحية كل خطر محتمل حتى تتمكن من الفرز والاستجابة بفعالية.  |  [أنشطة Microsoft Defender for Identity التي يتم مراقبتها](/defender-for-identity/monitored-activities)       |
| تنبيهات الأمان    | تشرح تنبيهات أمان Defender for Identity الأنشطة المريبة التي تكتشفها أدوات الاستشعار على شبكتك إلى جانب الجهات الخارجية وأجهزة الكمبيوتر المتدخلة في كل خطر.   | [تنبيهات أمان Microsoft Defender لالهوية](/defender-for-identity/suspicious-activity-guide?tabs=external)    |
| ملفات تعريف الكيانات    | توفر ملفات تعريف الكيانات عملية تحقيق شاملة حول المستخدمين وأجهزة الكمبيوتر والأجهزة والموارد إلى جانب محفوظات الوصول الخاصة بهم.   | [فهم ملفات تعريف الكيانات](/defender-for-identity/entity-profiles)  |
| مسارات الحركة اللاحقة    | أحد المكونات الأساسية رؤى أمان MDI هو تحديد مسارات الحركة اللاحقة التي يستخدم فيها المهاجم الحسابات غير الحساسة للوصول إلى الحسابات أو الأجهزة الحساسة في جميع أنحاء الشبكة.  | [مسارات الحركة اللاحقة ل Microsoft Defender for Identity (LMPs)](/defender-for-identity/use-case-lateral-movement-path)  |
| دقة اسم الشبكة    |  إن دقة اسم الشبكة (NNR) هي أحد مكونات وظيفة MDI التي تقوم بالتقاط الأنشطة استنادا إلى حركة مرور الشبكة، والأحداث Windows، و ETW، وما إلى ذلك، وربط هذه البيانات الخام بأجهزة الكمبيوتر ذات الصلة المتدخلة في كل نشاط.       | [ما هي دقة اسم الشبكة؟](/defender-for-identity/nnr-policy)      |
| التقارير    | تتيح لك تقارير Defender for Identity جدولة التقارير التي توفر معلومات حالة النظام والكيانات أو إنشاءها وتنزيلها على الفور.  يمكنك إنشاء تقارير حول حماية النظام وتنبيهات الأمان ومسارات الحركة اللاحقة المحتملة التي تم الكشف عنها في بيئتك.   | [Microsoft Defender لتقارير الهوية ](/defender-for-identity/reports)       |
| مجموعات الدور    | يوفر Defender for Identity مجموعات مستندة إلى الدور والوصول المفوض لحماية البيانات وفقا لاحتياجات التوافق والأمان الخاصة في مؤسستك التي تتضمن المسؤولين والمستخدمين والعارضين.        |  [مجموعات دور Microsoft Defender for Identity](/defender-for-identity/role-groups)       |
| المدخل الإداري    |  بالإضافة إلى مدخل Microsoft 365 Defender، يمكن استخدام مدخل Defender for Identity لمراقبة النشاط المريب والاستجابة له.      | [العمل مع مدخل Microsoft Defender for Identity](/defender-for-identity/workspace-portal)        |
| تكامل Microsoft Defender for Cloud Apps   | يتكامل Microsoft Defender for Cloud Apps مع Microsoft Defender for Identity لتوفير تحليلات سلوكية (UEBA) لكيان المستخدم عبر بيئة مختلطة - كل من تطبيق السحابة والتطبيق المحلي   | تكامل Microsoft Defender for Identity  |
| | | |


## <a name="review-prerequisites"></a>مراجعة المتطلبات الأساسية

يتطلب Defender for Identity بعض العمل الأساسي لضمان تلبية مكونات الشبكة وهويتك المحلية للحد الأدنى من المتطلبات. استخدم هذه المقالة كقائمة اختيار للتأكد من أن بيئتك جاهزة: [المتطلبات الأساسية ل Microsoft Defender for Identity](/defender-for-identity/prerequisites).


## <a name="next-steps"></a>الخطوات التالية

الخطوة 2 من 3: [تمكين بيئة التقييم Defender for Identity](eval-defender-identity-enable-eval.md)

العودة إلى نظرة عامة حول [تقييم Microsoft Defender for Identity](eval-defender-identity-overview.md)

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md) 
