---
title: الحدود في حالة eDiscovery (قياسي)
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
description: تصف هذه المقالة الحدود في حالة eDiscovery (قياسي) في Microsoft 365.
ms.openlocfilehash: 4eb43687e92d90179ff24d69827c3c2889d82b47
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971507"
---
# <a name="limits-in-ediscovery-standard"></a>الحدود في eDiscovery (قياسي)

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