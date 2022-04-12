---
title: تشغيل حماية السحابة في برنامج الحماية من الفيروسات من Microsoft Defender
description: تشغيل حماية السحابة للاستفادة من ميزات الحماية السريعة والمتقدمة.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، ومكافحة البرامج الضارة، والأمان، والسحابة، والحظر من النظرة الأولى
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
ms.openlocfilehash: 95269837e4ad26b4928a2ff82df65a259c707290
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790647"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>تشغيل حماية السحابة في برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على:**

- برنامج الحماية من الفيروسات من Microsoft Defender
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**منصات**
- بالنسبة لنظام التشغيل

توفر [حماية السحابة في برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) حماية دقيقة وفي الوقت الحقيقي وذكية. يجب تمكين حماية السحابة بشكل افتراضي؛ ومع ذلك، يمكنك تكوين حماية السحابة لتناسب احتياجات مؤسستك.

## <a name="methods-to-configure-cloud-protection"></a>أساليب تكوين حماية السحابة

يمكنك تشغيل حماية السحابة برنامج الحماية من الفيروسات من Microsoft Defender أو إيقاف تشغيلها باستخدام إحدى الطرق المتعددة:

- إدارة نقاط النهاية من Microsoft، الذي يتضمن Microsoft Intune و Configuration Manager
- نهج المجموعة
- PowerShell cmdlets

يمكنك أيضا تشغيل حماية السحابة أو إيقاف تشغيلها على نقاط النهاية الفردية باستخدام تطبيق أمن Windows. 

