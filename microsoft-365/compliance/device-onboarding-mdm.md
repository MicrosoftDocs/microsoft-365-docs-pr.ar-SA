---
title: أجهزة Windows 10 Windows 11 الأجهزة باستخدام أدوات إدارة أجهزة المحمول
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
description: استخدم أدوات "إدارة أجهزة المحمول" لنشر حزمة التكوين على الأجهزة بحيث يتم تهيئة هذه الحزمة في الخدمة.
ms.openlocfilehash: 578a1e06bf5f83f700c5db69ddc32a480d68b729
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/03/2022
ms.locfileid: "63578553"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>أجهزة Windows 10 Windows 11 الأجهزة باستخدام أدوات إدارة أجهزة المحمول

**ينطبق على:**

- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

يمكنك استخدام حلول إدارة أجهزة المحمول (MDM) لتكوين الأجهزة. Microsoft 365 حماية المعلومات إلى دعم MDMs من خلال توفير OMA-URIs لإنشاء سياسات لإدارة الأجهزة.


## <a name="before-you-begin"></a>قبل البدء
إذا كنت تستخدم Microsoft Intune، فيجب أن يكون الجهاز MDM مسجلا. وإلا، لن يتم تطبيق الإعدادات بنجاح. 

لمزيد من المعلومات حول تمكين MDM باستخدام Microsoft Intune، راجع [تسجيل الجهاز (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>الأجهزة المجهزة باستخدام Microsoft Intune

اتبع الإرشادات الواردة [من Intune](/intune/advanced-threat-protection).

> [!NOTE]
> - يستخدم **نهج حالة الصحة** للأجهزة المجهزة خصائص للقراءة فقط ولا يمكن إصلاحها.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>إيقاف تشغيل الأجهزة ومراقبتها باستخدام أدوات إدارة أجهزة المحمول

لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

1. احصل على حزمة إيقاف التشغيل من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a>.

2. في جزء التنقل **، حدد الإعدادات** >  **الإعادة الboardingOffboarding** > .

3. في الحقل **أسلوب النشر**، حدد **إدارة أجهزة المحمول / Microsoft Intune**.

4. انقر **فوق تنزيل الحزمة**، واحفظ .zip الملف.

5. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف *يسمى DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. استخدم Microsoft Intune التكوين المخصص لنشر إعدادات OMA-URI المدعومة التالية.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> إذا تم تكوين Microsoft Defender لنقطة النهاية بالفعل، يمكنك تشغيل إعداد  الجهاز ولم تعد الخطوة 6 مطلوبة.

> [!NOTE]
> يستخدم **نهج حالة الصحة** للأجهزة غير المجهزة خصائص للقراءة فقط ولا يمكن إصلاحها.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows 10 باستخدام "نهج المجموعة"](device-onboarding-gp.md)
- [أجهزة Windows 10 التي تستخدم Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [أجهزة Windows 10 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [استكشاف مشاكل توفير الحماية المتقدمة من المخاطر ل Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
