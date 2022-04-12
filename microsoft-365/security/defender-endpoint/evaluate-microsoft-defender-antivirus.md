---
title: تقييم برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكن للشركات من جميع الأحجام استخدام هذا الدليل لتقييم واختبار الحماية التي تقدمها برنامج الحماية من الفيروسات من Microsoft Defender في Windows.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، حماية السحابة، السحابة، الحماية من البرامج الضارة، الأمان، Defender، التقييم، الاختبار، الحماية، المقارنة، الحماية في الوقت الحقيقي
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 8c7ced9c85ec7c6075b44970d25e34ba5594404e
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787589"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>تقييم برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- برنامج الحماية من الفيروسات من Microsoft Defender
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)

**منصات**
- بالنسبة لنظام التشغيل

استخدم هذا الدليل لتحديد مدى حماية برنامج الحماية من الفيروسات من Microsoft Defender لك من الفيروسات والبرامج الضارة والتطبيقات التي يحتمل أن تكون غير مرغوب فيها.

> [!TIP]
>يمكنك أيضا زيارة موقع العرض التوضيحي Microsoft Defender لنقطة النهاية في [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) لتأكيد عمل الميزات التالية ومعرفة كيفية عملها:
>
> - الحماية المقدمة من السحابة
> - التعلم السريع (بما في ذلك الحظر من النظرة الأولى)
> - حظر التطبيقات غير المرغوب فيها

> [!NOTE]
> تم إهمال الموقع التجريبي ل Defender لنقطة النهاية في demo.wd.microsoft.com وستتم إزالته في المستقبل.

وهو يشرح ميزات الحماية من الجيل التالي المهمة برنامج الحماية من الفيروسات من Microsoft Defender المتاحة لكل من الشركات الصغيرة والكبيرة، وكيف تزيد من الكشف عن البرامج الضارة وحمايتها عبر شبكتك.

يمكنك اختيار تكوين وتقييم كل إعداد بشكل مستقل، أو كل ذلك في وقت واحد. لقد قمنا بتجميع إعدادات مماثلة استنادا إلى سيناريوهات التقييم النموذجية، وقمنا بتضمين إرشادات لاستخدام PowerShell لتمكين الإعدادات.

يتوفر الدليل بتنسيق PDF للعرض دون اتصال:

- [تنزيل الدليل بتنسيق PDF](https://www.microsoft.com/download/details.aspx?id=54795)

يمكنك أيضا تنزيل PowerShell الذي سيمكن جميع الإعدادات الموضحة في الدليل تلقائيا. يمكنك الحصول على البرنامج النصي إلى جانب تنزيل PDF أعلاه، أو بشكل فردي من معرض PowerShell:

- [تنزيل البرنامج النصي PowerShell لتكوين الإعدادات تلقائيا](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> الدليل مخصص حاليا لتقييم برنامج الحماية من الفيروسات من Microsoft Defender أحادية الجهاز. قد لا يكون تمكين جميع الإعدادات في هذا الدليل مناسبا للتوزيع في العالم الحقيقي.
>
> للحصول على أحدث التوصيات لنشر ومراقبة برنامج الحماية من الفيروسات من Microsoft Defender في العالم الحقيقي عبر شبكة، راجع [Deploy برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)