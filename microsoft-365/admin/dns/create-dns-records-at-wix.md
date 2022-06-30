---
title: توصيل سجلات DNS في Wix ب Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: تعرف على كيفية التحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online والخدمات الأخرى في Wix for Microsoft.
ms.openlocfilehash: 9ae245481173b99a9cb1221ed0650dc0b91feecd
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563176"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>توصيل سجلات DNS في Wix ب Microsoft 365

**[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

إذا كان Wix هو موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

بعد إضافة هذه السجلات في Wix، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من ملكيتك له. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من ملكيتك لمجالك؛ لا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا إذا أردت ذلك.

> [!NOTE]
> لا يدعم WIX إدخالات DNS للمساطر الفرعية.

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). ستتم مطالبتك بتسجيل الدخول أولا.

2. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدلة.":::

3. حدد **+ إضافة سجل** في صف **TXT (النص)** لمحرر DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="حدد &quot;إضافة سجل&quot;.":::

4. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها.

   |اسم المضيف|قيمة TXT|TTL|
   |---|---|---|
   |معبؤ تلقائيا (اتركه فارغا)|MS=ms *XXXXXXXX* <br/> **ملاحظه:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|ساعة واحدة|

5. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="حدد &quot;حفظ&quot;.":::

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

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). ستتم مطالبتك بتسجيل الدخول أولا.

1. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدلة.":::

1. ضمن **MX (تبادل البريد)،** حدد **"تحرير سجلات MX**".

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="حدد تحرير سجلات MX.":::

1. اختر **"أخرى** " من القائمة المنسدلة، وحدد **+ "إضافة سجل**".

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="حدد &quot;أخرى&quot; من القائمة المنسدلة.":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها:

   |اسم المضيف|يشير إلى|الاولويه|TTL|
   |---|---|---|---|
   |معبؤ تلقائيا|*\<domain-key\>*.mail.protection.outlook.com <br/> **ملاحظه:** احصل على حسابك *\<domain-key\>* في Microsoft.  [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|0 <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml)|ساعة واحدة|

1. إذا كانت هناك أي سجلات MX أخرى مدرجة، فاحذف كل منها.

  :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="حدد Delete.":::

1. حدد **حفظ**.

## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). ستتم مطالبتك بتسجيل الدخول أولا.

2. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدلة.":::

3. حدد **+ إضافة سجل** في صف **CNAME (الأسماء المستعارة)** لمحرر DNS لسجل CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="حدد + إضافة سجل.":::

4. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها:

   |اسم المضيف|قيمه|TTL|
   |---|---|---|
   |Autodiscover|autodiscover.outlook.com|ساعة واحدة|

5. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="حدد &quot;حفظ&quot;.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك يحتوي على أكثر من سجل SPF واحد، فستحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل في التسليم وتصنيف البريد العشوائي. إذا كان لديك بالفعل سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك سجل SPF *واحد* يتضمن مجموعتي القيم.

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). ستتم مطالبتك بتسجيل الدخول أولا.

2. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدلة.":::

3. حدد **+ إضافة سجل** في صف **TXT (النص)** لمحرر DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="حدد + إضافة سجل.":::

   **ملاحظة**: يوفر Wix صف SPF في محرر DNS. تجاهل هذا الصف واستخدام الصف **TXT (النص)** لإدخال قيم SPF أدناه.

4. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها:

   |اسم المضيف|قيمه|TTL|
   |---|---|---|
   |[اترك هذا فارغا]|v=spf1 include:spf.protection.outlook.com -all <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|ساعة واحدة|

5. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="حدد &quot;حفظ&quot;.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. يحتاج Skype إلى أربعة سجلات: سجلان SRV للاتصال من مستخدم إلى مستخدم، وسجلي CNAME لتسجيل الدخول وتوصيل المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). ستتم مطالبتك بتسجيل الدخول أولا.

1. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدلة.":::

1. حدد **+ إضافة سجل** في صف **SRV** لمحرر DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="حدد + إضافة سجل.":::

1. في مربعات السجل الجديد، اكتب القيم أو انسخها والصقها من الصف الأول في الجدول:

   |الخدمة|البروتوكول|اسم المضيف|الوزن|منفذ|الهدف|الاولويه|TTL|
   |---|---|---|---|---|---|---|---|
   |المسبار|Tls|معبؤ تلقائيا|1|443|sipdir.online.lync.com|100|ساعة واحدة|
   |sipfed|Tcp|معبؤ تلقائيا|1|5061|sipfed.online.lync.com|100|ساعة واحدة|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="حدد &quot;حفظ&quot;.":::

1. أضف سجل SRV الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>إضافة سجلي CNAME المطلوبين Skype for Business

1. حدد **+ أضف آخر** في صف **CNAME (الأسماء المستعارة)** لمحرر DNS، وأدخل القيم من الصف الأول في الجدول التالي.

   |نوع|Host|قيمه|TTL|
   |---|---|---|---|
   |CNAME|المسبار|sipdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
   |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="حدد &quot;حفظ&quot;.":::

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>خيار متقدم: إدارة الجهاز Intune و Mobile ل Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل بمجالك وإدارتها عن بعد. يحتاج إدارة الجهاز الجوال إلى سجلين CNAME حتى يتمكن المستخدمون من تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين ل Mobile إدارة الجهاز

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). ستتم مطالبتك بتسجيل الدخول أولا.

1. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدلة.":::

1. حدد **+ إضافة سجل** في صف **CNAME (الأسماء المستعارة)** لمحرر DNS لسجل CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="حدد + إضافة سجل.":::

1. أدخل القيم من الصف الأول في الجدول التالي.

    |نوع|Host|قيمه|TTL|
    |---|---|---|---|
    |CNAME|تسجيل المؤسسة|enterpriseregistration.windows.net. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
    |CNAME|تسجيل المؤسسة|enterpriseenrollment.manage.microsoft.com. <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="حدد &quot;حفظ&quot;.":::

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
