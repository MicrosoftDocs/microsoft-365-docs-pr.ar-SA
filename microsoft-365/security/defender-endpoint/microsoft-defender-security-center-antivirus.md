---
title: برنامج الحماية من الفيروسات من Microsoft Defender في أمن Windows التطبيق
description: مع برنامج الحماية من الفيروسات من Microsoft Defender الآن في تطبيق أمن Windows، يمكنك مراجعة المهام الشائعة ومقارنتها وأداءها.
keywords: wdav، الحماية من الفيروسات، جدار الحماية، الأمان، windows
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
ms.openlocfilehash: 5ad0d64ff2f296d0e8282afb02cbe7fc2bb21470
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63574250"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>برنامج الحماية من الفيروسات من Microsoft Defender في أمن Windows التطبيق

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

في Windows 10 الإصدار 1703 والإصدارات الأحدث، Windows Defender جزءا من أمن Windows.

الإعدادات دمج التطبيقات التي كانت جزءا من عميل Windows Defender Windows الإعدادات الرئيسي، ثم نقلها إلى التطبيق الجديد، الذي تم تثبيته بشكل افتراضي كجزء من Windows 10، الإصدار 1703.

> [!IMPORTANT]
> لا يعمل تعطيل أمن Windows التطبيق على تعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو [Windows Defender.](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) يتم تعطيل هذه البرامج تلقائيا عند تثبيت منتج برنامج الحماية من الفيروسات أو جدار الحماية التابع لجهات خارجية ومستمر في التحديث.
>
> إذا قمت بتعطيل خدمة تطبيق أمن Windows، أو قمت بتكوين إعدادات نهج المجموعة المقترنة بها لمنع بدء تشغيلها أو تشغيلها، فقد يعرض تطبيق أمن Windows معلومات مهترفة أو غير دقيقة حول أي من منتجات الحماية من الفيروسات أو جدار الحماية التي قمت بتثبيتها على الجهاز.
> وقد يمنع ذلك أيضا برنامج الحماية من الفيروسات من Microsoft Defender من تمكين نفسه إذا كان لديك برنامج مكافحة الفيروسات قديم أو قديم من جهة خارجية، أو إذا قمت ب إلغاء تثبيت أي منتجات برنامج الحماية من الفيروسات من جهة خارجية ربما قمت بتثبيتها مسبقا.
> سيؤدي ذلك إلى تقليل حماية جهازك بشكل ملحوظ وقد يؤدي إلى إصابة البرامج الضارة.

راجع المقالة [أمن Windows للحصول](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) على مزيد من المعلومات حول ميزات Windows الأخرى التي يمكن مراقبتها في التطبيق.

تطبيق أمن Windows هو واجهة عميل على Windows 10 الإصدار 1703 والإصدارات الأحدث. لا يتم استخدام Microsoft 365 Defender ويب لمراجعة [Microsoft Defender ل Endpoint وإدارته](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>مراجعة إعدادات الحماية من الفيروسات والتهديدات في تطبيق أمن Windows

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="إعدادات الحماية من الفيروسات والتهديدات في أمن Windows التطبيق.":::

1. افتح أمن Windows عن طريق النقر فوق أيقونة الدرع في شريط المهام أو البحث في قائمة **البدء عن أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر).

تصف الأقسام التالية كيفية تنفيذ بعض المهام الأكثر شيوعا عند مراجعة الحماية من المخاطر التي توفرها برنامج الحماية من الفيروسات من Microsoft Defender في أمن Windows التطبيق.

> [!NOTE]
> إذا تم تكوين هذه الإعدادات ونشرها باستخدام "نهج المجموعة"، ستكون الإعدادات الموضحة في هذا المقطع باللون الرمادي وغير متوفرة للاستخدام على نقاط النهاية الفردية. يجب نشر التغييرات التي يتم إدخالها من خلال "كائن نهج المجموعة" أولا على نقاط النهاية الفردية قبل أن يتم تحديث الإعداد في Windows الإعدادات. يصف [الموضوع تكوين تفاعل المستخدم مع](configure-end-user-interaction-microsoft-defender-antivirus.md) برنامج الحماية من الفيروسات من Microsoft Defender كيفية تكوين إعدادات تجاوز النهج المحلي.

## <a name="run-a-scan-with-the-windows-security-app"></a>تشغيل فحص باستخدام تطبيق أمن Windows

1. افتح أمن Windows من خلال البحث في قائمة البدء ل **الأمان**، **ثم تحديد أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر).

3. حدد **فحص سريع**. أو، لتشغيل فحص كامل **، حدد خيارات** الفحص، ثم حدد خيارا، مثل فحص **كامل**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>مراجعة إصدار تحديث معلومات الأمان وتنزيل التحديثات الأخيرة في تطبيق أمن Windows

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="رقم إصدار معلومات الأمان.":::

1. افتح أمن Windows من خلال البحث في قائمة البدء ل *الأمان*، **ثم تحديد أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر).

