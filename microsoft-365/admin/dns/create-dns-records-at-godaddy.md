---
title: الاتصال سجلات DNS في GoDaddy Microsoft 365
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
description: تعرف على كيفية التحقق من مجالك بإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في GoDaddy ل Microsoft.
ms.openlocfilehash: 728fd6cc34517213b338e3da07e6a275a1a727d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566064"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>الاتصال سجلات DNS في GoDaddy Microsoft 365

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه.

إذا كان GoDaddy هو موفر استضافة DNS لديك، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني Skype for Business عبر الإنترنت وما إلى ذلك.

## <a name="before-you-begin"></a>قبل البدء

لديك خياران لإعداد سجلات DNS لمجالك:

- [**استخدم المجال الاتصال**](#use-domain-connect-to-verify-and-set-up-your-domain) إذا لم تقم بإعداد مجالك مع موفر خدمة بريد إلكتروني آخر، فاستخدم الخطوات Domain الاتصال للتحقق من مجالك الجديد تلقائيا ثم إعداده لاستخدامه مع Microsoft 365.

   OR

- [**استخدام الخطوات اليدوية**](#create-dns-records-with-manual-setup) تحقق من مجالك باستخدام الخطوات اليدوية أدناه واختر السجلات التي تريد إضافتها إلى جهة تسجيل المجالات ومتى يجب إضافتها. يسمح لك هذا الأمر بإعداد سجلات MX (بريد) جديدة، على سبيل المثال، بما يلائمك.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>استخدام المجال الاتصال للتحقق من مجالك ثم إعداده

اتبع هذه الخطوات للتحقق من مجال GoDaddy الخاص بك بإعداده تلقائيا باستخدام Microsoft 365:

1. في مركز مسؤولي Microsoft 365، **حدد** >  الإعدادات <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**مجالات**</a>، وحدد المجال الذي تريد إعداده.

1. حدد النقاط الثلاث (المزيد من الإجراءات) > بدء **الإعداد**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. في كيف تريد توصيل مجالك؟ ، حدد **متابعة**.

1. في الصفحة إضافة سجلات DNS، حدد **إضافة سجلات DNS**.

1. في صفحة تسجيل الدخول إلى GoDaddy، سجل الدخول إلى حسابك، وحدد **تخويل**.

    هذا يكمل إعداد مجالك Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>إنشاء سجلات DNS باستخدام الإعداد اليدوي

بعد إضافة هذه السجلات في GoDaddy، سيتم إعداد مجالك للعمل مع خدمات Microsoft.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق من صحة

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.

> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من أنك تملك مجالك؛ ولا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **منتجاتي**.

1. ضمن **المجالات**، حدد النقاط الثلاث إلى بجانب المجال الذي تريد التحقق منه، ثم حدد **إدارة DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

1. ضمن **سجلات**، حدد **إضافة** (قد تحتاج إلى التمرير لأسفل).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد إضافة.":::

1. اختر **TXT** من القائمة المنسدل.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد TXT من القائمة المنسدل النوع.":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول أو انسخها واللصق بها.

   |**النوع** |**Host**|**قيمة TXT**|**TTL** |
   |:-----|:-----|:-----|:-----|
   |TXT |@|MS=ms *XXXXXXXX*<br>**ملاحظة**: هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [كيف يمكنني العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)|ساعة واحدة  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="قم بتعبئة القيم من الجدول لسجل TXT.":::

1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="حدد حفظ.":::

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

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX بحيث يتم إرسال البريد الإلكتروني لمجالك إلى Microsoft

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **منتجاتي**.

2. ضمن **المجالات**، حدد النقاط الثلاث إلى بجانب المجال الذي تريد التحقق منه، ثم حدد **إدارة DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

3. ضمن **سجلات**، حدد **إضافة**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد إضافة.":::

4. اختر **MX** من القائمة المنسدل.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد MX من القائمة المنسدل النوع.":::

5. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها.

    (اختر **قيمتي النوع** **و TTL** من القائمة المنسدل.)

    |**النوع**|**Host**|**يشير إلى**|**الأولوية**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX  <br/> |@  <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **ملاحظة:** احصل على  *\<domain-key\>*  حسابك في Microsoft.           [كيف يمكنني العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml) <br/> |ساعة واحدة  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="قم بتعبئة القيم من الجدول لسجل MX.":::

6. حدد **حفظ**.

### <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **منتجاتي**.

2. ضمن **المجالات**، حدد النقاط الثلاث إلى بجانب المجال الذي تريد التحقق منه، ثم حدد **إدارة DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

3. ضمن **سجلات**، حدد **إضافة**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد إضافة.":::

4. اختر **CNAME** من القائمة المنسدل.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد CNAME من القائمة المنسدل النوع.":::

5. إنشاء سجل CNAME.

    في مربعات السجل الجديد، اكتب القيم من الصف الأول في الجدول التالي أو انسخها واللصق بها.

    (اختر **قيمة TTL** من القائمة المنسدل.)

    |**النوع**|**Host**|**يشير إلى**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover <br/> |autodiscover.outlook.com  <br/> |ساعة واحدة  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="قم بتعبئة القيم من الجدول لسجل CNAME.":::

6. حدد **حفظ**.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك لديه أكثر من سجل SPF واحد، فسوف تحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل التسليم وتصنيف البريد العشوائي. إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك  *سجل SPF*  واحد يتضمن مجموعتي القيم.

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **منتجاتي**.

2. ضمن **المجالات**، حدد النقاط الثلاث إلى بجانب المجال الذي تريد التحقق منه، ثم حدد **إدارة DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

3. ضمن **سجلات**، حدد **إضافة**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد إضافة.":::

4. اختر **TXT** من القائمة المنسدل.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد TXT من القائمة المنسدل النوع.":::

5. في مربعات السجل الجديد، اكتب القيم التالية أو انسخها واللصق بها.

    (اختر **قيمة TTL** من القوائم المنسدل.)

    |**النوع**|**Host**|**قيمة TXT**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة. |ساعة واحدة  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="قم بتعبئة القيم من الجدول لسجل TXT.":::

6. حدد **حفظ**.

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. Skype 4 سجلات: سجلان SRV للاتصالات بين المستخدمين، وسجلين CNAME من أجل تسجيل الدخول وربط المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **منتجاتي**.

1. ضمن **المجالات**، حدد النقاط الثلاث إلى بجانب المجال الذي تريد التحقق منه، ثم حدد **إدارة DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

1. ضمن **سجلات**، حدد **إضافة**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد إضافة.":::

1. اختر **SRV** من القائمة المنسدل.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد SRV من القائمة المنسدل النوع.":::

1. إنشاء سجل SRV الأول.

    في مربعات السجل الجديد، اكتب القيم من الصف الأول في الجدول التالي أو انسخها واللصق بها.

    (اختر **قيمتي النوع** **و TTL** من القوائم المنسدل.)

    |**النوع**|**الخدمة**|**البروتوكول**| **الاسم** | **الهدف**|**الأولوية**|**الوزن**|**المنفذ**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV   <br/> |_sip  <br/> |_tls  <br/> |@  <br/> |sipdir.online.lync.com  <br/> |100 <br/> | 1  <br/> |443  <br/> |ساعة واحدة  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |_tcp  <br/> |@  <br/> | sipfed.online.lync.com  <br/> | 100  <br/> |1  <br/> |5061  <br/> |ساعة واحدة  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="قم بتعبئة القيم من الجدول لسجل SRV.":::

1. حدد **حفظ**.

1. أضف سجل SRV الآخر باختيار القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين
  
1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **منتجاتي**.

2. ضمن **المجالات**، حدد النقاط الثلاث إلى بجانب المجال الذي تريد التحقق منه، ثم حدد **إدارة DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

1. ضمن **سجلات**، حدد **إضافة**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد إضافة.":::

1. اختر **CNAME** من القائمة المنسدل.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد CNAME من القائمة المنسدل النوع.":::

1. في المربعات الفارغة للسجلات الجديدة، اكتب القيم من الصف الأول في الجدول التالي أو انسخها واللصق بها.

    |**النوع**|**Host**|**يشير إلى**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |ساعة واحدة  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |ساعة واحدة  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="قم بتعبئة القيم من الجدول لسجل CNAME.":::
  
1. حدد **حفظ**.
  
1. أضف سجل CNAME الآخر باختيار القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: إدارة أجهزة المحمول و Intune Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل مجالك وإدارتها عن بعد. تحتاج إدارة أجهزة المحمول إلى سجلين CNAME حتى يمكن للمستخدمين تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في GoDaddy باستخدام [هذا الارتباط](https://account.godaddy.com/products/?go_redirect=disabled).

   إذا تمت مطالبتك بتسجيل الدخول، فاستخدم بيانات اعتماد تسجيل الدخول، وحدد اسم تسجيل الدخول في الزاوية العلوية اليسرى، ثم حدد **منتجاتي**.

1. ضمن **المجالات**، حدد النقاط الثلاث إلى بجانب المجال الذي تريد التحقق منه، ثم حدد **إدارة DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="حدد إدارة DNS من القائمة المنسدل.":::

1. ضمن **سجلات**، حدد **إضافة**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="حدد إضافة.":::

1. اختر **CNAME** من القائمة المنسدل.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="حدد CNAME من القائمة المنسدل النوع.":::

1. في المربعات الفارغة للسجلات الجديدة، اكتب القيم من الصف الأول في الجدول التالي أو انسخها واللصق بها.

    |**النوع**|**Host**|**يشير إلى**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |ساعة واحدة  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |ساعة واحدة  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="قم بتعبئة القيم من الجدول لسجل CNAME.":::
  
1. حدد **حفظ**.
  
1. أضف سجل CNAME الآخر باختيار القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
