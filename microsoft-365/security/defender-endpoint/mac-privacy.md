---
title: الخصوصية ل Microsoft Defender لنقطة النهاية على Mac
description: عناصر التحكم بالخصوصية، وكيفية تكوين إعدادات النهج التي تؤثر على الخصوصية ومعلومات حول البيانات التشخيصية التي يتم تجميعها في Microsoft Defender for Endpoint على Mac.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، الخصوصية، التشخيص
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
ms.openlocfilehash: c49a6ff1440c7a3eee2e26eef90fb928e68458d1
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63575785"
---
# <a name="privacy-for-microsoft-defender-for-endpoint-on-macos"></a>الخصوصية ل Microsoft Defender ل Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تلتزم Microsoft بتزويدك بالمعلومات و عناصر التحكم التي تحتاج إليها لتحديد خيارات حول كيفية تجميع البيانات واستخدامها عند استخدام Microsoft Defender ل Endpoint على macOS.

يصف هذا الموضوع عناصر التحكم بالخصوصية المتوفرة داخل المنتج، وكيفية إدارة عناصر التحكم هذه باستخدام إعدادات النهج والمزيد من التفاصيل حول أحداث البيانات التي يتم تجميعها.

## <a name="overview-of-privacy-controls-in-microsoft-defender-for-endpoint-on-macos"></a>نظرة عامة حول عناصر التحكم بالخصوصية في Microsoft Defender ل Endpoint على macOS

يصف هذا القسم عناصر التحكم بالخصوصية لأنواع البيانات المختلفة التي يجمعها Microsoft Defender ل Endpoint على macOS.

### <a name="diagnostic-data"></a>البيانات التشخيصية

يتم استخدام البيانات التشخيصية لإبقاء Microsoft Defender ل Endpoint آمنا ومحددا، والكشف عن المشاكل وتشخصها وإصلاحها، وكذلك إجراء تحسينات على المنتج.

بعض البيانات التشخيصية مطلوب، بينما البعض الآخر اختياري. ونحن نتيح لك إمكانية اختيار إرسال البيانات التشخيصية المطلوبة أو الاختيارية إلينا عبر استخدام عناصر التحكم في الخصوصية، مثل إعدادات النهج للمؤسسات.

هناك مستويان من البيانات التشخيصية الخاصة برامج عميل نقطة النهاية ل Microsoft Defender التي يمكنك الاختيار من بينها:

- **مطلوب**: الحد الأدنى من البيانات الضرورية للمساعدة في الحفاظ على أمان Microsoft Defender لنقطة النهاية، ومواكبة التحديثات، وأداءه كما هو متوقع على الجهاز المثبت عليه.

- **اختياري**: بيانات إضافية تساعد Microsoft على إجراء تحسينات على المنتج وتوفر معلومات محسنة للمساعدة في الكشف عن المشاكل وتشخصها وحلها.

بشكل افتراضي، يتم إرسال البيانات التشخيصية المطلوبة فقط إلى Microsoft.

### <a name="cloud-delivered-protection-data"></a>بيانات الحماية التي تم تسليمها في السحابة

يتم استخدام الحماية التي يتم توفيرها في السحابة لتوفير حماية أكثر سرعة مع إمكانية الوصول إلى أحدث بيانات الحماية في السحابة.

إن تمكين خدمة الحماية التي يتم تسليمها من السحابة اختياري، ومع ذلك يوصى بشدة لأنها توفر حماية هامة من البرامج الضارة على نقاط النهاية وعبر شبكتك.

### <a name="sample-data"></a>بيانات نموذجية

يتم استخدام البيانات العينة لتحسين قدرات حماية المنتج، عن طريق إرسال عينات مريبة من Microsoft حتى يمكن تحليلها. تمكين إرسال العينة التلقائي اختياري.

عند تمكين هذه الميزة، ومن المرجح أن تحتوي العينة التي يتم تجميعها على معلومات شخصية، يتم مطالبة المستخدم بالموافقة.

## <a name="manage-privacy-controls-with-policy-settings"></a>إدارة عناصر التحكم في الخصوصية باستخدام إعدادات النهج

إذا كنت مسؤولا في تكنولوجيا البيانات، فقد ترغب في تكوين عناصر التحكم هذه على مستوى المؤسسة.

