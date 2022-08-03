---
title: ترحيل الخوادم من Microsoft Defender لنقطة النهاية إلى Microsoft Defender for Cloud
description: تعرف على كيفية ترحيل الخوادم من Microsoft Defender لنقطة النهاية إلى Microsoft Defender for Cloud.
keywords: ترحيل الخادم، والخادم، وخادم Microsoft Defender لنقطة النهاية، وMicrosoft Defender for Cloud، وMDE، وazure، وazure cloud، وCSPM، وCWP، وحماية حمل العمل السحابي، والحماية من التهديدات، والحماية المتقدمة من التهديدات، وMicrosoft Azure، والموصل متعدد السحابة
author: alekyaj
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: migrationguides
ms.date: 07/19/2022
ms.technology: mde
ms.openlocfilehash: d6ce0fe6b001c537a6bb801f18920f759a1cce09
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67171649"
---
# <a name="migrating-servers-from-microsoft-defender-for-endpoint-to-microsoft-defender-for-cloud"></a>ترحيل الخوادم من Microsoft Defender لنقطة النهاية إلى Microsoft Defender for Cloud

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

ترشدك هذه المقالة في ترحيل الخوادم من Microsoft Defender لنقطة النهاية (MDE) إلى Defender for Cloud.

[Microsoft Defender لنقطة النهاية](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-endpoint) (MDE) هو نظام أساسي لأمان نقطة نهاية المؤسسة مصمم لمساعدة شبكات المؤسسة على منع التهديدات المتقدمة واكتشافها والتحقيق فيها والاستجابة لها.

