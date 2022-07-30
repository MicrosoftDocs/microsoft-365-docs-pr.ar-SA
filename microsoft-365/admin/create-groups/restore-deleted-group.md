---
title: استعادة مجموعة Microsoft 365 محذوفة
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: scotv
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
description: يتم الاحتفاظ بالمجموعة المحذوفة لمدة 30 يوما ولا يزال بإمكانك استعادة المجموعة. بعد 30 يوما، يتم حذف المجموعة ومحتواها نهائيا.
ms.openlocfilehash: f16d8b13ad020aec48d39a61e2429b088cc5f2d1
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084180"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>استعادة مجموعة Microsoft 365 محذوفة

إذا قمت بحذف مجموعة، فسيتم الاحتفاظ بها لمدة 30 يوما بشكل افتراضي. تعتبر فترة ال 30 يوما هذه "حذفا مبدئيا" لأنه لا يزال بإمكانك استعادة المجموعة. بعد 30 يوما، يتم حذف المجموعة والمحتويات المقترنة بها بشكل دائم ولا يمكن استعادتها.

عند استعادة مجموعة، تتم استعادة المحتوى التالي:
  
- مجموعات Microsoft 365 Azure Active Directory (AD) الكائن والخصائص والأعضاء.
    
- عناوين البريد الإلكتروني للمجموعة.
    
- Exchange Online علبة الوارد والتقويم المشتركين.
    
- موقع فريق SharePoint Online وملفاته.
    
- دفتر ملاحظات OneNote
    
- Planner
    
- الفرق

- محتوى المجموعة ومجموعة Yammer (إذا تم إنشاء مجموعة Microsoft 365 من Yammer)

- [مساحة العمل الكلاسيكية](/power-bi/collaborate-share/service-create-workspaces) في Power BI

> [!NOTE]
> تصف هذه المقالة استعادة مجموعات Microsoft 365 فقط. لا يمكن استعادة كافة المجموعات الأخرى بمجرد حذفها.

## <a name="restore-a-group"></a>استعادة مجموعة

# <a name="outlook"></a>[Outlook](#tab/outlook)

إذا كنت مالك مجموعة Microsoft 365، يمكنك استعادة المجموعة بنفسك في Outlook على ويب باتباع الخطوات التالية:

1. في [صفحة المجموعات المحذوفة](https://outlook.office.com/people/group/deleted)، حدد الخيار **"إدارة المجموعات** " ضمن عقدة **"المجموعات** "، ثم اختر **"محذوفة**".

2. انقر فوق علامة التبويب **"استعادة** " إلى جانب المجموعة التي تريد استعادتها.

إذا لم تظهر المجموعة المحذوفة هنا، فاتصل بالمسؤول.

# <a name="admin-center"></a>[مركز مسؤول](#tab/admin-center)

إذا كنت مسؤولا عاما أو مسؤول مجموعات، يمكنك استعادة مجموعة محذوفة في مركز مسؤولي Microsoft 365:

1. انتقل إلى [مركز الإدارة](https://admin.microsoft.com).
2. قم بتوسيع **المجموعات**، ثم انقر فوق **المجموعات المحذوفة**.
3. حدد المجموعة التي تريد استعادتها، ثم انقر فوق **"استعادة المجموعة**".

> [!NOTE]
> في بعض الحالات، قد يستغرق الأمر 24 ساعة حتى تتم استعادة المجموعة وكافة بياناتها. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>هل لديك أسئلة حول مجموعات Microsoft 365؟

تفضل بزيارة [Microsoft Tech Community](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) لنشر الأسئلة والمشاركة في المحادثات حول مجموعات Microsoft 365. 
  
## <a name="related-content"></a>المحتويات ذات الصلة

[إدارة مجموعات Microsoft 365 باستخدام PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (مقالة)\
[حذف المجموعات باستخدام Remove-UnifiedGroup cmdlet](/powershell/module/exchange/remove-unifiedgroup) (article)\
[إدارة إعدادات موقع الفريق المتصل بالمجموعة](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) (مقالة)\
[حذف مجموعة في Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f) (مقالة)
