---
title: SharePoint النسبية للتخزين في بيئات متعددة الجغرافيا
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
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: تعرف على SharePoint النسبية للتخزين في بيئات متعددة الجغرافيا وكيفية إدارة الحصص النسبية من قبل مسؤول SharePoint Online.
ms.openlocfilehash: d1e47c206f1353093ba8bebf9db03ab7142d6da9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572886"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>SharePoint النسبية للتخزين في بيئات متعددة الجغرافيا

بشكل افتراضي، تشارك كل المواقع الجغرافية لبيئة متعددة الجغرافيا الحصة النسبية المتوفرة للتخزين للمستأجر.

باستخدام SharePoint الحصة النسبية للتخزين الجغرافي، يمكنك إدارة الحصة النسبية للتخزين لكل موقع جغرافي. عند تخصيص الحصة النسبية للتخزين لموقع جغرافي، تصبح الحد الأقصى لمقدار مساحة التخزين المتوفرة لهذا الموقع الجغرافي، وتخصم من الحصة النسبية المتوفرة لمساحة التخزين للمستأجر. بعد ذلك، يتم مشاركة الحصة النسبية المتبقية المتوفرة لمساحة التخزين للمستأجر عبر المواقع الجغرافية المكونة التي لم يتم تخصيص حصة تخزينية محددة لها.

يمكن SharePoint حصة التخزين النسبية لأي موقع جغرافي من قبل مسؤول SharePoint عبر الإنترنت من خلال الاتصال بموقع مركزي. يمكن لمسؤولي الموقع الجغرافي لمواقع الأقمار الصناعية عرض الحصة النسبية للتخزين ولكن لا يمكنهم تخصيصها.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>تكوين الحصة النسبية للتخزين لموقع جغرافي

استخدم Microsoft Office SharePoint Online [النمطية](https://www.microsoft.com/download/details.aspx?id=35588) واتصل بموقع مركزي لتخصيص الحصة النسبية للتخزين لموقع جغرافي.

لتخصيص الحصة النسبية للتخزين لموقع، قم بتشغيل cmdlet:

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>
```

لعرض الحصة النسبية للتخزين للموقع الجغرافي الحالي، يمكنك تشغيل:

```powershell
Get-SPOGeoStorageQuota
```

![لقطة شاشة من نافذة PowerShell تظهر Get-SPOGeoStorageQuota cmdlet.](../media/multi-geo-storage-quota.png)

لعرض الحصة النسبية للتخزين لكل المواقع الجغرافية، يمكنك تشغيل:

```powershell
Get-SPOGeoStorageQuota -AllLocations
```

لإزالة حصة التخزين النسبية المخصصة لموقع جغرافي، قم بتعيين `StorageQuota value = 0`:

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0
```
