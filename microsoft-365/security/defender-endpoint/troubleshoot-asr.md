---
title: استكشاف المشاكل المتعلقة بقواعد الحد من سطح الهجوم وإصلاحها
description: الموارد ونموذج التعليمات البرمجية لا استكشاف المشاكل المتعلقة بقواعد الحد من سطح الهجوم وإصلاحها في Microsoft Defender لنقطة النهاية.
keywords: استكشاف الأخطاء وإصلاحها والخطأ وإصلاحها و windows defender eg و asr والقواعد والوركين وإصلاحها والتدقيق والاستبعاد والإيجابية الخاطئة والكسر والحظر و Microsoft Defender ل Endpoint
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
ms.openlocfilehash: c503c3ed4cfea4ed0645cf18a9c9bf4ebe4a5ade
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63570153"
---
# <a name="troubleshoot-attack-surface-reduction-rules"></a>استكشاف الأخطاء في قواعد الحد من سطح الهجوم وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

عند استخدام قواعد تقليل [مساحة الهجوم](attack-surface-reduction.md) ، قد تجابه مشاكل، مثل:

- تقوم القاعدة بحظر ملف أو معالجة أو تنفيذ إجراء آخر لا يجب أن ينفذه (موجب خطأ)
- لا تعمل القاعدة كما هو موضح، أو لا تمنع ملفا أو عملية يجب أن تكون (سالبة خطأ)

هناك أربع خطوات يمكن من خلالها استكشاف هذه المشاكل وإصلاحها:

