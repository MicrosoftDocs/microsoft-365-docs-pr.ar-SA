---
title: إعداد نشر Microsoft Defender لنقطة النهاية
description: تعرف على كيفية إعداد النشر Microsoft Defender لنقطة النهاية
keywords: التوزيع، والإعداد، والتحقق من صحة الترخيص، وتكوين المستأجر، وتكوين الشبكة
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
ms.openlocfilehash: bae66223494d8de98737516cef1a2c407d7d1a6a
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783504"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>إعداد نشر Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

نشر Defender لنقطة النهاية هو عملية من ثلاث مراحل:

|[![مرحلة التوزيع - التحضير.](images/phase-diagrams/prepare.png#lightbox)](prepare-deployment.md)<br>[المرحلة 1: التحضير](prepare-deployment.md) | ![مرحلة التوزيع - الإعداد](images/phase-diagrams/setup.png#lightbox)<br>المرحلة 2: الإعداد | [![مرحلة التوزيع - الإلحاق](images/phase-diagrams/onboard.png#lightbox)](onboarding.md)<br>[المرحلة 3: التجهيز للاستخدام](onboarding.md)|
|---|---|---|
||*أنت هنا!*||

أنت حاليا في مرحلة الإعداد.

في سيناريو النشر هذا، سيتم إرشادك خلال الخطوات التالية:

- التحقق من صحة الترخيص
- تكوين المستأجر
- تكوين الشبكة

> [!NOTE]
> لغرض توجيهك من خلال نشر نموذجي، سيغطي هذا السيناريو فقط استخدام Microsoft Endpoint Configuration Manager. يدعم Defender لنقطة النهاية استخدام أدوات الإلحاق الأخرى ولكنه لن يغطي هذه السيناريوهات في دليل النشر. لمزيد من المعلومات، راجع [إلحاق الأجهزة Microsoft Defender لنقطة النهاية](onboard-configure.md).

## <a name="check-license-state"></a>التحقق من حالة الترخيص

يمكن التحقق من حالة الترخيص وما إذا تم توفيرها بشكل صحيح، من خلال مركز الإدارة أو من خلال **مدخل Microsoft Azure**.

1. لعرض التراخيص، انتقل إلى **مدخل Microsoft Azure** وانتقل إلى [قسم ترخيص مدخل Microsoft Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="images/atp-licensing-azure-portal.png" alt-text="صفحة ترخيص Azure" lightbox="images/atp-licensing-azure-portal.png":::

1. بدلا من ذلك، في مركز الإدارة، انتقل إلى **اشتراكات** **الفوترة**\>.

    على الشاشة، سترى جميع التراخيص المتوفرة وحالتها **الحالية**.

    :::image type="content" source="images/atp-billing-subscriptions.png" alt-text="صفحة تراخيص الفوترة" lightbox="images/atp-billing-subscriptions.png":::

## <a name="cloud-service-provider-validation"></a>التحقق من صحة موفر خدمة السحابة

للوصول إلى التراخيص التي يتم توفيرها لشركتك، وللتحقق من حالة التراخيص، انتقل إلى مركز الإدارة.

1. من **مدخل الشريك**، حدد **إدارة الخدمات > Office 365**.

2. سيؤدي النقر فوق ارتباط **مدخل الشريك** إلى فتح خيار **"المسؤول نيابة عن** " وسيمنحك حق الوصول إلى مركز إدارة العملاء.

   :::image type="content" source="images/atp-O365-admin-portal-customer.png" alt-text="مدخل مسؤول Office 365" lightbox="images/atp-O365-admin-portal-customer.png":::

## <a name="tenant-configuration"></a>تكوين المستأجر

الإلحاق Microsoft Defender لنقطة النهاية أمر سهل. من قائمة التنقل، حدد أي عنصر ضمن قسم نقاط النهاية، أو أي ميزة Microsoft 365 Defender مثل Incidents أو Hunting أو Action center أو Threat analytics لبدء عملية الإلحاق.

من مستعرض ويب، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>.

## <a name="data-center-location"></a>موقع مركز البيانات
سيقوم Microsoft Defender لنقطة النهاية بتخزين البيانات ومعالجتها في [نفس الموقع الذي تستخدمه Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable). إذا لم يتم تشغيل Microsoft 365 Defender بعد، فسيؤدي الإلحاق إلى Microsoft Defender لنقطة النهاية أيضا إلى تشغيل Microsoft 365 Defender ويتم تحديد موقع مركز بيانات جديد تلقائيا استنادا إلى موقع Microsoft 365 النشطة  خدمات الأمان. يظهر موقع مركز البيانات المحدد على الشاشة.

## <a name="network-configuration"></a>تكوين الشبكة

إذا لم تطلب المؤسسة نقاط النهاية لاستخدام وكيل للوصول إلى الإنترنت، فتخطى هذا القسم.

يتطلب مستشعر Microsoft Defender لنقطة النهاية من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات جهاز الاستشعار والتواصل مع خدمة Microsoft Defender لنقطة النهاية. يتم تشغيل مستشعر Microsoft Defender لنقطة النهاية المضمن في سياق النظام باستخدام حساب LocalSystem. يستخدم جهاز الاستشعار Microsoft Windows HTTP Services (WinHTTP) لتمكين الاتصال بخدمة السحابة Microsoft Defender لنقطة النهاية. إعداد تكوين WinHTTP مستقل عن إعدادات وكيل استعراض إنترنت Windows (WinINet) ويمكنه فقط اكتشاف خادم وكيل باستخدام أساليب الاكتشاف التالية:

- **أساليب الاكتشاف التلقائي**:
  - وكيل شفاف
  - بروتوكول الكشف التلقائي ل وكيل ويب (WPAD)

  إذا تم تنفيذ وكيل شفاف أو WPAD في مخطط الشبكة، فلا حاجة لإعدادات تكوين خاصة. لمزيد من المعلومات حول استثناءات عنوان URL Microsoft Defender لنقطة النهاية في الوكيل، راجع قسم [عناوين URL لخدمة الوكيل](production-deployment.md#proxy-service-urls) في هذا المستند لعناوين URL المسموح بها أو على [إعدادات تكوين وكيل الجهاز والاتصال بالإنترنت](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **تكوين وكيل ثابت يدوي**:
  - التكوين المستند إلى التسجيل
  - تم تكوين WinHTTP باستخدام أمر netsh

    مناسب فقط لأجهزة سطح المكتب في طوبولوجيا مستقرة (على سبيل المثال: سطح مكتب في شبكة شركة خلف نفس الوكيل).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>تكوين الخادم الوكيل يدويا باستخدام وكيل ثابت يستند إلى التسجيل

تكوين وكيل ثابت يستند إلى التسجيل للسماح فقط لأداة استشعار Microsoft Defender لنقطة النهاية بالإبلاغ عن البيانات التشخيصية والتواصل مع خدمات Microsoft Defender لنقطة النهاية إذا لم يسمح لجهاز كمبيوتر بالاتصال بالإنترنت. يمكن تكوين الوكيل الثابت من خلال نهج المجموعة (GP). يمكن العثور على نهج المجموعة ضمن:

- تقوم القوالب \> الإدارية Windows إصدارات تجميع البيانات والمعاينة للمكونات \> \> بتكوين استخدام الوكيل المصادق عليه لخدمة "تجربة المستخدم المتصل" و"بيانات تتبع الاستخدام"
- تعيينه إلى **"ممكن"** وحدد **"تعطيل استخدام الوكيل المصادق عليه**"

1. افتح وحدة تحكم إدارة نهج المجموعة.
2. إنشاء نهج أو تحرير نهج موجود استنادا إلى الممارسات التنظيمية.
3. قم بتحرير نهج المجموعة وانتقل إلى **القوالب \> الإدارية Windows تكوين إصدارات معاينة وجمع البيانات للمكونات \> \> وتكوين استخدام الوكيل المصادق عليه لخدمة "تجربة المستخدم المتصل" و"بيانات تتبع الاستخدام**".

   :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="الخيارات المتعلقة بتكوين نهج الاستخدام" lightbox="images/atp-gpo-proxy1.png":::

4. حدد **ممكن**.
5. حدد **تعطيل استخدام الوكيل المصادق عليه**.
6. انتقل إلى **القوالب \> الإدارية Windows إنشاءات معاينة وجمع البيانات للمكونات \> \> وتكوين تجارب المستخدم المتصلة وبيانات تتبع الاستخدام**.

   :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="الخيارات المتعلقة بتكوين تجربة المستخدم المتصلة وبيانات تتبع الاستخدام" lightbox="images/atp-gpo-proxy2.png":::

7. حدد **ممكن**.
8. أدخل **اسم الخادم الوكيل**.

يعين النهج قيمتي `TelemetryProxyServer` تسجيل كقيم REG_SZ وك `DisableEnterpriseAuthProxy` REG_DWORD ضمن مفتاح `HKLM\Software\Policies\Microsoft\Windows\DataCollection`التسجيل.

تأخذ قيمة `TelemetryProxyServer` التسجيل تنسيق السلسلة التالي:

```text
<server name or ip>:<port>
```

على سبيل المثال: 10.0.0.6:8080

يجب تعيين قيمة `DisableEnterpriseAuthProxy` التسجيل إلى 1.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>تكوين الخادم الوكيل يدويا باستخدام أمر netsh

استخدم netsh لتكوين وكيل ثابت على مستوى النظام.

> [!NOTE]
>
> - سيؤثر هذا على جميع التطبيقات بما في ذلك خدمات Windows التي تستخدم WinHTTP مع الوكيل الافتراضي.
> - ستعطل أجهزة الكمبيوتر المحمولة التي تغير الطبولوجيا (على سبيل المثال: من مكتب إلى منزل) مع netsh. استخدم تكوين الوكيل الثابت المستند إلى التسجيل.

1. فتح سطر أوامر غير مقيد:
    1. انتقل إلى **شاشة البدء** واكتب **cmd**.
    1. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

2. أدخل الأمر التالي واضغط على **مفتاح الإدخال Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   على سبيل المثال: netsh winhttp set proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>تكوين الوكيل للأجهزة ذات المستوى الأدنى

تتضمن أجهزة Down-Level Windows 7 SP1 ومحطات عمل Windows 8.1 بالإضافة إلى Windows Server 2008 R2 وأنظمة تشغيل الخادم الأخرى التي تم إلحاقها مسبقا باستخدام عامل مراقبة Microsoft. سيكون لدى أنظمة التشغيل هذه الوكيل الذي تم تكوينه كجزء من عامل إدارة Microsoft للتعامل مع الاتصال من نقطة النهاية إلى Azure. راجع دليل النشر السريع لعامل إدارة Microsoft للحصول على معلومات حول كيفية تكوين وكيل على هذه الأجهزة.

### <a name="proxy-service-urls"></a>عناوين URL لخدمة الوكيل

لا يلزم وجود عناوين URL التي تتضمن الإصدار 20 فيها إلا إذا كان لديك أجهزة Windows 10 أو الإصدار 1803 أو Windows 11. على سبيل المثال، `us-v20.events.data.microsoft.com` مطلوب فقط إذا كان الجهاز في Windows 10 أو الإصدار 1803 أو Windows 11.

إذا كان الوكيل أو جدار الحماية يمنع حركة المرور المجهولة، حيث يتصل جهاز الاستشعار Microsoft Defender لنقطة النهاية من سياق النظام، فتأكد من السماح بنسبة استخدام الشبكة المجهولة في عناوين URL المدرجة.

يسرد جدول البيانات التالي القابل للتنزيل الخدمات وعناوين URL المقترنة بها التي يجب أن تكون شبكتك قادرة على الاتصال بها. تأكد من عدم وجود جدار حماية أو قواعد تصفية شبكة من شأنها رفض الوصول إلى عناوين URL هذه، أو قد تحتاج إلى إنشاء قاعدة *سماح* خاصة بها.

<br>

****


|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|Microsoft Defender لنقطة النهاية قائمة URL للعملاء التجاريين| جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender لنقطة النهاية قائمة URL ل Gov/سحابة القطاع الحكومي/DoD | جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

## <a name="next-step"></a>الخطوة التالية

[![**المرحلة 3: إلحاق**.](images/onboard.png#lightbox)] <br> [المرحلة 3: إلحاق](onboarding.md) الأجهزة للخدمة بحيث يمكن لخدمة Microsoft Defender لنقطة النهاية الحصول على بيانات المستشعر منها.
