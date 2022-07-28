---
title: عرض فشل اتصال شبكة الكمبيوتر السحابي للمؤسسة في Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: katmartin
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية عرض فشل اتصال شبكة كمبيوتر سحابي للمؤسسة.
ms.openlocfilehash: e557c2cd01851c77d11aadf75e20b394b2944987
ms.sourcegitcommit: 23a53b5c5e372a2a7ad5e175850224d3d464f6dd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/28/2022
ms.locfileid: "67055845"
---
# <a name="view-an-enterprise-cloud-pc-failed-network-connection-in-microsoft-365-lighthouse"></a>عرض فشل اتصال شبكة الكمبيوتر السحابي للمؤسسة في Microsoft 365 Lighthouse

يوفر Microsoft 365 Lighthouse حالة الاتصال بين مستأجري العملاء وAzure Active Directory (Azure AD). عندما يكون اتصال الشبكة في Cloud PC فاشلا، يمكنك عرض معلومات مفصلة في مركز إدارة Microsoft Endpoint Manager.

## <a name="before-you-begin"></a>قبل البدء

- يجب أن تكون مسؤولا عاما في مستأجر الشريك.
- يجب أن يكون لديك مسؤول الكمبيوتر السحابي أو قارئ الكمبيوتر الشخصي السحابي لعرض مشكلات الاتصال.

## <a name="view-a-failed-network-connection"></a>عرض فشل اتصال الشبكة

1. في جزء التنقل الأيمن في Lighthouse، حدد **"Devices** >  **Windows 365**".

2. حدد علامة تبويب **اتصالات شبكة Azure** .

3. من شريط التعليقات التوضيحية الملونة، حدد **الاتصالات الفاشلة**.

4. من القائمة التي تمت تصفيتها، حدد **عرض تفاصيل الاتصال في Microsoft Endpoint Manager** بجوار الاتصال الذي تريد التحقق منه.

5. من مركز إدارة Microsoft Endpoint Manager، حدد **"عرض التفاصيل**" لمعرفة المزيد حول الخطأ.

## <a name="next-steps"></a>الخطوات التالية

لاستكشاف مشكلات الاتصال وإصلاحها، راجع [استكشاف أخطاء اتصال الشبكة المحلية وإصلاحها](/windows-365/enterprise/troubleshoot-on-premises-network-connection).

## <a name="related-content"></a>المحتويات ذات الصلة

[التحكم في الوصول المستند إلى دور الكمبيوتر السحابي ](/windows-365/enterprise/role-based-access)(مقالة)\
[صلة مجال Active Directory](/windows-365/enterprise/troubleshoot-on-premises-network-connection#active-directory-domain-join) (مقالة)\
[مزامنة جهاز Azure Active Directory](/windows-365/enterprise/troubleshoot-on-premises-network-connection#azure-active-directory-device-sync) (مقالة)
