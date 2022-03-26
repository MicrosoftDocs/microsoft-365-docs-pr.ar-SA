---
title: الاتصال سجلات DNS في IONOS من 1&1 إلى Microsoft 365
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: تعرف على كيفية التحقق من مجالك إعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في 1&1 IONOS ل Microsoft.
ms.openlocfilehash: 54e18972fe2d5e2ccd8c3ab266b20241e67f68a9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567498"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>الاتصال سجلات DNS في IONOS من 1&1 إلى Microsoft 365

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه. 

إذا كان IONOS by 1&1 هو موفر استضافة DNS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

## <a name="before-you-begin"></a>قبل البدء

لديك خياران لإعداد سجلات DNS لمجالك:

- [**استخدم المجال الاتصال**](#use-domain-connect-to-verify-and-set-up-your-domain) إذا لم تقم بإعداد مجالك مع موفر خدمة بريد إلكتروني آخر، فاستخدم الخطوات Domain الاتصال للتحقق من مجالك الجديد تلقائيا ثم إعداده لاستخدامه مع Microsoft 365. 

    OR

- [**استخدام الخطوات اليدوية**](#create-dns-records-with-manual-setup) تحقق من مجالك باستخدام الخطوات اليدوية أدناه واختر السجلات التي تريد إضافتها إلى جهة تسجيل المجالات ومتى يجب إضافتها. يسمح لك هذا الأمر بإعداد سجلات MX (بريد) جديدة، على سبيل المثال، بما يلائمك. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>استخدام المجال الاتصال للتحقق من مجالك ثم إعداده

اتبع هذه الخطوات للتحقق تلقائيا من مجال IONOS الخاص بك&1 بواسطة Microsoft 365:

1. في مركز مسؤولي Microsoft 365، **حدد** >  الإعدادات <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**مجالات**</a>، وحدد المجال الذي تريد إعداده.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="حدد مجالك في Microsoft 365.":::

1. حدد النقاط الثلاث (المزيد من الإجراءات) > بدء **الإعداد**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. في كيف تريد توصيل مجالك؟ ، حدد **متابعة**.   

1. في الصفحة إضافة سجلات DNS، حدد **إضافة سجلات DNS**.

1. في صفحة تسجيل الدخول إلى IONOS&1، سجل الدخول إلى حسابك، **وحدد الاتصال****، والسماح**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="حدد الاتصال، ثم السماح.":::

    هذا يكمل إعداد مجالك Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>إنشاء سجلات DNS باستخدام الإعداد اليدوي

بعد إضافة هذه السجلات في IONOS&1، سيتم إعداد مجالك للعمل مع خدمات Microsoft.
  
> [!CAUTION]
> تجدر الإشارة إلى أن IONOS&1 لا يسمح للمجال بأن يكون له سجل MX وسجل CNAME من المستوى الأعلى. وهذا يحد من الطرق التي يمكنك من خلالها تكوين Exchange Online Microsoft. يوجد حل بديل، ولكننا نوصي باستخدامه فقط إذا كان لديك  بالفعل خبرة في إنشاء مجالات فرعية في IONOS بنسبة 1&1.
> إذا اخترت إدارة سجلات [](../setup/domains-faq.yml) DNS الخاصة بك في IONOS في 1&1 على الرغم من قيود الخدمة هذه، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني و Skype for Business Online وما إلى ذلك.
  
> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
  
### <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق من صحة

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.
  
> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من أنك تملك مجالك؛ ولا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك.
  
1. للبدء، انتقل إلى صفحة المجالات في IONOS ب 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). سيطلب منك تسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::
  
1. ضمن **إجراءات** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدل.":::

1. حدد **إضافة سجل**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد إضافة سجل.":::

1. حدد مقطع **TXT** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="حدد مقطع TXT.":::

1. في الصفحة إضافة سجل DNS، في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها.

    |**اسم المضيف** <br/> |**القيمة** <br/> | **TTL**
    |:-----|:-----|:-----|
    |(اترك هذا الحقل فارغا)  <br/> |MS=ms *XXXXXXXX*  <br/> ملاحظة: هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول. [كيف يمكنني العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)          | ساعة واحدة |

1. حدد **حفظ**.
  
    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="حدد حفظ.":::
  
    انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.

الآن وقد أضفت السجل إلى موقع جهة تسجيل المجالات، سوف تعود إلى Microsoft 365 وتطلب Microsoft 365 للبحث عن السجل. عندما تعثر Microsoft على سجل TXT الصحيح، يتم التحقق من مجالك.

للتحقق من السجل في Microsoft 365:
  
1. في مركز الإدارة، انتقل **إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**المجالات**</a>.

1. في صفحة المجالات، حدد المجال الذي تتحقق منه، ثم حدد **بدء الإعداد**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="حدد بدء الإعداد.":::

1. حدد **متابعة**.
  
1. في صفحة **التحقق من المجال** ، حدد **التحقق**.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).
  
### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX بحيث يتم إرسال البريد الإلكتروني لمجالك إلى Microsoft
  
> [!NOTE]
> إذا قمت بالتسجيل باستخدام 1und1.de، [فسجل الدخول هنا](https://go.microsoft.com/fwlink/?linkid=859152). 

1. للبدء، انتقل إلى صفحة المجالات في IONOS ب 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). سيطلب منك تسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::
  
1. ضمن **إجراءات** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدل.":::

1. حدد **إضافة سجل**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد إضافة سجل.":::

1. حدد مقطع **MX** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="حدد مقطع MX.":::
  
1. في الصفحة إضافة سجل DNS، في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها.

    | **اسم المضيف**| **يشير إلى** |**الأولوية**| **TTL** |
    |:-----|:-----|:-----| :-----|
    |  @  | *\<domain-key\>*  .mail.protection.outlook.com  <br/>  ملاحظة: احصل على حسابك \<domain-key\> في Microsoft. [كيف يمكنني العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml) | ساعة واحدة |
  
1. حدد **حفظ**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="حدد حفظ.":::

1. إذا كانت هناك أي سجلات MX مدرجة بالفعل، فاحذف كل سجل منها عن طريق تحديد  سلة المهملات حذف السجلات في **الصفحة إضافة** سجل.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="حدد حذف سجل.":::

### <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

> [!NOTE]
> إذا قمت بالتسجيل باستخدام 1und1.de، [فسجل الدخول هنا](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. للبدء، انتقل إلى صفحة المجالات في IONOS ب 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). سيطلب منك تسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::
  
1. ضمن **إجراءات** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدل.":::

    الآن ستنشئ اثنين من مجالات العمل الفرعية وتعين قيمة **الاسم المستعار** لكل منهما.<br/>(هذا مطلوب لأن 1&IONOS يدعم سجل CNAME واحد فقط من المستوى الأعلى، ولكن Microsoft تتطلب سجلات CNAME متعددة.)<br/>أولا، ستنشئ المعرف الفرعي Autodiscover.

1. حدد **المناطق الفرعية**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="حدد فرعي.":::
  
1. حدد **إضافة منطقة فرعية**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="حدد إضافة المزيد من المناطق الفرعية.":::
  
1. في المربع **إضافة مجال** فرعي للمربع الفرعي الجديد، اكتب القيمة إضافة **مجال** فرعي فقط من الجدول التالي أو قم بنسخها ولصقها. (تضيف القيمة **الاسم المستعار** في خطوة لاحقة.)

    |**إضافة منطقة فرعية**| **الاسم المستعار** |
    |:-----|:-----|
    |autodiscover  <br/> | autodiscover.outlook.com |

1. ضمن **إجراءات** **للميدان الفرعي autodiscover** الذي أنشأته للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدل. <br/>

1. حدد **إضافة سجل**، ثم حدد المقطع **CNAME** .

1. في المربع **الاسم المستعار:** اكتب القيمة **الاسم** المستعار فقط من الجدول التالي أو انسخها واللصق بها. <br/>

    |**إضافة منطقة فرعية**| **الاسم المستعار** |
    |:-----|:-----|
    |autodiscover  <br/> | autodiscover.outlook.com |
  
1. حدد **حفظ**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك لديه أكثر من سجل SPF واحد، فسوف تحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل التسليم وتصنيف البريد العشوائي. إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك  *سجل SPF*  واحد يتضمن مجموعتي القيم. هل تحتاج إلى أمثلة؟ اطلع على [سجلات نظام أسماء المجالات الخارجية هذه ل Microsoft](../../enterprise/external-domain-name-system-records.md). للتحقق من صحة سجل SPF، يمكنك استخدام إحدى أدوات التحقق من صحة [SPF هذه](../setup/domains-faq.yml). 
  
