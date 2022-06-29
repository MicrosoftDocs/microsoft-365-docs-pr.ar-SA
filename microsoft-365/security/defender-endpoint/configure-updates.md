---
title: إنشاء عملية إطلاق تدريجي مخصصة لتحديثات Microsoft Defender
description: تعرف على كيفية استخدام الأدوات المدعومة لإنشاء عملية إطلاق تدريجي مخصصة للتحديثات
keywords: أدوات التحديث، gpo، intune، mdm، إدارة نقاط النهاية من Microsoft، النهج، powershell
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 491d51b30b45fb99cba9924f947c9566305c2fbc
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490952"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>إنشاء عملية إطلاق تدريجي مخصصة لتحديثات Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

> [!NOTE]
> تتطلب هذه الوظيفة إصدار برنامج الحماية من الفيروسات من Microsoft Defender 4.18.2106.X أو أحدث.

لإنشاء عملية الإطلاق التدريجي المخصصة لتحديثات Defender، يمكنك استخدام نهج المجموعة وMicrosoft إدارة نقاط النهاية وPowerShell.

يسرد الجدول التالي إعدادات نهج المجموعة المتوفرة لتكوين قنوات التحديث:

<br>

****

|تعيين عنوان|الوصف|موقع|
|---|---|---|
|تحديد التحديث التدريجي لتحديث النظام الأساسي الشهري ل Microsoft Defender|قم بتمكين هذا النهج لتحديد وقت تلقي الأجهزة لتحديثات النظام الأساسي ل Microsoft Defender أثناء الإطلاق التدريجي الشهري. <p> خيار التحديث بيتا: ستكون الأجهزة التي تم تعيينها إلى هذه القناة هي الأولى التي تتلقى تحديثات جديدة. حدد خيار التحديث بيتا للمشاركة في تحديد المشاكل وإرسالها إلى Microsoft. يتم الاشتراك في الأجهزة الموجودة في برنامج Windows Insider في هذه القناة بشكل افتراضي. للاستخدام في بيئات الاختبار (اليدوية) فقط وعدد محدود من الأجهزة. <p> خيار التحديث الحالي (معاينة): سيتم تقديم التحديثات للأجهزة التي تم تعيينها إلى هذه القناة في أقرب وقت خلال دورة الإصدار التدريجي الشهرية. مقترح لبيئات ما قبل الإنتاج/التحقق من الصحة. <p> خيار التحديث الحالي (مرحلي): سيتم عرض التحديثات على الأجهزة بعد دورة الإصدار التدريجي الشهرية. مقترح للتطبيق على جزء تمثيلي صغير من محتوى الإنتاج الخاص بك (~10٪). <p> خيار التحديث الحالي (واسع النطاق): لن يتم عرض التحديثات على الأجهزة إلا بعد اكتمال دورة الإصدار التدريجي. مقترح للتطبيق على مجموعة واسعة من الأجهزة في محتوى الإنتاج الخاص بك (~10-100٪). <p> هام - تأخير الوقت: سيتم تقديم تحديثات للأجهزة مع تأخير لمدة 48 ساعة. مقترح للبيئات الحرجة فقط. <p>إذا قمت بتعطيل هذا النهج أو لم تقم بتكوينه، فسيظل الجهاز محدثا تلقائيا أثناء دورة الإصدار التدريجي. مناسب لمعظم الأجهزة.|Windows Components\Microsoft Defender Antivirus|
|تحديد التحديث التدريجي لتحديث المحرك الشهري ل Microsoft Defender|قم بتمكين هذا النهج لتحديد وقت تلقي الأجهزة لتحديثات مشغل Microsoft Defender أثناء الإطلاق التدريجي الشهري. <p> خيار التحديث بيتا: ستكون الأجهزة التي تم تعيينها إلى هذه القناة هي الأولى التي تتلقى تحديثات جديدة. حدد خيار التحديث بيتا للمشاركة في تحديد المشاكل وإرسالها إلى Microsoft. يتم الاشتراك في الأجهزة الموجودة في برنامج Windows Insider في هذه القناة بشكل افتراضي. للاستخدام في بيئات الاختبار (اليدوية) فقط وعدد محدود من الأجهزة. <p> خيار التحديث الحالي (معاينة): سيتم تقديم التحديثات للأجهزة التي تم تعيينها إلى هذه القناة في أقرب وقت خلال دورة الإصدار التدريجي الشهرية. مقترح لبيئات ما قبل الإنتاج/التحقق من الصحة. <p> خيار التحديث الحالي (مرحلي): سيتم عرض التحديثات على الأجهزة بعد دورة الإصدار التدريجي الشهرية. مقترح للتطبيق على جزء تمثيلي صغير من محتوى الإنتاج الخاص بك (~10٪). <p> خيار التحديث الحالي (واسع النطاق): لن يتم عرض التحديثات على الأجهزة إلا بعد اكتمال دورة الإصدار التدريجي. مقترح للتطبيق على مجموعة واسعة من الأجهزة في محتوى الإنتاج الخاص بك (~10-100٪). <p> هام - تأخير الوقت: سيتم تقديم تحديثات للأجهزة مع تأخير لمدة 48 ساعة. مقترح للبيئات الحرجة فقط.<p> إذا قمت بتعطيل هذا النهج أو لم تقم بتكوينه، فسيظل الجهاز محدثا تلقائيا أثناء دورة الإصدار التدريجي. مناسب لمعظم الأجهزة.|Windows Components\Microsoft Defender Antivirus|
|تحديد التحديثات التدريجية لذكاء الأمان اليومي ل Microsoft Defender|تمكين هذا النهج لتحديد متى تتلقى الأجهزة تحديثات التحليل الذكي للأمان ل Microsoft Defender أثناء الإطلاق التدريجي اليومي. <p> خيار التحديث الحالي (مرحلي): سيتم عرض التحديثات على الأجهزة بعد دورة الإصدار. مقترح للتطبيق على جزء تمثيلي صغير من محتوى الإنتاج (~10٪). <p> خيار التحديث الحالي (واسع النطاق): لن يتم عرض التحديثات على الأجهزة إلا بعد اكتمال دورة الإصدار التدريجي. مقترح للتطبيق على مجموعة واسعة من الأجهزة في محتوى الإنتاج الخاص بك (~10-100٪). <p>  إذا قمت بتعطيل هذا النهج أو لم تقم بتكوينه، فسيظل الجهاز محدثا تلقائيا أثناء دورة الإصدار اليومية. مناسب لمعظم الأجهزة.|Windows Components\Microsoft Defender Antivirus|
|تعطيل الإطلاق التدريجي لتحديثات Microsoft Defender|تمكين هذا النهج لتعطيل الإطلاق التدريجي لتحديثات Defender. <p> خيار التحديث الحالي (واسع): سيتم تقديم التحديثات الأخيرة للأجهزة المعينة إلى هذه القناة خلال دورة الإصدار التدريجي. الأفضل لأجهزة مراكز البيانات التي تتلقى تحديثات محدودة فقط. <p> ملاحظة: ينطبق هذا الإعداد على كل من تحديثات Defender الشهرية وتحديثات Defender اليومية وسيتجاوز أي تحديدات قناة تم تكوينها مسبقا لتحديثات النظام الأساسي والمحرك. <p> إذا قمت بتعطيل هذا النهج أو لم تقم بتكوينه، فسيظل الجهاز في خيار التحديث الحالي (الافتراضي) ما لم يتم تحديد خلاف ذلك في قنوات معينة لتحديثات النظام الأساسي والمحرك. ابق على اطلاع تلقائيا خلال دورة الإصدار التدريجي. مناسب لمعظم الأجهزة.|Windows Components\Microsoft Defender Antivirus|
|

