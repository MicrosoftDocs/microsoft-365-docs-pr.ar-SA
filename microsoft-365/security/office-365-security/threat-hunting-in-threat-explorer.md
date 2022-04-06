---
title: التهديد بالصيد في "مستكشف التهديدات" Microsoft Defender لـ Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: استخدم "مستكشف التهديدات" أو الكشف في الوقت الحقيقي في Microsoft 365 Defender الإلكتروني للتحقق من التهديدات والاستجابة لها بفعالية.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5b6662a3268fa6ab83c103eb84cd1d77ab06d37d
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476390"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>التهديد بالصيد في "مستكشف التهديدات" Microsoft Defender لـ Office 365

في هذه المقالة:

- [عرض مستكشف التهديدات](#threat-explorer-walk-through)
- [التحقيق عبر البريد الإلكتروني](#email-investigation)
- [إصلاح البريد الإلكتروني](#email-remediation)
- [تحسينات على تجربة البحث عن المخاطر](#improvements-to-threat-hunting-experience)

> [!NOTE]
> يشكل هذا جزءا من سلسلة  ثلاثية المقالة حول "مستكشف التهديدات" **(المستكشف)** والأمان عبر البريد الإلكتروني والكشف في "المستكشف" و"الوقت الحقيقي **" (** كالاختلافات بين الأدوات والأذونات اللازمة لتشغيلها).  المقالات الأخرى في هذه السلسلة هي أمان [البريد الإلكتروني باستخدام](email-security-in-microsoft-defender.md) "مستكشف التهديدات" و"مستكشف التهديدات" [والكشف في الوقت الحقيقي](real-time-detections.md).


**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

إذا كانت مؤسستك تملك [Microsoft Defender لـ Office 365](defender-for-office-365.md)، وكان لديك الأذونات، يمكنك استخدام المستكشف أو الكشف في  الوقت الحقيقي  للكشف عن التهديدات و إصلاحها.[](#required-licenses-and-permissions)

في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى البريد الإلكتروني & **التعاون**، ثم اختر **المستكشف** أو **الكشف في الوقت الحقيقي**. للذهاب مباشرة إلى الصفحة، استخدم أو <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

باستخدام هذه الأدوات، يمكنك:

- الاطلاع على البرامج الضارة التي تم اكتشافها Microsoft 365 الأمان
- عرض عنوان URL التصيد الاحتيالي والنقر فوق بيانات الحكم
- بدء عملية تحقيق واستجابات تلقائية من طريقة عرض في المستكشف
- التحقق من البريد الإلكتروني الضار والمزيد

لمزيد من المعلومات، راجع [أمان البريد الإلكتروني باستخدام "مستكشف التهديدات](email-security-in-microsoft-defender.md)".

## <a name="threat-explorer-walk-through"></a>عرض مستكشف التهديدات

في Microsoft Defender لـ Office 365، هناك خطتان للاشتراك — الخطة 1 الخطة 2. توجد أدوات البحث عن المخاطر التي يتم تشغيلها يدويا في كلتا الخطتين، وأسماء مختلفة وإمكانات مختلفة.

Defender لـ Office 365 الخطة 1 الكشف في الوقت الحقيقي، وهي مجموعة فرعية من أداة الصيد "مستكشف التهديدات *" (* تسمى أيضا المستكشف *) في* الخطة 2. في هذه السلسلة من المقالات، تم إنشاء معظم الأمثلة باستخدام "مستكشف التهديدات" الكامل. يجب على المسؤولين اختبار أي خطوات في الكشف في الوقت الحقيقي لمعرفة مكان تطبيقها.

بعد الانتقال إلى **"المستكشف**"، ستصل بشكل افتراضي إلى صفحة البرامج  الضارة، ولكن استخدم المنسدل عرض للإلمام بالخيارات الخاصة بك. إذا كنت تصيد "التصيد الاحتيالي"، أو تصيد حملة تهديدات، فاختر طرق العرض هذه.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/view-drop-down.png" alt-text="منسدل &quot;طريقة العرض&quot; في &quot;مستكشف التهديدات&quot;" lightbox="../../media/view-drop-down.png":::

بمجرد أن يقوم أحد الأشخاص في عمليات الأمان (Sec Ops) بتحديد البيانات التي يريد رؤيتها، سواء كان النطاق ضيقا مثل عمليات إرسال المستخدم، أو طريقة عرض أوسع، مثل كل البريد الإلكتروني، يمكنه استخدام الزر  مرسل لمزيد من التصفية. تذكر تحديد تحديث لإكمال إجراءات التصفية.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/sender-drop-down.png" alt-text="الزر &quot;المرسل&quot; في &quot;مستكشف التهديدات&quot;" lightbox="../../media/sender-drop-down.png":::


يمكن التفكير في تحسين التركيز في المستكشف أو الكشف في الوقت الحقيقي في الطبقات. الأول هو **عرض**. يمكن التفكير في الثانية على أنها *تركيز تمت تصفيته*. على سبيل المثال، يمكنك سحب الخطوات التي اتخذتها في العثور على خطر عن طريق تسجيل قراراتك بهذا الطريقة: للعثور على المشكلة في المستكشف، اخترت طريقة عرض البرامج الضارة مع تركيز عامل تصفية **المستلم**. هذا يسهل عملية سحب الخطوات.

> [!TIP]
> إذا كانت Sec Ops تستخدم **العلامات** لعلامة الحسابات التي تعتبرها أهدافا ذات قيمة عالية، يمكنهم إجراء تحديدات مثل عرض التصيد الاحتيالي مع تركيز عامل تصفية العلامات (تضمين نطاق تاريخ إذا تم *استخدامه)*. سيعرض لهم هذا أي محاولات تصيد احتيالي موجهة إلى أهداف المستخدمين ذات القيمة العالية خلال فترة زمنية (مثل التواريخ التي تحدث فيها بعض هجمات التصيد الاحتيالي كثيرا في مجالهم).

يمكن إجراء التحسينات على نطاقات التاريخ باستخدام عناصر تحكم نطاق التاريخ. يمكنك هنا رؤية المستكشف في طريقة **عرض البرامج** الضارة، مع التركيز على عامل **تصفية تقنية** الكشف. ولكنه زر التصفية **المتقدمة** الذي يسمح لفرق Sec Ops بالتعمق.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/advanced-filter.png" alt-text="عامل التصفية المتقدم في &quot;مستكشف التهديدات&quot;" lightbox="../../media/advanced-filter.png":::

يؤدي النقر فوق **عامل التصفية** المتقدمة إلى انصهار لوحة تسمح ل "صائدي عمليات Sec" ببناء الاستعلامات بأنفسهم، مما يسمح لهم بتضمين المعلومات التي يحتاجون إليها أو استبعادها. سيعكس كل من المخطط وال جدول على صفحة المستكشف نتائجهما.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-chart-table.png" alt-text="النتائج من استعلام" lightbox="../../media/threat-explorer-chart-table.png":::

استخدم **زر خيارات العمود** للحصول على نوع المعلومات على الجدول الأكثر فائدة:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-column-options.png" alt-text="تم تمييز الزر &quot;خيارات العمود&quot;" lightbox="../../media/threat-explorer-column-options.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/column-options.png" alt-text="الخيارات المتوفرة في الأعمدة" lightbox="../../media/column-options.png":::

في نفس mien، تأكد من اختبار خيارات العرض. ستتفاعل فئات مستمعين مختلفة بشكل جيد مع العروض التقديمية المختلفة للبيانات نفسها. بالنسبة لبعض العارضين،  يمكن أن تظهر خريطة "أصول البريد الإلكتروني" أن التهديد واسع الانتشار أو غير متحفظ بشكل أسرع  من خيار عرض "الحملة" بجواره مباشرة. يمكن ل Sec Ops الاستفادة من هذه الشاشات للحصول على أفضل النقاط التي تبرز الحاجة إلى الأمان والحماية، أو المقارنة لاحقا، لزيادة فعالية إجراءاتها.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-origin-map.png" alt-text="خريطة &quot;أصول البريد الإلكتروني&quot;" lightbox="../../media/threat-explorer-email-origin-map.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-campaign-display.png" alt-text="خيارات عرض الحملة" lightbox="../../media/threat-explorer-campaign-display.png":::

### <a name="email-investigation"></a>التحقيق عبر البريد الإلكتروني

عندما ترى رسالة بريد إلكتروني مريبة، انقر فوق الاسم لتوسيع قائمة منتحلة على الجانب الأيمن. هنا، يتوفر الشعار الذي يسمح ل Sec Ops برؤية [صفحة كيان](mdo-email-entity-page.md) البريد الإلكتروني.

تجمع صفحة كيان البريد الإلكتروني معا المحتويات التي يمكن العثور عليها ضمن **التفاصيل** والمرفقات **والأجهزة**، ولكنها تتضمن بيانات أكثر تنظيما. يشمل ذلك أمورا مثل نتائج DMARC، وعرض النص العادي لرأس البريد الإلكتروني مع خيار نسخ، ومعلومات الحكم على المرفقات التي تم إقحامها بأمان، والملفات التي تم إسقاطها (يمكن أن تتضمن عناوين IP التي تم الاتصال بها ولقطات شاشة للصفحات أو الملفات). كما يتم سرد عناوين URL وحكامها بتفاصيل مماثلة تم نطقها.

عندما تصل إلى هذه المرحلة، ستكون صفحة كيان البريد الإلكتروني هامة للخطوة الأخيرة— *المعالجة*.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-entity-page.png" alt-text="صفحة كيان البريد الإلكتروني" lightbox="../../media/threat-explorer-email-entity-page.png":::

> [!TIP]
> لمعرفة المزيد حول صفحة كيان البريد الإلكتروني الغنية (المضمنة أدناه في  علامة التبويب تحليل)، بما في ذلك نتائج المرفقات المضمنة ونتائج عناوين URL المضمنة ومعاينة البريد الإلكتروني الآمنة، انقر [هنا](mdo-email-entity-page.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-analysis-tab.png" alt-text="علامة التبويب &quot;تحليل&quot; في صفحة كيان البريد الإلكتروني" lightbox="../../media/threat-explorer-analysis-tab.png":::

### <a name="email-remediation"></a>إصلاح البريد الإلكتروني

بمجرد أن يحدد أحد الأشخاص في Sec Ops أن البريد الإلكتروني يشكل خطرا، فإن الخطوة التالية في الكشف عن المستكشف أو في الوقت الحقيقي هي التعامل مع هذا الخطر وتعالجه. يمكن إجراء ذلك من خلال العودة إلى "مستكشف التهديدات"، وتحديد خانة الاختيار الخاصة بالبريد الإلكتروني للمشكلة، واستخدام **الزر إجراءات** .

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-button.png" alt-text="الزر &quot;إجراءات&quot; في &quot;مستكشف التهديدات&quot;" lightbox="../../media/threat-explorer-email-actions-button.png":::

هنا، يمكن للمحلل اتخاذ إجراءات مثل الإبلاغ عن البريد كبريد عشوائي أو تصيد احتيالي أو برنامج ضار أو الاتصال بالمستلمين أو إجراء المزيد من عمليات البحث التي يمكن أن تتضمن تشغيل دفاتر تشغيل "التحقيق والرد التلقائي" (أو AIR) (إذا كان لديك الخطة 2). أو، يمكن أيضا أن يتم إعلام البريد بأنه نظيف.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-drop-down.png" alt-text="منسدل الإجراءات" lightbox="../../media/threat-explorer-email-actions-drop-down.png":::

## <a name="improvements-to-threat-hunting-experience"></a>تحسينات على تجربة البحث عن المخاطر

### <a name="alert-id"></a>"معرّف التنبيه"

عند التنقل من تنبيه إلى "مستكشف التهديدات"، سيتم  تصفية طريقة العرض حسب **"مستكشف التنبيه**". ينطبق ذلك أيضا في الكشف في الوقت الحقيقي. يتم عرض الرسائل ذات الصلة بالتنبيه المحدد، وإجمالي البريد الإلكتروني (العدد). وستتمكن من معرفة ما إذا كانت الرسالة جزءا من تنبيه، بالإضافة إلى الانتقال من تلك الرسالة إلى التنبيه ذي الصلة.

وأخيرا، يتم تضمين "عنوان URL" في "عنوان URL"، على سبيل المثال: `https://https://security.microsoft.com/viewalerts`

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="عامل التصفية لم ID تنبيه" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="من خلال &quot;الماينة&quot; من خلال &quot;الماينة&quot; في التفاصيل" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>توسيع حد استبقاء البيانات والبحث في المستكشف (والكشف عنها في الوقت الحقيقي) للمستأجرين التجريبيين

وكجزء من هذا التغيير، سيكون بمقدور المحللين البحث عن بيانات البريد الإلكتروني وتصفيتها خلال 30 يوما (زيادة من سبعة أيام) في "مستكشف التهديدات" والكشف في الوقت الحقيقي لكل من المستأجرين التجريبيين ل Office P1 و P2. لا يؤثر هذا على أي مستأجري إنتاج لعملاء P1 و P2 E5، حيث يكون افتراضي الاستبقاء 30 يوما بالفعل.

### <a name="updated-export-limit"></a>حد التصدير المحدث

أصبح عدد سجلات رسائل البريد الإلكتروني التي يمكن تصديرها من "مستكشف التهديدات" الآن 200000 (كان 9990). لم تتغير مجموعة الأعمدة التي يمكن تصديرها.

### <a name="tags-in-threat-explorer"></a>العلامات في "مستكشف التهديدات"

> [!NOTE]
> تتوفر ميزة علامات المستخدم في Preview وقد لا تكون متوفرة للجميع. كما أن المعاينات عرضة للتغيير. للحصول على معلومات حول جدول الإصدار، راجع Microsoft 365 الجديد.

تحدد علامات المستخدم مجموعات معينة من المستخدمين في Microsoft Defender لـ Office 365. لمزيد من المعلومات حول العلامات، بما في ذلك الترخيص والتكوين، راجع [علامات المستخدم](user-tags.md).

في "مستكشف التهديدات"، يمكنك الاطلاع على معلومات حول علامات المستخدم في التجارب التالية.

#### <a name="email-grid-view"></a>طريقة عرض شبكة البريد الإلكتروني

عندما ينظر المحللون إلى عمود **العلامات** في شبكة البريد الإلكتروني، يرون كل العلامات التي تم تطبيقها على علب بريد المرسلين أو المستلمين. بشكل افتراضي، يتم عرض علامات النظام مثل *حسابات الأولوية* أولا.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="علامات التصفية في طريقة عرض شبكة البريد الإلكتروني" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>التصفية

يمكن استخدام العلامات ك عوامل تصفية. البحث بين حسابات الأولوية فقط، أو استخدام سيناريوهات علامات مستخدم معينة بهذه الطريقة. يمكنك أيضا استبعاد النتائج التي لها علامات معينة. يمكنك دمج العلامات مع عوامل التصفية ونطاقات التاريخ الأخرى لتضييق نطاق التحقيق.

[![تصفية العلامات.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="العلامات التي لم تمت تصفيتها" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>قائمة من حولاء تفاصيل البريد الإلكتروني

لعرض العلامات الفردية للمرسل والمستلم، حدد بريدا إلكترونيا لفتح قائمة منبعثة التفاصيل الخاصة بالرسالة. في علامة **التبويب ملخص** ، يتم عرض علامات المرسل والمستلم بشكل منفصل. يمكن تصدير المعلومات حول العلامات الفردية للمرسل والمستلم كالبيانات CSV.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="علامات تفاصيل البريد الإلكتروني" lightbox="../../media/tags-flyout.png":::

يتم أيضا عرض معلومات العلامات في معلومات النقر فوق عنوان URL. لمشاهدته، انتقل إلى طريقة عرض التصيد الاحتيالي أو كل البريد الإلكتروني > **عناوين URL** أو **نقرات URL** . حدد منتدية عناوين URL فردية للاطلاع على تفاصيل إضافية حول النقرات الخاصة ب URL هذا، بما في ذلك أي علامات مقترنة بهذه النقرة.

### <a name="updated-timeline-view"></a>طريقة عرض المخطط الزمني المحدثة

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="علامات URL" lightbox="../../media/tags-urls.png":::
>
تعرف على المزيد من خلال [مشاهدة هذا الفيديو](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="extended-capabilities"></a>الإمكانات الموسعة

### <a name="top-targeted-users"></a>أهم المستخدمين المستهدفين

تعرض أفضل عائلات البرامج الضارة **أهم المستخدمين المستهدفين** في قسم البرامج الضارة. سيتم توسيع أهم المستخدمين المستهدفين عبر طرق عرض التصيد الاحتيالي وجميع رسائل البريد الإلكتروني أيضا. وسيتمكن المحللون من رؤية أفضل خمسة مستخدمين مستهدفين، إلى جانب عدد المحاولات لكل مستخدم في كل طريقة عرض.

عمليات الأمان يمكن للأشخاص تصدير قائمة المستخدمين المستهدفين، بما يصل إلى 3000 شخص، إلى جانب عدد المحاولات التي تم القيام بها، للتحليل دون اتصال لكل طريقة عرض بريد إلكتروني. علاوة على ذلك، فإن تحديد عدد المحاولات (على سبيل المثال، 13 محاولة في الصورة أدناه) سيفتح طريقة عرض تمت تصفيتها في "مستكشف التهديدات"، حتى تتمكن من رؤية المزيد من التفاصيل عبر رسائل البريد الإلكتروني، والتهديدات لهذا المستخدم.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="المستخدمون المستهدفون بشكل أكبر" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>Exchange النقل

وسيتمكن فريق عمليات الأمان من رؤية جميع قواعد Exchange (أو قواعد تدفق البريد) المطبقة على رسالة، في طريقة عرض شبكة البريد الإلكتروني. حدد **خيارات العمود** في الشبكة ثم **Exchange قاعدة النقل** من خيارات العمود. كما Exchange خيار قواعد النقل الأخرى في قائمة التفاصيل في البريد الإلكتروني.

تظهر الأسماء وGUIDs لقواعد النقل المطبقة على الرسالة. وسيتمكن المحللون من البحث عن الرسائل باستخدام اسم قاعدة النقل. هذا بحث في CONTAINS، مما يعني أنه يمكنك إجراء عمليات بحث جزئية أيضا.

> [!IMPORTANT]
> Exchange البحث عن قاعدة النقل وتوفر الاسم على الدور المعين لك. يجب أن يكون لديك أحد الأدوار أو الأذونات التالية لعرض أسماء قواعد النقل والبحث. ومع ذلك، حتى بدون الأدوار أو الأذونات أدناه، قد يرى المحلل تسمية قاعدة النقل ومعلومات GUID في تفاصيل البريد الإلكتروني. لا تتأثر تجارب عرض السجلات الأخرى في "شبكات البريد الإلكتروني" و"قائمة البريد الإلكتروني" و"عوامل التصفية" و"التصدير".
>
> - Exchange Online فقط - منع فقدان البيانات: الكل
> - Exchange Online فقط - O365SupportViewConfig: الكل
> - Microsoft Azure Active Directory أو Exchange Online - مسؤول الأمان: الكل
> - Azure Active Directory أو Exchange Online - قارئ الأمان: الكل
> - Exchange Online فقط - قواعد النقل: الكل
> - Exchange Online فقط - View-Only التكوين: الكل
>
> ضمن شبكة البريد الإلكتروني، ومن القائمة منسدرة التفاصيل، و CSV التي تم تصديرها، يتم تقديم ETRs مع اسم/GUID كما هو موضح أدناه.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="القواعد في Exchange النقل" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>الموصلات الواردة

الموصلات هي مجموعة من الإرشادات التي تقوم بتخصيص كيفية تدفق بريدك الإلكتروني من Microsoft 365 أو Office 365 المؤسسة. فهي تمكنك من تطبيق أي قيود أمان أو عناصر تحكم. في "مستكشف التهديدات"، يمكنك عرض الموصلات المرتبطة بالبريد الإلكتروني والبحث عن رسائل البريد الإلكتروني باستخدام أسماء الموصلات.

البحث عن الموصلات هو استعلام CONTAINS، مما يعني أن عمليات البحث الجزئية للكلمة الأساسية يمكن أن تعمل:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="تفاصيل الموصل" lightbox="../../media/Connector_Details.png":::

## <a name="required-licenses-and-permissions"></a>التراخيص والأذونات المطلوبة

يجب أن يكون [Microsoft Defender لـ Office 365](defender-for-office-365.md) استخدام المستكشف أو الكشف في الوقت الحقيقي.

- المستكشف مضمن في Defender لـ Office 365 2.
- يتم تضمين تقرير الكشف في الوقت الحقيقي في Defender لـ Office 365 1.
- التخطيط لتعيين تراخيص لجميع المستخدمين الذين يجب حمايتهم بواسطة Defender لـ Office 365. تظهر الكشفات في المستكشف وفي الوقت الحقيقي بيانات الكشف للمستخدمين المرخص لهم.

لعرض المستكشف أو الكشف في الوقت الحقيقي واستخدامه، يجب أن تكون لديك الأذونات التالية:

- في مدخل Microsoft 365 Defender:
  - إدارة المؤسسة
  - مسؤول الأمان (يمكن تعيين هذا في مركز إدارة Azure Active Directory (<https://aad.portal.azure.com>)
  - قارئ الأمان
- في Exchange Online:
  - إدارة المؤسسة
  - View-Only Organization Management
  - View-Only المستلمين
  - إدارة التوافق

لمعرفة المزيد حول الأدوار والأذونات، راجع الموارد التالية:

- [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>معلومات إضافية

- [البحث عن البريد الإلكتروني الضار الذي تم تسليمه والتحقق من ذلك](investigate-malicious-email-that-was-delivered.md)
- [عرض الملفات الضارة التي تم اكتشافها في SharePoint عبر الإنترنت OneDrive و Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [الحصول على نظرة عامة حول طرق العرض في "مستكشف التهديدات" (والكشف في الوقت الحقيقي)](threat-explorer-views.md)
- [تقرير حالة الحماية من المخاطر](view-email-security-reports.md#threat-protection-status-report)
- [إجراء عمليات التحقيق والرد التلقائية في الحماية من المخاطر من Microsoft](automated-investigation-response-office.md)
- [التحقق من رسائل البريد الإلكتروني باستخدام صفحة كيان البريد الإلكتروني](mdo-email-entity-page.md)
