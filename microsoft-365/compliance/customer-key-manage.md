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
description: بعد إعداد "مفتاح العميل"، تعرف على كيفية إدارته من خلال استعادة مفاتيح AKV وإدارة الأذونات وإنشاء سياسات تشفير البيانات وتعيينها.
ms.openlocfilehash: 9dd333064c9fa121f8f1c99ffcd048f6b977dbf2
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63566780"
---
# <a name="manage-customer-key"></a>إدارة مفتاح العميل

بعد إعداد "مفتاح العميل" Office 365، ستحتاج إلى إنشاء واحد أو أكثر من سياسات تشفير البيانات وتعيينها (DEP). بعد تعيين DEPs، يمكنك إدارة المفاتيح كما هو موضح في هذه المقالة. تعرف على المزيد حول "مفتاح العميل" في المواضيع ذات الصلة.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>إنشاء DEP للاستخدام مع أحمال عمل متعددة لجميع المستخدمين المستأجرين

قبل البدء، تأكد من أنك أكملت المهام المطلوبة لإعداد العميل. للحصول على معلومات، راجع [إعداد مفتاح العميل](customer-key-set-up.md). لإنشاء DEP، تحتاج إلى URIs المخزن الرئيسي التي حصلت عليها أثناء الإعداد. للحصول على معلومات، راجع [الحصول على URI لكل مفتاح مخزن مفاتيح Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

لإنشاء DEP متعدد حمل العمل، اتبع الخطوات التالية:
  
1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، قم [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

2. لإنشاء DEP، استخدم New-M365DataAtRestEncryptionPolicy cmdlet.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   المكان:

   - *اسم النهج* هو الاسم الذي تريد استخدامه النهج. لا يمكن أن تحتوي الأسماء على مسافات. على سبيل المثال، Contoso_Global.

   - *KeyVaultURI1* هو URI للمفتاح الأول في النهج. على سبيل المثال، <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* هو URI للمفتاح الثاني في النهج. على سبيل المثال، <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. افصل بين URIs بواسطة فاصلة وم مسافة.

   - *وصف النهج* هو وصف سهل الاستخدام لهذا النهج سيساعدك على تذكر ما هو النهج. يمكنك تضمين مسافات في الوصف. على سبيل المثال، "النهج الجذر لأحمال العمل المتعددة لجميع المستخدمين في المستأجر".

على سبيل المثال:

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>تعيين نهج حمل العمل المتعدد

قم بتعيين DEP باستخدام Set-M365DataAtRestEncryptionPolicyAssignment cmdlet. بمجرد تعيين النهج، Microsoft 365 تشفير البيانات باستخدام المفتاح المعرف في DEP.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 حيث *يكون اسم* النهج هو اسم النهج. على سبيل المثال، Contoso_Global.

على سبيل المثال:

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>إنشاء DEP للاستخدام مع علب Exchange Online البريد

قبل البدء، تأكد من أنك أكملت المهام المطلوبة لإعداد مخزن مفاتيح Azure. للحصول على معلومات، راجع [إعداد مفتاح العميل](customer-key-set-up.md). ستكمل هذه الخطوات عن طريق الاتصال عن بعد Exchange Online باستخدام Windows PowerShell.

يقترن DEP مع مجموعة من المفاتيح المخزنة في مخزن مفاتيح Azure. يمكنك تعيين DEP إلى علبة بريد في Microsoft 365. Microsoft 365 بعد ذلك استخدام المفاتيح المحددة في النهج لتشفير علبة البريد. لإنشاء DEP، تحتاج إلى URIs المخزن الرئيسي التي حصلت عليها أثناء الإعداد. للحصول على معلومات، راجع [الحصول على URI لكل مفتاح مخزن مفاتيح Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

تذكر! عند إنشاء DEP، يمكنك تحديد مفتاحين في مخزنين مختلفين لمفاتيح Azure. أنشئ هذه المفاتيح في منطقتين Azure منفصلتين لضمان التكرار الجغرافي.

لإنشاء DEP لاستخدامه مع علبة بريد، اتبع الخطوات التالية:
  
1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه Exchange Online مسؤول عام في مؤسستك، اتصل ب [PowerShell Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في Windows PowerShell نافذة.

2. لإنشاء DEP، استخدم New-DataEncryptionPolicy cmdlet بكتابة الأمر التالي.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   المكان:

   - *اسم النهج* هو الاسم الذي تريد استخدامه النهج. لا يمكن أن تحتوي الأسماء على مسافات. على سبيل المثال، USA_mailboxes.

   - *وصف النهج* هو وصف سهل الاستخدام لهذا النهج سيساعدك على تذكر ما هو النهج. يمكنك تضمين مسافات في الوصف. على سبيل المثال، "المفتاح الجذر لعلب البريد في الولايات المتحدة الأمريكية وأراضيها".

   - *KeyVaultURI1* هو URI للمفتاح الأول في النهج. على سبيل المثال، <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* هو URI للمفتاح الثاني في النهج. على سبيل المثال، <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. افصل بين URIs بواسطة فاصلة وم مسافة.

   على سبيل المثال:
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-DataEncryptionPolicy](/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>تعيين DEP إلى علبة بريد

قم بتعيين DEP إلى علبة بريد باستخدام Set-Mailbox cmdlet. بمجرد تعيين النهج، Microsoft 365 تشفير علبة البريد باستخدام المفتاح المعرف في DEP.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

حيث *يحدد MailboxIdParameter* علبة بريد مستخدم. لمزيد من المعلومات حول Set-Mailbox cmdlet، راجع [تعيين علبة البريد](/powershell/module/exchange/set-mailbox).

في البيئات المختلطة، يمكنك تعيين DEP إلى بيانات علبة البريد المحلية التي يتم مزامنتها مع Exchange Online المستأجر. لتعيين DEP لبيانات علبة البريد المتزامنة هذه، سوف تستخدم Set-MailUser cmdlet. لمزيد من المعلومات حول بيانات علب البريد في البيئة المختلطة، راجع علب البريد المحلية باستخدام Outlook [لنظامي التشغيل iOS وAndroid مع المصادقة الحديثة المختلطة](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

حيث *يحدد MailUserIdParameter* مستخدم بريد (يعرف أيضا بمستخدم ممكن للبريد). لمزيد من المعلومات حول Set-MailUser cmdlet، راجع [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>إنشاء DEP للاستخدام مع ملفات SharePoint Online OneDrive for Business و Teams الإنترنت

قبل البدء، تأكد من أنك أكملت المهام المطلوبة لإعداد مخزن مفاتيح Azure. للحصول على معلومات، راجع [إعداد مفتاح العميل](customer-key-set-up.md).
  
لإعداد "مفتاح العميل" SharePoint عبر OneDrive for Business و Teams، يمكنك إكمال هذه الخطوات عن طريق الاتصال عن بعد SharePoint عبر الإنترنت Windows PowerShell.
  
تقوم بربط DEP مع مجموعة من المفاتيح المخزنة في مخزن مفاتيح Azure. يمكنك تطبيق DEP على كل بياناتك في موقع جغرافي واحد، يسمى أيضا جغرافيا. إذا كنت تستخدم ميزة الجغرافيا Office 365، يمكنك إنشاء DEP واحد لكل جغرافي مع إمكانية استخدام مفاتيح مختلفة لكل جغرافي. إذا لم تكن تستخدم الموقع الجغرافي المتعدد، يمكنك إنشاء DEP واحد في مؤسستك لاستخدامه مع ملفات SharePoint و OneDrive for Business و Teams أخرى. Microsoft 365 المفاتيح المحددة في DEP لتشفير البيانات في ذلك الموقع الجغرافي. لإنشاء DEP، تحتاج إلى URIs المخزن الرئيسي التي حصلت عليها أثناء الإعداد. للحصول على معلومات، راجع [الحصول على URI لكل مفتاح مخزن مفاتيح Azure](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).
  
تذكر! عند إنشاء DEP، يمكنك تحديد مفتاحين في مخزنين مختلفين لمفاتيح Azure. أنشئ هذه المفاتيح في منطقتين Azure منفصلتين لضمان التكرار الجغرافي.
  
لإنشاء DEP، تحتاج إلى الاتصال عن بعد SharePoint Online باستخدام Windows PowerShell.
  
1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، الاتصال إلى SharePoint [Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. في Microsoft Office SharePoint Online Management Shell، Register-SPODataEncryptionPolicy cmdlet كما يلي:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   على سبيل المثال:
  
   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a’
   ```

   عند تسجيل DEP، يبدأ التشفير على البيانات الموجودة في الموقع الجغرافي. قد يستغرق التشفير بعض الوقت. لمزيد من المعلومات حول استخدام هذه المعلمة، راجع [Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>عرض DEPs التي أنشأتها لعلب بريد Exchange Online البريد

لعرض قائمة بجميع DEPs التي أنشأتها لعلب البريد، استخدم الأمر Get-DataEncryptionPolicy PowerShell cmdlet.

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، اتصل [ب PowerShell Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. لإرجاع كل DEPs في مؤسستك، Get-DataEncryptionPolicy cmdlet بدون أي معلمات.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   لمزيد من المعلومات حول Get-DataEncryptionPolicy cmdlet، راجع [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>تعيين DEP قبل ترحيل علبة بريد إلى السحابة

عند تعيين DEP، Microsoft 365 تشفير محتويات علبة البريد باستخدام DEP المعين أثناء الترحيل. إن هذه العملية أكثر فعالية من عملية إعادة توارث علبة البريد وتعيين DEP ثم انتظار التشفير الذي قد يستغرق ساعات أو ربما أياما.

لتعيين DEP إلى علبة بريد قبل ترحيلها إلى Office 365، قم بتشغيل Set-MailUser cmdlet في Exchange Online PowerShell:

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، اتصل [ب PowerShell Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-MailUser cmdlet.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   حيث *يحدد GeneralMailboxOrMailUserIdParameter* علبة بريد، و *DataEncryptionPolicyIdParameter* هو الم ID الخاص ب DEP. لمزيد من المعلومات حول Set-MailUser cmdlet، راجع [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>تحديد DEP المعين إلى علبة بريد

لتحديد DEP المعين إلى علبة بريد، استخدم Get-MailboxStatistics cmdlet. يرجع cmdlet معرفا فريدا (GUID).
  
1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، اتصل [ب PowerShell Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   حيث *يحدد GeneralMailboxOrMailUserIdParameter* علبة بريد ويرجع DataEncryptionPolicyID GUID الخاص ب DEP. لمزيد من المعلومات حول Get-MailboxStatistics cmdlet، راجع [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).
  
2. قم بتشغيل Get-DataEncryptionPolicy cmdlet لمعرفة اسم DEP الذي تم تعيين علبة البريد له.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   حيث *GUID* هو GUID الذي تم إرجاعه بواسطة Get-MailboxStatistics cmdlet في الخطوة السابقة.

## <a name="verify-that-customer-key-has-finished-encryption"></a>التحقق من انتهاء "مفتاح العميل" من التشفير

سواء قمت بلف مفتاح عميل أو تعيين DEP جديد أو ترحيل علبة بريد، استخدم الخطوات الواردة في هذا القسم للتأكد من اكتمال التشفير.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>التحقق من اكتمال التشفير لعلب Exchange Online البريد

قد يستغرق تشفير علبة البريد بعض الوقت. بالنسبة للتشفير للمرة الأولى، يجب أيضا أن تنتقل علبة البريد بشكل كامل من قاعدة بيانات إلى أخرى قبل أن تتمكن الخدمة من تشفير علبة البريد.
  
استخدم Get-MailboxStatistics cmdlet لتحديد ما إذا كانت علبة البريد مشفرة.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

ترجع الخاصية IsEncrypted قيمة true إذا  كانت علبة البريد مشفرة وقيمة false إذا لم  تكن علبة البريد مشفرة. يتوقف وقت إكمال نقل علب البريد على عدد علب البريد التي تقوم بتعيين DEP لها للمرة الأولى، وحجم علب البريد. إذا لم يتم تشفير علب البريد بعد مرور أسبوع من الوقت الذي عينت فيه DEP، فاتصل ب Microsoft.

لم يعد New-MoveRequest cmdlet متوفرا لحركات علب البريد المحلية. راجع هذا [الإعلان](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) للحصول على معلومات إضافية.

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>التحقق من اكتمال التشفير لملفات SharePoint عبر الإنترنت OneDrive for Business والتشفير Teams الإنترنت

تحقق من حالة التشفير عن طريق تشغيل Get-SPODataEncryptionPolicy cmdlet كما يلي:

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

يتضمن الإخراج من cmdlet هذا:
  
- URI للمفتاح الأساسي.

- URI للمفتاح الثانوي.

- حالة تشفير الموقع الجغرافي. تتضمن الولايات المحتملة:

  - **غير مسجل:** لم يتم تطبيق تشفير "مفتاح العميل" بعد.

  - **التسجيل:** تم تطبيق تشفير "مفتاح العميل" وكانت ملفاتك في عملية تشفير. إذا كان مفتاح الموقع الجغرافي مسجلا، سيتم أيضا عرض معلومات حول النسبة المئوية للمواقع المكتملة في الموقع الجغرافي بحيث يمكنك مراقبة تقدم التشفير.

  - **مسجل:** تم تطبيق تشفير "مفتاح العميل"، كما تم تشفير جميع الملفات الموجودة في كل المواقع.

  - **المتداول:** هناك لفة مفاتيح في تقدم. إذا كان مفتاح الموقع الجغرافي متداولا، فسوف تظهر لك أيضا معلومات حول النسبة المئوية للمواقع التي أكملت عملية لفة المفاتيح حتى تتمكن من مراقبة التقدم.

- سيخرج أيضا النسبة المئوية للمواقع التي تم ا متنها.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>الحصول على تفاصيل حول DEPs التي تستخدمها مع أحمال عمل متعددة

للحصول على تفاصيل حول كل DEPs التي أنشأتها لاستخدامها مع أحمال عمل متعددة، أكمل الخطوات التالية:

1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، قم [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

   - لإرجاع قائمة بجميع DEPs متعددة حمل العمل في المؤسسة، تشغيل هذا الأمر.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - لإرجاع تفاصيل حول DEP معين، تشغيل هذا الأمر. يرجع هذا المثال معلومات تفصيلية ل DEP المسماة "Contoso_Global".

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>الحصول على معلومات تعيين DEP متعددة حمل العمل

لمعرفة DEP المعين حاليا للمستأجر، اتبع الخطوات التالية. 

1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، قم [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

2. اكتب هذا الأمر.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>تعطيل DEP متعدد حمل العمل

قبل تعطيل DEP متعدد حمل العمل، قم ب إلغاء تعيين DEP من أحمال العمل في المستأجر. لتعطيل DEP مستخدم مع أحمال عمل متعددة، أكمل الخطوات التالية:

1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، قم [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

2. تشغيل Set-M365DataAtRestEncryptionPolicy cmdlet.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

حيث *يكون اسم* النهج هو اسم النهج أو الم ID الفريد له. على سبيل المثال، Contoso_Global.

على سبيل المثال:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>استعادة مفاتيح مخزن مفاتيح Azure

قبل تنفيذ عملية استعادة، استخدم إمكانات الاسترداد المتوفرة بواسطة الحذف الناعم. كل المفاتيح المستخدمة مع "مفتاح العميل" مطلوبة لتمكين الحذف الناعم. يعمل الحذف الناعم مثل سلة معاد تدويره ويسمح باسترداده لمدة تصل إلى 90 يوما دون الحاجة إلى الاستعادة. يجب أن تكون الاستعادة مطلوبة فقط في الظروف القصوى أو غير العادية، على سبيل المثال إذا تم فقدان مخزن المفتاح أو المفتاح. إذا كان عليك استعادة مفتاح لاستخدامه مع "مفتاح العميل"، في Azure PowerShell، فدير Restore-AzureKeyVaultKey cmdlet كما يلي:
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

على سبيل المثال:
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

إذا كان مخزن المفاتيح يحتوي بالفعل على مفتاح بالاسم نفسه، تفشل عملية الاستعادة. Restore-AzKeyVaultKey استعادة كل الإصدارات الرئيسية وكل بيانات التعريف للمفتاح بما في ذلك اسم المفتاح.
  
## <a name="manage-key-vault-permissions"></a>إدارة أذونات المخزن الرئيسي

تتوفر العديد من cmdlets التي تمكنك من عرض أذونات المخزن الرئيسي وإزالتها، إذا لزم الأمر. قد تحتاج إلى إزالة الأذونات، على سبيل المثال، عندما يترك أحد الموظفين الفريق. لكل من هذه المهام، سوف تستخدم Azure PowerShell. للحصول على معلومات حول Azure PowerShell، راجع [نظرة عامة حول Azure PowerShell](/powershell/azure/).

لعرض أذونات المخزن الرئيسية، يمكنك تشغيل Get-AzKeyVault cmdlet.

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

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>العودة من "مفتاح العميل" إلى المفاتيح المدارة من Microsoft

إذا كنت بحاجة إلى العودة إلى المفاتيح المدارة من Microsoft، يمكنك ذلك. عند إيقاف التشغيل، يتم إعادة تشفير بياناتك باستخدام التشفير الافتراضي المدعوم من كل حمل عمل فردي. على سبيل المثال، Exchange Online يدعم التشفير الافتراضي باستخدام المفاتيح المدارة من Microsoft.

> [!IMPORTANT]
> لا يتشابه إيقاف التشغيل مع عملية إزالة البيانات. تعمل عملية إزالة البيانات بشكل دائم على حذف بيانات مؤسستك من Microsoft 365، ولا يتم حذفها. لا يمكنك تنفيذ عملية إزالة بيانات لن نهج حمل عمل متعدد.

إذا قررت عدم استخدام "مفتاح العميل" لتعيين برامج DEPS متعددة حمل العمل بعد الآن، ستحتاج إلى التواصل مع دعم Microsoft بطلب "إيقاف التشغيل" من "مفتاح العميل". اطلب من فريق الدعم تقديم طلب خدمة Microsoft 365 "مفتاح العميل". يمكنك التواصل m365-ck@service.microsoft.com إذا كانت لديك أي أسئلة.

إذا كنت لا تريد تشفير علب البريد الفردية باستخدام DEPs على مستوى علبة البريد بعد الآن، يمكنك إلغاء تعيين DEPS على مستوى علبة البريد من كل علب البريد.

إلغاء تعيين مكتبات DEPS لعلبة البريد، استخدم Set-Mailbox Cmdlet في PowerShell.

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، اتصل [ب PowerShell Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-Mailbox cmdlet.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

يعمل تشغيل الأمر cmdlet هذا على فك تعيين DEP المعين حاليا ويعاد تشفير علبة البريد باستخدام DEP المقترن بالمفاتيح الافتراضية المدارة من Microsoft. لا يمكنك إعادة تعيين DEP المستخدم بواسطة مفاتيح Microsoft المدارة. إذا كنت لا تريد استخدام مفاتيح مدارة من Microsoft، يمكنك تعيين DEP مفتاح عميل آخر إلى علبة البريد.

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>إبطال المفاتيح وبدء عملية مسار إزالة البيانات

يمكنك التحكم في إلغاء كل المفاتيح الجذر بما في ذلك مفتاح التوفر. يوفر "مفتاح العميل" التحكم في جانب تخطيط الخروج من المتطلبات التنظيمية لك. إذا قررت إبطال المفاتيح لإلغاء بياناتك والخروج من الخدمة، فإن الخدمة تحذف مفتاح التوفر بمجرد اكتمال عملية إزالة البيانات. هذا معتمد ل DEPs "مفتاح العميل" التي تم تعيينها إلى علب بريد فردية.

Microsoft 365 التدقيق والتحقق من صحة مسار إزالة البيانات. لمزيد من المعلومات، راجع تقرير SSAE 18 SOC 2 المتوفر على [Service Trust Portal](https://servicetrust.microsoft.com/). بالإضافة إلى ذلك، توصي Microsoft ب المستندات التالية:

- [دليل تقييم المخاطر والتوافق للمؤسسات المالية في Microsoft Cloud](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [اعتبارات تخطيط الخروج من O365](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

لا يتم دعم إزالة DEP متعددة حمل العمل Microsoft 365 العميل. يتم استخدام DEP متعدد حمل العمل لتشفير البيانات عبر أحمال عمل متعددة عبر جميع المستخدمين المستأجرين. قد يؤدي إزالة DEP هذا إلى الوصول إلى بيانات من أحمال عمل متعددة. إذا قررت إنهاء Microsoft 365 الخدمات بالكامل، يمكنك متابعة مسار حذف المستأجر لكل عملية موثقة. تعرف [على كيفية حذف مستأجر في Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>إبطال "مفاتيح العملاء" ومفتاح التوفر Exchange Online Skype for Business

عند بدء مسار إزالة البيانات Exchange Online البيانات Skype for Business، يمكنك تعيين طلب إزالة البيانات الدائم على DEP. القيام بذلك بشكل دائم يحذف البيانات المشفرة داخل علب البريد التي تم تعيين DEP لها.

بما أنه يمكنك فقط تشغيل الأمر PowerShell cmdlet مقابل DEP واحد في كل مرة، يمكنك إعادة تعيين DEP واحد إلى كل علب البريد قبل بدء مسار إزالة البيانات.

> [!WARNING]
> لا تستخدم مسار إزالة البيانات لحذف مجموعة فرعية من علب البريد. هذه العملية مخصصة فقط للعملاء الذين يخرجون من الخدمة.

لبدء مسار إزالة البيانات، أكمل الخطوات التالية:

1. قم بإزالة أذونات الالتفاف وإزالة الأذونات ل "O365 Exchange Online" من Azure Key Vaults.

2. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه امتيازات المسؤول العام في مؤسستك، اتصل [ب PowerShell Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

3. لكل DEP يحتوي على علب البريد التي تريد حذفها، قم بتشغيل الأمر [Cmdlet Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) كما يلي.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   إذا فشل الأمر، فتأكد من إزالة Exchange Online من كلا المفتاحين في مخزن مفاتيح Azure كما هو محدد سابقا في هذه المهمة.بمجرد تعيين المفتاح PermanentDataPurgeRequested باستخدام الأمر cmdlet Set-DataEncryptionPolicy، لن تتمكن من تعيين DEP هذا إلى علب البريد.

4. اتصل بدعم Microsoft واطلب إزالة البيانات eDocument.

    بناء على طلبك، ترسل لك Microsoft مستندا قانونيا لتقر بحذف البيانات وتفوضه. يحتاج الشخص في مؤسستك الذي قام بالتوقيع كموافق في FastTrack أثناء التكديع إلى توقيع هذا المستند. عادة ما يكون هذا الشخص مديرا تنفيذيا أو شخصا آخر معينا في شركتك ومرخصا له قانونا لتوقيع الأوراق بالنيابة عن مؤسستك.

5. بمجرد توقيع ممثلك للمستند القانوني، أرجعه إلى Microsoft (عادة من خلال توقيع eDoc).

    بعد تلقي Microsoft للمستند القانوني، تقوم Microsoft بتشغيل cmdlets لتحريك عملية إزالة البيانات التي تحذف النهج أولا، وت علامات علب البريد للحذف الدائم، ثم تحذف مفتاح التوفر. بمجرد اكتمال عملية إزالة البيانات، يتم إزالة البيانات، ويتعذر Exchange Online الوصول إليها، ولا يمكن استردادها.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>إبطال "مفاتيح العملاء" ومفتاح التوفر لملفات SharePoint عبر الإنترنت OneDrive for Business وملفات Teams الخاصة بك

لبدء مسار إزالة البيانات لملفات SharePoint عبر OneDrive for Business و Teams، أكمل الخطوات التالية:

1. إبطال الوصول إلى مخزن مفاتيح Azure. يجب أن يوافق جميع المسؤولين الأساسيين في المخزن على إبطال الوصول.

   لا تحذف مخزن مفاتيح Azure SharePoint Online. يمكن مشاركة المخزن الرئيسي بين عدة SharePoint الإنترنت والمستأجرين المكفوفين.

2. اتصل ب Microsoft لحذف مفتاح التوفر.

    عندما تتصل ب Microsoft لحذف مفتاح التوفر، سنرسل إليك مستندا قانونيا. يحتاج الشخص في مؤسستك الذي قام بالتوقيع كموافق في FastTrack أثناء التكديع إلى توقيع هذا المستند. عادة ما يكون هذا الشخص مديرا تنفيذيا أو شخصا آخر معينا في شركتك ومرخصا له قانونا لتوقيع الأوراق بالنيابة عن مؤسستك.

3. بمجرد توقيع ممثلك للمستند القانوني، قم بإرجاعه إلى Microsoft (عادة من خلال توقيع eDoc).

   بمجرد تلقي Microsoft للمستند القانوني، نقوم بتشغيل cmdlets لتشغيل عملية إزالة البيانات التي تقوم بتنفيذ حذف التشفير لمفتاح المستأجر ومفتاح الموقع وكل مفاتيح كل مستند فردي، مما يؤدي إلى كسر التسلسل الهيكلي للمفتاح بشكل نهائي. بمجرد اكتمال عملية إزالة البيانات cmdlets، يتم إزالة بياناتك.

## <a name="related-articles"></a>المقالات ذات الصلة

- [تشفير الخدمة باستخدام "مفتاح العميل"](customer-key-overview.md)

- [التعرف على مفتاح التوفر](customer-key-availability-key-understand.md)

- [إعداد مفتاح العميل](customer-key-set-up.md)

- [لف مفتاح عميل أو مفتاح توفر أو تدويره](customer-key-availability-key-roll.md)

- [Customer Lockbox](customer-lockbox-requests.md)

- [تشفير الخدمة](office-365-service-encryption.md)
