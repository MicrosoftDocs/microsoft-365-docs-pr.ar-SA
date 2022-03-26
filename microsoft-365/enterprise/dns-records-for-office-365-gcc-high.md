---
title: سجلات DNS ل Office 365 سحابة القطاع الحكومي High
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'ملخص: سجلات DNS Office 365 سحابة القطاع الحكومي High'
hideEdit: true
ms.openlocfilehash: 80c1a5d4473af0877e67b6bc9e14a9ffd890e3ba
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63569584"
---
# <a name="dns-records-for-office-365-gcc-high"></a>سجلات DNS ل Office 365 سحابة القطاع الحكومي High

*تنطبق هذه المقالة على Office 365 سحابة القطاع الحكومي عالية Microsoft 365 سحابة القطاع الحكومي عالية*

كجزء من الالإضافة إلى Office 365 سحابة القطاع الحكومي عالية، ستحتاج إلى إضافة مجالي SMTP وSIP إلى مستأجر الخدمات عبر الإنترنت.  يمكنك القيام بذلك باستخدام أمر cmdlet New-MsolDomain Azure AD PowerShell أو استخدام [مدخل Azure Government لبدء](https://portal.azure.us) عملية إضافة المجال وإثبات الملكية.

بعد إضافة المجالات إلى نطاق المستأجر والتحقق من صحتها، استخدم الإرشادات التالية لإضافة سجلات DNS المناسبة للخدمات أدناه.  قد تحتاج إلى تعديل الجدول أدناه ليتناسب مع احتياجات مؤسستك فيما يتعلق بسجلات (سجلات MX) الواردة وأي سجل (سجلات) موجود Exchange اكتشاف تلقائي (سجلات) موجودة لديك.  نوصي بشدة بتنسيق سجلات DNS هذه مع فريق المراسلة لتجنب أي انقطاع أو سوء تسليم للبريد الإلكتروني.

## <a name="exchange-online"></a>Exchange Online

| النوع | الأولوية | اسم المضيف | نقاط إلى العنوان أو القيمة | TTL |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant.mail.protection.office365.us* (راجع أدناه لمزيد من التفاصيل) | ساعة واحدة |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | ساعة واحدة |
| CNAME | - | autodiscover | autodiscover.office365.us | ساعة واحدة |

### <a name="exchange-autodiscover-record"></a>Exchange الاكتشاف التلقائي

إذا كان لديك Exchange Server، نوصي بترك السجل الموجود في مكانه أثناء الترحيل إلى Exchange Online، وتحديث هذا السجل بمجرد إكمال الترحيل. 

### <a name="exchange-online-mx-record"></a>Exchange Online MX

تتبع قيمة سجل MX للمجالات المقبولة تنسيقا قياسيا كما هو ملاحظ أعلاه: *tenant.mail.protection.office365.us*، استبدال المستأجر بجزء أول من اسم المستأجر الافتراضي.

على سبيل المثال، إذا كان اسم المستأجر contoso.onmicrosoft.us، **contoso.mail.protection.office365.us كقيمة** لسجل MX.

## <a name="skype-for-business-online"></a>Skype for Business Online

### <a name="cname-records"></a>سجلات CNAME

| النوع | اسم المضيف | نقاط إلى العنوان أو القيمة | TTL |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.gov.skypeforbusiness.us | ساعة واحدة |
| CNAME | lyncdiscover | webdir.online.gov.skypeforbusiness.us | ساعة واحدة |

### <a name="srv-records"></a>سجلات SRV

| النوع | الخدمة | البروتوكول | المنفذ | الوزن | الأولوية | الاسم | الهدف | TTL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_tls | 443 | 1 | 100 | @ | sipdir.online.gov.skypeforbusiness.us | ساعة واحدة |
| SRV | \_sipfederationtls | \_tcp | 5061 | 1 | 100 | @ | sipfed.online.gov.skypeforbusiness.us | ساعة واحدة |

## <a name="other-dns-records"></a>سجلات DNS الأخرى

> [!IMPORTANT]
> إذا كان لديك سجل *CNAME msoid* موجود في منطقة DNS، فيجب إزالة السجل من DNS في الوقت الحالي.  لا يتوافق سجل msoid مع Microsoft 365 Enterprise التطبيقات *(Office 365 ProPlus سابقا)* وسيمنع التنشيط من النجاح.
