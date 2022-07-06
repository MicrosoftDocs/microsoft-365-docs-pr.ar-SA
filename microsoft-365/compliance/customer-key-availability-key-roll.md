---
title: لف مفتاح عميل أو مفتاح توفر أو تدويره
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
description: تعرف على كيفية لف مفاتيح جذر العميل المخزنة في azure Key Vault المستخدمة مع مفتاح العميل. تتضمن الخدمات ملفات Exchange Online Skype for Business وSharePoint Online OneDrive for Business وTeams.
ms.openlocfilehash: 474df9b4776df09b4a46ca002f506155606bdb52
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636480"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>لف مفتاح عميل أو مفتاح توفر أو تدويره

> [!CAUTION]
> قم فقط بلف مفتاح التشفير الذي تستخدمه مع Customer Key عندما تفرض متطلبات الأمان أو التوافق الخاصة بك أنه يجب عليك إظهار المفتاح. بالإضافة إلى ذلك، لا تحذف أي مفاتيح مقترنة أو مقترنة بنهج. عند لف المفاتيح، سيكون هناك محتوى مشفر بالمفاتيح السابقة. على سبيل المثال، على الرغم من إعادة تشفير علب البريد النشطة بشكل متكرر، قد تظل علب البريد غير النشطة وغير المتصلة والمعطلة مشفرة باستخدام المفاتيح السابقة. يقوم SharePoint Online بإجراء نسخة احتياطية من المحتوى لأغراض الاستعادة والاسترداد، لذلك قد لا يزال هناك محتوى مؤرشف باستخدام المفاتيح القديمة.

## <a name="about-rolling-the-availability-key"></a>حول طرح مفتاح التوفر

