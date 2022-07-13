---
title: تمكين بيئة التقييم Microsoft Defender for Cloud Apps
description: تعرف على بنية Defender for Cloud Apps ضمن Microsoft Defender لـ Office 365 وفهم التفاعلات بين منتجات Microsoft 365 Defender.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 0c9f4687cf36d4db5f22cd6e1b95f55eebc84cf9
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749913"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>تمكين بيئة التقييم Microsoft Defender for Cloud Apps

**ينطبق على:**

- Microsoft 365 Defender

هذه المقالة هي [الخطوة 2 من 2](eval-defender-mcas-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender for Cloud Apps. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-mcas-overview.md).

ترشدك هذه المقالة خلال عملية الوصول إلى مدخل Defender for Cloud Apps وتكوين التكامل اللازم لجمع بيانات حركة مرور تطبيق السحابة.

لاكتشاف تطبيقات السحابة المستخدمة في بيئتك، يمكنك تنفيذ أحد الأسلوبين التاليين أو كليهما:

- يمكنك بدء الاستخدام والتشغيل بسرعة باستخدام Cloud Discovery من خلال التكامل مع Microsoft Defender لنقطة النهاية. يمكنك هذا التكامل الأصلي من البدء فورا في جمع البيانات حول حركة مرور السحابة عبر أجهزة Windows 10 Windows 11، على شبكتك وخارجها.
- لاكتشاف جميع تطبيقات السحابة التي يتم الوصول إليها من قبل جميع الأجهزة المتصلة بشبكتك، قم بنشر مجمع سجل Defender for Cloud Apps على جدران الحماية والوكلاء الآخرين. يساعد هذا النشر على جمع البيانات من نقاط النهاية الخاصة بك ويرسلها إلى Defender for Cloud Apps للتحليل. يتكامل Defender for Cloud Apps في الأصل مع بعض وكلاء الجهات الخارجية للحصول على المزيد من القدرات.

تتضمن هذه المقالة إرشادات لكلا الأسلوبين.

استخدم الخطوات التالية لإعداد Microsoft Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-eval-enable-steps.png" alt-text="خطوات تمكين Microsoft Microsoft Defender for Cloud Apps في بيئة تقييم Microsoft Defender" lightbox="../../media/defender/m365-defender-mcas-eval-enable-steps.png":::

- [الخطوة 1. الاتصال بمدخل Defender for Cloud Apps](#step-1)
- [الخطوة 2. التكامل مع Microsoft Defender لنقطة النهاية](#step-2)
- [الخطوة 3. توزيع مجمع سجل Defender for Cloud Apps على جدران الحماية والوكلاء الآخرين](#step-3)
- [الخطوة 4. عرض لوحة معلومات Cloud Discovery لمعرفة التطبيقات المستخدمة في مؤسستك](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>الخطوة 1. الاتصال بمدخل Defender for Cloud Apps

للتحقق من الترخيص وللاتصال بمدخل Defender for Cloud Apps، راجع [التشغيل السريع: بدء استخدام Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security).

إذا لم تتمكن من الاتصال بالمدخل على الفور، فقد تحتاج إلى إضافة عنوان IP إلى قائمة السماح لجدار الحماية الخاص بك. راجع [الإعداد الأساسي ل Defender for Cloud Apps](/cloud-app-security/general-setup).

إذا كنت لا تزال تواجه مشكلة، فراجع [متطلبات الشبكة](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>الخطوة 2. التكامل مع Microsoft Defender لنقطة النهاية

يتكامل Microsoft Defender for Cloud Apps مع Microsoft Defender لنقطة النهاية في الأصل. يبسط التكامل طرح Cloud Discovery، ويوسع قدرات Cloud Discovery خارج شبكة شركتك، ويمكن التحقيق المستند إلى الجهاز. يكشف هذا التكامل عن التطبيقات والخدمات السحابية التي يتم الوصول إليها من Windows 10 وأجهزة Windows 11 التي تديرها تكنولوجيا المعلومات.

إذا قمت بالفعل بإعداد Microsoft Defender لنقطة النهاية، فإن تكوين التكامل مع Defender for Cloud Apps هو تبديل في Microsoft 365 Defender. بعد تشغيل التكامل، يمكنك العودة إلى مدخل Defender for Cloud Apps وعرض البيانات الغنية في لوحة معلومات اكتشاف السحابة.

لإنجاز هذه المهام، راجع [Microsoft Defender لنقطة النهاية التكامل مع Microsoft Defender for Cloud Apps](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>الخطوة 3. توزيع مجمع سجل Defender for Cloud Apps على جدران الحماية والوكلاء الآخرين

للتغطية على جميع الأجهزة المتصلة بشبكتك، قم بنشر جامع سجل Defender for Cloud Apps على جدران الحماية والوكلاء الآخرين لجمع البيانات من نقاط النهاية وإرسالها إلى Defender for Cloud Apps للتحليل.

إذا كنت تستخدم إحدى بوابات الويب الآمنة التالية (SWG)، فإن Defender for Cloud Apps يوفر التوزيع والتكامل السلسين:

- Zscaler
- iboss
- Corrata
- أمان Menlo

لمزيد من المعلومات حول التكامل مع أجهزة الشبكة هذه، راجع [إعداد Cloud Discovery](/cloud-app-security/set-up-cloud-discovery).

<a name="step-4"></a>

## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>الخطوة 4. عرض لوحة معلومات Cloud Discovery لمعرفة التطبيقات المستخدمة في مؤسستك

تم تصميم لوحة معلومات Cloud Discovery لمنحك المزيد من المعلومات حول كيفية استخدام تطبيقات السحابة في مؤسستك. يوفر نظرة سريعة على أنواع التطبيقات المستخدمة والتنبيهات المفتوحة ومستويات المخاطر للتطبيقات في مؤسستك.

لبدء استخدام لوحة معلومات Cloud Discovery، راجع ["العمل مع التطبيقات المكتشفة](/cloud-app-security/discovered-apps)".

## <a name="next-steps"></a>الخطوات التالية

الخطوة 3 من 3: [Microsoft Defender for Cloud Apps التجريبية](eval-defender-mcas-pilot.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)