لمزيد من المعلومات حول متطلبات اتصال الشبكة المحددة لضمان إمكانية اتصال نقاط النهاية بخدمة حماية السحابة، راجع [تكوين اتصالات الشبكة والتحقق من صحتها](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> في Windows 10 Windows 11، لا يوجد فرق بين خيارات إعداد التقارير **الأساسية** **والمتقدمة** الموضحة في هذه المقالة. هذا تمييز قديم واختيار أي من الإعدادين سيؤدي إلى نفس مستوى الحماية السحابية. لا يوجد فرق في نوع المعلومات التي تتم مشاركتها أو مقدارها. لمزيد من المعلومات حول ما نجمعه، راجع [بيان خصوصية Microsoft](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>استخدام Intune لتشغيل حماية السحابة

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) وسجل الدخول.

2. في الجزء **"الشريط الرئيسي** "، حدد **تكوين الجهاز > ملفات التعريف**.

3. حدد نوع ملف تعريف **قيود الجهاز** الذي تريد تكوينه. إذا كنت بحاجة إلى إنشاء نوع ملف تعريف جديد **لقيود الجهاز**، فراجع [تكوين إعدادات تقييد الجهاز في Microsoft Intune](/intune/device-restrictions-configure).

4. حدد **إعدادات تكوين الخصائص**  \>: تحرير \> **برنامج الحماية من الفيروسات من Microsoft Defender**.

5. في مفتاح الحماية المقدم من **السحابة** ، حدد **«Enable»**.

6. في **"مطالبة المستخدمين" قبل نموذج الإرسال** المنسدلة، حدد **"إرسال كافة البيانات تلقائيا**".

لمزيد من المعلومات حول ملفات تعريف أجهزة Intune، بما في ذلك كيفية إنشاء إعداداتها وتكوينها، راجع [ما هي ملفات تعريف الأجهزة Microsoft Intune؟](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>استخدام إدارة نقاط النهاية من Microsoft لتشغيل حماية السحابة

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) وسجل الدخول.

2. اختر برنامج **الحماية من الفيروسات** **لأمان** \> نقطة النهاية.

3. حدد ملف تعريف برنامج الحماية من الفيروسات. (إذا لم يكن لديك ملف تعريف بعد، أو إذا كنت تريد إنشاء ملف تعريف جديد، فراجع [تكوين إعدادات تقييد الجهاز في Microsoft Intune](/intune/device-restrictions-configure).

4. تحديد **الخصائص**. بعد ذلك، إلى جانب **إعدادات التكوين**، اختر **"تحرير**".

5. قم بتوسيع **حماية السحابة**، ثم في قائمة **مستوى الحماية المقدمة من السحابة** ، حدد أحد الإجراءات التالية:
   - **عال**: يطبق مستوى قويا من الكشف.
   - **علامة الجمع العالية**: يستخدم المستوى **العالي** ويطبق المزيد من مقاييس الحماية (قد يؤثر على أداء العميل).
   - **عدم التسامح:** يحظر كافة الملفات التنفيذية غير المعروفة.

6. حدد **Review + save**، ثم اختر **"حفظ**".

لمزيد من المعلومات حول تكوين Microsoft Endpoint Configuration Manager، راجع [كيفية إنشاء نهج مكافحة البرامج الضارة ونشرها: خدمة حماية السحابة](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>استخدام نهج المجموعة لتشغيل حماية السحابة

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وحدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر**.

3. حدد **القوالب الإدارية**.

4. توسيع الشجرة إلى **مكونات** >  Windows **برنامج الحماية من الفيروسات من Microsoft Defender > MAPS**

    > [!NOTE]
    > إعدادات MAPS تساوي الحماية المقدمة من السحابة.

5. انقر نقرا مزدوجا فوق **الانضمام إلى Microsoft MAPS**. تأكد من تشغيل الخيار وتعيينه إلى **"الخرائط الأساسية"** أو **"الخرائط المتقدمة**". حدد **موافق**.

    يمكنك اختيار إرسال معلومات أساسية أو إضافية حول البرامج المكتشفة:

    - الخرائط الأساسية: سترسل العضوية الأساسية معلومات أساسية إلى Microsoft حول البرامج الضارة والبرامج غير المرغوب فيها التي تم اكتشافها على جهازك. تتضمن المعلومات المكان الذي جاء منه البرنامج (مثل عناوين URL والمسارات الجزئية)، والإجراءات التي تم اتخاذها لحل التهديد، وما إذا كانت الإجراءات ناجحة.

    - الخرائط المتقدمة: بالإضافة إلى المعلومات الأساسية، سترسل العضوية المتقدمة معلومات مفصلة حول البرامج الضارة والبرامج التي يحتمل أن تكون غير مرغوب فيها، بما في ذلك المسار الكامل للبرنامج، ومعلومات مفصلة حول كيفية تأثير البرنامج على جهازك.

6. انقر نقرا مزدوجا فوق **إرسال نماذج الملفات عند الحاجة إلى مزيد من التحليل**. تأكد من تعيين الخيار الأول إلى **"ممكن"** ومن تعيين الخيارات الأخرى إلى أي مما يلي:

   - **إرسال عينات آمنة** (1)
   - **إرسال كافة العينات** (3)

   >[!NOTE]
   > يعني خيار **إرسال عينات آمنة** (1) أنه سيتم إرسال معظم العينات تلقائيا. ستظل الملفات التي من المحتمل أن تحتوي على معلومات شخصية مطالبة وتتطلب تأكيدا إضافيا.
   > سيؤدي تعيين الخيار إلى **المطالبة الدائمة** (0) إلى خفض حالة حماية الجهاز. يعني تعيينه إلى **"عدم الإرسال أبدا**" (2) أن ميزة ["حظر عند النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md)" Microsoft Defender لنقطة النهاية لن تعمل.

7. حدد **موافق**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>استخدام PowerShell cmdlets لتشغيل حماية السحابة

يمكن ل cmdlets التالية تشغيل حماية السحابة:

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع [استخدام PowerShell cmdlets لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender و](use-powershell-cmdlets-microsoft-defender-antivirus.md) [ برنامج الحماية من الفيروسات من Microsoft Defender cmdlets](/powershell/module/defender/). [النهج CSP - كما أن Defender](/windows/client-management/mdm/policy-csp-defender) لديه المزيد من المعلومات على وجه التحديد على [-SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> يمكنك تعيين **-SubmitSamplesConsent** إلى `SendSafeSamples` (الإعداد الافتراضي أو الموصى به) `NeverSend`أو أو `AlwaysPrompt`. يعني `SendSafeSamples` الإعداد أنه سيتم إرسال معظم العينات تلقائيا. ستؤدي الملفات التي من المحتمل أن تحتوي على معلومات شخصية إلى مطالبة بالمتابعة وستتطلب تأكيدا.
> `AlwaysPrompt` وتخفض `NeverSend` الإعدادات مستوى الحماية للجهاز. علاوة على ذلك، `NeverSend` يعني الإعداد أن ميزة ["حظر عند النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md)" Microsoft Defender لنقطة النهاية لن تعمل.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>استخدام Windows Management Instruction (WMI) لتشغيل حماية السحابة

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) للخصائص التالية:

```WMI
MAPSReporting
SubmitSamplesConsent
```

لمزيد من المعلومات حول المعلمات المسموح بها، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>تشغيل حماية السحابة على العملاء الفرديين باستخدام تطبيق أمن Windows

> [!NOTE]
> إذا تم تعيين الإعداد **"تكوين الإعداد المحلي" للإبلاغ عن إعداد نهج المجموعة Microsoft MAPS** إلى **"معطل**"، فسيكون إعداد **الحماية المستند إلى السحابة** في Windows الإعدادات رمادي اللون وغير متوفر. يجب أولا نشر التغييرات التي تم إجراؤها من خلال كائن نهج المجموعة إلى نقاط النهاية الفردية قبل تحديث الإعداد في Windows الإعدادات.

1. افتح تطبيق أمن Windows عن طريق تحديد أيقونة الدرع في شريط المهام، أو عن طريق البحث في قائمة البدء عن **أمن Windows**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر)، ثم ضمن **"إدارة الإعدادات** "، حدد **إعدادات الحماية من الفيروسات & التهديدات**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="إعدادات الحماية من التهديدات & الفيروسات" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. تأكد من تبديل **الحماية المستندة إلى السحابة** **وإرسال العينة التلقائي** إلى **تشغيل**.

   > [!NOTE]
   > إذا تم تكوين الإرسال التلقائي للعينة مع نهج المجموعة فسيكون الإعداد رمادي اللون وغير متوفر.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [استخدام الحماية السحابية من Microsoft في برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- [كيفية إنشاء نهج مكافحة البرامج الضارة ونشرها: خدمة حماية السحابة](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [استخدم PowerShell cmdlets لإدارة برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
