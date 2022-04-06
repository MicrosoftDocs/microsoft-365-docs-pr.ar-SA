---
title: استكشاف مشاكل Microsoft Defender لنقطة النهاية الخدمة وإصلاحها
description: ابحث عن حلول وحلول بديلة للمشاكل المعروفة مثل أخطاء الخادم عند محاولة الوصول إلى الخدمة.
keywords: استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية، خطأ الخادم، رفض الوصول، بيانات اعتماد غير صالحة، لا بيانات، مدخل لوحة المعلومات، السماح، عارض الأحداث
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: bcd0f5ba70d154c40972c0b8035d1617a9e71966
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665833"
---
# <a name="troubleshoot-service-issues"></a>استكشاف مشاكل الخدمة وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

يعالج هذا القسم المشاكل التي قد تنشأ عند استخدام خدمة Microsoft Defender لنقطة النهاية.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>خطأ في الخادم - تم رفض الوصول بسبب بيانات اعتماد غير صالحة

إذا واجهت خطأ في الخادم عند محاولة الوصول إلى الخدمة، فستحتاج إلى تغيير إعدادات ملف تعريف الارتباط في المستعرض.
تكوين المستعرض للسماح لملفات تعريف الارتباط.

## <a name="elements-or-data-missing-on-the-portal"></a>العناصر أو البيانات المفقودة على المدخل

إذا كانت بعض العناصر أو البيانات مفقودة على Microsoft 365 Defender فمن المحتمل أن تكون إعدادات الوكيل تحظرها.

تأكد من `*.security.microsoft.com` تضمين قائمة السماح للوكيل.

> [!NOTE]
> يجب استخدام بروتوكول HTTPS عند إضافة نقاط النهاية التالية.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>تعرض خدمة Microsoft Defender لنقطة النهاية سجلات الأحداث أو الأخطاء في عارض الأحداث

راجع [مراجعة الأحداث والأخطاء باستخدام عارض الأحداث](event-error-codes.md) لقائمة معرفات الأحداث التي تم الإبلاغ عنها بواسطة خدمة Microsoft Defender لنقطة النهاية. تحتوي المقالة أيضا على خطوات استكشاف الأخطاء وإصلاحها لأخطاء الحدث.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>تفشل Microsoft Defender لنقطة النهاية الخدمة في البدء بعد إعادة التشغيل وتظهر الخطأ 577

إذا اكتمل إعداد الأجهزة بنجاح ولكن Microsoft Defender لنقطة النهاية لا يبدأ بعد إعادة التشغيل ويظهر الخطأ 577، فتحقق من أن Windows Defender غير معطل بواسطة نهج.

لمزيد من المعلومات، راجع [التأكد من عدم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender بواسطة النهج](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="known-issues-with-regional-formats"></a>المشاكل المعروفة في التنسيقات الإقليمية

### <a name="date-and-time-formats"></a>تنسيقات التاريخ والوقت

هناك بعض المشاكل المعروفة في تنسيقات الوقت والتاريخ.

تنسيقات التاريخ التالية معتمدة:

- MM/dd/yyyyy
- dd/MM/yyyyy

تنسيقات التاريخ والوقت التالية غير معتمدة حاليا:

- تنسيق التاريخ yyyy/MM/dd
- تنسيق التاريخ dd/MM/yy
- تنسيق التاريخ مع yy. سوف تظهر yyyyy فقط.
- تنسيق الوقت HH:mm:ss غير معتمد (تنسيق الساعة 12 ص/م غير معتمد). تنسيق 24 ساعة فقط معتمد.

### <a name="use-of-comma-to-indicate-thousand"></a>استخدام الفاصلة للإشارة إلى الألف

دعم استخدام الفاصلة كفاصل في الأرقام غير معتمد. المناطق التي يتم فيها فصل رقم بفاصلة للإشارة إلى ألف، لن ترى سوى استخدام نقطة كفاصل. على سبيل المثال، يتم عرض 15,5K ك 15.5K.

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>تم إنشاء مستأجر Microsoft Defender لنقطة النهاية تلقائيا في أوروبا

عند استخدام Microsoft Defender for Cloud لمراقبة الخوادم، يتم إنشاء مستأجر Microsoft Defender لنقطة النهاية تلقائيا. يتم تخزين بيانات Microsoft Defender لنقطة النهاية في أوروبا بشكل افتراضي.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [استكشاف أخطاء إلحاق Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-onboarding.md)
- [مراجعة الأحداث والأخطاء باستخدام عارض الأحداث](event-error-codes.md)
