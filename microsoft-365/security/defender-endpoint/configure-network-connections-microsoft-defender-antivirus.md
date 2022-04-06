---
title: تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها
description: قم بتكوين الاتصال بالخدمة برنامج الحماية من الفيروسات من Microsoft Defender السحابية واختباره.
keywords: مكافحة الفيروسات، برنامج الحماية من الفيروسات من Microsoft Defender، الحماية من البرامج الضارة، الأمان، defender، السحابة، الهمة، مستوى الحماية
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
ms.openlocfilehash: f29cf5f77acd52a4ff3ccc8384f3c64861e48b64
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63583236"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

للتأكد من برنامج الحماية من الفيروسات من Microsoft Defender الحماية التي يتم تسليمها عبر السحابة بشكل صحيح، يجب على فريق الأمان تكوين الشبكة للسماح للاتصالات بين نقاط النهاية وبعض خوادم Microsoft. تسرد هذه المقالة الاتصالات التي يجب السماح باستخدام قواعد جدار الحماية. كما يوفر إرشادات للتحقق من اتصالك. يضمن تكوين الحماية بشكل صحيح حصولك على أفضل قيمة من خدمات الحماية المقدمة من السحابة.

> [!IMPORTANT]
> تحتوي هذه المقالة على معلومات حول تكوين اتصالات الشبكة فقط برنامج الحماية من الفيروسات من Microsoft Defender. إذا كنت تستخدم Microsoft Defender لنقطة النهاية (التي تتضمن برنامج الحماية من الفيروسات من Microsoft Defender)، فحدد تكوين إعدادات اتصال الإنترنت ووكيل [الجهاز ل Defender لنقطة النهاية](configure-proxy-internet.md).


> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>السماح للاتصالات بالخدمة السحابية برنامج الحماية من الفيروسات من Microsoft Defender السحابية

توفر برنامج الحماية من الفيروسات من Microsoft Defender السحابية حماية سريعة وقوية لنقاط النهاية. من الاختياري تمكين خدمة الحماية التي يتم تسليمها من السحابة. برنامج الحماية من الفيروسات من Microsoft Defender خدمة السحابة، لأنها توفر حماية هامة من البرامج الضارة على نقاط النهاية والشبكات. لمزيد من المعلومات، راجع [](enable-cloud-protection-microsoft-defender-antivirus.md) تمكين الحماية التي يتم توفيرها من السحابة لتمكين الخدمة باستخدام Intune أو Microsoft Endpoint Configuration Manager أو نهج المجموعة أو PowerShell cmdlets أو العملاء الفرديين في أمن Windows التطبيق.

بعد تمكين الخدمة، ستحتاج إلى تكوين الشبكة أو جدار الحماية للسماح للاتصالات بين الشبكة ونقاط النهاية. نظرا لأن حمايتك هي خدمة سحابية، يجب أن يكون لأجهزة الكمبيوتر حق الوصول إلى الإنترنت والوصول إلى خدمات Microsoft السحابية. لا تستبعد عنوان URL `*.blob.core.windows.net` من أي نوع من عمليات فحص الشبكة.

> [!NOTE]
> توفر برنامج الحماية من الفيروسات من Microsoft Defender السحابية حماية محدثة للشبكة ونقاط النهاية. يجب عدم اعتبار الخدمة السحابية بمثابة حماية فقط للملفات المخزنة في السحابة؛ بدلا من ذلك، تستخدم الخدمة السحابية الموارد الموزعة والتعلم الآلي لتقديم الحماية لنقاط النهاية بمعدل أسرع من تحديثات معلومات الأمان التقليدية.

## <a name="services-and-urls"></a>الخدمات ومواعيد URL

يسرد الجدول في هذا القسم الخدمات وعناوين مواقع الويب المقترنة بها (عناوين URL).

تأكد من عدم وجود جدار حماية أو قواعد لتصفية الشبكة تحرم الوصول إلى عناوين URL هذه. وبخلاف ذلك، يجب إنشاء قاعدة السماح الخاصة عناوين URL هذه (باستثناء عنوان URL `*.blob.core.windows.net`). تستخدم عناوين URL في الجدول التالي المنفذ 443 للاتصال.

<br/><br/>

