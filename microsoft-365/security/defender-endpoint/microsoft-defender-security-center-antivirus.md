---
title: برنامج الحماية من الفيروسات من Microsoft Defender في تطبيق أمن Windows
description: مع تضمين برنامج الحماية من الفيروسات من Microsoft Defender الآن في تطبيق أمن Windows، يمكنك مراجعة المهام الشائعة ومقارنتها وتنفيذها.
keywords: wdav، ومكافحة الفيروسات، وجدار الحماية، والأمان، والنوافذ
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: bd045ac36f1685c3bf12cedf04dd074ed6c7fc5e
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873975"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>برنامج الحماية من الفيروسات من Microsoft Defender في تطبيق أمن Windows

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

في Windows 10 والإصدار 1703 والإصدارات الأحدث، يعد تطبيق Windows Defender جزءا من أمن Windows.

تم دمج الإعدادات التي كانت في السابق جزءا من عميل Windows Defender Windows الإعدادات الرئيسية ونقلها إلى التطبيق الجديد، الذي تم تثبيته بشكل افتراضي كجزء من Windows 10، الإصدار 1703.

> [!IMPORTANT]
> لا يؤدي تعطيل خدمة تطبيق أمن Windows إلى تعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو [جدار حماية Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). يتم تعطيلها تلقائيا عند تثبيت منتج برنامج الحماية من الفيروسات أو جدار الحماية تابع لجهة خارجية وإبقاؤه محدثا.
> إذا قمت بتعطيل خدمة تطبيق أمن Windows، أو قمت بتكوين إعدادات نهج المجموعة المقترنة بها لمنع بدء تشغيلها أو تشغيلها، فقد يعرض تطبيق أمن Windows معلومات قديمة أو غير دقيقة حول أي برامج الحماية من الفيروسات أو منتجات جدار الحماية التي قمت بتثبيتها على الجهاز.
> قد يمنع أيضا برنامج الحماية من الفيروسات من Microsoft Defender من تمكين نفسه إذا كان لديك برنامج الحماية من الفيروسات قديم أو قديم تابع لجهة خارجية، أو إذا قمت بإلغاء تثبيت أي منتجات مكافحة فيروسات تابعة لجهة خارجية ربما قمت بتثبيتها مسبقا.
> سيؤدي ذلك إلى تقليل حماية جهازك بشكل كبير وقد يؤدي إلى إصابة البرامج الضارة.

راجع [المقالة أمن Windows](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) لمزيد من المعلومات حول ميزات الأمان Windows الأخرى التي يمكن مراقبتها في التطبيق.

تطبيق أمن Windows هو واجهة عميل على Windows 10، الإصدار 1703 والإصدارات الأحدث. إنه ليس مدخل ويب Microsoft 365 Defender الذي يستخدم لمراجعة [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) وإدارتها.

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>مراجعة إعدادات الحماية من الفيروسات والتهديدات في تطبيق أمن Windows

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="إعدادات الحماية من الفيروسات والتهديدات في تطبيق أمن Windows" lightbox="../../media/wdav-protection-settings-wdsc.png":::

1. افتح تطبيق أمن Windows بالنقر فوق أيقونة الدرع في شريط المهام أو البحث في قائمة البدء عن **أمن Windows**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر).

تصف الأقسام التالية كيفية تنفيذ بعض المهام الأكثر شيوعا عند مراجعة الحماية من التهديدات التي توفرها برنامج الحماية من الفيروسات من Microsoft Defender في تطبيق أمن Windows أو التفاعل معها.

> [!NOTE]
> إذا تم تكوين هذه الإعدادات ونشرها باستخدام نهج المجموعة، فستكون الإعدادات الموضحة في هذا القسم رمادية اللون وغير متوفرة للاستخدام على نقاط النهاية الفردية. يجب أولا نشر التغييرات التي تم إجراؤها من خلال كائن نهج المجموعة إلى نقاط النهاية الفردية قبل تحديث الإعداد في Windows الإعدادات. يصف تكوين [تفاعل المستخدم النهائي مع موضوع برنامج الحماية من الفيروسات من Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md) كيفية تكوين إعدادات تجاوز النهج المحلي.

## <a name="run-a-scan-with-the-windows-security-app"></a>تشغيل فحص باستخدام تطبيق أمن Windows

1. افتح تطبيق أمن Windows عن طريق البحث في قائمة البدء عن **الأمان**، ثم تحديد **أمن Windows**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر).

3. حدد **الفحص السريع**. أو، لتشغيل فحص كامل، حدد **خيارات الفحص**، ثم حدد خيارا، مثل **الفحص الكامل**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>راجع إصدار تحديث معلومات الأمان وقم بتنزيل آخر التحديثات في تطبيق أمن Windows

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="رقم إصدار معلومات الأمان" lightbox="../../media/wdav-wdsc-defs.png":::

1. افتح تطبيق أمن Windows عن طريق البحث في قائمة البدء عن *الأمان*، ثم تحديد **أمن Windows**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر).

