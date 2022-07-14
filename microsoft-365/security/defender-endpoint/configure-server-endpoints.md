---
title: إلحاق خوادم Windows بخدمة Microsoft Defender لنقطة النهاية
description: إلحاق خوادم Windows بحيث يمكنها إرسال بيانات جهاز الاستشعار إلى أداة استشعار Microsoft Defender لنقطة النهاية.
keywords: خادم الإلحاق، الخادم، 2012r2، 2016، 2019، إلحاق الخادم، إدارة الأجهزة، تكوين خوادم Microsoft Defender لنقطة النهاية، إلحاق خوادم Microsoft Defender لنقطة النهاية، إلحاق Microsoft Defender لنقطة النهاية ملقمات
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
ms.openlocfilehash: ac40dcc986dfb4c66b9030cdf8c22ebabe1bd3d2
ms.sourcegitcommit: 5463d4518c269d9c125bb66836a780df292b4854
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/14/2022
ms.locfileid: "66795411"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>إلحاق خوادم Windows بخدمة Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- Windows Server 2012 R2
- Windows Server 2016‏
- Windows Server Semi-Annual قناة المؤسسة
- Windows Server 2019 والإطارات الأحدث
- إصدار Windows Server 2019 الأساسي
- Windows Server 2022
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configserver-abovefoldlink)

يقوم Defender لنقطة النهاية بتوسيع الدعم ليشمل أيضا نظام التشغيل Windows Server. يوفر هذا الدعم قدرات متقدمة للكشف عن الهجمات والتحقيق فيها بسلاسة من خلال وحدة التحكم Microsoft 365 Defender. يوفر دعم Windows Server رؤية أعمق لأنشطة الخادم، وتغطية الكشف عن هجمات النواة والذاكرة، وتمكين إجراءات الاستجابة.

يصف هذا الموضوع كيفية إلحاق خوادم Windows معينة Microsoft Defender لنقطة النهاية.

للحصول على إرشادات حول كيفية تنزيل أمن Windows الأساسات لخوادم Windows واستخدامها، راجع [أمن Windows الأساسات](/windows/device-security/windows-security-baselines).

## <a name="windows-server-onboarding-overview"></a>نظرة عامة على إلحاق Windows Server

ستحتاج إلى إكمال الخطوات العامة التالية لإلحاق الخوادم بنجاح.

:::image type="content" source="images/server-onboarding-tools-methods.png" alt-text="رسم توضيحي لتدفق الإلحاق لخوادم Windows والأجهزة Windows 10" lightbox="images/server-onboarding-tools-methods.png":::

## <a name="integration-with-microsoft-defender-for-servers"></a>التكامل مع Microsoft Defender for Servers

يتكامل Microsoft Defender لنقطة النهاية بسلاسة مع Microsoft Defender for Servers. يمكنك إلحاق الخوادم تلقائيا، وظهور الخوادم التي يراقبها Microsoft Defender for Cloud في Defender لنقطة النهاية، وإجراء تحقيقات مفصلة كعميل Microsoft Defender for Cloud.

لمزيد من المعلومات، راجع [التكامل مع Microsoft Defender for Cloud](azure-server-integration.md).

> [!NOTE]
> بالنسبة إلى Windows Server 2012 R2 و2016 الذي يقوم بتشغيل الحل الموحد الحديث، يمكنك إما تثبيت/ترقية الحل الجديد يدويا على هذه الأجهزة، أو استخدام التكامل لنشر الخوادم التي تغطيها خطة Microsoft Defender for Server الخاصة بك أو ترقيتها تلقائيا. مزيد من المعلومات حول إجراء التبديل في [حماية نقاط النهاية باستخدام حل EDR المتكامل ل Defender for Cloud: Microsoft Defender لنقطة النهاية](/azure/defender-for-cloud/integration-defender-for-endpoint?tabs=windows).
> - عند استخدام Microsoft Defender for Cloud لمراقبة الخوادم، يتم إنشاء مستأجر Defender لنقطة النهاية تلقائيا (في الولايات المتحدة لمستخدمي الولايات المتحدة، وفي الاتحاد الأوروبي للمستخدمين الأوروبيين، وفي المملكة المتحدة لمستخدمي المملكة المتحدة).
يتم تخزين البيانات التي يجمعها Defender لنقطة النهاية في الموقع الجغرافي للمستأجر كما هو محدد أثناء التوفير.
> - إذا كنت تستخدم Defender لنقطة النهاية قبل استخدام Microsoft Defender for Cloud، فسيتم تخزين بياناتك في الموقع الذي حددته عند إنشاء المستأجر الخاص بك حتى إذا قمت بالتكامل مع Microsoft Defender for Cloud في وقت لاحق.
> - بمجرد التكوين، لا يمكنك تغيير الموقع حيث يتم تخزين بياناتك. إذا كنت بحاجة إلى نقل بياناتك إلى موقع آخر، فستحتاج إلى الاتصال بدعم Microsoft لإعادة تعيين المستأجر.
> - تم توسيع التكامل بين Microsoft Defender للخوادم Microsoft Defender لنقطة النهاية لدعم Windows Server 2022 [وWindows Server 2019 وWindows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)
> - تم تعطيل مراقبة نقطة نهاية الخادم باستخدام هذا التكامل لعملاء Office 365 GCC.

