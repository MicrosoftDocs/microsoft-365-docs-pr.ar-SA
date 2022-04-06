---
title: إعداد الشبكة Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: landing-page
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: يمكنك العثور على ارتباطات إلى مقالات تتضمن معلومات لمساعدتك على إعداد الشبكة Microsoft 365، بما في ذلك نظرة عامة حول اتصال الشبكة وقائمة نقاط النهاية.
ms.openlocfilehash: c6dbc4362648b3695c23f363c0e6925ead97bacb
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680831"
---
# <a name="set-up-your-network-for-microsoft-365"></a>إعداد الشبكة Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

جزء هام من Microsoft 365 هو التأكد من إعداد اتصالات الشبكة والإنترنت للوصول المحسن. يختلف تكوين الشبكة المحلية للوصول إلى سحابة برامج كخدمة (SaaS) موزعة بشكل عام عن الشبكة التقليدية التي تم تحسينها لحركة المرور إلى مراكز البيانات المحلية واتصال إنترنت مركزي. 

استخدم هذه المقالات لفهم الاختلافات الرئيسية وتعديل أجهزة الحواف وأجهزة الكمبيوتر العميلة الشبكة المحلية للحصول على أفضل أداء للمستخدمين في الموقع.

## <a name="how-microsoft-365-networking-works"></a>كيفية Microsoft 365 الشبكة

راجع هذه المقالات للحصول على نظرة عامة حول الاتصال Microsoft 365:

- [Microsoft 365 عامة حول اتصال الشبكة](microsoft-365-networking-overview.md)
- [Microsoft 365 الاتصال بالشبكة](microsoft-365-network-connectivity-principles.md)
- [تقييم Microsoft 365 الشبكة](assessing-network-connectivity.md)

للحصول على نصيحة حول تحسين الأداء، راجع [تخطيط](network-planning-and-performance.md) الشبكة وتحسين الأداء Microsoft 365.

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>دعم Microsoft 365 الشبكة كمورد معدات الشبكة

إذا كنت مورد معدات الشبكة، فالانضمام إلى [Office 365 Networking Partner Program](microsoft-365-networking-partner-program.md). قم بالتسجيل في البرنامج Office 365 مبادئ اتصال الشبكة في المنتجات والحلول. 

## <a name="office-365-endpoints"></a>Office 365 نقاط النهاية

نقاط النهاية هي مجموعة عناوين IP الوجهة وأسماء مجالات DNS وعناوين URL Office 365 البيانات على الإنترنت. 

لتحسين الأداء Office 365 المستندة إلى السحابة، تحتاج بعض نقاط النهاية إلى معالجة خاصة بواسطة مستعرضات العميل والأجهزة في شبكة edge. تتضمن هذه الأجهزة جدران الحماية، وSSL Break وفحص أجهزة فحص الحزم وأجهزة منع فقدان البيانات.

راجع [إدارة Office 365 نقاط النهاية](managing-office-365-endpoints.md) للحصول على التفاصيل.

توجد حاليا خمس Office 365 مختلفة. يأخذك هذا الجدول إلى قائمة نقاط النهاية لكل منها.

| نقاط النهاية | الوصف |
|:-------|:-----|
| [نقاط النهاية في جميع أنحاء العالم](urls-and-ip-address-ranges.md) | نقاط النهاية لاشتراكات Office 365، التي تتضمن اشتراكات الولايات المتحدة سحابة القطاع الحكومي (سحابة القطاع الحكومي). |
| [نقاط نهاية DoD الخاصة ب Government DoD في الولايات المتحدة](microsoft-365-u-s-government-dod-endpoints.md) | نقاط النهاية لاشتراكات وزارة الدفاع الأمريكية (DoD). |
| [نقاط نهاية عالية سحابة القطاع الحكومي حكومية في الولايات المتحدة](microsoft-365-u-s-government-gcc-high-endpoints.md) | نقاط النهاية لاشتراكات الولايات المتحدة سحابة القطاع الحكومي العالية (سحابة القطاع الحكومي العالية). |
| [Office 365 التي يتم تشغيلها بواسطة نقاط نهاية 21Vianet](urls-and-ip-address-ranges-21vianet.md) | يتم تشغيل نقاط النهاية Office 365 21Vianet، والتي تم تصميمها لتلبية احتياجات Office 365 في الصين. |
|||

لأتمتة الحصول على أحدث قائمة بنقاط النهاية لسحابة Office 365، راجع عنوان [IP Office 365 IP وخدمة URL على الويب](microsoft-365-ip-web-service.md).

للحصول على نقاط نهاية إضافية، راجع المقالات التالية:

- [نقاط النهاية الإضافية غير المضمنة في خدمة ويب](additional-office365-ip-addresses-and-urls.md)
- [طلبات الشبكة في Office 2016 for Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>مواضيع إضافية Microsoft 365 الشبكة

راجع هذه المقالات للحصول على مواضيع متخصصة في Microsoft 365 الشبكة:

- [شبكات تسليم المحتوى](content-delivery-networks.md)
- [دعم IPv6 في Office 365 الخدمات](ipv6-support.md)
- [دعم NAT مع Office 365](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute Microsoft 365

راجع هذه المقالات للحصول على معلومات حول استخدام ExpressRoute Office 365 المرور:

- [Azure ExpressRoute Office 365](azure-expressroute.md)
- [تنفيذ ExpressRoute Office 365](implementing-expressroute.md)
- [تخطيط الشبكة باستخدام ExpressRoute Office 365](network-planning-with-expressroute.md)
- [التوجيه باستخدام ExpressRoute Office 365](routing-with-expressroute.md)
