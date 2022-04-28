---
title: إدارة المستأجرين Microsoft 365 باستخدام Windows PowerShell لشركاء DAP
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: في هذه المقالة، تعرف على كيفية استخدام PowerShell Microsoft 365 لإدارة إيجارات العملاء.
ms.openlocfilehash: 11869157a5ed106d1aea0a4ce0e21716be1cc78f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096777"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>إدارة المستأجرين Microsoft 365 باستخدام Windows PowerShell لشركاء أذونات الوصول المفوض (DAP)

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يسمح Windows PowerShell لشركاء المشاركة Cloud Solution Provider (CSP) بإدارة إعدادات إيجار العملاء غير المتوفرة في مركز مسؤولي Microsoft 365 والإبلاغ بها بسهولة. تجدر الإشارة إلى أن أذونات الإدارة بالنيابة عن (AOBO) مطلوبة لحساب المسؤول الشريك للاتصال بفواتير العملاء الخاصة به.

شركاء إذن الوصول المفوض (DAP) هم شركاء موفري حلول السحابة (CSP) وSyndication. وهي غالبا ما تكون موفرة للشبكات أو الاتصالات لشركات أخرى. وهي تقوم بتجميع اشتراكات Microsoft 365 في عروض الخدمة لعملائها. عندما يبيعون اشتراكا Microsoft 365، يتم منحهم تلقائيا أذونات الإدارة نيابة عن (AOBO) إلى إيجارات العميل حتى يتمكنوا من إدارة إيجارات العميل والإبلاغ عنها.
## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

تتطلب منك الإجراءات الواردة في هذا الموضوع الاتصال [الاتصال Microsoft 365 باستخدام PowerShell](connect-to-microsoft-365-powershell.md).

تحتاج أيضا إلى بيانات اعتماد مسؤول المستأجر الشريك.

## <a name="what-do-you-want-to-do"></a>ماذا تريد أن تفعل؟

### <a name="list-all-tenant-ids"></a>سرد كافة معرفات المستأجرين

> [!NOTE]
> إذا كان لديك أكثر من 500 مستأجر، فقل بناء جملة cmdlet باستخدام  _-All_ أو _-MaxResultsParameter_. ينطبق هذا على أوامر cmdlets الأخرى التي يمكن أن تعطي إخراجا كبيرا، مثل **Get-MsolUser**.

لإدراج كافة معرفات مستأجر العميل التي لديك حق الوصول إليها، قم بتشغيل هذا الأمر.

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

سيؤدي ذلك إلى عرض قائمة بجميع مستأجري العملاء حسب **TenantId**.

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a>الحصول على معرف مستأجر باستخدام اسم المجال

للحصول على **TenantId** لمستأجر عميل معين حسب اسم المجال، قم بتشغيل هذا الأمر. استبدل _<domainname.onmicrosoft.com>_ باسم المجال الفعلي لمستأجر العميل الذي تريده.

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>سرد كافة المجالات لمستأجر

للحصول على جميع المجالات لأي مستأجر عميل واحد، قم بتشغيل هذا الأمر. استبدال  _\<customer TenantId value>_ بالقيمة الفعلية.

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

إذا قمت بتسجيل مجالات إضافية، فسيؤدي ذلك إلى إرجاع كافة المجالات المقترنة ب **TenantId** الخاص بالعميل.

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>الحصول على تعيين لكافة المستأجرين والمجالات المسجلة

أظهرت لك أوامر PowerShell السابقة ل Microsoft 365 كيفية استرداد معرفات المستأجر أو المجالات ولكن ليس كليهما في نفس الوقت، وبدون تعيين واضح بينهما جميعا. ينشئ هذا الأمر قائمة بجميع معرفات مستأجر العميل ومجالاتها.

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>الحصول على جميع المستخدمين لمستأجر

سيؤدي ذلك إلى عرض **UserPrincipalName** و **DisplayName** والحالة **isLicensed** لكافة المستخدمين لمستأجر معين. استبدال _\<customer TenantId value>_ بالقيمة الفعلية.

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>الحصول على جميع التفاصيل حول مستخدم

إذا كنت تريد رؤية كافة خصائص مستخدم معين، فشغل هذا الأمر. استبدال  _\<customer TenantId value>_ القيم الفعلية واستبدالها _\<user principal name value>_ .

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>إضافة مستخدمين وتعيين الخيارات وتعيين التراخيص

يتسم الإنشاء والتكوين والترخيص المجمع لمستخدمي Microsoft 365 بكفاءة خاصة باستخدام PowerShell Microsoft 365. في هذه العملية المكونة من خطوتين، ستقوم أولا بإنشاء إدخالات لكافة المستخدمين الذين تريد إضافتهم في ملف قيم مفصولة بفواصل (CSV) ثم استيراد هذا الملف باستخدام PowerShell Microsoft 365.

#### <a name="create-a-csv-file"></a>إنشاء ملف CSV

إنشاء ملف CSV باستخدام هذا التنسيق:

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

حيث:

- **UsageLocation**: القيمة لهذا هي رمز بلد/منطقة ISO المكون من حرفين للمستخدم. يمكن النظر في رموز البلد/المنطقة في [النظام الأساسي للاستعراض عبر الإنترنت لISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). على سبيل المثال، التعليمات البرمجية للولايات المتحدة هي الولايات المتحدة، والتعليمة البرمجية للبرازيل هي BR.

- **LicenseAssignment**: تستخدم قيمة هذا التنسيق: `syndication-account:<PROVISIONING_ID>`. على سبيل المثال، إذا كنت تقوم بتعيين مستخدمين مستأجرين للعملاء O365_Business_Premium التراخيص، فإن قيمة **LicenseAssignment** تبدو كما يلي: **syndication-account:O365_Business_Premium**. ستجد PROVISIONING_IDs في مدخل شريك Syndication الذي يمكنك الوصول إليه كشريك Syndication أو CSP.

#### <a name="import-the-csv-file-and-create-the-users"></a>استيراد ملف CSV وإنشاء المستخدمين

بعد إنشاء ملف CSV، قم بتشغيل هذا الأمر لإنشاء حسابات مستخدمين باستخدام كلمات مرور غير منتهية الصلاحية يجب على المستخدم تغييرها عند تسجيل الدخول أولا والتي تعين الترخيص الذي تحدده. تأكد من استبدال اسم ملف CSV الصحيح.

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>راجع أيضًا

[تعليمات للشركاء](https://go.microsoft.com/fwlink/p/?LinkId=533477)
