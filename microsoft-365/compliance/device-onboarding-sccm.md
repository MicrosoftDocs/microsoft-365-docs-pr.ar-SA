---
title: أجهزة Windows 10 Windows 11 باستخدام "إدارة التكوين"
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
description: استخدم "إدارة التكوين" لنشر حزمة التكوين على الأجهزة بحيث يتم تهيئة هذه الحزمة في الخدمة.
ms.openlocfilehash: 9f9edc9543a446f98622ff80d8cceec406a2658a
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/12/2021
ms.locfileid: "63570896"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-configuration-manager"></a>أجهزة Windows 10 Windows 11 باستخدام "إدارة التكوين"

**ينطبق على:**

- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

### <a name="onboard-devices-using-system-center-configuration-manager"></a>الأجهزة المجهزة باستخدام System Center Configuration Manager

1. احصل على حزمة .zip ملف (*DeviceComplianceOnboardingPackage.zip*) من [مركز التوافق من Microsoft](https://compliance.microsoft.com/).

2. في جزء التنقل <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**، حدد الإعدادات**</a> >  **التأليف OnboardingOnboarding** > .

3. في الحقل **أسلوب النشر**، حدد Microsoft Endpoint Configuration Manager **2012/2012 R2/1511/1602**.

4. حدد **تنزيل الحزمة**، واحفظ الملف .zip.

5. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف *يسمى DeviceComplianceOnboardingScript.cmd*.

6. نشر الحزمة باتباع الخطوات في المقالة الحزم والبرامج [في System Center 2012 إدارة التكوين R2](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)) .

7. اختر مجموعة أجهزة محددة مسبقا لنشر الحزمة فيها.

> [!NOTE]
> Microsoft 365 عدم دعم حماية المعلومات أثناء مرحلة تجربة "خارج الصندوق" [(OOBE](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87)). تأكد من أن المستخدمين يكملون OOBE بعد Windows التثبيت أو الترقية.

