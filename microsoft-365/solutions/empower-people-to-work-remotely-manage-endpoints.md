---
title: الخطوة 4. نشر إدارة نقاط النهاية للأجهزة وأجهزة الكمبيوتر ونقاط النهاية الأخرى
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: استخدم إدارة نقاط النهاية من Microsoft لإدارة الأجهزة وأجهزة الكمبيوتر ونقاط النهاية الأخرى.
ms.openlocfilehash: d18a001021486c617aaf0fa04972e9464a5c2016
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568477"
---
# <a name="step-4-deploy-endpoint-management-for-your-devices-pcs-and-other-endpoints"></a>الخطوة 4. نشر إدارة نقاط النهاية للأجهزة وأجهزة الكمبيوتر ونقاط النهاية الأخرى

باستخدام العاملين المختلطين، ستحتاج إلى دعم عدد متزايد من الأجهزة الشخصية. إدارة نقاط النهاية هي نهج يستند إلى نهج الأمان يتطلب من الأجهزة الامتثال لمعايير معينة قبل منحها حق الوصول إلى الموارد. إدارة نقاط النهاية من Microsoft قدرات الإدارة الحديثة للحفاظ على أمان البيانات في السحابة وفي الموقع المحلية. 

[إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) خدمات وأدوات لإدارة الأجهزة المحمولة وأجهزة كمبيوتر سطح المكتب والأجهزة الظاهرية والأجهزة المضمنة الخوادم من خلال دمج الخدمات التالية التي قد تكون تعرفها بالفعل وتستخدمها.

:::image type="content" source="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png" alt-text="مكونات إدارة نقاط النهاية Microsoft 365" lightbox="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png":::

## <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune هي خدمة مستندة إلى السحابة تركز على إدارة أجهزة المحمول (MDM) وإدارة تطبيقات الأجهزة المحمولة (MAM) المضمنة مع Microsoft 365. 

- **MDM:** بالنسبة للأجهزة المملوكة لمنظمتك، يمكنك ممارسة التحكم الكامل بما في ذلك الإعدادات والميزات والأمان. يتم "تسجيل" الأجهزة في Intune حيث تتلقى سياسات Intune مع القواعد والإعدادات. على سبيل المثال، يمكنك تعيين متطلبات رمز PIN وكلمة المرور، وإنشاء اتصال VPN، إعداد الحماية من المخاطر، والمزيد.

- **MAM:** قد لا يرغب العاملون عن بعد في التحكم الكامل في أجهزتهم الشخصية، المعروفة أيضا بأجهزة إحضار جهازك الخاص (BYOD). يمكنك منح العاملين المختلطين خيارات مع حماية مؤسستك. على سبيل المثال، يمكن للعاملين المختلطين تسجيل أجهزتهم إذا كانوا يرغبون في الوصول الكامل إلى موارد مؤسستك. أو، إذا كان هؤلاء المستخدمون يرغبون فقط في الوصول إلى البريد الإلكتروني أو Microsoft Teams، فاستخدم نهج حماية التطبيق التي تتطلب مصادقة متعددة العوامل (MFA) لاستخدام هذه التطبيقات.

لمزيد من المعلومات، راجع [حل إدارة الأجهزة باستخدام Intune](manage-devices-with-intune-overview.md) foundation.

## <a name="configuration-manager"></a>إدارة التكوين

إدارة التكوين هو حل إدارة في الموقع لإدارة أسطح المكتب، الخوادم، وأجهزة الكمبيوتر المحمولة على الشبكة أو المستندة إلى الإنترنت. استخدم إدارة التكوين لنشر التطبيقات وتحديثات البرامج وأنظمت التشغيل. يمكنك أيضا مراقبة التوافق والاستعلام والعمل على العملاء في الوقت الحقيقي، والمزيد. يمكنك تمكين السحابة للتكامل مع Intune و Azure AD و Microsoft Defender ل Endpoint وخدمات السحابة الأخرى. 

لمزيد من المعلومات، راجع نظرة [عامة حول إدارة التكوين](/mem/configmgr/core/understand/introduction).

