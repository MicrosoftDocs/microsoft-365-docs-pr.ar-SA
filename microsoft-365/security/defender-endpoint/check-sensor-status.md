---
title: تحقق من حالة صحة المستشعر في Microsoft Defender لنقطة النهاية
description: تحقق من حماية المستشعر على الأجهزة لتحديد الأجهزة التي تم تكوينها بشكل غير جيد أو غير نشط أو لا تقوم بالإبلاغ عن بيانات المستشعر.
keywords: المستشعر، حماية المستشعر، تكوين خاطئ، غير نشط، عدم وجود بيانات استشعار، بيانات المستشعر، ضعف الاتصالات، الاتصال
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
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: bba5fde870b2916501f4154c6ff628a0d2e3ff1f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465439"
---
# <a name="check-sensor-health-state-at-microsoft-defender-for-endpoint"></a>تحقق من حالة صحة المستشعر في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-checksensor-abovefoldlink)

يتم **العثور على لوحة الأجهزة التي** بها مشاكل المستشعر على لوحة معلومات عمليات الأمان. توفر هذه اللوحة معلومات حول قدرة الجهاز الفردي على توفير بيانات المستشعر والتواصل مع خدمة Defender for Endpoint. كما أنها تقوم بلتقارير حول عدد الأجهزة التي تتطلب الانتباه وتساعدك على تحديد الأجهزة التي بها مشاكل واتخاذ الإجراءات اللازمة لتصحيح المشاكل المعروفة.

يوجد مؤشرا حالة على اللوحة يوفران معلومات حول عدد الأجهزة التي لا يتم إبلاغ الخدمة عنها بشكل صحيح:

- **تكوين غير** صحيح - قد تقوم هذه الأجهزة بشكل جزئي بالإبلاغ عن بيانات المستشعر إلى خدمة Defender for Endpoint وقد تكون بها أخطاء تكوين يجب تصحيحها.
- **غير نشط** - الأجهزة التي توقفت عن الإبلاغ عن خدمة Defender for Endpoint لأكثر من سبعة أيام في الشهر الماضي.

يؤدي النقر فوق أي من المجموعات إلى توجيهك **إلى قائمة** الأجهزة، التي تمت تصفيتها وفقا لاختيارك.

:::image type="content" source="images/atp-devices-with-sensor-issues-tile.png" alt-text="الأجهزة التي بها لوحة مشاكل المستشعر" lightbox="images/atp-devices-with-sensor-issues-tile.png":::

في **قائمة الأجهزة**، يمكنك تصفية قائمة حالة الصحة حسب الحالة التالية:

- **نشط** - الأجهزة التي تقدم تقارير نشطة إلى خدمة Defender for Endpoint.
- **تكوين غير** صحيح - قد تقوم هذه الأجهزة بشكل جزئي بالإبلاغ عن بيانات المستشعر إلى خدمة Defender for Endpoint ولكن بها أخطاء تكوين يجب تصحيحها. يمكن أن يكون للأجهزة التي تم تكوينها بشكل خاطئ مشكلة واحدة أو مجموعة من المشاكل التالية:
  - **لا توجد بيانات استشعار** - توقفت الأجهزة عن إرسال بيانات المستشعر. يمكن تشغيل تنبيهات محدودة من الجهاز.
  - **ضعف الاتصالات** - ضعف القدرة على التواصل مع الجهاز. قد لا يعمل إرسال الملفات للتحليل العميق وحظر الملفات وعزل الجهاز عن الشبكة والإجراءات الأخرى التي تتطلب الاتصال بهذا الجهاز.
- **غير نشط** - الأجهزة التي توقفت عن إعداد التقارير إلى خدمة Defender for Endpoint.

يمكنك أيضا تنزيل القائمة بأكملها بتنسيق CSV باستخدام **ميزة** التصدير. لمزيد من المعلومات حول عوامل التصفية، راجع [عرض قائمة الأجهزة وتنظيمها](machines-view-overview.md).

> [!NOTE]
> تصدير القائمة بتنسيق CSV لعرض البيانات غير الناسخة. سيتضمن ملف CSV كل الأجهزة في المؤسسة، بغض النظر عن أي تصفية مطبقة في طريقة العرض نفسها وقد يستغرق تنزيله وقتا طويلا، استنادا إلى حجم مؤسستك.

:::image type="content" source="images/atp-devices-list-page.png" alt-text="علامة التبويب &quot;تصدير&quot; في صفحة قائمة الأجهزة" lightbox="images/atp-devices-list-page.png":::

يمكنك عرض تفاصيل الجهاز عند النقر فوق جهاز غير تكوين أو غير نشط.

## <a name="see-also"></a>راجع أيضًا

- [إصلاح أدوات الاستشعار غير الصحية في Defender for Endpoint](fix-unhealthy-sensors.md)
- [نظرة عامة حول محلل العميل](overview-client-analyzer.md)
- [تنزيل محلل العميل وتشغيله](download-client-analyzer.md)
- [تشغيل محلل العميل على Windows](run-analyzer-windows.md)
- [تشغيل محلل العميل على macOS أو Linux](run-analyzer-macos-linux.md)
- [تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows](data-collection-analyzer.md)
