---
title: تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها
description: تكوين واختبار اتصالك بخدمة حماية السحابة برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: مكافحة الفيروسات، برنامج الحماية من الفيروسات من Microsoft Defender، ومكافحة البرامج الضارة، والأمان، والمدافع، والسحابة، والعدوانية، ومستوى الحماية
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 02/03/2022
ms.reviewer: mkaminska; pahuijbr
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 8da099332ffbe2cc3d860faef504e4c5d9663614
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418621"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

لضمان برنامج الحماية من الفيروسات من Microsoft Defender تعمل الحماية التي توفرها السحابة بشكل صحيح، يجب على فريق الأمان تكوين شبكتك للسماح بالاتصالات بين نقاط النهاية وبعض خوادم Microsoft. تسرد هذه المقالة الاتصالات التي يجب السماح بها لاستخدام قواعد جدار الحماية. كما يوفر إرشادات للتحقق من صحة الاتصال. سيضمن تكوين الحماية بشكل صحيح حصولك على أفضل قيمة من خدمات الحماية التي توفرها السحابة.

> [!IMPORTANT]
> تحتوي هذه المقالة على معلومات حول تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender فقط. إذا كنت تستخدم Microsoft Defender لنقطة النهاية (الذي يتضمن برنامج الحماية من الفيروسات من Microsoft Defender)، فراجع [تكوين إعدادات اتصال وكيل الجهاز والإنترنت ل Defender لنقطة النهاية](configure-proxy-internet.md).


> [!NOTE]
> تم إهمال الموقع التجريبي ل Defender لنقطة النهاية في demo.wd.microsoft.com وستتم إزالته في المستقبل.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>السماح بالاتصالات بخدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender

توفر خدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender حماية سريعة وقوية لنقاط النهاية الخاصة بك. من الاختياري تمكين خدمة الحماية المقدمة من السحابة. يوصى برنامج الحماية من الفيروسات من Microsoft Defender خدمة السحابة، لأنها توفر حماية مهمة من البرامج الضارة على نقاط النهاية والشبكة. لمزيد من المعلومات، راجع [تمكين الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) لتمكين الخدمة باستخدام Intune أو Microsoft Endpoint Configuration Manager أو نهج المجموعة أو PowerShell cmdlets أو العملاء الفرديين في تطبيق أمن Windows.

بعد تمكين الخدمة، تحتاج إلى تكوين الشبكة أو جدار الحماية للسماح بالاتصالات بين الشبكة ونقاط النهاية. نظرا لأن الحماية الخاصة بك هي خدمة سحابية، يجب أن يكون لدى أجهزة الكمبيوتر حق الوصول إلى الإنترنت والوصول إلى خدمات Microsoft السحابية. لا تستبعد عنوان URL `*.blob.core.windows.net` من أي نوع من فحص الشبكة.

> [!NOTE]
> توفر خدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender حماية محدثة للشبكة ونقاط النهاية. يجب عدم اعتبار الخدمة السحابية حماية فقط لملفاتك المخزنة في السحابة؛ بدلا من ذلك، تستخدم الخدمة السحابية الموارد الموزعة والتعلم الآلي لتوفير الحماية لنقاط النهاية بمعدل أسرع من تحديثات معلومات الأمان التقليدية.

## <a name="services-and-urls"></a>الخدمات وعناوين URL

يسرد الجدول الموجود في هذا القسم الخدمات وعناوين مواقع الويب المقترنة بها (URLs).

تأكد من عدم وجود جدار حماية أو قواعد تصفية شبكة تمنع الوصول إلى عناوين URL هذه. وإلا، يجب إنشاء قاعدة السماح خصيصا لعناوين URL هذه (باستثناء عنوان URL `*.blob.core.windows.net`). تستخدم عناوين URL في الجدول التالي المنفذ 443 للاتصال.

<br/><br/>

