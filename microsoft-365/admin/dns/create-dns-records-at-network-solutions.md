---
title: الاتصال سجلات DNS في Network Solutions Microsoft 365
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
ms.assetid: 1dc55f9f-5309-450f-acc3-b2b4119c8be3
description: تعرف على كيفية التحقق من مجالك بإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في Network Solutions ل Microsoft.
ms.openlocfilehash: a15b6ec2f06b08a32c0cf03bbc030731b91ea925
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63571013"
---
# <a name="connect-your-dns-records-at-network-solutions-to-microsoft-365"></a>الاتصال سجلات DNS في Network Solutions Microsoft 365

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه. 
  
إذا كانت Network Solutions هي موفر استضافة DNS الذي تتبعه، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.

بعد إضافة هذه السجلات في Network Solutions، سيتم إعداد مجالك للعمل مع خدمات Microsoft.
  
> [!NOTE]
>  يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق من صحة

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.
  
> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من أنك تملك مجالك؛ ولا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك. 
  
1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). سيطلب منك تسجيل الدخول.
  
1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. حدد خانة الاختيار إلى بجانب المجال الذي تريد تعديله.
  
1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::
  
1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.
  
1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **TXT** من القائمة المنسدل.
  
1. في مربعات السجل الجديد، اكتب القيم في الجدول التالي أو انسخها واللصق بها.
    
    | يشير إلى | قيمة TXT | TTL |
    |:-----|:-----|:-----|
    |@  <br/> (سيغير النظام هذه القيمة إلى **@ (بلا)** عند حفظ السجل.)  |MS=ms *XXXXXXXX*  <br/> **ملاحظة:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول.  [كيف يمكنني العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md) |3600  <br/>    | 

1. حدد **إضافة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="حدد إضافة.":::

    > [!NOTE]
    > حدد **طريقة العرض الكلاسيكية** في الزاوية العلوية اليسرى لعرض سجل TXT الذي أنشأته.   
  
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
  
1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). سيطلب منك تسجيل الدخول.
  
1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. حدد خانة الاختيار إلى بجانب المجال الذي تريد تعديله.
  
1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::
  
1. قم بالتمرير للأسفل لتحديد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **MX** من القائمة المنسدل.
  


1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها.
    
    | يشير إلى | خادم البريد | الأولوية | TTL |
    |:-----|:-----|:-----|:-----|
    | @ | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)** <br/> **ملاحظة:** احصل على  *\<domain-key\>*  حسابك في Microsoft. [كيف يمكنني العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md) | 0  <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml) | ساعة واحدة  |  
  
1. حدد **إضافة**.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-MX-add.png" alt-text="حدد إضافة.":::

    > [!NOTE]
    > حدد **طريقة العرض الكلاسيكية** في الزاوية العلوية اليسرى لعرض سجل TXT الذي أنشأته.  

1. إذا كان هناك أي سجلات MX أخرى، فاحذفها كلها عن طريق تحديد أداة التحرير، ثم **حذف** لكل سجل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-edit.png" alt-text="حدد أداة التحرير.":::
  
## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). سيطلب منك تسجيل الدخول.
  
1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. حدد خانة الاختيار إلى بجانب المجال الذي تريد تعديله.
  
1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::
  
1. حدد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدل.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="حدد نوع CNAME من القائمة المنسدل.":::
 
1. في مربعات سجل CNAME، اكتب القيم من الجدول التالي أو انسخها واللصق بها.
    
    | يشير إلى | اسم المضيف | الاسم المستعار إلى | TTL |
    |:-----|:-----|:-----|:-----|
    |مضيف آخر| autodiscover  | autodiscover.outlook.com **لا يمكن أن تنتهي هذه القيمة بفترة (.)** <br/> ساعة واحدة  |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها واللصق فيها من الجدول في النافذة.":::
  
1. حدد **إضافة**.

    > [!NOTE]
    > حدد **طريقة العرض الكلاسيكية** في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.  
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك لديه أكثر من سجل SPF واحد، فسوف تحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل التسليم وتصنيف البريد العشوائي. إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك  *سجل SPF*  واحد يتضمن مجموعتي القيم. 
  
1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). سيطلب منك تسجيل الدخول.
  
1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. حدد خانة الاختيار إلى بجانب المجال الذي تريد تعديله.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. حدد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **TXT** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-TXT.png" alt-text="حدد TXT من القائمة المنسدل النوع.":::

1. في مربعات السجل الجديد، اكتب القيم التالية أو انسخها واللصق بها.
    
    | يشير إلى | قيمة TXT | TTL
    |:-----|:-----|:-----|
    |@  <br/> (سيغير النظام هذه القيمة إلى **@ (بلا)** عند حفظ السجل.)  |v=spf1 include:spf.protection.outlook.com -all  <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة. | ساعة واحدة  |
       
