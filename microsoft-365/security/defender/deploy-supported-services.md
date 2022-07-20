---
title: توزيع الخدمات المدعومة من قبل Microsoft 365 Defender
description: تعرف على خدمات أمان Microsoft التي يمكن دمجها بواسطة Microsoft 365 Defender ومتطلبات الترخيص وإجراءات النشر الخاصة بها
keywords: النشر، والتراخيص، والخدمات المدعومة، والتوفير، Microsoft 365 Defender التكوين، وM365، وأهلية الترخيص، Microsoft Defender لنقطة النهاية، Microsoft Defender لـ Office 365، Microsoft Defender for Identity، Microsoft Cloud App Security، MCAS، E5، A5، EMS
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-getstarted
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: cf2e95a4d129280537f1d7a9d7dcf1b76b492ead
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893760"
---
# <a name="deploy-supported-services"></a>نشر الخدمات المعتمدة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Microsoft 365 Defender](microsoft-365-defender.md) دمج خدمات أمان Microsoft المختلفة لتوفير قدرات مركزية للكشف والوقاية والتحقيق ضد الهجمات المتطورة. تصف هذه المقالة الخدمات المدعومة ومتطلبات الترخيص الخاصة بها والمزايا والقيود المرتبطة بنشر واحدة أو أكثر من الخدمات وارتباطات إلى كيفية نشرها بشكل كامل بشكل فردي.

## <a name="supported-services"></a>الخدمات المدعومة