يتم وصف عناصر التحكم بالخصوصية لأنواع البيانات المختلفة الموضحة في المقطع السابق بالتفصيل في تعيين تفضيلات [ل Microsoft Defender ل Endpoint على macOS](mac-preferences.md).

وكما هو حال أي إعدادات نهج جديدة، يجب اختبارها بعناية في بيئة محدودة ومتحكم بها لضمان أن يكون والإعدادات التي تقوم بتكوينها التأثير المطلوب قبل تنفيذ إعدادات النهج على نطاق أوسع في مؤسستك.

## <a name="diagnostic-data-events"></a>أحداث البيانات التشخيصية

يصف هذا القسم البيانات التشخيصية المطلوبة وما يعتبر بيانات تشخيصية اختيارية، إلى جانب وصف للأحداث والحقول التي يتم تجميعها.

### <a name="data-fields-that-are-common-for-all-events"></a>حقول البيانات الشائعة لجميع الأحداث

هناك بعض المعلومات حول الأحداث تكون شائعة لكافة الأحداث، بغض النظر عن الفئة أو نوع البيانات الفرعي.

تعتبر الحقول التالية شائعة لجميع الأحداث:

|الحقل|الوصف|
|---|---|
|النظام الأساسي|التصنيف الواسع للبرنامج الأساسي الذي يتم تشغيل التطبيق عليه. تسمح ل Microsoft بتحديد الأنظمة الأساسية التي قد تحدث فيها مشكلة ما بحيث يمكن تحديد أولوياتها بشكل صحيح.|
|machine_guid|معرف فريد مقترن بجهاز. تسمح ل Microsoft بتحديد ما إذا كانت المشاكل تؤثر على مجموعة محددة من التثبيتات وعلى عدد المستخدمين الذين يؤثرون.|
|sense_guid|معرف فريد مقترن بجهاز. تسمح ل Microsoft بتحديد ما إذا كانت المشاكل تؤثر على مجموعة محددة من التثبيتات وعلى عدد المستخدمين الذين يؤثرون.|
|org_id|معرف فريد مرتبط بالمؤسسة التي ينتمي إليها الجهاز. تسمح ل Microsoft بتحديد ما إذا كانت المشاكل تؤثر على مجموعة محددة من المؤسسات وعلى عدد المؤسسات التي تم التأثير عليها.|
|hostname|اسم الجهاز المحلي (بدون لاحقة DNS). تسمح ل Microsoft بتحديد ما إذا كانت المشاكل تؤثر على مجموعة محددة من التثبيتات وعلى عدد المستخدمين الذين يؤثرون.|
|product_guid|معرف فريد للمنتج. تسمح ل Microsoft بتمييز المشاكل التي تؤثر على مختلف أنواع المنتج.|
|app_version|إصدار Microsoft Defender ل Endpoint على تطبيق macOS. تسمح ل Microsoft بتحديد إصدارات المنتج التي تعرض مشكلة بحيث يمكن تحديد أولوياته بشكل صحيح.|
|sig_version|إصدار قاعدة بيانات معلومات الأمان. تسمح ل Microsoft بتحديد إصدارات معلومات الأمان التي تعرض مشكلة بحيث يمكن تحديد أولوياتها بشكل صحيح.|
|supported_compressions|قائمة خوارزميات الضغط التي يدعمها التطبيق، على سبيل المثال `['gzip']`. تسمح ل Microsoft بفهم أنواع الضغطات التي يمكن استخدامها عند اتصالها مع التطبيق.|
|release_ring|رنين الجهاز المقترن به (على سبيل المثال، Insider Fast، Insider Slow، الإنتاج). تسمح ل Microsoft بتحديد حلقة الإصدار التي قد تحدث فيها مشكلة بحيث يمكن تحديد أولوياتها بشكل صحيح.|

### <a name="required-diagnostic-data"></a>البيانات التشخيصية المطلوبة

**البيانات التشخيصية** المطلوبة هي الحد الأدنى من البيانات الضرورية للمساعدة في الحفاظ على أمان Microsoft Defender لنقطة النهاية، ومواكبة التحديثات، وأداءها كما هو متوقع على الجهاز الذي تم تثبيته عليه.

