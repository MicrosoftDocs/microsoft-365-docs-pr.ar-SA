---
title: تكوين تجاوزات محلية برنامج الحماية من الفيروسات من Microsoft Defender الإعدادات
description: تمكين المستخدمين أو تعطيلهم من الإعدادات المتغيرة محليا في Microsoft Defender AV.
keywords: تجاوز محلي، نهج محلي، نهج المجموعة، gpo، تأمين، دمج، قوائم
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
ms.openlocfilehash: ec916b008ddb3e0669111efe2bd493c709327296
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63579542"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>منع المستخدمين من تعديل إعدادات نهج برنامج الحماية من الفيروسات من Microsoft Defender محليا أو السماح لهم بذلك


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

بشكل افتراضي، برنامج الحماية من الفيروسات من Microsoft Defender الإعدادات التي يتم نشرها عبر "كائن نهج المجموعة" إلى نقاط النهاية في شبكتك إلى منع المستخدمين من تغيير الإعدادات محليا. يمكنك تغيير ذلك في بعض الحالات.

على سبيل المثال، قد يكون من الضروري السماح لمجموعات معينة من المستخدمين (مثل الباحثين في مجال الأمان ومستخدمي التهديدات) بمزيد من التحكم في الإعدادات الفردية على نقاط النهاية التي يستخدمونها.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>تكوين تجاوزات محلية برنامج الحماية من الفيروسات من Microsoft Defender الإعدادات

الإعداد الافتراضي لهذه السياسات **معطل**.

إذا تم تعيينها إلى "تمكين"، يمكن للمستخدمين على نقاط النهاية إجراء تغييرات على الإعداد المقترن باستخدام تطبيق [أمن Windows](microsoft-defender-security-center-antivirus.md) وإعدادات نهج المجموعة المحلية و PowerShell cmdlets (حيثما يكون ذلك مناسبا).

يسرد الجدول التالي كل إعداد نهج تجاوز وإرشادات التكوين للميزة أو الإعداد المقترنين.

لتكوين هذه الإعدادات:

1. على كمبيوتر إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر** وانقر فوق **قوالب إدارية**.

3. قم بتوسيع الشجرة **Windows المكونات برنامج الحماية من الفيروسات من Microsoft Defender** >  ثم الموقع المحدد في جدول الإعدادات (في  هذه المقالة).

4. انقر نقرا مزدوجا **فوق إعداد النهج** كما هو محدد في الجدول أدناه، ثم قم بتعيين الخيار إلى التكوين المطلوب. انقر **فوق موافق**، وكرر أي إعدادات أخرى.

5. نشر كائن نهج المجموعة كالمعتاد.

## <a name="table-of-settings"></a>جدول الإعدادات

<br/><br/>

| الموقع | الإعداد | مقالة |
|---|---|---|---|
| الخرائط |تكوين تجاوز الإعدادات المحلية لإعداد التقارير إلى Microsoft MAPS|[تمكين الحماية التي يتم تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) |
| الفحص|تكوين تجاوز الإعداد المحلي لإزالة العناصر من مجلد "الفحص"|[تكوين المعالجة من أجل عمليات الفحص](configure-remediation-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعدادات المحلية لمراقبة نشاط الملف والبرنامج على الكمبيوتر|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمراقبة نشاط الملفات الواردة وال الصادرة | [تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمسح كل الملفات والمرفقات التي تم تنزيلها|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي من أجل تشغيل مراقبة السلوك|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md) |
| الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي ل تشغيل الحماية في الوقت الحقيقي|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md) |
| المعالجة|تكوين تجاوز الإعداد المحلي في وقت اليوم لتشغيل فحص كامل مجدول لإكمال المعالجة|[تكوين المعالجة من أجل عمليات الفحص](configure-remediation-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي للحصول على النسبة المئوية القصوى لاستخدام CPU|[تكوين عمليات الفحص وتشغيلها](run-scan-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي لجدولة يوم الفحص|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي في وقت الفحص السريع المجدول|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي للوقت المجدول للفحص|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| المسح الضوئي|تكوين تجاوز الإعداد المحلي لنوع الفحص لاستخدامه في عملية فحص مجدولة|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>تكوين كيفية دمج قوائم المعالجة والاستثناءات المحددة محليا وعلى مستوى العالم

يمكنك أيضا تكوين كيفية دمج القوائم المعرفة محليا أو دمجها مع القوائم المعرفة بشكل عام. ينطبق هذا الإعداد على [قوائم](configure-exclusions-microsoft-defender-antivirus.md) الاستثناء [وقوائم](configure-remediation-microsoft-defender-antivirus.md) المعالجة المحددة والحد [من سطح الهجوم](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).

بشكل افتراضي، يتم دمج القوائم التي تم تكوينها في نهج المجموعة المحلي أمن Windows مع القوائم المعرفة بواسطة "كائن نهج المجموعة" المناسب الذي قمت بنشره على الشبكة. في الحالات التي توجد فيها تعارضات، يكون للقائمة المعرفة بشكل عمومي الأسبقية.

يمكنك تعطيل هذا الإعداد لضمان استخدام القوائم المعرفة بشكل عمومي فقط (مثل تلك التي تم نشرها من أي من قوائم GPOs التي تم نشرها).

### <a name="use-group-policy-to-disable-local-list-merging"></a>استخدام "نهج المجموعة" لتعطيل دمج القائمة المحلية

1. على كمبيوتر إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر** وانقر فوق **قوالب إدارية**.

3. قم بتوسيع الشجرة Windows **مكونات > برنامج الحماية من الفيروسات من Microsoft Defender**.

4. انقر نقرا **مزدوجا فوق تكوين سلوك دمج المسؤول المحلي والقوائم** ، ثم قم بتعيين الخيار إلى **معطل**. انقر فوق **موافق**.

> [!NOTE]
> إذا قمت بتعطيل دمج القائمة المحلية، سيتم تجاوز إعدادات الوصول إلى المجلدات التي يتم التحكم بها. كما أنه يتجاوز أي مجلدات محمية أو تطبيقات مسموح بها يحددها المسؤول المحلي. لمزيد من المعلومات حول إعدادات الوصول إلى المجلدات التي يتم التحكم بها، راجع [السماح لتطبيق تم حظره في](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security) أمن Windows.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [تكوين تفاعل المستخدم النهائي مع برنامج الحماية من الفيروسات من Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