[Microsoft Defender for Cloud](https://azure.microsoft.com/services/defender-for-cloud/) هو حل لإدارة وضع أمان السحابة (CSPM) وحماية حمل العمل السحابي (CWP) الذي يعثر على نقاط ضعف عبر تكوين السحابة. كما أنه يساعد على تعزيز الوضع الأمني العام للبيئة الخاصة بك، ويمكن أن يحمي أحمال العمل عبر البيئات متعددة السحابة والمختلطة من التهديدات المتطورة.

في حين أن كلا المنتجين يوفران قدرات حماية الخادم، فإن Microsoft Defender for Cloud هو الحل الأساسي لحماية موارد البنية الأساسية، بما في ذلك الخوادم. 

## <a name="how-do-i-migrate-my-servers-from-microsoft-defender-for-endpoint-to-microsoft-defender-for-cloud"></a>كيف أعمل ترحيل خوادمي من Microsoft Defender لنقطة النهاية إلى Microsoft Defender for Cloud؟

إذا كان لديك خوادم تم إلحاقها ب Defender لنقطة النهاية، تختلف عملية الترحيل اعتمادا على نوع الجهاز، ولكن هناك مجموعة من المتطلبات الأساسية المشتركة. 

Microsoft Defender for Cloud هي خدمة مستندة إلى الاشتراك في مدخل Microsoft Azure. لذلك، يجب تمكين Defender for Cloud والخطط الأساسية مثل Microsoft Defender for Servers Plan 2 على اشتراكات Azure.

لتمكين Defender for Servers لأجهزة Azure الظاهرية والأجهزة غير المتصلة ب Azure المتصلة من خلال [الخوادم الممكنة بواسطة Azure Arc](/azure/azure-arc/servers/overview)، اتبع هذا الإرشادات:

1. إذا لم تكن تستخدم Azure بالفعل، فخطط بيئتك باتباع [Azure Well-Architected Framework](/azure/architecture/framework/).
2. تمكين [Microsoft Defender for Cloud](/azure/defender-for-cloud/get-started) على اشتراكك (اشتراكاتك).
3. تمكين إحدى خطط Microsoft Defender for Server على [اشتراكك (اشتراكاتك](/azure/defender-for-cloud/enable-enhanced-security)). في حالة استخدام Defender for Servers Plan 2، تأكد من تمكينه أيضا على مساحة عمل Log Analytics المتصلة بها أجهزتك؛ سيمكنك من استخدام ميزات اختيارية مثل File Integrity Monitoring وSive Application Controls والمزيد.
4. تأكد من تمكين [تكامل MDE](/azure/defender-for-cloud/integration-defender-for-endpoint?tabs=windows) على اشتراكك. إذا كان لديك اشتراكات Azure موجودة مسبقا، فقد ترى واحدا (أو كليهما) من زري الاشتراك المعروضين في الصورة أدناه.
     :::image type="content" source="images/mde-integration.png" alt-text="لقطة شاشة توضح كيفية تمكين تكامل MDE.":::
إذا كان لديك أي من هذه الأزرار في بيئتك، فتأكد من تمكين التكامل لكليهما. في الاشتراكات الجديدة، سيتم تمكين كلا الخيارين بشكل افتراضي.
5. تأكد من استيفاء متطلبات الاتصال ل Azure Arc. يتطلب Microsoft Defender for Cloud توصيل جميع الأجهزة المحلية وغير الخاصة ب Azure عبر عامل Azure Arc. بالإضافة إلى ذلك، لا يدعم Azure Arc جميع أنظمة التشغيل المدعومة من MDE. لذلك، تعرف على كيفية التخطيط [لعمليات نشر Azure Arc هنا](/azure/azure-arc/servers/plan-at-scale-deployment).
6. *اوصت:* إذا كنت تريد الاطلاع على نتائج الثغرات الأمنية في Defender for Cloud، فتأكد من تمكين [إدارة الثغرات الأمنية في Microsoft Defender](/azure/defender-for-cloud/enable-data-collection?tabs=autoprovision-va) ل Defender for Cloud.
   :::image type="content" source="images/enable-threat-and-vulnerability-management.png" alt-text="لقطة شاشة توضح كيفية تمكين إدارة الثغرات الأمنية."::: 

## <a name="how-do-i-migrate-existing-azure-vms-to-microsoft-defender-for-cloud"></a>كيف أعمل ترحيل أجهزة Azure الظاهرية الموجودة إلى Microsoft Defender for Cloud؟

بالنسبة إلى أجهزة Azure الظاهرية، لا يلزم اتخاذ أي خطوات إضافية، حيث يتم إلحاقها تلقائيا ب Microsoft Defender for Cloud، وذلك بفضل التكامل الأصلي بين منصة Azure و Defender for Cloud.

## <a name="how-do-i-migrate-on-premises-machines-to-microsoft-defender-for-servers"></a>كيف أعمل ترحيل الأجهزة المحلية إلى Microsoft Defender for Servers؟

[قم بتوصيل](/azure/defender-for-cloud/quickstart-onboard-machines?pivots=azure-arc) الأجهزة المحلية عبر الخوادم المتصلة ب Azure Arc.

## <a name="how-do-i-migrate-vms-from-aws-or-gcp-environments"></a>كيف أعمل ترحيل الأجهزة الظاهرية من بيئات AWS أو GCP؟

1. أنشئ موصلا جديدا متعدد السحابة على اشتراكك. (لمزيد من المعلومات حول الموصل، راجع [حسابات AWS](/azure/defender-for-cloud/quickstart-onboard-aws?pivots=env-settings) أو [مشاريع GCP](/azure/defender-for-cloud/quickstart-onboard-gcp?pivots=env-settings).
2. على موصل السحابة المتعددة، قم بتمكين Defender for Servers على موصلات [AWS](/azure/defender-for-cloud/quickstart-onboard-aws?pivots=env-settings#prerequisites) أو [GCP](/azure/defender-for-cloud/quickstart-onboard-gcp?pivots=env-settings#configure-the-servers-plan) .
3. تمكين التوفير التلقائي على موصل السحابة المتعددة لعامل Azure Arc، Microsoft Defender لنقطة النهاية الملحق، وتقييم الثغرات الأمنية، وبشكل اختياري، ملحق Log Analytics.
     :::image type="content" source="images/select-plans-aws-gcp.png" alt-text="لقطة شاشة توضح كيفية تمكين التوفير التلقائي لعامل Azure Arc.":::
لمزيد من المعلومات، راجع [قدرات Defender for Cloud متعددة السحابة](https://aka.ms/mdcmc).

## <a name="what-happens-once-all-migration-steps-are-completed"></a>ماذا يحدث بمجرد اكتمال جميع خطوات الترحيل؟

بمجرد الانتهاء من خطوات الترحيل ذات الصلة، سيقوم Microsoft Defender for Cloud بنشر `MDE.Windows` أو `MDE.Linux` الملحق إلى أجهزة Azure الظاهرية والأجهزة غير التابعة ل Azure المتصلة من خلال Azure Arc (بما في ذلك الأجهزة الظاهرية في AWS وحوسبة GCP).

يعمل الملحق كواجهة إدارة ونشر، والتي ستقوم بتنسيق البرامج النصية لتثبيت MDE والتفافها داخل نظام التشغيل وتعكس حالة التوفير الخاصة به إلى مستوى إدارة Azure. ستتعرف عملية التثبيت على تثبيت Defender لنقطة النهاية الموجودة وتوصيلها ب Defender for Cloud عن طريق إضافة علامات خدمة Defender لنقطة النهاية تلقائيا.

في حال توفرت لديك أجهزة Windows Server 2012 R2 أو 2016 التي تم توفيرها باستخدام حل Microsoft Defender لنقطة النهاية القديم المستند إلى Log Analytics، ستقوم عملية نشر Microsoft Defender for Cloud بنشر [الحل الموحد](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) ل Defender لنقطة النهاية. بعد نجاح النشر، سيتم إيقاف وتعطيل عملية Defender for Endpoint القديمة على هذه الأجهزة.
