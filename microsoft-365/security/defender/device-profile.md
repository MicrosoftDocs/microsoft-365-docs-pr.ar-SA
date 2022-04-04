---
title: ملف تعريف الجهاز في Microsoft 365 الأمان
description: عرض مستويات المخاطر والتعرض لجهاز في مؤسستك. يمكنك تحليل التهديدات السابقة والحاضرة، وحماية الجهاز باستخدام التحديثات الأخيرة.
keywords: الأمان والبرامج الضارة Microsoft 365 و M365 و Microsoft 365 Defender ومركز الأمان و Microsoft Defender ل Endpoint و Microsoft Defender ل Office 365 و Microsoft Defender for Identity وصفحة الجهاز وملف تعريف الجهاز وصفحة الجهاز وملف تعريف الجهاز
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: v-maave
author: martyav
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: eec3881d2fdb53bc03e4e730fecaf6f1c78c98c7
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755855"
---
# <a name="device-profile-page"></a>صفحة ملف تعريف الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


يوفر Microsoft 365 الأمان العام صفحات ملف تعريف الجهاز، بحيث يمكنك تقييم حالة الأجهزة على الشبكة بسرعة.

> [!IMPORTANT]
> قد تظهر صفحة ملف تعريف الجهاز مختلفة قليلا، استنادا إلى ما إذا كان الجهاز مسجلا في Microsoft Defender ل Endpoint أو Microsoft Defender for Identity أو كليهما.

إذا كان الجهاز مسجلا في Microsoft Defender ل Endpoint، يمكنك أيضا استخدام صفحة ملف تعريف الجهاز لتنفيذ بعض مهام الأمان الشائعة.

## <a name="navigating-the-device-profile-page"></a>التنقل في صفحة ملف تعريف الجهاز

يتم تقسيم صفحة ملف التعريف إلى مقاطع واسعة متعددة.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-overall.png" alt-text="صفحة ملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-overall.png":::

يسرد شريط الجانب (1) التفاصيل الأساسية حول الجهاز.

تحتوي منطقة المحتوى الرئيسي (2) على علامات تبويب يمكنك تبديلها لعرض أنواع مختلفة من المعلومات حول الجهاز.

إذا كان الجهاز مسجلا في Microsoft Defender ل Endpoint، سترى أيضا قائمة إجراءات الاستجابة (3). تسمح لك إجراءات الاستجابة بتنفيذ المهام الشائعة ذات الصلة ب الأمان.

## <a name="sidebar"></a>شريط جانبي

إلى جانب منطقة المحتوى الرئيسي لصفحة ملف تعريف الجهاز، يوجد شريط جانبي.

:::image type="content" source="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png" alt-text="علامة التبويب &quot;شريط جانبي&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png":::

يسرد شريط جانبي الاسم الكامل للجهاز ومستوى التعرض للضوء. كما يوفر أيضا بعض المعلومات الأساسية المهمة في أقسام فرعية صغيرة يمكن تبديلها مفتوحة أو مغلقة، مثل:

* **العلامات** - أي علامات Microsoft Defender ل Endpoint أو Microsoft Defender for Identity أو علامات مخصصة مقترنة بجهاز. العلامات من Microsoft Defender for Identity غير قابلة للتحرير.
* **معلومات الأمان** - فتح الأحداث والتنبيهات النشطة. ستعرض أيضا الأجهزة التي تم تسجيلها في Microsoft Defender لنقطة النهاية مستوى التعرض ومستوى المخاطر.

> [!TIP]
> يرتبط مستوى التعرض للضوء بمدى امتثال الجهاز لتوصيات الأمان، بينما يتم حساب مستوى المخاطر استنادا إلى عدد من العوامل، بما في ذلك أنواع التنبيهات النشطة ومدى خطورتها.