1. حدد **إضافة**.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="حدد إضافة.":::

    > [!NOTE]
    > حدد **طريقة العرض الكلاسيكية** في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.  
  
## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. Skype 4 سجلات: سجلان SRV للاتصالات بين المستخدمين، وسجلين CNAME من أجل تسجيل الدخول وربط المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). سيطلب منك تسجيل الدخول.
  
1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. حدد خانة الاختيار إلى بجانب المجال الذي تريد تعديله.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. حدد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **SRV** من القائمة المنسدل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv.png" alt-text="حدد SRV من القائمة المنسدل النوع.":::

1. في مربعات السجلين الجديدين، اكتب القيم من الجدول التالي أو انسخها واللصق بها.

    (اختر **قيم الخدمة** **والبروتوكول** من القوائم المنسدل.) 
    
    | النوع | الخدمة | البروتوكول | الوزن | المنفذ | الهدف | الأولوية | TTL |
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    | SRV |_sip  |TLS  |100  |443  |sipdir.online.lync.com  <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)** | 1  | ساعة واحدة  |
    | SRV |_sipfederationtls  |TCP  |100  |5061  |sipfed.online.lync.com  <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)** |1  | ساعة واحدة  |
  
1. حدد **إضافة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv-add.png" alt-text="حدد إضافة.":::

    > [!NOTE]
    > حدد **طريقة العرض الكلاسيكية** في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.  

1. أضف سجل SRV الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). سيطلب منك تسجيل الدخول.
  
1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. حدد خانة الاختيار إلى بجانب المجال الذي تريد تعديله.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. حدد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ إضافة سجل**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::

1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدل.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="حدد نوع CNAME من القائمة المنسدل.":::
 
1. في مربعات سجل CNAME، اكتب القيم من الجدول التالي أو انسخها واللصق بها.

    | النوع | يشير إلى | اسم المضيف | الاسم المستعار إلى | TTL |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | مضيف آخر | sip  <br/> |sipdir.online.lync.com  <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)** |ساعة واحدة |
    | CNAME| مضيف آخر | lyncdiscover  <br/> |webdir.online.lync.com  <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)** | ساعة واحدة |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها واللصق فيها من الجدول في النافذة.":::

1. حدد **إضافة**.

    > [!NOTE]
    > حدد **طريقة العرض الكلاسيكية** في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.  

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: إدارة أجهزة المحمول و Intune Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل مجالك وإدارتها عن بعد. تحتاج إدارة أجهزة المحمول إلى سجلين CNAME حتى يمكن للمستخدمين تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Network Solutions باستخدام [هذا الارتباط](https://www.networksolutions.com/manage-it). سيطلب منك تسجيل الدخول.
  
1. في الصفحة المنتقل عليها، حدد **أسماء المجالات**.

1. حدد خانة الاختيار إلى بجانب المجال الذي تريد تعديله.

1. ضمن **إجراءات**، حدد النقاط الثلاث، ثم حدد **إدارة** في القائمة المنسدل.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="حدد إدارة من القائمة المنسدل.":::

1. حدد **أدوات متقدمة**، وب **المجاورة لسجلات DNS المتقدمة**، حدد **إدارة**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="إلى بجانب سجلات DNS المتقدمة، حدد إدارة.":::

    قد تحتاج إلى تحديد **متابعة** للوصول إلى الصفحة إدارة سجلات DNS المتقدمة.

1. في الصفحة إدارة سجلات DNS المتقدمة، حدد **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="حدد +ADD RECORD.":::
  
1. ضمن **النوع**، حدد **CNAME** من القائمة المنسدل.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="حدد نوع CNAME من القائمة المنسدل.":::
 
1. في مربعات سجل CNAME، اكتب القيم من الجدول التالي أو انسخها واللصق بها.

    | النوع | يشير إلى | اسم المضيف | الاسم المستعار إلى | TTL |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | مضيف آخر | enterpriseregistration |enterpriseregistration.windows.net  <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)** | ساعة واحدة |
    | CNAME | مضيف آخر |enterpriseenrollment |enterpriseenrollment-s.manage.microsoft.com  <br/> **لا يمكن أن تنتهي هذه القيمة بفترة (.)** | ساعة واحدة |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="اكتب قيم CNAME أو انسخها واللصق فيها من الجدول في النافذة.":::

1. حدد **إضافة**.

    > [!NOTE]
    > حدد **طريقة العرض الكلاسيكية** في الزاوية العلوية اليسرى لعرض السجل الذي أنشأته.  

1. أضف سجل CNAME الآخر عن طريق نسخ القيم من الصف الثاني من الجدول.

> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md).

