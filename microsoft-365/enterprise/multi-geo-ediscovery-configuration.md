---
title: تكوين Microsoft 365 EDiscovery متعددة الجغرافيا
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
ms.collection: Strat_SP_gtc
description: تعرف على كيفية استخدام المعلمة Region لتكوين eDiscovery للاستخدام في مواقع الأقمار الصناعية في Microsoft 365 Multi-Geo.
ms.openlocfilehash: b0366470984abbdc0ed0b3e407ca8ef6b5a5743f
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63576905"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Microsoft 365 eDiscovery متعدد الجغرافيا

[Advanced eDiscovery](../compliance/overview-ediscovery-20.md) هذه الإمكانات مسؤول eDiscovery متعدد الجغرافيا للبحث في كل الجغرافيا دون الحاجة إلى استخدام عامل تصفية أمان "المنطقة". يتم تصدير البيانات إلى مثيل Azure للموقع المركزي للمستأجر الجغرافي المتعدد. يحدث الأمر نفسه عند تطبيق احتجاز على شخص غير مطبق، ومع ذلك، لن تظهر إحصائيات الاحتجاز داخل الاحتجاز بدون عامل تصفية الأمان "المنطقة". لا تعني إحصائيات الاستمرار التي تظهر 0 فشل الاستمرار طالما أن حالة الانتظار تظهر على (ناجحة).

بدون قدرات eDiscovery المتقدمة، سيكون مدير eDiscovery أو مسؤول مستأجر متعدد الجغرافيا قادرا على إدارة eDiscovery فقط في الموقع المركزي لذلك المستأجر. لدعم القدرة على إدارة eDiscovery لمواقع الأقمار الصناعية، تتوفر معلمة جديدة لتصفية أمان التوافق تسمى "المنطقة" عبر PowerShell. يمكن استخدام هذه المعلمة من قبل المستأجرين الذين يوجد موقعهم المركزي في أمريكا الشمالية أو أوروبا أو آسيا والمحيط الهادئ. Advanced eDiscovery للمستأجرين الذين لا يوجد موقعهم المركزي في أمريكا الشمالية أو أوروبا أو آسيا والمحيط الهادئ والذين يحتاجون إلى تنفيذ eDiscovery عبر مواقع الأقمار الصناعية الجغرافية. 

يجب على المسؤول العام ل Microsoft 365 تعيين أذونات eDiscovery Manager للسماح للآخرين بتنفيذ eDiscovery وتعيين معلمة "المنطقة" في عامل تصفية أمان التوافق المعمول به لتحديد المنطقة الخاصة بإجراء eDiscovery كمواقف أقمار صناعية، وإلا، لن يتم تنفيذ eDiscovery لموقع القمر الصناعي. يتم دعم عامل تصفية أمان "المنطقة" واحد فقط لكل مستخدم، لذا يجب أن تكون كل المناطق داخل عامل تصفية الأمان نفسه.

عند تعيين دور eDiscovery Manager أو المسؤول لموقع قمر صناعي معين، لن يتمكن مدير eDiscovery أو المسؤول إلا من تنفيذ إجراءات البحث في eDiscovery مقابل مواقع SharePoint ومواقع OneDrive الموجودة في موقع القمر الصناعي هذا. إذا حاول مدير eDiscovery أو المسؤول البحث SharePoint مواقع OneDrive خارج موقع القمر الصناعي المحدد، لن يتم إرجاع أي نتائج. أيضا، عندما يقوم eDiscovery Manager أو مسؤول موقع القمر الصناعي بتشغيل عملية تصدير، يتم تصدير البيانات إلى مثيل Azure لهذه المنطقة. يساعد ذلك المؤسسات على البقاء في حالة التوافق من خلال عدم السماح بتصدير المحتوى عبر الحدود الخاضعة للرقابة.

> [!NOTE]
> إذا كان من الضروري أن يقوم eDiscovery Manager بالبحث عبر مواقع أقمار SharePoint، يجب إنشاء حساب مستخدم آخر لمدير eDiscovery الذي يحدد موقع القمر الصناعي البديل حيث تقع مواقع OneDrive أو SharePoint.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

لتعيين عامل تصفية أمان التوافق للمنطقة:

1. [الاتصال Microsoft 365 أمان & مركز التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. استخدم بناء الجملة التالي:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   على سبيل المثال:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

راجع [مقالة New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) لمزيد من المعلمات بناء الجملة.
