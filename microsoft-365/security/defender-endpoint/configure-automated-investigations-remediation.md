---
title: تكوين قدرات المعالجة والتحري التلقائية
description: قم بإعداد قدرات المعالجة والتحري التلقائية في Microsoft Defender لنقطة النهاية.
keywords: تكوين، إعداد، تلقائي، التحقيق، الكشف، التنبيهات، المعالجة، الاستجابة
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.date: 01/27/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: f8416d480731c133e93a0a6e22e5b5b32913ba57
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575759"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>تكوين قدرات المعالجة والتحري التلقائية في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

إذا كانت مؤسستك تستخدم [Microsoft Defender ل Endpoint](/windows/security/threat-protection/) (Defender for Endpoint)، يمكن [](/microsoft-365/security/defender-endpoint/automated-investigations) أن توفر قدرات الإصلاح والتحري التلقائية الوقت والجهد في فريق عمليات الأمان. كما هو موضح في [منشور](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946) المدونة هذا، تحاكي هذه الإمكانات الخطوات المثالية التي يتخذها محلل الأمان للتحقق من التهديدات و إصلاحها. [تعرف على المزيد حول المعالجة والتحري التلقائي](/microsoft-365/security/defender-endpoint/automated-investigations).

لتكوين المعالجة والتحري التلقائي:

1. [تشغيل الميزات](#turn-on-automated-investigation-and-remediation)؛ و
2. [إعداد مجموعات الأجهزة](#set-up-device-groups).

## <a name="turn-on-automated-investigation-and-remediation"></a>تشغيل المعالجة والتحري التلقائي

1. كمسؤول عام أو مسؤول أمان، انتقل إلى Microsoft 365 Defender (<https://security.microsoft.com>) ثم سجل الدخول.
2. في جزء التنقل **، اختر الإعدادات**.
3. في المقطع **عام** ، حدد **الميزات المتقدمة**.
4. قم تشغيل كل من **"التحقيق التلقائي** " **و"حل التنبيهات تلقائيا**".

## <a name="set-up-device-groups"></a>إعداد مجموعات الأجهزة

1. في Microsoft 365 Defender (<https://security.microsoft.com>)، **على الإعدادات،** ضمن أذونات، حدد **مجموعات الأجهزة**.
2. حدد **+ إضافة مجموعة أجهزة**.
3. أنشئ مجموعة أجهزة واحدة على الأقل، كما يلي:
   - حدد اسما ووصفا لمجموعة الأجهزة.
   - في القائمة **مستوى التنفيذ التلقائي،** حدد مستوى، مثل تهديدات المعالجة الكاملة **تلقائيا**. يحدد مستوى التنفيذ التلقائي ما إذا كان يتم اتخاذ إجراءات المعالجة تلقائيا، أو عند الموافقة فقط. لمعرفة المزيد، راجع [مستويات التنفيذ التلقائي في المعالجة والتحري التلقائي](automation-levels.md).
   - في قسم **الأعضاء** ، استخدم أحد الشروط أو أكثر لتعريف الأجهزة وتضمينها.
   - على علامة **التبويب وصول المستخدم** ، حدد [مجموعات Azure Active Directory](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context) التي يجب أن يكون لها حق الوصول إلى مجموعة الأجهزة التي تقوم بإنشاءها.
4. حدد **تم** عند الانتهاء من إعداد مجموعة جهازك.

## <a name="next-steps"></a>الخطوات التالية

- [تفضل بزيارة مركز الإجراءات لعرض إجراءات المعالجة المعلقة والمكتملة](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [مراجعة الإجراءات المعلقة والموافقة عليها](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>راجع أيضًا

- [معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)
