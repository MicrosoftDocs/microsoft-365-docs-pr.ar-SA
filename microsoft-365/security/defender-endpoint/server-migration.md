---
title: سيناريوهات ترحيل الخادم للإصدار الجديد من Microsoft Defender لنقطة النهاية
description: اقرأ هذه المقالة للحصول على نظرة عامة حول كيفية ترحيل الخوادم من الحل السابق المستند إلى MMA إلى حزمة الحلول الموحدة الحالية ل Defender لنقطة النهاية.
keywords: ترحيل الخادم، الخادم، 2012r2، 2016، ترحيل الخادم، إدارة الأجهزة، تكوين خوادم Microsoft Defender لنقطة النهاية، إلحاق خوادم Microsoft Defender لنقطة النهاية
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
ms.openlocfilehash: 461a3e4ebb97d809bf61c11591f40448ef97f8cb
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490520"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>سيناريوهات ترحيل الخادم من الحل Microsoft Defender لنقطة النهاية السابق المستند إلى MMA

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- Windows Server 2012 R2
- Windows Server 2016‏
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> تأكد دائما من تحديث نظام التشغيل وMicrosoft Defender Antivirus على Windows Server 2016 بشكل كامل قبل متابعة التثبيت أو الترقية. لتلقي تحسينات وإصلاحات منتظمة للمنتج لمكون EDR Sensor، تأكد من تطبيق أو الموافقة على Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) بعد التثبيت. بالإضافة إلى ذلك، للحفاظ على تحديث مكونات الحماية، يرجى الرجوع إلى [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

تنطبق هذه الإرشادات على حزمة الحل الموحد الجديد والمثبت (MSI) من Microsoft Defender لنقطة النهاية ل Windows Server 2012 R2 وWindows Server 2016. تحتوي هذه المقالة على إرشادات عالية المستوى لمختلف سيناريوهات الترحيل المحتملة من الحل السابق إلى الحل الحالي. تهدف هذه الخطوات عالية المستوى إلى تعديلها وفقا لأدوات التوزيع والتكوين المتوفرة في بيئتك. 

**إذا كنت تستخدم Microsoft Defender for Cloud لتنفيذ النشر، يمكنك أتمتة التثبيت والترقية. راجع [يتكامل Defender for Servers Plan 2 الآن مع الحل الموحد MDE] (https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/defender-for-servers-plan-2-now-integrates-with-mde-unified/ba-p/3527534)**

> [!NOTE]
> ترقيات نظام التشغيل مع تثبيت Microsoft Defender لنقطة النهاية غير معتمدة. يرجى إلغاء التثبيت ثم إلغاء التثبيت قبل متابعة الترقية.

> [!NOTE]
> ستتوفر نقطة نهاية Microsoft الكاملة Configuration Manager الأتمتة والتكامل لإجراء ترقية تلقائية في إصدار لاحق من MECM. من إصدار 2107 مع أحدث مجموعة إصلاح عاجل، يمكنك استخدام عقدة Endpoint Protection للتكوين بالإضافة إلى نهج المجموعة أو PowerShell أو إرفاق مستأجر Microsoft إدارة نقاط النهاية أو التكوين المحلي. بالإضافة إلى ذلك، يمكنك الاستفادة من الوظائف الموجودة في نقطة نهاية Microsoft Configuration Manager لأتمتة خطوات الترقية اليدوية؛ الأساليب الموضحة أدناه.


## <a name="installer-script"></a>البرنامج النصي للمثبت

لتسهيل الترقيات عندما لا تكون نقطة نهاية Microsoft Configuration Manager متوفرة أو محدثة بعد لتنفيذ الترقية التلقائية، يمكنك استخدام [البرنامج النصي للترقية](https://github.com/microsoft/mdefordownlevelserver) هذا. يمكن أن يساعد في أتمتة الخطوات المطلوبة التالية:

1. إزالة مساحة عمل OMS Microsoft Defender لنقطة النهاية (اختياري).
2. إزالة عميل System Center Endpoint Protection (SCEP) إذا تم تثبيته.
3. تنزيل [المتطلبات الأساسية](configure-server-endpoints.md#prerequisites) (Windows Server 2012 R2) وتثبيتها إذا لزم الأمر.
4. تثبيت Microsoft Defender لنقطة النهاية.
5. تطبيق البرنامج النصي **للإلحاق للاستخدام مع نهج المجموعة** التي تم تنزيلها من [Microsoft 365 Defender](https://security.microsoft.com).

لاستخدام البرنامج النصي، قم بتنزيله إلى دليل تثبيت حيث قمت أيضا بوضع حزم التثبيت والإلحاق (راجع [تكوين نقاط نهاية الخادم](configure-server-endpoints.md).

مثال: .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript .\WindowsDefenderATPOnboardingScript.cmd"

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>سيناريوهات ترحيل Configuration Manager نقطة النهاية من Microsoft 

>[!NOTE]
>ستحتاج إلى microsoft Endpoint Configuration Manager، الإصدار 2107 أو إصدار أحدث لتكوين نهج حماية نقطة النهاية perfom.

خطوات الترحيل: 

1. قم بتحديث الجهاز بالكامل بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016).
2. إنشاء مجموعة جديدة مع قواعد العضوية لتضمين الأجهزة التي سيتم ترحيلها.
3. [إنشاء تطبيق](/mem/configmgr/apps/deploy-use/create-applications) لتنفيذ المهام التالية: 
   1. إلغاء تثبيت SCEP.
   2. تثبيت [المتطلبات الأساسية](configure-server-endpoints.md#prerequisites) عند الاقتضاء.
   3. تثبيت Microsoft Defender لنقطة النهاية (راجع [تكوين نقاط نهاية الخادم](configure-server-endpoints.md).
   4. تطبيق البرنامج النصي **للإلحاق للاستخدام مع نهج المجموعة** التي تم تنزيلها من [Microsoft 365 Defender](https://security.microsoft.com). 
   > [!TIP]
   > يمكنك استخدام [البرنامج النصي المثبت](server-migration.md#installer-script) كجزء من التطبيق الخاص بك لأتمتة الخطوات المذكورة أعلاه.
4. نشر التطبيق إلى المجموعة الجديدة.
5. إنشاء نهج حماية نقطة النهاية (الموجودة) و/أو تعيينها إلى المجموعة.
6. تطبيق التحديثات.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>أنت تستخدم حاليا نقطة نهاية Microsoft Configuration Manager لإدارة خوادمك، وتقوم بتشغيل حل الحماية من الفيروسات غير التابع ل Microsoft وجهاز الاستشعار المستند إلى MMA. تريد الترقية إلى Microsoft Defender لنقطة النهاية الجديدة.

خطوات الترحيل:

1. قم بتحديث الجهاز بالكامل بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016).
2. إنشاء مجموعة جديدة مع قواعد العضوية لتضمين الأجهزة التي سيتم ترحيلها. 
3. تأكد من أن إدارة مكافحة الفيروسات من جهة خارجية لم تعد تدفع برنامج الحماية من الفيروسات إلى هذه الأجهزة.*
4. تأليف النهج الخاصة بك في عقدة Endpoint Protection الخاصة ب MECM والهدف إلى المجموعة التي تم إنشاؤها حديثا.*
5. إنشاء تطبيق لتنفيذ المهام التالية:
   1. إزالة تكوين مساحة عمل MMA Microsoft Defender لنقطة النهاية. راجع [إزالة مساحة عمل باستخدام PowerShell](/azure/azure-monitor/agents/agent-manage). هذه الخطوة اختيارية؛ سيتوقف جهاز استشعار EDR السابق عن التشغيل بعد أن يصبح أحدث جهاز نشطا.
   2. تثبيت [المتطلبات الأساسية](configure-server-endpoints.md#prerequisites) عند الاقتضاء.
   3. تثبيت Microsoft Defender لنقطة النهاية لحزمة Windows Server 2012 R2 و2016 **وتمكين الوضع السلبي**. راجع [تثبيت برنامج الحماية من الفيروسات من Microsoft Defender باستخدام سطر الأوامر](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. تطبيق البرنامج النصي **للإلحاق للاستخدام مع نهج المجموعة** التي تم تنزيلها من [Microsoft 365 Defender](https://security.microsoft.com).
6. تطبيق التحديثات.
7. قم بإزالة برنامج الحماية من الفيروسات غير الخاص ب Microsoft إما باستخدام وحدة تحكم الحماية من الفيروسات غير الخاصة ب Microsoft أو باستخدام نقطة نهاية Microsoft Configuration Manager حسب الاقتضاء. تأكد من إزالة تكوين الوضع السلبي.*

> [!TIP]
> يمكنك استخدام [البرنامج النصي](server-migration.md#installer script) المثبت كجزء من التطبيق الخاص بك لأتمتة الخطوات المذكورة أعلاه. لتمكين الوضع الخامل، قم بتطبيق العلامة -Passive. على سبيل المثال، .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript .\WindowsDefenderATPOnboardingScript.cmd" -Passive

*تنطبق هذه الخطوات فقط إذا كنت تنوي استبدال حل الحماية من الفيروسات غير التابع ل Microsoft. اطلع [على أفضل معا: برنامج الحماية من الفيروسات من Microsoft Defender Microsoft Defender لنقطة النهاية](why-use-microsoft-defender-antivirus.md).

لنقل جهاز إلى خارج الوضع السلبي، قم بتعيين المفتاح التالي إلى 0:

المسار: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: قيمة REG_DWORD: 0


## <a name="other-migration-scenarios"></a>سيناريوهات الترحيل الأخرى

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>لديك خادم تم إلحاقه باستخدام Microsoft Defender لنقطة النهاية المستندة إلى MMA. تم تثبيت SCEP (Windows Server 2012 R2) أو برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016). **لا** تتم إدارة هذا الجهاز من خلال Microsoft Defender for Cloud أو Microsoft إدارة نقاط النهاية أو نقطة نهاية Microsoft Configuration Manager.

1. قم بتحديث الجهاز بالكامل بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016).
2. إزالة تكوين مساحة عمل MMA Microsoft Defender لنقطة النهاية. راجع [إزالة مساحة عمل باستخدام PowerShell](/azure/azure-monitor/agents/agent-manage).
3. إلغاء تثبيت System Center Endpoint Protection (Windows Server 2012 R2).
4. تثبيت [المتطلبات الأساسية](configure-server-endpoints.md#prerequisites) عند الاقتضاء. 
5. تثبيت Microsoft Defender لنقطة النهاية (راجع [تكوين نقاط نهاية الخادم](configure-server-endpoints.md).)
6. تطبيق البرنامج النصي **للإلحاق للاستخدام مع نهج المجموعة** التي تم تنزيلها من [Microsoft 365 Defender](https://security.microsoft.com). 
7. تطبيق التحديثات.
8. إنشاء النهج وتطبيقها باستخدام نهج المجموعة أو PowerShell أو حل إدارة الجهات الخارجية.

> [!TIP]
> يمكنك استخدام البرنامج النصي المثبت لأتمتة الخطوات المذكورة أعلاه.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>لديك خادم تريد تثبيت Microsoft Defender لنقطة النهاية عليه. يحتوي على حماية نقطة النهاية غير التابعة ل Microsoft أو تم تثبيت حل الاستجابة والكشف عن نقطة النهاية. لا تنوي استخدام نقطة نهاية Microsoft Configuration Manager أو Microsoft Defender for Cloud. يمكنك استخدام آلية التوزيع الخاصة بك. 

1. قم بتحديث الجهاز بالكامل بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender (Windows Server 2016).
2. تثبيت Microsoft Defender لنقطة النهاية لحزمة Windows Server 2012 R2 & 2016 **وتمكين الوضع السلبي**. راجع [تثبيت برنامج الحماية من الفيروسات من Microsoft Defender باستخدام سطر الأوامر](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. تطبيق البرنامج النصي الإلحاق، المناسب للبيئة الخاصة بك، التي تم تنزيلها من [Microsoft 365 Defender](https://security.microsoft.com). 
4. إزالة حماية نقطة النهاية غير التابعة ل Microsoft أو حل الكشف عن نقطة النهاية والاستجابة لها، وإزالة الوضع السلبي.*
5. تطبيق التحديثات.
6. إنشاء النهج وتطبيقها باستخدام نهج المجموعة أو PowerShell أو حل إدارة الجهات الخارجية.

> [!TIP]
> يمكنك استخدام [البرنامج النصي المثبت](server-migration.md#installer-script) للمساعدة في أتمتة الخطوات من 1 إلى 4. لتمكين الوضع السلبي، قم بتطبيق العلامة -Passive التي ستضمن أن برنامج الحماية من الفيروسات Defender ينتقل إلى الوضع السلبي قبل الإلحاق ولا يتداخل مع حل مكافحة البرامج الضارة غير التابع ل Microsoft. ثم لضمان بقاء Defender Antivirus في الوضع السلبي بعد الإعداد لدعم قدرات EDR مثل EDR Block، تأكد من تعيين مفتاح التسجيل "ForceDefenderPassiveMode". المثال: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*تنطبق هذه الخطوة فقط إذا كنت تنوي استبدال حل الحماية من الفيروسات غير التابع ل Microsoft. نوصي باستخدام برنامج الحماية من الفيروسات من Microsoft Defender، المضمن في Microsoft Defender لنقطة النهاية، لتوفير مجموعة كاملة من القدرات. اطلع [على أفضل معا: برنامج الحماية من الفيروسات من Microsoft Defender Microsoft Defender لنقطة النهاية](why-use-microsoft-defender-antivirus.md).

لنقل جهاز إلى خارج الوضع السلبي، قم بتعيين المفتاح التالي إلى 0:

المسار: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: قيمة REG_DWORD: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>سيناريوهات Microsoft Defender for Cloud

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>أنت تستخدم Microsoft Defender for Cloud. تم تثبيت عامل مراقبة Microsoft (MMA) و/أو Microsoft Antimalware ل Azure (SCEP) وتريد الترقية.
إذا كنت تستخدم Microsoft Defender for Cloud، يمكنك الاستفادة من عملية الترقية التلقائية. راجع [حماية نقاط النهاية باستخدام حل EDR المتكامل ل Defender for Cloud: Microsoft Defender لنقطة النهاية](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>تكوين نهج المجموعة
للتكوين باستخدام نهج المجموعة، تأكد من أنك تستخدم أحدث ملفات ADMX في متجرك المركزي للوصول إلى خيارات نهج Defender for Endpoint الصحيحة. الرجاء الرجوع [إلى كيفية إنشاء المخزن المركزي وإدارته للقوالب الإدارية نهج المجموعة في Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) وتنزيل أحدث الملفات **لاستخدامها مع Windows 10**.
