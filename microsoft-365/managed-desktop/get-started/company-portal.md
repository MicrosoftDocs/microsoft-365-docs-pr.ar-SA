---
title: تثبيت Intune Company Portal على الأجهزة
description: معلومات حول تثبيت تطبيق مدخل الشركة على أجهزة سطح المكتب المدارة من Microsoft
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، Company Portal
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: c7edc974bfd4a4f0d2d9611c80d0996aebc3ddb7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567109"
---
# <a name="install-intune-company-portal-on-devices"></a>تثبيت Intune Company Portal على الأجهزة

يتطلب سطح المكتب المدار من Microsoft أن يقوم مسؤول تكنولوجيا Intune Company Portal بتثبيت التطبيق للمستخدمين باستخدام أجهزة سطح المكتب المدارة من Microsoft. تتضمن المزايا التي تستفيد منها مؤسستك ما يلي:

- يتوفر للمستخدمين مكان واحد لاستعراض التطبيقات المتوفرة وتثبيتها.
- يمكن لمسؤولي تكنولوجيا المعلومات تنظيم التطبيقات حسب الفئات للمستخدمين.  
- تتطلب بعض التطبيقات (مثل Microsoft Project و Microsoft Visio) Company Portal النشر باستخدام Microsoft Managed Desktop.
- يمكن لمسؤولي تكنولوجيا المعلومات تخصيص Company Portal لمنظمتهم. تتضمن التخصيصات تصوير العلامة التجارية، وإضافة جهات اتصال الدعم المحلية، والمزيد. لمزيد من المعلومات، [راجع كيفية تكوين Microsoft Intune Company Portal التطبيق](/intune/company-portal-app).

توثق هذه المقالة عملية نشر Intune Company Portal إلى مستخدمي Microsoft Managed Desktop. تبدو العملية بشكل عام كما يلي:

1. [قم Company Portal من Microsoft Store للأعمال ومزامنة مع Intune](#step-1-purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune).
2. [تعيين Company Portal للمستخدمين](#step-2-assign-company-portal-to-your-users).
3. [تواصل مع المستخدمين بالتغيير.](#step-3-communicate-change-to-your-users)

## <a name="step-1-purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune"></a>الخطوة 1: شراء Company Portal من Microsoft Store للأعمال والمزامنة مع Intune

للحصول على معلومات حول كيفية شراء التطبيقات والمزامنة مع Intune، راجع Microsoft Store للأعمال [](deploy-apps.md#msfb-apps) في *نشر التطبيقات على أجهزة سطح المكتب المدارة من Microsoft*.

توفر هذه المقالة معلومات حول كيفية:

- شراء Company Portal من Microsoft Store للأعمال.
- فرض المزامنة بين Intune Microsoft Store للأعمال.
- تحقق من المزامنة النشطة بين Intune Microsoft Store للأعمال.

## <a name="step-2-assign-company-portal-to-your-users"></a>الخطوة 2: تعيين Company Portal للمستخدمين

بعد تسجيلك في Microsoft Managed Desktop، سنقوم تلقائيا بنشر Company Portal المستأجر وتثبيت التطبيق على أجهزة Microsoft Managed Desktop في مؤسستك.

## <a name="step-3-communicate-change-to-your-users"></a>الخطوة 3: توصيل التغيير إلى المستخدمين

ب دور مسؤول تكنولوجيا المعلومات في مؤسستك، من المهم أن تعلم المستخدمين بكيفية استخدام Company Portal في مؤسستك. يوصي Microsoft Managed Desktop:

- خطوات حول تثبيت التطبيقات من Company Portal. لمزيد من المعلومات، راجع [تثبيت التطبيقات ومشاركتها على جهازك](/intune-user-help/install-apps-cpapp-windows).
- كيفية إرسال طلبات إلى مسؤولي تكنولوجيا المعلومات للتطبيقات غير المتوفرة حاليا. لمزيد من المعلومات، راجع [طلب تطبيق للعمل أو المدرسة](/intune-user-help/install-apps-cpapp-windows#request-an-app-for-work-or-school).  

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>خطوات بدء تشغيل Microsoft Managed Desktop

1. مدخل [مسؤول Access](access-admin-portal.md).
1. [إضافة جهات اتصال المسؤول والتحقق منها في مدخل المسؤول](add-admin-contacts.md).
1. [ضبط الإعدادات بعد التسجيل](conditional-access.md).
1. نشر Intune Company Portal (هذه المقالة).
1. [تعيين التراخيص](assign-licenses.md).
1. [نشر التطبيقات](deploy-apps.md).
1. [تحضير الأجهزة](prepare-devices.md)
1. قم بإعداد [تجربة التشغيل الأولي باستخدام Autopilot وصفحة حالة التسجيل](esp-first-run.md).
1. [تمكين ميزات دعم المستخدم](enable-support.md).
1. [اجهز المستخدمين لاستخدام الأجهزة](get-started-devices.md).
1. [بدء استخدام عنصر تحكم التطبيق](get-started-app-control.md).
