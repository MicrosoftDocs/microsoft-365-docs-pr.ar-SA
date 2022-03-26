---
title: الاتصال سجلات DNS في Namecheap Microsoft 365
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
ms.assetid: 54ae2002-b38e-43a1-82fa-3e49d78fda56
description: تعرف على كيفية التحقق من مجالك بإعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وخدمات أخرى في Namecheap ل Microsoft.
ms.openlocfilehash: 146b76ef95a725faa3457eaf1795b153133cef92
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567300"
---
# <a name="connect-your-dns-records-at-namecheap-to-microsoft-365"></a>الاتصال سجلات DNS في Namecheap Microsoft 365

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه. 
  
إذا كان Namecheap هو موفر استضافة DNS الذي تتبعه، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني Skype for Business Online وما إلى ذلك.
  
بعد إضافة هذه السجلات في Namecheap، سيتم إعداد مجالك للعمل مع خدمات Microsoft.
  
> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>إضافة سجل TXT للتحقق من صحة

قبل استخدام مجالك مع Microsoft، يجب أن نتأكد من أنك تملكه. تثبت قدرتك على تسجيل الدخول إلى حسابك لدى جهة تسجيل المجالات وإنشاء سجل DNS لشركة Microsoft أنك تملك المجال.
  
> [!NOTE]
> يتم استخدام هذا السجل فقط للتحقق من أنك تملك مجالك؛ ولا يؤثر على أي شيء آخر. يمكنك حذفه لاحقا، إذا أردت ذلك. 
  
1. للبدء، انتقل إلى صفحة المجالات في Namecheap باستخدام [هذا الارتباط](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). سيطلب منك تسجيل الدخول والمتابعة.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="سجل الدخول إلى Namecheap.":::

1. على الصفحة المنتقل لها، ضمن **حساب**، اختر **قائمة المجالات** من القائمة المنسدل. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="حدد قائمة المجالات من القائمة المنسدل.":::

1. في صفحة قائمة المجالات، حدد المجال الذي تريد تحريره، ثم حدد **إدارة**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="حدد إدارة.":::

1. حدد **DNS المتقدم**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="حدد DNS المتقدم.":::

1. في المقطع **سجلات المضيف** ، حدد **إضافة سجل جديد**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="حدد إضافة سجل جديد.":::

1. في **المنسدل النوع** ، حدد **سجل TXT**.
    
    > [!NOTE]
    > تظهر **المنسدل** النوع تلقائيا عند تحديد **إضافة سجل جديد**. 

     :::image type="content" source="../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png" alt-text="حدد سجل TXT.":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها.
    
    (اختر **قيمة TTL** من القائمة المنسدل.) 
    
    |**النوع**|**Host**|**القيمة**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |MS=ms *XXXXXXXX*  <br/>**ملاحظة:** هذا مثال. استخدم قيمة **الوجهة أو نقاط العنوان** المحددة هنا، من الجدول.  [كيف يمكنني العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md) |30 دقيقة  <br/> |

     :::image type="content" source="../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png" alt-text="نسخ القيم من الجدول ولصقها.":::

1. حدد عنصر **التحكم حفظ التغييرات** (علامة الاختيار). 

     :::image type="content" source="../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png" alt-text="حدد عنصر التحكم حفظ التغييرات.":::

1. انتظر بضع دقائق قبل المتابعة، بحيث يمكن تحديث السجل الذي أنشأته للتو عبر الإنترنت.
    
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
  
1. للبدء، انتقل إلى صفحة المجالات في Namecheap باستخدام [هذا الارتباط](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). سيطلب منك تسجيل الدخول والمتابعة.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="سجل الدخول إلى Namecheap.":::

1. على الصفحة المنتقل لها، ضمن **حساب**، اختر **قائمة المجالات** من القائمة المنسدل. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="اختر قائمة المجالات من القائمة المنسدل.":::

1. في صفحة **قائمة المجالات** ، حدد المجال الذي تريد تحريره، ثم حدد **إدارة**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="حدد إدارة.":::

1. حدد **DNS المتقدم**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="حدد DNS المتقدم.":::

1. في المقطع **إعدادات البريد** ، حدد **MX مخصص** من القائمة المنسدل إعادة **توجيه** البريد الإلكتروني. 
    
    (قد تحتاج إلى التمرير لأسفل.)

     :::image type="content" source="../../media/40199e2c-42cf-4c3f-9936-3cbe5d4e81a4.png" alt-text="حدد MX مخصص."::: 

