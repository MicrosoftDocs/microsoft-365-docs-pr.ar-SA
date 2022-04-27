---
title: إضافة مجال إلى إيجار عميل باستخدام Windows PowerShell لشركاء DAP
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
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'ملخص: استخدم PowerShell Microsoft 365 لإضافة اسم مجال بديل إلى مستأجر عميل موجود.'
ms.openlocfilehash: c4dcdb34f9065009ccaa77d23222601506b537b5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099027"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>إضافة مجال إلى إيجار عميل باستخدام Windows PowerShell لشركاء إذن الوصول المفوض (DAP)

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك إنشاء مجالات جديدة وإقرانها بإجارة العميل مع PowerShell Microsoft 365 أسرع من استخدام مركز مسؤولي Microsoft 365.

شركاء إذن الوصول المفوض (DAP) هم شركاء موفري حلول السحابة (CSP) وSyndication. وهي غالبا ما تكون موفرة للشبكات أو الاتصالات لشركات أخرى. وهي تقوم بتجميع اشتراكات Microsoft 365 في عروض الخدمة لعملائها. عندما يبيعون اشتراكا Microsoft 365، يتم منحهم تلقائيا أذونات الإدارة نيابة عن (AOBO) إلى إيجارات العميل حتى يتمكنوا من إدارة إيجارات العميل والإبلاغ عنها.
## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

تتطلب منك الإجراءات الواردة في هذا الموضوع الاتصال [الاتصال Microsoft 365 باستخدام PowerShell](connect-to-microsoft-365-powershell.md).

تحتاج أيضا إلى بيانات اعتماد مسؤول المستأجر الشريك.

تحتاج أيضا إلى المعلومات التالية:

- تحتاج إلى اسم المجال المؤهل بالكامل (FQDN) الذي يريده العميل.

- تحتاج إلى **TenantId** الخاص بالعميل.

- يجب تسجيل FQDN لدى جهة تسجيل خدمة أسماء مجالات الإنترنت (DNS)، مثل GoDaddy. لمزيد من المعلومات حول كيفية تسجيل اسم مجال بشكل عام، راجع [كيفية شراء اسم مجال](../admin/get-help-with-domains/buy-a-domain-name.md).

- تحتاج إلى معرفة كيفية إضافة سجل TXT إلى منطقة DNS المسجلة لسجل DNS. لمزيد من المعلومات حول كيفية إضافة سجل TXT، راجع [إضافة سجلات DNS لتوصيل مجالك](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). إذا لم تعمل هذه الإجراءات نيابة عنك، فستحتاج إلى العثور على الإجراءات الخاصة بسجل DNS.

## <a name="create-domains"></a>إنشاء مجالات

 من المحتمل أن يطلب منك عملاؤك إنشاء مجالات إضافية لإقرانها بإجارتهم لأنهم لا يريدون أن يكون مجال .onmicrosoft.com الافتراضي \<domain>المجال الأساسي الذي يمثل هويات الشركة الخاصة بهم للعالم. يرشدك هذا الإجراء خلال إنشاء مجال جديد مقترن بإجرة العميل.

> [!NOTE]
> لتنفيذ بعض هذه العمليات، يجب تعيين حساب المسؤول الشريك الذي تسجل الدخول باستخدامه إلى **الإدارة الكاملة** لتعيين **الوصول الإداري إلى الشركات التي تدعمها التي تم** العثور عليها في تفاصيل حساب المسؤول في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>. لمزيد من المعلومات حول إدارة أدوار الشركاء، راجع [الشركاء: تقديم الإدارة المفوضة](https://go.microsoft.com/fwlink/p/?LinkId=532435).

### <a name="create-the-domain-in-azure-active-directory"></a>إنشاء المجال في Azure Active Directory

ينشئ هذا الأمر المجال في Azure Active Directory ولكنه لا يقوم بإقرانه بالمجال المسجل بشكل عام. يأتي ذلك عندما تثبت أنك تملك المجال المسجل علنا لدى Microsoft Microsoft 365 للمؤسسات.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>الحصول على بيانات سجل التحقق من DNS TXT

 ستقوم Microsoft 365 بإنشاء البيانات المحددة التي تحتاج إلى وضعها في سجل التحقق من DNS TXT. للحصول على البيانات، قم بتشغيل هذا الأمر.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

سيمنحك هذا الإخراج مثل:

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> ستحتاج إلى هذا النص لإنشاء سجل TXT في منطقة DNS المسجلة بشكل عام. تأكد من نسخه وحفظه.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>إضافة سجل TXT إلى منطقة DNS المسجلة بشكل عام

قبل أن تبدأ Microsoft 365 في قبول نسبة استخدام الشبكة التي يتم توجيهها إلى اسم المجال المسجل بشكل عام، يجب إثبات ملكيتك وأن لديك أذونات المسؤول للمجال. يمكنك إثبات ملكيتك للمجال عن طريق إنشاء سجل TXT في المجال. لا يقوم سجل TXT بأي شيء في مجالك، ويمكن حذفه بعد تأسيس ملكيتك للمجال. لإنشاء سجلات TXT، اتبع الإجراءات في [إضافة سجلات DNS لتوصيل مجالك](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). إذا لم تعمل هذه الإجراءات نيابة عنك، فستحتاج إلى العثور على الإجراءات الخاصة بسجل DNS.

تأكيد الإنشاء الناجح لسجل TXT عبر nslookup. اتبع بناء الجملة هذا.

```console
nslookup -type=TXT <FQDN of registered domain>
```

سيمنحك هذا الإخراج مثل:

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>التحقق من صحة ملكية المجال في Microsoft 365

في هذه الخطوة الأخيرة، يمكنك التحقق من صحة Microsoft 365 أنك تملك المجال المسجل بشكل عام. بعد هذه الخطوة، ستبدأ Microsoft 365 في قبول نسبة استخدام الشبكة التي تم توجيهها إلى اسم المجال الجديد. لإكمال عملية إنشاء المجال وتسجيله، قم بتشغيل هذا الأمر.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

لن يرجع هذا الأمر أي إخراج، لذا للتأكد من أن هذا يعمل، قم بتشغيل هذا الأمر.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

سيؤدي هذا إلى إرجاع شيء مثل هذا

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>راجع أيضًا

[تعليمات للشركاء](https://go.microsoft.com/fwlink/p/?LinkID=533477)
