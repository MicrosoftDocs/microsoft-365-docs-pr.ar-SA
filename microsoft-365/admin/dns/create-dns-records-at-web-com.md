---
title: توصيل سجلات DNS في web.com ب Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: تعرف على كيفية التحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في web.com ل Microsoft.
ms.openlocfilehash: d247ee24c107318289dfbca0ee741d5a04725d25
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563220"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>توصيل سجلات DNS في web.com ب Microsoft 365

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

إذا كان web.com هو موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

بعد إضافة هذه السجلات في web.com، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>تغيير سجلات خوادم الأسماء (NS) لمجالك

> [!IMPORTANT]
> يجب تنفيذ هذا الإجراء لدى جهة تسجيل المجالات حيث قمت بشراء مجالك وتسجيله.

عند التسجيل للحصول على web.com، أضفت مجالا باستخدام عملية **إعداد** web.com.

للتحقق من سجلات DNS وإنشاءها لمجالك في Microsoft، تحتاج أولا إلى تغيير خوادم الأسماء لدى جهة تسجيل المجالات بحيث تستخدم خوادم الأسماء web.com.

لتغيير خوادم أسماء مجالك في موقع جهة تسجيل المجالات على ويب بنفسك، اتبع الخطوات التالية.

1. ابحث عن المنطقة الموجودة على موقع جهة تسجيل المجالات على ويب حيث يمكنك تحرير خوادم الأسماء لمجالك.

2. يمكنك إما إنشاء سجلين لخوادم الأسماء باستخدام القيم الموجودة في الجدول التالي، أو تحرير سجلات خوادم الأسماء الموجودة بحيث تتطابق مع هذه القيم.

    |نوع|قيمه|
    |---|---|
    |خادم الأسماء الأول|استخدم قيمة خادم الأسماء التي توفرها web.com.|
    |خادم الأسماء الثاني|استخدم قيمة خادم الأسماء التي توفرها web.com.|

    > [!TIP]
    > يجب استخدام سجلين على الأقل لخادم الأسماء. إذا كان هناك أي خوادم أسماء أخرى مدرجة، يجب حذفها.

3. احفظ التغييرات التي أجريتها.

> [!NOTE]
> قد تستغرق تحديثات سجل خوادم الأسماء ما يصل إلى عدة ساعات للتحديث عبر نظام DNS الخاص بالإنترنت. بعد ذلك، سيتم تعيين البريد الإلكتروني والخدمات الأخرى من Microsoft للعمل مع مجالك.

## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من ملكيتك لمجالك؛ لا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. لبدء الاستخدام، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). تسجيل الدخول أولا.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

    قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

1. في صفحة إدارة سجلات DNS المتقدمة، حدد **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + ADD RECORD.":::

1. ضمن **النوع**، حدد **TXT** من القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="حدد TXT من القائمة المنسدلة &quot;النوع&quot;.":::

1. حدد القيم من الجدول التالي أو انسخها والصقها.

    |يشير|قيمة TXT|TTL|
    |---|---|:----|
    |@|MS=ms *XXXXXXXX* <br/> **ملاحظه:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|ساعة واحدة|

1. حدد **ADD**.

    انتظر بضع دقائق قبل التحقق من سجل TXT الجديد، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن بعد أن أضفت السجل إلى موقع جهة تسجيل المجالات، ستعود إلى Microsoft وتطالب بالسجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.

للتحقق من السجل في Microsoft 365:

1. في مركز الإدارة، انتقل إلى **"مجالات الإعدادات**\>".<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. في صفحة "المجالات"، حدد المجال الذي تتحقق منه، ثم حدد **"بدء الإعداد**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.

1. في صفحة **«Verify domain** »، حدد **«Verify»**.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX حتى يصل البريد الإلكتروني لمجالك إلى Microsoft

1. لبدء الاستخدام، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). تسجيل الدخول أولا.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

    قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

1. في صفحة إدارة سجلات DNS المتقدمة، حدد **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + ADD RECORD.":::

1. ضمن **النوع**، حدد **MX** من القائمة المنسدلة.

1. حدد القيم من الجدول التالي أو انسخها والصقها.

    |يشير إلى|خادم البريد|الاولويه|TTL|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com <br/> **ملاحظه:** احصل على معلوماتك *\<domain-key\>* من مركز إدارة Microsoft. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml) <br/> 1|ساعة واحدة|

