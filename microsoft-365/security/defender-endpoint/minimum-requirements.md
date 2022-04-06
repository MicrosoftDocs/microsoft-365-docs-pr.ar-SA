---
title: الحد الأدنى لمتطلبات Microsoft Defender لنقطة النهاية
description: فهم متطلبات ومتطلبات الترخيص للأجهزة المجهزة للخدمة
keywords: الحد الأدنى للمتطلبات والترخيص جدول المقارنة
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
ms.openlocfilehash: 754537d11a4c183cd1057b94d583a31543d9e4a5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467346"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>الحد الأدنى لمتطلبات Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-minreqs-abovefoldlink)

هناك بعض المتطلبات الدنيا لتكين الأجهزة للخدمة. تعرف على متطلبات الترخيص والأجهزة والبرامج وإعدادات التكوين الأخرى للأجهزة المجهزة للخدمة.

> [!TIP]
>
> - تصف هذه المقالة الحد الأدنى لمتطلبات Microsoft Defender لنقطة النهاية 2. إذا كنت تبحث عن معلومات حول Defender for Endpoint Plan 1، فاطلع على متطلبات [Defender لخطة نقطة النهاية 1](mde-p1-setup-configuration.md#review-the-requirements).
> - تعرف على التحسينات الأخيرة في Defender for Endpoint: [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - أظهر Defender ل Endpoint قدرات الكشف والبصريات الرائدة في تقييم MITRE الأخير. اقرأ: [Insights من تقييم MITRE ATT&المستند إلى CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>متطلبات الترخيص
للحصول على متطلبات ترخيص المعلومات Microsoft Defender لنقطة النهاية، راجع Microsoft Defender لنقطة النهاية [الترخيص.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint)


للحصول على معلومات الترخيص المفصلة، راجع [](https://www.microsoft.com/licensing/terms/) موقع شروط المنتج واعمل مع فريق حسابك لمعرفة المزيد حول الشروط والأحكام.

لمزيد من المعلومات حول صفيف الميزات في Windows، راجع [مقارنة Windows الإصدارات](https://www.microsoft.com/windowsforbusiness/compare).

## <a name="browser-requirements"></a>متطلبات المستعرض

يتم الوصول إلى Defender for Endpoint من خلال مستعرض، يدعم المستعرضات التالية:

- Microsoft Edge
- Google Chrome

> [!NOTE]
> على الرغم من أن المستعرضات الأخرى قد تعمل، فإن المستعرضات المذكورة هي المستعرضات المعتمدة.

## <a name="hardware-and-software-requirements"></a>متطلبات الأجهزة والبرامج

### <a name="supported-windows-versions"></a>الإصدارات Windows المعتمدة

- Windows 7 SP1 Enterprise ([يتطلب ESU للدعم](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 7 SP1 Pro ([يتطلب ESU للدعم](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 8.1 Enterprise
- Windows 8.1 Pro
- Windows 11 Enterprise
- Windows 11 Education
- Windows 11 Pro
- Windows 11 Pro Education
- Windows 10 Enterprise
- [Windows 10 Enterprise LTSC 2016 (أو أي وقت لاحق)](/windows/whats-new/ltsc/)
- Windows 10 Enterprise IoT

    >[!NOTE]
    >على الرغم من أن Windows 10 IoT Enterprise هو نظام تشغيل معتمد في Microsoft Defender لنقطة النهاية ويمكن الشركات الأصلية/الشركات المستضيفة للمنتجات/ODMs من توزيعه كجزء من المنتج أو الحل، يجب على العملاء اتباع إرشادات الشركة الأصلية/ODM حول البرامج المثبتة المستندة إلى المضيف وإمكانية الدعم.

- Windows 10 Education
- Windows 10 Pro
- Windows 10 Pro Education
- Windows الخادم
  - Windows Server 2008 R2 SP1 ([يتطلب ESU للدعم](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - Windows Server 2016‏
  - Windows Server، الإصدار 1803 أو الإصدارات الأحدث
  - Windows Server 2019
  - Windows Server 2022
- Windows سطح المكتب الظاهري

يجب أن تكون الأجهزة على شبكتك قيد تشغيل أحد هذه الإصدارات.

متطلبات الأجهزة ل Defender لنقطة النهاية على الأجهزة هي نفسها للطبعات المعتمدة.

> النواة: 2 الحد الأدنى، 4 الذاكرة المفضلة: 1 غيغابايت كحد أدنى، 4 مفضلة

لمزيد من المعلومات حول الإصدارات المعتمدة من Windows 10، راجع (/windows/release-health/release-information).

> [!NOTE]
> إن الأجهزة التي تعمل بالإصدارات Windows الأجهزة المحمولة (مثل Windows CE والإصدارات Windows 10 Mobile) غير معتمدة.
>
> قد تواجه الأجهزة الظاهرية Windows 10 Enterprise 2016 LTSB مشاكل في الأداء إذا تم تشغيلها على الأنظمة الأساسية الظاهرية غير Microsoft.
>
> بالنسبة للبيئات الظاهرية، نوصي باستخدام Windows 10 Enterprise LTSC 2019 أو أي وقت لاحق.

عندما تكون المكونات مدعمة على أنظمة التشغيل Windows Microsoft، فإن Microsoft Defender لنقطة النهاية سيتبع دورة حياة نظام التشغيل المعني. لمزيد من المعلومات، راجع [الأسئلة الشائعة حول دورة الحياة](/lifecycle/faq/general-lifecycle). يتم عادة توفير الميزات أو الإمكانات الجديدة فقط على أنظمة التشغيل التي لم تصل بعد إلى نهاية دورة حياتها. سيستمر توفير تحديثات معلومات الأمان (التعريف وتحديثات المحرك) ومنطق الكشف حتى:

- نهاية [تاريخ الدعم](/lifecycle/products/) (نظم التشغيل التي لا تملك برنامج تحديثات الأمان الموسعة (ESU).
- نهاية [تاريخ ESU](/lifecycle/faq/extended-security-updates) (أنظمة التشغيل التي لديها برنامج ESU).



### <a name="other-supported-operating-systems"></a>أنظمة تشغيل أخرى معتمدة

- [Android](microsoft-defender-endpoint-android.md)
- [iOS](microsoft-defender-endpoint-ios.md)
- [Linux](microsoft-defender-endpoint-linux.md)
- [macOS](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> ستحتاج إلى تأكيد توافق توزيعات Linux والإصدارات من Android و iOS و macOS مع Defender for Endpoint لكي يعمل التكامل.

### <a name="network-and-data-storage-and-configuration-requirements"></a>متطلبات تخزين الشبكة والبيانات وتكوينها

عند تشغيل معالج الإعداد للمرة الأولى، يجب أن تختار المكان الذي يتم فيه تخزين Microsoft Defender لنقطة النهاية ذات الصلة: في الاتحاد الأوروبي أو المملكة المتحدة أو مركز بيانات الولايات المتحدة.

> [!NOTE]
>
> - لا يمكنك تغيير موقع تخزين البيانات بعد الإعداد للمرة الأولى.
> - راجع Microsoft Defender لنقطة النهاية [تخزين البيانات](data-storage-privacy.md) والخصوصية للحصول على مزيد من المعلومات حول مكان تخزين Microsoft لبياناتك وكيفية تخزينها.

### <a name="diagnostic-data-settings"></a>إعدادات البيانات التشخيصية

> [!NOTE]
> Microsoft Defender لنقطة النهاية يتطلب أي مستوى تشخيص معين طالما أنه ممكن.

تأكد من تمكين خدمة البيانات التشخيصية على جميع الأجهزة في مؤسستك.
بشكل افتراضي، يتم تمكين هذه الخدمة. من الجيد التحقق للتأكد من أنك ستحصل على بيانات المستشعر منها.

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>استخدم سطر الأوامر للتحقق من نوع Windows بدء تشغيل خدمة البيانات التشخيصية

1. افتح موجه سطر أوامر مرتفعا على الجهاز:
   1. انتقل إلى **ابدأ** وا اكتب **cmd**.
   2. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

2. أدخل الأمر التالي، ثم اضغط على **Enter**:

   ```console
   sc qc diagtrack
   ```

   إذا تم تمكين الخدمة، يجب أن تبدو النتيجة على شكل لقطة الشاشة التالية:

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="نتيجة أمر استعلام sc ل diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

ستحتاج إلى تعيين الخدمة للبدء تلقائيا إذا لم يتم تعيين START_TYPE إلى **AUTO_START.**

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>استخدام سطر الأوامر لتعيين Windows البيانات التشخيصية تلقائيا

1. فتح موجه سطر أوامر مرتفع في نقطة النهاية:
    1. انتقل إلى **ابدأ** وا اكتب **cmd**.
    2. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

2. أدخل الأمر التالي، ثم اضغط على **Enter**:

    ```console
    sc config diagtrack start=auto
    ```

3. يتم عرض رسالة نجاح. تحقق من التغيير بإدخال الأمر التالي، ثم اضغط على **Enter**:

    ```console
    sc qc diagtrack
    ```

#### <a name="internet-connectivity"></a>الاتصال بالإنترنت

الاتصال بالإنترنت على الأجهزة مطلوب إما مباشرة أو من خلال الوكيل.

يمكن لمستشعر Defender لنقطة النهاية استخدام معدل ترددي يومي يبلغ 5 مبايت للتواصل مع خدمة السحابة Defender for Endpoint ولتقارير بيانات الإنترنت. لا يتم تضمين الأنشطة التي يتم إجراءها مرة واحدة مثل تحميل الملفات ومجموعة حزم التحقيق في هذا النطاق الترددي المتوسط اليومي.

لمزيد من المعلومات حول إعدادات تكوين الوكيل الإضافية، راجع [تكوين إعدادات](configure-proxy-internet.md) اتصال الإنترنت ووكيل الجهاز.

قبل أن تجهز الأجهزة، يجب تمكين خدمة البيانات التشخيصية. يتم تمكين الخدمة بشكل افتراضي في Windows 10 Windows 11.

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>برنامج الحماية من الفيروسات من Microsoft Defender متطلبات التكوين

يعتمد عامل Defender for Endpoint على قدرة برنامج الحماية من الفيروسات من Microsoft Defender على فحص الملفات وتوفير معلومات عنها.

قم بتكوين تحديثات معلومات الأمان على أجهزة Defender لنقطة النهاية سواء برنامج الحماية من الفيروسات من Microsoft Defender هو برنامج مكافحة البرامج الضارة النشط أم لا. لمزيد من المعلومات، [راجع إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus).

عندما برنامج الحماية من الفيروسات من Microsoft Defender تكون البرامج الضارة النشطة في مؤسستك وأنت تستخدم خدمة Defender for Endpoint، برنامج الحماية من الفيروسات من Microsoft Defender وضع غير نشط.

إذا كانت مؤسستك قد قمت برنامج الحماية من الفيروسات من Microsoft Defender من خلال نهج المجموعة أو أساليب أخرى، فيجب استبعاد الأجهزة المجهزة من نهج المجموعة هذا.

إذا كنت تقوم بتهيئة الخوادم برنامج الحماية من الفيروسات من Microsoft Defender لم تكن هذه هي البرامج الضارة النشطة على الخوادم، برنامج الحماية من الفيروسات من Microsoft Defender يجب إما تكوينها لكي تعمل في الوضع السلبي أو إلغاء تثبيتها. يعتمد التكوين على إصدار الخادم. لمزيد من المعلومات، [راجع برنامج الحماية من الفيروسات من Microsoft Defender التوافق](microsoft-defender-antivirus-compatibility.md).

> [!NOTE]
> لا ينطبق نهج المجموعة العادي على الحماية من العبث، وستتجاهل التغييرات برنامج الحماية من الفيروسات من Microsoft Defender الإعدادات عندما تكون الحماية من العبث مطبقة.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>برنامج الحماية من الفيروسات من Microsoft Defender تشغيل برنامج تشغيل البرامج الضارة المبكرة (ELAM)

إذا كنت تقوم بتشغيل برنامج الحماية من الفيروسات من Microsoft Defender البرنامج كمنتج أساسي لمكافحة البرامج الضارة على أجهزتك، فإن وكيل Defender for Endpoint سينجح في الالتحاق.

إذا كنت تقوم بتشغيل عميل مكافحة البرامج الضارة من جهة خارجية واستخدام حلول إدارة الجهاز Mobile إدارة نقاط النهاية من Microsoft (الفرع الحالي)، ستحتاج إلى التأكد من تمكين برنامج تشغيل برنامج الحماية من الفيروسات من Microsoft Defender ELAM. لمزيد من المعلومات، راجع [التأكد من عدم](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) برنامج الحماية من الفيروسات من Microsoft Defender النهج.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إعداد Microsoft Defender لنقطة النهاية النشر](production-deployment.md)
- [الأجهزة المجهزة](onboard-configure.md)
