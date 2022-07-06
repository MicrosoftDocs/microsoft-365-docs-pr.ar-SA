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
description: استخدم أدوات إدارة الجهاز الأجهزة المحمولة لنشر حزمة التكوين على الأجهزة بحيث يتم إلحاقها للخدمة.
ms.openlocfilehash: d5c03c80c9a38d34ab27f888084604372874a64a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624190"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام أدوات إدارة الأجهزة المحمولة

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)

يمكنك استخدام حلول إدارة أجهزة المحمول (MDM) لتكوين الأجهزة. تدعم حماية المعلومات في Microsoft 365 أجهزة MDMs من خلال توفير OMA-URIs لإنشاء نهج لإدارة الأجهزة.


## <a name="before-you-begin"></a>قبل البدء
إذا كنت تستخدم Microsoft Intune، يجب أن يكون الجهاز MDM مسجلا. وإلا، فلن يتم تطبيق الإعدادات بنجاح. 

لمزيد من المعلومات حول تمكين MDM باستخدام Microsoft Intune، راجع [تسجيل الجهاز (Microsoft Intune).](/mem/intune/enrollment/device-enrollment)

## <a name="onboard-devices-using-microsoft-intune"></a>إلحاق الأجهزة باستخدام Microsoft Intune

اتبع الإرشادات من [Intune](/mem/intune/protect/advanced-threat-protection-configure).
 
> [!NOTE]
> - يستخدم نهج **الحالة الصحية للأجهزة المضمنة** خصائص للقراءة فقط ولا يمكن معالجتها.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>إيقاف تشغيل الأجهزة ومراقبتها باستخدام أدوات إدارة الجهاز الأجهزة المحمولة

لأسباب تتعلق بالأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم الإلحاق المنتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة الإلحاق، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم وسيتم تضمينها أيضا في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر نهج الإلحاق والإلحاق على نفس الجهاز في نفس الوقت، وإلا فسيؤدي ذلك إلى تضاربات غير متوقعة.

1. احصل على حزمة الإلحاق من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a>.

2. في جزء التنقل، حدد **"إعدادات** > **الجهاز" ضمن** > **"إلغاء الإلحاق**".

3. في حقل **أسلوب النشر**، حدد **"Mobile إدارة الجهاز/ Microsoft Intune**".

4. انقر فوق **"تنزيل الحزمة**"، واحفظ ملف .zip.

5. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف يسمى *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. استخدم نهج التكوين المخصص Microsoft Intune لنشر إعدادات OMA-URI المدعومة التالية.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> إذا تم تكوين Microsoft Defender لنقطة النهاية بالفعل، يمكنك **تشغيل إلحاق الجهاز** ولم تعد الخطوة 6 مطلوبة.

> [!NOTE]
> يستخدم نهج **الحالة الصحية للأجهزة التي تم إلغاء إلحاقها** خصائص للقراءة فقط ولا يمكن معالجتها.

> [!IMPORTANT]
> يؤدي إلغاء الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات كان قد تم الاحتفاظ بها لمدة تصل إلى 6 أشهر.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [إلحاق أجهزة Windows 10 باستخدام نهج المجموعة](device-onboarding-gp.md)
- [إلحاق أجهزة Windows 10 باستخدام نقطة نهاية Microsoft Configuration Manager](device-onboarding-sccm.md)
- [إلحاق أجهزة Windows 10 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [استكشاف أخطاء الحماية المتقدمة من التهديدات في Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
