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
ms.openlocfilehash: 4b9ebc6366934db52c30d51091ac9991ff82d8c3
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570052"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>منع إضافة ضيوف إلى مجموعة Microsoft 365 أو فريق Microsoft Teams معين

إذا كنت تريد السماح للضيوف بالوصول إلى معظم المجموعات والفرق، ولكن لديك بعض المواقع التي تريد منع وصول الضيوف إليها، يمكنك حظر وصول الضيف للمجموعات والفرق الفردية. (يتم حظر وصول الضيف إلى فريق عن طريق حظر وصول الضيف إلى المجموعة المقترنة.) يمنع ذلك إضافة ضيوف جدد، ولكنه لا يزيل الضيوف ضيوفا موجودين بالفعل في المجموعة أو الفريق.

إذا كنت تستخدم تسميات الحساسية في مؤسستك، نوصي باستخدامها للتحكم في وصول الضيف على أساس كل مجموعة. للحصول على معلومات حول كيفية القيام بذلك، استخدم تسميات الحساسية لحماية المحتوى في Microsoft Teams Microsoft 365 والمجموعات [SharePoint المواقع](../compliance/sensitivity-labels-teams-groups-sites.md). هذا هو النهج الموصى به.

## <a name="change-group-settings-using-microsoft-powershell"></a>تغيير إعدادات المجموعة باستخدام Microsoft PowerShell

يمكنك أيضا منع إضافة ضيوف جدد إلى مجموعات فردية باستخدام PowerShell. (تذكر أن موقع الفريق المقترن SharePoint عناصر [تحكم مشاركة ضيوف منفصلة](/sharepoint/change-external-sharing-site).)

يجب استخدام إصدار المعاينة من [Azure Active Directory PowerShell ل Graph](/powershell/azure/active-directory/install-adv2) (اسم الوحدة النمطية **AzureADPreview**) لتغيير إعداد وصول الضيف على مستوى المجموعة:

- إذا لم تقم بتثبيت أي إصدار من وحدة Azure AD PowerShell النمطية من قبل، فشاهد تثبيت وحدة [Azure AD النمطية](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) واتبع الإرشادات لتثبيت إصدار المعاينة العامة.

- إذا كان لديك إصدار التوفر العام 2.0 من وحدة Azure AD PowerShell النمطية (AzureAD)، `Uninstall-Module AzureAD` فيجب إلغاء تثبيته عن طريق تشغيله في جلسة PowerShell، ثم تثبيت إصدار المعاينة عن طريق تشغيل `Install-Module AzureADPreview`.

- إذا قمت بتثبيت إصدار المعاينة بالفعل، فتأكد `Install-Module AzureADPreview` من أنه أحدث إصدار من هذه الوحدة النمطية.

> [!NOTE]
> يجب أن يكون لديك حقوق المسؤول العام لتشغيل هذه الأوامر. 

تشغيل البرنامج النصي التالي، مع *\<GroupName\>* التغيير إلى اسم المجموعة التي تريد حظر وصول الضيف إليها.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

للتحقق من الإعدادات، يمكنك تشغيل هذا الأمر:

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

يبدو التحقق كما يلي:
    
![لقطة شاشة من نافذة PowerShell تظهر تعيين الوصول إلى مجموعة الضيوف إلى خطأ.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

إذا كنت ترغب ```<GroupName>``` في تبديل الإعداد مرة أخرى للسماح للضيوف بالوصول إلى مجموعة معينة، فدير البرنامج النصي التالي، واتغير إلى اسم المجموعة حيث تريد السماح بالوصول إلى الضيف.

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

يمكنك السماح للضيوف الذين يستخدمون مجالا معينا أو حظرهم. على سبيل المثال، إذا كانت شركتك (Contoso) لديها شراكة مع شركة أخرى (Fabrikam)، يمكنك إضافة Fabrikam إلى قائمة السماح الخاصة بك حتى يمكن للمستخدمين إضافة هؤلاء الضيوف إلى مجموعاتهم.

لمزيد من المعلومات، راجع السماح بدعوات لمستخدمي [B2B أو حظرها من مؤسسات معينة](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>إضافة ضيوف إلى قائمة العنوان العام

بشكل افتراضي، لا يكون الضيوف مرئيين في Exchange العنوان العام. استخدم الخطوات المذكورة أدناه لجعل الضيف مرئيا في قائمة العنوان العام.

ابحث عن ObjectID الخاص بالضيف عن طريق تشغيل:

```PowerShell
Get-AzureADUser -Filter "userType eq 'Guest'"
```

ثم قم بتشغيل ما يلي باستخدام القيم المناسبة ل ObjectID و GivenName و Surname و DisplayName و TelephoneNumber.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>المواضيع ذات الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md)

[إدارة عضوية المجموعة في مركز مسؤولي Microsoft 365](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[مراجعات الوصول إلى Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
