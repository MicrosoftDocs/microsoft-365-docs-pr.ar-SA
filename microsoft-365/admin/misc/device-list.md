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
description: تعرف على كيفية عمل ملف CSV ل AutoPilot في Microsoft 365 للأعمال.
ms.openlocfilehash: 62dbcddbdab1a08ab3b19c6616b814c421a57c04
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/06/2021
ms.locfileid: "63568405"
---
# <a name="device-list-csv-file"></a>ملف CSV لقائمة الأجهزة

## <a name="device-list-csv-file-format"></a>قائمة الأجهزة .csv الملف

لإدارة الأجهزة ونشرها Windows Autopilot، ستحتاج إلى ملف .csv يحتوي على معلومات محددة حول الأجهزة.
  
يجب أن تتضمن الأعمدة في ملف قائمة الأجهزة رؤوسا بالترتيب المحدد:
  
- العمود A: الرقم التسلسلي للجهاز

- العمود B: اتركه فارغا

- العمود C: هاش الأجهزة

يمكنك الحصول على هذه المعلومات من مورد الأجهزة، أو يمكنك استخدام البرنامج النصي [Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) الذي سيولد ملف CSV. 

عند إضافة أجهزة، ستحتاج أيضا إلى إضافتها إلى ملف تعريف. يتم استخدام ملف تعريف لتطبيق ملفات تعريف نشر AutoPilot على جهاز أو مجموعة من الأجهزة.
  
## <a name="related-content"></a>المحتوى ذي الصلة

[Microsoft 365 ووثائق الأعمال ومواردها](../../index.yml)
  
[بدء العمل باستخدام Microsoft 365 للأعمال](../../admin/admin-overview/what-is-microsoft-365.md)