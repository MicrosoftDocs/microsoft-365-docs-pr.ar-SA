---
title: أجهزة Windows باستخدام برنامج نصي محلي
description: استخدم برنامج نصي محلي لنشر حزمة التكوين على الأجهزة لتمكين تهيئة الأجهزة للخدمة.
keywords: تكوين الأجهزة باستخدام برنامج نصي محلي، وإدارة الأجهزة، وتكوين Microsoft Defender لنقطة النهاية الكمبيوتر
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1ea1661a89585d46aa5fc234f6f88be66512c1be
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468688"
---
# <a name="onboard-windows-devices-using-a-local-script"></a>أجهزة Windows باستخدام برنامج نصي محلي

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

يمكنك أيضا إعادة تشغيل الأجهزة الفردية يدويا في Defender for Endpoint. قد ترغب في إجراء ذلك أولا عند اختبار الخدمة قبل الالتزام بتك الجديدة لجميع الأجهزة في الشبكة.

> [!IMPORTANT]
> تم تحسين هذا البرنامج النصي للاستخدام على ما يصل إلى عشرة أجهزة.
> البرمجة النصية المحلية هي طريقة خاصة لتكقيم Microsoft Defender لنقطة النهاية.
> يتم تعيين معدل تكرار الإبلاغ عن البيانات أعلى من استخدام أساليب التكهين الأخرى عند التكديب باستخدام برنامج نصي محلي.
> هذا الإعداد لأغراض التقييم ولا يستخدم عادة في عمليات نشر الإنتاج. لهذا السبب، هناك مخاوف بشأن التأثير البيئي، لذلك نوصي بقصر عدد عمليات النشر باستخدام البرامج النصية المحلية على عشرة عمليات.
> إذا كنت تقوم بالنشر في بيئة إنتاج كما هو موضح مسبقا، فاستخدم [](configure-endpoints.md) خيارات نشر أخرى مثل نهج المجموعة أو Microsoft Endpoint Configuration Manager.

اطلع على [ملف PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf) [أو Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) لرؤية المسارات المختلفة في نشر Defender لنقطة النهاية. 

## <a name="onboard-devices"></a>الأجهزة المجهزة 

1.  افتح حزمة تكوين GP .zip ملف (*WindowsDefenderATPOnboardingPackage.zip*) الذي قمت بتنزيلها من معالج إعداد الخدمة. يمكنك أيضا الحصول على الحزمة من مدخل Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">:</a>

    1. في جزء التنقل **، حدد الإعدادات** >  **EndpointsDevice** >  **managementOnboarding** > .


اطلع على [ملف PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [أو Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) لرؤية المسارات المختلفة في نشر Defender لنقطة النهاية.

1. افتح حزمة تكوين GP .zip ملف (*WindowsDefenderATPOnboardingPackage.zip*) الذي قمت بتنزيلها من معالج إعداد الخدمة. يمكنك أيضا الحصول على الحزمة من مدخل Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">:</a>
    1. في جزء التنقل **، حدد الإعدادات** \> **إدارة** \>  \> أجهزة نقاط **النهاية.**
    2. حدد Windows 10 أو Windows 11 نظام التشغيل.
    3. في الحقل **أسلوب النشر** ، حدد **برنامج نصي محلي**.
    4. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

2. استخراج محتويات حزمة التكوين إلى موقع على الجهاز الذي تريد االلوح به (على سبيل المثال، سطح المكتب). يجب أن يكون لديك ملف يسمى *WindowsDefenderATPLocalOnboardingScript.cmd*.

3. افتح موجه سطر أوامر مرتفعا على الجهاز و تشغيل البرنامج النصي:
   1. انتقل إلى **ابدأ** وا اكتب **cmd**.
   2. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

    :::image type="content" source="images/run-as-admin.png" alt-text="يشير قائمة البدء النافذة إلى تشغيل كمسؤول" lightbox="images/run-as-admin.png":::

4.  اكتب موقع ملف البرنامج النصي. إذا نسخت الملف إلى سطح المكتب، فا اكتب: *٪userprofile٪\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd*

5.  اضغط على **المفتاح Enter** أو انقر فوق **موافق**.

للحصول على معلومات حول كيفية التحقق من امتثال الجهاز يدويا وإعلام بيانات المستشعر بشكل صحيح، راجع استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية [التكهين](troubleshoot-onboarding.md).

> [!TIP]
> بعد تشغيل الجهاز، يمكنك أن تختار تشغيل اختبار الكشف للتحقق من أن الجهاز مواد بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على نقطة نهاية Microsoft Defender لنقطة النهاية حديثا](run-detection-test.md).

