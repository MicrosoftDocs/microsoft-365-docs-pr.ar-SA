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
ms.openlocfilehash: 28db179aea27bfff2520199d89b93c8260b7f089
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63569274"
---
# <a name="limits-in-core-ediscovery"></a>الحدود في eDiscovery الأساسي

يسرد الجدول التالي حدود حالات eDiscovery الأساسية ويحتجز المقترنة ب حالة eDiscovery أساسية. لمزيد من المعلومات حول eDiscovery الأساسي، راجع [نظرة عامة حول eDiscovery الأساسي](./get-started-core-ediscovery.md).
    
  | وصف الحد | الحد |
  |:-----|:-----|
  |الحد الأقصى لعدد الحالات في مؤسسة.  <br/> |بلا حد  <br/> |
  |الحد الأقصى لعدد الحالات المحتجزة في مؤسسة.  <br/> |10,000  <br/> |
  |الحد الأقصى لعدد علب البريد في حالة واحدة. يتضمن هذا الحد الإجمالي المجمع لعلب بريد المستخدمين، علب البريد المقترنة Microsoft 365 ومجموعات Microsoft Teams ومجموعات Yammer.  <br/> |1,000  <br/> |
  |الحد الأقصى لعدد المواقع في حالة واحدة. يتضمن هذا الحد الإجمالي المجمع لمواقع OneDrive for Business ومواقع SharePoint ومواقع الويب والمواقع المقترنة Microsoft 365 ومجموعات Microsoft Teams ومجموعات Yammer.  <br/> |100  <br/> |
  |الحد الأقصى لعدد الحالات المعروضة على الصفحة الرئيسية ل eDiscovery الأساسية، والحد الأقصى لعدد العناصر المعروضة على علامات التبويب "عمليات البحث" و"عمليات البحث" ضمن علامة التبويب "تصدير" ضمن حالة. <sup>1</sup> |1,000|
  |||

   > [!NOTE]
   > <sup>1</sup> لعرض قائمة تتضمن أكثر من 1,000 حالة، أو عمليات التحميل، أو عمليات البحث، أو التصدير، يمكنك استخدام cmdlets المطابقة Office 365 Security & Compliance PowerShell:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

للحصول على مزيد من المعلومات حول الحدود المتعلقة بعمليات البحث والتصدير المقترنة ب حالة eDiscovery الأساسية، راجع قيود البحث في [المحتوى و eDiscovery الأساسي](limits-for-content-search.md).