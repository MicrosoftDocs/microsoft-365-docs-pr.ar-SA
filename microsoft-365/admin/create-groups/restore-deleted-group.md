---
title: استعادة مجموعة Microsoft 365 محذوفة
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: يتم الاحتفاظ بالمجموعة المحذوفة لمدة 30 يوما ولا يزال بإمكانك استعادة المجموعة. بعد مرور 30 يوما، يتم حذف المجموعة ومحتواها بشكل دائم.
ms.openlocfilehash: 926cfa18972a7ca72009258b02b565bd28a183be
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63567301"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>استعادة مجموعة Microsoft 365 محذوفة

إذا قمت بحذف مجموعة، سيتم الاحتفاظ بها لمدة 30 يوما بشكل افتراضي. تعتبر فترة ال 30 يوما هذه "حذفا ناعما" لأنه لا يزال بإمكانك استعادة المجموعة. بعد مرور 30 يوما، يتم حذف المجموعة والمحتويات المقترنة بها بشكل دائم ولا يمكن استعادتها.

عند استعادة مجموعة، يتم استعادة المحتوى التالي:
  
- Azure Active Directory (AD) Microsoft 365 المجموعات والخصائص والأعضاء.
    
- عناوين البريد الإلكتروني للمجموعة.
    
- Exchange Online الوارد والتقويم المشترك.
    
- SharePoint موقع الفريق والملفات عبر الإنترنت.
    
- OneNote الملاحظات
    
- Planner
    
- الفرق

- Yammer مجموعة ومحتوى مجموعة (إذا Microsoft 365 المجموعة من Yammer)

- مساحة عمل Power BI [الكلاسيكية](/power-bi/collaborate-share/service-create-workspaces)

> [!NOTE]
> تصف هذه المقالة استعادة Microsoft 365 فقط. لا يمكن استعادة كل المجموعات الأخرى بمجرد حذفها.

## <a name="restore-a-group"></a>استعادة مجموعة

# <a name="outlook"></a>[Outlook](#tab/outlook)

إذا كنت مالك مجموعة Microsoft 365، يمكنك استعادة المجموعة بنفسك في Outlook على ويب باتباع الخطوات التالية:

1. في صفحة [المجموعات المحذوفة،](https://outlook.office.com/people/group/deleted) حدد الخيار **إدارة المجموعات** ضمن عقدة  المجموعات، ثم اختر **محذوف**.

2. انقر فوق علامة **التبويب** استعادة بجانب المجموعة التي تريد استعادتها.

إذا لم تظهر المجموعة المحذوفة هنا، فاتصل بمسؤول.

# <a name="admin-center"></a>[مركز الإدارة](#tab/admin-center)

إذا كنت مسؤولا عاما أو مسؤول مجموعات، يمكنك استعادة مجموعة محذوفة في مركز مسؤولي Microsoft 365:

1. انتقل إلى [مركز الإدارة](https://admin.microsoft.com).
2. قم **بتوسيع المجموعات**، ثم انقر فوق **المجموعات المحذوفة**.
3. حدد المجموعة التي تريد استعادتها، ثم انقر فوق **استعادة المجموعة**.

> [!NOTE]
> في بعض الحالات، قد يستغرق الأمر 24 ساعة حتى يتم استعادة المجموعة وكل بياناتها. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>هل لديك أسئلة حول Microsoft 365 المجموعات؟

تفضل بزيارة [مجتمع Microsoft التقني](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) لطرح الأسئلة والمشاركة في محادثات Microsoft 365 المجموعات. 
  
## <a name="related-content"></a>المحتوى ذي الصلة

[إدارة Microsoft 365 باستخدام PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (مقالة)\
[حذف المجموعات باستخدام Remove-UnifiedGroup cmdlet](/powershell/module/exchange/remove-unifiedgroup) (مقالة)\
[إدارة إعدادات موقع الفريق المتصل بالمجموعة](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) (مقالة)\
[حذف مجموعة في Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f) (مقالة)
