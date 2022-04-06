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
ms.openlocfilehash: 26a792a753b0855a12cd994256cef93a64a5a159
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469218"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>منع المستخدمين من رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكنك استخدام نهج المجموعة لمنع المستخدمين في نقاط النهاية من رؤية واجهة برنامج الحماية من الفيروسات من Microsoft Defender. يمكنك أيضا منعهم من وضع عمليات المسح الضوئية في وضع انتظار.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>إخفاء واجهة برنامج الحماية من الفيروسات من Microsoft Defender

في Windows 10، ستخفي الإصدارات 1703، إخفاء الواجهة إعلامات برنامج الحماية من الفيروسات من Microsoft Defender ومنع ظهور لوحة الحماية من المخاطر & الفيروسات في تطبيق أمن Windows.

مع تعيين الإعداد إلى **تمكين**:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="لا أمن Windows بدون أيقونة الدرع وأقسام الحماية من الفيروسات والتهديدات" lightbox="../../media/wdav-headless-mode-off-1703.png":::

مع تعيين الإعداد إلى **معطل** أو غير مكون:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="المقطع أمن Windows مع أيقونة الدرع وأقسام الحماية من المخاطر" lightbox="../../media/wdav-headless-mode-1703.png":::

> [!NOTE]
> سيمنع إخفاء الواجهة أيضا برنامج الحماية من الفيروسات من Microsoft Defender الإعلامات من الظهور على نقطة النهاية. Microsoft Defender لنقطة النهاية الإعلامات تظهر. يمكنك أيضا تكوين الإعلامات التي تظهر على [نقاط النهاية بشكل فردي](configure-notifications-microsoft-defender-antivirus.md)

في الإصدارات السابقة من Windows 10، سيخفي الإعداد Windows عميل Defender. إذا حاول المستخدم فتحه، سيتلقى تحذيرا يقول "قام مسؤول النظام بتقييد الوصول إلى هذا التطبيق".

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="رسالة التحذير عند تمكين وضع الرأس في Windows 10، إصدارات أقدم من 1703" lightbox="../../media/wdav-headless-mode-1607.png":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>استخدام نهج المجموعة لإخفاء واجهة Microsoft Defender AV من المستخدمين

1. على جهاز نهج المجموعة، افتح نهج المجموعة [إدارة](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) التحكم، وانقر بيمين فوق نهج المجموعة الذي تريد تكوينه، ثم انقر فوق **تحرير**.

2. باستخدام نهج المجموعة **إدارة الكمبيوتر،** انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات > برنامج الحماية من الفيروسات من Microsoft Defender > العميل**.

5. انقر نقرا مزدوجا فوق إعداد تمكين وضع **واجهة المستخدم** بدون رأس، ثم قم بتعيين الخيار **إلى تمكين**. انقر فوق **موافق**.

راجع [منع المستخدمين من](configure-local-policy-overrides-microsoft-defender-antivirus.md) تعديل إعدادات النهج محليا للحصول على مزيد من الخيارات حول منع المستخدمين من تعديل الحماية على أجهزة الكمبيوتر الخاصة بهم.

## <a name="prevent-users-from-pausing-a-scan"></a>منع المستخدمين من وضع الفحص

يمكنك منع المستخدمين من وضع عمليات الفحص بشكل توقف، والتي قد تكون مفيدة لضمان عدم مقاطعة عمليات الفحص المجدولة أو عند الطلب من قبل المستخدمين.

> [!NOTE]
> هذا الإعداد غير معتمد على Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>استخدام نهج المجموعة لمنع المستخدمين من وضع الفحص

1. على جهاز نهج المجموعة، افتح نهج المجموعة [إدارة](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) التحكم، وانقر بيمين فوق نهج المجموعة الذي تريد تكوينه، ثم انقر فوق **تحرير**.

2. باستخدام نهج المجموعة **إدارة الكمبيوتر،** انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **المسح الضوئي**.

5. انقر نقرا مزدوجا فوق **الإعداد السماح للمستخدمين بإيقاف الفحص** مؤقتا ثم قم بتعيين الخيار إلى **معطل**. انقر فوق **موافق**.

## <a name="related-articles"></a>المقالات ذات الصلة

- [تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)
- [تكوين تفاعل المستخدم النهائي مع برنامج الحماية من الفيروسات من Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
