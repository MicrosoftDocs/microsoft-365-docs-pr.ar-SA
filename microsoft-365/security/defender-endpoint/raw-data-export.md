---
title: حدث Stream Microsoft Defender for Endpoint
description: تعرف على كيفية تكوين Microsoft Defender لنقطة النهاية لبث أحداث "البحث المتقدم" إلى "مراكز الأحداث" أو حساب تخزين Azure
keywords: تصدير البيانات الخام، دفق API، API، مراكز الأحداث، تخزين Azure، حساب التخزين، البحث المتقدم، مشاركة البيانات الخام
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
ms.custom: api
ms.openlocfilehash: 94a815a6fc734c8e8e310a17f2e73931f4ffab5c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570657"
---
# <a name="raw-data-streaming-api"></a>API لتدفق البيانات الخام

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>دفق أحداث "البحث المتقدم" إلى "مراكز الأحداث" و/أو حساب تخزين Azure

يدعم Microsoft Defender ل Endpoint أحداث النقل المتدفق المتوفرة من خلال ["](../defender/advanced-hunting-overview.md) البحث المتقدم" إلى مركز [الأحداث و/](/azure/event-hubs/) أو حساب [تخزين Azure](/azure/storage/common/storage-account-overview).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4ga]

## <a name="in-this-section"></a>في هذا القسم

الموضوع|الوصف
:---|:---
[دفق أحداث Microsoft Defender لنقطة النهاية إلى مراكز أحداث Azure](raw-data-export-event-hub.md)|تعرف على كيفية تمكين دفق API في المستأجر وتكوين Defender ل Endpoint لبث ["](advanced-hunting-overview.md) البحث المتقدم إلى مراكز الأحداث".
[أحداث Stream Defender for Endpoint إلى حساب تخزين Azure](raw-data-export-storage.md)|تعرف على كيفية تمكين دفق API في المستأجر وتكوين Defender ل Endpoint لتدفق ["](advanced-hunting-overview.md) البحث المتقدم" إلى حساب تخزين Azure الخاص بك.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول "الصيد المتقدم"](advanced-hunting-overview.md)
- [وثائق Azure Event Hubs](/azure/event-hubs/)
- [وثائق حساب تخزين Azure](/azure/storage/common/storage-account-overview)