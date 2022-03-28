---
title: إنشاء أجهزة AutoPilot وتحريرها
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0f7b1d7c-4086-4331-8534-45d7886f9f34
description: تعرف على كيفية تحميل الأجهزة باستخدام AutoPilot في Microsoft 365 Business Premium. يمكنك تعيين ملف تعريف إلى جهاز أو مجموعة من الأجهزة.
ms.openlocfilehash: 784db256bb5dae16739722566b6f7a9c8511a678
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575637"
---
# <a name="create-and-edit-autopilot-devices"></a>إنشاء أجهزة AutoPilot وتحريرها

> [!NOTE]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="upload-a-list-of-devices"></a>Upload قائمة الأجهزة

يمكنك استخدام الدليل خطوة [بخطوة](add-autopilot-devices-and-profile.md) لتحميل الأجهزة، ولكن يمكنك أيضا تحميل الأجهزة في علامة **التبويب** أجهزة. 
  
يجب أن تلبي الأجهزة هذه المتطلبات:
  
- Windows 10 الإصدار 1703 أو الإصدارات الأحدث
    
- الأجهزة الجديدة التي لم تمر عبر تجربة Windows غير المجهزة

1. في مركز مسؤولي Microsoft 365، اختر **الأجهزة** \> **AutoPilot**.
  
2. في صفحة **AutoPilot** ، اختر علامة **التبويب أجهزة** \> **إضافة أجهزة**.
    
    ![في علامة التبويب الأجهزة، اختر إضافة أجهزة.](../../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. في اللوحة **إضافة أجهزة** ، استعرض بحثا عن ملف [CSV](../misc/device-list.md) لقائمة الأجهزة الذي قمت بإعداده \> **حفظ** \> **إغلاق**.
    
    يمكنك الحصول على هذه المعلومات من مورد الأجهزة، أو يمكنك استخدام البرنامج النصي [Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) لإنشاء ملف CSV. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>تعيين ملف تعريف إلى جهاز أو مجموعة من الأجهزة

1. في الصفحة **إعداد Windows**، **اختر علامة التبويب** أجهزة، وحدد خانة الاختيار بجانب جهاز واحد أو أكثر. 
    
2. في لوحة **الجهاز** ، حدد ملف تعريف من المنسدل **ملف التعريف** المعين. 
    
    إذا لم يكن لديك أي ملفات تعريف بعد، ف راجع [إنشاء ملفات تعريف AutoPilot](create-and-edit-autopilot-profiles.md) وتحريرها للحصول على الإرشادات. 

## <a name="see-also"></a>راجع أيضًا

[أفضل 10 طرق لتأمين Microsoft 365 خطط الأعمال](../security-and-compliance/secure-your-business-data.md)