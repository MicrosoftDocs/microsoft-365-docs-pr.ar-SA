---
title: Microsoft Defender for Cloud Apps تجريبي مع Microsoft 365 Defender
description: قم بإعداد بيئة الاختبار التجريبي أو التجربة Microsoft 365 Defender لاختبار حل الأمان المصمم لحماية الأجهزة والهوية والبيانات والتطبيقات وتجربة ذلك.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
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
ms.openlocfilehash: 7dbf9154769ab4b97c15dc5fc67593b376ab2f6d
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750331"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>Microsoft Defender for Cloud Apps تجريبي مع Microsoft 365 Defender


**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 3 من 3](eval-defender-mcas-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender for Cloud Apps. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-mcas-overview.md).

استخدم الخطوات التالية لإعداد وتكوين الإصدار التجريبي Microsoft Defender for Cloud Apps.


:::image type="content" source="../../media/defender/m365-defender-mcas-pilot-steps.png" alt-text="خطوات تجربة Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-pilot-steps.png":::
- [الخطوة 1. إنشاء مجموعة الإصدار التجريبي — تحديد نطاق نشر الإصدار التجريبي الخاص بك إلى مجموعات مستخدمين معينة](#step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups)
- [الخطوة 2. تكوين الحماية — التحكم في تطبيق الوصول المشروط](#step-2-configure-protectionconditional-access-app-control)
- [الخطوة 3. جرب القدرات — اطلع على البرامج التعليمية لحماية بيئتك](#step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment) 

## <a name="step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups"></a>الخطوة 1. إنشاء مجموعة الإصدار التجريبي — تحديد نطاق نشر الإصدار التجريبي الخاص بك إلى مجموعات مستخدمين معينة

يمكنك Microsoft Defender for Cloud Apps من تحديد نطاق التوزيع الخاص بك. يسمح لك النطاق بتحديد مجموعات مستخدمين معينة ليتم مراقبتها للتطبيقات أو استبعادها من المراقبة. يمكنك تضمين مجموعات المستخدمين أو استبعادها. لتحديد نطاق النشر التجريبي، راجع [النشر في النطاق](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protectionconditional-access-app-control"></a>الخطوة 2. تكوين الحماية — التحكم في تطبيق الوصول المشروط

أحد أقوى الحماية التي يمكنك تكوينها هو التحكم في تطبيق الوصول المشروط. تتطلب هذه الحماية التكامل مع Azure Active Directory (Azure AD). يسمح لك بتطبيق نهج الوصول المشروط، بما في ذلك النهج ذات الصلة (مثل طلب أجهزة سليمة)، على تطبيقات السحابة التي قمت بعقوباتها. 

الخطوة الأولى في استخدام Microsoft Defender for Cloud Apps لإدارة تطبيقات SaaS هي اكتشاف هذه التطبيقات ثم إضافتها إلى مستأجر Azure AD. إذا كنت بحاجة إلى مساعدة في الاكتشاف، فراجع [اكتشاف تطبيقات SaaS وإدارتها في شبكتك](/cloud-app-security/tutorial-shadow-it). بعد اكتشاف التطبيقات، [أضف هذه التطبيقات إلى مستأجر Azure AD](/azure/active-directory/manage-apps/add-application-portal).

يمكنك البدء في إدارة هذه التطبيقات عن طريق تنفيذ المهام التالية:

- أولا، في Azure AD، قم بإنشاء نهج وصول مشروط جديد وتكوينه إلى "استخدام التحكم في تطبيق الوصول المشروط". يساعد هذا التكوين على إعادة توجيه الطلب إلى Defender for Cloud Apps. يمكنك إنشاء نهج واحد وإضافة جميع تطبيقات SaaS إلى هذا النهج.
- بعد ذلك، في Defender for Cloud Apps، قم بإنشاء نهج جلسة العمل. إنشاء نهج واحد لكل عنصر تحكم تريد تطبيقه.

لمزيد من المعلومات، بما في ذلك التطبيقات والعملاء المعتمدين، راجع [حماية التطبيقات باستخدام Microsoft Defender for Cloud Apps التحكم في تطبيق الوصول المشروط](/cloud-app-security/proxy-intro-aad). 

على سبيل المثال، راجع [نهج Microsoft Defender for Cloud Apps الموصى بها لتطبيقات SaaS](../office-365-security/mcas-saas-access-policies.md). تعتمد هذه النهج على مجموعة من [نهج الهوية والوصول إلى الأجهزة الشائعة](../office-365-security/microsoft-365-policies-configurations.md) التي يوصى بها كنقطة بداية لجميع العملاء. 

## <a name="step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment"></a>الخطوة 3. جرب القدرات — اطلع على البرامج التعليمية لحماية بيئتك 

تتضمن وثائق Microsoft Defender for Cloud Apps سلسلة من البرامج التعليمية لمساعدتك على اكتشاف المخاطر وحماية بيئتك. 

جرب البرامج التعليمية ل Defender for Cloud Apps:

- [الكشف عن نشاط مستخدم مريب](/cloud-app-security/tutorial-suspicious-activity)
- [التحقيق مع المستخدمين المعرضين للمخاطر](/cloud-app-security/tutorial-ueba)
- [التحقيق في تطبيقات OAuth المحفوفة بالمخاطر](/cloud-app-security/investigate-risky-oauth)
- [اكتشاف المعلومات الحساسة وحمايتها](/cloud-app-security/tutorial-dlp)
- [حماية أي تطبيق في مؤسستك في الوقت الحقيقي](/cloud-app-security/tutorial-proxy)
- [حظر تنزيلات المعلومات الحساسة](/cloud-app-security/use-case-proxy-block-session-aad)
- [حماية ملفاتك باستخدام عزل المسؤول](/cloud-app-security/use-case-admin-quarantine)
- [طلب مصادقة خطوة بخطوة عند اتخاذ إجراء محفوف بالمخاطر](/cloud-app-security/tutorial-step-up-authentication)

لمزيد من المعلومات حول التتبع المتقدم في بيانات Microsoft Defender for Cloud Apps، راجع [الفيديو](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>الخطوات التالية

[التحقيق والاستجابة باستخدام Microsoft 365 Defender في بيئة تجريبية](eval-defender-investigate-respond.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)
