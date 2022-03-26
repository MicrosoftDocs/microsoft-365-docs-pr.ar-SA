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
description: تعرف على كيفية استخدام أمر cmdlet AllowSelfServicePurchase PowerShell ل تشغيل شراء الخدمة الذاتية أو إيقاف تشغيله.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 12/15/2021
ms.openlocfilehash: a3800f82386fafe509d9bdabb25cd91422cf058d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566977"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>استخدام AllowSelfServicePurchase للوحدة النمطية MSCommerce PowerShell

تتوفر **الآن الوحدة النمطية ل MSCommerce** PowerShell في [معرض PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery). تتضمن الوحدة النمطية قيمة المعلمة **PolicyID** ل **AllowSelfServicePurchase** التي تسمح لك بالتحكم في ما إذا كان يمكن للمستخدمين في مؤسستك إجراء عمليات شراء الخدمة الذاتية.

يمكنك استخدام الوحدة النمطية **ل MSCommerce** PowerShell من أجل:

- عرض الحالة الافتراضية **لقيمة المعلمة AllowSelfServicePurchase** — سواء تم تمكينها أو تعطيلها
- عرض قائمة بالمنتجات القابلة للتطبيق وما إذا كان الشراء الذاتي للخدمة يتم تمكينه أو تعطيله
- عرض الإعداد الحالي لمنتج معين أو تعديله إما لتمكينه أو تعطيله

## <a name="requirements"></a>المتطلبات

لاستخدام الوحدة النمطية **ل MSCommerce** PowerShell، ستحتاج إلى:

- جهاز Windows 10
- PowerShell 5 أو أقل. حاليا، PowerShell 6.x/7.x غير معتمد مع هذه الوحدة النمطية.
- إذن المسؤول للجهاز
- دور مسؤول الفوترة أو العام للمستأجر

## <a name="install-the-mscommerce-powershell-module"></a>تثبيت الوحدة النمطية ل MSCommerce PowerShell

يمكنك تثبيت وحدة **MSCommerce** PowerShell النمطية على Windows 10 مرة واحدة ثم استيرادها إلى كل جلسة PowerShell تبدأ بها. قم **بتنزيل الوحدة النمطية ل MSCommerce** PowerShell من [معرض PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery).

لتثبيت وحدة **MSCommerce** PowerShell النمطية مع **PowerShellGet**، قم بتشغيل الأمر التالي:

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>استيراد MSCommerce إلى جلسة عمل PowerShell

بعد تثبيت الوحدة النمطية على جهاز Windows 10، يمكنك استيرادها إلى كل جلسة PowerShell تبدأ بها. لاستيرادها إلى جلسة عمل PowerShell، تشغيل الأمر التالي:

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>الاتصال إلى MSCommerce باستخدام بيانات الاعتماد الخاصة بك

للاتصال الوحدة النمطية PowerShell باستخدام بيانات الاعتماد، قم بتشغيل الأمر التالي.

```powershell
Connect-MSCommerce
```

يربط هذا الأمر جلسة PowerShell الحالية ب مستأجر Azure Active Directory. يطالبك الأمر باسم المستخدم وكلمة المرور للمستأجر الذي تريد الاتصال به. إذا تم تمكين المصادقة متعددة العوامل للحصول على بيانات الاعتماد الخاصة بك، يمكنك استخدام الخيار التفاعلي لتسجيل الدخول.

## <a name="view-details-for-allowselfservicepurchase"></a>عرض تفاصيل AllowSelfServicePurchase

لعرض وصف لقيمة المعلمة **AllowSelfServicePurchase** مع الحالة الافتراضية، استنادا إلى مؤسستك، يمكنك تشغيل الأمر التالي:

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>عرض قائمة منتجات شراء الخدمة الذاتية ووضعها

لعرض قائمة بجميع منتجات شراء الخدمة الذاتية المتوفرة ووضع كل منها، يمكنك تشغيل الأمر التالي:

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

يسرد الجدول التالي المنتجات المتوفرة **ومنتجاتها**.

| المنتج | ProductId |
|-----------------------------|--------------|
| Power Apps لكل مستخدم | CFQ7TTC0KP0P |
| Power Automate لكل مستخدم | CFQ7TTC0KP0N |
| Power Automate RPA | CFQ7TTC0KXG6  |
| Power BI Premium (مستقل) | CFQ7TTC0KXG7  |
| Power BI Pro | CFQ7TTC0L3PB |
| Project (النظام 1)* | CFQ7TTC0HDB1 |
| Project (النظام 3)* | CFQ7TTC0HDB0 |
| Visio (النظام 1)* | CFQ7TTC0HD33 |
| Visio (النظام 2)* | CFQ7TTC0HD32 |
| Windows 365 Enterprise | CFQ7TTC0HHS9 |
| Windows 365 Business | CFQ7TTC0J203 |
| Windows 365 Business مع Windows المختلطة | CFQ7TTC0HX99 |

*تم تغيير هذه الم IDS. إذا قمت مسبقا بحظر المنتجات باستخدام الم IDS القديمة، يتم حظرها تلقائيا باستخدام الم IDS الجديدة. لا حاجة إلى أي عمل إضافي.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>عرض حالة AllowSelfServicePurchase أو تعيينها

بعد عرض قائمة المنتجات المتوفرة لشراء الخدمة الذاتية، يمكنك عرض الإعداد لمنتج معين أو تعديله.

للحصول على إعداد النهج لمنتج معين، يمكنك تشغيل الأمر التالي:

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

لتمكين إعداد النهج لمنتج معين، يمكنك تشغيل الأمر التالي:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

لتعطيل إعداد النهج لمنتج معين، قم بتشغيل الأمر التالي:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>مثال برنامج نصي لتعطيل AllowSelfServicePurchase

يستعرض المثال التالي كيفية استيراد وحدة **MSCommerce** النمطية، تسجيل الدخول باستخدام حسابك، والحصول على **ProductId** ل Power Automate، ثم تعطيل **AllowSelfServicePurchase** لهذا المنتج.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

إذا كانت هناك قيم متعددة للمنتج، يمكنك تشغيل الأمر بشكل فردي لكل قيمة كما هو موضح في المثال التالي:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>استكشاف الأخطاء وإصلاحها

### <a name="problem"></a>المشكلة

تظهر رسالة الخطأ التالية:

> معالج : فشل استرداد النهج باستخدام PolicyId 'AllowSelfServicePurchase', ErrorMessage - تم إغلاق الاتصال الأساسي: حدث خطأ غير متوقع في عملية إرسال.

قد يعود سبب ذلك إلى إصدار أقدم من "أمان طبقة النقل" (TLS). لتوصيل هذه الخدمة، ستحتاج إلى استخدام TLS 1.2 أو أكبر

### <a name="solution"></a>الحل

الترقية إلى TLS 1.2. يتم تحديث بناء الجملة التالي بروتوكول أمان ServicePointManager إلى TLS1.2:

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

لمعرفة المزيد، [راجع كيفية تمكين TLS 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>المحتوى ذي الصلة

[إدارة عمليات شراء الخدمة الذاتية (المسؤول)](manage-self-service-purchases-admins.md) (مقالة)

[الأسئلة الشائعة حول شراء الخدمة الذاتية](self-service-purchase-faq.yml) (مقالة)
