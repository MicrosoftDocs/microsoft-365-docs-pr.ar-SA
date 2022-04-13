---
title: الحدود في حالة eDiscovery الأساسية
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: تصف هذه المقالة الحدود في حالة eDiscovery الأساسية في Microsoft 365.
ms.openlocfilehash: 2d920fbe5973d07b7da656d6247038ab785bbe5c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822639"
---
# <a name="limits-in-core-ediscovery"></a>الحدود في Core eDiscovery

يسرد الجدول التالي حدود حالات eDiscovery الأساسية ويحتفظ بالحالة eDiscovery الأساسية. لمزيد من المعلومات حول Core eDiscovery، راجع [نظرة عامة على Core eDiscovery](./get-started-core-ediscovery.md).
    
  | وصف الحد | الحد |
  |:-----|:-----|
  |الحد الأقصى لعدد الحالات لمؤسسة ما.  <br/> |لا يوجد حد  <br/> |
  |الحد الأقصى لعدد حالات الاحتجاز لمؤسسة.  <br/> |10,000  <br/> |
  |الحد الأقصى لعدد علب البريد في قائمة احتجاز واحدة. يتضمن هذا الحد الإجمالي المدمج لعلب بريد المستخدمين وعلب البريد المقترنة بمجموعات مجموعات Microsoft 365 Microsoft Teams وعلب البريد Yammer.  <br/> |1,000  <br/> |
  |الحد الأقصى لعدد المواقع في حالة احتجاز واحدة. يتضمن هذا الحد الإجمالي المدمج لمواقع OneDrive for Business ومواقع SharePoint والمواقع المقترنة بمجموعات مجموعات Microsoft 365 Microsoft Teams Yammer.  <br/> |100  <br/> |
  |الحد الأقصى لعدد الحالات المعروضة على الصفحة الرئيسية الأساسية ل eDiscovery، والحد الأقصى لعدد العناصر المعروضة على علامات التبويب "عمليات الاحتجاز" و"عمليات البحث" و"التصدير" ضمن حالة ما. <sup>1</sup> |1,000|

   > [!NOTE]
   > <sup>1</sup> لعرض قائمة بأكثر من 1000 حالة أو احتجاز أو عمليات بحث أو تصدير، يمكنك استخدام أوامر cmdlets Office 365 Security & Compliance PowerShell:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

لمزيد من المعلومات حول الحدود المتعلقة بعمليات البحث والتصدير المقترنة بحالة eDiscovery الأساسية، راجع [حدود البحث في المحتوى و Core eDiscovery](limits-for-content-search.md).