يوفر ترخيص Microsoft 365 E5 أو E5 Security أو A5 أو A5 Security أو مجموعة صالحة من التراخيص الوصول إلى الخدمات المدعومة التالية ويؤه لك استخدام Microsoft 365 Defender. [الاطلاع على متطلبات الترخيص](prerequisites.md#licensing-requirements)

| الخدمة المدعومة | الوصف |
| ------ | ------ |
| Microsoft Defender for Endpoint | مجموعة حماية نقطة النهاية المبنية حول أجهزة الاستشعار السلوكية القوية والتحليلات السحابية والتحليل الذكي للمخاطر |
|Microsoft Defender لـ Office 365 | حماية متقدمة لتطبيقاتك وبياناتك في Office 365، بما في ذلك البريد الإلكتروني وأدوات التعاون الأخرى |
| Microsoft Defender للهوية | الدفاع ضد التهديدات المتقدمة والهويات المخترقة والمطلعين الضارين باستخدام إشارات Active Directory المرتبطة |
| Microsoft Defender for Cloud Apps | تحديد التهديدات الإلكترونية ومكافحتها عبر خدمات Microsoft والخدمات السحابية لجهات خارجية |

## <a name="deployed-services-and-functionality"></a>الخدمات والوظائف المنشورة

يوفر Microsoft 365 Defender رؤية وارتباطا ومعالجة أفضل أثناء نشر خدمات أكثر دعما.

### <a name="benefits-of-full-deployment"></a>فوائد النشر الكامل

للحصول على الفوائد الكاملة Microsoft 365 Defender، نوصي بنشر جميع الخدمات المدعومة. فيما يلي بعض الفوائد الرئيسية للنشر الكامل:

- يتم تحديد الحوادث وربطها استنادا إلى التنبيهات وإشارات الأحداث من جميع أجهزة الاستشعار المتاحة وقدرات التحليل الخاصة بخدمتها
- تنطبق أدلة مبادئ التحقيق والمعالجة التلقائية (AIR) عبر أنواع الكيانات المختلفة، بما في ذلك الأجهزة وعلب البريد وحسابات المستخدمين
- يمكن الاستعلام عن مخطط تتبع متقدم أكثر شمولا لبيانات الحدث والكيان من الأجهزة وعلب البريد والكيانات الأخرى

### <a name="limited-deployment-scenarios"></a>سيناريوهات توزيع محدودة

توفر كل خدمة مدعومة تقوم بنشرها مجموعة غنية للغاية من الإشارات الأولية بالإضافة إلى المعلومات المرتبطة. على الرغم من أن التوزيع المحدود لا يتسبب في إيقاف تشغيل وظائف Microsoft 365 Defender، فإن قدرتها على توفير رؤية شاملة عبر نقاط النهاية والتطبيقات والبيانات والهويات تتأثر. في الوقت نفسه، تنطبق أي قدرات معالجة فقط على الكيانات التي يمكن إدارتها بواسطة الخدمات التي قمت بنشرها.

يسرد الجدول أدناه كيف توفر كل خدمة مدعومة بيانات إضافية، وفرصا للحصول على نظرة ثاقبة إضافية من خلال ربط البيانات، وقدرات أفضل للمعالجة والاستجابة.

| الخدمة | البيانات (الإشارات & معلومات مرتبطة) | نطاق استجابة & المعالجة |
| ------ | ------ | ------ |
| Microsoft Defender for Endpoint |<ul><li>حالات نقطة النهاية والأحداث الأولية</li><li>عمليات الكشف عن نقاط النهاية والتنبيهات، بما في ذلك مكافحة الفيروسات، وEDR، وتقليل الأجزاء المعرضة للهجوم</li><li>معلومات حول الملفات والكيانات الأخرى التي تمت ملاحظتها على نقاط النهاية</li></ul> | النهايه |
|Microsoft Defender لـ Office 365 |<ul><li>حالات البريد وعلب البريد والأحداث الأولية</li><li>عمليات الكشف عن البريد الإلكتروني والمرفقات والارتباطات</li></ul> | <ul><li>صناديق البريد</li><li>حسابات Microsoft 365</li></ul> |
| Microsoft Defender للهوية |<ul><li>إشارات Active Directory، بما في ذلك أحداث المصادقة</li><li>عمليات الكشف السلوكية المتعلقة بالهوية</li></ul> | الهويات |
| Microsoft Defender for Cloud Apps |<ul><li>الكشف عن تطبيقات وخدمات السحابة غير الملغاة (Shadow IT)</li><li>تعرض البيانات لتطبيقات السحابة</li><li>نشاط التهديد المقترن بتطبيقات السحابة</li></ul> | تطبيقات السحابة |

## <a name="deploy-the-services"></a>توزيع الخدمات

يتطلب نشر كل خدمة عادة تزويد المستأجر وبعض التكوين الأولي. راجع الجدول التالي لفهم كيفية نشر كل من هذه الخدمات.

| الخدمة | تعليمات التزويد | التكوين الأولي |
| ------ | ------ | ------ |
| Microsoft Defender for Endpoint | [دليل نشر Microsoft Defender لنقطة النهاية](../defender-endpoint/deployment-phases.md) | *راجع إرشادات التزويد* |
|Microsoft Defender لـ Office 365 | *بلا، تم توفيره مع Office 365* | [تكوين نهج Microsoft Defender لـ Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) |
| Microsoft Defender للهوية | [التشغيل السريع: إنشاء مثيل Microsoft Defender for Identity](/azure-advanced-threat-protection/install-atp-step1) | *راجع إرشادات التزويد* |
| Microsoft Defender for Cloud Apps | *None* | [التشغيل السريع: بدء استخدام Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security) |

بمجرد نشر الخدمات المدعومة، [قم بتشغيل Microsoft 365 Defender](m365d-enable.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على Microsoft 365 Defender](microsoft-365-defender.md)
- [تمكين Microsoft 365 Defender](m365d-enable.md)
- [نظرة عامة على Microsoft Defender لنقطة النهاية](../defender-endpoint/microsoft-defender-endpoint.md)
- [نظرة عامة على Microsoft Defender لـ Office 365](../office-365-security/defender-for-office-365.md)
- [نظرة عامة على Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [نظرة عامة على Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)
