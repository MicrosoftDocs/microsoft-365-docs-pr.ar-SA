---
title: إدارة مجموعات Microsoft 365 باستخدام PowerShell
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
description: في هذه المقالة، تعرف على كيفية تنفيذ مهام الإدارة الشائعة لمجموعات Microsoft 365 في PowerShell.
ms.openlocfilehash: 407e242728bf37ebf8c11b8094bfa4931229e4ef
ms.sourcegitcommit: 3226bdf213b290ec5262670873c3a75f17b66ddd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65372192"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>إدارة مجموعات Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

توفر هذه المقالة الخطوات اللازمة للقيام بمهام الإدارة الشائعة للمجموعات في Microsoft PowerShell. كما يسرد أوامر PowerShell cmdlets للمجموعات. للحصول على معلومات حول إدارة مواقع SharePoint، راجع [إدارة مواقع SharePoint Online باستخدام PowerShell](/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>الارتباط بإرشادات استخدام مجموعات Microsoft 365

عندما يقوم المستخدمون [بإنشاء مجموعة أو تحريرها في Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)، يمكنك إظهار ارتباط إلى إرشادات استخدام مؤسستك. على سبيل المثال، إذا كنت بحاجة إلى إضافة بادئة أو لاحقة معينة إلى اسم مجموعة.

استخدم Azure Active Directory (Azure AD) PowerShell لتوجيه المستخدمين إلى إرشادات استخدام مؤسستك لمجموعات Microsoft 365. تحقق من [أوامر cmdlets Azure Active Directory لتكوين إعدادات المجموعة واتبع الخطوات](/azure/active-directory/enterprise-users/groups-settings-cmdlets) الواردة في **إعدادات الإنشاء على مستوى الدليل** لتحديد الارتباط التشعبي لإرشادات الاستخدام. بمجرد تشغيل AAD cmdlet، سيرى المستخدمون الارتباط إلى إرشاداتك عند إنشاء مجموعة أو تحريرها في Outlook.

![إنشاء مجموعة جديدة باستخدام ارتباط إرشادات الاستخدام.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![انقر فوق إرشادات استخدام المجموعة للاطلاع على إرشادات مجموعات Office 365 المؤسسات.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>السماح للمستخدمين بالإرسال كمجموعة Microsoft 365

إذا كنت تريد تمكين مجموعات Microsoft 365 الخاصة بك من "إرسال باسم"، فاستخدم [cmdlets Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) و [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission) لتكوين هذا. بمجرد تمكين هذا الإعداد، يمكن لمستخدمي المجموعة Microsoft 365 استخدام Outlook أو Outlook على ويب لإرسال البريد الإلكتروني والرد عليه كمجموعة Microsoft 365. يمكن للمستخدمين الانتقال إلى المجموعة وإنشاء بريد إلكتروني جديد وتغيير الحقل "إرسال باسم" إلى عنوان البريد الإلكتروني الخاص بالمجموعة.

([يمكنك أيضا القيام بذلك في مركز إدارة Exchange](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)

استخدم البرنامج النصي التالي، مع استبداله *\<GroupAlias\>* بالاسم المستعار للمجموعة التي تريد تحديثها، وباسم *\<UserAlias\>* المستخدم المستعار الذي تريد منحه الأذونات. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) لتشغيل هذا البرنامج النصي.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

بمجرد تنفيذ cmdlet، يمكن للمستخدمين الانتقال إلى Outlook أو Outlook على ويب لإرسالها كمجموعة، عن طريق إضافة عنوان البريد الإلكتروني للمجموعة إلى الحقل **"من**".

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>إنشاء تصنيفات مجموعات Microsoft 365 في مؤسستك

يمكنك إنشاء تسميات الحساسية التي يمكن للمستخدمين في مؤسستك تعيينها عند إنشاء مجموعة Microsoft 365. إذا كنت ترغب في تصنيف المجموعات، نوصي باستخدام تسميات الحساسية بدلا من ميزة تصنيف المجموعات السابقة. للحصول على معلومات حول استخدام أوصاف الحساسية، راجع [استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> إذا كنت تستخدم حاليا تسميات التصنيف، فلن تكون متوفرة للمستخدمين الذين ينشئون مجموعات بمجرد تمكين تسميات الحساسية.

لا يزال بإمكانك استخدام ميزة تصنيف المجموعات السابقة. يمكنك إنشاء تصنيفات يمكن للمستخدمين في مؤسستك تعيينها عند إنشاء مجموعة Microsoft 365. على سبيل المثال، يمكنك السماح للمستخدمين بتعيين "قياسي" و"سري" و"سري للغاية" على المجموعات التي يقومون بإنشائها. لا يتم تعيين تصنيفات المجموعات بشكل افتراضي وتحتاج إلى إنشائها لكي يقوم المستخدمون بتعيينها. استخدم Azure Active Directory PowerShell لتوجيه المستخدمين إلى إرشادات استخدام مؤسستك مجموعات Microsoft 365.

تحقق من [أوامر cmdlets Azure Active Directory لتكوين إعدادات المجموعة واتبع الخطوات](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) الواردة في **إعدادات الإنشاء على مستوى الدليل** لتعريف التصنيف مجموعات Microsoft 365.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

من أجل إقران وصف بكل تصنيف، يمكنك استخدام سمات الإعدادات  *ClassificationDescriptions* لتعريفها.

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

حيث يطابق التصنيف السلاسل في ClassificationList.

على سبيل المثال:

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

بعد تشغيل Cmdlet Azure Active Directory أعلاه لتعيين التصنيف الخاص بك، قم بتشغيل [Set-UnifiedGroup](/powershell/module/exchange/Set-UnifiedGroup) cmdlet إذا كنت تريد تعيين التصنيف لمجموعة معينة.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

أو أنشئ مجموعة جديدة مع تصنيف.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

اطلع على [استخدام PowerShell مع Exchange Online](/powershell/exchange/exchange-online-powershell) [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على مزيد من التفاصيل حول استخدام Exchange Online PowerShell.

بمجرد تمكين هذه الإعدادات، سيتمكن مالك المجموعة من اختيار تصنيف من القائمة المنسدلة في Outlook على ويب Outlook، وحفظه من صفحة المجموعة **"تحرير**".

![اختر تصنيف مجموعة Microsoft 365.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>إخفاء مجموعات Microsoft 365 من قائمة العناوين العمومية.

يمكنك تحديد ما إذا كانت مجموعة Microsoft 365 تظهر في قائمة العناوين العمومية (GAL) والقوائم الأخرى في مؤسستك. على سبيل المثال، إذا كانت لديك مجموعة قسم قانوني لا تريد إظهارها في قائمة العناوين، يمكنك إيقاف ظهور هذه المجموعة في قائمة العناوين العمومية. قم بتشغيل أمر cmdlet الخاص بمجموعة Set-Unified لإخفاء المجموعة من قائمة العناوين كما يلي:

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>السماح للمستخدمين الداخليين فقط بإرسال رسالة إلى مجموعات Microsoft 365

إذا كنت لا تريد أن يرسل المستخدمون من المؤسسات الأخرى رسائل بريد إلكتروني إلى مجموعة Microsoft 365، فيمكنك تغيير إعدادات هذه المجموعة. سيسمح فقط للمستخدمين الداخليين بإرسال بريد إلكتروني إلى مجموعتك. إذا حاول مستخدم خارجي إرسال رسالة إلى تلك المجموعة، فسيتم رفضها.

قم بتشغيل Set-UnifiedGroup cmdlet لتحديث هذا الإعداد، مثل هذا:

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>إضافة MailTips إلى مجموعات Microsoft 365

كلما حاول مرسل إرسال بريد إلكتروني إلى مجموعة Microsoft 365، يمكن عرض تلميح بريد له.

قم بتشغيل cmdlet لمجموعة Set-Unified لإضافة تلميح بريد إلى المجموعة:

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

إلى جانب MailTip، يمكنك أيضا تعيين MailTipTranslations التي تحدد لغات أخرى ل MailTip. لنفترض أنك تريد الحصول على الترجمة الإسبانية، ثم قم بتشغيل الأمر التالي:

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>تغيير اسم العرض لمجموعة Microsoft 365

يحدد اسم العرض اسم مجموعة Microsoft 365. يمكنك رؤية هذا الاسم في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> أو <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>. يمكنك تحرير اسم عرض المجموعة أو تعيين اسم عرض إلى مجموعة Microsoft 365 موجودة عن طريق تشغيل الأمر Set-UnifiedGroup:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>تغيير الإعداد الافتراضي مجموعات Microsoft 365 ل Outlook إلى عام أو خاص

يتم إنشاء مجموعات Microsoft 365 في Outlook كخاص بشكل افتراضي. إذا كانت مؤسستك تريد إنشاء مجموعات Microsoft 365 ك "عام" بشكل افتراضي (أو العودة إلى "خاص")، فاستخدم بناء جملة PowerShell cmdlet هذا:

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Public
 ```

لتعيين إلى خاص:

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Private
 ```

للتحقق من الإعداد:

 ```powershell
 Get-OrganizationConfig | ft DefaultGroupAccessType
 ```

لمعرفة المزيد، راجع [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) و [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>مجموعات Microsoft 365 cmdlets

يمكن استخدام cmdlets التالية مع مجموعات Microsoft 365.

|**اسم Cmdlet**|**الوصف**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |استخدم أمر cmdlet هذا للبحث عن مجموعات Microsoft 365 الموجودة، ولعرض خصائص كائن المجموعة  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |تحديث خصائص مجموعة Microsoft 365 معينة  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |إنشاء مجموعة Microsoft 365 جديدة. يوفر cmdlet هذا الحد الأدنى من مجموعة المعلمات. لتعيين قيم للخصائص الموسعة، استخدم Set-UnifiedGroup بعد إنشاء المجموعة الجديدة  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |حذف مجموعة Microsoft 365 موجودة  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |استرداد معلومات العضوية والمالك لمجموعة Microsoft 365  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |إضافة أعضاء ومالكين ومشتركين إلى مجموعة Microsoft 365 موجودة <br/> |
|[إزالة ارتباطات المجموعات الموحدة](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |إزالة المالكين والأعضاء من مجموعة Microsoft 365 موجودة  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |يستخدم لعرض معلومات حول صورة المستخدم المقترنة بحساب. يتم تخزين صور المستخدم في Active Directory  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |يستخدم لإقران صورة مستخدم بحساب. يتم تخزين صور المستخدم في Active Directory  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |إزالة الصورة لمجموعة Microsoft 365  <br/> |

## <a name="related-topics"></a>المواضيع ذات الصلة

[ترقية قوائم التوزيع إلى مجموعات Microsoft 365](/office365/admin/manage/upgrade-distribution-lists)

[إدارة الأشخاص الذين يمكنهم إنشاء مجموعات Microsoft 365](/office365/admin/create-groups/manage-creation-of-groups)

[إدارة وصول الضيف إلى مجموعات Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[تغيير عضوية المجموعة الثابتة إلى ديناميكية في](/azure/active-directory/users-groups-roles/groups-change-type)