|الخدمة والوصف|URL|
|---|---|
|يشار إلى برنامج الحماية من الفيروسات من Microsoft Defender خدمة الحماية التي توفرها السحابة على أنها Microsoft Active Protection Service (MAPS).<p> يستخدم برنامج الحماية من الفيروسات من Microsoft Defender خدمة MAPS لتوفير الحماية المقدمة من السحابة.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|Microsoft Update Service (MU) وخدمة Windows Update (WU) <p>ستسمح هذه الخدمات بذكاء الأمان وتحديثات المنتجات.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> لمزيد من المعلومات، راجع [نقاط نهاية الاتصال Windows Update](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|تحديث معلومات الأمان لموقع التنزيل البديل (ADL)<p>هذا موقع بديل برنامج الحماية من الفيروسات من Microsoft Defender تحديثات معلومات الأمان، إذا كان التحليل الذكي للأمان المثبت قديما (سبعة أيام أو أكثر بعد ذلك).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|تخزين إرسال البرامج الضارة <p>هذا موقع تحميل للملفات المرسلة إلى Microsoft عبر نموذج الإرسال أو نموذج الإرسال التلقائي.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|قائمة إبطال الشهادات (CRL) <p> Windows استخدام هذه القائمة أثناء إنشاء اتصال SSL ب MAPS لتحديث CRL.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|مخزن الرموز <p>برنامج الحماية من الفيروسات من Microsoft Defender استخدام مخزن الرموز لاستعادة بعض الملفات الهامة أثناء تدفقات المعالجة.|`https://msdl.microsoft.com/download/symbols`|
|عميل القانون العام لحماية البيانات (GDPR) العام <p> Windows استخدام هذا العميل لإرسال البيانات التشخيصية للعميل. <p> تستخدم برنامج الحماية من الفيروسات من Microsoft Defender "القانون العام لحماية البيانات" لأغراض جودة المنتج والمراقبة.|يستخدم التحديث SSL (منفذ TCP 443) لتنزيل البيانات وتحميل البيانات التشخيصية إلى Microsoft التي تستخدم نقاط نهاية DNS التالية: <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>التحقق من صحة الاتصالات بين الشبكة والسحابة

بعد السماح بعناوين URL المدرجة، اختبر ما إذا كنت متصلا بخدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender. اختبر أن عناوين URL تقوم بالإبلاغ عن المعلومات وتلقيها بشكل صحيح للتأكد من أنك محمي بالكامل.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>استخدام أداة cmdline للتحقق من صحة الحماية المقدمة من السحابة

استخدم الوسيطة التالية مع الأداة المساعدة لسطر الأوامر برنامج الحماية من الفيروسات من Microsoft Defender (`mpcmdrun.exe`) للتحقق من إمكانية اتصال شبكتك بخدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender:

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> افتح موجه الأوامر كمسؤول. انقر بزر الماوس الأيمن فوق العنصر في قائمة **البدء** ، وانقر فوق **"تشغيل كمسؤول** " ثم انقر فوق **"نعم** " في موجه الأذونات. سيعمل هذا الأمر على Windows 10 أو الإصدار 1703 أو الإصدارات الأحدث أو Windows 11 فقط.

لمزيد من المعلومات، راجع [إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام أداة سطر الأوامر mpcmdrun.exe](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>محاولة تنزيل ملف برامج ضارة مزيفة من Microsoft

يمكنك تنزيل نموذج ملف سيكتشفه برنامج الحماية من الفيروسات من Microsoft Defender ويحظره إذا كنت متصلا بشكل صحيح بالسحابة. تفضل بزيارة [https://aka.ms/ioavtest](https://aka.ms/ioavtest) لتنزيل الملف.

> [!NOTE]
> الملف الذي تم تنزيله ليس برنامجا ضارا بالضبط. إنه ملف مزيف مصمم لاختبار ما إذا كنت متصلا بشكل صحيح بالسحابة.

إذا كنت متصلا بشكل صحيح، فسترى إعلاما برنامج الحماية من الفيروسات من Microsoft Defender التحذير.

إذا كنت تستخدم Microsoft Edge، فسترى أيضا رسالة إعلام:

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="الإعلام الذي يفيد بأنه تم العثور على البرامج الضارة في Edge" lightbox="../../media/wdav-bafs-edge.png":::

تظهر رسالة مماثلة إذا كنت تستخدم Internet Explorer:

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="إعلام Microsoft Defender AV بأنه تم العثور على برامج ضارة" lightbox="../../media/wdav-bafs-ie.png":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>عرض الكشف عن البرامج الضارة المزيفة في تطبيق أمن Windows

1. على شريط المهام، حدد أيقونة Shield، وافتح تطبيق **أمن Windows**. أو ابحث في **قائمة البدء** عن *الأمان*.

2. حدد **الحماية من الفيروسات &،** ثم حدد **محفوظات الحماية**.

3. ضمن قسم **التهديدات المعزولة** ، حدد **"See full history** " لمشاهدة البرامج الضارة المزيفة المكتشفة.

   > [!NOTE]
   > إصدارات Windows 10 قبل الإصدار 1703 لها واجهة مستخدم مختلفة. راجع [برنامج الحماية من الفيروسات من Microsoft Defender في تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md).

   سيظهر سجل أحداث Windows أيضا [معرف حدث عميل Windows Defender 1116](troubleshoot-microsoft-defender-antivirus.md).

    > [!TIP]
    > إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
    > - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
    > - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
    > - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
    > - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
    > - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
    > - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
    > - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)


## <a name="see-also"></a>راجع أيضًا

- [تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت Microsoft Defender لنقطة النهاية](configure-proxy-internet.md)
- [استخدام إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها](use-group-policy-microsoft-defender-antivirus.md)
- [التغييرات المهمة في نقطة نهاية Microsoft Active Protection Services](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 