---
title: عرض حماية خدمة المستأجر في Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية عرض حالة خدمة المستأجر.
ms.openlocfilehash: 3db5085ac4226b3f2800cd46f3542dcb79b311d2
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621008"
---
# <a name="view-tenant-service-health-in-microsoft-365-lighthouse"></a>عرض حماية خدمة المستأجر في Microsoft 365 Lighthouse

يمكنك عرض حالة الخدمة للمستأجرين الذين تديرهم في Microsoft 365 Lighthouse. تتضمن Service health أحداثا ونصائح للعديد من الخدمات، بما في ذلك خدمات الهوية Microsoft Intune وAzure Active Directory (Azure AD) وخدمات السحابة لإدارة أجهزة المحمول (MDM). يمكنك أيضا معرفة عدد المستأجرين المدارين الذين يتأثرون بالحوادث. على سبيل المثال، إذا كان أحد المستأجرين يواجه مشاكل، يمكنك التحقق من صفحة Service health لتحديد ما إذا كانت مشكلة معروفة تتعلق بحل قيد التقدم أو ما إذا كان التغيير الأخير قد يؤثر عليها. قد يوفر لك ذلك الوقت لاستكشاف الأخطاء وإصلاحها وتقليل مكالمات الدعم.

إذا تعذر عليك تسجيل الدخول إلى Lighthouse، يمكنك استخدام [صفحة حالة حماية الخدمة Microsoft 365](https://status.office365.com/) للتحقق من المشاكل المعروفة التي تمنعك من تسجيل الدخول إلى مستأجر الشريك. سجل أيضا لمتابعة [@MSFT365status](https://twitter.com/MSFT365Status) على Twitter للاطلاع على معلومات حول أحداث خدمة معينة.

## <a name="before-you-begin"></a>قبل البدء

لعرض حالة الخدمة، ستحتاج إلى دور Azure AD في مستأجر الشريك مع مجموعة الخصائص التالية: **microsoft.office365.serviceHealth/allEntities/allTasks**. للحصول على قائمة بالأدوار Azure AD، راجع [Azure AD الأدوار المضمنة](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>عرض حالة حماية الخدمة لكافة المستأجرين

1. في جزء التنقل الأيمن في Lighthouse، حدد **Service health**.

2. في صفحة **Service health**، راجع حالة حماية الخدمة الحالية، بما في ذلك:

   - العدد الإجمالي للحوادث
   - إجمالي عدد الاستشارات التي تؤثر على أي من المستأجرين المدارين
   - عدد الخدمات ذات الحوادث النشطة.

3. في علامة التبويب **"كافة الخدمات** "، راجع المشكلات حسب الخدمة.

4. في علامة التبويب **"كافة المشاكل** "، راجع كافة المشاكل الحالية.

## <a name="review-issue-details"></a>مراجعة تفاصيل المشكلة

1. في جزء التنقل الأيمن في Lighthouse، حدد **Service health**.

2. في صفحة **Service health**، حدد علامة التبويب **"كافة الخدمات**" أو "**كافة المشاكل**".

3. حدد مشكلة من القائمة.

4. في جزء تفاصيل المشكلة، راجع المعلومات التفصيلية، بما في ذلك نوع المشكلة والمستأجرين المتأثرين وتأثير المستخدم ومحفوظات المشاكل.

في علامة التبويب **"المستأجرون المتأثرون** "، يمكنك تصدير قائمة بالمستأجرين المتأثرين إلى ملف قيم مفصولة بفواصل (.csv) حتى تتمكن من مشاركتها مع فرق الدعم.

## <a name="related-content"></a>المحتويات ذات الصلة

[كيفية التحقق من صحة الخدمة Microsoft 365](/microsoft-365/enterprise/view-service-health) (مقالة)\
[المشاكل المعروفة في Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (مقالة)\
[عرض أدوار Azure Active Directory في Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (مقالة)
