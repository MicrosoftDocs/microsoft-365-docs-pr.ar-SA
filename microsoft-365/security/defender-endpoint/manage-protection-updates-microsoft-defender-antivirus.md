---
title: إدارة كيفية تلقي التحديثات برنامج الحماية من الفيروسات من Microsoft Defender بها
description: قم بإدارة الأمر الاحتياطي  الكيفية التي برنامج الحماية من الفيروسات من Microsoft Defender بها تحديثات الحماية.
keywords: التحديثات، خطوط الأمان الأساسية، الحماية، الترتيب الاحتياطي، ADL، MMPC، UNC، مسار الملف، المشاركة، wsus
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
ms.openlocfilehash: 69c211e02b5bea12431e17bf2256405f96977b53
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467390"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>إدارة مصادر تحديثات برنامج الحماية من الفيروسات من Microsoft Defender الحماية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

من المهم إبقاء الحماية من الفيروسات مواكبا لها. هناك مكونان لإدارة تحديثات الحماية برنامج الحماية من الفيروسات من Microsoft Defender:

- *حيث* يتم تنزيل التحديثات من؛ و
- *عند* تنزيل التحديثات وتطبيقها.

تصف هذه المقالة كيفية التحديد من حيث يجب تنزيل التحديثات (يعرف هذا أيضا بالترتيب الاحتياطي). راجع [إدارة برنامج الحماية من الفيروسات من Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md) الأساسية وتطبيق موضوع الأساسات للحصول على نظرة عامة حول كيفية عمل التحديثات، وكيفية تكوين جوانب أخرى من التحديثات (مثل جدولة التحديثات).

