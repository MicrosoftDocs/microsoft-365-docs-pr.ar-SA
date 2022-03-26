---
title: دمج Microsoft Defender لنقطة النهاية مع حلول Microsoft الأخرى
description: تعرف على كيفية تكامل Microsoft Defender for Endpoint مع حلول Microsoft الأخرى، بما في ذلك Microsoft Defender for Identity و Microsoft Defender for Cloud.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender، الوصول الشرطي، office، Microsoft Defender ل Endpoint، microsoft defender للهوية، microsoft defender ل office، Azure Defender، أمان تطبيق microsoft السحابي، azure sentinel
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4f220b16b0402215aa1fad0681edf241b61062ed
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/02/2022
ms.locfileid: "63573407"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Microsoft Defender ل Endpoint وحلول Microsoft الأخرى

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>التكامل مع حلول Microsoft الأخرى

يتكامل Microsoft Defender for Endpoint مباشرة مع حلول Microsoft المختلفة.

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender for Cloud

يوفر Microsoft Defender ل Endpoint حلا شاملا لحماية الخادم، بما في ذلك الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية) على Windows Servers.

### <a name="microsoft-sentinel"></a>Microsoft Sentinel

يتيح لك موصل Microsoft Defender ل Endpoint دفق التنبيهات من Microsoft Defender ل Endpoint إلى Microsoft Sentinel. سيمكنك ذلك من تحليل أحداث الأمان عبر مؤسستك بشكل أكثر شمولية، فضلا عن إنشاء دفاتر تشغيل للاستجابة الفورية والفعالة.

### <a name="azure-information-protection"></a>Azure Information Protection

لقد تم إهمال تكامل Azure Information Protection مؤخرا حيث تتضمن قدرات DLP الخاصة بنقطة النهاية حلا محسنا للاكتشاف والحماية للبيانات الحساسة المخزنة على أجهزة نقاط النهاية التي تسهل رؤية أكبر وتكامل أكبر بين الحلول. تم الإعلان عن ذلك في المدونة [التالية](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555). نوصي بأن ينتقل العملاء إلى استخدام نقطة النهاية DLP.

### <a name="conditional-access"></a>الوصول الشرطي

يتم دمج نقاط مخاطر الأجهزة الديناميكية في Microsoft Defender for Endpoint في تقييم الوصول الشرطي، مع ضمان وصول الأجهزة الآمنة فقط إلى الموارد.

### <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender لتطبيقات السحابة

تستفيد Microsoft Defender for Cloud Apps من Microsoft Defender من إشارات نقطة النهاية للسماح بالرؤية المباشرة في استخدام التطبيقات السحابية بما في ذلك استخدام خدمات السحابة غير المضمنة (ظل IT) من جميع الأجهزة التي يتم مراقبتها من Microsoft Defender ل Endpoint.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

الأنشطة المريبة هي عمليات يتم تشغيلها ضمن سياق المستخدم. يوفر التكامل بين Microsoft Defender ل Endpoint و Microsoft Defender for Identity المرونة اللازمة لإجراء التحقيق بشأن الأمان عبر الإنترنت عبر الأنشطة والهويات.

### <a name="microsoft-defender-for-office"></a>Microsoft Defender Office

يساعد [defender for Office 365](/office365/securitycompliance/office-365-atp) على حماية مؤسستك من البرامج الضارة في رسائل البريد الإلكتروني أو الملفات من خلال ارتباطات خزينة، ومرفقات خزينة، وإمكانيات متقدمة لمكافحة التصيد الاحتيالي، وإمكانيات المعلومات الاستخبارية المنتحلة. يمكن التكامل بين Microsoft Defender for Office 365 و Microsoft Defender ل Endpoint محللي الأمان من الانتقال إلى أعلى البث للتحقق من نقطة إدخال هجوم. من خلال مشاركة المعلومات الاستخبارية للتهديدات، يمكن احتواء الهجمات وحظرها.

> [!NOTE]
> يتم عرض Office 365 البيانات الخاصة بالأحداث خلال آخر 30 يوما. بالنسبة للتنبيهات، يتم عرض Office 365 البيانات استنادا إلى وقت النشاط الأول. بعد ذلك، لن تكون البيانات متوفرة في Defender for Office 365.

### <a name="skype-for-business"></a>Skype for Business

يوفر Skype for Business التكامل طريقة للمحللين للتواصل مع مستخدم أو مالك جهاز يحتمل أن يكون فيه اختراق من خلال زر بسيط من المدخل.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender

باستخدام Microsoft 365 Defender، يشكل Microsoft Defender ل Endpoint وحلول أمان Microsoft المتنوعة مجموعة موحدة من الدفاع الخاص بالمؤسسات قبل الخرق وبعده تتكامل عادة عبر نقاط النهاية والهوية والبريد الإلكتروني والتطبيقات للكشف عن الهجمات المعقدة ومنعها التحقيق فيها والرد عليها تلقائيا.

[تعرف على المزيد حول Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [تكوين التكامل والميزات المتقدمة الأخرى](advanced-features.md)
- [Microsoft 365 Defender عامة](/microsoft-365/security/defender/microsoft-365-defender)
- [تشغيل Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable)
- [حماية المستخدمين والبيانات والأجهزة باستخدام الوصول الشرطي](conditional-access.md)
