---
title: استخدام AllowSelfServicePurchase للوحدة النمطية MSCommerce PowerShell
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: ''
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
search.appverid:
- MET150
description: تعرف على كيفية استخدام AllowSelfServicePurchase PowerShell cmdlet لتشغيل عملية شراء الخدمة الذاتية أو إيقاف تشغيلها.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 4/7/2022
ms.openlocfilehash: e4423892f2dc045a9729e68519c85d471838d5ac
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042176"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>استخدام AllowSelfServicePurchase للوحدة النمطية MSCommerce PowerShell

الوحدة النمطية **MSCommerce** PowerShell متوفرة الآن في [معرض PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery). تتضمن الوحدة النمطية قيمة معلمة **PolicyID** ل **AllowSelfServicePurchase** التي تتيح لك التحكم في ما إذا كان يمكن للمستخدمين في مؤسستك إجراء عمليات شراء الخدمة الذاتية.

يمكنك استخدام الوحدة النمطية **MSCommerce** PowerShell من أجل:

- عرض الحالة الافتراضية لقيمة المعلمة **AllowSelfServicePurchase** — سواء تم تمكينها أو تعطيلها
- عرض قائمة بالنواتج القابلة للتطبيق وما إذا كان شراء الخدمة الذاتية ممكنا أو معطلا
- عرض الإعداد الحالي لمنتج معين أو تعديله لتمكينه أو تعطيله

## <a name="requirements"></a>الاحتياجات

لاستخدام وحدة **MSCommerce** PowerShell، تحتاج إلى:

- جهاز Windows 10
- PowerShell 5 أو أقل. حاليا، PowerShell 6.x/7.x غير مدعوم مع هذه الوحدة النمطية.
- إذن المسؤول للجهاز
- دور مسؤول عمومي أو مسؤول فوترة للمستأجر

## <a name="install-the-mscommerce-powershell-module"></a>تثبيت الوحدة النمطية MSCommerce PowerShell

يمكنك تثبيت الوحدة النمطية **MSCommerce** PowerShell على جهازك Windows 10 مرة واحدة ثم استيراده إلى كل جلسة PowerShell تبدأها. قم بتنزيل الوحدة النمطية **MSCommerce** PowerShell من [معرض PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery).

لتثبيت الوحدة النمطية **MSCommerce** PowerShell مع **PowerShellGet**، قم بتشغيل الأمر التالي:

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>استيراد MSCommerce إلى جلسة عمل PowerShell

بعد تثبيت الوحدة النمطية على جهازك Windows 10، يمكنك استيرادها إلى كل جلسة عمل PowerShell تبدأها. لاستيراده إلى جلسة عمل PowerShell، قم بتشغيل الأمر التالي:

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>الاتصال إلى MSCommerce باستخدام بيانات الاعتماد الخاصة بك

للاتصال بالوحدة النمطية PowerShell باستخدام بيانات الاعتماد الخاصة بك، قم بتشغيل الأمر التالي.

```powershell
Connect-MSCommerce
```

يقوم هذا الأمر بتوصيل جلسة عمل PowerShell الحالية بمستأجر Azure Active Directory. يطالبك الأمر باسم مستخدم وكلمة مرور للمستأجر الذي تريد الاتصال به. إذا تم تمكين المصادقة متعددة العوامل لبيانات الاعتماد الخاصة بك، يمكنك استخدام الخيار التفاعلي لتسجيل الدخول.

## <a name="view-details-for-allowselfservicepurchase"></a>عرض تفاصيل AllowSelfServicePurchase

لعرض وصف لقيمة المعلمة **AllowSelfServicePurchase** والحالة الافتراضية، استنادا إلى مؤسستك، قم بتشغيل الأمر التالي:

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>عرض قائمة منتجات شراء الخدمة الذاتية وحالتها

لعرض قائمة بجميع منتجات شراء الخدمة الذاتية المتوفرة وحالة كل منها، قم بتشغيل الأمر التالي:

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

يسرد الجدول التالي المنتجات المتوفرة **ومعرف المنتج الخاص** بها.

| المنتج | Productid |
|-----------------------------|--------------|
| Power Apps لكل مستخدم | CFQ7TTC0LH2H |
| Power Automate لكل مستخدم | CFQ7TTC0KP0N |
| Power Automate RPA | CFQ7TTC0KXG6  |
| power BI Premium (مستقل) | CFQ7TTC0KXG7  |
| Power BI Pro | CFQ7TTC0L3PB |
| Project (النظام 1)* | CFQ7TTC0HDB1 |
| Project (النظام 3)* | CFQ7TTC0HDB0 |
| Visio (النظام 1)* | CFQ7TTC0HD33 |
| Visio (النظام 2)* | CFQ7TTC0HD32 |
| Windows 365 Enterprise | CFQ7TTC0HHS9 |
| Windows 365 Business | CFQ7TTC0J203 |
| Windows 365 Business باستخدام ميزة Windows المختلطة | CFQ7TTC0HX99 |

*تم تغيير هذه المعرفات. إذا قمت مسبقا بحظر المنتجات باستخدام المعرف القديم، يتم حظرها تلقائيا باستخدام المعرفات الجديدة. لا يلزم عمل إضافي.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>عرض حالة AllowSelfServicePurchase أو تعيينها

بعد عرض قائمة المنتجات المتوفرة لشراء الخدمة الذاتية، يمكنك عرض الإعداد لمنتج معين أو تعديله.

للحصول على إعداد النهج لمنتج معين، قم بتشغيل الأمر التالي:

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

لتمكين إعداد النهج لمنتج معين، قم بتشغيل الأمر التالي:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

لتعطيل إعداد النهج لمنتج معين، قم بتشغيل الأمر التالي:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>مثال على البرنامج النصي لتعطيل AllowSelfServicePurchase

يوضح لك المثال التالي كيفية استيراد وحدة **MSCommerce**، وتسجيل الدخول باستخدام حسابك، والحصول على **ProductId** Power Automate لكل مستخدم، ثم تعطيل **AllowSelfServicePurchase** لهذا المنتج.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate per user'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

إذا كانت هناك قيم متعددة للمنتج، يمكنك تشغيل الأمر بشكل فردي لكل قيمة كما هو موضح في المثال التالي:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>استكشاف الأخطاء وإصلاحها

### <a name="problem"></a>المشكله

تظهر رسالة الخطأ التالية:

> HandleError : فشل استرداد النهج باستخدام PolicyId 'AllowSelfServicePurchase', ErrorMessage - تم إغلاق الاتصال الأساسي: حدث خطأ غير متوقع في عملية إرسال.

قد يكون ذلك بسبب إصدار أقدم من بروتوكول أمان طبقة النقل (TLS). لتوصيل هذه الخدمة، تحتاج إلى استخدام TLS 1.2 أو إصدار أحدث

### <a name="solution"></a>الحل

الترقية إلى TLS 1.2. يقوم بناء الجملة التالي بتحديث بروتوكول أمان ServicePointManager إلى TLS1.2:

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

لمعرفة المزيد، راجع [كيفية تمكين TLS 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>المحتويات ذات الصلة

[إدارة مشتريات الخدمة الذاتية (المسؤول)](manage-self-service-purchases-admins.md) (مقالة)

[الأسئلة المتداولة حول شراء الخدمة الذاتية](self-service-purchase-faq.yml) (مقالة)
