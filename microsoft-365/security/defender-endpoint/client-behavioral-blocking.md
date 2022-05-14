---
title: الحظر السلوكي للعميل
description: الحظر السلوكي للعميل هو جزء من قدرات الحظر السلوكي والاحتواء في Microsoft Defender لنقطة النهاية
keywords: الحظر السلوكي، والحماية السريعة، وسلوك العميل، Microsoft Defender لنقطة النهاية
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 95c138b6613d610520a4e6870ae7a59b46159f5d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418729"
---
# <a name="client-behavioral-blocking"></a>الحظر السلوكي للعميل

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصه**
- بالنسبة لنظام التشغيل

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>نظرة عامة

الحظر السلوكي للعميل هو أحد مكونات [قدرات الحظر السلوكي والاحتواء](behavioral-blocking-containment.md) في Defender لنقطة النهاية. كما يتم الكشف عن السلوكيات المشبوهة على الأجهزة (يشار إليها أيضا باسم العملاء أو نقاط النهاية)، يتم حظر البيانات الاصطناعية (مثل الملفات أو التطبيقات) والتحقق منها ومعالجتها تلقائيا.

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="حماية السحابة والعميل" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

تعمل الحماية من الفيروسات بشكل أفضل عند إقرانها بحماية السحابة.

## <a name="how-client-behavioral-blocking-works"></a>كيفية عمل الحظر السلوكي للعميل

[يمكن برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) الكشف عن السلوك المشبوه، والتعليمات البرمجية الضارة، والهجمات بدون ملف وفي الذاكرة، والمزيد على الجهاز. عند الكشف عن السلوكيات المشبوهة، برنامج الحماية من الفيروسات من Microsoft Defender مراقبة وإرسال هذه السلوكيات المشبوهة وأشجار العمليات الخاصة بها إلى خدمة حماية السحابة. يميز التعلم الآلي بين التطبيقات الضارة والسلوكيات الجيدة في غضون مللي ثانية، ويصنف كل أداة. في الوقت الحقيقي تقريبا، بمجرد العثور على البيانات الاصطناعية لتكون ضارة، يتم حظرها على الجهاز.

كلما تم الكشف عن سلوك مريب، يتم إنشاء [تنبيه](alerts-queue.md) ويكون مرئيا أثناء الكشف عن الهجوم وتوقفه؛ يتم تشغيل التنبيهات، مثل "تنبيه الوصول الأولي"، وتظهر في [مدخل Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) (سابقا Microsoft 365 Defender).

الحظر السلوكي للعميل فعال لأنه لا يساعد فقط على منع بدء الهجوم، بل يمكن أن يساعد في إيقاف الهجوم الذي بدأ تنفيذه. ومع [حظر حلقة الملاحظات](feedback-loop-blocking.md) (إمكانية أخرى للحظر السلوكي والاحتواء)، يتم منع الهجمات على الأجهزة الأخرى في مؤسستك.

## <a name="behavior-based-detections"></a>عمليات الكشف المستندة إلى السلوك

تتم تسمية عمليات الكشف المستندة إلى السلوك وفقا [لمصفوفة MITRE ATT&CK ل Enterprise](https://attack.mitre.org/matrices/enterprise). يساعد اصطلاح التسمية في تحديد مرحلة الهجوم التي تمت فيها ملاحظة السلوك الضار:

|تكتيك|اسم التهديد للكشف|
|---|---|
|الوصول الأولي|`Behavior:Win32/InitialAccess.*!ml`|
|تنفيذ|`Behavior:Win32/Execution.*!ml`|
|استمرار|`Behavior:Win32/Persistence.*!ml`|
|تصعيد الامتيازات|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|التهرب الدفاعي|`Behavior:Win32/DefenseEvasion.*!ml`|
|الوصول إلى بيانات الاعتماد|`Behavior:Win32/CredentialAccess.*!ml`|
|اكتشاف|`Behavior:Win32/Discovery.*!ml`|
|الحركة الجانبية|`Behavior:Win32/LateralMovement.*!ml`|
|جمع|`Behavior:Win32/Collection.*!ml`|
|الأمر والتحكم|`Behavior:Win32/CommandAndControl.*!ml`|
|النقل غير المصرح به|`Behavior:Win32/Exfiltration.*!ml`|
|اثر|`Behavior:Win32/Impact.*!ml`|
|غير مصنف|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> لمعرفة المزيد حول تهديدات محددة، راجع **[نشاط التهديد العالمي الأخير](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>تكوين الحظر السلوكي للعميل

إذا كانت مؤسستك تستخدم Defender لنقطة النهاية، يتم تمكين الحظر السلوكي للعميل بشكل افتراضي. ومع ذلك، للاستفادة من جميع قدرات Defender لنقطة النهاية، بما في ذلك [الحظر السلوكي والاحتواء](behavioral-blocking-containment.md)، تأكد من تمكين الميزات والقدرات التالية ل Defender لنقطة النهاية وتكوينها:

- [Defender لأساسيات نقطة النهاية](configure-machines-security-baseline.md)
- [الأجهزة التي تم إلحاقها ب Defender لنقطة النهاية](onboard-configure.md)
- [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)
- [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)
- [حماية الجيل التالي](configure-microsoft-defender-antivirus-features.md) (الحماية من الفيروسات والبرامج الضارة وغيرها من قدرات الحماية من التهديدات)

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)
