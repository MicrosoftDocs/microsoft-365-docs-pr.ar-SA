---
title: إلحاق الإصدارات السابقة من Windows على Microsoft Defender لنقطة النهاية
description: إلحاق الإصدارات السابقة المدعومة من أجهزة Windows بحيث يمكنها إرسال بيانات جهاز الاستشعار إلى أداة استشعار Microsoft Defender لنقطة النهاية
keywords: إلحاق، نوافذ، 7، 81، oms، sp1، enterprise، pro، مستوى أسفل
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
ms.openlocfilehash: c330d3c8210ea0c83605a2b5e9f9f43d1c930442
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554390"
---
# <a name="onboard-previous-versions-of-windows"></a>الإصدارات السابقة من Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**الأنظمة الأساسية**

- Windows 7 SP1 Enterprise
- Windows 7 SP1 Pro
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows Server 2008 R2 SP1

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

يقوم Defender لنقطة النهاية بتوسيع الدعم ليشمل أنظمة التشغيل ذات المستوى الأدنى، ما يوفر قدرات متقدمة للكشف عن الهجمات والتحقيق فيها على إصدارات Windows المدعومة.

لإلحاق نقاط نهاية عميل Windows ذات المستوى السفلي ب Defender لنقطة النهاية، ستحتاج إلى:

- [تكوين عملاء System Center Endpoint Protection وتحديثهم](#configure-and-update-system-center-endpoint-protection-clients)
- [تثبيت وتكوين عامل مراقبة Microsoft (MMA) للإبلاغ عن بيانات جهاز الاستشعار](#install-and-configure-microsoft-monitoring-agent-mma)

بالنسبة ل Windows Server 2008 R2 SP1، لديك خيار [الإلحاق من خلال Microsoft Defender for Cloud](#onboard-windows-servers-through-microsoft-defender-for-cloud).

> [!NOTE]
> مطلوب ترخيص خادم مستقل ل Defender لنقطة النهاية، لكل عقدة، من أجل إلحاق خادم Windows من خلال عامل مراقبة Microsoft (الخيار 1). بدلا من ذلك، يلزم ترخيص Microsoft Defender للخوادم، لكل عقدة، من أجل إلحاق خادم Windows من خلال Microsoft Defender for Cloud (الخيار 2)، راجع [الميزات المدعومة المتوفرة في Microsoft Defender for Cloud](/azure/defender-for-cloud/supported-machines-endpoint-solutions-clouds-servers).

> [!TIP]
> بعد إلحاق الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أنه تم إلحاقه بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على نقطة نهاية Defender for Endpoint التي تم إلحاقها حديثا](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>تكوين عملاء System Center Endpoint Protection وتحديثهم

> [!IMPORTANT]
> هذه الخطوة مطلوبة فقط إذا كانت مؤسستك تستخدم System Center Endpoint Protection (SCEP).

يتكامل Defender لنقطة النهاية مع System Center Endpoint Protection لتوفير رؤية لاكتشاف البرامج الضارة وإيقاف نشر هجوم في مؤسستك عن طريق حظر الملفات التي يحتمل أن تكون ضارة أو البرامج الضارة المشتبه بها.

الخطوات التالية مطلوبة لتمكين هذا التكامل:

- تثبيت [تحديث النظام الأساسي لمكافحة البرامج الضارة في يناير 2017 لعملاء Endpoint Protection](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- تكوين عضوية خدمة حماية السحابة لعميل SCEP إلى الإعداد **المتقدم**
- تكوين الشبكة للسماح بالاتصالات إلى سحابة الحماية من الفيروسات من Microsoft Defender. لمزيد من المعلومات، راجع [تكوين اتصالات شبكة الحماية من الفيروسات ل Microsoft Defender والتحقق من صحتها](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>تثبيت وتكوين عامل مراقبة Microsoft (MMA)

### <a name="before-you-begin"></a>قبل البدء

راجع التفاصيل التالية للتحقق من الحد الأدنى لمتطلبات النظام:

- تثبيت [حزمة التحديث الشهري لشهر فبراير 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

  > [!NOTE]
  > ينطبق فقط على Windows Server 2008 R2 وWindows 7 SP1 Enterprise وWindows 7 SP1 Pro.

- تثبيت [التحديث لتجربة العملاء وبيانات تتبع الاستخدام التشخيصية](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- تثبيت [إطار عمل .NET 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (أو أحدث) أو [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > ينطبق فقط على Windows Server 2008 R2 وWindows 7 SP1 Enterprise وWindows 7 SP1 Pro.
    >
    > لا تقم بتثبيت .NET Framework 4.0.x، لأنه سيبطل التثبيت أعلاه.
    >
    > قد يتطلب تثبيت .NET 4.5 إعادة تشغيل الكمبيوتر بعد التثبيت.

- تلبية الحد الأدنى لمتطلبات النظام الخاصة بعامل Azure Log Analytics. لمزيد من المعلومات، راجع ["تجميع البيانات من أجهزة الكمبيوتر" في بيئة باستخدام Log Analytics](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)

### <a name="installation-steps"></a>خطوات التثبيت

1. قم بتنزيل ملف إعداد العامل: [عامل Windows 64 بت](https://go.microsoft.com/fwlink/?LinkId=828603) أو [عامل Windows 32 بت](https://go.microsoft.com/fwlink/?LinkId=828604).

    >[!NOTE]
    >بسبب [إهمال دعم SHA-1 من قبل عامل MMA](/azure/azure-monitor/agents/agent-windows#sha-2-code-signing-support-requirement)، يجب أن يكون عامل MMA الإصدار 10.20.18029 أو أحدث.
    

2. الحصول على معرف مساحة العمل:
   - في جزء التنقل في Defender لنقطة النهاية، حدد **الإعدادات > إدارة الأجهزة > الإلحاق**
   - حدد نظام التشغيل
   - نسخ معرف مساحة العمل ومفتاح مساحة العمل

3. يؤدي استخدام معرف مساحة العمل ومفتاح مساحة العمل إلى اختيار أي من أساليب التثبيت التالية لتثبيت العامل:
    - [تثبيت العامل يدويا باستخدام الإعداد](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      في صفحة **"Agent Setup Options** "، حدد **"Connect the agent to Azure Log Analytics (OMS)"**

    - [تثبيت العامل باستخدام سطر الأوامر](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [تكوين العامل باستخدام برنامج نصي](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation).

   > [!NOTE]
   > إذا كنت [عميلا لحكومة الولايات المتحدة](gov.md)، فستحتاج ضمن "Azure Cloud" إلى اختيار "Azure US Government" إذا كنت تستخدم معالج الإعداد، أو إذا كنت تستخدم سطر أوامر أو برنامج نصي - قم بتعيين المعلمة "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" إلى 1.

4. إذا كنت تستخدم وكيلا للاتصال بالإنترنت، فراجع قسم إعدادات تكوين الوكيل والاتصال بالإنترنت.

بمجرد الانتهاء، يجب أن تشاهد نقاط النهاية المضمنة في المدخل في غضون ساعة.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>تكوين إعدادات الوكيل والاتصال بالإنترنت
إذا كانت الخوادم تحتاج إلى استخدام وكيل للتواصل مع Defender لنقطة النهاية، فاستخدم إحدى الطرق التالية لتكوين MMA لاستخدام الخادم الوكيل:

- [تكوين MMA لاستخدام خادم وكيل](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [تكوين Windows لاستخدام خادم وكيل لكافة الاتصالات](configure-proxy-internet.md)

إذا كان الوكيل أو جدار الحماية قيد الاستخدام، فالرجاء التأكد من أن الخوادم يمكنها الوصول إلى كافة عناوين URL للخدمة Microsoft Defender لنقطة النهاية مباشرة وبدون اعتراض SSL. لمزيد من المعلومات، راجع [تمكين الوصول إلى عناوين URL لخدمة Defender لنقطة النهاية](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). سيؤدي استخدام اعتراض SSL إلى منع النظام من الاتصال بخدمة Defender لنقطة النهاية.

بمجرد الانتهاء، يجب أن تشاهد خوادم Windows المضمنة في المدخل في غضون ساعة.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>إلحاق خوادم Windows من خلال Microsoft Defender for Cloud

1. في جزء التنقل Microsoft 365 Defender، حدد **الإعدادات** >  الخاصة **بإدارة** >  **الأجهزة**.

2. حدد **Windows Server 2008 R2 SP1** كنظام التشغيل.

3. انقر فوق **"خوادم الإلحاق" في Microsoft Defender for Cloud**.

4. اتبع إرشادات الإلحاق في [Microsoft Defender لنقطة النهاية مع Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) وإذا كنت تستخدم Azure ARC، فاتبع إرشادات الإلحاق في [تمكين تكامل Microsoft Defender لنقطة النهاية](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

بعد إكمال خطوات الإلحاق، ستحتاج إلى [تكوين وتحديث System Center Endpoint Protection العملاء](#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
>
> - للإلحاق عبر Microsoft Defender للعمل على الخوادم كما هو متوقع، يجب أن يكون للخادم مساحة عمل مناسبة ومفتاح تم تكوينه داخل إعدادات عامل مراقبة Microsoft (MMA).
> - بمجرد تكوينها، يتم نشر حزمة إدارة السحابة المناسبة على الجهاز وسيتم نشر عملية الاستشعار (MsSenseS.exe) وبدء تشغيلها.
> - هذا مطلوب أيضا إذا تم تكوين الخادم لاستخدام خادم بوابة OMS كوكيل.



## <a name="verify-onboarding"></a>التحقق من الإلحاق

تحقق من تشغيل Microsoft Defender AV و Microsoft Defender لنقطة النهاية. 

> [!NOTE]
> تشغيل Microsoft Defender AV غير مطلوب ولكن يوصى به. إذا كان منتج مورد الحماية من الفيروسات آخر هو حل حماية نقطة النهاية الأساسي، يمكنك تشغيل Defender Antivirus في الوضع السلبي. يمكنك فقط تأكيد تشغيل الوضع السلبي بعد التحقق من تشغيل أداة استشعار Microsoft Defender لنقطة النهاية (SENSE). 

1. قم بتشغيل الأمر التالي للتحقق من تثبيت Microsoft Defender AV:

   ```sc.exe query Windefend```

    إذا كانت النتيجة هي "الخدمة المحددة غير موجودة كخدمة مثبتة"، فستحتاج إلى تثبيت Microsoft Defender AV. لمزيد من المعلومات، راجع [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-windows.md).

    للحصول على معلومات حول كيفية استخدام نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارته على خوادم Windows، راجع [استخدام إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارته](use-group-policy-microsoft-defender-antivirus.md).


2. قم بتشغيل الأمر التالي للتحقق من تشغيل Microsoft Defender لنقطة النهاية:

    ```sc.exe query sense```
    
    يجب أن تظهر النتيجة أنها قيد التشغيل. إذا واجهت مشاكل في الإلحاق، فراجع [استكشاف أخطاء الإلحاق وإصلاحها](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>تشغيل اختبار الكشف
اتبع الخطوات في [تشغيل اختبار الكشف على جهاز تم إلحاقه حديثا](run-detection-test.md) للتحقق من أن الخادم يقوم بالإبلاغ إلى Defender لخدمة نقطة النهاية.





## <a name="onboarding-endpoints-with-no-management-solution"></a>إلحاق نقاط النهاية بدون حل إدارة 

### <a name="using-group-policy"></a>استخدام نهج المجموعة

**الخطوة 1: تنزيل التحديث المقابل لنقطة النهاية.**

1. انتقل إلى c:\windows\sysvol\domain\scripts (قد تكون هناك حاجة إلى التحكم بالتغيير على إحدى وحدات التحكم بالمجال.)
1. إنشاء مجلد باسم MMA.
1. قم بتنزيل ما يلي ووضعها في مجلد MMA:
   
    - تحديث لتجربة العملاء وبيانات تتبع الاستخدام التشخيصية:
      - [ل Windows Server 2008 R2 x64](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    بالنسبة إلى Windows Server 2008 R2 SP1، يلزم أيضا إجراء التحديثات التالية:

    إظهار شهري لشهر فبراير 2018 - KB4074598 (Windows Server 2008 R2)

    [كتالوج تحديث Microsoft](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    تنزيل تحديثات Windows Server 2008 R2 x64
    
    .NET Framework 3.5.1 (KB315418)<br>
    [ل Windows Server 2008 R2 x64](/iis/install/installing-iis-7/install-windows-server-2008-and-windows-server-2008-r2)
    
    >[!NOTE]
    > تفترض هذه المقالة أنك تستخدم خوادم مستندة إلى x64 (عامل MMA .exe الإصدار المتوافق مع x64 New SHA-2).


**الخطوة 2: إنشاء اسم ملف DeployMMA.cmd (باستخدام المفكرة)** أضف الأسطر التالية إلى ملف cmd. لاحظ أنك ستحتاج إلى معرف مساحة العمل والمفتاح.

الأمر التالي مثال. استبدل القيم التالية:
- KB - استخدام KB المعمول به ذات الصلة بنقطة النهاية التي تقوم بإلحاقها
- معرف مساحة العمل والمفتاح - استخدم المعرف والمفتاح


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
"c:\windows\MMA\MMASetup-AMD64.exe" /c /t:"C:\Windows\MMA"
c:\windows\MMA\setup.exe /qn NOAPM=1 ADD_OPINSIGHTS_WORKSPACE=1 OPINSIGHTS_WORKSPACE_ID="<your workspace ID>" OPINSIGHTS_WORKSPACE_KEY="<your workspace key>" AcceptEndUserLicenseAgreement=1

) 
```





### <a name="group-policy-configuration"></a>تكوين نهج المجموعة

إنشاء نهج مجموعة جديد خصيصا لإلحاق الأجهزة مثل "Microsoft Defender لنقطة النهاية الإلحاق".

- إنشاء مجلد نهج المجموعة باسم "c:\windows\MMA"

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="موقع المجلدات" lightbox="images/grppolicyconfig1.png":::

    **سيؤدي ذلك إلى إضافة مجلد جديد على كل خادم يطبق عنصر نهج المجموعة، يسمى MMA، وسيتم تخزينه في c:\windows. سيحتوي هذا على ملفات التثبيت الخاصة ب MMA والمتطلبات الأساسية وتثبيت البرنامج النصي.**

- إنشاء تفضيل ملفات نهج المجموعة لكل ملف من الملفات المخزنة في تسجيل الدخول إلى Net.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="نهج المجموعة - 1" lightbox="images/grppolicyconfig2.png":::

ينسخ الملفات من DOMAIN\NETLOGON\MMA\filename إلى C:\windows\MMA\filename - **بحيث تكون ملفات التثبيت محلية للخادم**:

:::image type="content" source="images/deploymma.png" alt-text="توزيع خصائص mma cmd" lightbox="images/deploymma.png":::

كرر العملية ولكن قم بإنشاء مستوى عنصر مستهدف على علامة التبويب COMMON، بحيث يتم نسخ الملف فقط إلى إصدار النظام الأساسي/نظام التشغيل المناسب في النطاق:

:::image type="content" source="images/targeteditor.png" alt-text="المحرر الهدف" lightbox="images/targeteditor.png":::

بالنسبة ل Windows Server 2008 R2 ستحتاج (وسوف يتم نسخه فقط) إلى ما يلي:
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


بمجرد الانتهاء من ذلك، ستحتاج إلى إنشاء نهج برنامج نصي لبدء التشغيل:

:::image type="content" source="images/startupprops.png" alt-text="خصائص البدء" lightbox="images/startupprops.png":::

اسم الملف الذي سيتم تشغيله هنا هو c:\windows\MMA\DeployMMA.cmd.
بمجرد إعادة تشغيل الخادم كجزء من عملية البدء، سيقوم بتثبيت التحديث لتجربة العميل وبيانات تتبع الاستخدام التشخيصية KB، ثم تثبيت عامل MMA، مع تعيين معرف مساحة العمل والمفتاح، وسيتم إلحاق الخادم.

يمكنك أيضا استخدام **مهمة فورية** لتشغيل deployMMA.cmd إذا كنت لا تريد إعادة تشغيل كافة الخوادم.

ويمكن إجراء ذلك على مرحلتين. قم أولا بإنشاء **الملفات والمجلد في** عنصر نهج المجموعة - امنح وقت النظام للتأكد من تطبيق عنصر نهج المجموعة، وجميع الخوادم لديها ملفات التثبيت. بعد ذلك، أضف المهمة الفورية. سيؤدي ذلك إلى تحقيق النتيجة نفسها دون الحاجة إلى إعادة التشغيل.

نظرا لأن البرنامج النصي لديه أسلوب خروج ويتعذر إعادة تشغيله إذا تم تثبيت MMA، يمكنك أيضا استخدام مهمة مجدولة يوميا لتحقيق نفس النتيجة. على غرار نهج التوافق Configuration Manager، فإنه سيتم التحقق يوميا لضمان وجود MMA.

:::image type="content" source="images/schtask.png" alt-text="جدولة المهمة" lightbox="images/schtask.png":::

:::image type="content" source="images/newtaskprops.png" alt-text="خصائص المهمة الجديدة" lightbox="images/newtaskprops.png":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="توزيع خصائص تنزيل mma" lightbox="images/deploymmadowmload.png":::

:::image type="content" source="images/tasksch.png" alt-text="مجدول المهام" lightbox="images/tasksch.png":::

كما هو مذكور في وثائق الإلحاق ل Server على وجه التحديد حول Server 2008 R2 يرجى الاطلاع أدناه: ل Windows Server 2008 R2 SP1، تأكد من استيفاء المتطلبات التالية:

- تثبيت [حزمة التحديث الشهري لشهر فبراير 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- تثبيت [إطار عمل .NET 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (أو أحدث) أو [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

الرجاء التحقق من وجود KBs قبل إلحاق Windows Server 2008 R2. تسمح لك هذه العملية بإلحاق جميع الخوادم إذا لم يكن لديك Configuration Manager إدارة الخوادم.


## <a name="offboard-endpoints"></a>نقاط نهاية اللوحة

لديك خياران لإلغاء تشغيل نقاط نهاية Windows من الخدمة:

- إلغاء تثبيت عامل MMA
- إزالة تكوين مساحة عمل Defender لنقطة النهاية

> [!NOTE]
> يؤدي إلغاء الإلحاق إلى توقف نقطة نهاية Windows عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من نقطة النهاية، بما في ذلك الإشارة إلى أي تنبيهات تم الاحتفاظ بها لمدة تصل إلى 6 أشهر.

### <a name="uninstall-the-mma-agent"></a>إلغاء تثبيت عامل MMA

لإلغاء تشغيل نقطة نهاية Windows، يمكنك إلغاء تثبيت عامل MMA أو فصله عن إعداد التقارير إلى مساحة عمل Defender لنقطة النهاية. بعد إيقاف تشغيل العامل، لن ترسل نقطة النهاية بيانات المستشعر إلى Defender لنقطة النهاية.
لمزيد من المعلومات، راجع [تعطيل عامل](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>إزالة تكوين مساحة عمل Defender لنقطة النهاية

يمكنك استخدام أي من الأساليب التالية:

- إزالة تكوين مساحة عمل Defender لنقطة النهاية من عامل MMA
- تشغيل أمر PowerShell لإزالة التكوين

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>إزالة تكوين مساحة عمل Defender لنقطة النهاية من عامل MMA

1. في **خصائص عامل مراقبة Microsoft**، حدد علامة التبويب **Azure Log Analytics (OMS** ).

2. حدد مساحة عمل Defender لنقطة النهاية، وانقر فوق **"إزالة**".

    :::image type="content" source="images/atp-mma.png" alt-text="جزء مساحات العمل" lightbox="images/atp-mma.png":::

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>تشغيل أمر PowerShell لإزالة التكوين

1. الحصول على معرف مساحة العمل:

   1. في جزء التنقل، حدد **"إعدادات** > **الإلحاق**".

   1. حدد نظام التشغيل ذي الصلة واحصل على معرف مساحة العمل.

    
2. افتح PowerShell غير مقيد وقم بتشغيل الأمر التالي. استخدم معرف مساحة العمل الذي حصلت عليه واستبدل `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
