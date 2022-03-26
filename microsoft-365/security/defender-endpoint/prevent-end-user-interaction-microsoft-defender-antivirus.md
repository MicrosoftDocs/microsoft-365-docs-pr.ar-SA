---
title: إخفاء واجهة برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك إخفاء لوحة الحماية من الفيروسات والتهديدات في أمن Windows التطبيق.
keywords: تأمين واجهة المستخدم، وضع الرأس، إخفاء التطبيق، إخفاء الإعدادات، إخفاء الواجهة
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: d54d8ecf2d0c365168ae636cbe85ef1da9cfb6b1
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63574256"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>منع المستخدمين من رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكنك استخدام "نهج المجموعة" لمنع المستخدمين في نقاط النهاية من رؤية برنامج الحماية من الفيروسات من Microsoft Defender المجموعة. يمكنك أيضا منعهم من وضع عمليات المسح الضوئية في وضع انتظار.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>إخفاء واجهة برنامج الحماية من الفيروسات من Microsoft Defender

في Windows 10، ستخفي الإصدارات 1703، إخفاء الواجهة إعلامات برنامج الحماية من الفيروسات من Microsoft Defender ومنع ظهور لوحة الحماية من المخاطر & الفيروسات في تطبيق أمن Windows.

مع تعيين الإعداد إلى **تمكين**:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="لقطة شاشة أمن Windows بدون أيقونة الدرع وأقسام الحماية من الفيروسات والتهديدات.":::

مع تعيين الإعداد إلى **معطل** أو غير مكون:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="لقطة شاشة أمن Windows مع أيقونة الدرع وأقسام الحماية من المخاطر.":::

> [!NOTE]
> سيمنع إخفاء الواجهة أيضا برنامج الحماية من الفيروسات من Microsoft Defender الإعلامات من الظهور على نقطة النهاية. سيبقى Microsoft Defender الخاص بإشعارات نقطة النهاية في الظهور. يمكنك أيضا تكوين الإعلامات التي تظهر على [نقاط النهاية بشكل فردي](configure-notifications-microsoft-defender-antivirus.md)

في الإصدارات السابقة من Windows 10، سيخفي الإعداد Windows عميل Defender. إذا حاول المستخدم فتحه، سيتلقى تحذيرا يقول "قام مسؤول النظام بتقييد الوصول إلى هذا التطبيق".

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="رسالة تحذير عند تمكين وضع الرأس في Windows 10، إصدارات أقدم من 1703":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>استخدام "نهج المجموعة" لإخفاء واجهة Microsoft Defender AV عن المستخدمين

1. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. باستخدام **محرر إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات > برنامج الحماية من الفيروسات من Microsoft Defender > العميل**.

5. انقر نقرا مزدوجا فوق إعداد تمكين وضع **واجهة المستخدم** بدون رأس، ثم قم بتعيين الخيار **إلى تمكين**. انقر فوق **موافق**.

راجع [منع المستخدمين من](configure-local-policy-overrides-microsoft-defender-antivirus.md) تعديل إعدادات النهج محليا للحصول على مزيد من الخيارات حول منع المستخدمين من تعديل الحماية على أجهزة الكمبيوتر الخاصة بهم.

## <a name="prevent-users-from-pausing-a-scan"></a>منع المستخدمين من وضع الفحص

يمكنك منع المستخدمين من وضع عمليات الفحص بشكل توقف، والتي قد تكون مفيدة لضمان عدم مقاطعة عمليات الفحص المجدولة أو عند الطلب من قبل المستخدمين.

> [!NOTE]
> هذا الإعداد غير معتمد على Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>استخدام "نهج المجموعة" لمنع المستخدمين من وضع الفحص

1. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. باستخدام **محرر إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **المسح الضوئي**.

5. انقر نقرا مزدوجا فوق **الإعداد السماح للمستخدمين بإيقاف الفحص** مؤقتا ثم قم بتعيين الخيار إلى **معطل**. انقر فوق **موافق**.

## <a name="related-articles"></a>المقالات ذات الصلة

- [تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)
- [تكوين تفاعل المستخدم النهائي مع برنامج الحماية من الفيروسات من Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
