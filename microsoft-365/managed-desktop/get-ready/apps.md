---
title: التطبيقات في Microsoft Managed Desktop
description: يشرح كيفية التعامل مع التطبيقات، بما في ذلك كيفية حزمها ونشرها ودعمها.
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ce43080c284c4c15be5a8799f70a43de611ff9ba
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63566070"
---
# <a name="apps-in-microsoft-managed-desktop"></a>التطبيقات في Microsoft Managed Desktop

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->

## <a name="apps-generally"></a>التطبيقات بشكل عام

تتضمن Microsoft تطبيقات أساسية معينة إلى جانب ترخيص Microsoft 365 E3 E5 المطلوب للمشاركة في Microsoft Managed Desktop. ومع ذلك، على الرغم من أننا نوفر هذه التطبيقات، لا يزال لديك بعض المسؤوليات والإجراءات التي يجب إكمالها.

يمكنك أيضا نشر تطبيقات إضافية غير Microsoft للمستخدمين عبر الخدمة الذاتية عبر Company Portal أو تثبيت خلفية مطلوب باستخدام Microsoft Intune شبكة التوزيع الخاصة بك.

## <a name="apps-provided-by-microsoft"></a>التطبيقات التي توفرها Microsoft

يتضمن ترخيص Microsoft Managed Desktop الإصدارات 64 بت من التطبيقات في Microsoft 365 Apps ل Enterprise Standard Suite (Word و Excel و PowerPoint و Outlook و Publisher و Access و Teams و OneNote.)

لا يتم تضمين إصدارات Microsoft Project التشغيل Visio بشكل افتراضي، ولكن يمكنك طلب إضافتها.  لمزيد من المعلومات حول هذه التطبيقات، راجع [تثبيت Microsoft Project أو Microsoft Visio على أجهزة سطح المكتب المدارة من Microsoft](../get-started/project-visio.md).

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>ما الذي تقوم به Microsoft لدعم التطبيقات التي نوفرها

ستقوم Microsoft بتوفير الخدمة الكاملة لنشر التطبيقات Microsoft 365 Apps for enterprise وتحديثها ودعمها. لا يتم تضمين إصدارات Microsoft Project التشغيل Visio *بشكل* افتراضي. ومع ذلك، سيوفر Microsoft Managed Desktop مجموعات نشر للسماح لمسؤول تكنولوجيا المعلومات بإدارة التراخيص، ونشر هذه التطبيقات بشكل مناسب لمنظمتك. ستدعم Microsoft مستخدمي هذه التطبيقات من خلال قنوات دعم Microsoft Managed Desktop.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>ما يجب فعله لدعم التطبيقات التي نوفرها

لا تزال هناك بعض الأمور التي تحتاج إلى القيام بها باستخدام هذه التطبيقات:

| مهمة | الوصف |
| ------ | ------ |
| تعيين التراخيص | أنت مسؤول عن الحصول على التراخيص المناسبة وتعيينها للمستخدمين Microsoft 365 Apps for enterprise. |
| إضافة مستخدمين إلى مجموعات الأمان | إذا كنت تستخدم Microsoft Project أو Visio، فيجب على مسؤول تكنولوجيا البيانات إضافة هؤلاء المستخدمين إلى مجموعات النشر المناسبة. ويتحمل أيضا المسؤولون عن تكنولوجيا البيانات مسؤولية استعادة التراخيص من هؤلاء المستخدمين إذا غادروا الشركة. |
| نشر Microsoft 365 الإضافية | إذا كنت بحاجة إلى أي من الوظائف الإضافية لأي من تطبيقات Microsoft 365 Apps for enterprise، فنشرها مركزيا مثل أي تطبيق Windows 32.

## <a name="apps-you-provide"></a>التطبيقات التي تقدمها

من المحتمل أن يكون لديك تطبيقات أخرى تحتاج إليها لعملياتك التجارية. لا يمكن نشر هذه التطبيقات إلا على أجهزة سطح المكتب المدارة من Microsoft باستخدام Microsoft Intune التوزيع الخاصة ب Microsoft. لمزيد من المعلومات حول نشر التطبيق، اتبع الخطوات الواردة في [نشر التطبيقات على أجهزة سطح المكتب المدارة من Microsoft](../get-started/deploy-apps.md).

### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>تحضير تطبيقاتك لتضمينها في Microsoft Managed Desktop

راجع تطبيقاتك، ثم تحقق من:

- لا يحظر أي تطبيق من التطبيقات أو يكون سلوكه مقيدا، كما هو موضح في [متطلبات تطبيق Microsoft Managed Desktop](../service-description/mmd-app-requirements.md).
- يجب أن تكون التطبيقات جاهزة للإدارة Microsoft Intune. لمزيد من المعلومات، راجع Windows 10 [التطبيق باستخدام Microsoft Intune](/intune/apps-windows-10-app-deploy) [وإضافة تطبيقات إلى Microsoft Intune](/intune/apps-add).
- متطلبات التعبئة المسبقة الأخرى مثل توفير مفاتيح التراخيص، والاتفاقيات مع شروط الترخيص، واتصالات الخادم المسبقة.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>خطوات الاستعداد لسطح المكتب المدار من Microsoft

1. مراجعة [المتطلبات الأساسية لسطح المكتب المدار من Microsoft](prerequisites.md).
1. تشغيل [أدوات تقييم الجهوزية](readiness-assessment-tool.md).
1. شراء [Company Portal](../get-started/company-portal.md).
1. مراجعة [المتطلبات الأساسية الخاصة وحسابات الضيوف](guest-accounts.md).
1. تحقق [من تكوين الشبكة](network.md).
1. [إعداد الشهادات وملفات تعريف الشبكة](certs-wifi-lan.md).
1. [إعداد وصول المستخدم إلى البيانات](authentication.md).
1. تحضير التطبيقات (هذه المقالة).
1. [إعداد محركات أقراص تم تعيينها](mapped-drives.md).
1. [تحضير موارد الطباعة](printing.md).
1. أسماء [أجهزة العنوان](address-device-names.md).
