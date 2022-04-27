---
title: إعداد الشبكة Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: ابحث عن ارتباطات إلى مقالات تحتوي على معلومات لمساعدتك في إعداد شبكتك Microsoft 365، بما في ذلك نظرة عامة على اتصال الشبكة وقائمة بنقاط النهاية.
ms.openlocfilehash: 8651fa23983cddf243081248bf1e03fb067232e2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092834"
---
# <a name="set-up-your-network-for-microsoft-365"></a>إعداد الشبكة Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يتمثل جزء مهم من إعداد Microsoft 365 في التأكد من إعداد اتصالات الشبكة والإنترنت للوصول الأمثل. يختلف تكوين الشبكة المحلية للوصول إلى سحابة البرامج كخدمة (SaaS) الموزعة عالميا عن الشبكة التقليدية التي تم تحسينها لنسبة استخدام الشبكة إلى مراكز البيانات المحلية واتصال الإنترنت المركزي. 

استخدم هذه المقالات لفهم الاختلافات الرئيسية وتعديل أجهزة الحافة وأجهزة الكمبيوتر العميلة والشبكة المحلية للحصول على أفضل أداء للمستخدمين المحليين.

## <a name="how-microsoft-365-networking-works"></a>كيفية عمل Microsoft 365 الشبكات

راجع هذه المقالات للحصول على نظرة عامة حول الاتصال Microsoft 365:

- [نظرة عامة على اتصال الشبكة Microsoft 365](microsoft-365-networking-overview.md)
- [مبادئ اتصال الشبكة Microsoft 365](microsoft-365-network-connectivity-principles.md)
- [تقييم اتصال الشبكة Microsoft 365](assessing-network-connectivity.md)

للحصول على إرشادات حول تحسين الأداء، راجع [تخطيط الشبكة وضبط الأداء Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>دعم Microsoft 365 الشبكات كمورد معدات الشبكة

إذا كنت مورد معدات الشبكة، فانضم إلى [Office 365 Networking Partner Program](microsoft-365-networking-partner-program.md). سجل في البرنامج لإنشاء مبادئ اتصال الشبكة Office 365 في منتجاتك وحلولك. 

## <a name="office-365-endpoints"></a>نقاط نهاية Office 365

نقاط النهاية هي مجموعة عناوين IP الوجهة وأسماء مجالات DNS وعناوين URL لنسبة استخدام الشبكة Office 365 على الإنترنت. 

لتحسين الأداء Office 365 الخدمات المستندة إلى السحابة، تحتاج بعض نقاط النهاية إلى معالجة خاصة من قبل مستعرضات العميل والأجهزة الموجودة في شبكة edge. تتضمن هذه الأجهزة جدران الحماية وSSL Break وأجهزة فحص وفحص حزم البيانات وأنظمة منع فقدان البيانات.

راجع [إدارة نقاط نهاية Office 365](managing-office-365-endpoints.md) للحصول على التفاصيل.

هناك حاليا خمس سحب Office 365 مختلفة. ينقلك هذا الجدول إلى قائمة نقاط النهاية لكل منها.

| النهايه | الوصف |
|:-------|:-----|
| [نقاط النهاية في جميع أنحاء العالم](urls-and-ip-address-ranges.md) | نقاط النهاية لاشتراكات Office 365 في جميع أنحاء العالم، والتي تتضمن سحابة القطاع الحكومي الولايات المتحدة (سحابة القطاع الحكومي). |
| [نقاط نهاية DoD لحكومة الولايات المتحدة](microsoft-365-u-s-government-dod-endpoints.md) | نقاط النهاية لاشتراكات وزارة الدفاع الأمريكية (DoD). |
| [نقاط نهاية GCC High لحكومة الولايات المتحدة](microsoft-365-u-s-government-gcc-high-endpoints.md) | نقاط النهاية للولايات المتحدة سحابة القطاع الحكومي اشتراكات عالية (سحابة القطاع الحكومي عالية). |
| [Office 365 المشغل بواسطة نقاط نهاية 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Office 365 تشغيل نقاط النهاية بواسطة 21Vianet، والتي تم تصميمها لتلبية احتياجات Office 365 في الصين. |
|||

لأتمتة الحصول على أحدث قائمة بنقاط النهاية لسحابتك Office 365، راجع [عنوان IP Office 365 وخدمة ويب URL](microsoft-365-ip-web-service.md).

للحصول على نقاط نهاية إضافية، راجع هذه المقالات:

- [نقاط النهاية الإضافية غير مضمنة في خدمة ويب](additional-office365-ip-addresses-and-urls.md)
- [طلبات الشبكة في Office 2016 for Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>مواضيع إضافية للشبكات Microsoft 365

راجع هذه المقالات للمواضيع المتخصصة في Microsoft 365 الشبكات:

- [شبكات تسليم المحتوى](content-delivery-networks.md)
- [دعم IPv6 في خدمات Office 365](ipv6-support.md)
- [دعم NAT مع Office 365](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute ل Microsoft 365

راجع هذه المقالات للحصول على معلومات حول استخدام ExpressRoute لنسبة استخدام الشبكة Office 365:

- [Azure ExpressRoute ل Office 365](azure-expressroute.md)
- [تنفيذ ExpressRoute Office 365](implementing-expressroute.md)
- [تخطيط الشبكة باستخدام ExpressRoute لـ Office 365](network-planning-with-expressroute.md)
- [التوجيه باستخدام ExpressRoute لـ Office 365](routing-with-expressroute.md)
