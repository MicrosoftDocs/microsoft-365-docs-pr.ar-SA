---
title: توصيل سجلات DNS في Network Solutions ب Microsoft 365
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
ms.assetid: 1dc55f9f-5309-450f-acc3-b2b4119c8be3
description: تعرف على كيفية التحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online والخدمات الأخرى في Network Solutions for Microsoft.
ms.openlocfilehash: 6ebe81c17d02c0cc6126f75f3b6471e01a334db4
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563264"
---
# <a name="connect-your-dns-records-at-network-solutions-to-microsoft-365"></a>توصيل سجلات DNS في Network Solutions ب Microsoft 365

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

إذا كانت Network Solutions هي موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

بعد إضافة هذه السجلات في Network Solutions، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من ملكيتك لمجالك؛ لا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). ستتم مطالبتك بتسجيل الدخول.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. حدد خانة الاختيار الموجودة بجانب المجال الذي تريد تعديله.

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

   قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

1. في الصفحة "إدارة سجلات DNS المتقدمة"، حدد **+ADD RECORD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **TXT** من القائمة المنسدلة.

1. في مربعات السجل الجديد، اكتب القيم الموجودة في الجدول التالي أو انسخها والصقها.

   |يشير إلى|قيمة TXT|TTL|
   |---|---|---|
   |@  <br/> (سيقوم النظام بتغيير هذه القيمة إلى **@ (بلا)** عند حفظ السجل.)|MS=ms *XXXXXXXX*  <br/> **ملاحظه:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول.  [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|3600|

1. حدد **ADD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="حدد ADD.":::

   > [!NOTE]
   > حدد **"طريقة العرض الكلاسيكية** " في الزاوية العلوية اليسرى لعرض سجل TXT الذي أنشأته.

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

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

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). ستتم مطالبتك بتسجيل الدخول.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. حدد خانة الاختيار الموجودة بجانب المجال الذي تريد تعديله.

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. قم بالتمرير لأسفل لتحديد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

   قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

1. في الصفحة "إدارة سجلات DNS المتقدمة"، حدد **+ADD RECORD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **MX** من القائمة المنسدلة.

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها.

   |يشير إلى|خادم البريد|الاولويه|TTL|
   |---|---|---|---|
   |@|*\<domain-key\>*.mail.protection.outlook.com  <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)** <br/> **ملاحظه:** احصل على حسابك *\<domain-key\>* في Microsoft. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|0  <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml)|ساعة واحدة|

1. حدد **ADD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-MX-add.png" alt-text="حدد ADD.":::

   > [!NOTE]
   > حدد **"طريقة العرض الكلاسيكية** " في الزاوية العلوية اليسرى لعرض سجل TXT الذي أنشأته.

1. إذا كان هناك أي سجلات MX أخرى، فاحذفها كلها عن طريق تحديد أداة التحرير، ثم **احذف** لكل سجل.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-edit.png" alt-text="حدد أداة التحرير.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). ستتم مطالبتك بتسجيل الدخول.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. حدد خانة الاختيار الموجودة بجانب المجال الذي تريد تعديله.

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. حدد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

   قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

1. في الصفحة "إدارة سجلات DNS المتقدمة"، حدد **+ADD RECORD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="حدد نوع CNAME من القائمة المنسدلة.":::

1. في مربعات سجل CNAME، اكتب القيم من الجدول التالي أو انسخها والصقها.

   |يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
   |---|---|---|---|
   |مضيف آخر|Autodiscover|autodiscover.outlook.com **لا يمكن أن تنتهي هذه القيمة بنقطة (.)** <br/> ساعة واحدة|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها والصقها من الجدول في النافذة.":::

1. حدد **ADD**.

   > [!NOTE]
   > حدد **"طريقة العرض الكلاسيكية** " في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك يحتوي على أكثر من سجل SPF واحد، فستحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل في التسليم وتصنيف البريد العشوائي. إذا كان لديك بالفعل سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك سجل SPF  *واحد*  يتضمن مجموعتي القيم.

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). ستتم مطالبتك بتسجيل الدخول.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. حدد خانة الاختيار الموجودة بجانب المجال الذي تريد تعديله.

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. حدد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

   قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

1. في الصفحة "إدارة سجلات DNS المتقدمة"، حدد **+ADD RECORD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **TXT** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-TXT.png" alt-text="حدد TXT من القائمة المنسدلة &quot;النوع&quot;.":::

