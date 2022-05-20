---
title: أجهزة Windows باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول
description: استخدم أدوات إدارة الجهاز الأجهزة المحمولة لنشر حزمة التكوين على الأجهزة بحيث يتم إلحاقها بخدمة Defender لنقطة النهاية.
keywords: إلحاق الأجهزة باستخدام mdm، وإدارة الأجهزة، وتهيئة أجهزة Microsoft Defender لنقطة النهاية، وأجهزة mdm
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3e81470cb02742eb94e62118f77f1ae0e8c62f90
ms.sourcegitcommit: b5529afa84f7dde0a89b1e08aeaf6a3a15cd7679
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65599649"
---
# <a name="onboard-windows-devices-using-mobile-device-management-tools"></a>أجهزة Windows باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

يمكنك استخدام حلول إدارة أجهزة المحمول (MDM) لتكوين أجهزة Windows 10. يدعم Defender لنقطة النهاية أجهزة MDMs من خلال توفير OMA-URIs لإنشاء نهج لإدارة الأجهزة.


لمزيد من المعلومات حول استخدام Defender لنقطة النهاية، راجع ملف DDF ل [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) [وWindowsAdvancedThreatProtection DDF](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>قبل البدء

إذا كنت تستخدم Microsoft Intune، يجب أن يكون الجهاز MDM مسجلا. وإلا، فلن يتم تطبيق الإعدادات بنجاح.

لمزيد من المعلومات حول تمكين MDM باستخدام Microsoft Intune، راجع [تسجيل الجهاز (Microsoft Intune).](/mem/intune/enrollment/device-enrollment)

## <a name="onboard-devices-using-microsoft-intune"></a>إلحاق الأجهزة باستخدام Microsoft Intune

اطلع على [ملف PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) أو [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) للاطلاع على المسارات المختلفة في نشر Defender لنقطة النهاية.

اتبع الإرشادات من [Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).


لمزيد من المعلومات حول استخدام Defender لنقطة النهاية، راجع ملف DDF ل [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) [وWindowsAdvancedThreatProtection DDF](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - يستخدم نهج **الحالة الصحية للأجهزة المضمنة** خصائص للقراءة فقط ولا يمكن معالجتها.
> - يتوفر تكوين تكرار تقارير البيانات التشخيصية فقط للأجهزة على Windows 10، الإصدار 1703.


اطلع على [ملف PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) أو [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) للاطلاع على المسارات المختلفة في نشر Microsoft Defender لنقطة النهاية.

## <a name="run-a-detection-test-to-verify-onboarding"></a>تشغيل اختبار الكشف للتحقق من الإلحاق
بعد إلحاق الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أن الجهاز تم إلحاقه بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](run-detection-test.md).


## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>إيقاف تشغيل الأجهزة ومراقبتها باستخدام أدوات إدارة الجهاز الأجهزة المحمولة

لأسباب تتعلق بالأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم الإلحاق المنتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة الإلحاق، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم وسيتم تضمينها أيضا في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر نهج الإلحاق والإلحاق على نفس الجهاز في نفس الوقت، وإلا فسيؤدي ذلك إلى تضاربات غير متوقعة.

1. احصل على حزمة الإلحاق من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>:

   1. في جزء التنقل، حدد **"الإعدادات** \> **Endpoints** \> **Device Management** \> **Offboarding**".

   1. حدد Windows 10 أو Windows 11 كنظام التشغيل.

   1. في حقل **أسلوب النشر**، حدد **"Mobile إدارة الجهاز/ Microsoft Intune**".

   1. انقر فوق **"تنزيل الحزمة**"، واحفظ ملف .zip.

2. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف يسمى *WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding*.

3. استخدم نهج التكوين المخصص Microsoft Intune لنشر إعدادات OMA-URI المدعومة التالية.
   - OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - نوع التاريخ: سلسلة
   - القيمة: [نسخ القيمة ولصقها من محتوى ملف WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding]

لمزيد من المعلومات حول إعدادات نهج Microsoft Intune، راجع [إعدادات النهج Windows 10 في Microsoft Intune](/mem/intune/configuration/custom-settings-windows-10).

> [!NOTE]
> يستخدم نهج **الحالة الصحية للأجهزة التي تم إلغاء إلحاقها** خصائص للقراءة فقط ولا يمكن معالجتها.

> [!IMPORTANT]
> يؤدي إلغاء الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات كان قد تم الاحتفاظ بها لمدة تصل إلى 6 أشهر.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows باستخدام نهج المجموعة](configure-endpoints-gp.md)
- [أجهزة Windows التي تستخدم Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [أجهزة Windows باستخدام برنامج نصي محلي](configure-endpoints-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)
- [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](run-detection-test.md)
- [استكشاف أخطاء إلحاق Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-onboarding.md)
