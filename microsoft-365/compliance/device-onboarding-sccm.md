---
title: إلحاق الأجهزة Windows 10 وأجهزة Windows 11 باستخدام Configuration Manager
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: استخدم Configuration Manager لنشر حزمة التكوين على الأجهزة بحيث يتم إلحاقها للخدمة.
ms.openlocfilehash: 2cca9cc073ca08c7fabb19511a4253e4a682057a
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760702"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-configuration-manager"></a>إلحاق الأجهزة Windows 10 وأجهزة Windows 11 باستخدام Configuration Manager

**ينطبق على:**

- [Microsoft 365 منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

### <a name="onboard-devices-using-system-center-configuration-manager"></a>إلحاق الأجهزة باستخدام System Center Configuration Manager

1. احصل على ملف حزمة التكوين .zip (*DeviceComplianceOnboardingPackage.zip*) من [مركز التوافق من Microsoft](https://compliance.microsoft.com/).

2. في جزء التنقل، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**الإعدادات**</a> >  **Device OnboardingOnboarding** > .

3. في حقل **أسلوب النشر**، حدد **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

4. حدد **حزمة التنزيل**، واحفظ ملف .zip.

5. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف يسمى *DeviceComplianceOnboardingScript.cmd*.

6. نشر الحزمة باتباع الخطوات الواردة في المقالة "[الحزم والبرامج" في مركز النظام 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)).

7. اختر مجموعة أجهزة معرفة مسبقا لنشر الحزمة إليها.

> [!NOTE]
> لا تدعم حماية المعلومات Microsoft 365 الإلحاق أثناء مرحلة التجربة الجاهزة [(OOBE](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87)). تأكد من أن المستخدمين يكملون OOBE بعد تشغيل تثبيت Windows أو ترقيته.

