---
title: الاتصال سجلات DNS في IONOS بمقدار 1&1 إلى Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: تعرف على كيفية التحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في 1&1 IONOS ل Microsoft.
ms.openlocfilehash: 8afdfed0998a262b1df4c95a63e9086e4f71e5b6
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780666"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>الاتصال سجلات DNS في IONOS بمقدار 1&1 إلى Microsoft 365

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

إذا كان IONOS by 1&1 هو موفر استضافة DNS الخاص بك، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

## <a name="before-you-begin"></a>قبل البدء

لديك خياران لإعداد سجلات DNS لمجالك:

- [**استخدم المجال الاتصال**](#use-domain-connect-to-verify-and-set-up-your-domain) إذا لم تقم بإعداد مجالك مع موفر خدمة بريد إلكتروني آخر، فاستخدم الخطوات الاتصال المجال للتحقق تلقائيا من مجالك الجديد وإعداده لاستخدامه مع Microsoft 365.

    او

- [**استخدام الخطوات اليدوية**](#create-dns-records-with-manual-setup) تحقق من مجالك باستخدام الخطوات اليدوية أدناه واختر متى والسجلات التي تريد إضافتها إلى جهة تسجيل المجالات. يسمح لك هذا بإعداد سجلات MX (بريد) جديدة، على سبيل المثال، حسب راحتك.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>استخدام الاتصال المجال للتحقق من المجال وإعداده

اتبع هذه الخطوات للتحقق من IONOS وإعداده تلقائيا بواسطة مجال 1&1 باستخدام Microsoft 365:

1. في مركز مسؤولي Microsoft 365، حدد **الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>، وحدد المجال الذي تريد إعداده.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="حدد مجالك في Microsoft 365.":::

1. حدد النقاط الثلاث (المزيد من الإجراءات) > اختر **"بدء الإعداد**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. في "كيف تريد توصيل مجالك"؟ حدد **"متابعة**".

1. في صفحة إضافة سجلات DNS، حدد **إضافة سجلات DNS**.

1. في صفحة تسجيل الدخول IONOS بمقدار 1&1، سجل الدخول إلى حسابك، وحدد **الاتصال**، ثم **السماح**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="حدد الاتصال، ثم &quot;السماح&quot;.":::

    يؤدي ذلك إلى إكمال إعداد المجال Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>إنشاء سجلات DNS باستخدام الإعداد اليدوي

بعد إضافة هذه السجلات في IONOS بمقدار 1&1، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!CAUTION]
> لاحظ أن IONOS بمقدار 1&1 لا يسمح للمجال بالحصول على كل من سجل MX وسجل CNAME للمستوى الأعلى للتحقق التلقائي. هذا يحد من الطرق التي يمكنك من خلالها تكوين Exchange Online ل Microsoft. هناك حل بديل، ولكن نوصي باستخدامه **فقط** إذا كان لديك بالفعل خبرة في إنشاء مجالات فرعية في IONOS بمقدار 1&1.
> إذا [اخترت إدارة](../setup/domains-faq.yml) سجلات Microsoft DNS الخاصة بك في IONOS بواسطة 1&1، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من ملكيتك لمجالك؛ لا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في IONOS بمقدار 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). ستتم مطالبتك بتسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::

1. ضمن **Actions** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدلة.":::

1. حدد **"إضافة سجل**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد قسم **TXT** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="حدد قسم TXT.":::

1. في صفحة إضافة سجل DNS، في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها.

    |اسم المضيف|قيمه|TTL|
    |---|---|---|
    |(اترك هذا الحقل فارغا)|MS=ms *XXXXXXXX*  <br/> ملاحظة: هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|ساعة واحدة|

1. حدد **"حفظ**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="حدد &quot;حفظ&quot;.":::

    انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن بعد أن أضفت السجل إلى موقع جهة تسجيل المجالات، ستعود إلى Microsoft 365 وتطالب Microsoft 365 بالبحث عن السجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.

للتحقق من السجل في Microsoft 365:

1. في مركز الإدارة، انتقل إلى **الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.

