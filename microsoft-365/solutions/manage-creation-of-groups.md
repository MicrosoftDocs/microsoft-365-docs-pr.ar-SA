---
title: إدارة الأشخاص الذين يمكنهم إنشاء مجموعات Microsoft 365
f1.keywords: NOCSH
ms.author: mikeplum
ms.reviewer: arvaradh
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 4c46c8cb-17d0-44b5-9776-005fced8e618
recommendations: false
description: تعرف على كيفية التحكم في المستخدمين الذين يمكنهم إنشاء مجموعات Microsoft 365.
ms.openlocfilehash: 2136fbf51912e00b7552e687282d4a80688dcd9e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493032"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>إدارة الأشخاص الذين يمكنهم إنشاء مجموعات Microsoft 365

بشكل افتراضي، يمكن لجميع المستخدمين إنشاء مجموعات Microsoft 365. هذا هو النهج الموصى به لأنه يسمح للمستخدمين بالبدء في التعاون دون الحاجة إلى مساعدة من تكنولوجيا المعلومات.

إذا تطلب عملك تقييد الأشخاص الذين يمكنهم إنشاء مجموعات، فيمكنك تقييد إنشاء مجموعات Microsoft 365 لأعضاء مجموعة Microsoft 365 معينة أو مجموعة أمان معينة.

إذا كنت قلقا بشأن المستخدمين الذين ينشئون فرقا أو مجموعات لا تتوافق مع معايير عملك، ففكر في مطالبة المستخدمين بإكمال دورة تدريبية ثم إضافتهم إلى مجموعة المستخدمين المسموح لهم.

عندما تحدد الأشخاص الذين يمكنهم إنشاء مجموعة، يؤثر ذلك على جميع الخدمات التي تعتمد على المجموعات للوصول، بما في ذلك:

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planner
- Power BI (كلاسيكي)
- Project للويب / المخطط

لن تمنع الخطوات الواردة في هذه المقالة أعضاء أدوار معينة من إنشاء مجموعات. يمكن لمسؤولي Microsoft 365 العموميين إنشاء مجموعات عبر مركز مسؤولي Microsoft 365 و Planner وExchange وSharePoint، ولكن ليس مواقع أخرى مثل Teams. يمكن لأدوار أخرى إنشاء مجموعات Microsoft 365 عبر وسائل محدودة، مدرجة أدناه.

- مسؤول Exchange: مركز إدارة Exchange، Azure AD
- دعم الشريك من المستوى 1: مركز مسؤولي Microsoft 365 ومركز إدارة Exchange Azure AD
- دعم الشريك من المستوى 2: مركز مسؤولي Microsoft 365 ومركز إدارة Exchange Azure AD
- كتاب الدليل: Azure AD
- مسؤول SharePoint: مركز إدارة SharePoint، Azure AD
- مسؤول خدمة Teams: مركز إدارة Teams، Azure AD
- مسؤول المستخدم: مركز مسؤولي Microsoft 365، Azure AD

إذا كنت عضوا في أحد هذه الأدوار، يمكنك إنشاء مجموعات Microsoft 365 للمستخدمين المقيدين، ثم تعيين المستخدم كمالك للمجموعة.

## <a name="licensing-requirements"></a>متطلبات الترخيص

لإدارة من يقوم بإنشاء المجموعات، يحتاج الأشخاص التاليون Azure AD تراخيص Premium أو Azure AD تراخيص EDU الأساسية المعينة لهم:

- المسؤول الذي يقوم بتكوين إعدادات إنشاء المجموعة هذه
- أعضاء المجموعة المسموح لهم بإنشاء مجموعات

> [!NOTE]
> راجع [تعيين التراخيص أو إزالتها في مدخل Microsoft Azure Active Directory](/azure/active-directory/fundamentals/license-users-groups) للحصول على مزيد من التفاصيل حول كيفية تعيين تراخيص Azure.

لا يحتاج الأشخاص التاليون Azure AD تراخيص Premium أو Azure AD Basic EDU المعينة لهم:

- الأشخاص الأعضاء في مجموعات Microsoft 365 والذين ليس لديهم القدرة على إنشاء مجموعات أخرى.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>الخطوة 1: إنشاء مجموعة للمستخدمين الذين يحتاجون إلى إنشاء مجموعات Microsoft 365

يمكن استخدام مجموعة واحدة فقط في مؤسستك للتحكم في من يمكنه إنشاء مجموعات Microsoft 365. ولكن، يمكنك تداخل مجموعات أخرى كأعضاء في هذه المجموعة.

لا يحتاج المسؤولون في الأدوار المذكورة أعلاه إلى أن يكونوا أعضاء في هذه المجموعة: فهم يحتفظون بقدرتهم على إنشاء مجموعات.

