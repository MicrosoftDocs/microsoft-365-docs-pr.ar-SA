---
title: خوادم Windows إلى Microsoft Defender لنقطة النهاية الخدمة
description: يتم Windows على الخوادم بحيث يمكنهم إرسال بيانات المستشعر إلى Microsoft Defender لنقطة النهاية المستشعر.
keywords: خادم onboard، الخادم، 2012r2، 2016، 2019، تهيئة الخادم، إدارة الأجهزة، تكوين خوادم Microsoft Defender لنقطة النهاية، خوادم Microsoft Defender لنقطة النهاية، خوادم Microsoft Defender لنقطة النهاية الخوادم
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
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 14c759cd243b8da9f338b777e430d4de9f735fc1
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498902"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>خوادم Windows إلى Microsoft Defender لنقطة النهاية الخدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- Windows Server 2012 R2
- Windows Server 2016‏
- Windows Server Semi-Annual Enterprise Channel
- Windows Server 2019 واللاحقة
- Windows الأساسي ل Server 2019
- Windows Server 2022
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configserver-abovefoldlink)

يوسع Defender for Endpoint الدعم ليشمل أيضا نظام Windows Server. يوفر هذا الدعم قدرات متقدمة للكشف عن الهجمات والتحري عنها بسلاسة من خلال Microsoft 365 Defender التحكم. يوفر الدعم Windows Server معلومات أكثر عمقا حول أنشطة الخادم، والتغطية للكشف عن هجمات kernel والذاكرة، كما يمكن إجراءات الاستجابة.

يصف هذا الموضوع كيفية تشغيل خوادم Windows معينة Microsoft Defender لنقطة النهاية.

للحصول على إرشادات حول كيفية تنزيل أمن Windows الأساسية Windows، راجع أمن Windows [الأساسية](/windows/device-security/windows-security-baselines).

## <a name="windows-server-onboarding-overview"></a>Windows نظرة عامة حول ا متنبأ الخادم

ستحتاج إلى إكمال الخطوات العامة التالية لترك الخدمة للخوادم بنجاح.

:::image type="content" source="images/server-onboarding-tools-methods.png" alt-text="رسم توضيحي لتدفق التكاتف للخوادم Windows والأجهزة Windows 10 الأخرى" lightbox="images/server-onboarding-tools-methods.png":::

**Windows Server 2012 R2 Windows Server 2016 (Preview)**

