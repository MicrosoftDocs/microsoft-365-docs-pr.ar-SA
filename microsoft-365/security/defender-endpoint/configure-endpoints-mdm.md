---
title: أجهزة Windows الأجهزة باستخدام أدوات إدارة أجهزة المحمول
description: استخدم أدوات إدارة أجهزة المحمول لنشر حزمة التكوين على الأجهزة بحيث يتم تهيئة هذه الحزمة في خدمة Defender for Endpoint.
keywords: الأجهزة المجهزة باستخدام mdm، وإدارة الأجهزة، و Microsoft Defender للأجهزة التي تعمل بنقطة النهاية، وmdm
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
ms.openlocfilehash: c190795bd2136cf7cf7317093e3f0308bda43fef
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63571519"
---
# <a name="onboard-windows-devices-using-mobile-device-management-tools"></a>أجهزة Windows الأجهزة باستخدام أدوات إدارة أجهزة المحمول

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

يمكنك استخدام حلول إدارة أجهزة المحمول (MDM) لتكوين Windows 10 المحمول. يدعم Defender for Endpoint MDMs من خلال توفير OMA-URIs لإنشاء سياسات لإدارة الأجهزة.


لمزيد من المعلومات حول استخدام Defender ل Endpoint CSP، راجع [ملف WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) و [WindowsAdvancedThreatProtection DDF](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>قبل البدء

إذا كنت تستخدم Microsoft Intune، فيجب أن يكون الجهاز MDM مسجلا. وإلا، فلن يتم تطبيق الإعدادات بنجاح.

لمزيد من المعلومات حول تمكين MDM باستخدام Microsoft Intune، راجع [تسجيل الجهاز (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>الأجهزة المجهزة باستخدام Microsoft Intune

اطلع على [ملف PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [أو Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) لرؤية المسارات المختلفة في نشر Defender لنقطة النهاية.

اتبع الإرشادات الواردة [من Intune](/intune/advanced-threat-protection).

لمزيد من المعلومات حول استخدام Defender ل Endpoint CSP، راجع [ملف WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) و [WindowsAdvancedThreatProtection DDF](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - يستخدم **نهج حالة الصحة** للأجهزة المجهزة خصائص للقراءة فقط ولا يمكن إصلاحها.
> - يتوفر تكوين تكرار الإبلاغ عن البيانات التشخيصية فقط للأجهزة التي تعمل على Windows 10، الإصدار 1703.


اطلع على [ملف PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [أو Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) لرؤية المسارات المختلفة في نشر Microsoft Defender لنقطة النهاية.

## <a name="run-a-detection-test-to-verify-onboarding"></a>تشغيل اختبار الكشف للتحقق من ال
بعد تشغيل الجهاز، يمكنك أن تختار تشغيل اختبار الكشف للتحقق من أن الجهاز مواد بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender ل Endpoint](run-detection-test.md) تم تشغيله حديثا.


## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>إيقاف تشغيل الأجهزة ومراقبتها باستخدام أدوات إدارة أجهزة المحمول

لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

1. احصل على حزمة إيقاف التشغيل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">من مدخل Microsoft 365 Defender:</a>

   1. في جزء التنقل **، حدد الإعدادات** \> **إيقاف** \>  \> تشغيل إدارة أجهزة **نقاط النهاية**.

   1. حدد Windows 10 أو Windows 11 نظام التشغيل.

   1. في الحقل **أسلوب النشر**، حدد **إدارة أجهزة المحمول / Microsoft Intune**.

   1. انقر **فوق تنزيل الحزمة**، واحفظ .zip الملف.

2. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل مسؤولي الشبكة الذين سينشرون الحزمة. يجب أن يكون لديك ملف *يسمى WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding*.

3. استخدم Microsoft Intune التكوين المخصص لنشر إعدادات OMA-URI المدعومة التالية.
   - OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - نوع التاريخ: سلسلة
   - القيمة: [نسخ القيمة ولصقها من محتوى ملف WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding]

لمزيد من المعلومات حول إعدادات Microsoft Intune، راجع Windows 10 [النهج في](/mem/intune/configuration/custom-settings-windows-10) Microsoft Intune.

> [!NOTE]
> يستخدم **نهج حالة الصحة** للأجهزة غير المجهزة خصائص للقراءة فقط ولا يمكن إصلاحها.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows باستخدام "نهج المجموعة"](configure-endpoints-gp.md)
- [أجهزة Windows التي تستخدم Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [أجهزة Windows باستخدام برنامج نصي محلي](configure-endpoints-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)
- [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية الذي تم تشغيله حديثا](run-detection-test.md)
- [استكشاف مشاكل تشغيل نقطة النهاية وإصلاحها في Microsoft Defender](troubleshoot-onboarding.md)
