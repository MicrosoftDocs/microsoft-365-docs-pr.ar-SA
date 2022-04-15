---
title: أمان Office 365 بما في ذلك Microsoft Defender لـ Office 365 وExchange Online Protection
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
description: الأمان في Office 365، من EOP إلى Defender لـ Office 365 الخطتان 1 و2، القياسي مقابل تكوينات الأمان الصارمة، والمزيد. اعرف ممتلكاتك وكيفية تأمينها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a9f480575c712488a17dc7e9e91320edc11d0e50
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: HT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64835898"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>نظرة عامة على أمان Microsoft Defender لـ Office 365

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)

ستعرفك هذه المقالة على خصائص أمان Microsoft Defender الجديدة لـ Office 365 في السحابة. سواء كنت جزءاً من مركز عمليات الأمان، أو كنت مسؤول أمان جديداً في هذا المجال، أو تريد تجديداً للمعلومات، فلنبدأ.

> [!CAUTION]
> إذا كنت تستخدم **Outlook.com** أو **Microsoft 365 Family** أو **Microsoft 365 Personal** وتحتاج إلى *روابط آمنة* أو *معلومات المرفقات* الآمنة، ***فانقر فوق هذا الارتباط***: [أمان Outlook.com المتقدم لمشتركي Microsoft 365](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>ما هو أمان Defender لـ Office 365

يأتي كل اشتراك في Office 365 مزوداً بقدرات أمان. تعتمد الأهداف والإجراءات التي يمكنك اتخاذها على تركيز هذه الاشتراكات المختلفة. في أمان Office 365، هناك ثلاث خدمات (أو منتجات) أمان رئيسية مرتبطة بنوع اشتراكك:

1. Exchange Online Protection (EOP)
1. خطة 1 من Microsoft Defender لـ Office 365 (Defender لـ Office خطة 1)
1. خطة 2 من Microsoft Defender لـ Office 365 (Defender لـ Office خطة 2)

> [!NOTE]
> إذا اشتريت اشتراكك وتحتاج إلى طرح ميزات الأمان في *الوقت الحالي*، فانتقل إلى الخطوات الواردة في مقالة [الحماية ضد التهديدات](protect-against-threats.md). إذا كنت جديداً في اشتراكك وترغب في معرفة ترخيصك قبل أن تبدأ، فاستعرض الفوترة > منتجاتك في [مركز إدارة Microsoft 365](https://admin.microsoft.com/AdminPortal/#/homepage).

يعتمد أمان Office 365 على إجراءات الحماية الأساسية التي تقدمها EOP. EOP موجود في أي اشتراك حيث يمكن العثور على علب بريد Exchange Online (تذكر أن جميع منتجات الأمان التي تمت مناقشتها هنا مستندة إلى السحابة).

قد تكون معتاداً على رؤية هذه المكونات الثلاثة تمت مناقشتها بهذه الطريقة:

|EOP|خطة 1 من Microsoft Defender لـ Office 365|خطة 2 من Microsoft Defender لـ Office 365|
|---|---|---|
|يمنع الهجمات الواسعة والمعروفة والمعتمدة على الحجم.|يحمي البريد الإلكتروني والتعاون من اختراق البرامج الضارة والاحتيال والبريد الإلكتروني الخاص بالعمل.|يضيف تحقيق ما بعد الاختراق، والصيد، والاستجابة، بالإضافة إلى الأتمتة والمحاكاة (للتدريب).|

ولكن فيما يتعلق بالهندسة المعمارية، فلنبدأ بالتفكير في كل قطعة على أنها طبقات تراكمية للأمان، لكل منها تأكيد أمني. المزيد مثل هذا:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP وMicrosoft Defender لـ Office 365 وعلاقاتهما مع بعضهما البعض مع التركيز على الخدمة، بما في ذلك ملاحظة لمصادقة البريد الإلكتروني" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

على الرغم من أن كل خدمة من هذه الخدمات تؤكد على هدف من بين الحماية والكشف والتحقيق والاستجابة، *يمكن **لجميع** الخدمات تنفيذ _ *_أي_** من أهداف الحماية والكشف والتحقيق والاستجابة.

جوهر أمان Office 365 هو حماية EOP. يحتوي Microsoft Defender لـ خطة 1 من Office 365 على EOP فيه. تحتوي خطة 2 من Defender for Office 365 على خطة 1 وEOP. الهيكل تراكمي. لهذا السبب، عند تكوين هذا المنتج، يجب أن تبدأ بـ EOP وتعمل على Defender لـ Office 365.

على الرغم من أن تكوين مصادقة البريد الإلكتروني يتم في DNS العام، فمن المهم تكوين هذه الميزة للمساعدة في الدفاع ضد تزييف الهوية. *إذا كان لديك EOP*، ***فيجب عليك [تكوين مصادقة البريد الإلكتروني](email-validation-and-authentication.md)***.

إذا كان لديك Office 365 E3 أو أقل، فلديك EOP، ولكن مع خيار شراء Defender مستقل للخطة 1 من Office 365 من خلال الترقية. إذا كان لديك Office 365 E5، فهذا يعني أن لديك بالفعل Defender للخطة 2 من Office 365.

> [!TIP]
> إذا كان اشتراكك ليس Office 365 E3 أو E5، فلا يزال بإمكانك التحقق لمعرفة ما إذا كان لديك خيار الترقية إلى Microsoft Defender للخطة 1 Office 365. إذا كنت مهتماً، تسرد [صفحة الويب](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) هذه الاشتراكات المؤهلة لترقية Microsoft Defender للخطة 1 Office 365 (تحقق من نهاية الصفحة للحصول على الطباعة الدقيقة).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>سلم أمان Office 365 من EOP إلى Microsoft Defender لـ Office 365

> [!IMPORTANT]
> تعرّف على التفاصيل الموجودة في هذه الصفحات: [Exchange Online Protection](exchange-online-protection-overview.md) و[Defender لـ Office 365](defender-for-office-365.md).

قد يكون من الصعب معرفة ما يجعل إضافة خطط Microsoft Defender لـ Office 365 ميزة لإدارة تهديدات EOP الخالصة للوهلة الأولى. للمساعدة في معرفة ما إذا كان مسار الترقية مناسباً لمؤسستك، فلنلقِ نظرة على إمكانيات كل منتج عندما يتعلق الأمر بما يلي:

- منع التهديدات واكتشافها
- قيد التحقيق
- الاستجابة

البدء بـ **Exchange Online Protection**:
<p>

|منع/اكتشاف|تحقيق|استجابة|
|---|---|---|
|التكنولوجيا تشمل:<ul><li>بريد عشوائي</li><li>التصيد الاحتيالي</li><li>برنامج ضار</li><li>البريد المجمّع</li><li>التحليل الذكي لتزييف الهوية</li><li>الكشف عن الانتحال</li><li>عزل المسؤول</li><li>تقديمات المسؤول والمستخدم للإيجابيات الكاذبة والسلبيات الكاذبة</li><li>السماح/حظر لعناوين URL والملفات</li><li>التقارير</li></ul>|<li>البحث في سجل التدقيق</li><li>تتبع الرسائل</li>|<li>المسح اللحظي للرسائل غير المرغوبة (ZAP)</li><li>تحسين صياغة قوائم السماح والمنع واختبارها</li>|

إذا كنت تريد البحث في EOP، **[فانتقل إلى هذه المقالة](exchange-online-protection-overview.md)**.

نظراً لأن هذه المنتجات تراكمية، إذا قمت بتقييم Microsoft Defender للخطة 1 من Office 365 وقررت الاشتراك فيه، فستضيف هذه القدرات.

المكاسب مع **Defender لـ Office 365، الخطة 1** (حتى الآن):
<p>

|منع/اكتشاف|تحقيق|استجابة|
|---|---|---|
|تشمل التقنيات كل شيء في EOP plus:<ul><li>مرفقات آمنة</li><li>الارتباطات الآمنة<li>حماية Microsoft Defender لـ Office 365 لأحمال العمل (على سبيل المثال. (SharePoint Online وTeams وOneDrive for Business)</li><li>حماية وقت النقر في البريد الإلكتروني وعملاء Office وTeams</li><li>مكافحة التصيد الاحتيالي في Defender لـ Office 365</li><li>حماية انتحال هوية المستخدم والمجال</li><li>التنبيهات وتكامل واجهة برمجة تطبيقات SIEM للتنبيهات</li>|<li>التنبيهات وتكامل واجهة برمجة تطبيقات SIEM للاستكشافات</li><li>**أدوات الكشف في الوقت الحقيقي**</li><li>تعقب عناوين URL</li>|<li>متشابه</li></ul>

لذلك، يعمل Microsoft Defender for Office 365 P1 على توسيع نطاق ***الوقاية** _ وإضافة أشكال إضافية من _*_الكشف_**.

يضيف Microsoft Defender for Office 365 P1 أيضاً اكتشافات في **الوقت الحقيقي** للفحوصات. اسم أداة البحث عن التهديدات بخط غامق لأن وجودها وسيلة واضحة *لمعرفة* أن لديك Defender لـ Office 365 P1. لا يظهر في Defender لـ Office 365 P2.

المكاسب مع **Defender لـ Office 365، الخطة 2** (حتى الآن):
<p>

|منع/اكتشاف|تحقيق|استجابة|
|---|---|---|
|تتضمن التقنيات كل شيء في EOP وMicrosoft Defender لـ Office 365 P1 plus:<ul><li>متشابه</li>|<li>**طرق عرض مستكشف المخاطر**</li><li>متعقب المخاطر</li><li>طرق عرض الحملة</li>|<li>التحقيق التلقائي والاستجابة (AIR)</li><li>الفحص والاستجابة التلقائيين من مستكشف المخاطر</li><li>الفحص والاستجابة التلقائيين للمستخدمين المخترقين</li><li>واجهة برمجة تطبيقات تكامل SIEM للفحوصات الآلية</li>

لذلك، يتوسع Microsoft Defender لـ Office 365 P2 في ***جانب التحقيق والاستجابة*** في المنزل، ويضيف قوة صيد جديدة. التشغيل التلقائي.

في Microsoft Defender for Office 365 P2، تسمى أداة الصيد الأساسية **مستكشف المخاطر** بدلاً من الاكتشافات في الوقت الفعلي. إذا رأيت مستكشف التهديدات عند الانتقال إلى مدخل Microsoft 365 Defender، فأنت في Microsoft Defender لـ Office 365 P2.

للوصول إلى تفاصيل Microsoft Defender لـ Office 365 P1 وP2، **[انتقل إلى هذه المقالة](defender-for-office-365.md)**.

> [!TIP]
> يختلف EOP و Microsoft Defender for Office 365 أيضاً عندما يتعلق الأمر بالمستخدمين النهائيين. في EOP وDefender for Office 365 P1، ينصب التركيز على *الوعي*، ومن ثم فإن هاتين الخدمتين تتضمنان *رسالة تقرير الوظيفة الإضافية Outlook* حتى يتمكن المستخدمون من الإبلاغ عن رسائل البريد الإلكتروني التي يجدونها مريبة، لمزيد من التحليل. <p> في Defender for Office 365 P2 (الذي يحتوي على كل شيء في EOP وP1)، ينتقل التركيز إلى مزيد من *التدريب للمستخدمين النهائيين*، وبالتالي يتمتع مركز عمليات الأمان بإمكانية الوصول إلى أداة *محاكاة التهديدات* القوية ومقاييس المستخدم النهائي التي يوفرها.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>ورقة معلومات مرجعية لـ Microsoft Defender لـ Office 365 (الخطة 1) مقابل الخطة 2

سيساعدك هذا المرجع السريع في فهم الإمكانات التي تأتي مع كل اشتراك في Microsoft Defender لـ Office 365. عندما يقترن بمعرفتك بميزات EOP، يمكن أن يساعد صانعي القرار في الأعمال على تحديد ما هو Microsoft Defender for Office 365 الأفضل لاحتياجاتهم.

|Microsoft Defender للخطة 1 من Office 365|Microsoft Defender للخطة 2 من Office 365|
|---|---|
|إمكانيات التكوين، والحماية، والكشف: <ul><li>[مرفقات آمنة](safe-attachments.md)</li><li>[الارتباطات الآمنة](safe-links.md)</li><li>[المرفقات الآمنة لـ SharePoint وOneDrive وMicrosoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[الحماية من التصيد الاحتيالي في Defender لـ Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[عمليات الكشف في الوقت الحقيقي](threat-explorer.md)</li></ul>|قدرات Microsoft Defender للخطة 1 من Office 365 <p> Plus <p> المستخدمون المحميون بالأتمتة والاستقصاء والمعالجة والتعلقدرات الأتمتة والتحقيق والمعالجة والتعليم: <ul><li>[متعقب المخاطر](threat-trackers.md)</li><li>[مستكشف المخاطر](threat-explorer.md)</li><li>[التحقيق التلقائي والاستجابة (AIR)](office-365-air.md)</li><li>[أتمتة المحاكاة في التدريب على محاكاة الهجوم](attack-simulation-training.md)</li><li>[البحث عن التهديدات بشكل استباقي باستخدام الصيد المتقدم في Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[التحقيق في الحوادث في Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[التحقيق في التنبيهات في Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- تم تضمين Microsoft Defender لـ Office 365 (الخطة 2) في Office 365 E5 وOffice 365 A5 وMicrosoft 365 E5.

- تم تضمين Microsoft Defender لـ Office 365 (الخطة 1) في Microsoft 365 Business Premium.

- يتوفر كل من Microsoft Defender لـ Office 365 (الخطة 1) وDefender لـ Office 365 (الخطة 2) كإضافة لبعض الاشتراكات. لمعرفة المزيد، يوجد ارتباط آخر [متوفر عبر خطط Microsoft Defender لـ Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- ميزة [المستندات الآمنة](safe-docs.md) متاحة فقط للمستخدمين الذين لديهم تراخيص أمان Microsoft 365 E5 أو Microsoft 365 E5 (غير مضمنة في خطط Microsoft Defender لـ Office 365).

- إذا كان اشتراكك الحالي لا يتضمن Microsoft Defender لـ Office 365 وتريده، [فاتصل بالمبيعات لبدء نسخة تجريبية](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html)، واكتشف كيف يمكن أن يعمل Microsoft Defender لـ Office 365 في مؤسستك.

- يتمتع عملاء Microsoft Defender for Office 365 P2 بإمكانية الوصول إلى **تكامل Microsoft 365 Defender** لاكتشاف الحوادث والتنبيهات ومراجعتها والرد عليها بكفاءة.

> [!TIP]
> ***مركز Insider** _. يمكنك استخدام جدول المحتويات docs.microsoft.com للتعرّف على EOP وMicrosoft Defender لـ Office 365. انتقل مرة أخرى إلى هذه الصفحة، [نظرة عامة على أمان Office 365](index.yml)، وستلاحظ تنظيم جدول المحتويات في الشريط الجانبي. يبدأ بالنشر (بما في ذلك الترحيل) ثم يستمر في المنع والكشف والتحقيق والاستجابة. <p> يتم تقسيم هذه البنية بحيث تتبع موضوعات *إدارة الأمان* مواضيع **عمليات الأمان**. إذا كنت عضواً جديداً في أي دور وظيفي، فاستخدم الارتباط الموجود في هذه النصيحة، ومعرفتك بجدول المحتويات، للمساعدة في تعلم المساحة. تذكر استخدام *ارتباطات التعليقات* و *تقييم المقالات* أثناء التنقل. تساعدنا التعليقات على تحسين ما نقدمه لك.

## <a name="where-to-go-next"></a>التالي، الانتقال إلى

إذا كنت مسؤول أمان، فقد تحتاج إلى تكوين DKIM أو DMARC لبريدك. قد ترغب في طرح إعدادات أمان "صارمة" للمستخدمين ذوي الأولوية، أو البحث عن الجديد في المنتج. أو إذا كنت تستخدم Security Ops، فقد ترغب في الاستفادة من الاكتشافات في الوقت الفعلي أو Threat Explorer للتحقيق والرد، أو تدريب اكتشاف المستخدم النهائي باستخدام Attack Simulator. في كلتا الحالتين، إليك بعض التوصيات الإضافية لما يجب البحث عنه بعد ذلك.

[مصادقة البريد الإلكتروني، بما في ذلك SPF وDKIM وDMARC (مع روابط لإعداد الثلاثة)](email-validation-and-authentication.md)

[راجع التكوينات "الذهبية" المحددة الموصى بها](recommended-settings-for-eop-and-office365.md) [واستخدم الإعدادات المسبقة الموصى بها لتكوين نهج الأمان بسرعة](preset-security-policies.md)

تعرّف على [ما هو الجديد في Microsoft Defender لـ Office 365 (بما في ذلك تطورات EOP)](whats-new-in-defender-for-office-365.md)

[استخدام مستكشف المخاطر وعمليات الاستكشاف الفورية](threat-explorer.md)

استخدام [التدريب على محاكاة الهجوم](attack-simulation-training.md)