1. في مركز الإدارة، انتقل إلى [صفحة المجموعات](https://admin.microsoft.com/adminportal/home#/groups).

2. انقر فوق **"إضافة مجموعة**".

3. اختر نوع المجموعة الذي تريده. تذكر اسم المجموعة! ستحتاج إليها لاحقا.

4. قم بإنهاء إعداد المجموعة، وإضافة أشخاص أو مجموعات أخرى تريد تمكينهم من إنشاء مجموعات كأعضاء (وليس مالكين).

للحصول على إرشادات مفصلة، راجع [إنشاء مجموعة أمان أو تحريرها أو حذفها في مركز مسؤولي Microsoft 365](../admin/email/create-edit-or-delete-a-security-group.md).

## <a name="step-2-run-powershell-commands"></a>الخطوة 2: تشغيل أوامر PowerShell

يجب استخدام إصدار المعاينة من [Azure Active Directory PowerShell ل Graph (AzureAD)](/powershell/azure/active-directory/install-adv2) (اسم الوحدة النمطية **AzureADPreview**) لتغيير إعداد وصول الضيف على مستوى المجموعة:

- إذا لم تكن قد قمت بتثبيت أي إصدار من الوحدة النمطية Azure AD PowerShell من قبل، فراجع [تثبيت الوحدة النمطية Azure AD واتبع](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) الإرشادات لتثبيت إصدار المعاينة العامة.

- إذا كان لديك إصدار التوفر العام 2.0 للوحدة النمطية Azure AD PowerShell (AzureAD)، يجب إلغاء تثبيته عن طريق تشغيله `Uninstall-Module AzureAD` في جلسة عمل PowerShell، ثم تثبيت إصدار المعاينة عن طريق تشغيل `Install-Module AzureADPreview`.

- إذا قمت بالفعل بتثبيت إصدار المعاينة، فقم بتشغيله `Update-Module AzureADPreview` للتأكد من أنه أحدث إصدار من هذه الوحدة النمطية.

انسخ البرنامج النصي أدناه إلى محرر نص، مثل المفكرة، أو [Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

استبدل *\<GroupName\>* باسم المجموعة التي قمت بإنشائها. على سبيل المثال:

`$GroupName = "Group Creators"`

احفظ الملف GroupCreators.ps1.

في نافذة PowerShell، انتقل إلى الموقع حيث قمت بحفظ الملف (اكتب "CD \<FileLocation\>").

تشغيل البرنامج النصي عن طريق كتابة:

`.\GroupCreators.ps1`

[وسجل الدخول باستخدام حساب المسؤول](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) عند المطالبة.

```PowerShell
$GroupName = "<GroupName>"
$AllowGroupCreation = $False

Connect-AzureAD

$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
if(!$settingsObjectID)
{
    $template = Get-AzureADDirectorySettingTemplate | Where-object {$_.displayname -eq "group.unified"}
    $settingsCopy = $template.CreateDirectorySetting()
    New-AzureADDirectorySetting -DirectorySetting $settingsCopy
    $settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
}

$settingsCopy = Get-AzureADDirectorySetting -Id $settingsObjectID
$settingsCopy["EnableGroupCreation"] = $AllowGroupCreation

if($GroupName)
{
  $settingsCopy["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString $GroupName).objectid
} else {
$settingsCopy["GroupCreationAllowedGroupId"] = $GroupName
}
Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values
```

سيعرض السطر الأخير من البرنامج النصي الإعدادات المحدثة:

![لقطة شاشة لإخراج البرنامج النصي PowerShell.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

إذا كنت تريد في المستقبل تغيير المجموعة المستخدمة، يمكنك إعادة تشغيل البرنامج النصي باسم المجموعة الجديدة.

إذا كنت تريد إيقاف تشغيل تقييد إنشاء المجموعة والسماح مرة أخرى لكافة المستخدمين بإنشاء مجموعات، فقم بتعيين $GroupName إلى "" $AllowGroupCreation إلى "صواب" ثم أعد تشغيل البرنامج النصي.

## <a name="step-3-verify-that-it-works"></a>الخطوة 3: التحقق من عملها

قد تستغرق التغييرات 30 دقيقة أو أكثر لتدخل حيز التنفيذ. يمكنك التحقق من الإعدادات الجديدة من خلال القيام بما يلي:

1. سجل الدخول إلى Microsoft 365 باستخدام حساب مستخدم لشخص لا يجب أن يكون لديه القدرة على إنشاء مجموعات. أي أنها ليست عضوا في المجموعة التي أنشأتها أو المسؤول.

2. حدد لوحة **Planner** .

3. في Planner، حدد **"خطة جديدة** " في جزء التنقل الأيمن لإنشاء خطة.

4. يجب أن تتلقى رسالة تفيد بتعطيل إنشاء الخطة والمجموعة.

حاول الإجراء نفسه مرة أخرى مع عضو في المجموعة.

> [!NOTE]
> إذا لم يتمكن أعضاء المجموعة من إنشاء مجموعات، فتحقق من عدم حظرهم من خلال [نهج علبة بريد OWA](/powershell/module/exchange/set-owamailboxpolicy).

## <a name="related-topics"></a>المواضيع ذات الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md)

[بدء استخدام Office 365 PowerShell](../enterprise/getting-started-with-microsoft-365-powershell.md)

[إعداد إدارة مجموعة الخدمة الذاتية في Azure Active Directory](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[أوامر cmdlets Azure Active Directory لتكوين إعدادات المجموعة](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
