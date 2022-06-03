---
title: إلحاق أجهزة Windows باستخدام Configuration Manager
description: استخدم Configuration Manager لنشر حزمة التكوين على الأجهزة بحيث يتم إلحاقها بخدمة Defender for Endpoint.
keywords: إلحاق الأجهزة باستخدام sccm وإدارة الأجهزة وتكوين أجهزة Microsoft Defender لنقطة النهاية
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
ms.date: 09/22/2021
ms.technology: mde
ms.openlocfilehash: d60d01bd2a77d992110f85967196390f3dceae3d
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873699"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>إلحاق أجهزة Windows باستخدام Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager الفرع الحالي
- System Center 2012 R2 Configuration Manager

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)


يمكنك استخدام Configuration Manager لإلحاق نقاط النهاية بخدمة Microsoft Defender لنقطة النهاية. 

هناك العديد من الخيارات التي يمكنك استخدامها لإلحاق الأجهزة باستخدام Configuration Manager:
- [إلحاق الأجهزة باستخدام System Center Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [إرفاق المستأجر](/mem/configmgr/tenant-attach/)



بالنسبة إلى Windows Server 2012 R2 و Windows Server 2016 - بعد إكمال خطوات الإلحاق، ستحتاج إلى [تكوين العملاء System Center Endpoint Protection وتحديثهم](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
> لا يدعم Defender لنقطة النهاية الإعداد أثناء مرحلة [تجربة خارج الصندوق (OOBE](/windows-hardware/test/assessments/out-of-box-experience) ). تأكد من أن المستخدمين يكملون OOBE بعد تشغيل تثبيت Windows أو ترقيته.
>
> لاحظ أنه من الممكن إنشاء قاعدة الكشف على تطبيق Configuration Manager للتحقق باستمرار مما إذا كان قد تم إلحاق جهاز. التطبيق هو نوع مختلف من العناصر عن الحزمة والبرنامج.
> إذا لم يتم إلحاق جهاز بعد (بسبب الإكمال المعلق ل OOBE أو أي سبب آخر)، فسيعيد Configuration Manager محاولة إلحاق الجهاز حتى تكتشف القاعدة تغيير الحالة.
>
> يمكن إنجاز هذا السلوك عن طريق إنشاء قاعدة الكشف عن التحقق مما إذا كانت قيمة التسجيل "OnboardingState" (من النوع REG_DWORD) = 1.
> تقع قيمة التسجيل هذه ضمن "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
لمزيد من المعلومات، راجع [تكوين أساليب الكشف في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>تكوين إعدادات مجموعة العينة

لكل جهاز، يمكنك تعيين قيمة تكوين لتحديد ما إذا كان يمكن جمع العينات من الجهاز عند تقديم طلب من خلال Microsoft 365 Defender لإرسال ملف للتحليل العميق.

> [!NOTE]
> عادة ما تتم إعدادات التكوين هذه من خلال Configuration Manager.

يمكنك تعيين قاعدة توافق لعنصر التكوين في Configuration Manager لتغيير إعداد مشاركة العينة على جهاز.

يجب أن تكون هذه القاعدة عنصر تكوين قاعدة التوافق *المعالجة* الذي يعين قيمة مفتاح التسجيل على الأجهزة المستهدفة للتأكد من أنها شكاوى.

يتم تعيين التكوين من خلال إدخال مفتاح التسجيل التالي:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

حيث يكون نوع المفتاح هو D-WORD. القيم المحتملة هي:

- 0: لا يسمح بمشاركة عينة من هذا الجهاز
- 1: السماح بمشاركة كافة أنواع الملفات من هذا الجهاز

القيمة الافتراضية في حالة عدم وجود مفتاح التسجيل هي 1.

لمزيد من المعلومات حول System Center Configuration Manager Compliance، راجع [مقدمة حول إعدادات التوافق في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>إعدادات التكوين الموصى بها الأخرى

بعد إلحاق الأجهزة بالخدمة، من المهم الاستفادة من قدرات الحماية من التهديدات المضمنة من خلال تمكينها باستخدام إعدادات التكوين الموصى بها التالية.

### <a name="device-collection-configuration"></a>تكوين مجموعة الأجهزة

إذا كنت تستخدم Configuration Manager نقطة النهاية، الإصدار 2002 أو الإصدارات الأحدث، يمكنك اختيار توسيع النشر ليشمل خوادم أو عملاء من المستوى الأدنى.

### <a name="next-generation-protection-configuration"></a>تكوين حماية الجيل التالي

يوصى بإعدادات التكوين التالية:

#### <a name="scan"></a>المسح الضوئي

- فحص أجهزة التخزين القابلة للإزالة مثل محركات أقراص USB: نعم

#### <a name="real-time-protection"></a>الحماية في الوقت الحقيقي

- تمكين المراقبة السلوكية: نعم
- تمكين الحماية من التطبيقات غير المرغوب فيها عند التنزيل وقبل التثبيت: نعم

#### <a name="cloud-protection-service"></a>خدمة حماية السحابة

- نوع عضوية خدمة حماية السحابة: العضوية المتقدمة

#### <a name="attack-surface-reduction"></a>قواعد تقليل الأجزاء المعرضة للهجوم

تكوين كافة القواعد المتوفرة للتدقيق.

> [!NOTE]
> قد يؤدي حظر هذه الأنشطة إلى مقاطعة العمليات التجارية المشروعة. أفضل نهج هو تعيين كل شيء للتدقيق، وتحديد تلك الآمنة لتشغيلها، ثم تمكين تلك الإعدادات على نقاط النهاية التي لا تحتوي على اكتشافات إيجابية خاطئة.

#### <a name="network-protection"></a>حماية الشبكة

قبل تمكين حماية الشبكة في وضع التدقيق أو الحظر، تأكد من تثبيت تحديث النظام الأساسي لمكافحة البرامج الضارة، والذي يمكن الحصول عليه من [صفحة الدعم](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

#### <a name="controlled-folder-access"></a>الوصول إلى المجلدات الخاضعة للتحكم

تمكين الميزة في وضع التدقيق لمدة 30 يوما على الأقل. بعد هذه الفترة، راجع عمليات الكشف وأنشئ قائمة بالتطبيقات المسموح لها بالكتابة إلى الدلائل المحمية.

لمزيد من المعلومات، راجع [تقييم الوصول إلى المجلدات التي يتم التحكم فيها](evaluate-controlled-folder-access.md).

## <a name="run-a-detection-test-to-verify-onboarding"></a>تشغيل اختبار الكشف للتحقق من الإلحاق

بعد إلحاق الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أن الجهاز تم إلحاقه بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>إيقاف تشغيل الأجهزة باستخدام Configuration Manager

لأسباب تتعلق بالأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم الإلحاق المنتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة الإلحاق، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم وسيتم تضمينها أيضا في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر نهج الإلحاق والإلحاق على نفس الجهاز في نفس الوقت، وإلا فسيؤدي ذلك إلى تضاربات غير متوقعة.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>إيقاف تشغيل الأجهزة باستخدام الفرع الحالي إدارة نقاط النهاية من Microsoft

إذا كنت تستخدم إدارة نقاط النهاية من Microsoft الفرع الحالي، فراجع [إنشاء ملف تكوين الإلحاق](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>إيقاف تشغيل الأجهزة باستخدام System Center 2012 R2 Configuration Manager

1. احصل على حزمة الإلحاق من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>:
    1. في جزء التنقل، حدد **الإعدادات** \>**إلغاء إلحاق** **إدارة** \> أجهزة **نقاط** \> النهاية.  
    1. حدد Windows 10 أو Windows 11 كنظام التشغيل.
    1. في حقل **أسلوب النشر**، حدد **System Center Configuration Manager 2012/2012 R2/1511/1602**.
    1. حدد **حزمة التنزيل**، واحفظ ملف .zip.

2. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف يسمى *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. نشر الحزمة باتباع الخطوات الواردة في المقالة "[الحزم والبرامج" في مركز النظام 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)).

   اختر مجموعة أجهزة معرفة مسبقا لنشر الحزمة إليها.

> [!IMPORTANT]
> يؤدي إلغاء الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات كان قد تم الاحتفاظ بها لمدة تصل إلى 6 أشهر.

## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز

إذا كنت تستخدم إدارة نقاط النهاية من Microsoft الفرع الحالي، فاستخدم لوحة معلومات Defender لنقطة النهاية المضمنة في وحدة تحكم Configuration Manager. لمزيد من المعلومات، راجع [Defender لنقطة النهاية - Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

إذا كنت تستخدم System Center 2012 R2 Configuration Manager، تتكون المراقبة من جزأين:

1. تأكيد توزيع حزمة التكوين بشكل صحيح وتشغيلها (أو تشغيلها بنجاح) على الأجهزة في الشبكة.

2. التحقق من أن الأجهزة متوافقة مع خدمة Defender لنقطة النهاية (وهذا يضمن أن الجهاز يمكنه إكمال عملية الإلحاق ويمكنه الاستمرار في الإبلاغ عن البيانات إلى الخدمة).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>تأكيد نشر حزمة التكوين بشكل صحيح

1. في وحدة التحكم Configuration Manager، انقر فوق **"Monitoring**" في أسفل جزء التنقل.

2. حدد **"Overview** " ثم **"Deployments**".

3. حدد عند التوزيع باسم الحزمة.

4. راجع مؤشرات الحالة ضمن **إحصائيات الإكمال** **وحالة المحتوى**.

    إذا كانت هناك عمليات نشر فاشلة (أجهزة بها **حالات خطأ** أو **متطلبات غير مستوفية** أو **فاشلة**)، فقد تحتاج إلى استكشاف أخطاء الأجهزة وإصلاحها. لمزيد من المعلومات، راجع [استكشاف أخطاء Microsoft Defender لنقطة النهاية مشاكل الإلحاق وإصلاحها](troubleshoot-onboarding.md).

    :::image type="content" source="images/sccm-deployment.png" alt-text="تعرض Configuration Manager عملية نشر ناجحة بدون أخطاء" lightbox="images/sccm-deployment.png":::

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>تحقق من أن الأجهزة متوافقة مع خدمة Microsoft Defender لنقطة النهاية

يمكنك تعيين قاعدة توافق لعنصر التكوين في System Center 2012 R2 Configuration Manager لمراقبة التوزيع.

يجب أن تكون هذه القاعدة عنصر تكوين قاعدة توافق *غير معالجة* يراقب قيمة مفتاح التسجيل على الأجهزة المستهدفة.

مراقبة إدخال مفتاح التسجيل التالي:

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

لمزيد من المعلومات، راجع [مقدمة حول إعدادات التوافق في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows باستخدام نهج المجموعة](configure-endpoints-gp.md)
- [أجهزة Windows باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول](configure-endpoints-mdm.md)
- [أجهزة Windows باستخدام برنامج نصي محلي](configure-endpoints-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)
- [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](run-detection-test.md)
- [استكشاف أخطاء إلحاق Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-onboarding.md)
