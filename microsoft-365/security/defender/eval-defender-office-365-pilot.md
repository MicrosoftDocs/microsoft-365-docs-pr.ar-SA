---
title: Microsoft Defender لـ Office 365 التجريبية، استخدم التقييم في بيئة الإنتاج الخاصة بك
description: خطوات لتجربة التقييم الخاص بك مع مجموعات من المستخدمين النشطين والموجودين من أجل اختبار ميزات Microsoft Defender لـ Office 365 بشكل صحيح.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.custom: admindeeplinkEXCHANGE
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: fb246805ebf38cddfda6fe308d19e1dd1419531b
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748792"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Microsoft Defender لـ Office 365 الإصدار التجريبي

**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 3 من 3](eval-defender-office-365-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender لـ Office 365. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-office-365-overview.md).

استخدم الخطوات التالية لإعداد وتكوين الإصدار التجريبي Microsoft Defender لـ Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-pilot.png" alt-text="خطوات إنشاء الإصدار التجريبي في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/defender/m365-defender-office-pilot.png":::

- [الخطوة 1: إنشاء مجموعات تجريبية](#step-1-create-pilot-groups)
- [الخطوة 2: تكوين الحماية](#step-2-configure-protection)
- [الخطوة 3: تجربة القدرات — التعرف على المحاكاة والمراقبة والمقاييس](#step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics)

عند تقييم Microsoft Defender لـ Office 365، يمكنك اختيار تجربة مستخدمين محددين قبل تمكين النهج وفرضها لمؤسستك بأكملها. يمكن أن يساعد إنشاء مجموعات التوزيع في إدارة عمليات النشر. على سبيل المثال، أنشئ مجموعات مثل *Defender لـ Office 365 Users - Standard Protection* أو *Defender لـ Office 365 Users - Strict Protection* أو *Defender لـ Office 365 Users - Custom Protection* أو *Defender لـ Office 365  المستخدمون - الاستثناءات*.

قد لا يكون من الواضح سبب أن المصطلحات "قياسي" و"صارم" هي المصطلحات المستخدمة لهذه المجموعات، ولكن هذا سيصبح واضحا عند استكشاف المزيد حول الإعدادات المسبقة للأمان Defender لـ Office 365. تسمية المجموعات 'المخصصة' و'الاستثناءات' تتحدث عن نفسها، وعلى الرغم من أن معظم المستخدمين يجب أن يقعوا ضمن مجموعات *قياسية* *وصارمة* ومخصصة واستثناءات، فسيجمعون لك بيانات قيمة فيما يتعلق بإدارة المخاطر.

## <a name="step-1-create-pilot-groups"></a>الخطوة 1: إنشاء مجموعات تجريبية

يمكن إنشاء مجموعات التوزيع وتحديدها مباشرة في Exchange Online أو مزامنتها من Active Directory محلي.

1. سجل الدخول إلى Exchange مسؤول Center (EAC) باستخدام حساب تم منحه دور مسؤول المستلم أو تم تفويضه لأذونات إدارة المجموعة.
2. من قائمة التنقل، قم بتوسيع *المستلمين* وحدد *المجموعات*.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text=" عنصر القائمة &quot;مجموعات&quot; الذي سيتم النقر فوقه" lightbox="../../media/mdo-eval/1_mdo-eval-pilot.png":::

3. من لوحة معلومات المجموعات، حدد "إضافة مجموعة".

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="الخيار &quot;إضافة مجموعة&quot; الذي سيتم النقر فوقه" lightbox="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png":::

4. لنوع المجموعة، حدد *"التوزيع* " وانقر فوق "التالي".

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text=" المقطع &quot;اختيار نوع مجموعة&quot;" lightbox="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png":::

5. قم بتسمية المجموعة ووصفها ثم انقر فوق "التالي".

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="قسم &quot;إعداد الأساسيات&quot;" lightbox="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png":::

## <a name="step-2-configure-protection"></a>الخطوة 2: تكوين الحماية

يتم تكوين بعض القدرات في Defender لـ Office 365 وتشغيلها بشكل افتراضي، ولكن قد ترغب عمليات الأمان في رفع مستوى الحماية من الإعداد الافتراضي.

لم يتم تكوين بعض القدرات *بعد* . لديك ثلاثة خيارات لتكوين الحماية:

- **تعيين نهج الأمان المعينة مسبقا تلقائيا** — يتم توفير [نهج الأمان المعينة مسبقا](../office-365-security/preset-security-policies.md) كأسلوب لتعيين مستوى موحد من الحماية بسرعة عبر جميع الإمكانات. يمكنك الاختيار من **_بين standard_*_ أو _*_strict_**. النهج الجيد هو البدء بنهج الأمان المسبقة الإعداد ثم ضبط النهج بينما تتعلم المزيد حول القدرات وبيئة التهديد الفريدة الخاصة بك. الميزة هنا هي حماية مجموعات المستخدمين في أسرع وقت ممكن، مع القدرة على تعديل الحماية بعد ذلك. (يوصى بهذا الأسلوب.)
- **تكوين حماية الأساس يدويا** - إذا كنت تفضل تكوين البيئة بنفسك، يمكنك تحقيق *أساس* الحماية بسرعة باتباع الإرشادات الواردة في [الحماية من التهديدات](../office-365-security/protect-against-threats.md). باستخدام هذا النهج، يمكنك معرفة المزيد حول الإعدادات القابلة للتكوين. ويمكنك ضبط النهج لاحقا.
- **تكوين نهج الحماية *المخصصة*** — يمكنك أيضا إنشاء نهج حماية مخصصة وتعيينها كجزء من تقييمك. قبل البدء في تخصيص النهج، من المهم فهم الأسبقية التي يتم فيها تطبيق نهج الحماية هذه وفرضها. ستحتاج عمليات الأمان إلى إنشاء بعض النهج حتى إذا تم تطبيق الإعداد المسبق، بشكل محدد من أجل تحديد نهج الأمان للارتباطات الآمنة والمرفقات الآمنة.
> [!IMPORTANT]
> **إذا كنت بحاجة إلى تكوين نهج الحماية المخصصة**، يجب عليك فحص القيم التي تشكل تعريفات الأمان **القياسية** **والضيقة** هنا: *[الإعدادات الموصى بها ل EOP والأمان Microsoft Defender لـ Office 365](../office-365-security/recommended-settings-for-eop-and-office365.md)*. يتم أيضا سرد القيم الافتراضية، كما هو موضح قبل حدوث أي تكوين. احتفظ بجدول بيانات عن مكان انحراف البنية المخصصة.

### <a name="assign-preset-security-policies"></a>تعيين نهج الأمان المعينة مسبقا

يوصى بالبدء *بنهج الأساس الموصى بها* عند تقييم MDO ثم تحسينها حسب الحاجة على مدار فترة التقييم الخاصة بك.

يمكنك تمكين نهج EOP والحماية Defender لـ Office 365 الموصى بها بسرعة، وتعيينها إلى مستخدمين تجريبيين محددين أو مجموعات محددة كجزء من تقييمك. تقدم النهج المعينة مسبقا قالب حماية **قياسية** أساسيا أو قالب حماية **صارم** أكثر صرامة، والذي يمكن تعيينه بشكل مستقل أو دمجه.

فيما يلي [نهج الأمان المحددة مسبقا في EOP والمقالة Microsoft Defender لـ Office 365](../office-365-security/preset-security-policies.md) التي توضح الخطوات.

1. سجل الدخول إلى مستأجر Microsoft 365. استخدم حسابا له حق الوصول إلى مدخل Microsoft 365 Defender، تمت إضافته إلى دور إدارة المؤسسة في Office 365، أو دور مسؤول الأمان في Microsoft 365.
2. من قائمة التنقل، حدد *"قواعد & الشرطة* " ضمن "التعاون & البريد الإلكتروني".

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text=" عنصر قائمة قواعد & النهج المطلوب النقر فوقه" lightbox="../../media/mdo-eval/5_mdo-eval-pilot-policies.png":::

3. في لوحة معلومات "قواعد & النهج"، انقر فوق *"نهج التهديد*".

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text=" عنصر القائمة &quot;نهج التهديد&quot; الذي سيتم النقر فوقه" lightbox="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png":::

4. من مدخل Microsoft 365 Defender، قم بتوسيع إدارة المخاطر من قائمة التنقل ثم حدد Policy من القائمة الفرعية.
5. في لوحة معلومات النهج، انقر فوق *نهج الأمان المحددة مسبقا*.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="أنواع نهج التهديد" lightbox="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png":::

6. انقر فوق *"تحرير* " لتكوين النهج القياسي و/أو النهج الصارم وتعيينه.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="الإعدادات المختلفة المطبقة على نهج مختلفة في صفحة نهج الأمان المعينة مسبقا" lightbox="../../media/mdo-eval/8-mdo-eval-pilot-preset.png":::

7. أضف شروطا لتطبيق حماية الأساس ***EOP** _ على مستخدمين تجريبيين محددين، أو مجموعات من المستخدمين، حسب الحاجة، وحدد _Next* للمتابعة.

   على سبيل المثال، يمكن تطبيق شرط Defender لـ Office 365 للتقييمات التجريبية إذا كان المستلمون *أعضاء* *في مجموعة Defender لـ Office 365 Standard Protection* محددة، ثم تتم إدارتها عن طريق إضافة حسابات إلى المجموعة أو إزالتها منها.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="النهج التي تعتبر حماية EOP" lightbox="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png":::

8. أضف شروطا لتطبيق الحماية الأساسية ***MDO** _ على مستخدمين تجريبيين محددين، أو مجموعات من المستخدمين، حسب الحاجة. انقر فوق _Next* للمتابعة.

   على سبيل المثال، يمكن تطبيق شرط Defender لـ Office 365 للتقييمات التجريبية إذا كان المستلمون *أعضاء* *في مجموعة Defender لـ Office 365 Standard Protection* محددة ثم تمت إدارتها عن طريق إضافة / إزالة الحسابات عبر المجموعة.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="النهج التي تعتبر دفاعا عن حماية Office 365" lightbox="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png":::

9. راجع التغييرات التي أجريتها وتأكد من تعيين نهج الأمان المعينة مسبقا.
10. يمكن إدارة نهج الحماية المعينة مسبقا (إعادة تكوينها، وإعادة تطبيقها، وتعطيلها، وما إلى ذلك) عن طريق العودة إلى مدخل Microsoft 365 Defender > النهج & القواعد > نهج التهديد > والنقر فوق لوحة *نهج الأمان المعينة مسبقا*.

### <a name="configure-custom-protection-policies"></a>تكوين نهج الحماية المخصصة

تمنح قوالب النهج *القياسية* *أو الصارمة* Defender لـ Office 365 المحددة مسبقا لمستخدمي الإصدار التجريبي حماية الأساس الموصى بها. ومع ذلك، يمكنك أيضا إنشاء نهج حماية مخصصة وتعيينها كجزء من تقييمك.

من *المهم* أن تكون على دراية بأسبقية نهج الحماية هذه عند تطبيقها وفرضها، كما يوضح [ترتيب حماية البريد الإلكتروني وأسبقياته - Office 365](../office-365-security/how-policies-and-protections-are-combined.md).

يوفر الجدول أدناه مراجع وإرشادات إضافية لتكوين نهج الحماية المخصصة وتعيينها:

<br>

****

|السياسات|الوصف|المرجع|
|:---:|---|---|
|تصفية الاتصال|تحديد خوادم البريد الإلكتروني المصدر الجيدة أو غير الصالحة بواسطة عناوين IP الخاصة بها.|[تكوين نهج تصفية الاتصال الافتراضي في EOP](../office-365-security/configure-the-connection-filter-policy.md)|
|مكافحة البرامج الضارة|حماية المستخدمين من البرامج الضارة للبريد الإلكتروني بما في ذلك الإجراءات التي يجب اتخاذها والأشخاص الذين يجب إعلامهم إذا تم الكشف عن البرامج الضارة.|[تكوين نهج مكافحة البرامج الضارة في EOP](../office-365-security/configure-anti-malware-policies.md)|
|مكافحة الانتحال|حماية المستخدمين من محاولات تزييف الهوية باستخدام التحليل الذكي المخادعة والرؤى الذكية المخادعة.|[تكوين التحليل الذكي للانتحال في Defender لـ Office 365](../office-365-security/learn-about-spoof-intelligence.md)|
|مكافحة البريد العشوائي|حماية المستخدمين من البريد الإلكتروني العشوائي بما في ذلك الإجراءات التي يجب اتخاذها إذا تم الكشف عن البريد العشوائي.|[تكوين نهج مكافحة البريد العشوائي في Defender لـ Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|مكافحة التصيد الاحتيالي|حماية المستخدمين من هجمات التصيد الاحتيالي وتكوين تلميحات الأمان على الرسائل المشبوهة|[تكوين نهج مكافحة التصيد الاحتيالي في Defender لـ Office 365](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|مرفقات آمنة|حماية المستخدمين من المحتوى الضار في مرفقات البريد الإلكتروني والملفات في SharePoint وOneDrive وTeams.|[إعداد نهج المرفقات الآمنة في Defender لـ Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|الارتباطات الآمنة|حماية المستخدمين من فتح الارتباطات الضارة ومشاركتها في رسائل البريد الإلكتروني أو تطبيقات Office لسطح المكتب.|[إعداد نهج الارتباطات الآمنة في Defender لـ Office 365](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics"></a>الخطوة 3: تجربة القدرات والتعرف على المحاكاة والمراقبة والمقاييس

الآن بعد أن تم إعداد الإصدار التجريبي وتكوينه، من المفيد أن تصبح على دراية بأدوات محاكاة التقارير والمراقبة والهجمات الفريدة ل Microsoft Defender ل Microsoft 365.

<br>

****

|القدره|الوصف|معلومات إضافية|
|---|---|---|
|مستكشف المخاطر|مستكشف التهديدات هو أداة قوية بالقرب من الوقت الحقيقي لمساعدة فرق عمليات الأمان على التحقيق في التهديدات والاستجابة لها ويعرض معلومات حول البرامج الضارة المشتبه بها والتصيد الاحتيالي في البريد الإلكتروني والملفات في Office 365، بالإضافة إلى تهديدات الأمان والمخاطر الأخرى التي تتعرض لها مؤسستك.|[طرق العرض في مستكشف التهديدات والكشف في الوقت الحقيقي](../office-365-security/threat-explorer-views.md)|
|محاكي الهجوم|يمكنك استخدام تدريب محاكاة الهجوم في مدخل Microsoft 365 Defender لتشغيل سيناريوهات هجوم واقعية في مؤسستك، والتي تساعدك على تحديد المستخدمين المعرضين للخطر والعثور عليهم قبل أن يؤثر الهجوم الحقيقي على بيئتك.|[بدء استخدام التدريب على محاكاة الهجوم](../office-365-security/attack-simulation-training-get-started.md)|
|لوحة معلومات التقارير|في قائمة التنقل اليمنى، انقر فوق "تقارير" ثم قم بتوسيع عنوان التعاون & البريد الإلكتروني. تتعلق تقارير التعاون & البريد الإلكتروني بتحديد اتجاهات الأمان التي سيسمح لك بعضها باتخاذ إجراء (من خلال أزرار مثل "الانتقال إلى عمليات الإرسال")، والبعض الآخر الذي سيعرض الاتجاهات، مثل ملخص حالة Mailflow، وأعلى البرامج الضارة، واكتشافات الانتحال، والمستخدمين المخترقين، وزمن انتقال البريد، والارتباطات الآمنة، وتقارير المرفقات الآمنة. يتم إنشاء هذه المقاييس تلقائيا.|[عرض التقارير](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>الخطوات التالية

[تقييم Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender لـ Office 365](eval-defender-office-365-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)