> [!NOTE]
> إذا قمت بالتسجيل باستخدام 1und1.de، [فسجل الدخول هنا](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. للبدء، انتقل إلى صفحة المجالات في IONOS ب 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). سيطلب منك تسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::
  
1. ضمن **إجراءات** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدل.":::

1. حدد **إضافة سجل**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد إضافة سجل.":::

1. حدد المقطع **SPF (TXT** ).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="حدد المقطع SPF (TXT).":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها. <br/>

    |**النوع**|**اسم المضيف**|**القيمة**| **TTL** |
    |:-----|:-----|:-----|:-----|
    |SPF (TXT)  <br/> |(اترك هذا الحقل فارغا.)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة. | ساعة واحدة |
  
1. حدد **حفظ**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="حدد حفظ.":::

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. Skype 4 سجلات: سجلان SRV للاتصالات بين المستخدمين، وسجلين CNAME من أجل تسجيل الدخول وربط المستخدمين بالخدمة.

### <a name="add-two-additional-cname-records"></a>إضافة سجلي CNAME إضافيين
  
1. للبدء، انتقل إلى صفحة المجالات في IONOS ب 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). سيطلب منك تسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::
  
1. ضمن **إجراءات** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدل.":::

    الآن ستنشئ اثنين من مجالات العمل الفرعية وتعين قيمة **الاسم المستعار** لكل منهما.<br/>(هذا مطلوب لأن 1&IONOS يدعم سجل CNAME واحد فقط من المستوى الأعلى، ولكن Microsoft تتطلب سجلات CNAME متعددة.)<br/>أولا، ستنشئ lyncdiscover الفرعي.

1. حدد **المناطق الفرعية**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="حدد فرعي.":::
  
1. حدد **إضافة منطقة فرعية**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="حدد إضافة المزيد من المناطق الفرعية.":::

1. في المربع **إضافة مجال** فرعي للمربع الفرعي الجديد، اكتب القيمة إضافة **مجال** فرعي فقط من الجدول التالي أو قم بنسخها ولصقها. (تضيف القيمة **الاسم المستعار** في خطوة لاحقة.)<br/> 

    |**إضافة منطقة فرعية**|**الاسم المستعار**|
    |:-----|:-----|
    |lyncdiscover   |webdir.online.lync.com  |

1. ضمن **إجراءات** لميدان **lyncdiscover** الفرعي الذي أنشأته للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدل. <br/>

1. حدد **إضافة سجل**، ثم حدد المقطع **CNAME** .

1. في المربع **الاسم المستعار:** اكتب القيمة **الاسم** المستعار فقط من الجدول التالي أو انسخها واللصق بها. <br/>

    |**إنشاء منطقة فرعية**|**الاسم المستعار**|
    |:-----|:-----|
    |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |

1. إنشاء موقع فرعي آخر (SIP): <br/>حدد **إضافة منطقة فرعية**.

1. في المربع **إضافة مجال** فرعي للمربع الفرعي الجديد، اكتب القيمة إضافة **مجال** فرعي فقط من الجدول التالي أو قم بنسخها ولصقها. (تضيف القيمة **الاسم المستعار** في خطوة لاحقة.) <br/>

    |**إضافة منطقة فرعية**|**الاسم المستعار**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. ضمن **إجراءات** للميدان الفرعي الذي أنشأته للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدل. <br/>

1. حدد **إضافة سجل**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد إضافة سجل.":::

1. حدد المقطع **CNAME** .

1. في المربع **الاسم المستعار:** اكتب القيمة **الاسم** المستعار فقط من الجدول التالي أو انسخها واللصق بها. 

    |**إنشاء منطقة فرعية**|**الاسم المستعار**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. حدد خانة **الاختيار ل إخلاء** المسؤولية أنا على علم، ثم حدد **حفظ**.

## <a name="add-the-two-srv-records-required-for-microsoft"></a>إضافة سجلي SRV المطلوبين ل Microsoft
  
> [!NOTE]
> إذا قمت بالتسجيل باستخدام 1und1.de، [فسجل الدخول هنا](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. للبدء، انتقل إلى صفحة المجالات في IONOS ب 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). سيطلب منك تسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::
  
1. ضمن **إجراءات** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدل.":::

1. حدد **إضافة سجل**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد إضافة سجل.":::

