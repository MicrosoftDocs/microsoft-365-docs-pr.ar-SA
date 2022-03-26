---
title: تقييد SharePoint موقع إلى موقع جغرافي
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: في هذه المقالة، تعرف على كيفية تقييد SharePoint موقع جغرافي معين في بيئة متعددة الجغرافيا.
ms.openlocfilehash: 06401658afe9f6a26b1280f5931ba6b3ba761742
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569969"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>تقييد SharePoint موقع إلى موقع جغرافي

في بعض الحالات، قد تختار فرض موقع ومحتوى ملفه ليبقى في الموقع الجغرافي حيث تم إنشاء الموقع، إما عن طريق منع نقل الموقع أو منع التخزين المؤقت لمحتوى ملف الموقع في موقع جغرافي آخر.

يمكنك القيام بذلك باستخدام [الأمر cmdlet Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) مع المعلمة **RestrictedToGeo** . هذه المعلمة لديها قيمة افتراضية من NULL، ولكن يمكنك تغييرها إلى أحد الخيارات التالية:

|تقييد|الوصف|
|:----------|:----------|
|NoRestriction|يمكن نقل الموقع إلى موقع جغرافي آخر.|
|BlockMoveOnly|لا يمكن نقل الموقع إلى موقع جغرافي آخر، ولكن يمكن تخزين محتوى الموقع مؤقتا في مواقع جغرافية أخرى.|
|BlockFull|لا يمكن نقل الموقع إلى موقع جغرافي آخر، ولا يتم تخزين محتوى الملف الكامل مؤقتا في مواقع جغرافية أخرى. لا يزال يمكن تخزين عنوان الملفات (التي تم الحصول عليها من المحتوى) واسم الملف وخصائص أخرى للملف مؤقتا في مواقع جغرافية أخرى.<br>قد يستمر تخزين المحتوى المخزن في الموقع قبل تكوينه إلى BlockFull، مؤقتا في مواقع جغرافية أخرى.|

استخدم بناء الجملة التالي:

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

على سبيل المثال:

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`