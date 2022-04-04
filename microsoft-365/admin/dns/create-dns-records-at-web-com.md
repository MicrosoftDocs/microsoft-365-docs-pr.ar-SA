---
title: الاتصال سجلات DNS في web.com Microsoft 365
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
description: تعرف على كيفية التحقق من مجالك بإعداد سجلات DNS للبريد الإلكتروني Skype for Business عبر الإنترنت وخدمات أخرى في web.com Microsoft.
ms.openlocfilehash: 612c22b518402fccaf9ced76b2506aa15c0e89f6
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568401"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>الاتصال سجلات DNS في web.com Microsoft 365

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه.

إذا web.com موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني Skype for Business عبر الإنترنت وما إلى ذلك.

بعد إضافة هذه السجلات في web.com، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>تغيير سجلات أسماء (NS) لمجالك

> [!IMPORTANT]
> يجب تنفيذ هذا الإجراء لدى جهة تسجيل المجالات حيث اشتريت مجالك وسجلته.

عند التسجيل للحصول على web.com، أضفت مجالا باستخدام web.com **الإعداد** .

للتحقق من سجلات DNS وإنشاءها لمجالك في Microsoft، ستحتاج أولا إلى تغيير أسماء الخدمات لدى جهة تسجيل المجالات بحيث تستخدم web.com أسماء المستخدمين.

لتغيير خوادم أسماء مجالك في موقع جهة تسجيل المجالات على ويب بنفسك، اتبع الخطوات التالية.

1. ابحث عن المنطقة على موقع جهة تسجيل المجالات على ويب حيث يمكنك تحرير أسماء أسماء مجالاتك.

2. يمكنك إما إنشاء سجلين من سجلات أسماء الخدمة باستخدام القيم الموجودة في الجدول التالي، أو تحرير سجلات خدمات أسماء موجودة بحيث تتطابق مع هذه القيم.

    |النوع|القيمة|
    |---|---|
    |أول اسمserver|استخدم قيمة nameserver التي توفرها web.com.|
    |خدمات الاسم الثاني|استخدم قيمة nameserver التي توفرها web.com.|

    > [!TIP]
    > يجب استخدام سجلي خادم اسم على الأقل. إذا كان هناك أي خوادم أسماء أخرى مدرجة، يجب حذفها.

3. احفظ تغييراتك.

> [!NOTE]
> قد تستغرق تحديثات سجلات خدمة الاسم ما يصل إلى عدة ساعات للتحديث عبر نظام DNS على الإنترنت. بعد ذلك، سيتم تعيين البريد الإلكتروني والخدمات الأخرى من Microsoft للعمل مع مجالك.

## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق من صحة

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من أنك تملك مجالك؛ ولا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). سجل الدخول أولا.

1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ إضافة سجل**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + إضافة سجل.":::

1. ضمن **النوع**، حدد **TXT** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="حدد TXT من القائمة المنسدل النوع.":::

1. حدد القيم من الجدول التالي أو قم بنسخها ولصقها.

    |يشير إلى|قيمة TXT|TTL|
    |---|---|:----|
    |@|MS=*msXXXXXXXX* <br/> **ملاحظة:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [如何实现 العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|ساعة واحدة|

1. حدد **إضافة**.

    انتظر بضع دقائق قبل التحقق من سجل TXT الجديد، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن وقد أضفت السجل إلى موقع جهة تسجيل المجالات، سوف تعود إلى Microsoft وتطلب السجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.

للتحقق من السجل في Microsoft 365:

1. في مركز الإدارة، انتقل **إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**المجالات**</a>.

1. في صفحة المجالات، حدد المجال الذي تتحقق منه، ثم حدد **بدء الإعداد**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.

1. في صفحة **التحقق من المجال** ، حدد **التحقق**.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX بحيث يتم إرسال البريد الإلكتروني لمجالك إلى Microsoft

1. للبدء، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). سجل الدخول أولا.

1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ إضافة سجل**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + إضافة سجل.":::

1. ضمن **النوع**، حدد **MX** من القائمة المنسدل.

