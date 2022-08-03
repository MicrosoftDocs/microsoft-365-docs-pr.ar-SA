---
title: التبديل من حماية نقطة النهاية غير الخاصة ب Microsoft إلى Microsoft Defender لنقطة النهاية
description: قم بالتبديل إلى Microsoft Defender لنقطة النهاية، والتي تتضمن برنامج الحماية من الفيروسات من Microsoft Defender لحل حماية نقطة النهاية.
keywords: الترحيل، windows Defender، حماية متقدمة لنقطة النهاية، برنامج الحماية من الفيروسات، مكافحة البرامج الضارة، الوضع السلبي، الوضع النشط
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-overview
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
- m365initiative-defender-endpoint
ms.topic: overview
ms.custom: migrationguides
ms.date: 11/29/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: f922d618ac947646379f9d1022aba67c874e64fd
ms.sourcegitcommit: d7193ee954c01c4172e228d25b941026c8d92d30
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/02/2022
ms.locfileid: "67174949"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>التبديل من حماية نقطة النهاية غير الخاصة ب Microsoft إلى Microsoft Defender لنقطة النهاية

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


إذا كنت تفكر في التبديل من حل حماية نقطة النهاية غير التابع ل Microsoft إلى [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) (Defender لنقطة النهاية)، أو كنت في مرحلة التخطيط، فاستخدم هذه المقالة كدليل. تصف هذه المقالة العملية الشاملة للانتقال إلى Defender لنقطة النهاية.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="عملية الترحيل لتبديل حل حماية نقطة النهاية إلى Defender لنقطة النهاية" lightbox="images/nonms-mde-migration.png":::

عند التبديل إلى Defender لنقطة النهاية، تبدأ بالحماية من الفيروسات/الحماية من البرامج الضارة غير التابعة ل Microsoft في الوضع النشط. بعد ذلك، يمكنك تكوين برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، وإلحاق أجهزتك ب Defender لنقطة النهاية. بعد ذلك، يمكنك تكوين ميزات حماية نقطة النهاية، وتعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع النشط، والتحقق من أن كل شيء يعمل بشكل صحيح. وأخيرا، يمكنك إزالة الحل غير التابع ل Microsoft.

## <a name="the-migration-process"></a>عملية الترحيل

يمكن تقسيم عملية الترحيل إلى Defender لنقطة النهاية إلى ثلاث مراحل، كما هو موضح في الجدول التالي:

:::image type="content" source="images/phase-diagrams/migration-phases.png" alt-text="عملية ترحيل MDE" lightbox="images/phase-diagrams/migration-phases.png":::


<br/><br/>

|طور|الوصف|
|--|--|
|[التحضير لل ترحيلك](switch-to-mde-phase-1.md)|[أثناء مرحلة **الإعداد**](switch-to-mde-phase-1.md): <br/>1. تحديث أجهزة مؤسستك.<br/>2. الحصول على Defender لنقطة النهاية.<br/>3. تخطيط الأدوار والأذونات، ومنح حق الوصول إلى مدخل Microsoft 365 Defender.<br/>4. تكوين إعدادات وكيل جهازك والإنترنت لتمكين الاتصال بين أجهزة مؤسستك و Defender لنقطة النهاية. |
|[إعداد Defender لنقطة النهاية](switch-to-mde-phase-2.md)|[أثناء مرحلة **الإعداد**](switch-to-mde-phase-2.md): <br/>1. تمكين/إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender، وتعيينه إلى الوضع السلبي.<br/>2. تكوين Defender لنقطة النهاية.<br/>3. أضف Defender لنقطة النهاية إلى قائمة الاستبعاد لحلك الحالي.<br/>4. أضف الحل الموجود إلى قائمة الاستبعاد لبرنامج الحماية من الفيروسات من Microsoft Defender.<br/>5. إعداد مجموعات الأجهزة والمجموعات والوحدات التنظيمية.<br/>6. تكوين نهج الحماية من البرامج الضارة وإعدادات الحماية في الوقت الحقيقي.|
|[إلحاق Defender لنقطة النهاية](switch-to-mde-phase-3.md)|[أثناء مرحلة **الإلحاق**](switch-to-mde-phase-3.md): <br/>1. إلحاق أجهزتك ب Defender لنقطة النهاية.<br/>2. تشغيل اختبار الكشف.<br/>3. تأكد من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل.<br/>4. احصل على تحديثات برنامج الحماية من الفيروسات من Microsoft Defender.<br/>5. إلغاء تثبيت حل حماية نقطة النهاية الحالي.<br/>6. تأكد من أن Defender for Endpoint يعمل بشكل صحيح.|

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>ما المضمن في Microsoft Defender لنقطة النهاية؟