1. حدد **ADD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="حدد ADD.":::

1. إذا كان هناك أي سجلات MX أخرى، فاحذفها كلها عن طريق تحديد أداة التحرير، ثم **احذف** لكل سجل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="حدد &quot;تحرير&quot;.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. لبدء الاستخدام، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). تسجيل الدخول أولا.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

    قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

1. في صفحة إدارة سجلات DNS المتقدمة، حدد **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + ADD RECORD.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="حدد CNAME من القائمة المنسدلة &quot;النوع&quot;.":::

1. حدد القيم من الجدول التالي أو انسخها والصقها.

    |يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
    |---|---|---|---|
    |مضيف آخر|Autodiscover|autodiscover.outlook.com|ساعة واحدة|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها والصقها في النافذة.":::

1. حدد **ADD**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك يحتوي على أكثر من سجل SPF واحد، فستحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل في التسليم وتصنيف البريد العشوائي. إذا كان لديك بالفعل سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك سجل SPF *واحد* يتضمن مجموعتي القيم.

1. لبدء الاستخدام، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). تسجيل الدخول أولا.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

    قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

1. في صفحة إدارة سجلات DNS المتقدمة، حدد **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + ADD RECORD.":::

1. ضمن **النوع**، حدد **TXT** من القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="حدد TXT من القائمة المنسدلة &quot;النوع&quot;.":::

1. حدد القيم من الجدول التالي أو انسخها والصقها.

    |يشير إلى|قيمة TXT|TTL|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|ساعة واحدة|

1. حدد **ADD**.

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. يحتاج Skype إلى 4 سجلات: سجلان SRV للاتصال من مستخدم إلى مستخدم، وسجلي CNAME لتسجيل الدخول وتوصيل المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. لبدء الاستخدام، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). تسجيل الدخول أولا.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

    قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

1. في صفحة إدارة سجلات DNS المتقدمة، حدد **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + ADD RECORD.":::

1. ضمن **النوع**، حدد **SRV** من القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="حدد SRV من القائمة المنسدلة &quot;النوع&quot;.":::

1. حدد القيم من الجدول التالي أو انسخها والصقها.

    |نوع|الخدمة|البروتوكول|الوزن|منفذ|الهدف|الاولويه|TTL|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|1|ساعة واحدة|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|1|ساعة واحدة|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="اكتب القيم من الجدول أو انسخها والصقها في نافذة سجل SRV.":::

1. حدد **ADD**.

1. أضف سجل SRV الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>إضافة سجلي CNAME المطلوبين Skype for Business

1. لبدء الاستخدام، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). تسجيل الدخول أولا.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

    قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

1. في صفحة إدارة سجلات DNS المتقدمة، حدد **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + ADD RECORD.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="حدد CNAME من القائمة المنسدلة &quot;النوع&quot;.":::

1. حدد القيم من الجدول التالي أو انسخها والصقها.

    |نوع|يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
    |---|---|---|---|---|
    |CNAME|مضيف آخر|المسبار|sipdir.online.lync.com <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
    |CNAME|مضيف آخر|lyncdiscover|webdir.online.lync.com <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها والصقها في النافذة.":::

1. حدد **ADD**.

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>خيار متقدم: إدارة الجهاز Intune و Mobile ل Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل بمجالك وإدارتها عن بعد. يحتاج إدارة الجهاز الجوال إلى سجلين CNAME حتى يتمكن المستخدمون من تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين ل Mobile إدارة الجهاز

1. لبدء الاستخدام، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). تسجيل الدخول أولا.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

    قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

1. في صفحة إدارة سجلات DNS المتقدمة، حدد **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + ADD RECORD.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدلة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="حدد CNAME من القائمة المنسدلة &quot;النوع&quot;.":::

1. حدد القيم من الجدول التالي أو انسخها والصقها.

    |نوع|يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
    |---|---|---|---|---|
    |CNAME|مضيف آخر|تسجيل المؤسسة|enterpriseregistration.windows.net <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
    |CNAME|مضيف آخر|تسجيل المؤسسة|enterpriseenrollment-s.manage.microsoft.com <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها والصقها من الجدول في النافذة.":::

1. حدد **ADD**.

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