1. حدد **إضافة سجل جديد**.

     :::image type="content" source="../../media/8d169b81-ba48-4d51-84ea-a08fa1616457.png" alt-text="إضافة سجل جديد.":::

1. في مربعات السجل الجديد، اكتب القيم من الجدول التالي أو انسخها واللصق بها.
    
    ( **مربع الأولوية** هو المربع غير الملقب إلى يمين **المربع قيمة** . اختر **القيمة TTL** من القائمة المنسدل.) 
    
    |**النوع**|**Host**|**القيمة**|**الأولوية**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |سجل MX  <br/> |@  <br/> |\<*domain-key*\>.mail.protection.outlook.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> **ملاحظة:** احصل على  *\<domain-key\>*  حسابك في Microsoft.  [كيف يمكنني العثور على هذا؟](../get-help-with-domains/information-for-dns-records.md)          |0  <br/> لمزيد من المعلومات حول الأولوية، راجع [ما هي أولوية MX؟](../setup/domains-faq.yml) <br/> |30 دقيقة  <br/> |

     :::image type="content" source="../../media/f3b76d62-5022-48c1-901b-8615a8571309.png" alt-text="نسخ القيم من الجدول ولصقها.":::

1. حدد عنصر **التحكم حفظ التغييرات** (علامة الاختيار). 

     :::image type="content" source="../../media/ef4e3112-36d2-47c8-a478-136a565dd71d.png" alt-text="حدد عنصر التحكم حفظ التغييرات.":::

1. إذا كان هناك أي سجلات MX أخرى، فاستخدم العملية التالية على خطوتين لإزالة كل منها:
    
    أولا، حدد **حذف** (سلة المهملات) للسجل الذي تريد إزالته. 

     :::image type="content" source="../../media/7a7a751f-29c2-495f-8f55-98ca37ce555a.png" alt-text="حدد حذف.":::

    ثانيا، حدد **نعم** لتأكيد الحذف. 

     :::image type="content" source="../../media/85ebc0c7-8787-43ee-9e7b-647375b3345c.png" alt-text="حدد نعم.":::

    قم بإزالة كل سجلات MX باستثناء تلك التي أضفتها سابقا في هذا الإجراء.
  
## <a name="add-the-cname-record-required-for-microsoft"></a>إضافة سجل CNAME المطلوب ل Microsoft

1. للبدء، انتقل إلى صفحة المجالات في Namecheap باستخدام [هذا الارتباط](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). سيطلب منك تسجيل الدخول والمتابعة.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="سجل الدخول إلى Namecheap.":::

1. على الصفحة المنتقل لها، ضمن **حساب**، اختر **قائمة المجالات** من القائمة المنسدل. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="حدد قائمة المجالات.":::

1. في صفحة **قائمة المجالات** ، حدد المجال الذي تريد تحريره، ثم حدد **إدارة**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="حدد إدارة.":::

1. حدد **DNS المتقدم**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="حدد DNS المتقدم.":::

1. في المقطع **سجلات المضيف** ، حدد **إضافة سجل جديد**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="حدد إضافة سجل جديد.":::

1. في **المنسدل النوع** ، حدد **سجل CNAME**.
    
    > [!NOTE]
    > تظهر **المنسدل** النوع تلقائيا عند تحديد **إضافة سجل جديد**. 

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="حدد سجل CNAME.":::

1. في المربعات الفارغة للسجل الجديد، حدد **CNAME** لنوع السجل، ثم اكتب القيم من الصف الأول في الجدول التالي أو انسخها واللصق بها.
    
    |**النوع**|**Host**|**القيمة**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover  <br/> |autodiscover.outlook.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |تلقائي  <br/> |

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="نسخ القيم من الجدول ولصقها.":::

1. حدد عنصر **التحكم حفظ التغييرات** (علامة الاختيار). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="حدد عنصر التحكم حفظ التغييرات.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>إضافة سجل TXT ل SPF للمساعدة في منع البريد الإلكتروني العشوائي

