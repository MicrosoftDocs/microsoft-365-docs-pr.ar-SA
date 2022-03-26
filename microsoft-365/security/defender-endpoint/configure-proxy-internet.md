---
title: تكوين إعدادات اتصال الإنترنت ووكيل الجهاز
description: قم بتكوين وكيل Microsoft Defender لإعدادات الإنترنت ووكيل نقطة النهاية لتمكين الاتصال بالخدمة السحابية.
keywords: تكوين، وكيل، الإنترنت، اتصال الإنترنت، الإعدادات، إعدادات الوكيل، الشبكة، winhttp، خادم الوكيل
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d687273a3029f3de080f06f328d4d40853142353
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/18/2022
ms.locfileid: "63570159"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>تكوين إعدادات اتصال الإنترنت ووكيل الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

يتطلب مستشعر Defender for Endpoint من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات المستشعر والتواصل مع خدمة Defender for Endpoint. يتم تشغيل مستشعر Defender for Endpoint المضمن في سياق النظام باستخدام حساب LocalSystem. يستخدم المستشعر Microsoft Windows HTTP Services (WinHTTP) لتمكين التواصل مع خدمة السحابة Defender for Endpoint.

> [!TIP]
> بالنسبة إلى المؤسسات التي تستخدم تكاتف إعادة توجيه كبوابة إلى الإنترنت، يمكنك استخدام حماية الشبكة للتحقق من أحداث الاتصال التي تقع خلف تكاتف [إعادة توجيه](investigate-behind-proxy.md).

