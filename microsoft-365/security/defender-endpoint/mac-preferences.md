---
title: تعيين تفضيلات Microsoft Defender لنقطة النهاية على Mac
description: تكوين Microsoft Defender لنقطة النهاية على Mac في مؤسسات المؤسسة.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، الإدارة، التفضيلات، المؤسسة، intune، jamf، macos، catalina، mojave، high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ca619bbc2dd81dfe2f7de09186d748a0abb54e4c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949204"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية على macOS](microsoft-defender-endpoint-mac.md)
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> تحتوي هذه المقالة على إرشادات حول كيفية تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS في مؤسسات المؤسسة. لتكوين Microsoft Defender لنقطة النهاية على macOS باستخدام واجهة سطر الأوامر، راجع [الموارد](mac-resources.md#configuring-from-the-command-line).

## <a name="summary"></a>الملخص

في المؤسسات، يمكن إدارة Microsoft Defender لنقطة النهاية على macOS من خلال ملف تعريف تكوين يتم نشره باستخدام إحدى أدوات الإدارة المتعددة. التفضيلات التي يديرها فريق عمليات الأمان لديك لها الأسبقية على التفضيلات التي تم تعيينها محليا على الجهاز. يتطلب تغيير التفضيلات التي تم تعيينها من خلال ملف تعريف التكوين امتيازات متصاعدة وغير متوفرة للمستخدمين الذين ليس لديهم أذونات إدارية.

تصف هذه المقالة بنية ملف تعريف التكوين، وتتضمن ملف تعريف موصى به يمكنك استخدامه لبدء الاستخدام، وتوفر إرشادات حول كيفية نشر ملف التعريف.

## <a name="configuration-profile-structure"></a>بنية ملف تعريف التكوين

ملف تعريف التكوين هو ملف *plist.* يتكون من إدخالات تم تعريفها بواسطة مفتاح (يشير إلى اسم التفضيل)، متبوعا بقيمة، والتي تعتمد على طبيعة التفضيل. يمكن أن تكون القيم بسيطة (مثل قيمة رقمية) أو معقدة، مثل قائمة متداخلة من التفضيلات.

> [!CAUTION]
>يعتمد تخطيط ملف تعريف التكوين على وحدة تحكم الإدارة التي تستخدمها. تحتوي الأقسام التالية على أمثلة لملفات تعريف التكوين ل JAMF وIntune.

يتضمن المستوى الأعلى لملف تعريف التكوين تفضيلات وإدخالات على مستوى المنتج للحدود الفرعية Microsoft Defender لنقطة النهاية، والتي يتم شرحها بمزيد من التفصيل في المقاطع التالية.

### <a name="antivirus-engine-preferences"></a>تفضيلات محرك الحماية من الفيروسات

يستخدم قسم *antivirusEngine* لملف تعريف التكوين لإدارة تفضيلات مكون الحماية من الفيروسات Microsoft Defender لنقطة النهاية.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|برنامج مكافحة الفيروسات|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**تعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

#### <a name="enforcement-level-for-antivirus-engine"></a>مستوى الإنفاذ لمحرك الحماية من الفيروسات

تحديد تفضيل الإنفاذ لمحرك الحماية من الفيروسات. هناك ثلاث قيم لإعداد مستوى الإنفاذ:

- في الوقت الحقيقي (`real_time`): يتم تمكين الحماية في الوقت الحقيقي (مسح الملفات عند الوصول إليها).
- عند الطلب (`on_demand`): يتم مسح الملفات ضوئيا عند الطلب فقط. في هذا:
  - تم إيقاف تشغيل الحماية في الوقت الحقيقي.
- خامل (`passive`): تشغيل محرك الحماية من الفيروسات في الوضع السلبي. في هذا:
  - تم إيقاف تشغيل الحماية في الوقت الحقيقي.
  - يتم تشغيل المسح عند الطلب.
  - تم إيقاف تشغيل المعالجة التلقائية للمخاطر.
  - يتم تشغيل تحديثات معلومات الأمان.
  - أيقونة قائمة الحالة مخفية.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|مستوى الإنفاذ|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|real_time (افتراضي) <p> on_demand <p> السلبي|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 101.10.72 أو الإصدارات الأحدث.|
|||

#### <a name="configure-file-hash-computation-feature"></a>تكوين ميزة حساب تجزئة الملف

تمكين ميزة حساب تجزئة الملف أو تعطيلها. عند تمكين هذه الميزة، سيقوم Defender for Endpoint بحساب تجزئة الملفات التي يقوم بفحصها. لاحظ أن تمكين هذه الميزة قد يؤثر على أداء الجهاز. لمزيد من التفاصيل، يرجى الرجوع إلى: [إنشاء مؤشرات للملفات](indicator-file.md).

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|تمكينFileHashComputation|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|معطل (افتراضي) <p> تمكين|
|**تعليقات**|متوفر في إصدار Defender لنقطة النهاية 101.73.77 أو إصدار أحدث.|

#### <a name="run-a-scan-after-definitions-are-updated"></a>تشغيل فحص بعد تحديث التعريفات

تحديد ما إذا كان يجب بدء عملية فحص بعد تنزيل تحديثات جديدة لذكاء الأمان على الجهاز. سيؤدي تمكين هذا الإعداد إلى تشغيل فحص مكافحة الفيروسات على العمليات قيد التشغيل للجهاز.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|scanAfterDefinitionUpdate|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> كاذبه|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 101.41.10 أو الإصدارات الأحدث.|
|||

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>فحص الأرشيفات (عمليات مسح الحماية من الفيروسات عند الطلب فقط)

تحديد ما إذا كان يجب فحص الأرشيفات أثناء عمليات فحص الحماية من الفيروسات عند الطلب.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|الأرشفة الضوئية|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> كاذبه|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 101.41.10 أو الإصدارات الأحدث.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>درجة التوازي لإجراء عمليات الفحص عند الطلب

تحديد درجة التوازي لعمليات الفحص عند الطلب. يتوافق هذا مع عدد مؤشرات الترابط المستخدمة لإجراء الفحص ويؤثر على استخدام وحدة المعالجة المركزية، بالإضافة إلى مدة الفحص عند الطلب.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|maximumOnDemandScanThreads|
|**نوع البيانات**|صحيح|
|**القيم المحتملة**|2 (افتراضي). القيم المسموح بها هي أعداد صحيحة بين 1 و64.|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 101.41.10 أو الإصدارات الأحدث.|
|||

#### <a name="exclusion-merge-policy"></a>نهج دمج الاستبعاد

حدد نهج الدمج للاستثناءات. يمكن أن يكون هذا مزيجا من الاستثناءات المعرفة من قبل المسؤول والمعرفة من قبل المستخدم (`merge`)، أو الاستثناءات المعرفة من قبل المسؤول فقط (`admin_only`). يمكن استخدام هذا الإعداد لتقييد المستخدمين المحليين من تحديد استثناءاتهم الخاصة.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|exclusionsMergePolicy|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|دمج (افتراضي) <p> admin_only|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 100.83.73 أو الإصدارات الأحدث.|
|||

#### <a name="scan-exclusions"></a>مسح الاستثناءات

تحديد الكيانات المستبعدة من الفحص. يمكن تحديد الاستثناءات بواسطة المسارات الكاملة أو الملحقات أو أسماء الملفات.
(يتم تحديد الاستثناءات كصفيف من العناصر، ويمكن للمسؤول تحديد العديد من العناصر حسب الضرورة، بأي ترتيب.)

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|الاستبعادات|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**تعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

##### <a name="type-of-exclusion"></a>نوع الاستبعاد

حدد المحتوى المستثنى من الفحص حسب النوع.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|$type|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|||

##### <a name="path-to-excluded-content"></a>مسار المحتوى المستثنى

حدد المحتوى المستثنى من مسحه ضوئيا بواسطة مسار الملف الكامل.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|مسار|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|مسارات صالحة|
|**تعليقات**|ينطبق فقط إذا *تم* *استبعاد* $type|
|||

## <a name="supported-exclusion-types"></a>أنواع الاستبعاد المدعومة

يعرض الجدول التالي أنواع الاستبعاد التي يدعمها Defender لنقطة النهاية على Mac.

<br>

****

|الاستبعاد|تعريف|أمثلة|
|---|---|---|
|ملحق الملف|جميع الملفات ذات الملحق، في أي مكان على الجهاز|`.test`|
|ملف|ملف محدد تم تعريفه بواسطة المسار الكامل|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`|
|المجلد|كافة الملفات الموجودة ضمن المجلد المحدد (بشكل متكرر)|`/var/log/` <p> `/var/*/`|
|عمليه|عملية معينة (محددة إما بواسطة المسار الكامل أو اسم الملف) وكافة الملفات التي تم فتحها بواسطةها|`/bin/cat` <p> `cat` <p> `c?t`|
||||

> [!IMPORTANT]
> يجب أن تكون المسارات أعلاه ارتباطات ثابتة، وليست ارتباطات رمزية، لكي يتم استبعادها بنجاح. يمكنك التحقق مما إذا كان المسار ارتباطا رمزيا عن طريق التشغيل `file <path-name>`.

تدعم استثناءات الملفات والمجلدات والعمليات أحرف البدل التالية:

<br>

****

|بدل|الوصف|المثال|مباريات|غير متطابق|
|---|---|---|---|---|
|\*|يطابق أي عدد من الأحرف بما في ذلك بلا (لاحظ أنه عند استخدام حرف البدل هذا داخل مسار، فإنه سيستبدل مجلدا واحدا فقط)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`|
|?|مطابقة أي حرف مفرد|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`|
||||||

### <a name="path-type-file--directory"></a>نوع المسار (ملف / دليل)

الإشارة إلى ما إذا كانت خاصية *المسار* تشير إلى ملف أو دليل.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|isDirectory|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|خطأ (افتراضي) <p> صحيح|
|**تعليقات**|ينطبق فقط إذا *تم* *استبعاد* $type|
|||

### <a name="file-extension-excluded-from-the-scan"></a>ملحق الملف مستثنى من الفحص

حدد المحتوى المستثنى من مسحه ضوئيا بواسطة ملحق الملف.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|ملحق|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|ملحقات ملفات صالحة|
|**تعليقات**|ينطبق فقط إذا *تم استبعاد $type* *FileExtension*|
|||

### <a name="process-excluded-from-the-scan"></a>عملية مستثناة من الفحص

حدد عملية يتم استبعاد كافة أنشطة الملفات فيها من الفحص. يمكن تحديد العملية إما باسمها (على سبيل المثال، `cat`) أو المسار الكامل (على سبيل المثال، `/bin/cat`).

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|اسم|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|أي سلسلة|
|**تعليقات**|ينطبق فقط إذا *تم استبعاد $type* *FileName*|
|||

#### <a name="allowed-threats"></a>التهديدات المسموح بها

حدد التهديدات حسب الاسم التي لم يتم حظرها بواسطة Defender لنقطة النهاية على Mac. سيتم السماح بتشغيل هذه التهديدات.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|الميزات المسموح بها|
|**نوع البيانات**|صفيف من السلاسل|
|||

#### <a name="disallowed-threat-actions"></a>إجراءات التهديد غير مسموح بها

يقيد الإجراءات التي يمكن للمستخدم المحلي للجهاز اتخاذها عند اكتشاف التهديدات. لا يتم عرض الإجراءات المضمنة في هذه القائمة في واجهة المستخدم.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|عدم السماح بThreatActions|
|**نوع البيانات**|صفيف من السلاسل|
|**القيم المحتملة**|السماح (يقيد المستخدمين من السماح بالتهديدات) <p> الاستعادة (تقيد المستخدمين من استعادة التهديدات من العزل)|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 100.83.73 أو الإصدارات الأحدث.|
|||

#### <a name="threat-type-settings"></a>إعدادات نوع التهديد

حدد كيفية معالجة أنواع تهديدات معينة بواسطة Microsoft Defender لنقطة النهاية على macOS.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|threatTypeSettings|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**تعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

##### <a name="threat-type"></a>نوع التهديد

تحديد أنواع التهديدات.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|مفتاح|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|potentially_unwanted_application <p> archive_bomb|
|||

##### <a name="action-to-take"></a>الإجراء الذي يجب اتخاذه

حدد الإجراء الذي يجب اتخاذه عند الكشف عن تهديد من النوع المحدد في المقطع السابق. اختر من بين الخيارات التالية:

- **التدقيق**: جهازك غير محمي ضد هذا النوع من التهديدات، ولكن يتم تسجيل إدخال حول التهديد.
- **الحظر**: جهازك محمي ضد هذا النوع من التهديدات ويتم إعلامك في واجهة المستخدم ووحدة تحكم الأمان.
- **إيقاف التشغيل**: جهازك غير محمي ضد هذا النوع من التهديدات ولا يتم تسجيل أي شيء.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|قيمه|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|التدقيق (افتراضي) <p> كتله <p> قباله|
|||

#### <a name="threat-type-settings-merge-policy"></a>نهج دمج إعدادات نوع التهديد

حدد نهج الدمج لإعدادات نوع التهديد. يمكن أن يكون هذا مزيجا من الإعدادات المعرفة من قبل المسؤول والمعرفة من قبل المستخدم (`merge`) أو الإعدادات المعرفة من قبل المسؤول فقط (`admin_only`). يمكن استخدام هذا الإعداد لتقييد المستخدمين المحليين من تحديد الإعدادات الخاصة بهم لأنواع التهديدات المختلفة.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|threatTypeSettingsMergePolicy|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|دمج (افتراضي) <p> admin_only|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 100.83.73 أو الإصدارات الأحدث.|
|||

#### <a name="antivirus-scan-history-retention-in-days"></a>الاحتفاظ بمحفوظات فحص مكافحة الفيروسات (بالأيام)

حدد عدد الأيام التي يتم فيها الاحتفاظ بالنتائج في محفوظات الفحص على الجهاز. تتم إزالة نتائج الفحص القديمة من المحفوظات. الملفات المعزولة القديمة التي تتم إزالتها أيضا من القرص.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|scanResultsRetentionDays|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|90 (افتراضي). تتراوح القيم المسموح بها من يوم واحد إلى 180 يوما.|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 101.07.23 أو الإصدارات الأحدث.|
|||

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>الحد الأقصى لعدد العناصر في محفوظات فحص مكافحة الفيروسات

حدد الحد الأقصى لعدد الإدخالات التي يجب الاحتفاظ بها في محفوظات الفحص. تتضمن الإدخالات جميع عمليات الفحص عند الطلب التي تم إجراؤها في الماضي وجميع عمليات الكشف عن مكافحة الفيروسات.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|scanHistoryMaximumItems|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|10000 (افتراضي). تتراوح القيم المسموح بها من 5000 عنصر إلى 15000 عنصر.|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 101.07.23 أو الإصدارات الأحدث.|
|||

### <a name="cloud-delivered-protection-preferences"></a>تفضيلات الحماية المقدمة من السحابة

تكوين ميزات الحماية المستندة إلى السحابة Microsoft Defender لنقطة النهاية على macOS.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|cloudService|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**تعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

#### <a name="enable--disable-cloud-delivered-protection"></a>تمكين / تعطيل الحماية المقدمة من السحابة

حدد ما إذا كنت تريد تمكين الحماية التي توفرها السحابة للجهاز أم لا. لتحسين أمان خدماتك، نوصي بالاحتفاظ بهذه الميزة قيد التشغيل.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|تمكين|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> كاذبه|
|||

#### <a name="diagnostic-collection-level"></a>مستوى مجموعة التشخيص

يتم استخدام البيانات التشخيصية للحفاظ على أمان Microsoft Defender لنقطة النهاية وتحديثها، والكشف عن المشاكل وتشخيصها وإصلاحها، وكذلك إجراء تحسينات على المنتجات. يحدد هذا الإعداد مستوى التشخيصات المرسلة بواسطة Microsoft Defender لنقطة النهاية إلى Microsoft.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|مستوى التشخيص|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|اختياري (افتراضي) <p> مطلوب|
|||

#### <a name="configure-cloud-block-level"></a>تكوين مستوى كتلة السحابة

يحدد هذا الإعداد مدى قوة Defender لنقطة النهاية في حظر الملفات المشبوهة وفحصها. إذا كان هذا الإعداد قيد التشغيل، فسيكون Defender لنقطة النهاية أكثر صرامة عند تحديد الملفات المشبوهة لحظرها وفحصها؛ وإلا، سيكون أقل صرامة، وبالتالي حظره ومسحه ضوئيا بمعدل تردد أقل. هناك خمس قيم لإعداد مستوى كتلة السحابة:

- عادي (`normal`): مستوى الحظر الافتراضي.
- متوسط (`moderate`): يصدر الحكم فقط للكشف عن الثقة العالية.
- عال (`high`): يحظر بشدة الملفات غير المعروفة أثناء تحسين الأداء (فرصة أكبر لحظر الملفات غير الضارة).
- High Plus (`high_plus`): يحظر بشدة الملفات غير المعروفة ويطبق مقاييس حماية إضافية (قد تؤثر على أداء جهاز العميل).
- عدم التسامح مع (`zero_tolerance`): حظر كافة البرامج غير المعروفة.

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|cloudBlockLevel|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|عادي (افتراضي) <p> معتدله <p> عاليه <p> high_plus <p> zero_tolerance|
|**تعليقات**|متوفر في إصدار Defender لنقطة النهاية 101.56.62 أو إصدار أحدث.|

#### <a name="enable--disable-automatic-sample-submissions"></a>تمكين / تعطيل عمليات إرسال العينة التلقائية

تحديد ما إذا كانت العينات المشبوهة (التي من المحتمل أن تحتوي على تهديدات) يتم إرسالها إلى Microsoft. تتم مطالبتك إذا كان من المحتمل أن يحتوي الملف المرسل على معلومات شخصية.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|automaticSampleSubmission|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> كاذبه|
|||

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>تمكين / تعطيل تحديثات تحليل معلومات الأمان التلقائية

تحديد ما إذا كانت تحديثات التحليل الذكي للأمان مثبتة تلقائيا:

<br>

****

|قسم|قيمه|
|---|---|
|**المفتاح**|AutomaticDefinitionUpdateEnabled|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> كاذبه|
|||

### <a name="user-interface-preferences"></a>تفضيلات واجهة المستخدم

إدارة تفضيلات واجهة المستخدم Microsoft Defender لنقطة النهاية على macOS.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|userInterface|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**تعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

#### <a name="show--hide-status-menu-icon"></a>إظهار/ إخفاء أيقونة قائمة الحالة

حدد ما إذا كنت تريد إظهار أيقونة قائمة الحالة أو إخفاؤها في الزاوية العلوية اليسرى من الشاشة.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|إخفاءStatusMenuIcon|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|خطأ (افتراضي) <p> صحيح|
|||

#### <a name="show--hide-option-to-send-feedback"></a>إظهار/ إخفاء الخيار لإرسال الملاحظات

حدد ما إذا كان يمكن للمستخدمين إرسال ملاحظات إلى Microsoft بالانتقال إلى `Help` > `Send Feedback`.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|userInitiatedFeedback|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|ممكن (افتراضي) <p> ذوي الاحتياجات الخاصه|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 101.19.61 أو الإصدارات الأحدث.|
|||



#### <a name="control-sign-in-to-consumer-version-of-microsoft-defender"></a>التحكم في تسجيل الدخول إلى إصدار المستهلك من Microsoft Defender

حدد ما إذا كان يمكن للمستخدمين تسجيل الدخول إلى إصدار المستهلك من Microsoft Defender.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|Experience للمستهلكين|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|ممكن (افتراضي) <p> ذوي الاحتياجات الخاصه|
|**تعليقات**|متوفر في Microsoft Defender لنقطة النهاية الإصدار 101.60.18 أو الإصدارات الأحدث.|
|||


### <a name="endpoint-detection-and-response-preferences"></a>تفضيلات الكشف عن نقاط النهاية والاستجابة لها

إدارة تفضيلات مكون الكشف عن نقطة النهاية والاستجابة (EDR) Microsoft Defender لنقطة النهاية على macOS.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|يدر|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**تعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

#### <a name="device-tags"></a>علامات الجهاز

حدد اسم علامة وقيمتها.

- علامة GROUP، وضع علامة على الجهاز بالقيمة المحددة. تنعكس العلامة في المدخل ضمن صفحة الجهاز ويمكن استخدامها لأجهزة التصفية والتجميع.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|العلامات|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**تعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

##### <a name="type-of-tag"></a>نوع العلامة

تحديد نوع العلامة

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|مفتاح|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|`GROUP`|
|||

##### <a name="value-of-tag"></a>قيمة العلامة

تحديد قيمة العلامة

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|قيمه|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|أي سلسلة|
|||

> [!IMPORTANT]
>
> - يمكن تعيين قيمة واحدة فقط لكل نوع علامة.
> - نوع العلامات فريد، ويجب عدم تكراره في نفس ملف تعريف التكوين.

## <a name="recommended-configuration-profile"></a>ملف تعريف التكوين الموصى به

للبدء، نوصي بالتكوين التالي لمؤسستك للاستفادة من جميع ميزات الحماية التي يوفرها Microsoft Defender لنقطة النهاية.

ملف تعريف التكوين التالي (أو، في حالة JAMF، قائمة الخصائص التي يمكن تحميلها في ملف تعريف تكوين الإعدادات المخصصة) سوف:

- تمكين الحماية في الوقت الحقيقي (RTP)
- حدد كيفية معالجة أنواع التهديدات التالية:
  - يتم حظر **التطبيقات غير المرغوب فيها (PUA)**
  - يتم تدقيق **أرشيف المحفوظات** (ملف بمعدل ضغط عال) إلى سجلات Microsoft Defender لنقطة النهاية
- تمكين التحديثات التلقائية لذكاء الأمان
- تمكين الحماية المقدمة من السحابة
- تمكين الإرسال التلقائي للعينة

### <a name="property-list-for-jamf-recommended-configuration-profile"></a>قائمة الخصائص لملف تعريف التكوين الموصى به في JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
</dict>
</plist>
```

### <a name="intune-recommended-profile"></a>ملف التعريف الموصى به في Intune

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="full-configuration-profile-example"></a>مثال على ملف تعريف التكوين الكامل

تحتوي القوالب التالية على إدخالات لكافة الإعدادات الموضحة في هذا المستند ويمكن استخدامها لسيناريوهات أكثر تقدما حيث تريد المزيد من التحكم في Microsoft Defender لنقطة النهاية على macOS.

### <a name="property-list-for-jamf-full-configuration-profile"></a>قائمة الخصائص لملف تعريف التكوين الكامل ل JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>scanAfterDefinitionUpdate</key>
        <true/>
        <key>scanArchives</key>
        <true/>
        <key>maximumOnDemandScanThreads</key>
        <integer>2</integer>
        <key>exclusions</key>
        <array>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <false/>
                <key>path</key>
                <string>/var/log/system.log</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/home</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/Users/*/git</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileExtension</string>
                <key>extension</key>
                <string>pdf</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileName</string>
                <key>name</key>
                <string>cat</string>
            </dict>
        </array>
        <key>exclusionsMergePolicy</key>
        <string>merge</string>
        <key>allowedThreats</key>
        <array>
            <string>EICAR-Test-File (not a virus)</string>
        </array>
        <key>disallowedThreatActions</key>
        <array>
            <string>allow</string>
            <string>restore</string>
        </array>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
        <key>threatTypeSettingsMergePolicy</key>
        <string>merge</string>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>diagnosticLevel</key>
        <string>optional</string>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
    <key>edr</key>
    <dict>
        <key>tags</key>
        <array>
            <dict>
                <key>key</key>
                <string>GROUP</string>
                <key>value</key>
                <string>ExampleTag</string>
            </dict>
        </array>
    </dict>
    <key>userInterface</key>
    <dict>
        <key>hideStatusMenuIcon</key>
        <false/>
        <key>userInitiatedFeedback</key>
        <string>enabled</string>
    </dict>
</dict>
</plist>
```

### <a name="intune-full-profile"></a>ملف تعريف Intune الكامل

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>scanAfterDefinitionUpdate</key>
                    <true/>
                    <key>scanArchives</key>
                    <true/>
                    <key>maximumOnDemandScanThreads</key>
                    <integer>1</integer>
                    <key>exclusions</key>
                    <array>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <false/>
                            <key>path</key>
                            <string>/var/log/system.log</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/home</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/Users/*/git</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileExtension</string>
                            <key>extension</key>
                            <string>pdf</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileName</string>
                            <key>name</key>
                            <string>cat</string>
                        </dict>
                    </array>
                    <key>exclusionsMergePolicy</key>
                    <string>merge</string>
                    <key>allowedThreats</key>
                    <array>
                        <string>EICAR-Test-File (not a virus)</string>
                    </array>
                    <key>disallowedThreatActions</key>
                    <array>
                        <string>allow</string>
                        <string>restore</string>
                    </array>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                    <key>threatTypeSettingsMergePolicy</key>
                    <string>merge</string>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>diagnosticLevel</key>
                    <string>optional</string>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
                <key>edr</key>
                <dict>
                    <key>tags</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>GROUP</string>
                            <key>value</key>
                            <string>ExampleTag</string>
                        </dict>
                    </array>
                </dict>
                <key>userInterface</key>
                <dict>
                    <key>hideStatusMenuIcon</key>
                    <false/>
                    <key>userInitiatedFeedback</key>
                    <string>enabled</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="property-list-validation"></a>التحقق من صحة قائمة الخصائص

يجب أن تكون قائمة الخصائص ملف *.plist* صالحا. يمكن التحقق من ذلك عن طريق تنفيذ:

```bash
plutil -lint com.microsoft.wdav.plist
```

```Output
com.microsoft.wdav.plist: OK
```

إذا كان الملف منسقا بشكل جيد، يقوم الأمر أعلاه بمخرجات التعليمات `OK` البرمجية للخروج من `0`. وإلا، يتم عرض خطأ يصف المشكلة ويرجع الأمر رمز إنهاء ل `1`.

## <a name="configuration-profile-deployment"></a>نشر ملف تعريف التكوين

بمجرد إنشاء ملف تعريف التكوين لمؤسستك، يمكنك نشره من خلال وحدة تحكم الإدارة التي تستخدمها مؤسستك. توفر الأقسام التالية إرشادات حول كيفية نشر ملف التعريف هذا باستخدام JAMF وIntune.

### <a name="jamf-deployment"></a>نشر JAMF

من وحدة تحكم JAMF، افتح **"ملفات تعريف تكوين** **أجهزة الكمبيوتر**\>"، وانتقل إلى ملف تعريف التكوين الذي تريد استخدامه، ثم حدد **"إعدادات مخصصة**". إنشاء إدخال مع `com.microsoft.wdav` مجال التفضيل وتحميل قائمة *.plist* التي تم إنتاجها مسبقا.

> [!CAUTION]
> يجب إدخال مجال التفضيل الصحيح (`com.microsoft.wdav`)؛ وإلا، فلن يتم التعرف على التفضيلات بواسطة Microsoft Defender لنقطة النهاية.

### <a name="intune-deployment"></a>نشر Intune

1. فتح **تكوين إدارة** \> الجهاز. حدد **إدارة** \> **ملفات التعريف** \> **إنشاء ملف تعريف**.

2. اختر اسما لملف التعريف. تغيير **النظام الأساسي=macOS** إلى **نوع ملف التعريف=مخصص**. حدد Configure.

3. احفظ قائمة .plist التي تم إنتاجها مسبقا ك `com.microsoft.wdav.xml`.

4. أدخل `com.microsoft.wdav` **كاسم ملف تعريف التكوين المخصص**.

5. افتح ملف تعريف التكوين وحمل `com.microsoft.wdav.xml` الملف. (تم إنشاء هذا الملف في الخطوة 3.)

6. حدد **موافق**.

7. حدد **"إدارة** \> **التعيينات**". في علامة التبويب **"تضمين** "، حدد **"تعيين إلى كافة المستخدمين & كافة الأجهزة**".

> [!CAUTION]
> يجب إدخال اسم ملف تعريف التكوين المخصص الصحيح؛ وإلا، فلن يتم التعرف على هذه التفضيلات من قبل Microsoft Defender لنقطة النهاية.

## <a name="resources"></a>الموارد

- [مرجع ملف التعريف للتكوين (وثائق مطور Apple)](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
