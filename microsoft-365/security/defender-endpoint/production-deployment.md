---
title: إعداد Microsoft Defender لنشر نقطة النهاية
description: تعرف على كيفية إعداد النشر ل Microsoft Defender لنقطة النهاية
keywords: النشر والإعداد والتحقق من صحة الترخيص وتكوين المستأجر وتكوين الشبكة
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
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c59e07e1d11be406c1f954a656cef7b32fa2851f
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63575781"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>إعداد Microsoft Defender لنشر نقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

عملية نشر Defender لنقطة النهاية هي عملية من ثلاث مراحل:

|[![مرحلة النشر - التحضير.](images/phase-diagrams/prepare.png)](prepare-deployment.md)<br>[المرحلة 1: التحضير](prepare-deployment.md) | ![مرحلة النشر - الإعداد](images/phase-diagrams/setup.png)<br>المرحلة الثانية: الإعداد | [![مرحلة النشر - على اللوحة](images/phase-diagrams/onboard.png)](onboarding.md)<br>[المرحلة 3: Onboard](onboarding.md)|
|---|---|---|
||*أنت هنا!*||

أنت حاليا في مرحلة إعداد.

في سيناريو النشر هذا، سيتم إرشادك عبر الخطوات التالية:

- التحقق من صحة الترخيص
- تكوين المستأجر
- تكوين الشبكة

> [!NOTE]
> لغرض إرشادك عبر عملية نشر نموذجية، سيغطي هذا السيناريو فقط استخدام Microsoft Endpoint Configuration Manager. يدعم Defender ل Endpoint استخدام أدوات التكوين الأخرى ولكنه لن يغطي هذه السيناريوهات في دليل النشر. لمزيد من المعلومات، راجع [الأجهزة المجهزة ل Microsoft Defender لنقطة النهاية](onboard-configure.md).

## <a name="check-license-state"></a>التحقق من حالة الترخيص

التحقق من حالة الترخيص وما إذا تم توفيره بشكل صحيح، يمكن إجراء ذلك من خلال مركز الإدارة أو من خلال **مدخل Microsoft Azure**.