> [!TIP]
> بعد تشغيل الجهاز، يمكنك أن تختار تشغيل اختبار الكشف للتحقق من أن الجهاز مواد بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender ل Endpoint](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test) تم تشغيله حديثا.
>
> تجدر الإشارة إلى أنه من الممكن إنشاء قاعدة الكشف في تطبيق "إدارة التكوين" للتحقق بشكل مستمر مما إذا تم تهيئة جهاز. التطبيق هو نوع مختلف من الكائنات عن الحزمة والبرنامج.
> إذا لم يتم بعد تهيئة جهاز (بسبب اكتمال OOBE المعلق أو أي سبب آخر)، فإن إدارة التكوين ست محاولة لتهيئة الجهاز حتى تكتشف القاعدة تغيير الحالة.
>
> يمكن تنفيذ هذا السلوك عن طريق إنشاء قاعدة الكشف للتحقق مما إذا كانت قيمة السجل "OnboardingState" (من النوع REG_DWORD) = 1.
> تقع قيمة التسجيل هذه ضمن "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
لمزيد من المعلومات، راجع [تكوين أساليب الكشف في System Center 2012 تكوين R2](/previous-versions/system-center/system-center-2012-R2/gg682159(v=technet.10)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>تكوين إعدادات المجموعة العينة

لكل جهاز، يمكنك تعيين قيمة تكوين لتحدد ما إذا كان يمكن تجميع عينات من الجهاز عند تقديم طلب عبر مركز حماية Microsoft Defender لإرسال ملف لتحليله بعمق.

> [!NOTE]
> تتم إعدادات التكوين هذه عادة من خلال إدارة التكوين.

يمكنك تعيين قاعدة توافق لعناصر التكوين في "إدارة التكوين" لتغيير إعداد المشاركة العينة على جهاز.

يجب أن تكون هذه *القاعدة عنصرا لتكوين* قاعدة التوافق التي تقوم بتعيين قيمة مفتاح التسجيل على الأجهزة المستهدفة للتأكد من أنها شكوى.

يتم تعيين التكوين من خلال إدخال مفتاح التسجيل التالي:

```
Path: “HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection”
Name: "AllowSampleCollection"
Value: 0 or 1
```
المكان:<br>
نوع المفتاح هو D-WORD. <br>
القيم المحتملة هي:
- 0 - لا يسمح بالمشاركة العينة من هذا الجهاز
- 1 - يسمح بمشاركة كل أنواع الملفات من هذا الجهاز

القيمة الافتراضية في حالة عدم وجود مفتاح التسجيل هي 1.

لمزيد من المعلومات حول توافق إدارة تكوين مركز النظام، راجع [مقدمة حول إعدادات التوافق في System Center 2012 إدارة تكوين R2](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).


## <a name="other-recommended-configuration-settings"></a>إعدادات التكوين المستحسنة الأخرى
بعد تهيئة الأجهزة للخدمة، من المهم الاستفادة من إمكانات الحماية من المخاطر المضمنة من خلال تمكينها بإعدادات التكوين الموصى بها التالية.

### <a name="device-collection-configuration"></a>تكوين مجموعة الأجهزة
إذا كنت تستخدم إدارة تكوين نقطة النهاية، الإصدار 2002 أو الإصدارات الأحدث، يمكنك أن تختار تعزيز النشر ليشمل خوادم أو عملاء من المستوى الأسفل.


### <a name="next-generation-protection-configuration"></a>تكوين حماية الجيل التالي

يوصى بإعدادات التكوين التالية:

**المسح الضوئي**

- فحص أجهزة التخزين القابلة للإزالة مثل محركات أقراص USB: نعم

**الحماية في الوقت الحقيقي**

- تمكين المراقبة السلوكية: نعم
- تمكين الحماية من التطبيقات التي يحتمل أن تكون غير مرغوب فيها عند التنزيل وقبل التثبيت: نعم

**خدمة الحماية السحابية**

- نوع عضوية خدمة الحماية السحابية: العضوية المتقدمة

**الحد من سطح الهجوم** تكوين كافة القواعد المتوفرة للتدقيق.

> [!NOTE]
> قد يؤدي حظر هذه الأنشطة إلى مقاطعة عمليات الأعمال المشروعة. أفضل طريقة هي تعيين كل شيء للتدقيق، وتحديد الإعدادات الآمنة التي يمكن تشغيلها، ثم تمكين هذه الإعدادات على نقاط النهاية التي لا تملك عمليات الكشف الإيجابي الخاطئة.

**حماية الشبكة**

قبل تمكين حماية الشبكة في وضع التدقيق أو الحظر، تأكد من تثبيت تحديث النظام الأساسي للحماية من البرامج الضارة، الذي يمكن الحصول عليه من [صفحة الدعم](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).


**الوصول إلى المجلدات الخاضعة للتحكم**

تمكين الميزة في وضع التدقيق لمدة 30 يوما على الأقل. بعد هذه الفترة، راجع الاكتشافات وأنشئ قائمة التطبيقات المسموح لها الكتابة إلى الدلائل المحمية.

لمزيد من المعلومات، راجع [تقييم الوصول المتحكم به للمجلدات](/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access).


## <a name="offboard-devices-using-configuration-manager"></a>أجهزة إيقاف التشغيل باستخدام "إدارة التكوين"

لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>أجهزة إيقاف التشغيل التي تستخدم Microsoft Endpoint Configuration Manager الحالي

إذا كنت تستخدم Microsoft Endpoint Configuration Manager الحالي، فشاهد [إنشاء ملف تكوين إيقاف التشغيل](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>أجهزة إيقاف التشغيل System Center 2012 إدارة تكوين R2

1. احصل على حزمة إيقاف التشغيل من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a>:

2. في جزء التنقل <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**، حدد الإعدادات**</a> >   **الإعادة الboardingOffboarding**> .

3. حدد Windows 10 نظام التشغيل.

4. في الحقل **أسلوب النشر**، حدد Microsoft Endpoint Configuration Manager **2012/2012 R2/1511/1602**.

5. حدد **تنزيل الحزمة**، واحفظ الملف .zip.

6. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف *يسمى DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

7. نشر الحزمة باتباع الخطوات في المقالة الحزم والبرامج [في System Center 2012 إدارة التكوين R2](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)) .

8. اختر مجموعة أجهزة محددة مسبقا لنشر الحزمة فيها.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.


## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز

إذا كنت تستخدم Microsoft Endpoint Configuration Manager الحالي، فاستخدم لوحة معلومات Microsoft Defender المضمنة لنقطة النهاية في وحدة تحكم إدارة التكوين. لمزيد من المعلومات، راجع [الحماية المتقدمة من المخاطر من Microsoft Defender - جهاز العرض](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

إذا كنت تستخدم إدارة تكوين System Center 2012 R2، فإن المراقبة تتكون من جزأين:

1. تأكيد نشر حزمة التكوين بشكل صحيح وتشغيلها (أو تشغيلها بنجاح) على الأجهزة في شبكتك.

2. التحقق من أن الأجهزة متوافقة مع خدمة Microsoft 365 الأجهزة (يضمن ذلك أن الجهاز يمكنه إكمال عملية التكهين ويمكنه الاستمرار في الإبلاغ عن البيانات إلى الخدمة).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>تأكيد نشر حزمة التكوين بشكل صحيح

1. في وحدة تحكم إدارة التكوين، انقر فوق **مراقبة** في أسفل جزء التنقل.

2. حدد **نظرة عامة** ثم **عمليات النشر**.

3. حدد على النشر باستخدام اسم الحزمة.

4. راجع مؤشرات الحالة ضمن **إحصائيات الإكمال** حالة **المحتوى**.

    في حالة فشل عمليات النشر (الأجهزة التي بها أخطاء أو متطلبات **لم** يتم تحقيقها أو فشل الحالات)، فقد تحتاج إلى استكشاف أخطاء الأجهزة وإصلاحها. لمزيد من المعلومات، راجع استكشاف مشاكل التكدث المتقدمة للحماية من المخاطر من [Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![تعرض إدارة التكوين عملية نشر ناجحة بدون أخطاء.](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>التحقق من أن الأجهزة متوافقة مع خدمة منع فقدان Microsoft 365 نقطة نهاية النهاية

يمكنك تعيين قاعدة توافق لعناصر التكوين في System Center 2012 إدارة تكوين R2 لمراقبة النشر.

> [!NOTE]
> ينطبق هذا الإجراء وأدخل السجل على نقطة النهاية DLP وكذلك على Defender لنقطة النهاية.

يجب أن تكون هذه القاعدة *عنصر* تكوين قاعدة توافق غير معالجة يراقب قيمة مفتاح التسجيل على الأجهزة المستهدفة.

راقب إدخال مفتاح التسجيل التالي:
```
Path: “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status”
Name: “OnboardingState”
Value: “1”
```
لمزيد من المعلومات، راجع [مقدمة حول إعدادات التوافق في System Center 2012 إدارة تكوين R2](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows 10 Windows 11 باستخدام "نهج المجموعة"](device-onboarding-gp.md)
- [أجهزة Windows 10 Windows 11 الأجهزة باستخدام أدوات إدارة أجهزة المحمول](device-onboarding-mdm.md)
- [أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية الذي تم تشغيله حديثا](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [استكشاف مشاكل توفير الحماية المتقدمة من المخاطر ل Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)