---
title: نشر التطبيقات على الأجهزة
description: معلومات حول إضافة التطبيقات ونشرها على أجهزة سطح المكتب المدارة من Microsoft.
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق، التطبيقات، تطبيقات خط العمل، تطبيقات LOB
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: d0c8dbb71a56701cb5ca75aadb1a5bcc7290844f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566896"
---
# <a name="deploy-apps-to-devices"></a>نشر التطبيقات على الأجهزة

يتضمن جزء من الضم إلى Microsoft Managed Desktop إضافة التطبيقات ونشرها على أجهزة المستخدم. بمجرد استخدام مدخل Microsoft Managed Desktop، يمكنك إضافة تطبيقاتك ونشرها.

تبدو العملية بشكل عام كما يلي:

1. [إضافة تطبيقات إلى مدخل Microsoft Managed Desktop](#1): يمكن أن تكون هذه التطبيقات تطبيقات خط العمل (LOB) موجودة، أو تطبيقات من Microsoft Store للأعمال قمت بمزامنتها مع Intune.
2. [إنشاء مجموعات Azure Active Directory (AD)](#2) لواجبات التطبيق: سوف تستخدم هذه المجموعات لإدارة تعيين التطبيق.
3. [تعيين التطبيقات للمستخدمين](#3).

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>الخطوة 1: إضافة تطبيقات إلى مدخل Microsoft Managed Desktop

يمكنك إضافة [Win32 أو Windows المستندة إلى MSI](#lob-apps)، أو Microsoft Store للأعمال تطبيقات إلى Microsoft Managed [](#msfb-apps) Desktop، ثم نشرها على أجهزة Microsoft Managed Desktop.

<span id="lob-apps">

### <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>تطبيقات Win32 أو Windows المستندة إلى MSI إلى Microsoft Managed Desktop

يمكنك إضافة تطبيقات خط العمل (LOB) إلى مدخل Microsoft Managed Desktop. للحصول على معلومات المتطلبات للتطبيقات المثبتة على أجهزة سطح المكتب المدارة من Microsoft، راجع [متطلبات تطبيق Microsoft Managed Desktop](../service-description/mmd-app-requirements.md).

في هذا الإجراء، ستحدد نوع التطبيق الذي تريد إضافته، ثم قم بتكوين مصدر التطبيق وتحميله.

**لإضافة تطبيق LOB أو تطبيق Windows إلى مدخل سطح المكتب المدار من Microsoft:**

يمكنك تسجيل الدخول إلى مدخل Microsoft Managed Desktop، أو تسجيل الدخول إلى Intune ثم البحث عن Microsoft Managed Desktop. سنعرض تسجيل الدخول إلى مدخل Microsoft Managed Desktop أدناه:

1. سجل الدخول إلى [مدخل مسؤول سطح المكتب المدار من Microsoft](https://aka.ms/mmdportal).
2. ضمن **المخزون**، حدد **التطبيقات**.
3. في المقطع حمل عمل التطبيقات، حدد **إضافة**.
4. في **إضافة تطبيق،** حدد **تطبيق خط** العمل أو تطبيق Windows **(Win32)**.
    - إذا قمت بتحديد تطبيق خط العمل، فحدد إضافة تطبيق خط [](/intune/lob-apps-windows) Windows إلى Microsoft Intune للحصول على تعليمات حول إضافة تطبيقات خط العمل وتكوينها.
    - إذا قمت بتحديد Windows **التطبيق (Win32)،** فحدد إدارة تطبيق [Win32](/intune/apps-win32-app-management) للحصول على تعليمات حول إضافة تطبيقات Windows وتكوينها.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>Microsoft Store للأعمال التطبيقات

إذا لم تقم بالتوقيع باستخدام Microsoft Store للأعمال، يمكنك التسجيل عند التسوق للحصول على التطبيقات. بعد الحصول على تطبيقاتك، يمكنك مزامنتها مع Microsoft Managed Desktop.

**لشراء تطبيقات من Microsoft Store للأعمال:**

1. سجل [الدخول Microsoft Store للأعمال باستخدام](https://businessstore.microsoft.com) Microsoft Store للأعمال المسؤول الخاص بك.
2. حدد **التسوق لمجموعتي**.
3. استخدم البحث للعثور على التطبيق الذي تريده، وحدد التطبيق.
4. في تفاصيل المنتج، حدد **الحصول على التطبيق**.
Microsoft Store التطبيق إلى **منتجاتك** لمنظمتك.

**للتحقق من أن المزامنة بين Intune Microsoft Store للأعمال نشطة:**

1. سجل [الدخول Microsoft Store للأعمال باستخدام](https://businessstore.microsoft.com) Microsoft Store للأعمال المسؤول الخاص بك.
2. حدد **إدارة**.
3. حدد **الإعدادات** ثم حدد **توزيع**.
4. ضمن **أدوات الإدارة**، تحقق من إدراج Intune ومن أن الحالة **نشطة**.  

**فرض مزامنة بين Intune Microsoft Store للأعمال:**

1. سجل الدخول إلى إدارة نقاط النهاية من Microsoft [الإدارة](https://go.microsoft.com/fwlink/?linkid=2109431).
2. حدد **إدارة المستأجر** ، ثم **الموصلات والرموز** المميزة **، ثم Microsoft Store للأعمال**.
3. حدد **تمكين لتمكين** Microsoft Store للأعمال تتيح لك الوصول إلى التطبيقات التي تم شراؤها بشكل **مجلد باستخدام Intune.**
4. حدد اللغة المفضلة لديك، **ثم حدد مزامنة** للحصول على التطبيقات التي اشتريتها من Microsoft Store Intune.

<span id="2" />

## <a name="step-2-create-azure-ad-groups"></a>الخطوة 2: إنشاء مجموعات Azure AD

إنشاء ثلاث مجموعات Azure AD لكل تطبيق. يوضح هذا الجدول المجموعات التي ستحتاج إليها (متوفر ومطلوب و إلغاء تثبيت).

نوع تعيين التطبيق | استخدام المجموعة | مثال لاسم Azure AD |
--- | --- | --- |
متاح |  سيكون التطبيق متوفرا من Company Portal أو موقع ويب. | MMD – *اسم التطبيق* – متوفر |
مطلوب |  يتم تثبيت التطبيق على الأجهزة في المجموعات المحددة. | MMD – *اسم التطبيق* – مطلوب |
إلغاء التثبيت |  يتم إلغاء تثبيت التطبيق من الأجهزة في المجموعات المحددة. | MMD – *اسم التطبيق* – إلغاء التثبيت |

أضف المستخدمين إلى هذه المجموعات إلى أي من:

- جعل التطبيق متوفرا
- تثبيت التطبيق، أو
- قم بإزالة التطبيق من جهاز سطح المكتب المدار من Microsoft.

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>الخطوة 3: تعيين التطبيقات للمستخدمين

**لتعيين التطبيق للمستخدمين:**

1. سجل الدخول إلى [مدخل مسؤول سطح المكتب المدار من Microsoft](https://aka.ms/mmdportal).
2. في الجزء سطح المكتب المدار، حدد **التطبيقات**.
3. في قسم حمل عمل التطبيقات، حدد التطبيق الذي تريد تعيين المستخدمين له، وحدد **تعيين مجموعات المستخدمين**.
4. بالنسبة للتطبيق المحدد، حدد نوع واجب (متوفر، مطلوب، إلغاء تثبيت) ثم قم بتعيين المجموعة المناسبة.
5. في الجزء تعيين تطبيقات، حدد **موافق**.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>خطوات بدء تشغيل Microsoft Managed Desktop

1. مدخل [مسؤول Access](access-admin-portal.md).
1. [إضافة جهات اتصال المسؤول والتحقق منها في مدخل المسؤول](add-admin-contacts.md).
1. [ضبط الإعدادات بعد التسجيل](conditional-access.md).
1. نشر [Intune Company Portal.](company-portal.md)
1. [تعيين التراخيص](assign-licenses.md).
1. نشر التطبيقات (هذه المقالة).
1. [تحضير الأجهزة](prepare-devices.md).
1. قم بإعداد [تجربة التشغيل الأولي باستخدام Autopilot وصفحة حالة التسجيل](esp-first-run.md).
1. [تمكين ميزات دعم المستخدم](enable-support.md).
1. [اجهز المستخدمين لاستخدام الأجهزة](get-started-devices.md).
1. [بدء استخدام عنصر تحكم التطبيق](get-started-app-control.md).

<!--# Preparing apps for Microsoft Managed Desktop

This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.

-->
