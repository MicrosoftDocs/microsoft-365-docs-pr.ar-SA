---
title: الحظر السلوكي للعميل
description: الحظر السلوكي للعميل هو جزء من قدرات الحظر والاحتواء السلوكية في Microsoft Defender لنقطة النهاية
keywords: حظر السلوك والحماية السريعة وسلوك العميل و Microsoft Defender ل Endpoint
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
ms.openlocfilehash: c5a738584f1705365db1c4fad61f190a42d97660
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572297"
---
# <a name="client-behavioral-blocking"></a>الحظر السلوكي للعميل

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>نظرة عامة

الحظر السلوكي للعميل هو أحد مكونات قدرات [الحظر والاحتواء](behavioral-blocking-containment.md) السلوكية في Defender for Endpoint. عند اكتشاف سلوكيات مريبة على الأجهزة (يشار إليها أيضا باسم العملاء أو نقاط النهاية)، يتم حظر التحف (مثل الملفات أو التطبيقات) وفحصها وتصفيها تلقائيا.

:::image type="content" alt-text="حماية العميل والسحابة." source="images/pre-execution-and-post-execution-detection-engines.png" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

تعمل الحماية من الفيروسات بشكل أفضل عند إقرانها مع الحماية السحابية.

## <a name="how-client-behavioral-blocking-works"></a>كيفية عمل الحظر السلوكي للعميل

[برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) الكشف عن سلوك مريب، أو تعليمات برمجية ضارة، أو هجمات بدون ملفات أو داخل الذاكرة، والمزيد على جهاز. عند الكشف عن سلوكيات مريبة، برنامج الحماية من الفيروسات من Microsoft Defender أجهزة العرض هذه السلوكيات المريبة وأشجار العمليات الخاصة بها إلى خدمة الحماية السحابية. يميز التعلم الآلي بين التطبيقات الضارة والسلوكيات الجيدة في المللي ثانية، ويصنف كل قطعة فنية. في الوقت الحقيقي تقريبا، بمجرد أن يتم العثور على أداة ضار، سيتم حظرها على الجهاز.

كلما تم اكتشاف سلوك مريب، يتم إنشاء تنبيه[](alerts-queue.md)، وهو مرئي في أثناء الكشف عن الهجوم وتوقفه، يتم تشغيل التنبيهات، مثل "تنبيه الوصول الأولي"، وظهرت في مدخل [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) (سابقا Microsoft 365 Defender).

يعد الحظر السلوكي للعميل فعالا لأنه لا يساعد فقط على منع بدء أي هجوم، بل يمكن أن يساعد في إيقاف هجوم بدأ تنفيذه. ومع حظر [حلقة](feedback-loop-blocking.md) الملاحظات (إمكانية أخرى للحظر السلوكي والاحتواء)، يتم منع الهجمات على الأجهزة الأخرى في مؤسستك.

## <a name="behavior-based-detections"></a>الاكتشافات المستندة إلى السلوك

يتم تسمية الاكتشافات المستندة إلى السلوك وفقا ل [MITRE ATT&مصفوفة CK للمؤسسات](https://attack.mitre.org/matrices/enterprise). تساعد اصطلاحات التسمية في تحديد مرحلة الهجوم حيث تم ملاحظة السلوك الضار:

|تكتيك|اسم خطر الكشف|
|---|---|
|الوصول الأولي|`Behavior:Win32/InitialAccess.*!ml`|
|التنفيذ|`Behavior:Win32/Execution.*!ml`|
|الاستمرار|`Behavior:Win32/Persistence.*!ml`|
|تصاعد الامتيازات|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|التجنب الدفاعي|`Behavior:Win32/DefenseEvasion.*!ml`|
|الوصول إلى بيانات الاعتماد|`Behavior:Win32/CredentialAccess.*!ml`|
|اكتشاف|`Behavior:Win32/Discovery.*!ml`|
|الحركة اللاحقة|`Behavior:Win32/LateralMovement.*!ml`|
|المجموعة|`Behavior:Win32/Collection.*!ml`|
|الأمر والتحكم|`Behavior:Win32/CommandAndControl.*!ml`|
|Exfiltration|`Behavior:Win32/Exfiltration.*!ml`|
|التأثير|`Behavior:Win32/Impact.*!ml`|
|غير تصنيف|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> لمعرفة المزيد حول التهديدات المحددة، راجع **[نشاط التهديدات العالمية الأخير](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>تكوين الحظر السلوكي للعميل

إذا كانت مؤسستك تستخدم Defender for Endpoint، يتم تمكين الحظر السلوكي للعميل بشكل افتراضي. ومع ذلك، للاستفادة من جميع إمكانيات Defender لنقطة النهاية، بما [](behavioral-blocking-containment.md)في ذلك الحظر السلوكي والاحتواء، تأكد من تمكين الميزات التالية وإمكانيات Defender لنقطة النهاية وتكوينها:

- [Defender لخط أساسيات نقطة النهاية](configure-machines-security-baseline.md)
- [الأجهزة المجهزة إلى Defender لنقطة النهاية](onboard-configure.md)
- [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)
- [الحد من سطح الهجوم](attack-surface-reduction.md)
- [حماية الجيل التالي](configure-microsoft-defender-antivirus-features.md) (الحماية من الفيروسات والحماية من البرامج الضارة وإمكانيات الحماية من المخاطر الأخرى)
