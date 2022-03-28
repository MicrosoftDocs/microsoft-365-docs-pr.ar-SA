---
title: أسماء الأجهزة
description: كيفية إدارة Microsoft Managed Desktop لأسماء الأجهزة
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: fe29027dab3b3395c14729ee7e04cbe7cebf7261
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63573906"
---
# <a name="device-names"></a>أسماء الأجهزة

يستخدم Microsoft Managed Desktop Windows Autopilot و Azure Active Directory Microsoft Intune.

لكي تعمل هذه الخدمات معا بطريقة سلسة، تحتاج الأجهزة إلى أسماء متناسقة وموحدة. يطبق Microsoft Managed Desktop تنسيق اسم قياسي (من النموذج `MMD-%RAND11`) عند تسجيل الأجهزة. Windows Autopilot هذه الأسماء. لمزيد من المعلومات حول Autopilot، راجع تجربة التشغيل الأولي [مع Autopilot وصفحة حالة التسجيل](../get-started/esp-first-run.md).

## <a name="automated-name-changes"></a>تغييرات الاسم التلقائية

إذا تمت إعادة تسمية جهاز في وقت لاحق، سيعيد Microsoft Managed Desktop تلقائيا تسميته إلى اسم جديد بتنسيق قياسي. تحدث هذه العملية كل أربع ساعات. يحدث تغيير الاسم في المرة التالية التي يقوم فيها المستخدم بإعادة تشغيل الجهاز.

> [!IMPORTANT]
> إذا كانت بيئتك تعتمد على أسماء أجهزة معينة (على سبيل المثال، لدعم تكوين شبكة معين)، يجب التحقق من الخيارات لإزالة هذه التبعية قبل التسجيل في Microsoft Managed Desktop.<br><br>إذا كان عليك الاحتفاظ بتبعية الاسم، يمكنك إرسال طلب عبر مدخل المسؤول لتعطيل وظيفة إعادة التسمية واستخدام تنسيق الاسم المطلوب.[](../working-with-managed-desktop/admin-support.md)