3. حدد **تحديثات الحماية من التهديدات & الفيروسات**. يتم عرض الإصدار المثبت حاليا مع بعض المعلومات حول وقت تنزيله. يمكنك التحقق من حالتك مقابل أحدث إصدار متوفر للتنزيل اليدوي، أو مراجعة سجل التغيير لهذا الإصدار. راجع [تحديثات معلومات الأمان برنامج الحماية من الفيروسات من Microsoft Defender والبرامج الضارة الأخرى من Microsoft](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus).

4. حدد **"التحقق من وجود تحديثات** " لتنزيل تحديثات الحماية الجديدة (إن وجدت).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>تأكد من تمكين برنامج الحماية من الفيروسات من Microsoft Defender في تطبيق أمن Windows

1. افتح تطبيق أمن Windows عن طريق البحث في قائمة البدء عن *الأمان*، ثم تحديد **أمن Windows**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر).

3. حدد **إعدادات الحماية من التهديدات & الفيروسات**.

4. قم بتبديل مفتاح **الحماية في الوقت الحقيقي** إلى **تشغيل**.

    > [!NOTE]
    > إذا قمت بإيقاف تشغيل **الحماية في الوقت الحقيقي** ، فسيتم تشغيلها تلقائيا بعد تأخير قصير. هذا لضمان حمايتك من البرامج الضارة والتهديدات.
    > إذا قمت بتثبيت منتج آخر من برامج الحماية من الفيروسات، برنامج الحماية من الفيروسات من Microsoft Defender يعطل نفسه تلقائيا ويشار إليه على هذا النحو في تطبيق أمن Windows. سيظهر إعداد يسمح لك بتمكين [الفحص الدوري المحدود](limited-periodic-scanning-microsoft-defender-antivirus.md).

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>إضافة استثناءات برنامج الحماية من الفيروسات من Microsoft Defender في تطبيق أمن Windows

1. افتح تطبيق أمن Windows عن طريق البحث في قائمة البدء عن *الأمان*، ثم تحديد **أمن Windows**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر).

3. ضمن **إعدادات الحماية من الفيروسات & التهديدات**، حدد **"إدارة الإعدادات**".

4. ضمن **الاستثناءات**، حدد **إضافة استثناءات أو إزالتها**.

5. حدد أيقونة الجمع (**+**) لاختيار النوع وتعيين الخيارات لكل استثناء.

يلخص الجدول التالي أنواع الاستبعاد وما يحدث:

|نوع الاستبعاد|معرف بواسطة|ما يحدث|
|---|---|---|
|**ملف**|موقع <br/>على سبيل المثال:`c:\sample\sample.test`|يتم تخطي الملف المحدد بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.|
|**المجلد**|موقع <br/>على سبيل المثال:`c:\test\sample`|يتم تخطي كافة العناصر الموجودة في المجلد المحدد بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.|
|**نوع الملف**|ملحق الملف <br/>على سبيل المثال:`.test`|يتم تخطي جميع الملفات ذات الملحق في `.test` أي مكان على جهازك بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.|
|**عمليه**|مسار الملف القابل للتنفيذ <br>على سبيل المثال:`c:\test\process.exe`|يتم تخطي العملية المحددة وأي ملفات يتم فتحها بواسطة هذه العملية بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.|

لمعرفة المزيد، راجع الموارد التالية:

- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى ملحق الملف وموقع المجلد](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين استثناءات للملفات التي يتم فتحها بواسطة العمليات](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>مراجعة محفوظات الكشف عن التهديدات في تطبيق Windows Defender for Cloud

1. افتح تطبيق أمن Windows عن طريق البحث في قائمة البدء عن *الأمان*، ثم تحديد **أمن Windows**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر).

3. حدد **محفوظات الحماية**. يتم سرد أي عناصر حديثة.

## <a name="set-ransomware-protection-and-recovery-options"></a>تعيين خيارات الحماية من برامج الفدية الضارة واستردادها

1. افتح تطبيق أمن Windows عن طريق البحث في قائمة البدء عن *الأمان*، ثم تحديد **أمن Windows**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر).

3. ضمن **الحماية من برامج الفدية الضارة**، حدد **إدارة الحماية من برامج الفدية الضارة**.

4. لتغيير إعدادات **الوصول إلى المجلدات التي يتم التحكم فيها** ، راجع [حماية المجلدات المهمة باستخدام الوصول إلى المجلدات التي يتم التحكم فيها](/microsoft-365/security/defender-endpoint/controlled-folders).

5. لإعداد خيارات استرداد برامج الفدية الضارة، حدد **"إعداد"** ضمن **"استرداد بيانات برامج الفدية الضارة**" واتبع إرشادات ربط حساب OneDrive الخاص بك أو إعداده حتى تتمكن من التعافي بسهولة من هجوم برامج الفدية الضارة.

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)
