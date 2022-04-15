---
title: نشر Microsoft Defender لنقطة النهاية في الحلقات
description: تعرف على كيفية نشر Microsoft Defender لنقطة النهاية في الحلقات
keywords: النشر، الحلقات، التقييم، الإصدار التجريبي، الإصدار الأولي العاجل، الإصدار الآجل ل insider، الإعداد، الإلحاق، المرحلة، النشر، النشر، الاعتماد، التكوين
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
- m365solution-endpointprotect
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e308b1c1d8c26a4ec3d6b3044501ffe1ce92e1c7
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862863"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>نشر Microsoft Defender لنقطة النهاية في الحلقات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يمكن نشر Microsoft Defender لنقطة النهاية باستخدام نهج نشر يستند إلى حلقة.

يمكن تطبيق حلقات التوزيع في السيناريوهات التالية:

- [عمليات نشر جديدة](#new-deployments)
- [عمليات النشر الموجودة](#existing-deployments)

## <a name="new-deployments"></a>عمليات نشر جديدة

:::image type="content" source="images/deployment-rings.png" alt-text="حلقات التوزيع." lightbox="images/deployment-rings.png":::

النهج المستند إلى الحلقة هو طريقة لتحديد مجموعة من نقاط النهاية لإلحاقها والتحقق من استيفاء معايير معينة قبل المتابعة لنشر الخدمة على مجموعة أكبر من الأجهزة. يمكنك تحديد معايير الخروج لكل حلقة والتأكد من أنها مستوفية قبل الانتقال إلى الحلقة التالية.

يساعد اعتماد النشر المستند إلى الحلقة على تقليل المشكلات المحتملة التي قد تنشأ أثناء طرح الخدمة. من خلال تجربة عدد معين من الأجهزة أولا، يمكنك تحديد المشكلات المحتملة وتخفيف المخاطر المحتملة التي قد تنشأ.

يوفر الجدول 1 مثالا على حلقات النشر التي قد تستخدمها.

**الجدول 1**:

|حلقة التوزيع|الوصف|
|---|---|
|تقييم|الحلقة 1: تحديد 50 نظاما لاختبار الإصدار التجريبي|
|التجريبيه|الحلقة 2: تحديد نقاط النهاية 50-100 التالية في بيئة الإنتاج|
|النشر الكامل|الحلقة 3: طرح الخدمة لبقية البيئة بزيادات أكبر|

### <a name="exit-criteria"></a>معايير الإنهاء

يمكن أن تتضمن مجموعة أمثلة من معايير الخروج لهذه الحلقات ما يلي:

- تظهر الأجهزة في قائمة مخزون الأجهزة
- تظهر التنبيهات في لوحة المعلومات
- [تشغيل اختبار الكشف](run-detection-test.md)
- [تشغيل هجوم محاكاة على جهاز](attack-simulations.md)

### <a name="evaluate"></a>تقييم

حدد عددا صغيرا من أجهزة الاختبار في بيئتك لإلحاق الخدمة. من الناحية المثالية، ستكون هذه الأجهزة أقل من 50 نقطة نهاية.

### <a name="pilot"></a>التجريبيه

يدعم Microsoft Defender لنقطة النهاية مجموعة متنوعة من نقاط النهاية التي يمكنك إلحاقها للخدمة. في هذه الحلقة، حدد عدة أجهزة لإلحاقها واستنادا إلى معايير الخروج التي تحددها، قررت المتابعة إلى حلقة النشر التالية.

يعرض الجدول التالي نقاط النهاية المدعومة والأداة المقابلة التي يمكنك استخدامها لإلحاق الأجهزة للخدمة.

|نقطه النهايه|أداة النشر|
|---|---|
|**بالنسبة لنظام التشغيل**|[البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br> ملاحظة: إذا كنت تريد نشر أكثر من 10 أجهزة في بيئة إنتاج، فاستخدم أسلوب نهج المجموعة بدلا من ذلك أو الأدوات المعتمدة الأخرى المدرجة أدناه.<br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [إدارة الأجهزة إدارة نقاط النهاية من Microsoft/ الهاتف الجوال](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [البرامج النصية ل VDI](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)|
|**ماك**|[البرنامج النصي المحلي](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [PRO JAMF](mac-install-with-jamf.md) <br> [إدارة الجهاز الجوال](mac-install-with-other-mdm.md)|
|**Linux Server**|[البرنامج النصي المحلي](linux-install-manually.md) <br> [دميه](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**دائره الرقابه الداخليه**|[إدارة نقاط النهاية من Microsoft](ios-install.md)|
|**الروبوت**|[إدارة نقاط النهاية من Microsoft](android-intune.md)|

### <a name="full-deployment"></a>النشر الكامل

في هذه المرحلة، يمكنك استخدام مادة [نشر الخطة](deployment-strategy.md) لمساعدتك على التخطيط للتوزيع.

استخدم المواد التالية لتحديد بنية Microsoft Defender لنقطة النهاية المناسبة التي تلائم مؤسستك.

|البند|الوصف|
|---|---|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="استراتيجية نشر Microsoft Defender لنقطة النهاية." lightbox="images/mde-deployment-strategy.png":::](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) \| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)|تساعدك المواد المعمارية على تخطيط التوزيع الخاص بك للبنى التالية: <ul><li> السحابة الأصلية </li><li> الإدارة المشتركة </li><li> محلي</li><li>التقييم والإلحاق المحلي</li></ul>|

## <a name="existing-deployments"></a>عمليات النشر الموجودة

### <a name="windows-endpoints"></a>نقاط نهاية Windows

بالنسبة لخوادم Windows و/أو Windows، يمكنك تحديد عدة أجهزة لاختبارها مسبقا (قبل تصحيح الثلاثاء) باستخدام **برنامج التحقق من صحة تحديث الأمان (أداة التحقق من صحة تحديث الأمان(1).**

لمزيد من المعلومات، اطلع على:

- [ما هو برنامج التحقق من صحة تحديث الأمان](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [برنامج التحقق من صحة تحديث البرامج وإنشاء مركز الحماية من البرامج الضارة لـ Microsoft - الجزء 4 من المخطط الزمني التفاعلي ل TwC](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>نقاط النهاية غير Windows

باستخدام macOS وLinux، يمكنك أخذ نظامين وتشغيلهما في قناة Beta.

> [!NOTE]
> من الناحية المثالية مسؤول أمان واحد على الأقل ومطور واحد حتى تتمكن من العثور على مشكلات التوافق والأداء والموثوقية قبل أن يدخل البناء في القناة الحالية.

يحدد اختيار القناة نوع التحديثات التي يتم تقديمها لجهازك ومعدل تكرارها. الأجهزة في Beta هي أول الأجهزة التي تتلقى التحديثات والميزات الجديدة، متبوعة لاحقا بالمعاينة وأخيرا الحالية.

:::image type="content" source="images/insider-rings.png" alt-text="الحلقات الداخلية." lightbox="images/insider-rings.png":::

لمعاينة الميزات الجديدة وتقديم ملاحظات مبكرة، يوصى بتكوين بعض الأجهزة في مؤسستك لاستخدام الإصدار بيتا أو المعاينة.

> [!WARNING]
> يتطلب تبديل القناة بعد التثبيت الأولي إعادة تثبيت المنتج. لتبديل قناة المنتج: قم بإلغاء تثبيت الحزمة الموجودة، وأعد تكوين جهازك لاستخدام القناة الجديدة، واتبع الخطوات الواردة في هذا المستند لتثبيت الحزمة من الموقع الجديد.
