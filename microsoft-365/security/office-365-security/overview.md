---
title: Office 365 الأمان بما في ذلك Microsoft Defender لـ Office 365 Exchange Online Protection
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: الأمان في Office 365، من EOP إلى Defender لـ Office 365 1 و2، وتكوينات أمان قياسية مقابل صارمة، والمزيد. تعرف على ما لديك، وكيفية تأمين خصائصك.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8ddf81e038b4c055134498ee0a26751b735d786a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472166"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Microsoft Defender لـ Office 365 عامة حول الأمان

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)

ستحدثك هذه المقالة على خصائص أمان Microsoft Defender لـ Office 365 الجديد في السحابة. سواء كنت جزءا من مركز عمليات الأمان، أو كنت مسؤول أمان جديد في المساحة، أو إذا كنت تريد تحديث، فلنبدأ.

> [!CAUTION]
> إذا كنت تستخدم **Outlook.com** أو **Microsoft 365 Family** أو **Microsoft 365 Personal**، وأحتاج إلى معلومات ارتباطات *خزينة* أو *مرفقات خزينة*، انقر فوق هذا ***الارتباط: أمان*** [Outlook.com المتقدم ل Microsoft 365 المشتركين](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>ما هو Defender لـ Office 365 الأمان

كل Office 365 الاشتراك يأتي مع إمكانات الأمان. تعتمد الأهداف والإجراءات التي يمكنك اتخاذها على تركيز هذه الاشتراكات المختلفة. في Office 365 الأمان، هناك ثلاث خدمات أمان رئيسية (أو منتجات) مرتبطة بنوع اشتراكك:

1. Exchange Online Protection (EOP)
1. Microsoft Defender لـ Office 365 الخطة 1 (Defender for Office P1)
1. Microsoft Defender لـ Office 365 الخطة 2 (Defender for Office P2)

> [!NOTE]
> إذا اشتريت اشتراكك وأحتاجت إلى نشر ميزات الأمان الآن، فاتخطى إلى الخطوات في مقالة الحماية [من التهديدات](protect-against-threats.md). إذا كنت جديدا على اشتراكك وتحب معرفة ترخيصك قبل البدء، فاستعرض الفوترة > المنتجات في [مركز مسؤولي Microsoft 365.](https://admin.microsoft.com/AdminPortal/#/homepage)

Office 365 بناء الأمان على الحماية الأساسية التي يوفرها EOP. يكون EOP موجودا في أي اشتراك حيث Exchange Online علب البريد (تذكر أن جميع منتجات الأمان التي تمت مناقشتها هنا مستندة إلى السحابة).

قد تكون معتادا على عرض هذه المكونات الثلاثة التي تمت مناقشتها بهذه الطريقة:

|EOP|Microsoft Defender لـ Office 365 P1|Microsoft Defender لـ Office 365 P2|
|---|---|---|
|يمنع الهجمات المعروفة واسعة النطاق والمستندة إلى مستوى الصوت.|يحمي البريد الإلكتروني والتعاون من البرامج الضارة والتصيد الاحتيالي والبريد الإلكتروني للأعمال الذي لا يحدث أي اختراق.|يضيف عمليات التحقيق والصيد والاستجابة بعد الانتهاك، بالإضافة إلى التنفيذ التلقائي والمحاكاة (للتدريب).|

ولكن فيما يتعلق بالهندسة، فلنبدأ بالتفكير في كل قطعة كطبقات تراكمية من الأمان، كل منها مع تأكيد أمان. من هذا النوع:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="يتم Microsoft Defender لـ Office 365 و EOP وعلاقاتهما بالأخرى مع التوكيد على الخدمة، بما في ذلك ملاحظة لمصادقة البريد الإلكتروني" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

على الرغم من أن كل واحدة من هذه الخدمات تؤكد على هدف من بين الحماية والكشف والتحري والاستجابة، فإن ***all** _ يمكن للخدمات تنفيذ _ *_any_** من أهداف الحماية والكشف والتحقق والاستجابة.

إن حماية Office 365 الأساسي هي حماية EOP. Microsoft Defender لـ Office 365 يحتوي P1 على EOP فيه. Defender لـ Office 365 P2 على P1 و EOP. البنية تراكمية. ولهذا السبب، عند تكوين هذا المنتج، يجب أن تبدأ باستخدام EOP وأن تعمل على Defender لـ Office 365.

على الرغم من أن تكوين مصادقة البريد الإلكتروني يتم في DNS العام، إلا أنه من المهم تكوين هذه الميزة للمساعدة في الدفاع ضد التهزف. *إذا كان لديك EOP،* ***يجب [تكوين مصادقة البريد الإلكتروني](email-validation-and-authentication.md)***.

إذا كان لديك Office 365 E3، أو أدناه، لديك EOP، ولكن مع خيار شراء نظام Defender لـ Office 365 P1 من خلال الترقية. إذا كان لديك Office 365 E5، فإن لديك Defender لـ Office 365 P2.

> [!TIP]
> إذا لم يكن اشتراكك Office 365 E3 أو E5، فلا يزال بإمكانك التحقق لمعرفة ما إذا كان لديك خيار الترقية إلى Microsoft Defender لـ Office 365 P1. إذا كنت مهتما، فستعرض صفحة [](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) الويب هذه الاشتراكات المؤهلة لترقية Microsoft Defender لـ Office 365 P1 (تحقق من نهاية الصفحة للطباعة الدقيقة).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>الأمان Office 365 من EOP إلى Microsoft Defender لـ Office 365

> [!IMPORTANT]
> تعرف على التفاصيل على هذه [الصفحات: Exchange Online Protection](exchange-online-protection-overview.md) [Defender لـ Office 365.](defender-for-office-365.md)

ما يجعل Microsoft Defender لـ Office 365 خططك ميزة لإدارة تهديدات EOP فقط قد يكون من الصعب معرفة ذلك من النظرة الأولى. للمساعدة في الفرز إذا كان مسار الترقية صحيحا لمنظمتك، دعنا نطلع على إمكانات كل منتج عندما يتعلق الأمر بما يلي:

- منع التهديدات والكشف عنها
- التحقق
- الاستجابة

بدءا **من Exchange Online Protection**:
<p>

|منع/الكشف|التحقق|الاستجابة|
|---|---|---|
|تتضمن التقنيات:<ul><li>البريد العشوائي</li><li>التصيد الاحتيالي</li><li>البرامج الضارة</li><li>البريد المجمع</li><li>المعلومات المنتحلة</li><li>الكشف عن انتحال</li><li>عزل المسؤول</li><li>إرسالات المسؤول والمستخدم للإيجابيات الخاطئة والسلبيات الخاطئة</li><li>السماح/الحظر ل عناوين URL والملفات</li><li>التقارير</li></ul>|<li>البحث في سجل التدقيق</li><li>تتبع الرسائل</li>|<li>إزالة تلقائية لمدة ساعة (ZAP)</li><li>تحسين القوائم "السماح" و"الحظر" واختبارها</li>|

إذا كنت تريد البحث في EOP، **[فابحث عن هذه المقالة](exchange-online-protection-overview.md)**.

نظرا لأن هذه المنتجات تراكمية، إذا قمت Microsoft Defender لـ Office 365 P1 وقررت الاشتراك فيها، فسوف تضيف هذه القدرات.

المكاسب **Defender لـ Office 365، الخطة 1** (حتى الآن):
<p>

|منع/الكشف|التحقق|الاستجابة|
|---|---|---|
|تتضمن التقنيات كل شيء في EOP بالإضافة إلى:<ul><li>خزينة المرفقات</li><li>خزينة ارتباطات<li>Microsoft Defender لـ Office 365 حماية أحمال العمل (على سبيل Microsoft Defender لـ Office 365). SharePoint عبر الإنترنت، Teams، OneDrive for Business)</li><li>الحماية بنقرة واحدة في البريد الإلكتروني Office والعملاء Teams</li><li>مكافحة التصيد الاحتيالي في Defender لـ Office 365</li><li>حماية انتحال المستخدم والمجال</li><li>التنبيهات و API لتكامل SIEM للتنبيهات</li>|<li>API لتكامل SIEM للكشفات</li><li>**أداة الكشف في الوقت الحقيقي**</li><li>تتبع URL</li>|<li>نفس</li></ul>

وبالتالي، Microsoft Defender لـ Office 365 توسيع P1 على الجانب ***prevention** _ من المنزل، ويضيف نماذج إضافية من _*_الكشف_**.

Microsoft Defender لـ Office 365 P1 أيضا إلى **الكشف في الوقت الحقيقي** من أجل إجراء التحريات. يتم استخدام اسم أداة البحث عن المخاطر هذه بخط غامق لأن امتلاكها وسيلة واضحة لمعرفة  أنك Defender لـ Office 365 P1. ولا يظهر في Defender لـ Office 365 P2.

المكاسب Defender لـ Office 365 **، الخطة 2** (حتى الآن):
<p>

|منع/الكشف|التحقق|الاستجابة|
|---|---|---|
|تتضمن التقنيات كل شيء في EOP، Microsoft Defender لـ Office 365 P1 بالإضافة إلى:<ul><li>نفس</li>|<li>**مستكشف التهديدات**</li><li>متعقبات التهديدات</li><li>طرق عرض الحملة</li>|<li>التحقيق والرد التلقائي (AIR)</li><li>AIR من "مستكشف التهديدات"</li><li>AIR للمستخدمين الذين تم اختراقهم</li><li>API لتكامل SIEM من أجل "عمليات التحقيق التلقائية"</li>

وبالتالي، Microsoft Defender لـ Office 365 P2 على جانب التحقيق والاستجابة في المنزل، ويضيف قوة جديدة للصيد. التنفيذ التلقائي.

في Microsoft Defender لـ Office 365 P2، تسمى أداة الصيد **الأساسية "** مستكشف التهديدات" بدلا من الكشف في الوقت الحقيقي. إذا رأيت "مستكشف التهديدات" عند الانتقال إلى Microsoft 365 Defender، تكون في Microsoft Defender لـ Office 365 P2.

للوصول إلى تفاصيل Microsoft Defender لـ Office 365 P1 و P2، **[الانتقال إلى هذه المقالة](defender-for-office-365.md)**.

> [!TIP]
> تختلف Microsoft Defender لـ Office 365 EOP و EOP أيضا عندما يتعلق الأمر ب المستخدمين النهائيين. في EOP Defender لـ Office 365 P1، يكون التركيز على الوعي، وبالتالي تتضمن الهاتان الرسالتان الوظائف الإضافية تقرير *Outlook* حتى يمكن للمستخدمين الإبلاغ عن رسائل البريد الإلكتروني التي يجدونها مريبة، لمزيد من التحليل. <p> في Defender لـ Office 365 P2 (الذي يحتوي على كل شيء في EOP و P1)، يتحول التركيز إلى مزيد من التدريب  للمستخدمين النهائيين، وبالتالي يمكن لمركز عمليات الأمان الوصول إلى أداة فعالة من محاكي التهديدات،  ومقاييس المستخدم النهائي التي يوفرها.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender لـ Office 365 الخطة 1 مقابل ورقة معلومات الخطة 2

سيساعدك هذا المرجع السريع على فهم الإمكانيات التي تأتي مع كل Microsoft Defender لـ Office 365 اشتراك. عند دمجها مع معرفتك بميزات EOP، يمكن أن يساعد صانعو قرارات الأعمال في تحديد Microsoft Defender لـ Office 365 الأفضل لتلبية احتياجاتهم.

|Defender لـ Office 365 الخطة 1|Defender لـ Office 365 2|
|---|---|
|قدرات التكوين والحماية والكشف: <ul><li>[خزينة المرفقات](safe-attachments.md)</li><li>[الارتباطات الآمنة](safe-links.md)</li><li>[خزينة المرفقات SharePoint OneDrive و Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[الحماية من التصيد الاحتيالي في Defender لـ Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[الكشف في الوقت الحقيقي](threat-explorer.md)</li></ul>|Defender لـ Office 365 الخطة 1 <p> --- بالإضافة إلى --- <p> إمكانات التنفيذ التلقائي، والتحري، والوساطة، والتعليم: <ul><li>[متعقبات التهديدات](threat-trackers.md)</li><li>[مستكشف التهديدات](threat-explorer.md)</li><li>[إجراء عمليات التحقيق والاستجابة التلقائية](office-365-air.md)</li><li>[التدريب على محاكاة الهجمات](attack-simulation-training.md)</li><li>[البحث الاستباقي عن التهديدات باستخدام الصيد المتقدم في Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[التحقق من الأحداث في Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[التحقق من التنبيهات في Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Microsoft Defender لـ Office 365 الخطة 2 في Office 365 E5 Office 365 A5 Microsoft 365 E5.

- Microsoft Defender لـ Office 365 الخطة 1 مضمنة في Microsoft 365 Business Premium.

- Microsoft Defender لـ Office 365 الخطة 1 Defender لـ Office 365 الخطة 2 كل منهما كعينة إضافية لاشتراكات معينة. لمعرفة المزيد، إليك ارتباط آخر توفر ميزة [عبر Microsoft Defender لـ Office 365 أخرى](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- تتوفر [خزينة المستندات](safe-docs.md) فقط للمستخدمين الذين لديهم تراخيص Microsoft 365 E5 أو الأمان في Microsoft 365 E5 (غير مضمنة في Microsoft Defender لـ Office 365 أخرى).

- إذا لم يتضمن اشتراكك الحالي Microsoft Defender لـ Office 365 وتريد ذلك، فاتصل بالمبيعات لبدء تشغيل الإصدار [](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html)التجريبي، واكتشف كيف Microsoft Defender لـ Office 365 العمل في مؤسستك.

- Microsoft Defender لـ Office 365 عملاء P2 حق الوصول Microsoft 365 Defender **التكامل** للكشف عن الأحداث والتنبيهات ومراجعتها والاستجابة لها بفعالية.

> [!TIP]
> ***Insider tip** _. يمكنك استخدام docs.microsoft.com المحتويات للتعرف على EOP Microsoft Defender لـ Office 365. انتقل مرة أخرى إلى هذه الصفحة[، Office 365 نظرة](index.yml) عامة حول الأمان، وستلاحظ مؤسسة جدول المحتويات هذه في الشريط الجانبي. تبدأ هذه العملية بنشر (بما في ذلك الترحيل) ثم تستمر في المنع والكشف والتحري والاستجابة. <p> يتم تقسيم هذه البنية بحيث تكون مواضيع إدارة _ *الأمان** متبوعة بمواضيع **عمليات** الأمان. إذا كنت عضوا جديدا في أي من الدورين، فاستخدم الارتباط في هذا التلميح، ومعرفة جدول المحتويات، للمساعدة على معرفة المساحة. تذكر استخدام *ارتباطات الملاحظات* *ومقالات التقييم* كما تريد. تساعدنا الملاحظات على تحسين ما نقدمه لك.

## <a name="where-to-go-next"></a>إلى أين يجب الانتقال بعد ذلك

إذا كنت مسؤول أمان، فقد تحتاج إلى تكوين DKIM أو DMARC لبريدك. قد ترغب في طرح إعدادات أمان 'صارمة' للمستخدمين الذين لديهم الأولوية، أو البحث عن الجديد في المنتج. أو إذا كنت تستخدم "عمليات الأمان"، فقد ترغب في الاستفادة من عمليات الكشف في الوقت الحقيقي أو "مستكشف التهديدات" للتحقق منها والاستجابة لها، أو تدريب الكشف عن المستخدم النهائي باستخدام "محاكي الهجوم". وفي كلتا  كلتا  الطريقتين، إليك بعض التوصيات الإضافية حول ما يجب النظر فيه بعد ذلك.

[مصادقة البريد الإلكتروني، بما في ذلك SPF و DKIM و DMARC (مع ارتباطات لإعداد الثلاثة كلها)](email-validation-and-authentication.md)

[راجع التكوينات "الذهبية"](recommended-settings-for-eop-and-office365.md) الموصى بها واستخدام الإعدادات المسبقة الموصى بها لتكوين [سياسات الأمان بسرعة](preset-security-policies.md)

تعرف على [أحدث ما هو جديد في Microsoft Defender لـ Office 365 (بما في ذلك تطويرات EOP)](whats-new-in-defender-for-office-365.md)

[استخدام "مستكشف التهديدات" أو الكشف في الوقت الحقيقي](threat-explorer.md)

استخدام [التدريب على محاكاة الهجمات](attack-simulation-training.md)
