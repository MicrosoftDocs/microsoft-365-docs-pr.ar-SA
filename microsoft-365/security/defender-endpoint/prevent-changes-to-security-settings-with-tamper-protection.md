---
title: حماية إعدادات الأمان باستخدام الحماية من العبث
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: استخدم الحماية من العبث لمنع التطبيقات الضارة من تغيير إعدادات الأمان المهمة.
keywords: البرامج الضارة، والمدافع، والحماية من الفيروسات، والحماية من العبث
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom:
- nextgen
- admindeeplinkDEFENDER
ms.technology: mde
ms.date: 01/18/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: ef9db769811c3848646c0bf7b8f7755941918362
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/31/2022
ms.locfileid: "63573890"
---
# <a name="protect-security-settings-with-tamper-protection"></a>حماية إعدادات الأمان باستخدام الحماية من العبث

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

تتوفر الحماية من العبث للأجهزة التي تعمل بوا أحد الإصدارات التالية من Windows:

- Windows 10
- Windows 11
- Windows 10 Enterprise جلسات عمل متعددة
- Windows 11 Enterprise جلسات عمل متعددة 
- Windows Server 2019
- Windows Server 2022
- Windows Server، الإصدار 1803 أو الإصدارات الأحدث
- Windows Server 2016‏
- Windows Server 2012 R2

