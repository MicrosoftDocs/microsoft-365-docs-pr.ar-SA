---
title: تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت
description: تكوين وكيل Microsoft Defender لنقطة النهاية وإعدادات الإنترنت لتمكين الاتصال بخدمة السحابة.
keywords: التكوين والوكيل والإنترنت والاتصال بالإنترنت والإعدادات وإعدادات الوكيل وnetsh وwinhttp والخادم الوكيل
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
ms.openlocfilehash: 1faff638c9b33b933277dc74248c2d7daa43331c
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669661"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

يتطلب مستشعر Defender لنقطة النهاية من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات أداة الاستشعار والتواصل مع خدمة Defender لنقطة النهاية. يتم تشغيل مستشعر Defender لنقطة النهاية المضمن في سياق النظام باستخدام حساب LocalSystem. يستخدم جهاز الاستشعار Microsoft Windows HTTP Services (WinHTTP) لتمكين الاتصال بخدمة سحابة Defender لنقطة النهاية.

> [!TIP]
> بالنسبة للمؤسسات التي تستخدم وكلاء إعادة التوجيه كبوابة إلى الإنترنت، يمكنك استخدام حماية الشبكة [للتحقيق في أحداث الاتصال التي تحدث خلف وكلاء إعادة التوجيه](investigate-behind-proxy.md).

