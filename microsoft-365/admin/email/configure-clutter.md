---
title: تكوين البريد الإضافي لمؤسستك
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 832276bd-d024-47b6-a80a-a6b884907a5b
description: 'تعرف على كيفية تمكين ميزة البريد الإضافي أو تعطيلها لجميع المستخدمين أو المستخدمين المحددين في مؤسستك، باستخدام Exchange PowerShell. '
ms.openlocfilehash: 64c11b2a8bbce3747727c458a4427f5c0e1b135b
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437184"
---
# <a name="configure-microsoft-365-clutter-for-your-organization"></a>تكوين بريد إضافي Microsoft 365 لمؤسستك

> [!TIP]
> ستحل [علبة وارد المركز عليه](../setup/configure-focused-inbox.md) محل البريد الإضافي. تعرف على المزيد: [التحديث على "علبة وارد المركز عليه" وخططنا ل "البريد الإضافي"](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
بصفتك مسؤولا، قد تحتاج إلى إدارة ميزة البريد الإضافي في Microsoft 365. لتشغيل/إيقاف تشغيل ميزة البريد الإضافي للمستخدمين في مؤسستك، يجب استخدام Exchange PowerShell. (يمكن للأفراد تشغيله/إيقاف تشغيله باستخدام هذه الإرشادات: [إيقاف تشغيل/تشغيل البريد الإضافي في Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
اطلع على [استخدام PowerShell مع Exchange Online](/powershell/exchange/exchange-online-powershell) [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على تفاصيل حول استخدام Exchange PowerShell. يجب أن يكون لديك حساب لديه على الأقل دور مسؤول خدمة Exchange والقدرة على الاتصال Exchange Online باستخدام PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>تشغيل البريد الإضافي باستخدام Exchange PowerShell

يمكنك تمكين البريد الإضافي يدويا لعل بريد عن طريق تشغيل [Cmdlet Set-Clutter](/powershell/module/exchange/set-clutter) . يمكنك أيضا عرض إعدادات البريد الإضافي لعلب البريد في مؤسستك عن طريق تشغيل [Cmdlet Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
تشغيل البريد الإضافي لمستخدم واحد يسمى ألي بيلو
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>إيقاف تشغيل البريد الإضافي باستخدام Exchange PowerShell

يمكنك تعطيل البريد الإضافي يدويا لعل بريد عن طريق تشغيل [Cmdlet Set-Clutter](/powershell/module/exchange/set-clutter) . يمكنك أيضا عرض إعدادات **البريد الإضافي** لعلب البريد في مؤسستك عن طريق تشغيل [Cmdlet Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
إيقاف تشغيل البريد الإضافي لمستخدم واحد يسمى ألي بيلو:
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

إذا كنت تستخدم PowerShell لإنشاء المستخدمين بشكل مجمع، فستحتاج إلى تشغيل [Set-Clutter](/powershell/module/exchange/set-clutter) مقابل علبة بريد كل مستخدم لإدارة البريد الإضافي. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>متى يظهر زر "البريد الإضافي" على/إيقاف تشغيله للمستخدمين في Outlook على ويب؟
<a name="bkmk_onoff"> </a>

بصفتك مسؤولا، يمكنك إعادة تمكين البريد الإضافي باستخدام Exchange PowerShell. بمجرد الانتهاء من ذلك، سيتم إيقاف تشغيل "علبة وارد المركز عليه" وستكون ميزة البريد الإضافي نشطة مرة أخرى. 
  
 **إذا كنت تستخدم Outlook على ويب مع اشتراك Microsoft 365 Business Premium:**
  
- إذا كان لدى المستخدم حاليا بريد إضافي ممكن: 
    
  - تظهر إعدادات البريد الإضافي
    
- إذا كان لدى المستخدم حاليا "علبة وارد المركز عليه" ممكنة: 
    
  - لن تظهر إعدادات البريد الإضافي
    
- إذا لم يتم تمكين "البريد الإضافي" أو "علبة وارد المركز عليه": 
    
  - تظهر كل من "البريد الإضافي" و"علبة وارد المركز عليه" كخيارات في الإعدادات "البريد" الخاص بالمستخدم
    
 **إذا كنت تستخدم Outlook.com:**
  
- إذا كان لدى المستخدم حاليا بريد إضافي ممكن: 
    
  - تظهر إعدادات البريد الإضافي
    
- إذا كان لدى المستخدم حاليا "علبة وارد المركز عليه" ممكنة: 
    
  - لن تظهر إعدادات البريد الإضافي
    
- إذا لم يتم تمكين "البريد الإضافي" أو "علبة وارد المركز عليه": 
    
  - تظهر كل من "البريد الإضافي" و"علبة وارد المركز عليه" كخيارات في الإعدادات "البريد" الخاص بالمستخدم
    
- إذا قام المستخدم بتمكين "علبة وارد المركز عليه" في مرحلة ما في الماضي:
    
  - لن تظهر إعدادات البريد الإضافي أبدا
    
    خلاف ذلك 
    
  - ستظهر إعدادات البريد الإضافي
    
## <a name="related-content"></a>المحتويات ذات الصلة

[استخدام البريد الإضافي لفرز الرسائل ذات الأولوية المنخفضة في Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (مقالة)\
[استخدام البريد الإضافي لفرز الرسائل ذات الأولوية المنخفضة في OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (مقالة)\
[إيقاف تشغيل البريد الإضافي في Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (مقالة)
