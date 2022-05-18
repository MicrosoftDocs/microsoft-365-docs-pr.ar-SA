---
title: ملف CSV لقائمة الأجهزة
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- MSB365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 932e3676-2491-49f0-9177-d893d2f5276e
ROBOTS: NOINDEX
description: تعرف على كيفية إنشاء ملف CSV ل AutoPilot في Microsoft 365 للأعمال.
ms.openlocfilehash: af695448e31ea93d36b36a8831702acb84a92410
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469547"
---
# <a name="windows-autopilot-device-list-csv-file"></a>Windows Autopilot device list CSV-file

## <a name="device-list-csv-file-format"></a>تنسيق ملف .csv قائمة الأجهزة

لإدارة الأجهزة وتوزيعها من خلال Windows Autopilot، ستحتاج إلى ملف .csv يحتوي على معلومات محددة حول الأجهزة.
  
يجب أن تحتوي الأعمدة في ملف قائمة الأجهزة على الرؤوس التالية بالترتيب المحدد:
  
- العمود A: الرقم التسلسلي للجهاز

- العمود B: اتركه فارغا

- العمود C: تجزئة الأجهزة

يمكنك الحصول على هذه المعلومات من مورد الأجهزة، أو يمكنك استخدام [البرنامج النصي Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) الذي سينشئ ملف CSV. 

عند إضافة أجهزة، تحتاج أيضا إلى إضافتها إلى ملف تعريف. يتم استخدام ملف تعريف لتطبيق ملفات تعريف نشر AutoPilot على جهاز أو مجموعة من الأجهزة.
  
## <a name="related-content"></a>المحتوى ذو الصلة

[Microsoft 365 لوثائق وموارد الأعمال](../../index.yml)
  
[بدء استخدام Microsoft 365 للأعمال](../../admin/admin-overview/what-is-microsoft-365.md)