إعداد تكوين WinHTTP مستقل عن إعدادات وكيل استعراض الإنترنت Windows (WinINet) (انظر[، WinINet مقابل WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). يمكنه فقط اكتشاف خادم وكيل باستخدام أساليب الاكتشاف التالية:

- أساليب الاكتشاف التلقائي:

  - وكيل شفاف
  
  - بروتوكول الاكتشاف التلقائي ل وكيل ويب (WPAD)

    > [!NOTE]
    > إذا كنت تستخدم وكيلا شفافا أو WPAD في مخطط الشبكة، فلن تحتاج إلى إعدادات تكوين خاصة. لمزيد من المعلومات حول استثناءات عنوان URL ل Defender لنقطة النهاية في الوكيل، راجع [تمكين الوصول إلى عناوين URL لخدمة Defender لنقطة النهاية في الخادم الوكيل](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- تكوين وكيل ثابت يدوي:

  - التكوين المستند إلى التسجيل
  
  - تم تكوين WinHTTP باستخدام أمر netsh: مناسب فقط لأجهزة سطح المكتب في طوبولوجيا مستقرة (على سبيل المثال: سطح مكتب في شبكة شركة خلف نفس الوكيل)

> [!NOTE]
> يمكن تعيين برنامج الحماية من الفيروسات ووكلاء الكشف التلقائي والاستجابة على النقط النهائية Defender بشكل مستقل.  في الأقسام التالية، كن على دراية بهذه الفروق.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>تكوين الخادم الوكيل يدويا باستخدام وكيل ثابت يستند إلى التسجيل

تكوين وكيل ثابت يستند إلى التسجيل لأداة استشعار Defender للكشف عن نقاط النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) للإبلاغ عن البيانات التشخيصية والتواصل مع Defender لخدمات نقطة النهاية إذا لم يسمح لجهاز كمبيوتر بالاتصال بالإنترنت.

> [!NOTE]
> عند استخدام هذا الخيار على Windows 10 أو Windows 11 أو Windows Server 2019 أو Windows Server 2022، يوصى بطرح التحديث التراكمي والإنشاء التالي (أو الأحدث):
>
> - Windows 11
> - الإصدار 1809 من Windows 10 أو Windows Server 2019 أو Windows Server 2022 -<https://support.microsoft.com/kb/5001384>
> - Windows 10، الإصدار 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10، الإصدار 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10، الإصدار 20H2 -<https://support.microsoft.com/kb/4601382>
>
> تعمل هذه التحديثات على تحسين اتصال قناة CnC (Command and Control) وموثوقيتها.

يمكن تكوين الوكيل الثابت من خلال نهج المجموعة (GP)، يجب تكوين الإعدادين ضمن قيم نهج المجموعة إلى الخادم الوكيل لاستخدام الكشف التلقائي والاستجابة على النقط النهائية. يتوفر نهج المجموعة في القوالب الإدارية.

- **القوالب الإدارية > Windows المكونات > إصدارات تجميع البيانات ومعاينتها > تكوين استخدام الوكيل المصادق عليه لخدمة "تجربة المستخدم المتصل" و"بيانات تتبع الاستخدام**".

  قم بتعيينه إلى **Enabled** وحدد **Disable Authenticated Proxy usage**.

  :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="جزء الحالة نهج المجموعة setting1" lightbox="images/atp-gpo-proxy1.png":::

- **القوالب الإدارية > Windows المكونات > إصدارات تجميع البيانات ومعاينتها > تكوين تجارب المستخدم المتصلة وبيانات تتبع الاستخدام**:

  تكوين الوكيل.

  :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="جزء حالة إعداد2 نهج المجموعة" lightbox="images/atp-gpo-proxy2.png":::


| نهج المجموعة | مفتاح التسجيل | إدخال التسجيل | قيمه |
|:---|:---|:---|:---|
| تكوين استخدام الوكيل المصادق عليه لتجربة المستخدم المتصل وخدمة بيانات تتبع الاستخدام | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| تكوين تجارب المستخدم المتصلة وبيانات تتبع الاستخدام | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> على سبيل المثال: ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>تكوين وكيل ثابت برنامج الحماية من الفيروسات من Microsoft Defender

توفر برنامج الحماية من الفيروسات من Microsoft Defender [الحماية المقدمة من السحابة](cloud-protection-microsoft-defender-antivirus.md) حماية تلقائية شبه فورية ضد التهديدات الجديدة والناشئة. ملاحظة، الاتصال مطلوب [للمؤشرات المخصصة](manage-indicators.md) عندما يكون Defender Antivirus هو حل مكافحة البرامج الضارة النشط. بالنسبة [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)، يحتوي الحل الأساسي لمكافحة البرامج الضارة عند استخدام حل غير Microsoft.

تكوين الوكيل الثابت باستخدام نهج المجموعة المتوفرة في القوالب الإدارية:

1. > برنامج الحماية من الفيروسات من Microsoft Defender > **القوالب الإدارية > Windows المكونات تعريف خادم وكيل للاتصال بالشبكة**. 

2. قم بتعيينه إلى **Enabled** وتعريف الخادم الوكيل. ملاحظة، يجب أن يحتوي URL على http:// أو https://. للحصول على الإصدارات المعتمدة https://، راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="الخادم الوكيل برنامج الحماية من الفيروسات من Microsoft Defender" lightbox="images/proxy-server-mdav.png":::

3. ضمن مفتاح `HKLM\Software\Policies\Microsoft\Windows Defender`التسجيل، يعين النهج قيمة `ProxyServer` السجل كقيمة REG_SZ. 

   تأخذ قيمة `ProxyServer` التسجيل تنسيق السلسلة التالي:

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> لأغراض المرونة والطبيعة في الوقت الحقيقي للحماية المقدمة من السحابة، سيقوم برنامج الحماية من الفيروسات من Microsoft Defender بتخزين آخر وكيل عمل معروف مؤقتا. تأكد من أن حل الوكيل الخاص بك لا يقوم بفحص SSL. سيؤدي ذلك إلى قطع اتصال السحابة الآمن. 
>
> لن يستخدم برنامج الحماية من الفيروسات من Microsoft Defender الوكيل الثابت للاتصال Windows Update أو Microsoft Update لتنزيل التحديثات. بدلا من ذلك، سيستخدم وكيلا على مستوى النظام إذا تم تكوينه لاستخدام Windows Update، أو مصدر التحديث الداخلي الذي تم تكوينه وفقا [للأمر الاحتياطي الذي تم تكوينه](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> إذا لزم الأمر، يمكنك استخدام **القوالب الإدارية > Windows المكونات > برنامج الحماية من الفيروسات من Microsoft Defender > تعريف التكوين التلقائي للوكيل (.pac)** للاتصال بالشبكة. إذا كنت بحاجة إلى إعداد تكوينات متقدمة مع وكلاء متعددين، فاستخدم **القوالب الإدارية > Windows المكونات > برنامج الحماية من الفيروسات من Microsoft Defender > تعريف العناوين** لتجاوز الخادم الوكيل ومنع برنامج الحماية من الفيروسات من Microsoft Defender من استخدام خادم وكيل لتلك الوجهات. 
>
> يمكنك استخدام PowerShell مع `Set-MpPreference` cmdlet لتكوين هذه الخيارات: 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - ProxyServer 

> [!NOTE]
> لاستخدام الوكيل بشكل صحيح، قم بتكوين إعدادات الوكيل الثلاثة المختلفة التالية:
>  - Microsoft Defender لنقطة النهاية (MDE)
>  - AV (برنامج الحماية من الفيروسات)
>  - الكشف عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>تكوين الخادم الوكيل يدويا باستخدام أمر netsh

استخدم netsh لتكوين وكيل ثابت على مستوى النظام.

> [!NOTE]
>
> - سيؤثر هذا على جميع التطبيقات بما في ذلك خدمات Windows التي تستخدم WinHTTP مع الوكيل الافتراضي.</br>
> - ستعطل أجهزة الكمبيوتر المحمولة التي تقوم بتغيير الطبولوجيا (على سبيل المثال: من مكتب إلى منزل) مع أمر netsh. استخدم تكوين الوكيل الثابت المستند إلى التسجيل.

1. فتح سطر أوامر غير مقيد:
   1. انتقل إلى **شاشة البدء** واكتب **cmd**.
   1. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

2. أدخل الأمر التالي واضغط على **مفتاح الإدخال Enter**:

   ```command prompt
   netsh winhttp set proxy <proxy>:<port>
   ```

   على سبيل المثال: `netsh winhttp set proxy 10.0.0.6:8080`

لإعادة تعيين وكيل winhttp، أدخل الأمر التالي واضغط على **مفتاح الإدخال Enter**:

```command prompt
netsh winhttp reset proxy
```

راجع بناء [جملة أوامر Netsh والسياقات والتنسيق](/windows-server/networking/technologies/netsh/netsh-contexts) لمعرفة المزيد.

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>تمكين الوصول إلى عناوين URL للخدمة Microsoft Defender لنقطة النهاية في الخادم الوكيل

بشكل افتراضي، إذا كان الوكيل أو جدار الحماية يمنع كل نسبة استخدام الشبكة بشكل افتراضي ويسمح بمجالات معينة فقط، فقم بإضافة المجالات المدرجة في الورقة القابلة للتنزيل إلى قائمة المجالات المسموح بها.

يسرد جدول البيانات التالي القابل للتنزيل الخدمات وعناوين URL المقترنة بها التي يجب أن تكون شبكتك قادرة على الاتصال بها. تأكد من عدم وجود جدار حماية أو قواعد تصفية الشبكة لرفض الوصول لعناوين URL هذه. اختياري، قد تحتاج إلى إنشاء قاعدة *السماح* خصيصا لهم.

<br>

|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|Microsoft Defender لنقطة النهاية قائمة URL للعملاء التجاريين| جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender لنقطة النهاية قائمة URL ل Gov/سحابة القطاع الحكومي/DoD | جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

إذا قام وكيل أو جدار حماية بتمكين فحص HTTPS (فحص SSL)، فاستبعد المجالات المدرجة في الجدول أعلاه من مسح HTTPS.
في جدار الحماية الخاص بك، افتح كافة عناوين URL حيث العمود الجغرافي هو WW. بالنسبة إلى الصفوف التي لا يكون فيها عمود الجغرافيا WW، افتح عناوين URL لموقع البيانات المحدد. للتحقق من إعداد موقع البيانات، راجع [التحقق من موقع تخزين البيانات وتحديث إعدادات استبقاء البيانات Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows الأجهزة التي تعمل بالإصدار 1803 أو الاحتياجات `settings-win.data.microsoft.com`السابقة.  <br>
>
> لا يلزم وجود عناوين URL التي تتضمن الإصدار 20 فيها إلا إذا كان لديك أجهزة Windows تعمل بالإصدار 1803 أو إصدار أحدث. على سبيل المثال، `us-v20.events.data.microsoft.com` مطلوب لجهاز Windows يعمل بالإصدار 1803 أو إصدار أحدث وملحق بمنطقة تخزين البيانات الأمريكية.
>

إذا كان وكيل أو جدار حماية يمنع حركة المرور المجهولة كمستشعر Defender لنقطة النهاية، ويتم الاتصال من سياق النظام للتأكد من السماح بنسبة استخدام الشبكة المجهولة في عناوين URL المدرجة مسبقا.

> [!NOTE]
> لا توفر Microsoft خادم وكيل. يمكن الوصول إلى عناوين URL هذه عبر الخادم الوكيل الذي تقوم بتكوينه.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>عامل مراقبة Microsoft (MMA) - متطلبات الوكيل وجدار الحماية للإصدارات القديمة من عميل Windows أو خادم Windows

المعلومات الموجودة في قائمة معلومات تكوين الوكيل وجدار الحماية مطلوبة للاتصال بعامل Log Analytics (يشار إليه غالبا باسم عامل مراقبة Microsoft) للإصدارات السابقة من Windows، مثل Windows 7 SP1 و Windows 8.1 و Windows Server 2008 R2*.

<br>

****

|مورد عامل|المنافذ|الاتجاه|تجاوز فحص HTTPS|
|---|---|---|---|
|*.ods.opinsights.azure.com|المنفذ 443|الصادره|نعم|
|*.oms.opinsights.azure.com|المنفذ 443|الصادره|نعم|
|*.blob.core.windows.net|المنفذ 443|الصادره|نعم|
|*.azure-automation.net|المنفذ 443|الصادره|نعم|

> [!NOTE]
> *تنطبق متطلبات الاتصال هذه على Microsoft Defender لنقطة النهاية السابقة لخادم Windows 2016 وخادم Windows 2012 R2 الذي يتطلب MMA. توجد التعليمات لإلحاق أنظمة التشغيل هذه بالحل الموحد الجديد في [خوادم Windows](configure-server-endpoints.md)، أو الترحيل إلى الحل الموحد الجديد في [سيناريوهات ترحيل الخادم في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> كحل مستند إلى السحابة، يمكن أن يتغير نطاق IP. من المستحسن الانتقال إلى إعداد حل DNS.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>تأكيد متطلبات URL لخدمة عامل مراقبة Microsoft (MMA) 

 راجع الإرشادات التالية لإزالة متطلبات حرف البدل (*) للبيئة الخاصة بك عند استخدام عامل مراقبة Microsoft (MMA) للإصدارات السابقة من Windows.

1. إلحاق نظام تشغيل سابق مع عامل مراقبة Microsoft (MMA) في Defender لنقطة النهاية (لمزيد من المعلومات، راجع [إلحاق الإصدارات السابقة من Windows على Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2010326) [وخوادم Windows الإلحاق](configure-server-endpoints.md)).

2. تأكد من أن الجهاز يقوم بالإبلاغ بنجاح في مدخل Microsoft 365 Defender.

3. قم بتشغيل أداة TestCloudConnection.exe من "C:\Program Files\Microsoft Monitoring Agent\Agent" للتحقق من الاتصال، والحصول على عناوين URL المطلوبة لمساحة العمل الخاصة بك.

4. تحقق من قائمة عناوين URL Microsoft Defender لنقطة النهاية للحصول على قائمة كاملة بالمتطلبات لمنطقتك (راجع [جدول بيانات عناوين URL للخدمة](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)).

   :::image type="content" source="images/admin-powershell.png" alt-text="المسؤول في Windows PowerShell" lightbox="images/admin-powershell.png":::

يمكن استبدال أحرف البدل (\*) المستخدمة في \*نقاط نهاية .ods.opinsights.azure.com \*و.oms.opinsights.azure.com و.agentsvc.azure-automation.net \*URL بمعرف مساحة العمل المحدد. معرف مساحة العمل خاص بالبيئة ومساحة العمل. يمكن العثور عليه في قسم الإلحاق للمستأجر الخاص بك داخل مدخل Microsoft 365 Defender.

\*يمكن استبدال نقطة نهاية URL blob.core.windows.net. بعناوين URL الموضحة في قسم "قاعدة جدار الحماية: \*.blob.core.windows.net" في نتائج الاختبار.

> [!NOTE]
> في حالة الإلحاق عبر Microsoft Defender for Cloud، يمكن استخدام مساحات عمل متعددة. ستحتاج إلى تنفيذ الإجراء TestCloudConnection.exe على الجهاز المدمج من كل مساحة عمل (لتحديد ما إذا كانت هناك أي تغييرات على عناوين URL *.blob.core.windows.net بين مساحات العمل).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>التحقق من اتصال العميل بعناوين URL للخدمة Microsoft Defender لنقطة النهاية

تحقق من اكتمال تكوين الوكيل بنجاح. يمكن ل WinHTTP بعد ذلك اكتشاف الخادم الوكيل والتواصل من خلال بيئتك، ثم سيسمح الخادم الوكيل بنسبة استخدام الشبكة إلى عناوين URL لخدمة Defender لنقطة النهاية.

1. قم بتنزيل [أداة محلل العميل Microsoft Defender لنقطة النهاية](https://aka.ms/mdeanalyzer) إلى الكمبيوتر الشخصي، حيث يتم تشغيل مستشعر Defender لنقطة النهاية. بالنسبة إلى الخوادم المعطلة، استخدم أحدث إصدار للمعاينة المتوفر للتنزيل [Microsoft Defender لنقطة النهاية أداة Client Analyzer Beta](https://aka.ms/BetaMDEAnalyzer).

2. استخراج محتويات MDEClientAnalyzer.zip على الجهاز.

3. فتح سطر أوامر غير مقيد:
   1. انتقل إلى **شاشة البدء** واكتب **cmd**.
   1. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

4. أدخل الأمر التالي واضغط على **مفتاح الإدخال Enter**:

    ```command prompt
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    استبدل *HardDrivePath* بالمسار، حيث تم تنزيل أداة MDEClientAnalyzer. على سبيل المثال:

    ```command prompt
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. تقوم الأداة بإنشاء ملف *MDEClientAnalyzerResult.zip* واستخراجه في المجلد لاستخدامه في *HardDrivePath*.

6. افتح *MDEClientAnalyzerResult.txt* وتحقق من تنفيذ خطوات تكوين الوكيل لتمكين اكتشاف الخادم والوصول إلى عناوين URL للخدمة.

   تتحقق الأداة من اتصال عناوين URL لخدمة Defender لنقطة النهاية. تأكد من تكوين عميل Defender لنقطة النهاية للتفاعل. ستقوم الأداة بطباعة النتائج في ملف *MDEClientAnalyzerResult.txt* لكل عنوان URL يمكن استخدامه للتواصل مع خدمات Defender لنقطة النهاية. على سبيل المثال:

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

إذا أرجع أي من خيارات الاتصال حالة (200)، يمكن لعميل Defender for Endpoint الاتصال ب URL الذي تم اختباره بشكل صحيح باستخدام أسلوب الاتصال هذا.

ومع ذلك، إذا كانت نتائج التحقق من الاتصال تشير إلى فشل، يتم عرض خطأ HTTP (راجع رموز حالة HTTP). يمكنك بعد ذلك استخدام عناوين URL في الجدول الموضح في [تمكين الوصول إلى عناوين URL لخدمة Defender لنقطة النهاية في الخادم الوكيل](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). ستعتمد عناوين URL المتوفرة للاستخدام على المنطقة المحددة أثناء إجراء الإلحاق.

> [!NOTE]
> لا تتوافق عمليات التحقق من الاتصال السحابي لأداة محلل الاتصال مع [عمليات إنشاء قاعدة تقليل الأجزاء المعرضة للهجوم التي تنشأ من أوامر PSExec وWMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands). ستحتاج إلى تعطيل هذه القاعدة مؤقتا، لتشغيل أداة الاتصال. بدلا من ذلك، يمكنك إضافة [استثناءات ASR](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) مؤقتا عند تشغيل المحلل.
>
> عند تعيين TelemetryProxyServer في Registry أو عبر نهج المجموعة، سيتراجع Defender for Endpoint، ويفشل في الوصول إلى الوكيل المحدد.

## <a name="related-articles"></a>المقالات ذات الصلة

- [استخدام إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها](use-group-policy-microsoft-defender-antivirus.md)
- [إلحاق أجهزة Windows](configure-endpoints.md)
- [استكشاف أخطاء إلحاق Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-onboarding.md)
