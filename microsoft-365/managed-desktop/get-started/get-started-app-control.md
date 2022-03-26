---
title: بدء استخدام عنصر تحكم التطبيق
description: تصف هذه المقالة كيفية تمكين التحكم في التطبيق
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: a671bf36e957ffc416f51ec531aaeed6ddfa41b3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63571151"
---
# <a name="get-started-with-app-control"></a>بدء استخدام عنصر تحكم التطبيق

قبل تمكين التحكم في التطبيق في بيئتك، تأكد من مراجعة وفهم كيفية تنفيذ [Microsoft Managed Desktop](../service-description/app-control.md) له وأدوارك ومسؤولياتك.

يبسط Microsoft Managed Desktop التحكم في التطبيق من خلال الاهتمام بالجوانب الأكثر صعوبة للحصول على نهج أساس آمن.

يجب على مسؤولي تكنولوجيا معلومات اختبار تطبيقاتك في حلقة الاختبار ومراجعة السجلات لأي تحذيرات أو أخطاء. إذا كان التطبيق يحتاج إلى استثناء، يمكنك تقديم طلب، أو قد تكون عملية سطح المكتب المدارة من Microsoft، استنادا إلى الشخص الذي يكتشفه أولا.

## <a name="initial-deployment-of-apps"></a>النشر الأولي للتطبيقات

عند نشر التطبيقات لأول مرة، يحتاج Microsoft Managed Desktop إلى تقييم سلوكها الحالي. تعتمد الخطوات الدقيقة لتمكين التحكم في التطبيق على ما إذا كانت الأجهزة قد تم نشرها بالفعل في بيئتك.

### <a name="devices-not-yet-in-use"></a>الأجهزة التي لم يتم استخدامها بعد

إذا لم يكن لديك أي أجهزة تستخدم بعد، فافتح تذكرة دعم باستخدام عمليات سطح المكتب المدارة من Microsoft لطلب تشغيل التحكم في التطبيق. ستنشر العمليات تدريجيا سياسات لمجموعات النشر باتباع هذا الجدول:

| مجموعة النشر | نوع النهج | التوقيت |
| ------ | ------ | ------ |
| اختبار |  التدقيق |  اليوم 0 |
| أولا | فرض | اليوم الأول |
| سريع | فرض |  اليوم الثاني |
| واسع | فرض |  اليوم الثالث |

يمكنك دائما فتح طلب دعم آخر لإيقاف جزء من هذا النشر مؤقتا أو التراجع فيه في أي وقت أثناء عملية النشر.

### <a name="devices-already-in-use"></a>الأجهزة التي تستخدم بالفعل

إذا كان هناك جهاز سطح مكتب مدار واحد على الأقل من Microsoft يستخدم، فاتبع الخطوات التالية:

1. افتح تذكرة خدمة باستخدام عمليات سطح المكتب المدارة من Microsoft التي تطلب منا تشغيل التحكم في التطبيق. ستنشر العمليات نهج [تدقيق](../service-description/app-control.md#audit-policy) على جميع الأجهزة.
2. [اختبر تطبيقاتك](../working-with-managed-desktop/work-with-app-control.md#add-a-new-app) لمعرفة ما إذا كان سيتم حظر أي تطبيقات. إذا تم حظر أحد التطبيقات، فافتح [طلب توقيع](../working-with-managed-desktop/work-with-app-control.md#add-or-remove-a-trusted-signer).
3. بعد إكمال الاختبار (أيا كانت النتائج)، قم بإعلام العمليات، مع الإشارة إلى أي طلبات توقيع معلقة. ستنشر العمليات تدريجيا سياسات لمجموعات النشر باتباع هذا الجدول:

| مجموعة النشر | نوع النهج | التوقيت |
| ------ | ------ | ------ |
| اختبار     | التدقيق |  اليوم 0 |
| أولا     | فرض | اليوم الأول |
| سريع     | فرض |  تم إيقافه مؤقتا، مع طرحه عند الطلب |
| واسع     | فرض |  تم إيقافه مؤقتا، مع طرحه عند الطلب |

يمكنك دائما فتح طلب دعم آخر لإيقاف جزء من هذا النشر مؤقتا أو التراجع فيه في أي وقت أثناء عملية النشر.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>خطوات بدء تشغيل Microsoft Managed Desktop

1. مدخل [مسؤول Access](access-admin-portal.md).
1. [إضافة جهات اتصال المسؤول والتحقق منها في مدخل المسؤول](add-admin-contacts.md).
1. [ضبط الإعدادات بعد التسجيل](conditional-access.md).
1. نشر [Intune Company Portal.](company-portal.md)
1. [تعيين التراخيص](assign-licenses.md).
1. [نشر التطبيقات](deploy-apps.md).
1. [تحضير الأجهزة](prepare-devices.md).
1. قم بإعداد [تجربة التشغيل الأولي باستخدام Autopilot وصفحة حالة التسجيل](esp-first-run.md).
1. [تمكين ميزات دعم المستخدم](enable-support.md).
1. [اجهز المستخدمين لاستخدام الأجهزة](get-started-devices.md).
1. بدء استخدام عنصر تحكم التطبيق (هذه المقالة).
