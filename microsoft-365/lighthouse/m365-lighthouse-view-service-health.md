---
title: عرض صحة خدمة المستأجر
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
description: بالنسبة إلى موفري الخدمات المدارة (MSPs) Microsoft 365 المنارة، تعرف على كيفية عرض صحة خدمة المستأجر.
ms.openlocfilehash: 21315d0ea616fcd2865879d9d8aec66b17830208
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575209"
---
# <a name="view-tenant-service-health"></a>عرض صحة خدمة المستأجر

يمكنك عرض حالة الخدمة للمستأجرين الذين تديرهم في Microsoft 365 المنارة. تتضمن حماية الخدمة الأحداث والاستشارات الخاصة بعدة خدمات، بما في ذلك Microsoft Intune وخدمات هوية Azure Active Directory (Azure AD) وخدمات السحابة لإدارة أجهزة المحمول (MDM). يمكنك أيضا معرفة عدد المستأجرين المدارين المتأثرين بالحوادث. على سبيل المثال، إذا كان أحد المستأجرين يواجه مشاكل، يمكنك التحقق من صفحة حالة الخدمة لتحديد ما إذا كانت مشكلة معروفة في حلها في تقدم أو ما إذا كان هناك تغيير حديث قد يؤثر عليها. قد يوفر لك ذلك الوقت في استكشاف الأخطاء وإصلاحها وتقليل مكالمات الدعم.

إذا لم تتمكن من تسجيل الدخول إلى ["المنارة](https://status.office365.com/)"، يمكنك استخدام صفحة حالة Microsoft 365 الخدمة للتحقق من المشاكل المعروفة التي تمنعك من تسجيل الدخول إلى المستأجر الشريك. قم أيضا التسجيل [لمتابعة @MSFT365status على](https://twitter.com/MSFT365Status) Twitter لرؤية معلومات حول أحداث خدمة معينة.

## <a name="before-you-begin"></a>قبل البدء

لعرض حماية الخدمة، ستحتاج إلى دور Azure AD في المستأجر الشريك مع مجموعة الخاصية التالية: **microsoft.office365.serviceHealth/allEntities/allTasks**. للحصول على قائمة بأدوار Azure AD، راجع [أدوار Azure AD المضمنة](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>عرض حالة حالة الخدمة لجميع المستأجرين

1. في جزء التنقل الأيسر في المنارة، حدد **حالة الخدمة**.

2. على الصفحة **حالة الخدمة** ، راجع حالة حالة الخدمة الحالية، بما في ذلك:

   -   العدد الإجمالي للحوادث
   -   العدد الإجمالي للاستشارات التي تؤثر على أي من المستأجرين المدارين
   -   عدد الخدمات التي بها أحداث نشطة.

3. على علامة **التبويب كافة الخدمات** ، راجع المشاكل حسب الخدمة.

4. على علامة **التبويب كافة المشاكل** ، راجع كل المشاكل الحالية.

## <a name="review-issue-details"></a>مراجعة تفاصيل المشكلة

1. في جزء التنقل الأيسر في المنارة، حدد **حالة الخدمة**.

2. في الصفحة **حالة الخدمة** ، حدد **علامة التبويب كافة الخدمات** أو **كل** المشاكل.

3. حدد مشكلة من القائمة.

4. في جزء تفاصيل المشكلة، راجع المعلومات المفصلة، بما في ذلك نوع المشكلة والمستأجرين المتأثرين وتأثير المستخدم ومحفوظات المشكلة.

على **علامة التبويب** المستأجرون المتأثرون، يمكنك تصدير قائمة بالمستأجرين المتأثرين إلى ملف قيم مفصولة بفصول .csv) حتى تتمكن من مشاركته مع فرق الدعم.

## <a name="related-content"></a>المحتوى ذي الصلة
[كيفية التحقق من Microsoft 365 الخدمة](/microsoft-365/enterprise/view-service-health) (مقالة)\
[المشاكل المعروفة في Microsoft 365 المنارة](m365-lighthouse-known-issues.md) (مقالة)