تساعد البيانات التشخيصية المطلوبة في تحديد المشاكل المتعلقة ب Microsoft Defender لنقطة النهاية التي قد تكون مرتبطة لتكوين جهاز أو برنامج. على سبيل المثال، يمكنها المساعدة في تحديد ما إذا كانت ميزة Microsoft Defender لنقطة النهاية تعطلت بشكل متكرر على إصدار نظام تشغيل معين أو الميزات التي تم تقديمها حديثا أو عند تعطيل بعض ميزات Microsoft Defender لنقطة النهاية. تساعد البيانات التشخيصية المطلوبة Microsoft على الكشف عن هذه المشاكل وتشخصها وإصلاحها بسرعة أكبر حتى يتم تقليل التأثير على المستخدمين أو المؤسسات.

#### <a name="software-setup-and-inventory-data-events"></a>إعداد البرامج وأحداث بيانات المخزون

**تثبيت Microsoft Defender لنقطة النهاية / إلغاء التثبيت**:

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|correlation_id|معرف فريد مقترن بالتثبيت.|
|الإصدار|إصدار الحزمة.|
|الخطورة|خطورة الرسالة (على سبيل المثال معلوماتية).|
|التعليمة البرمجية|التعليمة البرمجية التي تصف العملية.|
|نص|معلومات إضافية مقترنة ب تثبيت المنتج.|

**تكوين Microsoft Defender لنقطة النهاية**:

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|antivirus_engine.enable_real_time_protection|سواء تم تمكين الحماية في الوقت الحقيقي على الجهاز أم لا.|
|antivirus_engine.passive_mode|سواء تم تمكين الوضع السلبي على الجهاز أم لا.|
|cloud_service.enabled|سواء تم تمكين الحماية التي تم تسليمها من السحابة على الجهاز أم لا.|
|cloud_service.timeout|انتهي الوقت عندما يتصل التطبيق بسحابة Microsoft Defender لنقطة النهاية.|
|cloud_service.heartbeat_interval|الفاصل الزمني بين دقات القلب المتتالية المرسلة بواسطة المنتج إلى السحابة.|
|cloud_service.service_uri|يستخدم URI للتواصل مع السحابة.|
|cloud_service.diagnostic_level|مستوى تشخيص الجهاز (مطلوب، اختياري).|
|cloud_service.automatic_sample_submission|سواء تم تشغيل إرسال العينة التلقائية أم لا.|
|cloud_service.automatic_definition_update_enabled|سواء تم تشغيل تحديث التعريف التلقائي أم لا.|
|edr.early_preview|ما إذا كان يجب تشغيل الجهاز الكشف التلقائي والاستجابة على النقط النهائية المعاينة المبكرة أم لا.|
|edr.group_id|معرف المجموعة المستخدم بواسطة مكون الكشف والاستجابة.|
|edr.tags|العلامات المعرفة من قبل المستخدم.|
|الميزات.\[ اسم ميزة اختياري\]|قائمة بميزات المعاينة، إلى جانب تمكينها أو عدم تمكينها.|

#### <a name="product-and-service-usage-data-events"></a>أحداث بيانات استخدام الخدمات والمنتجات

**تقرير تحديث معلومات الأمان**:

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|from_version|إصدار معلومات الأمان الأصلية.|
|to_version|إصدار جديد من معلومات الأمان.|
|الحالة|حالة التحديث تشير إلى النجاح أو الفشل.|
|using_proxy|ما إذا كان قد تم التحديث عبر وكيل.|
|خطأ|رمز الخطأ إذا فشل التحديث.|
|السبب|رسالة خطأ إذا تم تحديثها.|

#### <a name="product-and-service-performance-data-events-for-required-diagnostic-data"></a>أحداث بيانات أداء المنتجات والخدمات للبيانات التشخيصية المطلوبة

**إنهاء تطبيق غير متوقع (تعطل)**:

تجمع معلومات النظام و حالة التطبيق عند خروج تطبيق بشكل غير متوقع.

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|v1_crash_count|عدد مرات تعطل عملية محرك V1 كل ساعة على جهاز العميل|
|v2_crash_count|عدد المرات التي تعطلت فيها عملية محرك V2 كل ساعة على جهاز العميل|
|EDR_crash_count|عدد المرات التي الكشف التلقائي والاستجابة على النقط النهائية فيها تعطل العملية كل ساعة على جهاز العميل|

