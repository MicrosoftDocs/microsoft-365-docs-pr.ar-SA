---
title: أساليب تسجيل الجهاز في Microsoft Managed Desktop
description: معلومات حول أساليب تسجيل الجهاز في Microsoft Managed Desktop
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 7d0cabc0a9d11d337e5adabde568bd2a56ceca86
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704663"
---
# <a name="device-registration-methods"></a>أساليب تسجيل الجهاز

قبل أن تتمكن Microsoft من إدارة أجهزتك في Microsoft Managed Desktop، يجب أن يكون لديك أجهزة مسجلة في الخدمة.

## <a name="registration-process"></a>عملية التسجيل

يتم تشغيل Microsoft Managed Desktop بواسطة Windows Autopilot لسير عمل تسجيل الجهاز. يتطلب تسجيل الجهاز بنجاح عملية من خطوتين:

1. يتم التقاط هوية الجهاز الفريدة، المعروفة ب"هاشش الأجهزة"، وتحميلها إلى خدمة Autopilot.
1. يقترن الجهاز بم ID مستأجر Azure Active Directory.

وبشكل مثالي، يتم تنفيذ كلتا خطوتين من قبل OEM أو البائع أو الموزع حيث تم شراء الأجهزة. تستخدم الشركة الأصلية أو موفر الأجهزة الآخر عملية تخويل التسجيل لتنفيذ تسجيل الجهاز بالنيابة عنك.

## <a name="registration-methods"></a>أساليب التسجيل

يمكن أيضا إجراء التسجيل داخل مؤسستك من خلال جمع هوية الأجهزة من أجهزة جديدة أو موجودة وتحميلها يدويا. فيما يلي أساليب تسجيل الأجهزة التي يدعمها Microsoft Managed Desktop:

- تسجيل الشركة الأصلية
    - [استخدام مدخل الشريك](partner-registration.md#register-devices-using-the-partner-center)
    - [استخدام واجهات برمجة التطبيقات (برمجة التطبيقات) في OEM](partner-registration.md#register-devices-by-using-the-oem-api)
- [التسجيل اليدوي](manual-registration.md)
- [التسجيل اليدوي للأجهزة الموجودة](manual-registration-existing-devices.md)

## <a name="recommended-resources"></a>الموارد الموصى بها

- [نظرة عامة Windows Autopilot](/mem/autopilot/windows-autopilot)
- [Windows حول تسجيل Autopilot](/mem/autopilot/registration-overview)

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
1. [بدء استخدام عنصر تحكم التطبيق](get-started-app-control.md).
