---
title: إعداد الاستثناءات لمسح برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك استبعاد الملفات (بما في ذلك الملفات التي تم تعديلها بواسطة عمليات محددة) والمجلدات من أن يتم مسحها ضوئيا بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. التحقق من صحة استثناءاتك باستخدام PowerShell.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.technology: mde
ms.audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: c9796f4e5154fd46d1479f0cbfa25f2afaf4e9bb
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787501"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>تكوين الاستثناءات والتحقق من صحتها لمسح برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

يمكنك استبعاد بعض الملفات والمجلدات والعمليات والملفات التي تم فتحها للعمليات من عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender. تنطبق هذه الاستثناءات على [عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)، [والمسح الضوئي عند الطلب](run-scan-microsoft-defender-antivirus.md)، [والحماية والمراقبة في الوقت الحقيقي دائما](configure-real-time-protection-microsoft-defender-antivirus.md). تنطبق استثناءات الملفات التي يتم فتحها للعملية على الحماية في الوقت الحقيقي فقط.

## <a name="configure-and-validate-exclusions"></a>تكوين الاستثناءات والتحقق من صحتها

لتكوين الاستثناءات والتحقق من صحتها، راجع ما يلي:

- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى اسم الملف والملحق وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md). يمكنك استبعاد الملفات من عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender استنادا إلى ملحق الملف أو اسم الملف أو موقعه.

- [تكوين الاستثناءات للملفات التي تفتحها العمليات والتحقق من صحتها](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). يمكنك استبعاد الملفات من عمليات الفحص التي تم فتحها بواسطة عملية معينة.

## <a name="recommendations-for-defining-exclusions"></a>التوصيات لتعريف الاستثناءات

> [!IMPORTANT]
> تتضمن برنامج الحماية من الفيروسات من Microsoft Defender العديد من الاستثناءات التلقائية استنادا إلى سلوكيات نظام التشغيل المعروفة وملفات الإدارة النموذجية، مثل تلك المستخدمة في إدارة المؤسسة وإدارة قاعدة البيانات وسيناريوهات المؤسسة وحالاتها الأخرى.
>
> يؤدي تحديد الاستثناءات إلى تقليل الحماية التي توفرها برنامج الحماية من الفيروسات من Microsoft Defender. يجب عليك دائما تقييم المخاطر المقترنة بتنفيذ الاستثناءات، ويجب عليك فقط استبعاد الملفات التي أنت واثق من أنها ليست ضارة.

ضع النقاط التالية في الاعتبار عند تحديد الاستثناءات:

- الاستثناءات هي من الناحية الفنية فجوة حماية. ضع في اعتبارك جميع خياراتك عند تحديد الاستثناءات. يمكن أن تكون الخيارات الأخرى بسيطة مثل التأكد من أن الموقع المستبعد يحتوي على قوائم التحكم في الوصول المناسبة (ACLs) أو تعيين نهج لوضع التدقيق في البداية.

- راجع الاستثناءات بشكل دوري. أعد تدقيق عمليات التخفيف من المخاطر وإعادة فرضها كجزء من عملية المراجعة.

- من الناحية المثالية، تجنب تحديد الاستثناءات في محاولة لتكون استباقية. على سبيل المثال، لا تستبعد شيئا ما لأنك تعتقد أنه قد يكون مشكلة في المستقبل. استخدم الاستثناءات فقط للمشاكل المحددة، مثل تلك المتعلقة بالأداء أو توافق التطبيقات التي يمكن أن تخفف منها الاستثناءات.

- مراجعة التغييرات وتدقيقها في قائمة الاستثناءات الخاصة بك. يجب أن يحافظ فريق الأمان الخاص بك على السياق حول سبب إضافة استثناء معين لتجنب الإرباك لاحقا. يجب أن يكون فريق الأمان لديك قادرا على تقديم إجابات محددة للأسئلة حول سبب وجود الاستثناءات.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [استثناءات برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [الأخطاء الشائعة التي يجب تجنبها عند تحديد الاستثناءات](common-exclusion-mistakes-microsoft-defender-antivirus.md)
