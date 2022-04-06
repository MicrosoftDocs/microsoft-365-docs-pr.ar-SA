---
title: سجلات نظام أسماء المجالات الخارجية Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/10/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: قائمة مرجعية لسجلات نظام أسماء المجالات الخارجية لاستخدامها عند التخطيط لتوزيع Office 365.
ms.openlocfilehash: d2c73094da0547fbc02a4520d4361941b829619c
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651334"
---
# <a name="external-domain-name-system-records-for-office-365"></a>سجلات نظام أسماء المجالات الخارجية Office 365

![المجال.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**هل تريد الاطلاع على قائمة مخصصة بسجلات DNS لمؤسستك Office 365؟** يمكنك [العثور على المعلومات التي تحتاجها لإنشاء سجلات DNS Office 365](../admin/get-help-with-domains/information-for-dns-records.md) لمجالك في Office 365.

**هل تحتاج إلى مساعدة خطوة بخطوة لإضافة هذه السجلات في مضيف DNS لمجالك، مثل GoDaddy أو eNom؟** [ابحث عن ارتباطات إلى إرشادات مفصلة خطوة بخطوة للعديد من مضيفي DNS الشائعين](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**هل تريد الثبات لاستخدام القائمة المرجعية للتوزيع المخصص الخاص بك؟** يجب استخدام القائمة أدناه كمرجع لنشر Office 365 المخصص. ستحتاج إلى تحديد السجلات التي تنطبق على مؤسستك وتعبئة القيم المناسبة.

**ارجع إلى** [تخطيط الشبكة وضبط الأداء Office 365](./network-planning-and-performance.md).

غالبا ما تكون سجلات SPF وMX هي الأصعب في معرفة ذلك. لقد قمنا بتحديث إرشادات سجلات SPF في نهاية هذه المقالة. الشيء المهم الذي يجب تذكره هو أنه _يمكنك الحصول على سجل SPF واحد فقط لمجالك_. يمكنك الحصول على سجلات MX متعددة؛ ومع ذلك، يمكن أن يسبب ذلك مشاكل لتسليم البريد. يؤدي وجود سجل MX واحد يوجه البريد الإلكتروني إلى نظام بريد واحد إلى إزالة العديد من المشاكل المحتملة.
  
يتم تنظيم الأقسام أدناه حسب الخدمة في Office 365. للاطلاع على قائمة مخصصة بسجلات DNS Office 365 لمجالك، سجل الدخول إلى Office 365 [وجمع المعلومات التي تحتاجها لإنشاء سجلات DNS Office 365](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>سجلات DNS الخارجية المطلوبة Office 365 (الخدمات الأساسية)
<a name="BKMK_ReqdCore"> </a>

يلزم وجود سجل TXT لإثبات ملكيتك للمجال وأنه مطلوب لجميع العملاء.

سجل CNAME مطلوب فقط للعملاء الذين يستخدمون [Office 365 المشغلة بواسطة 21Vianet](/microsoft-365/admin/services-in-china/services-in-china). وهو يضمن أن Office 365 يمكنها توجيه محطات العمل للمصادقة مع النظام الأساسي للهوية المناسب. 


  
|**سجل DNS** <br/> |**الغرض** <br/> |**القيمة المراد استخدامها** <br/> |**ينطبق على**|
|----------|-----------|------------|------------|
|**النص** <br/> **(التحقق من المجال)** <br/> |يستخدمه Office 365 للتحقق فقط من ملكيتك لمجالك. لا يؤثر على أي شيء آخر.  <br/> |**المضيف:** @ (أو لبعض موفري استضافة DNS، اسم مجالك)  <br/> **قيمة TXT:** _سلسلة نصية توفرها_ Office 365  <br/> يوفر **معالج إعداد المجال** Office 365 القيم التي تستخدمها لإنشاء هذا السجل.  <br/> |جميع العملاء|
|**CNAME** <br/> **(مجموعة)** <br/> |يستخدمه Office 365 لتوجيه المصادقة إلى النظام الأساسي الصحيح للهوية. [معلومات إضافية](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **لاحظ** أن CNAME هذا ينطبق فقط على Office 365 المشغلة بواسطة 21Vianet. إذا لم يتم تشغيل Office 365 من قبل 21Vianet، فسيحصل المستخدمون على مجالك المخصص على خطأ "*المجال المخصص* غير موجود في نظامنا" ولن يتمكنوا من تنشيط ترخيص Office 365 الخاص بهم. [معلومات إضافية](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**الاسم المستعار:** msoid  <br/> **الهدف:** clientconfig.partner.microsoftonline-p.net.cn  <br/> | عملاء 21Vianet فقط|



## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>سجلات DNS الخارجية المطلوبة للبريد الإلكتروني في Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

يتطلب البريد الإلكتروني في Office 365 عدة سجلات مختلفة. السجلات الأساسية الثلاثة التي يجب على جميع العملاء استخدامها هي سجلات الكشف التلقائي وMX وSPF.
  
- يسمح **سجل الكشف التلقائي** لأجهزة الكمبيوتر العميلة بالبحث تلقائيا عن Exchange وتكوين العميل بشكل صحيح.

- **يخبر سجل MX** أنظمة البريد الأخرى بمكان إرسال البريد الإلكتروني لمجالك. **ملاحظه:** عند تغيير بريدك الإلكتروني إلى Office 365، من خلال تحديث سجل MX لمجالك، ستبدأ جميع رسائل البريد الإلكتروني المرسلة إلى هذا المجال في Office 365.  
هل تريد فقط تبديل بعض عناوين البريد الإلكتروني إلى Office 365؟ يمكنك [تجربة Office 365 مع بعض عناوين البريد الإلكتروني على مجالك المخصص](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- يتم استخدام **سجل TXT ل SPF** من قبل أنظمة البريد الإلكتروني للمستلمين للتحقق من أن الخادم الذي يرسل بريدك الإلكتروني هو الذي توافق عليه. يساعد ذلك على منع حدوث مشاكل مثل تزييف هوية البريد الإلكتروني والتصيد الاحتيالي. راجع [سجلات DNS الخارجية المطلوبة ل SPF](external-domain-name-system-records.md#BKMK_SPFrecords) في هذه المقالة لمساعدتك على فهم ما يجب تضمينه في السجل.

سيحتاج عملاء البريد الإلكتروني الذين يستخدمون Exchange Federation أيضا إلى سجل CNAME وTXT الإضافي المدرج في أسفل الجدول.
  
|**سجل DNS** <br/> |**الغرض** <br/> |**القيمة المراد استخدامها** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Exchange Online)** <br/> |يساعد Outlook العملاء على الاتصال بسهولة بخدمة Exchange Online باستخدام خدمة الكشف التلقائي. يبحث الاكتشاف التلقائي تلقائيا عن مضيف Exchange Server الصحيح وتكوين Outlook للمستخدمين.  <br/> |**الاسم المستعار:** Autodiscover  <br/> **الهدف:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |إرسال بريد وارد لمجالك إلى خدمة Exchange Online في Office 365.  <br/> **ملاحظه:** بمجرد تدفق البريد الإلكتروني إلى Exchange Online، يجب إزالة سجلات MX التي تشير إلى النظام القديم.   |**المجال:** على سبيل المثال، contoso.com  <br/> **خادم البريد الإلكتروني الهدف:**\<MX token\>. mail.protection.outlook.com  <br/> **قيمة وقت البقاء (TTL):** 3600 <br/> **التفضيل/الأولوية:** أقل من أي سجلات MX أخرى (وهذا يضمن تسليم البريد إلى Exchange Online) - على سبيل المثال 1 أو "منخفض"  <br/>  ابحث عن طريق \<MX token\> اتباع الخطوات التالية:  <br/>  سجل الدخول إلى Office 365، وانتقل إلى Office 365"admin \> Domains".  <br/>  في العمود "إجراء" لمجالك، اختر "إصلاح المشاكل".  <br/>  في قسم سجلات MX، اختر ما الذي يمكنني إصلاحه؟  <br/>  اتبع الإرشادات الموجودة في هذه الصفحة لتحديث سجل MX.  <br/> [ما هي أولوية MX؟](../admin/setup/domains-faq.yml) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |يساعد على منع الأشخاص الآخرين من استخدام مجالك لإرسال بريد عشوائي أو بريد إلكتروني ضار آخر. تعمل سجلات إطار عمل نهج المرسل (SPF) من خلال تحديد الخوادم المخولة بإرسال بريد إلكتروني من مجالك.  <br/> |[سجلات DNS الخارجية المطلوبة ل SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**النص** <br/> **(اتحاد Exchange)** <br/> |يستخدم Exchange الاتحاد للنشر المختلط.  <br/> |**سجل TXT 1:** على سبيل المثال، contoso.com ونص تجزئة إثبات المجال الذي تم إنشاؤه خصيصا (على سبيل المثال، Y96nu89138789315669824)  <br/> **سجل TXT 2:** على سبيل المثال، exchangedelegation.contoso.com ونص تجزئة إثبات المجال الذي تم إنشاؤه خصيصا (على سبيل المثال، Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(اتحاد Exchange)** <br/> |يساعد Outlook العملاء على الاتصال بسهولة بخدمة Exchange Online باستخدام خدمة الكشف التلقائي عندما تستخدم شركتك الاتحاد Exchange. يبحث الاكتشاف التلقائي تلقائيا عن مضيف Exchange Server الصحيح وتكوين Outlook للمستخدمين.  <br/> |**الاسم المستعار:** على سبيل المثال، Autodiscover.service.contoso.com  <br/> **الهدف:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>سجلات DNS الخارجية المطلوبة Skype for Business Online
<a name="BKMK_ReqdCore"> </a>

هناك خطوات محددة يجب اتخاذها عند استخدام [عناوين URL Office 365 ونطاقات عناوين IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) للتأكد من تكوين شبكتك بشكل صحيح.

> [!NOTE]
> تنطبق سجلات DNS هذه أيضا على Teams، خاصة في سيناريو Teams المختلط Skype for Business، حيث قد تنشأ بعض مشكلات الاتحاد.
  
|**سجل DNS** <br/> |**الغرض** <br/> |**القيمة المراد استخدامها** <br/> |
|----------|-----------|------------|
|**SRV** <br/> **(Skype for Business Online)** <br/> |السماح لمجالك Office 365 بمشاركة ميزات المراسلة الفورية (IM) مع العملاء الخارجيين من خلال تمكين اتحاد SIP. اقرأ المزيد حول [عناوين URL Office 365 ونطاقات عناوين IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**الخدمة:** sipfederationtls  <br/> **البروتوكول:** TCP  <br/> **الأولوية:** 100  <br/> **الوزن:** 1  <br/> **المنفذ:** 5061  <br/> **الهدف:** sipfed.online.lync.com  <br/> **ملاحظه:** إذا كان جدار الحماية أو الخادم الوكيل يحظر عمليات بحث SRV على DNS خارجي، يجب إضافة هذا السجل إلى سجل DNS الداخلي.   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |يستخدمه Skype for Business لتنسيق تدفق المعلومات بين عملاء Lync.  <br/> |**الخدمة:** sip  <br/> **البروتوكول:** TLS  <br/> **الأولوية:** 100  <br/> **الوزن:** 1  <br/> **المنفذ:** 443  <br/> **الهدف:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |يستخدمه عميل Lync للمساعدة في العثور على خدمة Skype for Business Online وتسجيل الدخول.  <br/> |**الاسم المستعار:** sip  <br/> **الهدف:** sipdir.online.lync.com  <br/> لمزيد من المعلومات، راجع [Office 365 نطاقات عناوين URL وعناوين IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |يستخدمه عميل Lync للأجهزة المحمولة للمساعدة في العثور على خدمة Skype for Business Online وتسجيل الدخول.  <br/> |**الاسم المستعار:** lyncdiscover  <br/> **الهدف:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>سجلات DNS الخارجية المطلوبة Office 365 single Sign-On
<a name="BKMK_ReqdCore"> </a>

|**سجل DNS** <br/> |**الغرض** <br/> |**القيمة المراد استخدامها** <br/> |
|----------|-----------|------------|
|**المضيف (أ)** <br/> |يستخدم لتسجيل الدخول الأحادي (SSO). يوفر نقطة النهاية للمستخدمين المحليين (والمستخدمين المحليين، إذا أردت) الاتصال بوكلاء خادم الأمان المشترك خدمات الأمان المشترك لـ Active Directory (AD FS) أو IP الظاهري (VIP) المتوازن التحميل.  <br/> |**الهدف:** على سبيل المثال، sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>سجلات DNS الخارجية المطلوبة ل SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> تم تصميم SPF للمساعدة في منع الانتحال، ولكن هناك تقنيات تزييف هوية لا يمكن ل SPF الحماية منها. من أجل الحماية من هذه، بمجرد إعداد SPF، يجب عليك أيضا تكوين DKIM وDMARC Office 365. لبدء الاستخدام، راجع [استخدام DKIM للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك في Office 365](../security/office-365-security/use-dkim-to-validate-outbound-email.md). بعد ذلك، راجع [استخدام DMARC للتحقق من صحة البريد الإلكتروني في Office 365](../security/office-365-security/use-dmarc-to-validate-email.md).
  
سجلات SPF هي سجلات TXT التي تساعد على منع الأشخاص الآخرين من استخدام مجالك لإرسال بريد عشوائي أو بريد إلكتروني ضار آخر. تعمل سجلات إطار عمل نهج المرسل (SPF) من خلال تحديد الخوادم المخولة بإرسال بريد إلكتروني من مجالك.
  
يمكنك الحصول على سجل SPF واحد فقط (أي سجل TXT الذي يعرف SPF) لمجالك. يمكن أن يحتوي هذا السجل المفرد على بعض التضمينات المختلفة ولكن لا يمكن أن يكون إجمالي عمليات بحث DNS التي ينتج عنها أكثر من 10 (وهذا يساعد على منع هجمات رفض الخدمة). راجع الجدول والأمثلة الأخرى أدناه لمساعدتك على إنشاء قيم سجل SPF المناسبة للبيئة الخاصة بك أو تحديثها.
  
### <a name="structure-of-an-spf-record"></a>بنية سجل SPF

تحتوي جميع سجلات SPF على ثلاثة أجزاء: الإعلان عن أنه سجل SPF والمجالات وعناوين IP التي يجب أن ترسل البريد الإلكتروني وقاعدة إنفاذ. تحتاج إلى الثلاثة في سجل SPF صالح. فيما يلي مثال على سجل SPF شائع Office 365 عند استخدام البريد الإلكتروني Exchange Online فقط:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

يبحث نظام البريد الإلكتروني الذي يتلقى بريدا إلكترونيا من مجالك في سجل SPF، وإذا كان خادم البريد الإلكتروني الذي أرسل الرسالة خادما Office 365، يتم قبول الرسالة. إذا كان الخادم الذي أرسل الرسالة هو نظام البريد القديم أو نظام ضار على الإنترنت، على سبيل المثال، فقد يفشل فحص SPF ولن يتم تسليم الرسالة. تتحقق مثل هذه التعليمات لمنع رسائل الانتحال والتصيد الاحتيالي.
  
### <a name="choose-the-spf-record-structure-you-need"></a>اختر بنية سجل SPF التي تحتاجها

بالنسبة للسيناريوهات التي لا تستخدم فيها البريد الإلكتروني Exchange Online فقط Office 365 (على سبيل المثال، عند استخدام البريد الإلكتروني الذي ينشأ من SharePoint Online أيضا)، استخدم الجدول التالي لتحديد ما يجب تضمينه في قيمة السجل.
  
> [!NOTE]
> إذا كان لديك سيناريو معقد يتضمن، على سبيل المثال، خوادم البريد الإلكتروني الحافة لإدارة نسبة استخدام الشبكة عبر جدار الحماية الخاص بك، سيكون لديك سجل SPF أكثر تفصيلا لإعداده. تعرف على كيفية: [إعداد سجلات SPF في Office 365 للمساعدة في منع الانتحال](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). يمكنك أيضا معرفة المزيد حول كيفية عمل SPF مع Office 365 من خلال قراءة [كيفية استخدام Office 365 إطار نهج المرسل (SPF) للمساعدة في منع الانتحال](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md).
  
| عدد|إذا كنت تستخدم...  <br/> |الغرض  <br/> |إضافة هذه بما في ذلك  <br/> |
|:-----|:-----|:-----|:-----|
|1  <br/> |كافة أنظمة البريد الإلكتروني (مطلوبة)  <br/> |تبدأ كافة سجلات SPF بهذه القيمة  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (شائع)  <br/> |استخدم مع Exchange Online فقط  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |نظام البريد الإلكتروني التابع لجهة خارجية (أقل شيوعا)  <br/> ||تشمل:\<email system like mail.contoso.com\>  <br/> |
|4  <br/> |نظام البريد المحلي (أقل شيوعا)  <br/> |يستخدم إذا كنت تستخدم Exchange Online Protection أو Exchange Online بالإضافة إلى نظام بريد آخر  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> تشمل:\<mail.contoso.com\>  <br/> يجب أن تكون القيمة بين قوسين (\<\>) أنظمة بريد أخرى سترسل بريدا إلكترونيا لمجالك.  <br/> |
|5  <br/> |كافة أنظمة البريد الإلكتروني (مطلوبة)  <br/> ||-الكل  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>مثال: إضافة إلى سجل SPF موجود
<a name="bkmk_addtospf"> </a>

إذا كان لديك سجل SPF بالفعل، فستحتاج إلى إضافة قيم Office 365 أو تحديثها. على سبيل المثال، لنفترض أن سجل SPF الموجود الخاص بك contoso.com هو التالي:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

تقوم الآن بتحديث سجل SPF الخاص بك Office 365. ستقوم بتحرير السجل الحالي بحيث يكون لديك سجل SPF يتضمن القيم التي تحتاج إليها. بالنسبة إلى Office 365، "spf.protection.outlook.com".
  
صحيح:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

غير صحيحه:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>المزيد من الأمثلة على قيم SPF الشائعة
<a name="bkmk_addtospf"> </a>

إذا كنت تستخدم مجموعة Office 365 الكاملة وتستخدم MailChimp لإرسال رسائل البريد الإلكتروني التسويقية بالنيابة عنك، فقد يبدو سجل SPF في contoso.com كما يلي، والذي يستخدم الصفوف 1 و3 و5 من الجدول أعلاه. تذكر أن الصفين 1 و5 مطلوبان.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

بدلا من ذلك، إذا كان لديك تكوين مختلط Exchange حيث سيتم إرسال البريد الإلكتروني من كل من Office 365 ونظام البريد المحلي، فقد يبدو سجل SPF في contoso.com كما يلي:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

هذه بعض الأمثلة الشائعة التي يمكن أن تساعدك على تكييف سجل SPF الموجود عند إضافة مجالك إلى Office 365 للبريد الإلكتروني. إذا كان لديك سيناريو معقد يتضمن، على سبيل المثال، خوادم البريد الإلكتروني الحافة لإدارة نسبة استخدام الشبكة عبر جدار الحماية الخاص بك، سيكون لديك سجل SPF أكثر تفصيلا لإعداده. تعرف على كيفية: [إعداد سجلات SPF في Office 365 للمساعدة في منع الانتحال](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  
فيما يلي ارتباط قصير يمكنك استخدامه للعودة: [https://aka.ms/o365edns]()
