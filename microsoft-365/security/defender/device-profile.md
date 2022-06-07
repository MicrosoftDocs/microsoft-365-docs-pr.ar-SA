---
title: ملف تعريف الجهاز في مدخل أمان Microsoft 365
description: عرض مستويات المخاطر والتعرض لجهاز في مؤسستك. تحليل التهديدات السابقة والحاضرة، وحماية الجهاز بآخر التحديثات.
keywords: الأمان والبرامج الضارة وMicrosoft 365 وM365 وMicrosoft 365 Defender ومركز الأمان وMicrosoft Defender لنقطة النهاية وMicrosoft Defender ل Office 365 وMicrosoft Defender for Identity وصفحة الجهاز وملف تعريف الجهاز وصفحة الجهاز وملف تعريف الجهاز
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: dansimp
author: martyav
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 962ec0c5ed6b7d6934678678be9a57ebcbaabc55
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923423"
---
# <a name="device-profile-page"></a>صفحة ملف تعريف الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


يوفر لك مدخل أمان Microsoft 365 صفحات ملف تعريف الجهاز، حتى تتمكن من تقييم حالة الأجهزة وحالتها بسرعة على شبكتك.

> [!IMPORTANT]
> قد تظهر صفحة ملف تعريف الجهاز مختلفة قليلا، اعتمادا على ما إذا كان الجهاز مسجلا في Microsoft Defender لنقطة النهاية أو Microsoft Defender for Identity أو كليهما.

إذا كان الجهاز مسجلا في Microsoft Defender لنقطة النهاية، يمكنك أيضا استخدام صفحة ملف تعريف الجهاز لتنفيذ بعض مهام الأمان الشائعة.

## <a name="navigating-the-device-profile-page"></a>التنقل في صفحة ملف تعريف الجهاز

يتم تقسيم صفحة ملف التعريف إلى عدة أقسام واسعة.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-overall.png" alt-text="صفحة ملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-overall.png":::

يسرد الشريط الجانبي (1) التفاصيل الأساسية حول الجهاز.

تحتوي منطقة المحتوى الرئيسي (2) على علامات تبويب يمكنك التبديل إليها لعرض أنواع مختلفة من المعلومات حول الجهاز.

إذا كان الجهاز مسجلا في Microsoft Defender لنقطة النهاية، فسترى أيضا قائمة بإجراءات الاستجابة (3). تسمح لك إجراءات الاستجابة بتنفيذ المهام الشائعة المتعلقة بالأمان.

## <a name="sidebar"></a>الشريط الجانبي

يوجد الشريط الجانبي بجانب منطقة المحتوى الرئيسية لصفحة ملف تعريف الجهاز.

:::image type="content" source="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png" alt-text="علامة تبويب الشريط الجانبي لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png":::

يسرد الشريط الجانبي الاسم الكامل للجهاز ومستوى التعرض له. كما يوفر بعض المعلومات الأساسية الهامة في الأقسام الفرعية الصغيرة التي يمكن تبديلها مفتوحة أو مغلقة، مثل:

* **العلامات** - أي Microsoft Defender لنقطة النهاية أو Microsoft Defender for Identity أو علامات مخصصة مقترنة بالجهاز. العلامات من Microsoft Defender for Identity غير قابلة للتحرير.
* **معلومات الأمان** - فتح الحوادث والتنبيهات النشطة. ستعرض الأجهزة المسجلة في Microsoft Defender لنقطة النهاية أيضا مستوى التعرض ومستوى المخاطر.

> [!TIP]
> يتعلق مستوى التعرض بالمقدار الذي يمتثل فيه الجهاز لتوصيات الأمان، بينما يتم حساب مستوى المخاطر استنادا إلى عدد من العوامل، بما في ذلك أنواع التنبيهات النشطة وشدتها.

