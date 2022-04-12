---
title: تخطيط نشر Microsoft Defender لنقطة النهاية
description: حدد أفضل استراتيجية نشر Microsoft Defender لنقطة النهاية للبيئة الخاصة بك
keywords: النشر والتخطيط واستراتيجية النشر والسحابة الأصلية والإدارة والإعداد والتقييم والإلحاق والنهج المحلي ونهج المجموعة وgp ومدير نقطة النهاية وال mem
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
ms.openlocfilehash: 63996aa4d046ac719e0e6b98ed4c5980e0d979be
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783854"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>تخطيط نشر Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

خطط لتوزيع Microsoft Defender لنقطة النهاية الخاص بك بحيث يمكنك زيادة قدرات الأمان داخل المجموعة وحماية مؤسستك بشكل أفضل من التهديدات الإلكترونية.

يوفر هذا الحل إرشادات حول كيفية تحديد بنية البيئة الخاصة بك، وتحديد نوع أداة النشر التي تناسب احتياجاتك بشكل أفضل، وإرشادات حول كيفية تكوين القدرات.

:::image type="content" source="images/deployment-guide-plan.png" alt-text="تدفق النشر" lightbox="images/deployment-guide-plan.png":::

## <a name="step-1-identify-architecture"></a>الخطوة 1: تحديد البنية

نحن نفهم أن كل بيئة مؤسسة فريدة من نوعها، لذلك قدمنا العديد من الخيارات لمنحك المرونة في اختيار كيفية نشر الخدمة.

اعتمادا على بيئتك، تكون بعض الأدوات أكثر ملاءمة لبنى معينة.

استخدم المواد التالية لتحديد بنية Defender المناسبة لنقطة النهاية التي تعمل على إنشاء أفضل مجموعات لمؤسستك.

| البند | الوصف |
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="استراتيجية نشر Defender لنقطة النهاية" lightbox="images/mde-deployment-strategy.png":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | تساعدك المواد المعمارية على تخطيط التوزيع الخاص بك للبنى التالية: <ul><li> السحابة الأصلية </li><li> الإدارة المشتركة </li><li> محلي</li><li>التقييم والإلحاق المحلي</li>

## <a name="step-2-select-deployment-method"></a>الخطوة 2: تحديد أسلوب النشر

| نقطه النهايه     | أداة النشر                       |
|--------------|------------------------------------------|
| **بالنسبة لنظام التشغيل**  |  [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [إدارة الأجهزة إدارة نقاط النهاية من Microsoft/ الهاتف الجوال](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [البرامج النصية ل VDI](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **ماك**    | [البرنامج النصي المحلي](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [PRO JAMF](mac-install-with-jamf.md) <br> [إدارة الجهاز الجوال](mac-install-with-other-mdm.md) |
| **Linux Server** | [البرنامج النصي المحلي](linux-install-manually.md) <br> [دميه](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **دائره الرقابه الداخليه**      | [إدارة نقاط النهاية من Microsoft](ios-install.md)                                |
| **الروبوت**  | [إدارة نقاط النهاية من Microsoft](android-intune.md)               | 

يسرد الجدول التالي نقاط النهاية المدعومة وأداة النشر المقابلة التي يمكنك استخدامها بحيث يمكنك التخطيط للتوزيع بشكل مناسب.

|نقطه النهايه|أداة النشر|
|---|---|
|**بالنسبة لنظام التشغيل**|[البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [إدارة الأجهزة إدارة نقاط النهاية من Microsoft/ الهاتف الجوال](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [البرامج النصية ل VDI](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)|
|**ماك**|[البرنامج النصي المحلي](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [PRO JAMF](mac-install-with-jamf.md) <br> [إدارة الجهاز الجوال](mac-install-with-other-mdm.md)|
|**Linux Server**|[البرنامج النصي المحلي](linux-install-manually.md) <br> [دميه](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**دائره الرقابه الداخليه**|[مستند إلى التطبيق](ios-install.md)|
|**الروبوت**|[إدارة نقاط النهاية من Microsoft](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>الخطوة 3: تكوين القدرات

بعد إلحاق نقاط النهاية، قم بتكوين قدرات الأمان في Defender لنقطة النهاية بحيث يمكنك زيادة حماية الأمان القوية المتوفرة في المجموعة. تتضمن الإمكانات ما يلي:

- الكشف عن نقطة النهاية والاستجابة لها
- حماية الجيل التالي
- قواعد تقليل الأجزاء المعرضة للهجوم

## <a name="related-topics"></a>المواضيع ذات الصلة

- [مراحل النشر](deployment-phases.md)
