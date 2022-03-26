---
title: أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي
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
description: استخدم برنامج نصي محلي لنشر حزمة التكوين على الأجهزة بحيث يتم تشغيلها في الخدمة.
ms.openlocfilehash: 14412e782cffd597786a4d2c322fe2b8fc20e5ca
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/12/2021
ms.locfileid: "63575148"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي

**ينطبق على:**

- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

يمكنك أيضا اجهزه فرديه يدويا Microsoft 365. قد ترغب في إجراء ذلك أولا عند اختبار الخدمة قبل الالتزام بتك الجديدة لجميع الأجهزة في الشبكة.

> [!IMPORTANT]
> تم تحسين هذا البرنامج النصي للاستخدام على ما يصل إلى 10 أجهزة.
>
> للنشر على نطاق واسع، استخدم [خيارات النشر الأخرى](device-onboarding-overview.md). على سبيل المثال، يمكنك نشر برنامج نصي للتوفر على أكثر من 10 أجهزة في الإنتاج مع البرنامج النصي المتوفر في أجهزة Windows 10 باستخدام ["نهج المجموعة](device-onboarding-gp.md)".

## <a name="onboard-devices"></a>الأجهزة المجهزة
 
1. الحصول على حزمة التكوين .zip ملف (*DeviceComplianceOnboardingPackage.zip*) من [مركز التوافق من Microsoft](https://compliance.microsoft.com)

2. في جزء التنقل <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**، حدد الإعدادات**</a> >  **التأليف.**

3. في الحقل **أسلوب النشر** ، حدد **برنامج نصي محلي**.

4. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.
  
5. استخراج محتويات حزمة التكوين إلى موقع على الجهاز الذي تريد االلوح به (على سبيل المثال، سطح المكتب). يجب أن يكون لديك ملف *يسمى DeviceOnboardingScript.cmd*.

6. افتح موجه سطر أوامر مرتفعا على الجهاز و تشغيل البرنامج النصي:

7. انتقل إلى **ابدأ** وا اكتب **cmd**.

8. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

    ![نافذة قائمة البدء تشير إلى تشغيل كمسؤول.](../media/dlp-run-as-admin.png)

9. اكتب موقع ملف البرنامج النصي. إذا نسخت الملف إلى سطح المكتب، فاكتوب: *٪userprofile٪\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. اضغط على **المفتاح Enter** أو انقر فوق **موافق**.

للحصول على معلومات حول كيفية التحقق يدويا من امتثال الجهاز وإعلام بيانات المستشعر بشكل صحيح، راجع استكشاف مشاكل توفير الحماية المتقدمة من المخاطر في [Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

## <a name="offboard-devices-using-a-local-script"></a>أجهزة إيقاف التشغيل باستخدام برنامج نصي محلي

لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

1. احصل على حزمة إيقاف التشغيل من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a>.

2. في جزء التنقل <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**، حدد الإعدادات**</a> >  **offboardce**.

3. في الحقل **أسلوب النشر** ، حدد **برنامج نصي محلي**.

4. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

5. استخراج محتويات الملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه بواسطة الأجهزة. يجب أن يكون لديك ملف *يسمى DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. افتح موجه سطر أوامر مرتفعا على الجهاز و تشغيل البرنامج النصي:

7. انتقل إلى **ابدأ** وا اكتب **cmd**.

8. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

    ![نافذة قائمة البدء تشير إلى تشغيل كمسؤول.](../media/dlp-run-as-admin.png)

9. اكتب موقع ملف البرنامج النصي. إذا قمت بنسخ الملف إلى سطح المكتب، فا اكتب: *٪userprofile٪\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. اضغط على **المفتاح Enter** أو انقر فوق **موافق**.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل.

## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز

يمكنك اتباع خطوات التحقق المختلفة في [استكشاف مشاكل التكميل وإصلاحها]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) للتحقق من اكتمال البرنامج النصي بنجاح وتشغيل الوكيل.

يمكن أيضا القيام بالمراقبة مباشرة على المدخل، أو باستخدام أدوات النشر المختلفة.

### <a name="monitor-devices-using-the-portal"></a>مراقبة الأجهزة باستخدام المدخل

1. انتقل إلى [Microsoft 365 التوافق](https://compliance.microsoft.com).

2. اختر **الإعدادات** >  **الأو إلىboardingDevices** > .

1. انتقل إلى مركز التوافق في Microsoft 365، <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**وحدد الإعدادات**</a> >  **الأو إلىboardingDevices** > .

1. تحقق من ظهور الأجهزة.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows 10 Windows 11 باستخدام "نهج المجموعة"](device-onboarding-gp.md)
- [أجهزة Windows 10 وأجهزة Windows 11 باستخدام Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [أجهزة Windows 10 Windows 11 الأجهزة باستخدام أدوات إدارة أجهزة المحمول](device-onboarding-mdm.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية الذي تم تشغيله حديثا](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [استكشاف مشاكل توفير الحماية المتقدمة من المخاطر ل Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)