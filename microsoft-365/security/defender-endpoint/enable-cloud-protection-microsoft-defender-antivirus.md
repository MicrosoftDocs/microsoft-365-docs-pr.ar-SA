---
title: تشغيل الحماية السحابية في برنامج الحماية من الفيروسات من Microsoft Defender
description: قم تشغيل الحماية السحابية للاستفادة من ميزات الحماية السريعة والمتقدمة.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، مكافحة البرامج الضارة، الأمان، السحابة، الحظر من النظرة الأولى
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.date: 02/03/2022
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 95abb603983ea16192d93b12757cde6fba026047
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63579554"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>تشغيل الحماية السحابية في برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

[توفر الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) حماية دقيقة وفي الوقت الحقيقي وذكية. يجب تمكين الحماية السحابية بشكل افتراضي؛ ومع ذلك، يمكنك تكوين الحماية السحابية لتتناسب مع احتياجات مؤسستك.

## <a name="methods-to-configure-cloud-protection"></a>أساليب لتكوين الحماية السحابية

يمكنك تشغيل برنامج الحماية من الفيروسات من Microsoft Defender السحابة أو إيقاف تشغيلها باستخدام إحدى الطرق العديدة:

- إدارة نقاط النهاية من Microsoft، الذي Microsoft Intune إدارة التكوين
- نهج المجموعة
- PowerShell cmdlets

يمكنك أيضا تشغيل الحماية السحابية أو إيقاف تشغيلها على نقاط النهاية الفردية باستخدام أمن Windows التطبيق. 

