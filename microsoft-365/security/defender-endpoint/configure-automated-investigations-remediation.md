---
title: تكوين قدرات التحقيق والمعالجة التلقائية
description: إعداد قدرات التحقيق والمعالجة التلقائية في Microsoft Defender لنقطة النهاية.
keywords: تكوين وإعداد وتلقائية والتحقيق والكشف والتنبيهات والمعالجة والاستجابة
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
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: c82962640f992f892e21205dcfc0725a79001f10
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437863"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>تكوين قدرات التحقيق والمعالجة التلقائية في Microsoft Defender لنقطة النهاية

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

إذا كانت مؤسستك تستخدم [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/) (Defender لنقطة النهاية)، يمكن أن توفر [قدرات التحقيق والمعالجة التلقائية](/microsoft-365/security/defender-endpoint/automated-investigations) الوقت والجهد لفريق عمليات الأمان. كما هو موضح في [منشور المدونة هذا](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946)، تحاكي هذه القدرات الخطوات المثالية التي يتخذها محلل الأمان للتحقيق في التهديدات ومعالجتها. [تعرف على المزيد حول التحقيق التلقائي والمعالجة](/microsoft-365/security/defender-endpoint/automated-investigations).

لتكوين التحقيق التلقائي والمعالجة:

1. [تشغيل الميزات](#turn-on-automated-investigation-and-remediation)؛ و
2. [إعداد مجموعات الأجهزة](#set-up-device-groups).

## <a name="turn-on-automated-investigation-and-remediation"></a>تشغيل التحقيق التلقائي والمعالجة

1. كمسؤول عام أو مسؤول أمان، انتقل إلى مدخل Microsoft 365 Defender (<https://security.microsoft.com>) وسجل الدخول.
2. في جزء التنقل، اختر **الإعدادات**.
3. حدد **نقاط النهاية**، ثم حدد **الميزات المتقدمة**.
4. قم بتشغيل كل من **التحقيق التلقائي** **وحل التنبيهات تلقائيا**.

## <a name="set-up-device-groups"></a>إعداد مجموعات الأجهزة

1. في مدخل Microsoft 365 Defender (<https://security.microsoft.com>)، في صفحة **الإعدادات**، ضمن **الأذونات**، حدد **مجموعات الأجهزة**.
2. حدد **+ إضافة مجموعة أجهزة**.
3. إنشاء مجموعة أجهزة واحدة على الأقل، كما يلي:
   - حدد اسما ووصفا لمجموعة الأجهزة.
   - في **قائمة مستوى التنفيذ التلقائي**، حدد مستوى، مثل **"كامل- معالجة التهديدات تلقائيا**". يحدد مستوى التشغيل التلقائي ما إذا كانت إجراءات المعالجة يتم اتخاذها تلقائيا، أو فقط عند الموافقة. لمعرفة المزيد، راجع [مستويات الأتمتة في التحقيق التلقائي والمعالجة](automation-levels.md).
   - في قسم **الأعضاء** ، استخدم شرطا واحدا أو أكثر لتحديد الأجهزة وتضمينها.
   - في علامة التبويب **"User access** "، حدد [مجموعات Azure Active Directory](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context) التي يجب أن يكون لديها حق الوصول إلى مجموعة الأجهزة التي تقوم بإنشائه.
4. حدد **"تم"** عند الانتهاء من إعداد مجموعة الأجهزة.

## <a name="next-steps"></a>الخطوات التالية

- [تفضل بزيارة مركز الصيانة لعرض إجراءات المعالجة المعلقة والمكتملة](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [مراجعة الإجراءات المعلقة والموافقة عليها](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>راجع أيضًا

- [معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)
