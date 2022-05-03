---
title: تعرف على ملحق Microsoft Purview
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: يوسع ملحق Microsoft Purview مراقبة أنشطة الملفات وإجراءات الحماية والتحكم فيها إلى مستعرض Google Chrome
ms.openlocfilehash: a74cfeb734f41622d491c8aaffe3a5e054479a2a
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172234"
---
# <a name="learn-about-the-microsoft-purview-extension"></a>تعرف على ملحق Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تعمل [ميزة منع فقدان بيانات نقطة النهاية (DLP)](endpoint-dlp-learn-about.md) على توسيع قدرات مراقبة النشاط وحمايتها [لمنع فقدان بيانات Microsoft Purview (DLP)](dlp-learn-about-dlp.md) إلى العناصر الحساسة الموجودة على أجهزة Windows 10. بمجرد إلحاق الأجهزة في حلول Microsoft Purview، تصبح المعلومات حول ما يفعله المستخدمون بالعناصر الحساسة مرئية في [مستكشف النشاط](data-classification-activity-explorer.md) ويمكنك فرض إجراءات الحماية على تلك العناصر عبر [نهج DLP](create-test-tune-dlp-policy.md).

بمجرد تثبيت الملحق على جهاز Windows 10، يمكن للمؤسسات المراقبة عندما يحاول المستخدم الوصول إلى عنصر حساس أو تحميله إلى خدمة سحابية باستخدام Google Chrome وفرض إجراءات الحماية عبر DLP.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>الأنشطة التي يمكنك مراقبتها واتخاذ إجراءات بشأنها

يمكنك الملحق من تدقيق وإدارة الأنواع التالية من الأنشطة التي يأخذها المستخدمون على العناصر الحساسة على الأجهزة التي تعمل Windows 10.

النشاط |وصف  | إجراءات النهج المدعومة|
|---------|---------|---------|
|ملف تم نسخه إلى السحابة  | الكشف عن الوقت الذي يحاول فيه مستخدم تحميل عنصر حساس إلى مجال خدمة مقيد من خلال مستعرض Chrome |تدقيق، كتلة مع تجاوز، كتلة|
|الملف المطبوع  |الكشف عن الوقت الذي يحاول فيه مستخدم طباعة عنصر حساس مفتوح في مستعرض Chrome إلى طابعة محلية أو طابعة شبكة |تدقيق، كتلة مع تجاوز، كتلة|
|ملف تم نسخه إلى الحافظة |الكشف عن الوقت الذي يحاول فيه مستخدم نسخ معلومات من عنصر حساس يتم عرضه في مستعرض Chrome ثم لصقها في تطبيق أو عملية أو عنصر آخر. |تدقيق، كتلة مع تجاوز، كتلة|
|ملف تم نسخه إلى تخزين قابل للإزالة    | الكشف عن الوقت الذي يحاول فيه مستخدم نسخ عنصر حساس أو معلومات من عنصر حساس مفتوح في مستعرض Chrome إلى وسائط قابلة للإزالة أو جهاز USB |تدقيق، كتلة مع تجاوز، كتلة|
|ملف تم نسخه إلى مشاركة الشبكة  |الكشف عن الوقت الذي يحاول فيه مستخدم نسخ عنصر حساس أو معلومات من عنصر حساس مفتوح في مستعرض Chrome إلى مشاركة شبكة أو محرك أقراص شبكة معين.|تدقيق، كتلة مع تجاوز، كتلة |

## <a name="deployment-process"></a>عملية التوزيع
1. [البدء في منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md)
2. [أدوات وأساليب الإلحاق للأجهزة Windows 10](device-onboarding-overview.md)
3. [تثبيت الملحق على أجهزة Windows 10](dlp-chrome-get-started.md)
4. [إنشاء نهج DLP أو تحريرها](create-test-tune-dlp-policy.md) التي تقيد التحميل إلى خدمة السحابة، أو الوصول من خلال إجراءات المستعرضات غير مسموح بها وتطبيقها على أجهزة Windows 10

## <a name="next-steps"></a>الخطوات التالية

راجع [بدء استخدام ملحق Microsoft Purview](dlp-chrome-get-started.md) لإجراءات وسيناريوهات النشر الكاملة.

## <a name="see-also"></a>راجع أيضًا

- [بدء استخدام ملحق Microsoft Purview](dlp-chrome-get-started.md)
- [التعرّف على تفادي فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [البدء في منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md)
- [استخدام تفادي فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)
- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)
- [إدارة المخاطر الداخلية](insider-risk-management.md)
