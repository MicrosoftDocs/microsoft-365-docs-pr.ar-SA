---
title: نشر إعدادات قابلة للتكوين في Microsoft Managed Desktop
description: نشر التغييرات في الإعدادات القابلة للتكوين وتعقبها في Microsoft Managed Desktop.
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق، النشر، النشر على مراحل، إعدادات قابلة للتكوين
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a52995ff9ab2f946ca11417d4ed7bfa13825353f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566498"
---
# <a name="deploy-and-track-configurable-settings---microsoft-managed-desktop"></a>نشر الإعدادات القابلة للتكوين وتعقبها - Microsoft Managed Desktop

بعد إجراء تغييرات على فئات الإعدادات ومرحلة نشر، تسمح لك صفحة حالة النشر ببدء نشر الإعدادات إلى المجموعات. تعرض هذه الصفحة ملخصا لكل إعداد قابل للتكوين. عند فتح فئة إعداد، يمكنك نشر الإعدادات للمجموعات وتعقب تقدم عمليات النشر هذه.

## <a name="deployment-statuses"></a>حالة النشر

فيما يلي الحالات التي ستشاهدها لكل عملية نشر.

الحالة | شرح
--- | ---
نشر | التغيير بانتظار نشره في هذه المجموعة.
التقدم | يتم تطبيق التغيير على الأجهزة النشطة في هذه المجموعة.
مكتمل | تم إكمال التغيير على جميع الأجهزة النشطة في هذه المجموعة.
فشل | فشل التغيير على 10 بالمائة من الأجهزة النشطة في المجموعة. تم إيقاف النشر.<br><br> سيتم فتح طلب دعم تلقائيا باستخدام عمليات Microsoft Managed Desktop لا استكشاف الأخطاء في النشر وإصلاحها.
تم الرجوع | تم إعادة التغيير إلى التغيير الأخير الذي تم نشره بنجاح إلى كل مجموعات النشر.

## <a name="deploy-changes"></a>نشر التغييرات

على سبيل المثال، سنستخدم صورة خلفية سطح المكتب في هذه الإرشادات. بعد إجراء عملية نشر، يمكنك نشر التغييرات من صفحة حالة النشر.

**لنشر التغييرات:**

1. سجل [الدخول إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/) وانتقل إلى **قائمة** الأجهزة.
2. في المقطع Microsoft Managed Desktop **، حدد الإعدادات**.
3. في مساحة **عمل حالة** النشر، حدد الإعداد الذي تريد نشره. بعد ذلك، حدد النشر المرحلي للنشر.
4. حدد **نشر** لنشر التغيير إلى إحدى مجموعات النشر.

> [!NOTE]
> تشير أيقونة التحذير البرتقالي إلى أن هناك مجموعة سابقة متوفرة للنشر حيث من المستحسن نشرها بالترتيب.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Trusted sites pane on the right. In the Deployment groups section are three columns: deployment groups, devices, and status. In the status column, "deploy" is highlighted.](../../media/1deployedit.png) -->

نوصي بالنشر لمجموعات النشر بهذا الترتيب: اختبار، أولا، سريع، ثم واسع.

عند اكتمال التغييرات في كل مجموعة، تتغير الحالة إلى **مكتمل**.

<!-- Needs picture updated to show MEM ![Deployment status workspace with columns for date updated, version, test, first, fast, and broad. The Proxy row is expanded, showing a dated setting flagged as "complete" in each of the four deployment groups.](../../media/2completeedit.png) -->

## <a name="revert-deployment"></a>إعادة النشر

بعد نشر التغيير، يمكنك العودة من حالة **النشر**. عندما تقوم بعكس تغيير يكون في **التقدم أو** **مكتمل**، يتوقف النشر الحالي. سيتم إعادة الإعداد إلى الإصدار الأخير الذي تم نشره إلى كل المجموعات.

على سبيل المثال، سنقوم بعكس صورة خلفية سطح المكتب.

**لإعادة تغيير:**

1. سجل [الدخول إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/) وانتقل إلى **قائمة** الأجهزة.
2. في المقطع Microsoft Managed Desktop **، حدد الإعدادات**.
3. في مساحة **عمل حالة** النشر، حدد الإعداد الذي تريد العودة. بعد ذلك، حدد النشر المرحلي للعكس.
4. ضمن **هل تحتاج إلى إعادة هذا التغيير؟**، حدد **إعادة النشر**.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Browser start pages is selected, opening a pane on the right side with data about the submitted change and its status. At the bottom is the "need to revert this change" area where you can select "Revert deployment."](../../media/3revert.png) -->

## <a name="additional-resources"></a>موارد إضافية

- [نظرة عامة على الإعدادات القابلة للتكوين](config-setting-overview.md)
- [مرجع الإعدادات القابلة للتكوين](config-setting-ref.md)
