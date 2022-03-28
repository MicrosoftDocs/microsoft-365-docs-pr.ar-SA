---
title: تقييم برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكن للشركات من جميع الأحجام استخدام هذا الدليل لتقييم واختبار الحماية التي يوفرها برنامج الحماية من الفيروسات من Microsoft Defender في Windows.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، حماية السحابة، السحابة، الحماية من البرامج الضارة، الأمان، الحماية، الحماية، التقييم، الاختبار، الحماية، المقارنة، الحماية في الوقت الحقيقي
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
ms.openlocfilehash: 4dd25a599f144a60bfd2ebeb3e9bb8b1876bd3c6
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63575476"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>تقييم برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

استخدم هذا الدليل لتحديد مدى برنامج الحماية من الفيروسات من Microsoft Defender تحميك من الفيروسات والبرامج الضارة والتطبيقات التي يحتمل أن تكون غير مرغوب فيها.

> [!TIP]
>يمكنك أيضا زيارة موقع العرض التوضيحي ل Microsoft Defender for Endpoint على [](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) demo.wd.microsoft.com للتأكد من أن الميزات التالية تعمل وترى كيفية عملها:
>
> - الحماية التي يتم تسليمها من السحابة
> - التعلم السريع (بما في ذلك الحظر من النظرة الأولى)
> - حظر التطبيقات غير المرغوب فيها

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

كما تشرح ميزات حماية الجيل التالي برنامج الحماية من الفيروسات من Microsoft Defender المتوفرة لكل من المؤسسات الصغيرة والكبيرة، وكيفية زيادة الكشف عن البرامج الضارة وحمايتها عبر شبكتك.

يمكنك اختيار تكوين كل إعداد وتقييمه بشكل مستقل، أو الكل في وقت واحد. لقد قمنا بتضمين إعدادات مماثلة استنادا إلى سيناريوهات التقييم النموذجية، ونتضمن إرشادات لاستخدام PowerShell لتمكين الإعدادات.

يتوفر الدليل بتنسيق PDF للعرض دون اتصال:

- [تنزيل الدليل بتنسيق PDF](https://www.microsoft.com/download/details.aspx?id=54795)

يمكنك أيضا تنزيل PowerShell لتمكين كل الإعدادات الموضحة في الدليل تلقائيا. يمكنك الحصول على البرنامج النصي إلى جانب تنزيل PDF أعلاه، أو بشكل فردي من معرض PowerShell:

- [تنزيل البرنامج النصي PowerShell لتكوين الإعدادات تلقائيا](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> الدليل مخصص حاليا لتقييم جهاز واحد برنامج الحماية من الفيروسات من Microsoft Defender. قد لا يكون تمكين كل الإعدادات في هذا الدليل مناسبا للنشر في العالم الحقيقي.
>
> للحصول على أحدث التوصيات لنشر ومراقبة العالم الحقيقي برنامج الحماية من الفيروسات من Microsoft Defender عبر الشبكة، راجع [نشر](deploy-manage-report-microsoft-defender-antivirus.md) برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)