1. حدد القيم من الجدول التالي أو قم بنسخها ولصقها.

    |يشير إلى|خادم البريد|الأولوية|TTL|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com <br/> **ملاحظة:** احصل على *\<domain-key\>* من مركز إدارة Microsoft. [如何实现 العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml) <br/> 1|ساعة واحدة|

1. حدد **إضافة**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="حدد إضافة.":::

1. إذا كان هناك أي سجلات MX أخرى، فاحذفها كلها عن طريق تحديد أداة التحرير، ثم **حذف** لكل سجل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="حدد تحرير.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). سجل الدخول أولا.

1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ إضافة سجل**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + إضافة سجل.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="حدد CNAME من القائمة المنسدل النوع.":::

1. حدد القيم من الجدول التالي أو قم بنسخها ولصقها.

    |يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
    |---|---|---|---|
    |مضيف آخر|autodiscover|autodiscover.outlook.com|ساعة واحدة|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها واللصق بها في النافذة.":::

1. حدد **إضافة**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك لديه أكثر من سجل SPF واحد، فسوف تحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل التسليم وتصنيف البريد العشوائي. إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك *سجل SPF* واحد يتضمن مجموعتي القيم.

1. للبدء، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). سجل الدخول أولا.

1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ إضافة سجل**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + إضافة سجل.":::

1. ضمن **النوع**، حدد **TXT** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="حدد TXT من القائمة المنسدل النوع.":::

1. حدد القيم من الجدول التالي أو قم بنسخها ولصقها.

    |يشير إلى|قيمة TXT|TTL|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة.|ساعة واحدة|

1. حدد **إضافة**.

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. Skype 4 سجلات: سجلان SRV للاتصالات بين المستخدمين، وسجلين CNAME من أجل تسجيل الدخول وربط المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). سجل الدخول أولا.

1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ إضافة سجل**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + إضافة سجل.":::

1. ضمن **النوع**، حدد **SRV** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="حدد SRV من القائمة المنسدل النوع.":::

1. حدد القيم من الجدول التالي أو قم بنسخها ولصقها.

    |النوع|الخدمة|البروتوكول|الوزن|المنفذ|الهدف|الأولوية|TTL|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)**|1|ساعة واحدة|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)**|1|ساعة واحدة|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="اكتب القيم من الجدول أو انسخها واللصق فيها في نافذة سجل SRV.":::

1. حدد **إضافة**.

1. أضف سجل SRV الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). سجل الدخول أولا.

1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ إضافة سجل**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + إضافة سجل.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="حدد CNAME من القائمة المنسدل النوع.":::

1. حدد القيم من الجدول التالي أو قم بنسخها ولصقها.

    |النوع|يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
    |---|---|---|---|---|
    |CNAME|مضيف آخر|sip|sipdir.online.lync.com <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|
    |CNAME|مضيف آخر|lyncdiscover|webdir.online.lync.com <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها واللصق بها في النافذة.":::

1. حدد **إضافة**.

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: Intune و Mobile 裝置管理 for Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل مجالك وإدارتها عن بعد. يحتاج 裝置管理 المحمول إلى سجلي CNAME حتى يمكن للمستخدمين تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين للهواتف 裝置管理

1. للبدء، انتقل إلى صفحة المجالات في web.com باستخدام [هذا الارتباط](https://checkout.web.com/manage-it/index.jsp). سجل الدخول أولا.

1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ إضافة سجل**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="حدد + إضافة سجل.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="حدد CNAME من القائمة المنسدل النوع.":::

1. حدد القيم من الجدول التالي أو قم بنسخها ولصقها.

    |النوع|يشير إلى|اسم المضيف|الاسم المستعار إلى|TTL|
    |---|---|---|---|---|
    |CNAME|مضيف آخر|enterpriseregistration|enterpriseregistration.windows.net <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|
    |CNAME|مضيف آخر|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها واللصق فيها من الجدول في النافذة.":::

1. حدد **إضافة**.

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