**Windows Server 2012 R2 وWindows Server 2016**:

- تنزيل حزم التثبيت والإلحاق
- تطبيق حزمة التثبيت
- اتبع خطوات الإلحاق للأداة المقابلة

**Windows Server Semi-Annual Enterprise Channel وWindows Server 2019**:

- تنزيل حزمة الإلحاق
- اتبع خطوات الإلحاق للأداة المقابلة

>[!IMPORTANT]
>لكي تكون مؤهلا لشراء Microsoft Defender لنقطة النهاية Server SKU، يجب أن تكون قد اشتريت بالفعل ما لا يقل عن أي مما يلي، Windows E5/A5 أو Microsoft 365 E5/A5 أو الأمان في Microsoft 365 E5 تراخيص الاشتراك.  لمزيد من المعلومات حول الترخيص، راجع [شروط المنتج](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).

### <a name="new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution"></a>وظائف Windows Server 2012 R2 و2016 الجديدة في الحل الموحد الحديث

يتطلب التنفيذ السابق لتهيئة Windows Server 2012 R2 وWindows Server 2016 استخدام عامل مراقبة Microsoft (MMA).

تسهل حزمة الحلول الموحدة الجديدة إلحاق الخوادم عن طريق إزالة التبعيات وخطوات التثبيت. بالإضافة إلى ذلك، تأتي حزمة الحلول الموحدة هذه مع التحسينات الرئيسية التالية:

- [برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) مع [حماية الجيل التالي](/microsoft-365/security/defender-endpoint/next-generation-protection) ل Windows Server 2012 R2
- [قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- [حماية الشبكة](/microsoft-365/security/defender-endpoint/network-protection)
- [الوصول إلى المجلد الذي يتم التحكم فيه](/microsoft-365/security/defender-endpoint/controlled-folders)
- [حظر التطبيق غير المرغوب فيه (PUA)](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [قدرات الكشف المحسنة](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
- [قدرات الاستجابة الموسعة](/microsoft-365/security/defender-endpoint/respond-machine-alerts) على الأجهزة [والملفات](/microsoft-365/security/defender-endpoint/respond-file-alerts)
- [EDR في وضع الحظر](/microsoft-365/security/defender-endpoint/edr-in-block-mode)
- [الاستجابة المباشرة](/microsoft-365/security/defender-endpoint/live-response)
- [التحقيق التلقائي والاستجابة (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations)
- [الحماية من العبث بالبيانات](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection)

استنادا إلى الخادم الذي تقوم بإلحاقه، يقوم الحل الموحد بتثبيت برنامج الحماية من الفيروسات من Microsoft Defender و/أو أداة استشعار EDR. يشير الجدول التالي إلى المكون المثبت وما هو مضمن بشكل افتراضي.

|إصدار الخادم|AV|يدر|
|----|----|----|
|Windows Server 2012 R2 SP1|![نعم.](images/svg/check-yes.svg)|![نعم.](images/svg/check-yes.svg)|
|Windows Server 2016‏|مضمن|![نعم.](images/svg/check-yes.svg)|
|Windows Server 2019 أو إصدار أحدث|مضمن|مضمن|

إذا كنت قد قمت مسبقا بإلحاق الخوادم باستخدام MMA، فاتبع الإرشادات المتوفرة في [ترحيل الخادم](server-migration.md) للرحل إلى الحل الجديد.

#### <a name="known-issues-and-limitations-in-the-new-unified-solution-package-for-windows-server-2012-r2-and-2016"></a>المشاكل والقيود المعروفة في حزمة الحلول الموحدة الجديدة ل Windows Server 2012 R2 و2016

تنطبق التفاصيل التالية على حزمة الحلول الموحدة الجديدة ل Windows Server 2012 R2 و2016:

- تأكد من تلبية متطلبات الاتصال كما هو محدد في [تمكين الوصول إلى عناوين URL للخدمة Microsoft Defender لنقطة النهاية في الخادم الوكيل](/microsoft-365/security/defender-endpoint/configure-proxy-internet?enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). وهي مكافئة لتلك الخاصة ب Windows Server 2019.
- لقد حددنا مشكلة في اتصال Windows Server 2012 R2 بالسحابة عند استخدام بيانات تتبع الاستخدام الثابتةProxyServer **ولا** يمكن الوصول إلى عناوين URL لقائمة إبطال الشهادات (CRL) من سياق حساب SYSTEM. التخفيف الفوري هو إما استخدام خيار وكيل بديل ("على مستوى النظام") يوفر مثل هذا الاتصال، أو تكوين نفس الوكيل عبر إعداد WinInet على سياق حساب SYSTEM.
بدلا من ذلك، استخدم الإرشادات المتوفرة في [الحل البديل لمشكلة معروفة في TelemetryProxyServer على الأجهزة غير المتصلة](#workaround-for-a-known-issue-with-telemetryproxyserver-on-disconnected-machines) لتثبيت شهادة كحل بديل.
- في السابق، كان استخدام عامل مراقبة Microsoft (MMA) على Windows Server 2016 وما يلي يسمح لبوابة OMS / Log Analytics بتوفير الاتصال بخدمات سحابة Defender. الحل الجديد، مثل Microsoft Defender لنقطة النهاية على Windows Server 2019 وWindows Server 2022 Windows 10، لا يدعم هذه البوابة.
- على Windows Server 2016، تحقق من تثبيت برنامج الحماية من الفيروسات من Microsoft Defender، وأنه نشط ومحدث. يمكنك تنزيل أحدث إصدار من النظام الأساسي وتثبيته باستخدام Windows Update. بدلا من ذلك، قم بتنزيل حزمة التحديث يدويا من [كتالوج تحديث Microsoft](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) أو من [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).
- على Windows Server 2012 R2، لا توجد واجهة مستخدم لبرنامج الحماية من الفيروسات من Microsoft Defender. بالإضافة إلى ذلك، تسمح واجهة المستخدم على Windows Server 2016 فقط بالعمليات الأساسية. لتنفيذ العمليات على جهاز محليا، راجع [إدارة Microsoft Defender لنقطة النهاية باستخدام PowerShell وWMI MPCmdRun.exe](/microsoft-365/security/defender-endpoint/manage-mde-post-migration-other-tools). ونتيجة لذلك، قد لا تعمل الميزات التي تعتمد بشكل خاص على تفاعل المستخدم، مثل المكان الذي تتم مطالبة المستخدم فيه لاتخاذ قرار أو تنفيذ مهمة معينة، كما هو متوقع. يوصى بتعطيل واجهة المستخدم أو عدم تمكينها ولا يتطلب تفاعل المستخدم على أي خادم مدار لأنه قد يؤثر على إمكانية الحماية.
- لا تتوفر جميع قواعد تقليل الأجزاء المعرضة للهجوم على جميع أنظمة التشغيل. راجع [قواعد تقليل الأجزاء المعرضة للهجوم (ASR](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)).
- لتمكين [Network Protection](/microsoft-365/security/defender-endpoint/network-protection)، يلزم تكوين إضافي:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

  بالإضافة إلى ذلك، على الأجهزة التي تحتوي على كمية كبيرة من نسبة استخدام الشبكة، يوصى بشدة باختبار الأداء في بيئتك قبل تمكين هذه الإمكانية على نطاق واسع. قد تحتاج إلى حساب استهلاك الموارد الإضافية.
- على Windows Server 2012 R2، قد لا يتم ملء أحداث الشبكة في المخطط الزمني. This issue requires a Windows Update released as part of the [October 12, 2021 monthly rollup (KB5006714)](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e).
- ترقيات نظام التشغيل غير معتمدة. قم بإلغاء التثبيت بعد ذلك قبل الترقية.
- الاستثناءات التلقائية **لأدوار الخادم** غير معتمدة على Windows Server 2012 R2؛ ومع ذلك، فإن الاستثناءات المضمنة لملفات نظام التشغيل هي. لمزيد من المعلومات حول إضافة استثناءات، راجع [توصيات فحص الفيروسات لأجهزة كمبيوتر المؤسسة التي تعمل حاليا بإصدارات مدعومة من Windows](https://support.microsoft.com/topic/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows-kb822158-c067a732-f24a-9079-d240-3733e39b40bc).
- على الأجهزة التي تمت ترقيتها من الحل السابق المستند إلى MMA ومستشعر EDR هو إصدار (معاينة) أقدم من 10.8047.22439.1056، قد يؤدي إلغاء تثبيت والعودة إلى الحل المستند إلى MMA إلى حدوث أعطال. إذا كنت تستخدم إصدار المعاينة هذا، فالرجاء التحديث باستخدام KB5005292.
- لنشر الحل الجديد وإلحاقه باستخدام Microsoft إدارة نقاط النهاية، يتطلب هذا حاليا إنشاء حزمة. لمزيد من المعلومات حول كيفية نشر البرامج والبرامج النصية في Configuration Manager، راجع [الحزم والبرامج في Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs). MECM 2107 مع مجموعة الإصلاح العاجل أو الأحدث مطلوب لدعم إدارة تكوين النهج باستخدام عقدة Endpoint Protection.

## <a name="workaround-for-a-known-issue-with-telemetryproxyserver-on-disconnected-machines"></a>حل بديل لمشكلة معروفة في TelemetryProxyServer على الأجهزة غير المتصلة

وصف المشكلة: عند استخدام إعداد TelemetryProxyServer لتحديد وكيل لاستخدامه من قبل مكون EDR Microsoft Defender لنقطة النهاية، على الأجهزة التي ليس لديها طريقة أخرى للوصول إلى عنوان URL لقائمة إبطال الشهادة (CRL)، ستتسبب الشهادة المتوسطة المفقودة في عدم اتصال مستشعر EDR بنجاح بخدمة السحابة.

السيناريو المتأثر: -Microsoft Defender لنقطة النهاية مع رقم إصدار Sense 10.8048.22439.1065 أو إصدارات المعاينة السابقة التي تعمل على Windows Server 2012 R2 -باستخدام تكوين وكيل TelemetryProxyServer؛ لا تتأثر الأساليب الأخرى

الحل:
1. تأكد من تشغيل الجهاز للإصدار 10.8048.22439.1065 أو إصدار أحدث إما عن طريق التثبيت باستخدام أحدث حزمة متوفرة من صفحة الإلحاق، أو عن طريق تطبيق KB5005292.
2. تنزيل الشهادة وإلغاء ضغطها من https://github.com/microsoft/mdefordownlevelserver/blob/main/InterCA.zip
3. استيراد الشهادة إلى مخزن "المراجع المصدقة المتوسطة" الموثوق به على الكمبيوتر المحلي.
يمكنك استخدام الأمر PowerShell: Import-Certificate -FilePath .\InterCA.cer -CertStoreLocation Cert:\LocalMachine\Ca

## <a name="integration-with-microsoft-defender-for-cloud"></a>التكامل مع Microsoft Defender for Cloud

يتكامل Microsoft Defender لنقطة النهاية بسلاسة مع Microsoft Defender for Cloud. يمكنك إلحاق الخوادم تلقائيا، وظهور الخوادم التي يراقبها Microsoft Defender for Cloud في Defender لنقطة النهاية، وإجراء تحقيقات مفصلة كعميل Microsoft Defender for Cloud. 

لمزيد من المعلومات، راجع [التكامل مع Microsoft Defender for Cloud](azure-server-integration.md). سيتم تعيين التكوين الأولي للخوادم التي تم إلحاقها من خلال Microsoft Defender for Cloud لتشغيل Defender Antivirus في [الوضع السلبي](/defender-endpoint/microsoft-defender-antivirus-compatibility#microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions).

> [!NOTE]
> - تم توسيع التكامل بين Microsoft Defender للخوادم Microsoft Defender لنقطة النهاية لدعم Windows Server 2022 [وWindows Server 2019 وWindows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)
> - تم تعطيل مراقبة نقطة نهاية الخادم باستخدام هذا التكامل لعملاء Office 365 GCC.

## <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 وWindows Server 2016

### <a name="prerequisites"></a>المتطلبات الأساسية

#### <a name="prerequisites-for-windows-server-2012-r2"></a>المتطلبات الأساسية ل Windows Server 2012 R2

إذا قمت بتحديث أجهزتك بالكامل بأحدث [حزمة مجموعة شهرية](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e) ، **فلا توجد متطلبات** أساسية إضافية.

ستتحقق حزمة المثبت مما إذا كانت المكونات التالية قد تم تثبيتها بالفعل عبر تحديث:

- [تحديث لتجربة العملاء وبيانات تتبع الاستخدام التشخيصية](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [تحديث لوقت تشغيل Universal C في Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

#### <a name="prerequisites-for-windows-server-2016"></a>المتطلبات الأساسية ل Windows Server 2016

- يجب تثبيت تحديث مكدس الخدمة (SSU) من 14 سبتمبر 2021 أو الإصدارات الأحدث.
- يجب تثبيت التحديث التراكمي الأخير (LCU) من 20 سبتمبر 2018 أو أحدث.  يوصى بتثبيت أحدث SSU وLCU المتوفرة على الخادم.  - يجب تمكين/تثبيت ميزة برنامج الحماية من الفيروسات من Microsoft Defender وتحديثها. يمكنك تنزيل أحدث إصدار من النظام الأساسي وتثبيته باستخدام Windows Update. بدلا من ذلك، قم بتنزيل حزمة التحديث يدويا من [كتالوج تحديث Microsoft](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) أو من [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).

#### <a name="prerequisites-for-running-with-third-party-security-solutions"></a>المتطلبات الأساسية للعمل باستخدام حلول أمان الجهات الخارجية

إذا كنت تنوي استخدام حل مكافحة البرامج الضارة التابع لجهة خارجية، فستحتاج إلى تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. يجب أن تتذكر التعيين إلى الوضع السلبي أثناء عملية التثبيت والإلحاق.

> [!NOTE]
> إذا كنت تقوم بتثبيت Microsoft Defender لنقطة النهاية على الخوادم باستخدام McAfee Endpoint Security (ENS) أو VirusScan Enterprise (VSE)، فقد تحتاج إلى تحديث إصدار النظام الأساسي McAfee لضمان عدم إزالة برنامج الحماية من الفيروسات من Microsoft Defender أو تعطيله. لمزيد من المعلومات بما في ذلك أرقام الإصدارات المحددة المطلوبة، راجع [مقالة McAfee Knowledge Center](https://kc.mcafee.com/corporate/index?page=content&id=KB88214).

#### <a name="update-package-for-microsoft-defender-for-endpoint-on-windows-server-2012-r2-and-2016"></a>حزمة التحديث Microsoft Defender لنقطة النهاية على Windows Server 2012 R2 و2016

لتلقي تحسينات وإصلاحات منتظمة للمنتج لمكون EDR Sensor، تأكد من تطبيق أو الموافقة على Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277). بالإضافة إلى ذلك، للحفاظ على تحديث مكونات الحماية، راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

إذا كنت تستخدم خادم Windows Server Update Services (WSUS) و/أو نقطة نهاية Microsoft Configuration Manager، فهذا التحديث الجديد "Microsoft Defender لنقطة النهاية لأداة استشعار EDR" متوفر ضمن الفئة " Microsoft Defender لنقطة النهاية".

### <a name="onboarding-steps-summary"></a>ملخص خطوات الإلحاق

- الخطوة 1: [تنزيل حزم التثبيت والإلحاق](#step-1-download-installation-and-onboarding-packages)
- الخطوة 2: [تطبيق حزمة التثبيت والإلحاق](#step-2-apply-the-installation-and-onboarding-package)
- الخطوة 3: [إكمال خطوات الإلحاق](#step-3-complete-the-onboarding-steps)

### <a name="step-1-download-installation-and-onboarding-packages"></a>الخطوة 1: تنزيل حزم التثبيت والإلحاق

ستحتاج إلى تنزيل حزم **التثبيت** **والإلحاق** من المدخل.

> [!NOTE]
> يتم تحديث حزمة التثبيت شهريا. تأكد من تنزيل أحدث حزمة قبل الاستخدام.

> [!div class="mx-imgBorder"]
> ![صورة لوحة معلومات الإلحاق](images/install-agent-onboard.png)

   > [!NOTE]
   > على Windows Server 2012R2، سيتم تثبيت برنامج الحماية من الفيروسات من Microsoft Defender بواسطة حزمة التثبيت وسيكون نشطا ما لم تقم بتعيينه إلى الوضع السلبي. في Windows Server 2016، يجب تثبيت برنامج الحماية من الفيروسات من Microsoft Defender كميزة (راجع [التبديل إلى MDE](/microsoft-365/security/defender-endpoint/switch-to-mde-phase-2#re-enable-microsoft-defender-antivirus-on-windows-server-2016)) أولا وتحديثه بالكامل قبل متابعة التثبيت.
   >
   > إذا كنت تقوم بتشغيل حل مكافحة البرامج الضارة غير التابع ل Microsoft، فتأكد من إضافة استثناءات لبرنامج الحماية من الفيروسات من Microsoft Defender ([من هذه القائمة من عمليات Microsoft Defender على علامة التبويب "عمليات Defender](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)") إلى الحل غير التابع ل Microsoft قبل التثبيت.  يوصى أيضا بإضافة حلول أمان غير أمنية من Microsoft إلى قائمة استبعاد Defender Antivirus.

تحتوي **حزمة التثبيت** على ملف MSI يقوم بتثبيت عامل Microsoft Defender لنقطة النهاية.

تحتوي **حزمة الإلحاق على** الملفات التالية:

- `OptionalParamsPolicy` - يحتوي على الإعداد الذي يمكن مجموعة العينة
- `WindowsDefenderATPOnboardingScript.cmd` - يحتوي على البرنامج النصي الإلحاقي

استخدم الخطوات التالية لتنزيل الحزم:

1. في Microsoft 365 Defender، انتقل إلى **الإعدادات > إدارة الجهاز > الإلحاق**.

2. حدد **Windows Server 2012 R2 و2016**.

3. حدد **تنزيل حزمة التثبيت** واحفظ ملف .msi.

4. حدد **تنزيل حزمة الإلحاق** واحفظ ملف .zip.

5. تثبيت حزمة التثبيت باستخدام أي من الخيارات لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender. يتطلب التثبيت أذونات إدارية.

### <a name="step-2-apply-the-installation-and-onboarding-package"></a>الخطوة 2: تطبيق حزمة التثبيت والإلحاق

في هذه الخطوة، ستقوم بتثبيت مكونات الوقاية والكشف المطلوبة قبل إلحاق جهازك ببيئة السحابة Microsoft Defender لنقطة النهاية، لإعداد الجهاز للإلحاق. تأكد من استيفاء جميع [المتطلبات الأساسية](#prerequisites) .

   > [!NOTE]
   > سيتم تثبيت برنامج الحماية من الفيروسات من Microsoft Defender وسيكون نشطا ما لم تقم بتعيينه إلى الوضع السلبي.

#### <a name="options-to-install-the-microsoft-defender-for-endpoint-packages"></a>خيارات لتثبيت حزم Microsoft Defender لنقطة النهاية

في القسم السابق، قمت بتنزيل حزمة تثبيت. تحتوي حزمة التثبيت على المثبت لكافة مكونات Microsoft Defender لنقطة النهاية.

يمكنك استخدام أي من الخيارات التالية لتثبيت العامل:

- [التثبيت باستخدام سطر الأوامر](#install-microsoft-defender-for-endpoint-using-the-command-line)
- [التثبيت باستخدام برنامج نصي](#install-microsoft-defender-for-endpoint-using-a-script)
- [تطبيق حزم التثبيت والإلحاق باستخدام نهج المجموعة](#apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy)

##### <a name="install-microsoft-defender-for-endpoint-using-the-command-line"></a>تثبيت Microsoft Defender لنقطة النهاية باستخدام سطر الأوامر

استخدم حزمة التثبيت من الخطوة السابقة لتثبيت Microsoft Defender لنقطة النهاية.

قم بتشغيل الأمر التالي لتثبيت Microsoft Defender لنقطة النهاية:

```console
Msiexec /i md4ws.msi /quiet
```

لإلغاء التثبيت، تأكد من إلغاء إلحاق الجهاز أولا باستخدام البرنامج النصي المناسب لإلغاء الإلحاق. ثم استخدم لوحة التحكم \> البرامج \> والميزات لتنفيذ إلغاء التثبيت.

بدلا من ذلك، قم بتشغيل أمر إلغاء التثبيت التالي لإلغاء تثبيت Microsoft Defender لنقطة النهاية:

```console
Msiexec /x md4ws.msi /quiet
```

يجب استخدام نفس الحزمة التي استخدمتها للتثبيت حتى ينجح الأمر أعلاه.

يمنع `/quiet` مفتاح التبديل كافة الإعلامات.

> [!NOTE]
> لا ينتقل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا إلى الوضع السلبي. يمكنك اختيار تعيين برنامج الحماية من الفيروسات من Microsoft Defender لتشغيله في الوضع السلبي إذا كنت تقوم بتشغيل حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft. بالنسبة إلى عمليات تثبيت سطر الأوامر، يقوم الخيار الاختياري `FORCEPASSIVEMODE=1` بتعيين مكون برنامج الحماية من الفيروسات من Microsoft Defender على الفور إلى الوضع السلبي لتجنب التداخل. بعد ذلك، لضمان بقاء Defender Antivirus في الوضع السلبي بعد الإعداد لدعم قدرات مثل EDR Block، قم بتعيين مفتاح التسجيل "ForceDefenderPassiveMode".

يوفر دعم Windows Server رؤية أعمق لأنشطة الخادم، وتغطية الكشف عن هجمات النواة والذاكرة، وتمكين إجراءات الاستجابة.

##### <a name="install-microsoft-defender-for-endpoint-using-a-script"></a>تثبيت Microsoft Defender لنقطة النهاية باستخدام برنامج نصي

يمكنك استخدام [البرنامج النصي المثبت](server-migration.md#installer-script) للمساعدة في أتمتة التثبيت وإلغاء التثبيت والإلحاق. لمزيد من المعلومات، راجع الإرشادات الواردة في القسم التالي لاستخدام البرنامج النصي مع نهج المجموعة.

##### <a name="apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy"></a>تطبيق حزم التثبيت والإلحاق Microsoft Defender لنقطة النهاية باستخدام نهج المجموعة

1. إنشاء نهج مجموعة: <br> افتح [وحدة تحكم إدارة نهج المجموعة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC)، وانقر بزر الماوس الأيمن **فوق نهج المجموعة العناصر** التي تريد تكوينها وانقر فوق **"جديد**". أدخل اسم عنصر نهج المجموعة الجديد في مربع الحوار المعروض وانقر فوق **"موافق**".

2. افتح [وحدة تحكم إدارة نهج المجموعة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC)، وانقر بزر الماوس الأيمن فوق الكائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **"تحرير**".

3. في **نهج المجموعة Management Editor**، انتقل إلى **تكوين الكمبيوتر**، ثم **التفضيلات**، ثم **إعدادات لوحة التحكم**.

4. انقر بزر الماوس الأيمن فوق **المهام المجدولة**، وأشر إلى **"جديد**"، ثم انقر فوق **"مهمة فورية" (Windows 7 على الأقل).**

5. في النافذة **"مهمة** " التي يتم فتحها، انتقل إلى علامة التبويب **"عام** ". ضمن **خيارات الأمان** ، انقر فوق **"تغيير المستخدم أو المجموعة** " واكتب "نظام" ثم انقر فوق **"التحقق من الأسماء** " ثم " **موافق**". يظهر NT AUTHORITY\SYSTEM كحساب المستخدم الذي سيتم تشغيل المهمة عليه.

6. حدد **"تشغيل" سواء تم تسجيل دخول المستخدم أم لا** وحدد خانة الاختيار **"تشغيل بامتيازات أعلى** ".

7. في حقل "الاسم"، اكتب اسما مناسبا للمهمة المجدولة (على سبيل المثال، Defender for Endpoint Deployment).

8. انتقل إلى علامة التبويب **"إجراءات** " وحدد **"جديد"...** تأكد **من تحديد "بدء برنامج** " في الحقل **"إجراء** ". يعالج [البرنامج النصي المثبت](server-migration.md#installer-script) التثبيت، وينفذ على الفور خطوة الإلحاق بعد اكتمال التثبيت. حدد *C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe* ثم قم بتوفير الوسيطات:

    ```console
     -ExecutionPolicy RemoteSigned \\servername-or-dfs-space\share-name\install.ps1 -OnboardingScript \\servername-or-dfs-space\share-name\windowsdefenderatponboardingscript.cmd
    ```

    > [!NOTE]

    > إعداد نهج التنفيذ الموصى به هو `Allsigned`. يتطلب هذا استيراد شهادة توقيع البرنامج النصي إلى مخزن الناشرين الموثوق بهم للكمبيوتر المحلي إذا كان البرنامج النصي قيد التشغيل ك SYSTEM على نقطة النهاية.

    استبدل \\servername-or-dfs-space\share-name بمسار UNC، باستخدام اسم المجال المؤهل بالكامل لخادم الملفات (FQDN)، لملف *install.ps1* المشترك. يجب وضع حزمة المثبت md4ws.msi في نفس الدليل.  تأكد من أن أذونات مسار UNC تسمح بالوصول للكتابة إلى حساب الكمبيوتر الذي يقوم بتثبيت الحزمة، لدعم إنشاء ملفات السجل. إذا كنت ترغب في تعطيل إنشاء ملفات السجل (غير مستحسن)، يمكنك استخدام معلمات -noETL -noETW.

    بالنسبة للسيناريوهات التي تريد أن يتعايش فيها برنامج الحماية من الفيروسات من Microsoft Defender مع حلول مكافحة البرامج الضارة غير الخاصة ب Microsoft، أضف المعلمة $Passive لتعيين الوضع السلبي أثناء التثبيت.

9. حدد **"موافق** " وأغلق أي نوافذ GPMC مفتوحة.

10. لربط عنصر نهج المجموعة بوحدة تنظيم (OU)، انقر بزر الماوس الأيمن وحدد **"ربط عنصر نهج المجموعة" الموجود**. في مربع الحوار الذي يتم عرضه، حدد العنصر نهج المجموعة الذي تريد ربطه. انقر فوق **موافق**.

للحصول على إعدادات تكوين إضافية، راجع [تكوين إعدادات مجموعة العينة وإعدادات](configure-endpoints-gp.md#configure-sample-collection-settings) [التكوين المستحسنة الأخرى](configure-endpoints-gp.md#other-recommended-configuration-settings).

### <a name="step-3-complete-the-onboarding-steps"></a>الخطوة 3: إكمال خطوات الإلحاق

لا تنطبق الخطوات التالية إلا إذا كنت تستخدم حلا تابعا لجهة خارجية لمكافحة البرامج الضارة. ستحتاج إلى تطبيق إعداد وضع Microsoft Defender Antivirus الخامل التالي. تحقق من تكوينه بشكل صحيح:

1. تعيين إدخال التسجيل التالي:
    - مسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
    - الاسم: `ForceDefenderPassiveMode`
    - نوع: `REG_DWORD`
    - قيمه: `1`

   :::image type="content" source="images/atp-verify-passive-mode.png" alt-text="نتيجة التحقق من الوضع الخامل" lightbox="images/atp-verify-passive-mode.png":::

> [!IMPORTANT]
>
> - حزمة الإلحاق ل Windows Server 2012 R2 و2016 و2019 و2022 من خلال Microsoft إدارة نقاط النهاية يتم إرسالها حاليا كنص نصي. لمزيد من المعلومات حول كيفية نشر البرامج والبرامج النصية في Configuration Manager، راجع [الحزم والبرامج في Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs).
> - البرنامج النصي المحلي مناسب لإثبات المبدأ ولكن لا ينبغي استخدامه لتوزيع الإنتاج. لنشر الإنتاج، نوصي باستخدام نهج المجموعة أو Configuration Manager نقطة نهاية Microsoft.

## <a name="windows-server-semi-annual-enterprise-channel-sac-windows-server-2019-and-windows-server-2022"></a>Windows Server Semi-Annual Enterprise Channel (SAC) وWindows Server 2019 وWindows Server 2022

### <a name="download-package"></a>حزمة التنزيل

1. في Microsoft 365 Defender، انتقل إلى **الإعدادات > إدارة الجهاز > الإلحاق**.

2. حدد **Windows Server 1803 و2019**.

3. حدد **حزمة التنزيل**. احفظه WindowsDefenderATPOnboardingPackage.zip.

4. اتبع الخطوات [الواردة في القسم "إكمال خطوات الإلحاق](#step-3-complete-the-onboarding-steps) ".

## <a name="verify-the-onboarding-and-installation"></a>التحقق من الإلحاق والتثبيت

تحقق من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender Microsoft Defender لنقطة النهاية.

## <a name="run-a-detection-test-to-verify-onboarding"></a>تشغيل اختبار الكشف للتحقق من الإلحاق

بعد إلحاق الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أن الجهاز تم إلحاقه بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](run-detection-test.md).

> [!NOTE]
> تشغيل برنامج الحماية من الفيروسات من Microsoft Defender غير مطلوب ولكنه مستحسن. إذا كان منتج مورد الحماية من الفيروسات آخر هو حل حماية نقطة النهاية الأساسي، يمكنك تشغيل Defender Antivirus في الوضع السلبي. يمكنك فقط تأكيد تشغيل الوضع السلبي بعد التحقق من تشغيل أداة استشعار Microsoft Defender لنقطة النهاية (SENSE).

1. قم بتشغيل الأمر التالي للتحقق من تثبيت برنامج الحماية من الفيروسات من Microsoft Defender:

    > [!NOTE]
    > خطوة التحقق هذه مطلوبة فقط إذا كنت تستخدم برنامج الحماية من الفيروسات من Microsoft Defender كحل نشط لمكافحة البرامج الضارة.

    ```DOS
    sc.exe query Windefend
    ```

    إذا كانت النتيجة هي "الخدمة المحددة غير موجودة كخدمة مثبتة"، فستحتاج إلى تثبيت برنامج الحماية من الفيروسات من Microsoft Defender.

    للحصول على معلومات حول كيفية استخدام نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارته على خوادم Windows، راجع [استخدام إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارته](use-group-policy-microsoft-defender-antivirus.md).

2. قم بتشغيل الأمر التالي للتحقق من تشغيل Microsoft Defender لنقطة النهاية:

    ```DOS
    sc.exe query sense
    ```

    يجب أن تظهر النتيجة أنها قيد التشغيل. إذا واجهت مشاكل في الإلحاق، فراجع [استكشاف أخطاء الإلحاق وإصلاحها](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>تشغيل اختبار الكشف

اتبع الخطوات في [تشغيل اختبار الكشف على جهاز تم إلحاقه حديثا](run-detection-test.md) للتحقق من أن الخادم يقوم بالإبلاغ إلى Defender لخدمة نقطة النهاية.

## <a name="next-steps"></a>الخطوات التالية

بعد إلحاق الأجهزة إلى الخدمة بنجاح، ستحتاج إلى تكوين المكونات الفردية Microsoft Defender لنقطة النهاية. اتبع [أمر الاعتماد](prepare-deployment.md#adoption-order) ليتم إرشاده حول تمكين المكونات المختلفة.

## <a name="offboard-windows-servers"></a>إيقاف تشغيل خوادم Windows

يمكنك إلغاء تشغيل Windows Server 2012 R2 وWindows Server 2016 وWindows Server (SAC) وWindows Server 2019 وإصدار Windows Server 2019 Core بنفس الطريقة المتوفرة لأجهزة العميل Windows 10.

- [إيقاف تشغيل الأجهزة باستخدام نهج المجموعة](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [إيقاف تشغيل الأجهزة باستخدام Configuration Manager](configure-endpoints-sccm.md#offboard-devices-using-configuration-manager)
- [إيقاف تشغيل الأجهزة باستخدام أدوات إدارة الجهاز الأجهزة المحمولة](configure-endpoints-mdm.md#offboard-devices-using-mobile-device-management-tools)
- [إيقاف تشغيل الأجهزة باستخدام برنامج نصي محلي](configure-endpoints-script.md#offboard-devices-using-a-local-script)

بعد إلغاء الإلحاق، يمكنك المتابعة لإلغاء تثبيت حزمة الحلول الموحدة على Windows Server 2012 R2 وWindows Server 2016.

بالنسبة إلى إصدارات خادم Windows الأخرى، لديك خياران لإلغاء تشغيل خوادم Windows من الخدمة:

- إلغاء تثبيت عامل MMA
- إزالة تكوين مساحة عمل Defender لنقطة النهاية

> [!NOTE]
> تنطبق إرشادات إلغاء الإلحاق هذه لإصدارات خادم Windows الأخرى أيضا إذا كنت تقوم بتشغيل Microsoft Defender لنقطة النهاية السابقة ل Windows Server 2016 وWindows Server 2012 R2 التي تتطلب MMA. توجد إرشادات الترحيل إلى الحل الموحد الجديد في [سيناريوهات ترحيل الخادم في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الإصدارات السابقة من Windows](onboard-downlevel.md)
- [إلحاق أجهزة Windows 10](configure-endpoints.md)
- [الأجهزة غير المجهزة Windows](configure-endpoints-non-windows.md)
- [تكوين إعدادات الوكيل والاتصال بالإنترنت](configure-proxy-internet.md)
- [تشغيل اختبار الكشف على جهاز Defender لنقطة النهاية الذي تم إلحاقه حديثا](run-detection-test.md)
- [استكشاف أخطاء إلحاق Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-onboarding.md)
