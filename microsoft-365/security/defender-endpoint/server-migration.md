---
title: سيناريوهات ترحيل الخادم للإصدار الجديد من Microsoft Defender لنقطة النهاية
description: اقرأ هذه المقالة للحصول على نظرة عامة حول كيفية ترحيل الخوادم من الحل السابق المستند إلى MMA إلى حزمة الحل الموحدة الحالية ل Defender for Endpoint.
keywords: ترحيل الخادم، الخادم، 2012r2، 2016، ترحيل الخادم، إدارة الأجهزة، تكوين Microsoft Defender للخوادم Endpoint، تهيئة Microsoft Defender للخوادم Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7fd4ca4931c060c0eb7092f74ed708c0b8d69738
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63570846"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>سيناريوهات ترحيل الخادم من حل Microsoft Defender لنقطة النهاية السابق المستند إلى MMA

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- Windows Server 2012 R2
- Windows Server 2016‏
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> تأكد دائما برنامج الحماية من الفيروسات من Microsoft Defender التحديث الكامل على Windows Server 2016 قبل المتابعة مع التثبيت أو الترقية. لتلقي تحسينات المنتج العادية وإصلاحات لمكون استشعار الكشف التلقائي والاستجابة على النقط النهائية، تأكد من Windows [تحديث KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) أو الموافقة عليه. بالإضافة إلى ذلك، لإبقاء مكونات الحماية محدثة، [الرجاء الرجوع إلى إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

تنطبق هذه الإرشادات على الحل الموحد الجديد وحزمة المثبت من Microsoft Defender ل Endpoint ل Windows Server 2012 R2 وs Windows Server 2016. تحتوي هذه المقالة على إرشادات عالية المستوى لمختلف سيناريوهات الترحيل المحتملة من السابق إلى الحل الحالي. تم إعداد هذه الخطوات عالية المستوى كمرشادات لكي يتم ضبطها مع أدوات النشر والتكوين المتوفرة في بيئتك.

> [!NOTE]
> إن ترقيات نظام التشغيل مع تثبيت Microsoft Defender ل Endpoint غير معتمدة. الرجاء إيقاف التشغيل ثم إلغاء التثبيت قبل المتابعة مع الترقية.

> [!NOTE]
> أثناء المعاينة، Microsoft Endpoint Configuration Manager التنفيذ التلقائي والتكامل الكامل لتنفيذ ترقية تلقائية في إصدار لاحق من MECM. من إصدار 2107 الذي تم فيه أحدث مجموعة من مستجدات hotfix، يمكنك استخدام عقدة Endpoint Protection لتكوينها بالإضافة إلى نهج المجموعة أو PowerShell أو إدارة نقاط النهاية من Microsoft المستأجر أو التكوين المحلي. بالإضافة إلى ذلك، يمكنك الاستفادة من الوظائف الموجودة في Microsoft Endpoint Configuration Manager لأتمتة خطوات الترقية اليدوية؛ الأساليب الموضحة أدناه.


## <a name="installer-script"></a>البرنامج النصي "المثبت"

لتسهيل الترقيات عندما Microsoft Endpoint Configuration Manager أو Microsoft Defender for Cloud غير متوفر أو غير متوفر بعد لتنفيذ الترقية، يمكنك استخدام البرنامج النصي [للترقية هذا](https://github.com/microsoft/mdefordownlevelserver). يمكن أن يساعد ذلك على أتمتة الخطوات المطلوبة التالية:

1. إزالة مساحة عمل OMS ل Microsoft Defender لنقطة النهاية (اختياري).
2. إزالة System Center Endpoint Protection إذا كان مثبتا.
3. قم بتنزيل (Windows Server 2012 R2) [وتثبيتها](configure-server-endpoints.md#prerequisites) إذا لزم الأمر.
4. تثبيت Microsoft Defender لنقطة النهاية.
5. قم بتطبيق البرنامج النصي ل **الإستخدام مع نهج المجموعة** الذي تم تنزيله [من Microsoft 365 Defender](https://security.microsoft.com).

لاستخدام البرنامج النصي، قم بتنزيلها إلى دليل تثبيت حيث قمت أيضا بوضع حزم التثبيت والتثبيت (راجع [تكوين نقاط نهاية الخادم](configure-server-endpoints.md).

مثال: .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd"

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>Microsoft Endpoint Configuration Manager الترحيل 

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-including-system-center-endpoint-protection-scep-and-are-running-the-microsoft-monitoring-agent-mma-based-sensor-you-want-to-upgrade-to-the-microsoft-defender-for-endpoint-unified-solution-preview"></a>أنت تستخدم حاليا Microsoft Endpoint Configuration Manager لإدارة الخوادم، بما في ذلك System Center Endpoint Protection (SCEP) وتشغيل المستشعر المستند إلى Microsoft Monitoring Agent (MMA). تريد الترقية إلى معاينة حلول Microsoft Defender ل Endpoint **الموحدة**.

>[!NOTE]
>ستحتاج إلى Microsoft Endpoint Configuration Manager، الإصدار 2107.


خطوات الترحيل: 

1. قم بتحديث الجهاز بالكامل بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016).
2. إنشاء مجموعة جديدة مع قواعد العضوية لتضمين الأجهزة التي سيتم ترحيلها.
3. [إنشاء تطبيق لتنفيذ](/mem/configmgr/apps/deploy-use/create-applications) المهام التالية: 
   1. إزالة تكوين مساحة عمل MMA ل Microsoft Defender لنقطة النهاية. راجع [إزالة مساحة عمل باستخدام PowerShell](/azure/azure-monitor/agents/agent-manage). هذه الخطوة اختيارية؛ سيتوقف الكشف التلقائي والاستجابة على النقط النهائية السابق عن التشغيل بعد أن يصبح المستشعر الجديد نشطا (لاحظ أن هذا قد يستغرق عدة ساعات).
   2. إلغاء تثبيت SCEP.
   3. ثبت المتطلبات [الأساسية عند](configure-server-endpoints.md#prerequisites) الاقتضاء.
   4. تثبيت Microsoft Defender لنقطة النهاية (راجع [تكوين نقاط نهاية الخادم](configure-server-endpoints.md).
   5. قم بتطبيق البرنامج النصي ل **الإستخدام مع نهج المجموعة** الذي تم تنزيله [من Microsoft 365 Defender](https://security.microsoft.com). 

   > [!TIP]
   > يمكنك استخدام [البرنامج النصي للمثبت](server-migration.md#installer-script) كجزء من التطبيق لأتمتة الخطوات المذكورة أعلاه.
4. نشر التطبيق إلى المجموعة الجديدة.
5. إنشاء و/أو تعيين (Endpoint Protection) إلى المجموعة.
6. تطبيق التحديثات.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>أنت تستخدم حاليا Microsoft Endpoint Configuration Manager لإدارة خوادمك، وتشغيل حل برنامج الحماية من الفيروسات من Microsoft ومستشعر مستند إلى MMA. تريد الترقية إلى Microsoft Defender الجديد لنقطة النهاية.

خطوات الترحيل:

1. قم بتحديث الجهاز بالكامل بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016).
2. إنشاء مجموعة جديدة مع قواعد العضوية لتضمين الأجهزة التي سيتم ترحيلها. 
3. تأكد من أن إدارة برنامج الحماية من الفيروسات من جهة خارجية لم تعد تدفع برنامج الحماية من الفيروسات إلى هذه الأجهزة.*
4. قم بكاتب النهج في عقدة Endpoint Protection MECM واستهداف المجموعة التي تم إنشاؤها حديثا.*
5. إنشاء تطبيق لتنفيذ المهام التالية:
   1. إزالة تكوين مساحة عمل MMA ل Microsoft Defender لنقطة النهاية. راجع [إزالة مساحة عمل باستخدام PowerShell](/azure/azure-monitor/agents/agent-manage). هذه الخطوة اختيارية؛ سيتوقف الكشف التلقائي والاستجابة على النقط النهائية السابق عن التشغيل بعد أن يصبح المستشعر الجديد نشطا (لاحظ أن هذا قد يستغرق عدة ساعات).
   2. ثبت المتطلبات [الأساسية عند](configure-server-endpoints.md#prerequisites) الاقتضاء.
   3. قم بتثبيت حزمة Microsoft Defender ل Endpoint Windows Server 2012 R2 و2016 وتمكين **الوضع السلبي**. راجع [تثبيت برنامج الحماية من الفيروسات من Microsoft Defender باستخدام سطر الأوامر](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. قم بتطبيق البرنامج النصي ل **الإستخدام مع نهج المجموعة** الذي تم تنزيله [من Microsoft 365 Defender](https://security.microsoft.com).
6. تطبيق التحديثات.
7. قم بإزالة برنامج الحماية من الفيروسات غير التابع ل Microsoft إما باستخدام وحدة التحكم في مكافحة الفيروسات غير الخاصة ب Microsoft أو باستخدام Microsoft Endpoint Configuration Manager حسب الاقتضاء. تأكد من إزالة تكوين الوضع السلبي.*

> [!TIP]
> يمكنك استخدام [البرنامج النصي المثبت](server-migration.md#installer script) كجزء من التطبيق لأتمتة الخطوات المذكورة أعلاه. لتمكين الوضع السلبي، قم بتطبيق العلامة -Passive. على سبيل المثال، .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive

*تنطبق هذه الخطوات فقط إذا كنت تنوي استبدال حل برنامج الحماية من الفيروسات غير التابع ل Microsoft. راجع [أفضل معا: برنامج الحماية من الفيروسات من Microsoft Defender و Microsoft Defender ل Endpoint](why-use-microsoft-defender-antivirus.md).

لنقل جهاز خارج الوضع السلبي، قم بتعيين المفتاح التالي إلى 0:

المسار: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD القيمة: 0


## <a name="other-migration-scenarios"></a>سيناريوهات الترحيل الأخرى

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>لديك خادم تم استخدامه باستخدام Microsoft Defender لنقطة النهاية المستندة إلى MMA. تم تثبيت SCEP (Windows Server 2012 R2) أو برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016). لا يتم إدارة **هذا الجهاز** من خلال Microsoft Defender for Cloud أو إدارة نقاط النهاية من Microsoft أو Microsoft Endpoint Configuration Manager.

1. قم بتحديث الجهاز بالكامل بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016).
2. إزالة تكوين مساحة عمل MMA ل Microsoft Defender لنقطة النهاية. راجع [إزالة مساحة عمل باستخدام PowerShell](/azure/azure-monitor/agents/agent-manage).
3. إلغاء تثبيت System Center Endpoint Protection (Windows Server 2012 R2).
4. ثبت المتطلبات [الأساسية عند](configure-server-endpoints.md#prerequisites) الاقتضاء. 
5. تثبيت Microsoft Defender لنقطة النهاية (راجع [تكوين نقاط نهاية الخادم](configure-server-endpoints.md).)
6. قم بتطبيق البرنامج النصي ل **الإستخدام مع نهج المجموعة** الذي تم تنزيله [من Microsoft 365 Defender](https://security.microsoft.com). 
7. تطبيق التحديثات.
8. إنشاء نهج وتطبيقها باستخدام "نهج المجموعة" أو PowerShell أو حل إدارة جهة خارجية.

> [!TIP]
> يمكنك استخدام البرنامج النصي للمثبت لأتمتة الخطوات المذكورة أعلاه.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>لديك خادم تريد تثبيت Microsoft Defender لنقطة النهاية عليه. فهو يوفر حماية لنقطة نهاية غير Microsoft أو الكشف عن تهديدات نقاط النهاية والرد عليها مثبتا. لا تنوي استخدام Microsoft Endpoint Configuration Manager Microsoft Defender for Cloud. يمكنك استخدام آلية النشر الخاصة بك. 

1. قم بتحديث الجهاز بالكامل بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016).
2. قم بتثبيت حزمة Microsoft Defender ل Endpoint Windows Server 2012 R2 & 2016 وتمكين الوضع **السلبي**. راجع [تثبيت برنامج الحماية من الفيروسات من Microsoft Defender باستخدام سطر الأوامر](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. قم بتطبيق البرنامج النصي لتهيئة، المناسب لبيئة عملك، الذي تم تنزيله من [Microsoft 365 Defender](https://security.microsoft.com). 
4. إزالة حل نقطة نهاية غير Microsoft أو الكشف عن تهديدات نقاط النهاية والرد عليها، وإزالة الوضع السلبي.*
5. تطبيق التحديثات.
6. إنشاء نهج وتطبيقها باستخدام "نهج المجموعة" أو PowerShell أو حل إدارة جهة خارجية.

> [!TIP]
> يمكنك استخدام البرنامج [النصي للمثبت](server-migration.md#installer-script) للمساعدة على أتمتة الخطوات من 1 إلى 4. لتمكين الوضع السلبي، قم بتطبيق العلامة -Passive التي ستضمن وصول Defender Antivirus إلى الوضع السلبي قبل التكامل ولا تتداخل مع حل مكافحة البرامج الضارة غير Microsoft. بعد ذلك، للتأكد من أن برنامج الحماية من الفيروسات ل Defender يظل في الوضع السلبي بعد التكحيل لدعم قدرات الكشف التلقائي والاستجابة على النقط النهائية مثل الكشف التلقائي والاستجابة على النقط النهائية Block، تأكد من تعيين مفتاح التسجيل "ForceDefenderPassiveMode". مثال: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*تنطبق هذه الخطوة فقط إذا كنت تنوي استبدال حل برنامج الحماية من الفيروسات غير التابع ل Microsoft. نوصي باستخدام برنامج الحماية من الفيروسات من Microsoft Defender، المضمنة في Microsoft Defender لنقطة النهاية، لتوفير مجموعة كاملة من الإمكانات. راجع [أفضل معا: برنامج الحماية من الفيروسات من Microsoft Defender و Microsoft Defender ل Endpoint](why-use-microsoft-defender-antivirus.md).

لنقل جهاز خارج الوضع السلبي، قم بتعيين المفتاح التالي إلى 0:

المسار: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD القيمة: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>سيناريوهات Microsoft Defender for Cloud

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>أنت تستخدم Microsoft Defender for Cloud. تم تثبيت وكيل مراقبة Microsoft (MMA) و/أو Microsoft Antimalware ل Azure (SCEP) وتريد الترقية.
إذا كنت تستخدم Microsoft Defender for Cloud، يمكنك الاستفادة من عملية الترقية التلقائية. راجع حماية نقاط النهاية باستخدام الحل المتكامل ل [Defender for Cloud الكشف التلقائي والاستجابة على النقط النهائية: Microsoft Defender ل Endpoint](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>تكوين نهج المجموعة
للحصول على التكوين باستخدام "نهج المجموعة"، تأكد من استخدام أحدث ملفات ADMX في متجرك المركزي للوصول إلى خيارات نهج نقاط النهاية الصحيحة ل Defender for Endpoint. الرجاء الرجوع [إلى كيفية إنشاء](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) المتجر المركزي للقالب الإدارية لنهة المجموعة وإدارته في Windows وتنزيل أحدث الملفات لاستخدامها **مع** Windows 10.