## <a name="co-management"></a>الإدارة المشاركة

تجمع الإدارة المشاركة بين استثمار مدير التكوين المحلي الحالي والسحابة باستخدام Intune وخدمات Microsoft 365 السحابية الأخرى. يمكنك اختيار ما إذا كانت إدارة التكوين أو Intune هي مرجع الإدارة لأحمال العمل المختلفة. 

تستخدم الإدارة المشاركة ميزات السحابة المستندة إلى Intune، بما في ذلك الوصول الشرطي وفرض توافق الجهاز. يمكنك الاحتفاظ ببعض المهام في الموقع، أثناء تشغيل مهام أخرى في السحابة.

لمزيد من المعلومات، راجع نظرة [عامة حول الإدارة المشاركة](/mem/configmgr/comanage/overview).

## <a name="endpoint-analytics"></a>تحليلات نقطة النهاية

تهدف تحليلات نقطة النهاية إلى تحسين إنتاجية المستخدم وتقليل تكاليف دعم المعلومات من خلال توفير تحليلات حول تجربة المستخدم. تمكن الرؤى معلومات المعلومات من تحسين تجربة المستخدم النهائي مع دعم استباقي والكشف عن الانحدار إلى تجربة المستخدم من خلال تقييم تأثير المستخدم على تغييرات التكوين.

لمزيد من المعلومات، راجع نظرة [عامة حول تحليلات نقطة النهاية](/mem/analytics/overview)

## <a name="windows-autopilot"></a>Windows Autopilot

Windows Autopilot هو نظام أساسي للنشر بدون Windows تلقائي. ويتضمن مجموعة من التقنيات التي تستخدمها لإعداد الأجهزة الجديدة وتكوينها مسبقا، حتى تكون جاهزة للاستخدام الإنتاجي. يمكنك أيضا استخدام Windows Autopilot لإعادة تعيين الأجهزة وإعادة ترتيبها واستردادها. 

Windows Autopilot إلى تمكين قسم قسم المعلومات من تكوين الأجهزة مسبقا مع بنية أساسية قليلة إلى بلا بنية أساسية يمكن إدارتها، باستخدام عملية سهلة وبسيطة. 

- من منظور المستخدم، يتطلب الأمر بضع عمليات بسيطة فقط لجعل جهازه جاهزا للاستخدام. 
- من منظور محترفي IT، التفاعل الوحيد المطلوب من المستخدم هو الاتصال بشبكة والتحقق من بيانات الاعتماد الخاصة به.

لمزيد من المعلومات، راجع هذه [النظرة العامة Windows Autopilot](/windows/deployment/windows-autopilot/windows-autopilot).

## <a name="admin-technical-resources-for-endpoint-management"></a>الموارد التقنية للمسؤول لإدارة نقاط النهاية

- [خارطة طريق إدارة الأجهزة Microsoft 365](../enterprise/device-management-roadmap-microsoft-365.md)
- [كيفية تسجيل أنواع مختلفة من الأجهزة لإدارة أجهزة المحمول](/mem/intune/enrollment/device-enrollment)
- [كيفية تعليم المستخدمين النهائيين حول Microsoft Intune](/mem/intune/fundamentals/end-user-educate)
 
## <a name="results-of-step-4"></a>نتائج الخطوة 4

أنت تستخدم مجموعة من إدارة نقاط النهاية وإمكانيات إدارة الأجهزة المحمولة وأجهزة كمبيوتر سطح المكتب والأجهزة الظاهرية والأجهزة المضمنة و الخوادم.

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 5: نشر تطبيقات وخدمات إنتاجية العامل البعيد.](../media/empower-people-to-work-remotely/remote-workers-step-grid-5.png)](empower-people-to-work-remotely-teams-productivity-apps.md)

تابع مع [الخطوة 5](empower-people-to-work-remotely-teams-productivity-apps.md) للحصول على العاملين المختلطين باستخدام Microsoft 365 الإنتاجية مثل Microsoft Teams.