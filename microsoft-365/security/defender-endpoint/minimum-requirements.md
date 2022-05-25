---
title: الحد الأدنى من متطلبات Microsoft Defender لنقطة النهاية
description: فهم متطلبات الترخيص ومتطلبات إلحاق الأجهزة للخدمة
keywords: الحد الأدنى من المتطلبات والترخيص وجدول المقارنة
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 355fc0f367c415ae679259195e18ff3920812f4a
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670147"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>الحد الأدنى من متطلبات Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-minreqs-abovefoldlink)

هناك بعض المتطلبات الدنيا لإلحاق الأجهزة للخدمة. تعرف على متطلبات الترخيص والأجهزة والبرامج وإعدادات التكوين الأخرى لإلحاق الأجهزة للخدمة.

> [!TIP]
>
> - تصف هذه المقالة الحد الأدنى من متطلبات Microsoft Defender لنقطة النهاية الخطة 2. إذا كنت تبحث عن معلومات حول Defender لنقطة النهاية الخطة 1، فراجع [متطلبات Defender لنقطة النهاية الخطة 1](mde-p1-setup-configuration.md#review-the-requirements).
> - تعرف على أحدث التحسينات في Defender لنقطة النهاية: [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - أظهر Defender لنقطة النهاية قدرات الكشف والبصريات الرائدة في الصناعة في تقييم MITRE الأخير. قراءة: [Insights من التقييم المستند إلى MITRE ATT&CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>متطلبات الترخيص
للحصول على متطلبات ترخيص المعلومات Microsoft Defender لنقطة النهاية، راجع [Microsoft Defender لنقطة النهاية معلومات الترخيص](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).


للحصول على معلومات تفصيلية حول الترخيص، راجع [موقع "شروط المنتج"](https://www.microsoft.com/licensing/terms/) والعمل مع فريق حسابك لمعرفة المزيد حول الشروط والأحكام.

لمزيد من المعلومات حول صفيف الميزات في إصدارات Windows، راجع [مقارنة إصدارات Windows](https://www.microsoft.com/windowsforbusiness/compare).

## <a name="browser-requirements"></a>متطلبات المستعرض

يتم الوصول إلى Defender لنقطة النهاية من خلال مستعرض يدعم المستعرضات التالية:

- Microsoft Edge
- Google Chrome

> [!NOTE]
> على الرغم من أن المستعرضات الأخرى قد تعمل، فإن المستعرضات المذكورة هي المستعرضات المدعومة.

## <a name="hardware-and-software-requirements"></a>متطلبات الأجهزة والبرامج

### <a name="supported-windows-versions"></a>إصدارات Windows المدعومة

- Windows 7 SP1 Enterprise ([يتطلب ESU للدعم](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 7 SP1 Pro ([يتطلب ESU للدعم](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 8.1 Enterprise
- Windows 8.1 Pro
- Windows 11 Enterprise
- Windows 11 Education
- Windows 11 Pro
- Windows 11 Pro Education
- Windows 10 Enterprise
- [Windows 10 Enterprise LTSC 2016 (أو أحدث)](/windows/whats-new/ltsc/)
- Windows 10 Enterprise IoT

    >[!NOTE]
    >على الرغم من أن Windows 10 IoT Enterprise هو نظام تشغيل مدعوم في Microsoft Defender لنقطة النهاية ويمكن الشركات المصنعة للمعدات الأصلية/ODMs من توزيعها كجزء من منتجاتها أو حلولها، يجب على العملاء اتباع إرشادات OEM/ODM حول البرامج المثبتة المستندة إلى المضيف وقابلية الدعم.

- Windows 10 Education
- Windows 10 Pro
- Windows 10 Pro Education
- خادم Windows
  - Windows Server 2008 R2 SP1 ([يتطلب ESU للدعم](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - Windows Server 2016‏
  - Windows Server، الإصدار 1803 أو أحدث
  - Windows Server 2019
  - Windows Server 2022
- Windows Virtual Desktop
- Windows 365

يجب أن تشغل الأجهزة الموجودة على شبكتك أحد هذه الإصدارات.

متطلبات الأجهزة ل Defender لنقطة النهاية على الأجهزة هي نفسها للإصدارات المدعومة.

> الذاكرات الأساسية: 2 كحد أدنى، 4 ذاكرة مفضلة: 1 غيغابايت كحد أدنى، 4 مفضلة

لمزيد من المعلومات حول الإصدارات المدعومة من Windows 10، راجع (/windows/release-health/release-information).

> [!NOTE]
> الأجهزة التي تقوم بتشغيل إصدارات الأجهزة المحمولة من Windows (مثل Windows CE Windows 10 Mobile) غير مدعومة.
>
> قد تواجه الأجهزة الظاهرية التي تعمل Windows 10 Enterprise 2016 LTSB مشكلات في الأداء إذا تم تشغيلها على الأنظمة الأساسية الظاهرية غير الخاصة ب Microsoft.
>
> بالنسبة للبيئات الظاهرية، نوصي باستخدام Windows 10 Enterprise LTSC 2019 أو الإصدارات الأحدث.

عندما تكون المكونات محدثة على أنظمة تشغيل Microsoft Windows، سيتبع دعم Microsoft Defender لنقطة النهاية دورة حياة نظام التشغيل المعني. لمزيد من المعلومات، راجع [الأسئلة المتداولة حول دورة الحياة](/lifecycle/faq/general-lifecycle). عادة ما يتم توفير الميزات أو القدرات الجديدة فقط على أنظمة التشغيل التي لم تصل بعد إلى نهاية دورة حياتها. سيستمر توفير تحديثات معلومات الأمان (تحديثات التعريف والمحرك) ومنطق الكشف حتى:

- [تاريخ نهاية الدعم](/lifecycle/products/) (لأنظمة التشغيل التي ليس لديها برنامج تحديثات الأمان الموسعة (ESU).
- [نهاية تاريخ ESU](/lifecycle/faq/extended-security-updates) (لأنظمة التشغيل التي لديها برنامج ESU).



### <a name="other-supported-operating-systems"></a>أنظمة التشغيل الأخرى المدعومة

- [الروبوت](microsoft-defender-endpoint-android.md)
- [دائره الرقابه الداخليه](microsoft-defender-endpoint-ios.md)
- [ينكس](microsoft-defender-endpoint-linux.md)
- [macOS](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> ستحتاج إلى تأكيد أن توزيعات Linux وإصدارات Android وiOS macOS متوافقة مع Defender لنقطة النهاية لكي يعمل التكامل.

### <a name="network-and-data-storage-and-configuration-requirements"></a>متطلبات تخزين الشبكة والبيانات وتكوينها

عند تشغيل معالج الإلحاق للمرة الأولى، يجب اختيار مكان تخزين المعلومات المتعلقة Microsoft Defender لنقطة النهاية: في الاتحاد الأوروبي أو المملكة المتحدة أو مركز بيانات الولايات المتحدة.

> [!NOTE]
>
> - لا يمكنك تغيير موقع تخزين البيانات بعد الإعداد لأول مرة.
> - راجع [تخزين البيانات Microsoft Defender لنقطة النهاية والخصوصية](data-storage-privacy.md) لمزيد من المعلومات حول مكان تخزين Microsoft لبياناتك وكيفية تخزينها.

### <a name="diagnostic-data-settings"></a>إعدادات البيانات التشخيصية

> [!NOTE]
> لا يتطلب Microsoft Defender لنقطة النهاية أي مستوى تشخيص محدد طالما تم تمكينه.

تأكد من تمكين خدمة البيانات التشخيصية على جميع الأجهزة في مؤسستك.
بشكل افتراضي، يتم تمكين هذه الخدمة. من الجيد التحقق للتأكد من أنك ستحصل على بيانات المستشعر منها.

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>استخدم سطر الأوامر للتحقق من نوع بدء تشغيل خدمة البيانات التشخيصية Windows

1. افتح موجه سطر أوامر غير مقيد على الجهاز:
   1. انتقل إلى **شاشة البدء** واكتب **cmd**.
   2. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

2. أدخل الأمر التالي، ثم اضغط على **مفتاح الإدخال Enter**:

   ```console
   sc qc diagtrack
   ```

   إذا تم تمكين الخدمة، يجب أن تبدو النتيجة مثل لقطة الشاشة التالية:

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="نتيجة أمر استعلام sc ل diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

ستحتاج إلى تعيين الخدمة للبدء تلقائيا إذا لم يتم تعيين **START_TYPE** إلى **AUTO_START**.

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>استخدام سطر الأوامر لتعيين خدمة البيانات التشخيصية Windows للبدء تلقائيا

1. افتح موجه سطر أوامر غير مقيد على نقطة النهاية:
    1. انتقل إلى **شاشة البدء** واكتب **cmd**.
    2. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

2. أدخل الأمر التالي، ثم اضغط على **مفتاح الإدخال Enter**:

    ```console
    sc config diagtrack start=auto
    ```

3. يتم عرض رسالة نجاح. تحقق من التغيير عن طريق إدخال الأمر التالي، ثم اضغط على **مفتاح الإدخال Enter**:

    ```console
    sc qc diagtrack
    ```

#### <a name="internet-connectivity"></a>الاتصال بالإنترنت

الاتصال بالإنترنت على الأجهزة مطلوب إما مباشرة أو من خلال الوكيل.

يمكن لأداة استشعار Defender لنقطة النهاية استخدام متوسط عرض نطاق ترددي يومي يبلغ 5 ميغابايت للتواصل مع خدمة سحابة Defender لنقطة النهاية والإبلاغ عن البيانات الإلكترونية. لا يتم تضمين الأنشطة لمرة واحدة مثل تحميلات الملفات ومجموعة حزم التحقيق في هذا النطاق الترددي المتوسط اليومي.

لمزيد من المعلومات حول إعدادات تكوين الوكيل الإضافية، راجع [تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت](configure-proxy-internet.md).

قبل إلحاق الأجهزة، يجب تمكين خدمة البيانات التشخيصية. يتم تمكين الخدمة بشكل افتراضي في Windows 10 Windows 11.

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>متطلبات التكوين برنامج الحماية من الفيروسات من Microsoft Defender

يعتمد عامل Defender لنقطة النهاية على قدرة برنامج الحماية من الفيروسات من Microsoft Defender على فحص الملفات وتوفير معلومات عنها.

تكوين تحديثات معلومات الأمان على أجهزة Defender لنقطة النهاية سواء كان برنامج الحماية من الفيروسات من Microsoft Defender هو برنامج مكافحة البرامج الضارة النشط أم لا. لمزيد من المعلومات، راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus).

عندما لا يكون برنامج الحماية من الفيروسات من Microsoft Defender هو برنامج مكافحة البرامج الضارة النشط في مؤسستك وتستخدم خدمة Defender لنقطة النهاية، برنامج الحماية من الفيروسات من Microsoft Defender ينتقل إلى الوضع الخامل.

إذا أوقفت مؤسستك تشغيل برنامج الحماية من الفيروسات من Microsoft Defender من خلال نهج المجموعة أو أساليب أخرى، فيجب استبعاد الأجهزة التي تم إلحاقها من نهج المجموعة هذا.

إذا كنت تقوم بإلحاق الخوادم ولم تكن برنامج الحماية من الفيروسات من Microsoft Defender هي مكافحة البرامج الضارة النشطة على خوادمك، برنامج الحماية من الفيروسات من Microsoft Defender ستحتاج إما إلى تكوينها للانتقال إلى الوضع الخامل أو إلغاء تثبيتها. يعتمد التكوين على إصدار الخادم. لمزيد من المعلومات، راجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

> [!NOTE]
> لا ينطبق نهج المجموعة العادي على الحماية من العبث، وسيتم تجاهل التغييرات على إعدادات برنامج الحماية من الفيروسات من Microsoft Defender عند تشغيل الحماية من العبث.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>برنامج الحماية من الفيروسات من Microsoft Defender تمكين برنامج تشغيل مكافحة البرامج الضارة (ELAM) للإطلاق المبكر

إذا كنت تقوم بتشغيل برنامج الحماية من الفيروسات من Microsoft Defender كمنتج أساسي لمكافحة البرامج الضارة على أجهزتك، فسيلحق عامل Defender لنقطة النهاية بنجاح.

إذا كنت تقوم بتشغيل عميل مكافحة البرامج الضارة تابع لجهة خارجية وتستخدم حلول إدارة الجهاز الجوال أو إدارة نقاط النهاية من Microsoft (الفرع الحالي)، فستحتاج إلى التأكد من تمكين برنامج تشغيل برنامج الحماية من الفيروسات من MICROSOFT DEFENDER ELAM. لمزيد من المعلومات، راجع [التأكد من عدم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender بواسطة النهج](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إعداد نشر Microsoft Defender لنقطة النهاية](production-deployment.md)
- [إلحاق الأجهزة](onboard-configure.md)
