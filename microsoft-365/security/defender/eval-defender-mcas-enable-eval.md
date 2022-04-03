---
title: تمكين بيئة التقييم Microsoft Defender for Cloud Apps
description: تعرف على تصميم Defender for Cloud Apps Microsoft Defender لـ Office 365 التفاعلات بين Microsoft 365 Defender السحابة.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: a66a3563d01e8e4239a0f4815fec9234fd46e1fc
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498968"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>تمكين بيئة التقييم Microsoft Defender for Cloud Apps

**ينطبق على:**

- Microsoft 365 Defender

هذه المقالة هي [الخطوة 2 من 2](eval-defender-mcas-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender for Cloud Apps. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-mcas-overview.md).

ادفعك هذه المقالة خلال عملية الوصول إلى مدخل Defender for Cloud Apps وتكوين التكامل اللازم لجمع بيانات حركة مرور تطبيقات السحابة.

لاكتشاف تطبيقات السحابة المستخدمة في بيئتك، يمكنك تنفيذ أحد الأساليب التالية أو كليهما:

- يمكنك العمل بسرعة مع "اكتشاف السحابة" من خلال التكامل مع Microsoft Defender لنقطة النهاية. يمكنك هذا التكامل الأصلي من البدء فورا في تجميع البيانات على حركة مرور السحابة عبر أجهزة Windows 10 وأجهزة Windows 11، على الشبكة أو خارجها.
- لاكتشاف جميع تطبيقات السحابة التي يمكن الوصول إليها من قبل جميع الأجهزة المتصلة بالشبكة، انتشر سجل Defender for Cloud Apps الذي تم تجميعه على جدران الحماية الخاصة بك وغيرها من المحترفين. يساعد هذا النشر في تجميع البيانات من نقاط النهاية وإرسالها إلى Defender for Cloud Apps لتحليلها. يتكامل Defender for Cloud Apps بشكل أصلي مع بعض تكاملات  الأطراف الخارجية للحصول على المزيد من الإمكانات.

تتضمن هذه المقالة إرشادات لكلا الطريقة.

استخدم الخطوات التالية لإعداد Microsoft Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-eval-enable-steps.png" alt-text="الخطوات اللازمة لتمكين Microsoft Microsoft Defender for Cloud Apps في بيئة تقييم Microsoft Defender" lightbox="../../media/defender/m365-defender-mcas-eval-enable-steps.png":::

- [الخطوة 1. الاتصال إلى مدخل Defender for Cloud Apps](#step-1)
- [الخطوة 2. التكامل مع Microsoft Defender لنقطة النهاية](#step-2)
- [الخطوة 3. نشر سجل Defender for Cloud Apps الذي تم تجميعه على جدران الحماية الخاصة بك والتك وكلائك الآخرين](#step-3)
- [الخطوة 4. عرض لوحة معلومات "اكتشاف السحابة" لمعرفة التطبيقات المستخدمة في مؤسستك](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>الخطوة 1. الاتصال إلى مدخل Defender for Cloud Apps

للتحقق من الترخيص والاتصال بمدخل Defender for Cloud Apps، راجع البدء السريع[: بدء استخدام](/cloud-app-security/getting-started-with-cloud-app-security) Microsoft Defender for Cloud Apps.

إذا لم تتمكن من الاتصال مباشرة إلى المدخل، فقد تحتاج إلى إضافة عنوان IP إلى قائمة السماح بجدار الحماية. راجع [الإعداد الأساسي ل Defender for Cloud Apps](/cloud-app-security/general-setup).

إذا كنت لا تزال تواجه مشكلة، فراجع [متطلبات الشبكة](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>الخطوة 2. التكامل مع Microsoft Defender لنقطة النهاية

Microsoft Defender for Cloud Apps التكامل مع Microsoft Defender لنقطة النهاية الأصلية. يبسط التكامل عملية طرح "اكتشاف السحابة"، ويوسع إمكانات "اكتشاف السحابة" خارج شبكة الشركة، كما يمكن إجراء تحقيق مستند إلى الأجهزة. يكشف هذا التكامل عن تطبيقات السحابة والخدمات التي يتم الوصول إليها من أجهزة Windows 10 المعلومات Windows 11 الأجهزة.

إذا سبق لك إعداد Microsoft Defender لنقطة النهاية، فإن تكوين التكامل مع Defender for Cloud Apps هو تبديل في Microsoft 365 Defender. بعد تشغيل التكامل، يمكنك العودة إلى مدخل Defender for Cloud Apps وعرض البيانات الغنية في لوحة معلومات اكتشاف السحابة.

لتنفيذ هذه المهام، راجع Microsoft Defender لنقطة النهاية [التكامل مع Microsoft Defender for Cloud Apps](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>الخطوة 3. نشر سجل Defender for Cloud Apps الذي تم تجميعه على جدران الحماية الخاصة بك والتك وكلائك الآخرين

للتغطية على جميع الأجهزة المتصلة بالشبكة، قم بنشر سجل Defender for Cloud Apps الذي تم تجميعه على جدران الحماية الخاصة بك والتك وكلائك الآخرين لتجميع البيانات من نقاط النهاية وإرسالها إلى Defender for Cloud Apps لتحليلها.

إذا كنت تستخدم إحدى بوابات الويب الآمنة (SWG) التالية، فإن Defender for Cloud Apps يوفر النشر والتكامل السلسين:

- Zscaler
- iboss
- Corrata
- أمان Menlo

لمزيد من المعلومات حول التكامل مع أجهزة الشبكة هذه، راجع [إعداد اكتشاف السحابة](/cloud-app-security/set-up-cloud-discovery).

<a name="step-4"></a>

## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>الخطوة 4. عرض لوحة معلومات "اكتشاف السحابة" لمعرفة التطبيقات المستخدمة في مؤسستك

تم تصميم لوحة معلومات Cloud Discovery لتعطيك معرفة أكثر حول كيفية استخدام تطبيقات السحابة في مؤسستك. ويوفر نظرة عامة سريعة حول أنواع التطبيقات المستخدمة والتنبيهات المفتوحة ومستويات المخاطر للتطبيقات في مؤسستك.

للبدء باستخدام لوحة معلومات "اكتشاف السحابة"، راجع [استخدام التطبيقات المكتشفة](/cloud-app-security/discovered-apps).

## <a name="next-steps"></a>الخطوات التالية

الخطوة 3 من 3: [التجربة Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md)

العودة إلى نظرة عامة [حول تقييم](eval-defender-mcas-overview.md) Microsoft Defender for Cloud Apps

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)
