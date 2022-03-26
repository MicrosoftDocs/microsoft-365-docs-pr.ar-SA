---
title: تكوين تصفية الأذونات ل eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1adffc35-38e5-4f7d-8495-8e0e8721f377
description: استخدم تصفية أذونات البحث لكي تسمح لمديري eDiscovery بالبحث في مجموعة فرعية فقط من علب البريد والمواقع في مؤسستك.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6310334bdbfd1a94456d5e826daebb9f2945af14
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63566328"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>تكوين تصفية الأذونات ل eDiscovery

يمكنك استخدام تصفية أذونات البحث لتدع مدير eDiscovery يبحث فقط في مجموعة فرعية من علب البريد والمواقع في مؤسستك. يمكنك أيضا استخدام تصفية الأذونات لتدع إدارة eDiscovery نفسها تبحث فقط عن علبة البريد أو محتوى الموقع الذي يلبي معايير بحث معينة. على سبيل المثال، قد تسمح لمدير eDiscovery بالبحث في علب بريد المستخدمين في موقع أو قسم معين فقط. يمكنك القيام بذلك عن طريق إنشاء عامل تصفية يستخدم عامل تصفية مستلم معتمد للحد من علب البريد التي يمكن لمستخدم معين أو مجموعة من المستخدمين البحث فيها. يمكنك أيضا إنشاء عامل تصفية يحدد محتوى علبة البريد التي يمكن للمستخدم البحث عنها. يتم ذلك عن طريق إنشاء عامل تصفية يستخدم خاصية رسالة قابلة للبحث. وبالمثل، يمكنك السماح لمدير eDiscovery بالبحث في مواقع SharePoint محددة فقط في مؤسستك. يمكنك القيام بذلك عن طريق إنشاء عامل تصفية يحد من الموقع الذي يمكن البحث فيه. يمكنك أيضا إنشاء عامل تصفية يحدد محتوى الموقع الذي يمكن البحث فيه. يتم ذلك عن طريق إنشاء عامل تصفية يستخدم خاصية موقع قابلة للبحث.

يتم تطبيق عوامل تصفية أذونات البحث عند البحث عن محتوى باستخدام البحث في المحتوى و eDiscovery الأساسي Advanced eDiscovery في مركز التوافق في Microsoft 365. عند تطبيق عامل تصفية أذونات البحث على مستخدم معين، يمكن لهذا المستخدم تنفيذ الإجراءات التالية ذات الصلة بالبحث:

- البحث عن المحتوى

- معاينة نتائج البحث

- تصدير نتائج البحث

- إزالة العناصر التي تم إرجاعها بواسطة عملية بحث

يمكنك أيضا استخدام تصفية أذونات البحث لإنشاء حدود منطقية (تسمى حدود *التوافق) داخل* مؤسسة تتحكم في مواقع محتوى المستخدم (مثل علب البريد ومواقع SharePoint وحسابات OneDrive) التي يمكن لمديري eDiscovery المعينين البحث فيها. لمزيد من المعلومات، راجع [إعداد حدود التوافق لتحريات eDiscovery](set-up-compliance-boundaries.md).
  
تسمح لك cmdlets الأربعة التالية & الأمان في PowerShell بتكوين عوامل تصفية أذونات البحث وإدارتها:
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>متطلبات لتكوين تصفية الأذونات

