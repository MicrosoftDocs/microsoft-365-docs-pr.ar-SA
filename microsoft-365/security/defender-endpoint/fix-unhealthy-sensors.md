---
title: إصلاح أدوات الاستشعار غير السليمة في Microsoft Defender لنقطة النهاية
description: إصلاح أجهزة استشعار الجهاز التي تقوم بالإبلاغ عن أنها تم تكوينها بشكل خاطئ أو غير نشطة بحيث تتلقى الخدمة البيانات من الجهاز.
keywords: تم تكوينه بشكل خاطئ، وغير نشط، وأداة استشعار الإصلاح، وحماية جهاز الاستشعار، وعدم وجود بيانات أداة الاستشعار، وبيانات الاستشعار، والاتصالات الضعيفة، والاتصالات
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
ms.openlocfilehash: cc88fa877c0c284555f1702a5fa3190a06e7e47e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490852"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>إصلاح أدوات الاستشعار غير السليمة في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

يمكن تصنيف الأجهزة على أنها تم تكوينها بشكل خاطئ أو غير نشطة تم وضع علامة عليها لأسباب مختلفة. يوفر هذا القسم بعض التفسيرات حول ما قد يكون تسبب في تصنيف الجهاز على أنه غير نشط أو تم تكوينه بشكل خاطئ.

## <a name="inactive-devices"></a>الأجهزة غير النشطة

لا يتم بالضرورة وضع علامة على الجهاز غير النشط بسبب مشكلة. يمكن أن تؤدي الإجراءات التالية التي يتم اتخاذها على جهاز إلى تصنيف الجهاز على أنه غير نشط:

- الجهاز غير مستخدم
- تمت إعادة تثبيت الجهاز أو إعادة تسميته
- تم إيقاف تشغيل الجهاز
- لا يرسل الجهاز إشارات


### <a name="device-isnt-in-use"></a>الجهاز غير مستخدم

سيحتفظ أي جهاز غير مستخدم لأكثر من سبعة أيام بحالة "غير نشط" في المدخل.

### <a name="device-was-reinstalled-or-renamed"></a>تمت إعادة تثبيت الجهاز أو إعادة تسميته
يتم إنشاء كيان جهاز جديد في Microsoft 365 Defender للأجهزة المعاد تثبيتها أو إعادة تسميتها. يبقى كيان الجهاز السابق، مع حالة "غير نشط" في المدخل. إذا قمت بإعادة تثبيت جهاز ونشر حزمة Defender لنقطة النهاية، فابحث عن اسم الجهاز الجديد للتحقق من أن الجهاز يقوم بإعداد التقارير بشكل طبيعي.

### <a name="device-was-offboarded"></a>تم إيقاف تشغيل الجهاز
إذا تم إيقاف تشغيل الجهاز، فسيظل يظهر في قائمة الأجهزة. بعد سبعة أيام، يجب أن تتغير حالة صحة الجهاز إلى غير نشطة.

### <a name="device-isnt-sending-signals"></a>لا يرسل الجهاز إشارات
إذا لم يرسل الجهاز أي إشارات إلى أي قنوات Microsoft Defender لنقطة النهاية لأكثر من سبعة أيام لأي سبب من الأسباب، يمكن اعتبار الجهاز غير نشط؛ وهذا يشمل الشروط التي تندرج ضمن تصنيف الأجهزة المكونة بشكل خاطئ.

هل تتوقع أن يكون الجهاز في حالة "نشط"؟ [افتح تذكرة دعم](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>الأجهزة التي تم تكوينها بشكل خاطئ
يمكن تصنيف الأجهزة التي تم تكوينها بشكل خاطئ إلى:
- الاتصالات الضعيفة
- لا توجد بيانات مستشعر

### <a name="impaired-communications"></a>الاتصالات الضعيفة
تشير هذه الحالة إلى وجود اتصال محدود بين الجهاز والخدمة.

يمكن أن تساعد الإجراءات المقترحة التالية في إصلاح المشكلات المتعلقة بجهاز تم تكوينه بشكل خاطئ مع ضعف الاتصالات:

- [تأكد من أن الجهاز لديه اتصال بالإنترنت](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  يتطلب مستشعر Microsoft Defender لنقطة النهاية من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات جهاز الاستشعار والتواصل مع خدمة Microsoft Defender لنقطة النهاية.

- [التحقق من اتصال العميل بعناوين URL للخدمة Microsoft Defender لنقطة النهاية](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  تحقق من اكتمال تكوين الوكيل بنجاح، ومن أن WinHTTP يمكنه اكتشاف خادم الوكيل في بيئتك والاتصال به، وأن الخادم الوكيل يسمح بنسبة استخدام الشبكة إلى عناوين URL للخدمة Microsoft Defender لنقطة النهاية.

إذا اتخذت إجراءات تصحيحية ولم يتم تكوين حالة الجهاز بشكل صحيح، [فافتح تذكرة دعم](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>لا توجد بيانات مستشعر
جهاز تم تكوينه بشكل خاطئ بحالة "لا توجد بيانات أداة استشعار" لديه اتصال بالخدمة ولكن يمكنه الإبلاغ عن بيانات المستشعر الجزئي فقط.

اتبع إجراءات هذه الإجراءات لتصحيح المشكلات المعروفة المتعلقة بجهاز تم تكوينه بشكل خاطئ مع الحالة "لا توجد بيانات مستشعر":

- [تأكد من أن الجهاز لديه اتصال بالإنترنت](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  يتطلب مستشعر Microsoft Defender لنقطة النهاية من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات جهاز الاستشعار والتواصل مع خدمة Microsoft Defender لنقطة النهاية.

- [التحقق من اتصال العميل بعناوين URL للخدمة Microsoft Defender لنقطة النهاية](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  تحقق من اكتمال تكوين الوكيل بنجاح، ومن أن WinHTTP يمكنه اكتشاف خادم الوكيل في بيئتك والاتصال به، وأن الخادم الوكيل يسمح بنسبة استخدام الشبكة إلى عناوين URL للخدمة Microsoft Defender لنقطة النهاية.

- [تأكد من تمكين خدمة البيانات التشخيصية](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
إذا لم تكن الأجهزة تقوم بإعداد التقارير بشكل صحيح، يجب عليك التحقق من تعيين خدمة البيانات التشخيصية ل Windows للبدء تلقائيا. تحقق أيضا من تشغيل خدمة بيانات تشخيص Windows على نقطة النهاية.

- [تأكد من عدم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender بواسطة النهج](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
إذا كانت أجهزتك تقوم بتشغيل عميل مكافحة البرامج الضارة تابع لجهة خارجية، فإن عامل Defender لنقطة النهاية يتطلب تمكين برنامج تشغيل برنامج التشغيل المبكر لبرامج الحماية من الفيروسات (ELAM) من Microsoft Defender.

إذا اتخذت إجراءات تصحيحية ولم يتم تكوين حالة الجهاز بشكل صحيح، [فافتح تذكرة دعم](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>راجع أيضًا
- [التحقق من حالة حماية جهاز الاستشعار في Microsoft Defender لنقطة النهاية](check-sensor-status.md)
- [نظرة عامة حول محلل العميل](overview-client-analyzer.md)
- [تنزيل محلل العميل وتشغيله](download-client-analyzer.md)
- [تشغيل محلل العميل على Windows](run-analyzer-windows.md)
- [تشغيل محلل العميل على macOS أو Linux](run-analyzer-macos-linux.md)
- [تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows](data-collection-analyzer.md)

