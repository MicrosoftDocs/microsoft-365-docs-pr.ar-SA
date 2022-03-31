---
title: تعريف كيفية تحديث الأجهزة المحمولة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender
description: إدارة كيفية تحديث الأجهزة المحمولة، مثل أجهزة الكمبيوتر المحمولة، برنامج الحماية من الفيروسات من Microsoft Defender تحديثات الحماية.
keywords: التحديثات والحماية وجدولة التحديثات والبطارية والجهاز المحمول وأجهزة الكمبيوتر المحمول، دفتر الملاحظات، الاشتراك، تحديث microsoft، wsus، التجاوز
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
ms.openlocfilehash: 3fc6d5a8b8fa7889f65f21111b3af82e124516b4
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63578175"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

قد تتطلب الأجهزة المحمولة وأجهزة VMs المزيد من التكوين لضمان عدم تأثير التحديثات على الأداء.

هناك إعدادان مفيدان لهذه الأجهزة:

- الاشتراك في Microsoft Update على أجهزة الكمبيوتر المحمولة بدون اتصال WSUS
- منع تحديثات معلومات الأمان عند التشغيل على طاقة البطارية

قد تكون المقالات التالية مفيدة أيضا في هذه الحالات:
- [تكوين عمليات الفحص المجدولة والملحقة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [دليل النشر برنامج الحماية من الفيروسات من Microsoft Defender في بيئة البنية الأساسية لسطح المكتب الظاهري (VDI)](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>الاشتراك في Microsoft Update على أجهزة الكمبيوتر المحمولة بدون اتصال WSUS

يمكنك استخدام Microsoft Update لإبقاء معلومات الأمان على الأجهزة المحمولة برنامج الحماية من الفيروسات من Microsoft Defender محدثة عندما لا تكون متصلة بشبكة الشركة أو إذا لم يكن لديك اتصال WSUS.

وهذا يعني أنه يمكن تسليم تحديثات الحماية إلى الأجهزة (عبر Microsoft Update) حتى لو قمت بتعيين WSUS لتجاوز Microsoft Update.

يمكنك الاشتراك في Microsoft Update على الجهاز المحمول باستخدام إحدى الطرق التالية:

- تغيير الإعداد باستخدام نهج المجموعة.
- استخدم VBScript لإنشاء برنامج نصي، ثم قم بتشغيله على كل كمبيوتر في الشبكة.
- يمكنك الاشتراك يدويا في كل كمبيوتر على الشبكة من **خلال** الإعدادات.

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>استخدام "نهج المجموعة" لاختيار الاشتراك في Microsoft Update

1. على جهاز إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وحدد **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. حدد **سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **التواقيع**.

5. قم **بتعيين السماح بتحديثات معلومات الأمان من Microsoft Update** إلى **تمكين**، ثم حدد  **موافق**.

### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>استخدام VBScript لإلغاء الاشتراك في Microsoft Update

1. استخدم الإرشادات الواردة في مقالة MSDN [الاشتراك في Microsoft Update](/windows/win32/wua_sdk/opt-in-to-microsoft-update) لإنشاء VBScript.

2. قم بتشغيل VBScript الذي أنشأته على كل كمبيوتر في الشبكة.

### <a name="manually-opt-in-to-microsoft-update"></a>الاشتراك يدويا في Microsoft Update

1. افتح **Windows التحديث في** **تحديث &** إعدادات الأمان على الكمبيوتر الذي تريد الاشتراك فيه.

2. حدد **خيارات** متقدمة.

3. حدد خانة الاختيار الخاصة **بتحديثات "أعطني" لمنتجات Microsoft الأخرى عند تحديث Windows**.

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>منع تحديثات معلومات الأمان عند التشغيل على طاقة البطارية

يمكنك تكوين برنامج الحماية من الفيروسات من Microsoft Defender لتنزيل تحديثات الحماية فقط عندما يكون الكمبيوتر متصلا بمصدر طاقة سلكي.

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>استخدام "نهج المجموعة" لمنع تحديثات معلومات الأمان على طاقة البطارية

1. على جهاز إدارة نهج المجموعة، [افتح وحدة تحكم](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) إدارة نهج المجموعة، واختر كائن نهج المجموعة الذي تريد تكوينه، وافتحه للتحرير.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. حدد **سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> التواقيع، ثم قم بتعيين السماح بتحديثات معلومات الأمان عند التشغيل على طاقة **البطارية إلى** **معطل**. ثم حدد **موافق**.

يمنع هذا الإجراء تنزيل تحديثات الحماية عندما يكون الكمبيوتر على طاقة البطارية.

## <a name="related-articles"></a>المقالات ذات الصلة

- [إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيقها](manage-updates-baselines-microsoft-defender-antivirus.md)
- [تحديث وإدارة برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)