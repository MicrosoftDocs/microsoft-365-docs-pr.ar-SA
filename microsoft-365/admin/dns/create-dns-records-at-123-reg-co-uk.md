---
title: توصيل سجلات DNS في 123-reg.co.uk ب Microsoft 365
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
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: تعرف على كيفية التحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في 123-reg.co.uk ل Microsoft.
ms.openlocfilehash: 97a00c046f467dd4ced4c63a4cbfc8114d06d2dd
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563396"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>توصيل سجلات DNS في 123-reg.co.uk ب Microsoft 365

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

إذا كان 123-reg.co.uk هو موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

بعد إضافة هذه السجلات في 123-reg.co.uk، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من ملكيتك لمجالك؛ لا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). ستتم مطالبتك بتسجيل الدخول أولا.

2. حدد **المجالات**، وفي صفحة النظرة العامة على اسم المجال، حدد اسم المجال الذي تريد التحقق منه أو انتقل إلى لوحة التحكم.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد المجال الذي تريد التحقق منه.":::

3. في صفحة "إدارة المجال"، ضمن **إعدادات المجال المتقدمة**، اختر **"إدارة DNS**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

4. في صفحة "إدارة DNS"، حدد علامة التبويب **"DNS متقدمة** ".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب Advanced DNS.":::

5. في مربع **"النوع"** للسجل الجديد، اختر **TXT/SPF** من القائمة المنسدلة، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها والصقها.

    |المضيف|نوع|الوجهة TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|MS=ms *XXXXXXXX* <br/> **ملاحظه:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="حدد نوع TXT/SPF من القائمة المنسدلة، وقم بتعبئة القيم.":::

6. حدد **"إضافة**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="حدد &quot;إضافة&quot;.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن بعد أن أضفت السجل إلى موقع جهة تسجيل المجالات، ستعود إلى Microsoft وتطالب بالبحث عن السجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.

للتحقق من السجل في Microsoft 365:

1. في مركز الإدارة، انتقل إلى **"مجالات الإعدادات**\>".<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. في صفحة "المجالات"، حدد المجال الذي تتحقق منه، ثم حدد **"بدء الإعداد**".

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.

1. في صفحة **«Verify domain** »، حدد **«Verify»**.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX حتى يصل البريد الإلكتروني لمجالك إلى Microsoft

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). ستتم مطالبتك بتسجيل الدخول أولا.

2. في صفحة نظرة عامة على اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

3. في صفحة "إدارة المجال"، ضمن **إعدادات المجال المتقدمة**، اختر **"إدارة DNS**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

4. في صفحة "إدارة DNS"، حدد علامة التبويب **"DNS متقدمة** ".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب Advanced DNS.":::

5. في المربع **"النوع"** للسجل الجديد، اختر **MX** من القائمة المنسدلة، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها والصقها.

    |المضيف|نوع|الاولويه|الوجهة MX|
    |---|---|---|---|
    |@|MX|1 <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml)|*\<domain-key\>*.mail.protection.outlook.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)** <br/> **ملاحظه:** احصل على حسابك \<domain-key\> في Microsoft. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="حدد نوع MX من القائمة المنسدلة، وقم بتعبئة القيم.":::

6. حدد **"إضافة**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="حدد &quot;إضافة&quot;.":::

7. إذا كان هناك أي سجلات MX أخرى، فقم بإزالة كل منها عن طريق تحديد أيقونة **Delete (سلة المهملات)** لهذا السجل.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="حدد Delete (سلة المهملات).":::

## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). ستتم مطالبتك بتسجيل الدخول أولا.

2. في صفحة نظرة عامة على اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

3. في صفحة "إدارة المجال"، ضمن **إعدادات المجال المتقدمة**، اختر **"إدارة DNS**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

4. في صفحة "إدارة DNS"، حدد علامة التبويب **"DNS متقدمة** ".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب Advanced DNS.":::

5. إضافة سجل CNAME.

    في المربع **"النوع"** للسجل الجديد، اختر **CNAME** من القائمة المنسدلة، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها والصقها.

    |المضيف|نوع|CNAME الوجهة|
    |---|---|---|
    |Autodiscover|CNAME|autodiscover.outlook.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="حدد نوع CNAME من القائمة المنسدلة، وقم بتعبئة القيم.":::