> [!TIP]
> بعد إلحاق الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أن الجهاز تم إلحاقه بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test).
>
> لاحظ أنه من الممكن إنشاء قاعدة الكشف على تطبيق Configuration Manager للتحقق باستمرار مما إذا كان قد تم إلحاق جهاز. التطبيق هو نوع مختلف من العناصر عن الحزمة والبرنامج.
> إذا لم يتم إلحاق جهاز بعد (بسبب الإكمال المعلق ل OOBE أو أي سبب آخر)، فسيعيد Configuration Manager محاولة إلحاق الجهاز حتى تكتشف القاعدة تغيير الحالة.
>
> يمكن إنجاز هذا السلوك عن طريق إنشاء قاعدة الكشف عن التحقق مما إذا كانت قيمة التسجيل "OnboardingState" (من النوع REG_DWORD) = 1.
> تقع قيمة التسجيل هذه ضمن "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
لمزيد من المعلومات، راجع [تكوين أساليب الكشف في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159(v=technet.10)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>تكوين إعدادات مجموعة العينة

لكل جهاز، يمكنك تعيين قيمة تكوين لتحديد ما إذا كان يمكن جمع العينات من الجهاز عند تقديم طلب من خلال مركز حماية Microsoft Defender لإرسال ملف للتحليل العميق.

> [!NOTE]
> عادة ما تتم إعدادات التكوين هذه من خلال Configuration Manager.

يمكنك تعيين قاعدة توافق لعنصر التكوين في Configuration Manager لتغيير إعداد مشاركة العينة على جهاز.

يجب أن تكون هذه القاعدة عنصر تكوين قاعدة التوافق *المعالجة* الذي يعين قيمة مفتاح التسجيل على الأجهزة المستهدفة للتأكد من أنها شكاوى.

يتم تعيين التكوين من خلال إدخال مفتاح التسجيل التالي:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

حيث:

نوع المفتاح هو D-WORD.

القيم المحتملة هي:

- 0 - لا يسمح بمشاركة العينة من هذا الجهاز
- 1 - يسمح بمشاركة كافة أنواع الملفات من هذا الجهاز

القيمة الافتراضية في حالة عدم وجود مفتاح التسجيل هي 1.

لمزيد من المعلومات حول System Center Configuration Manager Compliance، راجع [مقدمة حول إعدادات التوافق في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).


## <a name="other-recommended-configuration-settings"></a>إعدادات التكوين الموصى بها الأخرى

بعد إلحاق الأجهزة بالخدمة، من المهم الاستفادة من قدرات الحماية من التهديدات المضمنة من خلال تمكينها باستخدام إعدادات التكوين الموصى بها التالية.

### <a name="device-collection-configuration"></a>تكوين مجموعة الأجهزة

إذا كنت تستخدم Configuration Manager نقطة النهاية، الإصدار 2002 أو الإصدارات الأحدث، يمكنك اختيار توسيع النشر ليشمل خوادم أو عملاء من المستوى الأدنى.

### <a name="next-generation-protection-configuration"></a>تكوين حماية الجيل التالي

يوصى بإعدادات التكوين التالية:

**المسح الضوئي**

- فحص أجهزة التخزين القابلة للإزالة مثل محركات أقراص USB: نعم

**الحماية في الوقت الحقيقي**

- تمكين المراقبة السلوكية: نعم
- تمكين الحماية من التطبيقات غير المرغوب فيها عند التنزيل وقبل التثبيت: نعم

**خدمة حماية السحابة**

- نوع عضوية خدمة حماية السحابة: العضوية المتقدمة

**تقليل الأجزاء المعرضة للهجوم** تكوين كافة القواعد المتوفرة للتدقيق.

> [!NOTE]
> قد يؤدي حظر هذه الأنشطة إلى مقاطعة العمليات التجارية المشروعة. أفضل نهج هو تعيين كل شيء للتدقيق، وتحديد تلك الآمنة لتشغيلها، ثم تمكين تلك الإعدادات على نقاط النهاية التي لا تحتوي على اكتشافات إيجابية خاطئة.

**حماية الشبكة**

قبل تمكين حماية الشبكة في وضع التدقيق أو الحظر، تأكد من تثبيت تحديث النظام الأساسي لمكافحة البرامج الضارة، والذي يمكن الحصول عليه من [صفحة الدعم](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

**الوصول إلى المجلدات الخاضعة للتحكم**

تمكين الميزة في وضع التدقيق لمدة 30 يوما على الأقل. بعد هذه الفترة، راجع عمليات الكشف وأنشئ قائمة بالتطبيقات المسموح لها بالكتابة إلى الدلائل المحمية.

لمزيد من المعلومات، راجع [تقييم الوصول إلى المجلدات التي يتم التحكم فيها](/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access).

## <a name="offboard-devices-using-configuration-manager"></a>إيقاف تشغيل الأجهزة باستخدام Configuration Manager

لأسباب تتعلق بالأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم الإلحاق المنتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة الإلحاق، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم وسيتم تضمينها أيضا في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر نهج الإلحاق والإلحاق على نفس الجهاز في نفس الوقت، وإلا فسيؤدي ذلك إلى تضاربات غير متوقعة.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>إيقاف تشغيل الأجهزة باستخدام الفرع الحالي Microsoft Endpoint Configuration Manager

إذا كنت تستخدم Microsoft Endpoint Configuration Manager الفرع الحالي، فراجع [إنشاء ملف تكوين الإلحاق](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>إيقاف تشغيل الأجهزة باستخدام System Center 2012 R2 Configuration Manager

1. احصل على حزمة الإلحاق من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a>:

2. في جزء التنقل، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**الإعدادات**</a> >   **Device onboardingOffboarding**> .

3. حدد Windows 10 كنظام التشغيل.

4. في حقل **أسلوب النشر**، حدد **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

5. حدد **حزمة التنزيل**، واحفظ ملف .zip.

6. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف باسم *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

7. نشر الحزمة باتباع الخطوات الواردة في المقالة "[الحزم والبرامج" في مركز النظام 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)).

8. اختر مجموعة أجهزة معرفة مسبقا لنشر الحزمة إليها.

> [!IMPORTANT]
> يؤدي إلغاء الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات كان قد تم الاحتفاظ بها لمدة تصل إلى 6 أشهر.

## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز

إذا كنت تستخدم الفرع الحالي Microsoft Endpoint Configuration Manager، فاستخدم لوحة معلومات Microsoft Defender لنقطة النهاية المضمنة في وحدة التحكم Configuration Manager. لمزيد من المعلومات، راجع [الحماية المتقدمة من التهديدات من Microsoft Defender - Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

إذا كنت تستخدم System Center 2012 R2 Configuration Manager، تتكون المراقبة من جزأين:

1. تأكيد توزيع حزمة التكوين بشكل صحيح وتشغيلها (أو تشغيلها بنجاح) على الأجهزة في الشبكة.

2. التحقق من أن الأجهزة متوافقة مع خدمة إلحاق الجهاز Microsoft 365 (وهذا يضمن أن الجهاز يمكنه إكمال عملية الإلحاق ويمكنه الاستمرار في الإبلاغ عن البيانات إلى الخدمة).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>تأكيد نشر حزمة التكوين بشكل صحيح

1. في وحدة التحكم Configuration Manager، انقر فوق **"Monitoring**" في أسفل جزء التنقل.

2. حدد **"Overview** " ثم **"Deployments**".

3. حدد عند التوزيع باسم الحزمة.

4. راجع مؤشرات الحالة ضمن **إحصائيات الإكمال** **وحالة المحتوى**.

    إذا كانت هناك عمليات نشر فاشلة (أجهزة بها **حالات خطأ** أو **متطلبات غير مستوفية** أو **فاشلة**)، فقد تحتاج إلى استكشاف أخطاء الأجهزة وإصلاحها. لمزيد من المعلومات، راجع [استكشاف أخطاء الحماية المتقدمة من التهديدات في Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![Configuration Manager تظهر عملية نشر ناجحة بدون أخطاء.](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>تحقق من أن الأجهزة متوافقة مع خدمة منع فقدان بيانات نقطة النهاية Microsoft 365

يمكنك تعيين قاعدة توافق لعنصر التكوين في System Center 2012 R2 Configuration Manager لمراقبة التوزيع.

> [!NOTE]
> ينطبق هذا الإجراء وإدخال التسجيل على DLP نقطة النهاية وكذلك Defender لنقطة النهاية.

يجب أن تكون هذه القاعدة عنصر تكوين قاعدة توافق *غير معالجة* يراقب قيمة مفتاح التسجيل على الأجهزة المستهدفة.

مراقبة إدخال مفتاح التسجيل التالي:

```text
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

لمزيد من المعلومات، راجع [مقدمة حول إعدادات التوافق في System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام نهج المجموعة](device-onboarding-gp.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام أدوات إدارة الأجهزة المحمولة](device-onboarding-mdm.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [استكشاف أخطاء الحماية المتقدمة من التهديدات في Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
