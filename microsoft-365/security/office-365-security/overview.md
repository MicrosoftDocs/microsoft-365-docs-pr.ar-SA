---
title: Office 365 الأمان بما في ذلك Microsoft Defender لـ Office 365 Exchange Online Protection
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: الأمان في Office 365، من EOP إلى Defender لـ Office 365 الخطط 1 و2، وتكوينات أمان قياسية مقابل صارمة، والمزيد. فهم ما لديك، وكيفية تأمين خصائصك.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a9f480575c712488a17dc7e9e91320edc11d0e50
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64835898"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>نظرة عامة على الأمان Microsoft Defender لـ Office 365

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 والخطة 2](defender-for-office-365.md)

ستعرفك هذه المقالة على خصائص الأمان Microsoft Defender لـ Office 365 الجديدة في السحابة. سواء كنت جزءا من مركز عمليات الأمان، أو كنت مسؤول أمان جديدا على المساحة، أو تريد تحديثا، فلنبدأ.

> [!CAUTION]
> إذا كنت تستخدم **Outlook.com** أو **Microsoft 365 Family** أو **Microsoft 365 Personal**، وكنت بحاجة إلى *خزينة ارتباطات* أو معلومات *خزينة المرفقات*، ***فانقر فوق هذا الارتباط***: [الأمان المتقدم Outlook.com ل Microsoft 365 المشتركين](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>ما هو الأمان Defender لـ Office 365

كل اشتراك Office 365 يأتي مع قدرات الأمان. تعتمد الأهداف والإجراءات التي يمكنك اتخاذها على تركيز هذه الاشتراكات المختلفة. في Office 365 الأمان، هناك ثلاث خدمات أمان رئيسية (أو منتجات) مرتبطة بنوع اشتراكك:

1. Exchange Online Protection (EOP)
1. Microsoft Defender لـ Office 365 الخطة 1 (Defender ل Office P1)
1. Microsoft Defender لـ Office 365 الخطة 2 (Defender for Office P2)

> [!NOTE]
> إذا اشتريت اشتراكك وتحتاج إلى طرح ميزات الأمان *الآن*، فانتقل إلى الخطوات الواردة في مقالة [الحماية من التهديدات](protect-against-threats.md) . إذا كنت جديدا على اشتراكك وترغب في معرفة ترخيصك قبل البدء، فتصفح الفوترة > منتجاتك في [مركز مسؤولي Microsoft 365](https://admin.microsoft.com/AdminPortal/#/homepage).

يعتمد الأمان Office 365 على الحماية الأساسية التي تقدمها EOP. EOP موجود في أي اشتراك حيث يمكن العثور على علب بريد Exchange Online (تذكر، جميع منتجات الأمان التي تمت مناقشتها هنا تستند إلى السحابة).

قد تكون معتادا على رؤية هذه المكونات الثلاثة التي تمت مناقشتها بهذه الطريقة:

|EOP|Microsoft Defender لـ Office 365 P1|Microsoft Defender لـ Office 365 P2|
|---|---|---|
|يمنع الهجمات الواسعة والمستندة إلى مستوى الصوت والمعروفة.|يحمي البريد الإلكتروني والتعاون من البرامج الضارة والتصيد الاحتيالي واختراق البريد الإلكتروني للأعمال.|إضافة التحقيق بعد الاختراق والتتبع والاستجابة، بالإضافة إلى الأتمتة والمحاكاة (للتدريب).|

ولكن من حيث البنية، دعونا نبدأ بالتفكير في كل قطعة كطبقات تراكمية من الأمان، كل منها مع تركيز أمني. أكثر مثل هذا:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP Microsoft Defender لـ Office 365 وعلاقاتهما مع بعضهما البعض مع تأكيد الخدمة، بما في ذلك ملاحظة لمصادقة البريد الإلكتروني" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

على الرغم من أن كل من هذه الخدمات تؤكد على هدف من بين الحماية والكشف والتحقيق والاستجابة، ***all** _ يمكن للخدمات تنفيذ _ *_any_** من أهداف الحماية والكشف والتحقيق والاستجابة.

جوهر أمان Office 365 هو حماية EOP. يحتوي Microsoft Defender لـ Office 365 P1 على EOP فيه. يحتوي Defender لـ Office 365 P2 على P1 وEOP. البنية تراكمية. لهذا السبب، عند تكوين هذا المنتج، يجب أن تبدأ ب EOP وتعمل على Defender لـ Office 365.

على الرغم من أن تكوين مصادقة البريد الإلكتروني يحدث في DNS العام، فمن المهم تكوين هذه الميزة للمساعدة في الدفاع ضد الانتحال. *إذا كان لديك EOP،* ***يجب [تكوين مصادقة البريد الإلكتروني](email-validation-and-authentication.md)***.

إذا كان لديك Office 365 E3 أو أدناه، فلديك EOP، ولكن مع خيار شراء Defender لـ Office 365 P1 مستقل من خلال الترقية. إذا كان لديك Office 365 E5، فلديك بالفعل Defender لـ Office 365 P2.

> [!TIP]
> إذا لم يكن اشتراكك Office 365 E3 أو E5، فلا يزال بإمكانك التحقق لمعرفة ما إذا كان لديك خيار الترقية إلى Microsoft Defender لـ Office 365 P1. إذا كنت مهتما، تسرد [صفحة الويب هذه](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) الاشتراكات المؤهلة لترقية Microsoft Defender لـ Office 365 P1 (تحقق من نهاية الصفحة للحصول على الطباعة الدقيقة).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>سلم الأمان Office 365 من EOP إلى Microsoft Defender لـ Office 365

> [!IMPORTANT]
> تعرف على التفاصيل الموجودة في هذه الصفحات: [Exchange Online Protection](exchange-online-protection-overview.md) [Defender لـ Office 365.](defender-for-office-365.md)

ما يجعل إضافة خطط Microsoft Defender لـ Office 365 ميزة لإدارة مخاطر EOP فقط قد يكون من الصعب معرفة ذلك للوهلة الأولى. للمساعدة في الفرز إذا كان مسار الترقية مناسبا لمؤسستك، دعنا ننظر إلى قدرات كل منتج عندما يتعلق الأمر:

- منع التهديدات واكتشافها
- التحقيق
- الاستجابه

بدءا من **Exchange Online Protection**:
<p>

|منع/الكشف|تحقيق|استجابة|
|---|---|---|
|وتشمل التقنيات ما يلي:<ul><li>البريد المزعج</li><li>فيش</li><li>البرامج الضاره</li><li>البريد المجمع</li><li>التحليل الذكي للانتحال</li><li>الكشف عن الانتحال</li><li>عزل المسؤول</li><li>عمليات إرسال المسؤول والمستخدم من الإيجابيات الخاطئة والسلبيات الخاطئة</li><li>السماح/الحظر لعناوين URL والملفات</li><li>التقارير</li></ul>|<li>البحث في سجل التدقيق</li><li>تتبع الرسائل</li>|<li>الإزالة التلقائية بدون ساعة (ZAP)</li><li>تحسين قوائم السماح والحظر واختبارها</li>|

إذا كنت تريد البحث في EOP، **[فان انتقل إلى هذه المقالة](exchange-online-protection-overview.md)**.

نظرا لأن هذه المنتجات تراكمية، إذا قمت بتقييم Microsoft Defender لـ Office 365 P1 وقررت الاشتراك فيها، فستضيف هذه القدرات.

المكاسب مع **Defender لـ Office 365، الخطة 1** (حتى الآن):
<p>

|منع/الكشف|تحقيق|استجابة|
|---|---|---|
|تتضمن التقنيات كل شيء في EOP بالإضافة إلى:<ul><li>مرفقات خزينة</li><li>ارتباطات خزينة<li>حماية Microsoft Defender لـ Office 365 لأحمال العمل (على سبيل المثال. SharePoint Online أو Teams أو OneDrive for Business)</li><li>حماية وقت النقر في البريد الإلكتروني والعملاء Office Teams</li><li>مكافحة التصيد الاحتيالي في Defender لـ Office 365</li><li>حماية انتحال المستخدم والمجال</li><li>التنبيهات وواجهة برمجة تطبيقات تكامل SIEM للتنبيهات</li>|<li>واجهة برمجة تطبيقات تكامل SIEM للكشف</li><li>**أداة الكشف في الوقت الحقيقي**</li><li>تتبع عنوان URL</li>|<li>نفس</li></ul>

لذلك، Microsoft Defender لـ Office 365 P1 يتوسع على الجانب ***prevention** _ من المنزل، ويضيف أشكالا إضافية من _*_detection_**.

Microsoft Defender لـ Office 365 P1 يضيف أيضا **عمليات الكشف في الوقت الحقيقي** للتحقيقات. اسم أداة تتبع المخاطر هذه غامق لأن وجودها يعني بوضوح *معرفة* أن لديك Defender لـ Office 365 P1. لا يظهر في Defender لـ Office 365 P2.

المكاسب مع **Defender لـ Office 365، الخطة 2** (حتى الآن):
<p>

|منع/الكشف|تحقيق|استجابة|
|---|---|---|
|تتضمن التقنيات كل شيء في EOP، Microsoft Defender لـ Office 365 P1 بالإضافة إلى:<ul><li>نفس</li>|<li>**مستكشف المخاطر**</li><li>متعقب المخاطر</li><li>طرق عرض الحملة</li>|<li>التحقيق التلقائي والاستجابة (AIR)</li><li>AIR من مستكشف المخاطر</li><li>AIR للمستخدمين المخترقين</li><li>واجهة برمجة تطبيقات تكامل SIEM للتحقيقات التلقائية</li>

لذلك، Microsoft Defender لـ Office 365 P2 يتوسع على جانب ***التحقيق والاستجابة*** من المنزل، ويضيف قوة تتبع جديدة. اتمته.

في Microsoft Defender لـ Office 365 P2، تسمى أداة التتبع الأساسية **مستكشف المخاطر** بدلا من عمليات الكشف في الوقت الحقيقي. إذا رأيت مستكشف المخاطر عند الانتقال إلى مدخل Microsoft 365 Defender، فأنت في Microsoft Defender لـ Office 365 P2.

للوصول إلى تفاصيل Microsoft Defender لـ Office 365 P1 وP2، **[انتقل إلى هذه المقالة](defender-for-office-365.md)**.

> [!TIP]
> تختلف EOP Microsoft Defender لـ Office 365 أيضا عندما يتعلق الأمر للمستخدمين النهائيين. في EOP Defender لـ Office 365 P1، يكون التركيز على *الوعي*، ومن ثم فإن هاتين الخدمتين تتضمنان *رسالة التقرير Outlook الوظيفة الإضافية* حتى يتمكن المستخدمون من الإبلاغ عن رسائل البريد الإلكتروني التي يجدونها مريبة، لمزيد من التحليل. <p> في Defender لـ Office 365 P2 (الذي يحتوي على كل شيء في EOP وP1)، ينتقل التركيز إلى *مزيد من التدريب* للمستخدمين النهائيين، وبالتالي فإن مركز عمليات الأمان لديه حق الوصول إلى أداة *محاكي المخاطر* القوية، ومقاييس المستخدم النهائي التي يوفرها.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender لـ Office 365 الخطة 1 مقابل ورقة المعلومات المرجعية للخطة 2

سيساعدك هذا المرجع السريع على فهم القدرات التي تأتي مع كل اشتراك Microsoft Defender لـ Office 365. عند دمجها مع معرفتك بميزات EOP، يمكن أن تساعد صانعي القرار في الأعمال على تحديد Microsoft Defender لـ Office 365 الأفضل لاحتياجاتهم.

|Defender لـ Office 365 الخطة 1|Defender لـ Office 365 الخطة 2|
|---|---|
|قدرات التكوين والحماية والكشف: <ul><li>[مرفقات خزينة](safe-attachments.md)</li><li>[الارتباطات الآمنة](safe-links.md)</li><li>[المرفقات الآمنة لـ SharePoint وOneDrive وMicrosoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[الحماية من التصيد الاحتيالي في Defender لـ Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[عمليات الكشف في الوقت الحقيقي](threat-explorer.md)</li></ul>|قدرات Defender لـ Office 365 الخطة 1 <p> --- بالإضافة إلى --- <p> قدرات الأتمتة والتحقيق والمعالجة والتعليم: <ul><li>[متعقب المخاطر](threat-trackers.md)</li><li>[مستكشف المخاطر](threat-explorer.md)</li><li>[التحقيق التلقائي والاستجابة](office-365-air.md)</li><li>[تدريب محاكاة الهجوم](attack-simulation-training.md)</li><li>[البحث بشكل استباقي عن التهديدات مع التتبع المتقدم في Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[التحقيق في الحوادث في Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[التحقيق في التنبيهات في Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- يتم تضمين Microsoft Defender لـ Office 365 الخطة 2 في Office 365 E5 Office 365 A5 Microsoft 365 E5.

- يتم تضمين Microsoft Defender لـ Office 365 الخطة 1 في Microsoft 365 Business Premium.

- يتوفر كل Microsoft Defender لـ Office 365 الخطة 1 والخطة Defender لـ Office 365 2 كوظيفة إضافية لاشتراكات معينة. لمعرفة المزيد، إليك ارتباط آخر [حول توفر الميزة عبر خطط Microsoft Defender لـ Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- تتوفر ميزة [خزينة Documents](safe-docs.md) فقط للمستخدمين الذين لديهم تراخيص Microsoft 365 E5 أو الأمان في Microsoft 365 E5 (غير مضمنة في خطط Microsoft Defender لـ Office 365).

- إذا لم يتضمن اشتراكك الحالي Microsoft Defender لـ Office 365 وتريده، [فاتصل بالمبيعات لبدء إصدار تجريبي](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html)، وتعرف على كيفية عمل Microsoft Defender لـ Office 365 في مؤسستك.

- Microsoft Defender لـ Office 365 عملاء P2 لديهم حق الوصول إلى **تكامل Microsoft 365 Defender** للكشف عن الحوادث والتنبيهات ومراجعتها والاستجابة لها بكفاءة.

> [!TIP]
> ***تلميح Insider** _. يمكنك استخدام جدول المحتويات docs.microsoft.com للتعرف على EOP Microsoft Defender لـ Office 365. انتقل مرة أخرى إلى هذه الصفحة، [Office 365 نظرة عامة على الأمان](index.yml)، وستلاحظ أن تنظيم جدول المحتويات في الشريط الجانبي. يبدأ النشر (بما في ذلك الترحيل) ثم يستمر في الوقاية والكشف والتحقيق والاستجابة. <p> يتم تقسيم هذه البنية بحيث تكون مواضيع _ *Security Administration** متبوعة بمواضيع **عمليات الأمان** . إذا كنت عضوا جديدا في أي من دوري الوظيفة، فاستخدم الارتباط الموجود في هذا التلميح، ومعرفتك بجدول المحتويات، للمساعدة في معرفة المساحة. تذكر استخدام *ارتباطات الملاحظات* *وتصنيب المقالات* أثناء التنقل. تساعدنا الملاحظات على تحسين ما نقدمه لك.

## <a name="where-to-go-next"></a>أين تنتقل بعد ذلك

إذا كنت مسؤول أمان، فقد تحتاج إلى تكوين DKIM أو DMARC للبريد الخاص بك. قد تحتاج إلى طرح إعدادات الأمان 'الصارمة' المسبقة للمستخدمين الذين يتمتعون بالأولوية، أو البحث عن أحدث الميزات في المنتج. أو إذا كنت تستخدم عمليات الأمان، فقد تحتاج إلى الاستفادة من عمليات الكشف في الوقت الحقيقي أو مستكشف التهديدات للتحقيق والاستجابة، أو تدريب الكشف عن المستخدم النهائي باستخدام Attack Simulator. وفي كلتا الحالتين، إليك بعض التوصيات الإضافية لما يجب أن ننظر إليه بعد ذلك.

[مصادقة البريد الإلكتروني، بما في ذلك SPF وDKIM وDMARC (مع ارتباطات لإعداد الثلاثة)](email-validation-and-authentication.md)

[راجع التكوينات 'الذهبية' الموصى بها المحددة](recommended-settings-for-eop-and-office365.md) [واستخدم الإعدادات المسبقة الموصى بها لتكوين نهج الأمان بسرعة](preset-security-policies.md)

التعرف على [أحدث الميزات في Microsoft Defender لـ Office 365 (بما في ذلك تطويرات EOP)](whats-new-in-defender-for-office-365.md)

[استخدام مستكشف التهديدات أو عمليات الكشف في الوقت الحقيقي](threat-explorer.md)

استخدام [التدريب على محاكاة الهجوم](attack-simulation-training.md)
