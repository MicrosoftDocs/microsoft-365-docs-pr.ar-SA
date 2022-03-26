---
title: أجهزة Windows 10 Windows 11 عبر "نهج المجموعة"
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: استخدم "نهج المجموعة" لنشر حزمة التكوين على Windows 10 والأجهزة Windows 11 بحيث يتم إعدادها في الخدمة.
ms.openlocfilehash: fbba73fcf15ee9f71c4caacc57155a64e6cb9e9c
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/12/2021
ms.locfileid: "63572074"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>أجهزة Windows 10 وأجهزة Windows 11 باستخدام "نهج المجموعة" 

**ينطبق على:**

- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- نهج المجموعة

> [!NOTE]
> لاستخدام تحديثات نهج المجموعة (GP) لنشر الحزمة، يجب أن تكون على Windows Server 2008 R2 أو إصدار أحدث.

> بالنسبة Windows Server 2019، قد تحتاج إلى استبدال NT AUTHORITY\Well-Known-System-Account بملف NT AUTHORITY\SYSTEM لملف XML الذي ينشئه تفضيلات نهج المجموعة.

## <a name="onboard-devices-using-group-policy"></a>الأجهزة المجهزة باستخدام "نهج المجموعة"

1. افتح [مركز التوافق](https://compliance.microsoft.com).

2. في جزء التنقل **، حدد الإعدادات** >  **التأليف**.

3. في الحقل **أسلوب النشر** ، حدد **نهج المجموعة**.

4. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

5. استخراج محتويات الملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الجهاز. يجب أن يكون لديك مجلد يسمى *اختياريParamsPolicy* والملف *DeviceComplianceLocalOnboardingScript.cmd*.

6. افتح وحدة [تحكم إدارة نهج](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) المجموعة (GPMC)، وانقر بز الماوس الأيمن فوق كائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **تحرير**.

7. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر**، ثم **التفضيلات**، ثم إعدادات **لوحة التحكم**.

8. انقر بز الماوس الأيمن فوق **المهام المجدولة**، وأشير إلى **جديد**، ثم انقر فوق مهمة فورية (على الأقل **Windows 7)**.

9. في نافذة **المهمة** التي تفتح، انتقل إلى علامة **التبويب عام** . ضمن **خيارات الأمان،** انقر **فوق تغيير المستخدم أو المجموعة** وا اكتب النظام، ثم انقر **فوق التحقق من الأسماء** ثم **موافق**. يظهر NT AUTHORITY\SYSTEM ك حساب المستخدم الذي سيتم تشغيل المهمة عليه.

10. حدد **تشغيل ما إذا كان المستخدم قد سجل دخوله** أم لا وحدد خانة الاختيار **تشغيل بأعلى** امتيازات.

11. انتقل إلى علامة **التبويب** إجراءات وانقر فوق **جديد...** تأكد من **تحديد بدء** برنامج في **حقل** الإجراء. أدخل اسم الملف وموقع ملف *WindowsDefenderATPOnboardingScript.cmd* المشترك.

12. انقر **فوق موافق** وأغلق أي نوافذ GPMC مفتوحة.

## <a name="offboard-devices-using-group-policy"></a>أجهزة إيقاف التشغيل باستخدام "نهج المجموعة"
لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة لألواح التشغيل بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

1. احصل على حزمة إيقاف التشغيل من [مركز التوافق من Microsoft](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. في جزء التنقل **، حدد الإعدادات** > **/Device onboardingOffboarding** > .

3. في الحقل **أسلوب النشر** ، حدد **نهج المجموعة**.

4. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

5. استخراج محتويات الملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الجهاز. يجب أن يكون لديك ملف *يسمى DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. افتح وحدة [تحكم إدارة نهج](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) المجموعة (GPMC)، وانقر بز الماوس الأيمن فوق كائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **تحرير**.

7. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر، ثم** **التفضيلات**، ثم إعدادات **لوحة التحكم**.

8. انقر **بضغطة زر الماوس الأيمن فوق المهام المجدولة**، وأشير إلى **جديد**، ثم انقر فوق **مهمة فورية**.

9. في نافذة **المهمة** التي تفتح، انتقل إلى علامة **التبويب عام** . اختر حساب مستخدم النظام المحلي (BUILTIN\SYSTEM) ضمن **خيارات الأمان**.

10. حدد **تشغيل سواء قام المستخدم بتسجيل الدخول أم** لا وحدد خانة  الاختيار تشغيل بأعلى امتيازات.

11. انتقل إلى علامة **التبويب** إجراءات وانقر فوق **جديد...**. تأكد من **تحديد بدء** برنامج في **حقل** الإجراء. أدخل اسم الملف وموقع الملف المشترك DeviceComplianceOffboardingScript_valid_until_YYYY  *MM-DD.cmd* .

12. انقر **فوق موافق** وأغلق أي نوافذ GPMC مفتوحة.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن البيانات من الجهاز.


## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز
باستخدام "نهج المجموعة"، لا يوجد خيار لمراقبة نشر النهج على الأجهزة. يمكن القيام بالمراقبة مباشرة على المدخل، أو باستخدام أدوات النشر المختلفة.

## <a name="monitor-devices-using-the-portal"></a>مراقبة الأجهزة باستخدام المدخل
1. انتقل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">إلى مركز التوافق في Microsoft 365.</a>
2. انقر **فوق قائمة** الأجهزة.
3. تحقق من ظهور الأجهزة.

> [!NOTE]
> قد يستغرق ظهور الأجهزة على قائمة **الأجهزة عدة أيام**. يشمل ذلك الوقت الذي يستغرقه توزيع السياسات على الجهاز والوقت الذي يستغرقه تسجيل دخول المستخدم والوقت الذي تستغرقه نقطة النهاية لبدء إعداد التقارير.


## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows 10 وأجهزة Windows 11 باستخدام Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [أجهزة Windows 10 Windows 11 الأجهزة باستخدام أدوات إدارة أجهزة المحمول](device-onboarding-mdm.md)
- [أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [تشغيل اختبار الكشف على Microsoft Defender للأجهزة التي تم تشغيلها حديثا في نقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [استكشاف مشاكل توفير الحماية المتقدمة من المخاطر ل Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)