>[!IMPORTANT]
> ستحتاج إلى تشغيل ميزات المعاينة في قسم نقاط النهاية في Microsoft 365 Defender لاستخدام هذه الوظيفة. انتقل إلى [Microsoft 365 Defender > الإعدادات > نقاط النهاية > الميزات المتقدمة](https://security.microsoft.com/preferences2/integration) و تشغيل ميزات المعاينة.

- تنزيل حزم التثبيت والتركيب
- تطبيق حزمة التثبيت
- اتبع خطوات الboarding للأداة المقابلة

**Windows Server Semi-Annual Enterprise Channel Windows Server 2019**

- تنزيل حزمة الboarding
- اتبع خطوات الboarding للأداة المقابلة

>[!IMPORTANT]
>لكي تكون مؤهلا لشراء Microsoft Defender لنقطة النهاية Server SKU، يجب أن تكون قد اشتريت بالفعل حدا أدنى مدمجا لأي من تراخيص الاشتراك التالية أو Windows E5/A5 أو Microsoft 365 E5/A5 أو الأمان في Microsoft 365 E5 اشتراك.  لمزيد من المعلومات حول الترخيص، راجع [شروط المنتج](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  



### <a name="new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview"></a>وظائف Windows Server 2012 R2 و2016 الجديدة في الحل الموحد الحديث (معاينة)

يتطلب التنفيذ السابق ل Windows Server 2012 R2 Windows Server 2016 استخدام Microsoft Monitoring Agent (MMA).

تسهل حزمة الحل الموحد الجديدة من تشغيل الخوادم من خلال إزالة التبعيات والخطوات اللازمة للتثبيت. بالإضافة إلى ذلك، تأتي حزمة الحلول الموحدة هذه مع التحسينات الرئيسية التالية:

- [برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) [مع حماية الجيل التالي](/microsoft-365/security/defender-endpoint/next-generation-protection) Windows Server 2012 R2
- [قواعد تقليل مساحة الهجوم (ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- [حماية الشبكة](/microsoft-365/security/defender-endpoint/network-protection)
- [الوصول إلى المجلدات الخاضعة للتحكم](/microsoft-365/security/defender-endpoint/controlled-folders)
- [حظر التطبيقات (PUA) غير المرغوب فيها](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [قدرات الكشف المحسنة](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
- [إمكانات الاستجابة الموسعة](/microsoft-365/security/defender-endpoint/respond-machine-alerts) على الأجهزة [والملفات](/microsoft-365/security/defender-endpoint/respond-file-alerts)
- [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](/microsoft-365/security/defender-endpoint/edr-in-block-mode)
- [الاستجابة المباشرة](/microsoft-365/security/defender-endpoint/live-response)
- [التحقيق والرد التلقائي (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations)
- [الحماية من العبث](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection)

استنادا إلى الخادم الذي تقوم بتركيبه، يتم تثبيت الحل الموحد برنامج الحماية من الفيروسات من Microsoft Defender و/أو الكشف التلقائي والاستجابة على النقط النهائية المستشعر. يشير الجدول التالي إلى المكون الذي تم تثبيته وما هو مضمن بشكل افتراضي.

|إصدار الخادم|AV|الكشف التلقائي والاستجابة على النقط النهائية|
|----|----|----|
|Windows Server 2012 R2 SP1|![نعم.](images/svg/check-yes.svg)|![نعم.](images/svg/check-yes.svg)|
|Windows Server 2016‏|مضمن|![نعم.](images/svg/check-yes.svg)|
|Windows Server 2019 أو أي وقت لاحق|مضمن|مضمن|

إذا سبق لك أن قمت بتكحيل الخوادم باستخدام MMA، فاتبع الإرشادات المتوفرة في ترحيل [الخادم](server-migration.md) للترحيل إلى الحل الجديد.

>[!NOTE]
>أثناء وجود طريقة التكميل هذه Windows Server 2012 R2 و Windows Server 2016 في وضع المعاينة، يمكنك اختيار الاستمرار في استخدام أسلوب الإستخدام السابق باستخدام Microsoft Monitoring Agent (MMA). لمزيد من المعلومات، راجع تثبيت نقاط النهاية [وتكوينها باستخدام MMA](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma).

#### <a name="known-issues-and-limitations-on-the-new-unified-solution-package-for-windows-server-2012-r2-and-2016"></a>المشاكل والقيود المعروفة في حزمة الحلول الموحدة الجديدة Windows Server 2012 R2 و2016

تنطبق المحددات التالية على حزمة الحلول الموحدة الجديدة Windows Server 2012 R2 و2016:

- تأكد من تلبية متطلبات الاتصال كما هو محدد في تمكين الوصول [Microsoft Defender لنقطة النهاية عناوين URL للخدمة في الخادم](/microsoft-365/security/defender-endpoint/configure-proxy-internet?enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) الوكيل. وهي مكافئة لتلك الخاصة Windows Server 2019. 
- نحن نعمل على التحقق من مشكلة في اتصال Windows Server 2012 R2 بالسحابة عند استخدام TelemetryProxyServer الثابت ولا يمكن الوصول إلى عناوين URL لقائمة إلغاء الشهادة (CRL) من سياق حساب النظام. إن التخفيف الفوري هو إما استخدام خيار وكيل بديل يوفر مثل هذا الاتصال، أو تكوين الوكيل نفسه عبر إعداد WinInet في سياق حساب النظام.
- في السابق، كان استخدام وكيل مراقبة Microsoft (MMA) على Windows Server 2016 وما يليه يسمح لبوابة OMS / Log Analytics بتوفير الاتصال بالخدمات السحابية ل Defender. الحل الجديد، مثل Microsoft Defender لنقطة النهاية على Windows Server 2019 و Windows Server 2022 و Windows 10، لا يدعم هذه البوابة.

- على Windows Server 2016، تحقق من أن برنامج الحماية من الفيروسات من Microsoft Defender تم تثبيته، وهو نشط وم التحديث. يمكنك تنزيل أحدث إصدار من النظام الأساسي وتثبيته باستخدام Windows Update. بدلا من ذلك، قم بتنزيل حزمة التحديث يدويا من [كتالوج Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) أو [من MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).  
- على Windows Server 2012 R2، لا توجد واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender. بالإضافة إلى ذلك، تسمح واجهة المستخدم Windows Server 2016 فقط للعمليات الأساسية. لتنفيذ عمليات على جهاز محليا، يمكنك الرجوع إلى إدارة Microsoft Defender لنقطة النهاية [باستخدام PowerShell و WMI MPCmdRun.exe](/microsoft-365/security/defender-endpoint/manage-mde-post-migration-other-tools). ونتيجة لذلك، قد لا تعمل الميزات التي تعتمد بشكل خاص على تفاعل المستخدم، مثل المكان الذي يتم فيه مطالبة المستخدم لاتخاذ قرار أو تنفيذ مهمة معينة، كما هو متوقع. من المستحسن تعطيل واجهة المستخدم أو عدم تمكينها ولا يتطلب تفاعل المستخدم على أي خادم مدار حيث قد يؤثر على إمكانية الحماية.
- لا تتوفر كل قواعد تقليل مساحة الهجوم على كل أنظمة التشغيل. راجع [قواعد تقليل مساحة الهجوم (ASR](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)).
- لتمكين ["حماية الشبكة"](/microsoft-365/security/defender-endpoint/network-protection)، يلزم تكوين إضافي:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

  بالإضافة إلى ذلك، من المستحسن إجراء اختبار الأداء في بيئتك على الأجهزة التي بها نسبة كبيرة من حركة مرور الشبكة قبل تمكين هذه الإمكانية على نطاق واسع. قد تحتاج إلى حساب استهلاك موارد إضافي.
- على Windows Server 2012 R2، قد لا يتم ملء أحداث الشبكة في المخطط الزمني. تتطلب هذه المشكلة إصدار Windows Update كجزء من مجموعة [12 أكتوبر 2021 الشهرية (KB5006714)](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e).
- إن ترقيات نظام التشغيل غير معتمدة. إيقاف التشغيل ثم إلغاء التثبيت قبل الترقية.
- لا يتم دعم الاستثناءات  التلقائية لأدوار الخادم على Windows Server 2012 R2؛ ومع ذلك، فإن الاستثناءات المضمنة لملفات نظام التشغيل هي استثناءات. لمزيد من المعلومات حول إضافة الاستثناءات، راجع توصيات فحص الفيروسات لأجهزة الكمبيوتر الخاصة بالمؤسسات التي تعمل بالإصدارات المدعمة [حاليا من](https://support.microsoft.com/topic/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows-kb822158-c067a732-f24a-9079-d240-3733e39b40bc) Windows.
- في الوقت الحالي، إذا اخترت إيقاف تشغيل الحل الحديث الموحد وإبعاد تثبيت مستشعر الكشف التلقائي والاستجابة على النقط النهائية المستند إلى MMA `MsSenseS.exe` السابق، فقد تواجه أعطال متكررة. 

كحل بديل، قم بإزالة مفاتيح التسجيل التالية إذا كانت موجودة:
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security\fdedb2b8-61e4-4a7e-8b15-abf214a08fcc`
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security\c60418cc-7e07-400f-ae3b-d521c5dbd96f`

يمكنك استخدام الأوامر التالية:

```cmd
reg delete HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security /v fdedb2b8-61e4-4a7e-8b15-abf214a08fcc /f
reg delete HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security /v c60418cc-7e07-400f-ae3b-d521c5dbd96f /f
```
لا حاجة إلى إعادة التشغيل.


<a name="integration-with-azure-defender"></a>

## <a name="integration-with-microsoft-defender-for-cloud"></a>التكامل مع Microsoft Defender for Cloud

Microsoft Defender لنقطة النهاية الدمج بسلاسة مع Microsoft Defender for Cloud. يمكنك تشغيل الخوادم تلقائيا، وظهور الخوادم التي يراقبها Azure Defender في Defender for Endpoint، وإجراء عمليات تحقيق تفصيلية كعميل Microsoft Defender for Cloud.

لمزيد من المعلومات، راجع [التكامل مع Microsoft Defender for Cloud](azure-server-integration.md).

> [!NOTE]
> بالنسبة Windows Server 2012 R2 و2016 الذي يعمل بمعاينة الحل الموحد الحديثة، لا يتوفر التكامل مع Microsoft Defender for Cloud / Microsoft Defender للخوادم للتنبيه والنشر التلقائي حتى الآن. على الرغم من أنه يمكنك تثبيت الحل الجديد يدويا على هذه الأجهزة، لن يتم عرض أي تنبيهات في Microsoft Defender for Cloud.

> [!NOTE]
> - تم توسيع التكامل بين Microsoft Defender للخوادم Microsoft Defender لنقطة النهاية لدعم Windows Server 2022 و Windows [Server 2019 و Windows Virtual Desktop (WVD)](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview) .
> - تم تعطيل مراقبة نقطة نهاية الخادم باستخدام هذا التكامل Office 365 سحابة القطاع الحكومي العملاء.

## <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 Windows Server 2016

> [!NOTE]
> أثناء وجود طريقة التكميل هذه Windows Server 2012 R2 و Windows Server 2016 في وضع المعاينة، يمكنك اختيار الاستمرار في استخدام أسلوب الإستخدام السابق باستخدام Microsoft Monitoring Agent (MMA). لمزيد من المعلومات، راجع تثبيت نقاط النهاية [وتكوينها باستخدام MMA](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma).

### <a name="prerequisites"></a>المتطلبات الأساسية

**المتطلبات الأساسية Windows Server 2012 R2**

إذا قمت بتحديث الأجهزة بالكامل بأحدث حزمة [مجموعة شهرية،](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e) فلا **توجد أي متطلبات** أساسية إضافية.

ستتحقق حزمة المثبت مما إذا كانت المكونات التالية مثبتة بالفعل عبر تحديث:

- [التحديث لتجربة العملاء و بيانات التشخيص](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [تحديث "وقت تشغيل C العام" في Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

**المتطلبات الأساسية Windows Server 2016** 

إلى جانب تحديث الجهاز بالكامل باستخدام التحديث التراكمي الأخير (LCU)، تحقق من أن برنامج الحماية من الفيروسات من Microsoft Defender مثبتا، نشطا ومحدثا. يمكنك تنزيل أحدث إصدار من النظام الأساسي وتثبيته باستخدام Windows Update. بدلا من ذلك، قم بتنزيل حزمة التحديث يدويا من [كتالوج Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) أو [من MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64). 

> [!NOTE]
> من أجل تحديث الإصدار المضمن من Windows Defender بنجاح، الذي لديه رقم إصدار يبدأ ب 4.10، إلى النظام الأساسي الأخير المتوفر، يجب تطبيق تحديث مكدس الخدمة بالإضافة إلى التحديث التراكمي الأخير (LCU) المساوي أو الأحدث من 20 سبتمبر 2018— KB4457127 (إصدار نظام التشغيل 14393.2515).

**المتطلبات الأساسية لتشغيل حلول الأمان الخاصة ب جهة خارجية**

إذا كنت تنوي استخدام حل مكافحة البرامج الضارة من جهة خارجية، فسوف تحتاج إلى تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. يجب عليك تذكر تعيين الوضع السلبي أثناء عملية التثبيت والتركيب.

**حزمة تحديث جديدة Microsoft Defender لنقطة النهاية على Windows Server 2012 R2 و2016**

لتلقي تحسينات المنتج العادية وإصلاحات لمكون استشعار الكشف التلقائي والاستجابة على النقط النهائية، تأكد من Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) أو الموافقة عليه. بالإضافة إلى ذلك، لإبقاء مكونات الحماية محدثة، راجع إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية [وتطبيق الأساسات](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

### <a name="onboarding-steps-summary"></a>ملخص خطوات الboarding

- الخطوة 1: [تنزيل حزم التثبيت والتركيب](#step-1-download-installation-and-onboarding-packages)
- الخطوة 2: [تطبيق حزمة التثبيت والتركيب](#step-2-apply-the-installation-and-onboarding-package)
- الخطوة 3: [إكمال خطوات الboarding](#step-3-complete-the-onboarding-steps) 


### <a name="step-1-download-installation-and-onboarding-packages"></a>الخطوة 1: تنزيل حزم التثبيت والتركيب

ستحتاج إلى تنزيل حزم التثبيت **والتركيب** من المدخل.

> [!div class="mx-imgBorder"]
> ![صورة لوحة معلومات الboarding](images/install-agent-onboard.png)


   > [!NOTE]
   > على Windows Server 2012R2، برنامج الحماية من الفيروسات من Microsoft Defender تثبيت حزمة التثبيت وسيبقى نشطا إلا إذا قمت بتعيينه إلى الوضع السلبي. على Windows Server 2016، برنامج الحماية من الفيروسات من Microsoft Defender تثبيت ميزة (راجع التبديل إلى [MDE](/microsoft-365/security/defender-endpoint/switch-to-mde-phase-2#re-enable-microsoft-defender-antivirus-on-windows-server-2016)) أولا وتحديثها بالكامل قبل بدء التثبيت.
   > 
   > إذا كنت تقوم بتشغيل حل غير Microsoft لمكافحة البرامج الضارة، فتأكد من إضافة استثناءات ل برنامج الحماية من الفيروسات من Microsoft Defender (من قائمة عمليات [Microsoft Defender](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) هذه على علامة التبويب عمليات Defender) إلى الحل غير الخاص ب Microsoft قبل التثبيت.  من المستحسن أيضا إضافة حلول أمان غير Microsoft إلى قائمة استثناءات Defender Antivirus.


تحتوي **حزمة التثبيت** على ملف MSI الذي يثبت Microsoft Defender لنقطة النهاية.

تحتوي **حزمة التكهين** على الملفات التالية:

- `OptionalParamsPolicy` - يحتوي على الإعداد الذي يمكن مجموعة العينة
- `WindowsDefenderATPOnboardingScript.cmd` - يحتوي على البرنامج النصي ل الboarding

استخدم الخطوات التالية لتنزيل الحزم: 

1. في Microsoft 365 Defender، انتقل إلى الإعدادات > إدارة الجهاز > **في الحافظة**.

2. حدد **Windows Server 2012 R2 و2016**.

3. حدد **تنزيل حزمة التثبيت** واحفظ الملف .msi. 
 
4. حدد **تنزيل حزمة التكهيل** واحفظ الملف .zip.

5. ثبت حزمة التثبيت باستخدام أي من الخيارات لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender. يتطلب التثبيت أذونات إدارية.



### <a name="step-2-apply-the-installation-and-onboarding-package"></a>الخطوة 2: تطبيق حزمة التثبيت والتركيب
في هذه الخطوة، سيتم تثبيت مكونات المنع والكشف المطلوبة قبل تهيئة جهازك في بيئة Microsoft Defender لنقطة النهاية السحابة، لتحضير الجهاز للتركيب. تأكد من [أن كل المتطلبات](#prerequisites) الأساسية قد تم تحقيقها. 

   > [!NOTE]
   > برنامج الحماية من الفيروسات من Microsoft Defender سيتم تثبيته وسيبقى نشطا إلا إذا قمت بتعيينه إلى الوضع السلبي. 

#### <a name="options-to-install-the-microsoft-defender-for-endpoint-packages"></a>خيارات لتثبيت حزم Microsoft Defender لنقطة النهاية

في المقطع السابق، قمت بتنزيل حزمة تثبيت. تحتوي حزمة التثبيت على المثبت لجميع مكونات Microsoft Defender لنقطة النهاية. 

يمكنك استخدام أي من الخيارات التالية لتثبيت الوكيل:
- [تثبيت باستخدام سطر الأوامر](#install-microsoft-defender-for-endpoint-using-the-command-line)
- [التثبيت باستخدام برنامج نصي](#install-microsoft-defender-for-endpoint-using-a-script)
- [تطبيق حزم التثبيت والتركيب باستخدام نهج المجموعة](#apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy)

##### <a name="install-microsoft-defender-for-endpoint-using-the-command-line"></a>تثبيت Microsoft Defender لنقطة النهاية باستخدام سطر الأوامر
استخدم حزمة التثبيت من الخطوة السابقة لتثبيت Microsoft Defender لنقطة النهاية. 


قم بتشغيل الأمر التالي لتثبيت Microsoft Defender لنقطة النهاية:

```console
Msiexec /i md4ws.msi /quiet
```

إلغاء التثبيت، تأكد من إيقاف تشغيل الجهاز أولا باستخدام البرنامج النصي المناسب ل offboarding. بعد ذلك، لوحة التحكم \> البرامج \> والميزات لتنفيذ إلغاء التثبيت.

بدلا من ذلك، يمكنك تشغيل أمر إلغاء التثبيت التالي  إلغاء تثبيت Microsoft Defender لنقطة النهاية:

```console
Msiexec /x md4ws.msi /quiet
```

يجب استخدام الحزمة نفسها التي استخدمتها للتركيب لكي ينجح الأمر أعلاه.

يمنع `/quiet` مفتاح التبديل كل الإعلامات.

> [!NOTE]
> برنامج الحماية من الفيروسات من Microsoft Defender الانتقال تلقائيا إلى الوضع السلبي. يمكنك اختيار تعيين برنامج الحماية من الفيروسات من Microsoft Defender لتشغيله في الوضع السلبي إذا كنت تقوم بتشغيل حل مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft. بالنسبة إلى عمليات تثبيت سطر الأوامر`FORCEPASSIVEMODE=1`، يحدد الاختياري على الفور برنامج الحماية من الفيروسات من Microsoft Defender المكون إلى الوضع "غير النشط" لتجنب التداخل. بعد ذلك، للتأكد من أن برنامج الحماية من الفيروسات ل Defender يظل في الوضع السلبي بعد التكحيل لدعم قدرات مثل الكشف التلقائي والاستجابة على النقط النهائية Block، قم بتعيين مفتاح التسجيل "ForceDefenderPassiveMode".

يوفر الدعم Windows Server معلومات أكثر عمقا حول أنشطة الخادم، والتغطية للكشف عن هجمات kernel والذاكرة، كما يمكن إجراءات الاستجابة.

##### <a name="install-microsoft-defender-for-endpoint-using-a-script"></a>تثبيت Microsoft Defender لنقطة النهاية باستخدام برنامج نصي

يمكنك استخدام البرنامج [النصي للمثبت](server-migration.md#installer-script) للمساعدة في أتمتة التثبيت، إلغاء التثبيت، والتركيب. لمزيد من المعلومات، راجع الإرشادات الموجودة في المقطع التالي لاستخدام البرنامج النصي مع نهج المجموعة.

##### <a name="apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy"></a>تطبيق Microsoft Defender لنقطة النهاية التثبيت وحزم التركيب باستخدام نهج المجموعة

1. إنشاء نهج مجموعة: <br> افتح نهج المجموعة [إدارة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) البيانات (GPMC)، وانقر بضغطة نهج المجموعة فوق  العناصر التي تريد تكوينها وانقر فوق **جديد**. أدخل اسم "مجموعة العناصر" الجديدة في مربع الحوار الذي يتم عرضه وانقر فوق **موافق**.

2. افتح نهج المجموعة [إدارة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) البيانات (GPMC)، وانقر بز الماوس الأيمن فوق نهج المجموعة كائن (GPO) الذي تريد تكوينه وانقر فوق **تحرير**.

3. في نهج المجموعة **إدارة،** انتقل إلى **تكوين** الكمبيوتر، ثم **التفضيلات**، ثم **إعدادات لوحة التحكم**.

4. انقر بز الماوس الأيمن فوق **المهام المجدولة**، وأشير إلى **جديد**، ثم انقر فوق مهمة فورية (على الأقل **Windows 7)**.

5. في نافذة **المهمة** التي تفتح، انتقل إلى علامة **التبويب عام** . ضمن **خيارات الأمان،** انقر **فوق تغيير المستخدم أو المجموعة** وا اكتب النظام، ثم انقر **فوق التحقق من الأسماء** ثم **موافق**. يظهر NT AUTHORITY\SYSTEM ك حساب المستخدم الذي سيتم تشغيل المهمة عليه.

6. حدد **تشغيل ما إذا كان المستخدم قد سجل دخوله** أم لا وحدد خانة الاختيار **تشغيل بأعلى** امتيازات.

7. في الحقل الاسم، اكتب اسما مناسبا للمهمة المجدولة (على سبيل المثال، Defender لنشر نقطة النهاية).

8. انتقل إلى علامة **التبويب** إجراءات وحدد **جديد...** تأكد من **تحديد بدء** برنامج في **حقل** الإجراء. يقوم [البرنامج النصي المثبت](server-migration.md#installer-script) بمعالجة عملية التثبيت، ثم تنفيذ خطوة التركيب مباشرة بعد اكتمال التثبيت. حدد *C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe* ثم قم بتوفير الوسيطات:

    ```console
     -ExecutionPolicy RemoteSigned \\servername-or-dfs-space\share-name\install.ps1 -OnboardingScript \\servername-or-dfs-space\share-name\windowsdefenderatponboardingscript.cmd
    ```  

     >[!NOTE]
    >إذا كنت بحاجة إلى استكشاف مشاكل تثبيت الوكيل وإصلاحها، ف أضف '-etl -log' إلى install.ps1 البرنامج النصي.
    >
    >إعداد نهج التنفيذ الموصى به هو `Allsigned`. يتطلب هذا الأمر استيراد شهادة توقيع البرنامج النصي إلى مخزن الناشرين الموثوق بهم في الكمبيوتر المحلي إذا كان البرنامج النصي قيد التشغيل ك SYSTEM في نقطة النهاية.

    استبدل \\servername-or-dfs-space\share-name بمسار UNC، باستخدام اسم المجال المؤهل بالكامل (FQDN) *لخادم الملفاتinstall.ps1* المشترك. يجب وضع md4ws.msi حزمة المثبت في الدليل نفسه.  تأكد أيضا من أن أذونات مسار UNC تسمح بالوصول للقراءة إلى حساب الكمبيوتر الذي يتم تثبيت النظام الأساسي له.

   

    بالنسبة إلى السيناريوهات التي تريد برنامج الحماية من الفيروسات من Microsoft Defender فيها مع حلول مكافحة البرامج الضارة غير الخاصة ب Microsoft، أضف المعلمة $Passive لتعيين الوضع السلبي أثناء التثبيت.

9. حدد **موافق** وأغلق أي نوافذ GPMC مفتوحة.

10. لربط "مجموعة وحدات المجموعة" بوحدة تنظيم (OU)، انقر بز الماوس الأيمن وحدد ربط "مجموعة" **موجودة**. في مربع الحوار الذي يتم عرضه، حدد نهج المجموعة الذي تريد ربطه. انقر فوق **موافق**.

للحصول على إعدادات تكوين إضافية، راجع [تكوين إعدادات مجموعة](configure-endpoints-gp.md#configure-sample-collection-settings) العينة وإعدادات التكوين [المستحسنة الأخرى](configure-endpoints-gp.md#other-recommended-configuration-settings).

### <a name="step-3-complete-the-onboarding-steps"></a>الخطوة 3: إكمال خطوات الboarding

لا تنطبق الخطوات التالية إلا إذا كنت تستخدم حل مكافحة البرامج الضارة من جهة خارجية. ستحتاج إلى تطبيق الإعدادات التالية برنامج الحماية من الفيروسات من Microsoft Defender وضع غير سلبي. تحقق من تكوينه بشكل صحيح:

1. تعيين إدخال السجل التالي:
    - المسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
    - الاسم: `ForceDefenderPassiveMode`
    - اكتب: `REG_DWORD`
    - القيمة: `1`

       :::image type="content" source="images/atp-verify-passive-mode.png" alt-text="نتيجة التحقق من الوضع السلبي" lightbox="images/atp-verify-passive-mode.png":::
> [!IMPORTANT]
>
> - عند استخدام Microsoft Defender for Cloud لمراقبة الخوادم، يتم تلقائيا إنشاء مستأجر Defender for Endpoint (في الولايات المتحدة للمستخدمين الأميركيين، وفي الاتحاد الأوروبي للمستخدمين الأوروبيين، وفي المملكة المتحدة لمستخدمي المملكة المتحدة).
يتم تخزين البيانات التي يقوم Defender for Endpoint بتجميعها في الموقع الجغرافي للمستأجر كما هو محدد أثناء توفيرها.
> - إذا كنت تستخدم Defender ل Endpoint قبل استخدام Microsoft Defender for Cloud، سيتم تخزين بياناتك في الموقع الذي حددته عند إنشاء المستأجر الخاص بك حتى لو قمت بالدمج مع Microsoft Defender for Cloud في وقت لاحق.
> - بمجرد تكوينها، لا يمكنك تغيير الموقع الذي تم تخزين البيانات فيه. إذا كنت بحاجة إلى نقل بياناتك إلى موقع آخر، يجب الاتصال بدعم Microsoft لإعادة تعيين المستأجر.
> - تقوم حزمة "Windows Server 2019" و"Windows Server 2022 إدارة نقاط النهاية من Microsoft" حاليا بشحن برنامج نصي. لمزيد من المعلومات حول كيفية نشر البرامج النصية في Configuration Manager، راجع [الحزم والبرامج في](/configmgr/apps/deploy-use/packages-and-programs) Configuration Manager.
> - البرنامج النصي المحلي مناسب لإثبات المبدأ ولكن لا يجب استخدامه لنشر الإنتاج. لنشر الإنتاج، نوصي باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager.



## <a name="windows-server-semi-annual-enterprise-channel-and-windows-server-2019-and-windows-server-2022"></a>Windows Server Semi-Annual Enterprise Channel Windows Server 2019 Windows Server 2022

تقوم حزمة التكهين Windows Server 2019 Windows Server 2022 حتى إدارة نقاط النهاية من Microsoft حاليا بشحن برنامج نصي. لمزيد من المعلومات حول كيفية نشر البرامج النصية في Configuration Manager، راجع [الحزم والبرامج في](/configmgr/apps/deploy-use/packages-and-programs) Configuration Manager.

### <a name="download-package"></a>تنزيل الحزمة

1. في Microsoft 365 Defender، انتقل إلى الإعدادات > إدارة الجهاز > **في الحافظة**.

2. حدد **Windows Server 1803 و2019**.

3. حدد **تنزيل الحزمة**. احفظه WindowsDefenderATPOnboardingPackage.zip.

4. اتبع الخطوات المتوفرة في [القسم إكمال خطوات التكهين](#step-3-complete-the-onboarding-steps) .


## <a name="verify-the-onboarding-and-installation"></a>التحقق من التركيب والتركيب

تحقق من برنامج الحماية من الفيروسات من Microsoft Defender Microsoft Defender لنقطة النهاية قيد التشغيل.

## <a name="run-a-detection-test-to-verify-onboarding"></a>تشغيل اختبار الكشف للتحقق من ال

بعد تشغيل الجهاز، يمكنك أن تختار تشغيل اختبار الكشف للتحقق من أن الجهاز مواد بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية جديد](run-detection-test.md).

> [!NOTE]
> تشغيل برنامج الحماية من الفيروسات من Microsoft Defender غير مطلوب ولكن من المستحسن. إذا كان منتج مورد برنامج الحماية من الفيروسات آخر هو حل الحماية الأساسي لنقطة النهاية، يمكنك تشغيل Defender Antivirus في الوضع السلبي. يمكنك فقط تأكيد تشغيل الوضع السلبي بعد التحقق من أن Microsoft Defender لنقطة النهاية استشعار (SENSE) قيد التشغيل.

1. تشغيل الأمر التالي للتحقق من تثبيت برنامج الحماية من الفيروسات من Microsoft Defender:

    >[!NOTE]
    >لا يلزم إجراء خطوة التزيين هذه إلا إذا كنت تستخدم برنامج الحماية من الفيروسات من Microsoft Defender كحل نشط لمكافحة البرامج الضارة.

    `sc.exe query Windefend`


    إذا كانت النتيجة 'الخدمة المحددة غير موجودة كخدمة مثبتة'، ستحتاج إلى تثبيت برنامج الحماية من الفيروسات من Microsoft Defender. 


    للحصول على معلومات حول كيفية استخدام نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها على خوادم Windows، راجع استخدام إعدادات نهج المجموعة لتكوين وإدارة [ برنامج الحماية من الفيروسات من Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md).

2. تشغيل الأمر التالي للتحقق من أن Microsoft Defender لنقطة النهاية قيد التشغيل:

    `sc.exe query sense`

    يجب أن تظهر النتيجة أنها قيد التشغيل. إذا واجهت مشاكل تتعلق بالتكدث، فشاهد استكشاف الأخطاء في [الرصيد وإصلاحها](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>تشغيل اختبار الكشف

اتبع الخطوات في [تشغيل اختبار الكشف](run-detection-test.md) على جهاز تم إعداده حديثا للتحقق من أن الخادم يعمل على إعداد تقرير إلى Defender لخدمة نقطة النهاية.

## <a name="next-steps"></a>الخطوات التالية

بعد تهيئة الأجهزة للخدمة بنجاح، ستحتاج إلى تكوين المكونات الفردية للخدمة Microsoft Defender لنقطة النهاية. اتبع [أمر الاعتماد](prepare-deployment.md#adoption-order) لكي تسترشد في تمكين المكونات المختلفة.

## <a name="offboard-windows-servers"></a>إيقاف تشغيل Windows الخادم

يمكنك إيقاف تشغيل Windows Server 2012 R2 و Windows Server 2016 و Windows Server (SAC) و Windows Server 2019 و Windows Server 2019 Core بالطريقة نفسها المتوفرة للأجهزة العميلة ل Windows 10.

- [أجهزة إيقاف التشغيل التي تستخدم نهج المجموعة](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [أجهزة إيقاف التشغيل التي تستخدم Configuration Manager](configure-endpoints-sccm.md#offboard-devices-using-configuration-manager)
- [إيقاف تشغيل الأجهزة ومراقبتها باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)
- [أجهزة إيقاف التشغيل باستخدام برنامج نصي محلي](configure-endpoints-script.md#offboard-devices-using-a-local-script)

بالنسبة إلى Windows الخادم الأخرى، لديك خياران ل Windows خوادم من الخدمة:

- إلغاء تثبيت عامل MMA
- إزالة تكوين مساحة عمل Defender لنقطة النهاية

> [!NOTE]
> تنطبق إرشادات إيقاف التشغيل هذه لإصدارات خوادم Windows الأخرى أيضا إذا كنت تقوم بتشغيل الإصدار Microsoft Defender لنقطة النهاية السابق ل Windows Server 2016 و Windows Server 2012 R2 الذي يتطلب MMA. توجد إرشادات الترحيل إلى الحل الموحد الجديد في سيناريوهات ترحيل الخادم [في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الإصدارات السابقة من Windows](onboard-downlevel.md)
- [أجهزة Windows 10 الأجهزة](configure-endpoints.md)
- [الأجهزة غير المجهزة Windows](configure-endpoints-non-windows.md)
- [تكوين إعدادات الوكيل والاتصال بالإنترنت](configure-proxy-internet.md)
- [تشغيل اختبار الكشف على جهاز جديد ل Defender for Endpoint](run-detection-test.md)
- [استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية في الحافظة](troubleshoot-onboarding.md)