في دليل الترحيل هذا، نركز على [الجيل التالي من قدرات الحماية](microsoft-defender-antivirus-in-windows-10.md) [والكشف عن نقطة النهاية والاستجابة](overview-endpoint-detection-response.md) كنقطة بداية للانتقال إلى Defender لنقطة النهاية. ومع ذلك، يتضمن Defender لنقطة النهاية أكثر بكثير من الحماية من الفيروسات ونقطة النهاية. Defender لنقطة النهاية هو نظام أساسي موحد للحماية الوقائية، والكشف بعد الاختراق، والتحقيق التلقائي، والاستجابة. يلخص الجدول التالي الميزات والقدرات في Defender لنقطة النهاية.

<br/><br/>

|الميزة/القدرة|الوصف|
|---|---|
|[التهديدات وإدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)|تساعد قدرات إدارة الثغرات الأمنية & المخاطر في تحديد نقاط الضعف وتقييمها ومعالجتها عبر نقاط النهاية (مثل الأجهزة).|
|[قواعد تقليل الأجزاء المعرضة للهجوم](overview-attack-surface-reduction.md)|تساعد قواعد تقليل الأجزاء المعرضة للهجوم على حماية أجهزة مؤسستك وتطبيقاتها من التهديدات الإلكترونية والهجمات.|
|[حماية الجيل التالي](microsoft-defender-antivirus-in-windows-10.md)|تتضمن حماية الجيل التالي برنامج الحماية من الفيروسات من Microsoft Defender للمساعدة في حظر التهديدات والبرامج الضارة.|
|[الكشف عن نقطة النهاية والاستجابة لها](overview-endpoint-detection-response.md)|اكتشاف نقاط النهاية وقدرات الاستجابة للكشف عن محاولات الاختراق والاختراقات النشطة والتحقيق فيها والاستجابة لها.|
|[الصيد المتقدم](advanced-hunting-overview.md)|تمكن قدرات التتبع المتقدمة فريق عمليات الأمان من تحديد موقع مؤشرات وكيانات التهديدات المعروفة أو المحتملة.|
|[الحظر السلوكي والاحتواء](behavioral-blocking-containment.md)|تساعد قدرات الحظر السلوكي والاحتواء على تحديد التهديدات وإيقافها، استنادا إلى سلوكياتها ومعالجة الأشجار حتى عندما يبدأ تنفيذ التهديد.|
|[التحقيق التلقائي والمعالجة](automated-investigations.md)|تفحص قدرات التحقيق والاستجابة التلقائية التنبيهات واتخاذ إجراءات معالجة فورية لحل الخروقات.|
|[خدمة تتبع المخاطر](microsoft-threat-experts.md) (خبراء المخاطر في Microsoft)|توفر خدمات تتبع التهديدات لفرق عمليات الأمان مراقبة وتحليلا على مستوى الخبراء، وللمساعدة على ضمان عدم تفويت التهديدات الحرجة.|

**هل تريد معرفة المزيد؟ راجع [Defender لنقطة النهاية](microsoft-defender-endpoint.md).**

## <a name="next-step"></a>الخطوة التالية

- تابع [للتحضير لل ترحيلك](switch-to-mde-phase-1.md).
