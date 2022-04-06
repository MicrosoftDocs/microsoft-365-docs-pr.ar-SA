---
title: الإبلاغ عن قواعد ASR Microsoft Defender لنقطة النهاية وإصلاحها
description: يصف هذا الموضوع كيفية الإبلاغ عن قواعد ASR Microsoft Defender لنقطة النهاية وإصلاحها
keywords: قواعد الحد من سطح الهجوم، asr، hips، نظام منع اقتحام المضيف، قواعد الحماية، مكافحة استغلال، مكافحة استغلال، استغلال، منع الإصابة، microsoft defender لنقطة النهاية
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: b1a90ec887f62a3c486c30ed50b87482de451c01
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470980"
---
# <a name="report-and-troubleshoot-microsoft-defender-for-endpoint-asr-rules"></a>الإبلاغ عن قواعد ASR Microsoft Defender لنقطة النهاية وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

إن <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender الجديد</a> هو واجهة جديدة لمراقبة الأمان وإدارته عبر هويات Microsoft وبياناته والأجهزة والتطبيقات والبنية الأساسية الخاصة بك. يمكنك هنا عرض حالة أمان مؤسستك بسهولة، والعمل على تكوين الأجهزة والمستخدمين والتطبيقات، والحصول على تنبيهات حول نشاط مريب. إن Microsoft 365 Defender الإلكتروني مخصص لمسؤولي الأمان وفرق عمليات الأمان لإدارة المؤسسة وحمايتها بشكل أفضل. تفضل بزيارة Microsoft 365 Defender على<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender،</a> نقدم لك نظرة كاملة على تكوين قواعد ASR الحالية والأحداث في مكانك. تجدر الإشارة إلى أنه يجب أن يتم إحاطة أجهزتك Microsoft Defender لنقطة النهاية الخدمة حتى يتم ملء هذه التقارير.
إليك لقطة شاشة من مدخل Microsoft 365 Defender (ضمن **تقليل** \>  \> مساحة الهجوم على أجهزة **التقارير**). على مستوى الجهاز، حدد **تكوين** من جزء قواعد **تقليل مساحة** الهجوم. يتم عرض الشاشة التالية، حيث يمكنك تحديد جهاز معين والتحقق من تكوين قاعدة ASR الفردية الخاصة به.

:::image type="content" source="images/asrrulesnew.png" alt-text="صفحة قواعد ASR" lightbox="images/asrrulesnew.png":::

## <a name="microsoft-defender-for-endpoint---advanced-hunting"></a>Microsoft Defender لنقطة النهاية - الصيد المتقدم

إحدى أكثر ميزات Microsoft Defender لنقطة النهاية هي الصيد المتقدم. إذا كنت غير مألوف بالنسبة إلى الصيد المتقدم، يمكنك الرجوع إلى البحث الاستباقي عن [التهديدات باستخدام الصيد المتقدم](advanced-hunting-overview.md).

الصيد المتقدم هو أداة بحث عن تهديدات تستند إلى استعلام (لغة استعلام Kusto) تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات التي تم التقاطها (الخام)، والتي يجمعها Defender for Endpoint من أجهزتك. من خلال البحث المتقدم، يمكنك فحص الأحداث بشكل استباقي لتحديد موقع المؤشرات والكيانات المثيرة للاهتمام. يساعد الوصول المرن إلى البيانات في البحث غير المقيد عن التهديدات المعروفة والمحتملة.

من خلال البحث المتقدم، من الممكن استخراج معلومات قواعد ASR وإنشاء التقارير والحصول على معلومات معمقة حول سياق حدث حظر أو تدقيق قاعدة ASR معينة.

تتوفر أحداث قواعد ASR للاستعلام عنها من الجدول DeviceEvents في قسم الصيد المتقدم في Microsoft 365 Defender. على سبيل المثال، يمكن للاستعلام البسيط مثل الاستعلام أدناه الإبلاغ عن كل الأحداث التي تتضمن قواعد ASR كمصدر بيانات، خلال آخر 30 يوما، وتلخيصها حسب عدد الإجراءات، حيث سيكون في هذه الحالة اسم الرمز الفعلي لقاعدة ASR.

:::image type="content" source="images/adv-hunt-querynew.png" alt-text="استعلام البحث المتقدم" lightbox="images/adv-hunt-querynew.png":::

:::image type="content" source="images/adv-hunt-sc-2new.png" alt-text="صفحة الصيد المتقدمة" lightbox="images/adv-hunt-sc-2new.png":::

باستخدام البحث المتقدم، يمكنك تشكيل الاستعلامات على نحو يعجبك، بحيث تتمكن من رؤية ما يحدث، بغض النظر عما إذا كنت تريد تثبيت شيء ما على جهاز فردي، أو تريد استخراج رؤى من بيئتك بالكامل.

## <a name="microsoft-defender-for-endpoint-machine-timeline"></a>Microsoft Defender لنقطة النهاية زمني للجهاز

بديل للصيد المتقدم، ولكن بنطاق أضيق، هو Microsoft Defender لنقطة النهاية الزمني للجهاز. يمكنك عرض كل الأحداث التي تم تجميعها لجهاز، خلال الأشهر الستة الماضية، في Microsoft 365 Defender، عن طريق الذهاب إلى قائمة الأجهزة، حدد جهازا معينا، ثم انقر فوق علامة التبويب المخطط الزمني.

