---
title: إزالة الأجهزة
description: إزالة الأجهزة من إدارة سطح المكتب المدار من Microsoft
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
ms.openlocfilehash: 82e14fbd2bc991505c84d219c0624f52791376d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575492"
---
# <a name="remove-devices"></a>إزالة الأجهزة

يمكنك إزالة الأجهزة من إدارة سطح المكتب المدار من Microsoft باستخدام مدخل المسؤول. هذا الإجراء دائم، ولكن يمكنك تسجيله في Microsoft Managed Desktop مرة أخرى باتباع [خطوات التسجيل اليدوية](../get-started/manual-registration.md).

عند إزالة جهاز، يحدث كل ما يلي:

- نقوم بإزالة الجهاز من Autopilot.
- نقوم بإزالة الجهاز من كل مجموعات الأجهزة "Modern Workplace".
- نقوم بإزالة الجهاز من شفرة **الأجهزة** في مدخل المسؤول.

عند إزالة جهاز، يمكنك أيضا إزالته من Azure Active Directory (Azure AD) Microsoft Intune.
  
> [!CAUTION]
> إن إزالة العناصر المرتبطة بجهاز من Azure AD Microsoft Intune دائم. إذا قمت بإزالة العناصر، فلن تتمكن من عرض الأجهزة أو إدارتها من مدخلي Intune و Azure. لن تتمكن الأجهزة من الوصول إلى موارد الشركة الخاصة بها. قد يتم حذف بيانات الشركة منها إذا حاولت الأجهزة تسجيل الدخول بعد حذفها.

**لإزالة جهاز:**

1. في [إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/)، حدد **الأجهزة** في جزء التنقل الأيسر.
2. في المقطع **Microsoft Managed Desktop** ، حدد **الأجهزة**.
3. في مساحة **عمل أجهزة سطح المكتب المدارة من Microsoft**، حدد الأجهزة التي تريد حذفها.
4. حدد **إجراءات الجهاز**، ثم حدد **حذف الجهاز** الذي يفتح رسالة مطيرة لإزالة الأجهزة.
5. في النشرة، راجع الأجهزة المحددة ثم حدد **إزالة الأجهزة**. إذا كنت تريد أيضا إزالة كائنات Azure AD و Intune في الوقت نفسه، فحدد خانة الاختيار. قد يستغرق إكمال إزالة الجهاز بضع دقائق.

> [!NOTE]
> لا يمكنك إزالة الأجهزة التي في حالة **تسجيل** معلقة.