3. حدد **تحديثات الحماية & الفيروسات**. يتم عرض الإصدار المثبت حاليا مع بعض المعلومات حول وقت تنزيله. يمكنك التحقق من الإصدار الحالي مقابل الإصدار الأخير المتوفر للتنزيل اليدوي، أو مراجعة سجل التغيير لهذا الإصدار. راجع [تحديثات معلومات الأمان برنامج الحماية من الفيروسات من Microsoft Defender البرامج الضارة الأخرى من Microsoft](https://www.microsoft.com/wdsi/defenderupdates).

4. حدد **التحقق من وجود تحديثات** لتنزيل تحديثات الحماية الجديدة (في حال وجود أي تحديثات).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>التأكد برنامج الحماية من الفيروسات من Microsoft Defender تمكين التطبيق في أمن Windows التطبيق

1. افتح أمن Windows من خلال البحث في قائمة البدء ل *الأمان*، **ثم تحديد أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر).

3. حدد **إعدادات الحماية & الفيروسات.**

4. قم بتبديل **مفتاح الحماية** في الوقت الحقيقي إلى **تشغيل**.

    > [!NOTE]
    > إذا قمت **بتبديل الحماية في** الوقت الحقيقي، سيتم تشغيلها مرة أخرى تلقائيا بعد تأخير قصير. وذلك لضمان حمايتك من البرامج الضارة والتهديدات.
    > إذا قمت بتثبيت منتج برنامج مكافحة الفيروسات برنامج الحماية من الفيروسات من Microsoft Defender يقوم بتعطيل نفسه تلقائيا ويشار إليه على هذا النحو في أمن Windows التطبيق. سيظهر إعداد يسمح لك بتمكين [الفحص الدوري المحدود](limited-periodic-scanning-microsoft-defender-antivirus.md).

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>إضافة استثناءات برنامج الحماية من الفيروسات من Microsoft Defender في تطبيق أمن Windows

1. افتح أمن Windows من خلال البحث في قائمة البدء ل *الأمان*، **ثم تحديد أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر).

3. ضمن **إعدادات الحماية & الفيروسات،** حدد **إدارة الإعدادات**.

4. ضمن **الاستثناءات**، حدد **إضافة استثناءات أو إزالتها**.

5. حدد أيقونة علامة اضافة (**+**) لاختيار النوع، ثم قم بتعيين الخيارات لكل استثناء.

يلخص الجدول التالي أنواع الاستثناءات وما يحدث:

<br>

****
|نوع الاستثناء|معرف بواسطة|ماذا يحدث|
|---|---|---|
|**ملف**|الموقع <br/>على سبيل المثال:`c:\sample\sample.test`|يتم تخطي الملف المحدد بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.|
|**المجلد**|الموقع <br/>على سبيل المثال:`c:\test\sample`|يتم تخطي كل العناصر الموجودة في المجلد المحدد بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.|
|**نوع الملف**|ملحق الملف <br/>على سبيل المثال:`.test`|يتم تخطي جميع الملفات ذات `.test` الملحق في أي مكان على جهازك بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.|
|**معالجة**|مسار ملف قابل للتنفيذ <br>على سبيل المثال:`c:\test\process.exe`|يتم تخطي العملية المحددة وأي ملفات يتم فتحها بواسطة هذه العملية برنامج الحماية من الفيروسات من Microsoft Defender.|
|

لمعرفة المزيد، راجع الموارد التالية:

- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى ملحق الملف وموقع المجلد](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات للملفات التي يتم فتحها بواسطة العمليات](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>مراجعة محفوظات الكشف عن المخاطر في تطبيق Windows Defender for Cloud

1. افتح أمن Windows من خلال البحث في قائمة البدء ل *الأمان*، **ثم تحديد أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر).

3. حدد **محفوظات الحماية**. يتم سرد أي عناصر حديثة.

## <a name="set-ransomware-protection-and-recovery-options"></a>تعيين خيارات الحماية من برامج الفدية الضارة واستردادها

1. افتح أمن Windows من خلال البحث في قائمة البدء ل *الأمان*، **ثم تحديد أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر).

3. ضمن **الحماية من برامج الفدية الضارة**، حدد **إدارة الحماية من برامج الفدية الضارة**.

4. لتغيير إعدادات **الوصول إلى المجلدات** الخاضعة للتحكم، راجع [حماية المجلدات المهمة باستخدام الوصول إلى المجلدات الخاضعة للتحكم](/microsoft-365/security/defender-endpoint/controlled-folders).

5. لإعداد خيارات استرداد برامج الفدية الضارة، حدد  إعداد ضمن استرداد  بيانات برامج الفدية الضارة واتبع الإرشادات المتعلقة بربط حساب OneDrive الخاص بك أو إعداده حتى تتمكن من استرداده بسهولة من هجوم برامج الفدية الضارة.

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)