لمزيد من المعلومات حول متطلبات اتصال الشبكة المحددة لضمان إمكانية اتصال نقاط النهاية الخاصة بك لخدمة الحماية السحابية، راجع تكوين اتصالات [الشبكة والتحقق من صحتها](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> في Windows 10 Windows 11، لا فرق بين خيارات إعداد التقارير الأساسية وخيارات التقارير المتقدمة الموضحة في  هذه المقالة. هذا هو التمييز القديم، وسينتج عن اختيار أي من الإعدادين مستوى الحماية السحابي نفسه. لا يوجد اختلاف في نوع المعلومات التي تمت مشاركتها أو مقدارها. لمزيد من المعلومات حول ما نجمعه، راجع بيان [خصوصية Microsoft](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>استخدام Intune ل تشغيل الحماية السحابية

1. انتقل إلى إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ثم سجل الدخول.

2. في الجزء **الصفحة** الرئيسية، حدد **تكوين الجهاز > ملفات التعريف**.

3. حدد نوع **ملف تعريف قيود** الجهاز الذي تريد تكوينه. إذا كنت بحاجة إلى إنشاء **نوع ملف تعريف** جديد لقيود الجهاز، فشاهد تكوين إعدادات تقييد الجهاز [في](/intune/device-restrictions-configure) Microsoft Intune.

4. حدد **إعدادات** \> **تكوين الخصائص: تحرير برنامج الحماية من الفيروسات من Microsoft Defender**\>.

5. على مفتاح **تبديل الحماية التي تم تسليمها في** السحابة، حدد **تمكين**.

6. في **المنسدلة مطالبة المستخدمين قبل إرسال** العينة، حدد **إرسال كل البيانات تلقائيا**.

لمزيد من المعلومات حول ملفات تعريف أجهزة Intune، بما في ذلك كيفية إنشاء إعداداتها وتكوينها، راجع ما هي Microsoft Intune [ملفات تعريف الأجهزة؟](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>استخدام إدارة نقاط النهاية من Microsoft تشغيل الحماية السحابية

1. انتقل إلى إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ثم سجل الدخول.

2. اختر **الحماية من الفيروسات لنقطة** \> **النهاية**.

3. حدد ملف تعريف برنامج الحماية من الفيروسات. (إذا لم يكن لديك ملف تعريف بعد، أو إذا كنت تريد إنشاء ملف تعريف جديد، فشاهد تكوين إعدادات تقييد الجهاز [في](/intune/device-restrictions-configure) Microsoft Intune.

4. حدد **خصائص**. بعد ذلك، إلى بجانب **إعدادات التكوين،** اختر **تحرير**.

5. قم **بتوسيع الحماية السحابية**، ثم **في قائمة مستوى** الحماية التي تم تسليمها في السحابة، حدد أحد ما يلي:
   - **عال**: تطبيق مستوى عال من الكشف.
   - **مرتفع بالإضافة** إلى: يستخدم المستوى **العالي** ويطبق المزيد من تدابير الحماية (قد يؤثر على أداء العميل).
   - **عدم التسامح** إطلاقا: حظر جميع القابلة للتنفيذ غير المعروفة.

6. حدد **مراجعة + حفظ**، ثم اختر **حفظ**.

لمزيد من المعلومات حول Microsoft Endpoint Configuration Manager، راجع كيفية إنشاء سياسات الحماية من البرامج الضارة [ونشرها: خدمة الحماية من السحابة](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>استخدام "نهج المجموعة" ل تشغيل الحماية السحابية

1. على جهاز إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) المجموعة، وانقر بز الماوس الأيمن فوق كائن نهج المجموعة الذي تريد تكوينه وحدد **تحرير**.

2. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر**.

3. حدد **القوالب الإدارية**.

4. توسيع الشجرة Windows **مكوناتها** >  برنامج الحماية من الفيروسات من Microsoft Defender > **الخرائط**

    > [!NOTE]
    > تكون إعدادات الخرائط مساوية للحماية التي يتم تسليمها من السحابة.

5. انقر نقرا **مزدوجا فوق الانضمام إلى خرائط Microsoft**. تأكد من تشغيل الخيار ثم تعيينه إلى **الخرائط** الأساسية أو **الخرائط المتقدمة**. حدد **موافق**.

    يمكنك اختيار إرسال معلومات أساسية أو إضافية حول البرامج التي تم الكشف عنها:

    - الخرائط الأساسية: سترسل العضوية الأساسية معلومات أساسية إلى Microsoft حول البرامج الضارة والبرامج التي يحتمل أن تكون غير مرغوب فيها التي تم الكشف عنها على جهازك. تتضمن المعلومات من أين يأتي البرنامج (مثل عناوين URL والمسارات الجزئية)، والإجراءات التي تم اتخاذها لحل الخطر، وما إذا كانت الإجراءات قد نجحت أم لا.

    - الخرائط المتقدمة: بالإضافة إلى المعلومات الأساسية، سترسل العضوية المتقدمة معلومات مفصلة حول البرامج الضارة والبرامج التي يحتمل أن تكون غير مرغوب فيها، بما في ذلك المسار الكامل إلى البرنامج ومعلومات مفصلة حول كيفية تأثر البرنامج بجهازك.

6. انقر نقرا **مزدوجا فوق إرسال نماذج الملفات عندما يكون إجراء المزيد من التحليل مطلوبا**. تأكد من تعيين الخيار الأول إلى **تمكين** ومن تعيين الخيارات الأخرى على أي من الخيارين:

   - **إرسال عينات آمنة** (1)
   - **إرسال كل العينات** (3)

   >[!NOTE]
   > يعني **الخيار إرسال عينات آمنة** (1) أنه سيتم إرسال معظم العينات تلقائيا. وستبقى الملفات التي من المرجح أن تحتوي على معلومات شخصية مطالبة وستتطلب تأكيدا إضافيا.
   > سيخفض تعيين الخيار **المطالبة** دوما (0) حالة حماية الجهاز. يعني تعيينه إلى **عدم إرسال** (2) أن ميزة الحظر [](configure-block-at-first-sight-microsoft-defender-antivirus.md) عند النظرة الأولى من Microsoft Defender لنقطة النهاية لن تعمل.

7. حدد **موافق**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>استخدام PowerShell cmdlets ل تشغيل الحماية السحابية

يمكن ل cmdlets التالية تشغيل الحماية السحابية:

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع استخدام [PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender و [ برنامج الحماية من الفيروسات من Microsoft Defender cmdlets](/powershell/module/defender/). [نهج CSP - كما أن Defender](/windows/client-management/mdm/policy-csp-defender) لديه المزيد من المعلومات بشكل خاص على [-SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> يمكنك تعيين **-SubmitSamplesConsent** إلى `SendSafeSamples` (الإعداد الافتراضي أو الموصى به) `NeverSend`أو أو `AlwaysPrompt`. يعني `SendSafeSamples` الإعداد أنه سيتم إرسال معظم العينات تلقائيا. ستنتج عن الملفات التي من المرجح أن تحتوي على معلومات شخصية مطالبة للمتابعة وستتطلب تأكيدا.
> يخفض `NeverSend` `AlwaysPrompt` الإعدادان و مستوى حماية الجهاز. علاوة على ذلك، يعني `NeverSend` الإعداد أن ميزة [الحظر عند](configure-block-at-first-sight-microsoft-defender-antivirus.md) النظرة الأولى من Microsoft Defender لنقطة النهاية لن تعمل.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>استخدام Windows إدارة البيانات (WMI) ل تشغيل الحماية السحابية

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) للخصائص التالية:

```WMI
MAPSReporting
SubmitSamplesConsent
```

لمزيد من المعلومات حول المعلمات المسموح بها، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>تشغيل الحماية السحابية على العملاء الفرديين باستخدام أمن Windows

> [!NOTE]
> إذا تم تعيين تجاوز تكوين الإعداد المحلي للإبلاغ عن إعداد نهج مجموعة **MICROSOFT MAPS** إلى معطل، فإن إعداد الحماية المستند إلى السحابة في Windows الإعدادات سيكون رمادي اللون وغير متوفر. يجب نشر التغييرات التي يتم إدخالها من خلال "كائن نهج المجموعة" أولا على نقاط النهاية الفردية قبل أن يتم تحديث الإعداد في Windows الإعدادات.

1. افتح أمن Windows عن طريق تحديد أيقونة الدرع في شريط المهام، أو البحث في قائمة **البدء عن أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر)، ثم ضمن إدارة الإعدادات،  حدد **& الحماية من المخاطر**.

3. تأكد من **تبديل كل** من "الحماية  المستندة إلى السحابة" و"إرسال العينة التلقائية" إلى **تشغيل**.

   > [!NOTE]
   > إذا تم تكوين نموذج الإرسال التلقائي باستخدام "نهج المجموعة"، سيكون الإعداد رمادي اللون وغير متوفر.

## <a name="see-also"></a>راجع أيضًا

- [استخدام الحماية السحابية من Microsoft في برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- [كيفية إنشاء سياسات الحماية من البرامج الضارة ونشرها: خدمة الحماية من السحابة](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [استخدم PowerShell cmdlets لإدارة برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
