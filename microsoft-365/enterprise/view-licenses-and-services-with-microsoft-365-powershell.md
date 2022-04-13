---
title: عرض Microsoft 365 التراخيص والخدمات باستخدام PowerShell
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
description: يشرح كيفية استخدام PowerShell لعرض معلومات حول خطط الترخيص والخدمات والتراخيص المتوفرة في مؤسستك Microsoft 365.
ms.openlocfilehash: 8b5ff01f15e4dea7a44b423609b6533cc5729a5f
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823883"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>عرض Microsoft 365 التراخيص والخدمات باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يتكون كل اشتراك Microsoft 365 من العناصر التالية:

- **خطط الترخيص** تعرف هذه أيضا بخطط الترخيص أو خطط Microsoft 365. تحدد خطط الترخيص خدمات Microsoft 365 المتوفرة للمستخدمين. قد يحتوي اشتراكك في Microsoft 365 على خطط ترخيص متعددة. ومن الأمثلة على خطة الترخيص Microsoft 365 E3.
    
- **خدمات** تعرف هذه أيضا بخطط الخدمة. الخدمات هي المنتجات والميزات والقدرات Microsoft 365 المتوفرة في كل خطة ترخيص، على سبيل المثال، Exchange Online Microsoft 365 Apps for enterprise (المسمى سابقا Office 365 ProPlus). يمكن أن يكون لدى المستخدمين تراخيص متعددة معينة لهم من خطط ترخيص مختلفة تمنح حق الوصول إلى خدمات مختلفة.
    
- **التراخيص** تحتوي كل خطة ترخيص على عدد التراخيص التي اشتريتها. يمكنك تعيين تراخيص للمستخدمين حتى يتمكنوا من استخدام خدمات Microsoft 365 التي تم تعريفها بواسطة خطة الترخيص. يتطلب كل حساب مستخدم ترخيصا واحدا على الأقل من خطة ترخيص واحدة حتى يتمكنوا من تسجيل الدخول إلى Microsoft 365 واستخدام الخدمات.
    
