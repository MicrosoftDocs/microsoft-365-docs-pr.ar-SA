---
title: التجربة Microsoft Defender for Cloud Apps مع Microsoft 365 Defender
description: قم بإعداد Microsoft 365 Defender التجريبية أو الاختبارية لاختبار حل الأمان المصمم لحماية الأجهزة والهوية والبيانات والتطبيقات وتجربة ذلك.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 73601660fc4b7ee2f58748d7e59a10aa53157745
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570118"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>التجربة Microsoft Defender for Cloud Apps مع Microsoft 365 Defender


**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 3 من 3](eval-defender-mcas-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender for Cloud Apps. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-mcas-overview.md).

استخدم الخطوات التالية لإعداد التجربة وتكوينها Microsoft Defender for Cloud Apps.


:::image type="content" source="../../media/defender/m365-defender-mcas-pilot-steps.png" alt-text="خطوات تجريب Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-pilot-steps.png":::
- [الخطوة 1. إنشاء مجموعة تجريبية —تحديد نطاق نشر التجربة لمجموعات معينة من المستخدمين](#step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups)
- [الخطوة 2. تكوين الحماية —التحكم في تطبيق الوصول الشرطي](#step-2-configure-protectionconditional-access-app-control)
- [الخطوة 3. جرب الإمكانات— يمكنك تجربة البرامج التعليمية لحماية بيئتك](#step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment) 

## <a name="step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups"></a>الخطوة 1. إنشاء مجموعة تجريبية —تحديد نطاق نشر التجربة لمجموعات معينة من المستخدمين

Microsoft Defender for Cloud Apps إمكانية تحديد نطاق النشر. يتيح لك تحديد تحديد مجموعات معينة من المستخدمين لكي يتم مراقبتها للتطبيقات أو استبعادها من المراقبة. يمكنك تضمين مجموعات المستخدمين أو استبعادها. لنطاق نشر التجربة، راجع [نشر النطاق](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protectionconditional-access-app-control"></a>الخطوة 2. تكوين الحماية —التحكم في تطبيق الوصول الشرطي

أحد أكثر الحماية التي يمكنك تكوينها قوة هي التحكم في تطبيق الوصول الشرطي. تتطلب هذه الحماية التكامل مع Azure Active Directory (Azure AD). وهو يسمح لك بتطبيق سياسات الوصول المشروط، بما في ذلك السياسات ذات الصلة (مثل طلب أجهزة سليمة)، على تطبيقات السحابة التي قمت بفرض الفرض عليها. 

الخطوة الأولى في Microsoft Defender for Cloud Apps إدارة تطبيقات SaaS هي اكتشاف هذه التطبيقات ثم إضافتها إلى مستأجر Azure AD. إذا كنت بحاجة إلى مساعدة في الاكتشاف، فشاهد اكتشاف تطبيقات [SaaS وإدارتها في شبكتك](/cloud-app-security/tutorial-shadow-it). بعد اكتشاف التطبيقات، [أضف هذه التطبيقات إلى مستأجر Azure AD](/azure/active-directory/manage-apps/add-application-portal).

يمكنك البدء في إدارة هذه التطبيقات من خلال تنفيذ المهام التالية:

- أولا، في Azure AD، قم بإنشاء نهج وصول شرطي جديد وتكوينه إلى "استخدام التحكم في تطبيق الوصول الشرطي". يساعد هذا التكوين على إعادة توجيه الطلب إلى Defender for Cloud Apps. يمكنك إنشاء نهج واحد وإضافة جميع تطبيقات SaaS إلى هذا النهج.
- بعد ذلك، في Defender for Cloud Apps، قم بإنشاء سياسات جلسات العمل. قم بإنشاء نهج واحد لكل عنصر تحكم تريد تطبيقه.

لمزيد من المعلومات، بما في ذلك التطبيقات والعملاء المعتمدين، راجع حماية التطبيقات [باستخدام Microsoft Defender for Cloud Apps التحكم في تطبيق الوصول الشرطي](/cloud-app-security/proxy-intro-aad). 

على سبيل المثال، السياسات[، راجع Microsoft Defender for Cloud Apps المستحسنة لتطبيقات SaaS](../office-365-security/mcas-saas-access-policies.md). وتنبني هذه النهج على مجموعة [](../office-365-security/microsoft-365-policies-configurations.md) من سياسات الوصول إلى الأجهزة والهوية الشائعة الموصى بها كنقطة بداية لجميع العملاء. 

## <a name="step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment"></a>الخطوة 3. جرب الإمكانات— يمكنك تجربة البرامج التعليمية لحماية بيئتك 

تتضمن Microsoft Defender for Cloud Apps الوثائق سلسلة من البرامج التعليمية لمساعدتك على اكتشاف المخاطر وحماية بيئتك. 

جرب البرامج التعليمية ل Defender for Cloud Apps:

- [الكشف عن نشاط مستخدم مريب](/cloud-app-security/tutorial-suspicious-activity)
- [التحقق من المستخدمين الخطرين](/cloud-app-security/tutorial-ueba)
- [التحقق من تطبيقات OAuth المعرضة للمخاطر](/cloud-app-security/investigate-risky-oauth)
- [اكتشاف المعلومات الحساسة وحمايتها](/cloud-app-security/tutorial-dlp)
- [حماية أي تطبيق في مؤسستك في الوقت الحقيقي](/cloud-app-security/tutorial-proxy)
- [حظر تنزيلات المعلومات الحساسة](/cloud-app-security/use-case-proxy-block-session-aad)
- [حماية ملفاتك باستخدام عزل المسؤول](/cloud-app-security/use-case-admin-quarantine)
- [يتطلب مصادقة خطوة بخطوة عند اتخاذ إجراء خطر](/cloud-app-security/tutorial-step-up-authentication)

لمزيد من المعلومات حول البحث المتقدم في Microsoft Defender for Cloud Apps البيانات، راجع [الفيديو](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>الخطوات التالية

[التحقق والاستجابة باستخدام Microsoft 365 Defender في بيئة تجريبية](eval-defender-investigate-respond.md)

العودة إلى نظرة عامة [حول تقييم](eval-defender-mcas-overview.md) Microsoft Defender for Cloud Apps

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)
