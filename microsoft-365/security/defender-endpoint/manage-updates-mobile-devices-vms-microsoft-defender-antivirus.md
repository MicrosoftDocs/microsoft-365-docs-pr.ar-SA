---
title: تحديد كيفية تحديث الأجهزة المحمولة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender
description: إدارة كيفية تحديث الأجهزة المحمولة، مثل أجهزة الكمبيوتر المحمولة، بتحديثات الحماية برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: التحديثات، والحماية، والتحديثات المجدولة، والبطارية، والجهاز المحمول، والكمبيوتر المحمول، ودفتر الملاحظات، والموافقة، وتحديث Microsoft، وwsus، والتجاوز
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: f582e33f2d77c8560b773b79d54026e38bcde8c9
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790361"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

قد تتطلب الأجهزة المحمولة والأجهزة الظاهرية المزيد من التكوين لضمان عدم تأثر الأداء بالتحديثات.

هناك إعدادان مفيدان لهذه الأجهزة:

- الاشتراك في Microsoft Update على أجهزة الكمبيوتر المحمولة بدون اتصال WSUS
- منع تحديثات التحليل الذكي للأمان عند التشغيل على طاقة البطارية

قد تكون المقالات التالية مفيدة أيضا في هذه الحالات:
- [تكوين عمليات الفحص المجدولة والمتابعة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [دليل النشر برنامج الحماية من الفيروسات من Microsoft Defender في بيئة البنية الأساسية لسطح المكتب الظاهري (VDI)](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>الاشتراك في Microsoft Update على أجهزة الكمبيوتر المحمولة بدون اتصال WSUS

يمكنك استخدام Microsoft Update لإبقاء معلومات الأمان على الأجهزة المحمولة قيد التشغيل برنامج الحماية من الفيروسات من Microsoft Defender محدثة عندما لا تكون متصلة بشبكة الشركة أو إذا لم يكن لديها اتصال WSUS.

وهذا يعني أنه يمكن تسليم تحديثات الحماية إلى الأجهزة (عبر Microsoft Update) حتى إذا قمت بتعيين WSUS لتجاوز Microsoft Update.

يمكنك الاشتراك في Microsoft Update على الجهاز المحمول بإحدى الطرق التالية:

- تغيير الإعداد باستخدام نهج المجموعة.
- استخدم VBScript لإنشاء برنامج نصي، ثم قم بتشغيله على كل كمبيوتر في شبكتك.
- اختر كل كمبيوتر على الشبكة يدويا من خلال قائمة **الإعدادات**.

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>استخدام نهج المجموعة للاشتراك في Microsoft Update

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وحدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. حدد **النهج** ثم **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **تحديثات التوقيع**.

5. قم بتعيين **السماح بتحديثات التحليل الذكي للأمان من Microsoft Update** إلى **ممكن**، ثم حدد  **"موافق**".

### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>استخدام VBScript للاشتراك في Microsoft Update

1. استخدم الإرشادات الواردة في مقالة MSDN ["الاشتراك في Microsoft Update](/windows/win32/wua_sdk/opt-in-to-microsoft-update) " لإنشاء VBScript.

2. قم بتشغيل VBScript الذي أنشأته على كل كمبيوتر في شبكتك.

### <a name="manually-opt-in-to-microsoft-update"></a>الاشتراك يدويا في Microsoft Update

1. افتح **Windows Update** في تحديث إعدادات **الأمان &** على الكمبيوتر الذي تريد الاشتراك فيه.

2. حدد **خيارات متقدمة** .

3. حدد خانة الاختيار الخاصة **بتحديثات "إعطائي" لمنتجات Microsoft الأخرى عند تحديث Windows**.

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>منع تحديثات التحليل الذكي للأمان عند التشغيل على طاقة البطارية

يمكنك تكوين برنامج الحماية من الفيروسات من Microsoft Defender لتنزيل تحديثات الحماية فقط عندما يكون الكمبيوتر متصلا بمصدر طاقة سلكي.

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>استخدام نهج المجموعة لمنع تحديثات التحليل الذكي للأمان على طاقة البطارية

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، واختر العنصر نهج المجموعة الذي تريد تكوينه، وافتحه للتحرير.

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. حدد **النهج** ثم **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **تحديثات التوقيع**، ثم قم بتعيين **السماح بتحديثات تحليل معلومات الأمان عند التشغيل على طاقة البطارية** إلى **"معطل".** ثم حدد **"موافق**".

يمنع هذا الإجراء تنزيل تحديثات الحماية عندما يكون الكمبيوتر في طاقة البطارية.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md)
- [تحديث برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها في Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)