1. لعرض التراخيص، انتقل إلى مدخل **Microsoft Azure** وانتقل إلى قسم [ترخيص مدخل Microsoft Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   ![صورة لصفحة ترخيص Azure.](images/atp-licensing-azure-portal.png)

1. بدلا من ذلك، في مركز الإدارة، انتقل إلى **اشتراكات** \> **الفوترة**.

    على الشاشة، سترى كل التراخيص التي تم توفيرها ووضعها **الحالي**.

    ![صورة لتراخيص الفوترة.](images/atp-billing-subscriptions.png)

## <a name="cloud-service-provider-validation"></a>التحقق من صحة موفر خدمة السحابة

للوصول إلى التراخيص التي يتم توفيرها للشركة، ولتحقق من حالة التراخيص، انتقل إلى مركز الإدارة.

1. من مدخل **الشريك،** حدد **إدارة الخدمات > Office 365**.

2. يؤدي النقر فوق ارتباط **مدخل الشريك** إلى فتح الخيار **المسؤول** بالنيابة عن وسيمنحك إمكانية الوصول إلى مركز إدارة العملاء.

   ![صورة مدخل مسؤول O365.](images/atp-O365-admin-portal-customer.png)

## <a name="tenant-configuration"></a>تكوين المستأجر

من السهل التكهين في Microsoft Defender لنقطة النهاية. من قائمة التنقل، حدد أي عنصر ضمن المقطع نقاط النهاية أو أي ميزة Microsoft 365 Defender مثل الحوادث أو الصيد أو مركز الإجراءات أو تحليل التهديدات لبدء عملية التهيئة.

من مستعرض ويب، انتقل إلى مدخل Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">.</a>

## <a name="data-center-location"></a>موقع مركز البيانات
سيخزن Microsoft Defender for Endpoint البيانات ويمررها في الموقع [نفسه الذي](/microsoft-365/security/defender/m365d-enable) يستخدمه Microsoft 365 Defender. إذا لم Microsoft 365 Defender التشغيل بعد، فإن التكوين في Microsoft Defender لنقطة النهاية سيتم أيضا تشغيل Microsoft 365 Defender، كما يتم تحديد موقع مركز بيانات جديد تلقائيا استنادا إلى موقع خدمات Microsoft 365 النشطة. يظهر موقع مركز البيانات المحدد على الشاشة.

## <a name="network-configuration"></a>تكوين الشبكة

إذا لم تطلب المؤسسة نقاط النهاية لاستخدام وكيل للوصول إلى الإنترنت، فتخطى هذا المقطع.

يتطلب مستشعر Microsoft Defender لنقطة النهاية من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات المستشعر والتواصل مع خدمة Microsoft Defender for Endpoint. يتم تشغيل مستشعر Microsoft Defender المضمن لنقطة النهاية في سياق النظام باستخدام حساب LocalSystem. يستخدم المستشعر Microsoft Windows HTTP Services (WinHTTP) لتمكين التواصل مع خدمة سحابة Microsoft Defender ل Endpoint. يكون إعداد تكوين WinHTTP مستقلا عن إعدادات وكيل استعراض الإنترنت Windows Internet (WinINet) ويمكنه اكتشاف خادم وكيل فقط باستخدام أساليب الاكتشاف التالية:

- **أساليب الاكتشاف التلقائي**:
  - وكيل شفاف
  - بروتوكول Autodiscovery لوكيل ويب (WPAD)

  إذا تم تنفيذ وكيل شفاف أو WPAD في طبولوجيا الشبكة، فلا حاجة لإعدادات تكوين خاصة. للحصول على مزيد من المعلومات حول استثناءات URL ل Microsoft Defender لنقطة النهاية في الوكيل، راجع المقطع عناوين [URL](production-deployment.md#proxy-service-urls) للخدمة الوكيلة في هذا المستند لقائمة السماح عناوين URL أو في تكوين إعدادات وكيل الجهاز واتصال [الإنترنت](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **تكوين وكيل ثابت يدوي**:
  - تكوين مستند إلى السجل
  - تم تكوين WinHTTP باستخدام الأمر netsh

    مناسب فقط لأسطح المكتب في طبولوجيا ثابتة (على سبيل المثال: سطح مكتب في شبكة شركة خلف الوكيل نفسه).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>تكوين الخادم الوكيل يدويا باستخدام وكيل ثابت مستند إلى السجل

قم بتكوين وكيل ثابت يستند إلى السجل للسماح فقط لمستشعر نقطة النهاية ل Microsoft Defender ب الإبلاغ عن البيانات التشخيصية والتواصل مع Microsoft Defender لخدمات نقطة النهاية إذا لم يسمح للكمبيوتر بالاتصال بالإنترنت. يمكن تكوين الوكيل الثابت من خلال نهج المجموعة (GP). يمكن العثور على نهج المجموعة ضمن:

- القوالب الإدارية Windows \> تجميع \> \> البيانات والمكونات ونمط المعاينة تكوين استخدام الوكيل المصادق عليه لخدمة استخدام المستخدمين المتصلين وبيانات بيانات الاستخدام
- قم بتعيينه إلى **"تمكين"** وحدد **"تعطيل استخدام الوكيل المصادق عليه"**

1. افتح وحدة تحكم إدارة نهج المجموعة.
2. إنشاء نهج أو تحرير نهج موجود يستند إلى الممارسات التنظيمية.
3. تحرير نهج المجموعة والانتقال إلى القوالب **الإدارية Windows \> \> إنشاءات المعاينة وجمع البيانات لمكونات تكوين استخدام الوكيل المصادق عليه لخدمة استخدام المستخدمين المتصلين وبيانات الاستخدام.\>**

   ![صورة تكوين نهج المجموعة.](images/atp-gpo-proxy1.png)

4. حدد **تمكين**.
5. حدد **تعطيل استخدام الوكيل المصادق عليه**.
6. انتقل إلى **القوالب \> الإدارية Windows تجميع \> البيانات والمكونات وبناءات \> المعاينة تكوين تجارب المستخدمين المتصلين وبيانات بيانات الاستخدام**.

    ![صورة لإعداد تكوين نهج المجموعة.](images/atp-gpo-proxy2.png)

7. حدد **تمكين**.
8. أدخل **اسم الخادم الوكيل**.

يحدد النهج قيمتي تسجيل `TelemetryProxyServer` REG_SZ كقيم REG_DWORD `DisableEnterpriseAuthProxy` أسفل مفتاح التسجيل `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

تأخذ قيمة السجل `TelemetryProxyServer` تنسيق السلسلة التالي:

```text
<server name or ip>:<port>
```

على سبيل المثال: 10.0.0.6:8080

يجب تعيين قيمة `DisableEnterpriseAuthProxy` السجل إلى 1.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>تكوين الخادم الوكيل يدويا باستخدام الأمر netsh

استخدم الشبكة لتكوين وكيل ثابت على مستوى النظام.

> [!NOTE]
>
> - سيؤثر هذا على جميع التطبيقات بما في ذلك Windows التي تستخدم WinHTTP مع الوكيل الافتراضي.
> - ستعطل أجهزة الكمبيوتر المحمولة التي تغير طبولوجيا (على سبيل المثال: من Office إلى home) باستخدام الشبكة. استخدم تكوين الوكيل الثابت المستند إلى السجل.

1. فتح سطر أوامر مرتفع:
    1. انتقل إلى **ابدأ** وا اكتب **cmd**.
    1. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

2. أدخل الأمر التالي واضغط على **Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   على سبيل المثال: netsh winhttp set proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>تكوين الوكيل للأجهزة ذات المستوى الأسفل

تتضمن أجهزة Down-Level محطات عمل Windows 7 SP1 و Windows 8.1 بالإضافة إلى Windows Server 2008 R2 و Windows Server 2012 و Windows Server 2012 R2 و إصدارات Windows Server 2016 قبل Windows Server CB 1803. ستقوم أنظمة التشغيل هذه بتكوين الوكيل كجزء من وكيل إدارة Microsoft لمعالجة الاتصالات من نقطة النهاية إلى Azure. راجع دليل النشر السريع لعامل إدارة Microsoft للحصول على معلومات حول كيفية تكوين وكيل على هذه الأجهزة.

### <a name="proxy-service-urls"></a>عناوين URL لخدمة الوكيل

لا يلزم استخدام عناوين URL التي تتضمن الإصدار 20 منها إلا إذا كان لديك Windows 10 أو الإصدار 1803 أو Windows 11 الأجهزة. على سبيل المثال، `us-v20.events.data.microsoft.com` لا يلزم استخدام الجهاز إلا إذا كان Windows 10 أو الإصدار 1803 أو Windows 11.

إذا كان الوكيل أو جدار الحماية يمنع حركة مرور مجهولة، حيث أن مستشعر نقطة النهاية من Microsoft Defender يتصل من سياق النظام، فتأكد من أن حركة المرور المجهولة مسموح بها في عناوين URL المدرجة.

يسرد جدول البيانات القابل للتنزيل التالي الخدمات وقوائم URL المقترنة بها التي يجب أن تتمكن شبكتك من الاتصال بها. تأكد من عدم وجود جدار حماية أو قواعد لتصفية الشبكة من شأنها رفض الوصول إلى عناوين URL هذه، أو قد تحتاج إلى إنشاء قاعدة السماح  خاصة بها.

<br>

****


|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|قائمة URL ل Microsoft Defender لنقطة النهاية للعملاء التجاريين | جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| قائمة URL ل Microsoft Defender لنقطة النهاية لعملاء Gov/سحابة القطاع الحكومي/DoD| جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|

## <a name="next-step"></a>الخطوة التالية

![**المرحلة 3: Onboard**.](images/onboard.png) <br> [المرحلة 3: Onboard](onboarding.md): الأجهزة المجهزة للخدمة حتى تتمكن خدمة Microsoft Defender for Endpoint من الحصول على بيانات المستشعر منها.
