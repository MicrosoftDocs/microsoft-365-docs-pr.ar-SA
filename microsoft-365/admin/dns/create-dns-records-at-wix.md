---
title: الاتصال سجلات DNS في Wix Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: تعرف على كيفية التحقق من مجالك بإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في Wix for Microsoft.
ms.openlocfilehash: 13dd84c9e7704a0680c2a3f0ca2e456767f6d231
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568489"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>الاتصال سجلات DNS في Wix Microsoft 365

**[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه.

إذا كان Wix هو موفر استضافة DNS الذي تتبعه، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني Skype for Business عبر الإنترنت وما إلى ذلك.

بعد إضافة هذه السجلات في Wix، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق من صحة

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من أنك تملك مجالك؛ ولا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا إذا أردت ذلك.

> [!NOTE]
> لا يدعم WIX إدخالات DNS للمناوين الفرعية.

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). سيطلب منك تسجيل الدخول أولا.

2. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدل.":::

3. حدد **+ إضافة سجل** في **صف TXT (نص)** لمحرر DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="حدد إضافة سجل.":::

4. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها.

   |اسم المضيف|قيمة TXT|TTL|
   |---|---|---|
   |ملء تلقائيا (اتركه فارغا)|MS=*msXXXXXXXX* <br/> **ملاحظة:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [如何实现 العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|ساعة واحدة|

5. **SelectSave**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="حدد حفظ.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.


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

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). سيطلب منك تسجيل الدخول أولا.

1. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدل.":::

1. ضمن **MX (تبادل البريد)**، حدد **تحرير سجلات MX**.

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="حدد تحرير سجلات MX.":::

1. اختر **غير** ذلك من القائمة المنسدل، وحدد **+ إضافة سجل**.

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="حدد غير ذلك من القائمة المنسدل.":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها:

   |اسم المضيف|يشير إلى|الأولوية|TTL|
   |---|---|---|---|
   |ملء تلقائيا|*\<domain-key\>*.mail.protection.outlook.com <br/> **ملاحظة:** احصل على *\<domain-key\>* حسابك في Microsoft.  [如何实现 العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|0 <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml)|ساعة واحدة|

1. إذا كانت هناك أي سجلات MX أخرى مدرجة، فاحذف كل سجل منها.

  :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="حدد حذف.":::

1. حدد **حفظ**.

## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). سيطلب منك تسجيل الدخول أولا.

2. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدل.":::

3. حدد **+ إضافة سجل** في **الصف CNAME (الأسماء** المستعارة) في محرر DNS لسجل CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="حدد + إضافة سجل.":::

4. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها:

   |اسم المضيف|القيمة|TTL|
   |---|---|---|
   |autodiscover|autodiscover.outlook.com|ساعة واحدة|

5. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="حدد حفظ.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك لديه أكثر من سجل SPF واحد، فسوف تحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل التسليم وتصنيف البريد العشوائي. إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك *سجل SPF* واحد يتضمن مجموعتي القيم.

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). سيطلب منك تسجيل الدخول أولا.

2. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدل.":::

3. حدد **+ إضافة سجل** في **صف TXT (نص)** لمحرر DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="حدد + إضافة سجل.":::

   **ملاحظة**: يوفر Wix صف SPF في محرر DNS. تجاهل هذا الصف، ثم استخدم **صف TXT (نص)** لإدخال قيم SPF أدناه.

4. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها:

   |اسم المضيف|القيمة|TTL|
   |---|---|---|
   |[اترك هذا فارغا]|v=spf1 include:spf.protection.outlook.com -all <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة.|ساعة واحدة|

5. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="حدد حفظ.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. Skype إلى أربعة سجلات: سجلي SRV للاتصالات بين المستخدمين، وسجلي CNAME من أجل تسجيل الدخول والاتصال بين المستخدمين والخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). سيطلب منك تسجيل الدخول أولا.

1. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدل.":::

1. حدد **+ إضافة سجل** في صف **SRV** في محرر DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="حدد + إضافة سجل.":::

1. في مربعات السجل الجديد، اكتب القيم من الصف الأول في الجدول أو انسخها واللصق بها:

   |الخدمة|البروتوكول|اسم المضيف|الوزن|المنفذ|الهدف|الأولوية|TTL|
   |---|---|---|---|---|---|---|---|
   |sip|tls|ملء تلقائيا|1|443|sipdir.online.lync.com|100|ساعة واحدة|
   |sipfed|tcp|ملء تلقائيا|1|5061|sipfed.online.lync.com|100|ساعة واحدة|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="حدد حفظ.":::

1. أضف سجل SRV الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

1. حدد **+ إضافة آخر** في **الصف CNAME (الأسماء** المستعارة) لمحرر DNS، وأدخل القيم من الصف الأول في الجدول التالي.

   |النوع|Host|القيمة|TTL|
   |---|---|---|---|
   |CNAME|sip|sipdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|
   |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="حدد حفظ.":::

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: Intune و Mobile 裝置管理 for Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل مجالك وإدارتها عن بعد. يحتاج 裝置管理 المحمول إلى سجلي CNAME حتى يمكن للمستخدمين تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين للهواتف 裝置管理

1. للبدء، انتقل إلى صفحة المجالات في Wix باستخدام [هذا الارتباط](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). سيطلب منك تسجيل الدخول أولا.

1. حدد **المجالات** \> **...**، ثم حدد **إدارة سجلات DNS** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدل.":::

1. حدد **+ إضافة سجل** في **الصف CNAME (الأسماء** المستعارة) في محرر DNS لسجل CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="حدد + إضافة سجل.":::

1. أدخل القيم من الصف الأول في الجدول التالي.

    |النوع|Host|القيمة|TTL|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|
    |CNAME|enterpriseenrollment|enterpriseenrollment.manage.microsoft.com. <br/> **يجب أن تنتهي هذه القيمة بفترة (.)**|ساعة واحدة|

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="حدد حفظ.":::

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
