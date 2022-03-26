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
description: قائمة مرجعية لسجلات نظام أسماء المجالات الخارجية لاستخدامها عند التخطيط Office 365 النشر.
ms.openlocfilehash: 39b6f093c196d8b696a8d36458d2ebc18be2a5f2
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/10/2021
ms.locfileid: "63569383"
---
# <a name="external-domain-name-system-records-for-office-365"></a>سجلات نظام أسماء المجالات الخارجية Office 365

![المجال.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**هل تريد الاطلاع على قائمة مخصصة بسجلات DNS Office 365 مؤسستك؟** يمكنك العثور [على المعلومات التي تحتاج إليها لإنشاء Office 365 DNS](../admin/get-help-with-domains/information-for-dns-records.md) لمجالك في Office 365.

**هل تحتاج إلى مساعدة خطوة بخطوة لإضافة هذه السجلات لدى مضيف DNS لمجالك، مثل GoDaddy أو eNom؟** [ابحث عن ارتباطات إلى إرشادات مفصلة خطوة بخطوة للعديد من مضيفي DNS الشائعين](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**هل تريد الالتفاف لاستخدام القائمة المرجعية للنشر المخصص الخاص بك؟** يجب استخدام القائمة أدناه كمرجع لنشر Office 365 المخصص. ستحتاج إلى تحديد السجلات التي تنطبق على مؤسستك وملء القيم المناسبة.

**ارجع إلى** [تخطيط الشبكة وضبط الأداء Office 365](./network-planning-and-performance.md).

غالبا ما تكون سجلات SPF و MX الأصعب في معرفة ذلك. لقد قمنا بتحديث إرشادات سجلات SPF في نهاية هذه المقالة. الشيء المهم الذي يجب تذكره هو أنه يمكنك الحصول على سجل _SPF واحد فقط لمجالك_. يمكنك الحصول على سجلات MX متعددة؛ ومع ذلك، قد يسبب ذلك مشاكل لتسليم البريد. إن امتلاك سجل MX واحد يوجه البريد الإلكتروني إلى نظام بريد واحد يزيل الكثير من المشاكل المحتملة.
  
يتم تنظيم المقاطع أدناه حسب الخدمة في Office 365. لرؤية قائمة مخصصة لسجلات DNS Office 365 مجالك، سجل الدخول إلى Office 365 واجمع المعلومات التي تحتاج إليها [لإنشاء Office 365 DNS](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>سجلات DNS الخارجية المطلوبة Office 365 (الخدمات الأساسية)
<a name="BKMK_ReqdCore"> </a>

يحتاج Office 365 العميل إلى إضافة سجلين إلى DNS الخارجي. يضمن سجل CNAME الأول أنه Office 365 توجيه محطات العمل للمصادقة باستخدام النظام الأساسي المناسب للهوية. أما السجل الثاني المطلوب فيكمن في إثبات أنك تملك اسم مجالك.
  
|**سجل DNS** <br/> |**الغرض** <br/> |**القيمة التي يجب استخدامها** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Suite)** <br/> |يستخدمه Office 365 لتوجيه المصادقة إلى النظام الأساسي الصحيح للهوية. [معلومات إضافية](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **ملاحظة:** ينطبق CNAME هذا فقط على Office 365 التي يتم تشغيلها بواسطة 21Vianet. إذا كان موجودا ولم يتم تشغيل Office 365 بواسطة 21Vianet، سيحصل المستخدمون على مجالك المخصص على *خطأ "المجال* المخصص غير موجود في نظامنا" ولن يتمكنوا من تنشيط ترخيص Office 365 الخاص بهم. [معلومات إضافية](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**الاسم المستعار:** msoid  <br/> **الهدف: clientconfig.partner.microsoftonline-p.net.cn**  <br/> |
|**TXT** <br/> **(التحقق من المجال)** <br/> |يستخدمه Office 365 للتحقق فقط من أنك تملك مجالك. ولا يؤثر ذلك على أي شيء آخر.  <br/> |**المضيف:** @ (أو، لبعض موفري استضافة DNS، اسم مجالك)  <br/> **قيمة TXT:** _سلسلة نصية توفرها Office 365_  <br/> يوفر Office 365 **إعداد** المجال القيم التي تستخدمها لإنشاء هذا السجل.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>سجلات DNS الخارجية المطلوبة للبريد الإلكتروني في Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

يتطلب البريد الإلكتروني Office 365 عدة سجلات مختلفة. السجلات الأساسية الثلاثة التي يجب أن يستخدمها كل العملاء هي سجلات الاكتشاف التلقائي و MX و SPF.
  
- **يسمح سجل الاكتشاف التلقائي** لأجهزة الكمبيوتر العميلة Exchange العميل وتكوينه بشكل صحيح.

- **يخبر سجل MX** أنظمة البريد الأخرى بمكان إرسال البريد الإلكتروني لمجالك. **ملاحظة:** عند تغيير البريد الإلكتروني إلى Office 365، من خلال تحديث سجل MX لمجالك، ستبدأ جميع رسائل البريد الإلكتروني المرسلة إلى هذا المجال في Office 365.  
هل تريد فقط تبديل بعض عناوين البريد الإلكتروني إلى Office 365؟ يمكنك استخدام [Office 365 مع بعض عناوين البريد الإلكتروني على مجالك المخصص](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- تستخدم أنظمة البريد الإلكتروني للمستلم سجل **TXT ل SPF** للتحقق من أن الخادم الذي يرسل بريدك الإلكتروني هو الخادم الذي توافق عليه. يساعد ذلك على منع حدوث مشاكل مثل خادعة البريد الإلكتروني والتصيد الاحتيالي. راجع سجلات [DNS الخارجية المطلوبة ل SPF](external-domain-name-system-records.md#BKMK_SPFrecords) في هذه المقالة لمساعدتك على فهم ما يجب تضمينه في السجل.

ستحتاج أيضا عملاء البريد الإلكتروني الذين يستخدمون Exchange إلى سجل CNAME وTXT الإضافي المدرج في أسفل الجدول.
  
|**سجل DNS** <br/> |**الغرض** <br/> |**القيمة التي يجب استخدامها** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Exchange Online)** <br/> |يساعد Outlook العملاء على الاتصال بسهولة Exchange Online الخدمة باستخدام خدمة الاكتشاف التلقائي. يعثر "الاكتشاف التلقائي" تلقائيا على Exchange Server المضيف الصحيح ويكو Outlook للمستخدمين.  <br/> |**الاسم المستعار:** Autodiscover  <br/> **الهدف: autodiscover.outlook.com**  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |يرسل البريد الوارد لمجالك إلى Exchange Online البريد الإلكتروني Office 365.  <br/> **ملاحظة:** بمجرد تدفق البريد الإلكتروني إلى Exchange Online، يجب إزالة سجلات MX التي تشير إلى النظام القديم.   |**المجال:** على سبيل المثال، contoso.com  <br/> **خادم البريد الإلكتروني الهدف:**\<MX token\>. mail.protection.outlook.com  <br/> **التفضيل/الأولوية:** أقل من أي سجلات MX أخرى (يضمن ذلك تسليم البريد إلى Exchange Online) - على سبيل المثال 1 أو "منخفض"  <br/>  ابحث عن من \<MX token\> خلال اتباع الخطوات التالية:  <br/>  سجل الدخول Office 365، واذهب إلى Office 365 المسؤول\>.  <br/>  في العمود الإجراء لمجالك، اختر إصلاح المشاكل.  <br/>  في المقطع سجلات MX، اختر ما الذي يمكنني إصلاحه؟  <br/>  اتبع التوجيهات في هذه الصفحة لتحديث سجل MX.  <br/> [ما هي أولوية MX؟](../admin/setup/domains-faq.yml) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |يساعد على منع الأشخاص الآخرين من استخدام مجالك لإرسال بريد عشوائي أو بريد إلكتروني ضار آخر. تعمل سجلات إطار نهج المرسل (SPF) من خلال تحديد الخوادم المعتمدة لإرسال البريد الإلكتروني من مجالك.  <br/> |[سجلات DNS الخارجية المطلوبة ل SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange الخارجية)** <br/> |يستخدم هذا Exchange التوزيع المختلط.  <br/> |**سجل TXT 1:** على سبيل المثال، contoso.com نص مقترن بتقصوصة مخصصة تم إنشاؤها خصيصا (على سبيل المثال، Y96nu89138789315669824)  <br/> **سجل TXT 2:** على سبيل المثال، exchangedelegation.contoso.com ونص مقترن بتفهيش إثبات المجال تم إنشاؤه بشكل مخصص (على سبيل المثال، Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Exchange الخارجية)** <br/> |يساعد Outlook العملاء على الاتصال بسهولة Exchange Online الخدمة باستخدام خدمة الاكتشاف التلقائي عندما تستخدم شركتك Exchange الخارجية. يعثر الاكتشاف التلقائي تلقائيا على Exchange Server المضيف الصحيح ويكو Outlook للمستخدمين.  <br/> |**الاسم المستعار:** على سبيل المثال، Autodiscover.service.contoso.com  <br/> **الهدف: autodiscover.outlook.com**  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>سجلات DNS الخارجية المطلوبة Skype for Business Online
<a name="BKMK_ReqdCore"> </a>

هناك خطوات معينة يجب اتخاذها عند استخدام نطاقات عناوين IP Office 365 عناوين [URL](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) للتأكد من تكوين الشبكة بشكل صحيح.

> [!NOTE]
> تنطبق سجلات DNS هذه أيضا على Teams، خاصة في سيناريو Teams المختلط Skype for Business، حيث قد تنشأ بعض مشاكل الاتحاد.
  
|**سجل DNS** <br/> |**الغرض** <br/> |**القيمة التي يجب استخدامها** <br/> |
|----------|-----------|------------|
|**SRV** <br/> **(Skype for Business Online)** <br/> |يسمح لمجالك Office 365 مشاركة ميزات المراسلة الفورية (IM) مع العملاء الخارجيين من خلال تمكين اتحاد SIP. اقرأ المزيد [حول Office 365 URL ونطاقات عناوين IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**الخدمة:** sipfederationtls  <br/> **البروتوكول:** TCP  <br/> **الأولوية:** 100  <br/> **الوزن:** 1  <br/> **المنفذ:** 5061  <br/> **الهدف: sipfed.online.lync.com**  <br/> **ملاحظة:** إذا كان جدار الحماية أو الخادم الوكيل يمنع عمليات البحث في SRV على DNS خارجي، يجب إضافة هذا السجل إلى سجل DNS الداخلي.   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |يستخدمه Skype for Business لتنسيق تدفق المعلومات بين عملاء Lync.  <br/> |**الخدمة:** sip  <br/> **البروتوكول:** TLS  <br/> **الأولوية:** 100  <br/> **الوزن:** 1  <br/> **المنفذ:** 443  <br/> **الهدف: sipdir.online.lync.com**  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |يستخدمه عميل Lync للمساعدة في العثور على Skype for Business عبر الإنترنت تسجيل الدخول.  <br/> |**الاسم المستعار:** sip  <br/> **الهدف: sipdir.online.lync.com**  <br/> لمزيد من المعلومات، [راجع Office 365 عناوين URL وIP النطاقات](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |يستخدمه عميل Lync mobile للمساعدة في العثور على Skype for Business عبر الإنترنت تسجيل الدخول.  <br/> |**الاسم المستعار:** lyncdiscover  <br/> **الهدف: webdir.online.lync.com**  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>سجلات DNS الخارجية المطلوبة Office 365 سجلات Sign-On
<a name="BKMK_ReqdCore"> </a>

|**سجل DNS** <br/> |**الغرض** <br/> |**القيمة التي يجب استخدامها** <br/> |
|----------|-----------|------------|
|**المضيف (A)** <br/> |يستخدم تسجيل الدخول الفردي (SSO). فهو يوفر نقطة النهاية للمستخدمين غير المحليين (والمستخدمين المحليين، إذا أردت ذلك) للاتصال بتكوين خوادم خوادم خدمات الاتحاد ل Active Directory (AD FS) أو IP الظاهري (VIP) المتوازن للتحميل.  <br/> |**الهدف:** على سبيل المثال، sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>سجلات DNS الخارجية المطلوبة ل SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> تم تصميم SPF للمساعدة في منع ال انتحال، ولكن هناك أساليب انتحال لا يمكن ل SPF حمايتها. للحماية من هذه، بعد إعداد SPF، يجب أيضا تكوين DKIM و DMARC Office 365. للبدء، راجع [استخدام DKIM للتحقق من صحة](../security/office-365-security/use-dkim-to-validate-outbound-email.md) البريد الإلكتروني الصادر المرسل من مجالك في Office 365. بعد ذلك، راجع [استخدام DMARC للتحقق من صحة البريد الإلكتروني في Office 365](../security/office-365-security/use-dmarc-to-validate-email.md).
  
سجلات SPF هي سجلات TXT التي تساعد على منع الأشخاص الآخرين من استخدام مجالك لإرسال بريد عشوائي أو بريد إلكتروني ضار آخر. تعمل سجلات إطار نهج المرسل (SPF) من خلال تحديد الخوادم المعتمدة لإرسال البريد الإلكتروني من مجالك.
  
يمكنك الحصول على سجل SPF واحد فقط (أي سجل TXT يعرف SPF) لمجالك. يمكن أن يكون لهذا السجل الواحد بعض التضمينات المختلفة، ولكن لا يمكن أن يزيد إجمالي عمليات البحث عن DNS التي ينتج عنها عن 10 عمليات (يساعد ذلك على منع هجمات رفض الخدمة). راجع الجدول والأمثلة الأخرى أدناه لمساعدتك على إنشاء قيم سجل SPF المناسبة لبيئة أو تحديثها.
  
### <a name="structure-of-an-spf-record"></a>بنية سجل SPF

تحتوي كل سجلات SPF على ثلاثة أجزاء: الإعلان بأنه سجل SPF والمجالات وعناوين IP التي يجب أن ترسل البريد الإلكتروني، ولقاعدة فرض. تحتاج إلى الثلاثة كلها في سجل SPF صالح. فيما يلي مثال لسجل SPF شائع Office 365 عند استخدام بريد إلكتروني Exchange Online الإلكتروني فقط:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

إن نظام البريد الإلكتروني الذي يتلقى رسالة بريد إلكتروني من مجالك ينظر إلى سجل SPF، وإذا كان خادم البريد الإلكتروني الذي أرسل الرسالة Office 365 الخادم، يتم قبول الرسالة. إذا كان الخادم الذي أرسل الرسالة هو نظام البريد القديم أو نظام ضار على الإنترنت، على سبيل المثال، فقد تفشل عملية التحقق من SPF ولن يتم تسليم الرسالة. تساعد عمليات التحقق هذه على منع رسائل الخادعة والتصيد الاحتيالي.
  
### <a name="choose-the-spf-record-structure-you-need"></a>اختر بنية سجل SPF التي تحتاج إليها

بالنسبة إلى السيناريوهات التي لا تستخدم فيها بريد Exchange Online الإلكتروني ل Office 365 فقط (على سبيل المثال، عند استخدام البريد الإلكتروني الذي ينشأ من SharePoint Online أيضا)، استخدم الجدول التالي لتحديد ما يجب تضمينه في قيمة السجل.
  
> [!NOTE]
> إذا كان لديك سيناريو معقد يتضمن، على سبيل المثال، خوادم البريد الإلكتروني edge لإدارة حركة مرور البريد الإلكتروني عبر جدار الحماية، سيكون لديك سجل SPF أكثر تفصيلا لإعداده. تعرف على كيفية القيام بذلك: إعداد سجلات [SPF في Office 365 للمساعدة في منع التهزاء](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). يمكنك أيضا معرفة المزيد حول كيفية عمل SPF مع Office 365 من خلال قراءة كيفية استخدام Office 365 نهج المرسل [(SPF) للمساعدة](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md) في منع الانتحال.
  
| رقم|إذا كنت تستخدم...  <br/> |الغرض  <br/> |إضافة هذه تتضمن  <br/> |
|:-----|:-----|:-----|:-----|
|1  <br/> |كل أنظمة البريد الإلكتروني (مطلوبة)  <br/> |تبدأ كل سجلات SPF بهذه القيمة  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (شائع)  <br/> |استخدم مع Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |نظام بريد إلكتروني جهة خارجية (أقل شيوعا)  <br/> ||تتضمن:\<email system like mail.contoso.com\>  <br/> |
|4  <br/> |نظام البريد المحلي (أقل شيوعا)  <br/> |استخدم إذا كنت تستخدم Exchange Online Protection أو Exchange Online بريد إلكتروني آخر  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> تتضمن:\<mail.contoso.com\>  <br/> يجب أن تكون القيمة بين قوسين (\<\>) أنظمة بريد أخرى سترسل بريدا إلكترونيا لمجالك.  <br/> |
|5  <br/> |كل أنظمة البريد الإلكتروني (مطلوبة)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>مثال: إضافة إلى سجل SPF موجود
<a name="bkmk_addtospf"> </a>

إذا كان لديك سجل SPF بالفعل، ستحتاج إلى إضافة قيم أو تحديثها Office 365. على سبيل المثال، لنقول أن سجل SPF contoso.com هو التالي:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

أنت الآن تقوم بتحديث سجل SPF Office 365. ستحرر السجل الحالي بحيث يكون لديك سجل SPF يتضمن القيم التي تحتاج إليها. بالنسبة Office 365، "spf.protection.outlook.com".
  
صحيح:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

غير صحيح:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>مزيد من الأمثلة حول قيم SPF الشائعة
<a name="bkmk_addtospf"> </a>

إذا كنت تستخدم مجموعة Office 365 الكاملة وتستخدم MailChimp لإرسال رسائل البريد الإلكتروني التسويقية بالنيابة عنك، فقد يبدو سجل SPF في contoso.com كما يلي، الذي يستخدم الصفوف 1 و3 و5 من الجدول أعلاه. تذكر أن الصفين 1 و5 مطلوبان.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

بدلا من ذلك، إذا كان لديك تكوين Exchange المختلط حيث سيتم إرسال البريد الإلكتروني من كل من Office 365 ونظام البريد الخاص بك في الموقع، فقد يبدو سجل SPF في contoso.com كما يلي:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

هذه بعض الأمثلة الشائعة التي يمكن أن تساعدك على تكييف سجل SPF الموجود عند إضافة مجالك Office 365 البريد الإلكتروني. إذا كان لديك سيناريو معقد يتضمن، على سبيل المثال، خوادم البريد الإلكتروني edge لإدارة حركة مرور البريد الإلكتروني عبر جدار الحماية، سيكون لديك سجل SPF أكثر تفصيلا لإعداده. تعرف على كيفية القيام بذلك: إعداد سجلات [SPF في Office 365 للمساعدة في منع التهزاء](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  
إليك ارتباط مختصر يمكنك استخدامه للعودة: [https://aka.ms/o365edns]()
