---
title: إضافة مجال إلى إيجار عميل مع Windows PowerShell DAP
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
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'ملخص: استخدم PowerShell Microsoft 365 لإضافة اسم مجال بديل إلى مستأجر عميل موجود.'
ms.openlocfilehash: 1a121407ebe242747a693084289e972e56e1cbee
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569385"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>إضافة مجال إلى إيجار عميل Windows PowerShell لشركاء إذن الوصول المفوض (DAP)

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك إنشاء مجالات جديدة وإقرانها مع إيجار العميل باستخدام PowerShell Microsoft 365 أسرع من استخدام مركز مسؤولي Microsoft 365.

شركاء إذن الوصول المفوض (DAP) هم شركاء Syndication وموفرو حلول السحابة (CSP). فهي غالبا ما تكون موفري شبكة أو اتصالات لشركات أخرى. كما يمكنهم Microsoft 365 اشتراكاتهم في عروض الخدمات الخاصة بهم للعملاء. عند بيعهم لاشتراك Microsoft 365، يتم منحهم تلقائيا أذونات الإدارة بالنيابة عن (AOBO) إلى أذونات العميل بحيث يمكنهم إدارة أذونات العميل والتقارير بشأنها.
## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

تتطلب الإجراءات في هذا الموضوع الاتصال الاتصال [Microsoft 365 PowerShell](connect-to-microsoft-365-powershell.md).

تحتاج أيضا إلى بيانات اعتماد مسؤول المستأجر الشريك.

تحتاج أيضا إلى المعلومات التالية:

- أنت بحاجة إلى اسم المجال المؤهل بالكامل (FQDN) الذي يريده العميل.

- أنت بحاجة إلى **TenantId الخاص للعميل**.

- يجب أن تكون FQDN مسجلة لدى جهة تسجيل خدمة أسماء مجالات الإنترنت (DNS)، مثل GoDaddy. لمزيد من المعلومات حول كيفية تسجيل اسم مجال بشكل عام، راجع [كيفية شراء اسم مجال](../admin/get-help-with-domains/buy-a-domain-name.md).

- يجب أن تعرف كيفية إضافة سجل TXT إلى منطقة DNS المسجلة لدى جهة تسجيل DNS. لمزيد من المعلومات حول كيفية إضافة سجل TXT، راجع [إضافة سجلات DNS لتوصيل مجالك](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). إذا لم تكن هذه الإجراءات تعمل من أجلك، ستحتاج إلى العثور على الإجراءات الخاصة جهة تسجيل DNS.

## <a name="create-domains"></a>إنشاء مجالات

 من المرجح \<domain>أن يطلب منك عملاؤك إنشاء مجالات إضافية لاقرانها بأوجارهم لأنهم لا يرغبون في أن يكون مجال onmicrosoft.com الافتراضي المجال الأساسي الذي يمثل هويات شركاتهم للعالم. يرحلك هذا الإجراء من خلال إنشاء مجال جديد مقترن بأوجار العميل.

> [!NOTE]
> لتنفيذ بعض هذه العمليات، يجب تعيين حساب مسؤول الشريك الذي تقوم تسجيل الدخول باستخدامه إلى الإدارة الكاملة  لإعداد تعيين الوصول الإداري  إلى الشركات التي تدعمها والمعثر عليه في تفاصيل حساب المسؤول في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>. لمزيد من المعلومات حول إدارة أدوار مسؤولي الشركاء، راجع [الشركاء: عرض الإدارة المفوضة](https://go.microsoft.com/fwlink/p/?LinkId=532435).

### <a name="create-the-domain-in-azure-active-directory"></a>إنشاء المجال في Azure Active Directory

ينشئ هذا الأمر المجال في Azure Active Directory ولكنه لا يقوم بربطه بالمجال المسجل بشكل عام. يأتي ذلك عندما تثبت أنك تملك المجال المسجل بشكل عام في Microsoft Microsoft 365 للمؤسسات.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع **Msol** في اسمها. لمواصلة استخدام هذه cmdlets، يجب تشغيلها من Windows PowerShell.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>الحصول على بيانات سجل التحقق من TXT ل DNS

 Microsoft 365 إنشاء البيانات المحددة التي تحتاج إلى وضعها في سجل التحقق من TXT ل DNS. للحصول على البيانات، يمكنك تشغيل هذا الأمر.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

سيمنحك ذلك إخراجا مثل:

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> ستحتاج إلى هذا النص لإنشاء سجل TXT في منطقة DNS المسجلة بشكل عام. تأكد من نسخه وحفظه.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>إضافة سجل TXT إلى منطقة DNS المسجلة بشكل عام

قبل Microsoft 365 قبول حركة المرور الموجهة إلى اسم المجال المسجل بشكل عام، يجب أن تثبت أنك تملك أذونات المسؤول وأن لديك أذونات المسؤول للمجال. تثبت أنك تملك المجال من خلال إنشاء سجل TXT في المجال. لا يفعل سجل TXT أي شيء في مجالك، ويمكن حذفه بعد إنشاء ملكيتك للمجال. لإنشاء سجلات TXT، اتبع الإجراءات في [إضافة سجلات DNS لتوصيل مجالك](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). إذا لم تكن هذه الإجراءات تعمل معك، تحتاج إلى العثور على الإجراءات الخاصة جهة تسجيل DNS.

تأكد من نجاح إنشاء سجل TXT عبر nslookup. اتبع بناء الجملة هذا.

```console
nslookup -type=TXT <FQDN of registered domain>
```

سيمنحك ذلك إخراجا مثل:

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>التحقق من ملكية المجال في Microsoft 365

في هذه الخطوة الأخيرة، تحقق Microsoft 365 أنك تملك المجال المسجل بشكل عام. بعد هذه الخطوة، Microsoft 365 قبول حركة المرور التي تم توجيهها إلى اسم المجال الجديد. لإكمال عملية إنشاء المجال وتسجيله، تشغيل هذا الأمر.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

لن يرجع هذا الأمر أي إخراج، لذا لتأكيد عمل ذلك، يمكنك تشغيل هذا الأمر.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

سيرجع هذا شيئا مثل هذا

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>راجع أيضًا

[تعليمات للشركاء](https://go.microsoft.com/fwlink/p/?LinkID=533477)
