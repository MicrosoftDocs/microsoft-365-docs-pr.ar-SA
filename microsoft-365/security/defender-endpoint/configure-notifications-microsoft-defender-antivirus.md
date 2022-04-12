---
title: تكوين إعلامات برنامج الحماية من الفيروسات من Microsoft Defender
description: تعرف على كيفية تكوين وتخصيص كل من إعلامات برنامج الحماية من الفيروسات من Microsoft Defender القياسية وغيرها على نقاط النهاية.
keywords: الإعلامات، والمدافع، ومكافحة الفيروسات، ونقطة النهاية، والإدارة، والمسؤول
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: e38a8e9de3bef132dfdf3d2a088190a5038a2941
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790185"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>تكوين إعلامات برنامج الحماية من الفيروسات من Microsoft Defender التي تظهر على نقاط النهاية

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

في Windows 10 Windows 11، تكون إعلامات التطبيق حول الكشف عن البرامج الضارة ومعالجتها أكثر قوة واتساقا وإيجازا. تظهر إعلامات برنامج الحماية من الفيروسات من Microsoft Defender على نقاط النهاية عند اكتمال عمليات الفحص واكتشاف التهديدات. تتبع الإعلامات عمليات الفحص المجدولة والمشغلة يدويا. تظهر هذه الإعلامات أيضا في **مركز الإعلامات**، ويظهر ملخص عمليات الفحص والكشف عن التهديدات في فواصل زمنية منتظمة.

إذا كنت جزءا من فريق الأمان في مؤسستك، يمكنك تكوين كيفية ظهور الإعلامات على نقاط النهاية، مثل الإعلامات التي تطالب بإعادة تشغيل النظام أو التي تشير إلى اكتشاف تهديد ومعالجتها.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>تكوين إعلامات مكافحة الفيروسات باستخدام نهج المجموعة أو تطبيق أمن Windows

يمكنك تكوين عرض إعلامات إضافية، مثل ملخصات الكشف عن التهديدات الأخيرة، في [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md) ومع نهج المجموعة.

> [!NOTE]
> في Windows 10، كان الإصدار 1607 يسمى الميزة **إعلامات محسنة** وتم تكوينها ضمن **Windows الإعدادات** \> **Update & security** \> **Windows Defender**. في إعدادات نهج المجموعة لكل إصدارات Windows 10 Windows 11، تسمى ميزة **الإعلامات "الإعلامات المحسنة**".

### <a name="use-group-policy-to-disable-additional-notifications"></a>استخدام نهج المجموعة لتعطيل الإعلامات الإضافية

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انقر بزر الماوس الأيمن فوق الكائن نهج المجموعة الذي تريد تكوينه، ثم حدد **"تحرير**".

3. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

4. حدد **القوالب الإدارية**.

5. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** >  **Reporting**.

6. انقر نقرا مزدوجا **فوق إيقاف تشغيل الإعلامات المحسنة**، ثم قم بتعيين الخيار إلى **ممكن**. ثم حدد **"موافق**". سيؤدي ذلك إلى منع ظهور إعلامات إضافية.

> [!IMPORTANT]
> لن يؤدي تعطيل الإعلامات الإضافية إلى تعطيل الإعلامات الهامة، مثل الكشف عن التهديدات وتنبيهات المعالجة.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>استخدام تطبيق أمن Windows لتعطيل الإعلامات الإضافية

1. افتح تطبيق أمن Windows بالنقر فوق أيقونة الدرع في شريط المهام أو البحث في قائمة البدء عن **الأمان**.

2. حدد **إطار الحماية من الفيروسات &** (أو أيقونة الدرع على شريط القوائم الأيسر)، ثم حدد **إعدادات الحماية من الفيروسات & التهديدات**

3. قم بالتمرير إلى قسم **الإعلامات** وحدد **تغيير إعدادات الإعلامات**.

4. مرر مفتاح التبديل إلى **"إيقاف تشغيل"** أو " **تشغيل** " لتعطيل الإعلامات الإضافية أو تمكينها.

> [!IMPORTANT]
> لن يؤدي تعطيل الإعلامات الإضافية إلى تعطيل الإعلامات الهامة، مثل الكشف عن التهديدات وتنبيهات المعالجة.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>تكوين الإعلامات القياسية على نقاط النهاية باستخدام نهج المجموعة

يمكنك استخدام نهج المجموعة من أجل:

- عرض نص إضافي ومخصص على نقاط النهاية عندما يحتاج المستخدم إلى تنفيذ إجراء
- إخفاء كافة الإعلامات على نقاط النهاية
- إخفاء إعلامات إعادة التشغيل على نقاط النهاية

قد يكون إخفاء الإعلامات مفيدا في الحالات التي لا يمكنك فيها إخفاء واجهة برنامج الحماية من الفيروسات من Microsoft Defender بأكملها. راجع [منع المستخدمين من رؤية واجهة المستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها](prevent-end-user-interaction-microsoft-defender-antivirus.md) للحصول على مزيد من المعلومات. لن يحدث إخفاء الإعلامات إلا على نقاط النهاية التي تم نشر النهج إليها. ستظل الإشعارات المتعلقة بالإجراءات التي يجب اتخاذها (مثل إعادة التشغيل) تظهر على [لوحة معلومات المراقبة والتقارير إدارة نقاط النهاية من Microsoft Endpoint Protection](/configmgr/protect/deploy-use/monitor-endpoint-protection). 

لإضافة معلومات جهة اتصال مخصصة إلى إعلامات نقطة النهاية، راجع [تخصيص تطبيق أمن Windows لمؤسستك](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).

### <a name="use-group-policy-to-hide-notifications"></a>استخدام نهج المجموعة لإخفاء الإعلامات

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انقر بزر الماوس الأيمن فوق الكائن نهج المجموعة الذي تريد تكوينه، ثم حدد **"تحرير**".

3. في **نهج المجموعة انتقل محرر الإدارة** إلى **تكوين الكمبيوتر** ثم حدد **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **واجهة العميل**. 

5. انقر نقرا مزدوجا فوق **"منع كافة الإعلامات**" وعين الخيار "**ممكن".** 

6. حدد **موافق**. سيؤدي ذلك إلى منع ظهور إعلامات إضافية.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>استخدام نهج المجموعة لإخفاء إعلامات إعادة التشغيل

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انقر بزر الماوس الأيمن فوق الكائن نهج المجموعة الذي تريد تكوينه ثم حدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **واجهة العميل**.

5. انقر نقرا **مزدوجا فوق منع إعلامات إعادة التشغيل** وتعيين الخيار إلى **ممكن**. 

5. حدد **موافق**. سيؤدي ذلك إلى منع ظهور إعلامات إضافية.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)