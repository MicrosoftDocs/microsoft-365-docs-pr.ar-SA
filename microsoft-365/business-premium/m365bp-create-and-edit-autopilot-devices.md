---
title: إنشاء أجهزة Autopilot وتحريرها
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
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
description: تعرف على كيفية تحميل الأجهزة باستخدام Autopilot في Microsoft 365 Business Premium. يمكنك تعيين ملف تعريف إلى جهاز أو مجموعة من الأجهزة.
ms.openlocfilehash: 994eab29d4b04e2de21d3e42a4abc174270f67f7
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857423"
---
# <a name="create-and-edit-autopilot-devices"></a>إنشاء أجهزة Autopilot وتحريرها

## <a name="upload-a-list-of-devices"></a>تحميل قائمة بالأجهزة

يمكنك استخدام [الدليل المفصل خطوة بخطوة](m365bp-add-Autopilot-devices-and-profile.md) لتحميل الأجهزة، ولكن يمكنك أيضا تحميل الأجهزة في علامة التبويب **"الأجهزة** ". 
  
يجب أن تفي الأجهزة بهذه المتطلبات:
  
- Windows 10، الإصدار 1703 أو أحدث
    
- الأجهزة الجديدة التي لم تمر بتجربة Windows الجاهزة

1. في مركز مسؤولي Microsoft 365، اختر **Devices** \> **Autopilot**.
  
2. في صفحة **Autopilot** ، اختر علامة التبويب **"** \> **إضافة أجهزة**".
    
    ![في علامة التبويب "الأجهزة"، اختر "إضافة أجهزة".](./../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. في لوحة **"إضافة أجهزة** "، استعرض وصولا إلى [ملف CSV لقائمة الأجهزة](../admin/misc/device-list.md)  الذي قمت بإعداده \> **"حفظ** \> **إغلاق**".
    
    يمكنك الحصول على هذه المعلومات من مورد الأجهزة، أو يمكنك استخدام [البرنامج النصي Get-WindowsAutopilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) لإنشاء ملف CSV. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>تعيين ملف تعريف إلى جهاز أو مجموعة من الأجهزة

1. في صفحة **"إعداد Windows** "، اختر علامة التبويب **"الأجهزة** "، وحدد خانة الاختيار إلى جانب جهاز واحد أو أكثر. 
    
2. في لوحة **الجهاز** ، حدد ملف تعريف من القائمة المنسدلة **لملف التعريف المعين** . 
    
    إذا لم يكن لديك أي ملفات تعريف حتى الآن، فراجع [إنشاء ملفات تعريف Autopilot وتحريرها](../admin/devices/create-and-edit-Autopilot-profiles.md) للحصول على الإرشادات. 

## <a name="see-also"></a>راجع أيضًا

[أفضل الممارسات لتأمين خطط Microsoft 365 للأعمال](../admin/security-and-compliance/secure-your-business-data.md)
