---
title: الاتصال سجلات DNS في GoDaddy إلى Microsoft 365
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
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: تعرف على كيفية التحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في GoDaddy ل Microsoft.
ms.openlocfilehash: 6cf110b55c76ce6c857f13dcd5b0075b309b654f
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780336"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>الاتصال سجلات DNS في GoDaddy إلى Microsoft 365

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

إذا كان GoDaddy هو موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك وإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

## <a name="before-you-begin"></a>قبل البدء

لديك خياران لإعداد سجلات DNS لمجالك:

- [**استخدم المجال الاتصال**](#use-domain-connect-to-verify-and-set-up-your-domain) إذا لم تقم بإعداد مجالك مع موفر خدمة بريد إلكتروني آخر، فاستخدم الخطوات الاتصال المجال للتحقق تلقائيا من مجالك الجديد وإعداده لاستخدامه مع Microsoft 365.

   او

- [**استخدام الخطوات اليدوية**](#create-dns-records-with-manual-setup) تحقق من مجالك باستخدام الخطوات اليدوية أدناه واختر متى والسجلات التي تريد إضافتها إلى جهة تسجيل المجالات. يسمح لك هذا بإعداد سجلات MX (بريد) جديدة، على سبيل المثال، حسب راحتك.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>استخدام الاتصال المجال للتحقق من المجال وإعداده

اتبع هذه الخطوات للتحقق تلقائيا من مجال GoDaddy وإعداده باستخدام Microsoft 365:

1. في مركز مسؤولي Microsoft 365، حدد **الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>، وحدد المجال الذي تريد إعداده.

1. حدد النقاط الثلاث (المزيد من الإجراءات) > اختر **"بدء الإعداد**".

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. في "كيف تريد توصيل مجالك"؟ حدد **"متابعة**".

1. في صفحة إضافة سجلات DNS، حدد **إضافة سجلات DNS**.

1. في صفحة تسجيل الدخول إلى GoDaddy، سجل الدخول إلى حسابك، وحدد **Authorize**.

   يؤدي ذلك إلى إكمال إعداد المجال Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>إنشاء سجلات DNS باستخدام الإعداد اليدوي

بعد إضافة هذه السجلات في GoDaddy، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من ملكيتك لمجالك؛ لا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **"المنتجات الخاصة بي**".

1. ضمن **"المجالات"**، حدد النقاط الثلاث الموجودة بجانب المجال الذي تريد التحقق منه، ثم حدد **"إدارة DNS**".

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

1. ضمن **"سجلات"**، حدد **ADD** (قد تحتاج إلى التمرير لأسفل).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد ADD.":::

1. اختر **TXT** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد TXT من القائمة المنسدلة &quot;النوع&quot;.":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول أو انسخها والصقها.

   |نوع|Host|قيمة TXT|TTL|
   |---|---|---|---|
   |النص|@|MS=ms *XXXXXXXX*<br>**ملاحظة**: هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|ساعة واحدة  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="املأ القيم من الجدول لسجل TXT.":::

1. حدد **"حفظ**".

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="حدد &quot;حفظ&quot;.":::

   انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن بعد أن أضفت السجل إلى موقع جهة تسجيل المجالات، ستعود إلى Microsoft وتطالب بالسجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.
  
للتحقق من السجل في Microsoft 365:
  
1. في مركز الإدارة، انتقل إلى **الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.

1. في صفحة "المجالات"، حدد المجال الذي تتحقق منه، ثم حدد **"بدء الإعداد**".

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.
  
1. في صفحة **«Verify domain** »، حدد **«Verify»**.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX حتى يصل البريد الإلكتروني لمجالك إلى Microsoft

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **"المنتجات الخاصة بي**".

2. ضمن **"المجالات"**، حدد النقاط الثلاث الموجودة بجانب المجال الذي تريد التحقق منه، ثم حدد **"إدارة DNS**".

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

3. ضمن **السجلات**، حدد **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد ADD.":::

4. اختر **MX** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد MX من القائمة المنسدلة &quot;النوع&quot;.":::

5. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها والصقها.

   (اختر **قيمي "النوع** " و" **TTL** " من القائمة المنسدلة.)

   |نوع|Host|يشير إلى|الاولويه|TTL|
   |---|---|---|---|---|
   |MX|@| *\<domain-key\>*.mail.protection.outlook.com  <br/> **ملاحظه:** احصل على حسابك *\<domain-key\>* في Microsoft. [كيف أعمل العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|10  <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml)|ساعة واحدة|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="املأ القيم من الجدول لسجل MX.":::

6. حدد **"حفظ**".

### <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **"المنتجات الخاصة بي**".

2. ضمن **"المجالات"**، حدد النقاط الثلاث الموجودة بجانب المجال الذي تريد التحقق منه، ثم حدد **"إدارة DNS**".

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

3. ضمن **السجلات**، حدد **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد ADD.":::

4. اختر **CNAME** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد CNAME من القائمة المنسدلة &quot;النوع&quot;.":::

5. إنشاء سجل CNAME.

   في مربعات السجل الجديد، اكتب القيم من الصف الأول من الجدول التالي أو انسخها والصقها.

   (اختر قيمة **TTL** من القائمة المنسدلة.)

   |نوع|Host|يشير إلى|TTL|
   |---|---|---|---|
   |CNAME|Autodiscover|autodiscover.outlook.com|ساعة واحدة|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="املأ القيم من الجدول لسجل CNAME.":::

6. حدد **"حفظ**".

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك يحتوي على أكثر من سجل SPF واحد، فستحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل في التسليم وتصنيف البريد العشوائي. إذا كان لديك بالفعل سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك سجل SPF  *واحد*  يتضمن مجموعتي القيم.

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **"المنتجات الخاصة بي**".

2. ضمن **"المجالات"**، حدد النقاط الثلاث الموجودة بجانب المجال الذي تريد التحقق منه، ثم حدد **"إدارة DNS**".

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

3. ضمن **السجلات**، حدد **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد ADD.":::

4. اختر **TXT** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد TXT من القائمة المنسدلة &quot;النوع&quot;.":::

5. في مربعات السجل الجديد، اكتب القيم التالية أو انسخها والصقها.

   (اختر قيمة **TTL** من القوائم المنسدلة.)

   |نوع|Host|قيمة TXT|TTL|
   |---|---|---|---|
   |النص|@|v=spf1 include:spf.protection.outlook.com -all  <br/> **ملاحظه:** نوصي بنسخ هذا الإدخال ولصقه، بحيث يبقى كل التباعد صحيحا.|ساعة واحدة|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="املأ القيم من الجدول لسجل TXT.":::

6. حدد **"حفظ**".

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمكالمات الجماعية ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. يحتاج Skype إلى 4 سجلات: سجلان SRV للاتصال من مستخدم إلى مستخدم، وسجلان CNAME لتسجيل الدخول وتوصيل المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **"المنتجات الخاصة بي**".

1. ضمن **"المجالات"**، حدد النقاط الثلاث الموجودة بجانب المجال الذي تريد التحقق منه، ثم حدد **"إدارة DNS**".

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

1. ضمن **السجلات**، حدد **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد ADD.":::

1. اختر **SRV** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد SRV من القائمة المنسدلة &quot;النوع&quot;.":::

1. إنشاء سجل SRV الأول.

   في مربعات السجل الجديد، اكتب القيم من الصف الأول من الجدول التالي أو انسخها والصقها.

   (اختر **قيمي "النوع** " و" **TTL** " من القوائم المنسدلة.)

   |نوع|الخدمة|البروتوكول|الاسم|الهدف|الاولويه|الوزن|منفذ|TTL|
   |---|---|---|---|---|---|---|---|---|
   |SRV|_sip|_tls|@|sipdir.online.lync.com|100| 1|443|ساعة واحدة|
   |SRV|_sipfederationtls|_tcp|@| sipfed.online.lync.com| 100|1|5061|ساعة واحدة|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="املأ القيم من الجدول لسجل SRV.":::

1. حدد **"حفظ**".

1. أضف سجل SRV الآخر عن طريق اختيار القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>إضافة سجلي CNAME المطلوبين Skype for Business
  
1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **"المنتجات الخاصة بي**".

1. ضمن **"المجالات"**، حدد النقاط الثلاث الموجودة بجانب المجال الذي تريد التحقق منه، ثم حدد **"إدارة DNS**".

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

1. ضمن **السجلات**، حدد **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد ADD.":::

1. اختر **CNAME** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد CNAME من القائمة المنسدلة &quot;النوع&quot;.":::

1. في المربعات الفارغة للسجلات الجديدة، اكتب القيم أو انسخها والصقها من الصف الأول في الجدول التالي.

   |نوع|Host|يشير إلى|TTL|
   |---|---|---|---|
   |CNAME|المسبار|sipdir.online.lync.com.  <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
   |CNAME|lyncdiscover|webdir.online.lync.com.  <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="املأ القيم من الجدول لسجل CNAME.":::
  
1. حدد **"حفظ**".
  
1. أضف سجل CNAME الآخر عن طريق اختيار القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: إدارة الجهاز Intune و Mobile ل Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل بمجالك وإدارتها عن بعد. يحتاج إدارة الجهاز الجوال إلى سجلين CNAME حتى يتمكن المستخدمون من تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records-mobile-device-management"></a>إضافة سجلي CNAME المطلوبين إدارة الجهاز Mobile

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **"المنتجات الخاصة بي**".

1. ضمن **"المجالات"**، حدد النقاط الثلاث الموجودة بجانب المجال الذي تريد التحقق منه، ثم حدد **"إدارة DNS**".

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدلة.":::

1. ضمن **السجلات**، حدد **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد ADD.":::

1. اختر **CNAME** من القائمة المنسدلة.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد CNAME من القائمة المنسدلة &quot;النوع&quot;.":::

1. في المربعات الفارغة للسجلات الجديدة، اكتب القيم أو انسخها والصقها من الصف الأول في الجدول التالي.

   |نوع|Host|يشير إلى|TTL|
   |---|---|---|---|
   |CNAME|تسجيل المؤسسة|enterpriseregistration.windows.net.  <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|
   |CNAME|تسجيل المؤسسة|enterpriseenrollment-s.manage.microsoft.com.  <br/> **يجب أن تنتهي هذه القيمة بنقطة (.)**|ساعة واحدة|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="املأ القيم من الجدول لسجل CNAME.":::
  
1. حدد **"حفظ**".
  
1. أضف سجل CNAME الآخر عن طريق اختيار القيم من الصف الثاني من الجدول.

> [!NOTE]
> عادة ما تستغرق تغييرات DNS حوالي 15 دقيقة لتدخل حيز التنفيذ. ومع ذلك، قد يستغرق التحديث الذي أجريته عبر نظام DNS على الإنترنت وقتا أطول في بعض الأحيان. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فراجع [استكشاف المشكلات وإصلاحها بعد تغيير اسم المجال أو سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
