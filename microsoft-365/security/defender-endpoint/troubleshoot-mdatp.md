---
title: استكشاف مشاكل خدمة Microsoft Defender لنقطة النهاية وإصلاحها
description: يمكنك العثور على الحلول والحلول البديل للحلول المعروفة مثل أخطاء الخادم عند محاولة الوصول إلى الخدمة.
keywords: استكشاف أخطاء Microsoft Defender لنقطة النهاية وإصلاحها، خطأ الخادم، رفض الوصول، بيانات الاعتماد غير الصالحة، عدم وجود بيانات، مدخل لوحة المعلومات، السماح، عارض الأحداث
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
ms.openlocfilehash: e9a0fdb1bd10d734da95ba88c459ec665635f40e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63571489"
---
# <a name="troubleshoot-service-issues"></a>استكشاف مشاكل الخدمة وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

يتناول هذا القسم المشاكل التي قد تنشأ عند استخدام خدمة Microsoft Defender لنقطة النهاية.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>خطأ الخادم - تم رفض Access بسبب بيانات الاعتماد غير الصالحة

إذا واجهت خطأ في الخادم عند محاولة الوصول إلى الخدمة، ستحتاج إلى تغيير إعدادات ملفات تعريف الارتباط في المستعرض.
قم بتكوين المستعرض للسماح لملفات تعريف الارتباط.

## <a name="elements-or-data-missing-on-the-portal"></a>العناصر أو البيانات المفقودة على المدخل

إذا كانت بعض العناصر أو البيانات مفقودة على Microsoft 365 Defender فمن المحتمل أن تكون إعدادات الوكيل قد حظرتها.

تأكد من تضمين `*.security.microsoft.com` قائمة السماح للوكيل.

> [!NOTE]
> يجب استخدام بروتوكول HTTPS عند إضافة نقاط النهاية التالية.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>يعرض Microsoft Defender لخدمة Endpoint سجلات الأحداث أو الأخطاء في "عارض الأحداث"

راجع [مراجعة الأحداث والأخطاء باستخدام "](event-error-codes.md) عارض الأحداث" للحصول على قائمة بمحددات الأحداث التي يتم اعراضها بواسطة خدمة Microsoft Defender لنقطة النهاية. تحتوي المقالة أيضا على خطوات استكشاف الأخطاء وإصلاحها لأخطاء الأحداث.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>فشل بدء تشغيل خدمة Microsoft Defender لنقطة النهاية بعد إعادة التشغيل ويظهر الخطأ 577

إذا اكتملت أجهزة التكوين بنجاح ولكن لم يبدأ تشغيل Microsoft Defender ل Endpoint بعد إعادة التشغيل ويظهر الخطأ 577، فتحقق من أن Windows Defender غير معطل بواسطة نهج.

لمزيد من المعلومات، راجع [التأكد من عدم](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) برنامج الحماية من الفيروسات من Microsoft Defender النهج.

## <a name="known-issues-with-regional-formats"></a>المشاكل المعروفة في التنسيقات الإقليمية

### <a name="date-and-time-formats"></a>تنسيقات التاريخ والوقت

هناك بعض المشاكل المعروفة في تنسيقات التاريخ والوقت.

تنسيقات التاريخ التالية معتمدة:

- MM/dd/yyyy
- dd/MM/yyyy

تنسيقات التاريخ والوقت التالية غير معتمدة حاليا:

- تنسيق التاريخ yyyy/MM/dd
- تنسيق التاريخ dd/MM/yy
- تنسيق التاريخ باستخدام yy. سيتم عرض yyyy فقط.
- تنسيق الوقت HH:mm:ss غير معتمد (تنسيق 12 ساعة ص/م غير معتمد). يتم دعم تنسيق 24 ساعة فقط.

### <a name="use-of-comma-to-indicate-thousand"></a>استخدام الفاصلة للإشارة إلى ألف

دعم استخدام الفاصلة كفواصل في الأرقام غير معتمد. أما المناطق حيث يتم فصل رقم ب فاصلة للإشارة إلى الألف، فترى فقط استخدام نقطة كفواصل. على سبيل المثال، يتم عرض 15,5K ك 15,5K.

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>تم إنشاء مستأجر Microsoft Defender لنقطة النهاية تلقائيا في أوروبا

عند استخدام Microsoft Defender for Cloud لمراقبة الخوادم، يتم تلقائيا إنشاء مستأجر Microsoft Defender لنقطة النهاية. يتم تخزين بيانات Microsoft Defender لنقطة النهاية في أوروبا بشكل افتراضي.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [استكشاف مشاكل تشغيل نقطة النهاية وإصلاحها في Microsoft Defender](troubleshoot-onboarding.md)
- [مراجعة الأحداث والأخطاء باستخدام "عارض الأحداث"](event-error-codes.md)
