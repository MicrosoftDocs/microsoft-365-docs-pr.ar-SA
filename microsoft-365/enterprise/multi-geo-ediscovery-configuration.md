---
title: تكوين eDiscovery متعدد المواقع الجغرافية لـ Microsoft 365
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
description: تعرف على كيفية استخدام معلمة المنطقة لتكوين eDiscovery للاستخدام في مواقع الأقمار الصناعية في Microsoft 365 Multi-Geo.
ms.openlocfilehash: a220e68e6dbe010f2eab6876dc2813dcd84d5d6d
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130922"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Microsoft 365 تكوين eDiscovery متعدد المناطق الجغرافية

تسمح [قدرات eDiscovery (Premium)](../compliance/overview-ediscovery-20.md) لمسؤول eDiscovery متعدد المناطق الجغرافية بالبحث في جميع المناطق الجغرافية دون الحاجة إلى استخدام عامل تصفية أمان "المنطقة". يتم تصدير البيانات إلى مثيل Azure للموقع المركزي للمستأجر متعدد المناطق الجغرافية.

بدون قدرات eDiscovery (Premium)، سيتمكن مدير eDiscovery أو مسؤول مستأجر متعدد المناطق الجغرافية من إجراء eDiscovery فقط في الموقع المركزي لذلك المستأجر. لدعم القدرة على إجراء eDiscovery لمواقع الأقمار الصناعية، تتوفر معلمة عامل تصفية أمان امتثال جديدة تسمى "المنطقة" عبر PowerShell. يمكن استخدام هذه المعلمة من قبل المستأجرين الذين يوجد موقعهم المركزي في أمريكا الشمالية أو أوروبا أو آسيا والمحيط الهادئ. يوصى باستخدام eDiscovery (Premium) للمستأجرين الذين لا يوجد موقعهم المركزي في أمريكا الشمالية أو أوروبا أو آسيا والمحيط الهادئ ويحتاجون إلى تنفيذ eDiscovery عبر المواقع الجغرافية للأقمار الصناعية.

يجب على المسؤول العام Microsoft 365 تعيين أذونات eDiscovery Manager للسماح للآخرين بتنفيذ eDiscovery وتعيين معلمة "Region" في عامل تصفية أمان التوافق المعمول به لتحديد المنطقة لإجراء eDiscovery كموقع قمر صناعي، وإلا فلن يتم تنفيذ eDiscovery لموقع القمر الصناعي. يتم دعم عامل تصفية أمان "المنطقة" واحد فقط لكل مستخدم، لذلك يجب أن تكون جميع المناطق داخل نفس عامل تصفية الأمان.

عند تعيين دور eDiscovery Manager أو Administrator لموقع قمر صناعي معين، سيتمكن مدير eDiscovery أو المسؤول فقط من تنفيذ إجراءات البحث eDiscovery مقابل مواقع SharePoint ومواقع OneDrive الموجودة في موقع الأقمار الصناعية هذا. إذا حاول مدير eDiscovery أو مسؤول البحث في مواقع SharePoint أو OneDrive خارج موقع الأقمار الصناعية المحدد، فلن يتم إرجاع أي نتائج. أيضا، عندما يقوم مدير eDiscovery أو المسؤول لموقع قمر صناعي بتشغيل تصدير، يتم تصدير البيانات إلى مثيل Azure لتلك المنطقة. يساعد هذا المؤسسات على البقاء في حالة امتثال من خلال عدم السماح بتصدير المحتوى عبر الحدود الخاضعة للرقابة.

> [!NOTE]
> إذا كان من الضروري أن يبحث مدير eDiscovery عبر مواقع أقمار صناعية متعددة SharePoint، فسيلزم إنشاء حساب مستخدم آخر ل eDiscovery Manager الذي يحدد موقع الأقمار الصناعية البديل حيث توجد مواقع OneDrive أو SharePoint.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

لتعيين عامل تصفية أمان التوافق لمنطقة:

1. [الاتصال إلى Microsoft 365 Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. استخدم بناء الجملة التالي:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   على سبيل المثال:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

راجع [مقالة New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) للحصول على معلمات بناء جملة إضافية.
