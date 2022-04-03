---
title: الاتصال سجلات DNS في Cloudflare Microsoft 365
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
description: تعرف على كيفية التحقق من مجالك بإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في Cloudflare ل Microsoft.
ms.openlocfilehash: a7f1307530d5dc874120db0f40b631ada4b833e8
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568017"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>الاتصال سجلات DNS في Cloudflare Microsoft 365

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه.

إذا كان Cloudflare هو موفر استضافة DNS الذي تتبعه، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

## <a name="before-you-begin"></a>قبل البدء

لديك خياران لإعداد سجلات DNS لمجالك:

- [**استخدم المجال الاتصال**](#use-domain-connect-to-verify-and-set-up-your-domain) إذا لم تقم بإعداد مجالك مع موفر خدمة بريد إلكتروني آخر، فاستخدم الخطوات Domain الاتصال للتحقق من مجالك الجديد تلقائيا ثم إعداده لاستخدامه مع Microsoft 365.

    OR

- [**استخدام الخطوات اليدوية**](#create-dns-records-with-manual-setup) تحقق من مجالك باستخدام الخطوات اليدوية أدناه واختر السجلات التي تريد إضافتها إلى جهة تسجيل المجالات ومتى يجب إضافتها. يسمح لك هذا الأمر بإعداد سجلات MX (بريد) جديدة، على سبيل المثال، بما يلائمك.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>استخدام المجال الاتصال للتحقق من مجالك ثم إعداده

اتبع هذه الخطوات للتحقق تلقائيا من مجال Cloudflare الخاص بك بإعداده باستخدام Microsoft 365:

1. في مركز مسؤولي Microsoft 365، **حدد** \> الإعدادات <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**المجالات**</a>، وحدد المجال الذي تريد إعداده.

1. حدد النقاط الثلاث (المزيد من الإجراءات) \> اختر **بدء الإعداد**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. في كيف تريد توصيل مجالك؟ ، حدد **متابعة**.

1. في الصفحة إضافة سجلات DNS، حدد **إضافة سجلات DNS**.

1. في صفحة تسجيل الدخول إلى Cloudflare، سجل الدخول إلى حسابك، وحدد **تخويل**.

    هذا يكمل إعداد مجالك Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>إنشاء سجلات DNS باستخدام الإعداد اليدوي

بعد إضافة هذه السجلات في Cloudflare، سيتم إعداد مجالك للعمل مع Microsoft 365 الخدمات.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="change-your-domains-nameserver-ns-records"></a>تغيير سجلات أسماء (NS) لمجالك

> [!IMPORTANT]
> يجب تنفيذ هذا الإجراء لدى جهة تسجيل المجالات حيث اشتريت مجالك وسجلته.

عند التسجيل للحصول على Cloudflare، أضفت مجالا باستخدام عملية إعداد Cloudflare.

تم شراء المجال الذي أضفته من Cloudflare أو جهة تسجيل مجالات منفصلة. للتحقق من سجلات DNS وإنشاءها لمجالك في Microsoft 365، ستحتاج أولا إلى تغيير خدمات أسماء جهة تسجيل المجالات بحيث تستخدم خدمات أسماء Cloudflare.

لتغيير خوادم أسماء مجالك في موقع جهة تسجيل المجالات على ويب بنفسك، اتبع الخطوات التالية.

1. ابحث عن المنطقة على موقع جهة تسجيل المجالات على ويب حيث يمكنك تحرير أسماء أسماء مجالاتك.

2. يمكنك إما إنشاء سجلين من سجلات أسماء الخدمة باستخدام القيم الموجودة في الجدول التالي، أو تحرير سجلات خدمات أسماء موجودة بحيث تتطابق مع هذه القيم.

    |النوع|القيمة|
    |---|---|
    |أول اسمserver|استخدم قيمة خدمة الاسم التي توفرها Cloudflare.|
    |خدمات الاسم الثاني|استخدم قيمة خدمة الاسم التي توفرها Cloudflare.|

    > [!TIP]
    > يجب استخدام سجلي خادم اسم على الأقل. إذا كان هناك أي خوادم أسماء أخرى مدرجة، يجب حذفها.

3. احفظ تغييراتك.

> [!NOTE]
> قد تستغرق تحديثات سجلات خدمة الاسم ما يصل إلى عدة ساعات للتحديث عبر نظام DNS على الإنترنت. بعد ذلك، سيتم تعيين البريد الإلكتروني والخدمات الأخرى من Microsoft للعمل مع مجالك.

### <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق من صحة

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من أنك تملك مجالك؛ ولا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة نظرة عامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+إضافة سجل**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد إضافة سجل.":::

1. حدد نوع TXT من القائمة المنسدل، ثم اكتب القيم من هذا الجدول أو انسخها واللصق بها.

    |النوع|الاسم|TTL|المحتوى|
    |---|---|---|:----|
    |TXT|@|30 دقيقة|MS=*msXXXXXXXX* <br/> **ملاحظة:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [如何实现 العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="حدد إضافة سجل.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن وقد أضفت السجل إلى موقع جهة تسجيل المجالات، سوف تعود إلى Microsoft وتبحث عن السجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.

للتحقق من السجل في Microsoft 365:

1. في مركز الإدارة، انتقل **إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**المجالات**</a>.

1. في صفحة المجالات، حدد المجال الذي تتحقق منه، ثم حدد **بدء الإعداد**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.

1. في صفحة **التحقق من المجال** ، حدد **التحقق**.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX بحيث يتم إرسال البريد الإلكتروني لمجالك إلى Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة نظرة عامة لمجالك، حدد **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+إضافة سجل**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد إضافة سجل.":::

1. حدد نوع MX من القائمة المنسدل، وا اكتب القيم من هذا الجدول أو انسخها واللصق بها.

   |النوع|الاسم|خادم البريد|TTL|الأولوية|
   |---|---|---|---|---|
   |MX|@|*\<domain-key\>*.mail.protection.outlook.com <br/> **ملاحظة:** احصل على *\<domain-key\>* حسابك من Microsoft 365 الخاص بك. [如何实现 العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|30 دقيقة|1 <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml) <br/>|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="حدد إضافة سجل.":::

1. إذا كانت هناك أي سجلات MX أخرى مدرجة في المقطع **سجلات MX** ، فاحذفها بتحديد **تحرير**، ثم حدد **حذف**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="حدد حذف.":::

1. في مربع حوار التأكيد، حدد **حذف** لتأكيد التغييرات.

### <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة نظرة عامة لمجالك، حدد **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة **إدارة DNS** ، حدد **+إضافة سجل**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد إضافة سجل.":::

1. حدد نوع CNAME من القائمة المنسدل، وا اكتب القيم من هذا الجدول أو انسخها واللصق بها.

    |النوع|الاسم|الهدف|TTL|
    |---|---|---|---|
    |CNAME|autodiscover|autodiscover.outlook.com|تلقائي|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="حدد حفظ.":::

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك لديه أكثر من سجل SPF واحد، فسوف تحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل التسليم وتصنيف البريد العشوائي. إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا لمجالك Microsoft 365. بدلا من ذلك، أضف Microsoft 365 المطلوبة إلى السجل الحالي بحيث يكون لديك *سجل SPF* واحد يتضمن مجموعتي القيم.

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة نظرة عامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+إضافة سجل**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد إضافة سجل.":::

1. حدد نوع TXT من القائمة المنسدل، ثم اكتب القيم من هذا الجدول أو انسخها واللصق بها.

    |النوع|الاسم|TTL|المحتوى|
    |---|---|---|---|
    |TXT|@|30 دقيقة|v=spf1 include:spf.protection.outlook.com -all <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة.|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="حدد حفظ.":::

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. Skype 4 سجلات: سجلان SRV للاتصالات بين المستخدمين، وسجلين CNAME من أجل تسجيل الدخول وربط المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

> [!IMPORTANT]
> ضع في اعتبارك أن Cloudflare مسؤول عن توفير هذه الوظيفة. في حال رأيت تعارضات بين الخطوات أدناه وواجهة مستخدم Cloudflare GUI (واجهة مستخدم رسومية)، يمكنك الاستفادة من [مجتمع Cloudflare](https://community.cloudflare.com/).

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة نظرة عامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+إضافة سجل**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد إضافة سجل.":::

1. حدد نوع SRV من القائمة المنسدل، وا اكتب القيم من هذا الجدول أو انسخها واللصق بها.

    |النوع|الاسم|الخدمة|البروتوكول|TTL|الأولوية|الوزن|المنفذ|الهدف|
    |---|---|---|---|---|---|---|---|---|
    |SRV|استخدم *domain_name؛* على سبيل المثال، contoso.com|_sip|TLS|30 دقيقة|100|1|443|sipfed.online.lync.com|
    |SRV|_sipfederationtls|TCP|استخدم *domain_name؛* على سبيل المثال، contoso.com|30 دقيقة|100|1|5061|sipfed.online.lync.com|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="حدد حفظ.":::

1. أضف سجل SRV الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة نظرة عامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+إضافة سجل**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد إضافة سجل.":::

1. حدد نوع CNAME من القائمة المنسدل، وا اكتب القيم من هذا الجدول أو انسخها واللصق بها.

    |النوع|الاسم|الهدف|TTL|
    |---|---|---|---|
    |CNAME|sip|sipdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|
    |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="حدد حفظ.":::

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: Intune و Mobile 裝置管理 for Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل مجالك وإدارتها عن بعد. يحتاج 裝置管理 المحمول إلى سجلي CNAME حتى يمكن للمستخدمين تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين للهواتف 裝置管理

1. للبدء، انتقل إلى صفحة المجالات في Cloudflare باستخدام [هذا الارتباط](https://www.cloudflare.com/a/login). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة الرئيسية، حدد المجال الذي تريد تحديثه.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="حدد المجال الذي تريد تحديثه.":::

1. في صفحة نظرة عامة لمجالك، حدد **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="حدد DNS.":::

1. في صفحة إدارة DNS، حدد **+إضافة سجل**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="حدد إضافة سجل.":::

1. حدد نوع CNAME من القائمة المنسدل، وا اكتب القيم من هذا الجدول أو انسخها واللصق بها.

    |النوع|الاسم|الهدف|TTL|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|
    |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="حدد حفظ.":::

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
