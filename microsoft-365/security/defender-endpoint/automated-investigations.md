---
title: استخدام الاستقصاءات التلقائية للتحقق من التهديدات و إصلاحها
description: فهم تدفق التحقيق التلقائي في Microsoft Defender لنقطة النهاية.
keywords: تلقائي، التحقيق، الكشف، Microsoft Defender ل Endpoint
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.date: 11/24/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: 31b2a7b41c26bdba22e6f364e517471e31e9115c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63571533"
---
# <a name="overview-of-automated-investigations"></a>نظرة عامة على عمليات البحث التلقائية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

هل تريد الاطلاع على كيفية عمله؟ شاهد الفيديو التالي:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

تستخدم التقنية في التحقيق التلقائي خوارزميات فحص متنوعة والاستناد إلى العمليات التي يستخدمها محللو الأمان. تم تصميم قدرات AIR لفحص التنبيهات واتخاذ إجراء فوري لحل الخروقات. تخفض قدرات AIR حجم التنبيهات بشكل ملحوظ، مما يسمح لعمليات الأمان بالتركيز على تهديدات أكثر تعقيدا وغيرها من المبادرات ذات القيمة العالية. يتم تعقب جميع إجراءات المعالجة، سواء كانت معلقة أو مكتملة، في [مركز الإجراءات](auto-investigation-action-center.md). في مركز الإجراءات، يتم الموافقة على الإجراءات المعلقة (أو رفضها)، ويمكن التراجع عن الإجراءات المكتملة إذا لزم الأمر.

توفر هذه المقالة نظرة عامة على AIR وتتضمن ارتباطات إلى الخطوات التالية وموارد إضافية.

> [!TIP]
> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>كيفية بدء التحقيق التلقائي

يمكن أن يبدأ التحقيق التلقائي عند تشغيل تنبيه أو عندما يبدأ عامل أمان التحقيق.

<br>

****

|الحالة|ماذا يحدث|
|---|---|
|يتم تشغيل تنبيه|بشكل عام، يبدأ التحقيق التلقائي عند تشغيل تنبيه[](review-alerts.md)، وإنشاء حادث.[](view-incidents-queue.md) على سبيل المثال، افترض أن ملفا ضارا موجود على جهاز. عند اكتشاف هذا الملف، يتم تشغيل تنبيه، كما يتم إنشاء حادث. تبدأ عملية تحقيق تلقائية على الجهاز. مع إنشاء تنبيهات أخرى بسبب الملف نفسه على الأجهزة الأخرى، تضاف إلى الحادث المقترن ونم إلى التحقيق التلقائي.|
|يتم بدء التحقيق يدويا|يمكن بدء إجراء تحقيق تلقائي يدويا بواسطة فريق عمليات الأمان. على سبيل المثال، لنفترض أن عامل تشغيل الأمان يراجع قائمة بالأجهزة ويلاحظ أن الجهاز لديه مستوى عال من المخاطر. يمكن لعامل الأمان تحديد الجهاز في القائمة لفتح القائمة من القائمة من القائمة، ثم تحديد **بدء التحقيق التلقائي**.|
|

## <a name="how-an-automated-investigation-expands-its-scope"></a>كيفية توسيع التحقيق التلقائي لنطاقه

أثناء تشغيل التحقيق، تضاف أي تنبيهات أخرى تم إنشاؤها من الجهاز إلى تحقيق تلقائي جار حتى اكتمال هذا التحقيق. بالإضافة إلى ذلك، إذا تم رؤية الخطر نفسه على أجهزة أخرى، تضاف هذه الأجهزة إلى التحقيق.

إذا تم رؤية كيان غير مهين في جهاز آخر، فإن عملية التحقيق التلقائية توسع نطاقه لتضمين هذا الجهاز، ويبدأ تشغيل مصنف أمان عام على هذا الجهاز. إذا تم العثور على 10 أجهزة أو أكثر أثناء عملية التوسيع هذه من الكيان نفسه، فهذا يعني أن إجراء التوسيع هذا يتطلب موافقة، وهو مرئي على علامة التبويب **الإجراءات المعلقة** .