- لتشغيل cmdlets لتصفية أمان التوافق، يجب أن تكون عضوا في مجموعة دور إدارة المؤسسة في مركز التوافق في Microsoft 365. لمزيد من المعلومات، راجع [الأذونات في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- يجب الاتصال بكل من Exchange Online والأمان & مركز التوافق PowerShell لاستخدام cmdlets لتصفية أمان التوافق. وهذا ضروري لأن أمر cmdlets هذا يتطلب الوصول إلى خصائص علبة البريد، ولهذا السبب يجب الاتصال ب PowerShell Exchange Online PowerShell. راجع الخطوات في المقطع التالي.

- راجع القسم [مزيد من المعلومات](#more-information) للحصول على معلومات إضافية حول عوامل تصفية أذونات البحث.

- تنطبق تصفية أذونات البحث على علب البريد غير النشطة، مما يعني أنه يمكنك استخدام تصفية محتوى علبة البريد علبة البريد وحصر الأشخاص الذين يمكنهم البحث في علبة بريد غير نشطة. راجع القسم [مزيد من المعلومات](#more-information) للحصول على معلومات إضافية حول تصفية الأذونات علب البريد غير النشطة.

- لا يمكن استخدام تصفية أذونات البحث للحد من الأشخاص الذين يمكنهم البحث في المجلدات العامة في Exchange.

- لا يوجد حد لعدد عوامل تصفية أذونات البحث التي يمكن إنشاؤها في مؤسسة. ومع ذلك، يمكن أن يكون لاستعلام البحث 100 شروط كحد أقصى. في هذه الحالة، يتم تعريف الشرط كشيء متصل باستعلام بواسطة عامل تشغيل منطقي (مثل **AND** و **OR** و **NEAR**). يتضمن الحد الأقصى لعدد الشروط استعلام البحث نفسه بالإضافة إلى كل عوامل تصفية أذونات البحث التي يتم تطبيقها على المستخدم الذي يقوم بتشغيل البحث. وبالتالي، كلما زاد عدد عوامل تصفية أذونات البحث لديك (خاصة إذا تم تطبيق عوامل التصفية هذه على نفس المستخدم أو مجموعة المستخدمين)، كانت فرصة تجاوز الحد الأقصى لعدد الشروط للبحث أفضل. لمنع مؤسستك من بلوغ الحد الأقصى للشروط، احتفظ بعدد عوامل تصفية أذونات البحث في مؤسستك إلى عدد قليل قدر الإمكان لتلبية متطلبات عملك. لمزيد من المعلومات، راجع [إعداد حدود التوافق لتحريات eDiscovery](set-up-compliance-boundaries.md#frequently-asked-questions).

## <a name="connect-to-exchange-online-and-security--compliance-center-powershell-in-a-single-session"></a>الاتصال إلى Exchange Online والأمان & مركز التوافق PowerShell في جلسة عمل واحدة

قبل أن تتمكن من تشغيل البرنامج النصي بنجاح في هذا المقطع، يجب تنزيل الوحدة النمطية Exchange Online PowerShell V2 وتثبيتها. للحصول على معلومات، راجع [حول الوحدة النمطية Exchange Online PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف **.ps1.** على سبيل المثال، يمكنك حفظه في ملف يسمى **ConnectEXO-SCC.ps1.**

    ```powershell
    Import-Module ExchangeOnlineManagement
    $UserCredential = Get-Credential
    Connect-ExchangeOnline -Credential $UserCredential -ShowBanner:$false
    Connect-IPPSSession -Credential $UserCredential
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. على الكمبيوتر المحلي، افتح Windows PowerShell، واذهب إلى المجلد حيث يوجد البرنامج النصي الذي أنشأته في الخطوة السابقة، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

    ```powershell
    .\ConnectEXO-SCC.ps1
    ```

كيف يمكنك معرفة ما إذا كان هذا الأمر يعمل؟ بعد تشغيل البرنامج النصي، يتم استيراد cmdlets من Exchange Online والأمان & التوافق PowerShell إلى جلسة عمل Windows PowerShell المحلية. إذا لم تتلق أي أخطاء، يمكنك الاتصال بنجاح. الاختبار السريع هو تشغيل Exchange Online والأمان & Cmdlets لمركز التوافق PowerShell. على سبيل المثال، يمكنك تشغيل **Get-Mailbox** و **Get-ComplianceSearch**.

للحصول على أخطاء اتصال PowerShell وإصلاحها، راجع:

- [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

يتم **استخدام New-ComplianceSecurityFilter** لإنشاء عامل تصفية أذونات البحث. إليك بناء الجملة الأساسي ل cmdlet هذا:

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

تصف الأقسام التالية معلمات الأمر cmdlet هذا. كل المعلمات مطلوبة لإنشاء عامل تصفية أذونات البحث.

### <a name="filtername"></a>*FilterName*

تحدد  _المعلمة FilterName_ اسم عامل تصفية الأذونات. يتم استخدام هذا الاسم لتصفية هوية عامل تصفية عند استخدام **أمر cmdlets Get-ComplianceSecurityFilter** و **Set-ComplianceSecurityFilter** و **Remove-ComplianceFilter** .

### <a name="filters"></a>*عوامل التصفية*

تحدد  _المعلمة_ عوامل التصفية معايير البحث لتصفية أمان التوافق. يمكنك إنشاء ثلاثة أنواع مختلفة من عوامل التصفية:  

- **علبة البريد أو OneDrive** التصفية: يحدد هذا النوع من التصفية علب البريد OneDrive الحسابات التي يمكن للمستخدمين المعينين البحث فيها (المحددة بواسطة المعلمة _Users)._ يسمى هذا النوع من عوامل التصفية عامل *تصفية موقع* المحتوى لأنه يعرف مواقع المحتوى التي يمكن للمستخدم البحث فيها. بناء جملة هذا النوع من التصفية هو **Mailbox_** _MailboxPropertyName_، حيث _يحدد MailboxPropertyName_ خاصية علبة البريد المستخدمة لنطاق علب البريد وحسابات OneDrive التي يمكن البحث فيها. `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` على سبيل المثال، قد يسمح عامل تصفية علبة البريد للمستخدم الذي تم تعيين عامل التصفية هذا بالبحث في علب البريد وحسابات OneDrive التي لها القيمة "تم تعيين المستخدمين" في الخاصية CustomAttribute10 فقط.

  يمكن استخدام أي خاصية مستلم معتمدة قابلة للتصفية لل خاصية _MailboxPropertyName_ في علبة بريد أو OneDrive عامل تصفية. سرد الجدول التالي أربع خصائص مستلم شائعة استخدامها لإنشاء علبة بريد أو OneDrive عامل تصفية. يتضمن الجدول أيضا مثالا لاستخدام الخاصية في عامل تصفية.

  |اسم الخاصية  |مثال  |
  |---------|---------|
  |الاسم المستعار    |`"Mailbox_Alias -like 'v-'"`         |
  |الشركة  |`"Mailbox_Company -eq 'Contoso'"`        |
  |CountryOrRegion |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |القسم |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **تصفية محتوى علبة البريد:** يتم تطبيق هذا النوع من عوامل التصفية على المحتوى الذي يمكن البحث عنه. يسمى هذا النوع من عوامل التصفية *عامل تصفية* المحتوى لأنه يحدد محتوى علبة البريد أو خصائص البريد الإلكتروني القابلة للبحث التي يمكن للمستخدمين المعينين البحث عنها. بناء جملة هذا النوع من عوامل **التصفية** هو MailboxContent__SearchablePropertyName، حيث  _يحدد SearchablePropertyName_ خاصية لغة استعلام الكلمة الأساسية (KQL) التي يمكن تحديدها في عملية بحث. على سبيل المثال، قد `"MailboxContent_Recipients  -like 'contoso.com'"` يسمح عامل تصفية محتوى علبة البريد للمستخدم الذي تم تعيين عامل التصفية هذا له بالبحث فقط عن الرسائل المرسلة إلى المستلمين في contoso.com المجال. للحصول على قائمة ب خصائص البريد الإلكتروني القابلة للبحث، راجع استعلامات الكلمات الأساسية [وشروط البحث ل eDiscovery](keyword-queries-and-search-conditions.md#searchable-email-properties).

  > [!IMPORTANT]
  > لا يمكن أن يحتوي عامل تصفية بحث واحد على عامل تصفية علبة بريد وتصفية محتوى علبة البريد. لدمجها في عامل تصفية واحد، يجب استخدام قائمة [عوامل التصفية](#using-a-filters-list-to-combine-filter-types).  ولكن يمكن أن يحتوي عامل التصفية على استعلام أكثر تعقيدا من النوع نفسه. على سبيل المثال `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **تصفية محتوى الموقع و الموقع:** هناك عاملا SharePoint و OneDrive ذات صلة يمكنك استخدامها لتحديد محتوى الموقع أو الموقع الذي يمكن للمستخدمين المعينين البحث فيه.

  - **Site_**_SearchableSiteProperty_
  
  - **SiteContent_**_SearchableSiteProperty_
  
   يمكن تبادل عاملي التصفية هذين. على سبيل المثال، `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` وإرجاع  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` النتائج نفسها. للحصول على قائمة ب خصائص الموقع القابلة للبحث، راجع استعلامات الكلمات الأساسية وشروط البحث ل [eDiscovery](keyword-queries-and-search-conditions.md#searchable-site-properties) للحصول على قائمة أكثر اكتمالا، راجع نظرة عامة حول الخصائص التي تم تتبع ارتباطاتها [وإدارتها في](/SharePoint/technical-reference/crawled-and-managed-properties-overview) SharePoint. يمكن استخدام الخصائص التي تم وضع **علامة "نعم** " عليها في العمود **"** استعلام" لإنشاء عامل تصفية محتوى موقع أو موقع.  

  > [!IMPORTANT]
  > لا يعني إعداد عامل تصفية موقع باستخدام إحدى الخصائص المعتمدة أن خاصية الموقع في عامل التصفية ستنشر في كل المستندات على هذا الموقع. وهذا يعني أن المستخدم لا يزال مسؤولا عن ملء حقول الخاصية المحددة المقترنة بالمستندات على هذا الموقع لكي يعمل عامل تصفية الموقع ويلتقط المحتوى المناسب. على سبيل المثال، إذا كان لدى المستخدم عامل تصفية أمان "Site_RefineableString00 eq 'abc'" مطبق، ثم يقوم المستخدم بتشغيل بحث باستخدام استعلام الكلمة الأساسية "xyz". يتم إلحاق عامل تصفية الأمان للاستعلام والاستعلام الفعلي قيد التشغيل سيكون "xyz **AND RefineableString0:'abc'**". يحتاج المستخدم إلى التأكد من أن المستندات على الموقع لها بالفعل قيم في الحقل RefineableString00 ك "abc". إذا لم يكن الأمر كذلك، فلن يرجع استعلام البحث أي نتائج.

ضع الاعتبارات التالية في الاعتبار عند تكوين *معلمة عوامل التصفية* لتصفية أذونات البحث:

- بخلاف علب البريد، لا يوجد عامل تصفية موقع المحتوى للمواقع على الرغم من  أن عامل تصفية الموقع يبدو مثل عامل تصفية الموقع. كل عوامل التصفية ل SharePoint و OneDrive هي عوامل تصفية المحتوى (وهذا هو أيضا سبب تبادل عوامل تصفية *Site_* و SiteContent_) لأن  الخصائص ذات الصلة بالموقع مثل *Path* يتم ختمها مباشرة على المستندات. لماذا هذا؟ إنها نتيجة لطريقة تصميم SharePoint. في SharePoint، لا يوجد "كائن موقع" مع خصائص، كما هو Exchange علب البريد. وبالتالي، *يتم ختم* الخاصية Path على المستند وتحتوي على عنوان URL للموقع حيث يوجد المستند. ولهذا *السبب، يعتبر* عامل تصفية الموقع عامل تصفية محتوى وليس عامل تصفية موقع المحتوى.

- يجب إنشاء عامل تصفية أذونات البحث لمنع المستخدمين صراحة من البحث في مواقع المحتوى في خدمة معينة (مثل منع المستخدم من البحث في أي علبة بريد Exchange بريد أو أي SharePoint ويب). بعبارة أخرى، لا يؤدي إنشاء عامل تصفية أذونات البحث الذي يسمح للمستخدم بالبحث في كل SharePoint في المؤسسة إلى منع ذلك المستخدم من البحث في علب البريد. على سبيل المثال، للسماح لمسؤولي SharePoint بالبحث فقط SharePoint المواقع، يجب إنشاء عامل تصفية يمنعهم من البحث في علب البريد. وبالمثل، للسماح لمسؤولي Exchange بالبحث في علب البريد فقط، يجب إنشاء عامل تصفية يمنعهم من البحث في المواقع.

### <a name="users"></a>*المستخدمون*

تحدد  _المعلمة_ Users المستخدمين الذين يتم تطبيق عامل التصفية هذا على عمليات البحث الخاصة بهم. تحديد المستخدمين حسب الاسم المستعار أو عنوان SMTP الأساسي. يمكنك تحديد قيم متعددة مفصولة بفصول، أو يمكنك تعيين عامل التصفية لجميع المستخدمين باستخدام القيمة **الكل**.

يمكنك أيضا استخدام المعلمة _Users_ (المستخدمون) لتحديد مجموعة مركز التوافق في Microsoft 365 أخرى. يتيح لك ذلك إنشاء مجموعة دور مخصصة ثم تعيين مجموعة الدور هذه لتصفية أذونات البحث. على سبيل المثال، لنقل أن لديك مجموعة دور مخصصة لمديري eDiscovery للشركة الفرعية الأمريكية لشركة متعددة الجنسيات. يمكنك استخدام المعلمة  _Users_ (المستخدمون) لتحديد مجموعة الدور هذه (باستخدام الخاصية Name (الاسم) لمجموعة الدور) ثم استخدام المعلمة  _Filter_ للسماح فقط بالبحث في علب البريد في الولايات المتحدة. لا يمكنك تحديد مجموعات التوزيع باستخدام هذه المعلمة.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>استخدام قائمة عوامل تصفية لدمج أنواع عوامل التصفية

إن *قائمة عوامل التصفية* هي عامل تصفية يتضمن عامل تصفية علبة بريد وتصفية موقع مفصولة ب فاصلة. تعمل هذه الفاصلة أيضا كعامل **تشغيل OR** . يعد استخدام قائمة عوامل التصفية الطريقة الوحيدة المعتمدة لدمج أنواع مختلفة من عوامل التصفية. في المثال التالي، لاحظ أن الفاصلة تفصل بين عاملي تصفية  "علبة **البريد" و**"الموقع":

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

عند معالجة عامل تصفية يحتوي على قائمة عوامل تصفية أثناء تشغيل عملية بحث، يتم إنشاء عاملي تصفية لأذونات البحث من قائمة عوامل التصفية: واحدة لكل عامل تصفية مفصول ب فاصلة. وبالتالي، في المثال السابق، سيتم إنشاء عامل تصفية أذونات البحث في علبة بريد واحد وتصفية أذونات البحث في موقع واحد. يتم توصيل عوامل التصفية هذه بواسطة **عامل التشغيل OR** .

البديل لاستخدام قائمة عوامل التصفية هو إنشاء عاملي تصفية منفصلين لأذونات البحث. وبالتالي، في المثال السابق، يمكنك إنشاء عامل تصفية واحد لنسبة علبة البريد وتصفية واحدة لنسبة الموقع. وفي كلتا الحالتين، تكون النتائج هي نفسها. إن استخدام قائمة عوامل تصفية أو إنشاء عوامل تصفية منفصلة لأذونات البحث هو أمر تفضيلات.

ضع الأمور التالية في الاعتبار حول استخدام قائمة عوامل التصفية:

- يجب استخدام قائمة عوامل تصفية لإنشاء عامل تصفية يتضمن عامل تصفية **علبة** البريد وتصفية **MailboxContent** .

- يمكن أن يحتوي كل مكون من عناصر قائمة عوامل التصفية على بناء جملة عامل تصفية معقد. على سبيل المثال، يمكن أن تحتوي عوامل تصفية علبة البريد وعامل تصفية الموقع على عوامل تصفية متعددة مفصولة **بعامل التشغيل -أو** عامل التشغيل:

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>أمثلة حول إنشاء عوامل تصفية أذونات البحث

فيما يلي أمثلة حول استخدام **cmdlet New-ComplianceSecurityFilter** لإنشاء عامل تصفية أذونات البحث.

يسمح هذا المثال لأعضاء مجموعة الدور "مديرو الاكتشافات الأمريكية" بالبحث فقط في علب البريد OneDrive الحسابات في الولايات المتحدة.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
يسمح هذا المثال annb@contoso.com المستخدم بتنفيذ إجراءات البحث فقط لعلب البريد OneDrive في كندا. يحتوي عامل التصفية هذا على رمز البلد الرقمي المكون من ثلاثة أرقام لكندا من ISO 3166-1.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

يسمح هذا المثال للمستخدمين دونه وسوكيرتوف بالبحث في علب البريد فقط OneDrive الحسابات التي لها القيمة "التسويق" ل خاصية علب البريد CustomAttribute1.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

يسمح هذا المثال لأعضاء مجموعة الدور "Fourth Coffee eDiscovery Managers" بالبحث في علب البريد وحسابات OneDrive التي لها القيمة 'FourthCoffee' ل خاصية علبة بريد القسم. يسمح عامل التصفية أيضا لأعضاء مجموعة الدور بالبحث عن المستندات في موقع fourth Coffee SharePoint الويب.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> في المثال السابق، يجب تضمين عامل تصفية محتوى موقع إضافي (`SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`) حتى يمكن لأعضاء مجموعة الدور البحث عن المستندات في OneDrive الحسابات. إذا لم يكن عامل التصفية هذا مضمنا، فإن عامل التصفية سيسمح فقط لأعضاء مجموعة الدور بالبحث عن المستندات الموجودة في `https://contoso.sharepoint.com/sites/FourthCoffee`.

يسمح هذا المثال لأعضاء مجموعة دور eDiscovery Manager بالبحث في علب البريد فقط OneDrive حسابات أعضاء مجموعة توزيع "المستخدمون الذين تم السماح لهم بالمهمة". يتم Get-DistributionGroup cmdlet في Exchange Online PowerShell للعثور على أعضاء مجموعة المستخدمون الذين تم تقديمهم.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

يمنع هذا المثال أي مستخدم من تنفيذ إجراءات البحث على علب البريد OneDrive حسابات أعضاء مجموعة توزيع الفريق التنفيذي. وهذا يعني أنه يمكن للمستخدمين حذف المحتوى من علب البريد هذه. يتم Get-DistributionGroup cmdlet Exchange Online PowerShell للعثور على أعضاء مجموعة الفريق التنفيذي.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

يسمح هذا المثال لأعضاء مجموعة OneDrive eDiscovery Managers المخصصة بالبحث عن المحتوى فقط في OneDrive في المؤسسة.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
يقيد هذا المثال المستخدم من تنفيذ إجراءات البحث فقط على رسائل البريد الإلكتروني المرسلة خلال سنة التقويم 2015.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

على غرار المثال السابق، يقيد هذا المثال المستخدم من تنفيذ إجراءات البحث فقط على المستندات التي تم تغييرها في وقت ما في سنة التقويم 2015.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

يمنع هذا المثال أعضاء مجموعة OneDrive "مديرو الاكتشاف" من تنفيذ إجراءات البحث على أي علبة بريد في المؤسسة.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

يمنع هذا المثال أي شخص في المؤسسة من تنفيذ إجراءات البحث على رسائل البريد الإلكتروني التي تم إرسالها أو تلقيها بواسطة janets أو sarad.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

يستخدم هذا المثال قائمة عوامل تصفية لدمج عوامل تصفية علبة البريد وتصفية الموقع. في هذا المثال، عامل تصفية علبة البريد هو عامل تصفية موقع المحتوى وتصفية الموقع هي عامل تصفية محتوى.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

يتم **استخدام Get-ComplianceSecurityFilter** لإرجاع قائمة بتصفية أذونات البحث. استخدم  _المعلمة FilterName_ لإرجاع معلومات لتصفية بحث معينة.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

يتم **استخدام Set-ComplianceSecurityFilter** لتعديل عامل تصفية أذونات بحث موجود. تصف الأقسام التالية معلمات الأمر cmdlet هذا. المعلمة المطلوبة فقط هي  _FilterName_.
  
### <a name="filtername"></a>*FilterName*

تحدد  _المعلمة FilterName_ اسم عامل تصفية الأذونات.

### <a name="users"></a>*المستخدمون*

تحدد  _المعلمة_ Users المستخدمين الذين يتم تطبيق عامل التصفية هذا على عمليات البحث الخاصة بهم. نظرا لأن هذه الخاصية متعددة القيم، فإن تحديد مستخدم أو مجموعة من المستخدمين الذين لديهم هذه المعلمة الكتابة فوق قائمة المستخدمين الموجودة. راجع الأمثلة التالية بناء الجملة لإضافة مستخدمين محددين وإزالهم.

يمكنك أيضا استخدام المعلمة _Users_ (المستخدمون) لتحديد مجموعة مركز التوافق في Microsoft 365 أخرى. يتيح لك ذلك إنشاء مجموعة دور مخصصة ثم تعيين مجموعة الدور هذه لتصفية أذونات البحث. على سبيل المثال، لنقل أن لديك مجموعة دور مخصصة لمديري eDiscovery للشركة الفرعية الأمريكية لشركة متعددة الجنسيات. يمكنك استخدام المعلمة  _Users_ (المستخدمون) لتحديد مجموعة الدور هذه (باستخدام الخاصية Name (الاسم) لمجموعة الدور) ثم استخدام المعلمة  _Filter_ للسماح فقط بالبحث في علب البريد في الولايات المتحدة. لا يمكنك تحديد مجموعات توزيع باستخدام هذه المعلمة.

### <a name="filters"></a>*عوامل التصفية*

تحدد  _المعلمة_ عوامل التصفية معايير البحث لتصفية أمان التوافق. يمكنك إنشاء ثلاثة أنواع مختلفة من عوامل التصفية:

- **علبة البريد OneDrive التصفية:** يحدد هذا النوع من التصفية علب البريد OneDrive الحسابات التي يمكن للمستخدمين المعينين البحث عنها (المحددة بواسطة المعلمة _Users)._ بناء جملة هذا النوع من التصفية هو **Mailbox_** _MailboxPropertyName_، حيث  _يحدد MailboxPropertyName_ خاصية علبة البريد المستخدمة لنطاق علب البريد التي يمكن البحث عنها. على سبيل المثال  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` ، قد يسمح عامل تصفية علبة البريد للمستخدم الذي تم تعيين عامل التصفية هذا بالبحث في علب البريد التي لها القيمة "المستخدمون" في الخاصية CustomAttribute10 فقط.  يمكن استخدام أي خاصية مستلم معتمدة قابلة للتصفية لل خاصية  _MailboxPropertyName_ . للحصول على قائمة بالخصائص المعتمدة، راجع [الخصائص القابلة للتصفية للمعلمة -RecipientFilter](/powershell/exchange/recipientfilter-properties).

- **تصفية محتوى علبة البريد:** يتم تطبيق هذا النوع من عوامل التصفية على المحتوى الذي يمكن البحث عنه. فهي تحدد محتوى علبة البريد التي يمكن للمستخدمين المعينين البحث عنها. بناء جملة هذا النوع من عوامل التصفية هو **MailboxContent_**_SearchablePropertyName_، حيث  _يحدد SearchablePropertyName_ خاصية لغة الاستعلام الأساسية (KQL) التي يمكن تحديدها في عملية بحث. على سبيل المثال، قد `"MailboxContent_Recipients  -like 'contoso.com'"` يسمح عامل تصفية محتوى علبة البريد للمستخدم الذي تم تعيين عامل التصفية هذا له بالبحث فقط عن الرسائل المرسلة إلى المستلمين في contoso.com المجال.  للحصول على قائمة ب خصائص البريد الإلكتروني القابلة للبحث، راجع استعلامات الكلمات الأساسية [وشروط البحث ل eDiscovery](keyword-queries-and-search-conditions.md).

- **تصفية محتوى الموقع و الموقع:** هناك عاملا تصفية SharePoint و OneDrive for Business ذات صلة بالموقع يمكنك استخدامها لتحديد محتوى الموقع أو الموقع الذي يمكن للمستخدمين المعينين البحث فيه:

  - **Site_** *SearchableSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  يمكن تبادل عاملي التصفية هذين. على سبيل المثال،  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` وإرجاع  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` النتائج نفسها. للحصول على قائمة ب خصائص الموقع القابلة للبحث، راجع [نظرة عامة](/SharePoint/technical-reference/crawled-and-managed-properties-overview) حول الخصائص التي تم تتبع ارتباطاتها وإدارتها في SharePoint. يمكن استخدام الخصائص التي تم وضع **علامة "نعم** " عليها في العمود **"** استعلام" لإنشاء عامل تصفية محتوى موقع أو موقع.

### <a name="examples-of-changing-search-permissions-filters"></a>أمثلة لتغيير عوامل تصفية أذونات البحث

تظهر هذه الأمثلة كيفية استخدام **الأمرين Cmdletter Get-ComplianceSecurityFilter** و **Set-ComplianceSecurityFillets** لإضافة مستخدم أو إزالته إلى قائمة المستخدمين الموجودة التي تم تعيين عامل التصفية لها. عند إضافة مستخدمين أو إزالتهم من عامل تصفية، حدد المستخدم باستخدام عنوان SMTP الخاص به.
  
يضيف هذا المثال مستخدما إلى عامل التصفية.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.add("pilarp@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

يزيل هذا المثال مستخدما من عامل التصفية.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.remove("annb@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

## <a name="remove-compliancesecurityfilter"></a>Remove-ComplianceSecurityFilter

يتم **استخدام Remove-ComplianceSecurityFilter** لحذف عامل تصفية البحث. استخدم  _المعلمة FilterName_ لتحديد عامل التصفية الذي تريد حذفه.
  
## <a name="more-information"></a>معلومات إضافية

- **كيف تعمل تصفية أذونات البحث؟** يتم إلحاق عامل تصفية الأذونات باستعلام البحث عند تشغيل عملية بحث. يتم ضم عامل تصفية الأذونات إلى استعلام البحث بواسطة **عامل التشغيل AND** Boolean. سيبدو منطق الاستعلام لاستعلام البحث وتصفية الأذونات كما يلي:

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  على سبيل المثال، لديك عامل تصفية أذونات يسمح ل باهيا بتنفيذ جميع إجراءات البحث على علب بريد أعضاء مجموعة توزيع "العاملين". بعد ذلك، يقوم بافلام البحث عن كل علب البريد في المؤسسة باستخدام استعلام البحث  `sender:jerry@adatum.com`. نظرا لتصفية الأذونات ودمج استعلام البحث منطقيا بواسطة عامل تشغيل **AND** ، يرجع البحث أي رسالة مرسلة بواسطة jerry@adatum.com إلى أي عضو في مجموعة توزيع "العاملين". 

- **ماذا يحدث إذا كان لديك عوامل تصفية أذونات بحث متعددة؟** في استعلام البحث، يتم دمج عوامل تصفية أذونات متعددة بواسطة **عوامل تشغيل OR** Boolean. وبالتالي، سيتم إرجاع النتائج إذا كانت أي من عوامل التصفية صحيحة. في عملية بحث، يتم دمج كل عوامل التصفية (التي يتم دمجها بواسطة **عوامل تشغيل OR** ) بعد ذلك مع استعلام البحث بواسطة **عامل التشغيل AND** .

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  فلنأخذ المثال السابق، حيث يسمح عامل تصفية البحث ل 'عادل' بالبحث في علب البريد الخاصة بأعضاء مجموعة توزيع "العاملين" فقط. بعد ذلك، نقوم بإنشاء عامل تصفية آخر يمنع باهى من البحث في علبة بريد فيل ("Mailbox_Alias -ne 'فيل"). ولنفترض أيضا أن فيل عضو في مجموعة "العاملون". عندما يقوم 'سهى' بتشغيل عملية بحث (من المثال السابق) على كل علب البريد في المؤسسة، يتم إرجاع نتائج البحث لعلبة بريد فيل على الرغم من تطبيق عامل التصفية لمنع باستر من البحث في علبة بريد فيل. وذلك لأن عامل التصفية الأول، الذي يسمح ل بابحث في مجموعة "العاملون"، صحيح. ونظرا لأن فيل عضو في مجموعة "العاملون"، يمكن أن يبحث باستر في علبة بريد فيل.

- **هل تعمل تصفية أذونات البحث مع علب البريد غير النشطة؟** نعم، يمكنك استخدام عوامل تصفية محتوى علب البريد علبة البريد والحد من الأشخاص الذين يمكنهم البحث في علب البريد غير النشطة في مؤسستك. مثل علبة بريد عادية، يجب تكوين علبة بريد غير نشطة باستخدام خاصية المستلم المستخدمة لإنشاء عامل تصفية الأذونات. إذا لزم الأمر، يمكنك استخدام الأمر **Get-Mailbox -InactiveMailboxOnly** لعرض خصائص علب البريد غير النشطة. لمزيد من المعلومات، راجع [إنشاء علب بريد غير نشطة وإدارتها](create-and-manage-inactive-mailboxes.md).
  
- **هل تعمل تصفية أذونات البحث للمجلدات العامة؟** لا. كما تم شرحه مسبقا، لا يمكن استخدام تصفية أذونات البحث للحد من الأشخاص الذين يمكنهم البحث في المجلدات العامة في Exchange. على سبيل المثال، لا يمكن استبعاد العناصر الموجودة في مواقع المجلدات العامة من نتائج البحث بواسطة عامل تصفية الأذونات.

- **هل السماح للمستخدم بالبحث في كل مواقع المحتوى في خدمة معينة يمنعه أيضا من البحث في مواقع المحتوى في خدمة مختلفة؟** لا. كما تم شرحه مسبقا، يجب إنشاء عامل تصفية أذونات البحث لمنع المستخدمين صراحة من البحث في مواقع المحتوى في خدمة معينة (مثل منع المستخدم من البحث في أي علبة بريد Exchange أو أي موقع SharePoint). بعبارة أخرى، لا يؤدي إنشاء عامل تصفية أذونات البحث الذي يسمح للمستخدم بالبحث في كل SharePoint في المؤسسة إلى منع ذلك المستخدم من البحث في علب البريد. على سبيل المثال، للسماح لمسؤولي SharePoint بالبحث فقط SharePoint المواقع، يجب إنشاء عامل تصفية يمنعهم من البحث في علب البريد. وبالمثل، للسماح لمسؤولي Exchange بالبحث في علب البريد فقط، يجب إنشاء عامل تصفية يمنعهم من البحث في المواقع.

- **هل يتم حساب عوامل تصفية أذونات البحث في مقابل حدود أحرف استعلام البحث؟** نعم. تحسب عوامل تصفية أذونات البحث مقابل حد الأحرف لاستعلامات البحث. لمزيد من المعلومات، راجع [الحدود في Advanced eDiscovery](limits-ediscovery20.md).

**ما هو الحد الأقصى لعدد عوامل تصفية أذونات البحث التي يمكن إنشاؤها في مؤسسة؟**
  
لا يوجد حد لعدد عوامل تصفية أذونات البحث التي يمكن إنشاؤها في مؤسسة. ومع ذلك، يمكن أن يكون لاستعلام البحث 100 شروط كحد أقصى. في هذه الحالة، يتم تعريف الشرط كشيء متصل باستعلام بواسطة عامل تشغيل منطقي (مثل **AND** و **OR** و **NEAR**). يتضمن الحد الأقصى لعدد الشروط استعلام البحث نفسه بالإضافة إلى كل عوامل تصفية أذونات البحث التي يتم تطبيقها على المستخدم الذي يقوم بتشغيل البحث. وبالتالي، كلما زاد عدد عوامل تصفية أذونات البحث لديك (خاصة إذا تم تطبيق عوامل التصفية هذه على نفس المستخدم أو مجموعة المستخدمين)، كانت فرصة تجاوز الحد الأقصى لعدد الشروط للبحث أفضل.

لفهم كيفية عمل هذا الحد، يجب أن تدرك أنه يتم إلحاق عامل تصفية أذونات البحث باستعلام البحث عند تشغيل عملية بحث. يتم ضم عامل تصفية أذونات البحث إلى استعلام البحث بواسطة **عامل التشغيل AND** Boolean. سيبدو منطق الاستعلام لاستعلام البحث وتصفية أذونات البحث الواحدة كما يلي:

```text
<SearchQuery> AND <PermissionsFilter>
```

يتم دمج عوامل تصفية أذونات البحث المتعددة معا بواسطة **عامل التشغيل OR** Boolean، ثم يتم توصيل هذه الشروط باستعلام البحث بواسطة **عامل التشغيل AND** .

قد يبدو منطق الاستعلام لاستعلام البحث وتصفية أذونات البحث المتعددة كما يلي:

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

من المحتمل أن يتكون استعلام البحث نفسه من شروط متعددة متصلة بواسطة عوامل التشغيل منطقية. سيتم أيضا حساب كل شرط في استعلام البحث مقابل حد الشرط 100.

يعتمد أيضا عدد عوامل تصفية أذونات البحث الملحقة باستعلام على المستخدم الذي يقوم بتشغيل البحث. عندما يقوم مستخدم معين بتشغيل عملية بحث، يتم إلحاق أذونات البحث بالتصفية التي يتم تطبيقها على المستخدم (والتي يتم تعريفها بواسطة المعلمة *المستخدمون* في عامل التصفية) إلى الاستعلام. قد تملك مؤسستك المئات من عوامل تصفية أذونات البحث، ولكن إذا تم تطبيق أكثر من 100 عامل تصفية على المستخدمين نفسهم، فمن المرجح أن يتم تجاوز الحد الأقصى ل 100 شرط عند تشغيل هؤلاء المستخدمين لعمليات البحث.

هناك شيء آخر يجب وضعه في الاعتبار حول حد الشرط. يتم أيضا حساب عدد المواقع SharePoint المحددة المضمنة في استعلام البحث أو عوامل تصفية أذونات البحث مقابل هذا الحد. 

لمنع مؤسستك من بلوغ الحد الأقصى للشروط، احتفظ بعدد عوامل تصفية أذونات البحث في مؤسستك إلى عدد قليل قدر الإمكان لتلبية متطلبات عملك.