1. [تأكيد المتطلبات الأساسية](#confirm-prerequisites)
2. [استخدام وضع التدقيق لاختبار القاعدة](#use-audit-mode-to-test-the-rule)
3. [إضافة استثناءات للقاعدة المحددة](#add-exclusions-for-a-false-positive) (للموجبة الخاطئة)
4. [إرسال سجلات الدعم](#collect-diagnostic-data-for-file-submissions)

## <a name="confirm-prerequisites"></a>تأكيد المتطلبات الأساسية

ستعمل قواعد تقليل مساحة الهجوم فقط على الأجهزة بالشروط التالية:

- يتم تشغيل نقاط النهاية Windows 10 Enterprise، الإصدار 1709 (المعروف أيضا بتحديث المبدعين الخريف).

- تستخدم نقاط النهاية برنامج الحماية من الفيروسات من Microsoft Defender تطبيق الحماية من الفيروسات الوحيد. [سيؤدي استخدام أي تطبيق آخر لمكافحة الفيروسات برنامج الحماية من الفيروسات من Microsoft Defender تعطيل نفسه](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

- [يتم تمكين الحماية](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) في الوقت الحقيقي.

- وضع التدقيق غير ممكن. استخدم نهج المجموعة لتعيين القاعدة إلى **معطل** (القيمة: **0**) كما هو موضح في [تمكين قواعد تقليل مساحة الهجوم](enable-attack-surface-reduction.md).

إذا تم كل هذه المتطلبات الأساسية، فاتابع إلى الخطوة التالية لاختبار القاعدة في وضع التدقيق.

## <a name="use-audit-mode-to-test-the-rule"></a>استخدام وضع التدقيق لاختبار القاعدة

يمكنك زيارة موقع الويب الأرضي لاختبار Windows Defender في [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) لتأكيد أن قواعد تقليل مساحة الهجوم تعمل بشكل عام مع السيناريوهات والعمليات التي تم تكوينها مسبقا على جهاز، أو يمكنك استخدام وضع التدقيق، الذي يمكن القواعد لإعداد التقارير فقط.

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

اتبع هذه الإرشادات في [استخدام أداة](evaluate-attack-surface-reduction.md) العرض التوضيحي لمعرفة كيفية عمل قواعد الحد من سطح الهجوم لاختبار القاعدة المحددة التي تواجه مشاكل معها.

1. تمكين وضع التدقيق للقاعدة المحددة التي تريد اختبارها. استخدم نهج المجموعة لتعيين القاعدة إلى وضع **التدقيق** (القيمة: **2**) كما هو موضح في [تمكين قواعد تقليل مساحة الهجوم](enable-attack-surface-reduction.md). يسمح وضع التدقيق للقاعدة ب الإبلاغ عن الملف أو العملية، ولكنه مع ذلك سيسمح بتشغيلها.

2. تنفيذ النشاط الذي يسبب مشكلة (على سبيل المثال، فتح الملف أو العملية التي يجب حظرها أو تنفيذها ولكن يتم السماح بها).

3. [راجع سجلات](attack-surface-reduction.md) أحداث قاعدة تقليل مساحة الهجوم لمعرفة ما إذا كانت القاعدة قد حظرت الملف أو العملية إذا تم تعيين القاعدة إلى **"تمكين**".

إذا كانت القاعدة لا تقوم بحظر ملف أو عملية تتوقع أن يتم حظرها، فتحقق أولا مما إذا كان وضع التدقيق قد تم تمكينه.

من الممكن أن يكون وضع التدقيق قد تم تمكينه لاختبار ميزة أخرى أو برنامج PowerShell النصي التلقائي، وربما لم يتم تعطيله بعد إكمال الاختبارات.

إذا كنت قد اختبرت القاعدة باستخدام أداة العرض التوضيحي ومع وضع التدقيق، وكانت قواعد الحد من سطح الهجوم تعمل على سيناريوهات تم تكوينها مسبقا، ولكن القاعدة لا تعمل كما هو متوقع، فاتبع أي من المقاطع التالية استنادا إلى وضعك:

1. إذا كانت قاعدة الحد من سطح الهجوم تمنع شيئا لا يجب حظره (يعرف أيضا بالإيجابية الخاطئة)، يمكنك أولا إضافة استثناء لقاعدة الحد من سطح [الهجوم](#add-exclusions-for-a-false-positive).

2. إذا كانت قاعدة الحد من سطح الهجوم لا تمنع شيئا يجب حظره (يعرف أيضا بالسلب الزائف)، يمكنك المتابعة مباشرة إلى الخطوة الأخيرة، وجمع البيانات التشخيصية وتقديم المشكلة [إلينا](#collect-diagnostic-data-for-file-submissions).

## <a name="add-exclusions-for-a-false-positive"></a>إضافة استثناءات لإيجابية خاطئة

إذا كانت قاعدة الحد من سطح الهجوم تمنع شيئا لا يجب حظره (يعرف أيضا بالإيجابية الخاطئة)، يمكنك إضافة استثناءات لمنع قواعد الحد من سطح الهجوم من تقييم الملفات أو المجلدات المستبعدة.

لإضافة استثناء، راجع [تخصيص تقليل مساحة الهجوم](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules).

> [!IMPORTANT]
> يمكنك تحديد الملفات والمجلدات الفردية التي سيتم استبعادها، ولكن لا يمكنك تحديد قواعد فردية.
> وهذا يعني أنه سيتم استبعاد أي ملفات أو مجلدات مستبعدة من جميع قواعد ASR.

## <a name="report-a-false-positive-or-false-negative"></a>الإبلاغ عن سالب موجب أو خطأ خطأ

استخدم نموذج [Windows المعلومات](https://www.microsoft.com/wdsi/filesubmission) الأمنية المستندة إلى الويب ل Defender للتقارير عن خطأ سالب أو خطأ موجبة لحماية الشبكة. باستخدام اشتراك Windows E5، يمكنك أيضا توفير [ارتباط إلى أي تنبيه مقترن](alerts-queue.md).

## <a name="collect-diagnostic-data-for-file-submissions"></a>تجميع البيانات التشخيصية لملفات الإرسال

عندما تقوم ب الإبلاغ عن مشكلة تتعلق بقواعد الحد من سطح الهجوم، سيطلب منك تجميع البيانات التشخيصية التي يمكن استخدامها بواسطة فرق الدعم والهندسة من Microsoft وإرسالها للمساعدة في استكشاف المشاكل وإصلاحها.

1. افتح موجه أوامر غير مرفأ ثم غيره إلى Windows Defender:

   ```console
   cd "c:\program files\windows defender"
   ```

2. قم بتشغيل هذا الأمر لإنشاء سجلات التشخيص:

   ```console
   mpcmdrun -getfiles
   ```

3. بشكل افتراضي، يتم حفظها في `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`. أرفق الملف ب نموذج الإرسال.

## <a name="related-articles"></a>المقالات ذات الصلة

- [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)
- [تمكين قواعد الحد من سطح الهجوم](enable-attack-surface-reduction.md)
- [تقييم قواعد الحد من سطح الهجوم](evaluate-attack-surface-reduction.md)
