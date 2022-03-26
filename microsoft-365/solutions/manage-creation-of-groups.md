---
title: إدارة الأشخاص الذين يمكنهم إنشاء Microsoft 365 المجموعات
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
description: تعرف على كيفية التحكم في المستخدمين الذين يمكنهم Microsoft 365 المجموعات.
ms.openlocfilehash: 4280b6859358580547302ccf9497e8cd1e7ed752
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63569557"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>إدارة الأشخاص الذين يمكنهم إنشاء Microsoft 365 المجموعات

بشكل افتراضي، يمكن لجميع المستخدمين إنشاء مجموعات Microsoft 365 المستخدمين. هذا هو النهج الموصى به لأنه يسمح للمستخدمين ببدء التعاون دون الحاجة إلى المساعدة من تقنية المعلومات.

إذا تطلب عملك تقييد الأشخاص الذين يمكنهم إنشاء مجموعات، يمكنك تقييد Microsoft 365 المجموعات لأعضاء مجموعة معينة Microsoft 365 مجموعة أو مجموعة أمان.

إذا كنت قلقا بشأن إنشاء المستخدمين لفرق أو مجموعات لا تتوافق مع معايير العمل، فنظر في مطالبة المستخدمين لإكمال دورة تدريبية ثم إضافتهم إلى مجموعة المستخدمين المسموح بهم.

عند تحديد الأشخاص الذين يمكنهم إنشاء مجموعة، يؤثر ذلك على كل الخدمات التي تعتمد على المجموعات للوصول إليها، بما في ذلك:

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planner
- Power BI (كلاسيكي)
- Project ويب / المخطط

لن تمنع الخطوات في هذه المقالة أعضاء أدوار معينة من إنشاء المجموعات. Office 365 يمكن للمسؤولين العامين إنشاء المجموعات عبر مركز مسؤولي Microsoft 365 و Planner Exchange و SharePoint Online. يمكن لأدوار أخرى إنشاء مجموعات عبر وسائل محدودة، مدرجة أدناه.

- Exchange المسؤول: Exchange إدارة Azure AD
- دعم من المستوى 1 الشريك: مركز مسؤولي Microsoft 365، Exchange إدارة، Azure AD
- دعم من المستوى 2 الشريك: مركز مسؤولي Microsoft 365، Exchange إدارة، Azure AD
- كتاب الدليل: Azure AD
- SharePoint: SharePoint إدارة Azure AD
- Teams الخدمة: Teams إدارة Azure AD
- مسؤول المستخدم: مركز مسؤولي Microsoft 365، Azure AD

إذا كنت عضوا في أحد هذه الأدوار، يمكنك إنشاء مجموعات Microsoft 365 للمستخدمين المقيدين، ثم تعيين المستخدم كمالك المجموعة.

## <a name="licensing-requirements"></a>متطلبات الترخيص

لإدارة الأشخاص الذين ينشئون المجموعات، يحتاج الأشخاص التاليون إلى تعيين تراخيص Azure AD Premium لهم:

- المسؤول الذي قام بتكوين إعدادات إنشاء المجموعة هذه
- أعضاء المجموعة المسموح لهم بإنشاء مجموعات

> [!NOTE]
> راجع [تعيين تراخيص أو إزالتها في مدخل Azure Active Directory](/azure/active-directory/fundamentals/license-users-groups) للحصول على مزيد من التفاصيل حول كيفية تعيين تراخيص Azure.

لا يحتاج الأشخاص التاليون إلى تراخيص Azure AD Premium تعيينها لهم:

- الأشخاص الذين هم أعضاء Microsoft 365 المجموعات وليس لديهم القدرة على إنشاء مجموعات أخرى.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>الخطوة 1: إنشاء مجموعة للمستخدمين الذين يحتاجون إلى إنشاء مجموعات Microsoft 365

يمكن استخدام مجموعة واحدة فقط في مؤسستك للتحكم في الأشخاص القادرين على إنشاء المجموعات. ولكن، يمكنك تداخل المجموعات الأخرى كأعضاء في هذه المجموعة.

لا يحتاج المسؤولون في الأدوار المذكورة أعلاه إلى أن يكونوا أعضاء في هذه المجموعة: حيث يحتفظون بقدرتهم على إنشاء مجموعات.