لا تعرض Microsoft التحكم المباشر لمفتاح التوفر للعملاء. على سبيل المثال، يمكنك فقط لف (تدوير) المفاتيح التي تملكها في Azure Key Vault. يقوم Microsoft 365 بطرح مفاتيح التوفر في جدول زمني محدد داخليا. لا توجد اتفاقية على مستوى الخدمة (SLA) تواجه العملاء لهذه اللفات الرئيسية. يقوم Microsoft 365 بتدوير مفتاح التوفر باستخدام رمز خدمة Microsoft 365 في عملية تلقائية وغير يدوية. يمكن لمسؤولي Microsoft بدء عملية اللف. يتم طرح المفتاح باستخدام آليات تلقائية دون الوصول المباشر إلى مخزن المفاتيح. لا يتم توفير الوصول إلى مخزن مفاتيح التوفر السري لمسؤولي Microsoft. يستفيد المتداول لمفتاح التوفر من نفس الآلية المستخدمة لإنشاء المفتاح في البداية. لمزيد من المعلومات حول مفتاح التوفر، راجع [فهم مفتاح التوفر](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> يمكن إظهار Exchange Online ومفاتيح التوفر Skype for Business بشكل فعال من قبل العملاء الذين ينشئون DEP جديدا، حيث يتم إنشاء مفتاح توفر فريد لكل DEP تقوم بإنشائه. توجد مفاتيح التوفر لملفات SharePoint Online و OneDrive for Business وTeams على مستوى الغابة وتتم مشاركتها عبر DEPs والعملاء، مما يعني أن النشر يحدث فقط في جدول زمني محدد داخليا من Microsoft. للتخفيف من مخاطر عدم نشر مفتاح التوفر في كل مرة يتم فيها إنشاء DEP جديد، يقوم SharePoint وOneDrive وTeams بطرح المفتاح الوسيط للمستأجر (TIK)، والمفتاح الملتف بواسطة مفاتيح جذر العميل ومفتاح التوفر، في كل مرة يتم فيها إنشاء DEP جديد.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>طلب إصدار جديد من كل مفتاح جذر موجود تريد لفه

عند لف مفتاح، يمكنك طلب إصدار جديد من مفتاح موجود. لطلب إصدار جديد من مفتاح موجود، يمكنك استخدام cmdlet نفسه، [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey)، بنفس بناء الجملة الذي استخدمته لإنشاء المفتاح في المقام الأول. بعد الانتهاء من طرح أي مفتاح مقترن بنهج تشفير البيانات (DEP)، يمكنك تشغيل أمر cmdlet آخر للتأكد من أن مفتاح العميل يبدأ باستخدام المفتاح الجديد. قم بهذه الخطوة في كل Key Vault Azure (AKV).

على سبيل المثال:

1. سجل الدخول إلى اشتراك Azure باستخدام Azure PowerShell. للحصول على الإرشادات، راجع [تسجيل الدخول باستخدام Azure PowerShell](/powershell/azure/authenticate-azureps).

2. قم بتشغيل Add-AzKeyVaultKey cmdlet كما هو موضح في المثال التالي:

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   في هذا المثال، نظرا لوجود مفتاح يسمى **Contoso-CK-EX-NA-VaultA1-Key001** في مخزن **Contoso-CK-EX-NA-VaultA1** ، ينشئ cmdlet إصدارا جديدا من المفتاح. تحافظ هذه العملية على الإصدارات الرئيسية السابقة في محفوظات الإصدارات للمفتاح. تحتاج إلى إصدار المفتاح السابق لفك تشفير البيانات التي لا يزال يقوم بتشفيرها. بمجرد الانتهاء من طرح أي مفتاح مقترن ب DEP، قم بتشغيل أمر cmdlet إضافي للتأكد من أن مفتاح العميل يبدأ باستخدام المفتاح الجديد. تصف الأقسام التالية أوامر cmdlets بمزيد من التفصيل.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>تحديث المفاتيح ل DEPs متعددة حمل العمل

عند لف أي من مفاتيح azure Key Vault المقترنة ب DEP المستخدم مع أحمال عمل متعددة، يجب تحديث DEP للإشارة إلى المفتاح الجديد. لا تقوم هذه العملية بتدوير مفتاح التوفر.

لإرشاد Customer Key لاستخدام المفتاح الجديد لتشفير أحمال عمل متعددة، أكمل الخطوات التالية:

1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-M365DataAtRestEncryptionPolicy cmdlet.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

حيث *يكون PolicyName* هو اسم النهج أو معرفه الفريد. على سبيل المثال، Contoso_Global.

على سبيل المثال:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>تحديث مفاتيح Exchange Online DEPs

عند لف أي من مفاتيح Key Vault Azure المقترنة ب DEP المستخدم مع Exchange Online Skype for Business، يجب تحديث DEP للإشارة إلى المفتاح الجديد. لا يقوم هذا بتدوير مفتاح التوفر.

لإرشاد Customer Key لاستخدام المفتاح الجديد لتشفير علب البريد، قم بتشغيل Set-DataEncryptionPolicy cmdlet كما يلي:

1. تشغيل Set-DataEncryptionPolicy cmdlet في Azure PowerShell:
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. للتحقق من قيمة خاصية DataEncryptionPolicyID لعلبة البريد، استخدم الخطوات [الواردة في تحديد DEP المعين إلى علبة بريد](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). تتغير قيمة هذه الخاصية بمجرد تطبيق الخدمة للمفتاح المحدث.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>تحديث مفاتيح ملفات SharePoint Online و OneDrive for Business وTeams

يسمح لك SharePoint Online فقط بطرح مفتاح واحد في كل مرة. إذا كنت تريد لف كلا المفتاحين في مخزن مفاتيح، فانتظر حتى تكتمل العملية الأولى. توصي Microsoft بتدرج عملياتك لتجنب هذه المشكلة. عند لف أي من مفاتيح Key Vault Azure المقترنة ب DEP المستخدم مع SharePoint Online OneDrive for Business، يجب تحديث DEP للإشارة إلى المفتاح الجديد. لا يقوم هذا بتدوير مفتاح التوفر.

1. شغل أمر cmdlet Update-SPODataEncryptionPolicy كما يلي:
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   بينما يبدأ أمر cmdlet هذا عملية لفة المفاتيح ل SharePoint Online OneDrive for Business، لا يكتمل الإجراء على الفور.

2. للاطلاع على تقدم عملية لفة المفتاح، قم بتشغيل Get-SPODataEncryptionPolicy cmdlet كما يلي:

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>المقالات ذات الصلة

- [تشفير الخدمة باستخدام مفتاح العميل](customer-key-overview.md)

- [إعداد مفتاح العميل](customer-key-set-up.md)

- [إدارة مفتاح العميل](customer-key-manage.md)

- [التعرف على مفتاح التوفر](customer-key-availability-key-understand.md)
