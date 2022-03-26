---
title: الأنظمة الأساسية وإمكانيات أنظمة التشغيل المعتمدة
description: تأكد من أنك تلبي متطلبات نظام التشغيل أو النظام الأساسي إدارة المخاطر والثغرات الأمنية، بحيث يتم حساب الأنشطة في جميع أجهزتك بشكل صحيح.
keywords: المخاطر & إدارة الثغرات الأمنية، إدارة المخاطر والثغرات الأمنية، نظام التشغيل، متطلبات النظام الأساسي، المتطلبات الأساسية، Microsoft Defender لنظام التشغيل المدعم ل Endpoint-tvm، Microsoft Defender ل Endpoint-tvm، أنظمة التشغيل المعتمدة، الأنظمة الأساسية المعتمدة، دعم linux، دعم mac
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2e9322a5fc04824482fdd764eb113d9904b3c224
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/01/2022
ms.locfileid: "63570688"
---
# <a name="supported-operating-systems-platforms-and-capabilities---for-threat-and-vulnerability-management"></a>أنظمة التشغيل و الأنظمة الأساسية والإمكانات المعتمدة - إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

قبل البدء، تأكد من أنك تلبي متطلبات نظام التشغيل أو النظام الأساسي التالية إدارة المخاطر والثغرات الأمنية بحيث يتم حساب الأنشطة في أجهزتك بشكل صحيح.

> [!NOTE]
> قد تختلف الأنظمة و الأنظمة الأساسية المعتمدة إدارة المخاطر والثغرات الأمنية عن الحد الأدنى لمتطلبات [قائمة نقاط النهاية ل Microsoft Defender](minimum-requirements.md).

## <a name="capabilities-per-supported-operating-systems-os-and-platforms"></a>القدرات لكل أنظمة التشغيل و الأنظمة الأساسية المعتمدة

في الجدول التالي، تشير "نعم" إلى أن إمكانية إدارة المخاطر والثغرات الأمنية معتمدة ل OS أو النظام الأساسي في ذلك الصف.

نظام التشغيل أو النظام الأساسي المعتمد|نقاط الضعف في نظام التشغيل|الثغرات في منتجات البرامج|تقييم تكوين نظام التشغيل|تقييم تكوين عناصر التحكم في الأمان|تقييم تكوين منتج البرنامج
:---|:---|:---|:---|:---|:---
Windows 7|نعم|غير معتمد|غير معتمد|غير معتمد|غير معتمد
Windows 8.1|نعم|نعم|نعم|نعم|نعم
Windows 10 الإصدارات 1607-1703|نعم|غير معتمد|غير معتمد|غير معتمد|غير معتمد
Windows 10 الإصدار 1709 أو الإصدارات الأحدث|نعم|نعم|نعم|نعم|نعم
Windows 11|نعم|نعم|نعم|نعم|نعم
Windows Server 2008 R2|نعم|نعم|نعم|نعم|نعم
Windows Server 2012 R2|نعم|نعم|نعم|نعم|نعم
Windows Server 2016‏|نعم|نعم|نعم|نعم|نعم
Windows Server 2019|نعم|نعم|نعم|نعم|نعم
Windows Server 2022|نعم|نعم|نعم|غير معتمد|نعم
macOS 10.14 "Mojave" والأعلى|نعم|نعم|نعم|نعم|نعم 
Red Hat Enterprise Linux 7.2 أو الإصدارات الأعلى بما في ذلك إصدارات EUS المطابقة (\* راجع إشعار "هام" أدناه)|نعم|نعم|نعم|نعم|نعم
CentOS 7.2 أو أعلى|نعم|نعم|نعم|نعم|نعم
Ubuntu 16.04 LTS أو LTS الأعلى|نعم|نعم|نعم|نعم|نعم
Oracle Linux 7.2 أو أعلى|نعم|نعم|نعم|نعم|نعم
SUSE Linux Enterprise Server 12 أو أعلى|نعم|نعم|نعم|نعم|نعم
Linux Debian 9 أو أعلى|نعم|نعم|نعم|نعم|نعم
Android 6.0 أو إصدار أعلى|نعم|نعم|غير معتمد|غير معتمد|غير معتمد
iOS 12.0 أو أعلى|نعم|غير معتمد|غير معتمد|غير معتمد|غير معتمد

> [!NOTE]
> لا تتوفر بعض الميزات لنظام التشغيل على مستوى أدنى، تحقق من Microsoft 365 Defender المدخل للحصول على مزيد من التفاصيل حول نظام التشغيل المعتمد.

> [!IMPORTANT]
> \* Red Hat Enterprise Linux: "يتم توفير بيانات الثغرة الأمنية المتوفرة والموضحة كجزء من خدمات Microsoft Defender for Endpoint الخاصة بك بشكلها الخام، "AS IS"، من Red Hat, Inc. وقد لا تكون منتهي الصلاحية. يتم ترخيص البيانات التي يمكن الوصول إليها في API بيانات أمان Red Hat بموجب الترخيص الدولي Creative Commons Attribution 4.0. تتحمل مسؤولية استخدام هذه البيانات. وتنقر شركة Microsoft ومورديها من جهة خارجية عن أي مسؤولية وكلية عن الأضرار المترتبة وغير المباشرة الأخرى وعلى الضمانات الضمنية، بما في ذلك الضمانات الضمنية بعدم الانتهاك والتاجرة واللياقة لغرض معين. © 2020 Red Hat. كافة الحقوق محفوظة. © 2020 Microsoft. كل الحقوق محفوظة"."

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [المتطلبات الأساسية & الأذونات](tvm-prerequisites.md)
