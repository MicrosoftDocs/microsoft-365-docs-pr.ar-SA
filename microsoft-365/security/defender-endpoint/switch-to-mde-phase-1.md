---
title: التبديل إلى Microsoft Defender لنقطة النهاية - التحضير
description: استعد للتبديل إلى Microsoft Defender لنقطة النهاية. قم بتحديث أجهزتك وتكوين اتصالات الشبكة.
keywords: الترحيل، Microsoft Defender ل Endpoint، أفضل الممارسات
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
ms.date: 11/30/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: d9d122c9d114aa135eb2a82e1168eabec2aeec7b
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63578570"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>التبديل إلى Microsoft Defender لنقطة النهاية - المرحلة 1: التحضير

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![المرحلة 1: التحضير.](images/phase-diagrams/prepare.png)<br/>المرحلة 1: التحضير | [![المرحلة الثانية: إعداد](images/phase-diagrams/setup.png)](switch-to-mde-phase-2.md)<br/>[المرحلة الثانية: إعداد](switch-to-mde-phase-2.md) | [![المرحلة 3: Onboard](images/phase-diagrams/onboard.png)](switch-to-mde-phase-3.md)<br/>[المرحلة 3: Onboard](switch-to-mde-phase-3.md) |
|--|--|--|
|*أنت هنا!*| | |

**مرحبا بك في مرحلة التحضير [للتبديل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)**.

تتضمن مرحلة الترحيل هذه الخطوات التالية:

