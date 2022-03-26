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
description: تعرف على كيفية لفة المفاتيح الجذر للعملاء المخزنة في مخزن مفاتيح Azure المستخدمة مع "مفتاح العميل". تتضمن الخدمات Exchange Online Skype for Business و SharePoint عبر الإنترنت OneDrive for Business و Teams الملفات.
ms.openlocfilehash: 5f2de108d493e4b6d4233f4a932a24f524e468bb
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63566985"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>لف مفتاح عميل أو مفتاح توفر أو تدويره

> [!CAUTION]
> يمكنك فقط لف مفتاح تشفير تستخدمه مع "مفتاح العميل" عندما تفرض متطلبات الأمان أو التوافق أن عليك لفة المفتاح. بالإضافة إلى ذلك، لا تحذف أي مفاتيح مقترنة أو مقترنة ونهج. عند لف المفاتيح، سيكون هناك محتوى مشفر باستخدام المفاتيح السابقة. على سبيل المثال، في حين سيتم إعادة تشفير علب البريد النشطة بشكل متكرر، قد لا يزال يتم تشفير علب البريد غير النشطة وغير النشطة والمعطلة باستخدام المفاتيح السابقة. SharePoint Online النسخ الاحتياطي للمحتوى لأغراض الاسترداد والاستعادة، لذلك قد لا يزال هناك محتوى مؤرشف باستخدام المفاتيح القديمة.

## <a name="about-rolling-the-availability-key"></a>حول طرح مفتاح التوفر

