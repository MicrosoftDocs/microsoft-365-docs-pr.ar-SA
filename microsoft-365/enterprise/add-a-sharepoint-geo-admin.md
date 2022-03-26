---
title: إضافة مسؤول جغرافي أو إزالته
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: هل تحتاج إلى تكوين مسؤولي منفصلين لكل موقع جغرافي؟ تعرف على كيفية إضافة مسؤول جغرافي أو إزالته Microsoft 365 Multi-Geo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e661e42759fe0b035bfe97c33165f78316973403
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572882"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a>إضافة مسؤول جغرافي أو إزالته في Microsoft 365 الجغرافيا المتعددة

يمكنك تكوين مسؤولي منفصلين لكل موقع جغرافي لديك في المستأجر. سيكون لهؤلاء المسؤولين حق الوصول إلى SharePoint عبر الإنترنت OneDrive الإعدادات الخاصة بموقعهم الجغرافي.

يتم إدارة بعض الخدمات، مثل مخزن المصطلحات، من الموقع المركزي ونسخها في مواقع الأقمار الصناعية. يمكن لمسؤول الموقع المركزي الوصول إلى هذه المواقع، بينما لا يمكن للمسؤولين الجغرافيين لمواقع الأقمار الصناعية الوصول إليها.

لا يزال المسؤولون SharePoint عبر الإنترنت لديهم حق الوصول إلى الإعدادات في الموقع المركزي وجميع مواقع الأقمار الصناعية.

## <a name="configuring-geo-administrators"></a>تكوين مسؤولي الجغرافيا

يتطلب تكوين المسؤولين الجغرافيين SharePoint PowerShell النمطية عبر الإنترنت.

استخدم [الاتصال SPOService](/powershell/module/sharepoint-online/Connect-SPOService) للاتصال بمركز إدارة الموقع الجغرافي حيث تريد إضافة المسؤول الجغرافي. (على سبيل المثال، Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

لعرض المسؤولين الجغرافيين  الموجودين لموقع ما، يمكنك تشغيل `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>إضافة مستخدم كمسؤول جغرافي

لإضافة مستخدم كمسؤول جغرافي، قم بتشغيل `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

لإزالة مستخدم كمسؤول جغرافي لموقع، قم بتشغيل  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>إضافة مجموعة كمسؤول جغرافي

يمكنك إضافة مجموعة أمان أو مجموعة أمان ممكن للبريد كمسؤول جغرافي. (مجموعات التوزيع ومجموعات Microsoft 365 غير معتمدة.)

لإضافة مجموعة كمسؤول جغرافي، قم بتشغيل `Add-SPOGeoAdministrator -GroupAlias <alias>`

لإزالة مجموعة كمسؤول جغرافي، قم بتشغيل `Remove-SPOGeoAdministrator -GroupAlias <alias>`

تجدر الإشارة إلى أنه لا تملك كل مجموعات الأمان اسما مستعارا للمجموعة. إذا كنت تريد إضافة مجموعة أمان لا تتضمن اسما مستعارا، ف قم بتشغيل [Get-MsolGroup](/powershell/module/msonline/get-msolgroup) لاسترداد قائمة بالمجموعات، واعثر على ObjectID الخاص بالمجموعة الأمنية، ثم قم بتشغيل:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

لإزالة مجموعة باستخدام ObjectID، قم بتشغيل `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="related-topics"></a>المواضيع ذات الصلة

[Add-SPOGeoAdministrator](/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](/powershell/module/sharepoint-online/remove-spogeoadministrator)

[تعيين اسم مستعار (MailNickName) لمجموعة أمان](/powershell/module/azuread/set-azureadgroup)