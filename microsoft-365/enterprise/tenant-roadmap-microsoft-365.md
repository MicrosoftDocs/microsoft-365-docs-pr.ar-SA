---
title: مخطط المستأجر ل Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: مخطط إعداد المستأجرين ل Microsoft 365.
ms.openlocfilehash: 5eed55d45e4b34962b08d236f8659cfd2cf209c1
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940393"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>مخطط المستأجر ل Microsoft 365

مستأجر Microsoft 365 هو مجموعة الخدمات المعينة لمؤسستك. عادة ما يقترن هذا المستأجر باسم واحد أو أكثر من أسماء مجالات DNS العامة ويعمل كحاوية مركزية ومعزولة للاشتراكات المختلفة والتراخيص داخلها التي تقوم بتعيينها لحسابات المستخدمين. لمزيد من المعلومات، راجع [الاشتراكات والتراخيص والحسابات والمستأجرين لعروض Microsoft السحابية](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

عند إنشاء مستأجر Microsoft 365، يمكنك تعيينه إلى موقع جغرافي محدد. يمكنك أيضا أن يكون لديك مستأجر مع مواقع جغرافية متعددة ونقل المستأجر الخاص بك من موقع إلى آخر.

لجعل المستأجر جاهزا للمستخدم والمجموعات والتراخيص والتطبيقات السحابية، من المهم التخطيط بعناية لتكوين المستأجر وتنفيذه.

## <a name="set-up-your-microsoft-365-tenant"></a>إعداد مستأجر Microsoft 365

بعد التأكد من تحسين شبكاتك للوصول إلى Microsoft 365 لكل من العاملين المحليين والعاملين عن بعد، تقوم مهامك الكبيرة التالية بالتخطيط لمستأجر Microsoft 365 الخاص بك ثم تكوينه لأسماء مجالات DNS والخدمات الشائعة والبنية الأساسية للهوية التي تدعم تسجيل دخول المستخدم الآمن.

### <a name="plan"></a>الخطة

للتخطيط لتنفيذ المستأجر الخاص بك:

- [فهم الاشتراكات والتراخيص ومستأجري Azure Active Directory (Azure AD)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [فهم كيفية استخدام شهادات SSL التابعة لجهة خارجية](plan-for-third-party-ssl-certificates.md)
- [فهم الطرق التي يتم بها دمج مستأجر Microsoft 365 مع خدمات Azure AD](integrated-apps-and-azure-ads.md)
- [التخطيط لدعم تطبيق العميل](microsoft-365-client-support-certificate-based-authentication.md)
- [تحديد كيفية استخدام المصادقة الحديثة المختلطة](hybrid-modern-auth-overview.md)
- [التخطيط لترقيات Office 2007 وOffice 2010](plan-upgrade-previous-versions-office.md)
- [فهم عزل المستأجر](/microsoft-365-isolation-in-microsoft-365?view=o365-worldwide&preserve-view=true)

### <a name="deploy"></a>النشر

لنشر المستأجر الخاص بك: 

- أضف [مجالات DNS](../admin/setup/add-domain.md) لمؤسستك.
- استخدم [إرشادات الإعداد في مركز إدارة Microsoft 365](setup-guides-for-microsoft-365.md).
- إنشاء [البنية الأساسية لهويتك](deploy-identity-solution-overview.md).

### <a name="move-a-tenants-geographic-locations"></a>نقل المواقع الجغرافية للمستأجر

تواصل Microsoft فتح مواقع جغرافية جديدة لمركز البيانات (جغرافيا) لخدمات Microsoft 365. تضيف هذه المناطق الجغرافية الجديدة لمركز البيانات موارد السعة والحساب لدعم طلب العملاء ونمو الاستخدام. بالإضافة إلى ذلك، توفر جغرافيات مركز البيانات الجديد موقع بيانات في الموقع الجغرافي لبيانات العملاء الأساسية.

لمزيد من المعلومات، راجع [نقل البيانات الأساسية إلى جيو مركز بيانات Microsoft 365 الجديد](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>توزيع Microsoft 365 Multi-Geo

باستخدام Microsoft 365 Multi-Geo، يمكن لمؤسستك توسيع وجودها في Microsoft 365 إلى مناطق جغرافية متعددة و/أو بلدان داخل المستأجر الحالي.

لمزيد من المعلومات، راجع [Microsoft 365 Multi-Geo](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>إدارة العديد من مستأجري Microsoft 365 

على الرغم من أن وجود مستأجر واحد ل oganization الخاص بك أمر مثالي، فقد تكون واحدة من العديد من المؤسسات التي لديها مستأجرين متعددين. يمكن أن تتضمن الأسباب عمليات الدمج والاستحواذ، أو تريد العزل الإداري، أو لديك تكنولوجيا المعلومات اللامركزية.

إذا كان لديك العديد من مستأجري Microsoft 365، فراجع هذه المقالات للحصول على مزيد من المعلومات حول:

- [التعاون بين المستأجرين](microsoft-365-inter-tenant-collaboration.md)
- [ترحيل علبة بريد عبر المستأجرين](cross-tenant-mailbox-migration.md)
- [عمليات الترحيل من المستأجر إلى المستأجر](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>الخطوة التالية

ابدأ تخطيط المستأجر باستخدام [الاشتراكات والتراخيص والحسابات والمستأجرين](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).