---
title: تكوين "الفوضى" لمنظمتك
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
description: 'تعرف على كيفية تمكين ميزة "الفوضى" أو تعطيلها لجميع المستخدمين أو مستخدمين معينين في مؤسستك، باستخدام Exchange PowerShell. '
ms.openlocfilehash: 5037e7cb6518ca90f3d12c183fcff3c838c29907
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63567748"
---
# <a name="configure-clutter-for-your-organization"></a>تكوين "الفوضى" لمنظمتك

> [!TIP]
> [ستحل "علبة وارد مركز](../setup/configure-focused-inbox.md) عليه" محل البريد الإلكتروني. تعرف على المزيد: [التحديث على "علبة وارد مركز عليه" وخططنا للتكدث](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
برتبة مسؤول، قد تحتاج إلى إدارة ميزة البريد غير المعبأ في Microsoft 365. ل تشغيل ميزة "الفوضى" /إيقاف تشغيلها للمستخدمين في مؤسستك، يجب استخدام Exchange PowerShell. (يمكن للأفراد تشغيله/إيقاف تشغيله باستخدام هذه الإرشادات: إيقاف [تشغيل/تشغيل](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) "الفوضى" في Outlook.
  
اطلع على [استخدام PowerShell](/powershell/exchange/exchange-online-powershell) مع Exchange Online [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على تفاصيل حول Exchange PowerShell. يجب أن يكون لديك حساب له على الأقل Exchange مسؤول الخدمة والقدرة على الاتصال Exchange Online PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>تشغيل "الفوضى" باستخدام Exchange PowerShell

يمكنك تمكين البريد البريدي يدويا لعلبة بريد عن طريق تشغيل [الأمر Cmdlet Set-Clutter](/powershell/module/exchange/set-clutter) . يمكنك أيضا عرض إعدادات البريد البريدي لعلب البريد في مؤسستك عن طريق تشغيل [الأمر Cmdlet الخاص ب Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
تشغيل "الفوضى" لمستخدم واحد يسمى "آلي بيلو"
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>إيقاف تشغيل "الفوضى" Exchange PowerShell

يمكنك تعطيل البريد البريدي يدويا لعلبة بريد عن طريق تشغيل [الأمر Cmdlet Set-Clutter](/powershell/module/exchange/set-clutter) . يمكنك أيضا عرض **إعدادات البريد** البريدي لعلب البريد في مؤسستك عن طريق تشغيل [الأمر Cmdlet الخاص ب Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
إيقاف تشغيل "الفوضى" لمستخدم واحد يسمى "آلي بيلو":
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

إذا كنت تستخدم PowerShell لإنشاء المستخدمين بشكل مجمع، فسوف تحتاج إلى تشغيل [Set-Clutter](/powershell/module/exchange/set-clutter) مقابل علبة بريد كل مستخدم لإدارة البريد الإلكتروني. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>متى يظهر مفتاح التبديل "تشغيل/إيقاف تشغيل" للمستخدمين في Outlook على ويب؟
<a name="bkmk_onoff"> </a>

برتبة مسؤول، يمكنك إعادة تمكين البريد البريدي باستخدام Exchange PowerShell. بمجرد القيام بذلك، سيتم إيقاف تشغيل "علبة وارد مركز عليه" وسيبقى البريد الإلكتروني "بريدا غير نشط" مجددا. 
  
 **إذا كنت تستخدم Outlook على ويب مع اشتراك Microsoft 365 Business Premium:**
  
- إذا قام المستخدم حاليا بتمكين "الفوضى": 
    
  - تظهر إعدادات "الفوضى"
    
- إذا قام المستخدم حاليا بتمكين "علبة وارد مركز عليه": 
    
  - لن تظهر إعدادات "الفوضى"
    
- إذا لم يتم تمكين أي من "البريد غير المزدوج" أو "علبة وارد مركز عليه": 
    
  - تظهر كل من "البريد غير المرغوب فيه" و"علبة وارد مركز عليه" كالخيارات في "البريد" الخاص الإعدادات
    
 **إذا كنت تستخدم Outlook.com:**
  
- إذا قام المستخدم حاليا بتمكين "الفوضى": 
    
  - تظهر إعدادات "الفوضى"
    
- إذا قام المستخدم حاليا بتمكين "علبة وارد مركز عليه": 
    
  - لن تظهر إعدادات "الفوضى"
    
- إذا لم يتم تمكين أي من "البريد غير المزدوج" أو "علبة وارد مركز عليه": 
    
  - تظهر كل من "البريد غير المرغوب فيه" و"علبة وارد مركز عليه" كالخيارات في "البريد" الخاص الإعدادات
    
- إذا قام المستخدم بتمكين "علبة وارد مركز عليه" في وقت ما في الماضي:
    
  - لن تظهر إعدادات "الفوضى" أبدا
    
    وبخلاف ذلك، 
    
  - ستظهر إعدادات "الفوضى"
    
## <a name="related-content"></a>المحتوى ذي الصلة

[استخدام البريد غير المزدوج لفرز الرسائل ذات الأولوية المنخفضة في](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) Outlook (مقالة)\
[استخدام البريد الإلكتروني لفرز الرسائل ذات الأولوية المنخفضة في OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (مقالة)\
[إيقاف تشغيل "الفوضى" في Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (مقالة)
