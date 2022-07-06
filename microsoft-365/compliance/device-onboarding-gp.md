---
title: إلحاق أجهزة Windows 10 وأجهزة Windows 11 عبر نهج المجموعة
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
description: استخدم نهج المجموعة لنشر حزمة التكوين على Windows 10 والأجهزة Windows 11 بحيث يتم إلحاقها إلى الخدمة.
ms.openlocfilehash: 6c8c70d1bfdf3de0bc3848069a22b8610d445e42
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623242"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>إلحاق أجهزة Windows 10 Windows 11 باستخدام نهج المجموعة 

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)
- نهج المجموعة

> [!NOTE]
> لاستخدام تحديثات نهج المجموعة (GP) لنشر الحزمة، يجب أن تكون على Windows Server 2008 R2 أو إصدار أحدث.

> بالنسبة إلى Windows Server 2019، قد تحتاج إلى استبدال NT AUTHORITY\Well-Known-System-Account ب NT AUTHORITY\SYSTEM لملف XML الذي ينشئه تفضيل نهج المجموعة.

## <a name="onboard-devices-using-group-policy"></a>إلحاق الأجهزة باستخدام نهج المجموعة

1. افتح [مركز التوافق](https://compliance.microsoft.com).

2. في جزء التنقل، حدد **الإعدادات** > **"إلحاق الجهاز**".

3. في حقل **أسلوب النشر** ، حدد **نهج المجموعة**.

4. انقر فوق **"تنزيل الحزمة** " واحفظ ملف .zip.

5. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الجهاز. يجب أن يكون لديك مجلد يسمى *OptionalParamsPolicy* وملف *DeviceComplianceLocalOnboardingScript.cmd*.

6. افتح [وحدة تحكم إدارة نهج المجموعة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC)، وانقر بزر الماوس الأيمن فوق الكائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **"تحرير**".

7. في **نهج المجموعة Management Editor**، انتقل إلى **تكوين الكمبيوتر**، ثم **التفضيلات**، ثم **إعدادات لوحة التحكم**.

8. انقر بزر الماوس الأيمن فوق **المهام المجدولة**، وأشر إلى **"جديد**"، ثم انقر فوق **"مهمة فورية" (Windows 7 على الأقل).**

9. في النافذة **"مهمة** " التي يتم فتحها، انتقل إلى علامة التبويب **"عام** ". ضمن **خيارات الأمان** ، انقر فوق **"تغيير المستخدم أو المجموعة** " واكتب "نظام" ثم انقر فوق **"التحقق من الأسماء** " ثم " **موافق**". يظهر NT AUTHORITY\SYSTEM كحساب المستخدم الذي سيتم تشغيل المهمة عليه.

10. حدد **"تشغيل" سواء تم تسجيل دخول المستخدم أم لا** وحدد خانة الاختيار **"تشغيل بامتيازات أعلى** ".

11. انتقل إلى علامة التبويب **"إجراءات** " وانقر فوق **"جديد"...** تأكد **من تحديد "بدء برنامج** " في الحقل **"إجراء** ". أدخل اسم الملف وموقع ملف *WindowsDefenderATPOnboardingScript.cmd* المشترك.

12. انقر فوق **"موافق** " وأغلق أي نوافذ GPMC مفتوحة.

## <a name="offboard-devices-using-group-policy"></a>إيقاف تشغيل الأجهزة باستخدام نهج المجموعة
لأسباب أمنية، ستنتهي صلاحية الحزمة المستخدمة لإلغاء إلحاق الأجهزة بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم الإلحاق المنتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة الإلحاق، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم وسيتم تضمينها أيضا في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر نهج الإلحاق والإلحاق على نفس الجهاز في نفس الوقت، وإلا فسيؤدي ذلك إلى تضاربات غير متوقعة.

1. احصل على حزمة الإلحاق من [مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. في جزء التنقل، حدد **Settings** > **/Device onboarding** > **Offboarding**.

3. في حقل **أسلوب النشر** ، حدد **نهج المجموعة**.

4. انقر فوق **"تنزيل الحزمة** " واحفظ ملف .zip.

5. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الجهاز. يجب أن يكون لديك ملف باسم *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. افتح [وحدة تحكم إدارة نهج المجموعة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC)، وانقر بزر الماوس الأيمن فوق الكائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **"تحرير**".

7. في **نهج المجموعة Management Editor**، انتقل إلى **تكوين الكمبيوتر،** ثم **التفضيلات**، ثم **إعدادات لوحة التحكم**.

8. انقر بزر الماوس الأيمن فوق **المهام المجدولة**، وأشر إلى **"جديد"**، ثم انقر فوق **"مهمة فورية**".

9. في النافذة **"مهمة** " التي يتم فتحها، انتقل إلى علامة التبويب **"عام** ". اختر حساب مستخدم SYSTEM المحلي (BUILTIN\SYSTEM) ضمن **خيارات الأمان**.

10. حدد **"تشغيل" سواء تم تسجيل دخول المستخدم أم لا** وحدد خانة الاختيار **"تشغيل بامتيازات أعلى** ".

11. انتقل إلى علامة التبويب **"إجراءات** " وانقر فوق **"جديد"...**. تأكد **من تحديد "بدء برنامج** " في الحقل **"إجراء** ". أدخل اسم الملف وموقع الملف  *المشترك DeviceComplianceOffboardingScript_valid_until_YYYY MM-DD.cmd* .

12. انقر فوق **"موافق** " وأغلق أي نوافذ GPMC مفتوحة.

> [!IMPORTANT]
> يؤدي إيقاف الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن البيانات من الجهاز.


## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز
مع نهج المجموعة لا يوجد خيار لمراقبة نشر النهج على الأجهزة. يمكن إجراء المراقبة مباشرة على المدخل، أو باستخدام أدوات النشر المختلفة.

## <a name="monitor-devices-using-the-portal"></a>مراقبة الأجهزة باستخدام المدخل
1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a>.
2. انقر فوق قائمة **الأجهزة** .
3. تحقق من ظهور الأجهزة.

> [!NOTE]
> قد يستغرق ظهور الأجهزة في **قائمة الأجهزة** عدة أيام. وهذا يشمل الوقت الذي يستغرقه توزيع النهج على الجهاز والوقت الذي يستغرقه المستخدم قبل تسجيل الدخول والوقت الذي تستغرقه نقطة النهاية لبدء إعداد التقارير.


## <a name="related-topics"></a>المواضيع ذات الصلة
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام Configuration Manager نقطة نهاية Microsoft](device-onboarding-sccm.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام أدوات إدارة الأجهزة المحمولة](device-onboarding-mdm.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [تشغيل اختبار الكشف على أجهزة Microsoft Defender لنقطة النهاية تم إلحاقها حديثا](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [استكشاف أخطاء الحماية المتقدمة من التهديدات في Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