1. في صفحة "المجالات"، حدد المجال الذي تتحقق منه، ثم حدد **"بدء الإعداد**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.

1. في صفحة **«Verify domain** »، حدد **«Verify»**.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX حتى يصل البريد الإلكتروني لمجالك إلى Microsoft

> [!NOTE]
> إذا قمت بالتسجيل باستخدام 1und1.de، [فسجل دخولك إلى هنا](https://go.microsoft.com/fwlink/?linkid=859152).

1. للبدء، انتقل إلى صفحة المجالات في IONOS بمقدار 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). ستتم مطالبتك بتسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::

1. ضمن **Actions** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدلة.":::

1. حدد **"إضافة سجل**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد قسم **MX** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="حدد قسم MX.":::

1. في صفحة إضافة سجل DNS، في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها.

    |اسم المضيف|يشير إلى|الاولويه|TTL|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com  <br/>  ملاحظة: احصل على حسابك \<domain-key\> في Microsoft. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|10  <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml)|ساعة واحدة|

1. حدد **"حفظ**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="حدد &quot;حفظ&quot;.":::

1. إذا كانت هناك أي سجلات MX مدرجة بالفعل، فاحذف كل منها عن طريق تحديد سلة المهملات " **حذف سجل** " في صفحة **"إضافة سجل** ".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="حدد حذف سجل.":::

### <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

> [!NOTE]
> إذا قمت بالتسجيل باستخدام 1und1.de، [فسجل دخولك إلى هنا](https://go.microsoft.com/fwlink/?linkid=859152).

1. للبدء، انتقل إلى صفحة المجالات في IONOS بمقدار 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). ستتم مطالبتك بتسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::

1. ضمن **Actions** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدلة.":::

   ستقوم الآن بإنشاء مجالين فرعيين وتعيين قيمة **الاسم المستعار** لكل منهما.

   (هذا مطلوب لأن 1&1 IONOS يدعم سجل CNAME واحد من المستوى الأعلى فقط، ولكن Microsoft تتطلب العديد من سجلات CNAME.)

   أولا، ستقوم بإنشاء المجال الفرعي Autodiscover.

1. حدد **المجالات الفرعية**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="حدد المجال الفرعي.":::

1. حدد **"Add subdomain**".

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="حدد إضافة مجالات فرعية.":::

1. في المربع **"إضافة مجال فرعي** " للمربع الفرعي الجديد، اكتب قيمة **"إضافة مجال فرعي** " أو انسخها والصقها فقط من الجدول التالي. (ستضيف قيمة **الاسم المستعار** في خطوة لاحقة.)

    |إضافة مجال فرعي|الاسم المستعار|
    |---|---|
    |Autodiscover|autodiscover.outlook.com|

1. ضمن **"Actions** " للمقطع الفرعي **للانشاء التلقائي** الذي قمت بإنشائه للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدلة.

1. حدد **"إضافة سجل**"، ثم حدد المقطع **CNAME** .

1. في الاسم **المستعار:** المربع، اكتب قيمة **الاسم المستعار** فقط من الجدول التالي أو انسخها والصقها.

    |إضافة مجال فرعي|الاسم المستعار|
    |---|---|
    |Autodiscover|autodiscover.outlook.com|

1. حدد **"حفظ**".

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك يحتوي على أكثر من سجل SPF واحد، فستحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل في التسليم وتصنيف البريد العشوائي. إذا كان لديك بالفعل سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك سجل SPF  *واحد*  يتضمن مجموعتي القيم. هل تحتاج إلى أمثلة؟ اطلع على [سجلات نظام أسماء المجالات الخارجية هذه ل Microsoft](../../enterprise/external-domain-name-system-records.md). للتحقق من صحة سجل SPF، يمكنك استخدام إحدى [أدوات التحقق من صحة SPF](../setup/domains-faq.yml) هذه.

> [!NOTE]
> إذا قمت بالتسجيل باستخدام 1und1.de، [فسجل دخولك إلى هنا](https://go.microsoft.com/fwlink/?linkid=859152).

1. للبدء، انتقل إلى صفحة المجالات في IONOS بمقدار 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). ستتم مطالبتك بتسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::

