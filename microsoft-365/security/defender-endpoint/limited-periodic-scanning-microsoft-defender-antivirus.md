---
title: تمكين ميزة فحص برنامج الحماية من الفيروسات من Microsoft Defender الدوري المحدود
description: يتيح لك الفحص الدوري المحدود استخدام برنامج الحماية من الفيروسات من Microsoft Defender بالإضافة إلى موفري AV المثبتين الآخرين
keywords: lps, limited, periodic, scan, scaning, compatibility, 3rd party, other av, disable
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 2b9320c5d7086d41be363fd01b786c98ffbc52d5
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417897"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>استخدام الفحص الدوري المحدود في برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

الفحص الدوري المحدود هو نوع خاص من الكشف عن التهديدات والمعالجة التي يمكن تمكينها عند تثبيت منتج آخر من مكافحة الفيروسات على جهاز Windows 10 أو Windows 11.

ولا يمكن تمكينه إلا في حالات معينة. لمزيد من المعلومات حول الفحص الدوري المحدود وكيفية عمل برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات مكافحة الفيروسات الأخرى، راجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

**لا توصي Microsoft باستخدام هذه الميزة في بيئات المؤسسة. هذه ميزة مخصصة بشكل أساسي للمستهلكين.** تستخدم هذه الميزة فقط مجموعة فرعية محدودة من قدرات برنامج الحماية من الفيروسات من Microsoft Defender للكشف عن البرامج الضارة، ولن تكون قادرة على الكشف عن معظم البرامج الضارة والبرامج التي يحتمل أن تكون غير مرغوب فيها. كما ستكون قدرات الإدارة وإعداد التقارير محدودة. توصي Microsoft المؤسسات باختيار حل الحماية من الفيروسات الأساسي واستخدامه حصريا.

## <a name="how-to-enable-limited-periodic-scanning"></a>كيفية تمكين الفحص الدوري المحدود

بشكل افتراضي، سيمكن برنامج الحماية من الفيروسات من Microsoft Defender نفسه على جهاز Windows 10 أو جهاز Windows 11 إذا لم يكن هناك منتج آخر لمكافحة الفيروسات مثبت، أو إذا كان المنتج الآخر قديما أو منتهيا الصلاحية أو لا يعمل بشكل صحيح.

إذا تم تمكين برنامج الحماية من الفيروسات من Microsoft Defender، فستظهر الخيارات المعتادة لتكوينه على هذا الجهاز:

:::image type="content" source="images/vtp-wdav.png" alt-text="يعرض تطبيق أمن Windows خيارات Microsoft Defender AV، بما في ذلك خيارات الفحص والإعدادات وخيارات التحديث" lightbox="images/vtp-wdav.png":::

إذا تم تثبيت منتج آخر من برامج الحماية من الفيروسات ويعمل بشكل صحيح، فسيعطل برنامج الحماية من الفيروسات من Microsoft Defender نفسه. سيقوم تطبيق أمن Windows بتغيير قسم **الحماية من التهديدات & الفيروسات** لإظهار حالة منتج AV، وتوفير ارتباط إلى خيارات تكوين المنتج.

أسفل أي منتجات AV لجهة خارجية، سيظهر ارتباط جديد **كخيارات برنامج الحماية من الفيروسات من Microsoft Defender**. سيؤدي النقر فوق هذا الارتباط إلى توسيع لإظهار التبديل الذي يمكن الفحص الدوري المحدود. لاحظ أن الخيار الدوري المحدود هو تبديل لتمكين المسح الدوري أو تعطيله. 

سيؤدي تمرير مفتاح التبديل إلى **"تشغيل** " إلى إظهار خيارات Microsoft Defender AV القياسية أسفل منتج AV الخاص بالجهة الخارجية. سيظهر خيار الفحص الدوري المحدود في أسفل الصفحة.

## <a name="related-articles"></a>المقالات ذات الصلة

- [تكوين الحماية السلوكية، والحماية التحليلية، والحماية في الوقت الحقيقي](configure-protection-features-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)