> [!NOTE]
> تتوفر الحماية من Windows Server 2012 R2 للأجهزة المجهزة باستخدام حزمة الحلول الموحدة الحديثة. لمزيد من المعلومات، راجع وظائف جديدة في الحل الموحد الحديث Windows [Server 2012 R2 و2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

## <a name="overview"></a>نظرة عامة

أثناء بعض أنواع الهجمات الإلكترونية، يحاول الجهات غير النادرة تعطيل ميزات الأمان، مثل الحماية من الفيروسات، على الأجهزة. ترغب الجهات الضارة في تعطيل ميزات الأمان للحصول على وصول أسهل إلى بياناتك، أو لتثبيت البرامج الضارة، أو لاستغلال بياناتك وهويتك وأجهزتك. تساعد الحماية من التلاعب في منع حدوث هذه الأنواع من الأشياء.

مع الحماية من العبث، يتم منع التطبيقات الضارة من اتخاذ إجراءات مثل:

- تعطيل الحماية من الفيروسات والتهديدات
- تعطيل الحماية في الوقت الحقيقي
- إيقاف تشغيل مراقبة السلوك
- تعطيل برنامج الحماية من الفيروسات (مثل IOfficeAntivirus (IOAV))
- تعطيل الحماية التي يتم تسليمها عبر السحابة
- إزالة تحديثات المعلومات الأمنية
- تعطيل الإجراءات التلقائية على التهديدات المكتشفة

### <a name="how-it-works"></a>كيفية عمل ذلك

تعمل الحماية من العبث برنامج الحماية من الفيروسات من Microsoft Defender تأمين قيمها الافتراضية الآمنة بشكل أساسي، كما تمنع تغيير إعدادات الأمان من خلال التطبيقات والأساليب مثل:

- تكوين الإعدادات في "محرر السجل" على جهاز Windows
- تغيير الإعدادات من خلال PowerShell cmdlets
- تحرير إعدادات الأمان أو إزالتها من خلال "نهج المجموعة"

لا تمنعك الحماية من العبث من عرض إعدادات الأمان. ولا تؤثر الحماية من العبث على كيفية تسجيل تطبيقات مكافحة الفيروسات غير الخاصة ب Microsoft أمن Windows التطبيق. إذا كانت مؤسستك تستخدم Windows 10 Enterprise E5، لا يمكن للمستخدمين الفرديين تغيير إعداد الحماية من التلاعب؛ وفي هذه الحالات، يدير فريق الأمان الحماية من العبث.

### <a name="what-do-you-want-to-do"></a>ماذا تريد أن تفعل؟

<br/><br/>

|لتنفيذ هذه المهمة...|راجع هذا القسم...|
|---|---|
|إدارة الحماية من العبث عبر المستأجر <p> استخدام مدخل Microsoft 365 Defender تشغيل الحماية من التلاعب أو إيقاف تشغيلها|[إدارة الحماية من العبث لمنظمتك باستخدام Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|ضبط إعدادات الحماية من التلاعب في مؤسستك <p> استخدم Intune (إدارة نقاط النهاية من Microsoft) ل تشغيل الحماية من العبث أو إيقاف تشغيلها. يمكنك تكوين الحماية من العبث لبعض المستخدمين أو جميع المستخدمين باستخدام هذه الطريقة.|[إدارة الحماية من العبث لمنظمتك باستخدام إدارة نقاط النهاية من Microsoft](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|تشغيل الحماية من العبث (أو إيقاف تشغيلها) لمنظمتك باستخدام "إدارة التكوين"|[إدارة الحماية من العبث لمنظمتك باستخدام إرفاق المستأجر مع "إدارة التكوين"، الإصدار 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|تشغيل الحماية من العبث (أو إيقاف تشغيلها) لجهاز فردي|[إدارة الحماية من العبث على جهاز فردي](#manage-tamper-protection-on-an-individual-device)|
|عرض تفاصيل حول محاولات التلاعب على الأجهزة|[عرض معلومات حول محاولات التلاعب](#view-information-about-tampering-attempts)|
|مراجعة توصيات الأمان|[مراجعة توصيات الأمان](#review-your-security-recommendations)|
|مراجعة قائمة الأسئلة المتكررة (الأسئلة المتكررة)|[استعراض الأسئلة المفهمة](#view-information-about-tampering-attempts)|

استنادا إلى الأسلوب أو أداة الإدارة التي تستخدمها لتمكين الحماية من العبث، قد يكون هناك تبعية للحماية التي يتم تسليمها من السحابة.

يوفر الجدول التالي تفاصيل حول الأساليب والأدوات والتبعيات.

<br/><br/>

|كيفية تمكين الحماية من التلاعب|الاعتماد على الحماية التي يتم تسليمها من السحابة (MAPS)|
|---|---|
|Microsoft Intune|لا|
|Microsoft Endpoint Configuration Manager + مستأجر إرفاق|لا|
|Microsoft 365 Defender المدخل ([https://security.microsoft.com](https://security.microsoft.com))|نعم|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>إدارة الحماية من العبث لمنظمتك باستخدام Microsoft 365 Defender الإلكتروني

يمكن تشغيل الحماية من العبث أو إيقاف تشغيلها للمستأجر باستخدام Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). فيما يلي بعض النقاط التي يجب تذكرها:

- حاليا، يكون خيار إدارة الحماية من العبث في Microsoft 365 Defender قيد الإعداد بشكل افتراضي للنشرات الجديدة. بالنسبة إلى عمليات النشر الموجودة، تتوفر الحماية من التلاعب على أساس الاشتراك. ل الاشتراك، في مدخل Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">،</a> **اختر الإعدادات** \> **نقاط** \> النهاية **المتقدمة** \> الحماية من **العبث**.

- عند استخدام مدخل Microsoft 365 Defender لإدارة الحماية من العبث، لن تحتاج إلى استخدام Intune أو أسلوب إرفاق المستأجر.

- عند إدارة الحماية من العبث في مدخل Microsoft 365 Defender، يتم تطبيق الإعداد على نطاق المستأجر، مما يؤثر على جميع أجهزتك التي تعمل Windows 10، Windows 10 Enterprise جلسات عمل متعددة، Windows 11، Windows 11 Enterprise  جلسات عمل متعددة Windows Server 2012 R2 أو Windows Server 2016 أو Windows Server 2019 أو Windows Server 2022. لضبط الحماية من التلاعب (مثل حماية العبث لبعض الأجهزة ولكن مع إيقاف تشغيلها للأجهزة الأخرى)، استخدم إما إدارة نقاط النهاية من Microsoft [](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) أو إدارة التكوين مع [إرفاق المستأجر](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006).

- إذا كانت لديك بيئة مختلطة، فإن إعدادات الحماية من التلاعب التي تم تكوينها في Intune تكون لها الأسبقية على الإعدادات التي تم تكوينها في Microsoft 365 Defender المدخل.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>متطلبات إدارة الحماية من العبث في مدخل Microsoft 365 Defender

- يجب أن يكون لديك [الأذونات](/microsoft-365/security/defender-endpoint/assign-portal-access) المناسبة المعينة، مثل المسؤول العام أو مسؤول الأمان أو عمليات الأمان.

- يجب Windows تشغيل أحد الإصدارات التالية من Windows:
  
  - Windows 10
  - Windows 11
  - Windows 10 Enterprise جلسات عمل متعددة
  - Windows 11 Enterprise جلسات عمل متعددة 
  - Windows Server 2019
  - Windows Server 2022
  - Windows Server، الإصدار 1803 أو الإصدارات الأحدث
  - Windows Server 2016‏
  - Windows Server 2012 R2

لمزيد من المعلومات حول الإصدارات، راجع Windows 10 [الإصدار.](/windows/release-health/release-information)

- يجب أن تكون أجهزتك [مجهزه في Microsoft Defender ل Endpoint](/microsoft-365/security/defender-endpoint/onboarding).

- يجب أن تستخدم أجهزتك إصدار النظام الأساسي لمكافحة البرامج الضارة `4.18.2010.7` (أو الإصدارات الأحدث) ونسخة مشغل مكافحة البرامج الضارة `1.1.17600.5` (أو الإصدارات الأحدث). ([إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).)

- [يجب تشغيل الحماية التي يتم](enable-cloud-protection-microsoft-defender-antivirus.md) تسليمها من السحابة.

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>تشغيل الحماية من العبث (أو إيقاف تشغيلها) في Microsoft 365 Defender المدخل

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="تشغيل الحماية من العبث في Microsoft 365 Defender المدخل.":::

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. اختر **الإعدادات** \> **نقاط النهاية**.

3. انتقل إلى **الميزات** \> **المتقدمة العامة**، ثم قم تشغيل الحماية من العبث.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>إدارة الحماية من العبث لمنظمتك باستخدام إدارة نقاط النهاية من Microsoft

إذا كانت مؤسستك تستخدم إدارة نقاط النهاية من Microsoft (MEM) يمكنك تشغيل الحماية من العبث (أو إيقاف تشغيلها) لمنظمتك في إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). استخدم Intune عندما تريد ضبط إعدادات الحماية من التلاعب. على سبيل المثال، إذا كنت تريد تمكين الحماية من العبث على بعض الأجهزة، وليس كلها، فاستخدم Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>متطلبات إدارة الحماية من العبث في إدارة نقاط النهاية

- يجب أن تكون أجهزتك [مجهزه في Microsoft Defender ل Endpoint](/microsoft-365/security/defender-endpoint/onboarding).

- يجب أن يكون لديك [الأذونات](/microsoft-365/security/defender-endpoint/assign-portal-access) المناسبة المعينة، مثل المسؤول العام أو مسؤول الأمان أو عمليات الأمان.

- تستخدم مؤسستك إدارة نقاط النهاية من Microsoft [لإدارة الأجهزة](/mem/endpoint-manager-getting-started). (إدارة نقاط النهاية من Microsoft (MEM) مطلوبة؛ يتم تضمين MEM في Microsoft 365 E3/E5، Enterprise Mobility + Security E3/E5، Microsoft 365 Business Premium، Microsoft 365 F1/F3، Microsoft 365  Government G3/G5، والتراخيص التعليمية المناظرة.)

- يجب Windows تشغيل الأجهزة Windows 11 أو Windows 10 [1709](/windows/release-health/status-windows-10-1709) أو [1803](/windows/release-health/status-windows-10-1803) أو [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) أو أي وقت لاحق. (لمزيد من المعلومات حول الإصدارات، [راجع Windows 10 الإصدار](/windows/release-health/release-information).)

- يجب أن تستخدم Windows مع [تحديث](https://www.microsoft.com/wdsi/definitions) معلومات الأمان إلى الإصدار 1.287.60.0 (أو الإصدارات الأحدث).

- يجب أن تستخدم أجهزتك إصدار النظام الأساسي لمكافحة البرامج الضارة 4.18.1906.3 (أو الإصدارات الأحدث) ونسخة مشغل مكافحة البرامج الضارة `1.1.15500.X` (أو الإصدارات الأحدث). ([إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).)

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>تشغيل الحماية من العبث (أو إيقاف تشغيلها) في إدارة نقاط النهاية من Microsoft

![تشغيل الحماية من العبث باستخدام إدارة نقاط النهاية.](images/turnontamperprotectinmem.png)

1. في مركز [إدارة نقاط النهاية من Microsoft،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى برنامج الحماية من الفيروسات **لأمن** \> نقطة **النهاية، ثم** اختر **+ إنشاء نهج**.

   - في قائمة **النظام** الأساسي، حدد Windows 10 **واللاحقة**.
   - في قائمة **ملف التعريف**، حدد أمن Windows **المستخدم**.

2. إنشاء ملف تعريف يتضمن الإعداد التالي:

    - **تمكين الحماية من العبث لمنع تعطيل Microsoft Defender: تمكين**

3. تعيين ملف التعريف إلى مجموعة واحدة أو أكثر.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>إدارة الحماية من العبث لمنظمتك باستخدام "إدارة التكوين"، الإصدار 2006

إذا كنت تستخدم الإصدار [2006 من "](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006)إدارة التكوين"، يمكنك إدارة إعدادات الحماية من العبث على Windows 10 و Windows 10 Enterprise متعدد جلسات العمل و Windows 11 و Windows 11 Enterprise متعدد جلسات العمل و Windows Server 2012 R2 و Windows  Server 2016 و Windows Server 2019 و Windows Server 2022 باستخدام طريقة تسمى *إرفاق المستأجر*. يمكنك إرفاق المستأجر من مزامنة أجهزة إدارة التكوين المحلي فقط إلى مركز إدارة إدارة نقاط النهاية من Microsoft، ثم تقديم سياسات تكوين أمان نقاط النهاية إلى المجموعات & الأجهزة.

> [!NOTE]
> يمكن استخدام الإجراء لتوسيع الحماية من العبث للأجهزة التي تعمل Windows 10 و Windows 10 Enterprise جلسة عمل متعددة و Windows 11 و Windows 11 Enterprise متعدد جلسات العمل و Windows Server 2019 و Windows Server 2022. تأكد من مراجعة المتطلبات الأساسية والمعلومات الأخرى في الموارد المذكورة في هذا الإجراء.

1. إعداد إرفاق المستأجر. لمعرفة المزيد، راجع [بدء العمل: إنشاء](/mem/configmgr/tenant-attach/endpoint-security-get-started) سياسات أمان نقاط النهاية ونشرها من مركز الإدارة.

2. في مركز [إدارة نقاط النهاية من Microsoft،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى برنامج الحماية من الفيروسات **لأمن** \> نقطة **النهاية، ثم** اختر **+ إنشاء نهج**.

   - في قائمة **النظام** الأساسي، حدد Windows 10 **Windows 11 وخادم Windows (ConfigMgr)**.
   - في قائمة **ملف التعريف**، حدد أمن Windows **(معاينة)**.

3. نشر النهج في مجموعة الأجهزة.

#### <a name="need-help-with-this-method"></a>هل تحتاج إلى مساعدة في استخدام هذه الطريقة؟

راجع الموارد التالية:

- [الإعدادات ملف تعريف تجربة أمن Windows في Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [مدونة المجتمع التقني: الإعلان عن الحماية من العبث لعملاء مستأجر "إدارة التكوين" إرفاق العملاء](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>إدارة الحماية من العبث على جهاز فردي

> [!NOTE]
> تحاول كتل الحماية من التلاعب برنامج الحماية من الفيروسات من Microsoft Defender الإعدادات من خلال السجل.
>
> للمساعدة على ضمان عدم تدخل الحماية من العبث في منتجات الأمان غير الخاصة ب Microsoft أو برامج تثبيت المؤسسة النصية التي تعدل هذه الإعدادات، انتقل إلى **أمن Windows** وحدث معلومات الأمان  إلى الإصدار 1.287.60.0 أو الإصدارات الأحدث. (راجع [تحديثات معلومات الأمان](https://www.microsoft.com/wdsi/definitions).)
>
> بمجرد القيام بهذا التحديث، تستمر الحماية من التلاعب في حماية إعدادات التسجيل، وتسجل محاولات تعديلها دون إرجاع الأخطاء.

إذا كنت مستخدما منزليا، أو إذا كنت لا تخضع لإعدادات يديرها فريق أمان، يمكنك استخدام تطبيق أمن Windows لإدارة الحماية من العبث. يجب أن يكون لديك أذونات المسؤول المناسبة على جهازك لتغيير إعدادات الأمان، مثل الحماية من العبث.

إليك ما تراه في تطبيق أمن Windows:

![تم تشغيل الحماية من العبث في Windows 10 Home.](images/tamperprotectionturnedon.png)

1. حدد **بدء**، وابدأ بكتابة *الأمان*. في نتائج البحث **، حدد أمن Windows**.

2. حدد **إعدادات الحماية & الفيروسات** \> & **المخاطر**.

3. تعيين **الحماية من العبث** إلى **تشغيل أو** **إيقاف تشغيل**.

## <a name="are-you-using-windows-server-2016-or-windows-version-1709-1803-or-1809"></a>هل تستخدم Windows Server 2016 أو Windows 1709 أو 1803 أو 1809؟

إذا كنت تستخدم Windows Server 2016 أو Windows 10 1709 أو 1803 أو [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019)، فلن ترى **الحماية** من العبث في تطبيق أمن Windows. بدلا من ذلك، يمكنك استخدام PowerShell لتحديد ما إذا كان يتم تمكين الحماية من العبث أم لا.

في Windows Server 2016، لن يعكس تطبيق الإعدادات بدقة حالة الحماية في الوقت الحقيقي عند تمكين الحماية من التلاعب.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>استخدام PowerShell لتحديد ما إذا كان يتم تشغيل الحماية من العبث والحماية في الوقت الحقيقي

1. افتح Windows PowerShell التطبيق.

2. استخدم [أمر cmdlet Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell.

3. في قائمة النتائج، ابحث عن أو `IsTamperProtected` `RealTimeProtectionEnabled`. (تعني القيمة *true* أنه تم تمكين الحماية من العبث.)

## <a name="view-information-about-tampering-attempts"></a>عرض معلومات حول محاولات التلاعب

تشير محاولات التلاعب عادة إلى الهجمات الإلكترونية الأكبر حجما. يحاول الممثلون السيئون تغيير إعدادات الأمان كطريقة للمثابرة والبقاء غير م اكتشاف. إذا كنت جزءا من فريق الأمان في مؤسستك، يمكنك عرض معلومات حول مثل هذه المحاولات، ثم اتخاذ الإجراءات المناسبة للحد من التهديدات.

عند اكتشاف محاولة عبث، يتم رفع تنبيه في مدخل [Microsoft 365 Defender (](/microsoft-365/security/defender-endpoint/portal-overview)[https://security.microsoft.com](https://security.microsoft.com)).

![Microsoft 365 Defender.](images/tamperattemptalert.png)

باستخدام [الكشف عن تهديدات نقاط النهاية والرد عليها](overview-endpoint-detection-response.md) [وإمكانيات](advanced-hunting-overview.md) الصيد المتقدمة في Microsoft Defender ل Endpoint، يمكن لفريق عمليات الأمان التحقق من مثل هذه المحاولات ومعالجة هذه المحاولات.

## <a name="review-your-security-recommendations"></a>مراجعة توصيات الأمان

تتكامل الحماية من العبث مع [قدرات إدارة & المخاطر](next-gen-threat-and-vuln-mgt.md) . [تتضمن توصيات الأمان](tvm-security-recommendation.md) التأكد من تشغيل الحماية من العبث. على سبيل المثال، يمكنك البحث عن *التلاعب*. في النتائج، يمكنك تحديد **تشغيل الحماية** من العبث لمعرفة المزيد و تشغيلها.

![تشغيل الحماية من العبث.](images/tamperprotectsecurityrecos.png)

لمعرفة المزيد حول المخاطر & إدارة الثغرات، راجع تحليلات لوحة المعلومات [-](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management) إدارة المخاطر والثغرات الأمنية.

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>ما هي إصدارات Windows يمكنني تكوين الحماية من العبث؟

Windows 10 OS [1709](/windows/release-health/status-windows-10-1709) أو [1803](/windows/release-health/status-windows-10-1803) أو [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) أو أي وقت [لاحق مع Microsoft Defender ل Endpoint](/microsoft-365/security/defender-endpoint).
  
Windows 10 Enterprise جلسات عمل متعددة

Windows 11

Windows 11 Enterprise جلسات عمل متعددة
  
إذا كنت تستخدم إدارة التكوين، الإصدار 2006، مع إرفاق المستأجر، يمكن توسيع الحماية من العبث إلى Windows Server 2012 R2 و Windows Server 2016 و Windows Server 2019 و Windows Server 2022. راجع [إرفاق المستأجر: إنشاء نهج الحماية من الفيروسات لنقطة النهاية ونشره من مركز الإدارة (معاينة)](/mem/configmgr/tenant-attach/deploy-antivirus-policy).

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>هل ستؤثر الحماية من العبث على التسجيل بدون برامج الحماية من الفيروسات من Microsoft في أمن Windows؟

لا. ستستمر عروض مكافحة الفيروسات غير الخاصة ب Microsoft في التسجيل في أمن Windows Microsoft.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>ماذا يحدث إذا لم برنامج الحماية من الفيروسات من Microsoft Defender نشطا على جهاز؟

سيتم تشغيل الأجهزة التي تم تشغيلها في Microsoft Defender ل Endpoint برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. في هذه الحالات، ستستمر الحماية من العبث في حماية الخدمة ومميزاتها.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>كيف يمكنني تشغيل الحماية من العبث أو إيقاف تشغيلها؟

إذا كنت مستخدما منزليا، فشاهد [إدارة الحماية من العبث على جهاز فردي](#manage-tamper-protection-on-an-individual-device).

إذا كنت مؤسسة تستخدم [Microsoft Defender ل Endpoint](/microsoft-365/security/defender-endpoint)، يجب أن تكون قادرا على إدارة الحماية من العبث في Intune بطريقة مماثلة لكيفية إدارة ميزات حماية نقاط النهاية الأخرى. راجع المقاطع التالية من هذه المقالة:

- [إدارة الحماية من العبث باستخدام إدارة نقاط النهاية من Microsoft](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [إدارة الحماية من العبث باستخدام Microsoft 365 Defender الإلكتروني](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>كيف يؤثر تكوين الحماية من العبث في Intune على برنامج الحماية من الفيروسات من Microsoft Defender نهج المجموعة؟

لا ينطبق نهج المجموعة على الحماية من التلاعب. يتم تجاهل برنامج الحماية من الفيروسات من Microsoft Defender الإعدادات عند وجود حماية من التلاعب.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>إذا استخدمنا Microsoft Intune لتكوين الحماية من العبث، فهل ينطبق ذلك على المؤسسة بأكملها فقط؟

لديك المرونة في تكوين الحماية من العبث باستخدام Intune. يمكنك استهداف مؤسستك بكاملها، أو تحديد أجهزة ومجموعات مستخدمين معينة.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>هل يمكنني تكوين الحماية من العبث باستخدام Microsoft Endpoint Configuration Manager؟

إذا كنت تستخدم إرفاق المستأجر، يمكنك استخدام Microsoft Endpoint Configuration Manager. راجع الموارد التالية:

- [إدارة الحماية من العبث لمنظمتك باستخدام "إدارة التكوين"، الإصدار 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [مدونة المجتمع التقني: الإعلان عن الحماية من العبث لعملاء مستأجر "إدارة التكوين" إرفاق العملاء](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>لدي تسجيل Windows E3. هل يمكنني استخدام تكوين الحماية من العبث في Intune؟

حاليا، يتوفر تكوين الحماية من التلاعب في Intune فقط للعملاء الذين لديهم [Microsoft Defender ل Endpoint](/microsoft-365/security/defender-endpoint).

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>ماذا يحدث إذا حاولت تغيير إعدادات Microsoft Defender لنقطة النهاية في Intune و Microsoft Endpoint Configuration Manager و Windows أدوات الإدارة عند تمكين الحماية من العبث على جهاز؟

لن تتمكن من تغيير الميزات المحمية بواسطة الحماية من العبث؛ يتم تجاهل طلبات التغيير هذه.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>أنا عميل مؤسسة. هل يمكن للمسؤولين المحليين تغيير الحماية من العبث على أجهزتهم؟

لا. لا يمكن للمسؤولين المحليين تغيير إعدادات الحماية من التلاعب أو تعديلها.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>ماذا يحدث إذا تم تشغيل جهازي مع Microsoft Defender ل Endpoint ثم انتقل إلى حالة خارج اللوحة؟

إذا تم إيقاف تشغيل جهاز من Microsoft Defender لنقطة النهاية، يتم تشغيل الحماية من التلاعب، وهي الحالة الافتراضية للأجهزة غير الإدارة.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>إذا تم تغيير حالة الحماية من العبث، هل يتم عرض التنبيهات في Microsoft 365 Defender الإلكتروني؟

نعم. يظهر التنبيه ضمن [https://security.microsoft.com](https://security.microsoft.com) **تنبيهات**.

يمكن لفريق عمليات الأمان أيضا استخدام استعلامات البحث، مثل المثال التالي:

`AlertInfo|where Title == "Tamper Protection bypass"`

[عرض معلومات حول محاولات التلاعب](#view-information-about-tampering-attempts).

## <a name="see-also"></a>راجع أيضًا

[المساعدة في Windows على أجهزة الكمبيوتر الشخصية Endpoint Protection Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[الحصول على نظرة عامة حول Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint)

[أفضل معا: برنامج الحماية من الفيروسات من Microsoft Defender و Microsoft Defender ل Endpoint](why-use-microsoft-defender-antivirus.md)