لا تعرض Microsoft إمكانية التحكم المباشر في مفتاح التوفر للعملاء. على سبيل المثال، يمكنك فقط لف (تدوير) المفاتيح التي تملكها في مخزن مفاتيح Azure. Microsoft 365 مفاتيح التوفر في جدول معرف داخليا. لا توجد اتفاقية على مستوى الخدمة (SLA) للعملاء لهذه القوائم الرئيسية. Microsoft 365 تدوير مفتاح التوفر باستخدام Microsoft 365 الخدمة في عملية تلقائية غير يدوية. يمكن لمسؤولي Microsoft بدء عملية لفة. يتم تدحرج المفتاح باستخدام آليات تلقائية بدون الوصول المباشر إلى مخزن المفاتيح. لا يتم توفير الوصول إلى مخزن سري مفتاح التوفر لمسؤولي Microsoft. يستخدم المتداول لمفتاح التوفر الآلية نفسها المستخدمة لإنشاء المفتاح في البداية. لمزيد من المعلومات حول مفتاح التوفر، راجع [فهم مفتاح التوفر](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Exchange Online مفاتيح التوفر Skype for Business من قبل العملاء الذين ينشئون DEP جديدا، نظرا لإنشاء مفتاح توفر فريد لكل DEP تقوم بإنشاءه. توجد مفاتيح التوفر لملفات SharePoint Online و OneDrive for Business و Teams على مستوى الغابات وهي مشتركة بين عملاء DEPS والعملاء، مما يعني أن عملية التدحرج تحدث فقط في جدول معرف داخليا من Microsoft. للحد من مخاطر عدم نشر مفتاح التوفر في كل مرة يتم فيها إنشاء DEP جديد، يقوم SharePoint و OneDrive و Teams بقلب المفتاح الوسيط للمستأجر (TIK)، وهو المفتاح الملتف بالمفاتيح الجذر للعميل ومفتاح التوفر، في كل مرة يتم فيها إنشاء DEP جديد.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>طلب إصدار جديد من كل مفتاح جذر موجود تريد لفه

عند لفة مفتاح، تطلب إصدارا جديدا من مفتاح موجود. لطلب إصدار جديد من مفتاح موجود، استخدم الأمر cmdlet نفسه، [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey)، مع بناء الجملة نفسه الذي استخدمته لإنشاء المفتاح في المقام الأول. بعد الانتهاء من نشر أي مفتاح مقترن ب "نهج تشفير البيانات" (DEP)، يمكنك تشغيل cmdlet آخر للتأكد من أن مفتاح العميل يبدأ باستخدام المفتاح الجديد. يمكنك القيام بهذه الخطوة في كل مخزن مفاتيح Azure (AKV).

على سبيل المثال:

1. سجل الدخول إلى اشتراكك في Azure باستخدام Azure PowerShell. للحصول على الإرشادات، راجع [تسجيل الدخول باستخدام Azure PowerShell](/powershell/azure/authenticate-azureps).

2. تشغيل Add-AzKeyVaultKey cmdlet كما هو موضح في المثال التالي:

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   في هذا المثال، بما أن مفتاحا يسمى **Contoso-CK-EX-NA-VaultA1-Key001** موجود في **المخزن Contoso-CK-EX-NA-VaultA1** ، ينشئ الأمر cmdlet إصدارا جديدا من المفتاح. تحافظ هذه العملية على الإصدارات الأساسية السابقة في محفوظات الإصدارات للمفتاح. تحتاج إلى إصدار المفتاح السابق لفك تشفير البيانات التي لا يزال يقوم بتشفيرها. بمجرد إكمال نشر أي مفتاح مقترن ب DEP، يمكنك تشغيل cmdlet إضافي للتأكد من أن مفتاح العميل يبدأ باستخدام المفتاح الجديد. تصف المقاطع التالية cmdlets بتفاصيل إضافية.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>تحديث المفاتيح ل DEPs متعددة حمل العمل

عند لف أي من مفاتيح مخزن مفاتيح Azure المقترنة ب DEP المستخدمة مع أحمال عمل متعددة، يجب تحديث DEP لتشير إلى المفتاح الجديد. لا تقوم هذه العملية بتدوير مفتاح التوفر.

للحصول على تعليمات لمفتاح العميل لاستخدام المفتاح الجديد لتشفير أحمال عمل متعددة، أكمل الخطوات التالية:

1. على الكمبيوتر المحلي، باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام أو مسؤول التوافق في مؤسستك، قم [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) في نافذة Windows PowerShell.

2. تشغيل Set-M365DataAtRestEncryptionPolicy cmdlet.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

حيث *يكون اسم* النهج هو اسم النهج أو الم ID الفريد له. على سبيل المثال، Contoso_Global.

على سبيل المثال:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>تحديث مفاتيح Exchange Online DEPs

عند لف أي من مفاتيح مخزن مفاتيح Azure المقترنة ب DEP المستخدمة مع Exchange Online و Skype for Business، يجب تحديث DEP لتشير إلى المفتاح الجديد. لا يقوم هذا بتدوير مفتاح التوفر.

للحصول على تعليمات لمفتاح العميل لاستخدام المفتاح الجديد لتشفير علب البريد، Set-DataEncryptionPolicy cmdlet كما يلي:

1. تشغيل Set-DataEncryptionPolicy cmdlet في Azure PowerShell:
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. للتحقق من قيمة الخاصية DataEncryptionPolicyID لعلبة البريد، استخدم الخطوات الواردة في [تحديد DEP المعين إلى علبة بريد](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). تتغير قيمة هذه الخاصية بمجرد تطبيق الخدمة للمفتاح المحدث.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>تحديث المفاتيح لملفات SharePoint عبر الإنترنت OneDrive for Business والملفات Teams

SharePoint Online فقط بلف مفتاح واحد في كل مرة. إذا كنت تريد لف كلا المفتاحين في مخزن مفاتيح، فانتظر حتى تكتمل العملية الأولى. توصي Microsoft بتبرير عملياتك لتجنب هذه المشكلة. عند لف أي من مفاتيح مخزن مفاتيح Azure المقترنة ب DEP المستخدمة مع SharePoint Online و OneDrive for Business، يجب تحديث DEP لتشير إلى المفتاح الجديد. لا يقوم هذا بتدوير مفتاح التوفر.

1. تشغيل Update-SPODataEncryptionPolicy cmdlet كما يلي:
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   على الرغم من أن الأمر cmdlet هذا يبدأ عملية لفة المفاتيح SharePoint عبر الإنترنت OneDrive for Business، لا يكتمل الإجراء على الفور.

2. لمشاهدة تقدم عملية لفة المفاتيح، ادير Get-SPODataEncryptionPolicy cmdlet كما يلي:

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>المقالات ذات الصلة

- [تشفير الخدمة باستخدام "مفتاح العميل" Office 365](customer-key-overview.md)

- [إعداد مفتاح العميل Office 365](customer-key-set-up.md)

- [إدارة مفتاح العميل Office 365](customer-key-manage.md)

- [التعرف على مفتاح التوفر](customer-key-availability-key-understand.md)
