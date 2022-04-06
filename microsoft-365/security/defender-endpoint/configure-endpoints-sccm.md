---
title: أجهزة Windows التي تستخدم Configuration Manager
description: استخدم Configuration Manager لنشر حزمة التكوين على الأجهزة بحيث يتم إعدادها في خدمة Defender for Endpoint.
keywords: الأجهزة المجهزة باستخدام sccm وإدارة الأجهزة وتكوين Microsoft Defender لنقطة النهاية الأجهزة
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
ms.openlocfilehash: d67a4ca067f16d74b15a1d7ece5c47d563f1a941
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471887"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>أجهزة Windows التي تستخدم Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager الفرع الحالي
- System Center 2012 R2 Configuration Manager

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)


يمكنك استخدام Configuration Manager لتكوين نقاط النهاية Microsoft Defender لنقطة النهاية الخدمة. 

هناك العديد من الخيارات التي يمكنك استخدامها للأجهزة المجهزة باستخدام Configuration Manager:
- [الأجهزة المجهزة باستخدام System Center Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [إرفاق المستأجر](/mem/configmgr/tenant-attach/)



بالنسبة Windows Server 2012 R2 Windows Server 2016 - بعد إكمال خطوات التهيئة، ستحتاج إلى تكوين System Center Endpoint Protection [العملاء وتحديثهم](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
> لا يدعم Defender لنقطة النهاية التكوين أثناء مرحلة تجربة "خارج الصندوق" [(OOBE](https://answers.microsoft.com/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) ). تأكد من أن المستخدمين يكملون OOBE بعد Windows التثبيت أو الترقية.
>
> لاحظ أنه من الممكن إنشاء قاعدة الكشف على تطبيق Configuration Manager للتحقق بشكل مستمر مما إذا تم تهيئة جهاز. التطبيق هو نوع مختلف من الكائنات عن الحزمة والبرنامج.
> إذا لم يتم بعد اكمال الجهاز (بسبب اكتمال OOBE المعلق أو أي سبب آخر)، سي محاولة Configuration Manager ل متن الجهاز حتى تكتشف القاعدة تغيير الحالة.
>
> يمكن تنفيذ هذا السلوك عن طريق إنشاء قاعدة الكشف للتحقق مما إذا كانت قيمة السجل "OnboardingState" (من النوع REG_DWORD) = 1.
> تقع قيمة التسجيل هذه ضمن "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
لمزيد من المعلومات، راجع [تكوين أساليب الكشف في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>تكوين إعدادات المجموعة العينة

لكل جهاز، يمكنك تعيين قيمة تكوين لتحدد ما إذا كان يمكن تجميع عينات من الجهاز عند تقديم طلب عبر Microsoft 365 Defender لإرسال ملف لتحليله بعمق.

> [!NOTE]
> تتم إعدادات التكوين هذه عادة من خلال Configuration Manager.

يمكنك تعيين قاعدة توافق لعناصر التكوين Configuration Manager لتغيير إعداد المشاركة العينة على جهاز.

يجب أن تكون هذه *القاعدة عنصرا لتكوين* قاعدة التوافق التي تقوم بتعيين قيمة مفتاح التسجيل على الأجهزة المستهدفة للتأكد من أنها شكوى.

يتم تعيين التكوين من خلال إدخال مفتاح التسجيل التالي:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

حيث نوع المفتاح هو D-WORD. القيم المحتملة هي:

- 0: لا يسمح بالمشاركة العينة من هذا الجهاز
- 1: السماح بمشاركة كل أنواع الملفات من هذا الجهاز

القيمة الافتراضية في حالة عدم وجود مفتاح التسجيل هي 1.

لمزيد من المعلومات حول "مركز Configuration Manager"، راجع مقدمة حول [إعدادات التوافق في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>إعدادات التكوين المستحسنة الأخرى

بعد تهيئة الأجهزة للخدمة، من المهم الاستفادة من إمكانات الحماية من المخاطر المضمنة من خلال تمكينها بإعدادات التكوين الموصى بها التالية.

### <a name="device-collection-configuration"></a>تكوين مجموعة الأجهزة

إذا كنت تستخدم Configuration Manager Endpoint أو الإصدار 2002 أو الإصدارات الأحدث، يمكنك أن تختار توزيع التوزيع لتضمين خوادم أو عملاء من المستوى الأسفل.

### <a name="next-generation-protection-configuration"></a>تكوين حماية الجيل التالي

يوصى بإعدادات التكوين التالية:

#### <a name="scan"></a>المسح الضوئي

- فحص أجهزة التخزين القابلة للإزالة مثل محركات أقراص USB: نعم

#### <a name="real-time-protection"></a>الحماية في الوقت الحقيقي

- تمكين المراقبة السلوكية: نعم
- تمكين الحماية من التطبيقات التي يحتمل أن تكون غير مرغوب فيها عند التنزيل وقبل التثبيت: نعم

#### <a name="cloud-protection-service"></a>خدمة الحماية السحابية

- نوع عضوية خدمة الحماية السحابية: العضوية المتقدمة

#### <a name="attack-surface-reduction"></a>الحد من سطح الهجوم

تكوين كافة القواعد المتوفرة للتدقيق.

> [!NOTE]
> قد يؤدي حظر هذه الأنشطة إلى مقاطعة عمليات الأعمال المشروعة. أفضل طريقة هي تعيين كل شيء للتدقيق، وتحديد الإعدادات الآمنة التي يمكن تشغيلها، ثم تمكين هذه الإعدادات على نقاط النهاية التي لا تملك عمليات الكشف الإيجابي الخاطئة.

#### <a name="network-protection"></a>حماية الشبكة

قبل تمكين حماية الشبكة في وضع التدقيق أو الحظر، تأكد من تثبيت تحديث النظام الأساسي للحماية من البرامج الضارة، الذي يمكن الحصول عليه من [صفحة الدعم](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

#### <a name="controlled-folder-access"></a>الوصول إلى المجلدات الخاضعة للتحكم

تمكين الميزة في وضع التدقيق لمدة 30 يوما على الأقل. بعد هذه الفترة، راجع الاكتشافات وأنشئ قائمة التطبيقات المسموح لها الكتابة إلى الدلائل المحمية.

لمزيد من المعلومات، راجع [تقييم الوصول المتحكم به للمجلدات](evaluate-controlled-folder-access.md).

## <a name="run-a-detection-test-to-verify-onboarding"></a>تشغيل اختبار الكشف للتحقق من ال

بعد تشغيل الجهاز، يمكنك أن تختار تشغيل اختبار الكشف للتحقق من أن الجهاز مواد بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية جديد](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>أجهزة إيقاف التشغيل التي تستخدم Configuration Manager

لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>أجهزة إيقاف التشغيل التي تستخدم إدارة نقاط النهاية من Microsoft الحالي

إذا كنت تستخدم إدارة نقاط النهاية من Microsoft الحالي، فشاهد [إنشاء ملف تكوين خارج](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file) الإعداد.

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>أجهزة إيقاف التشغيل التي تستخدم System Center 2012 R2 Configuration Manager

1. احصل على حزمة إيقاف التشغيل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">من مدخل Microsoft 365 Defender:</a>
    1. في جزء التنقل **، حدد الإعدادات** \> **إيقاف** \>  \> تشغيل إدارة أجهزة **نقاط النهاية**.  
    1. حدد Windows 10 أو Windows 11 نظام التشغيل.
    1. في **الحقل أسلوب** النشر، حدد **مركز Configuration Manager 2012/2012 R2/1511/1602**.
    1. حدد **تنزيل الحزمة**، واحفظ الملف .zip.

2. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف *يسمى WindowsDefenderATPOffboardingScript_valid_until_YYYY MM-DD.cmd*.

3. نشر الحزمة باتباع الخطوات في مقالة الحزم والبرامج [في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)).

   اختر مجموعة أجهزة محددة مسبقا لنشر الحزمة فيها.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.

## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز

إذا كنت تستخدم إدارة نقاط النهاية من Microsoft الحالي، فاستخدم لوحة معلومات Defender for Endpoint المضمنة في وحدة Configuration Manager التحكم. لمزيد من المعلومات، راجع [Defender for Endpoint - جهاز العرض](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

إذا كنت تستخدم System Center 2012 R2 Configuration Manager، فإن المراقبة تتكون من جزأين:

1. تأكيد نشر حزمة التكوين بشكل صحيح وتشغيلها (أو تشغيلها بنجاح) على الأجهزة في شبكتك.

2. التحقق من أن الأجهزة متوافقة مع خدمة Defender for Endpoint (يضمن ذلك أن الجهاز يمكنه إكمال عملية التكوين ويمكنه الاستمرار في الإبلاغ عن البيانات إلى الخدمة).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>تأكيد نشر حزمة التكوين بشكل صحيح

1. في وحدة Configuration Manager، **انقر فوق مراقبة** في أسفل جزء التنقل.

2. حدد **نظرة عامة** ثم **عمليات النشر**.

3. حدد على النشر باستخدام اسم الحزمة.

4. راجع مؤشرات الحالة ضمن **إحصائيات الإكمال** حالة **المحتوى**.

    في حالة فشل عمليات النشر (الأجهزة التي بها أخطاء أو متطلبات **لم** يتم تحقيقها أو فشل الحالات)، فقد تحتاج إلى استكشاف أخطاء الأجهزة وإصلاحها. لمزيد من المعلومات، راجع استكشاف مشاكل Microsoft Defender لنقطة النهاية [وإصلاحها](troubleshoot-onboarding.md).

    :::image type="content" source="images/sccm-deployment.png" alt-text="تظهر Configuration Manager نشر ناجح بدون أخطاء" lightbox="images/sccm-deployment.png":::

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>التحقق من أن الأجهزة متوافقة مع خدمة Microsoft Defender لنقطة النهاية

يمكنك تعيين قاعدة توافق لعناصر التكوين في System Center 2012 R2 Configuration Manager لمراقبة النشر.

يجب أن تكون هذه القاعدة *عنصر* تكوين قاعدة توافق غير معالجة يراقب قيمة مفتاح التسجيل على الأجهزة المستهدفة.

راقب إدخال مفتاح التسجيل التالي:

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
- [تشغيل اختبار الكشف على جهاز تم Microsoft Defender لنقطة النهاية جديد](run-detection-test.md)
- [استكشاف مشاكل Microsoft Defender لنقطة النهاية في الحافظة وإصلاحها](troubleshoot-onboarding.md)