في الصورة أدناه، لقطة شاشة ل طريقة عرض الخط الزمني لهذه الأحداث على نقطة نهاية معينة. من طريقة العرض هذه، يمكنك تصفية قائمة الأحداث استنادا إلى أي من مجموعات الأحداث على طول الجزء على الجانب الأيسر. يمكنك أيضا تمكين الأحداث ذات العلامة والمسهبة أو تعطيلها أثناء عرض التنبيهات والتمرير عبر المخطط الزمني التاريخي.

:::image type="content" source="images/mic-sec-def-timelinenew.png" alt-text="المخطط الزمني Microsoft 365 Defender الزمني" lightbox="images/mic-sec-def-timelinenew.png":::

## <a name="how-to-troubleshoot-asr-rules"></a>كيفية استكشاف الأخطاء في قواعد ASR وإصلاحها؟

الطريقة الأولى والأكثر مباشرة هي التحقق محليا، على جهاز Windows، حيث يتم تمكين قواعد ASR (وتكوينها) باستخدام أمر cmdlets في PowerShell.

فيما يلي بعض مصادر المعلومات الأخرى التي Windows بها، لا استكشاف تأثير قواعد ASR وتشغيلها وإصلاحها.

### <a name="querying-which-rules-are-active"></a>الاستعلام عن القواعد النشطة

إحدى أسهل الطرق لتحديد ما إذا كانت قواعد ASR تم تمكينها بالفعل هي من خلال أمر cmdlet PowerShell، Get-MpPreference.

فيما يلي مثال على ذلك:

:::image type="content" source="images/getmpreferencescriptnew.png" alt-text="البرنامج النصي &quot;الحصول على mppreference&quot;" lightbox="images/getmpreferencescriptnew.png":::

هناك العديد من قواعد ASR نشطة، مع إجراءات مكونة مختلفة.

لتوسيع المعلومات أعلاه حول قواعد ASR، يمكنك استخدام الخصائص **AttackSurfaceReductionRules_Ids و/****أو AttackSurfaceReductionRules_Actions**.

على سبيل المثال:

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Ids
```

:::image type="content" source="images/getmpref-examplenew.png" alt-text="مثال الحصول على mpreference" lightbox="images/getmpref-examplenew.png":::

يعرض ما سبق كل الم IDs لقواعد ASR التي لها إعداد مختلف عن 0 (غير مكون).

الخطوة التالية هي بعد ذلك سرد الإجراءات الفعلية (الحظر أو التدقيق) التي يتم تكوين كل قاعدة باستخدامها.

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Actions
```

:::image type="content" source="images/getmpref-example2new.png" alt-text="مثال الحصول على mppreference2" lightbox="images/getmpref-example2new.png":::

### <a name="querying-blocking-and-auditing-events"></a>استعلام أحداث الحظر والتدقيق

يمكن عرض أحداث قواعد ASR ضمن Windows Defender.

للوصول إليها، افتح Windows عارض الأحداث واستعرض للوصول إلى **التطبيقات** \> والخدمات سجلات **Microsoft** \>  \> Windows **Windows Defender** \> **التشغيلية**.

:::image type="content" source="images/eventviewerscrnew.png" alt-text="الصفحة عارض الأحداث" lightbox="images/eventviewerscrnew.png":::

## <a name="microsoft-defender-antimalware-protection-logs"></a>سجلات الحماية من البرامج الضارة من Microsoft Defender

يمكنك أيضا عرض أحداث القواعد من خلال `*mpcmdrun.exe*`برنامج الحماية من الفيروسات من Microsoft Defender سطر الأوامر المخصصة، التي تسمى ، التي يمكن استخدامها لإدارة المهام وتكوينها، وأتمتة المهام إذا لزم الأمر.

يمكنك العثور على هذه الأداة المساعدة في *٪ProgramFiles٪\Windows Defender\MpCmdRun.exe*. يجب تشغيله من موجه أوامر مرتفع (أي، تشغيل كمسؤول).

لإنشاء معلومات الدعم، اكتبMpCmdRun.exe *-getfiles*. بعد مرور بعض الوقت، سيتم وضع عدة سجلات في حزمة في أرشيف (MpSupportFiles.cab) وستتوفر في *C:\ProgramData\Microsoft\Windows Defender\Support*.

:::image type="content" source="images/malware-prot-logsnew.png" alt-text="سجلات الحماية من البرامج الضارة" lightbox="images/malware-prot-logsnew.png":::

استخرج هذا الأرشيف وسوف يكون لديك العديد من الملفات المتوفرة لأغراض استكشاف الأخطاء وإصلاحها.

الملفات الأكثر صلة هي كما يلي:

- **MPOperationalEvents.txt**: يحتوي هذا الملف على مستوى المعلومات نفسه الذي تم العثور عليه في عارض الأحداث Windows التشغيلية ل Defender.
- **MPRegistry.txt**: في هذا الملف، يمكنك تحليل كافة تكوينات Windows Defender، من اللحظة التي تم فيها التقاط سجلات الدعم.
- **MPLog.txt**: يحتوي هذا السجل على مزيد من المعلومات المهينة حول جميع إجراءات/عمليات Windows Defender.
