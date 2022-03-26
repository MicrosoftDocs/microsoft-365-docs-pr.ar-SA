---
title: التعرف على ملحق التوافق من Microsoft
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
description: يعمل ملحق التوافق من Microsoft على توسيع مراقبة أنشطة الملفات والإجراءات الحماية والتحكم فيها إلى مستعرض Google Chrome
ms.openlocfilehash: 15c62369bb8b4fc02926fa0e2b0bfc4834c371ac
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/19/2022
ms.locfileid: "63572228"
---
# <a name="learn-about-the-microsoft-compliance-extension"></a>التعرف على ملحق التوافق من Microsoft

تعمل عملية منع فقدان بيانات نقطة النهاية [(DLP)](endpoint-dlp-learn-about.md) على توسيع قدرات مراقبة النشاط والحماية ل Microsoft 365 فقدان البيانات [(DLP)](dlp-learn-about-dlp.md) إلى العناصر الحساسة الموجودة على Windows 10 الأجهزة. بمجرد أن يتم االأجهزة في حلول توافق Microsoft 365، تظهر المعلومات حول ما يفعله المستخدمون بالعناصر الحساسة في مستكشف النشاط، كما يمكنك فرض إجراءات [](data-classification-activity-explorer.md) الحماية على هذه العناصر عبر سياسات [DLP](create-test-tune-dlp-policy.md).

بمجرد تثبيت ملحق التوافق من Microsoft على جهاز Windows 10، يمكن أن تراقب المؤسسات عندما يحاول المستخدم الوصول إلى عنصر حساس أو تحميله إلى خدمة سحابية باستخدام Google Chrome وفرض إجراءات الحماية عبر DLP.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>الأنشطة التي يمكنك مراقبتها واتخاذ إجراء بشأنها

يمكنك ملحق التوافق من Microsoft من تدقيق وإدارة أنواع الأنشطة التالية التي ينفذها المستخدمون على العناصر الحساسة على الأجهزة التي تعمل Windows 10.

نشاط |الوصف  | إجراءات النهج المعتمدة|
|---------|---------|---------|
|ملف تم نسخه إلى السحابة  | الكشف عن الوقت الذي يحاول فيه المستخدم تحميل عنصر حساس إلى مجال خدمة مقيد من خلال مستعرض Chrome |تدقيق، حظر مع تجاوز، حظر|
|الملف المطبوع  |الكشف عن الوقت الذي يحاول فيه المستخدم طباعة عنصر حساس مفتوح في مستعرض Chrome إلى طابعة محلية أو على الشبكة |تدقيق، حظر مع تجاوز، حظر|
|ملف تم نسخه إلى الحافظة |الكشف عن الوقت الذي يحاول فيه المستخدم نسخ معلومات من عنصر حساس يتم عرضه في مستعرض Chrome ثم لصقها في تطبيق أو عملية أو عنصر آخر. |تدقيق، حظر مع تجاوز، حظر|
|ملف تم نسخه إلى مساحة تخزين قابلة للإزالة    | الكشف عن متى يحاول المستخدم نسخ عنصر حساس أو معلومات من عنصر حساس مفتوح في مستعرض Chrome إلى وسائط قابلة للإزالة أو جهاز USB |تدقيق، حظر مع تجاوز، حظر|
|ملف تم نسخه لمشاركة الشبكة  |الكشف عن الوقت الذي يحاول فيه المستخدم نسخ عنصر أو معلومات حساسة من عنصر حساس مفتوح في مستعرض Chrome إلى مشاركة شبكة أو محرك أقراص شبكة تم تعيينه.|تدقيق، حظر مع تجاوز، حظر |

## <a name="deployment-process"></a>عملية النشر
1. [بدء استخدام منع فقدان البيانات في نقطة النهاية](endpoint-dlp-getting-started.md)
2. [أدوات وأساليب التكهين للأجهزة Windows 10 الأجهزة](device-onboarding-overview.md)
3. [تثبيت الملحق على الأجهزة Windows 10 الخاصة بك](dlp-chrome-get-started.md)
4. [إنشاء أو تحرير سياسات DLP](create-test-tune-dlp-policy.md) التي تقيد التحميل إلى خدمة السحابة، أو الوصول بواسطة إجراءات المستعرضات غير مسموح بها وتطبيقها على أجهزة Windows 10 الخاصة بك

## <a name="next-steps"></a>الخطوات التالية

راجع [بدء استخدام ملحق التوافق من Microsoft](dlp-chrome-get-started.md) للحصول على إجراءات وسيناريوهات النشر الكاملة.

## <a name="see-also"></a>راجع أيضًا

- [بدء العمل باستخدام ملحق التوافق من Microsoft](dlp-chrome-get-started.md)
- [التعرف على Microsoft 365 فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [بدء استخدام منع فقدان بيانات نقطة نهاية Microsoft](endpoint-dlp-getting-started.md)
- [استخدام منع فقدان بيانات نقطة نهاية Microsoft](endpoint-dlp-using.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام "مستكشف النشاط"](data-classification-activity-explorer.md)
- [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)
- [إدارة مخاطر Insider](insider-risk-management.md)