## <a name="how-threats-are-remediated"></a>كيفية معالجة التهديدات

عند تشغيل التنبيهات، و تشغيل التحقيق التلقائي، يتم إنشاء قرار لكل قطعة من الإثباتات التي يتم التحقق منها. يمكن أن تكون الأحكام:

- *ضار*؛
- *مريبا؛* أو
- *لم يتم العثور على أي تهديدات*.

عند الوصول إلى الأحكام، يمكن أن تؤدي عمليات التحقيق التلقائية إلى إجراء واحد أو أكثر من إجراءات الإصلاح. تتضمن أمثلة إجراءات الإصلاح إرسال ملف إلى الفحص، أو إيقاف خدمة، أو إزالة مهمة مجدولة، والمزيد. لمعرفة المزيد، راجع [إجراءات المعالجة](manage-auto-investigation.md#remediation-actions).

استنادا إلى [مستوى التنفيذ التلقائي](automation-levels.md) الذي تم تعيينه لمنظمتك، بالإضافة إلى إعدادات الأمان الأخرى، يمكن أن تحدث إجراءات المعالجة تلقائيا أو فقط عند موافقة فريق عمليات الأمان. تتضمن إعدادات الأمان الإضافية التي يمكن أن تؤثر على المعالجة التلقائية الحماية من التطبيقات التي يحتمل أن تكون غير مرغوب [فيها](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) (PUA).

يتم تعقب جميع إجراءات المعالجة، سواء كانت معلقة أو مكتملة، في [مركز الإجراءات](auto-investigation-action-center.md). إذا لزم الأمر، يمكن لفريق عمليات الأمان التراجع عن إجراء إصلاحي. لمعرفة المزيد، راجع [مراجعة إجراءات المعالجة والموافقة عليها بعد إجراء تحقيق تلقائي](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> اطلع على صفحة التحقيق الموحدة الجديدة في Microsoft 365 Defender الإلكتروني. لمعرفة المزيد، راجع [(NEW!) صفحة التحقيق الموحدة](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>متطلبات AIR

يجب أن يكون لدى مؤسستك Defender for Endpoint (راجع [الحد الأدنى لمتطلبات Microsoft Defender لنقطة النهاية](minimum-requirements.md)).

> [!NOTE]
> يتطلب إجراء الاستجابات والتحري التلقائي برنامج الحماية من الفيروسات من Microsoft Defender التشغيل في الوضع السلبي أو الوضع النشط. إذا برنامج الحماية من الفيروسات من Microsoft Defender أو تم إلغاء تثبيته، لن يعمل "التحقيق التلقائي" و"الاستجابة" بشكل صحيح.

حاليا، تدعم AIR إصدارات نظام التشغيل التالية فقط:

- Windows Server 2012 R2 (معاينة)
- Windows Server 2016 (Preview)
- Windows Server 2019
- Windows Server 2022
- Windows 10، الإصدار 1709 (إصدار نظام التشغيل 16299.1085 مع [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) أو إصدار أحدث
- Windows 10، الإصدار 1803 (إصدار نظام التشغيل 17134.704 مع [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) أو إصدار أحدث
- Windows 10 الإصدار [1803 أو](/windows/release-information/status-windows-10-1809-and-windows-server-2019) الإصدارات الأحدث
- Windows 11

## <a name="next-steps"></a>الخطوات التالية

- [معرفة المزيد حول مستويات التنفيذ التلقائي](automation-levels.md)
- [راجع الدليل التفاعلي: التحقق من التهديدات وتصفياتها باستخدام Microsoft Defender لنقطة النهاية](https://aka.ms/MDATP-IR-Interactive-Guide)
- [تكوين قدرات المعالجة والتحري التلقائية في Microsoft Defender لنقطة النهاية](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>راجع أيضًا

- [حماية PUA](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [إجراء عمليات التحقيق والاستجابة التلقائية في Microsoft Defender Office 365](/microsoft-365/security/office-365-security/office-365-air)
- [إجراء عمليات التحقيق والاستجابة التلقائية في Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