* **تفاصيل الجهاز** - المجال ونظام التشغيل والطوابع الزمنية لوقت ظهور الجهاز لأول مرة وعناوين IP والموارد. كما تعرض الأجهزة المسجلة في Microsoft Defender لنقطة النهاية حالة السلامة. ستعرض الأجهزة المسجلة في Microsoft Defender for Identity اسم SAM وطوبة زمنية لوقت إنشاء الجهاز لأول مرة.
* **نشاط الشبكة** - الطوابع الزمنية لأول مرة وآخر مرة تم فيها رؤية الجهاز على الشبكة.
* **بيانات الدليل** (*فقط للأجهزة المسجلة في Microsoft Defender for Identity*) - علامات [UAC](/windows/security/identity-protection/user-account-control/user-account-control-overview) و [SPNs](/windows/win32/ad/service-principal-names) وعضوية المجموعة.

## <a name="response-actions"></a>إجراءات الاستجابة

توفر إجراءات الاستجابة طريقة سريعة للدفاع ضد التهديدات وتحليلها.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-long-action-bar.png" alt-text="شريط الإجراءات لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-long-action-bar.png":::

> [!IMPORTANT]
> * لا تتوفر [إجراءات الاستجابة](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) إلا إذا كان الجهاز مسجلا في Microsoft Defender لنقطة النهاية.
> * قد تعرض الأجهزة المسجلة في Microsoft Defender لنقطة النهاية أعدادا مختلفة من إجراءات الاستجابة، استنادا إلى نظام التشغيل ورقم الإصدار الخاص بالجهاز.

تتضمن الإجراءات المتوفرة على صفحة ملف تعريف الجهاز ما يلي:

* **إدارة العلامات** - تحديث العلامات المخصصة التي قمت بتطبيقها على هذا الجهاز.
* **عزل الجهاز** - عزل الجهاز عن شبكة مؤسستك مع الاحتفاظ به متصلا ب Microsoft Defender لنقطة النهاية. يمكنك اختيار السماح بتشغيل Outlook وTeams وSkype for Business أثناء عزل الجهاز لأغراض الاتصال.
* **مركز الصيانة** - عرض حالة الإجراءات المرسلة. متوفر فقط إذا تم تحديد إجراء آخر بالفعل.
* **تقييد تنفيذ التطبيق** - يمنع تشغيل التطبيقات التي لم يتم توقيعها من قبل Microsoft.
* **تشغيل فحص مكافحة الفيروسات** - تحديث تعريفات برنامج الحماية من الفيروسات ل Windows Defender وتشغيل فحص مكافحة الفيروسات على الفور. الاختيار بين الفحص السريع أو الفحص الكامل.
* **تجميع حزمة التحقيق** - جمع معلومات حول الجهاز. عند اكتمال التحقيق، يمكنك تنزيله.
* **بدء جلسة الاستجابة المباشرة** - تحميل shell بعيد على الجهاز [لإجراء تحقيقات أمنية متعمقة](/microsoft-365/security/defender-endpoint/live-response).
* **بدء التحقيق التلقائي** - التحقيق تلقائيا [في التهديدات ومعالجتها](../office-365-security/office-365-air.md). على الرغم من أنه يمكنك تشغيل التحقيقات التلقائية يدويا لتشغيلها من هذه الصفحة، فإن [بعض نهج التنبيه](../../compliance/alert-policies.md#default-alert-policies) تشغل التحقيقات التلقائية من تلقاء نفسها.
* **مركز الصيانة** - يعرض معلومات حول أي إجراءات استجابة قيد التشغيل حاليا.

## <a name="tabs-section"></a>مقطع علامات التبويب

تسمح لك علامات تبويب ملف تعريف الجهاز بالتبديل من خلال نظرة عامة حول تفاصيل الأمان حول الجهاز والجداول التي تحتوي على قائمة من التنبيهات.

ستعرض الأجهزة المسجلة في Microsoft Defender لنقطة النهاية أيضا علامات تبويب تتضمن مخططا زمنيا وقائمة بتوصيات الأمان ومخزون برامج وقائمة بالثغرات الأمنية المكتشفة وKBs المفقودة (تحديثات الأمان).

### <a name="overview-tab"></a>علامة التبويب "نظرة عامة"

علامة التبويب الافتراضية هي **"نظرة عامة**". يوفر نظرة سريعة على أهم حقيقة أمنية حول الجهاز.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-overview.png" alt-text="علامة التبويب &quot;نظرة عامة&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-overview.png":::

هنا، يمكنك الحصول على نظرة سريعة على التنبيهات النشطة للجهاز، وأي مستخدمين تم تسجيل دخولهم حاليا.

إذا كان الجهاز مسجلا في Microsoft Defender لنقطة النهاية، فسترى أيضا مستوى مخاطر الجهاز وأي بيانات متوفرة في تقييمات الأمان. تصف تقييمات الأمان مستوى تعرض الجهاز، وتوفر توصيات أمنية، وتدرج البرامج المتأثرة والثغرات الأمنية المكتشفة.

### <a name="alerts-tab"></a>علامة التبويب "تنبيهات"

تحتوي علامة التبويب **Alerts** على قائمة بالتنبيهات التي تم رفعها على الجهاز، من كل من Microsoft Defender for Identity وMicrosoft Defender لنقطة النهاية.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-alerts.png" alt-text="علامة التبويب &quot;تنبيهات&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-alerts.png":::

يمكنك تخصيص عدد العناصر المعروضة، بالإضافة إلى الأعمدة التي يتم عرضها لكل عنصر. السلوك الافتراضي هو سرد 30 عنصرا لكل صفحة.

تتضمن الأعمدة في علامة التبويب هذه معلومات حول خطورة التهديد الذي أدى إلى التنبيه، بالإضافة إلى الحالة وحالة التحقيق والأشخاص الذين تم تعيين التنبيه إليهم.

يشير عمود *الكيانات المتأثرة* إلى الجهاز (الكيان) الذي تعرض ملف تعريفه حاليا، بالإضافة إلى أي أجهزة أخرى في شبكتك تتأثر.

سيؤدي تحديد عنصر من هذه القائمة إلى فتح قائمة منبثقة تحتوي على مزيد من المعلومات حول التنبيه المحدد.

يمكن تصفية هذه القائمة حسب الخطورة أو الحالة أو الأشخاص الذين تم تعيين التنبيه إليهم.

### <a name="timeline-tab"></a>علامة التبويب "خط زمني"

تتضمن علامة التبويب **"الخط الزمني** " مخططا تفاعليا زمنيا لكافة الأحداث التي تم رفعها على الجهاز. من خلال نقل المنطقة المميزة من المخطط لليسار أو لليمين، يمكنك عرض الأحداث على مدى فترات زمنية مختلفة. يمكنك أيضا اختيار نطاق مخصص من التواريخ من القائمة المنسدلة بين المخطط التفاعلي وقائمة الأحداث.

توجد أسفل المخطط قائمة بالأحداث لنطاق التواريخ المحدد.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-timeline.png" alt-text="علامة التبويب &quot;الخط الزمني&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-timeline.png":::

يمكن تخصيص عدد العناصر المعروضة والأعمدة في القائمة. تسرد الأعمدة الافتراضية وقت الحدث والمستخدم النشط ونوع الإجراء والكيانات (العمليات) ومعلومات إضافية حول الحدث.

سيؤدي تحديد عنصر من هذه القائمة إلى فتح قائمة منبثقة تعرض رسما بيانيا لكيانات الحدث، يعرض العمليات الأصل والتابعة المتضمنة في الحدث.

يمكن تصفية القائمة حسب نوع الحدث المحدد؛ على سبيل المثال، أحداث التسجيل أو أحداث الشاشة الذكية.

يمكن أيضا تصدير القائمة إلى ملف CSV، للتنزيل. على الرغم من أن الملف لا يقتصر على عدد الأحداث، فإن الحد الأقصى للنطاق الزمني الذي يمكنك اختيار تصديره هو سبعة أيام.

### <a name="security-recommendations-tab"></a>علامة التبويب "توصيات الأمان"

تسرد علامة تبويب **توصيات الأمان** الإجراءات التي يمكنك اتخاذها لحماية الجهاز. سيؤدي تحديد عنصر في هذه القائمة إلى فتح قائمة منبثقة حيث يمكنك الحصول على إرشادات حول كيفية تطبيق التوصية.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png" alt-text="علامة التبويب &quot;توصيات الأمان&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png":::

كما هو الحال مع علامات التبويب السابقة، يمكن تخصيص عدد العناصر المعروضة لكل صفحة، بالإضافة إلى الأعمدة المرئية.

تتضمن طريقة العرض الافتراضية أعمدة تفصل نقاط الضعف الأمنية التي تمت معالجتها، والخطر المرتبط بها، والمكون أو البرامج ذات الصلة المتأثرة بالخطر، والمزيد. يمكن تصفية العناصر حسب حالة التوصية.

### <a name="software-inventory"></a>بيانات البرامج

تسرد علامة تبويب **مخزون البرامج** البرامج المثبتة على الجهاز.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png" alt-text="علامة التبويب &quot;مخزون البرامج&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png":::

تعرض طريقة العرض الافتراضية مورد البرامج ورقم الإصدار المثبت وعدد نقاط ضعف البرامج المعروفة ونتائج تحليلات المخاطر والتعليمات البرمجية للمنتج والعلامات. يمكن تخصيص عدد العناصر المعروضة والأعمدة المعروضة.

يؤدي تحديد عنصر من هذه القائمة إلى فتح قائمة منبثقة تحتوي على مزيد من التفاصيل حول البرنامج المحدد، بالإضافة إلى المسار والطوابع الزمنية لآخر مرة تم فيها العثور على البرنامج.

يمكن تصفية هذه القائمة حسب رمز المنتج.

### <a name="discovered-vulnerabilities-tab"></a>علامة تبويب الثغرات الأمنية المكتشفة

تسرد علامة تبويب **الثغرات الأمنية المكتشفة** أي ثغرات أمنية ومستغلات شائعة (CVEs) قد تؤثر على الجهاز.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png" alt-text="علامة التبويب &quot;اكتشاف الثغرات الأمنية&quot; لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png":::

تسرد طريقة العرض الافتراضية خطورة CVE، ودرجة الثغرات الأمنية الشائعة (CVS)، والبرنامج المتعلق ب CVE، ووقت نشر CVE، ووقت آخر تحديث ل CVE، والتهديدات المرتبطة ب CVE.

كما هو الحال مع علامات التبويب السابقة، يمكن تخصيص عدد العناصر المعروضة والأعمدة المرئية.

سيؤدي تحديد عنصر من هذه القائمة إلى فتح قائمة منبثقة تصف CVE.

### <a name="missing-kbs"></a>كيلوبايت مفقود

تسرد علامة تبويب **KBs المفقودة** أي تحديثات Microsoft لم يتم تطبيقها بعد على الجهاز. و"مؤشرات الأداء الرئيسية" المعنية هي [مقالات قاعدة المعارف](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) التي تصف هذه التحديثات؛ على سبيل المثال، [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG" alt-text="علامة التبويب «Missing KBs» لملف تعريف الجهاز في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG":::

تسرد طريقة العرض الافتراضية النشرة التي تحتوي على التحديثات وإصدار نظام التشغيل والمنتجات المتأثرة وCVEs التي تمت معالجتها ورقم KB والعلامات.

يمكن تخصيص عدد العناصر المعروضة لكل صفحة والأعمدة المعروضة.

سيؤدي تحديد عنصر إلى فتح قائمة منبثقة ترتبط بالتحديث.

## <a name="related-topics"></a>المواضيع ذات الصلة

* [نظرة عامة على Microsoft 365 Defender](microsoft-365-defender.md)
* [تمكين Microsoft 365 Defender](m365d-enable.md)
* [التحقيق في الكيانات على الأجهزة، باستخدام الاستجابة المباشرة](../defender-endpoint/live-response.md)
* [التحقيق التلقائي والاستجابة (AIR) في Office 365](../office-365-security/office-365-air.md)