**إحصائيات ملحقات Kernel**:

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|الإصدار|إصدار Microsoft Defender ل Endpoint على macOS.|
|instance_id|معرف فريد تم إنشاؤه على بدء تشغيل ملحق kernel.|
|trace_level|تتبع مستوى ملحق النواة.|
|النظام الفرعي|النظام الفرعي الأساسي المستخدم للحماية في الوقت الحقيقي.|
|ipc.connects|عدد طلبات الاتصال التي يتلقاها ملحق kernel.|
|ipc.rejects|عدد طلبات الاتصال التي رفضها ملحق kernel.|
|ipc.connected|ما إذا كان هناك أي اتصال نشط بامتداد kernel.|

#### <a name="support-data"></a>دعم البيانات

**سجلات التشخيص**:

يتم تجميع السجلات التشخيصية فقط بموافقة المستخدم كجزء من ميزة إرسال الملاحظات. يتم تجميع الملفات التالية كجزء من سجلات الدعم:

- كل الملفات ضمن */Library/Logs/Microsoft/mdatp/*
- مجموعة فرعية من الملفات ضمن */Library/Application Support/Microsoft/Defender/* التي تم إنشاؤها باستخدام Microsoft Defender ل Endpoint على macOS
- مجموعة فرعية من الملفات ضمن */Library/Managed Preferences* التي يستخدمها Microsoft Defender ل Endpoint على macOS
- /Library/Logs/Microsoft/autoupdate.log
- $HOME/Library/Preferences/com.microsoft.autoupdate2.plist

### <a name="optional-diagnostic-data"></a>البيانات التشخيصية الاختيارية

**البيانات التشخيصية الاختيارية** هي بيانات إضافية تساعد Microsoft على إجراء تحسينات على المنتج وتوفر معلومات محسنة للمساعدة في الكشف عن المشاكل وتشخصها وإصلاحها.

إذا اخترت إرسال البيانات التشخيصية الاختيارية إلينا، فسيتم أيضًا تضمين إلى البيانات التشخيصية المطلوبة.

تتضمن أمثلة البيانات التشخيصية الاختيارية البيانات التي تجمعها Microsoft حول تكوين المنتج (على سبيل المثال، عدد الاستثناءات التي تم تعيينها على الجهاز) وأداء المنتج (قياسات تجميعية حول أداء مكونات المنتج).

#### <a name="software-setup-and-inventory-data-events-for-optional-diagnostic-data"></a>أحداث بيانات إعداد البرامج والمخزون للبيانات التشخيصية الاختيارية

**تكوين Microsoft Defender لنقطة النهاية**:

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|connection_retry_timeout|إعادة محاولة وقت الاتصال عند الاتصال بالسحابة.|
|file_hash_cache_maximum|حجم ذاكرة التخزين المؤقت للمنتج.|
|crash_upload_daily_limit|حد سجلات الأععطل التي يتم تحميلها يوميا.|
|antivirus_engine.exclusions[].is_directory|سواء كان الاستثناء من المسح الضوئي دليل أم لا.|
|antivirus_engine.exclusions[].path|المسار الذي تم استبعاده من الفحص.|
|antivirus_engine.exclusions[].extension|الملحق مستبعد من الفحص.|
|antivirus_engine.exclusions[].name|اسم الملف الذي تم استبعاده من الفحص.|
|antivirus_engine.scan_cache_maximum|حجم ذاكرة التخزين المؤقت للمنتج.|
|antivirus_engine.maximum_scan_threads|الحد الأقصى لعدد مؤشرات الترابط المستخدمة للمسح الضوئي.|
|antivirus_engine.threat_restoration_exclusion_time|افحص الملف قبل أن يتم استعادته من الفحص مرة أخرى.|
|antivirus_engine.threat_type_settings|تكوين كيفية معالجة أنواع المخاطر المختلفة بواسطة المنتج.|
|filesystem_scanner.full_scan_directory|دليل الفحص الكامل.|
|filesystem_scanner.quick_scan_directories|قائمة الدلائل المستخدمة في الفحص السريع.|
|edr.latency_mode|وضع زمن زمن التأخر المستخدم بواسطة مكون الكشف والاستجابة.|
|edr.proxy_address|عنوان الوكيل المستخدم بواسطة مكون الكشف والاستجابة.|

