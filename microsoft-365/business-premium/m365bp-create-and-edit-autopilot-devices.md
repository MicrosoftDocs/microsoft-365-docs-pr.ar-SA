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
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية تحميل الأجهزة باستخدام Autopilot في Microsoft 365 Business Premium. يمكنك تعيين ملف تعريف إلى جهاز أو مجموعة من الأجهزة.
ms.openlocfilehash: 9e02b985e5742331426210d6d3824dfa120a21d3
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894976"
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