> [!IMPORTANT]
> لا يمكن أن يكون لديك أكثر من سجل TXT واحد ل SPF لمجال. إذا كان مجالك لديه أكثر من سجل SPF واحد، فسوف تحصل على أخطاء البريد الإلكتروني، بالإضافة إلى مشاكل التسليم وتصنيف البريد العشوائي. إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا ل Microsoft. بدلا من ذلك، أضف قيم Microsoft المطلوبة إلى السجل الحالي بحيث يكون لديك *سجل SPF*  واحد يتضمن مجموعتي القيم. 

1. للبدء، انتقل إلى صفحة المجالات في Namecheap باستخدام [هذا الارتباط](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). سيطلب منك تسجيل الدخول والمتابعة.
    
1. على الصفحة المنتقل لها، ضمن **حساب**، اختر **قائمة المجالات** من القائمة المنسدل. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="حدد قائمة المجالات.":::

1. في صفحة **قائمة المجالات** ، حدد المجال الذي تريد تحريره، ثم حدد **إدارة**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="حدد إدارة.":::

1. حدد **DNS المتقدم**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="حدد DNS المتقدم.":::

1. في المقطع **سجلات المضيف** ، حدد **إضافة سجل جديد**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="حدد إضافة سجل جديد.":::

1. في **المنسدل النوع** ، حدد **سجل TXT**.
    
    > [!NOTE]
    > تظهر **المنسدل** النوع تلقائيا عند تحديد **إضافة سجل جديد**. 

     :::image type="content" source="../../media/c5d1fddb-28b5-48ec-91c9-3e5d3955ac80.png" alt-text="حدد سجل TXT.":::

1. في مربعات السجل الجديد، اكتب القيم التالية من الجدول التالي أو انسخها واللصق بها.
    
    (اختر **قيمة TTL** من القائمة المنسدل.) 
    
    |**النوع**|**Host**|**القيمة**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **ملاحظة:** نوصي بنسخ هذا الإدخال ولصقه، بحيث تبقى كل التباعدات صحيحة. |30 دقيقة  <br/> |

     :::image type="content" source="../../media/ea0829f1-990b-424b-b26e-9859468318dd.png" alt-text="نسخ القيم من الجدول ولصقها.":::

1. حدد عنصر **التحكم حفظ التغييرات** (علامة الاختيار). 

     :::image type="content" source="../../media/f2846c36-ace3-43d8-be5d-a65e2c267619.png" alt-text="حدد عنصر التحكم حفظ التغييرات.":::

## <a name="advanced-option-skype-for-business"></a>الخيار المتقدم: Skype for Business

حدد هذا الخيار فقط إذا كانت مؤسستك تستخدم Skype for Business لخدمات الاتصال عبر الإنترنت مثل الدردشة والمؤتمرات عبر الهاتف ومكالمات الفيديو، بالإضافة إلى Microsoft Teams. Skype 4 سجلات: سجلان SRV للاتصالات بين المستخدمين، وسجلين CNAME من أجل تسجيل الدخول وربط المستخدمين بالخدمة.

### <a name="add-the-two-required-srv-records"></a>إضافة سجلي SRV المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Namecheap باستخدام [هذا الارتباط](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). سيطلب منك تسجيل الدخول.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="سجل الدخول إلى Namecheap.":::

1. على الصفحة المنتقل لها، ضمن **حساب**، اختر **قائمة المجالات** من القائمة المنسدل. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="اختر قائمة المجالات.":::

1. في صفحة **قائمة المجالات** ، حدد المجال الذي تريد تحريره، ثم حدد **إدارة**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="حدد إدارة.":::

1. حدد **DNS المتقدم**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="حدد DNS المتقدم.":::

1. في المقطع **سجلات المضيف** ، حدد **إضافة سجل جديد**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="حدد إضافة سجل جديد.":::

1. في **المنسدل النوع** ، حدد **سجل SRV**.
    
    > [!NOTE]
    > تظهر **المنسدل** النوع تلقائيا عند تحديد **إضافة سجل جديد**. 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="حدد نوع سجل SRV.":::

1. في المربعات الفارغة للسجلات الجديدة، اكتب القيم من الصف الأول في الجدول التالي أو انسخها واللصق بها.
    
    |**الخدمة**|**البروتوكول**|**الأولوية**|**الوزن**|**المنفذ**|**الهدف**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |100  <br/> |1  <br/> |443  <br/> |sipdir.online.lync.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |تلقائي  <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |100  <br/> |1  <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |تلقائي  <br/> |
       
     :::image type="content" source="../../media/ff9566ea-0096-4b7f-873c-027080a23b56.png" alt-text="نسخ القيم من الجدول ولصقها.":::

