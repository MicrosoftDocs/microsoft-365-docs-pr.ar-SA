---
title: استكشاف مشكلات قواعد تقليل الأجزاء المعرضة للهجوم وإصلاحها
description: الموارد وعينة التعليمات البرمجية لاستكشاف المشكلات وإصلاحها مع قواعد تقليل الأجزاء المعرضة للهجوم في Microsoft Defender لنقطة النهاية.
keywords: استكشاف الأخطاء وإصلاحها، والخطأ، وإصلاحها، وwindows defender eg، و asr، والقواعد، والوركين، واستكشاف الأخطاء وإصلاحها، والتدقيق، والاستبعاد، والإيجابية الخاطئة، والمعطلة، والحظر، Microsoft Defender لنقطة النهاية
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.date: 03/27/2019
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 9c884ab9a4ee2180d3c491c4257fb04129c40bc9
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717199"
---
# <a name="troubleshoot-attack-surface-reduction-rules"></a>استكشاف أخطاء قواعد تقليل الأجزاء المعرضة للهجوم وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

عند استخدام [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md) ، قد تتعرض للمشاكل، مثل:

- تمنع القاعدة ملفا أو معالجة أو تنفذ بعض الإجراءات الأخرى التي لا ينبغي أن تكون (إيجابية خاطئة)
- لا تعمل القاعدة كما هو موضح، أو لا تحظر ملفا أو عملية يجب أن تعمل عليها (سلبي خطأ)

هناك أربع خطوات لاستكشاف هذه المشاكل وإصلاحها:

1. [تأكيد المتطلبات الأساسية](#confirm-prerequisites)
2. [استخدام وضع التدقيق لاختبار القاعدة](#use-audit-mode-to-test-the-rule)
3. [إضافة استثناءات للقاعدة المحددة](#add-exclusions-for-a-false-positive) (للإيجابيات الخاطئة)
4. [إرسال سجلات الدعم](#collect-diagnostic-data-for-file-submissions)

## <a name="confirm-prerequisites"></a>تأكيد المتطلبات الأساسية

ستعمل قواعد تقليل الأجزاء المعرضة للهجوم فقط على الأجهزة التي تتضمن الشروط التالية:

- يتم تشغيل نقاط النهاية Windows 10 Enterprise، الإصدار 1709 (المعروف أيضا باسم Fall Creators Update).

- تستخدم نقاط النهاية برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات الوحيد. [سيؤدي استخدام أي تطبيق آخر من تطبيقات الحماية من الفيروسات إلى تعطيل Microsoft Defender Antivirus نفسه](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

- يتم تمكين [الحماية في الوقت الحقيقي](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus).

- لم يتم تمكين وضع التدقيق. استخدم نهج المجموعة لتعيين القاعدة إلى **معطل** (القيمة: **0**) كما هو موضح في [تمكين قواعد تقليل الأجزاء المعرضة للهجوم](enable-attack-surface-reduction.md).

إذا تم استيفاء جميع هذه المتطلبات الأساسية، فانطلق إلى الخطوة التالية لاختبار القاعدة في وضع التدقيق.

## <a name="use-audit-mode-to-test-the-rule"></a>استخدام وضع التدقيق لاختبار القاعدة

اتبع هذه الإرشادات في [استخدام أداة العرض التوضيحي لمعرفة كيفية عمل قواعد تقليل الأجزاء المعرضة للهجوم](evaluate-attack-surface-reduction.md) لاختبار القاعدة المحددة التي تواجه مشاكل معها.

1. تمكين وضع التدقيق للقاعدة المحددة التي تريد اختبارها. استخدم نهج المجموعة لتعيين القاعدة إلى **وضع التدقيق** (القيمة: **2**) كما هو موضح في [تمكين قواعد تقليل الأجزاء المعرضة للهجوم](enable-attack-surface-reduction.md). يسمح وضع التدقيق للقاعدة بالإبلاغ عن الملف أو العملية، ولكنه سيسمح بتشغيلها.

2. قم بتنفيذ النشاط الذي يتسبب في حدوث مشكلة (على سبيل المثال، فتح الملف أو العملية التي يجب حظرها أو تنفيذها ولكن يتم السماح بها).

3. [راجع سجلات أحداث قاعدة تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md) لمعرفة ما إذا كانت القاعدة قد حظرت الملف أو العملية إذا تم تعيين القاعدة إلى **Enabled**.

إذا كانت القاعدة لا تحظر ملفا أو عملية تتوقع أن تقوم بحظرها، فتحقق أولا مما إذا كان وضع التدقيق ممكنا.

ربما تم تمكين وضع التدقيق لاختبار ميزة أخرى، أو بواسطة برنامج نصي PowerShell مؤتمت، وربما لم يتم تعطيله بعد اكتمال الاختبارات.

إذا قمت باختبار القاعدة باستخدام أداة العرض التوضيحي ووضع التدقيق، وتعمل قواعد تقليل الأجزاء المعرضة للهجوم على سيناريوهات تم تكوينها مسبقا، ولكن القاعدة لا تعمل كما هو متوقع، فانتقل إلى أي من الأقسام التالية استنادا إلى حالتك:

1. إذا كانت قاعدة تقليل الأجزاء المعرضة للهجوم تحظر شيئا لا ينبغي حظره (يعرف أيضا بالايجابية الخاطئة)، يمكنك [أولا إضافة استثناء قاعدة تقليل الأجزاء المعرضة للهجوم](#add-exclusions-for-a-false-positive).

2. إذا كانت قاعدة تقليل الأجزاء المعرضة للهجوم لا تحظر شيئا يجب أن تحظره (المعروف أيضا باسم سلبي خطأ)، يمكنك المتابعة مباشرة إلى الخطوة الأخيرة، [وجمع البيانات التشخيصية وإرسال المشكلة إلينا](#collect-diagnostic-data-for-file-submissions).

## <a name="add-exclusions-for-a-false-positive"></a>إضافة استثناءات للإيجابية الخاطئة

إذا كانت قاعدة تقليل الأجزاء المعرضة للهجوم تحظر شيئا لا ينبغي حظره (يعرف أيضا بإيجابية خاطئة)، يمكنك إضافة استثناءات لمنع قواعد تقليل الأجزاء المعرضة للهجوم من تقييم الملفات أو المجلدات المستبعدة.

لإضافة استثناء، راجع [تخصيص تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules).

> [!IMPORTANT]
> يمكنك تحديد الملفات والمجلدات الفردية التي سيتم استبعادها، ولكن لا يمكنك تحديد قواعد فردية.
> وهذا يعني أن أي ملفات أو مجلدات يتم استبعادها سيتم استبعادها من كافة قواعد ASR.

## <a name="report-a-false-positive-or-false-negative"></a>الإبلاغ عن قيمة سلبية خاطئة أو إيجابية خاطئة

استخدم [نموذج الإرسال المستند إلى Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) للإبلاغ عن إيجابية سلبية أو خطأ خاطئة لحماية الشبكة. باستخدام اشتراك Windows E5، يمكنك أيضا [توفير ارتباط إلى أي تنبيه مقترن](alerts-queue.md).

## <a name="collect-diagnostic-data-for-file-submissions"></a>تجميع البيانات التشخيصية الخاصة بإرسالات الملفات

عند الإبلاغ عن مشكلة في قواعد تقليل الأجزاء المعرضة للهجوم، يطلب منك جمع وإرسال البيانات التشخيصية التي يمكن أن تستخدمها فرق الدعم والهندسة في Microsoft للمساعدة في استكشاف المشكلات وإصلاحها.

1. افتح موجه أوامر غير مقيد وقم بالتغيير إلى دليل Windows Defender:

   ```console
   cd "c:\program files\windows defender"
   ```

2. تشغيل هذا الأمر لإنشاء سجلات التشخيص:

   ```console
   mpcmdrun -getfiles
   ```

3. بشكل افتراضي، يتم حفظها في `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`. إرفاق الملف بنموذج الإرسال.

## <a name="related-articles"></a>المقالات ذات الصلة

- [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)
- [تمكين قواعد تقليل الأجزاء المعرضة للهجوم](enable-attack-surface-reduction.md)
- [تقييم قواعد تقليل الأجزاء المعرضة للهجوم](evaluate-attack-surface-reduction.md)
