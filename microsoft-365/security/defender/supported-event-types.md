---
title: Microsoft 365 Defender أنواع أحداث الدفق المعتمدة في واجهة برمجة تطبيقات تدفق الأحداث
description: تعرف على أنواع أحداث الدفق (الجداول) التي تدعمها واجهة برمجة التطبيقات المتدفقة
keywords: تصدير البيانات الأولية، وواجهة برمجة تطبيقات الدفق، وواجهة برمجة التطبيقات، ومراكز الأحداث، وتخزين Azure، وحساب التخزين، والتتبع، ومشاركة البيانات الأولية
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
ms.openlocfilehash: 4f6f098c9d2ec09a777110955b8acb1663e102ed
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057840"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>أنواع أحداث دفق Microsoft 365 Defender المعتمدة في واجهة برمجة تطبيقات دفق الأحداث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


يتم توسيع واجهة برمجة تطبيقات تدفق الأحداث باستمرار لدعم المزيد من أنواع الأحداث. تعرف على جداول التتبع المتوفرة بشكل عام، حاليا في المعاينة العامة، أو غير المعتمدة بعد. 
**جديد - أنواع/جداول أحداث البريد الإلكتروني هي الآن GA**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>تدعم جداول التتبع حالة في واجهة برمجة تطبيقات تدفق الأحداث

يتضمن الجدول التالي فقط قائمة الجداول المعتمدة في واجهة برمجة التطبيقات المتدفقة، وهو غير شامل لكافة مخطط AH. للحصول على قائمة كاملة بواجهة برمجة التطبيقات، [تعرف على جداول المخطط](advanced-hunting-schema-tables.md#learn-the-schema-tables).

| اسم الجدول | حاله<br>(تجاري) | سحابة القطاع الحكومي | سحابة القطاع الحكومي عالية | وزاره الدفاع |
|----|----|----|----|----|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | GA | GA | GA | GA |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |GA | GA | GA | GA |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |GA | GA | GA | GA |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | GA | GA | GA | GA |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | GA | GA | GA | GA |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | GA | GA | GA | GA |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |GA | GA | GA | GA |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | GA | GA | GA | GA |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | GA | GA | GA | GA |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | GA |![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | GA |![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | GA |![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | GA |![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)**|GA|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)**|GA|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)**|GA|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)**|GA|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|![لا](../defender-endpoint/images/svg/check-no.svg)|