|الخدمة والوصف|URL|
|---|---|
|برنامج الحماية من الفيروسات من Microsoft Defender خدمة الحماية التي يتم تسليمها عبر السحابة باسم Microsoft Active Protection Service (الخرائط).<p> تستخدم برنامج الحماية من الفيروسات من Microsoft Defender خدمة الخرائط لتوفير حماية يتم تسليمها من السحابة.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|خدمة Microsoft Update (MU) Windows Update Service (WU) <p>ستسمح هذه الخدمات بتحديثات معلومات الأمان و المنتج.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> لمزيد من المعلومات، راجع نقاط [نهاية الاتصال Windows التحديث](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|تحديثات معلومات الأمان موقع التنزيل البديل (ADL)<p>هذا موقع بديل لتحديثات برنامج الحماية من الفيروسات من Microsoft Defender الأمان، إذا كانت معلومات الأمان المثبتة غير محدثة (أي بعد سبعة أيام أو أكثر).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|تخزين إرسال البرامج الضارة <p>هذا موقع تحميل للملفات المرسلة إلى Microsoft عبر نموذج الإرسال أو إرسال العينة التلقائي.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|قائمة إلغاء الشهادة (CRL) <p> Windows استخدام هذه القائمة أثناء إنشاء اتصال SSL ب MAPS لتحديث CRL.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|متجر الرموز <p>برنامج الحماية من الفيروسات من Microsoft Defender استخدام 'متجر الرموز' لاستعادة بعض الملفات الهامة أثناء تدفقات المعالجة.|`https://msdl.microsoft.com/download/symbols`|
|عميل GDPR العام <p> Windows استخدام هذا العميل لإرسال بيانات العميل التشخيصية. <p> برنامج الحماية من الفيروسات من Microsoft Defender "القانون العام لحماية البيانات" لأغراض مراقبة وجودة المنتج.|يستخدم التحديث SSL (منفذ TCP 443) لتنزيل البيانات وتحميل البيانات التشخيصية إلى Microsoft التي تستخدم نقاط نهاية DNS التالية: <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>التحقق من صحة الاتصالات بين الشبكة والسحابة

بعد السماح بإدراج عناوين URL، اختبر ما إذا كنت متصلا برنامج الحماية من الفيروسات من Microsoft Defender السحابية. اختبار تقوم عناوين URL بالإبلاغ عن المعلومات وتلقيها بشكل صحيح للتأكد من أنك محمي بالكامل.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>استخدام أداة cmdline للتحقق من الحماية التي يتم تسليمها من السحابة

استخدم الوسيطة التالية مع الأداة المساعدة برنامج الحماية من الفيروسات من Microsoft Defender سطر الأوامر (`mpcmdrun.exe`) للتحقق من أن شبكتك يمكنها التواصل مع برنامج الحماية من الفيروسات من Microsoft Defender السحابة:

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> افتح موجه الأوامر كمسؤول. انقر بضغطة زر الماوس الأيمن فوق العنصر في قائمة **البدء،** وانقر فوق **تشغيل كمسؤول** ، ثم انقر فوق **نعم** في مطالبة الأذونات. لن يعمل هذا الأمر إلا على Windows 10 أو الإصدار 1703 أو الإصدارات الأحدث أو Windows 11.

لمزيد من المعلومات، [راجع إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام أداة mpcmdrun.exe الأوامر](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>محاولة تنزيل ملف برامج ضارة زائفة من Microsoft

يمكنك تنزيل نموذج ملف برنامج الحماية من الفيروسات من Microsoft Defender كشفه وحظره إذا كنت متصلا بشكل صحيح بالسحابة. تفضل [https://aka.ms/ioavtest](https://aka.ms/ioavtest) بزيارة لتنزيل الملف.

> [!NOTE]
> لا يحتوي الملف الذي تم تنزيله على البرامج الضارة بالضبط. إنه ملف زائف مصمم لاختبار ما إذا كنت متصلا بشكل صحيح بالسحابة.

إذا كنت متصلا بشكل صحيح، فسوف ترى تحذيرا برنامج الحماية من الفيروسات من Microsoft Defender إعلام.

إذا كنت تستخدم Microsoft Edge، سترى أيضا رسالة إعلام:

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="لقطة شاشة للإعلام بأنه تم العثور على البرامج الضارة في Azure IoT Edge.":::

تحدث رسالة مماثلة إذا كنت تستخدم Internet Explorer:

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="إعلام Microsoft Defender AV بأنه تم العثور على البرامج الضارة.":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>عرض الكشف عن البرامج الضارة الزائفة في تطبيقك أمن Windows

1. على شريط المهام، حدد أيقونة درع **،** وافتح أمن Windows التطبيق. أو ابحث في **البدء** عن *الأمان*.

2. حدد **الحماية & الحماية من** المخاطر، ثم حدد **محفوظات الحماية**.

3. ضمن القسم **التهديدات المعزولة** ، حدد **الاطلاع على المحفوظات الكاملة** لرؤية البرامج الضارة الزائفة التي تم الكشف عنها.

   > [!NOTE]
   > إصدارات Windows 10 قبل الإصدار 1703 لديها واجهة مستخدم مختلفة. راجع [برنامج الحماية من الفيروسات من Microsoft Defender في أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md).

   سيعرض Windows الأحداث أيضا Windows [حدث عميل Defender 1116](troubleshoot-microsoft-defender-antivirus.md).

## <a name="see-also"></a>راجع أيضًا

- [تكوين إعدادات اتصال الإنترنت ووكيل الجهاز ل Microsoft Defender لنقطة النهاية](configure-proxy-internet.md)
- [استخدم إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md)
- [التغييرات الهامة في نقطة نهاية خدمات Microsoft Active Protection](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 