---
title: تحسين عمليات نشر قاعدة ASR واكتشافها
description: تحسين قواعد الحد من الهجمات (ASR) لتحديد عمليات استغلال البرامج الضارة النموذجية ومنعها.
keywords: onboard, Intune management, Microsoft Defender for Endpoint, Microsoft Defender, Windows Defender, attack surface reduction, ASR, security baseline
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bd5b88c5d43f2ec20c200ee55458e2ef204775ae
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570456"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>تحسين عمليات نشر قاعدة ASR واكتشافها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[تحدد قواعد الحد من سطح الهجوم (ASR)](./attack-surface-reduction.md) عمليات استغلال البرامج الضارة النموذجية وتمنعها. فهي تتحكم في وقت تشغيل التعليمات البرمجية الضارة المحتملة وكيفية تشغيلها. على سبيل المثال، يمكنهم منع JavaScript أو VBScript من بدء تشغيل قابل للتنفيذ تم تنزيله، وحظر مكالمات Win32 API من وحدات Office الماكرو، وحظر العمليات التي يتم تشغيلها من محركات أقراص USB.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="بطاقة إدارة سطح الهجوم.":::
<br>
*بطاقة إدارة سطح الهجوم*

بطاقة *إدارة سطح الهجوم* هي نقطة إدخال إلى الأدوات Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">المدخل</a> الذي يمكنك استخدامه ل:

* فهم كيفية نشر قواعد ASR حاليا في مؤسستك.
* راجع اكتشافات ASR وحدد الاكتشافات غير الصحيحة المحتملة.
* قم بتحليل تأثير الاستثناءات وإنشاء قائمة مسارات الملفات التي يجب استبعادها.

حدد **الانتقال إلى إدارة سطح الهجوم** \> **تقارير** \> الحد من سطح **الهجوم قواعد** \> **إضافة استثناءات**. من هناك، يمكنك الانتقال إلى مقاطع أخرى من Microsoft 365 Defender المدخل.

![علامة التبويب "إضافة استثناءات" في صفحة قواعد تقليل مساحة الهجوم Microsoft 365 Defender المدخل.](images/secconmgmt_asr_m365exlusions.png)<br>
علامة ***التبويب "إضافة استثناءات**" في صفحة قواعد تقليل مساحة الهجوم في Microsoft 365 Defender مدخل*

> [!NOTE]
> للوصول إلى Microsoft 365 Defender، تحتاج إلى ترخيص Microsoft 365 E3 أو E5، إلى حساب له أدوار معينة على Azure Active Directory. [اقرأ حول الأذونات والتراخيص المطلوبة](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions).

لمزيد من المعلومات حول نشر قاعدة ASR <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">في</a> Microsoft 365 Defender، راجع مراقبة عمليات نشر قاعدة [ASR واكتشافها وإدارتها](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections).

**المواضيع ذات الصلة**

* [التأكد من تكوين أجهزتك بشكل صحيح](configure-machines.md)
* [الحصول على الأجهزة المجهزة في Microsoft Defender لنقطة النهاية](configure-machines-onboarding.md)
* [مراقبة التوافق مع خط أساسي أمان نقطة النهاية ل Microsoft Defender](configure-machines-security-baseline.md)
