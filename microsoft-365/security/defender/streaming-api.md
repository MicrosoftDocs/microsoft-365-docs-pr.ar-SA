---
title: دفق Microsoft 365 Defender الأحداث
description: تعرف على كيفية تكوين Microsoft 365 Defender لبث أحداث "الصيد المتقدم" إلى "مراكز الأحداث" أو حساب تخزين Azure
keywords: تصدير البيانات الخام، دفق API، API، مراكز الأحداث، تخزين Azure، حساب التخزين، البحث المتقدم، مشاركة البيانات الخام
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c6c3cedffb1b827d441d37cc8beb53b20f3521f2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63578252"
---
# <a name="streaming-api"></a>برمجة تطبيقات النقل المتدفق

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>دفق أحداث "البحث المتقدم" إلى "مراكز الأحداث" و/أو حساب تخزين Azure.

Microsoft 365 Defender دفق الأحداث من خلال [البحث](../defender/advanced-hunting-overview.md) المتقدم إلى مركز [الأحداث و/](/azure/event-hubs/)أو حساب [تخزين Azure](/azure/event-hubs/).

لمزيد من المعلومات حول Microsoft 365 Defender دفق API، راجع [الفيديو](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga).

## <a name="in-this-section"></a>في هذا القسم

الموضوع | الوصف
:---|:---
[دفق الأحداث إلى Azure Event Hubs](streaming-api-event-hub.md)| تعرف على كيفية تمكين دفق API في المستأجر وتكوين Microsoft 365 Defender لبث ["](../defender/advanced-hunting-overview.md)البحث المتقدم" إلى مراكز الأحداث.
[دفق الأحداث إلى حساب تخزين Azure](streaming-api-storage.md)| تعرف على كيفية تمكين دفق API في المستأجر وتكوين Microsoft 365 Defender للصيد المتقدم إلى حساب تخزين Azure الخاص بك.[](advanced-hunting-overview.md)
[أنواع الأحداث المعتمدة](supported-event-types.md) | تعرف على الأحداث المتقدمة التي تدعمها API للصيد المتقدم.


## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة حول "الصيد المتقدم"](../defender/advanced-hunting-overview.md)
- [وثائق Azure Event Hubs](/azure/event-hubs/)
- [وثائق حساب تخزين Azure](/azure/storage/common/storage-account-overview)