يمكنك استخدام PowerShell Microsoft 365 لعرض تفاصيل حول خطط الترخيص والتراخيص والخدمات المتوفرة في مؤسستك Microsoft 365. لمزيد من المعلومات حول المنتجات والميزات والخدمات المتوفرة في اشتراكات Office 365 مختلفة، راجع [Office 365 خيارات الخطة](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-microsoft-graph-powershell-sdk"></a>استخدام Microsoft Graph PowerShell SDK

أولا، [اتصل بمستأجر Microsoft 365](/graph/powershell/get-started#authentication).

تتطلب قراءة خطط ترخيص الاشتراك نطاق أذونات Organization.Read.All أو أحد الأذونات الأخرى المدرجة في [الصفحة المرجعية "List subscribedSkus" Graph API](/graph/api/subscribedsku-list).

```powershell
Connect-Graph -Scopes Organization.Read.All
```

لعرض معلومات موجزة حول خطط الترخيص الحالية والتراخيص المتوفرة لكل خطة، قم بتشغيل هذا الأمر:
  
```powershell
Get-MgSubscribedSku | Select -Property Sku*, ConsumedUnits -ExpandProperty PrepaidUnits | Format-List
```

تحتوي النتائج على:
  
- **SkuPartNumber:** إظهار خطط الترخيص المتوفرة لمؤسستك. على سبيل المثال، `ENTERPRISEPACK` هو اسم خطة الترخيص Office 365 Enterprise E3.
    
- **تمكين:** عدد التراخيص التي اشتريتها لخطة ترخيص معينة.
    
- **العناصر المستهلكة:** عدد التراخيص التي قمت بتعيينها للمستخدمين من خطة ترخيص معينة.
    
لعرض تفاصيل حول خدمات Microsoft 365 المتوفرة في جميع خطط الترخيص، قم أولا بعرض قائمة بخطط الترخيص.

```powershell
Get-MgSubscribedSku
```

بعد ذلك، قم بتخزين معلومات خطط الترخيص في متغير.

```powershell
$licenses = Get-MgSubscribedSku
```

بعد ذلك، اعرض الخدمات في خطة ترخيص معينة.

```powershell
$licenses[<index>].ServicePlans
```

\<index> هو عدد صحيح يحدد رقم صف خطة الترخيص من عرض `Get-MgSubscribedSku | Select SkuPartNumber` الأمر، ناقص 1.

على سبيل المثال، إذا كان عرض `Get-MgSubscribedSku | Select SkuPartNumber` الأمر هو التالي:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

ثم الأمر لعرض الخدمات لخطة ترخيص ENTERPRISEPREMIUM هو:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM هو الصف الثالث. لذلك، قيمة الفهرس هي (3 - 1)، أو 2.

للحصول على قائمة كاملة بخطط الترخيص (المعروفة أيضا باسم أسماء المنتجات)، وخطط الخدمة المضمنة، وأسماءها المألوفة المقابلة، راجع [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
لعرض معلومات موجزة حول خطط الترخيص الحالية والتراخيص المتوفرة لكل خطة، قم بتشغيل هذا الأمر:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

تحتوي النتائج على:
  
- **SkuPartNumber:** إظهار خطط الترخيص المتوفرة لمؤسستك. على سبيل المثال، `ENTERPRISEPACK` هو اسم خطة الترخيص Office 365 Enterprise E3.
    
- **تمكين:** عدد التراخيص التي اشتريتها لخطة ترخيص معينة.
    
- **العناصر المستهلكة:** عدد التراخيص التي قمت بتعيينها للمستخدمين من خطة ترخيص معينة.
    
لعرض تفاصيل حول خدمات Microsoft 365 المتوفرة في جميع خطط الترخيص، قم أولا بعرض قائمة بخطط الترخيص.

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

\<index> هو عدد صحيح يحدد رقم صف خطة الترخيص من عرض `Get-AzureADSubscribedSku | Select SkuPartNumber` الأمر، ناقص 1.

على سبيل المثال، إذا كان عرض `Get-AzureADSubscribedSku | Select SkuPartNumber` الأمر هو التالي:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

ثم الأمر لعرض الخدمات لخطة ترخيص ENTERPRISEPREMIUM هو:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM هو الصف الثالث. لذلك، قيمة الفهرس هي (3 - 1)، أو 2.

للحصول على قائمة كاملة بخطط الترخيص (المعروفة أيضا باسم أسماء المنتجات)، وخطط الخدمة المضمنة، وأسماءها المألوفة المقابلة، راجع [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>يتوفر برنامج نصي PowerShell يقوم بأتمتة الإجراءات الموضحة في هذا الموضوع. على وجه التحديد، يتيح لك البرنامج النصي عرض الخدمات وتعطيلها في مؤسستك Microsoft 365، بما في ذلك Sway. لمزيد من المعلومات، راجع [تعطيل الوصول إلى Sway باستخدام PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
لعرض معلومات موجزة حول خطط الترخيص الحالية والتراخيص المتوفرة لكل خطة، قم بتشغيل الأمر التالي:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.
>

تحتوي النتائج على المعلومات التالية:
  
- **AccountSkuId:** إظهار خطط الترخيص المتوفرة لمؤسستك باستخدام بناء الجملة `<CompanyName>:<LicensingPlan>`.  _\<CompanyName>_ هي القيمة التي قدمتها عند التسجيل في Microsoft 365، وهي فريدة لمؤسستك. _\<LicensingPlan>_ القيمة هي نفسها للجميع. على سبيل المثال، في القيمة`litwareinc:ENTERPRISEPACK`، يكون اسم `litwareinc`الشركة، واسم `ENTERPRISEPACK`خطة الترخيص، وهو اسم النظام Office 365 Enterprise E3.
    
- **ActiveUnits:** عدد التراخيص التي اشتريتها لخطة ترخيص معينة.
    
- **WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.
    
- **العناصر المستهلكة:** عدد التراخيص التي قمت بتعيينها للمستخدمين من خطة ترخيص معينة.
    
لعرض تفاصيل حول خدمات Microsoft 365 المتوفرة في جميع خطط الترخيص، قم بتشغيل الأمر التالي:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

يعرض الجدول التالي خطط خدمة Microsoft 365 وأسماءها المألوفة للخدمات الأكثر شيوعا. قد تكون قائمة خطط الخدمة الخاصة بك مختلفة. 
  
|**خطة الخدمة**|**الوصف**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 Apps for enterprise *(المسمى سابقا Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online الخطة 2  <br/> |
   
للحصول على قائمة كاملة بخطط الترخيص (المعروفة أيضا باسم أسماء المنتجات)، وخطط الخدمة المضمنة، وأسماءها المألوفة المقابلة، راجع [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

لعرض تفاصيل حول خدمات Microsoft 365 المتوفرة في خطة ترخيص معينة، استخدم بناء الجملة التالي.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

يوضح هذا المثال الخدمات المتوفرة في خطة ترخيص litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)