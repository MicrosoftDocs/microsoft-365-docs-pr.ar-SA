---
title: استخدام التحقيقات التلقائية للتحقيق في التهديدات ومعالجتها
description: فهم تدفق التحقيق التلقائي في Microsoft Defender لنقطة النهاية.
keywords: تلقائي، التحقيق، الكشف، Microsoft Defender لنقطة النهاية
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
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: cfc3ebb1a32487bf2b32074059091c0d4d3517ec
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535769"
---
# <a name="overview-of-automated-investigations"></a>نظرة عامة على التحقيقات التلقائية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

هل تريد معرفة كيفية عملها؟ شاهد الفيديو التالي:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

تستخدم التقنية في التحقيق التلقائي خوارزميات فحص مختلفة وتستند إلى العمليات التي يستخدمها محللو الأمان. تم تصميم قدرات AIR لفحص التنبيهات واتخاذ إجراءات فورية لحل الخروقات. تقلل قدرات AIR بشكل كبير من حجم التنبيه، ما يسمح للعمليات الأمنية بالتركيز على التهديدات الأكثر تطورا والمبادرات الأخرى عالية القيمة. يتم تعقب جميع إجراءات المعالجة، سواء كانت معلقة أو مكتملة، في [مركز الصيانة](auto-investigation-action-center.md). في مركز الصيانة، تتم الموافقة على الإجراءات المعلقة (أو رفضها)، ويمكن التراجع عن الإجراءات المكتملة إذا لزم الأمر.

توفر هذه المقالة نظرة عامة على AIR وتتضمن ارتباطات إلى الخطوات التالية والموارد الإضافية.

> [!TIP]
> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>كيفية بدء التحقيق التلقائي

يمكن أن يبدأ التحقيق التلقائي عند تشغيل تنبيه أو عندما يبدأ عامل تشغيل الأمان التحقيق.

|الحاله|ما يحدث|
|---|---|
|يتم تشغيل تنبيه|بشكل عام، يبدأ التحقيق التلقائي عند تشغيل [تنبيه](review-alerts.md) ، ويتم إنشاء [حدث](view-incidents-queue.md) . على سبيل المثال، افترض وجود ملف ضار على جهاز. عند الكشف عن هذا الملف، يتم تشغيل تنبيه، ويتم إنشاء الحدث. تبدأ عملية التحقيق التلقائي على الجهاز. كما يتم إنشاء تنبيهات أخرى بسبب نفس الملف على أجهزة أخرى، تتم إضافتها إلى الحادث المرتبط والتحقيق التلقائي.|
|يتم بدء التحقيق يدويا|يمكن بدء التحقيق التلقائي يدويا من قبل فريق عمليات الأمان. على سبيل المثال، افترض أن عامل تشغيل الأمان يراجع قائمة بالأجهزة ويلاحظ أن الجهاز لديه مستوى عال من المخاطر. يمكن لمشغل الأمان تحديد الجهاز في القائمة لفتح القائمة المنبثقة الخاصة به، ثم تحديد **بدء التحقيق التلقائي**.|

## <a name="how-an-automated-investigation-expands-its-scope"></a>كيف يوسع التحقيق التلقائي نطاقه

في أثناء تشغيل التحقيق، تتم إضافة أي تنبيهات أخرى تم إنشاؤها من الجهاز إلى تحقيق تلقائي مستمر حتى يكتمل هذا التحقيق. بالإضافة إلى ذلك، إذا تمت رؤية نفس التهديد على أجهزة أخرى، تتم إضافة هذه الأجهزة إلى التحقيق.

إذا تم رؤية كيان متجنى عليه في جهاز آخر، فإن عملية التحقيق التلقائي توسع نطاقها لتشمل هذا الجهاز، ويبدأ دليل مبادئ الأمان العام على هذا الجهاز. إذا تم العثور على 10 أجهزة أو أكثر أثناء عملية التوسيع هذه من نفس الكيان، فإن إجراء التوسيع هذا يتطلب موافقة، ويكون مرئيا في علامة تبويب **الإجراءات المعلقة** .