يكون إعداد تكوين WinHTTP مستقلا عن إعدادات وكيل الاستعراض Windows Internet (WinINet) (راجع [WinINet مقابل WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). ويمكنه اكتشاف خادم وكيل فقط باستخدام أساليب الاكتشاف التالية:

- أساليب الاكتشاف التلقائي:

  - وكيل شفاف
  
  - بروتوكول الاكتشاف التلقائي لوكيل ويب (WPAD)

    > [!NOTE]
    > إذا كنت تستخدم وكيل شفاف أو WPAD في طبولوجيا الشبكة، فلا تحتاج إلى إعدادات تكوين خاصة. لمزيد من المعلومات حول استثناءات URL ل Defender لنقطة النهاية في الوكيل، راجع تمكين الوصول إلى عناوين URL لخدمة [Defender لنقطة النهاية في الخادم الوكيل](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- تكوين وكيل ثابت يدوي:

  - تكوين مستند إلى السجل
  
  - تم تكوين WinHTTP باستخدام الأمر netsh: مناسب فقط لأسطح المكتب في طبولوجيا ثابتة (على سبيل المثال: سطح مكتب في شبكة شركة خلف الوكيل نفسه)

> [!NOTE]
> يمكن تعيين الكشف التلقائي والاستجابة على النقط النهائية الحماية من الفيروسات ومهارة الحماية من الفيروسات بشكل مستقل.  في المقاطع التالية، كن على دراية بهذه التمييزات.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>تكوين الخادم الوكيل يدويا باستخدام وكيل ثابت مستند إلى السجل

قم بتكوين وكيل ثابت يستند إلى السجل ل "أداة استشعار الكشف عن نقاط النهاية ل Defender" (الكشف التلقائي والاستجابة على النقط النهائية) للتقارير حول البيانات التشخيصية والتواصل مع Defender لخدمات نقطة النهاية إذا لم يسمح للكمبيوتر بالاتصال بالإنترنت.

> [!NOTE]
> عند استخدام هذا الخيار على Windows 10 أو Windows 11 أو Windows Server 2019 أو Windows Server 2022، من المستحسن أن يكون لديك إصدار التحديث التراكمي والبنية التالية (أو إصدار أحدث):
>
> - Windows 11
> - الإصدار 1809 من Windows 10 أو Windows Server 2019 أو Windows Server 2022 -<https://support.microsoft.com/kb/5001384>
> - Windows 10، الإصدار 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10، الإصدار 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10، الإصدار 20H2 -<https://support.microsoft.com/kb/4601382>
>
> تحسن هذه التحديثات اتصال قناة CnC (الأمر والتحكم) ووثوقيتها.

يكون الوكيل الثابت قابلا للتكوين من خلال نهج المجموعة (GP)، ويجب تكوين الإعدادين ضمن قيم نهج المجموعة إلى الخادم الوكيل لاستخدام الكشف التلقائي والاستجابة على النقط النهائية. يتوفر نهج المجموعة في القوالب الإدارية.

- **القوالب الإدارية > Windows مكونات >** البيانات والمعاينة > تكوين استخدام الوكيل المصادق عليه لخدمة استخدام المستخدمين المتصلين وبيانات الاستخدام.

  قم بتعيينه **إلى تمكين** وحدد **تعطيل استخدام الوكيل المصادق عليه**.

  ![صورة لإعداد نهج المجموعة1.](images/atp-gpo-proxy1.png)

- **القوالب الإدارية > Windows مكونات >** البيانات وبناءات المعاينة > تكوين تجارب المستخدمين المتصلة وبيانات بيانات الاستخدام:

  تكوين الوكيل.

  ![صورة لإعداد نهج المجموعة2.](images/atp-gpo-proxy2.png)


| نهج المجموعة | مفتاح التسجيل | إدخال السجل | القيمة |
|:---|:---|:---|:---|
| تكوين استخدام الوكيل المصادق له لتجربة المستخدم المتصلة وخدمة بيانات الاستخدام | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| تكوين تجارب المستخدمين المتصلة و بيانات بيانات الاستخدام | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> على سبيل المثال: ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>تكوين وكيل ثابت برنامج الحماية من الفيروسات من Microsoft Defender

برنامج الحماية من الفيروسات من Microsoft Defender [الحماية التي يتم توفيرها](cloud-protection-microsoft-defender-antivirus.md) عبر السحابة حماية فورية وأتمتة من التهديدات الجديدة والناشئة. تجدر الإشارة إلى أن الاتصال مطلوب للمؤشرات [المخصصة عندما يكون](manage-indicators.md) Defender Antivirus هو الحل النشط لمكافحة البرامج الضارة. على [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md) حل أساسي لمكافحة البرامج الضارة عند استخدام حل غير Microsoft.

تكوين الوكيل الثابت باستخدام نهج المجموعة المتوفر في القوالب الإدارية:

1. **القوالب الإدارية > Windows مكونات > برنامج الحماية من الفيروسات من Microsoft Defender > تعريف الخادم الوكيل للاتصال بالشبكة**. 

2. قم **بتعيينه إلى Enabled** وحدد الخادم الوكيل. ملاحظة، يجب أن يحتوي عنوان URL على http:// أو https://. للحصول على الإصدارات المعتمدة https://، راجع [إدارة برنامج الحماية من الفيروسات من Microsoft Defender التحديثات](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="الخادم الوكيل برنامج الحماية من الفيروسات من Microsoft Defender.":::

3. ضمن مفتاح التسجيل، `HKLM\Software\Policies\Microsoft\Windows Defender`يحدد النهج قيمة `ProxyServer` السجل REG_SZ. 

   تأخذ قيمة السجل `ProxyServer` تنسيق السلسلة التالي:

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> لأغراض مرونة ولطبيعة الحماية التي يتم تسليمها من السحابة في الوقت الحقيقي، برنامج الحماية من الفيروسات من Microsoft Defender ذاكرة التخزين المؤقت لأخير وكيل عمل معروف. تأكد من أن حل الوكيل لا يقوم بإجراء فحص SSL. سيقطع هذا الاتصال السحابي الآمن. 
>
> برنامج الحماية من الفيروسات من Microsoft Defender استخدام الوكيل الثابت للاتصال Windows التحديث أو Microsoft Update لتنزيل التحديثات. بدلا من ذلك، سيستخدم وكيلا على مستوى النظام إذا تم تكوينه لاستخدام Windows التحديث، أو مصدر التحديث الداخلي الذي تم تكوينه وفقا للت ترتيب الاحتياطي [الذي تم تكوينه](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> إذا لزم الأمر، يمكنك استخدام القوالب الإدارية > Windows مكونات > برنامج الحماية من الفيروسات من Microsoft Defender > تعريف المؤتمرات التلقائية للوكيل **(pac.)** للاتصال بالشبكة. إذا كنت بحاجة إلى إعداد تكوينات متقدمة مع عدة وكيلين، فاستخدم القوالب الإدارية > Windows **مكونات > برنامج الحماية من الفيروسات من Microsoft Defender > تعريف** العناوين لتجاوز الخادم الوكيل ومنع برنامج الحماية من الفيروسات من Microsoft Defender استخدام خادم وكيل لتلك الوجهات. 
>
> يمكنك استخدام PowerShell مع `Set-MpPreference` cmdlet لتكوين هذه الخيارات: 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - ProxyServer 

> [!NOTE]
> لاستخدام الوكيل بشكل صحيح، قم بتكوين إعدادات الوكيل الثلاثة المختلفة هذه:
>  - Microsoft Defender لنقطة النهاية (MDE)
>  - AV (Antivirus)
>  - الكشف عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>تكوين الخادم الوكيل يدويا باستخدام الأمر netsh

استخدم الشبكة لتكوين وكيل ثابت على مستوى النظام.

> [!NOTE]
>
> - سيؤثر هذا على جميع التطبيقات بما في ذلك Windows التي تستخدم WinHTTP مع الوكيل الافتراضي.</br>
> - ستعطل أجهزة الكمبيوتر المحمولة التي تغير طبولوجيا (على سبيل المثال: من Office إلى home) باستخدام أمر الشبكة. استخدم تكوين الوكيل الثابت المستند إلى السجل.

1. فتح سطر أوامر مرتفع:
   1. انتقل إلى **ابدأ** وا اكتب **cmd**.
   1. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

2. أدخل الأمر التالي واضغط على **Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   على سبيل المثال: `netsh winhttp set proxy 10.0.0.6:8080`

لإعادة تعيين وكيل winhttp، أدخل الأمر التالي واضغط على **Enter**:

```PowerShell
netsh winhttp reset proxy
```

راجع [بناء جملة أوامر Netsh والسياقات وتنسيق لمعرفة](/windows-server/networking/technologies/netsh/netsh-contexts) المزيد.

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>تمكين الوصول إلى عناوين URL لخدمة Microsoft Defender لنقطة النهاية في الخادم الوكيل

بشكل افتراضي، إذا كان الوكيل أو جدار الحماية يمنع كل حركة المرور بشكل افتراضي ويسمح فقط بمجالات معينة، أضف المجالات المدرجة في الورقة القابلة للتنزيل إلى قائمة المجالات المسموح بها.

يسرد جدول البيانات القابل للتنزيل التالي الخدمات وقوائم URL المقترنة بها التي يجب أن تتمكن شبكتك من الاتصال بها. تأكد من عدم وجود جدار حماية أو قواعد لتصفية الشبكة لرفض الوصول إلى عناوين URL هذه. اختياري، قد تحتاج إلى إنشاء قاعدة *السماح* لهم بشكل خاص.

<br>

**** 
|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|قائمة URL ل Microsoft Defender لنقطة النهاية للعملاء التجاريين| جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| قائمة URL ل Microsoft Defender لنقطة النهاية لعملاء Gov/سحابة القطاع الحكومي/DoD | جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

إذا تم تمكين فحص HTTPS (فحص SSL) للوكيل أو جدار الحماية، فاستبعد المجالات المدرجة في الجدول أعلاه من فحص HTTPS.
في جدار الحماية، افتح كل عناوين URL حيث العمود الجغرافي هو WW. بالنسبة للصفوف التي لا يكون العمود الجغرافي فيها "WW"، افتح عناوين URL إلى موقع البيانات المحدد. للتحقق من إعداد موقع البيانات، راجع التحقق من موقع تخزين البيانات وتحديث إعدادات استبقاء البيانات [ل Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows الأجهزة التي تعمل بالإصدار 1803 أو الاحتياجات السابقة`settings-win.data.microsoft.com`.  <br>
>
> لا يلزم استخدام عناوين URL التي تتضمن الإصدار 20 منها إلا إذا كان لديك Windows تعمل بالإصدار 1803 أو إصدار أحدث. على سبيل المثال`us-v20.events.data.microsoft.com`، هناك حاجة لجهاز Windows يعمل بالإصدار 1803 أو الإصدارات الأحدث ومخزن في منطقة "تخزين البيانات الأمريكية".
>

إذا كان الوكيل أو جدار الحماية يمنع حركة مرور مجهولة كمستشعر Defender لنقطة النهاية، وكان متصلا من سياق النظام للتأكد من أن حركة المرور المجهولة مسموح بها في عناوين URL المدرجة سابقا.

> [!NOTE]
> لا توفر Microsoft خادما وكيلا. يمكن الوصول إلى عناوين URL هذه عبر الخادم الوكيل الذي تقوم بتكوينه.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) - متطلبات الوكيل وجدار الحماية للإصدارات القديمة من Windows أو Windows Server

المعلومات في قائمة معلومات تكوين الوكيل وجدار الحماية مطلوبة للتواصل مع وكيل Log Analytics (يشار إليه غالبا ب Microsoft Monitoring Agent) للإصدارات السابقة من Windows، مثل Windows 7 SP1 و Windows 8.1 و Windows Server 2008 R2*.

<br>

****

|مورد الوكيل|المنافذ|الاتجاه|تجاوز فحص HTTPS|
|---|---|---|---|
|*.ods.opinsights.azure.com|المنفذ 443|الصادر|نعم|
|*.oms.opinsights.azure.com|المنفذ 443|الصادر|نعم|
|*.blob.core.windows.net|المنفذ 443|الصادر|نعم|
|*.azure-automation.net|المنفذ 443|الصادر|نعم|

> [!NOTE]
> *تنطبق متطلبات الاتصال هذه على Microsoft Defender السابق لنقطة نهاية Windows Server 2016، Windows Server 2012 R2 الذي يتطلب MMA. توجد إرشادات لتكوين أنظمة التشغيل هذه بالحل الموحد الجديد في خوادم [Onboard Windows](configure-server-endpoints.md)، أو الترحيل إلى الحل الموحد الجديد في سيناريوهات ترحيل [الخادم في Microsoft Defender ل Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> كحل مستند إلى السحابة، يمكن أن يتغير نطاق IP. من المستحسن الانتقال إلى إعداد حل DNS.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>تأكيد متطلبات URL لخدمة وكيل مراقبة Microsoft (MMA) 

 راجع الإرشادات التالية لإزالة متطلبات أحرف البدل (*) لبيئة معينة عند استخدام Microsoft Monitoring Agent (MMA) للإصدارات السابقة من Windows.

1. تشغيل نظام تشغيل سابق باستخدام "وكيل مراقبة Microsoft" (MMA) في Defender for Endpoint (لمزيد من المعلومات، راجع تشغيل الإصدارات السابقة من [Windows على Defender ل Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2010326) وخادم [Onboard Windows).](configure-server-endpoints.md)

2. تأكد من أن الجهاز قد نجح في Microsoft 365 Defender المدخل.

3. يمكنك تشغيل TestCloudConnection.exe من "C:\Program Files\Microsoft Monitoring Agent\Agent" للتحقق من الاتصال، والحصول على عناوين URL المطلوبة لمساحة العمل المحددة.

4. تحقق من قائمة عناوين URL الخاصة بنقطة النهاية ل Microsoft Defender للحصول على قائمة المتطلبات الكاملة لم والمنطقة (راجع جدول بيانات عناوين URL [للخدمة](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)).

    ![صورة المسؤول في Windows PowerShell.](images/admin-powershell.png)

يمكن استبدال أحرف البدل (\*) \*المستخدمة في .ods.opinsights.azure.com \*و .oms.opinsights.azure.com \*و .agentsvc.azure-automation.net نقاط نهاية URL بمحددات "مساحة العمل". إن "معرّف مساحة العمل" خاص ببيئة ومساحة العمل. يمكن العثور عليه في قسم "التكهين" للمستأجر داخل Microsoft 365 Defender المدخل.

يمكن \*blob.core.windows.net نقطة نهاية URL. مع عناوين URL الموضحة في المقطع "قاعدة جدار الحماية: \*.blob.core.windows.net" من نتائج الاختبار.

> [!NOTE]
> في حالة التكهين عبر Microsoft Defender for Cloud، يمكن استخدام مساحات عمل متعددة. ستحتاج إلى تنفيذ إجراء TestCloudConnection.exe على الجهاز المعمل من كل مساحة عمل (لتحديد ما إذا كانت هناك أي تغييرات على عناوين URL *.blob.core.windows.net بين مساحات العمل).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>التحقق من اتصال العميل مع عناوين URL لخدمة Microsoft Defender لنقطة النهاية

تحقق من اكتمال تكوين الوكيل بنجاح. يمكن ل WinHTTP بعد ذلك اكتشاف الخادم الوكيل في بيئتك والتواصل معه، ومن ثم سيسمح الخادم الوكيل ب نقل البيانات إلى عناوين URL لخدمة Defender for Endpoint.

1. قم [بتنزيل أداة محلل عميل Microsoft Defender لنقطة](https://aka.ms/mdeanalyzer) النهاية إلى الكمبيوتر الشخصي، حيث يتم تشغيل أداة استشعار Defender لنقطة النهاية. بالنسبة للخوادم على المستوى الراقي، يمكنك استخدام إصدار المعاينة الأخير لتنزيل [أداة Microsoft Defender for Endpoint Client Analyzer Beta](https://aka.ms/BetaMDEAnalyzer).

2. استخراج محتويات MDEClientAnalyzer.zip على الجهاز.

3. فتح سطر أوامر مرتفع:
   1. انتقل إلى **ابدأ** وا اكتب **cmd**.
   1. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

4. أدخل الأمر التالي واضغط على **Enter**:

    ```PowerShell
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    *استبدل HardDrivePath* بالمسار، حيث تم تنزيل أداة MDEClientAnalyzer. على سبيل المثال:

    ```PowerShell
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. تقوم الأداة بإنشاء *MDEClientAnalyzerResult.zipالملف في* المجلد لاستخدامه في *HardDrivePath*.

6. افتح *MDEClientAnalyzerResult.txt* وتحقق من تنفيذ خطوات تكوين الوكيل لتمكين اكتشاف الخادم والوصول إلى عناوين URL للخدمة.

   تحقق الأداة من اتصال Defender for Endpoint service URLs. تأكد من تكوين عميل Defender for Endpoint للتفاعل. ستطبع الأداة النتائج في ملف *MDEClientAnalyzerResult.txtلكل عنوان* URL يمكن استخدامه للتواصل مع خدمات Defender for Endpoint. على سبيل المثال:

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

إذا كان أحد خيارات الاتصال يرجع حالة (200)، يمكن عندئذ للعميل Defender for Endpoint التواصل مع عنوان URL الذي تم اختباره بشكل صحيح باستخدام أسلوب الاتصال هذا.

ومع ذلك، إذا كانت نتائج التحقق من الاتصال تشير إلى فشل، يتم عرض خطأ HTTP (راجع رموز حالة HTTP). يمكنك بعد ذلك استخدام عناوين URL في الجدول الموضح في تمكين الوصول إلى عناوين URL لخدمة [Defender for Endpoint في الخادم الوكيل](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). تعتمد عناوين URL المتوفرة للاستخدام على المنطقة المحددة أثناء إجراء التوفر.

> [!NOTE]
> لا تتوافق عمليات التحقق من الاتصال السحابي الخاصة بأداة "محلل الاتصال" مع عمليات حظر عمليات حظر قواعد تقليل مساحة الهجوم التي تنشأ من [أوامر PSExec و WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands). ستحتاج إلى تعطيل هذه القاعدة مؤقتا، لتشغيل أداة الاتصال. بدلا من ذلك، يمكنك إضافة استثناءات [ASR مؤقتا](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) عند تشغيل المحلل.
>
> عندما يتم تعيين TelemetryProxyServer في السجل أو عبر نهج المجموعة، سيتراجع Defender for Endpoint، ويفشل في الوصول إلى الوكيل المحدد.

## <a name="related-articles"></a>المقالات ذات الصلة

- [استخدم إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md)
- [أجهزة Windows](configure-endpoints.md)
- [استكشاف مشاكل تشغيل نقطة النهاية وإصلاحها في Microsoft Defender](troubleshoot-onboarding.md)