6. حدد **"إضافة**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="حدد &quot;إضافة&quot;.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك يحتوي على أكثر من سجل SPF واحد، فستحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل في التسليم وتصنيف البريد العشوائي. إذا كان لديك بالفعل سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsfot. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك سجل SPF *واحد* يتضمن مجموعتي القيم. هل تحتاج إلى أمثلة؟ اطلع على [سجلات نظام أسماء المجالات الخارجية هذه ل Microsoft](../../enterprise/external-domain-name-system-records.md). للتحقق من صحة سجل SPF، يمكنك استخدام إحدى [أدوات التحقق من صحة SPF](../setup/domains-faq.yml) هذه.

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). ستتم مطالبتك بتسجيل الدخول أولا.

2. في صفحة نظرة عامة على اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

3. في صفحة "إدارة المجال"، ضمن **إعدادات المجال المتقدمة**، اختر **"إدارة DNS**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

4. في صفحة "إدارة DNS"، حدد علامة التبويب **"DNS متقدمة** ".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب Advanced DNS.":::

5. في مربع **"النوع"** للسجل الجديد، اختر **TXT/SPF** من القائمة المنسدلة، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها والصقها.

    |المضيف|نوع|الوجهة TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|v=spf1 include:spf.protection.outlook.com -all <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="حدد نوع TXT/SPF من القائمة المنسدلة، وقم بتعبئة القيم.":::

6. حدد **"إضافة**".

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. يحتاج Skype إلى 4 سجلات: سجلان SRV للاتصال من مستخدم إلى مستخدم، وسجلي CNAME لتسجيل الدخول وتوصيل المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). ستتم مطالبتك بتسجيل الدخول أولا.

2. في صفحة نظرة عامة على اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

3. في صفحة "إدارة المجال"، ضمن **إعدادات المجال المتقدمة**، اختر **"إدارة DNS**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

4. في صفحة "إدارة DNS"، حدد علامة التبويب **"DNS متقدمة** ".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب Advanced DNS.":::

5. أضف أول سجل من سجلي SRV:

   في المربع **"النوع"** للسجل الجديد، اختر **SRV** من القائمة المنسدلة، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها والصقها.

    |المضيف|نوع|الاولويه|TTL|SRV الوجهة|
    |---|---|---|---|---|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **يجب أن تنتهي هذه القيمة بنقطة (.)** <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **يجب أن تنتهي هذه القيمة بنقطة (.)** <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="حدد نوع TXT/SPF من القائمة المنسدلة، وقم بتعبئة القيم.":::

6. حدد **"إضافة**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="حدد &quot;إضافة&quot;.":::

7. أضف سجل SRV الآخر.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>إضافة سجلي CNAME المطلوبين Skype for Business

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). ستتم مطالبتك بتسجيل الدخول أولا.

1. في صفحة نظرة عامة على اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

1. في صفحة "إدارة المجال"، ضمن **إعدادات المجال المتقدمة**، اختر **"إدارة DNS**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

1. في صفحة "إدارة DNS"، حدد علامة التبويب **"DNS متقدمة** ".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب Advanced DNS.":::

1. أضف سجل CNAME الأول.

    في المربع **"النوع"** للسجل الجديد، اختر **CNAME** من القائمة المنسدلة، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها والصقها.

    |المضيف|نوع|CNAME الوجهة|
    |---|---|---|
    |المسبار|CNAME|sipdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|
    |lyncdiscover|CNAME|webdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="حدد نوع CNAME من القائمة المنسدلة، وقم بتعبئة القيم.":::

1. حدد **"إضافة**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="حدد &quot;إضافة&quot;.":::

1. أضف سجل CNAME الآخر.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>خيار متقدم: إدارة الجهاز Intune و Mobile ل Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل بمجالك وإدارتها عن بعد. يحتاج إدارة الجهاز الجوال إلى سجلين CNAME حتى يتمكن المستخدمون من تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين ل Mobile إدارة الجهاز

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). ستتم مطالبتك بتسجيل الدخول أولا.

1. في صفحة نظرة عامة على اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

1. في صفحة "إدارة المجال"، ضمن **إعدادات المجال المتقدمة**، اختر **"إدارة DNS**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

1. في صفحة "إدارة DNS"، حدد علامة التبويب **"DNS متقدمة** ".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب Advanced DNS.":::

1. أضف سجل CNAME الأول.

    في المربع **"النوع"** للسجل الجديد، اختر **CNAME** من القائمة المنسدلة، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها والصقها.

   |المضيف|نوع|CNAME الوجهة|
   |---|---|---|
   |تسجيل المؤسسة|CNAME|enterpriseregistration.windows.net. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|
   |تسجيل المؤسسة|CNAME|enterpriseenrollment.manage.microsoft.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="حدد نوع CNAME من القائمة المنسدلة، وقم بتعبئة القيم.":::

1. حدد **"إضافة**".

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="حدد &quot;إضافة&quot;.":::

1. أضف سجل CNAME الآخر.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
