---
title: إجراء عمليات التحقيق والاستجابة التلقائية في Microsoft Defender Office 365
keywords: AIR، autoIR، Microsoft Defender ل Endpoint، تلقائي، تحقيق، استجابة، معالجة، تهديدات، متقدم، خطر، حماية
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
description: بدء استخدام قدرات الاستجابة والتحري التلقائي في Microsoft Defender Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 70a5eba3eb78878cc1f15bdd711a3331e9af870a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680875"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>إجراء عمليات التحقيق والاستجابة التلقائية (AIR) في Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[يتضمن Microsoft Defender for Office 365](defender-for-office-365.md) إمكانات فعالة للتحري والاستجابة التلقائية (AIR) التي يمكن أن توفر الوقت والجهد في فريق عمليات الأمان. عند تشغيل التنبيهات، الأمر متروك لفريق عمليات الأمان لمراجعة تلك التنبيهات وتحديد أولوياتها والاستجابة لها. قد يكون مواكبة حجم التنبيهات الواردة غامرا. يمكن أن تساعدك أتمتة بعض هذه المهام.

تمكن AIR فريق عمليات الأمان من العمل بفعالية وفعالية أكبر. تتضمن قدرات AIR عمليات التحقيق التلقائية استجابة للتهديدات المعروفة الموجودة اليوم. تنتظر إجراءات المعالجة المناسبة الموافقة، مما يمكن فريق عمليات الأمان من الاستجابة بفعالية للتهديدات التي تم الكشف عنها. باستخدام AIR، يمكن لفريق عمليات الأمان التركيز على المهام ذات الأولوية العليا دون أن يغفل عن التنبيهات المهمة التي يتم تشغيلها.

تصف هذه المقالة:

