---
title: الاتصال سجلات DNS في 123-reg.co.uk Microsoft 365
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
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: تعرف على كيفية التحقق من مجالك بإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في 123-reg.co.uk Microsoft.
ms.openlocfilehash: 262aa3757e6dde90d328f596f43b20952d3080b0
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568127"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>الاتصال سجلات DNS في 123-reg.co.uk Microsoft 365

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه.

إذا 123-reg.co.uk موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني Skype for Business عبر الإنترنت وما إلى ذلك.

بعد إضافة هذه السجلات في 123-reg.co.uk، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق من صحة

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من أنك تملك مجالك؛ ولا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). سيطلب منك تسجيل الدخول أولا.

2. حدد **المجالات،** وفي الصفحة نظرة عامة حول اسم المجال، حدد اسم المجال الذي تريد التحقق منه أو انتقل إلى لوحة التحكم.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد المجال الذي تريد التحقق منه.":::

3. في الصفحة إدارة المجال، ضمن **إعدادات المجال المتقدمة**، اختر **إدارة DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

4. في الصفحة إدارة DNS، حدد **علامة التبويب DNS** المتقدمة.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب DNS المتقدمة.":::

5. في المربع **النوع** للسجل الجديد، اختر **TXT/SPF** من القائمة المنسدل، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها واللصق بها.

    |Hostname|النوع|الوجهة TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|MS=*msXXXXXXXX* <br/> **ملاحظة:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [如何实现 العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="حدد نوع TXT/SPF من القائمة المنسدل، ثم قم بتعبئة القيم.":::

6. حدد **إضافة**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="حدد إضافة.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن وقد أضفت السجل إلى موقع جهة تسجيل المجالات، سوف تعود إلى Microsoft وتطلب البحث عن السجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.

للتحقق من السجل في Microsoft 365:

1. في مركز الإدارة، انتقل **إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**المجالات**</a>.

1. في صفحة المجالات، حدد المجال الذي تتحقق منه، ثم حدد **بدء الإعداد**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.

1. في صفحة **التحقق من المجال** ، حدد **التحقق**.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX بحيث يتم إرسال البريد الإلكتروني لمجالك إلى Microsoft

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). سيطلب منك تسجيل الدخول أولا.

2. في الصفحة نظرة عامة حول اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

3. في الصفحة إدارة المجال، ضمن **إعدادات المجال المتقدمة**، اختر **إدارة DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

4. في الصفحة إدارة DNS، حدد **علامة التبويب DNS** المتقدمة.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب DNS المتقدمة.":::

5. في المربع **النوع** للسجل الجديد، اختر **MX** من القائمة المنسدل، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها واللصق بها.

    |Hostname|النوع|الأولوية|الوجهة MX|
    |---|---|---|---|
    |@|MX|1 <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml)|*\<domain-key\>*.mail.protection.outlook.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> **ملاحظة:** احصل على \<domain-key\> حسابك في Microsoft. [如何实现 العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="حدد نوع MX من القائمة المنسدل، ثم قم بتعبئة القيم.":::

6. حدد **إضافة**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="حدد إضافة.":::

7. إذا كان هناك أي سجلات MX أخرى، فإزالة كل منها عن طريق تحديد الأيقونة **حذف (** سلة المهملات) لهذا السجل.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="حدد حذف (سلة المهملات).":::

## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). سيطلب منك تسجيل الدخول أولا.

2. في الصفحة نظرة عامة حول اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

3. في الصفحة إدارة المجال، ضمن **إعدادات المجال المتقدمة**، اختر **إدارة DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

4. في الصفحة إدارة DNS، حدد **علامة التبويب DNS** المتقدمة.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب DNS المتقدمة.":::

5. إضافة سجل CNAME.

    في المربع **النوع** للسجل الجديد، اختر **CNAME** من القائمة المنسدل، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها واللصق بها.

    |Hostname|النوع|الوجهة CNAME|
    |---|---|---|
    |autodiscover|CNAME|autodiscover.outlook.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="حدد نوع CNAME من القائمة المنسدل، ثم قم بتعبئة القيم.":::

6. حدد **إضافة**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="حدد إضافة.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك لديه أكثر من سجل SPF واحد، فسوف تحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل التسليم وتصنيف البريد العشوائي. إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsfot. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك *سجل SPF* واحد يتضمن مجموعتي القيم. هل تحتاج إلى أمثلة؟ اطلع على [سجلات نظام أسماء المجالات الخارجية هذه ل Microsoft](../../enterprise/external-domain-name-system-records.md). للتحقق من صحة سجل SPF، يمكنك استخدام إحدى أدوات التحقق من صحة [SPF هذه](../setup/domains-faq.yml).

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). سيطلب منك تسجيل الدخول أولا.

