---
title: التحقيق التلقائي والاستجابة في Microsoft Defender لـ Office 365
keywords: AIR، و autoIR، Microsoft Defender لنقطة النهاية، وأتمتة، والتحقيق، والاستجابة، والمعالجة، والتهديدات، والمتقدمة، والتهديدات، والحماية
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 01/29/2021
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: ابدأ باستخدام قدرات التحقيق والاستجابة التلقائية في Microsoft Defender لـ Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ca64509321ff43bbe8b7baf7ec7dfa270d9afdc4
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941512"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>التحقيق التلقائي والاستجابة (AIR) في Microsoft Defender لـ Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تتضمن [Microsoft Defender لـ Office 365](defender-for-office-365.md) قدرات قوية للتحقيق والاستجابة التلقائية (AIR) التي يمكن أن توفر الوقت والجهد لفريق عمليات الأمان. مع تشغيل التنبيهات، يعود الأمر إلى فريق عمليات الأمان لمراجعة تلك التنبيهات وتحديد أولوياتها والاستجابة لها. قد يكون مواكبة حجم التنبيهات الواردة أمرا مرهقا. يمكن أن تساعد أتمتة بعض هذه المهام.

يتيح AIR لفريق عمليات الأمان لديك العمل بفعالية وفعالية أكبر. تتضمن قدرات AIR عمليات التحقيق التلقائية استجابة للتهديدات المعروفة الموجودة اليوم. تنتظر إجراءات المعالجة المناسبة الموافقة، ما يمكن فريق عمليات الأمان من الاستجابة بفعالية للتهديدات المكتشفة. باستخدام AIR، يمكن لفريق عمليات الأمان التركيز على المهام ذات الأولوية الأعلى دون فقدان رؤية التنبيهات المهمة التي يتم تشغيلها.

تصف هذه المقالة:

