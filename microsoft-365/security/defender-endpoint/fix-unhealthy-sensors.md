---
title: إصلاح أدوات الاستشعار غير الصحية في Microsoft Defender لنقطة النهاية
description: يمكنك إصلاح أدوات استشعار الجهاز التي تقوم بالإبلاغ عن خطأ في تكوينها أو عدم تنشيطها بحيث تتلقى الخدمة البيانات من الجهاز.
keywords: تكوين غير نشط، غير نشط، مستشعر الإصلاح، حماية المستشعر، عدم وجود بيانات المستشعر، بيانات المستشعر، ضعف الاتصالات، الاتصال
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
ms.topic: article
ms.date: 11/23/2020
ms.technology: mde
ms.openlocfilehash: e801776001b79bf1ae3e6e8a220c5e4c395896db
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63569916"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>إصلاح أدوات الاستشعار غير الصحية في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

يمكن تصنيف الأجهزة على أنها غير مصنفة بشكل خاطئ أو غير نشطة وقد تم وضع علامة عليها بسبب أسباب مختلفة. يوفر هذا القسم بعض التوضيحات حول ما قد يتسبب في تصنيف الجهاز على أنه غير نشط أو غير تكوين خاطئ.

## <a name="inactive-devices"></a>الأجهزة غير النشطة

لا يتم وضع علامة بالضرورة على الجهاز غير نشط بسبب مشكلة. يمكن أن تتسبب الإجراءات التالية التي تم اتخاذها على جهاز في تصنيف الجهاز على أنه غير نشط:

### <a name="device-is-not-in-use"></a>الجهاز غير المستخدم

سيحتفظ أي جهاز لا يستخدم لأكثر من سبعة أيام حالة "غير نشط" في المدخل.

### <a name="device-was-reinstalled-or-renamed"></a>تمت إعادة تثبيت الجهاز أو إعادة تسميته
يتم إنشاء كيان جهاز جديد في Microsoft 365 Defender الأجهزة المعاد تثبيتها أو إعادة تسميتها. يبقى كيان الجهاز السابق، مع حالة "غير نشط" في المدخل. إذا قمت بإعادة تثبيت جهاز ونشر حزمة Defender for Endpoint، فابحث عن اسم الجهاز الجديد للتحقق من أن الجهاز يتم إعداد التقارير له بشكل طبيعي.

### <a name="device-was-offboarded"></a>تم إيقاف تشغيل الجهاز
إذا تم إيقاف تشغيل الجهاز، سيبقى يظهر في قائمة الأجهزة. بعد سبعة أيام، يجب أن تتغير حالة حالة الجهاز إلى غير نشطة.

### <a name="device-is-not-sending-signals"></a>الجهاز لا يرسل الإشارات
إذا لم يرسل الجهاز أي إشارات إلى أي قناة من قنوات نقطة النهاية ل Microsoft Defender لأكثر من سبعة أيام لأي سبب من الأسباب، يمكن اعتبار الجهاز غير نشط؛ يشمل ذلك الشروط التي تندرج ضمن تصنيف الأجهزة التي تم تكوينها بشكل غير جيد.

هل تتوقع أن يكون الجهاز في حالة "نشط"؟ [افتح تذكرة دعم](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>الأجهزة التي تم تكوينها بشكل خاطئ
يمكن تصنيف الأجهزة التي تم تكوينها بشكل خاطئ بشكل أكبر إلى:
- الاتصالات المكفوفين
- لا توجد بيانات استشعار

### <a name="impaired-communications"></a>الاتصالات المكفوفين
تشير هذه الحالة إلى وجود اتصال محدود بين الجهاز والخدمة.

يمكن أن تساعد الإجراءات المقترحة التالية في إصلاح المشاكل المتعلقة بجهاز تم تكوينه بشكل خاطئ مع ضعف الاتصالات:

- [التأكد من أن الجهاز لديه اتصال بالإنترنت](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  يتطلب مستشعر Microsoft Defender لنقطة النهاية من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات المستشعر والتواصل مع خدمة Microsoft Defender for Endpoint.

- [التحقق من اتصال العميل مع عناوين URL لخدمة Microsoft Defender لنقطة النهاية](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  تحقق من اكتمال تكوين الوكيل بنجاح، ومن إمكانية اكتشاف WinHTTP والتواصل عبر الخادم الوكيل في بيئتك، ومن أن الخادم الوكيل يتيح نقل البيانات إلى عناوين URL لخدمة Microsoft Defender for Endpoint.

إذا اتخذت إجراءات تصحيحية ولا تزال حالة الجهاز غير صحيحة، [فافتح تذكرة دعم](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>لا توجد بيانات استشعار
جهاز تم تكوينه بشكل غير جيد مع الحالة "لا توجد بيانات أداة استشعار" لديه اتصال بالخدمة ولكن يمكنه الإبلاغ عن بيانات استشعار جزئية فقط.

اتبع الإجراءات التالية لتصحيح المشاكل المعروفة المتعلقة بجهاز تم تكوينه بشكل غير صحيح مع الحالة "لا توجد بيانات أداة استشعار":

- [التأكد من أن الجهاز لديه اتصال بالإنترنت](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  يتطلب مستشعر Microsoft Defender لنقطة النهاية من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات المستشعر والتواصل مع خدمة Microsoft Defender for Endpoint.

- [التحقق من اتصال العميل مع عناوين URL لخدمة Microsoft Defender لنقطة النهاية](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  تحقق من اكتمال تكوين الوكيل بنجاح، ومن إمكانية اكتشاف WinHTTP والتواصل عبر الخادم الوكيل في بيئتك، ومن أن الخادم الوكيل يتيح نقل البيانات إلى عناوين URL لخدمة Microsoft Defender for Endpoint.

- [التأكد من تمكين خدمة البيانات التشخيصية](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
إذا لم يتم الإبلاغ عن الأجهزة بشكل صحيح، يجب التحقق من تعيين Windows البيانات التشخيصية إلى بدء التشغيل تلقائيا. تحقق أيضا من Windows تشغيل خدمة البيانات التشخيصية على نقطة النهاية.

- [تأكد من أن برنامج الحماية من الفيروسات من Microsoft Defender غير معطل بواسطة النهج](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
إذا كانت أجهزتك تعمل عميلا لمكافحة البرامج الضارة من جهة خارجية، فإن وكيل Defender for Endpoint يتطلب تمكين برنامج التشغيل برنامج الحماية من الفيروسات من Microsoft Defender التشغيل المبكر لمكافحة البرامج الضارة (ELAM).

إذا اتخذت إجراءات تصحيحية ولا تزال حالة الجهاز غير صحيحة، [فافتح تذكرة دعم](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>راجع أيضًا
- [التحقق من حالة صحة المستشعر في Microsoft Defender لنقطة النهاية](check-sensor-status.md)
- [نظرة عامة حول محلل العميل](overview-client-analyzer.md)
- [تنزيل محلل العميل وتشغيله](download-client-analyzer.md)
- [تشغيل محلل العميل على Windows](run-analyzer-windows.md)
- [تشغيل محلل العميل على macOS أو Linux](run-analyzer-macos-linux.md)
- [تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows](data-collection-analyzer.md)

