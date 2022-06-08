---
title: إنشاء مجموعة Microsoft 365 مع موقع بيانات مفضل محدد
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
description: تعرف على كيفية إنشاء مجموعة Microsoft 365 مع موقع بيانات مفضل محدد في بيئة متعددة المناطق الجغرافية.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: ff9b6ae6949ab1e6af1ee102abfcf2cb132fed9f
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940701"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>إنشاء مجموعة Microsoft 365 مع موقع بيانات مفضل محدد

عندما ينشئ المستخدمون في بيئة متعددة المناطق الجغرافية مجموعة Microsoft 365، يتم تعيين موقع البيانات المفضل للمجموعة (PDL) تلقائيا إلى موقع المستخدم. يمكن لمسؤولي Global وSharePoint وExchange إنشاء مجموعات في أي منطقة يختارونها. 

إذا كنت بحاجة إلى إنشاء مجموعة باستخدام PDL معين، يمكنك القيام بذلك باستخدام <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">من مركز إدارة SharePoint</a> أو من خلال Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet. عند القيام بذلك، سيتم توفير كل من علبة بريد المجموعة وموقع SharePoint المقترن بالمجموعة في PDL المحدد.

لإنشاء مجموعة Microsoft 365 باستخدام PDL الذي تحدده، انتقل إلى <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">مركز إدارة SharePoint</a> في الموقع الجغرافي حيث تريد إنشاء موقع المجموعة.

على سبيل المثال:

إذا كنت تريد إنشاء موقع مجموعة في موقع أستراليا الخاص بك، يمكنك الانتقال إلى `https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement`

1. حدد **+ إنشاء**.
2. اتبع العملية لإنشاء موقع مجموعة.

سيتم توفير موقع المجموعة في الموقع الجغرافي المطابق لمركز إدارة SharePoint الذي بدأت منه طلب إنشاء الموقع. 

استخدام Exchange PowerShell 

اتصل ب Exchange Online PowerShell ومرر المعلمة *-MailBoxRegion* باستخدام رمز الموقع الجغرافي.

على سبيل المثال: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![لقطة شاشة New-UnifiedGroup PowerShell cmdlet مع بناء الجملة.](../media/multi-geo-new-group-with-pdl-powershell.png)

> [!Note]
> يتم توفير موقع مجموعة SharePoint عند الطلب. سيتم توفير الموقع في المرة الأولى التي يحاول فيها مالك المجموعة أو العضو الوصول إليه.

## <a name="geo-location-codes"></a>رموز الموقع الجغرافي

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>المواضيع ذات الصلة

[الاتصال ب Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[إنشاء مجموعات مع موقع بيانات مفضل محدد باستخدام Graph API](/graph/api/group-post-groups)