2. في الصفحة نظرة عامة حول اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

3. في الصفحة إدارة المجال، ضمن **إعدادات المجال المتقدمة**، اختر **إدارة DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

4. في الصفحة إدارة DNS، حدد **علامة التبويب DNS** المتقدمة.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب DNS المتقدمة.":::

5. في المربع **النوع** للسجل الجديد، اختر **TXT/SPF** من القائمة المنسدل، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها واللصق بها.

    |Hostname|النوع|الوجهة TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|v=spf1 include:spf.protection.outlook.com -all <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="حدد نوع TXT/SPF من القائمة المنسدل، ثم قم بتعبئة القيم.":::

6. حدد **إضافة**.

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. Skype 4 سجلات: سجلان SRV للاتصالات بين المستخدمين، وسجلين CNAME من أجل تسجيل الدخول وربط المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). سيطلب منك تسجيل الدخول أولا.

2. في الصفحة نظرة عامة حول اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

3. في الصفحة إدارة المجال، ضمن **إعدادات المجال المتقدمة**، اختر **إدارة DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

4. في الصفحة إدارة DNS، حدد **علامة التبويب DNS** المتقدمة.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب DNS المتقدمة.":::

5. إضافة أول سجل من سجلي SRV:

   في المربع **النوع** للسجل الجديد، اختر **SRV** من القائمة المنسدل، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها واللصق بها.

    |Hostname|النوع|الأولوية|TTL|الوجهة SRV|
    |---|---|---|---|---|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة.|
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="حدد نوع TXT/SPF من القائمة المنسدل، ثم قم بتعبئة القيم.":::

6. حدد **إضافة**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="حدد إضافة.":::

7. إضافة سجل SRV الآخر.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>إضافة سجلي CNAME المطلوبين Skype for Business

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة نظرة عامة حول اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

1. في الصفحة إدارة المجال، ضمن **إعدادات المجال المتقدمة**، اختر **إدارة DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

1. في الصفحة إدارة DNS، حدد **علامة التبويب DNS** المتقدمة.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب DNS المتقدمة.":::

1. إضافة سجل CNAME الأول.

    في المربع **النوع** للسجل الجديد، اختر **CNAME** من القائمة المنسدل، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها واللصق بها.

    |Hostname|النوع|الوجهة CNAME|
    |---|---|---|
    |sip|CNAME|sipdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|
    |lyncdiscover|CNAME|webdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="حدد نوع CNAME من القائمة المنسدل، ثم قم بتعبئة القيم.":::

1. حدد **إضافة**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="حدد إضافة.":::

1. أضف سجل CNAME الآخر.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: Intune و Mobile 裝置管理 for Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل مجالك وإدارتها عن بعد. يحتاج 裝置管理 المحمول إلى سجلي CNAME حتى يمكن للمستخدمين تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين للهواتف 裝置管理

1. للبدء، انتقل إلى صفحة المجالات في 123-reg.co.uk باستخدام [هذا الارتباط](https://www.123-reg.co.uk/secure/cpanel/domain/overview). سيطلب منك تسجيل الدخول أولا.

1. في الصفحة نظرة عامة حول اسم المجال، حدد اسم المجال الذي تريد تحريره.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="حدد اسم المجال الذي تريد تحريره.":::

1. في الصفحة إدارة المجال، ضمن **إعدادات المجال المتقدمة**، اختر **إدارة DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

1. في الصفحة إدارة DNS، حدد **علامة التبويب DNS** المتقدمة.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="حدد علامة التبويب DNS المتقدمة.":::

1. إضافة سجل CNAME الأول.

    في المربع **النوع** للسجل الجديد، اختر **CNAME** من القائمة المنسدل، ثم اكتب القيم الأخرى من الجدول التالي أو انسخها واللصق بها.

   |Hostname|النوع|الوجهة CNAME|
   |---|---|---|
   |enterpriseregistration|CNAME|enterpriseregistration.windows.net. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|
   |enterpriseenrollment|CNAME|enterpriseenrollment.manage.microsoft.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="حدد نوع CNAME من القائمة المنسدل، ثم قم بتعبئة القيم.":::

1. حدد **إضافة**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="حدد إضافة.":::

1. أضف سجل CNAME الآخر.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
