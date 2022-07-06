---
title: حماية وصول المستخدم والجهاز
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 4/17/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: تعرف على كيفية حماية وصول المستخدم والجهاز إلى بيانات وخدمات Microsoft 365 والحماية من فقدان البيانات.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f8b6b266d037e8bbc185643e530bf7a2f6919038
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623685"
---
# <a name="protect-user-and-device-access"></a>حماية وصول المستخدم والجهاز

تعد حماية الوصول إلى بيانات وخدمات Microsoft 365 أمرا بالغ الأهمية للدفاع ضد الهجمات الإلكترونية والحماية من فقدان البيانات. يمكن تطبيق نفس الحماية على تطبيقات SaaS الأخرى في بيئتك وحتى على التطبيقات المحلية المنشورة باستخدام وكيل تطبيق Azure Active Directory.
  
## <a name="step-1-review-recommendations"></a>الخطوة 1: مراجعة التوصيات

القدرات الموصى بها لحماية الهويات والأجهزة التي تصل إلى Office 365 وخدمات SaaS الأخرى والتطبيقات المحلية المنشورة مع وكيل تطبيق Azure AD.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) |  [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657) |  [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>الخطوة 2: حماية حسابات المسؤولين والوصول

تتضمن الحسابات الإدارية التي تستخدمها لإدارة بيئة Microsoft 365 امتيازات مرتفعة. هذه أهداف قيمة للمتسللين والهجمات الإلكترونية.

ابدأ باستخدام حسابات المسؤول للإدارة فقط. يجب أن يكون لدى المسؤولين حساب مستخدم منفصل للاستخدام العادي وغير الإداري واستخدام حسابهم الإداري فقط عند الضرورة لإكمال مهمة مقترنة بوظيفة الوظيفة الخاصة بهم.

حماية حسابات المسؤول من خلال المصادقة متعددة العوامل والوصول المشروط. لمزيد من المعلومات، راجع [حماية حسابات المسؤولين](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

بعد ذلك، قم بتكوين Microsoft Purview Privileged Access Management. تسمح إدارة الوصول المتميز بالتحكم في الوصول متعدد المستويات لمهام المسؤول المتميزة في Office 365. يمكن أن يساعد في حماية مؤسستك من الخروقات التي قد تستخدم حسابات المسؤول المتميزة الحالية مع الوصول الدائم إلى البيانات الحساسة أو الوصول إلى إعدادات التكوين الهامة.

- [نظرة عامة على إدارة الوصول المتميز](privileged-access-management.md)
- [تكوين إدارة الوصول المتميز](privileged-access-management-configuration.md)

توصية أخرى هي استخدام محطات العمل التي تم تكوينها بشكل خاص للعمل الإداري. هذه هي الأجهزة المخصصة التي تستخدم فقط للمهام الإدارية. راجع [تأمين الوصول المتميز](/windows-server/identity/securing-privileged-access/securing-privileged-access).

وأخيرا، يمكنك التخفيف من تأثير الافتقار غير المقصود إلى الوصول الإداري عن طريق إنشاء حسابين أو أكثر من حسابات الوصول في حالات الطوارئ في المستأجر الخاص بك. راجع [إدارة حسابات الوصول في حالات الطوارئ في Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>الخطوة 3: تكوين نهج الوصول إلى الهوية والجهاز الموصى بها

تعد المصادقة متعددة العوامل (MFA) ونهج الوصول المشروط أدوات قوية للتخفيف من الحسابات المخترقة والوصول غير المصرح به. نوصي بتنفيذ مجموعة من النهج التي تم اختبارها معا. لمزيد من المعلومات، بما في ذلك خطوات النشر، راجع [تكوينات الهوية والوصول إلى الجهاز](../security/office-365-security/microsoft-365-policies-configurations.md).

 تنفذ هذه النهج القدرات التالية:

- المصادقة متعددة العوامل
- الوصول المشروط
- حماية تطبيق Intune (حماية التطبيقات والبيانات للأجهزة)
- توافق جهاز Intune
- حماية الهوية في Azure AD

يتطلب تنفيذ توافق جهاز Intune تسجيل الجهاز. تسمح لك إدارة الأجهزة بالتأكد من أنها سليمة ومتوافقة قبل السماح لها بالوصول إلى الموارد في بيئتك. راجع [تسجيل الأجهزة للإدارة في Intune](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>الخطوة 4: تكوين نهج الوصول إلى أجهزة SharePoint

توصي Microsoft بحماية المحتوى في مواقع SharePoint باستخدام محتوى حساس ومنظم للغاية باستخدام عناصر التحكم في الوصول إلى الجهاز. لمزيد من المعلومات، راجع [توصيات النهج لتأمين مواقع SharePoint وملفاته](../security/office-365-security/sharepoint-file-access-policies.md).
