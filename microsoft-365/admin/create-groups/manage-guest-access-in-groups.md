---
title: إدارة وصول الضيف في Microsoft 365 المجموعات
ms.reviewer: arvaradh
f1.keywords: NOCSH
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
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: تعرف على كيفية إضافة ضيوف إلى مجموعة Microsoft 365، وعرض المستخدمين الضيوف، واستخدام PowerShell للتحكم في وصول الضيوف.
ms.openlocfilehash: 99c0a9f46abfffe56f8c751ca614287181f39a5d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569136"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>إدارة وصول الضيف في Microsoft 365 المجموعات

بشكل افتراضي، يتم تشغيل Microsoft 365 وصول الضيوف لمجموعاتك لمنظمتك. يمكن للمسؤولين التحكم في السماح للضيوف بالوصول إلى المجموعات لمنظمتهم بكاملها أو للمجموعات الفردية.

عند تشغيلها، يمكن لأعضاء المجموعة دعوة المستخدمين الضيوف إلى مجموعة Microsoft 365 عبر Outlook ويب. يتم إرسال الدعوات إلى مالك المجموعة للموافقة عليها.

بعد الموافقة، يضاف المستخدم الضيف إلى الدليل والمجموعة.

> [!Note]
> Yammer شبكات Enterprise في الوضع الأصلي أو الاتحاد [الأوروبي Geo](/yammer/manage-security-and-compliance/manage-data-compliance) لا تدعم ضيوف الشبكة.
> Microsoft 365 مجموعات الاتصال Yammer دعم وصول الضيوف حاليا، ولكن يمكنك إنشاء مجموعات خارجية غير متصلة في Yammer الاتصال. راجع [إنشاء مجموعات خارجية وإدارتها في](/yammer/work-with-external-users/create-and-manage-external-groups) Yammer للحصول على الإرشادات.

غالبا ما يتم استخدام وصول الضيف في المجموعات كجزء من سيناريو أوسع يتضمن SharePoint أو Teams. لدى هذه الخدمات إعدادات مشاركة الضيوف الخاصة بها. للحصول على إرشادات كاملة لإعداد مشاركة الضيوف عبر المجموعات SharePoint Teams، راجع:

- [التعاون في العمل مع الضيوف في موقع](../../solutions/collaborate-in-site.md)
- [التعاون في العمل مع الضيوف في فريق](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>إدارة وصول الضيف إلى المجموعات

إذا كنت تريد تمكين وصول الضيف أو تعطيله في المجموعات، يمكنك القيام بذلك في <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**المجموعات**</a>.

1. في مركز الإدارة، انتقل إلى **إظهار** \>  \> كل الإعدادات **المؤسسة** وعلى علامة التبويب خدمات، حدد Microsoft 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**المجموعات**</a>.
  
2. في صفحة **Microsoft 365** المجموعات، اختر ما إذا كنت تريد السماح للأشخاص من خارج مؤسستك بالوصول إلى موارد المجموعة أو السماح لمالكي المجموعات بإضافة أشخاص من خارج مؤسستك إلى المجموعات.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>إضافة ضيوف إلى مجموعة Microsoft 365 من مركز الإدارة

إذا كان الضيف موجودا بالفعل في الدليل، يمكنك إضافته إلى مجموعاتك <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">من مركز مسؤولي Microsoft 365</a>. (يجب إدارة المجموعات ذات العضوية [الديناميكية في Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule).)
  
1. في مركز الإدارة، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**GroupsGroups**</a> > .
  
2. انقر فوق المجموعة التي تريد إضافة الضيف لها، وحدد **عرض الكل** وإدارة الأعضاء ضمن علامة **التبويب** أعضاء. 
  
4. حدد **إضافة أعضاء**، واختر اسم الضيف الذي تريد إضافته.
    
5. حدد **حفظ**.

إذا كنت تريد إضافة ضيف إلى الدليل مباشرة، يمكنك إضافة [مستخدمي التعاون في Azure Active Directory B2B في مدخل Azure](/azure/active-directory/b2b/add-users-administrator).

إذا كنت تريد تحرير أي من معلومات الضيف، يمكنك إضافة معلومات ملف تعريف مستخدم أو تحديثها [باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="related-content"></a>المحتوى ذي الصلة

[حظر المستخدمين الضيوف من مجموعة](../../solutions/per-group-guest-access.md) معينة (مقالة)\
[إدارة عضوية المجموعة في مركز مسؤولي Microsoft 365](add-or-remove-members-from-groups.md) (مقالة)\
[مراجعات الوصول إلى Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review) (مقالة)\
[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (مقالة)