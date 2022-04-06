---
title: التجربة Microsoft Defender لـ Office 365، استخدم التقييم في بيئة الإنتاج
description: خطوات تجربة التقييم مع مجموعات من المستخدمين النشطين والموجودين من أجل اختبار ميزات Microsoft Defender لـ Office 365 بشكل صحيح.
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
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: d8cd0132c8b02ae29cf49c9a700a868fa3a93554
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501344"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>التجربة Microsoft Defender لـ Office 365

**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 3 من 3](eval-defender-office-365-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender لـ Office 365. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-office-365-overview.md).

استخدم الخطوات التالية لإعداد التجربة وتكوينها Microsoft Defender لـ Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-pilot.png" alt-text="خطوات إنشاء التجربة في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/defender/m365-defender-office-pilot.png":::

- [الخطوة 1: إنشاء مجموعات تجريبية](#step-1-create-pilot-groups)
- [الخطوة 2: تكوين الحماية](#step-2-configure-protection)
- [الخطوة 3: تجربة الإمكانات — التعرف على المحاكاة والمراقبة والمقاييس](#step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics)

عند تقييم Microsoft Defender لـ Office 365، يمكنك اختيار إجراء تجريبي لمستخدمين معينين قبل تمكين السياسات وفرضها لمنظمتك بكاملها. يمكن أن يساعد إنشاء مجموعات التوزيع على إدارة عمليات النشر. على سبيل المثال، قم بإنشاء مجموعات مثل *Defender لـ Office 365 المستخدمين -* الحماية القياسية أو Defender لـ Office 365 *المستخدمين -* حماية صارمة أو Defender لـ Office 365 المستخدمون *-* حماية *مخصصة أو Defender لـ Office 365  المستخدمون - الاستثناءات*.

قد لا يكون واضحا سبب استخدام المصطلحين "قياسي" و"صارم" لهذه المجموعات، ولكن سيصبح ذلك واضحا عند استكشاف المزيد حول إعدادات الأمان Defender لـ Office 365 المسبقة. تحدث تسمية المجموعات "المخصصة" و"الاستثناءات" عن نفسها، وعلى الرغم من أن معظم المستخدمين يجب أن يقعوا  ضمن المجموعات القياسية والمتقيدة، فإن المجموعات المخصصة والاستثناءات ستجمع بيانات قيمة بالنسبة لك فيما يتعلق بإدارة المخاطر.

## <a name="step-1-create-pilot-groups"></a>الخطوة 1: إنشاء مجموعات تجريبية

يمكن إنشاء مجموعات التوزيع تعريفها مباشرة في Exchange Online أو مزامنتها من Active Directory محلي.

1. سجل الدخول إلى مركز إدارة Exchange (EAC) باستخدام حساب تم منحه دور مسؤول المستلم أو تم تفويض أذونات إدارة المجموعة له.
2. من قائمة التنقل، قم بتوسيع *المستلمين* وحدد *مجموعات*.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text=" عنصر القائمة &quot;مجموعات&quot; الذي يجب النقر فوقه" lightbox="../../media/mdo-eval/1_mdo-eval-pilot.png":::

3. من لوحة معلومات المجموعات، حدد "إضافة مجموعة".

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="الخيار &quot;إضافة مجموعة&quot; الذي يجب النقر فوقه" lightbox="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png":::

4. بالنسبة لنوع المجموعة، حدد *توزيع* وانقر فوق التالي.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text=" المقطع &quot;اختيار نوع مجموعة&quot;" lightbox="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png":::

5. قم امنح المجموعة اسما ووصفا، ثم انقر فوق التالي.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="القسم &quot;إعداد الأساسيات&quot;" lightbox="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png":::

## <a name="step-2-configure-protection"></a>الخطوة 2: تكوين الحماية

يتم تكوين Defender لـ Office 365 بشكل افتراضي، ولكن قد ترغب عمليات الأمان في رفع مستوى الحماية من الإعداد الافتراضي.

لم يتم *بعد تكوين بعض* الإمكانات. لديك ثلاثة خيارات لتكوين الحماية:

- **تعيين سياسات الأمان** المعينة مسبقا تلقائيا — [يتم](../office-365-security/preset-security-policies.md) توفير سياسات الأمان المعينة مسبقا كطريقة لتعيين مستوى حماية موحد بسرعة عبر جميع الإمكانات. يمكنك الاختيار من **_standard_*_ أو _*_strict_**. النهج الجيد هو البدء بنهج أمان معدة مسبقا ثم ضبط النهج عندما تتعلم المزيد حول الإمكانات وبيئة التهديدات الفريدة الخاصة بك. الميزة هنا هي أنك تحمي مجموعات من المستخدمين بأسرع وقت ممكن، مع إمكانية تعديل الحماية بعد ذلك. (يوصى باستخدام هذا الأسلوب.)
- **تكوين حماية الأساس يدويا**— إذا كنت تفضل تكوين البيئة بنفسك، يمكنك بسرعة تحقيق أساس للحماية باتباع الإرشادات في الحماية [من التهديدات](../office-365-security/protect-against-threats.md). باستخدام هذا النهج، يمكنك التعرف على المزيد حول الإعدادات التي يمكن تكوينها. كما يمكنك ضبط النهج في وقت لاحق.
- **تكوين *سياسات* الحماية المخصصة** — يمكنك أيضا إنشاء سياسات حماية مخصصة وتعيينها كجزء من التقييم. قبل بدء تخصيص السياسات، من المهم فهم الأسبقية التي يتم فيها تطبيق سياسات الحماية هذه وتطبيقها. ستحتاج عمليات الأمان إلى إنشاء بعض السياسات حتى إذا تم تطبيق الإعداد المسبق، بشكل محدد من أجل تعريف سياسات الأمان خزينة الارتباطات خزينة المرفقات.
> [!IMPORTANT]
> **إذا كنت بحاجة** إلى تكوين سياسات حماية مخصصة، يجب فحص القيم التي تكون تعريفات الأمان القياسية والمتقيدة هنا: الإعدادات المستحسنة ل *[EOP Microsoft Defender لـ Office 365 الأمان](../office-365-security/recommended-settings-for-eop-and-office365.md)*. يتم أيضا سرد القيم الافتراضية، كما هو مشاهد قبل أي تكوين. احتفظ ب جدول بيانات حيث ينحرف البناء المخصص.

### <a name="assign-preset-security-policies"></a>تعيين سياسات أمان معينة مسبقا

من المستحسن أن تبدأ ونهج الأساس الموصى  بها عند تقييم MDO ثم تحسينها حسب الحاجة خلال فترة التقييم.

يمكنك تمكين EOP الموصى Defender لـ Office 365 ونهج الحماية بسرعة، وتعيينها لمستخدمين تجريبيين معينين أو مجموعات معرفة كجزء من التقييم. توفر السياسات المعينة مسبقا قالب حماية  قياسي أساسي أو قالب حماية صارمة أكثر  صرامة، يمكن تعيينه بشكل مستقل أو دمجه.

فيما يلخص هذا المقال سياسات الأمان التي تم Microsoft Defender لـ Office 365 مسبقا في [EOP](../office-365-security/preset-security-policies.md) والخطوات.

1. سجل دخولك إلى Microsoft 365 المستأجر. استخدم حسابا مع إمكانية الوصول إلى مدخل Microsoft 365 Defender، يضاف إلى دور إدارة المؤسسة في Office 365 أو دور مسؤول الأمان في Microsoft 365.
2. من قائمة التنقل، حدد & *القواعد ضمن* البريد الإلكتروني & التعاون.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text=" عنصر القائمة & &quot;&&quot; الذي يجب النقر فوقه" lightbox="../../media/mdo-eval/5_mdo-eval-pilot-policies.png":::

3. على لوحة المعلومات نهج &، انقر فوق *نهج التهديدات*.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text=" عنصر القائمة &quot;سياسات التهديدات&quot; الذي يجب النقر فوقه" lightbox="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png":::

4. من مدخل Microsoft 365 Defender، قم بتوسيع إدارة المخاطر من قائمة التنقل ثم حدد نهج من القائمة الفرعية.
5. على لوحة معلومات النهج، انقر فوق *نهج الأمان المحددة مسبقا*.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="أنواع سياسات المخاطر" lightbox="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png":::

6. انقر *فوق* تحرير لتكوين النهج القياسي و/أو النهج الصارم وتعيينه.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="الإعدادات المختلفة المطبقة على مختلف السياسات على صفحة &quot;سياسات الأمان&quot; التي تم تعيينها مسبقا" lightbox="../../media/mdo-eval/8-mdo-eval-pilot-preset.png":::

7. أضف شروطا لتطبيق الحماية الأساسية ***EOP** _لمستخدمين تجريبيين معينين أو مجموعات من المستخدمين، حسب الحاجة، وحدد _Next* للمتابعة.

   على سبيل المثال، Defender لـ Office 365 تطبيق شرط تقييم تجريبي إذا كان المستلمون أعضاء في مجموعة *حماية قياسية Defender لـ Office 365* محددة، ثم تتم إدارتهم بإضافة حسابات إلى المجموعة أو إزالتها منها.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="السياسات التي تعتبر من حماية EOP" lightbox="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png":::

8. أضف شروطا لتطبيق الحماية الأساسية ***MDO** _ لمستخدمين تجريبيين معينين أو مجموعات من المستخدمين، حسب الحاجة. انقر _Next* للمتابعة.

   على سبيل المثال، Defender لـ Office 365 تطبيق شرط تقييم تجريبي إذا كان المستلمون أعضاء في مجموعة حماية قياسية Defender لـ Office 365 محددة، ثم تتم إدارتهم عن طريق إضافة /إزالة حسابات عبر المجموعة.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="السياسات التي تعتبر ذات Office 365 حماية" lightbox="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png":::

9. قم بمراجعة التغييرات وتأكيدها لتعيين سياسات أمان معينة مسبقا.
10. يمكن إدارة سياسات الحماية المحددة مسبقا (إعادة تكوينها أو إعادة تطبيقها أو تعطيلها وغير ذلك) عن طريق العودة إلى مدخل Microsoft 365 Defender > قواعد & > سياسات التهديدات > والنقر فوق لوحة سياسات الأمان التي تم الإعداد المسبق لها.

### <a name="configure-custom-protection-policies"></a>تكوين سياسات الحماية المخصصة

تمنح *قوالب نهج المعايير* *أو Defender لـ Office 365* المحددة مسبقا للمستخدمين التجريبيين الحماية الأساسية الموصى بها. ومع ذلك، يمكنك أيضا إنشاء سياسات حماية مخصصة وتعيينها كجزء من التقييم.

من المهم *أن تكون* على علم بما تتخذه سياسات الحماية هذه من أسبقية عند تطبيقها وتطبيقها، كما هو موضح في ترتيب حماية البريد الإلكتروني وأسبقية [Office 365](../office-365-security/how-policies-and-protections-are-combined.md) البريد الإلكتروني.

يوفر الجدول أدناه مراجع وإرشادات إضافية لتكوين سياسات الحماية المخصصة وتعيينها:

<br>

****

|النهج|الوصف|المرجع|
|:---:|---|---|
|تصفية الاتصال|حدد خوادم البريد الإلكتروني الجيدة أو غير الصالحة المصدر حسب عناوين IP الخاصة بها.|[تكوين نهج تصفية الاتصال الافتراضي في EOP](../office-365-security/configure-the-connection-filter-policy.md)|
|مكافحة البرامج الضارة|حماية المستخدمين من البرامج الضارة للبريد الإلكتروني بما في ذلك الإجراءات التي يجب اتخاذها ومن يجب إعلامه إذا تم الكشف عن البرامج الضارة.|[تكوين سياسات مكافحة البرامج الضارة في EOP](../office-365-security/configure-anti-malware-policies.md)|
|مكافحة ال انتحال|حماية المستخدمين من المحاولات المنتحلة باستخدام المعلومات الاستخبارية المنتحلة ورؤى المعلومات الاستخبارية المنتحلة.|[تكوين المعلومات المنتحلة في Defender لـ Office 365](../office-365-security/learn-about-spoof-intelligence.md)|
|مكافحة البريد العشوائي|حماية المستخدمين من البريد الإلكتروني العشوائي بما في ذلك الإجراءات التي يجب اتخاذها إذا تم اكتشاف البريد العشوائي.|[تكوين سياسات مكافحة البريد العشوائي في Defender لـ Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|مكافحة التصيد الاحتيالي|حماية المستخدمين من هجمات التصيد الاحتيالي وتكوين تلميحات الأمان على الرسائل المريبة|[تكوين سياسات مكافحة التصيد الاحتيالي في Defender لـ Office 365](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|خزينة المرفقات|حماية المستخدمين من المحتوى الضار في مرفقات وملفات البريد الإلكتروني في SharePoint OneDrive Teams.|[إعداد سياسات المرفقات الآمنة في Defender لـ Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|الارتباطات الآمنة|حماية المستخدمين من فتح الارتباطات الضارة ومشاركتها في رسائل البريد الإلكتروني أو Office سطح المكتب.|[إعداد سياسات الارتباطات الآمنة في Defender لـ Office 365](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics"></a>الخطوة 3: تجربة الإمكانات و التعرف على المحاكاة والمراقبة والمقاييس

الآن وقد تم إعداد طيارك وتكوينه، من المفيد أن تصبح على دراية بأدوات محاكاة الهجمات والمتابعة وإعداد التقارير التي تنفرد بها Microsoft Defender Microsoft 365.

<br>

****

|الإمكانية|الوصف|معلومات إضافية|
|---|---|---|
|مستكشف التهديدات|إن "مستكشف التهديدات" هو أداة فعالة في الوقت الحقيقي لمساعدة فرق عمليات الأمان على التحقق من التهديدات والاستجابة لها وعرض معلومات حول البرامج الضارة والتصيد الاحتيالي المشتبه به في البريد الإلكتروني والملفات في Office 365، بالإضافة إلى التهديدات والمخاطر الأخرى التي تواجهها مؤسستك.|[طرق العرض في "مستكشف التهديدات" والكشف في الوقت الحقيقي](../office-365-security/threat-explorer-views.md)|
|محاكي الهجوم|يمكنك استخدام التدريب على محاكاة الهجمات في مدخل Microsoft 365 Defender لتشغيل سيناريوهات هجوم واقعية في مؤسستك، مما يساعدك على تحديد المستخدمين الضعاف والعثور علىهم قبل أن يؤثر هجوم حقيقي على بيئتك.|[بدء استخدام التدريب على محاكاة الهجمات](../office-365-security/attack-simulation-training-get-started.md)|
|لوحة معلومات التقارير|في قائمة التنقل اليسرى، انقر فوق تقارير ثم قم بتوسيع عنوان البريد الإلكتروني & التعاون. تقارير تعاون البريد الإلكتروني & حول تحديد اتجاهات الأمان التي سيتيح لك بعضها اتخاذ إجراء (من خلال أزرار مثل "الانتقال إلى عمليات الإرسال")، والبعض الآخر الذي سيعرض الاتجاهات، مثل ملخص حالة تدفق البريد، والبرامج الضارة العلوية، والكشف عن الانتحال، والمستخدمين المعرضين للخطر، زمن الانتقال للبريد، ارتباطات خزينة، تقارير مرفقات خزينة. يتم إنشاء هذه المقاييس تلقائيا.|[عرض التقارير](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>الخطوات التالية

[تقييم Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)

العودة إلى نظرة عامة [حول تقييم](eval-defender-office-365-overview.md) Microsoft Defender لـ Office 365

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)
