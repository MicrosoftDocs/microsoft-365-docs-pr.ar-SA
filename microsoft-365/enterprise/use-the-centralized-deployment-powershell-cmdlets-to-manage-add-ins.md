---
title: استخدام Cmdlets للنشر المركزي في PowerShell لإدارة الوظائف الإضافية
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
ms.custom:
- seo-marvel-apr2020
description: استخدم الأمرين Cmdlets للنشر المركزي في PowerShell لمساعدتك على نشر الوظائف الإضافية Office الإضافية وإدارتها Microsoft 365 مؤسستك.
ms.openlocfilehash: acdda1c30dbd0a19762040140b1bb3bf1a7715d4
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63569616"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>استخدام Cmdlets للنشر المركزي في PowerShell لإدارة الوظائف الإضافية

كمسؤول Microsoft 365 عام، يمكنك نشر Office الإضافية للمستخدمين عبر ميزة "النشر المركزي" (راجع نشر Office الإضافية في [مركز الإدارة](../admin/manage/manage-deployment-of-add-ins.md). بالإضافة إلى نشر Office الإضافية عبر مركز مسؤولي Microsoft 365، يمكنك أيضا استخدام Microsoft PowerShell. قم بتثبيت [وحدة O365 المركزية Add-In النمطية للنشر Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

بعد تنزيل الوحدة النمطية، افتح نافذة عادية Windows PowerShell ثم قم بتشغيل cmdlet التالي:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>الاتصال استخدام بيانات اعتماد المسؤول

قبل أن تتمكن من استخدام cmdlets "النشر المركزي"، ستحتاج إلى تسجيل الدخول.
  
1. ابدأ تشغيل PowerShell.
    
2. الاتصال إلى PowerShell باستخدام بيانات اعتماد مسؤول الشركة. تشغيل الأمر cmdlet التالي.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. في الصفحة **إدخال بيانات الاعتماد**، أدخل Microsoft 365 **المستخدم** **أو بيانات اعتماد** المسؤول العام. بدلا من ذلك، يمكنك إدخال بيانات الاعتماد مباشرة في الأمر cmdlet. 
    
    قم بتشغيل الأمر cmdlet التالي الذي يحدد بيانات اعتماد مسؤول الشركة كعائن PSCredential.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> لمزيد من المعلومات حول استخدام PowerShell، راجع الاتصال [Microsoft 365 PowerShell](./connect-to-microsoft-365-powershell.md). 
  
## <a name="upload-an-add-in-manifest"></a>Upload بيان الوظائف الإضافية

قم بتشغيل **أمر cmdlet New-OrganizationAdd-In** لتحميل بيان الوظائف الإضافية من مسار، والذي يمكن أن يكون إما موقع ملف أو عنوان URL. يوضح المثال التالي موقع ملف لقيمة  _المعلمة ManifestPath_ . 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

يمكنك أيضا تشغيل **الأمر cmdlet New-OrganizationAdd-In** لتحميل الوظائف الإضافية وتعيينها إلى المستخدمين أو المجموعات مباشرة باستخدام المعلمة  _Members_ ، كما هو موضح في المثال التالي. افصل عناوين البريد الإلكتروني للأعضاء باستخدام فاصلة. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Upload إضافة من متجر Office

قم بتشغيل **الأمر cmdlet New-OrganizationAddIn** لتحميل بيان من Office Store.
  
في المثال التالي، يحدد **الأمر cmdlet New-OrganizationAddIn** AssetId لتسويق محتوى وموقع للولايات المتحدة.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

لتحديد قيمة المعلمة _AssetId_، يمكنك نسخها من عنوان URL ل صفحة ويب Office Store ل الإضافية. يبدأ AssetIds دائما ب "WA" متبوع ب رقم. على سبيل المثال، في المثال السابق، مصدر قيمة AssetId ل WA104099688 هو عنوان URL ل صفحة ويب Office Store ل الوظائف الإضافية: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
تكون قيم  _المعلمة Locale_ والمعلمة  _ContentMarket_ متطابقة وتشير إلى البلد/المنطقة التي تحاول تثبيت الوظائف الإضافية منها. التنسيق هو en-US، fr-FR. وهكذا. 
  
> [!NOTE]
> سيتم تحديث الوظائف الإضافية التي تم تحميلها Office Store تلقائيا في غضون بضعة أيام من توفر التحديث الأخير على Office Store. 
  
## <a name="get-details-of-an-add-in"></a>الحصول على تفاصيل عن الوظائف الإضافية

قم بتشغيل **الأمر Cmdlet Get-OrganizationAddIn** كما هو موضح أدناه للحصول على تفاصيل حول كل الوظائف الإضافية التي تم تحميلها إلى المستأجر، بما في ذلك "معر ة منتج" ل الإضافة.
  
```powershell
Get-OrganizationAddIn
```

قم بتشغيل **أمر cmdlet Get-OrganizationAddIn** مع قيمة لمعلمة  _ProductId_ لتحديد أي من الوظائف الإضافية تريد استرداد التفاصيل لها. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

للحصول على التفاصيل الكاملة لكل الوظائف الإضافية بالإضافة إلى المستخدمين والمجموعات المعينة، قم بتنصل إخراج **الأمر Cmdlet Get-OrganizationAddIn** إلى Format-List cmdlet، كما هو موضح في المثال التالي.
  
```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>تشغيل أو إيقاف تشغيل أي من الوظائف الإضافية

إيقاف تشغيل أحد الوظائف الإضافية بحيث لا يعود بإمكان المستخدمين والمجموعات التي تم تعيينها إليها الوصول إليها، قم بتشغيل الأمر **Cmdlet Set-OrganizationAddIn** باستخدام المعلمة  _ProductId_ والمعلمة  _Enabled_  `$false`التي تم تعيينها إلى ، كما هو موضح في المثال التالي.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

لتشغيل أحد الوظائف الإضافية مرة أخرى، قم بتشغيل الأمر cmdlet نفسه مع تعيين المعلمة  _Enabled_ إلى  `$true`.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>إضافة مستخدمين إلى أي من الوظائف الإضافية أو إزالتهم منها

لإضافة مستخدمين ومجموعات إلى واحدة معينة من الوظائف الإضافية، قم بتشغيل **الأمر Cmdlet Set-OrganizationAddInAssignments** باستخدام  _المعلمات ProductId_  _وAdd_ و  _Members_ . افصل عناوين البريد الإلكتروني للأعضاء باستخدام فاصلة. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

لإزالة المستخدمين والمجموعات، قم بتشغيل الأمر cmdlet نفسه باستخدام  _المعلمة Remove_ . 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

لتعيين إضافة إلى جميع المستخدمين على المستأجر، قم بتشغيل الأمر cmdlet نفسه باستخدام المعلمة  _AssignToEveryone_ مع تعيين القيمة إلى  `$true`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

لكي لا يتم تعيين مهمة جديدة للجميع، ثم العودة إلى المستخدمين والمجموعات المعينة مسبقا، يمكنك تشغيل الأمر cmdlet نفسه، ثم إيقاف تشغيل المعلمة  _AssignToEveryone_  `$false`بتعيين قيمتها إلى .
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>تحديث أي من الوظائف الإضافية

لتحديث أحد الوظائف الإضافية من بيان، قم بتشغيل الأمر **Cmdlet Set-OrganizationAddIn** باستخدام المعلمات  _ProductId_ و  _ManifestPath_ و  _Locale_ ، كما هو موضح في المثال التالي. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> سيتم تحديث الوظائف الإضافية التي تم تحميلها Office Store تلقائيا في غضون بضعة أيام من توفر التحديث الأخير على Office Store. 
  
## <a name="delete-an-add-in"></a>حذف أي من الوظائف الإضافية

لحذف أحد الوظائف الإضافية، قم بتشغيل **الأمر cmdlet Remove-OrganizationAddIn** باستخدام المعلمة  _ProductId_ ، كما هو موضح في المثال التالي. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<!--
## Customize Microsoft Store add-ins for your organization

You must customize the add-in before you deploy it to your organization. Add-ins older than version 1.1 are not supported by this feature. 

We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.

Note also the following restrictions:
- All URLs must be absolute (include http or https) and valid.
- *DisplayName* must not exceed 125 characters 
- *DisplayName*, *Resources* and *AppDomains* must not include the following characters: 
 
    - \<
    -  \>
    -  ;
    -  =   

If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.

To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
To customize multiple tags for an add-in, add those tags to the commandline:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> You must apply multiple customized tags to one add-in as one command. If you customize tags one by one, only the last customization will be applied. Additionally, if you customize a tag by mistake, you must remove all customizations and start over.

### Tags you can customize

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| The URL of the image used as the add-in’s icon (in admin center). </br> |
| \<DisplayName>| The title of the add-in  (in admin center).|
| \<Hosts>| List of apps that will support the add-in.|
| \<SourceLocation> | The source URL that the add-in will connect to.| 
| \<AppDomains> | A list of domains that the add-in can connect with. | 
| \<SupportURL>| The URL users can use to access help and support. | 
| \<Resources>  | This tag contains a number of elements including titles, tooltips, and icons of different sizes.| 
|
### Customize Resources tag

Any element in the <Resources> tag of the manifest can be customized dynamically. You first need to check the manifest to find the element id to which you want to assign a new value. The <Resources> tag looks like this:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

You can customize as many elements with the command as you need to.

### Remove customization from an add-in

The only option currently available for deleting customizations is to delete all of them at once:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### View add-in customizations

To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet. If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.  

```powershell
Get-OrganizationAddInOverrides 
```
If ProductId is specified, then a list of overrides applied to that add-in is returned. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### Remove an add-in from local cache

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remive an add-in from cache:

1. Navigate to the “Users” folder in C:\ 
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a>الحصول على تعليمات مفصلة لكل cmdlet

يمكنك النظر في التعليمات المفصلة لكل cmdlet باستخدام الأمر Cmdlet الخاص ب Get-help. على سبيل المثال، يوفر الأمر cmdlet التالي معلومات مفصلة حول Remove-OrganizationAddIn cmdlet.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```