1. ضمن **Actions** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدلة.":::

1. حدد **"إضافة سجل**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد مقطع **SPF (TXT** ).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="حدد مقطع SPF (TXT).":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها.

    |نوع|اسم المضيف|قيمه|TTL|
    |---|---|---|---|
    |SPF (TXT)|(اترك هذا الحقل فارغا.)|v=spf1 include:spf.protection.outlook.com -all  <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|ساعة واحدة|

1. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="حدد &quot;حفظ&quot;.":::

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمكالمات الجماعية ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. يحتاج Skype إلى 4 سجلات: سجلان SRV للاتصال من مستخدم إلى مستخدم، وسجلان CNAME لتسجيل الدخول وتوصيل المستخدمين بالخدمة.

### <a name="add-two-additional-cname-records"></a>إضافة سجلين إضافيين من سجلات CNAME

1. للبدء، انتقل إلى صفحة المجالات في IONOS بمقدار 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). ستتم مطالبتك بتسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::

1. ضمن **Actions** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدلة.":::

   ستقوم الآن بإنشاء مجالين فرعيين وتعيين قيمة **الاسم المستعار** لكل منهما.

   (هذا مطلوب لأن 1&1 IONOS يدعم سجل CNAME واحد من المستوى الأعلى فقط، ولكن Microsoft تتطلب العديد من سجلات CNAME.)

   أولا، ستقوم بإنشاء المجال الفرعي lyncdiscover.

1. حدد **المجالات الفرعية**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="حدد المجال الفرعي.":::

1. حدد **"Add subdomain**".

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="حدد إضافة مجالات فرعية.":::

1. في المربع **"إضافة مجال فرعي** " للمربع الفرعي الجديد، اكتب قيمة **"إضافة مجال فرعي** " أو انسخها والصقها فقط من الجدول التالي. (ستضيف قيمة **الاسم المستعار** في خطوة لاحقة.)

    |إضافة مجال فرعي|الاسم المستعار|
    |---|---|
    |lyncdiscover   |webdir.online.lync.com  |

1. ضمن **"Actions** " **لمنطقة lyncdiscover** الفرعية التي قمت بإنشائها للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدلة.

1. حدد **"إضافة سجل**"، ثم حدد المقطع **CNAME** .

1. في الاسم **المستعار:** المربع، اكتب قيمة **الاسم المستعار** فقط من الجدول التالي أو انسخها والصقها.

    |إنشاء مجال فرعي|الاسم المستعار|
    |---|---|
    |lyncdiscover|webdir.online.lync.com|

1. إنشاء مجال فرعي آخر (SIP): حدد **"Add subdomain**".

1. في المربع **"إضافة مجال فرعي** " للمربع الفرعي الجديد، اكتب قيمة **"إضافة مجال فرعي** " أو انسخها والصقها فقط من الجدول التالي. (ستضيف قيمة **الاسم المستعار** في خطوة لاحقة.)

    |إضافة مجال فرعي|الاسم المستعار|
    |---|---|
    |المسبار|sipdir.online.lync.com|

1. ضمن **إجراءات** المجال الفرعي الذي أنشأته للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدلة.

1. حدد **"إضافة سجل**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد قسم **CNAME** .

1. في الاسم **المستعار:** المربع، اكتب قيمة **الاسم المستعار** فقط من الجدول التالي أو انسخها والصقها.

    |إنشاء مجال فرعي|الاسم المستعار|
    |---|---|
    |المسبار|sipdir.online.lync.com|

1. حدد خانة الاختيار لإخلاء المسؤولية **"أنا على علم** "، ثم حدد **"حفظ**".

## <a name="add-the-two-srv-records-required-for-microsoft"></a>إضافة سجلي SRV المطلوبين ل Microsoft

> [!NOTE]
> إذا قمت بالتسجيل باستخدام 1und1.de، [فسجل دخولك إلى هنا](https://go.microsoft.com/fwlink/?linkid=859152).

1. للبدء، انتقل إلى صفحة المجالات في IONOS بمقدار 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). ستتم مطالبتك بتسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::

