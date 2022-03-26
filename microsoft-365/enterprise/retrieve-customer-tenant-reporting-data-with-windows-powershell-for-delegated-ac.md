---
title: استرداد بيانات إعداد تقارير مستأجر العميل باستخدام Windows PowerShell لشركاء DAP
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.openlocfilehash: cc9046ab5c90dcb40cbf012772fd80b56f71ec79
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575282"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>استرداد بيانات إعداد تقارير مستأجر العميل باستخدام Windows PowerShell أذونات الوصول المفوض (DAP)

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

استخدم Windows PowerShell عن بعد Microsoft Exchange Online لاسترداد التقارير من مستأجري العملاء الفرديين.

يمكن لشركاء Cloud Solution Provider (CSP) الوصول إلى البيانات التي تكون تقارير مستأجر العميل مباشرة عبر Windows PowerShell البعيد Exchange Online PowerShell. يسمح هذا للشركاء بتجميع بيانات التقارير وحفظها ثم تنفيذ عمليات أخرى عليها. بعد فتح اتصال عن بعد، يكون استرداد بيانات إعداد التقارير حول إيجار العميل مماثلا لتشغيل أي أمر cmdlet مقابل إيجار العميل.

في هذه المقالة، يمكنك استخدام Windows PowerShell عن بعد Exchange Online الاتصال باستئجار عميل واحد واسترداد تقرير. بشكل افتراضي Windows PowerShell لا تدعم هذه Windows PowerShell تجميع بيانات التقارير من عدة عملاء. التقارير التي تستردها باستخدام هذا الإجراء هي فقط ل  _المفوضأورج_ الذي تتصل به.

## <a name="before-you-begin"></a>قبل البدء

- تحتاج إلى الاتصال بمستأجر Exchange Online عن بعد باستخدام Windows PowerShell. للحصول على الإرشادات، راجع الاتصال Exchange Online المستأجرين الذين Windows PowerShell عن بعد لشركاء أذونات الوصول المفوض [(DAP)](/powershell/exchange/connect-to-exchange-online-powershell)

## <a name="run-the-get-stalemailboxreport-sample"></a>تشغيل Get-StaleMailboxReport النموذجي

بعد فتح جلسة عمل بعيدة ل Exchange Online، يمكنك تشغيل هذا الأمر لاسترداد **Get-StaleMailboxReport** لنطاق التاريخ من 03/25/2015 إلى 03/31/2015.

```powershell
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

يتوفر عدد كبير من cmdlets لإعداد التقارير Exchange Online وLync Online وLync Online SharePoint Online بالإضافة إلى غيرها لتعقب الرسائل التي يمكنك استخدامها. لمعرفة المزيد حول cmdlets المتوفرة لإعداد التقارير Office 365 خدمة إعداد التقارير على الويب، راجع المواضيع في القسم التالي.

## <a name="see-also"></a>راجع أيضًا

[Office 365 على الويب لإعداد التقارير](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))

[الإبلاغ عن cmdlets في Exchange Online](/powershell/module/exchange/get-csclientdevicedetailreport)

[تعليمات للشركاء](https://go.microsoft.com/fwlink/p/?LinkID=533477)