1. حدد عنصر **التحكم حفظ التغييرات** (علامة الاختيار). 

     :::image type="content" source="../../media/48a8dee4-c66d-449d-8759-9e9784c82b13.png" alt-text="حدد عنصر التحكم حفظ التغييرات.":::

1. أضف سجل SRV الآخر باختيار القيم من الصف الثاني من الجدول.
    
> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين 
  
1. في المقطع **سجلات المضيف** ، حدد **إضافة سجل جديد**.
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="حدد إضافة اسم جديد.":::

1. في **المنسدل النوع** ، حدد **CNAME**.
    
    > [!NOTE]
    > تظهر **المنسدل** النوع تلقائيا عند تحديد **إضافة سجل جديد**. 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="حدد CNAME.":::

1. في المربعات الفارغة للسجلات الجديدة، اكتب القيم من الصف الأول في الجدول أو انسخها واللصق بها.
    
    |**النوع**|**Host**|**القيمة**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |تلقائي  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |تلقائي  <br/> |

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="انسخ قيم CNAME ولصقها من الجدول.":::

1. حدد عنصر **التحكم حفظ التغييرات** (علامة الاختيار). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="حدد عنصر التحكم حفظ التغييرات.":::

1. أضف سجل CNAME الآخر باختيار القيم من الصف الثاني من الجدول.
    
> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>الخيار المتقدم: إدارة أجهزة المحمول و Intune Microsoft 365

تساعدك هذه الخدمة على تأمين الأجهزة المحمولة التي تتصل مجالك وإدارتها عن بعد. تحتاج إدارة أجهزة المحمول إلى سجلي CNAME حتى يمكن للمستخدمين تسجيل الأجهزة في الخدمة.

### <a name="add-the-two-required-cname-records"></a>إضافة سجلي CNAME المطلوبين

1. للبدء، انتقل إلى صفحة المجالات في Namecheap باستخدام [هذا الارتباط](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). سيطلب منك تسجيل الدخول.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="سجل الدخول إلى Namecheap.":::

1. على الصفحة المنتقل لها، ضمن **حساب**، اختر **قائمة المجالات** من القائمة المنسدل. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="حدد قائمة المجالات.":::

1. في صفحة **قائمة المجالات** ، حدد المجال الذي تريد تحريره، ثم حدد **إدارة**.
    
     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="حدد إدارة.":::

1. حدد **DNS المتقدم**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="حدد إدارة سجلات DNS من القائمة المنسدل.":::

1. في المقطع **سجلات المضيف** ، حدد **إضافة سجل جديد**.
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="حدد إضافة سجل جديد.":::

1. في **المنسدل النوع** ، حدد **سجل CNAME**.
    
    > [!NOTE]
    > تظهر **المنسدل** النوع تلقائيا عند تحديد **إضافة سجل جديد**. 
  
     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="حدد سجل CNAME.":::

1. في المربعات الفارغة للسجلات الجديدة، اكتب القيم من الصف الأول في الجدول أو انسخها واللصق بها.
    
    |**النوع**|**Host**|**القيمة**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |تلقائي  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **يجب أن تنتهي هذه القيمة بفترة (.)** <br/> |تلقائي  <br/> |
       
     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="نسخ القيم من الجدول ولصقها.":::

1. حدد عنصر **التحكم حفظ التغييرات** . 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="حدد عنصر التحكم حفظ التغييرات.":::

1. أضف سجل CNAME الآخر باختيار القيم من الصف الثاني من الجدول.
    
> [!NOTE]
> يستغرق عادة الأمر حوالي 15 دقيقة حتى يتم إدخال تغييرات DNS. ومع ذلك، قد يستغرق تحديث نظام DNS على الإنترنت وقتا أطول أحيانا. إذا كنت تواجه مشكلة في تدفق البريد أو مشاكل أخرى بعد إضافة سجلات DNS، فشاهد استكشاف الأخطاء وإصلاحها بعد تغيير اسم المجال أو [سجلات DNS](../get-help-with-domains/find-and-fix-issues.md). 


