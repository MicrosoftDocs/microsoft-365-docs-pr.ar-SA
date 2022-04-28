---
title: استرداد بيانات تقارير مستأجر العميل باستخدام Windows PowerShell لشركاء DAP
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'ملخص: استخدم Windows PowerShell عن بعد Microsoft Exchange Online لاسترداد التقارير من مستأجري العملاء الفرديين.'
ms.openlocfilehash: 8529e95e8aefbd45cf381ff21bec49e669fd7c6a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096689"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>استرداد بيانات تقارير مستأجر العميل باستخدام Windows PowerShell لشركاء أذونات الوصول المفوض (DAP)

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

استخدم Windows PowerShell عن بعد Microsoft Exchange Online لاسترداد التقارير من مستأجري العملاء الفرديين.

يمكن لشركاء المشاركة Cloud Solution Provider (CSP) الوصول إلى البيانات التي تشكل تقارير مستأجر العميل مباشرة عبر Windows PowerShell عن بعد Exchange Online PowerShell. يتيح هذا للشركاء جمع بيانات التقارير وحفظها ثم تنفيذ عمليات أخرى عليها. بعد فتح اتصال عن بعد، يكون استرداد بيانات إعداد التقارير حول إيجار العميل مطابقا لتشغيل أي أمر cmdlet مقابل إيجار العميل.

في هذه المقالة، يمكنك استخدام Windows PowerShell عن بعد Exchange Online للاتصال باستئجار عميل واحد واسترداد تقرير. بشكل افتراضي، لا يدعم Windows PowerShell تجميع بيانات التقارير من عدة إيجارات عملاء. التقارير التي تستردها باستخدام هذا الإجراء مخصصة فقط ل  _DelegatedOrg_ الذي تتصل به.

## <a name="before-you-begin"></a>قبل البدء

- تحتاج إلى الاتصال بمستأجر Exchange Online باستخدام Windows PowerShell عن بعد. للحصول على الإرشادات، راجع [الاتصال Exchange Online المستأجرين الذين لديهم Windows PowerShell بعيد لشركاء أذونات الوصول المفوض (DAP)](/powershell/exchange/connect-to-exchange-online-powershell)

## <a name="run-the-get-stalemailboxreport-sample"></a>تشغيل عينة Get-StaleMailboxReport

بعد فتح جلسة عمل بعيدة Exchange Online، قم بتشغيل هذا الأمر لاسترداد **Get-StaleMailboxReport** لنطاق التاريخ 03/25/2015 حتى 03/31/2015.

```powershell
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

تتوفر العديد من أوامر cmdlets الأخرى لإعداد التقارير ل Exchange Online وLync Online و SharePoint Online بالإضافة إلى أوامر أخرى لتتبع الرسائل التي يمكنك استخدامها. لمعرفة المزيد حول أوامر cmdlets المتوفرة وخدمة ويب Office 365 Reporting، راجع المواضيع في القسم التالي.

## <a name="see-also"></a>راجع أيضًا

[خدمة ويب Office 365 Reporting](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))

[الإبلاغ عن أوامر cmdlets في Exchange Online](/powershell/module/exchange/get-csclientdevicedetailreport)

[تعليمات للشركاء](https://go.microsoft.com/fwlink/p/?LinkID=533477)