**تكوين التحديث التلقائي من Microsoft**:

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|how_to_check|يحدد كيفية التحقق من تحديثات المنتجات (على سبيل المثال، تلقائي أو يدوي).|
|channel_name|تحديث القناة المقترنة بجهاز.|
|manifest_server|الخادم المستخدم لتنزيل التحديثات.|
|update_cache|موقع ذاكرة التخزين المؤقت المستخدمة لتخزين التحديثات.|

### <a name="product-and-service-usage"></a>استخدام المنتجات والخدمات

#### <a name="diagnostic-log-upload-started-report"></a>تقرير بدء تحميل السجل التشخيصي

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|sha256|معرف SHA256 لسجل الدعم.|
|الحجم|حجم سجل الدعم.|
|original_path|مسار سجل الدعم (دائما ضمن */Library/Application Support/Microsoft/Defender/wdavdiag/*).|
|تنسيق|تنسيق سجل الدعم.|
|بيانات التعريف|معلومات حول محتوى سجل الدعم.|

#### <a name="diagnostic-log-upload-completed-report"></a>تقرير مكتمل لتحميل السجل التشخيصي

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|request_id|"معرّف الارتباط" لطلب تحميل سجل الدعم.|
|sha256|معرف SHA256 لسجل الدعم.|
|blob_sas_uri|URI المستخدم بواسطة التطبيق لتحميل سجل الدعم.|

#### <a name="product-and-service-performance-data-events-for-product-and-service-usage"></a>أحداث بيانات أداء المنتجات والخدمات لاستخدام المنتجات والخدمات

**إنهاء تطبيق غير متوقع (تعطل)**:

إنهاء التطبيق بشكل غير متوقع وحالة التطبيق عند حدوث ذلك.

**إحصائيات ملحقات Kernel**:

يتم تجميع الحقول التالية:

|الحقل|الوصف|
|---|---|
|pkt_ack_timeout|الخصائص التالية هي قيم رقمية مجمعة، تمثل عدد الأحداث التي حدثت منذ بدء تشغيل ملحق kernel.|
|pkt_ack_conn_timeout||
|ipc.ack_pkts||
|ipc.nack_pkts||
|ipc.send.ack_no_conn||
|ipc.send.nack_no_conn||
|ipc.send.ack_no_qsq||
|ipc.send.nack_no_qsq||
|ipc.ack.no_space||
|ipc.ack.timeout||
|ipc.ack.ackd_fast||
|ipc.ack.ackd||
|ipc.recv.bad_pkt_len||
|ipc.recv.bad_reply_len||
|ipc.recv.no_waiter||
|ipc.recv.copy_failed||
|ipc.kauth.vnode.mask||
|ipc.kauth.vnode.read||
|ipc.kauth.vnode.write||
|ipc.kauth.vnode.exec||
|ipc.kauth.vnode.del||
|ipc.kauth.vnode.read_attr||
|ipc.kauth.vnode.write_attr||
|ipc.kauth.vnode.read_ex_attr||
|ipc.kauth.vnode.write_ex_attr||
|ipc.kauth.vnode.read_sec||
|ipc.kauth.vnode.write_sec||
|ipc.kauth.vnode.take_own||
|ipc.kauth.vnode.link||
|ipc.kauth.vnode.create||
|ipc.kauth.vnode.move||
|ipc.kauth.vnode.mount||
|ipc.kauth.vnode.denied||
|ipc.kauth.vnode.ackd_before_deadline||
|ipc.kauth.vnode.missed_deadline||
|ipc.kauth.file_op.mask||
|ipc.kauth_file_op.open||
|ipc.kauth.file_op.close||
|ipc.kauth.file_op.close_modified||
|ipc.kauth.file_op.move||
|ipc.kauth.file_op.link||
|ipc.kauth.file_op.exec||
|ipc.kauth.file_op.remove||
|ipc.kauth.file_op.unmount||
|ipc.kauth.file_op.fork||
|ipc.kauth.file_op.create||

## <a name="resources"></a>الموارد

- [الخصوصية في Microsoft](https://privacy.microsoft.com/)
