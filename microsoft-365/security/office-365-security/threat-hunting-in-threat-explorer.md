---
title: تتبع التهديدات في مستكشف المخاطر Microsoft Defender لـ Office 365
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
description: استخدم مستكشف التهديدات أو عمليات الكشف في الوقت الحقيقي في مدخل Microsoft 365 Defender للتحقيق في التهديدات والاستجابة لها بكفاءة.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2c99bc2ce004156320ec8f53f6b956f7989ee056
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648812"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>تتبع التهديدات في مستكشف المخاطر Microsoft Defender لـ Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على:**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في هذه المقالة:

- [إرشادات مستكشف التهديدات](#threat-explorer-walk-through)
- [التحقيق في البريد الإلكتروني](#email-investigation)
- [معالجة البريد الإلكتروني](#email-remediation)
- [تحسينات على تجربة تتبع التهديدات](#improvements-to-threat-hunting-experience)

> [!NOTE]
> هذا جزء من سلسلة من **3 مقالات** حول **مستكشف التهديدات (Explorer)** **وأمان البريد الإلكتروني** **واكتشافات المستكشف في الوقت الحقيقي** (مثل الاختلافات بين الأدوات والأذونات اللازمة لتشغيلها). المقالتان الآخرتان في هذه السلسلة هما [أمان البريد الإلكتروني باستخدام مستكشف التهديدات](email-security-in-microsoft-defender.md) [ومستكشف التهديدات والكشف في الوقت الحقيقي](real-time-detections.md).

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

إذا كان لدى مؤسستك [Microsoft Defender لـ Office 365](defender-for-office-365.md)، ولديك [الأذونات](#required-licenses-and-permissions)، يمكنك استخدام **عمليات الكشف في الوقت الحقيقي** أو **المستكشف** للكشف عن التهديدات وإصلاحها.

في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **التعاون في & البريد الإلكتروني**، ثم اختر **المستكشف** أو **عمليات الكشف في الوقت الحقيقي**. للانتقال مباشرة إلى الصفحة، استخدم <https://security.microsoft.com/threatexplorer> أو <https://security.microsoft.com/realtimereports>.

باستخدام هذه الأدوات، يمكنك:

- الاطلاع على البرامج الضارة التي تم الكشف عنها بواسطة ميزات الأمان Microsoft 365
- عرض عنوان URL للتصيد الاحتيالي والنقر فوق بيانات الحكم
- بدء عملية التحقيق والاستجابة التلقائية من طريقة عرض في Explorer
- التحقيق في رسائل البريد الإلكتروني الضارة والمزيد

لمزيد من المعلومات، راجع [أمان البريد الإلكتروني باستخدام مستكشف التهديدات](email-security-in-microsoft-defender.md).

شاهد هذا الفيديو القصير لمعرفة كيفية تتبع التهديدات المستندة إلى البريد الإلكتروني والتعاون والتحقيق فيها باستخدام Microsoft Defender لـ Office 365. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyPRU]

## <a name="threat-explorer-walk-through"></a>إرشادات مستكشف التهديدات

في Microsoft Defender لـ Office 365، هناك خطتان للاشتراك- الخطة 1 والخطة 2. توجد أدوات تتبع المخاطر المشغلة يدويا في كلتا الخطتين، تحت أسماء مختلفة وبإمكانات مختلفة.

تستخدم Defender لـ Office 365 الخطة 1 *عمليات الكشف في الوقت الحقيقي*، وهي مجموعة فرعية من أداة تتبع *مستكشف التهديدات* (تسمى أيضا *Explorer*) في الخطة 2. في هذه السلسلة من المقالات، تم إنشاء معظم الأمثلة باستخدام مستكشف التهديدات الكامل. يجب على المسؤولين اختبار أي خطوات في عمليات الكشف في الوقت الحقيقي لمعرفة مكان تطبيقها.

بعد الانتقال إلى **Explorer**، ستصل بشكل افتراضي إلى صفحة **البرامج الضارة** ، ولكن استخدم القائمة المنسدلة **"عرض"** للتعرف على خياراتك. إذا كنت تتتبع التصيد الاحتيالي، أو تتعمق في حملة التهديد، فاختر طرق العرض هذه.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/view-drop-down.png" alt-text="القائمة المنسدلة &quot;طريقة العرض&quot; في مستكشف التهديدات" lightbox="../../media/view-drop-down.png":::

بمجرد أن يحدد شخص عمليات الأمان (Sec Ops) البيانات التي يريد رؤيتها، سواء كان النطاق عبارة عن طريقة عرض ضيقة مثل **عمليات إرسال** المستخدم، أو طريقة عرض أوسع، مثل **كل البريد الإلكتروني**، يمكنه استخدام الزر **"مرسل"** لتصفية إضافية. تذكر تحديد "تحديث" لإكمال إجراءات التصفية.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/sender-drop-down.png" alt-text="الزر &quot;المرسل&quot; في مستكشف التهديدات" lightbox="../../media/sender-drop-down.png":::

يمكن التفكير في تحسين التركيز في المستكشف أو الكشف في الوقت الحقيقي في الطبقات. الأول هو **View**. ويمكن اعتبار الثانية *تركيزا تمت تصفيته*. على سبيل المثال، يمكنك سحب الخطوات التي اتخذتها للعثور على تهديد عن طريق تسجيل قراراتك مثل هذا: للعثور على المشكلة في Explorer، **اخترت طريقة عرض البرامج الضارة مع تركيز عامل تصفية المستلم**. وهذا يجعل سحب خطواتك أسهل.

> [!TIP]
> If Sec Ops uses **Tags** to mark accounts they consider high valued targets, they can make selections like *Phish View with a Tags filter focus (include a date range if used)*. سيظهر ذلك لهم أي محاولات تصيد احتيالي موجهة إلى أهداف المستخدمين ذات القيمة العالية خلال نطاق زمني (مثل التواريخ التي تحدث فيها هجمات تصيد احتيالي معينة كثيرا بالنسبة إلى صناعتهم).

يمكن إجراء تحسينات على نطاقات التاريخ باستخدام عناصر تحكم نطاق التاريخ. هنا يمكنك مشاهدة Explorer في طريقة عرض **البرامج الضارة** ، مع تركيز عامل تصفية **تقنية الكشف** . ولكن زر **التصفية المتقدمة** هو الذي يسمح لفرق عمليات Sec بالتعمق.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/advanced-filter.png" alt-text="عامل التصفية المتقدم في مستكشف التهديدات" lightbox="../../media/advanced-filter.png":::

يؤدي النقر فوق **عامل التصفية المتقدم** إلى ظهور لوحة تسمح لمتتبعي عمليات Sec Ops بإنشاء استعلامات بأنفسهم، مما يسمح لهم بتضمين المعلومات التي يحتاجون إلى رؤيتها أو استبعادها. سيعكس كل من المخطط والجدول على صفحة المستكشف نتائجهما.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-chart-table.png" alt-text="النتائج من استعلام" lightbox="../../media/threat-explorer-chart-table.png":::

استخدم الزر **"خيارات العمود** " للحصول على نوع المعلومات التي قد تكون أكثر فائدة على الجدول:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-column-options.png" alt-text="الزر &quot;خيارات العمود&quot; مميز" lightbox="../../media/threat-explorer-column-options.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/column-options.png" alt-text="الخيارات المتوفرة في الأعمدة" lightbox="../../media/column-options.png":::

في نفس mien، تأكد من اختبار خيارات العرض الخاصة بك. ستتفاعل الجماعات المستهدفة المختلفة بشكل جيد مع العروض التقديمية المختلفة لنفس البيانات. بالنسبة إلى بعض المشاهدين، يمكن أن تظهر خريطة **"أصول البريد الإلكتروني** " أن التهديد واسع الانتشار أو غير محدد بسرعة أكبر من خيار **عرض "الحملة"** بجواره مباشرة. يمكن للعمليات الثانية الاستفادة من هذه العروض لتقديم أفضل النقاط التي تبرز الحاجة إلى الأمان والحماية، أو للمقارنة لاحقا، لإظهار فعالية إجراءاتها.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-origin-map.png" alt-text="خريطة أصول البريد الإلكتروني" lightbox="../../media/threat-explorer-email-origin-map.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-campaign-display.png" alt-text="خيارات عرض الحملة" lightbox="../../media/threat-explorer-campaign-display.png":::

### <a name="email-investigation"></a>التحقيق في البريد الإلكتروني

عندما ترى رسالة بريد إلكتروني مريبة، انقر فوق الاسم لتوسيع القائمة المنبثقة على اليمين. هنا، يتوفر الشعار الذي يسمح ل Sec Ops برؤية [صفحة كيان البريد الإلكتروني](mdo-email-entity-page.md) .

تجمع صفحة كيان البريد الإلكتروني المحتويات التي يمكن العثور عليها ضمن **التفاصيل** **والمرفقات** **والأجهزة**، ولكنها تتضمن بيانات أكثر تنظيما. يتضمن ذلك أشياء مثل نتائج DMARC وعرض النص العادي لرأس البريد الإلكتروني مع خيار النسخ ومعلومات الحكم على المرفقات التي تم إلغاء تأمينها بشكل آمن والملفات التي تم إسقاطها (يمكن أن تتضمن عناوين IP التي تم الاتصال بها ولقطات شاشة للصفحات أو الملفات). كما يتم سرد عناوين URL وأحكامها بتفاصيل مماثلة تم الإبلاغ عنها.

عند الوصول إلى هذه المرحلة، ستكون صفحة كيان البريد الإلكتروني مهمة للخطوة الأخيرة - *المعالجة*.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-entity-page.png" alt-text="صفحة كيان البريد الإلكتروني" lightbox="../../media/threat-explorer-email-entity-page.png":::

> [!TIP]
> لمعرفة المزيد حول صفحة كيان البريد الإلكتروني الغنية (التي تظهر أدناه ضمن علامة التبويب **"تحليل** ")، بما في ذلك نتائج المرفقات غير المثبتة والنتائج الخاصة بعناوين URL المضمنة ومعاينة البريد الإلكتروني الآمنة، انقر [هنا](mdo-email-entity-page.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-analysis-tab.png" alt-text="علامة التبويب &quot;تحليل&quot; في صفحة كيان البريد الإلكتروني" lightbox="../../media/threat-explorer-analysis-tab.png":::

### <a name="email-remediation"></a>معالجة البريد الإلكتروني

بمجرد أن يحدد شخص Sec Ops أن رسالة البريد الإلكتروني تشكل تهديدا، فإن خطوة الكشف التالية في الوقت الحقيقي أو المستكشف تتعامل مع التهديد وتعالجه. يمكن القيام بذلك عن طريق العودة إلى مستكشف التهديدات، وتحديد خانة الاختيار للبريد الإلكتروني للمشكلة، واستخدام الزر **"إجراءات** ".

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-button.png" alt-text="الزر &quot;إجراءات&quot; في مستكشف المخاطر" lightbox="../../media/threat-explorer-email-actions-button.png":::

هنا، يمكن للمحلل اتخاذ إجراءات مثل الإبلاغ عن البريد الإلكتروني كرسائل البريد العشوائي أو التصيد الاحتيالي أو البرامج الضارة، أو الاتصال بالمستلمين، أو المزيد من التحقيقات التي يمكن أن تتضمن تشغيل أدلة مبادئ التحقيق والاستجابة التلقائية (أو AIR) (إذا كان لديك الخطة 2). أو، يمكن أيضا الإبلاغ عن البريد على أنه نظيف.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-drop-down.png" alt-text="القائمة المنسدلة &quot;إجراءات&quot;" lightbox="../../media/threat-explorer-email-actions-drop-down.png":::

## <a name="improvements-to-threat-hunting-experience"></a>تحسينات على تجربة تتبع التهديدات

### <a name="alert-id"></a>معرف التنبيه

عند التنقل من تنبيه إلى مستكشف المخاطر، ستتم تصفية **طريقة العرض** حسب **معرف التنبيه**. ينطبق هذا أيضا في الكشف في الوقت الحقيقي. يتم عرض الرسائل ذات الصلة بالتنبيه المحدد، وإجمالي البريد الإلكتروني (عدد). ستتمكن من معرفة ما إذا كانت الرسالة جزءا من تنبيه، بالإضافة إلى الانتقال من تلك الرسالة إلى التنبيه ذي الصلة.

وأخيرا، يتم تضمين معرف التنبيه في عنوان URL، على سبيل المثال: `https://https://security.microsoft.com/viewalerts`

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="عامل التصفية لمعرف التنبيه" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="القائمة المنبثقة لمعرف التنبيه في التفاصيل" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>توسيع نطاق استبقاء بيانات Explorer (واكتشافات الوقت الحقيقي) وحدود البحث للمستأجرين التجريبيين

وكجزء من هذا التغيير، سيتمكن المحللون من البحث عن بيانات البريد الإلكتروني وتصفيتها عبر 30 يوما (زيادة من سبعة أيام) في مستكشف المخاطر والكشف في الوقت الحقيقي لكل من Defender لمستأجري الإصدار التجريبي من P1 وP2 Office. لا يؤثر هذا على أي مستأجري إنتاج لكل من عملاء P1 وP2 E5، حيث يكون الإعداد الافتراضي للاستبقاء بالفعل 30 يوما.

### <a name="updated-export-limit"></a>حد التصدير المحدث

عدد سجلات رسائل البريد الإلكتروني التي يمكن تصديرها من مستكشف المخاطر هو الآن 200,000 (كان 9990). مجموعة الأعمدة التي يمكن تصديرها لم تتغير.

### <a name="tags-in-threat-explorer"></a>العلامات في مستكشف المخاطر

> [!NOTE]
> ميزة علامات المستخدم في المعاينة وقد لا تكون متوفرة للجميع. أيضا، تخضع المعاينات للتغيير. للحصول على معلومات حول جدول الإصدار، راجع خارطة طريق Microsoft 365.

تحدد علامات المستخدم مجموعات معينة من المستخدمين في Microsoft Defender لـ Office 365. لمزيد من المعلومات حول العلامات، بما في ذلك الترخيص والتكوين، راجع [علامات المستخدم](user-tags.md).

في مستكشف المخاطر، يمكنك مشاهدة معلومات حول علامات المستخدم في التجارب التالية.

#### <a name="email-grid-view"></a>طريقة عرض شبكة البريد الإلكتروني

عندما ينظر المحللون إلى عمود **العلامات** في شبكة البريد الإلكتروني، فإنهم يرون جميع العلامات التي تم تطبيقها على علب بريد المرسل أو المستلم. بشكل افتراضي، تظهر علامات النظام مثل *حسابات الأولوية* أولا.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="علامات التصفية في طريقة عرض شبكة البريد الإلكتروني" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>تصفيه

يمكن استخدام العلامات كعوامل تصفية. التتبع بين حسابات الأولوية فقط، أو استخدام سيناريوهات علامات مستخدم معينة بهذه الطريقة. يمكنك أيضا استبعاد النتائج التي تحتوي على علامات معينة. قم بدمج العلامات مع عوامل التصفية الأخرى ونطاقات التاريخ لتضييق نطاق التحقيق الخاص بك.

[![تصفية العلامات.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="العلامات التي لم تتم تصفيتها" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>القائمة المنبثقة لتفاصيل البريد الإلكتروني

لعرض العلامات الفردية للمرسل والمستلم، حدد رسالة بريد إلكتروني لفتح القائمة المنبثقة لتفاصيل الرسالة. في علامة التبويب **"ملخص** "، تظهر علامات المرسل والمستلم بشكل منفصل. يمكن تصدير المعلومات حول العلامات الفردية للمرسل والمستلم كبيانات CSV.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="علامات تفاصيل البريد الإلكتروني" lightbox="../../media/tags-flyout.png":::

كما تظهر معلومات العلامات في القائمة المنبثقة للنقر فوق عنوان URL. للاطلاع عليه، انتقل إلى طريقة عرض التصيد الاحتيالي أو كل البريد الإلكتروني > **عناوين URL** أو علامة التبويب **"نقرات URL** ". حدد قائمة منبثقة ل URL فردي للاطلاع على تفاصيل إضافية حول النقرات الخاصة ب URL هذا، بما في ذلك أي علامات مقترنة بتلك النقرة.

### <a name="updated-timeline-view"></a>طريقة عرض الخط الزمني المحدثة

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="علامات URL" lightbox="../../media/tags-urls.png":::
>
تعرف على المزيد من خلال مشاهدة [هذا الفيديو](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="extended-capabilities"></a>القدرات الموسعة

### <a name="top-targeted-users"></a>أفضل المستخدمين المستهدفين

تظهر أفضل مجموعات البرامج الضارة **أفضل المستخدمين المستهدفين** في قسم البرامج الضارة. سيتم توسيع المستخدمين المستهدفين من خلال التصيد الاحتيالي وجميع طرق عرض البريد الإلكتروني أيضا. سيتمكن المحللون من رؤية أفضل خمسة مستخدمين مستهدفين، إلى جانب عدد محاولات كل مستخدم في كل طريقة عرض.

يمكن لأشخاص عمليات الأمان تصدير قائمة المستخدمين المستهدفين، بحد أقصى 3000، بالإضافة إلى عدد المحاولات التي تمت، للتحليل دون اتصال لكل طريقة عرض للبريد الإلكتروني. أيضا، سيؤدي تحديد عدد المحاولات (على سبيل المثال، 13 محاولة في الصورة أدناه) إلى فتح طريقة عرض تمت تصفيتها في مستكشف المخاطر، حتى تتمكن من رؤية المزيد من التفاصيل عبر رسائل البريد الإلكتروني، والتهديدات لهذا المستخدم.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="المستخدمون الأكثر استهدافا" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>قواعد النقل Exchange

سيتمكن فريق عمليات الأمان من رؤية جميع قواعد النقل Exchange (أو قواعد تدفق البريد) المطبقة على رسالة، في طريقة عرض شبكة البريد الإلكتروني. حدد **خيارات العمود** في الشبكة ثم **أضف Exchange قاعدة النقل** من خيارات العمود. يكون خيار قواعد النقل Exchange مرئيا أيضا في القائمة المنبثقة **للتفاصيل** في البريد الإلكتروني.

تظهر أسماء قواعد النقل المطبقة على الرسالة وGUIDs. سيتمكن المحللون من البحث عن الرسائل باستخدام اسم قاعدة النقل. هذا بحث CONTAINS، ما يعني أنه يمكنك إجراء عمليات بحث جزئية أيضا.

> [!IMPORTANT]
> يعتمد Exchange البحث عن قاعدة النقل وتوافر الاسم على الدور المعين لك. يجب أن يكون لديك أحد الأدوار أو الأذونات التالية لعرض أسماء قواعد النقل والبحث. ومع ذلك، حتى بدون الأدوار أو الأذونات أدناه، قد يرى المحلل تسمية قاعدة النقل ومعلومات GUID في تفاصيل البريد الإلكتروني. لا تتأثر تجارب عرض السجلات الأخرى في شبكات البريد الإلكتروني والقوائم المنبثقة للبريد الإلكتروني وعوامل التصفية والتصدير.
>
> - Exchange Online فقط - منع فقدان البيانات: الكل
> - Exchange Online فقط - O365SupportViewConfig: الكل
> - Microsoft Azure Active Directory أو Exchange Online - مسؤول الأمان: الكل
> - Azure Active Directory أو Exchange Online - قارئ الأمان: الكل
> - Exchange Online فقط - قواعد النقل: الكل
> - Exchange Online فقط - تكوين View-Only: الكل
>
> ضمن شبكة البريد الإلكتروني، القائمة المنبثقة للتفاصيل، و CSV المصدرة، يتم تقديم ETRs باسم/GUID كما هو موضح أدناه.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="القواعد في Exchange Transport" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>الموصلات الواردة

الموصلات عبارة عن مجموعة من الإرشادات التي تقوم بتخصيص كيفية تدفق بريدك الإلكتروني من وإلى Microsoft 365 أو مؤسسة Office 365. وهي تمكنك من تطبيق أي قيود أو عناصر تحكم أمنية. في مستكشف المخاطر، يمكنك عرض الموصلات المرتبطة بالبريد الإلكتروني والبحث عن رسائل البريد الإلكتروني باستخدام أسماء الموصلات.

البحث عن الموصلات هو استعلام CONTAINS، ما يعني أن عمليات البحث الجزئية للكلمة الأساسية يمكن أن تعمل:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="تفاصيل الموصل" lightbox="../../media/Connector_Details.png":::

## <a name="required-licenses-and-permissions"></a>التراخيص والأذونات المطلوبة

يجب أن يكون لديك [Microsoft Defender لـ Office 365](defender-for-office-365.md) لاستخدام عمليات الكشف في الوقت الحقيقي أو المستكشف.

- المستكشف مضمن في Defender لـ Office 365 الخطة 2.
- يتم تضمين تقرير الكشف في الوقت الحقيقي في Defender لـ Office 365 الخطة 1.
- خطط لتعيين تراخيص لكافة المستخدمين الذين يجب حمايتهم بواسطة Defender لـ Office 365. تعرض عمليات الكشف في المستكشف والوقت الحقيقي بيانات الكشف للمستخدمين المرخصين.

لعرض عمليات الكشف عن المستكشف أو في الوقت الحقيقي واستخدامها، يجب أن يكون لديك الأذونات التالية:

- في مدخل Microsoft 365 Defender:
  - إدارة المؤسسة
  - مسؤول الأمان (يمكن تعيين هذا في مركز إدارة Azure Active Directory (<https://aad.portal.azure.com>)
  - قارئ الأمان
- في Exchange Online:
  - إدارة المؤسسة
  - View-Only Organization Management
  - مستلمو View-Only
  - إدارة التوافق

لمعرفة المزيد حول الأدوار والأذونات، راجع الموارد التالية:

- [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>معلومات إضافية

- [البحث عن البريد الإلكتروني الضار الذي تم تسليمه والتحقيق فيه](investigate-malicious-email-that-was-delivered.md)
- [عرض الملفات الضارة التي تم اكتشافها في SharePoint Online و OneDrive و Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [الحصول على نظرة عامة على طرق العرض في مستكشف التهديدات (والكشف في الوقت الحقيقي)](threat-explorer-views.md)
- [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report)
- [التحقيق التلقائي والاستجابة في Microsoft Threat Protection](automated-investigation-response-office.md)
- [التحقيق في رسائل البريد الإلكتروني باستخدام صفحة وحدة البريد الإلكتروني](mdo-email-entity-page.md)