- [التدفق العام ل AIR](#the-overall-flow-of-air)؛
- [كيفية الحصول على AIR](#how-to-get-air)؛ و
- [الأذونات المطلوبة](#required-permissions-to-use-air-capabilities) لتكوين قدرات AIR أو استخدامها.
- التغييرات التي سيتم إدخالها قريبا على مدخل Microsoft 365 Defender

تتضمن هذه المقالة أيضا [الخطوات التالية](#next-steps) والموارد لمعرفة المزيد.

## <a name="the-overall-flow-of-air"></a>التدفق العام ل AIR

يتم تشغيل تنبيه، ويبدأ دليل مبادئ الأمان في تحقيق تلقائي، ما يؤدي إلى النتائج والإجراءات الموصى بها. فيما يلي التدفق العام ل AIR، خطوة بخطوة:

1. يبدأ التحقيق التلقائي بإحدى الطرق التالية:
   - يتم [تشغيل تنبيه](#which-alert-policies-trigger-automated-investigations) بواسطة شيء مريب في البريد الإلكتروني (مثل رسالة أو مرفق أو URL أو حساب مستخدم مخترق). يتم إنشاء حادث، ويبدأ التحقيق التلقائي؛ او
   - يبدأ محلل الأمان [تحقيق تلقائي](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) أثناء استخدام [Explorer](threat-explorer.md).
2. في أثناء تشغيل تحقيق تلقائي، فإنه يجمع بيانات حول البريد الإلكتروني المعني والكيانات المتعلقة بهذا البريد الإلكتروني. يمكن أن تتضمن هذه الكيانات الملفات وعناوين URL والمستلمين. يمكن أن يزيد نطاق التحقيق مع تشغيل التنبيهات الجديدة وذات الصلة.
3. في أثناء التحقيق التلقائي وبعده، تتوفر [التفاصيل والنتائج](air-view-investigation-results.md) لعرضها. وتشمل النتائج [الإجراءات الموصى بها](air-remediation-actions.md) التي يمكن اتخاذها للاستجابة لأي تهديدات تم العثور عليها ومعالجتها.
4. يراجع فريق عمليات الأمان [نتائج التحقيق وتوصياته](air-view-investigation-results.md)، [ويوافق على إجراءات المعالجة أو يرفضها](air-review-approve-pending-completed-actions.md).
5. مع الموافقة على إجراءات المعالجة المعلقة (أو رفضها)، يكتمل التحقيق التلقائي.

في Microsoft Defender لـ Office 365، لا يتم اتخاذ أي إجراءات معالجة تلقائيا. يتم اتخاذ إجراءات المعالجة فقط عند موافقة فريق الأمان في مؤسستك. توفر قدرات AIR وقت فريق عمليات الأمان من خلال تحديد إجراءات المعالجة وتوفير التفاصيل اللازمة لاتخاذ قرار مستنير.

في أثناء وبعد كل تحقيق مؤتمت، يمكن لفريق عمليات الأمان لديك:

- [عرض تفاصيل حول تنبيه متعلق بالتحقيق](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [عرض تفاصيل نتائج التحقيق](air-view-investigation-results.md#view-details-of-an-investigation)
- [مراجعة الإجراءات والموافقة عليها نتيجة للتحقيق](air-review-approve-pending-completed-actions.md)

> [!TIP]
> للحصول على نظرة عامة أكثر تفصيلا، راجع [كيفية عمل AIR](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>كيفية الحصول على AIR

يتم تضمين قدرات AIR في [Microsoft Defender لـ Office 365](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2)، شريطة تكوين النهج والتنبيهات الخاصة بك. هل تحتاج إلى بعض المساعدة؟ اتبع الإرشادات الواردة في [الحماية من التهديدات](protect-against-threats.md) لإعداد إعدادات الحماية التالية أو تكوينها:

- [تسجيل التدقيق](../../compliance/turn-audit-log-search-on-or-off.md) (يجب أن يكون قيد التشغيل)
- [الحماية من البرامج الضارة](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [الحماية من التصيد الاحتيالي](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [الحماية من البريد العشوائي](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [ارتباطات خزينة ومرفقات خزينة](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

بالإضافة إلى ذلك، تأكد من [مراجعة نهج التنبيه الخاصة بمؤسستك](../../compliance/alert-policies.md)، خاصة [النهج الافتراضية في فئة إدارة المخاطر](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>ما هي نهج التنبيه التي تؤدي إلى التحقيقات التلقائية؟

يوفر Microsoft 365 العديد من نهج التنبيه المضمنة التي تساعد في تحديد إساءة استخدام أذونات المسؤول Exchange ونشاط البرامج الضارة والتهديدات الخارجية والداخلية المحتملة ومخاطر إدارة المعلومات. يمكن أن تؤدي العديد من [نهج التنبيه الافتراضية](../../compliance/alert-policies.md#default-alert-policies) إلى إجراء تحقيقات تلقائية. يصف الجدول التالي التنبيهات التي تؤدي إلى التحقيقات التلقائية، وشدتها في مدخل Microsoft 365 Defender، وكيفية إنشائها:

|تنبيه|شده|كيفية إنشاء التنبيه|
|---|---|---|
|تم الكشف عن نقرة URL يحتمل أن تكون ضارة|**عاليه**|يتم إنشاء هذا التنبيه عند حدوث أي مما يلي: <ul><li>مستخدم محمي بواسطة [ارتباطات خزينة](safe-links.md) في مؤسستك ينقر فوق ارتباط ضار</li><li>يتم تحديد تغييرات الحكم لعناوين URL بواسطة Microsoft Defender لـ Office 365</li><li>يتجاوز المستخدمون صفحات تحذير الارتباطات خزينة (استنادا إلى [نهج الارتباطات خزينة](set-up-safe-links-policies.md) الخاصة بالمؤسسة.</li></ul> <p> لمزيد من المعلومات حول الأحداث التي تقوم بتشغيل هذا التنبيه، راجع [إعداد نهج الارتباطات خزينة](set-up-safe-links-policies.md).|
|يتم الإبلاغ عن رسالة بريد إلكتروني من قبل المستخدم على أنها برامج ضارة أو تصيد احتيالي|**اعلاميه**|يتم إنشاء هذا التنبيه عندما يقوم المستخدمون في مؤسستك بالإبلاغ عن رسائل التصيد الاحتيالي باستخدام [الوظيفة الإضافية "رسالة التقرير](enable-the-report-message-add-in.md) " أو [الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي](enable-the-report-phish-add-in.md)".|
|تتم إزالة رسائل البريد الإلكتروني التي تحتوي على برامج ضارة بعد التسليم|**اعلاميه**|يتم إنشاء هذا التنبيه عند تسليم أي رسائل بريد إلكتروني تحتوي على برامج ضارة إلى علب البريد في مؤسستك. إذا حدث هذا الحدث، تقوم Microsoft بإزالة الرسائل المصابة من علب بريد Exchange Online باستخدام [إزالة تلقائية بدون ساعة (ZAP).](zero-hour-auto-purge.md)|
|تتم إزالة رسائل البريد الإلكتروني التي تحتوي على عناوين URL للتصيد الاحتيالي بعد التسليم|**اعلاميه**|يتم إنشاء هذا التنبيه عند تسليم أي رسائل تحتوي على تصيد احتيالي إلى علب البريد في مؤسستك. إذا حدث هذا الحدث، تقوم Microsoft بإزالة الرسائل المصابة من علب بريد Exchange Online باستخدام [ZAP](zero-hour-auto-purge.md).|
|تم الكشف عن أنماط إرسال البريد الإلكتروني المشبوهة|**المتوسطه**|يتم إنشاء هذا التنبيه عندما يرسل شخص ما في مؤسستك بريدا إلكترونيا مريبا ويخاطر بتقييده من إرسال البريد الإلكتروني. التنبيه هو تحذير مبكر للسلوك الذي قد يشير إلى أن الحساب مخترق، ولكنه ليس شديد بما يكفي لتقييد المستخدم. <p> على الرغم من أنه نادر، قد يكون التنبيه الذي تم إنشاؤه بواسطة هذا النهج حالة شاذة. ومع ذلك، من الجيد [التحقق مما إذا كان حساب المستخدم قد تم اختراقه](responding-to-a-compromised-email-account.md).|
|المستخدم مقيد من إرسال البريد الإلكتروني|**عاليه**|يتم إنشاء هذا التنبيه عندما يكون شخص ما في مؤسستك مقيدا من إرسال البريد الصادر. ينتج هذا التنبيه عادة عند [اختراق حساب بريد إلكتروني](responding-to-a-compromised-email-account.md). <p> لمزيد من المعلومات حول المستخدمين المقيدين، راجع [إزالة المستخدمين المحظورين من مدخل "المستخدمون المقيدون" في Microsoft 365](removing-user-from-restricted-users-portal-after-spam.md).|

> [!TIP]
> لمعرفة المزيد حول نهج التنبيه أو تحرير الإعدادات الافتراضية، راجع [نهج التنبيه في مدخل توافق Microsoft Purview](../../compliance/alert-policies.md).

## <a name="required-permissions-to-use-air-capabilities"></a>الأذونات المطلوبة لاستخدام قدرات AIR

يتم منح الأذونات من خلال أدوار معينة، مثل تلك الموضحة في الجدول التالي:

|المهمه|الدور (الأدوار) المطلوبة|
|---|---|
|إعداد ميزات AIR|أحد الأدوار التالية: <ul><li>المسؤول العام</li><li>مسؤول الأمان</li></ul> <p> يمكن تعيين هذه الأدوار في [Azure Active Directory](/azure/active-directory/roles/permissions-reference) أو في [مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|بدء تحقيق تلقائي <p> --- أو --- <p> الموافقة على الإجراءات الموصى بها أو رفضها|أحد الأدوار التالية، المعينة في [Azure Active Directory](/azure/active-directory/roles/permissions-reference) أو في [مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md): <ul><li>المسؤول العام</li><li>مسؤول الأمان</li><li>عامل تشغيل الأمان</li><li>قارئ الأمان <br> --- --- </li><li>البحث والإزالة (يتم تعيين هذا الدور فقط في [مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md). قد تحتاج إلى إنشاء مجموعة دور **تعاون جديدة & البريد الإلكتروني** هناك وإضافة دور البحث والإزالة إلى مجموعة الأدوار الجديدة هذه.</li></ul>|

## <a name="required-licenses"></a>التراخيص المطلوبة

Microsoft Defender لـ Office 365 يجب تعيين تراخيص [الخطة 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) إلى:

- مسؤولو الأمان (بما في ذلك المسؤولون العموميون)
- فريق عمليات الأمان في مؤسستك (بما في ذلك برامج قراءة الأمان وأولئك الذين لهم دور **البحث والإزالة** )
- المستخدمون النهائيون

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>ستتوفر التغييرات قريبا في مدخل Microsoft 365 Defender

إذا كنت تستخدم بالفعل قدرات AIR في Microsoft Defender لـ Office 365، فأنت على وشك رؤية بعض التغييرات في [مدخل Microsoft 365 Defender المحسن](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="مركز الإجراءات الموحدة" lightbox="../../media/m3d-action-center-unified.png":::

تجمع بوابة <https://security.microsoft.com> Microsoft 365 Defender الجديدة والمحسنة قدرات AIR في [Microsoft Defender لـ Office 365](defender-for-office-365.md) وفي [Microsoft Defender لنقطة النهاية](../defender-endpoint/automated-investigations.md). باستخدام هذه التحديثات والتحسينات، سيتمكن فريق عمليات الأمان من عرض تفاصيل حول التحقيقات التلقائية وإجراءات المعالجة عبر البريد الإلكتروني ومحتوى التعاون وحسابات المستخدمين والأجهزة، كل ذلك في مكان واحد.

> [!TIP]
> يستبدل مدخل Microsoft 365 Defender الجديد مراكز الإدارة التالية:
>
> - مركز توافق & الأمان (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> بالإضافة إلى تغيير عنوان URL، هناك شكل وأسلوب جديدان، مصممان لمنح فريق الأمان تجربة أكثر انسيابية، مع رؤية المزيد من عمليات الكشف عن التهديدات في مكان واحد.

### <a name="what-to-expect"></a>ما يجب توقعه

يسرد الجدول التالي التغييرات والتحسينات القادمة إلى AIR في Microsoft Defender لـ Office 365.

|البند|ما الذي يتغير؟|
|---|---|
|صفحة **التحقيقات**|صفحة **التحقيقات المحدثة** أكثر اتساقا مع ما تراه في [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations). سترى بعض تغييرات التنسيق والأنماط العامة التي تتماشى مع طريقة عرض **التحقيقات الموحدة** الجديدة. على سبيل المثال، يحتوي الرسم البياني للتحقيق على تنسيق أكثر توحيدا.|
|علامة التبويب **"المستخدمون**"|أصبحت علامة التبويب **"المستخدمون** " الآن علامة التبويب **"علب البريد** ". يتم سرد تفاصيل حول المستخدمين في علامة التبويب **"علبة البريد** ".|
|علامة تبويب **البريد الإلكتروني**|تمت إزالة علامة التبويب **"بريد إلكتروني** "؛ تفضل بزيارة علامة التبويب **Entities** للاطلاع على قائمة بالعناصر الخاصة بمجموعة البريد الإلكتروني والبريد الإلكتروني.|
|علامة تبويب **الكيانات**|تحتوي علامة التبويب **Entities** على نمط علامة تبويب في علامة التبويب يتضمن طريقة عرض الملخص بالكامل، والقدرة على التصفية حسب نوع الكيان. تتضمن علامة التبويب **Entities** الآن خيار **التتبع Go** بالإضافة إلى خيار **Open in Explorer** . يمكنك الآن استخدام إما [المستكشف](threat-explorer.md) أو [التتبع المتقدم](../defender-endpoint/advanced-hunting-overview.md) للعثور على الكيانات والتهديدات، والتصفية حسب النتائج.|
|علامة التبويب **"إجراءات**"|تتضمن علامة التبويب **"إجراءات** " المحدثة الآن علامة تبويب **إجراءات معلقة** وعلامة تبويب **محفوظات الإجراءات** . يمكن الموافقة على الإجراءات (أو رفضها) في جزء جانبي يتم فتحه عند تحديد إجراء معلق.|
|علامة التبويب **"دليل**"|تظهر **علامة** تبويب دليل جديدة نتائج الكيان الرئيسي المتعلقة بالإجراءات. يمكن الموافقة على الإجراءات المتعلقة بكل جزء من الأدلة (أو رفضها) في جزء جانبي يفتح عند تحديد إجراء معلق.|
|**مركز الصيانة**|يجمع **مركز الصيانة** المحدث (<https://security.microsoft.com/action-center>) الإجراءات المعلقة والمكتملة عبر البريد الإلكتروني والأجهزة والهويات. لمعرفة المزيد، راجع مركز الصيانة. (لمعرفة المزيد، راجع [مركز الصيانة](../defender/m365d-action-center.md).)|
|صفحة **الأحداث**|ترتبط صفحة **الحوادث** الآن بالتحقيقات المتعددة معا لتوفير عرض موحد أفضل للتحقيقات. ([تعرف على المزيد حول الحوادث](../defender/incidents-overview.md).)|

## <a name="next-steps"></a>الخطوات التالية

- [الاطلاع على تفاصيل ونتائج التحقيق التلقائي](air-view-investigation-results.md#view-details-of-an-investigation)
- [مراجعة الإجراءات المعلقة والموافقة عليها](air-remediation-actions.md)
