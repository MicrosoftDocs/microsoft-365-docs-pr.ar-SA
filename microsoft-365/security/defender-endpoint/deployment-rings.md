---
title: نشر Microsoft Defender لنقطة النهاية في حلقات
description: تعرف على كيفية نشر Microsoft Defender لنقطة النهاية في حلقات
keywords: النشر، الرنين، التقييم، التجربة، سرعة insider، بطء insider، الإعداد، التهيئة، التهيئة، اللوحة، المرحلة، النشر، النشر، الاعتماد، التكوين
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
ms.openlocfilehash: a7a9673591f4d77197390541a58169a58b04fe91
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63569851"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>نشر Microsoft Defender لنقطة النهاية في حلقات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يمكن نشر Microsoft Defender لنقطة النهاية باستخدام نهج نشر مستند إلى الرنين.

يمكن تطبيق حلقات النشر في السيناريوهات التالية:

- [عمليات نشر جديدة](#new-deployments)
- [عمليات النشر الموجودة](#existing-deployments)

## <a name="new-deployments"></a>عمليات نشر جديدة

![صورة حلقات النشر.](images/deployment-rings.png)

النهج المستند إلى الرنين هو أسلوب لتحديد مجموعة من نقاط النهاية لل متن الطائرة والتحقق من تحقيق معايير معينة قبل المتابعة لنشر الخدمة على مجموعة أكبر من الأجهزة. يمكنك تحديد معايير الخروج لكل حلقة والتأكد من أنها راضية قبل الانتقال إلى الحلقة التالية.

يساعد استخدام النشر المستند إلى الرنين على تقليل المشاكل المحتملة التي قد تنشأ أثناء نشر الخدمة. من خلال تجريب عدد معين من الأجهزة أولا، يمكنك تحديد المشاكل المحتملة وتخفيف المخاطر المحتملة التي قد تنشأ.

يوفر الجدول 1 مثالا على حلقات النشر التي قد تستخدمها.

**الجدول 1**:

<br>

****

|حلقة النشر|الوصف|
|---|---|
|تقييم|الحلقة 1: تحديد 50 نظام اختبار تجريبي|
|طيار|الحلقة 2: تحديد نقاط النهاية من 50 إلى 100 التالية في بيئة الإنتاج|
|النشر الكامل|الحلقة 3: طرح الخدمة لبقية البيئة بزيادات أكبر|
|

### <a name="exit-criteria"></a>معايير الخروج

يمكن أن تتضمن مجموعة أمثلة لمعايير الخروج لهذه الحلقات ما يلي:

- تظهر الأجهزة في قائمة مخزون الأجهزة
- تظهر التنبيهات في لوحة المعلومات
- [تشغيل اختبار الكشف](run-detection-test.md)
- [تشغيل هجوم محاكاة على جهاز](attack-simulations.md)

### <a name="evaluate"></a>تقييم

حدد عددا صغيرا من أجهزة الاختبار في بيئتك لتهيئة الخدمة. وبشكل مثالي، ستكون هذه الأجهزة أقل من 50 نقطة نهاية.

### <a name="pilot"></a>طيار

يدعم Microsoft Defender ل Endpoint مجموعة متنوعة من نقاط النهاية التي يمكنك ا متنها في الخدمة. في هذه الحلقة، حدد عدة أجهزة لداخلها واستنادا إلى معايير الخروج التي تحددها، قرر المتابعة إلى حلقة النشر التالية.

يعرض الجدول التالي نقاط النهاية المعتمدة والأداة المقابلة التي يمكنك استخدامها للأجهزة المجهزة للخدمة.

| نقطة النهاية     | أداة النشر                       |
|--------------|------------------------------------------|
| **بالنسبة لنظام التشغيل**  |  [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br> ملاحظة: إذا كنت تريد نشر أكثر من 10 أجهزة في بيئة إنتاج، فاستخدم أسلوب نهج المجموعة بدلا من ذلك أو الأدوات المعتمدة الأخرى المذكورة أدناه.<br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [إدارة نقاط النهاية من Microsoft/ Mobile Device Manager](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [برامج VDI النصية](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [برنامج نصي محلي](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [إدارة أجهزة المحمول](mac-install-with-other-mdm.md) |
| **Linux Server** | [برنامج نصي محلي](linux-install-manually.md) <br> [مهى](linux-install-with-puppet.md) <br> [غير قابل للطي](linux-install-with-ansible.md)|
| **iOS**      | [إدارة نقاط النهاية من Microsoft](ios-install.md)                                |
| **Android**  | [إدارة نقاط النهاية من Microsoft](android-intune.md)               |

### <a name="full-deployment"></a>النشر الكامل

في هذه المرحلة، يمكنك [استخدام مادة نشر](deployment-strategy.md) الخطة لمساعدتك على التخطيط للنشر.

استخدم المواد التالية لتحديد بنية Microsoft Defender المناسبة لنقطة النهاية التي تلائم مؤسستك بشكل أفضل.

|**عنصر**|**الوصف**|
|:-----|:-----|
|[![صورة مصغرة لا استراتيجية نشر نقطة النهاية ل Microsoft Defender.](images/mde-deployment-strategy.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | تساعدك المواد الهندسية على التخطيط لنشرك للهندسة التالية: <ul><li> السحابة الأصلية </li><li> الإدارة المشاركة </li><li> في الموقع</li><li>التقييم واللوح المحلي</li></ul>

## <a name="existing-deployments"></a>عمليات النشر الموجودة

### <a name="windows-endpoints"></a>Windows نقاط النهاية

بالنسبة Windows و/أو Windows، يمكنك تحديد عدة أجهزة لاختبارها مسبقا (قبل التصحيح يوم الثلاثاء) باستخدام برنامج التحقق من صحة تحديث الأمان **(SUVP).**

لمزيد من المعلومات، اطلع على:

- [ما هو برنامج التحقق من صحة تحديث الأمان](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [برنامج التحقق من صحة تحديث البرامج مركز الحماية من البرامج الضارة لـ Microsoft - الجزء 4 من المخطط الزمني التفاعلي TwC](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>نقاط النهاية Windows غير المنقطة

باستخدام macOS و Linux، يمكنك استخدام نظامين وتشغيلها في قناة Beta.

> [!NOTE]
> وبشكل مثالي، يوجد مسؤول أمان واحد على الأقل ومطور واحد حتى تتمكن من العثور على مشاكل التوافق والأداء والوثوقية قبل أن يتمكن الإصدار من الوصول إلى القناة الحالية.

يحدد اختيار القناة نوع التحديثات التي يتم تقديمها لجهازك وتكرارها. الأجهزة في Beta هي الأجهزة الأولى التي تتلقى التحديثات والميزات الجديدة، متبوعا لاحقا بمعاينة وأخيرا ب Current.

![صورة حلقات insider.](images/insider-rings.png)

من أجل معاينة الميزات الجديدة وتقديم ملاحظات مبكرة، من المستحسن تكوين بعض الأجهزة في المؤسسة لاستخدام بيتا أو معاينة.

> [!WARNING]
> يتطلب تبديل القناة بعد التثبيت الأولي إعادة تثبيت المنتج. لتبديل قناة المنتج: قم ب إلغاء تثبيت الحزمة الموجودة، ثم إعادة تكوين الجهاز لاستخدام القناة الجديدة، واتبع الخطوات الموجودة في هذا المستند لتثبيت الحزمة من الموقع الجديد.
