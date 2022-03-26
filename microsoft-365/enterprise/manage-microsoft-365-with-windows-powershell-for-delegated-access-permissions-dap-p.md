---
title: إدارة Microsoft 365 باستخدام Windows PowerShell DAP
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: hub-page
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
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: كيف يمكن لشركاء syndication Cloud Solution Provider (CSP) استخدام Windows PowerShell لإدارة Microsoft 365 المستأجرين للعملاء.
ms.openlocfilehash: 2678489d1e281a60d230c65e29b358dff5f1a8ad
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572867"
---
# <a name="how-to-manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-partners"></a>كيفية إدارة Microsoft 365 مع Windows PowerShell أذونات الوصول المفوض

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

شركاء إذن الوصول المفوض (DAP) هم شركاء Syndication وموفرو حلول السحابة (CSP). العديد منهم هم موفرو الشبكة أو الاتصالات. يتم تجميع Microsoft 365 اشتراكات في عروض الخدمات الخاصة بهم. عند بيعهم لاشتراك Microsoft 365، يتم منحهم تلقائيا أذونات الإدارة بالنيابة عن (AOBO) إلى أذونات العميل العشرية حتى يمكنهم إدارة هذه الأذونات والتقارير بشأنها. ويصعب تنفيذ هذه المهام في مركز مسؤولي Microsoft 365. من الأسهل استخدام PowerShell Microsoft 365 تنفيذ مهام إدارية مثل:
- سرد جميع **مستأجري** العملاء ومجالاتهم 
- تحديد جميع المستخدمين في إيجار العميل والتراخيص المعينة لهم
> [!NOTE]
> لا يمكن تنفيذ بعض المهام الإدارية إلا في PowerShell.

تظهر المقالات التالية كيفية استخدام شركاء Syndication وCSP ل PowerShell لإدارة اضمان العملاء:
  
- [إدارة Microsoft 365 المستأجرين باستخدام Windows PowerShell أذونات الوصول المفوض (DAP)](manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [إضافة مجال إلى إيجار عميل Windows PowerShell لشركاء إذن الوصول المفوض (DAP)](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
- [استرداد بيانات إعداد تقارير مستأجر العميل باستخدام Windows PowerShell أذونات الوصول المفوض (DAP)](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
