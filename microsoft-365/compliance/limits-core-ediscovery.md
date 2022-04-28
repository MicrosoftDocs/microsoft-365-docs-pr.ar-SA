---
title: الحدود في حالة eDiscovery (قياسي)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: تصف هذه المقالة الحدود في حالة eDiscovery (قياسي) في Microsoft 365.
ms.openlocfilehash: 6cc058bee09563d6a9914b9602b2fc6a3bfdf7f6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093032"
---
# <a name="limits-in-ediscovery-standard"></a>الحدود في eDiscovery (قياسي)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يسرد الجدول التالي حدود حالات eDiscovery (قياسي) ويحتفظ بالحالة eDiscovery (قياسي). لمزيد من المعلومات حول Microsoft Purview eDiscovery (قياسي)، راجع [نظرة عامة على eDiscovery (Standard).](./get-started-core-ediscovery.md)
    
  | وصف الحد | الحد |
  |:-----|:-----|
  |الحد الأقصى لعدد الحالات لمؤسسة ما.  <br/> |لا يوجد حد  <br/> |
  |الحد الأقصى لعدد حالات الاحتجاز لمؤسسة.  <br/> |10,000  <br/> |
  |الحد الأقصى لعدد علب البريد في قائمة احتجاز واحدة. يتضمن هذا الحد الإجمالي المدمج لعلب بريد المستخدمين وعلب البريد المقترنة بمجموعات مجموعات Microsoft 365 Microsoft Teams وعلب البريد Yammer.  <br/> |1,000  <br/> |
  |الحد الأقصى لعدد المواقع في حالة احتجاز واحدة. يتضمن هذا الحد الإجمالي المدمج لمواقع OneDrive for Business ومواقع SharePoint والمواقع المقترنة بمجموعات مجموعات Microsoft 365 Microsoft Teams Yammer.  <br/> |100  <br/> |
  |الحد الأقصى لعدد الحالات المعروضة على الصفحة الرئيسية eDiscovery (قياسي)، والحد الأقصى لعدد العناصر المعروضة في علامات التبويب "احتجاز" و"عمليات البحث" و"التصدير" ضمن حالة ما. <sup>1</sup> |1,000|

   > [!NOTE]
   > <sup>1</sup> لعرض قائمة بأكثر من 1000 حالة أو احتجاز أو عمليات بحث أو تصدير، يمكنك استخدام أوامر cmdlets Office 365 Security & Compliance PowerShell:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

لمزيد من المعلومات حول الحدود المتعلقة بعمليات البحث والتصدير المقترنة بحالة eDiscovery (قياسي)، راجع [حدود البحث في المحتوى وeDiscovery (قياسي).](limits-for-content-search.md)