## <a name="how-threats-are-remediated"></a>كيفية معالجة التهديدات

مع تشغيل التنبيهات، وإجراء تحقيق تلقائي، يتم إصدار حكم لكل قطعة من الأدلة التي يتم التحقيق فيها. يمكن أن تكون الأحكام:

- *ضار*؛
- *مريب*؛ او
- *لم يتم العثور على أي تهديدات*.

ومع التوصل إلى الأحكام، يمكن أن تؤدي التحقيقات التلقائية إلى إجراء واحد أو أكثر من إجراءات المعالجة. تتضمن أمثلة إجراءات المعالجة إرسال ملف إلى العزل وإيقاف خدمة وإزالة مهمة مجدولة والمزيد. لمعرفة المزيد، راجع [إجراءات المعالجة](manage-auto-investigation.md#remediation-actions).

اعتمادا على [مستوى التشغيل التلقائي](automation-levels.md) المعين لمؤسستك، بالإضافة إلى إعدادات الأمان الأخرى، يمكن أن تحدث إجراءات المعالجة تلقائيا أو فقط بناء على موافقة فريق عمليات الأمان. تتضمن إعدادات الأمان الإضافية التي يمكن أن تؤثر على المعالجة التلقائية [الحماية من التطبيقات التي قد تكون غير مرغوب فيها](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) (PUA).

يتم تعقب جميع إجراءات المعالجة، سواء كانت معلقة أو مكتملة، في [مركز الصيانة](auto-investigation-action-center.md). إذا لزم الأمر، يمكن لفريق عمليات الأمان التراجع عن إجراء المعالجة. لمعرفة المزيد، راجع [مراجعة إجراءات المعالجة والموافقة عليها بعد إجراء تحقيق تلقائي](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> تحقق من صفحة التحقيق الموحدة الجديدة في مدخل Microsoft 365 Defender. لمعرفة المزيد، راجع [صفحة التحقيق الموحد](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>متطلبات AIR

يجب أن يتضمن اشتراكك [Defender لنقطة النهاية](microsoft-defender-endpoint.md) أو [Defender for Business](../defender-business/mdb-overview.md).

> [!NOTE]
> يتطلب التحقيق التلقائي والاستجابة برنامج الحماية من الفيروسات من Microsoft Defender لتشغيلها في الوضع الخامل أو الوضع النشط. إذا تم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيتها، فلن يعمل التحقيق التلقائي والاستجابة بشكل صحيح.

حاليا، يدعم AIR إصدارات نظام التشغيل التالية فقط:

- Windows Server 2012 R2 (معاينة)
- Windows Server 2016 (معاينة)
- Windows Server 2019
- Windows Server 2022
- Windows 10، الإصدار 1709 (إصدار نظام التشغيل 16299.1085 مع [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) أو إصدار أحدث
- Windows 10، الإصدار 1803 (إصدار نظام التشغيل 17134.704 مع [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) أو إصدار أحدث
- Windows 10، الإصدار [1803](/windows/release-information/status-windows-10-1809-and-windows-server-2019) أو أحدث
- Windows 11

## <a name="next-steps"></a>الخطوات التالية

- [معرفة المزيد حول مستويات التشغيل التلقائي](automation-levels.md)
- [راجع الدليل التفاعلي: التحقيق في التهديدات ومعالجتها باستخدام Microsoft Defender لنقطة النهاية](https://aka.ms/MDATP-IR-Interactive-Guide)
- [تكوين قدرات التحقيق والمعالجة التلقائية في Microsoft Defender لنقطة النهاية](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>راجع أيضًا

- [حماية PUA](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [التحقيق التلقائي والاستجابة في Microsoft Defender لـ Office 365](/microsoft-365/security/office-365-security/office-365-air)
- [التحقيق التلقائي والاستجابة في Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