## <a name="configure-sample-collection-settings"></a>تكوين إعدادات المجموعة العينة

لكل جهاز، يمكنك تعيين قيمة تكوين لتحدد ما إذا كان يمكن تجميع عينات من الجهاز عند تقديم طلب عبر Microsoft 365 Defender لإرسال ملف لتحليله بعمق.

يمكنك تكوين إعداد المشاركة العينة يدويا على الجهاز باستخدام *regedit* أو إنشاء ملف *.reg* وتشغيله.

يتم تعيين التكوين من خلال إدخال مفتاح التسجيل التالي:

```console
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

حيث يكون نوع الاسم D-WORD. القيم المحتملة هي:

- 0 - لا يسمح بالمشاركة العينة من هذا الجهاز
- 1 - يسمح بمشاركة كل أنواع الملفات من هذا الجهاز

القيمة الافتراضية في حالة عدم وجود مفتاح التسجيل هي 1.

## <a name="run-a-detection-test-to-verify-onboarding"></a>تشغيل اختبار الكشف للتحقق من ال

بعد تشغيل الجهاز، يمكنك أن تختار تشغيل اختبار الكشف للتحقق من أن الجهاز مواد بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية جديد](run-detection-test.md).

## <a name="offboard-devices-using-a-local-script"></a>أجهزة إيقاف التشغيل باستخدام برنامج نصي محلي

لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

1. احصل على حزمة إيقاف التشغيل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">من مدخل Microsoft 365 Defender:</a>
    1. في جزء التنقل **، حدد الإعدادات** \> **إيقاف** \>  \> تشغيل إدارة أجهزة **نقاط النهاية**.
    2. حدد Windows 10 أو Windows 11 نظام التشغيل.
    3. في الحقل **أسلوب النشر** ، حدد **برنامج نصي محلي**.
    4. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

2. استخراج محتويات الملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه بواسطة الأجهزة. يجب أن يكون لديك ملف *يسمى WindowsDefenderATPOffboardingScript_valid_until_YYYY MM-DD.cmd*.

3. افتح موجه سطر أوامر مرتفعا على الجهاز و تشغيل البرنامج النصي:
   1. انتقل إلى **ابدأ** وا اكتب **cmd**.
   2. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

      :::image type="content" source="images/run-as-admin.png" alt-text="يشير Windows قائمة البدء إلى الخيار &quot;تشغيل كمسؤول&quot;" lightbox="images/run-as-admin.png":::

4. اكتب موقع ملف البرنامج النصي. إذا قمت بنسخ الملف إلى سطح المكتب، فا اكتب: *٪userprofile٪\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

5. اضغط على **المفتاح Enter** أو انقر فوق **موافق**.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.

## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز

يمكنك اتباع خطوات التحقق المختلفة في استكشاف مشاكل التكميل وإصلاحها للتحقق من اكتمال البرنامج النصي بنجاح وتشغيل الوكيل.[](troubleshoot-onboarding.md)

يمكن أيضا القيام بالمراقبة مباشرة على المدخل، أو باستخدام أدوات النشر المختلفة.

### <a name="monitor-devices-using-the-portal"></a>مراقبة الأجهزة باستخدام المدخل

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل</a>.
2. انقر **فوق مخزون الأجهزة**.
3. تحقق من ظهور الأجهزة.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows باستخدام نهج المجموعة](configure-endpoints-gp.md)
- [أجهزة Windows التي تستخدم Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [أجهزة Windows باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول](configure-endpoints-mdm.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)
- [تشغيل اختبار الكشف على جهاز تم Microsoft Defender لنقطة النهاية جديد](run-detection-test.md)
- [استكشاف مشاكل Microsoft Defender لنقطة النهاية في الحافظة وإصلاحها](troubleshoot-onboarding.md)