* **تفاصيل الجهاز** - المجال، نظام التشغيل، الوقت للوقت الذي تم فيه رؤية الجهاز للمرة الأولى وعناوين IP والموارد. تعرض الأجهزة التي تم تسجيلها في Microsoft Defender ل Endpoint حالة الصحة أيضا. ستقوم الأجهزة التي تم تسجيلها في Microsoft Defender for Identity بعرض اسم SAM وampstamp للوقت الذي تم فيه إنشاء الجهاز للمرة الأولى.
* **نشاط الشبكة** - الamps الزمنية للمرة الأولى والمرة الأخيرة التي تم فيها رؤية الجهاز على الشبكة.
* **بيانات الدليل** (فقط للأجهزة *التي تم تسجيلها في Microsoft Defender for Identity*) - أعلام [UAC](/windows/security/identity-protection/user-account-control/user-account-control-overview) و [SPNs](/windows/win32/ad/service-principal-names) وعضويات المجموعة.

## <a name="response-actions"></a>إجراءات الاستجابة

توفر إجراءات الاستجابة طريقة سريعة للدفاع عن التهديدات وتحليلها.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-long-action-bar.png" alt-text="شريط الإجراءات لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-long-action-bar.png":::

> [!IMPORTANT]
> * [تتوفر إجراءات](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) الاستجابة فقط إذا كان الجهاز مسجلا في Microsoft Defender لنقطة النهاية.
> * قد تعرض الأجهزة التي تم تسجيلها في Microsoft Defender لنقطة النهاية أعدادا مختلفة من إجراءات الاستجابة، استنادا إلى نظام تشغيل الجهاز وعدد الإصدارات.

تتضمن الإجراءات المتوفرة على صفحة ملف تعريف الجهاز ما يلي:

