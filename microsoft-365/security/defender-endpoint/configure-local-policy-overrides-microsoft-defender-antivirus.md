---
title: تكوين التجاوزات المحلية لإعدادات برنامج الحماية من الفيروسات من Microsoft Defender
description: تمكين المستخدمين أو تعطيلهم من تغيير الإعدادات محليا في Microsoft Defender AV.
keywords: تجاوز محلي، نهج محلي، نهج المجموعة، عنصر نهج المجموعة، تأمين، دمج، قوائم
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: ae90694bab8191c2ad83fa1de7563bc2ba7643e8
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789745"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>منع المستخدمين أو السماح لهم بتعديل إعدادات نهج برنامج الحماية من الفيروسات من Microsoft Defender محليا


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

بشكل افتراضي، ستمنع إعدادات برنامج الحماية من الفيروسات من Microsoft Defender التي يتم نشرها عبر عنصر نهج المجموعة إلى نقاط النهاية في الشبكة المستخدمين من تغيير الإعدادات محليا. يمكنك تغيير هذا في بعض المثيلات.

على سبيل المثال، قد يكون من الضروري السماح لمجموعات مستخدمين معينة (مثل الباحثين الأمنيين ومحققي التهديدات) بمزيد من التحكم في الإعدادات الفردية على نقاط النهاية التي يستخدمونها.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>تكوين التجاوزات المحلية لإعدادات برنامج الحماية من الفيروسات من Microsoft Defender

الإعداد الافتراضي لهذه النهج **معطل**.

إذا تم تعيينها إلى **"ممكن"**، يمكن للمستخدمين على نقاط النهاية إجراء تغييرات على الإعداد المقترن بتطبيق [أمن Windows](microsoft-defender-security-center-antivirus.md) وإعدادات نهج المجموعة المحلية وPowerShell cmdlets (عند الاقتضاء).

يسرد الجدول التالي كل إعداد من إعداد نهج التجاوز وإرشادات التكوين للميزة أو الإعداد المقترن.

لتكوين هذه الإعدادات:

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر** وانقر فوق **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات** >  Windows **برنامج الحماية من الفيروسات من Microsoft Defender** ثم **الموقع** المحدد في جدول الإعدادات (في هذه المقالة).

4. انقر نقرا مزدوجا فوق **"إعداد النهج"** كما هو محدد في الجدول أدناه، ثم قم بتعيين الخيار إلى التكوين المطلوب. انقر فوق **"موافق**"، ثم كرر أي إعدادات أخرى.

5. نشر كائن نهج المجموعة كالمعتاد.

## <a name="table-of-settings"></a>جدول الإعدادات

<br/><br/>

| موقع | اعداد | الماده |
|---|---|---|---|
| خرائط |تكوين تجاوز الإعداد المحلي لإعداد التقارير إلى Microsoft MAPS|[تمكين الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) |
| العزل|تكوين تجاوز الإعداد المحلي لإزالة العناصر من مجلد العزل|[تكوين المعالجة لإجراء عمليات الفحص](configure-remediation-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمراقبة نشاط الملفات والبرامج على الكمبيوتر|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمراقبة نشاط الملفات الواردة والصادرة | [تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمسح كافة الملفات والمرفقات التي تم تنزيلها|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لتشغيل مراقبة السلوك|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعدادات المحلية لتشغيل الحماية في الوقت الحقيقي|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الاصلاح|تكوين تجاوز الإعداد المحلي لوقت اليوم لتشغيل فحص كامل مجدول لإكمال المعالجة|[تكوين المعالجة لإجراء عمليات الفحص](configure-remediation-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي للحد الأقصى للنسبة المئوية لاستخدام وحدة المعالجة المركزية|[تكوين عمليات الفحص وتشغيلها](run-scan-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي ليوم فحص الجدول|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي لوقت الفحص السريع المجدول|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي لوقت الفحص المجدول|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي لنوع الفحص لاستخدامه لإجراء فحص مجدول|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>تكوين كيفية دمج قوائم معالجة المخاطر والاستثناءات المحددة محليا وبشكل عمومي

يمكنك أيضا تكوين كيفية دمج القوائم المعرفة محليا أو دمجها مع القوائم المعرفة عالميا. ينطبق هذا الإعداد على [قوائم الاستبعاد](configure-exclusions-microsoft-defender-antivirus.md) [وقوائم المعالجة المحددة](configure-remediation-microsoft-defender-antivirus.md) [وتقليل الأجزاء المعرضة للهجوم](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).

بشكل افتراضي، يتم دمج القوائم التي تم تكوينها في نهج المجموعة المحلية وتطبيق أمن Windows مع القوائم التي تم تعريفها بواسطة كائن نهج المجموعة المناسب الذي قمت بنشره على شبكتك. في حالة وجود تعارضات، تكون للقائمة المعرفة عالميا الأسبقية.

يمكنك تعطيل هذا الإعداد للتأكد من استخدام القوائم المعرفة عالميا فقط (مثل تلك من أي عناصر نهج المجموعة المنشورة).

### <a name="use-group-policy-to-disable-local-list-merging"></a>استخدام نهج المجموعة لتعطيل دمج القوائم المحلية

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر** وانقر فوق **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender**.

4. انقر نقرا مزدوجا فوق **تكوين سلوك دمج المسؤولين المحليين للقوائم** وتعيين الخيار إلى **"معطل**". انقر فوق **موافق**.

> [!NOTE]
> إذا قمت بتعطيل دمج القائمة المحلية، فسيتجاوز إعدادات الوصول إلى المجلدات التي يتم التحكم فيها. كما أنه يتجاوز أي مجلدات محمية أو تطبيقات مسموح بها تم تعيينها من قبل المسؤول المحلي. لمزيد من المعلومات حول إعدادات الوصول إلى المجلدات التي يتم التحكم فيها، راجع [السماح بتطبيق محظور في أمن Windows](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [تكوين تفاعل المستخدم النهائي مع برنامج الحماية من الفيروسات من Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
