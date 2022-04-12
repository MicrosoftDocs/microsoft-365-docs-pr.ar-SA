---
title: الاتصال سجلات DNS في Cloudflare إلى Microsoft 365
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
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: تعرف على كيفية التحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online والخدمات الأخرى في Cloudflare ل Microsoft.
ms.openlocfilehash: 164a681cccac3385d2ca963ac58706c8e743bc1e
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780358"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>الاتصال سجلات DNS في Cloudflare إلى Microsoft 365

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

إذا كان Cloudflare هو موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

## <a name="before-you-begin"></a>قبل البدء

لديك خياران لإعداد سجلات DNS لمجالك:

- [**استخدم المجال الاتصال**](#use-domain-connect-to-verify-and-set-up-your-domain) إذا لم تقم بإعداد مجالك مع موفر خدمة بريد إلكتروني آخر، فاستخدم الخطوات الاتصال المجال للتحقق تلقائيا من مجالك الجديد وإعداده لاستخدامه مع Microsoft 365.

    او

- [**استخدام الخطوات اليدوية**](#create-dns-records-with-manual-setup) تحقق من مجالك باستخدام الخطوات اليدوية أدناه واختر متى والسجلات التي تريد إضافتها إلى جهة تسجيل المجالات. يسمح لك هذا بإعداد سجلات MX (بريد) جديدة، على سبيل المثال، حسب راحتك.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>استخدام الاتصال المجال للتحقق من المجال وإعداده

اتبع هذه الخطوات للتحقق تلقائيا من مجال Cloudflare وإعداده باستخدام Microsoft 365:

1. في مركز مسؤولي Microsoft 365، حدد **الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**المجالات**</a>، وحدد المجال الذي تريد إعداده.

1. حدد النقاط الثلاث (مزيد من الإجراءات) \> اختر **بدء الإعداد**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. في "كيف تريد توصيل مجالك"؟ حدد **"متابعة**".

1. في صفحة إضافة سجلات DNS، حدد **إضافة سجلات DNS**.

1. في صفحة تسجيل الدخول إلى Cloudflare، سجل الدخول إلى حسابك، وحدد **Authorize**.

    يؤدي ذلك إلى إكمال إعداد المجال Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>إنشاء سجلات DNS باستخدام الإعداد اليدوي

بعد إضافة هذه السجلات في Cloudflare، سيتم إعداد مجالك للعمل مع خدمات Microsoft 365.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="change-your-domains-nameserver-ns-records"></a>تغيير سجلات خوادم الأسماء (NS) لمجالك

> [!IMPORTANT]
> يجب تنفيذ هذا الإجراء لدى جهة تسجيل المجالات حيث قمت بشراء مجالك وتسجيله.

عند التسجيل في Cloudflare، أضفت مجالا باستخدام عملية إعداد Cloudflare.

تم شراء المجال الذي أضفته من Cloudflare أو من جهة تسجيل مجالات منفصلة. للتحقق من سجلات DNS وإنشاءها لمجالك في Microsoft 365، تحتاج أولا إلى تغيير خوادم الأسماء لدى جهة تسجيل المجالات بحيث تستخدم خوادم أسماء Cloudflare.

لتغيير خوادم أسماء مجالك في موقع جهة تسجيل المجالات على ويب بنفسك، اتبع الخطوات التالية.

1. ابحث عن المنطقة الموجودة على موقع جهة تسجيل المجالات على ويب حيث يمكنك تحرير خوادم الأسماء لمجالك.

2. يمكنك إما إنشاء سجلين لخوادم الأسماء باستخدام القيم الموجودة في الجدول التالي، أو تحرير سجلات خوادم الأسماء الموجودة بحيث تتطابق مع هذه القيم.

    |نوع|قيمه|
    |---|---|
    |خادم الأسماء الأول|استخدم قيمة خادم الأسماء التي توفرها Cloudflare.|
    |خادم الأسماء الثاني|استخدم قيمة خادم الأسماء التي توفرها Cloudflare.|

    > [!TIP]
    > يجب استخدام سجلين على الأقل لخادم الأسماء. إذا كان هناك أي خوادم أسماء أخرى مدرجة، يجب حذفها.

3. احفظ التغييرات التي أجريتها.

> [!NOTE]
> قد تستغرق تحديثات سجل خوادم الأسماء ما يصل إلى عدة ساعات للتحديث عبر نظام DNS الخاص بالإنترنت. بعد ذلك، سيتم تعيين البريد الإلكتروني والخدمات الأخرى من Microsoft للعمل مع مجالك.

### <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من ملكيتك لمجالك؛ لا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). ستتم مطالبتك بتسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة النظرة العامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+Add record**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد نوع TXT من القائمة المنسدلة، واكتب القيم من هذا الجدول أو انسخها والصقها.

    |نوع|الاسم|TTL|المحتوي|
    |---|---|---|:----|
    |النص|@|30 دقيقة|MS=*msXXXXXXXXXX* <br/> **ملاحظه:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|

1. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن بعد أن أضفت السجل إلى موقع جهة تسجيل المجالات، ستعود إلى Microsoft وتبحث عن السجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.

للتحقق من السجل في Microsoft 365:

1. في مركز الإدارة، انتقل إلى **الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.

1. في صفحة "المجالات"، حدد المجال الذي تتحقق منه، ثم حدد **"بدء الإعداد**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.

1. في صفحة **«Verify domain** »، حدد **«Verify»**.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX حتى يصل البريد الإلكتروني لمجالك إلى Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). ستتم مطالبتك بتسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة النظرة العامة لمجالك، حدد **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+Add record**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد نوع MX من القائمة المنسدلة، واكتب القيم من هذا الجدول أو انسخها والصقها.

   |نوع|الاسم|خادم البريد|TTL|الاولويه|
   |---|---|---|---|---|
   |MX|@|*\<domain-key\>*.mail.protection.outlook.com <br/> **ملاحظه:** احصل على حسابك *\<domain-key\>* في Microsoft 365. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|30 دقيقة|1 <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml) <br/>|

1. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. إذا كانت هناك أي سجلات MX أخرى مدرجة في قسم **سجلات MX** ، فاحذفها عن طريق تحديد **"تحرير**"، ثم حدد **"حذف**".

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="حدد Delete.":::

1. في مربع حوار التأكيد، حدد **"حذف** " لتأكيد التغييرات.

### <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). ستتم مطالبتك بتسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة النظرة العامة لمجالك، حدد **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة **إدارة DNS** ، حدد **+Add record**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد نوع CNAME من القائمة المنسدلة، واكتب القيم من هذا الجدول أو انسخها والصقها.

    |نوع|الاسم|الهدف|TTL|
    |---|---|---|---|
    |CNAME|Autodiscover|autodiscover.outlook.com|تلقائي|

1. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="حدد &quot;حفظ&quot;.":::

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك يحتوي على أكثر من سجل SPF واحد، فستحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل في التسليم وتصنيف البريد العشوائي. إذا كان لديك بالفعل سجل SPF لمجالك، فلا تنشئ سجلا جديدا Microsoft 365. بدلا من ذلك، أضف قيم Microsoft 365 المطلوبة إلى السجل الحالي بحيث يكون لديك سجل SPF *واحد* يتضمن مجموعتي القيم.

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). ستتم مطالبتك بتسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة النظرة العامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+Add record**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد نوع TXT من القائمة المنسدلة، واكتب القيم من هذا الجدول أو انسخها والصقها.

    |نوع|الاسم|TTL|المحتوي|
    |---|---|---|---|
    |النص|@|30 دقيقة|v=spf1 include:spf.protection.outlook.com -all <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|

1. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="حدد &quot;حفظ&quot;.":::

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمكالمات الجماعية ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. يحتاج Skype إلى 4 سجلات: سجلان SRV للاتصال من مستخدم إلى مستخدم، وسجلان CNAME لتسجيل الدخول وتوصيل المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

> [!IMPORTANT]
> ضع في اعتبارك أن Cloudflare مسؤول عن إتاحة هذه الوظيفة. في حالة ظهور اختلافات بين الخطوات أدناه وواجهة المستخدم الرسومية Cloudflare الحالية (واجهة المستخدم الرسومية)، يمكنك الاستفادة من [Cloudflare Community](https://community.cloudflare.com/).

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). ستتم مطالبتك بتسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة النظرة العامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+Add record**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد نوع SRV من القائمة المنسدلة، واكتب القيم من هذا الجدول أو انسخها والصقها.

    |نوع|الاسم|الخدمة|البروتوكول|TTL|الاولويه|الوزن|منفذ|الهدف|
    |---|---|---|---|---|---|---|---|---|
    |SRV|استخدم *domain_name* الخاص بك؛ على سبيل المثال، contoso.com|_sip|TLS|30 دقيقة|100|1|443|sipfed.online.lync.com|
    |SRV|_sipfederationtls|TCP|استخدم *domain_name* الخاص بك؛ على سبيل المثال، contoso.com|30 دقيقة|100|1|5061|sipfed.online.lync.com|

1. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="حدد &quot;حفظ&quot;.":::

1. أضف سجل SRV الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>إضافة سجلي CNAME المطلوبين Skype for Business

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). ستتم مطالبتك بتسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة النظرة العامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+Add record**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد نوع CNAME من القائمة المنسدلة، واكتب القيم من هذا الجدول أو انسخها والصقها.

    |نوع|الاسم|الهدف|TTL|
    |---|---|---|---|
    |CNAME|المسبار|sipdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
    |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

1. حدد **الحفظ**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="حدد &quot;حفظ&quot;.":::

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: إدارة الجهاز Intune و Mobile ل Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل بمجالك وإدارتها عن بعد. يحتاج إدارة الجهاز الجوال إلى سجلين CNAME حتى يتمكن المستخدمون من تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين ل Mobile إدارة الجهاز

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). ستتم مطالبتك بتسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة النظرة العامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+Add record**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

1. حدد نوع CNAME من القائمة المنسدلة، واكتب القيم من هذا الجدول أو انسخها والصقها.

    |نوع|الاسم|الهدف|TTL|
    |---|---|---|---|
    |CNAME|تسجيل المؤسسة|enterpriseregistration.windows.net. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
    |CNAME|تسجيل المؤسسة|enterpriseenrollment-s.manage.microsoft.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

1. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="حدد &quot;حفظ&quot;.":::

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