> [!IMPORTANT]
> برنامج الحماية من الفيروسات من Microsoft Defender تحديثات معلومات الأمان عبر Windows Update بدءا من يوم الاثنين 21 أكتوبر 2019، سيتم توقيع جميع تحديثات معلومات الأمان بشكل حصري على SHA-2. يجب تحديث أجهزتك لدعم SHA-2 لتحديث معلومات الأمان الخاصة بك. لمعرفة المزيد، راجع متطلبات دعم توقيع التعليمات البرمجية [ل SHA-2 Windows و WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>الأمر الاحتياطي

تقوم عادة بتكوين نقاط النهاية لتنزيل التحديثات بشكل فردي من مصدر أساسي متبوع بمصادر أخرى حسب الأولوية، استنادا إلى تكوين الشبكة. يتم الحصول على التحديثات من المصادر بالترتيب الذي تحدده. إذا كانت التحديثات من المصدر الحالي غير محدثة، فيستخدم المصدر التالي في القائمة على الفور.

عند نشر التحديثات، يتم تطبيق بعض المنطق لتصغير حجم التحديث. في معظم الحالات، يتم تنزيل الاختلافات فقط بين التحديث الأخير والتحديث المثبت حاليا (يشار إلى ذلك باسم دلتا) على الجهاز وتطبيقه. ومع ذلك، يعتمد حجم دلتا على عاملين رئيسيين:

- عمر التحديث الأخير على الجهاز؛ و
- المصدر المستخدم لتنزيل التحديثات وتطبيقها.

كلما كانت التحديثات قديمة على نقطة نهاية، زاد حجم التنزيل. ومع ذلك، يجب عليك أيضا التفكير في تكرار التنزيل أيضا. يمكن أن يؤدي جدول التحديث الأكثر تكرارا إلى زيادة استخدام الشبكة، في حين أن الجدول الأقل تكرارا قد يؤدي إلى أحجام ملفات أكبر لكل تنزيل.

هناك خمسة مواقع حيث يمكنك تحديد المكان الذي يجب أن تحصل فيه نقطة النهاية على التحديثات:

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows Server Update Service](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) <sup>[[1](#fn1)]<sup></sup>  
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [مشاركة ملف الشبكة](#unc-share)
- [تحديثات معلومات الأمان برنامج الحماية من الفيروسات من Microsoft Defender والبرامج الضارة](https://www.microsoft.com/wdsi/defenderupdates) الأخرى من Microsoft <sup>[[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) Intune Internal Definition Update Server - إذا كنت تستخدم SCCM/SUP للحصول على تحديثات التعريف ل برنامج الحماية من الفيروسات من Microsoft Defender، وأحتاجت إلى الوصول إلى Windows Update على الأجهزة المحظورة على الأجهزة العميلة، يمكنك الانتقال إلى الإدارة المشاركة وإثقال حمل عمل حماية نقطة النهاية إلى Intune. في نهج مكافحة البرامج الضارة الذي تم تكوينه في Intune، يوجد خيار "خادم تحديث التعريف الداخلي" الذي يمكن تكوينه لاستخدام WSUS الداخلي كمصدر التحديث. يساعدك ذلك على التحكم في التحديثات التي تمت الموافقة عليها من خادم WU الرسمي للمؤسسة، كما يساعد الوكيل وحفظ حركة مرور الشبكة في شبكة Windows UPdates الرسمية.

(<a id="fn1">2</a>) قد يكون هذا النهج والسجل مدرجين مركز الحماية من البرامج الضارة لـ Microsoft الأمان (MMPC) ، اسم السجل السابق.

لضمان الحصول على أفضل مستوى من الحماية، يتيح Microsoft Update الإصدارات السريعة، مما يعني تنزيلات أصغر بشكل متكرر. توفر Windows "خدمة تحديث Microsoft Endpoint Configuration Manager" و"معلومات الأمان من Microsoft" تحديثات أقل تكرارا. وبالتالي، يمكن أن تكون دلتا أكبر، مما يؤدي إلى تنزيلات أكبر.

> [!IMPORTANT]
> إذا قمت بتعيين تحديثات صفحة معلومات الأمان من [Microsoft](https://www.microsoft.com/security/portal/definitions/adl.aspx) كمصدر خلفي بعد Windows Server Update Service أو Microsoft Update، يتم تنزيل التحديثات فقط من تحديثات معلومات الأمان عندما يعتبر التحديث الحالي محدثا. (بشكل افتراضي، هذا هو سبعة أيام متتالية من عدم القدرة على تطبيق التحديثات من Windows Server Update Service أو خدمات Microsoft Update).
> ومع ذلك، يمكنك تعيين عدد الأيام قبل أن يتم إعداد التقارير حول الحماية على أنها غير [مكتشفة](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).<p>
> بدءا من يوم الاثنين، 21 أكتوبر 2019، ستكون تحديثات المعلومات الأمنية موقعة بشكل حصري على SHA-2. يجب تحديث الأجهزة لدعم SHA-2 للحصول على آخر تحديثات معلومات الأمان. لمعرفة المزيد، راجع متطلبات دعم توقيع التعليمات البرمجية [ل SHA-2 Windows و WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

يحتوي كل مصدر على سيناريوهات نموذجية تعتمد على كيفية تكوين الشبكة، بالإضافة إلى عدد مرات نشر التحديثات، كما هو موضح في الجدول التالي:

<br/><br/>

|الموقع|سيناريو نموذج|
|---|---|
|Windows Server Update Service|أنت تستخدم Windows Server Update لإدارة التحديثات للشبكة.|
|Microsoft Update|تريد أن تتصل نقاط النهاية مباشرة ب Microsoft Update. قد يكون هذا مفيدا لنقاط النهاية التي تتصل بشكل غير منتظم بشبكة المؤسسة، أو إذا لم تستخدم Windows Server Update لإدارة التحديثات.|
|مشاركة الملف|لديك أجهزة غير متصلة بالإنترنت (مثل أجهزة VMs). يمكنك استخدام مضيف VM المتصل بالإنترنت لتنزيل التحديثات إلى مشاركة شبكة، حيث يمكن ل VMs الحصول على التحديثات منها. راجع دليل [نشر VDI](deployment-vdi-microsoft-defender-antivirus.md) لمعرفة كيفية استخدام مشاركة الملفات في بيئات البنية الأساسية لسطح المكتب الظاهري (VDI).|
|إدارة نقاط النهاية من Microsoft|أنت تستخدم إدارة نقاط النهاية من Microsoft لتحديث نقاط النهاية.|
|تحديثات معلومات الأمان برنامج الحماية من الفيروسات من Microsoft Defender والبرامج الضارة الأخرى من Microsoft (يشار إليها سابقا باسم MMPC)|[تأكد من تحديث أجهزتك لدعم SHA-2](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). برنامج الحماية من الفيروسات من Microsoft Defender تحديثات الأمان عبر Windows Update، وبدءا من يوم الاثنين 21 أكتوبر 2019، سيتم توقيع تحديثات معلومات الأمان على SHA-2 بشكل حصري. <br/>قم بتنزيل آخر تحديثات الحماية بسبب إصابة حديثة أو للمساعدة في توفير صورة أساسية قوية لنشر [VDI](deployment-vdi-microsoft-defender-antivirus.md). يجب استخدام هذا الخيار بشكل عام كمصدر خلفي نهائي فقط، وليس كمصدر أساسي. سيتم استخدامه فقط إذا لم يكن من الممكن تنزيل التحديثات من Windows Server Update Service أو Microsoft Update [لعدد معين من الأيام](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).|

يمكنك إدارة الترتيب الذي يتم به استخدام مصادر التحديث مع نهج المجموعة Microsoft Endpoint Configuration Manager و PowerShell cmdlets و WMI.

> [!IMPORTANT]
> إذا قمت Windows خدمة تحديث الخادم كم موقع تنزيل، فيجب الموافقة على التحديثات، بغض النظر عن أداة الإدارة التي تستخدمها لتحديد الموقع. يمكنك إعداد قاعدة موافقة تلقائية باستخدام Windows Server Update Service، والتي قد تكون مفيدة عند وصول التحديثات مرة واحدة على الأقل في اليوم. لمعرفة المزيد، راجع مزامنة تحديثات حماية نقطة النهاية في موقع Windows [Server Update Service](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

تصف الإجراءات في هذه المقالة أولا كيفية تعيين الترتيب، ثم كيفية إعداد خيار مشاركة الملف إذا قمت بتمكينه.

## <a name="use-group-policy-to-manage-the-update-location"></a>استخدام نهج المجموعة لإدارة موقع التحديث

1. على جهاز نهج المجموعة، افتح نهج المجموعة [إدارة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) التحكم، وانقر بيمين فوق نهج المجموعة الذي تريد تكوينه، ثم انقر فوق **تحرير**.

2. في نهج المجموعة **إدارة الكمبيوتر،** انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة **Windows مكونات Windows** \> **"توقيع Defender**\>" وتكوين الإعدادات التالية:

   1. انقر نقرا **مزدوجا فوق إعداد** تحديد ترتيب المصادر لتنزيل تحديثات معلومات الأمان، ثم قم بتعيين الخيار إلى **تمكين**.

   2. أدخل ترتيب المصادر، مفصولة بأنبوب واحد، على سبيل المثال: `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`، كما هو موضح في لقطة الشاشة التالية.

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="إعداد نهج المجموعة الذي ي سرد ترتيب المصادر" lightbox="../../media/wdav-order-update-sources.png":::

   3. حدد **موافق**. سيحدد ذلك ترتيب مصادر تحديث الحماية.

   4. انقر نقرا مزدوجا فوق **الإعداد تعريف أسهم الملفات لتنزيل تحديثات معلومات** الأمان، ثم قم بتعيين الخيار **إلى تمكين**.

   5. حدد مصدر مشاركة الملف. إذا كانت لديك مصادر متعددة، أدخل كل مصدر بالترتيب الذي يجب استخدامه، مفصولا بواسطة أنبوب واحد. استخدم ["تنويه UNC" القياسي](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) لتضمين المسار، على سبيل المثال: `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. إذا لم تدخل أي مسارات، سيتم تخطي هذا المصدر عندما يتم تحديث VM.

   6. انقر فوق **موافق**. من خلال ذلك، سيتم تعيين ترتيب أسهم الملفات عند الإشارة إلى هذا المصدر في إعداد تحديد ترتيب المصادر **...** نهج المجموعة.

> [!NOTE]
> بالنسبة Windows 10، الإصدارات 1703 إلى 1809 بما في ذلك، مسار النهج هو **Windows مكونات > برنامج الحماية من الفيروسات من Microsoft Defender >** تحديثات التواقيع ل Windows 10، الإصدار 1903، مسار النهج **Windows المكونات > برنامج الحماية من الفيروسات من Microsoft Defender > "تحديثات معلومات الأمان"**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>استخدام Configuration Manager لإدارة موقع التحديث

راجع [تكوين تحديثات معلومات الأمان Endpoint Protection](/configmgr/protect/deploy-use/endpoint-definition-updates) للحصول على تفاصيل حول تكوين إدارة نقاط النهاية من Microsoft (الفرع الحالي).

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>استخدام PowerShell cmdlets لإدارة موقع التحديث

استخدم أمر cmdlets التالي في PowerShell لتعيين أمر التحديث.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

لمزيد من المعلومات، راجع المقالات التالية:

- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [استخدم PowerShell cmdlets لتكوين برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Cmdlets ل Defender Antivirus](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>استخدام Windows إدارة البيانات (WMI) لإدارة موقع التحديث

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

لمزيد من المعلومات، راجع المقالات التالية:

- [Windows واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>استخدام إدارة الجهاز Mobile (MDM) لإدارة موقع التحديث

راجع [النهج CSP - Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) للحصول على تفاصيل حول تكوين MDM.

## <a name="what-if-were-using-a-third-party-vendor"></a>ماذا لو كنا نستخدم موردا من جهة خارجية؟

تصف هذه المقالة كيفية تكوين التحديثات وإدارتها برنامج الحماية من الفيروسات من Microsoft Defender. ومع ذلك، يمكن استخدام موردي الجهات الخارجية لتنفيذ هذه المهام.

على سبيل المثال، افترض أن شركة Contoso قد عينت شركة Fabrikam لإدارة حل الأمان الذي يتضمن برنامج الحماية من الفيروسات من Microsoft Defender. تستخدم Fabrikam [عادة Windows أدوات](./use-wmi-microsoft-defender-antivirus.md) الإدارة أو [أوامر PowerShell cmdlets](./use-powershell-cmdlets-microsoft-defender-antivirus.md) أو Windows الأوامر لنشر التصحيحات والتحديثات.[](./command-line-arguments-microsoft-defender-antivirus.md)

> [!NOTE]
> لا تختبر Microsoft حلول  الأطراف الخارجية لإدارة برنامج الحماية من الفيروسات من Microsoft Defender.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-updates"></a>إنشاء مشاركة UNC لتحديثات المعلومات الأمنية

قم بإعداد مشاركة ملف شبكة (UNC/محرك أقراص محدد) لتنزيل تحديثات معلومات الأمان من موقع MMPC باستخدام مهمة مجدولة.

1. على النظام الذي تريد توفير المشاركة عليه وتنزيل التحديثات، أنشئ مجلدا ستحفظ البرنامج النصي فيه.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. قم بإنشاء المجلد الذي سيتم حفظ تحديثات التوقيع فيه.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. قم بتنزيل البرنامج النصي PowerShell [من www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. انقر **فوق تنزيل يدوي**.

5. انقر **فوق تنزيل ملف nupkg الخام**.

6. استخراج الملف.

7. انسخ الملف SignatureDownloadCustomTask.ps1 إلى المجلد الذي أنشأته مسبقا، `C:\Tool\PS-Scripts\` .

8. استخدم سطر الأوامر لإعداد المهمة المجدولة.

   > [!NOTE]
   > هناك نوعان من التحديثات: التحديث الكامل والدلتا.

   - بالنسبة إلى دلتا x64:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - لل x64 بالكامل:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - في دلتا x86:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - لل x86 بالكامل:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   > [!NOTE]
   > عند إنشاء المهام المجدولة، يمكنك العثور عليها في "جدول المهام" ضمن `Microsoft\Windows\Windows Defender`.

9. تشغيل كل مهمة يدويا والتحقق من أن لديك بيانات (`mpam-d.exe`و`mpam-fe.exe``nis_full.exe`) في المجلدات التالية (ربما قمت باختيار مواقع مختلفة):

   - `C:\Temp\TempSigs\x86`
   - `C:\Temp\TempSigs\x64`

   إذا فشلت المهمة المجدولة، فدير الأوامر التالية:

    ```console
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```

    > [!NOTE]
    > قد يعود سبب المشاكل أيضا إلى نهج التنفيذ.

10. إنشاء مشاركة تشير إلى `C:\Temp\TempSigs` (على سبيل المثال، `\\server\updates`).

    > [!NOTE]
    > كحد أدنى، يجب أن يكون لدى المستخدمين المصادق عليهم حق الوصول "للقراءة". ينطبق هذا المتطلب أيضا على أجهزة كمبيوتر المجال، المشاركة، وNTFS (الأمان).

11. تعيين موقع المشاركة في النهج إلى المشاركة.

    > [!NOTE]
    > لا تضيف المجلد x64 (أو x86) في المسار. تقوم mpcmdrun.exe العملية بإضافتها تلقائيا.

## <a name="related-articles"></a>المقالات ذات الصلة

- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيقها](manage-updates-baselines-microsoft-defender-antivirus.md)
- [إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)
- [إدارة التحديثات للأجهزة المحمولة وأجهزة VMs](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
