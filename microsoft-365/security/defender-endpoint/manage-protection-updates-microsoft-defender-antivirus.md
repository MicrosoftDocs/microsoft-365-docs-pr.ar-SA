---
title: إدارة كيفية تلقي برنامج الحماية من الفيروسات من Microsoft Defender للتحديثات ومكان تلقيها
description: إدارة الأمر الاحتياطي لكيفية تلقي برنامج الحماية من الفيروسات من Microsoft Defender تحديثات الحماية.
keywords: التحديثات، وخطوط أساس الأمان، والحماية، والنظام الاحتياطي، وACDL، وMMPC، و UNC، ومسار الملف، والمشاركة، وwsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: b01a9315e143a3fb49cedef84e1f7b9e505441d5
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873325"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>إدارة مصادر تحديثات برنامج الحماية من الفيروسات من Microsoft Defender الحماية

> [!IMPORTANT]
> قد يكون العملاء الذين قاموا بتطبيق تحديث محرك Microsoft Defender لشهر مارس 2022 (**1.1.19100.5**) قد واجهوا استخداماً كبيراً للموارد (وحدة المعالجة المركزية و / أو الذاكرة). أصدرت Microsoft تحديثاً (**1.1.19200.5**) يعمل على حل الأخطاء التي تم تقديمها في الإصدار السابق. يوصى العملاء بالتحديث إلى هذا المحرك الجديد لمحرك مكافحة الفيروسات (**1.1.19200.5**). لضمان إصلاح أي مشكلات في الأداء بشكل كامل، يوصى بإعادة تشغيل الأجهزة بعد تطبيق التحديث. لمزيد من المعلومات، راجع [إصدارات النظام الأساسي والمحرك الشهرية](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**ينطبق على:**

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

يعد الحفاظ على الحماية من الفيروسات محدثا أمرا بالغ الأهمية. هناك مكونان لإدارة تحديثات الحماية برنامج الحماية من الفيروسات من Microsoft Defender:

- *من أين* يتم تنزيل التحديثات؛ و
- *عند* تنزيل التحديثات وتطبيقها.

تصف هذه المقالة كيفية التحديد من حيث يجب تنزيل التحديثات (يعرف هذا أيضا بالترتيب الاحتياطي). راجع [إدارة التحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق موضوع الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md) للحصول على نظرة عامة حول كيفية عمل التحديثات وكيفية تكوين جوانب أخرى من التحديثات (مثل جدولة التحديثات).

> [!IMPORTANT]
> برنامج الحماية من الفيروسات من Microsoft Defender يتم تسليم تحديثات معلومات الأمان وتحديثات النظام الأساسي من خلال Windows Update وبدءا من يوم الاثنين، 21 أكتوبر 2019، سيتم توقيع جميع تحديثات معلومات الأمان SHA-2 حصريا. يجب تحديث أجهزتك لدعم SHA-2 من أجل تحديث معلومات الأمان. لمعرفة المزيد، راجع [متطلبات دعم توقيع التعليمات البرمجية SHA-2 2 2019 Windows وWSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>ترتيب احتياطي

عادة ما تقوم بتكوين نقاط النهاية لتنزيل التحديثات بشكل فردي من مصدر أساسي متبوعا بمصادر أخرى بترتيب الأولوية، استنادا إلى تكوين الشبكة. يتم الحصول على التحديثات من المصادر بالترتيب الذي تحدده. إذا كانت التحديثات من المصدر الحالي قديمة، يتم استخدام المصدر التالي في القائمة على الفور.

عند نشر التحديثات، يتم تطبيق بعض المنطق لتقليل حجم التحديث. في معظم الحالات، يتم تنزيل الاختلافات فقط بين التحديث الأخير والتحديث المثبت حاليا (يشار إلى هذا باسم دلتا) على الجهاز وتطبيقه. ومع ذلك، يعتمد حجم دلتا على عاملين رئيسيين:

- عمر التحديث الأخير على الجهاز؛ و
- المصدر المستخدم لتنزيل التحديثات وتطبيقها.

كلما كانت التحديثات على نقطة النهاية أقدم، كان التنزيل أكبر. ومع ذلك، يجب عليك أيضا مراعاة تكرار التنزيل أيضا. يمكن أن يؤدي جدول التحديث الأكثر تكرارا إلى المزيد من استخدام الشبكة، بينما يمكن أن يؤدي الجدول الأقل تكرارا إلى أحجام ملفات أكبر لكل تنزيل.

هناك خمسة مواقع حيث يمكنك تحديد المكان الذي يجب أن تحصل فيه نقطة النهاية على التحديثات:

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows Server Update Service](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) <sup>[[1](#fn1)]<sup></sup>  
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [مشاركة ملف الشبكة](#unc-share)
- [تحديثات معلومات الأمان برنامج الحماية من الفيروسات من Microsoft Defender والبرامج الضارة](/microsoft-365/security/defender-endpoint/manage-protection-update-schedule-microsoft-defender-antivirus) <sup>الأخرى من Microsoft [[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) خادم تحديث التعريف الداخلي Intune - إذا كنت تستخدم SCCM/SUP للحصول على تحديثات التعريف برنامج الحماية من الفيروسات من Microsoft Defender، وتحتاج إلى الوصول إلى Windows Update على أجهزة العميل المحظورة، يمكنك الانتقال إلى الإدارة المشتركة وتفريغ حمل عمل حماية نقطة النهاية إلى Intune. في نهج مكافحة البرامج الضارة الذي تم تكوينه في Intune، هناك خيار ل "خادم تحديث التعريف الداخلي" الذي يمكن تكوينه لاستخدام WSUS المحلي كمصدر التحديث. يساعدك هذا على التحكم في التحديثات من خادم WU الرسمي المعتمدة للمؤسسة، ويساعد أيضا الوكيل وحفظ نسبة استخدام الشبكة إلى شبكة UPdates Windows الرسمية.

(<a id="fn1">2</a>) قد يكون هذا النهج والسجل مدرجين كذكاء أمان مركز الحماية من البرامج الضارة لـ Microsoft (MMPC)، اسمه السابق.

لضمان أفضل مستوى من الحماية، يسمح Microsoft Update بإصدارات سريعة، ما يعني تنزيلات أصغر بشكل متكرر. توفر Windows Server Update Service، Microsoft Endpoint Configuration Manager، وتحديثات معلومات الأمان من Microsoft، ومصادر تحديثات النظام الأساسي تحديثات أقل تكرارا. ومن ثم، يمكن أن تكون دلتا أكبر، ما يؤدي إلى تنزيلات أكبر.

> [!NOTE]
> تحتوي تحديثات التحليل الذكي للأمان على تحديثات المحرك ويتم إصدارها على إيقاع شهري.
يتم أيضا تسليم تحديثات معلومات الأمان عدة مرات في اليوم، ولكن هذه الحزمة لا تحتوي على محرك.


> [!IMPORTANT]
> إذا قمت بتعيين تحديثات [صفحة معلومات الأمان من Microsoft](https://www.microsoft.com/security/portal/definitions/adl.aspx) كمصدر احتياطي بعد Windows Server Update Service أو Microsoft Update، يتم تنزيل التحديثات فقط من تحديثات معلومات الأمان وتحديثات النظام الأساسي عندما يعتبر التحديث الحالي قديما. (بشكل افتراضي، هذا هو سبعة أيام متتالية من عدم القدرة على تطبيق التحديثات من خدمة تحديث خادم Windows أو خدمات Microsoft Update).
> ومع ذلك، يمكنك [تعيين عدد الأيام قبل الإبلاغ عن الحماية على أنها قديمة](/microsoft-365/security/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus).<p>
> اعتبارا من يوم الاثنين، 21 أكتوبر 2019، سيتم توقيع تحديثات معلومات الأمان وتحديثات النظام الأساسي SHA-2 حصريا. يجب تحديث الأجهزة لدعم SHA-2 من أجل الحصول على أحدث تحديثات معلومات الأمان وتحديثات النظام الأساسي. لمعرفة المزيد، راجع [متطلبات دعم توقيع التعليمات البرمجية SHA-2 2 2019 Windows وWSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

يحتوي كل مصدر على سيناريوهات نموذجية تعتمد على كيفية تكوين شبكتك، بالإضافة إلى عدد مرات نشر التحديثات، كما هو موضح في الجدول التالي:

|موقع|نموذج السيناريو|
|---|---|
|خدمة تحديث خادم Windows|أنت تستخدم Windows Server Update Service لإدارة تحديثات الشبكة.|
|Microsoft Update|تريد أن تتصل نقاط النهاية مباشرة ب Microsoft Update. قد يكون هذا مفيدا لنقاط النهاية التي تتصل بشبكة المؤسسة بشكل غير منتظم، أو إذا لم تستخدم خدمة تحديث الخادم Windows لإدارة التحديثات.|
|مشاركة الملف|لديك أجهزة غير متصلة بالإنترنت (مثل الأجهزة الظاهرية). يمكنك استخدام مضيف الجهاز الظاهري المتصل بالإنترنت لتنزيل التحديثات إلى مشاركة الشبكة، والتي يمكن للأجهزة الظاهرية الحصول على التحديثات منها. راجع [دليل نشر VDI](deployment-vdi-microsoft-defender-antivirus.md) لمعرفة كيفية استخدام مشاركات الملفات في بيئات البنية الأساسية لسطح المكتب الظاهري (VDI).|
|إدارة نقاط النهاية من Microsoft|أنت تستخدم إدارة نقاط النهاية من Microsoft لتحديث نقاط النهاية.|
|تحديثات معلومات الأمان وتحديثات النظام الأساسي برنامج الحماية من الفيروسات من Microsoft Defender والبرامج الضارة الأخرى من Microsoft (يشار إليها سابقا باسم MMPC)|[تأكد من تحديث أجهزتك لدعم SHA-2](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). برنامج الحماية من الفيروسات من Microsoft Defender يتم تسليم معلومات الأمان وتحديثات النظام الأساسي من خلال Windows Update، وسيتم توقيع تحديثات معلومات الأمان وتحديثات النظام الأساسي يوم الاثنين 21 أكتوبر 2019 حصريا. <br/>قم بتنزيل آخر تحديثات الحماية بسبب إصابة حديثة أو للمساعدة في توفير صورة أساسية قوية [لنشر VDI](deployment-vdi-microsoft-defender-antivirus.md). يجب استخدام هذا الخيار بشكل عام كمصدر احتياطي نهائي فقط، وليس المصدر الأساسي. سيتم استخدامه فقط إذا تعذر تنزيل التحديثات من Windows Server Update Service أو Microsoft Update [لعدد محدد من الأيام](/microsoft-365/security/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).|

يمكنك إدارة الترتيب الذي تستخدم به مصادر التحديث مع نهج المجموعة Microsoft Endpoint Configuration Manager وPowerShell cmdlets وWMI.

> [!IMPORTANT]
> إذا قمت بتعيين خدمة تحديث خادم Windows كموقع تنزيل، فيجب الموافقة على التحديثات، بغض النظر عن أداة الإدارة التي تستخدمها لتحديد الموقع. يمكنك إعداد قاعدة موافقة تلقائية باستخدام خدمة تحديث خادم Windows، والتي قد تكون مفيدة مع وصول التحديثات مرة واحدة على الأقل في اليوم. لمعرفة المزيد، راجع [مزامنة تحديثات حماية نقطة النهاية في خدمة تحديث خادم Windows مستقلة](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

تصف الإجراءات الواردة في هذه المقالة أولا كيفية تعيين الطلب، ثم كيفية إعداد خيار **مشاركة الملف** إذا قمت بتمكينه.

## <a name="use-group-policy-to-manage-the-update-location"></a>استخدام نهج المجموعة لإدارة موقع التحديث

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows Windows **تحديث توقيع** **Defender** \> وتكوين الإعدادات التالية:

   1. انقر نقرا مزدوجا فوق **"تعريف ترتيب المصادر" لتنزيل إعداد تحديثات معلومات الأمان** وقم بتعيين الخيار "**ممكن".**

   2. أدخل ترتيب المصادر، مفصولة بميناء واحد، على سبيل المثال: `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`، كما هو موضح في لقطة الشاشة التالية.

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="إعداد نهج المجموعة الذي يسرد ترتيب المصادر" lightbox="../../media/wdav-order-update-sources.png":::

   3. حدد **موافق**. سيؤدي ذلك إلى تعيين ترتيب مصادر تحديث الحماية.

   4. انقر نقرا مزدوجا فوق **"تعريف مشاركات الملفات" لتنزيل إعداد تحديثات معلومات الأمان** وقم بتعيين الخيار "**ممكن".**

   5. حدد مصدر مشاركة الملف. إذا كان لديك مصادر متعددة، أدخل كل مصدر بالترتيب الذي يجب استخدامه، مفصولا بمصدر واحد. استخدم [رمز UNC القياسي](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) للدلالة على المسار، على سبيل المثال: `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. إذا لم تدخل أي مسارات، فسيتم تخطي هذا المصدر عند تحديث تنزيلات الجهاز الظاهري.

   6. انقر فوق **موافق**. سيؤدي ذلك إلى تعيين ترتيب مشاركات الملفات عند الإشارة إلى هذا المصدر في **تحديد ترتيب المصادر...** إعداد نهج المجموعة.

> [!NOTE]
> بالنسبة Windows 10، الإصدارات 1703 حتى 1809 وتضمينها، مسار النهج هو **Windows المكونات > برنامج الحماية من الفيروسات من Microsoft Defender > تحديثات التوقيع** Windows 10، الإصدار 1903، مسار النهج **هو Windows المكونات > برنامج الحماية من الفيروسات من Microsoft Defender > تحديثات معلومات الأمان**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>استخدام Configuration Manager لإدارة موقع التحديث

راجع [تكوين تحديثات معلومات الأمان Endpoint Protection](/configmgr/protect/deploy-use/endpoint-definition-updates) للحصول على تفاصيل حول تكوين إدارة نقاط النهاية من Microsoft (الفرع الحالي).

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>استخدام PowerShell cmdlets لإدارة موقع التحديث

استخدم أوامر PowerShell cmdlets التالية لتعيين أمر التحديث.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

راجع المقالات التالية للحصول على مزيد من المعلومات:

- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [استخدم أوامر cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [أوامر cmdlets الخاصة بالحماية من الفيروسات ل Defender](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>استخدام Windows Management Instruction (WMI) لإدارة موقع التحديث

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

راجع المقالات التالية للحصول على مزيد من المعلومات:

- [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>استخدام إدارة الجهاز الجوال (MDM) لإدارة موقع التحديث

راجع [Policy CSP - Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) للحصول على تفاصيل حول تكوين MDM.

## <a name="what-if-were-using-a-third-party-vendor"></a>ماذا لو كنا نستخدم موردا تابعا لجهة خارجية؟

تصف هذه المقالة كيفية تكوين تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها. ومع ذلك، يمكن استخدام موردي الجهات الخارجية لتنفيذ هذه المهام.

على سبيل المثال، افترض أن شركة Contoso قد عينت شركة Fabrikam لإدارة حل الأمان الخاص بها، والذي يتضمن برنامج الحماية من الفيروسات من Microsoft Defender. تستخدم Fabrikam عادة [Windows Management Instrumentation](./use-wmi-microsoft-defender-antivirus.md) أو [PowerShell cmdlets](./use-powershell-cmdlets-microsoft-defender-antivirus.md) أو [Windows سطر الأوامر](./command-line-arguments-microsoft-defender-antivirus.md) لنشر التصحيحات والتحديثات.

> [!NOTE]
> لا تختبر Microsoft حلول الجهات الخارجية لإدارة برنامج الحماية من الفيروسات من Microsoft Defender.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-and-platform-updates"></a>إنشاء مشاركة UNC لذكاء الأمان وتحديثات النظام الأساسي

قم بإعداد مشاركة ملف شبكة (UNC/محرك أقراص معين) لتنزيل معلومات الأمان وتحديثات النظام الأساسي من موقع MMPC باستخدام مهمة مجدولة.

1. في النظام الذي تريد توفير المشاركة عليه وتنزيل التحديثات، قم بإنشاء مجلد ستحفظ البرنامج النصي إليه.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. قم بإنشاء المجلد الذي ستحفظ تحديثات التوقيع إليه.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. قم بتنزيل البرنامج النصي PowerShell من [www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. انقر فوق **"تنزيل يدوي**".

5. انقر فوق **"Download the raw nupkg file**".

6. استخراج الملف.

7. انسخ الملف SignatureDownloadCustomTask.ps1 إلى المجلد الذي أنشأته مسبقا. `C:\Tool\PS-Scripts\`

8. استخدم سطر الأوامر لإعداد المهمة المجدولة.

   > [!NOTE]
   > هناك نوعان من التحديثات: كامل ودلتا.

   - بالنسبة إلى دلتا x64:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - للإصدار x64 الكامل:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - بالنسبة إلى دلتا x86:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - للإصدار x86 الكامل:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   > [!NOTE]
   > عند إنشاء المهام المجدولة، يمكنك العثور عليها في "جدولة المهام" ضمن `Microsoft\Windows\Windows Defender`.

9. قم بتشغيل كل مهمة يدويا وتحقق من أن لديك بيانات (`mpam-d.exe`و، `mpam-fe.exe`و `nis_full.exe`) في المجلدات التالية (ربما تكون قد اخترت مواقع مختلفة):

   - `C:\Temp\TempSigs\x86`
   - `C:\Temp\TempSigs\x64`

   إذا فشلت المهمة المجدولة، فشغل الأوامر التالية:

    ```console
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```

    > [!NOTE]
    > ويمكن أن تكون المشاكل أيضا بسبب نهج التنفيذ.

10. إنشاء مشاركة تشير إلى `C:\Temp\TempSigs` (على سبيل المثال، `\\server\updates`).

    > [!NOTE]
    > كحد أدنى، يجب أن يكون لدى المستخدمين المصادق عليهم حق الوصول "قراءة". ينطبق هذا المطلب أيضا على أجهزة كمبيوتر المجال والمشاركة وNTFS (الأمان).

11. تعيين موقع المشاركة في النهج إلى المشاركة.

    > [!NOTE]
    > لا تقم بإضافة المجلد x64 (أو x86) في المسار. تضيفها عملية mpcmdrun.exe تلقائيا.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md)
- [إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)
- [إدارة تحديثات الأجهزة المحمولة والأجهزة الظاهرية](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