## <a name="group-policy"></a>نهج المجموعة

> [!NOTE]
> سيتم نشر قالب Defender ADMX محدث مع إصدار 21H2 من Windows 10. يتوفر إصدار غير مترجم للتنزيل في https://github.com/microsoft/defender-updatecontrols.

يمكنك استخدام [نهج المجموعة](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارته على نقاط النهاية.

بشكل عام، يمكنك استخدام الإجراء التالي لتكوين إعدادات نهج مجموعة الحماية من الفيروسات من Microsoft Defender أو تغييرها:

1. على جهاز إدارة نهج المجموعة، افتح **وحدة تحكم إدارة نهج المجموعة**، وانقر بزر الماوس الأيمن فوق **الكائن نهج المجموعة** (GPO) الذي تريد تكوينه وانقر فوق **"تحرير**".

2. باستخدام محرر إدارة نهج المجموعة انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender**.

5. قم بتوسيع المقطع (يشار إليه باسم **الموقع** في الجدول في هذا الموضوع) الذي يحتوي على الإعداد الذي تريد تكوينه، وانقر نقرا مزدوجا فوق الإعداد لفتحه، وأدخل تغييرات على التكوين.

6. [نشر عنصر نهج المجموعة المحدث كما تفعل عادة](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx).

## <a name="intune"></a>Intune

اتبع الإرشادات الواردة أدناه لإنشاء نهج مخصص في Intune:

[إضافة إعدادات مخصصة للأجهزة Windows 10 في Microsoft Intune - Azure \|Microsoft Docs](/mem/intune/configuration/custom-settings-windows-10)

لمزيد من المعلومات حول Defender CSP المستخدم لعملية الإطلاق التدريجي، راجع [Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

`Set-MpPreference` استخدم cmdlet لتكوين طرح التحديثات التدريجية.

استخدم المعلمات التالية:

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-DisableGradualRelease 1|0
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

على سبيل المثال:

يستخدم `Set-MpPreference -PlatformUpdatesChannel Beta` لتكوين تحديثات النظام الأساسي للوصول من خيار التحديث بيتا.

لمزيد من المعلومات حول المعلمات وكيفية تكوينها، راجع [Set-MpPreference (Microsoft Defender Antivirus)|Microsoft Docs](/powershell/module/defender/set-mppreference).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)
