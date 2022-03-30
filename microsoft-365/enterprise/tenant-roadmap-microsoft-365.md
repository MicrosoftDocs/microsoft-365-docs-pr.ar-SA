---
title: خارطة طريق المستأجر Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: المخطط لإعداد المستأجرين Microsoft 365.
ms.openlocfilehash: 180f7f998819986d05febe6ae19877da290d20a5
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63576950"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>خارطة طريق المستأجر Microsoft 365

إن Microsoft 365 المستأجر الخاص بك هو مجموعة الخدمات المعينة لمنظمتك. يقترن هذا المستأجر عادة باسم واحد أو أكثر من أسماء مجالات DNS العامة، وهو يعمل ك حاوية مركزية ومعزولة لاشتراكات مختلفة والتراخيص ضمنها التي تقوم بتعيينها إلى حسابات المستخدمين. لمزيد من المعلومات، راجع الاشتراكات والتراخيص والحسابات والمستأجرين [ل عروض Microsoft السحابية](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

عند إنشاء مستأجر Microsoft 365، يمكنك تعيينه إلى موقع جغرافي معين. يمكنك أيضا الحصول على مستأجر مع مواقع جغرافية متعددة وتحريك المستأجر من موقع إلى آخر.

لتهيئة المستأجر لتطبيقات المستخدم والمجموعات والتراخيص والسحابة، من المهم التخطيط لتكوين المستأجر وتنفيذه بعناية.

## <a name="set-up-your-microsoft-365-tenant"></a>إعداد المستأجر Microsoft 365 المستأجر

بعد التأكد من تحسين الشبكة للوصول إلى Microsoft 365 لكل من العاملين على المستوى المحلية والنائية، تخطط مهامك الكبيرة التالية لمستأجر Microsoft 365 لأسماء مجالات DNS والخدمات العامة والبنية الأساسية للهوية التي تدعم تسجيل الدخول الآمن للمستخدم.

### <a name="plan"></a>الخطة

التخطيط لتنفيذ المستأجر:

- [فهم الاشتراكات والتراخيص ومستأجري Azure Active Directory (Azure AD)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [فهم كيفية استخدام شهادات SSL جهة خارجية](plan-for-third-party-ssl-certificates.md)
- [فهم طرق تكامل Microsoft 365 المستأجر مع خدمات Azure AD](integrated-apps-and-azure-ads.md)
- [التخطيط لدعم تطبيق العميل](microsoft-365-client-support-certificate-based-authentication.md)
- [تحديد كيفية استخدام المصادقة الحديثة المختلطة](hybrid-modern-auth-overview.md)
- [التخطيط Office 2007 Office 2010](plan-upgrade-previous-versions-office.md)
- [فهم عزل المستأجر](/compliance/assurance/microsoft-365-isolation-controls)

### <a name="deploy"></a>نشر

لنشر المستأجر: 

- أضف مجالات [DNS](../admin/setup/add-domain.md) لمنظمتك.
- استخدم [أدلة الإعداد في مركز مسؤولي Microsoft 365](setup-guides-for-microsoft-365.md).
- قم ببناء [البنية الأساسية لهويتك](deploy-identity-solution-overview.md).

### <a name="move-a-tenants-geographic-locations"></a>نقل المواقع الجغرافية لمستأجر

تواصل Microsoft فتح المواقع الجغرافية الجديدة في مركز البيانات (المواقع الجغرافية) لخدمات Microsoft 365 البيانات. تضيف هذه المدارات الجغرافية الجديدة في مركز البيانات موارد القدرة الإنتاجية والحساب لدعم طلب العملاء ونمو الاستخدام. بالإضافة إلى ذلك، توفر الجغرافيا الجغرافية الجديدة في مركز البيانات الإقامة في البيانات الجغرافية لبيانات العملاء الأساسية.

لمزيد من المعلومات، راجع نقل [البيانات الأساسية إلى Microsoft 365 جيو مركز البيانات الجديد](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>نشر Microsoft 365 Geo

باستخدام Microsoft 365 Multi-Geo، يمكن لمنظمتك توسيع Microsoft 365 الجغرافيا المتعددة و/أو البلدان ضمن نطاق المستأجر الحالي.

لمزيد من المعلومات، راجع Microsoft 365 [الجغرافيا المتعددة](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>إدارة مستأجرين متعددين Microsoft 365 المستأجرين 

على الرغم من أن وجود مستأجر واحد ل oganization هو أمر مثالي، إلا أنك قد تكون إحدى المؤسسات العديدة التي لديها مستأجرين متعددين. يمكن أن تتضمن الأسباب عمليات الدمج والاستحواذ، أو تريد عزلك إداريا، أو إذا كان لديك تقنية معلومات لا مركزية.

إذا كان لديك عدة Microsoft 365 مستأجرين، فشاهد المقالات التالية للحصول على مزيد من المعلومات حول:

- [التعاون بين المستأجرين](microsoft-365-inter-tenant-collaboration.md)
- [ترحيل علبة البريد عبر المستأجرين](cross-tenant-mailbox-migration.md)
- [الترحيل من مستأجر إلى مستأجر](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>الخطوة التالية

ابدأ التخطيط للمستأجر باستخدام [الاشتراكات والتراخيص والحسابات والمستأجرين](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).