* **إدارة العلامات** - تحديث العلامات المخصصة التي قمت بتطبيقها على هذا الجهاز.
* **عزل الجهاز** - يعزل الجهاز عن شبكة مؤسستك مع إبقائك متصلا ب Microsoft Defender لنقطة النهاية. يمكنك اختيار السماح بتشغيل Outlook Teams و Skype for Business الجهاز أثناء عزله، لأغراض الاتصال.
* **مركز الإجراءات** - عرض حالة الإجراءات التي تم إرسالها. يتوفر فقط إذا تم تحديد إجراء آخر بالفعل.
* **تقييد تنفيذ التطبيق** - يمنع تشغيل التطبيقات التي لم يتم توقيعها بواسطة Microsoft.
* **تشغيل مسح الحماية** من الفيروسات - برنامج الحماية من الفيروسات لـ Windows Defender تعريفات البرامج وتشغيل فحص برنامج الحماية من الفيروسات على الفور. اختر من بين المسح السريع أو الفحص الكامل.
* **تجميع حزمة التحقيق** - يجمع معلومات حول الجهاز. عند اكتمال التحقيق، يمكنك تنزيله.
* **بدء جلسة الاستجابة المباشرة** - تحميل قوقعة بعيدة على الجهاز [من أجل إجراء تحقيق أمني معمق](/microsoft-365/security/defender-endpoint/live-response).
* **بدء الاستقصاء التلقائي** - يقوم تلقائيا [بالتحقق من التهديدات و إصلاحها](../office-365-security/office-365-air.md). على الرغم من أنه يمكنك تشغيل عمليات التحقيق التلقائية يدويا من هذه الصفحة، إلا أن بعض سياسات [التنبيه تقوم بتشغيل](../../compliance/alert-policies.md#default-alert-policies) عمليات التحقيق التلقائية بمفردها.
* **مركز الإجراءات** - يعرض معلومات حول أي إجراءات استجابة يتم تشغيلها حاليا.

## <a name="tabs-section"></a>مقطع علامات التبويب

تتيح لك علامات تبويب ملف تعريف الجهاز تبديل نظرة عامة حول تفاصيل الأمان حول الجهاز والجداول التي تحتوي على قائمة تنبيهات.

ستقوم الأجهزة التي تم تسجيلها في Microsoft Defender لنقطة النهاية أيضا بعرض علامات تبويب تتضمن مخططا زمنيا وقائمة بتوصيات الأمان ومخزون برامج وقائمة بالثغرات الأمنية التي تم اكتشافها وKBs المفقودة (تحديثات الأمان).

### <a name="overview-tab"></a>علامة التبويب "نظرة عامة"

علامة التبويب الافتراضية هي **نظرة عامة**. إنه يوفر نظرة سريعة على حقيقة الأمان الأكثر أهمية حول الجهاز.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-overview.png" alt-text="علامة التبويب &quot;نظرة عامة&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-overview.png":::

هنا، يمكنك الحصول على نظرة سريعة على التنبيهات النشطة للجهاز وأي مستخدمين مسجلين حاليا.

إذا كان الجهاز مسجلا في Microsoft Defender ل Endpoint، سترى أيضا مستوى مخاطر الجهاز وأي بيانات متوفرة حول تقييمات الأمان. تصف تقييمات الأمان مستوى التعرض للجهاز وتوفر توصيات الأمان وقائمة البرامج المتأثرة والنقاط المكتشفة.

### <a name="alerts-tab"></a>علامة التبويب "تنبيهات"

تحتوي **علامة التبويب** تنبيهات على قائمة بالتنبيهات التي تم رفعها على الجهاز، من كل من Microsoft Defender for Identity و Microsoft Defender for Endpoint.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-alerts.png" alt-text="علامة التبويب &quot;تنبيهات&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-alerts.png":::

يمكنك تخصيص عدد العناصر المعروضة، بالإضافة إلى الأعمدة التي يتم عرضها لكل عنصر. السلوك الافتراضي هو سرد 30 عنصر في كل صفحة.

تتضمن الأعمدة في علامة التبويب هذه معلومات حول خطورة الخطر الذي قام بتشغيل التنبيه، بالإضافة إلى الحالة، حالة التحقيق، ومن تم تعيين التنبيه له.

يشير *عمود الكيانات المتأثرة* إلى الجهاز (الكيان) الذي تعرض ملف تعريفه حاليا، بالإضافة إلى أي أجهزة أخرى متأثرة في شبكتك.

سيفتح تحديد عنصر من هذه القائمة قائمة منبهة تحتوي على مزيد من المعلومات حول التنبيه المحدد.

يمكن تصفية هذه القائمة حسب الخطورة أو الحالة أو الشخص الذي تم تعيين التنبيه له.

### <a name="timeline-tab"></a>علامة التبويب "المخطط الزمني"

تتضمن **علامة** التبويب مخطط زمني مخططا زمنيا تفاعليا لكل الأحداث التي يتم رفعها على الجهاز. من خلال نقل المنطقة التي تم تمييزها من المخطط لليسار أو لليمين، يمكنك عرض الأحداث خلال فترات زمنية مختلفة. يمكنك أيضا اختيار نطاق مخصص من التواريخ من القائمة المنسدلة بين المخطط التفاعلي وقائمة الأحداث.

يوجد أسفل المخطط قائمة بالأحداث الخاصة بمجموعة التواريخ المحددة.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-timeline.png" alt-text="علامة التبويب &quot;المخطط الزمني&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-timeline.png":::

يمكن تخصيص عدد العناصر المعروضة والأعمدة الموجودة في القائمة. سرد الأعمدة الافتراضية وقت الحدث والمستخدم النشط ونوع الإجراء والكيانات (العمليات) والمعلومات الإضافية حول الحدث.

سيفتح تحديد عنصر من هذه القائمة قائمة منفتحة تعرض رسما بيانيا لكيانات الحدث، يعرض العمليات الأصل وال التابعة المتدخلة في الحدث.

يمكن تصفية القائمة حسب نوع الحدث المحدد؛ على سبيل المثال، أحداث التسجيل أو أحداث الشاشة الذكية.

يمكن أيضا تصدير القائمة إلى ملف CSV، للتنزيل. على الرغم من أن عدد الأحداث لا يقتصر على الملف، إلا أن الحد الأقصى لنطاق الوقت الذي يمكنك اختياره لتصديره هو سبعة أيام.

### <a name="security-recommendations-tab"></a>علامة التبويب "توصيات الأمان"

**تسرد علامة التبويب توصيات** الأمان الإجراءات التي يمكنك اتخاذها لحماية الجهاز. سيفتح تحديد عنصر في هذه القائمة قائمة منبهاة حيث يمكنك الحصول على إرشادات حول كيفية تطبيق التوصية.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png" alt-text="علامة التبويب &quot;توصيات الأمان&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png":::

كما هو الأمر مع علامات التبويب السابقة، يمكن تخصيص عدد العناصر المعروضة لكل صفحة، بالإضافة إلى الأعمدة المرئية.

تتضمن طريقة العرض الافتراضية أعمدة تتضمن تفاصيل نقاط ضعف الأمان التي تم معالجتها، والتهديد المقترن به، والمكون أو البرنامج ذي الصلة المتأثر بالخطر، والمزيد. يمكن تصفية العناصر حسب حالة التوصية.

### <a name="software-inventory"></a>مخزون البرامج

**تسرد علامة تبويب** مخزون البرامج البرامج المثبتة على الجهاز.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png" alt-text="علامة التبويب &quot;مخزون البرامج&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png":::

تعرض طريقة العرض الافتراضية مورد البرنامج، رقم الإصدار المثبت، وعدد نقاط ضعف البرامج المعروفة، ورؤى المخاطر، رمز المنتج، والعلامات. يمكن تخصيص عدد العناصر المعروضة والأعمدة المعروضة.

عند تحديد عنصر من هذه القائمة، يتم فتح قائمة منفتحة تحتوي على مزيد من التفاصيل حول البرنامج المحدد، بالإضافة إلى المسار والمسار الزمني لآخر مرة تم فيها العثور على البرنامج.

يمكن تصفية هذه القائمة حسب رمز المنتج.

### <a name="discovered-vulnerabilities-tab"></a>علامة التبويب "نقاط الضعف المكتشفة"

**تسرد علامة التبويب نقاط** الضعف المكتشفة أي نقاط الضعف والمآثر الشائعة (CVEs) التي قد تؤثر على الجهاز.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png" alt-text="علامة التبويب &quot;نقاط الضعف المكتشفة&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png":::

تسرد طريقة العرض الافتراضية خطورة CVE ونقاط الضعف الشائعة (CVS) والبرامج ذات الصلة ب CVE، وعند نشر CVE، وعند آخر تحديث ل CVE، والتهديدات المقترنة ب CVE.

وكما هو الأمر مع علامات التبويب السابقة، يمكن تخصيص عدد العناصر المعروضة والأعمدة المرئية.

سيفتح تحديد عنصر من هذه القائمة قائمة منفتحة تصف CVE.

### <a name="missing-kbs"></a>KBs مفقود

**تسرد علامة التبويب KBs** المفقودة أي تحديثات Microsoft لم يتم تطبيقها بعد على الجهاز. إن "KBs" المعنية هي [مقالات قاعدة](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) المعارف التي تصف هذه التحديثات؛ على سبيل المثال [، KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG" alt-text="علامة التبويب &quot;ملفات KBs مفقودة&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG":::

تسرد طريقة العرض الافتراضية النشرة التي تحتوي على التحديثات، إصدار نظام التشغيل، المنتجات المتأثرة، CVEs التي تم تناولها، رقم KB، والعلامات.

يمكن تخصيص عدد العناصر المعروضة لكل صفحة والأعمدة التي يتم عرضها.

سيفتح تحديد عنصر قائمة منفتحة تربطها التحديث.

## <a name="related-topics"></a>المواضيع ذات الصلة

* [Microsoft 365 Defender عامة](microsoft-365-defender.md)
* [تشغيل Microsoft 365 Defender](m365d-enable.md)
* [التحقق من الكيانات على الأجهزة، باستخدام الاستجابة المباشرة](../defender-endpoint/live-response.md)
* [إجراء عمليات التحقيق والاستجابة التلقائية (AIR) في Office 365](../office-365-security/office-365-air.md)
