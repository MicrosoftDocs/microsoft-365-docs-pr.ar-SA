---
title: تخطيط عملية Microsoft Defender لنقطة النهاية النشر
description: تحديد أفضل Microsoft Defender لنقطة النهاية نشر لبيئة
keywords: النشر، التخطيط، استراتيجية النشر، السحابة الأصلية، الإدارة، على prem، التقييم، التكوين، نهج المجموعة المحلي، gp، مدير نقطة النهاية، mem
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 05ae6e0669784aef515d678835f0fa48be0f9f3f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471242"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>تخطيط عملية Microsoft Defender لنقطة النهاية النشر

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

خطط Microsoft Defender لنقطة النهاية النشر بحيث يمكنك تكبير قدرات الأمان داخل المجموعة وحماية المؤسسة بشكل أفضل من التهديدات الإلكترونية.

يوفر هذا الحل إرشادات حول كيفية تحديد بنية البيئة، وتحديد نوع أداة النشر الأكثر ملائمة لاحتياجاتك، وإرشادات حول كيفية تكوين القدرات.

:::image type="content" source="images/deployment-guide-plan.png" alt-text="تدفق النشر" lightbox="images/deployment-guide-plan.png":::

## <a name="step-1-identify-architecture"></a>الخطوة 1: تحديد الهندسة

نحن ندرك أن كل بيئة مؤسسة فريدة، لذلك قمنا ب توفير العديد من الخيارات لتعطيك المرونة في اختيار كيفية نشر الخدمة.

استنادا إلى بيئتك، تكون بعض الأدوات أكثر ملاءمة لبعض التصميمات.

استخدم المواد التالية لتحديد بنية Defender لنقطة النهاية المناسبة التي تلائم مؤسستك بشكل أفضل.

| عنصر | الوصف |
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="استراتيجية نشر Defender لنقطة النهاية" lightbox="images/mde-deployment-strategy.png":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | تساعدك المواد الهندسية على التخطيط لنشرك للهندسة التالية: <ul><li> السحابة الأصلية </li><li> الإدارة المشاركة </li><li> في الموقع</li><li>التقييم واللوح المحلي</li>

## <a name="step-2-select-deployment-method"></a>الخطوة 2: تحديد طريقة النشر

| نقطة النهاية     | أداة النشر                       |
|--------------|------------------------------------------|
| **بالنسبة لنظام التشغيل**  |  [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [إدارة نقاط النهاية من Microsoft/Mobile إدارة الأجهزة](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [برامج VDI النصية](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [برنامج نصي محلي](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [الأجهزة إدارة الجهاز](mac-install-with-other-mdm.md) |
| **Linux Server** | [برنامج نصي محلي](linux-install-manually.md) <br> [مهى](linux-install-with-puppet.md) <br> [غير قابل للطي](linux-install-with-ansible.md)|
| **iOS**      | [إدارة نقاط النهاية من Microsoft](ios-install.md)                                |
| **Android**  | [إدارة نقاط النهاية من Microsoft](android-intune.md)               | 

يسرد الجدول التالي نقاط النهاية المعتمدة وأداة النشر المقابلة التي يمكنك استخدامها حتى تتمكن من التخطيط للنشر بشكل مناسب.

|نقطة النهاية|أداة النشر|
|---|---|
|**بالنسبة لنظام التشغيل**|[البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [إدارة نقاط النهاية من Microsoft/Mobile إدارة الأجهزة](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [برامج VDI النصية](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-azure-defender)|
|**macOS**|[برنامج نصي محلي](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [الأجهزة إدارة الجهاز](mac-install-with-other-mdm.md)|
|**Linux Server**|[برنامج نصي محلي](linux-install-manually.md) <br> [مهى](linux-install-with-puppet.md) <br> [غير قابل للطي](linux-install-with-ansible.md)|
|**iOS**|[مستند إلى التطبيق](ios-install.md)|
|**Android**|[إدارة نقاط النهاية من Microsoft](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>الخطوة 3: تكوين القدرات

بعد إعداد نقاط النهاية، قم بتكوين قدرات الأمان في Defender for Endpoint بحيث يمكنك تكبير حماية الأمان القوية المتوفرة في المجموعة. تتضمن الإمكانات:

- الكشف عن نقطة النهاية والاستجابة لها
- حماية الجيل التالي
- الحد من سطح الهجوم

## <a name="related-topics"></a>المواضيع ذات الصلة

- [مراحل النشر](deployment-phases.md)
