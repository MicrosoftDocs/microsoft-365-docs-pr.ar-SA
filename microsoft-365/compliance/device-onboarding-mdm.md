---
title: إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام أدوات إدارة الأجهزة المحمولة
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
description: استخدم أدوات إدارة الجهاز المحمول لنشر حزمة التكوين على الأجهزة بحيث يتم تهيئةها للخدمة.
ms.openlocfilehash: 9b329ccf86a2364c13ac72bd4348711d72c17ff5
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634482"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام أدوات إدارة الأجهزة المحمولة

**ينطبق على:**

- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

يمكنك استخدام حلول إدارة أجهزة المحمول (MDM) لتكوين الأجهزة. Microsoft 365 حماية المعلومات إلى دعم MDMs من خلال توفير OMA-URIs لإنشاء سياسات لإدارة الأجهزة.


## <a name="before-you-begin"></a>قبل البدء
إذا كنت تستخدم Microsoft Intune، فيجب أن يكون الجهاز MDM مسجلا. وإلا، لن يتم تطبيق الإعدادات بنجاح. 

لمزيد من المعلومات حول تمكين MDM باستخدام Microsoft Intune، راجع [تسجيل الجهاز (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>الأجهزة المجهزة باستخدام Microsoft Intune

اتبع الإرشادات الواردة [من Intune](/mem/intune/protect/advanced-threat-protection-configure).
 
> [!NOTE]
> - يستخدم **نهج حالة الصحة** للأجهزة المجهزة خصائص للقراءة فقط ولا يمكن إصلاحها.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>إيقاف تشغيل الأجهزة ومراقبتها باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول

لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

1. احصل على حزمة إيقاف التشغيل من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a>.

2. في جزء التنقل **، حدد الإعدادات** >  **الإعادة الboardingOffboarding** > .

3. في الحقل **أسلوب النشر**، حدد الأجهزة المحمولة إدارة الجهاز **/ Microsoft Intune**.

4. انقر **فوق تنزيل الحزمة**، واحفظ .zip الملف.

5. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف *يسمى DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. استخدم Microsoft Intune التكوين المخصص لنشر إعدادات OMA-URI المدعومة التالية.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> إذا Microsoft Defender لنقطة النهاية تم تكوينه بالفعل، يمكنك **تشغيل** تهيئة الجهاز ولم تعد الخطوة 6 مطلوبة.

> [!NOTE]
> يستخدم **نهج حالة الصحة** للأجهزة غير المجهزة خصائص للقراءة فقط ولا يمكن إصلاحها.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows 10 باستخدام نهج المجموعة](device-onboarding-gp.md)
- [أجهزة Windows 10 التي تستخدم Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [أجهزة Windows 10 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [استكشاف مشاكل توفير الحماية المتقدمة من المخاطر ل Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