1. حدد مقطع **SRV** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="حدد مقطع SRV.":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها. <br/>

    |**النوع**|**الخدمة**|**البروتوكول**|**اسم المضيف**|**يشير إلى**|**الأولوية**|**الوزن**|**المنفذ**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV  <br/> |_sip  <br/> |tls  <br/> |(اترك هذا الحقل فارغا.)  <br/> |sipdir.online.lync.com  <br/> |100  <br/> |1  <br/> |443  <br/> |ساعة واحدة  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |tcp  <br/> |(اترك هذا الحقل فارغا.)  <br/> |sipfed.online.lync.com  <br/> |100  <br/> |1  <br/> |5061  <br/> |ساعة واحدة <br/> |  
  
1. حدد **حفظ**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="حدد حفظ.":::

1. إضافة سجل SRV الآخر.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: إدارة أجهزة المحمول و Intune Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل مجالك وإدارتها عن بعد. تحتاج إدارة أجهزة المحمول إلى سجلين CNAME حتى يمكن للمستخدمين تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

> [!IMPORTANT]
> اتبع إجراء المجالات الفرعية الذي استخدمته لسجلات CNAME الأخرى، وزود القيم من الجدول التالي. 
  
1. للبدء، انتقل إلى صفحة المجالات في IONOS ب 1&1 باستخدام [هذا الارتباط](https://my.1and1.com/). سيطلب منك تسجيل الدخول.

1. حدد **القائمة**، ثم حدد **المجالات وSSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="حدد المجالات وSSL.":::
  
1. ضمن **إجراءات** للمجال الذي تريد تحديثه، حدد عنصر تحكم الترس، ثم حدد **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="حدد DNS من القائمة المنسدل.":::

    الآن ستنشئ اثنين من مجالات العمل الفرعية وتعين قيمة **الاسم المستعار** لكل منهما.<br/>(هذا مطلوب لأن 1&IONOS يدعم سجل CNAME واحد فقط من المستوى الأعلى، ولكن Microsoft تتطلب سجلات CNAME متعددة.)<br/>أولا، ستنشئ lyncdiscover الفرعي.

1. حدد **المناطق الفرعية**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="حدد فرعي.":::
  
1. حدد **إضافة منطقة فرعية**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="حدد إضافة المزيد من المناطق الفرعية.":::

1. في المربع **إضافة مجال** فرعي للمربع الفرعي الجديد، اكتب القيمة إضافة **مجال** فرعي فقط من الجدول التالي أو قم بنسخها ولصقها. (تضيف القيمة **الاسم المستعار** في خطوة لاحقة.)<br/> 

    |**إضافة منطقة فرعية**|**الاسم المستعار**|
    |:-----|:-----|
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |

1. ضمن **إجراءات** **للميدان الفرعي enterpriseregistration** الذي أنشأته للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدل. <br/>

1. حدد **إضافة سجل**، ثم حدد المقطع **CNAME** .

1. في المربع **الاسم المستعار:** اكتب القيمة **الاسم** المستعار فقط من الجدول التالي أو انسخها واللصق بها. <br/>

    |**إضافة منطقة فرعية**|**الاسم المستعار**|
    |:-----|:-----|
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |

1. إنشاء موقع فرعي آخر: <br/>حدد **إضافة منطقة فرعية**.

1. في المربع **إضافة مجال** فرعي للمربع الفرعي الجديد، اكتب القيمة إضافة **مجال** فرعي فقط من الجدول التالي أو قم بنسخها ولصقها. (تضيف القيمة **الاسم المستعار** في خطوة لاحقة.) <br/>

    |**إضافة منطقة فرعية**|**الاسم المستعار**|
    |:-----|:-----|
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

1. ضمن **إجراءات** **للميدان الفرعي enterpriseenrollment** الذي أنشأته للتو، حدد عنصر تحكم الترس، ثم حدد **DNS** من القائمة المنسدل. <br/>

1. حدد **إضافة سجل**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="حدد إضافة سجل.":::

1. حدد المقطع **CNAME** .

1. في المربع **الاسم المستعار:** اكتب القيمة **الاسم** المستعار فقط من الجدول التالي أو انسخها واللصق بها. 

    |**إنشاء منطقة فرعية**|**الاسم المستعار**|
    |:-----|:-----|
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

1. حدد خانة **الاختيار ل إخلاء** المسؤولية أنا على علم، ثم حدد **حفظ**.