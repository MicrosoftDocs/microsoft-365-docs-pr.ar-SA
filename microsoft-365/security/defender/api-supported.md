---
title: واجهات Microsoft 365 Defender برمجة التطبيقات المعتمدة
description: واجهات Microsoft 365 Defender برمجة التطبيقات المعتمدة
keywords: Microsoft 365 Defender، واجهات برمجة التطبيقات، api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 1785186f778c489cb4a254fe39cc41921a4de86e
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63583012"
---
# <a name="supported-microsoft-365-defender-apis"></a>واجهات Microsoft 365 Defender برمجة التطبيقات المعتمدة 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

## <a name="list-of-available-apis"></a>قائمة واجهات برمجة التطبيقات المتوفرة

مقالة | الوصف
-|-
[API للصيد المتقدم](api-advanced-hunting.md) | تشغيل استعلامات البحث المتقدم.
[واجهات برمجة التطبيقات للحوادث](api-incident.md) | سرد الأحداث وتحديثها، إلى جانب المهام العملية الأخرى.
[برمجة تطبيقات النقل المتدفق](streaming-api.md) | قم بشحن الأحداث والتنبيهات في الوقت الحقيقي عند حدوثها في دفق بيانات واحد.

### <a name="endpoint-uris"></a>URIs لنقطة النهاية

إن URI الأساسي لكل من واجهات برمجة التطبيقات الرئيسية هو: https://api.security.microsoft.com. للحصول على أداء أفضل، استخدم خادما أقرب إلى الموقع الجغرافي:

- الولايات المتحدة: api-us.security.microsoft.com
- أوروبا: api-eu.security.microsoft.com
- المملكة المتحدة: api-uk.security.microsoft.com

يمكن الحصول على الرموز المميزة من خلال الوصول إلى https://api.security.microsoft.com.

تستخدم كل واجهات برمجة التطبيقات على `/api` طول المسار بروتوكول [OData](/odata/overview) ؛ على سبيل المثال، https://api.security.microsoft.com/api/incidents.

## <a name="related-articles"></a>المقالات ذات الصلة

- [Microsoft 365 Defender نظرة عامة على واجهات برمجة التطبيقات](api-overview.md)
- [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)
- [برمجة تطبيقات النقل المتدفق](../defender-endpoint/raw-data-export.md)
- [التعرف على حدود API والترخيص](api-terms.md)
- [فهم رموز الخطأ](api-error-codes.md)
