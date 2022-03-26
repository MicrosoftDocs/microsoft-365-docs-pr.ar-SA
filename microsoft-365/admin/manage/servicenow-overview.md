---
title: Microsoft 365 تكامل الدعم مع نظرة عامة حول تكوين ServiceNow
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: دليل تكوين وتثبيت تطبيق معتمد النطاق ل ServiceNow.
ms.openlocfilehash: dc69f6210eda4ba04dfd0aecf9795bfcba2efe22
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572042"
---
# <a name="microsoft-365-support-integration-with-servicenow-configuration-overview"></a>Microsoft 365 تكامل الدعم مع نظرة عامة حول تكوين ServiceNow

ينطبق المحتوى التالي على Microsoft 365 تكامل الدعم مع إصدار **1.0.7 كحد أدنى**.

**Microsoft 365 تكامل** الدعم من دمج Microsoft 365 التعليمات والدعم وصحة الخدمة مع مثيلات ServiceNow. يمكنك البحث عن المشاكل المعروفة والمبأولة في Microsoft، وحل الحوادث، وإكمال المهام باستخدام الحلول الموصى بها من Microsoft، والتصعيد، إذا لزم الأمر، إلى الدعم الذي يساعده الإنسان من Microsoft.

للحصول على **Microsoft 365 تكامل الدعم** من متجر ServiceNow، انتقل إلى [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

## <a name="key-features"></a>الميزات الأساسية

هذه هي الميزات الرئيسية التي ستحصل عليها مع تطبيق Microsoft 365 تكامل الدعم في مثيل ServiceNow:

- أحداث حالة الخدمة: معلومات حول أحداث حالة خدمة Microsoft المعروفة، بما في ذلك تأثير المستخدم والنطاق الحالة الحالية والتحديث المتوقع التالي. باستخدام التعلم الآلي، تتطابق أحداث ServiceNow مع أحداث خدمة Microsoft الصحية استنادا إلى حقل الوصف القصير.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" alt-text="حقل وصف &quot;أحداث صحة الخدمة&quot;.":::

- الحلول المستحسنة: يتم استخدام أوصاف المهام والحوادث للتوصية بحلول مستهدفة دقيقة ومقالات ذات صلة من Microsoft يتم تشغيلها بواسطة التعلم الآلي. يمكنك أيضا استخدام البحث للعثور على حلول أخرى، إذا لزم الأمر.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" alt-text="حقل وصف الحلول الموصى بها.":::

- طلب خدمة Microsoft: يمكنك تصعيد المشاكل إلى وكلاء دعم Microsoft وتلقي تحديثات الحالة لحالتك.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-service-request.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-service-request.png" alt-text="نموذج طلب الخدمة.":::

## <a name="prerequisites"></a>المتطلبات الأساسية

### <a name="permissions-requirements"></a>متطلبات الأذونات

للمتابعة باستخدام هذا الدليل، تأكد من توفر الأذونات التالية وتكوينها للبيئات خلال العملية بأكملها:

- مسؤول Azure Active Directory (AAD (دليل Azure النشط)) الذي يمكنه إنشاء تطبيقات Azure AD

- مسؤول ServiceNow

- Microsoft 365 المستأجر

### <a name="configuration-highlights"></a>تمييزات التكوين

لإعداد تكامل Microsoft 365 **الدعم**:

- قم بتسجيل التطبيقات في Microsoft Azure Active Directory (AAD (دليل Azure النشط)) للمصادقة على كل من مكالمات API الصادرة والداخلة.

- إنشاء كيانات ServiceNow Microsoft Azure AD التطبيق لتدفق البيانات الصادرة والداخلة.

- ادمج مثيل ServiceNow مع دعم Microsoft Microsoft 365 مدخل المسؤول.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-integration-diagram.png" alt-text="رسم تخطيطي لتكامل ServiceNow.":::

### <a name="application-dependencies-in-your-servicenow-environments"></a>تبعيات التطبيق في بيئات ServiceNow

الأذونات المطلوبة:

- oauthentity\_

- oauthentityprofile\_\_

بعد تثبيت Microsoft 365 تكامل الدعم، يتم إنشاء وصولين عبر النطاق للتطبيق. إذا لم يتم إنشاؤها بنجاح، فنشئها يدويا.

## <a name="setup-the-integration"></a>إعداد التكامل

بعد تنزيل التطبيق، انتقل إلى معالج Microsoft 365 في بيئة SNOW لإكمال عملية الإعداد.
:::image type="content" source="../../media/154124985-76e13e7d-b32e-4741-830b-bbb110d3ecbf.png" alt-text="معالج إعداد الثلج":::

يمكنك معرفة المزيد حول الخطوات من خلال زيارة الصفحات التالية:
- إذا كانت بيئة ServiceNow تسمح بالمصادقة الأساسية (الوصول باستخدام بيانات اعتماد مستخدم ServiceNow) لمكالمات خدمات الويب الواردة، فاتبع الإرشادات الواردة في إعداد Microsoft 365 تكامل الدعم مع [ServiceNow Basic Authentication](servicenow-basic-authentication.md).
- إذا كانت بيئة ServiceNow لا تسمح بالمصادقة الأساسية (الوصول باستخدام بيانات اعتماد مستخدم ServiceNow) لمكالمات خدمات الويب الواردة، فاتبع الإرشادات الواردة في [إعداد تكامل دعم Microsoft 365 مع رمز Azure AD Auth المميز](servicenow-aad-oauth-token.md).
  - سيتطلب هذا التكوين وجود مستأجر SSO لكي AAD (دليل Azure النشط) الرمز المميز ل Auth بشكل صحيح.

لفهم كل ميزة، راجع Microsoft 365 [تكامل الدعم](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

> [!NOTE]
> هذا التطبيق غير معتمد في البيئات المنظمة أو المقيدة.
