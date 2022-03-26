---
title: إدارة Microsoft 365 باستخدام PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: في هذه المقالة، تعرف على كيفية تنفيذ مهام الإدارة الشائعة Microsoft 365 في PowerShell.
ms.openlocfilehash: 460444e1cb2f862f4d96ed6aad0178a146864658
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63568950"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>إدارة Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

توفر هذه المقالة الخطوات اللازمة للقيام بمهام الإدارة الشائعة للمجموعات في Microsoft PowerShell. كما تسرد أيضا قوائم PowerShell cmdlets للمجموعات. للحصول على معلومات حول إدارة SharePoint، راجع إدارة SharePoint [عبر الإنترنت باستخدام PowerShell](/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>الارتباط إلى إرشادات استخدام Microsoft 365 المجموعات

عندما يقوم [المستخدمون بإنشاء مجموعة أو تحريرها](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx) في Outlook، يمكنك إظهار ارتباط إلى إرشادات استخدام مؤسستك. على سبيل المثال، إذا كنت بحاجة إلى إضافة بديهة أو لاحقة معينة إلى اسم مجموعة.

استخدم Azure Active Directory (Azure AD) PowerShell لتأشير المستخدمين إلى إرشادات استخدام مؤسستك Microsoft 365 المجموعات. اطلع على [Cmdlets Azure Active Directory](/azure/active-directory/enterprise-users/groups-settings-cmdlets) لتكوين إعدادات المجموعة واتبع الخطوات في إنشاء إعدادات على مستوى الدليل  لتحديد الارتباط التشعبي إرشادات الاستخدام. بمجرد تشغيل AAD (دليل Azure النشط) cmdlet، سيشاهد المستخدمون الارتباط إلى إرشاداتك عند إنشاء مجموعة أو تحريرها في Outlook.

![إنشاء مجموعة جديدة باستخدام ارتباط إرشادات الاستخدام.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![انقر فوق إرشادات استخدام المجموعة للاطلاع على إرشادات المجموعات Office 365 الخاصة بك.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>السماح للمستخدمين بإرسال كمجموعة Microsoft 365

إذا كنت تريد تمكين Microsoft 365 "إرسال باسم"، فاستخدم [الأمرين Cmdlets Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) و [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission) لتكوين هذا الأمر. بعد تمكين هذا الإعداد Microsoft 365 يمكن لمستخدمي المجموعة استخدام Outlook أو Outlook على ويب لإرسال البريد الإلكتروني والرد عليه كمجموعة Microsoft 365. يمكن للمستخدمين الانتقال إلى المجموعة وإنشاء بريد إلكتروني جديد وتغيير الحقل "إرسال باسم" إلى عنوان البريد الإلكتروني للمجموعة.

([يمكنك أيضا القيام بذلك في مركز](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group) إدارة Exchange).)

استخدم البرنامج النصي التالي، *\<GroupAlias\>* *\<UserAlias\>* مع استبداله باسم المجموعة المستعار الذي تريد تحديثه، والاسم المستعار للمستخدم الذي تريد منح الأذونات له. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) لتشغيل هذا البرنامج النصي.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

بمجرد تنفيذ أمر cmdlet، يمكن للمستخدمين الانتقال إلى Outlook أو Outlook على ويب لإرسالها كمجموعة، عن طريق إضافة عنوان البريد الإلكتروني للمجموعة إلى **الحقل من**.

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>إنشاء تصنيفات Microsoft 365 المجموعات في مؤسستك

يمكنك إنشاء تسميات الحساسية التي يمكن للمستخدمين في مؤسستك تعيينها عند إنشاء Microsoft 365 المجموعة. إذا كنت تريد تصنيف المجموعات، نوصي باستخدام تسميات الحساسية بدلا من ميزة تصنيف المجموعات السابقة. للحصول على معلومات حول استخدام تسميات الحساسية، راجع استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع [SharePoint ويب](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> إذا كنت تستخدم حاليا تسميات التصنيف، فإنها لن تكون متوفرة للمستخدمين الذين ينشئون مجموعات بمجرد تمكين تسميات الحساسية.

لا يزال بإمكانك استخدام ميزة تصنيف المجموعات السابقة. يمكنك إنشاء تصنيفات يمكن للمستخدمين في مؤسستك تعيينها عند إنشاء Microsoft 365 المجموعة. على سبيل المثال، يمكنك السماح للمستخدمين بتعيين "قياسي" و"سري" و"سري للغاية" على المجموعات التي ينشئونها. لا يتم تعيين تصنيفات المجموعات بشكل افتراضي، وأنت بحاجة إلى إنشائها لكي يقوم المستخدمون بتعيينها. استخدم Azure Active Directory PowerShell لتأشير المستخدمين إلى إرشادات استخدام مؤسستك Microsoft 365 المجموعات.

اطلع على [Cmdlets Azure Active Directory](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) لتكوين إعدادات المجموعة واتبع الخطوات في إنشاء إعدادات على مستوى الدليل  لتحديد تصنيف Microsoft 365 المجموعات.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

من أجل إقران وصف بكل تصنيف، يمكنك استخدام سمة  *الإعدادات ClassificationDescriptions* لتعريفها.

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

حيث يتطابق التصنيف مع السلاسل في "قائمة التصنيف".

على سبيل المثال:

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

بعد تشغيل الأمر cmdlet أعلاه Azure Active Directory لتعيين تصنيفك، قم بتشغيل الأمر [cmdlet Set-UnifiedGroup](/powershell/module/exchange/Set-UnifiedGroup) إذا كنت تريد تعيين التصنيف لمجموعة معينة.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

أو أنشئ مجموعة جديدة ذات تصنيف.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

اطلع على [استخدام PowerShell](/powershell/exchange/exchange-online-powershell) مع Exchange Online الاتصال Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على مزيد من التفاصيل حول Exchange Online PowerShell.

بعد تمكين هذه الإعدادات، سيكون مالك المجموعة قادرا على اختيار تصنيف من القائمة المنسدلة في Outlook على الويب Outlook، وحفظه من صفحة المجموعة تحرير.

![اختر Microsoft 365 تصنيف المجموعة.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>إخفاء Microsoft 365 من قائمة العنوان العام.

يمكنك تحديد ما إذا كانت Microsoft 365 المجموعة تظهر في قائمة العنوان العام (GAL) والقوائم الأخرى في مؤسستك. على سبيل المثال، إذا كان لديك مجموعة قسم قانوني لا تريد ظهورها في قائمة العنوان، يمكنك منع ظهور هذه المجموعة في GAL. تشغيل الأمر Set-Unified Cmdlet الخاص بالمجموعة لإخفاء المجموعة من قائمة العنوان كما يلي:

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>السماح للمستخدمين الداخليين فقط بإرسال رسالة إلى Microsoft 365 المجموعات

إذا كنت لا تريد أن يرسل المستخدمون من مؤسسات أخرى رسائل بريد إلكتروني إلى مجموعة Microsoft 365، يمكنك تغيير الإعدادات الخاصة بهذه المجموعة. سيسمح للمستخدمين الداخليين فقط بإرسال بريد إلكتروني إلى المجموعة. إذا حاول مستخدم خارجي إرسال رسالة إلى تلك المجموعة، سيتم رفضها.

قم بتشغيل Set-UnifiedGroup cmdlet لتحديث هذا الإعداد، كما يلي:

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>إضافة MailTips إلى Microsoft 365 المجموعات

كلما حاول مرسل إرسال رسالة بريد إلكتروني إلى مجموعة Microsoft 365، يمكن عرض MailTip له.

قم بتشغيل Set-Unified cmdlet الخاص ب "مجموعة" لإضافة mailTip إلى المجموعة:

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

إلى جانب MailTip، يمكنك أيضا تعيين MailTipTranslations، التي تحدد لغات أخرى ل MailTip. لنفترض أنك تريد الحصول على الترجمة الأسبانية، ثم قم بتشغيل الأمر التالي:

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>تغيير اسم العرض لمجموعة Microsoft 365

يحدد اسم العرض اسم مجموعة Microsoft 365. يمكنك رؤية هذا الاسم في مركز إدارة Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">أو</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365.</a> يمكنك تحرير اسم العرض للمجموعة أو تعيين اسم عرض إلى مجموعة Microsoft 365 عن طريق تشغيل الأمر Set-UnifiedGroup:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>تغيير الإعداد الافتراضي Microsoft 365 مجموعات Outlook إلى عامة أو خاصة

Microsoft 365 المجموعات Outlook يتم إنشاؤها ك "خاصة" بشكل افتراضي. إذا كانت مؤسستك Microsoft 365 إنشاء مجموعات ك "عامة" بشكل افتراضي (أو الرجوع إلى "خاصة")، فاستخدم بناء جملة الأمر cmdlet هذا في PowerShell:

 `Set-OrganizationConfig -DefaultGroupAccessType Public`

لتعيين إلى خاص:

 `Set-OrganizationConfig -DefaultGroupAccessType Private`

للتحقق من الإعداد:

 `Get-OrganizationConfig | ft DefaultGroupAccessType`

لمعرفة المزيد، راجع [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) و [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>Microsoft 365 cmdlets الخاصة بالمجموعات

يمكن استخدام cmdlets التالية مع Microsoft 365 المجموعات.

|**اسم Cmdlet**|**الوصف**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |استخدم الأمر cmdlet هذا للبحث عن Microsoft 365 مجموعات موجودة، ول عرض خصائص كائن المجموعة  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |تحديث خصائص مجموعة Microsoft 365 معينة  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |إنشاء مجموعة Microsoft 365 جديدة. يوفر cmdlet هذا مجموعة قليلة من المعلمات. لتعيين قيم للخصائص الموسعة، استخدم Set-UnifiedGroup بعد إنشاء المجموعة الجديدة  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |حذف مجموعة Microsoft 365 موجودة  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |استرداد معلومات العضوية ومالك مجموعة Microsoft 365  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |إضافة أعضاء ومالاك ومشتركين إلى مجموعة Microsoft 365 موجودة <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |إزالة المالكين والأعضاء من مجموعة Microsoft 365 موجودة  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |يتم استخدامها لعرض معلومات حول صورة المستخدم المقترنة مع حساب. يتم تخزين صور المستخدمين في Active Directory  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |يستخدم هذا الاقتران لاقران صورة مستخدم مع حساب. يتم تخزين صور المستخدمين في Active Directory  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |إزالة الصورة لمجموعة Microsoft 365  <br/> |

## <a name="related-topics"></a>المواضيع ذات الصلة

[ترقية قوائم التوزيع Microsoft 365 المجموعات](/office365/admin/manage/upgrade-distribution-lists)

[إدارة الأشخاص الذين يمكنهم إنشاء Microsoft 365 المجموعات](/office365/admin/create-groups/manage-creation-of-groups)

[إدارة وصول الضيف إلى Microsoft 365 المجموعات](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[تغيير عضوية المجموعة الثابتة إلى عضوية ديناميكية في](/azure/active-directory/users-groups-roles/groups-change-type)