1. [الحصول على التحديثات ونشرها عبر أجهزة مؤسستك](#get-and-deploy-updates-across-your-organizations-devices)
2. [احصل على Defender لنقطة النهاية](#get-microsoft-defender-for-endpoint).
3. [منح حق الوصول إلى Microsoft 365 Defender الإلكتروني](#grant-access-to-the-microsoft-365-defender-portal).
4. [تكوين إعدادات اتصال](#configure-device-proxy-and-internet-connectivity-settings) الإنترنت ووكيل الجهاز.

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>الحصول على التحديثات ونشرها عبر أجهزة مؤسستك

كأفضل ممارسة، حافظ على أجهزة المؤسسة ونقاط النهاية مواكبا لها. تأكد من تحديث حل الحماية من الفيروسات والحماية من الفيروسات الموجود لديك، ومن أن أنظمة التشغيل والتطبيقات في مؤسستك لديها أيضا التحديثات الأخيرة. يمكن أن يساعد القيام بذلك الآن على منع حدوث المشاكل لاحقا عند الترحيل إلى Defender for Endpoint برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>تأكد من أن الحل الموجود م تاريخ

حافظ على تحديث حل حماية نقطة النهاية الحالي، وتأكد من أن أجهزة مؤسستك لديها آخر تحديثات الأمان.

هل تحتاج إلى مساعدة؟ راجع وثائق موفر الحلول.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>التأكد من أن أجهزة مؤسستك م الحديثة

هل تحتاج إلى مساعدة في تحديث أجهزة مؤسستك؟ راجع الموارد التالية:

<br/><br/>

|نظام التشغيل|المورد|
|---|---|
|بالنسبة لنظام التشغيل|[Microsoft Update](https://www.update.microsoft.com)|
|macOS|[كيفية تحديث البرنامج على جهاز Mac](https://support.apple.com/HT201541)|
|iOS|[تحديث iPhone أو iPad أو iPod touch](https://support.apple.com/HT204204)|
|Android|[التحقق & تحديث إصدار Android](https://support.google.com/android/answer/7680439)|
|Linux|[Linux 101: تحديث النظام](https://www.linux.com/training-tutorials/linux-101-updating-your-system)|

## <a name="get-microsoft-defender-for-endpoint"></a>الحصول على Microsoft Defender لنقطة النهاية

الآن وقد قمت بتحديث أجهزة مؤسستك، الخطوة التالية هي الحصول على Defender for Endpoint وتعيين التراخيص والتأكد من توفير الخدمة.

1. اشتر أو جرب Defender لنقطة النهاية اليوم. [ابدأ تجربة مجانية أو اطلب عرض أسعار](https://aka.ms/mdatp).

2. تحقق من توفير التراخيص بشكل صحيح. [تحقق من حالة الترخيص](production-deployment.md#check-license-state).

3. قم بإعداد مثيل السحابة المخصص ل Defender ل Endpoint. راجع [Defender لإعداد نقطة النهاية: تكوين المستأجر](production-deployment.md#tenant-configuration).

4. إذا كانت نقاط النهاية (مثل الأجهزة) في مؤسستك تستخدم وكيلا للوصول إلى الإنترنت، فا راجع [Defender لإعداد نقطة النهاية: تكوين الشبكة](production-deployment.md#network-configuration).

في هذه المرحلة، أنت جاهز لمنح حق الوصول إلى مسؤولي الأمان و عوامل تشغيل الأمان الذين سيستخدمون Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">الإلكتروني</a>.

> [!NOTE]
> يشار Microsoft 365 Defender في بعض الأحيان بمدخل Defender for Endpoint، ويمكن الوصول إليه في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>. سيعاد مركز حماية Microsoft Defender السابق (https://securitycenter.windows.com) قريبا إلى Microsoft 365 Defender المدخل. لمعرفة المزيد، راجع نظرة [Microsoft 365 Defender المدخل](portal-overview.md).

## <a name="grant-access-to-the-microsoft-365-defender-portal"></a>منح حق الوصول إلى مدخل Microsoft 365 Defender

المدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender هو</a> المكان الذي يمكنك فيه الوصول إلى ميزات وإمكانات Defender لنقطة النهاية وتكوينها. لمعرفة المزيد، راجع نظرة [عامة Microsoft 365 Defender المدخل](use.md).

يمكن منح Microsoft 365 Defender الوصول باستخدام الأذونات الأساسية أو التحكم بالوصول المستند إلى الدور (RBAC). نوصي باستخدام RBAC حتى يكون لديك تحكم أكثر تفردا في الأذونات.

1. خطط للأدوار والأذونات لمسؤولي الأمان و عوامل تشغيل الأمان. راجع [التحكم بالوصول المستند إلى الدور](prepare-deployment.md#role-based-access-control).

2. إعداد RBAC وتكوينه. نوصي باستخدام [Intune](/mem/intune/fundamentals/what-is-intune) لتكوين RBAC، خاصة إذا كانت مؤسستك تستخدم مجموعة من أجهزة Windows 10 و macOS و iOS و Android. راجع [إعداد RBAC باستخدام Intune](/mem/intune/fundamentals/role-based-access-control).

    إذا كانت مؤسستك تتطلب أسلوبا غير Intune، فاختر أحد الخيارات التالية:

    - [إدارة التكوين](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)
    - [إدارة نهج المجموعة المتقدمة](/microsoft-desktop-optimization-pack/agpm)
    - [Windows مركز الإدارة](/windows-server/manage/windows-admin-center/overview)

3. منح حق الوصول إلى Microsoft 365 Defender الإلكتروني. (هل تحتاج إلى مساعدة؟ راجع [إدارة الوصول إلى المدخل باستخدام RBAC](rbac.md).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>تكوين إعدادات اتصال الإنترنت ووكيل الجهاز

لتمكين الاتصال بين أجهزتك و Defender for Endpoint، قم بتكوين إعدادات الوكيل والإنترنت. يتضمن الجدول التالي ارتباطات إلى الموارد التي يمكنك استخدامها لتكوين إعدادات الوكيل والإنترنت لمختلف أنظمة التشغيل والقدرات:

<br/><br/>

|الإمكانات|نظام التشغيل|الموارد|
|---|---|---|
|[الكشف عن نقطة النهاية والاستجابة](overview-endpoint-detection-response.md) لها (الكشف التلقائي والاستجابة على النقط النهائية)|[Windows 10](/windows/release-health/release-information) أو أي وقت لاحق<br/><br/>Windows Server 2022 <br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/>[Windows Server 1803 أو أي وقت لاحق](/windows-server/get-started/whats-new-in-windows-server-1803)|[تكوين إعدادات اتصال الإنترنت ووكيل الجهاز](configure-proxy-internet.md)|
|الكشف التلقائي والاستجابة على النقط النهائية|[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)|[تكوين إعدادات الوكيل والاتصال بالإنترنت](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings)|
|الكشف التلقائي والاستجابة على النقط النهائية|macOS (راجع [متطلبات النظام](microsoft-defender-endpoint-mac.md)|[Defender for Endpoint على macOS: اتصالات الشبكة](microsoft-defender-endpoint-mac.md#network-connections)|
|[برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)|[Windows 10](/windows/release-health/release-information) <br/><br/> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/> Windows Server 2022 <br/><br/> [Windows Server 1803 أو أي وقت لاحق](/windows-server/get-started/whats-new-in-windows-server-1803) <br/><br/> [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)|[تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها](configure-network-connections-microsoft-defender-antivirus.md)|
|برنامج الحماية من الفيروسات|macOS (راجع [متطلبات النظام](microsoft-defender-endpoint-mac.md)|[Defender for Endpoint على macOS: اتصالات الشبكة](microsoft-defender-endpoint-mac.md#network-connections)|
|برنامج الحماية من الفيروسات|Linux (راجع [متطلبات النظام](microsoft-defender-endpoint-linux.md#system-requirements))|[Defender for Endpoint على Linux: اتصالات الشبكة](microsoft-defender-endpoint-linux.md#network-connections)|


## <a name="next-step"></a>الخطوة التالية

**تهانينا**! لقد أكملت مرحلة **الإعداد** [للتبديل إلى Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [تابع لإعداد Defender لنقطة النهاية](switch-to-mde-phase-2.md).
