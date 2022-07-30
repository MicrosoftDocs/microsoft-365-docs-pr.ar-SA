---
title: إدارة وصول الضيف في مجموعات Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
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
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: تعرف على كيفية إضافة ضيوف إلى مجموعة Microsoft 365 وعرض الضيوف واستخدام PowerShell للتحكم في وصول الضيوف.
ms.openlocfilehash: 59ec932aea516107f08570f899987c4d619aa66b
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084202"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>إدارة وصول الضيف في مجموعات Microsoft 365

بشكل افتراضي، يتم تشغيل وصول الضيف لمجموعات Microsoft 365 لمؤسستك. يمكن للمسؤولين التحكم في ما إذا كان يجب السماح بوصول الضيف إلى المجموعات لمؤسستهم بأكملها أو للمجموعات الفردية.

عند تشغيله، يمكن لأعضاء المجموعة دعوة الضيوف إلى مجموعة Microsoft 365 من خلال Outlook على ويب. يتم إرسال الدعوات إلى مالك المجموعة للموافقة عليها.

بمجرد الموافقة، تتم إضافة الضيف إلى الدليل والمجموعة.

> [!Note]
> لا تدعم شبكات Yammer Enterprise الموجودة في الوضع الأصلي أو [الموقع الجغرافي للاتحاد الأوروبي](/yammer/manage-security-and-compliance/manage-data-compliance) ضيوف الشبكة.
> لا تدعم مجموعات Microsoft 365 Connected Yammer حاليا وصول الضيف، ولكن يمكنك إنشاء مجموعات خارجية غير متصلة في شبكة Yammer. راجع [إنشاء مجموعات خارجية وإدارتها في Yammer](/yammer/work-with-external-users/create-and-manage-external-groups) للحصول على الإرشادات.

غالبا ما يتم استخدام وصول الضيف في المجموعات كجزء من سيناريو أوسع يتضمن SharePoint أو Teams. تحتوي هذه الخدمات على إعدادات مشاركة الضيف الخاصة بها. للحصول على إرشادات كاملة لإعداد مشاركة الضيف عبر المجموعات وSharePoint وTeams، راجع:

- [التعاون مع الضيوف في موقع](../../solutions/collaborate-in-site.md)
- [التعاون مع الضيوف في فريق](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>إدارة وصول ضيف المجموعات

إذا كنت تريد تمكين وصول الضيف أو تعطيله في المجموعات، يمكنك القيام بذلك في <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**المجموعات**</a>.

1. في مركز الإدارة، انتقل إلى **"إظهار كافة** \>  \> **إعدادات المؤسسة**" وعلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">علامة التبويب **"الخدمات**"</a>، حدد **مجموعات Microsoft 365**.
  
2. في صفحة **مجموعات Microsoft 365**، اختر ما إذا كنت تريد السماح للأشخاص من خارج مؤسستك بالوصول إلى موارد المجموعة أو السماح لمالكي المجموعة بإضافة أشخاص من خارج مؤسستك إلى مجموعات.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>إضافة ضيوف إلى مجموعة Microsoft 365 من مركز الإدارة

إذا كان الضيف موجودا بالفعل في الدليل، يمكنك إضافته إلى مجموعاتك من <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">مركز مسؤولي Microsoft 365</a>. (يجب إدارة المجموعات ذات العضوية [الديناميكية في Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule).)
  
1. في مركز الإدارة، انتقل إلى **مجموعات المجموعات** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
  
2. انقر فوق المجموعة التي تريد إضافة الضيف إليها، وحدد **"عرض الكل" وقم بإدارة الأعضاء** على علامة التبويب **"الأعضاء** ". 
  
4. حدد **"إضافة أعضاء**"، واختر اسم الضيف الذي تريد إضافته.
    
5. حدد **حفظ**.

إذا كنت تريد إضافة ضيف إلى الدليل مباشرة، يمكنك [إضافة مستخدمي تعاون Azure Active Directory B2B في مدخل Microsoft Azure](/azure/active-directory/b2b/add-users-administrator).

إذا كنت تريد تحرير أي من معلومات الضيف، يمكنك [إضافة معلومات ملف تعريف المستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="related-content"></a>المحتويات ذات الصلة

[حظر الضيوف من مجموعة معينة](../../solutions/per-group-guest-access.md) (مقالة)\
[إدارة عضوية المجموعة في مركز مسؤولي Microsoft 365](add-or-remove-members-from-groups.md) (مقالة)\
[مراجعات صلاحية الوصول إلى Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review) (المقالة)\
[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (مقال)
