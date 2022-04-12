---
title: إخفاء واجهة برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك إخفاء لوحة الحماية من الفيروسات والتهديدات في تطبيق أمن Windows.
keywords: تأمين واجهة المستخدم، وضع بلا رأس، إخفاء التطبيق، إخفاء الإعدادات، إخفاء الواجهة
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
ms.openlocfilehash: fdd212efd50d55bbcdae80275f5d2ca8a97cdeb3
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787655"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>منع المستخدمين من رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

يمكنك استخدام نهج المجموعة لمنع المستخدمين على نقاط النهاية من رؤية واجهة برنامج الحماية من الفيروسات من Microsoft Defender. يمكنك أيضا منعهم من إيقاف عمليات المسح المؤقت.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>إخفاء واجهة برنامج الحماية من الفيروسات من Microsoft Defender

في Windows 10، الإصدارات 1703، سيؤدي إخفاء الواجهة إلى إخفاء إعلامات برنامج الحماية من الفيروسات من Microsoft Defender ومنع ظهور لوحة الحماية من الفيروسات & التهديد في تطبيق أمن Windows.

مع تعيين الإعداد إلى **ممكن**:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="أمن Windows بدون أيقونة الدرع وأقسام الحماية من الفيروسات والتهديدات" lightbox="../../media/wdav-headless-mode-off-1703.png":::

مع تعيين الإعداد إلى **"معطل"** أو لم يتم تكوينه:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="أمن Windows مع أيقونة الدرع وأقسام الحماية من التهديدات" lightbox="../../media/wdav-headless-mode-1703.png":::

> [!NOTE]
> سيؤدي إخفاء الواجهة أيضا إلى منع ظهور إعلامات برنامج الحماية من الفيروسات من Microsoft Defender على نقطة النهاية. ستظل إعلامات Microsoft Defender لنقطة النهاية تظهر. يمكنك أيضا [تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md) بشكل فردي

في الإصدارات السابقة من Windows 10، سيخفي الإعداد واجهة عميل Windows Defender. إذا حاول المستخدم فتحه، فسيتلقى تحذيرا يقول: "قام مسؤول النظام بتقييد الوصول إلى هذا التطبيق."

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="رسالة التحذير عند تمكين الوضع بلا رأس في Windows 10، الإصدارات الأقدم من 1703" lightbox="../../media/wdav-headless-mode-1607.png":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>استخدام نهج المجموعة لإخفاء واجهة Microsoft Defender AV عن المستخدمين

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. باستخدام **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender > واجهة العميل**.

5. انقر نقرا مزدوجا فوق إعداد **"تمكين وضع واجهة المستخدم بلا رأس** " وقم بتعيين الخيار إلى **"ممكن**". انقر فوق **موافق**.

راجع [منع المستخدمين من تعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md) لمزيد من الخيارات حول منع المستخدمين من تعديل الحماية على أجهزة الكمبيوتر الخاصة بهم.

## <a name="prevent-users-from-pausing-a-scan"></a>منع المستخدمين من إيقاف عملية المسح المؤقت

يمكنك منع المستخدمين من إيقاف عمليات المسح مؤقتا، والتي يمكن أن تكون مفيدة لضمان عدم مقاطعة عمليات الفحص المجدولة أو عند الطلب من قبل المستخدمين.

> [!NOTE]
> هذا الإعداد غير معتمد في Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>استخدام نهج المجموعة لمنع المستخدمين من إيقاف عملية الفحص

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. باستخدام **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **المسح الضوئي**.

5. انقر نقرا مزدوجا فوق " **السماح للمستخدمين بإيقاف إعداد الفحص مؤقتا** وتعيين الخيار إلى **"معطل**". انقر فوق **موافق**.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)
- [تكوين تفاعل المستخدم النهائي مع برنامج الحماية من الفيروسات من Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
