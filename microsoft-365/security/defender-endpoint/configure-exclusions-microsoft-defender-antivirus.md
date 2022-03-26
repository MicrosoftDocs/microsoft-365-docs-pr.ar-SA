---
title: إعداد الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي
description: يمكنك استثناء الملفات (بما في ذلك الملفات التي تم تعديلها بواسطة عمليات محددة) والمجلدات التي لا يتم فحصها بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. تحقق من صحة استثناءاتك باستخدام PowerShell.
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
ms.openlocfilehash: 6ef9cfcec1c54cf9754d7152c098d7ef5b67b456
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570230"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>تكوين الاستثناءات والتحقق من صحتها برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


يمكنك استبعاد بعض الملفات والمجلدات والعمليات والملفات التي تم فتحها من برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي. تنطبق هذه الاستثناءات على عمليات [](scheduled-catch-up-scans-microsoft-defender-antivirus.md)الفحص المجدولة، [](run-scan-microsoft-defender-antivirus.md)والفحص عند الطلب، والحماية والمراقبة في الوقت [الحقيقي دائما](configure-real-time-protection-microsoft-defender-antivirus.md). تنطبق استثناءات الملفات المفتوحة على الحماية في الوقت الحقيقي فقط.

## <a name="configure-and-validate-exclusions"></a>تكوين الاستثناءات والتحقق من صحتها

لتكوين الاستثناءات والتحقق من صحتها، راجع ما يلي:

- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى اسم الملف والملحق وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md). يمكنك استثناء الملفات من عمليات برنامج الحماية من الفيروسات من Microsoft Defender استنادا إلى ملحق الملف أو اسم الملف أو موقعه.

- [تكوين الاستثناءات والتحقق من صحتها للملفات التي يتم فتحها بواسطة العمليات](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). يمكنك استثناء الملفات من عمليات الفحص التي تم فتحها بواسطة عملية معينة.

## <a name="recommendations-for-defining-exclusions"></a>التوصيات لتعريف الاستثناءات

> [!IMPORTANT]
> برنامج الحماية من الفيروسات من Microsoft Defender العديد من الاستثناءات التلقائية استنادا إلى سلوكيات نظام التشغيل المعروفة وملفات الإدارة النموذجية، مثل تلك المستخدمة في إدارة المؤسسة وإدارة قاعدة البيانات وسيناريوهات ومواد أخرى خاصة بالمؤسسة.
>
> إن تحديد الاستثناءات يقلل من الحماية التي يوفرها برنامج الحماية من الفيروسات من Microsoft Defender. يجب عليك دائما تقييم المخاطر المقترنة بتنفيذ الاستثناءات، ويجب استبعاد الملفات التي تثق بها فقط على أنها ليست ضارة.

ضع النقاط التالية في الاعتبار عند تحديد الاستثناءات:

- إن الاستثناءات هي من الناحية التقنية ثغرة في الحماية. يجب وضع كل الخيارات في الاعتبار عند تحديد الاستثناءات. يمكن أن تكون الخيارات الأخرى بسيطة مثل التأكد من أن الموقع المستبعد به قوائم التحكم بالوصول المناسبة (ACLs) أو تعيين سياسات إلى وضع التدقيق في بادئ الأمر.

- راجع الاستثناءات بشكل دوري. إعادة فحص عمليات التخفيف من المخاطر وفرضها كجزء من عملية المراجعة.

- وبشكل مثالي، تجنب تعريف الاستثناءات في محاولة لتكون استباقية. على سبيل المثال، لا تستثني شيئا ما فقط لأنك تعتقد أنه قد يكون مشكلة في المستقبل. استخدم الاستثناءات لقضايا معينة فقط، مثل تلك المتعلقة بتوافق التطبيقات أو الأداء التي يمكن أن تخفف من الاستثناءات.

- راجع التغييرات التي تم إدخالها على قائمة الاستثناءات وتدقيقها. يجب أن يحافظ فريق الأمان على السياق حول سبب إضافة استثناء معين لتجنب حدوث إرباك في وقت لاحق. يجب أن يكون فريق الأمان قادرا على توفير إجابات محددة على الأسئلة حول سبب وجود الاستثناءات.

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender استثناءات على Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات](common-exclusion-mistakes-microsoft-defender-antivirus.md)
