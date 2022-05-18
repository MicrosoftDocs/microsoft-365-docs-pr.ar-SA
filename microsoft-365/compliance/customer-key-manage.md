---
title: إدارة مفتاح العميل
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: بعد إعداد مفتاح العميل، تعرف على كيفية إدارته عن طريق استعادة مفاتيح AKV، وإدارة الأذونات وإنشاء نهج تشفير البيانات وتعيينها.
ms.openlocfilehash: 0ca6aa1e2cf725359d74477b486a4763a35ba681
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/18/2022
ms.locfileid: "65465899"
---
# <a name="manage-customer-key"></a>إدارة مفتاح العميل

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

بعد إعداد مفتاح العميل، ستحتاج إلى إنشاء نهج تشفير بيانات واحد أو أكثر وتعيينه (DEP). بمجرد تعيين DEPs، يمكنك إدارة مفاتيحك كما هو موضح في هذه المقالة. تعرف على المزيد حول مفتاح العميل في المواضيع ذات الصلة.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>إنشاء DEP للاستخدام مع أحمال عمل متعددة لجميع المستخدمين المستأجرين

قبل البدء، تأكد من إكمال المهام المطلوبة لإعداد مفتاح العميل. للحصول على معلومات، راجع [إعداد مفتاح العميل](customer-key-set-up.md). لإنشاء DEP، تحتاج إلى معرفات الموارد المنتظمة Key Vault التي حصلت عليها أثناء الإعداد. للحصول على معلومات، راجع [الحصول على URI لكل مفتاح Key Vault Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

لإنشاء DEP متعدد حمل العمل، اتبع الخطوات التالية:
  
1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

2. لإنشاء DEP، استخدم New-M365DataAtRestEncryptionPolicy cmdlet.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   المكان:

   - *PolicyName* هو الاسم الذي تريد استخدامه للنهج. لا يمكن أن تحتوي الأسماء على مسافات. على سبيل المثال، Contoso_Global.

   - *KeyVaultURI1* هو URI للمفتاح الأول في النهج. على سبيل المثال، <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* هو URI للمفتاح الثاني في النهج. على سبيل المثال، <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. افصل معرفات الموارد المنتظمة (URIs) عن طريق فاصلة ومساحة.

   - *وصف النهج* هو وصف سهل الاستخدام للنهج الذي سيساعدك على تذكر ما هو النهج من أجله. يمكنك تضمين مسافات في الوصف. على سبيل المثال، "نهج الجذر لأحمال عمل متعددة لكافة المستخدمين في المستأجر".

على سبيل المثال:

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>تعيين نهج حمل عمل متعدد

تعيين DEP باستخدام Set-M365DataAtRestEncryptionPolicyAssignment cmdlet. بمجرد تعيين النهج، يقوم Microsoft 365 بتشفير البيانات باستخدام المفتاح المحدد في DEP.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 حيث *يكون PolicyName* هو اسم النهج. على سبيل المثال، Contoso_Global.

على سبيل المثال:

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>إنشاء DEP للاستخدام مع علب بريد Exchange Online

قبل البدء، تأكد من إكمال المهام المطلوبة لإعداد Azure Key Vault. للحصول على معلومات، راجع [إعداد مفتاح العميل](customer-key-set-up.md). ستكمل هذه الخطوات عن طريق الاتصال عن بعد Exchange Online باستخدام Windows PowerShell.

يقترن DEP بمجموعة من المفاتيح المخزنة في azure Key Vault. يمكنك تعيين DEP إلى علبة بريد في Microsoft 365. ثم سيستخدم Microsoft 365 المفاتيح المحددة في النهج لتشفير علبة البريد. لإنشاء DEP، تحتاج إلى معرفات الموارد المنتظمة Key Vault التي حصلت عليها أثناء الإعداد. للحصول على معلومات، راجع [الحصول على URI لكل مفتاح Key Vault Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

تذكر! عند إنشاء DEP، يمكنك تحديد مفتاحين في اثنين من Azure Key Vaults مختلفة. أنشئ هذه المفاتيح في منطقتين منفصلتين من مناطق Azure لضمان التكرار الجغرافي.

لإنشاء DEP لاستخدامه مع علبة بريد، اتبع الخطوات التالية:
  
1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات مسؤول عام أو مسؤول Exchange Online في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

2. لإنشاء DEP، استخدم أمر cmdlet New-DataEncryptionPolicy بكتابة الأمر التالي.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   المكان:

   - *PolicyName* هو الاسم الذي تريد استخدامه للنهج. لا يمكن أن تحتوي الأسماء على مسافات. على سبيل المثال، USA_mailboxes.

   - *وصف النهج* هو وصف سهل الاستخدام للنهج الذي سيساعدك على تذكر ما هو النهج من أجله. يمكنك تضمين مسافات في الوصف. على سبيل المثال، "المفتاح الجذر لعلب البريد في الولايات المتحدة الأمريكية والمناطق التابعة لها".

   - *KeyVaultURI1* هو URI للمفتاح الأول في النهج. على سبيل المثال، <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* هو URI للمفتاح الثاني في النهج. على سبيل المثال، <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. افصل معرفات الموارد المنتظمة (URIs) عن طريق فاصلة ومساحة.

   على سبيل المثال:
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-DataEncryptionPolicy](/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>تعيين DEP إلى علبة بريد

قم بتعيين DEP إلى علبة بريد باستخدام cmdlet Set-Mailbox. بمجرد تعيين النهج، يمكن Microsoft 365 تشفير علبة البريد باستخدام المفتاح المحدد في DEP.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

حيث تحدد *MailboxIdParameter* علبة بريد مستخدم. لمزيد من المعلومات حول Set-Mailbox cmdlet، راجع ["تعيين علبة البريد](/powershell/module/exchange/set-mailbox)".

في البيئات المختلطة، يمكنك تعيين DEP لبيانات علبة البريد المحلية التي تتم مزامنتها مع مستأجر Exchange Online. لتعيين DEP لبيانات علبة البريد المتزامنة هذه، ستستخدم Set-MailUser cmdlet. لمزيد من المعلومات حول بيانات علبة البريد في البيئة المختلطة، راجع [علب البريد المحلية باستخدام Outlook لنظامي التشغيل iOS وAndroid مع المصادقة الحديثة المختلطة](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

حيث يحدد *MailUserIdParameter* مستخدم بريد (يعرف أيضا باسم مستخدم ممكن للبريد). لمزيد من المعلومات حول Set-MailUser cmdlet، راجع [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>إنشاء DEP للاستخدام مع ملفات SharePoint Online و OneDrive for Business و Teams

قبل البدء، تأكد من إكمال المهام المطلوبة لإعداد Azure Key Vault. للحصول على معلومات، راجع [إعداد مفتاح العميل](customer-key-set-up.md).
  
لإعداد مفتاح العميل لملفات SharePoint Online و OneDrive for Business و Teams، أكمل هذه الخطوات عن طريق الاتصال عن بعد ب SharePoint Online باستخدام Windows PowerShell.
  
يمكنك إقران DEP بمجموعة من المفاتيح المخزنة في Key Vault Azure. يمكنك تطبيق DEP على جميع بياناتك في موقع جغرافي واحد، يسمى أيضا جغرافيا. إذا كنت تستخدم ميزة متعددة المناطق الجغرافية من Office 365، يمكنك إنشاء DEP واحد لكل جغرافيا مع القدرة على استخدام مفاتيح مختلفة لكل جغرافيا. إذا كنت لا تستخدم جغرافيا متعددا، يمكنك إنشاء DEP واحد في مؤسستك لاستخدامه مع ملفات SharePoint Online و OneDrive for Business و Teams. تستخدم Microsoft 365 المفاتيح المحددة في DEP لتشفير بياناتك في تلك المنطقة الجغرافية. لإنشاء DEP، تحتاج إلى معرفات الموارد المنتظمة Key Vault التي حصلت عليها أثناء الإعداد. للحصول على معلومات، راجع [الحصول على URI لكل مفتاح Key Vault Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).
  
تذكر! عند إنشاء DEP، يمكنك تحديد مفتاحين في اثنين من Azure Key Vaults مختلفة. أنشئ هذه المفاتيح في منطقتين منفصلتين من مناطق Azure لضمان التكرار الجغرافي.
  
لإنشاء DEP، تحتاج إلى الاتصال عن بعد SharePoint Online باستخدام Windows PowerShell.
  
1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، [الاتصال إلى SharePoint PowerShell عبر الإنترنت](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. في Microsoft Office SharePoint Online Management Shell، قم بتشغيل Register-SPODataEncryptionPolicy cmdlet كما يلي:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   على سبيل المثال:
  
   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a'
   ```

   عند تسجيل DEP، يبدأ التشفير على البيانات في المنطقة الجغرافية. قد يستغرق التشفير بعض الوقت. لمزيد من المعلومات حول استخدام هذه المعلمة، راجع [Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>عرض DEPs التي أنشأتها لعلب بريد Exchange Online

لعرض قائمة بجميع DEPs التي أنشأتها لعلب البريد، استخدم Get-DataEncryptionPolicy PowerShell cmdlet.

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. لإرجاع جميع DEPs في مؤسستك، قم بتشغيل cmdlet Get-DataEncryptionPolicy دون أي معلمات.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   لمزيد من المعلومات حول Get-DataEncryptionPolicy cmdlet، راجع [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>تعيين DEP قبل ترحيل علبة بريد إلى السحابة

عند تعيين DEP، يقوم Microsoft 365 بتشفير محتويات علبة البريد باستخدام DEP المعين أثناء الترحيل. هذه العملية أكثر كفاءة من ترحيل علبة البريد، وتعيين DEP، ثم انتظار إجراء التشفير، والذي قد يستغرق ساعات أو ربما أياما.

لتعيين DEP إلى علبة بريد قبل ترحيله إلى Office 365، قم بتشغيل Set-MailUser cmdlet في Exchange Online PowerShell:

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-MailUser cmdlet.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   حيث يحدد *GeneralMailboxOrMailUserIdParameter* علبة بريد، ويكون *DataEncryptionPolicyIdParameter* هو معرف DEP. لمزيد من المعلومات حول Set-MailUser cmdlet، راجع [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>تحديد DEP المعين إلى علبة بريد

لتحديد DEP المعين إلى علبة بريد، استخدم Get-MailboxStatistics cmdlet. يقوم cmdlet بإرجاع معرف فريد (GUID).
  
1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   حيث يحدد *GeneralMailboxOrMailUserIdParameter* علبة بريد ويرجع DataEncryptionPolicyID GUID الخاص ب DEP. لمزيد من المعلومات حول Get-MailboxStatistics cmdlet، راجع [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).
  
2. قم بتشغيل Get-DataEncryptionPolicy cmdlet لمعرفة الاسم المألوف ل DEP الذي تم تعيين علبة البريد إليه.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   حيث *GUID* هو GUID الذي تم إرجاعه بواسطة cmdlet Get-MailboxStatistics في الخطوة السابقة.

## <a name="verify-that-customer-key-has-finished-encryption"></a>التحقق من أن مفتاح العميل قد انتهى من التشفير

سواء قمت بطرح مفتاح عميل أو تعيين DEP جديد أو ترحيل علبة بريد، استخدم الخطوات الواردة في هذا القسم لضمان اكتمال التشفير.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>التحقق من اكتمال التشفير لعلب بريد Exchange Online

قد يستغرق تشفير علبة البريد بعض الوقت. للتشفير للمرة الأولى، يجب أيضا نقل علبة البريد بشكل كامل من قاعدة بيانات إلى أخرى قبل أن تتمكن الخدمة من تشفير علبة البريد.
  
استخدم Get-MailboxStatistics cmdlet لتحديد ما إذا كانت علبة البريد مشفرة.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

ترجع الخاصية IsEncrypted قيمة **true** إذا كانت علبة البريد مشفرة وقيمة **خطأ** إذا لم تكن علبة البريد مشفرة. يعتمد وقت إكمال عمليات نقل علبة البريد على عدد علب البريد التي تقوم بتعيين DEP إليها للمرة الأولى، وحجم علب البريد. إذا لم يتم تشفير علب البريد بعد مرور أسبوع من الوقت الذي عينت فيه DEP، فاتصل ب Microsoft.

لم يعد New-MoveRequest cmdlet متوفرا لحركات علبة البريد المحلية. راجع [هذا الإعلان](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) للحصول على معلومات إضافية.

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>التحقق من اكتمال التشفير لملفات SharePoint Online و OneDrive for Business و Teams

تحقق من حالة التشفير عن طريق تشغيل Get-SPODataEncryptionPolicy cmdlet كما يلي:

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

يتضمن الإخراج من أمر cmdlet هذا ما يلي:
  
- URI للمفتاح الأساسي.

- URI للمفتاح الثانوي.

- حالة التشفير جغرافيا. تتضمن الحالات المحتملة ما يلي:

  - **مسجله:** لم يتم بعد تطبيق تشفير مفتاح العميل.

  - **تسجيل:** تم تطبيق تشفير مفتاح العميل والملفات الخاصة بك قيد التشفير. إذا كان مفتاح المنطقة الجغرافية قيد التسجيل، فستظهر لك أيضا معلومات حول النسبة المئوية لاكتمال المواقع في المنطقة الجغرافية بحيث يمكنك مراقبة تقدم التشفير.

  - **المسجله:** تم تطبيق تشفير مفتاح العميل، وتم تشفير جميع الملفات الموجودة في جميع المواقع.

  - **المتداول:** هناك مجموعة مفاتيح قيد التقدم. إذا كان مفتاح المنطقة الجغرافية قيد التشغيل، فستظهر لك أيضا معلومات حول النسبة المئوية للمواقع التي أكملت عملية لفة المفاتيح حتى تتمكن من مراقبة التقدم.

- كما ستعرض النسبة المئوية للمواقع التي تم إلحاقها.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>الحصول على تفاصيل حول DEPs التي تستخدمها مع أحمال عمل متعددة

للحصول على تفاصيل حول جميع DEPs التي أنشأتها لاستخدامها مع أحمال عمل متعددة، أكمل الخطوات التالية:

1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

   - لإرجاع قائمة بكافة برامج DEPs متعددة حمل العمل في المؤسسة، قم بتشغيل هذا الأمر.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - لإرجاع تفاصيل حول DEP معين، قم بتشغيل هذا الأمر. يرجع هذا المثال معلومات مفصلة ل DEP المسمى "Contoso_Global".

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>الحصول على معلومات تعيين DEP متعددة حمل العمل

لمعرفة أي DEP تم تعيينه حاليا إلى المستأجر الخاص بك، اتبع الخطوات التالية. 

1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

2. اكتب هذا الأمر.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>تعطيل DEP متعدد حمل العمل

قبل تعطيل DEP متعدد حمل العمل، قم بإلغاء تعيين DEP من أحمال العمل في المستأجر الخاص بك. لتعطيل DEP مستخدم مع أحمال عمل متعددة، أكمل الخطوات التالية:

1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

2. تشغيل Set-M365DataAtRestEncryptionPolicy cmdlet.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

حيث *يكون PolicyName* هو اسم النهج أو معرفه الفريد. على سبيل المثال، Contoso_Global.

على سبيل المثال:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>استعادة مفاتيح Key Vault Azure

قبل إجراء الاستعادة، استخدم قدرات الاسترداد التي يوفرها الحذف المبدئي. جميع المفاتيح المستخدمة مع مفتاح العميل مطلوبة لتمكين الحذف المبدئي. يعمل الحذف المبدئي مثل سلة المحذوفات ويسمح بالاسترداد لمدة تصل إلى 90 يوما دون الحاجة إلى الاستعادة. يجب أن تكون الاستعادة مطلوبة فقط في ظروف شديدة أو غير عادية، على سبيل المثال إذا فقد المفتاح أو المخزن الرئيسي. إذا كان عليك استعادة مفتاح للاستخدام مع Customer Key، في Azure PowerShell، فشغل Restore-AzureKeyVaultKey cmdlet كما يلي:
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

على سبيل المثال:
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

إذا كان المخزن الرئيسي يحتوي بالفعل على مفتاح بنفس الاسم، تفشل عملية الاستعادة. Restore-AzKeyVaultKey استعادة كافة الإصدارات الرئيسية وكافة بيانات التعريف للمفتاح بما في ذلك اسم المفتاح.
  
## <a name="manage-key-vault-permissions"></a>إدارة أذونات key vault

تتوفر العديد من أوامر cmdlets التي تمكنك من عرض أذونات key vault وإزالتها إذا لزم الأمر. قد تحتاج إلى إزالة الأذونات، على سبيل المثال، عندما يترك أحد الموظفين الفريق. لكل مهمة من هذه المهام، ستستخدم Azure PowerShell. للحصول على معلومات حول Azure PowerShell، راجع [نظرة عامة على Azure PowerShell](/powershell/azure/).

لعرض أذونات key vault، قم بتشغيل Get-AzKeyVault cmdlet.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

على سبيل المثال:

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

لإزالة أذونات المسؤول، قم بتشغيل Remove-AzKeyVaultAccessPolicy cmdlet:
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

على سبيل المثال:

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>العودة من مفتاح العميل إلى المفاتيح المدارة من Microsoft

إذا كنت بحاجة إلى العودة إلى المفاتيح التي تديرها Microsoft، يمكنك ذلك. عند الإلحاق، تتم إعادة تشفير بياناتك باستخدام التشفير الافتراضي المدعوم من قبل كل حمل عمل فردي. على سبيل المثال، يدعم Exchange Online التشفير الافتراضي باستخدام المفاتيح التي تديرها Microsoft.

> [!IMPORTANT]
> إلغاء الإلحاق ليس هو نفسه عملية إزالة البيانات. يؤدي حذف البيانات بشكل دائم إلى حذف بيانات مؤسستك من Microsoft 365، ولا يؤدي إلغاء الإلحاق إلى حذفها. لا يمكنك إجراء إزالة بيانات لنهج حمل عمل متعدد.

إذا قررت عدم استخدام Customer Key لتعيين DEPs متعددة أحمال العمل بعد الآن، فستحتاج إلى التواصل مع دعم Microsoft مع طلب "إلغاء الإلحاق" من Customer Key. اطلب من فريق الدعم تقديم طلب خدمة ضد فريق مفتاح العميل Microsoft Purview. تواصل مع m365-ck@service.microsoft.com إذا كانت لديك أي أسئلة.

إذا لم تعد ترغب في تشفير علب البريد الفردية باستخدام DEPs على مستوى علبة البريد، فيمكنك إلغاء تعيين DEPs على مستوى علبة البريد من كل علب البريد.

لإلغاء تعيين DEPs لعلب البريد، استخدم Set-Mailbox PowerShell cmdlet.

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-Mailbox cmdlet.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

يؤدي تشغيل أمر cmdlet هذا إلى إلغاء تعيين DEP المعين حاليا وإعادة تشفير علبة البريد باستخدام DEP المقترن بالمفاتيح الافتراضية التي تديرها Microsoft. لا يمكنك إلغاء تعيين DEP المستخدم من قبل المفاتيح المدارة من Microsoft. إذا كنت لا تريد استخدام المفاتيح التي تديرها Microsoft، يمكنك تعيين مفتاح عميل آخر DEP إلى علبة البريد.

> [!IMPORTANT]
> لا يتم دعم العودة من مفتاح العميل إلى المفاتيح المدارة من Microsoft للملفات SharePoint Online و OneDrive for Business و Teams. 

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>إبطال المفاتيح وبدء عملية مسار إزالة البيانات

يمكنك التحكم في إبطال كافة مفاتيح الجذر بما في ذلك مفتاح التوفر. يوفر مفتاح العميل التحكم في جانب تخطيط الخروج من المتطلبات التنظيمية لك. إذا قررت إبطال المفاتيح لإزالة البيانات والخروج من الخدمة، فإن الخدمة تحذف مفتاح التوفر بمجرد اكتمال عملية إزالة البيانات. هذا معتمد ل DEPs لمفتاح العميل التي تم تعيينها إلى علب بريد فردية.

Microsoft 365 تدقيق مسار إزالة البيانات والتحقق من صحته. لمزيد من المعلومات، راجع تقرير SSAE 18 SOC 2 المتوفر على [Service Trust Portal](https://servicetrust.microsoft.com/). بالإضافة إلى ذلك، توصي Microsoft بالمستندات التالية:

- [دليل تقييم المخاطر والامتثال للمؤسسات المالية في Microsoft Cloud](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [اعتبارات تخطيط الخروج من O365](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

إزالة DEP متعددة حمل العمل غير معتمدة لمفتاح العميل. يتم استخدام DEP متعدد حمل العمل لتشفير البيانات عبر أحمال عمل متعددة عبر جميع مستخدمي المستأجرين. قد تؤدي إزالة DEP هذه إلى بيانات من خلال أحمال عمل متعددة تصبح غير قابلة للوصول. إذا قررت إنهاء خدمات Microsoft 365 تماما، فيمكنك اتباع مسار حذف المستأجر لكل عملية موثقة. تعرف [على كيفية حذف مستأجر في Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>إبطال "مفاتيح العملاء" ومفتاح التوفر Exchange Online Skype for Business

عند بدء مسار إزالة البيانات Exchange Online Skype for Business، يمكنك تعيين طلب إزالة بيانات دائم على DEP. يؤدي القيام بذلك إلى حذف البيانات المشفرة بشكل دائم داخل علب البريد التي تم تعيين DEP إليها.

نظرا لأنه يمكنك فقط تشغيل PowerShell cmdlet مقابل DEP واحد في كل مرة، ففكر في إعادة تعيين DEP واحد لجميع علب البريد قبل بدء مسار إزالة البيانات.

> [!WARNING]
> لا تستخدم مسار إزالة البيانات لحذف مجموعة فرعية من علب البريد. هذه العملية مخصصة فقط للعملاء الذين يخرجون من الخدمة.

لبدء مسار إزالة البيانات، أكمل الخطوات التالية:

1. إزالة أذونات الالتفاف وإلغاء الالتفاف ل "O365 Exchange Online" من Azure Key Vaults.

2. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه امتيازات المسؤول العمومي في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

3. لكل DEP يحتوي على علب البريد التي تريد حذفها، قم بتشغيل [Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) cmdlet كما يلي.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   إذا فشل الأمر، فتأكد من إزالة أذونات Exchange Online من كلا المفتاحين في Azure Key Vault كما هو محدد سابقا في هذه المهمة. بمجرد تعيين التبديل PermanentDataPurgeRequested باستخدام Set-DataEncryptionPolicy cmdlet، لن تتمكن من تعيين DEP هذا إلى علب البريد.

4. اتصل بدعم Microsoft واطلب eDocument لإزالة البيانات.

    بناء على طلبك، ترسل لك Microsoft مستندا قانونيا للإقرار بحذف البيانات وتخويله. يحتاج الشخص الذي قام بالتسجيل كموافق في عرض FastTrack أثناء الإلحاق إلى توقيع هذا المستند. عادة ما يكون هذا مديرا تنفيذيا أو شخصا آخر معينا في شركتك مخولا بشكل قانوني بالتوقيع على الأوراق نيابة عن مؤسستك.

5. بمجرد توقيع ممثلك للمستند القانوني، قم بإرجاعه إلى Microsoft (عادة من خلال توقيع eDoc).

    بمجرد تلقي Microsoft للمستند القانوني، تقوم Microsoft بتشغيل cmdlets لتشغيل عملية إزالة البيانات التي تحذف النهج أولا، وعلامات علب البريد للحذف الدائم، ثم تحذف مفتاح التوفر. بمجرد اكتمال عملية إزالة البيانات، تمت إزالة البيانات، ولا يمكن الوصول إليها Exchange Online، ولا يمكن استردادها.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>إبطال "مفاتيح العملاء" ومفتاح التوفر لملفات SharePoint Online و OneDrive for Business و Teams

إزالة SharePoint، OneDrive للعمل أو المؤسسة التعليمية، Teams الملفات DEPs غير معتمدة في مفتاح العميل. تستخدم برامج DEPs متعددة حمل العمل هذه لتشفير البيانات عبر أحمال عمل متعددة عبر جميع مستخدمي المستأجرين. سيؤدي إزالة مثل هذا DEP إلى تعذر الوصول إلى البيانات من خلال أحمال عمل متعددة. إذا قررت إنهاء خدمات Microsoft 365 تماما، يمكنك متابعة مسار حذف المستأجر لكل عملية موثقة. تعرف على كيفية [حذف مستأجر في Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).  

## <a name="related-articles"></a>المقالات ذات الصلة

- [تشفير الخدمة باستخدام مفتاح عميل Microsoft Purview](customer-key-overview.md)

- [التعرف على مفتاح التوفر](customer-key-availability-key-understand.md)

- [إعداد مفتاح العميل](customer-key-set-up.md)

- [لف مفتاح عميل أو مفتاح توفر أو تدويره](customer-key-availability-key-roll.md)

- [صندوق تأمين بيانات العملاء](customer-lockbox-requests.md)

- [تشفير الخدمة](office-365-service-encryption.md)