- التدفق [الإجمالي ل AIR](#the-overall-flow-of-air)؛
- [كيفية الحصول على AIR](#how-to-get-air)؛ و
- [الأذونات المطلوبة](#required-permissions-to-use-air-capabilities) لتكوين قدرات AIR أو استخدامها.
- التغييرات التي ستدخل قريبا إلى مدخل Microsoft 365 Defender

تتضمن هذه المقالة أيضا [الخطوات التالية](#next-steps) والموارد لمعرفة المزيد.

## <a name="the-overall-flow-of-air"></a>التدفق الإجمالي ل AIR

يتم تشغيل تنبيه، ويبدأ مصنف أمان بإجراء تحقيق تلقائي، مما يؤدي إلى نتائج والإجراءات الموصى بها. فيما يلي التدفق الإجمالي ل AIR، خطوة بخطوة:

1. يتم بدء التحقيق التلقائي باستخدام إحدى الطرق التالية:
   - إما [أن يتم تشغيل التنبيه بسبب شيء](#which-alert-policies-trigger-automated-investigations) مريب في البريد الإلكتروني (مثل رسالة أو مرفق أو عنوان URL أو حساب مستخدم مريب). يتم إنشاء حادث، ويبدأ التحقيق التلقائي؛ أو
   - يبدأ محلل [الأمان إجراء تحقيق تلقائي](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) أثناء استخدام [المستكشف](threat-explorer.md).
2. أثناء تشغيل التحقيق التلقائي، يجمع بيانات حول البريد الإلكتروني المعني والكيانات ذات الصلة بهذا البريد الإلكتروني. يمكن أن تتضمن هذه الكيانات ملفات، عناوين URL، ومستلمين. يمكن أن يزيد نطاق التحقيق عند تشغيل التنبيهات الجديدة والم ذات الصلة.
3. أثناء إجراء تحقيق تلقائي وبعده [، تتوفر](air-view-investigation-results.md) التفاصيل والنتائج لعرضها. تتضمن النتائج [الإجراءات الموصى](air-remediation-actions.md) بها التي يمكن اتخاذها للاستجابة لأي تهديدات تم العثور عليها والاستجابة لها.
4. يراجع فريق عمليات الأمان [نتائج التحقيق وتوصياته](air-view-investigation-results.md)، [ويوافق على إجراءات المعالجة أو يرفضها](air-review-approve-pending-completed-actions.md).
5. مع الموافقة على إجراءات المعالجة المعلقة (أو رفضها)، يكتمل التحقيق التلقائي.

في Microsoft Defender Office 365، لا يتم اتخاذ أي إجراءات إصلاح تلقائيا. يتم اتخاذ إجراءات الإصلاح فقط عند موافقة فريق الأمان في مؤسستك. توفر قدرات AIR وقت فريق عمليات الأمان من خلال تحديد إجراءات المعالجة وتوفير التفاصيل اللازمة لاتخاذ قرار مطلع.

أثناء كل تحقيق تلقائي وبعده، يمكن لفريق عمليات الأمان القيام بما يلي:

- [عرض تفاصيل حول تنبيه مرتبط بالتحقيق](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [عرض تفاصيل نتائج التحقيق](air-view-investigation-results.md#view-details-of-an-investigation)
- [مراجعة الإجراءات والموافقة عليها نتيجة التحقيق](air-review-approve-pending-completed-actions.md)

> [!TIP]
> للحصول على نظرة عامة أكثر تفصيلا، راجع [كيفية عمل AIR](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>كيفية الحصول على AIR

يتم تضمين قدرات AIR في [Microsoft Defender Office 365](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2)، شرط تكوين سياساتك وتنبيهاتك. هل تحتاج إلى بعض المساعدة؟ اتبع الإرشادات في [الحماية من التهديدات](protect-against-threats.md) لإعداد إعدادات الحماية التالية أو تكوينها:

- [تسجيل التدقيق](../../compliance/turn-audit-log-search-on-or-off.md) (يجب أن يكون تشغيل)
- [الحماية من البرامج الضارة](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [الحماية من التصيد الاحتيالي](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [الحماية من البريد العشوائي](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [خزينة الارتباطات خزينة المرفقات](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

بالإضافة إلى ذلك، تأكد من [](../../compliance/alert-policies.md)مراجعة سياسات التنبيه الخاصة مؤسستك، لا سيما السياسات الافتراضية في [فئة إدارة المخاطر](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>ما هي سياسات التنبيه التي تؤدي إلى إجراء عمليات تحقيق تلقائية؟

Microsoft 365 العديد من سياسات التنبيه المضمنة التي تساعد على تحديد Exchange إساءة استخدام أذونات المسؤول، ونشاط البرامج الضارة، والمخاطر الخارجية والداخلية المحتملة، ومخاطر إدارة المعلومات. يمكن أن تؤدي العديد من [سياسات التنبيه الافتراضية](../../compliance/alert-policies.md#default-alert-policies) إلى تشغيل عمليات تحقيق تلقائية. يصف الجدول التالي التنبيهات التي تقوم بتشغيل عمليات التحقيق التلقائية، ومدى خطورتها في مدخل Microsoft 365 Defender، وكيفية إنشاؤها:

|تنبيه|الخطورة|كيفية إنشاء التنبيه|
|---|---|---|
|تم الكشف عن نقرة URL يحتمل أن تكون ضارة|**عال**|يتم إنشاء هذا التنبيه عند حدوث أي من ما يلي: <ul><li>يقوم مستخدم محمي بواسطة خزينة [في](safe-links.md) مؤسستك بالنقر فوق ارتباط ضار</li><li>يحدد Microsoft Defender Office 365</li><li>يتجاوز المستخدمون خزينة تحذير الارتباطات (استنادا إلى نهج الارتباطات خزينة [الخاص بك](set-up-safe-links-policies.md).</li></ul> <p> لمزيد من المعلومات حول الأحداث التي تؤدي إلى تشغيل هذا التنبيه، راجع [إعداد خزينة الارتباطات](set-up-safe-links-policies.md).|
|يتم إرسال رسالة بريد إلكتروني بواسطة مستخدم كبرامج ضارة أو تصيد احتيالي|**معلوماتية**|يتم إنشاء هذا التنبيه عندما يقوم المستخدمون في مؤسستك ب الإبلاغ عن رسائل بريد إلكتروني تصيد [](enable-the-report-message-add-in.md) احتيالي باستخدام الوظائف الإضافية "الإبلاغ عن رسالة" أو "الإبلاغ عن التصيد [الاحتيالي".](enable-the-report-phish-add-in.md)|
|تتم إزالة رسائل البريد الإلكتروني التي تحتوي على البرامج الضارة بعد التسليم|**معلوماتية**|يتم إنشاء هذا التنبيه عند تسليم أي رسائل بريد إلكتروني تحتوي على برامج ضارة إلى علب البريد في مؤسستك. إذا حدث هذا الحدث، فإن Microsoft تزيل الرسائل المصابة من علب Exchange Online البريد باستخدام إزالة تلقائية [لمدة ساعة (ZAP)](zero-hour-auto-purge.md) .|
|تتم إزالة رسائل البريد الإلكتروني التي تحتوي على عناوين URL لتصيد احتيالي بعد التسليم|**معلوماتية**|يتم إنشاء هذا التنبيه عند تسليم أي رسائل تحتوي على تصيد احتيالي إلى علب البريد في مؤسستك. إذا حدث هذا الحدث، فإن Microsoft تزيل الرسائل المصابة من علب Exchange Online البريد باستخدام [ZAP](zero-hour-auto-purge.md).|
|تم الكشف عن أنماط إرسال البريد الإلكتروني المريبة|**متوسط**|يتم إنشاء هذا التنبيه عندما يرسل شخص ما في مؤسستك بريدا إلكترونيا مريبا ويخاطر بتقييده من إرسال البريد الإلكتروني. التنبيه هو تحذير مبكر للسلوك الذي قد يشير إلى أنه تم اختراق الحساب، ولكنه ليس شديد بما يكفي لتقييد المستخدم. <p> على الرغم من أن هذا التنبيه نادر الحدوث، إلا أن التنبيه الذي يتم إنشاؤه بواسطة هذا النهج قد يكون غير صحيح. ومع ذلك، من الجيد التحقق مما إذا كان [حساب المستخدم قد تم اختراقه](responding-to-a-compromised-email-account.md).|
|المستخدم مقيد من إرسال البريد الإلكتروني|**عال**|يتم إنشاء هذا التنبيه عندما يكون أحد الأشخاص في مؤسستك مقيدا من إرسال البريد الصادر. ينتج هذا التنبيه عادة عند اختراق [حساب بريد إلكتروني](responding-to-a-compromised-email-account.md). <p> لمزيد من المعلومات حول المستخدمين المقيدين، راجع إزالة [المستخدمين](removing-user-from-restricted-users-portal-after-spam.md) المحظورين من مدخل المستخدمين المقيدين في Microsoft 365.|

> [!TIP]
> لمعرفة المزيد حول سياسات التنبيه أو تحرير الإعدادات الافتراضية، راجع [تنبيهات](../../compliance/alert-policies.md) في مركز التوافق في Microsoft 365.

## <a name="required-permissions-to-use-air-capabilities"></a>الأذونات المطلوبة لاستخدام قدرات AIR

يتم منح الأذونات من خلال أدوار معينة، مثل تلك التي تم وصفها في الجدول التالي:

|مهمة|الدور (الدور) مطلوب|
|---|---|
|إعداد ميزات AIR|أحد الأدوار التالية: <ul><li>المسؤول العام</li><li>مسؤول الأمان</li></ul> <p> يمكن تعيين هذه الأدوار في [Azure Active Directory](/azure/active-directory/roles/permissions-reference) أو في مدخل Microsoft 365 Defender[.](permissions-microsoft-365-security-center.md)|
|بدء تحقيق تلقائي <p> --- أو --- <p> الموافقة على الإجراءات الموصى بها أو رفضها|أحد الأدوار التالية، المعينة في [Azure Active Directory](/azure/active-directory/roles/permissions-reference) أو [في مدخل Microsoft 365 Defender:](permissions-microsoft-365-security-center.md) <ul><li>المسؤول العام</li><li>مسؤول الأمان</li><li>عامل تشغيل الأمان</li><li>قارئ الأمان <br> --- --- </li><li>البحث و الازدحام (يتم تعيين هذا الدور فقط في Microsoft 365 Defender [المدخل](permissions-microsoft-365-security-center.md). قد تحتاج إلى إنشاء مجموعة جديدة لدور  & البريد الإلكتروني هناك وإضافة دور البحث و الازدحام إلى مجموعة الدور الجديدة هذه.</li></ul>|

## <a name="required-licenses"></a>التراخيص المطلوبة

[يجب تعيين Office 365 Microsoft Defender](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) لتراخيص الخطة 2 إلى:

- مسؤولي الأمان (بما في ذلك المسؤولون العامون)
- فريق عمليات الأمان في مؤسستك (بما في ذلك قراء الأمان وأولئك الذين يلعبون دور البحث **و الازدحام** )
- المستخدمون النهائيون

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>ستدخل التغييرات قريبا في مدخل Microsoft 365 Defender

إذا كنت تستخدم قدرات AIR بالفعل في Microsoft Defender Office 365، أنت على وشك رؤية بعض التغييرات في مدخل Microsoft 365 Defender [المحسن](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="مركز الإجراءات الموحد.":::

يجمع مدخل Microsoft 365 Defender <https://security.microsoft.com> الجديد والمحسن قدرات AIR في [Microsoft Defender Office 365](defender-for-office-365.md) وفي [Microsoft Defender ل Endpoint](../defender-endpoint/automated-investigations.md). باستخدام هذه التحديثات والتحسينات، سيكون فريق عمليات الأمان قادرا على عرض تفاصيل حول عمليات البحث التلقائية والإجراءات الإصلاحية عبر البريد الإلكتروني ومحتوى التعاون وحسابات المستخدمين والأجهزة، كل ذلك في مكان واحد.

> [!TIP]
> يحل المدخل Microsoft 365 Defender الجديد محل مراكز الإدارة التالية:
>
> - مركز & الأمان (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> بالإضافة إلى تغيير عنوان URL، هناك شكل جديد ومنظر جديد، تم تصميمه ليمنح فريق الأمان تجربة أكثر تنظيما، مع الرؤية لمزيد من عمليات الكشف عن المخاطر في مكان واحد.

### <a name="what-to-expect"></a>ما يجب توقعه

يسرد الجدول التالي التغييرات والتحسينات التي يتم إدخالها على AIR في Microsoft Defender Office 365.

|عنصر|ما الذي يتغير؟|
|---|---|
|**صفحة "التحقيق** "|صفحة **"التحقيقات** " المحدثة أكثر تناسقا مع ما تراه في [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations). سترى بعض التغييرات العامة في التنسيق والتصميم التي تتماشى مع طريقة عرض "التحقيقات" **الموحدة الجديدة** . على سبيل المثال، يكون تنسيق رسم التحقيق أكثر توحيدا.|
|**علامة التبويب "المستخدمون** "|أصبحت **علامة التبويب** المستخدمون الآن علامة **التبويب علب البريد** . يتم سرد تفاصيل حول المستخدمين على علامة التبويب **علبة** البريد.|
|**علامة تبويب البريد** الإلكتروني|تمت **إزالة** علامة التبويب بريد إلكتروني؛ تفضل بزيارة **علامة التبويب** الكيانات لرؤية قائمة عناصر مجموعات البريد الإلكتروني والبريد الإلكتروني.|
|**علامة التبويب "الكيانات** "|تتضمن **علامة التبويب** الكيانات نمط علامة التبويب في علامة التبويب الذي يتضمن طريقة عرض ملخصة، والقدرة على التصفية حسب نوع الكيان. تتضمن **علامة التبويب** الكيانات الآن خيار **"الانتقال للصيد** " بالإضافة إلى **الخيار "فتح في المستكشف** ". يمكنك الآن استخدام "[المستكشف](threat-explorer.md)" [](../defender-endpoint/advanced-hunting-overview.md) أو البحث المتقدم للعثور على الكيانات والتهديدات، وتصفية النتائج.|
|**علامة التبويب "إجراءات** "|تتضمن علامة **التبويب إجراءات** محدثة الآن علامة **التبويب إجراءات معلقة** و علامة **تبويب محفوظات** الإجراءات. يمكن الموافقة على الإجراءات (أو رفضها) في جزء جانبي يفتح عند تحديد إجراء معلق.|
|**علامة التبويب "دليل** "|تعرض علامة **التبويب دليل** جديدة نتائج الكيان الرئيسية ذات الصلة بالتصرفات. يمكن الموافقة على الإجراءات المتعلقة بكل قطعة من الإثباتات (أو رفضها) في جزء جانبي يفتح عند تحديد إجراء معلق.|
|**مركز الإجراءات**|يجمع مركز **الإجراءات المحدث** (<https://security.microsoft.com/action-center>) الإجراءات المعلقة والمكتملة عبر البريد الإلكتروني والأجهزة والهويات. لمعرفة المزيد، راجع مركز الإجراءات. (لمعرفة المزيد، راجع [مركز الإجراءات](../defender/m365d-action-center.md).)|
|**صفحة الأحداث**|تعمل **صفحة "** الأحداث" الآن على ربط عدة عمليات تحقيق معا لتوفير طريقة عرض موحدة أفضل من عمليات التحقيق. ([تعرف على المزيد حول الأحداث](../defender/incidents-overview.md).)|

## <a name="next-steps"></a>الخطوات التالية

- [الاطلاع على تفاصيل ونتائج التحقيق التلقائي](air-view-investigation-results.md#view-details-of-an-investigation)
- [مراجعة الإجراءات المعلقة والموافقة عليها](air-remediation-actions.md)
