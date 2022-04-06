---
title: تم ا متن الإصدارات السابقة من Windows على Microsoft Defender لنقطة النهاية
description: الإصدارات السابقة المدعمة Windows الأجهزة بحيث يمكنها إرسال بيانات المستشعر إلى Microsoft Defender لنقطة النهاية المستشعر
keywords: onboard, windows, 7, 81, oms, sp1, enterprise, pro, down level
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8fc3f86aa15a9fe54a410c869eb84b2b1ff79872
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474498"
---
# <a name="onboard-previous-versions-of-windows"></a>الإصدارات السابقة من Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**الأنظمة الأساسية**

- Windows 7 SP1 Enterprise
- Windows 7 SP1 Pro
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows Server 2008 R2 SP1

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

يوسع Defender for Endpoint الدعم ليشمل أنظمة تشغيل ذات مستوى أدنى، مما يوفر قدرات متقدمة للكشف عن الهجمات والتحري عنها على الإصدارات Windows الإصدارات المعتمدة.

لتركب نقاط نهاية العميل Windows إلى Defender لنقطة النهاية، ستحتاج إلى:

- [تكوين عملاء System Center Endpoint Protection وتحديثهم](#configure-and-update-system-center-endpoint-protection-clients)
- [تثبيت Microsoft Monitoring Agent (MMA) وتكوينه للتقرير عن بيانات المستشعر](#install-and-configure-microsoft-monitoring-agent-mma)

بالنسبة Windows Server 2008 R2 SP1، لديك خيار التكائم [من خلال Microsoft Defender for Cloud](#onboard-windows-servers-through-microsoft-defender-for-cloud).

> [!NOTE]
> يجب أن يكون ترخيص خادم Defender ل Endpoint مستقلا، لكل عقدة، من أجل ا متن خادم Windows من خلال Microsoft Monitoring Agent (الخيار 1). بدلا من ذلك، يكون ترخيص Microsoft Defender للخوادم مطلوبا لكل عقدة، من أجل ا متن خادم Windows من خلال Microsoft Defender for Cloud (الخيار 2)، راجع الميزات المعتمدة المتوفرة في [Microsoft Defender for Cloud](/azure/security-center/security-center-services).

> [!TIP]
> بعد تشغيل الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أنه تم التكهين بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على "Defender" جديد لنقطة نهاية نقطة النهاية](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>تكوين عملاء System Center Endpoint Protection وتحديثهم

> [!IMPORTANT]
> هذه الخطوة مطلوبة فقط إذا كانت مؤسستك تستخدم System Center Endpoint Protection (SCEP).

يتكامل Defender for Endpoint مع System Center Endpoint Protection لتوفير إمكانية الرؤية للكشف عن البرامج الضارة ولوقف نشر هجوم في مؤسستك من خلال حظر الملفات الضارة أو البرامج الضارة المشتبه بها.

الخطوات التالية مطلوبة لتمكين هذا التكامل:

- تثبيت تحديث النظام الأساسي لمكافحة البرامج الضارة لشهر يناير [2017 Endpoint Protection العملاء](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- تكوين عضوية خدمة الحماية السحابية للعميل SCEP إلى **الإعداد** "خيارات متقدمة"
- قم بتكوين الشبكة للسماح للاتصالات برنامج الحماية من الفيروسات من Microsoft Defender السحابة. لمزيد من المعلومات، راجع [تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender التحقق من صحتها](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>تثبيت Microsoft Monitoring Agent (MMA) وتكوينه

### <a name="before-you-begin"></a>قبل البدء

راجع التفاصيل التالية للتحقق من الحد الأدنى لمتطلبات النظام:

- تثبيت مجموعة التحديث الشهري لشهر فبراير [2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

  > [!NOTE]
  > ينطبق فقط على Windows Server 2008 R2 Windows 7 SP1 Enterprise Windows 7 SP1 Pro.

- تثبيت التحديث [لتجربة العملاء و بيانات التشخيص](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- تثبيت [إما .NET framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (أو أي وقت لاحق) أو [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > ينطبق فقط على Windows Server 2008 R2 Windows 7 SP1 Enterprise Windows 7 SP1 Pro.
    >
    > لا تقوم بتثبيت .NET Framework 4.0.x، لأنه سيبطل التثبيت أعلاه.
    >
    > قد يتطلب تثبيت .NET 4.5 إعادة تشغيل الكمبيوتر بعد التثبيت.

- تلبية الحد الأدنى لمتطلبات النظام لعامل Azure Log Analytics. لمزيد من المعلومات، راجع [تجميع البيانات من أجهزة الكمبيوتر في بيئتك باستخدام Log Analytics](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)

### <a name="installation-steps"></a>خطوات التثبيت

1. قم بتنزيل ملف إعداد الوكيل: Windows [64](https://go.microsoft.com/fwlink/?LinkId=828603) بت أو Windows [32 بت](https://go.microsoft.com/fwlink/?LinkId=828604).

2. الحصول على "معرّف مساحة العمل":
   - في جزء التنقل في Defender for Endpoint، حدد الإعدادات > **إدارة الأجهزة > الالوح**
   - تحديد نظام التشغيل
   - نسخ مفتاح مساحة العمل ومفتاح مساحة العمل

3. باستخدام مفتاح "المستعرض مساحة العمل" ومفتاح مساحة العمل، اختر أي من أساليب التثبيت التالية لتثبيت العامل:
    - [ثبت الوكيل يدويا باستخدام الإعداد](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      في الصفحة **خيارات إعداد** الوكيل، حدد الاتصال **إلى Azure Log Analytics (OMS)**

    - [ثبت الوكيل باستخدام سطر الأوامر](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [تكوين الوكيل باستخدام برنامج نصي](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation).

   > [!NOTE]
   > إذا كنت عميلا [](gov.md)في الحكومة الأمريكية، ضمن "Azure Cloud"، ستحتاج إلى اختيار "Azure US Government" إذا كنت تستخدم معالج الإعداد، أو إذا كنت تستخدم سطر أوامر أو برنامج نصي - قم بتعيين المعلمة "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" إلى 1.

4. إذا كنت تستخدم وكيلا للاتصال بالإنترنت، فشاهد المقطع تكوين إعدادات الوكيل والاتصال بالإنترنت.

بمجرد الانتهاء، من المفترض أن ترى نقاط النهاية المضمنة في المدخل في غضون ساعة.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>تكوين إعدادات الوكيل والاتصال بالإنترنت
إذا كانت الخوادم تحتاج إلى استخدام وكيل للتواصل مع Defender for Endpoint، فاستخدم أحد الأساليب التالية لتكوين MMA لاستخدام الخادم الوكيل:

- [تكوين MMA لاستخدام خادم وكيل](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [تكوين Windows لاستخدام خادم وكيل لجميع الاتصالات](configure-proxy-internet.md)

إذا كان الوكيل أو جدار الحماية يستخدم، فالرجاء التأكد من أن الخوادم يمكنها الوصول إلى كل عناوين URL Microsoft Defender لنقطة النهاية الخدمة مباشرة وبدون اعتراض SSL. لمزيد من المعلومات، راجع [تمكين الوصول إلى عناوين URL لخدمة Defender for Endpoint](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). سيمنع استخدام تقاطع SSL النظام من التواصل مع خدمة Defender for Endpoint.

بمجرد الانتهاء، من المفترض أن ترى خوادم Windows في المدخل في غضون ساعة واحدة.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>تشغيل Windows عبر Microsoft Defender for Cloud

1. في جزء Microsoft 365 Defender التنقل **، حدد الإعدادات** >  **إدارة لوحة** >  **المعلوماتOnboarding**.

2. حدد **Windows Server 2008 R2 SP1** ك نظام التشغيل.

3. انقر **فوق خوادم Onboard في Microsoft Defender for Cloud**.

4. اتبع إرشادات التهيئة في Microsoft Defender لنقطة النهاية [باستخدام Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) وإذا كنت تستخدم Azure ARC، فاتبع إرشادات التهيئة في تمكين [Microsoft Defender لنقطة النهاية التشغيل](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

بعد إكمال خطوات التهيئة، ستحتاج إلى تكوين العملاء System Center Endpoint Protection [تحديثهم](#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
>
> - للتهيئة عبر Microsoft Defender لكي تعمل الخوادم كما هو متوقع، يجب أن يكون للخادم مساحة عمل ومفتاح مناسبين تم تكوينها ضمن إعدادات Microsoft Monitoring Agent (MMA).
> - بعد تكوينها، يتم نشر حزمة إدارة السحابة المناسبة على الجهاز، وستنشر عملية الاستشعار (MsSenseS.exe) وستبدأ.
> - هذا مطلوب أيضا إذا تم تكوين الخادم لاستخدام خادم بوابة OMS كوكيل.



## <a name="verify-onboarding"></a>التحقق من الboarding

تحقق من أن Microsoft Defender AV Microsoft Defender لنقطة النهاية قيد التشغيل. 

> [!NOTE]
> تشغيل Microsoft Defender AV غير مطلوب ولكن من المستحسن. إذا كان منتج مورد برنامج الحماية من الفيروسات آخر هو حل الحماية الأساسي لنقطة النهاية، يمكنك تشغيل Defender Antivirus في الوضع السلبي. يمكنك فقط تأكيد تشغيل الوضع السلبي بعد التحقق من أن Microsoft Defender لنقطة النهاية استشعار (SENSE) قيد التشغيل. 

1. تشغيل الأمر التالي للتحقق من تثبيت Microsoft Defender AV:

   ```sc.exe query Windefend```

    إذا كانت النتيجة 'الخدمة المحددة غير موجودة كخدمة مثبتة'، ستحتاج إلى تثبيت Microsoft Defender AV. لمزيد من المعلومات، راجع برنامج الحماية من الفيروسات من Microsoft Defender [في Windows 10](microsoft-defender-antivirus-windows.md).

    للحصول على معلومات حول كيفية استخدام نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها على خوادم Windows، راجع استخدام إعدادات نهج المجموعة لتكوين وإدارة [ برنامج الحماية من الفيروسات من Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md).


2. تشغيل الأمر التالي للتحقق من أن Microsoft Defender لنقطة النهاية قيد التشغيل:

    ```sc.exe query sense```
    
    يجب أن تظهر النتيجة أنها قيد التشغيل. إذا واجهت مشاكل تتعلق بالتكدث، فشاهد استكشاف الأخطاء في [الرصيد وإصلاحها](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>تشغيل اختبار الكشف
اتبع الخطوات في [تشغيل اختبار الكشف](run-detection-test.md) على جهاز تم إعداده حديثا للتحقق من أن الخادم يعمل على إعداد تقرير إلى Defender لخدمة نقطة النهاية.





## <a name="onboarding-endpoints-with-no-management-solution"></a>تعيين نقاط النهاية دون حل إدارة 

### <a name="using-group-policy"></a>استخدام نهج المجموعة

**الخطوة 1: تنزيل udpate المطابق لنقطة النهاية.**

1. انتقل إلى c:\windows\sysvol\domain\scripts (قد تكون هناك حاجة إلى تغيير عنصر التحكم في أحد وحدات التحكم بالمجال.)
1. إنشاء مجلد باسم MMA.
1. قم بتنزيل ما يلي وضعها في مجلد MMA:
   
    - التحديث لتجربة العملاء و بيانات التكميل التشخيصية:
      - [بالنسبة Windows Server 2008 R2 x64](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    بالنسبة Windows Server 2008 R2 SP1، يجب أيضا إجراء التحديثات التالية:

    فبراير 2018 شهريا - KB4074598 (Windows Server 2008 R2)

    [كتالوج Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    تنزيل تحديثات Windows Server 2008 R2 x64
    
    .NET Framework 3.5.1 (KB315418)<br>
    [بالنسبة Windows Server 2008 R2 x64](https://download.microsoft.com/download/6/8/0/680ee424-358c-4fdf-a0de-b45dee07b711/windows6.1-kb3154518-x64.msu)
    
    >[!NOTE]
    > تفترض هذه المقالة أنك تستخدم خوادم مستندة إلى x64 (MMA Agent .exe x64 New SHA-2 المتوافقة).


**الخطوة 2: إنشاء اسم ملف DeployMMA.cmd (باستخدام المفكرة)** أضف الأسطر التالية إلى ملف cmd. تجدر الإشارة إلى أنك ستحتاج إلى "مفتاح ومعرف مساحة العمل".

الأمر التالي مثال على ذلك. استبدل القيم التالية:
- KB - استخدام KB المعمول به ذي الصلة بنقطة النهاية التي تقوم بستخدامها
- "مفتاح ومفتاح" لمفتاح ومفتاح "مساحة العمل"


```dos
@echo off 
cd "C:"
IF EXIST "C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe" ( 
exit
) ELSE (

wusa.exe C:\Windows\MMA\Windows6.1-KB3080149-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows6.1-KB4074598-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows6.1-KB3154518-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows8.1-KB3080149-x64.msu /quiet /norestart
"c:\windows\MMA\MMASetup-AMD64.exe" /c /t: "C:\Windows\MMA"c:\windows\MMA\ setup.exe /qn NOAPM=1 ADD_OPINSIGHTS_WORKSPACE=1
OPINSIGHTS_WORKSPACE_ID="<your workspace ID>"
OPINSIGHTS_WORKSPACE_KEY="<your workspace key>" AcceptEndUserLicenseAgreement=1
)

)
```





### <a name="group-policy-configuration"></a>نهج المجموعة التكوين

قم بإنشاء نهج مجموعة جديد خصيصا للأجهزة التي تقوم بالتهيئة مثل "Microsoft Defender لنقطة النهاية التهيئة".

- إنشاء مجلد نهج المجموعة باسم "c:\windows\MMA"

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="موقع المجلدات" lightbox="images/grppolicyconfig1.png":::

    **سيضيف هذا مجلدا جديدا على كل خادم يتم تطبيق "GPO"، يسمى MMA، وسوف يتم تخزينه في c:\windows. سيحتوي ذلك على ملفات التثبيت ل MMA والمتطلبات الأساسية وتثبيت البرنامج النصي.**

- قم بإنشاء نهج المجموعة الملفات لكل ملف من الملفات المخزنة في تسجيل صافي.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="نهج المجموعة - 1" lightbox="images/grppolicyconfig2.png":::

وهو ينسخ الملفات من DOMAIN\NETLOGON\MMA\filename إلى C:\windows\MMA\filename - بحيث تكون ملفات التثبيت محلية **للخادم**:

:::image type="content" source="images/deploymma.png" alt-text="خصائص cmd لنشر mma" lightbox="images/deploymma.png":::

كرر العملية ولكن قم بإنشاء استهداف مستوى العنصر على علامة التبويب COMMON، بحيث يتم نسخ الملف فقط إلى إصدار النظام الأساسي/نظام التشغيل المناسب في النطاق:

:::image type="content" source="images/targeteditor.png" alt-text="المحرر الهدف" lightbox="images/targeteditor.png":::

على Windows Server 2008 R2 ستحتاج إلى (وسينسخ لأسفل فقط) ما يلي:
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


بمجرد القيام بذلك، ستحتاج إلى إنشاء نهج برنامج نصي للبدء:

:::image type="content" source="images/startupprops.png" alt-text="خصائص البدء" lightbox="images/startupprops.png":::

اسم الملف الذي يجب تشغيله هنا هو c:\windows\MMA\DeployMMA.cmd.
بمجرد إعادة تشغيل الخادم كجزء من عملية البدء، سيتم تثبيت تحديث لتجربة العملاء وKB لاتمتة التشخيص، ثم تثبيت عامل MMA، أثناء تعيين "مفتاح ومفتاح" ومفتاح مساحة العمل، وسيصبح الخادم مثبتا.

يمكنك أيضا استخدام مهمة **فورية** لتشغيل deployMMA.cmd إذا كنت لا تريد إعادة تشغيل كل الخوادم.

يمكن تنفيذ ذلك على مرحلتين. أولا قم **بإنشاء الملفات** والمجلد في GPO - امنح وقت النظام للتأكد من تطبيق GPO، وأن كل الخوادم لديها ملفات التثبيت. بعد ذلك، أضف المهمة الفورية. سيحقق هذا النتيجة نفسها دون الحاجة إلى إعادة التشغيل.

بما أن البرنامج النصي لديه أسلوب خروج ولن يتم إعادة تشغيله إذا تم تثبيت MMA، يمكنك أيضا استخدام مهمة مجدولة يوميا لتحقيق النتيجة نفسها. على غرار نهج Configuration Manager، سيتم التحقق يوميا للتأكد من وجود MMA.

:::image type="content" source="images/schtask.png" alt-text="جدولة مهمة" lightbox="images/schtask.png":::

:::image type="content" source="images/newtaskprops.png" alt-text="خصائص المهمة الجديدة" lightbox="images/newtaskprops.png":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="خصائص تنزيل mma النشر" lightbox="images/deploymmadowmload.png":::

:::image type="content" source="images/tasksch.png" alt-text="مجدول المهام" lightbox="images/tasksch.png":::

كما هو مذكور في وثائق إعداد الخادم حول Server 2008 R2 تحديدا، الرجاء الاطلاع على ما يلي: للحصول على Windows Server 2008 R2 SP1، تأكد من استيفاء المتطلبات التالية:

- تثبيت مجموعة التحديث الشهري لشهر فبراير [2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- تثبيت [إما .NET framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (أو أي وقت لاحق) أو [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

يرجى التحقق من أن KBs موجودة قبل Windows Server 2008 R2. تتيح لك هذه العملية إمكانية ا متنبأ كل الخوادم إذا لم يكن لديك Configuration Manager إدارة الخوادم.


## <a name="offboard-endpoints"></a>نقاط نهاية إيقاف التشغيل

لديك خياران ل Windows نقاط النهاية من الخدمة:

- إلغاء تثبيت عامل MMA
- إزالة تكوين مساحة عمل Defender لنقطة النهاية

> [!NOTE]
> يؤدي إيقاف تشغيل Windows إلى إيقاف إرسال بيانات المستشعر إلى المدخل، ولكن سيتم الاحتفاظ بالبيانات من نقطة النهاية، بما في ذلك الإشارة إلى أي تنبيهات كانت مضمنة فيها لمدة تصل إلى 6 أشهر.

### <a name="uninstall-the-mma-agent"></a>إلغاء تثبيت عامل MMA

لإنهاء تشغيل Windows النهاية، يمكنك إلغاء تثبيت عامل MMA أو فصله عن إعداد التقارير إلى مساحة عمل Defender for Endpoint. بعد إيقاف تشغيل العامل، لن ترسل نقطة النهاية بيانات المستشعر إلى Defender لنقطة النهاية.
لمزيد من المعلومات، راجع [لتعطيل عامل](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>إزالة تكوين مساحة عمل Defender لنقطة النهاية

يمكنك استخدام أي من الأساليب التالية:

- إزالة تكوين مساحة عمل Defender for Endpoint من عامل MMA
- تشغيل أمر PowerShell لإزالة التكوين

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>إزالة تكوين مساحة عمل Defender for Endpoint من عامل MMA

1. في خصائص **وكيل مراقبة Microsoft**، حدد علامة التبويب **Azure Log Analytics (OMS).**

2. حدد مساحة عمل Defender لنقطة النهاية، وانقر فوق **إزالة**.

    :::image type="content" source="images/atp-mma.png" alt-text="جزء مساحات العمل" lightbox="images/atp-mma.png":::

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>تشغيل أمر PowerShell لإزالة التكوين

1. احصل على "معرّف مساحة العمل":

   1. في جزء التنقل **، حدد الإعدادات** >  **Onboarding**.

   1. حدد نظام التشغيل ذي الصلة واحصل على "معرّف مساحة العمل".

    
2. افتح PowerShell غير مرفوط وتشغيل الأمر التالي. استخدم "معرّف مساحة العمل" الذي حصلت عليه واستبدل `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
