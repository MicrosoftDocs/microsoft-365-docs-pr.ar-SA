---
title: تعيين تفضيلات ل Microsoft Defender لنقطة النهاية على Mac
description: تكوين Microsoft Defender ل Endpoint على Mac في المؤسسات.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، الإدارة، التفضيلات، المؤسسة، intune، jamf، macos، catalina، mojave، high sierra
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
ms.openlocfilehash: cb3f38b861f85849165be330e03fe1d96a9c708c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570538"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>تعيين تفضيلات ل Microsoft Defender ل Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender ل Endpoint على macOS](microsoft-defender-endpoint-mac.md)
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> تحتوي هذه المقالة على إرشادات حول كيفية تعيين تفضيلات ل Microsoft Defender ل Endpoint على macOS في مؤسسات المؤسسة. لتكوين Microsoft Defender ل Endpoint على macOS باستخدام واجهة سطر الأوامر، راجع [الموارد](mac-resources.md#configuring-from-the-command-line).

## <a name="summary"></a>الملخص

في مؤسسات المؤسسات، يمكن إدارة Microsoft Defender ل Endpoint على macOS من خلال ملف تعريف تكوين يتم نشره باستخدام إحدى أدوات الإدارة العديدة. تكون للتفضيلات التي يديرها فريق عمليات الأمان الأسبقية على التفضيلات التي يتم تعيينها محليا على الجهاز. يتطلب تغيير التفضيلات التي تم تعيينها من خلال ملف تعريف التكوين امتيازات متصاعدة ولا تتوفر للمستخدمين الذين ليس لديهم أذونات إدارية.

تصف هذه المقالة بنية ملف تعريف التكوين، وتتضمن ملف تعريف مستحسن يمكنك استخدامه للبدء، وتوفر إرشادات حول كيفية نشر ملف التعريف.

## <a name="configuration-profile-structure"></a>بنية ملف تعريف التكوين

ملف تعريف التكوين هو ملف *plist.* يتكون من إدخالات محددة بواسطة مفتاح (يشير إلى اسم التفضيل)، متبوعا بقيمة، تعتمد على طبيعة التفضيل. يمكن أن تكون القيم بسيطة (مثل قيمة رقمية) أو معقدة، مثل قائمة متداخلة من التفضيلات.

> [!CAUTION]
>يعتمد تخطيط ملف تعريف التكوين على وحدة تحكم الإدارة التي تستخدمها. تحتوي المقاطع التالية على أمثلة لملفات تعريف التكوين ل JAMF و Intune.

يتضمن المستوى الأعلى لملف تعريف التكوين تفضيلات على مستوى المنتج وإد إدخالات للمنازل الفرعية ل Microsoft Defender لنقطة النهاية، والتي يتم شرحها بتفاصيل أكثر في الأقسام التالية.

### <a name="antivirus-engine-preferences"></a>تفضيلات مشغل برنامج الحماية من الفيروسات

يتم *استخدام قسم antivirusEngine* لملف تعريف التكوين لإدارة تفضيلات مكون الحماية من الفيروسات في Microsoft Defender ل Endpoint.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|antivirusEngine|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

#### <a name="enforcement-level-for-antivirus-engine"></a>مستوى التنفيذ لمحرك الحماية من الفيروسات

يحدد تفضيلات التنفيذ لمحرك الحماية من الفيروسات. هناك ثلاث قيم لإعداد مستوى التنفيذ:

- في الوقت الحقيقي (`real_time`): يتم تمكين الحماية في الوقت الحقيقي (مسح الملفات ضوئيا بمجرد الوصول إليها).
- عند الطلب (`on_demand`): يتم فحص الملفات عند الطلب فقط. في هذا:
  - تم إيقاف تشغيل الحماية في الوقت الحقيقي.
- غير سلبي (`passive`): يقوم بتشغيل محرك الحماية من الفيروسات في الوضع السلبي. في هذا:
  - تم إيقاف تشغيل الحماية في الوقت الحقيقي.
  - يتم تشغيل الفحص عند الطلب.
  - تم إيقاف تشغيل المعالجة التلقائية للتهديدات.
  - يتم تشغيل تحديثات معلومات الأمان.
  - أيقونة قائمة الحالة مخفية.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|enforcementLevel|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|real_time (افتراضي) <p> on_demand <p> غير سلبي|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 101.10.72 أو الإصدارات الأحدث.|
|||

#### <a name="run-a-scan-after-definitions-are-updated"></a>تشغيل فحص بعد تحديث التعريفات

يحدد ما إذا كنت تريد بدء عملية فحص بعد تنزيل تحديثات معلومات الأمان الجديدة على الجهاز. يؤدي تمكين هذا الإعداد إلى تشغيل عملية فحص برنامج الحماية من الفيروسات على عمليات تشغيل الجهاز.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|scanAfterDefinitionUpdate|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> خطأ|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 101.41.10 أو الإصدارات الأحدث.|
|||

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>فحص الأرشيفات (عمليات فحص الحماية من الفيروسات عند الطلب فقط)

يحدد ما إذا كنت تريد فحص الأرشيفات أثناء عمليات فحص الحماية من الفيروسات عند الطلب.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|scanArchives|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> خطأ|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 101.41.10 أو الإصدارات الأحدث.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>درجة التوازي لمسح عند الطلب

تحدد درجة التوازي لمسح عند الطلب. يتوافق هذا مع عدد مؤشرات الترابط المستخدمة لإجراء الفحص والتأثير على استخدام CPU، بالإضافة إلى مدة الفحص عند الطلب.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|maximumOnDemandScanThreads|
|**نوع البيانات**|عدد صحيح|
|**القيم المحتملة**|2 (افتراضي). القيم المسموح بها هي عدد صحيح بين 1 و64.|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 101.41.10 أو الإصدارات الأحدث.|
|||

#### <a name="exclusion-merge-policy"></a>نهج دمج الاستثناء

حدد نهج الدمج لالاستثناءات. يمكن أن يكون هذا مزيجا من الاستثناءات المعرفة من قبل المسؤول والاستثناءات المعرفة من قبل المستخدم (`merge`)، أو الاستثناءات المعرفة من قبل المسؤول فقط (`admin_only`). يمكن استخدام هذا الإعداد لتقييد المستخدمين المحليين من تعريف استثناءاتهم الخاصة.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|الاستثناءاتMergePolicy|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|الدمج (افتراضي) <p> admin_only|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 100.83.73 أو الإصدارات الأحدث.|
|||

#### <a name="scan-exclusions"></a>استثناءات المسح الضوئي

تحديد الكيانات المستبعدة من الفحص. يمكن تحديد الاستثناءات بواسطة المسارات الكاملة أو الملحقات أو أسماء الملفات.
(يتم تحديد الاستثناءات كصفيف من العناصر، يمكن للمسؤول تحديد العدد اللازم من العناصر، بأي ترتيب.)

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|الاستثناءات|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

##### <a name="type-of-exclusion"></a>نوع الاستثناء

حدد المحتوى الذي تم استبعاده من أن يتم فحصه حسب النوع.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|$type|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|||

##### <a name="path-to-excluded-content"></a>المسار إلى المحتوى المستبعد

حدد المحتوى الذي تم استبعاده من أن يتم فحصه بواسطة مسار الملف الكامل.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|مسار|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|مسارات صالحة|
|**التعليقات**|ينطبق فقط *إذا* $type *Path*|
|||

## <a name="supported-exclusion-types"></a>أنواع الاستثناءات المعتمدة

يعرض الجدول التالي أنواع الاستثناءات التي يدعمها Defender for Endpoint على Mac.

<br>

****

|الاستثناء|التعريف|أمثلة|
|---|---|---|
|ملحق الملف|جميع الملفات ذات الملحق، في أي مكان على الجهاز|`.test`|
|ملف|ملف معين تم تعريفه بواسطة المسار الكامل|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`|
|المجلد|كل الملفات الموجودة ضمن المجلد المحدد (بشكل تكراري)|`/var/log/` <p> `/var/*/`|
|معالجة|عملية معينة (محددة بواسطة المسار الكامل أو اسم الملف) وجميع الملفات التي يتم فتحها بواسطة|`/bin/cat` <p> `cat` <p> `c?t`|
||||

> [!IMPORTANT]
> يجب أن تكون المسارات أعلاه ارتباطات صعبة، وليس ارتباطات رمزية، لكي يتم استبعادها بنجاح. يمكنك التحقق مما إذا كان المسار هو ارتباط رمزي عن طريق تشغيل `file <path-name>`.

تدعم استثناءات الملفات والمجلدات و العملية أحرف البدل التالية:

<br>

****

|أحرف البدل|الوصف|مثال|تطابقات|غير متطابق|
|---|---|---|---|---|
|\*|يطابق أي عدد من الأحرف بما في ذلك بلا (لاحظ أنه عند استخدام حرف البدل هذا داخل مسار سيستبدل مجلدا واحدا فقط)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`|
|?|يطابق أي حرف مفرد|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`|
||||||

### <a name="path-type-file--directory"></a>نوع المسار (ملف / دليل)

الإشارة إلى *ما إذا كانت خاصية* المسار تشير إلى ملف أو دليل.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|isDirectory|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|خطأ (افتراضي) <p> true|
|**التعليقات**|ينطبق فقط *إذا* $type *Path*|
|||

### <a name="file-extension-excluded-from-the-scan"></a>ملحق الملف مستبعد من الفحص

حدد المحتوى المستبعد من أن يتم مسحه ضوئيا بواسطة ملحق الملف.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|ملحق|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|ملحقات الملفات الصحيحة|
|**التعليقات**|ينطبق فقط *$type* *تم استبعادFileExtension*|
|||

### <a name="process-excluded-from-the-scan"></a>معالجة مستبعدة من الفحص

حدد عملية يتم فيها استبعاد كل نشاط الملف من الفحص. يمكن تحديد العملية إما باسمها ( `cat`على سبيل المثال، ) أو المسار الكامل (على سبيل المثال، `/bin/cat`).

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|الاسم|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|أي سلسلة|
|**التعليقات**|ينطبق فقط *$type* *تم استبعادFileName*|
|||

#### <a name="allowed-threats"></a>التهديدات المسموح بها

حدد التهديدات حسب الاسم التي لم يتم حظرها بواسطة Defender for Endpoint على Mac. سيتم السماح بتشغيل هذه التهديدات.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|allowedThreats|
|**نوع البيانات**|صفيف من السلاسل|
|||

#### <a name="disallowed-threat-actions"></a>إجراءات التهديد غير مسموح بها

تقييد الإجراءات التي يمكن أن يتخذها المستخدم المحلي للجهاز عند اكتشاف التهديدات. لا يتم عرض الإجراءات المضمنة في هذه القائمة في واجهة المستخدم.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|disallowedThreatActions|
|**نوع البيانات**|صفيف من السلاسل|
|**القيم المحتملة**|السماح (يمنع المستخدمين من السماح للتهديدات) <p> استعادة (تقيد المستخدمين من استعادة التهديدات من الفحص)|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 100.83.73 أو الإصدارات الأحدث.|
|||

#### <a name="threat-type-settings"></a>إعدادات نوع التهديدات

حدد كيفية معالجة أنواع معينة من التهديدات بواسطة Microsoft Defender ل Endpoint على macOS.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|threatTypeSettings|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

##### <a name="threat-type"></a>نوع التهديد

تحديد أنواع التهديدات.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|مفتاح|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|potentially_unwanted_application <p> archive_bomb|
|||

##### <a name="action-to-take"></a>الإجراء الذي يجب اتخاذه

حدد الإجراء الذي يجب اتخاذه عند الكشف عن خطر من النوع المحدد في المقطع السابق. اختر من الخيارات التالية:

- **التدقيق**: جهازك غير محمي من هذا النوع من التهديدات، ولكن يتم تسجيل إدخال حول هذا الخطر.
- **الحظر**: جهازك محمي ضد هذا النوع من التهديدات، كما يتم إعلامك في واجهة المستخدم ووحدة التحكم في الأمان.
- **إيقاف** التشغيل: جهازك غير محمي من هذا النوع من التهديدات ولا يتم تسجيل أي شيء.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|قيمة|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|التدقيق (افتراضي) <p> حظر <p> إيقاف التشغيل|
|||

#### <a name="threat-type-settings-merge-policy"></a>نهج دمج إعدادات نوع التهديدات

حدد نهج الدمج لإعدادات نوع التهديدات. يمكن أن يكون هذا مزيجا من الإعدادات المعرفة من قبل المسؤول والإعدادات المعرفة من قبل المستخدم (`merge`) أو الإعدادات المعرفة من قبل المسؤول فقط (`admin_only`). يمكن استخدام هذا الإعداد لتقييد المستخدمين المحليين من تعريف الإعدادات الخاصة بهم لأنواع التهديدات المختلفة.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|threatTypeSettingsMergePolicy|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|الدمج (افتراضي) <p> admin_only|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 100.83.73 أو الإصدارات الأحدث.|
|||

#### <a name="antivirus-scan-history-retention-in-days"></a>استبقاء محفوظات مسح الفيروسات (خلال أيام)

حدد عدد الأيام التي يتم فيها الاحتفاظ بالنتائج في محفوظات الفحص على الجهاز. تتم إزالة نتائج الفحص القديمة من المحفوظات. الملفات القديمة التي تم فحصها والمزالة أيضا من القرص.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|scanResultsRetentionDays|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|90 (افتراضي). القيم المسموح بها من يوم واحد إلى 180 يوما.|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 101.07.23 أو الإصدارات الأحدث.|
|||

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>الحد الأقصى لعدد العناصر في محفوظات مسح الفيروسات

حدد الحد الأقصى لعدد الإدخالات التي يجب الاحتفاظ بها في محفوظات الفحص. تتضمن الإدخالات جميع عمليات الفحص عند الطلب التي تم تنفيذها في الماضي وجميع عمليات الكشف عن الفيروسات.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|scanHistoryMaximumItems|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|10000 (افتراضي). القيم المسموح بها من 5000 عنصر إلى 15000 عنصر.|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 101.07.23 أو الإصدارات الأحدث.|
|||

### <a name="cloud-delivered-protection-preferences"></a>تفضيلات الحماية التي يتم تسليمها من السحابة

تكوين ميزات الحماية المستندة إلى السحابة من Microsoft Defender ل Endpoint على macOS.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|cloudService|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

#### <a name="enable--disable-cloud-delivered-protection"></a>تمكين / تعطيل الحماية التي يتم تسليمها من السحابة

حدد ما إذا كنت تريد تمكين الحماية التي يتم تسليمها من السحابة للجهاز أم لا. لتحسين أمان خدماتك، نوصي بإبقاء هذه الميزة في وضع تشغيل.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|تم التمكين|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> خطأ|
|||

#### <a name="diagnostic-collection-level"></a>مستوى المجموعة التشخيصية

يتم استخدام البيانات التشخيصية لإبقاء Microsoft Defender ل Endpoint آمنا ومحددا، والكشف عن المشاكل وتشخصها وإصلاحها، وكذلك إجراء تحسينات على المنتج. يحدد هذا الإعداد مستوى التشخيصات المرسلة بواسطة Microsoft Defender ل Endpoint إلى Microsoft.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|diagnosticLevel|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|اختياري (افتراضي) <p> مطلوب|
|||

#### <a name="enable--disable-automatic-sample-submissions"></a>تمكين / تعطيل عمليات الإرسال التلقائية العينة

يحدد ما إذا كانت العينات المريبة (التي من المرجح أن تحتوي على تهديدات) مرسلة إلى Microsoft. وستطالب إذا كان الملف الذي تم إرساله يحتوي على معلومات شخصية.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|automaticSampleSubmission|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> خطأ|
|||

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>تمكين / تعطيل تحديثات معلومات الأمان التلقائية

يحدد ما إذا كانت تحديثات معلومات الأمان مثبتة تلقائيا:

<br>

****

|مقطع|القيمة|
|---|---|
|**المفتاح**|automaticDefinitionUpdateEnabled|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|true (افتراضي) <p> خطأ|
|||

### <a name="user-interface-preferences"></a>تفضيلات واجهة المستخدم

يمكنك إدارة تفضيلات واجهة مستخدم Microsoft Defender ل Endpoint على macOS.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|userInterface|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

#### <a name="show--hide-status-menu-icon"></a>إظهار / إخفاء أيقونة قائمة الحالة

حدد ما إذا كنت تريد إظهار أيقونة قائمة الحالة أو إخفائها في الزاوية العلوية اليسرى من الشاشة.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|إخفاءStatusMenuIcon|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|خطأ (افتراضي) <p> true|
|||

#### <a name="show--hide-option-to-send-feedback"></a>إظهار /إخفاء الخيار لإرسال الملاحظات

حدد ما إذا كان يمكن للمستخدمين إرسال ملاحظات إلى Microsoft عن طريق الذهاب إلى `Help` > `Send Feedback`.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|userInitiatedFeedback|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|تم التمكين (افتراضي) <p> معطل|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 101.19.61 أو الإصدارات الأحدث.|
|||



#### <a name="control-sign-in-to-consumer-version-of-microsoft-defender"></a>التحكم في إصدار تسجيل الدخول إلى المستهلك من Microsoft Defender

حدد ما إذا كان يمكن للمستخدمين تسجيل الدخول إلى إصدار المستهلك من Microsoft Defender.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|consumerExperience|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|تم التمكين (افتراضي) <p> معطل|
|**التعليقات**|متوفر في Microsoft Defender للإصدار 101.60.18 أو الإصدارات الأحدث.|
|||


### <a name="endpoint-detection-and-response-preferences"></a>تفضيلات الاستجابة والكشف عن نقطة النهاية

يمكنك إدارة تفضيلات مكون الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية) من Microsoft Defender ل Endpoint على macOS.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|edr|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

#### <a name="device-tags"></a>علامات الجهاز

تحديد اسم علامة وقيمتها.

- علامة GROUP، وضع علامة على الجهاز بالقيمة المحددة. تنعكس العلامة في المدخل ضمن صفحة الجهاز ويمكن استخدامها لتصفية الأجهزة وت تجميعها.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|العلامات|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|||

##### <a name="type-of-tag"></a>نوع العلامة

تحديد نوع العلامة

<br>

****

|مقطع|القيمة|
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

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|قيمة|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|أي سلسلة|
|||

> [!IMPORTANT]
>
> - يمكن تعيين قيمة واحدة فقط لكل نوع علامة.
> - نوع العلامات فريد، ويجب عدم تكراره في ملف تعريف التكوين نفسه.

## <a name="recommended-configuration-profile"></a>ملف تعريف التكوين المستحسن

للبدء، نوصي بإجراء التكوين التالي لمؤسستك للاستفادة من جميع ميزات الحماية التي يوفرها Microsoft Defender ل Endpoint.

ملف تعريف التكوين التالي (أو، في حالة JAMF، قائمة بممتلكات يمكن تحميلها إلى ملف تعريف تكوين الإعدادات المخصصة) سوف:

- تمكين الحماية في الوقت الحقيقي (RTP)
- حدد كيفية التعامل مع أنواع التهديدات التالية:
  - **يتم حظر التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA)**
  - **أرشفة المحفوظات** (ملف بمعدل ضغط عال) يتم تدقيقها في سجلات نقطة النهاية ل Microsoft Defender
- تمكين التحديثات التلقائية لذكاء الأمان
- تمكين الحماية التي يتم تسليمها من السحابة
- تمكين الإرسال النموذجي التلقائي

### <a name="property-list-for-jamf-recommended-configuration-profile"></a>قائمة الخاصية لملف تعريف التكوين المستحسن JAMF

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

### <a name="intune-recommended-profile"></a>ملف تعريف Intune الموصى به

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

## <a name="full-configuration-profile-example"></a>مثال لملف تعريف التكوين الكامل

تحتوي القوالب التالية على إدخالات لكل الإعدادات الموضحة في هذا المستند ويمكن استخدامها لسيناريوهات أكثر تقدما حيث تريد التحكم بشكل أكبر في Microsoft Defender ل Endpoint على macOS.

### <a name="property-list-for-jamf-full-configuration-profile"></a>قائمة الخاصية لملف تعريف التكوين الكامل ل JAMF

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

## <a name="property-list-validation"></a>التحقق من صحة قائمة الممتلكات

يجب أن تكون قائمة الخاصية ملف *plist.* صالحا. يمكن التحقق من ذلك عن طريق تنفيذ:

```bash
plutil -lint com.microsoft.wdav.plist
```

```Output
com.microsoft.wdav.plist: OK
```

إذا كان الملف مشكلا بشكل جيد `OK` ، فيخرج الأمر أعلاه ويرجع رمز الخروج الخاص ب `0`. وبخلاف ذلك، يتم عرض خطأ يصف المشكلة ويرجع الأمر رمز الخروج ل `1`.

## <a name="configuration-profile-deployment"></a>نشر ملف تعريف التكوين

بعد إنشاء ملف تعريف التكوين لمؤسستك، يمكنك نشره من خلال وحدة تحكم الإدارة التي تستخدمها المؤسسة. توفر الأقسام التالية إرشادات حول كيفية نشر ملف التعريف هذا باستخدام JAMF و Intune.

### <a name="jamf-deployment"></a>نشر JAMF

من وحدة تحكم JAMF  \>، افتح ملفات تعريف تكوين أجهزة الكمبيوتر، وانتقل إلى ملف تعريف التكوين الذي تريد استخدامه، ثم حدد **ملفات تعريف مخصصة الإعدادات**. قم بإنشاء إدخال باستخدام `com.microsoft.wdav` مجال التفضيل وتحميل *.plist* الذي تم إنتاجه سابقا.

> [!CAUTION]
> يجب إدخال مجال التفضيل الصحيح (`com.microsoft.wdav`)؛ وإلا، لن يتم التعرف على التفضيلات بواسطة Microsoft Defender ل Endpoint.

### <a name="intune-deployment"></a>نشر Intune

1. افتح **تكوين** \> **إدارة الجهاز**. حدد **إدارة ملفات** \> **التعريف** \> **إنشاء ملف تعريف**.

2. اختر اسما لملف التعريف. تغيير **Platform=macOS** إلى **Profile type=Custom**. حدد تكوين.

3. احفظ .plist الذي تم إنتاجه سابقا ك `com.microsoft.wdav.xml`.

4. أدخل `com.microsoft.wdav` باسم **ملف تعريف التكوين المخصص**.

5. افتح ملف تعريف التكوين ثم قم بتحميل `com.microsoft.wdav.xml` الملف. (تم إنشاء هذا الملف في الخطوة 3.)

6. حدد **موافق**.

7. حدد **إدارة** \> **الواجبات**. في علامة **التبويب تضمين** ، حدد **تعيين إلى كل** المستخدمين & كافة الأجهزة.

> [!CAUTION]
> يجب إدخال اسم ملف تعريف التكوين المخصص الصحيح؛ وإلا، فإن Microsoft Defender لنقطة النهاية لن يتعرف على هذه التفضيلات.

## <a name="resources"></a>الموارد

- [مرجع ملف التعريف للتكوين (وثائق مطور Apple)](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
