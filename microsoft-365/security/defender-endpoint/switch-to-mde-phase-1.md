---
title: التبديل إلى Microsoft Defender لنقطة النهاية - التحضير
description: استعد للتبديل إلى Microsoft Defender لنقطة النهاية. قم بتحديث أجهزتك وتكوين اتصالات الشبكة.
keywords: الترحيل، Microsoft Defender لنقطة النهاية، أفضل الممارسات
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.topic: article
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: c08ab1c96adc2b9d83cc6869573f2f0dbe75ac78
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782908"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>التبديل إلى Microsoft Defender لنقطة النهاية - المرحلة 1: التحضير

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![المرحلة 1: التحضير.](images/phase-diagrams/prepare.png#lightbox)<br/>المرحلة 1: التحضير | [![المرحلة 2: إعداد](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[المرحلة 2: إعداد](switch-to-mde-phase-2.md) | [![المرحلة 3: التجهيز للاستخدام](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[المرحلة 3: التجهيز للاستخدام](switch-to-mde-phase-3.md) |
|--|--|--|
|*أنت هنا!*| | |

**مرحبا بك في مرحلة التحضير [للتبديل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)**.

تتضمن مرحلة الترحيل هذه الخطوات التالية:

1. [الحصول على التحديثات ونشرها عبر أجهزة مؤسستك](#get-and-deploy-updates-across-your-organizations-devices)
2. [الحصول على Defender لنقطة النهاية](#get-microsoft-defender-for-endpoint).
3. [منح حق الوصول إلى مدخل Microsoft 365 Defender](#grant-access-to-the-microsoft-365-defender-portal).
4. [تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت](#configure-device-proxy-and-internet-connectivity-settings).

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>الحصول على التحديثات ونشرها عبر أجهزة مؤسستك

كأفضل ممارسة، حافظ على تحديث أجهزة مؤسستك ونقاط النهاية الخاصة بها. تأكد من أن حل حماية نقطة النهاية والحماية من الفيروسات الحالي محدث، وأن أنظمة التشغيل والتطبيقات الخاصة بمؤسستك لديها أيضا آخر التحديثات. يمكن أن يساعد القيام بذلك الآن في منع حدوث مشاكل في وقت لاحق أثناء الترحيل إلى Defender لنقطة النهاية برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>تأكد من أن الحل الحالي محدث

حافظ على تحديث حل حماية نقطة النهاية الحالي، وتأكد من أن أجهزة مؤسستك تحتوي على آخر تحديثات الأمان.

هل تحتاج إلى مساعدة؟ راجع وثائق موفر الحلول.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>تأكد من تحديث أجهزة مؤسستك

هل تحتاج إلى مساعدة في تحديث أجهزة مؤسستك؟ راجع الموارد التالية:

|OS|الموارد|
|---|---|
|بالنسبة لنظام التشغيل|[Microsoft Update](https://www.update.microsoft.com)|
|ماك|[كيفية تحديث البرنامج على جهاز Mac](https://support.apple.com/HT201541)|
|دائره الرقابه الداخليه|[تحديث iPhone أو iPad أو iPod touch](https://support.apple.com/HT204204)|
|الروبوت|[تحقق من & تحديث إصدار Android](https://support.google.com/android/answer/7680439)|
|ينكس|[Linux 101: تحديث النظام الخاص بك](https://www.linux.com/training-tutorials/linux-101-updating-your-system)|

## <a name="get-microsoft-defender-for-endpoint"></a>الحصول على Microsoft Defender لنقطة النهاية

الآن بعد أن قمت بتحديث أجهزة مؤسستك، فإن الخطوة التالية هي الحصول على Defender لنقطة النهاية، وتعيين التراخيص، والتأكد من توفير الخدمة.

1. شراء Defender لنقطة النهاية أو تجربته اليوم. [ابدأ إصدارا تجريبيا مجانيا أو اطلب اقتباسا](https://aka.ms/mdatp).

2. تحقق من توفير تراخيصك بشكل صحيح. [تحقق من حالة الترخيص](production-deployment.md#check-license-state).

3. إعداد مثيل السحابة المخصص ل Defender لنقطة النهاية. راجع [إعداد Defender لنقطة النهاية: تكوين المستأجر](production-deployment.md#tenant-configuration).

4. إذا كانت نقاط النهاية (مثل الأجهزة) في مؤسستك تستخدم وكيلا للوصول إلى الإنترنت، فراجع [إعداد Defender لنقطة النهاية: تكوين الشبكة](production-deployment.md#network-configuration).

في هذه المرحلة، أنت مستعد لمنح حق الوصول إلى مسؤولي الأمان ومشغلي الأمان الذين سيستخدمون <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>.

> [!NOTE]
> يشار أحيانا إلى مدخل Microsoft 365 Defender باسم مدخل Defender لنقطة النهاية، ويمكن الوصول إليه في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>. مركز حماية Microsoft Defender السابقة (https://securitycenter.windows.com)ستتم إعادة توجيهها قريبا إلى مدخل Microsoft 365 Defender. لمعرفة المزيد، راجع [نظرة عامة على مدخل Microsoft 365 Defender](portal-overview.md).

## <a name="grant-access-to-the-microsoft-365-defender-portal"></a>منح حق الوصول إلى مدخل Microsoft 365 Defender

مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> هو المكان الذي يمكنك فيه الوصول إلى ميزات وإمكانات Defender لنقطة النهاية وتكوينها. لمعرفة المزيد، راجع [نظرة عامة على مدخل Microsoft 365 Defender](use.md).

يمكن منح الأذونات إلى مدخل Microsoft 365 Defender باستخدام إما الأذونات الأساسية أو التحكم في الوصول استنادا إلى الدور (RBAC). نوصي باستخدام RBAC بحيث يكون لديك تحكم أكثر دقة في الأذونات.

1. تخطيط الأدوار والأذونات لمسؤولي الأمان ومشغلي الأمان. راجع [التحكم في الوصول المستند إلى الدور](prepare-deployment.md#role-based-access-control).

2. إعداد وتكوين RBAC. نوصي باستخدام [Intune](/mem/intune/fundamentals/what-is-intune) لتكوين RBAC، خاصة إذا كانت مؤسستك تستخدم مجموعة من أجهزة Windows 10 وmacOS وiOS وAndroid. راجع [إعداد RBAC باستخدام Intune](/mem/intune/fundamentals/role-based-access-control).

    إذا كانت مؤسستك تتطلب أسلوبا آخر غير Intune، فاختر أحد الخيارات التالية:

    - [إدارة التكوين](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)

    - [إدارة نهج المجموعة المتقدمة](/microsoft-desktop-optimization-pack/agpm)
    
    - [مركز إدارة Windows](/windows-server/manage/windows-admin-center/overview)

3. منح حق الوصول إلى مدخل Microsoft 365 Defender. (هل تحتاج إلى مساعدة؟ راجع [إدارة الوصول إلى المدخل باستخدام RBAC](rbac.md).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت

لتمكين الاتصال بين أجهزتك و Defender لنقطة النهاية، قم بتكوين إعدادات الوكيل والإنترنت. يتضمن الجدول التالي ارتباطات إلى الموارد التي يمكنك استخدامها لتكوين إعدادات الوكيل والإنترنت لأنظمة التشغيل والقدرات المختلفة:

|قدرات|نظام التشغيل|الموارد|
|---|---|---|
|[الكشف عن نقطة النهاية والاستجابة](overview-endpoint-detection-response.md) لها (الكشف التلقائي والاستجابة على النقط النهائية)|[Windows 10](/windows/release-health/release-information) أو أحدث<br/><br/>Windows Server 2022 <br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/>[Windows Server 1803 أو إصدار أحدث](/windows-server/get-started/whats-new-in-windows-server-1803)<br/><br/>[Windows Server 2016*](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت](configure-proxy-internet.md)|
|الكشف التلقائي والاستجابة على النقط النهائية [Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)|[تكوين إعدادات الاتصال بالإنترنت والوكيل](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings)|
|الكشف التلقائي والاستجابة على النقط النهائية|macOS (راجع [متطلبات النظام](microsoft-defender-endpoint-mac.md)|[Defender لنقطة النهاية على macOS: اتصالات الشبكة](microsoft-defender-endpoint-mac.md#network-connections)|
|[برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)|[Windows 10](/windows/release-health/release-information) <br/><br/> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/> Windows Server 2022 <br/><br/> [Windows Server 1803 أو إصدار أحدث](/windows-server/get-started/whats-new-in-windows-server-1803) <br/><br/> [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها](configure-network-connections-microsoft-defender-antivirus.md)|
|مكافحه الفيروسات|macOS (راجع [متطلبات النظام](microsoft-defender-endpoint-mac.md)|[Defender لنقطة النهاية على macOS: اتصالات الشبكة](microsoft-defender-endpoint-mac.md#network-connections)|
|مكافحه الفيروسات|Linux (راجع [متطلبات النظام](microsoft-defender-endpoint-linux.md#system-requirements))|[Defender لنقطة النهاية على Linux: اتصالات الشبكة](microsoft-defender-endpoint-linux.md#network-connections)|

*يتطلب تثبيت الحل الحديث الموحد لخادم Windows 2012 R2 و2016. لمزيد من المعلومات، راجع [إلحاق خوادم Windows بخدمة Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

## <a name="next-step"></a>الخطوة التالية

**تهانينا**! لقد أكملت مرحلة **التحضير** [للتبديل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)!

- [تابع لإعداد Defender لنقطة النهاية](switch-to-mde-phase-2.md).
