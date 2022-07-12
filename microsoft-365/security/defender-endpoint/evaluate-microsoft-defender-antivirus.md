---
title: تقييم برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكن للشركات من جميع الأحجام استخدام هذا الدليل لتقييم واختبار الحماية التي يوفرها برنامج الحماية من الفيروسات من Microsoft Defender في Windows.
keywords: Microsoft Defender Antivirus، حماية السحابة، السحابة، الحماية من البرامج الضارة، الأمان، Defender، التقييم، الاختبار، الحماية، المقارنة، الحماية في الوقت الحقيقي
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
ms.openlocfilehash: 89da56c0230772dab59ad02a751c3bb1ada164e7
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717791"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>تقييم برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- برنامج الحماية من الفيروسات من Microsoft Defender
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

استخدم هذا الدليل لتحديد مدى حماية Microsoft Defender Antivirus لك من الفيروسات والبرامج الضارة والتطبيقات التي قد تكون غير مرغوب فيها. وهو يشرح ميزات الحماية من الجيل التالي الهامة من برنامج الحماية من الفيروسات من Microsoft Defender المتوفرة لكل من المؤسسات الصغيرة والكبيرة، وكيف تزيد من الكشف عن البرامج الضارة وحمايتها عبر شبكتك.

يمكنك اختيار تكوين وتقييم كل إعداد بشكل مستقل، أو كل ذلك في وقت واحد. لقد قمنا بتجميع إعدادات مماثلة استنادا إلى سيناريوهات التقييم النموذجية، وقمنا بتضمين إرشادات لاستخدام PowerShell لتمكين الإعدادات.

يتوفر الدليل بتنسيق PDF للعرض دون اتصال:

- [تنزيل الدليل بتنسيق PDF](https://www.microsoft.com/download/details.aspx?id=54795)

يمكنك أيضا تنزيل PowerShell الذي سيمكن جميع الإعدادات الموضحة في الدليل تلقائيا. يمكنك الحصول على البرنامج النصي إلى جانب تنزيل PDF أعلاه، أو بشكل فردي من معرض PowerShell:

- [تنزيل البرنامج النصي PowerShell لتكوين الإعدادات تلقائيا](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> الدليل مخصص حاليا لتقييم جهاز واحد من برنامج الحماية من الفيروسات من Microsoft Defender. قد لا يكون تمكين جميع الإعدادات في هذا الدليل مناسبا للتوزيع في العالم الحقيقي.
>
> للحصول على أحدث التوصيات لنشر ومراقبة برنامج الحماية من الفيروسات في العالم الحقيقي من Microsoft Defender عبر شبكة، راجع [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)