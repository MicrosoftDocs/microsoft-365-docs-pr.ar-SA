---
title: خارطة طريق الشبكة Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 03/03/2022
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: خارطة الطريق لتخطيط الشبكات Microsoft 365 تنفيذها وإدارتها.
ms.openlocfilehash: cfefd668f91eb074259d056b3b573b9c0f636bb6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63576922"
---
# <a name="networking-roadmap-for-microsoft-365"></a>خارطة طريق الشبكة Microsoft 365

Microsoft 365 الخاصة بالمؤسسة خدمات سحابة التعاون والإنتاجية Microsoft Intune والعديد من خدمات الهوية والأمان ل Microsoft Azure. تعتمد كل هذه الخدمات المستندة إلى السحابة على أمان الاتصالات وأداءها ووثوقيتها من أجهزة العميل عبر الإنترنت أو الدوائر المخصصة. لاستضافة هذه الخدمات وجعلها متوفرة للعملاء في جميع أنحاء العالم، قامت Microsoft بتصميم بنية أساسية للشبكات تركز على الأداء والتكامل.

الجزء المهم من Microsoft 365 هو التأكد من إعداد الشبكة واتصالات الإنترنت للوصول المحسن. يختلف تكوين الشبكة المحلية للوصول إلى سحابة برامج كخدمة (SaaS) موزعة بشكل عام عن الشبكة التقليدية التي تم تحسينها لحركة المرور إلى مراكز البيانات المحلية واتصال إنترنت مركزي.

استخدم هذه المقالات لفهم الاختلافات الرئيسية وتعديل أجهزة الحواف وأجهزة الكمبيوتر العميلة الشبكة المحلية للحصول على أفضل أداء للمستخدمين في الموقع.

## <a name="plan"></a>الخطة

في مرحلة التخطيط لتنفيذ الشبكة:

- [فهم كيفية Microsoft 365 الشبكات](microsoft-365-networking-overview.md)
- [التعرف على مبادئ اتصال الشبكة](microsoft-365-network-connectivity-principles.md)
- [تقييم اتصال الشبكة الحالي](assessing-network-connectivity.md)
- [تحديد ما إذا كان ExpressRoute صحيحا لمنظمتك](network-planning-with-expressroute.md)
- [التخطيط للأجهزة على الشبكة](plan-for-network-devices.md)
- [إعداد الشبكة ل الترحيل](network-and-migration-planning.md)

## <a name="deploy"></a>نشر

في مرحلة نشر تنفيذ الشبكة:

- [التأكد من تحسين شبكة المؤسسة Microsoft 365 الاتصال](set-up-network-for-microsoft-365.md)
- [إضافة مجالات DNS لمنظمتك](../admin/setup/add-domain.md)
- [تحسين الاتصال للعاملين عن بعد باستخدام تقسيم VPN](microsoft-365-vpn-split-tunnel.md)
- [تكوين CDN لتحسين أداء الشبكة](office-365-cdn-quickstart.md)
- [تحسين الاتصالية Microsoft 365 نقاط النهاية](microsoft-365-ip-web-service.md)
- تكوين [ExpressRoute](azure-expressroute.md)، إذا لزم الأمر

## <a name="manage"></a>إدارة

في مرحلة الإدارة الخاصة بتنفيذ الشبكة:

- [اختبار أداة اختبار اتصال Microsoft 365 الشبكة وتحسينها](office-365-network-mac-perf-onboarding-tool.md)
- [تأكد من أن أجهزة الشبكة تستخدم أحدث Office 365 النهاية](microsoft-365-endpoints.md)
- [مراقبة أداء الشبكة وضبطه](network-planning-and-performance.md)
- [مراقبة Microsoft 365 الاتصال](monitor-connectivity.md)

## <a name="network-equipment-vendors"></a>موردو معدات الشبكة

إذا كنت مورد معدات الشبكة، فالانضمام إلى [Microsoft 365 Networking Partner Program](microsoft-365-networking-partner-program.md). قم بالتسجيل في البرنامج Microsoft 365 مبادئ اتصال الشبكة في المنتجات والحلول.

## <a name="how-contoso-did-networking-for-microsoft-365"></a>كيفية استخدام Contoso للشبكات Microsoft 365

تعرف على كيفية تحسين شركة Contoso Corporation، وهي شركة خيالية ولكنها تمثيلية متعددة [](contoso-networking.md) الجنسيات، لأجهزتها على الشبكة واتصالات الإنترنت Microsoft 365 السحابية.

![شركة Contoso Corporation.](../media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>الخطوة التالية

ابدأ التخطيط للشبكات باستخدام نظرة عامة Microsoft 365 [الاتصال بالشبكة](microsoft-365-networking-overview.md).
