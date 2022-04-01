---
title: التبديل من حماية نقطة نهاية غير Microsoft إلى Microsoft Defender لنقطة النهاية
description: قم بالتبديل إلى Microsoft Defender لنقطة النهاية، الذي يتضمن برنامج الحماية من الفيروسات من Microsoft Defender لحل حماية نقطة النهاية.
keywords: الترحيل، windows defender، حماية نقاط النهاية المتقدمة، الحماية من الفيروسات، الحماية من البرامج الضارة، الوضع السلبي، الوضع النشط
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
ms.openlocfilehash: e93e762501b942a67cef35a95bb2a9a2b1113e3a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465850"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>التبديل من حماية نقطة نهاية غير Microsoft إلى Microsoft Defender لنقطة النهاية

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804) إذا كنت تفكر في التبديل من حل حماية نقطة نهاية غير Microsoft إلى [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) (Defender for Endpoint)، أو إذا كنت في مرحلة التخطيط، فاستخدم هذه المقالة كدليل. تصف هذه المقالة العملية الشاملة لعملية الانتقال إلى Defender for Endpoint.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="عملية الترحيل لتبديل حل حماية نقطة النهاية إلى Defender لنقطة النهاية" lightbox="images/nonms-mde-migration.png":::

عندما تقوم بالتبديل إلى Defender for Endpoint، تبدأ بحماية برامج الحماية من الفيروسات/البرامج الضارة غير من Microsoft في الوضع النشط. بعد ذلك، يمكنك برنامج الحماية من الفيروسات من Microsoft Defender في الوضع غير النشط، وتهيئة أجهزتك إلى Defender for Endpoint. بعد ذلك، يمكنك تكوين ميزات حماية نقطة النهاية، برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع النشط، والتحقق من أن كل شيء يعمل بشكل صحيح. وأخيرا، يمكنك إزالة الحل غير الخاص ب Microsoft.

## <a name="the-migration-process"></a>عملية الترحيل

يمكن تقسيم عملية ارحل إلى Defender for Endpoint إلى ثلاث مراحل، كما هو موضح في الجدول التالي:

:::image type="content" source="images/phase-diagrams/migration-phases.png" alt-text="عملية ترحيل MDE" lightbox="images/phase-diagrams/migration-phases.png":::


<br/><br/>

|المرحلة|الوصف|
|--|--|
|[التحضير ل الترحيل](switch-to-mde-phase-1.md)|أثناء [مرحلة **الإعداد**](switch-to-mde-phase-1.md): <br/>1. تحديث أجهزة مؤسستك.<br/>2. احصل على Defender لنقطة النهاية.<br/>3. تخطيط الأدوار والأذونات ومنح حق الوصول إلى Microsoft 365 Defender الإلكتروني.<br/>4. قم بتكوين إعدادات وكيل الجهاز والإنترنت لتمكين الاتصال بين أجهزة مؤسستك و Defender for Endpoint. |
|[إعداد Defender لنقطة النهاية](switch-to-mde-phase-2.md)|أثناء [مرحلة **الإعداد**](switch-to-mde-phase-2.md): <br/>1. تمكين/إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender، ثم تعيينه إلى الوضع السلبي.<br/>2. تكوين Defender لنقطة النهاية.<br/>3. أضف Defender for Endpoint إلى قائمة الاستثناء الخاصة بالحل الحالي.<br/>4. أضف الحل الموجود إلى قائمة استثناءات برنامج الحماية من الفيروسات من Microsoft Defender.<br/>5. إعداد مجموعات الأجهزة والمجموعات والوحدات التنظيمية.<br/>6. قم بتكوين سياسات الحماية من البرامج الضارة وإعدادات الحماية في الوقت الحقيقي.|
|[Onboard to Defender for Endpoint](switch-to-mde-phase-3.md)|أثناء [مرحلة **"الحافظة** "](switch-to-mde-phase-3.md): <br/>1. ادفع أجهزتك إلى Defender for Endpoint.<br/>2. تشغيل اختبار الكشف.<br/>3. تأكد من أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع غير النشط.<br/>4. احصل على تحديثات برنامج الحماية من الفيروسات من Microsoft Defender.<br/>5. إلغاء تثبيت حل الحماية الحالي لنقطة النهاية.<br/>6. تأكد من أن Defender for Endpoint يعمل بشكل صحيح.|

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>ما المضمن في Microsoft Defender لنقطة النهاية؟

في دليل الترحيل هذا، نركز على حماية [](microsoft-defender-antivirus-in-windows-10.md) الجيل التالي [الكشف عن تهديدات نقاط النهاية والرد عليها القدرات](overview-endpoint-detection-response.md) كنقطة بداية الانتقال إلى Defender for Endpoint. ومع ذلك، يتضمن Defender for Endpoint أكثر بكثير من الحماية من الفيروسات ونقطة النهاية. Defender for Endpoint هو نظام أساسي موحد للحماية الوقائية، والكشف بعد الخرق، والتحري التلقائي، والاستجابة. يلخص الجدول التالي الميزات والإمكانات في Defender for Endpoint.

<br/><br/>

|الميزة/الإمكانية|الوصف|
|---|---|
|[التهديدات & إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)|تساعد & إدارة الثغرات الأمنية المخاطر على تحديد نقاط الضعف وتقييمها وتصفية نقاط الضعف عبر نقاط النهاية (مثل الأجهزة).|
|[الحد من سطح الهجوم](overview-attack-surface-reduction.md)|تساعد قواعد الحد من سطح الهجوم على حماية أجهزة المؤسسة وتطبيقاتها من الهجمات ولهجمات الإنترنت.|
|[حماية الجيل التالي](microsoft-defender-antivirus-in-windows-10.md)|تتضمن حماية الجيل التالي برنامج الحماية من الفيروسات من Microsoft Defender للمساعدة على منع التهديدات والبرامج الضارة.|
|[الكشف عن نقطة النهاية والاستجابة لها](overview-endpoint-detection-response.md)|كشف قدرات الكشف عن نقاط النهاية والاستجابة لها، والكشف عنها، والاستجابة لمحاولات الاقتحام والانتهاكات النشطة.|
|[الصيد المتقدم](advanced-hunting-overview.md)|تمكن قدرات الصيد المتقدمة فريق عمليات الأمان من تحديد موقع المؤشرات والكيانات ذات التهديدات المعروفة أو المحتملة.|
|[الحظر السلوكي والاحتواء](behavioral-blocking-containment.md)|تساعد قدرات الحظر والاحتواء السلوكية على تحديد التهديدات والتوقف عن تنفيذها، استنادا إلى سلوكياتها وأشجار المعالجة حتى عندما يبدأ التهديد التنفيذ.|
|[المعالجة والتحري التلقائي](automated-investigations.md)|تقوم قدرات الاستجابة والتحري التلقائي بفحص التنبيهات واتخاذ إجراء إصلاح فوري لحل الخروقات.|
|[خدمة البحث عن خبراء المخاطر في Microsoft](microsoft-threat-experts.md))|توفر خدمات البحث عن المخاطر لفرق عمليات الأمان المراقبة والتحليل على مستوى الخبراء، وتساعد على ضمان عدم تفوية التهديدات الهامة.|

**هل تريد معرفة المزيد؟ راجع [Defender for Endpoint](microsoft-defender-endpoint.md).**

## <a name="next-step"></a>الخطوة التالية

- تابع إلى [التحضير ل الترحيل](switch-to-mde-phase-1.md).
