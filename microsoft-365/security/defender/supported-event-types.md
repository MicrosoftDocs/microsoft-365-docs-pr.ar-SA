---
title: Microsoft 365 Defender أحداث الدفق المعتمدة في API لتدفق الأحداث
description: تعرف على أنواع أحداث النقل المتدفق (الجداول) المعتمدة بواسطة API المتدفق
keywords: تصدير البيانات الخام، API المتدفق، API، مراكز الأحداث، تخزين Azure، حساب التخزين، البحث، مشاركة البيانات الخام
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
ms.openlocfilehash: e8264ccb9e3181f6b58a6206417eb2b842bec6e7
ms.sourcegitcommit: 317fab13e84b2867087a6ba0a593313ecf43bbed
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/15/2021
ms.locfileid: "63574637"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>أنواع Microsoft 365 Defender النقل المتدفق المعتمدة في API لتدفق الأحداث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


يتم توسيع API لتدفق الأحداث باستمرار لدعم المزيد من أنواع الأحداث. تعرف على جداول "الصيد" المتوفرة بشكل عام، حاليا في المعاينة العامة، أو غير المعتمدة بعد. 
**جديد - أنواع/جداول أحداث البريد الإلكتروني أصبحت الآن GA**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>حالة دعم جداول الصيد في API لتدفق الأحداث

يتضمن الجدول التالي فقط قائمة الجداول المعتمدة في تدفق API، وهو غير شامل لكل مخطط AH. للحصول على قائمة كاملة ب API، راجع [التعرف على جداول المخططات](advanced-hunting-schema-tables.md#learn-the-schema-tables).


| اسم الجدول | الحالة |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | GA |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | GA  |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |GA |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |GA |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | GA |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | GA |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | GA |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | GA |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |GA |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | GA |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | GA |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | GA |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | GA |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | GA |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | GA |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | GA |


