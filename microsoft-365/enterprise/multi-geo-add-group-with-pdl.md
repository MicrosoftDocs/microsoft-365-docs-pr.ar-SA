---
title: إنشاء مجموعة Microsoft 365 موقع بيانات مفضل معين
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: تعرف على كيفية إنشاء مجموعة Microsoft 365 مع موقع بيانات مفضل محدد في بيئة متعددة الجغرافيا.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 7de00ad0d94cda0a47f4981d78ebc07cedab6ada
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570001"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>إنشاء مجموعة Microsoft 365 موقع بيانات مفضل معين

عندما ينشئ المستخدمون في بيئة متعددة الجغرافيا مجموعة Microsoft 365، يتم تعيين موقع البيانات المفضل للمجموعة (PDL) تلقائيا إلى موقع المستخدم. يمكن للمسؤولين العامين SharePoint Exchange إنشاء مجموعات في أي منطقة تحددها. 

إذا كنت بحاجة إلى إنشاء مجموعة باستخدام PDL معين، يمكنك القيام بذلك باستخدام <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint مركز إدارة Exchange Online New-UnifiedGroup</a> Microsoft PowerShell cmdlet. عند القيام بذلك، سيتم توفير كل من علبة بريد المجموعة SharePoint موقع المجموعة المقترن بالمجموعة في PDL المحدد.

لإنشاء مجموعة Microsoft 365 باستخدام PDL الذي تحدده، انتقل إلى مركز إدارة SharePoint في الموقع الجغرافي <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank"></a> حيث تريد إنشاء موقع المجموعة.

على سبيل المثال:

إذا كنت تريد إنشاء موقع مجموعة في موقعك في أستراليا، يمكنك الانتقال إلى https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. حدد **+ إنشاء**.
2. اتبع العملية لإنشاء موقع مجموعة.

سيتم توفير موقع المجموعة في الموقع الجغرافي المناظر لمركز إدارة SharePoint الذي بدأت منه طلب إنشاء الموقع. 

استخدام Exchange PowerShell 

الاتصال إلى Exchange Online PowerShell وتمرر المعلمة *-MailBoxRegion* باستخدام رمز الموقع الجغرافي.

على سبيل المثال: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![لقطة شاشة New-UnifiedGroup PowerShell cmdlet مع بناء الجملة.](../media/multi-geo-new-group-with-pdl-powershell.png)

لاحظ أن SharePoint موقع المجموعة عند الطلب. سيتم توفير الموقع في المرة الأولى التي يحاول فيها مالك المجموعة أو العضو الوصول إليه.

## <a name="geo-location-codes"></a>رموز الموقع الجغرافي

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>المواضيع ذات الصلة

[الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[إنشاء مجموعات ذات موقع بيانات مفضل معين باستخدام Graph API](/graph/api/group-post-groups)
