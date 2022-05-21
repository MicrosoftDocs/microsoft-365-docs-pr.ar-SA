---
title: دفق أحداث Microsoft 365 Defender
description: تعرف على كيفية تكوين Microsoft 365 Defender لدفق أحداث التتبع المتقدمة إلى Event Hubs أو حساب تخزين Azure
keywords: تصدير البيانات الأولية، وتدفق واجهة برمجة التطبيقات، وواجهة برمجة التطبيقات، ومراكز الأحداث، وتخزين Azure، وحساب التخزين، والتتبع المتقدم، ومشاركة البيانات الأولية
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
ms.openlocfilehash: d9f980656df636632c5903853c2784de81131d81
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621413"
---
# <a name="streaming-api"></a>واجهات برمجة تطبيقات البث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>دفق أحداث التتبع المتقدم إلى مراكز الأحداث و/أو حساب تخزين Azure.

يدعم Microsoft 365 Defender بث الأحداث من خلال [التتبع المتقدم](../defender/advanced-hunting-overview.md) إلى [Event Hubs](/azure/event-hubs/) و/أو [حساب تخزين Azure](/azure/event-hubs/).

لمزيد من المعلومات حول Microsoft 365 Defender واجهة برمجة التطبيقات المتدفقة، راجع [الفيديو](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga).

## <a name="in-this-section"></a>في هذا القسم

الموضوع | الوصف
:---|:---
[دفق الأحداث إلى Azure Event Hubs](streaming-api-event-hub.md)| تعرف على كيفية تمكين واجهة برمجة التطبيقات المتدفقة في المستأجر وتكوين Microsoft 365 Defender لدفق [التتبع المتقدم](../defender/advanced-hunting-overview.md) إلى مراكز الأحداث.
[دفق الأحداث إلى حساب تخزين Azure](streaming-api-storage.md)| تعرف على كيفية تمكين واجهة برمجة التطبيقات المتدفقة في المستأجر وتكوين Microsoft 365 Defender لدفق [Advanced Hunting](advanced-hunting-overview.md) إلى حساب تخزين Azure الخاص بك.
[أنواع الأحداث المعتمدة](supported-event-types.md) | تعرف على أحداث التتبع المتقدم التي تدعمها واجهة برمجة التطبيقات المتدفقة.

شاهد هذا الفيديو القصير لمعرفة كيفية إعداد واجهة برمجة التطبيقات المتدفقة لشحن معلومات الحدث مباشرة إلى مراكز أحداث Azure للاستهلاك من خلال خدمات المرئيات أو محركات معالجة البيانات أو تخزين Azure للاحتفاظ بالبيانات على المدى الطويل.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga]

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة على التتبع المتقدم](../defender/advanced-hunting-overview.md)
- [وثائق Azure Event Hubs](/azure/event-hubs/)
- [وثائق حساب تخزين Azure](/azure/storage/common/storage-account-overview)