1. في مربعات السجل الجديد، اكتب القيم التالية أو انسخها والصقها.

   |يشير إلى|قيمة TXT|TTL
   |---|---|---|
   |@  <br/> (سيقوم النظام بتغيير هذه القيمة إلى **@ (بلا)** عند حفظ السجل.)|v=spf1 include:spf.protection.outlook.com -all  <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|ساعة واحدة|

1. حدد **ADD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="حدد ADD.":::

   > [!NOTE]
   > حدد **"طريقة العرض الكلاسيكية** " في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. يحتاج Skype إلى 4 سجلات: سجلان SRV للاتصال من مستخدم إلى مستخدم، وسجلي CNAME لتسجيل الدخول وتوصيل المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). ستتم مطالبتك بتسجيل الدخول.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. حدد خانة الاختيار الموجودة بجانب المجال الذي تريد تعديله.

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. حدد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

   قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

1. في الصفحة "إدارة سجلات DNS المتقدمة"، حدد **+ADD RECORD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **SRV** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv.png" alt-text="حدد SRV من القائمة المنسدلة &quot;النوع&quot;.":::

1. في مربعات السجلين الجديدين، اكتب القيم من الجدول التالي أو انسخها والصقها.

   (اختر قيم **الخدمة** **والبروتوكول** من القوائم المنسدلة.)

   |نوع|الخدمة|البروتوكول|الوزن|منفذ|الهدف|الاولويه|TTL|
   |---|---|---|---|---|---|---|---|
   |SRV|_sip|TLS|100|443|sipdir.online.lync.com  <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|1|ساعة واحدة|
   |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com  <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|1|ساعة واحدة|

1. حدد **ADD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv-add.png" alt-text="حدد ADD.":::

   > [!NOTE]
   > حدد **"طريقة العرض الكلاسيكية** " في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.

1. أضف سجل SRV الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>إضافة سجلي CNAME المطلوبين Skype for Business

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). ستتم مطالبتك بتسجيل الدخول.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. حدد خانة الاختيار الموجودة بجانب المجال الذي تريد تعديله.

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. حدد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

   قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

1. في صفحة إدارة سجلات DNS المتقدمة، حدد **+ ADD RECORD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="حدد نوع CNAME من القائمة المنسدلة.":::

1. في مربعات سجل CNAME، اكتب القيم من الجدول التالي أو انسخها والصقها.

   |نوع|يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
   |---|---|---|---|---|
   |CNAME|مضيف آخر|المسبار|sipdir.online.lync.com  <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
   |CNAME|مضيف آخر|lyncdiscover|webdir.online.lync.com  <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها والصقها من الجدول في النافذة.":::

1. حدد **ADD**.

   > [!NOTE]
   > حدد **"طريقة العرض الكلاسيكية** " في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>خيار متقدم: إدارة الجهاز Intune و Mobile ل Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل بمجالك وإدارتها عن بعد. يحتاج إدارة الجهاز الجوال إلى سجلين CNAME حتى يتمكن المستخدمون من تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين ل Mobile إدارة الجهاز

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). ستتم مطالبتك بتسجيل الدخول.

1. في الصفحة المنتقل إليها، حدد **"أسماء المجالات**".

1. حدد خانة الاختيار الموجودة بجانب المجال الذي تريد تعديله.

1. ضمن **"Actions"**، حدد النقاط الثلاث، ثم حدد **"إدارة** " في القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد &quot;إدارة&quot; من القائمة المنسدلة.":::

1. حدد **"أدوات متقدمة**"، وإلى جانب **سجلات DNS المتقدمة**، حدد **MANAGE**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى جانب سجلات DNS المتقدمة، حدد MANAGE.":::

   قد تحتاج إلى تحديد **"متابعة** " للوصول إلى صفحة "إدارة سجلات DNS المتقدمة".

1. في الصفحة "إدارة سجلات DNS المتقدمة"، حدد **+ADD RECORD**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="حدد نوع CNAME من القائمة المنسدلة.":::

1. في مربعات سجل CNAME، اكتب القيم من الجدول التالي أو انسخها والصقها.

   |نوع|يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
   |---|---|---|---|---|
   |CNAME|مضيف آخر|تسجيل المؤسسة|enterpriseregistration.windows.net  <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
   |CNAME|مضيف آخر|تسجيل المؤسسة|enterpriseenrollment-s.manage.microsoft.com  <br/> **لا يمكن أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها والصقها من الجدول في النافذة.":::

1. حدد **ADD**.

   > [!NOTE]
   > حدد **"طريقة العرض الكلاسيكية** " في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

