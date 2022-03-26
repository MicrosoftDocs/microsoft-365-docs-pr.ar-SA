---
title: إدارة Microsoft 365 المستأجرين باستخدام Windows PowerShell لشركاء DAP
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: في هذه المقالة، تعرف على كيفية استخدام PowerShell Microsoft 365 لإدارة عشرات عملاءك.
ms.openlocfilehash: ff74cc0ec710996c66a659034f4fb4a49ee57ab1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572831"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>إدارة Microsoft 365 المستأجرين باستخدام Windows PowerShell أذونات الوصول المفوض (DAP)

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

Windows PowerShell شركاء Syndication Cloud Solution Provider (CSP) بإدارة إعدادات إيجار العميل غير المتوفرة في مركز مسؤولي Microsoft 365 بسهولة وإعداد تقرير بشأنها. تجدر الإشارة إلى أن أذونات الإدارة بالنيابة عن (AOBO) مطلوبة لحساب مسؤول الشريك للاتصال بأذونات العملاء الخاصة به.

شركاء إذن الوصول المفوض (DAP) هم شركاء Syndication وموفرو حلول السحابة (CSP). فهي غالبا ما تكون موفري شبكة أو اتصالات لشركات أخرى. كما يمكنهم Microsoft 365 اشتراكاتهم في عروض الخدمات الخاصة بهم للعملاء. عند بيعهم لاشتراك Microsoft 365، يتم منحهم تلقائيا أذونات الإدارة بالنيابة عن (AOBO) إلى أذونات العميل بحيث يمكنهم إدارة أذونات العميل والتقارير بشأنها.
## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

تتطلب الإجراءات في هذا الموضوع الاتصال الاتصال [Microsoft 365 PowerShell](connect-to-microsoft-365-powershell.md).

تحتاج أيضا إلى بيانات اعتماد مسؤول المستأجر الشريك.

## <a name="what-do-you-want-to-do"></a>ماذا تريد أن تفعل؟

### <a name="list-all-tenant-ids"></a>سرد جميع هويات المستأجر

> [!NOTE]
> إذا كان لديك أكثر من 500 مستأجر، فوسع نطاق بناء جملة cmdlet باستخدام  _-All_ أو _-MaxResultsParameter_. ينطبق هذا الأمر على cmdlets الأخرى التي يمكن أن تقدم إخراجا كبيرا، مثل **Get-MsolUser**.

لتضمين جميع "هويات مستأجر العميل" التي يمكنك الوصول إليها، يمكنك تشغيل هذا الأمر.

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

سيعرض هذا قائمة بكل مستأجري العملاء حسب **TenantId**.

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع **Msol** في اسمها. لمواصلة استخدام هذه cmdlets، يجب تشغيلها من Windows PowerShell.
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a>الحصول على "مستأجر" باستخدام اسم المجال

للحصول على **TenantId** لمستأجر عميل معين حسب اسم المجال، يمكنك تشغيل هذا الأمر. _استبدل<domainname.onmicrosoft.com>_ باسم المجال الفعلي لمستأجر العميل الذي تريده.

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>سرد كافة المجالات لمستأجر

للحصول على كل المجالات لأي مستأجر عميل واحد، يمكنك تشغيل هذا الأمر. استبدال  _\<customer TenantId value>_ بالقيمة الفعلية.

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

إذا قمت بتسجيل مجالات إضافية، فإن ذلك سيرجع كل المجالات المقترنة ب **TenantId الخاص للعميل**.

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>الحصول على تعيين لجميع المستأجرين والمجالات المسجلة

أظهرت لك أوامر PowerShell Microsoft 365 السابقة كيفية استرداد أي من نطاقات أو نطاقات المستأجرين ولكن ليس كلاهما في الوقت نفسه، ومن دون تعيين واضح بينهما جميعا. يؤدي هذا الأمر إلى إنشاء قائمة بكل "هويات مستأجر العميل" ومجالاتها.

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>الحصول على جميع المستخدمين لمستأجر

سيعرض هذا **UserPrincipalName** و **DisplayName** و **الحالة isLicensed** لجميع المستخدمين لمستأجر معين. استبدال _\<customer TenantId value>_ بالقيمة الفعلية.

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>الحصول على كل التفاصيل حول مستخدم

إذا كنت تريد رؤية كل خصائص مستخدم معين، فدير هذا الأمر. استبدال  _\<customer TenantId value>_ القيم _\<user principal name value>_ الفعلية ومعها.

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>إضافة مستخدمين وتعيين خيارات وتعيين تراخيص

تتسم عمليات الإنشاء والتكوين والترخيص المجمعة للمستخدمين Microsoft 365 بكفاءة خاصة باستخدام PowerShell Microsoft 365. في هذه العملية على خطوتين، عليك أولا إنشاء إدخالات لجميع المستخدمين الذين تريد إضافتهم في ملف قيم مفصولة بفصول فاصلة (CSV)، ثم استيراد هذا الملف باستخدام PowerShell Microsoft 365.

#### <a name="create-a-csv-file"></a>إنشاء ملف CSV

إنشاء ملف CSV باستخدام هذا التنسيق:

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

حيث:

- **UsageLocation**: القيمة الخاصة بذلك هي رمز البلد/المنطقة الخاص ب ISO للمستخدم من حرفين. يمكن البحث عن رموز البلد/المنطقة في النظام الأساسي [لاستعراضISO Online](https://go.microsoft.com/fwlink/p/?LinkId=532703). على سبيل المثال، التعليمة البرمجية للولايات المتحدة هي الولايات المتحدة، و التعليمات البرمجية للبرازيل هي BR.

- **LicenseAssignment**: تستخدم القيمة لهذا التنسيق: `syndication-account:<PROVISIONING_ID>`. على سبيل المثال، إذا كنت تقوم بتعيين مستخدمين مستأجرين عملاء O365_Business_Premium تراخيص، فإن قيمة **LicenseAssignment** تبدو كما يلي: **syndication-account:O365_Business_Premium**. ستعثر على PROVISIONING_IDs في مدخل شريك Syndication التي يمكنك الوصول إليها كقناة Syndication أو شريك CSP.

#### <a name="import-the-csv-file-and-create-the-users"></a>استيراد ملف CSV وإنشاء المستخدمين

بعد إنشاء ملف CSV، قم بتشغيل هذا الأمر لإنشاء حسابات مستخدمين باستخدام كلمات مرور غير منتهية الصلاحية يجب على المستخدم تغييرها عند تسجيل الدخول أولا وتعيين الترخيص الذي تحدده. تأكد من استبدال اسم ملف CSV الصحيح.

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>راجع أيضًا

[تعليمات للشركاء](https://go.microsoft.com/fwlink/p/?LinkId=533477)
