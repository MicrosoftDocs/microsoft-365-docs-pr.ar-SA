---
title: إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي
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
description: استخدم برنامج نصي محلي لنشر حزمة التكوين على الأجهزة بحيث يتم إلحاقها للخدمة.
ms.openlocfilehash: 840573794b447162f917fed162bb1f869585286e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634412"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)

يمكنك أيضا إلحاق الأجهزة الفردية يدويا ب Microsoft 365. قد ترغب في القيام بذلك أولا عند اختبار الخدمة قبل الالتزام بإلحاق جميع الأجهزة في شبكتك.

> [!IMPORTANT]
> تم تحسين هذا البرنامج النصي للاستخدام على ما يصل إلى 10 أجهزة.
>
> للنشر على نطاق واسع، استخدم [خيارات النشر الأخرى](device-onboarding-overview.md). على سبيل المثال، يمكنك نشر برنامج نصي للإلحاق لأكثر من 10 أجهزة في الإنتاج مع البرنامج النصي المتوفر في الأجهزة [Windows 10 على متن أجهزة باستخدام نهج المجموعة](device-onboarding-gp.md).

## <a name="onboard-devices"></a>إلحاق الأجهزة
 
1. الحصول على حزمة التكوين .zip ملف (*DeviceComplianceOnboardingPackage.zip*) الحزمة من [مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com)

2. في جزء التنقل، حدد إعداد **جهاز** <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**الإعدادات**</a> > .

3. في حقل **أسلوب النشر** ، حدد **البرنامج النصي المحلي**.

4. انقر فوق **"تنزيل الحزمة** " واحفظ ملف .zip.
  
5. استخراج محتويات حزمة التكوين إلى موقع على الجهاز الذي تريد إلحاقه (على سبيل المثال، سطح المكتب). يجب أن يكون لديك ملف يسمى *DeviceOnboardingScript.cmd*.

6. افتح موجه سطر أوامر غير مقيد على الجهاز وقم بتشغيل البرنامج النصي:

7. انتقل إلى **شاشة البدء** واكتب **cmd**.

8. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

    ![قائمة بدء النافذة التي تشير إلى "تشغيل كمسؤول".](../media/dlp-run-as-admin.png)

9. اكتب موقع ملف البرنامج النصي. إذا قمت بنسخ الملف إلى سطح المكتب، فاكتب: *٪userprofile٪\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. اضغط على المفتاح **Enter** أو انقر فوق **"موافق**".

للحصول على معلومات حول كيفية التحقق يدويا من توافق الجهاز وتقارير بيانات المستشعر بشكل صحيح، قم [باستكشاف أخطاء الحماية المتقدمة من التهديدات في Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) وإصلاحها.

## <a name="offboard-devices-using-a-local-script"></a>إيقاف تشغيل الأجهزة باستخدام برنامج نصي محلي

لأسباب تتعلق بالأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم الإلحاق المنتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة الإلحاق، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم وسيتم تضمينها أيضا في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر نهج الإلحاق والإلحاق على نفس الجهاز في نفس الوقت، وإلا فسيؤدي ذلك إلى تضاربات غير متوقعة.

1. احصل على حزمة الإلحاق من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a>.

2. في جزء التنقل، حدد **"إلغاء إلحاق جهاز** <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**الإعدادات**</a> > ".

3. في حقل **أسلوب النشر** ، حدد **البرنامج النصي المحلي**.

4. انقر فوق **"تنزيل الحزمة** " واحفظ ملف .zip.

5. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الأجهزة. يجب أن يكون لديك ملف باسم *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. افتح موجه سطر أوامر غير مقيد على الجهاز وقم بتشغيل البرنامج النصي:

7. انتقل إلى **شاشة البدء** واكتب **cmd**.

8. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

    ![قائمة بدء النافذة التي تشير إلى "تشغيل كمسؤول".](../media/dlp-run-as-admin.png)

9. اكتب موقع ملف البرنامج النصي. إذا قمت بنسخ الملف إلى سطح المكتب، فاكتب: *٪userprofile٪\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. اضغط على المفتاح **Enter** أو انقر فوق **"موافق**".

> [!IMPORTANT]
> يؤدي الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل.

## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز

يمكنك اتباع خطوات التحقق المختلفة في [استكشاف أخطاء الإلحاق وإصلاحها]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) للتحقق من اكتمال البرنامج النصي بنجاح وتشغيل العامل.

يمكن أيضا إجراء المراقبة مباشرة على المدخل، أو باستخدام أدوات النشر المختلفة.

### <a name="monitor-devices-using-the-portal"></a>مراقبة الأجهزة باستخدام المدخل

1. انتقل إلى [مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com).

2. اختر "**أجهزة** **إلحاق** >  جهاز **الإعدادات** > ".

1. انتقل إلى مدخل التوافق في Microsoft Purview، وحدد "**أجهزة** **إلحاق** >  جهاز <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**الإعدادات**</a> > ".

1. تحقق من ظهور الأجهزة.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام نهج المجموعة](device-onboarding-gp.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام Configuration Manager نقطة نهاية Microsoft](device-onboarding-sccm.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام أدوات إدارة الأجهزة المحمولة](device-onboarding-mdm.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md)
- [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [استكشاف أخطاء الحماية المتقدمة من التهديدات في Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
