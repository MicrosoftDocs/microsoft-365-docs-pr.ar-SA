---
title: عرض Microsoft 365 والخدمات باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: يشرح كيفية استخدام PowerShell لعرض معلومات حول خطط الترخيص والخدمات والتراخيص المتوفرة في Microsoft 365 مؤسستك.
ms.openlocfilehash: 3b90596c68e3beadcc2b33ef59ff9c3503b84f8a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575303"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>عرض Microsoft 365 والخدمات باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يتكون Microsoft 365 الاشتراك من العناصر التالية:

- **خطط الترخيص** تعرف أيضا بخطط الترخيص أو Microsoft 365 أخرى. تحدد خطط الترخيص Microsoft 365 المتوفرة للمستخدمين. قد Microsoft 365 الاشتراك خطط ترخيص متعددة. قد يكون أحد أمثلة خطة الترخيص Microsoft 365 E3.
    
- **الخدمات** تعرف أيضا بخطط الخدمة. الخدمات هي Microsoft 365 والميزات والإمكانات المتوفرة في كل خطة ترخيص، على سبيل المثال، Exchange Online Microsoft 365 Apps for enterprise (التي كانت تسمى سابقا Office 365 ProPlus). يمكن أن يكون لدى المستخدمين تراخيص متعددة تم تعيينها لهم من خطط ترخيص مختلفة تمنح حق الوصول إلى خدمات مختلفة.
    
- **التراخيص** تحتوي كل خطة ترخيص على عدد التراخيص التي اشتريتها. يمكنك تعيين تراخيص للمستخدمين حتى يمكنهم استخدام Microsoft 365 التي تم تعريفها بواسطة خطة الترخيص. يتطلب كل حساب مستخدم ترخيصا واحدا على الأقل من خطة ترخيص واحدة حتى يمكنهم تسجيل الدخول Microsoft 365 واستخدام الخدمات.
    
يمكنك استخدام PowerShell Microsoft 365 لعرض تفاصيل حول خطط الترخيص والتراخيص والخدمات المتوفرة في Microsoft 365 مؤسستك. لمزيد من المعلومات حول المنتجات والميزات والخدمات المتوفرة في اشتراكات Office 365 مختلفة، راجع Office 365 [خيارات الخطة](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
لعرض معلومات ملخصة حول خطط الترخيص الحالية والتراخيص المتوفرة لكل خطة، يمكنك تشغيل هذا الأمر:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

تحتوي النتائج على:
  
- **SkuPartNumber:** يعرض خطط الترخيص المتوفرة لمنظمتك. على سبيل المثال`ENTERPRISEPACK`، هو اسم خطة الترخيص Office 365 Enterprise E3.
    
- **تم التمكين:** عدد التراخيص التي اشتريتها لخطة ترخيص معينة.
    
- **ConsumedUnits:** عدد التراخيص التي قمت بتعيينها إلى مستخدمين من خطة ترخيص معينة.
    
لعرض تفاصيل حول Microsoft 365 المتوفرة في كل خطط الترخيص، اعرض أولا قائمة بخطط الترخيص.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

بعد ذلك، قم بتخزين معلومات خطط الترخيص في متغير.

```powershell
$licenses = Get-AzureADSubscribedSku
```

بعد ذلك، اعرض الخدمات في خطة ترخيص معينة.

```powershell
$licenses[<index>].ServicePlans
```

\<index> هو عدد صحيح يحدد رقم الصف لخطة الترخيص `Get-AzureADSubscribedSku | Select SkuPartNumber` من عرض الأمر، ناقص 1.

على سبيل المثال، إذا كان عرض `Get-AzureADSubscribedSku | Select SkuPartNumber` الأمر هو التالي:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

بعد ذلك، يكون الأمر لعرض الخدمات لخطة ترخيص ENTERPRISEPREMIUM هو:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM هو الصف الثالث. وبالتالي، تكون قيمة الفهرس (3 - 1) أو 2.

للحصول على قائمة كاملة بخطط الترخيص (المعروفة أيضا باسم أسماء المنتجات) وخطط الخدمة المضمنة الخاصة بها وأسماءها المناسبة، راجع أسماء المنتجات ومعرفات خطط [الخدمة للترخيص](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>يتوفر برنامج PowerShell النصي الذي يأتمتة الإجراءات الموضحة في هذا الموضوع. وبشكل خاص، يتيح لك البرنامج النصي عرض الخدمات وتعطيلها في Microsoft 365، بما في ذلك Sway. لمزيد من المعلومات، راجع [تعطيل الوصول إلى Sway باستخدام PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
لعرض معلومات ملخصة حول خطط الترخيص الحالية والتراخيص المتوفرة لكل خطة، يمكنك تشغيل الأمر التالي:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع **Msol** في اسمها. لمواصلة استخدام هذه cmdlets، يجب تشغيلها من Windows PowerShell.
>

تحتوي النتائج على المعلومات التالية:
  
- **AccountSkuId:** إظهار خطط الترخيص المتوفرة لمنظمتك باستخدام بناء الجملة `<CompanyName>:<LicensingPlan>`.  _\<CompanyName>_ هي القيمة التي قدمتها عند التسجيل في Microsoft 365، وهي قيمة فريدة لمنظمتك. القيمة _\<LicensingPlan>_ هي نفسها للجميع. على سبيل المثال`litwareinc:ENTERPRISEPACK`، في القيمة ، `litwareinc`يكون اسم الشركة ، `ENTERPRISEPACK`واسم خطة الترخيص ، وهو اسم النظام Office 365 Enterprise E3.
    
- **ActiveUnits:** عدد التراخيص التي اشتريتها لخطة ترخيص معينة.
    
- **WarningUnits:** عدد التراخيص في خطة ترخيص لم تقم بتجديدها، وستنتهي صلاحيتها بعد فترة السماح التي مدتها 30 يوما.
    
- **ConsumedUnits:** عدد التراخيص التي قمت بتعيينها إلى مستخدمين من خطة ترخيص معينة.
    
لعرض تفاصيل حول Microsoft 365 المتوفرة في كل خطط الترخيص، يمكنك تشغيل الأمر التالي:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

يعرض الجدول التالي Microsoft 365 الجديدة وأسماءها مألوفة للخدمات الأكثر شيوعا. قد تكون قائمة خطط الخدمة الخاصة بك مختلفة. 
  
|**خطة الخدمة**|**الوصف**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 Apps for enterprise *(التي كانت تسمى سابقا Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 2  <br/> |
   
للحصول على قائمة كاملة بخطط الترخيص (المعروفة أيضا باسم أسماء المنتجات) وخطط الخدمة المضمنة الخاصة بها وأسماءها المناسبة، راجع أسماء المنتجات ومعرفات خطط [الخدمة للترخيص](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

لعرض تفاصيل حول Microsoft 365 المتوفرة في خطة ترخيص معينة، استخدم بناء الجملة التالي.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

يوضح هذا المثال الخدمات المتوفرة في خطة ترخيص litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)