1. في مركز الإدارة، انتقل إلى [صفحة المجموعات](https://admin.microsoft.com/adminportal/home#/groups).

2. انقر فوق **إضافة مجموعة**.

3. اختر نوع المجموعة الذي تريده. تذكر اسم المجموعة! ستحتاج إليها لاحقا.

4. قم بالانتهاء من إعداد المجموعة، وإضافة الأشخاص أو المجموعات الأخرى التي تريد أن تكون قادرة على إنشاء مجموعات في المؤسسة.

للحصول على إرشادات مفصلة، راجع [إنشاء مجموعة أمان أو تحريرها أو حذفها في](../admin/email/create-edit-or-delete-a-security-group.md) مركز مسؤولي Microsoft 365.

## <a name="step-2-run-powershell-commands"></a>الخطوة 2: تشغيل أوامر PowerShell

يجب استخدام إصدار المعاينة من [Azure Active Directory PowerShell ل Graph (AzureAD) (](/powershell/azure/active-directory/install-adv2)اسم الوحدة النمطية **AzureADPreview**) لتغيير إعداد وصول الضيف على مستوى المجموعة:

- إذا لم تقم بتثبيت أي إصدار من وحدة Azure AD PowerShell النمطية من قبل، فشاهد تثبيت وحدة [Azure AD النمطية](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) واتبع الإرشادات لتثبيت إصدار المعاينة العامة.

- إذا كان لديك إصدار التوفر العام 2.0 من وحدة Azure AD PowerShell النمطية (AzureAD)، `Uninstall-Module AzureAD` فيجب إلغاء تثبيته عن طريق تشغيله في جلسة PowerShell، ثم تثبيت إصدار المعاينة عن طريق تشغيل `Install-Module AzureADPreview`.

- إذا قمت بتثبيت إصدار المعاينة بالفعل، فتأكد `Install-Module AzureADPreview` من أنه أحدث إصدار من هذه الوحدة النمطية.

انسخ البرنامج النصي أدناه إلى محرر نص، مثل المفكرة أو Windows PowerShell [ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

استبدل *\<GroupName\>* باسم المجموعة التي أنشأتها. على سبيل المثال:

`$GroupName = "Group Creators"`

احفظ الملف GroupCreators.ps1.

في نافذة PowerShell، انتقل إلى الموقع حيث حفظت الملف (اكتب "CD \<FileLocation\>").

تشغيل البرنامج النصي بالكتابة:

`.\GroupCreators.ps1`

سجل [الدخول باستخدام حساب المسؤول عند](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) مطالبتك بذلك.

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

![لقطة شاشة إخراج البرنامج النصي من PowerShell.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

إذا كنت تريد تغيير المجموعة التي يتم استخدامها في المستقبل، يمكنك إعادة تشغيل البرنامج النصي باسم المجموعة الجديدة.

إذا كنت تريد إيقاف تشغيل تقييد إنشاء المجموعة والسماح مرة أخرى لجميع المستخدمين بإنشاء مجموعات، فحدد $GroupName إلى "" $AllowGroupCreation إلى "True" ثم إعادة تشغيل البرنامج النصي.

## <a name="step-3-verify-that-it-works"></a>الخطوة 3: التحقق من عملها

قد تستغرق التغييرات 30 دقيقة أو أكثر لكي يتم إدخالها حيز التنفيذ. يمكنك التحقق من الإعدادات الجديدة عبر القيام بما يلي:

1. سجل الدخول Microsoft 365 حساب مستخدم لشخص لا يجب أن يكون لديه القدرة على إنشاء مجموعات. وهذا يعني أنه ليس عضوا في المجموعة التي أنشأتها أو مسؤولا.

2. حدد لوحة **Planner** .

3. في Planner، حدد **خطة جديدة** في التنقل الأيسر لإنشاء خطة.

4. يجب أن تظهر رسالة تعلمك بتعطيل الخطة وإنشاء المجموعة.

جرب الإجراء نفسه مرة أخرى مع أحد أعضاء المجموعة.

> [!NOTE]
> إذا لم يتمكن أعضاء المجموعة من إنشاء مجموعات، فتحقق من عدم حظرهم من خلال نهج [علبة بريد OWA](/powershell/module/exchange/set-owamailboxpolicy).

## <a name="related-topics"></a>المواضيع ذات الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md)

[بدء العمل مع Office 365 PowerShell](../enterprise/getting-started-with-microsoft-365-powershell.md)

[إعداد إدارة مجموعة الخدمة الذاتية في Azure Active Directory](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Cmdlets في Azure Active Directory لتكوين إعدادات المجموعة](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
