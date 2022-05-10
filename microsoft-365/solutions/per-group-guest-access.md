---
title: منع إضافة الضيوف إلى مجموعة معينة
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: تعرف على كيفية منع إضافة الضيوف إلى مجموعة معينة
ms.openlocfilehash: f050011427ceeeff8347c2acd5b6d3fbbcf11bec
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285303"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>منع إضافة الضيوف إلى مجموعة Microsoft 365 معينة أو فريق Microsoft Teams معين

إذا كنت تريد السماح بوصول الضيف إلى معظم المجموعات والفرق، ولكن في مكان ما تريد منع وصول الضيف، يمكنك حظر وصول الضيف للمجموعات والفرق الفردية. (يتم حظر وصول الضيف إلى فريق عن طريق حظر وصول الضيف إلى المجموعة المقترنة.) يؤدي ذلك إلى منع إضافة ضيوف جدد ولكنه لا يزيل الضيوف الأشخاص مقيمين بالفعل في المجموعة أو الفريق.

إذا كنت تستخدم أوصاف الحساسية في مؤسستك، نوصي باستخدامها للتحكم في وصول الضيف على أساس كل مجموعة. للحصول على معلومات حول كيفية القيام بذلك، [استخدم تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md). هذا هو النهج الموصى به.

## <a name="change-group-settings-using-microsoft-powershell"></a>تغيير إعدادات المجموعة باستخدام Microsoft PowerShell

يمكنك أيضا منع إضافة ضيوف جدد إلى مجموعات فردية باستخدام PowerShell. (تذكر أن موقع SharePoint المقترن بالفريق يحتوي على [عناصر تحكم منفصلة لمشاركة الضيف](/sharepoint/change-external-sharing-site).)

يجب استخدام إصدار المعاينة من [Azure Active Directory PowerShell Graph](/powershell/azure/active-directory/install-adv2) (اسم الوحدة النمطية **AzureADPreview**) لتغيير إعداد الوصول إلى الضيف على مستوى المجموعة:

- إذا لم تكن قد قمت بتثبيت أي إصدار من الوحدة النمطية Azure AD PowerShell من قبل، فراجع [تثبيت الوحدة النمطية Azure AD واتبع](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) الإرشادات لتثبيت إصدار المعاينة العامة.

- إذا كان لديك إصدار التوفر العام 2.0 للوحدة النمطية Azure AD PowerShell (AzureAD)، يجب إلغاء تثبيته عن طريق تشغيله `Uninstall-Module AzureAD` في جلسة عمل PowerShell، ثم تثبيت إصدار المعاينة عن طريق تشغيل `Install-Module AzureADPreview`.

- إذا قمت بالفعل بتثبيت إصدار المعاينة، فقم بتشغيله `Install-Module AzureADPreview` للتأكد من أنه أحدث إصدار من هذه الوحدة النمطية.

> [!NOTE]
> يجب أن يكون لديك حقوق المسؤول العمومي لتشغيل هذه الأوامر. 

قم بتشغيل البرنامج النصي التالي، مع التغيير *\<GroupName\>* إلى اسم المجموعة حيث تريد حظر وصول الضيف.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

للتحقق من الإعدادات، قم بتشغيل هذا الأمر:

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

يبدو التحقق كما يلي:
    
![لقطة شاشة لنافذة PowerShell تظهر أنه تم تعيين وصول مجموعة الضيف إلى false.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

إذا كنت ترغب في إعادة تبديل الإعداد للسماح بوصول الضيف إلى مجموعة معينة، فشغل البرنامج النصي التالي، مع التغيير ```<GroupName>``` إلى اسم المجموعة حيث تريد السماح بوصول الضيف.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$True
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
$id = (get-AzureADObjectSetting -TargetType groups -TargetObjectId $groupID).id
Set-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy -id $id
```

## <a name="allow-or-block-guest-access-based-on-their-domain"></a>السماح بالوصول إلى الضيف أو حظره استنادا إلى مجاله

يمكنك السماح للضيوف الذين يستخدمون مجالا معينا أو حظرهم. على سبيل المثال، إذا كانت شركتك (Contoso) لديها شراكة مع شركة أخرى (Fabrikam)، يمكنك إضافة Fabrikam إلى قائمة السماح الخاصة بك حتى يتمكن المستخدمون من إضافة هؤلاء الضيوف إلى مجموعاتهم.

لمزيد من المعلومات، راجع [السماح بالدعوات أو حظرها لمستخدمي B2B من مؤسسات معينة](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>إضافة ضيوف إلى قائمة العناوين العمومية

بشكل افتراضي، لا يكون الضيوف مرئيين في قائمة العناوين العمومية Exchange. استخدم الخطوات المذكورة أدناه لجعل الضيف مرئيا في قائمة العناوين العمومية.

ابحث عن ObjectID الخاص بالضيف عن طريق تشغيل:

```PowerShell
get-AzureADUser -all $true | ?{$_.CreationType -eq "Invitation"}
```

ثم قم بتشغيل ما يلي باستخدام القيم المناسبة ل ObjectID و GivenName و Surname و DisplayName و TelephoneNumber.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>المواضيع ذات الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md)

[إدارة عضوية المجموعة في مركز مسؤولي Microsoft 365](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[مراجعات صلاحية الوصول إلى Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
