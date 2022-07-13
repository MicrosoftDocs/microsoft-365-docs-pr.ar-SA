---
title: مراجعة متطلبات البنية والإطار التقني Microsoft Defender for Identity
description: سيساعدك الرسم التخطيطي التقني Microsoft Defender for Identity في Microsoft 365 Defender على فهم الهوية في Microsoft 365 قبل إنشاء مختبر تجريبي أو بيئة تجريبية.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e92fa629b49664b6f87c8e72c23a2f9cae74afe6
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750221"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-identity"></a>مراجعة متطلبات البنية والمفاهيم الرئيسية Microsoft Defender for Identity


**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 1 من 3](eval-defender-identity-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender for Identity. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-identity-overview.md).

قبل تمكين Microsoft Defender for Identity، تأكد من فهمك للبنية ويمكن أن تفي بالمتطلبات.

تستخدم Microsoft Defender for Identity التعلم الآلي والتحليلات السلوكية لتحديد الهجمات عبر شبكتك المحلية إلى جانب الكشف عن مخاطر تسجيل دخول المستخدم المرتبطة بالهويات السحابية ومنعها بشكل استباقي. لمزيد من المعلومات، راجع [ما هو Microsoft Defender for Identity؟](/defender-for-identity/what-is)

يحمي Defender for Identity المستخدمين Active Directory محلي و/أو المستخدمين الذين تمت مزامنتهم مع Azure Active Directory (Azure AD). لحماية بيئة مكونة من مستخدمين Azure AD فقط، راجع [Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="understand-the-architecture"></a>فهم البنية

يوضح الرسم التخطيطي التالي بنية الأساس ل Defender for Identity. 

:::image type="content" source="../../media/defender/m365-defender-identity-architecture.png" alt-text="بنية الهوية Microsoft Defender for Identity" lightbox="../../media/defender/m365-defender-identity-architecture.png":::

في هذا الرسم التوضيحي:

- تقوم أجهزة الاستشعار المثبتة على وحدات تحكم مجال AD بتحليل السجلات وحركة مرور الشبكة وإرسالها إلى Microsoft Defender for Identity للتحليل وإعداد التقارير.
-  يمكن لأدوات الاستشعار أيضا تحليل خدمات الأمان المشترك لـ Active Directory (AD FS) عند تكوين Azure AD لاستخدام المصادقة الموحدة (خط منقط في الرسم التوضيحي). 
- Microsoft Defender for Identity تشارك الإشارات إلى Microsoft 365 Defender للكشف والاستجابة الموسعين (XDR).

يمكن تثبيت أجهزة استشعار Defender for Identity مباشرة على الخوادم التالية:

- وحدات التحكم بالمجال: يراقب جهاز الاستشعار مباشرة حركة مرور وحدة التحكم بالمجال، دون الحاجة إلى خادم مخصص، أو تكوين النسخ المتطابق للمنفذ.
- AD FS: يراقب جهاز الاستشعار مباشرة حركة مرور الشبكة وأحداث المصادقة.

لإلقاء نظرة أعمق على بنية Defender for Identity، بما في ذلك التكامل مع Defender for Cloud Apps، راجع [بنية Microsoft Defender for Identity](/defender-for-identity/architecture).


## <a name="understand-key-concepts"></a>فهم المفاهيم الرئيسية

حدد الجدول التالي المفاهيم الرئيسية التي من المهم فهمها عند تقييم Microsoft Defender for Identity وتكوينها ونشرها.

|مفهوم  |الوصف |معلومات إضافية  |
|---------|---------|---------|
| الأنشطة المراقبة | يراقب Defender for Identity الإشارات التي تم إنشاؤها من داخل مؤسستك للكشف عن النشاط المشبوه أو الضار ويساعدك على تحديد صلاحية كل تهديد محتمل حتى تتمكن من الفرز والاستجابة بفعالية.  |  [Microsoft Defender for Identity الأنشطة المراقبة](/defender-for-identity/monitored-activities)       |
| تنبيهات الأمان    | تشرح تنبيهات أمان Defender for Identity الأنشطة المشبوهة التي اكتشفتها أجهزة الاستشعار على شبكتك إلى جانب الجهات الفاعلة وأجهزة الكمبيوتر المشاركة في كل تهديد.   | [Microsoft Defender for Identity تنبيهات الأمان](/defender-for-identity/suspicious-activity-guide?tabs=external)    |
| ملفات تعريف الكيان    | توفر ملفات تعريف الكيانات استقصاء شاملا متعمقا للمستخدمين وأجهزة الكمبيوتر والأجهزة والموارد جنبا إلى جنب مع محفوظات الوصول الخاصة بهم.   | [فهم ملفات تعريف الكيان](/defender-for-identity/entity-profiles)  |
| مسارات الحركة الجانبية    | أحد المكونات الرئيسية لتفاصيل أمان MDI هو تحديد مسارات الحركة الجانبية التي يستخدم فيها المهاجم حسابات غير حساسة للوصول إلى الحسابات أو الأجهزة الحساسة في جميع أنحاء شبكتك.  | [Microsoft Defender for Identity مسارات الحركة الجانبية (LMPs)](/defender-for-identity/use-case-lateral-movement-path)  |
| تحليل اسم الشبكة    |  تحليل اسم الشبكة (NNR) هو مكون من وظائف MDI التي تلتقط الأنشطة استنادا إلى نسبة استخدام الشبكة وأحداث Windows و ETW وما إلى ذلك وربط هذه البيانات الأولية بأجهزة الكمبيوتر ذات الصلة المشاركة في كل نشاط.       | [ما هو تحليل اسم الشبكة؟](/defender-for-identity/nnr-policy)      |
| التقارير    | تسمح لك تقارير Defender for Identity بجدولة التقارير التي توفر معلومات حالة النظام والكيان أو إنشاءها وتنزيلها على الفور.  يمكنك إنشاء تقارير حول صحة النظام، وتنبيهات الأمان، ومسارات الحركة الجانبية المحتملة المكتشفة في بيئتك.   | [تقارير Microsoft Defender for Identity](/defender-for-identity/reports)       |
| مجموعات الأدوار    | يوفر Defender for Identity المجموعات المستندة إلى الأدوار والوصول المفوض لحماية البيانات وفقا لاحتياجات الأمان والتوافق المحددة لمؤسستك والتي تتضمن المسؤولين والمستخدمين والعارضين.        |  [مجموعات الأدوار Microsoft Defender for Identity](/defender-for-identity/role-groups)       |
| مدخل إداري    |  بالإضافة إلى مدخل Microsoft 365 Defender، يمكن استخدام مدخل Defender for Identity لمراقبة النشاط المشبوه والاستجابة له.      | [العمل مع مدخل Microsoft Defender for Identity](/defender-for-identity/workspace-portal)        |
| تكامل Microsoft Defender for Cloud Apps   | يتكامل Microsoft Defender for Cloud Apps مع Microsoft Defender for Identity لتوفير التحليلات السلوكية لكيانات المستخدم (UEBA) عبر بيئة مختلطة - سواء تطبيق السحابة أو محليا   | تكامل Microsoft Defender for Identity  |

## <a name="review-prerequisites"></a>مراجعة المتطلبات الأساسية

يتطلب Defender for Identity بعض العمل المسبق لضمان تلبية مكونات الهوية والشبكات المحلية للحد الأدنى من المتطلبات. استخدم هذه المقالة كلقائمة اختيار للتأكد من أن بيئتك جاهزة: [Microsoft Defender for Identity المتطلبات الأساسية](/defender-for-identity/prerequisites).


## <a name="next-steps"></a>الخطوات التالية

الخطوة 2 من 3: [تمكين بيئة التقييم Defender for Identity](eval-defender-identity-enable-eval.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender for Identity](eval-defender-identity-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md) 
