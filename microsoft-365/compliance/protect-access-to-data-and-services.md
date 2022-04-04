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
description: تعرف على كيفية حماية وصول المستخدم والجهاز إلى Microsoft 365 البيانات والخدمات والدفاع ضد فقدان البيانات.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 48f483422fda158c02429aec642f60e05b8c933a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679577"
---
# <a name="protect-user-and-device-access"></a>حماية وصول المستخدم والجهاز

إن حماية الوصول إلى Microsoft 365 والخدمات أمر ضروري للحماية من الهجمات الإلكترونية والحماية من فقدان البيانات. يمكن تطبيق نفس الحماية على تطبيقات SaaS الأخرى في بيئتك وحتى على التطبيقات المحلية المنشورة مع وكيل تطبيق Azure Active Directory.
  
## <a name="step-1-review-recommendations"></a>الخطوة 1: مراجعة التوصيات

الإمكانات الموصى بها لحماية الهويات والأجهزة التي Office 365 وخدمات SaaS الأخرى والتطبيقات المحلية المنشورة مع وكيل تطبيق Azure AD.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) |  [](https://go.microsoft.com/fwlink/p/?linkid=841657) |  Visio [لغات أخرى](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>الخطوة 2: حماية حسابات المسؤولين والوصول
تتضمن الحسابات الإدارية التي تستخدمها لإدارة بيئة Microsoft 365 امتيازات مرتفعة. هذه أهداف قيمة للمتسللين والمتسللين عبر الإنترنت. 

ابدأ باستخدام حسابات المسؤولين للإدارة فقط. يجب أن يكون لدى المسؤولين حساب مستخدم منفصل للاستخدام العادي وغير الإداري واستخدام حسابهم الإداري فقط عند الضرورة لإكمال مهمة مقترنة بوظيفتهم.

يمكنك حماية حسابات المسؤولين باستخدام المصادقة متعددة العوامل والوصول الشرطي. لمزيد من المعلومات، راجع [حماية حسابات المسؤولين](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

بعد ذلك، قم بتكوين إدارة الوصول المتميزة في Office 365. تسمح إدارة الوصول المتميز بالتحكم في الوصول بشكل كبير على مهام الإدارة المتميزة في Office 365. يمكن أن يساعد ذلك في حماية مؤسستك من الخروقات التي قد تستخدم حسابات المسؤولين المتميزين الموجودة مع إمكانية الوصول الدائم إلى البيانات الحساسة أو الوصول إلى إعدادات التكوين الهامة.

- [نظرة عامة حول إدارة الوصول المتميزة](privileged-access-management-overview.md)
- [تكوين إدارة الوصول المتميزة](privileged-access-management-configuration.md)

هناك توصية أخرى هي استخدام محطات العمل التي تم تكوينها خصيصا للعمل الإداري. هذه الأجهزة مخصصة يتم استخدامها فقط للمهام الإدارية. راجع [تأمين الوصول المميز](/windows-server/identity/securing-privileged-access/securing-privileged-access).

وأخيرا، يمكنك تقليل تأثير عدم الوصول الإداري عن غير قصد من خلال إنشاء حسابين أو أكثر للوصول إلى خدمات الطوارئ في المستأجر. راجع [إدارة حسابات الوصول إلى الطوارئ في Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>الخطوة 3: تكوين سياسات الوصول إلى الأجهزة والهوية الموصى بها
إن مصادقة العوامل المتعددة ونهج الوصول الشرطي هي أدوات فعالة لتخفيف المخاطر ضد الحسابات المساسة والوصول غير المصرح به. نوصي بتنفيذ مجموعة من السياسات التي تم اختبارها معا. لمزيد من المعلومات، بما في ذلك خطوات النشر، راجع [تكوينات الوصول إلى الهوية والجهاز](../security/office-365-security/microsoft-365-policies-configurations.md).

 تنفذ هذه السياسات القدرات التالية:
- المصادقة متعددة العوامل
- الوصول الشرطي
- حماية تطبيق Intune (حماية التطبيقات والبيانات للأجهزة)
- توافق جهاز Intune
- حماية هوية Azure AD

يتطلب تنفيذ توافق أجهزة Intune تسجيل الجهاز. تسمح لك إدارة الأجهزة بالتأكد من أنها سليمة ومتوافقة قبل السماح لها بالوصول إلى الموارد في بيئتك. راجع [تسجيل الأجهزة للإدارة في Intune](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>الخطوة 4: تكوين SharePoint الوصول إلى الأجهزة

توصي Microsoft بحماية المحتوى في SharePoint المواقع ذات المحتوى الحساس والمنظم إلى حد كبير باستخدام عناصر التحكم بالوصول إلى الجهاز. لمزيد من المعلومات، راجع توصيات النهج [لتأمين SharePoint والملفات](../security/office-365-security/sharepoint-file-access-policies.md).