1. ضمن **Actions** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدلة.":::

1. حدد **"إضافة سجل**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد قسم **SRV** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="حدد قسم SRV.":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها.

    |نوع|الخدمة|البروتوكول|اسم المضيف|يشير إلى|الاولويه|الوزن|منفذ|TTL|
    |---|---|---|---|---|---|---|---|---|
    |SRV|_sip|Tls|(اترك هذا الحقل فارغا.)|sipdir.online.lync.com|100|1|443|ساعة واحدة|
    |SRV|_sipfederationtls|Tcp|(اترك هذا الحقل فارغا.)|sipfed.online.lync.com|100|1|5061|ساعة واحدة|

1. حدد **"حفظ**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="حدد &quot;حفظ&quot;.":::

1. أضف سجل SRV الآخر.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: إدارة الجهاز Intune و Mobile ل Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل بمجالك وإدارتها عن بعد. يحتاج إدارة الجهاز الجوال إلى سجلين CNAME حتى يتمكن المستخدمون من تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

> [!IMPORTANT]
> اتبع إجراء المجال الفرعي الذي استخدمته لسجلات CNAME الأخرى، وقم بتوفير القيم من الجدول التالي.

1. للبدء، انتقل إلى صفحة المجالات في IONOS بمقدار 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). ستتم مطالبتك بتسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::

1. ضمن **Actions** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدلة.":::

   ستقوم الآن بإنشاء مجالين فرعيين وتعيين قيمة **الاسم المستعار** لكل منهما.

   (هذا مطلوب لأن 1&1 IONOS يدعم سجل CNAME واحد من المستوى الأعلى فقط، ولكن Microsoft تتطلب العديد من سجلات CNAME.)

   أولا، ستقوم بإنشاء المجال الفرعي lyncdiscover.

1. حدد **المجالات الفرعية**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="حدد المجال الفرعي.":::

1. حدد **"Add subdomain**".

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="حدد إضافة مجالات فرعية.":::

1. في المربع **"إضافة مجال فرعي** " للمربع الفرعي الجديد، اكتب قيمة **"إضافة مجال فرعي** " أو انسخها والصقها فقط من الجدول التالي. (ستضيف قيمة **الاسم المستعار** في خطوة لاحقة.)

    |إضافة مجال فرعي|الاسم المستعار|
    |---|---|
    |تسجيل المؤسسة|enterpriseregistration.windows.net|

1. ضمن **«Actions** » للمجال الفرعي **«enterpriseregistration»** الذي قمت بإنشائه للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدلة.

1. حدد **"إضافة سجل**"، ثم حدد المقطع **CNAME** .

1. في الاسم **المستعار:** المربع، اكتب قيمة **الاسم المستعار** فقط من الجدول التالي أو انسخها والصقها.

    |إضافة مجال فرعي|الاسم المستعار|
    |---|---|
    |تسجيل المؤسسة|enterpriseregistration.windows.net|

1. إنشاء مجال فرعي آخر: حدد **"Add subdomain**".

1. في المربع **"إضافة مجال فرعي** " للمربع الفرعي الجديد، اكتب قيمة **"إضافة مجال فرعي** " أو انسخها والصقها فقط من الجدول التالي. (ستضيف قيمة **الاسم المستعار** في خطوة لاحقة.)

    |إضافة مجال فرعي|الاسم المستعار|
    |---|---|
    |تسجيل المؤسسة|enterpriseenrollment-s.manage.microsoft.com|

1. ضمن **"Actions** " للمنطق الفرعي **"enterpriseenrollment** " الذي قمت بإنشائه للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدلة.

1. حدد **"إضافة سجل**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد قسم **CNAME** .

1. في الاسم **المستعار:** المربع، اكتب قيمة **الاسم المستعار** فقط من الجدول التالي أو انسخها والصقها.

    |إنشاء مجال فرعي|الاسم المستعار|
    |---|---|
    |تسجيل المؤسسة|enterpriseenrollment-s.manage.microsoft.com|

1. حدد خانة الاختيار لإخلاء المسؤولية **"أنا على علم** "، ثم حدد **"حفظ**".
