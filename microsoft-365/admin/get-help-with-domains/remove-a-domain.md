---
title: إزالة مجال
f1.keywords:
- NOCSH
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
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: تعرف على كيفية إزالة مجال قديم من Microsoft 365 المستخدمين والمجموعات إلى مجال آخر أو إلغاء اشتراكك.
ms.openlocfilehash: 3da47275e090296c9b192b4bd60ad19dd8cf4149
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567744"
---
# <a name="remove-a-domain"></a>إزالة مجال

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه.

هل تقوم بإزالة مجالك لأنك تريد إضافته إلى خطة اشتراك Microsoft 365 أخرى؟ أو هل تريد فقط إلغاء اشتراكك؟ يمكنك تغيير [خطتك أو اشتراكك](../../commerce/subscriptions/switch-to-a-different-plan.md) أو [إلغاء اشتراكك](../../commerce/subscriptions/cancel-your-subscription.md).

> [!TIP]
> إذا كنت بحاجة إلى مساعدة بشأن الخطوات في هذا الموضوع، فنظر [في العمل مع أحد متخصصي Microsoft small business](https://go.microsoft.com/fwlink/?linkid=2186871). باستخدام "المساعدة في العمل"، يمكنك أنت وموظفيك الوصول على مدار الساعة إلى المتخصصين في الشركات الصغيرة بينما تنمو أعمالك، من التكهين إلى الاستخدام اليومي.

### <a name="step-1-move-users-to-another-domain"></a>الخطوة 1: نقل المستخدمين إلى مجال آخر

#### <a name="move-users"></a>نقل المستخدمين

::: moniker range="o365-worldwide"

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز الإدارة</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">مركز الإدارة</a>.

::: moniker-end

2. حدد **UsersActive** >  users.

3. حدد المربعات بجانب أسماء جميع المستخدمين الذين تريد نقلهم.

4. في أعلى الصفحة، ثم اختر **تغيير المجالات**.

5. في الجزء **تغيير المجالات** ، حدد مجالا مختلفا.

ستحتاج إلى القيام بذلك لنفسك أيضا، إذا كنت على المجال الذي تريد إزالته. عند تحرير المجال لحسابك، يجب تسجيل الخروج وتسجيل الدخول مرة أخرى باستخدام المجال الجديد الذي اخترته للمتابعة.

#### <a name="move-yourself"></a>نقل نفسك

::: moniker range="o365-worldwide"

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز الإدارة</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">مركز الإدارة</a>.

::: moniker-end

2. انتقل إلى **المستخدمون** \> **الناشطون**، وحدد حسابك من القائمة.

3. على علامة **التبويب حساب** ، حدد **إدارة اسم** المستخدم، ثم اختر مجالا مختلفا.

4. في الأعلى، حدد اسم حسابك، ثم حدد **تسجيل الخروج**.

5. سجل الدخول باستخدام المجال الجديد وكلمة المرور نفسها.

يمكنك أيضا استخدام PowerShell لنقل المستخدمين إلى مجال آخر. راجع [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname) للحصول على مزيد من المعلومات. لتعيين المجال الافتراضي، استخدم [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

### <a name="step-2-move-groups-to-another-domain"></a>الخطوة 2: نقل المجموعات إلى مجال آخر

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى صفحة **مجموعات** \> المجموعات.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">مركز الإدارة،</a> انتقل إلى صفحة **مجموعات** > المجموعات.

::: moniker-end

2. حدد اسم المجموعة، ثم على علامة التبويب **عام** ضمن **عنوان البريد الإلكتروني،** أساسي، حدد **تحرير**.

3. استخدم القائمة المنسدل لاختيار مجال آخر.

4. حدد **حفظ**، ثم **إغلاق**. كرر هذه العملية لأي مجموعات أو قوائم توزيع مقترنة بالمجال الذي تريد إزالته.

### <a name="step-3-remove-the-old-domain"></a>الخطوة 3: إزالة المجال القديم

::: moniker range="o365-worldwide"

> [!NOTE]
> إذا كنت تقوم بإزالة مجال مخصص، فشاهد [إزالة مجال مخصص قبل](#remove-a-custom-domain) المتابعة.

1. في مركز الإدارة، **انتقل إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">المجالات</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى **الصفحة إعداد** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">مجالات</a> .

::: moniker-end

2. في صفحة **المجالات** ، حدد المجال الذي تريد إزالته.

3. في الجزء الأيمن، حدد **إزالة**.

4. اتبع أي مطالبة إضافية، ثم حدد **إغلاق**.




### <a name="remove-a-custom-domain"></a>إزالة مجال مخصص

إذا كنت تقوم بإلغاء اشتراكك واستخدام مجال مخصص، فهناك بعض الخطوات الإضافية التي يجب عليك القيام بها قبل أن تتمكن من إلغاء اشتراكك. 

#### <a name="change-your-domain-nameserver-records-if-needed"></a>تغيير سجلات أسماء المجالات (إذا لزم الأمر)

إذا قمت بإعداد مجال مخصص، أضفت سجلات DNS حتى يعمل المجال مع Microsoft 365 الخدمات. قبل إزالة مجالك، تأكد من تحديث سجلات DNS، مثل سجل MX لمجالك، لدى مضيف DNS.

على سبيل المثال، غير سجل MX لدى مضيف DNS. يتوقف البريد الإلكتروني المرسل إلى مجالك عن الوصول إلى عنوان Microsoft ويذهب إلى موفر البريد الإلكتروني الجديد بدلا من ذلك. (يحدد سجل MX مكان إرسال البريد الإلكتروني لمجالك.)

- إذا كانت سجلات خدمات الاسم (NS) تشير إلى [Microsoft 365](../../admin/setup/add-domain.md) من أسماء الخدمات، فلا يتم إدخال التغييرات على سجل MX حتى تقوم بتغيير سجلات NS لتشير إلى مضيف DNS الجديد (راجع الخطوة 2).

- قبل تحديث سجل MX، دع المستخدمين يعرفون التاريخ الذي تخطط فيه لتبديل بريدهم الإلكتروني وموفر البريد الإلكتروني الجديد الذي تخطط لاستخدامه. أيضا، إذا كان المستخدمون يرغبون في نقل بريدهم الإلكتروني الحالي من Microsoft إلى الموفر الجديد، فيجب عليهم اتخاذ خطوات إضافية.

- في اليوم الذي تقوم فيه بتغيير سجل MX، تأكد من حفظ [](/microsoft-365/commerce/subscriptions/cancel-your-subscription#save-your-data) البيانات و إلغاء [تثبيت Office إذا لزم الأمر](/microsoft-365/commerce/subscriptions/cancel-your-subscription#uninstall-office-optional).

#### <a name="update-your-domain-mx-and-other-dns-records-if-youre-using-a-custom-domain"></a>تحديث مجال MX وسجلات DNS الأخرى (إذا كنت تستخدم مجالا مخصصا)

إذا قمت بتبديل سجلات خدمات الاسم (NS) إلى Microsoft 365 عند إعداد مجالك، فيجب إعداد سجل MX وسجلات DNS الأخرى أو تحديثها لدى مضيف DNS الذي تخطط لاستخدامه، ثم تغيير سجل NS إلى مضيف DNS هذا.

إذا لم تقوم بتبديل سجلات NS عند إعداد مجالك، فعندما تغير سجل MX، يبدأ البريد الخاص بك في الانتقال إلى العنوان الجديد على الفور.

لتغيير سجلات NS، راجع تغيير أسماء الخدمات لإعداد Microsoft 365 [جهة تسجيل المجالات](../../admin/get-help-with-domains/change-nameservers-at-any-domain-registrar.md).



## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>ما المدة التي يستغرقها إزالة مجال ما؟

قد يستغرق الأمر أقل من 5 دقائق Microsoft 365 لإزالة مجال إذا لم يتم الإشارة إليه في الكثير من الأماكن مثل مجموعات الأمان وقوائم التوزيع والمستخدمين Microsoft 365 المجموعات. إذا كان هناك العديد من المراجع التي تستخدم المجال، فقد يستغرق الأمر عدة ساعات (يوم) لإزالة المجال.

إذا كان لديك المئات أو الآلاف من المستخدمين، فاستخدم PowerShell للاستعلام عن جميع المستخدمين ثم انتقالهم إلى مجال آخر. وإلا، فمن الممكن أن تفوت مجموعة من المستخدمين في واجهة المستخدم، وعند الانتقال لإزالة المجال، لن تتمكن من ذلك ولن تعرف السبب. راجع [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname) للحصول على مزيد من المعلومات. لتعيين المجال الافتراضي، استخدم [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

## <a name="still-need-help"></a>هل ما زلت بحاجة إلى المساعدة؟

::: moniker range="o365-worldwide"

> [!NOTE]
> لا يمكنك إزالة [المجال "onmicrosoft.com"](../setup/domains-faq.yml) من حسابك. عند إزالة مجال، سترجع حسابات المستخدمين إلى عنوان "onmicrosoft.com" ك SMTP/UserprincipalName الأساسي.

هل ما زلت لا تعمل؟ قد تحتاج إلى إزالة مجالك يدويا. [اتصل بنا](../../business-video/get-help-support.md) وسنساعدك على الاعتناء بها!

::: moniker-end

::: moniker range="o365-21vianet"

> [!NOTE]
> لا يمكنك إزالة [المجال "partner.onmschina.cn"](../setup/domains-faq.yml) من حسابك. عند إزالة مجال، سترجع حسابات المستخدمين إلى العنوان "partner.onmschina.cn" ك SMTP/UserprincipalName الأساسي.

هل ما زلت لا تعمل؟ قد تحتاج إلى إزالة مجالك يدويا. [اتصل بنا](../../business-video/get-help-support.md?view=o365-21vianet&preserve-view=true) وسنساعدك على الاعتناء بها!

::: moniker-end

## <a name="related-content"></a>المحتوى ذي الصلة

[الأسئلة الشائعة حول المجالات](../setup/domains-faq.yml) (مقالة)

[التبديل إلى خطة Microsoft 365 للأعمال](../../commerce/subscriptions/switch-to-a-different-plan.md) (مقالة)

[إلغاء اشتراكك](../../commerce/subscriptions/cancel-your-subscription.md) (مقالة)
