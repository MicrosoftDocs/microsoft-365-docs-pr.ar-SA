---
title: تكوين تصفية الأذونات ل eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: استخدم تصفية أذونات البحث للسماح لمديري eDiscovery بالبحث في مجموعة فرعية فقط من علب البريد والمواقع في مؤسستك.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4ebd42882c7b914fe661df589382482d9f0595bc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625006"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>تكوين تصفية الأذونات ل eDiscovery

يمكنك استخدام تصفية أذونات البحث للسماح لمدير eDiscovery بالبحث في مجموعة فرعية فقط من علب البريد والمواقع في مؤسستك. يمكنك أيضا استخدام تصفية الأذونات للسماح لمدير eDiscovery نفسه بالبحث فقط عن علبة البريد أو محتوى الموقع الذي يفي بمعايير بحث معينة. على سبيل المثال، قد تسمح لمدير eDiscovery بالبحث فقط في علب بريد المستخدمين في موقع أو قسم معين. يمكنك القيام بذلك عن طريق إنشاء عامل تصفية يستخدم عامل تصفية مستلم معتمد لتحديد علب البريد التي يمكن لمستخدم معين أو مجموعة من المستخدمين البحث فيها. يمكنك أيضا إنشاء عامل تصفية يحدد محتوى علبة البريد الذي يمكن للمستخدم البحث فيه. يتم ذلك عن طريق إنشاء عامل تصفية يستخدم خاصية رسالة قابلة للبحث. وبالمثل، يمكنك السماح لمدير eDiscovery بالبحث في مواقع SharePoint معينة فقط في مؤسستك. يمكنك القيام بذلك عن طريق إنشاء عامل تصفية يحد من الموقع الذي يمكن البحث فيه. يمكنك أيضا إنشاء عامل تصفية يحدد محتوى الموقع الذي يمكن البحث فيه. يتم ذلك عن طريق إنشاء عامل تصفية يستخدم خاصية موقع قابلة للبحث.

يتم تطبيق عوامل تصفية أذونات البحث عند البحث عن المحتوى باستخدام البحث عن المحتوى Microsoft Purview eDiscovery (قياسي) Microsoft Purview eDiscovery (Premium) في مدخل التوافق في Microsoft Purview. عند تطبيق عامل تصفية أذونات البحث على مستخدم معين، يمكن لهذا المستخدم تنفيذ الإجراءات التالية المتعلقة بالبحث:

- البحث عن المحتوى

- معاينة نتائج البحث

- تصدير نتائج البحث

- إزالة العناصر التي تم إرجاعها بواسطة عملية بحث

يمكنك أيضا استخدام تصفية أذونات البحث لإنشاء حدود منطقية (تسمى *حدود التوافق*) داخل مؤسسة تتحكم في مواقع محتوى المستخدم (مثل علب البريد ومواقع SharePoint وحسابات OneDrive) التي يمكن لمديري eDiscovery المحددين البحث فيها. لمزيد من المعلومات، راجع [إعداد حدود التوافق لتحقيقات eDiscovery](set-up-compliance-boundaries.md).
  
تتيح لك أوامر cmdlets الأربعة التالية في Security & Compliance PowerShell تكوين عوامل تصفية أذونات البحث وإدارتها:
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>متطلبات تكوين تصفية الأذونات

- لتشغيل cmdlets لتصفية أمان التوافق، يجب أن تكون عضوا في مجموعة دور إدارة المؤسسة في مدخل التوافق. لمزيد من المعلومات، راجع [الأذونات في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- يجب عليك الاتصال بكل من Exchange Online والأمان & Compliance PowerShell لاستخدام cmdlets لتصفية أمان التوافق. هذا ضروري لأن أوامر cmdlets هذه تتطلب الوصول إلى خصائص علبة البريد، ولهذا السبب يجب عليك الاتصال Exchange Online PowerShell. راجع الخطوات في القسم التالي.

- راجع القسم ["مزيد من المعلومات](#more-information) " للحصول على معلومات إضافية حول عوامل تصفية أذونات البحث.

- تنطبق تصفية أذونات البحث على علب البريد غير النشطة، مما يعني أنه يمكنك استخدام تصفية محتوى علبة البريد وعلب البريد للحد من الأشخاص الذين يمكنهم البحث في علبة بريد غير نشطة. راجع القسم ["مزيد من المعلومات](#more-information) " للحصول على معلومات إضافية حول تصفية الأذونات وعلب البريد غير النشطة.

- لا يمكن استخدام تصفية أذونات البحث للحد من الأشخاص الذين يمكنهم البحث في المجلدات العامة في Exchange.

- لا يوجد حد لعدد عوامل تصفية أذونات البحث التي يمكن إنشاؤها في مؤسسة. ومع ذلك، يمكن أن يحتوي استعلام البحث على 100 شرط كحد أقصى. في هذه الحالة، يتم تعريف الشرط على أنه شيء متصل بالاستعلام بواسطة عامل تشغيل منطقي (مثل **AND** **وOR** و **NEAR**). يتضمن حد عدد الشروط استعلام البحث نفسه بالإضافة إلى كافة عوامل تصفية أذونات البحث التي يتم تطبيقها على المستخدم الذي يقوم بتشغيل البحث. لذلك، كلما زادت عوامل تصفية أذونات البحث لديك (خاصة إذا تم تطبيق عوامل التصفية هذه على نفس المستخدم أو مجموعة المستخدمين)، كانت فرصة تجاوز الحد الأقصى لعدد الشروط للبحث أفضل. لمنع مؤسستك من الوصول إلى الحد الأقصى للشروط، احتفظ بعدد عوامل تصفية أذونات البحث في مؤسستك إلى أقل عدد ممكن لتلبية متطلبات عملك. لمزيد من المعلومات، راجع [إعداد حدود التوافق لتحقيقات eDiscovery](set-up-compliance-boundaries.md#frequently-asked-questions).

## <a name="connect-to-exchange-online-and-security--compliance-powershell-in-a-single-session"></a>الاتصال Exchange Online والأمان & Compliance PowerShell في جلسة واحدة

قبل أن تتمكن من تشغيل البرنامج النصي بنجاح في هذا القسم، عليك تنزيل وتثبيت الوحدة النمطية Exchange Online PowerShell V2. للحصول على معلومات، راجع [حول الوحدة النمطية Exchange Online PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. احفظ النص التالي في ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف **.ps1**. على سبيل المثال، يمكنك حفظه في ملف يسمى **ConnectEXO-SCC.ps1**.

    ```powershell
    Import-Module ExchangeOnlineManagement
    $UserCredential = Get-Credential
    Connect-ExchangeOnline -Credential $UserCredential -ShowBanner:$false
    Connect-IPPSSession -Credential $UserCredential
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. على الكمبيوتر المحلي، افتح Windows PowerShell، وانتقل إلى المجلد حيث يوجد البرنامج النصي الذي أنشأته في الخطوة السابقة، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

    ```powershell
    .\ConnectEXO-SCC.ps1
    ```

كيف يمكنك معرفة ما إذا كان هذا يعمل؟ بعد تشغيل البرنامج النصي، تتوفر أوامر cmdlets من Exchange Online PowerShell والأمان & Compliance PowerShell. إذا لم تتلق أي أخطاء، فيمكنك الاتصال بنجاح. الاختبار السريع هو تشغيل Exchange Online PowerShell و Security & Compliance PowerShell cmdlets. على سبيل المثال، يمكنك التشغيل والحصول **على علبة البريد** والحصول **على ComplianceSearch**.

لاستكشاف أخطاء اتصال PowerShell وإصلاحها، راجع:

- [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [الاتصال ب Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

يتم استخدام **New-ComplianceSecurityFilter** لإنشاء عامل تصفية أذونات البحث. فيما يلي بناء الجملة الأساسي ل cmdlet هذا:

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

تصف الأقسام التالية معلمات أمر cmdlet هذا. كافة المعلمات مطلوبة لإنشاء عامل تصفية أذونات البحث.

### <a name="filtername"></a>*اسم عامل التصفية*

تحدد المعلمة  _FilterName_ اسم عامل تصفية الأذونات. يستخدم هذا الاسم لتحديد عامل تصفية عند استخدام **Get-ComplianceSecurityFilter** و **Set-ComplianceSecurityFilter** و **Remove-ComplianceSecurityFilter** cmdlets.

### <a name="filters"></a>*عوامل التصفيه*

تحدد  _معلمة عوامل التصفية_ معايير البحث لعامل تصفية أمان التوافق. يمكنك إنشاء ثلاثة أنواع مختلفة من عوامل التصفية:  

- **تصفية علبة البريد أو OneDrive:** يحدد هذا النوع من عوامل التصفية علب البريد وحسابات OneDrive التي يمكن للمستخدمين المعينين (المحددين بواسطة معلمة  _المستخدمين_ ) البحث فيها. يسمى هذا النوع من عوامل التصفية عامل تصفية *موقع المحتوى* لأنه يعرف مواقع المحتوى التي يمكن للمستخدم البحث فيها. بناء الجملة لهذا النوع من عوامل التصفية هو **Mailbox_** _MailboxPropertyName_، حيث يحدد  _MailboxPropertyName_ خاصية علبة البريد المستخدمة لتحديد نطاق علب البريد وحسابات OneDrive التي يمكن البحث فيها. على سبيل المثال، قد يسمح عامل تصفية  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` علبة البريد للمستخدم بتعيين عامل التصفية هذا للبحث فقط في علب البريد وحسابات OneDrive التي تحتوي على القيمة "المستخدمون_ في الخاصية CustomAttribute10.

  يمكن استخدام أي خاصية مستلم معتمدة قابلة للتصفية  _للخاصية MailboxPropertyName_ في علبة بريد أو عامل تصفية OneDrive. يتضمن الجدول التالي أربع خصائص مستلم شائعة الاستخدام تستخدم لإنشاء علبة بريد أو عامل تصفية OneDrive. يتضمن الجدول أيضا مثالا لاستخدام الخاصية في عامل تصفية.

  |اسم الخاصية  |المثال  |
  |---------|---------|
  |الاسم المستعار    |`"Mailbox_Alias -like 'v-'"`         |
  |الشركه  |`"Mailbox_Company -eq 'Contoso'"`        |
  |البلد/المنطقة |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |اداره |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **تصفية محتوى علبة البريد:** يتم تطبيق هذا النوع من عوامل التصفية على المحتوى الذي يمكن البحث فيه. يسمى هذا النوع من عوامل *التصفية عامل تصفية محتوى* لأنه يحدد محتوى علبة البريد أو خصائص البريد الإلكتروني القابلة للبحث التي يمكن للمستخدمين المعينين البحث عنها. بناء الجملة لهذا النوع من عوامل التصفية **هو MailboxContent_** _SearchablePropertyName، حيث يحدد  _SearchablePropertyName_ خاصية لغة استعلام الكلمات الأساسية (KQL) التي يمكن تحديدها في عملية بحث. على سبيل المثال، يسمح عامل تصفية `"MailboxContent_Recipients  -like 'contoso.com'"` محتوى علبة البريد للمستخدم بتعيين عامل التصفية هذا للبحث فقط عن الرسائل المرسلة إلى المستلمين في مجال contoso.com. للحصول على قائمة بخصائص البريد الإلكتروني القابلة للبحث، راجع [استعلامات الكلمات الأساسية وشروط البحث في eDiscovery](keyword-queries-and-search-conditions.md#searchable-email-properties).

  > [!IMPORTANT]
  > لا يمكن أن يحتوي عامل تصفية بحث واحد على عامل تصفية علبة بريد وعامل تصفية محتوى علبة البريد. لدمجها في عامل تصفية واحد، يجب استخدام [قائمة عوامل التصفية](#using-a-filters-list-to-combine-filter-types).  ولكن يمكن أن يحتوي عامل التصفية على استعلام أكثر تعقيدا من نفس النوع. على سبيل المثال `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **تصفية محتوى الموقع والموقع:** هناك عاملا تصفية مرتبطان ب SharePoint وOneDrive يمكنك استخدامهما لتحديد محتوى الموقع أو الموقع الذي يمكن للمستخدمين المعينين البحث فيه.

  - **Site_**_SearchableSiteProperty_
  
  - **SiteContent_**_SearchableSiteProperty_
  
   يمكن تبادل عاملي التصفية هذين. على سبيل المثال، `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` وإرجاع  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` نفس النتائج. للحصول على قائمة بخصائص الموقع القابلة للبحث، راجع [استعلامات الكلمات الأساسية وشروط البحث في eDiscovery](keyword-queries-and-search-conditions.md#searchable-site-properties)  للحصول على قائمة أكثر اكتمالا، راجع [نظرة عامة حول الخصائص المدارة والمتتبعة في SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). يمكن استخدام الخصائص التي تم وضع علامة **"نعم** " عليها في العمود **"قابل للاستعلام** " لإنشاء عامل تصفية محتوى موقع أو موقع.  

  > [!IMPORTANT]
  > لا يعني إعداد عامل تصفية موقع بإحدى الخصائص المعتمدة أن خاصية الموقع في عامل التصفية ستنشر إلى كافة المستندات الموجودة على هذا الموقع. وهذا يعني أن المستخدم لا يزال مسؤولا عن تعبئة حقول الخصائص المحددة المقترنة بالمستندات الموجودة على هذا الموقع لكي يعمل عامل تصفية الموقع ويلتقط المحتوى الصحيح. على سبيل المثال، إذا كان لدى المستخدم عامل تصفية أمان "Site_RefineableString00 -eq 'abc' مطبق ثم يقوم المستخدم بتشغيل بحث باستخدام استعلام الكلمة الأساسية "xyz". يتم إلحاق عامل تصفية الأمان بالاستعلام وسيكون الاستعلام الفعلي قيد التشغيل "xyz **AND RefineableString0:'abc'**". يحتاج المستخدم إلى التأكد من أن المستندات الموجودة على الموقع تحتوي بالفعل على قيم في الحقل RefineableString00 ك "abc". إذا لم يكن الأمر كذلك، فلن يرجع استعلام البحث أي نتائج.

ضع الاعتبارات التالية في الاعتبار عند تكوين معلمة *عوامل التصفية* لعوامل تصفية أذونات البحث:

- على عكس علب البريد، لا يوجد عامل تصفية موقع محتوى للمواقع على الرغم من أن عامل تصفية *الموقع* يبدو كعامل تصفية موقع. كل عوامل التصفية ل SharePoint وOneDrive هي عوامل تصفية المحتوى (وهذا هو السبب أيضا في *أن عوامل* التصفية *Site_ وعوامل* التصفية SiteContent_ قابلة للتبادل) لأن الخصائص المتعلقة بالموقع مثل *المسار* يتم طابعها مباشرة على المستندات. لماذا هذا؟ إنها نتيجة للطريقة التي تم بها تصميم SharePoint. في SharePoint، لا يوجد "كائن موقع" بخصائص، كما هو الحال مع علب بريد Exchange. لذلك، يتم وضع طابع على خاصية *المسار* على المستند وتحتوي على عنوان URL للموقع حيث يوجد المستند. هذا هو السبب في أن عامل تصفية *الموقع* يعتبر عامل تصفية محتوى وليس عامل تصفية موقع محتوى.

- يجب عليك إنشاء عامل تصفية أذونات بحث لمنع المستخدمين من البحث في مواقع المحتوى في خدمة معينة بشكل صريح (مثل منع مستخدم من البحث في أي علبة بريد Exchange أو أي موقع SharePoint). بمعنى آخر، لا يمنع إنشاء عامل تصفية أذونات البحث الذي يسمح للمستخدم بالبحث في كافة مواقع SharePoint في المؤسسة هذا المستخدم من البحث في علب البريد. على سبيل المثال، للسماح لمسؤولي SharePoint بالبحث في مواقع SharePoint فقط، يجب عليك إنشاء عامل تصفية يمنعهم من البحث في علب البريد. وبالمثل، للسماح لمسؤولي Exchange بالبحث في علب البريد فقط، يجب إنشاء عامل تصفية يمنعهم من البحث في المواقع.

### <a name="users"></a>*المستخدمون*

تحدد معلمة  _"المستخدمون_ " المستخدمين الذين تم تطبيق عامل التصفية هذا على عمليات البحث الخاصة بهم. تحديد المستخدمين حسب الاسم المستعار أو عنوان SMTP الأساسي. يمكنك تحديد قيم متعددة مفصولة بفواصل، أو يمكنك تعيين عامل التصفية لكافة المستخدمين باستخدام القيمة **All**.

يمكنك أيضا استخدام معلمة  _المستخدمين_ لتحديد مجموعة دور مدخل التوافق. يتيح لك ذلك إنشاء مجموعة أدوار مخصصة ثم تعيين عامل تصفية أذونات البحث لمجموعة الأدوار هذه. على سبيل المثال، لنفترض أن لديك مجموعة أدوار مخصصة لمديري eDiscovery للشركة الفرعية الأمريكية لشركة متعددة الجنسيات. يمكنك استخدام المعلمة  _"المستخدمون_ " لتحديد مجموعة الأدوار هذه (باستخدام خاصية "الاسم" لمجموعة الأدوار) ثم استخدام المعلمة  _"تصفية_ " للسماح بالبحث في علب البريد في الولايات المتحدة فقط. لا يمكنك تحديد مجموعات توزيع بهذه المعلمة.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>استخدام قائمة عوامل تصفية لدمج أنواع عوامل التصفية

*قائمة عوامل التصفية* هي عامل تصفية يتضمن عامل تصفية علبة بريد وعامل تصفية موقع مفصول بفاواصل. تعمل هذه الفاصلة أيضا كعامل تشغيل **OR** . استخدام قائمة عوامل التصفية هو الأسلوب الوحيد المعتمد للجمع بين أنواع مختلفة من عوامل التصفية. في المثال التالي، لاحظ أن الفاصلة تفصل بين **عاملي تصفية "علبة البريد** " و" **الموقع** ":

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

عند معالجة عامل تصفية يحتوي على قائمة عوامل تصفية أثناء تشغيل عملية بحث، يتم إنشاء عاملي تصفية لأذونات البحث من قائمة عوامل التصفية: واحد لكل عامل تصفية مفصول بفاواصل. لذلك في المثال السابق، سيتم إنشاء عامل تصفية أذونات بحث علبة بريد واحد وعامل تصفية أذونات بحث موقع واحد. يتم توصيل عوامل التصفية هذه بواسطة عامل تشغيل **OR** .

بديل لاستخدام قائمة عوامل التصفية هو إنشاء عاملي تصفية منفصلين لأذونات البحث. لذلك في المثال السابق، يمكنك إنشاء عامل تصفية واحد لسمة علبة البريد وعامل تصفية واحد لسمة الموقع. في كلتا الحالتين، تكون النتائج هي نفسها. يعد استخدام قائمة عوامل تصفية أو إنشاء عوامل تصفية منفصلة لأذونات البحث مسألة تفضيل.

ضع الأشياء التالية في الاعتبار حول استخدام قائمة عوامل التصفية:

- يجب استخدام قائمة عوامل تصفية لإنشاء عامل تصفية يتضمن عامل تصفية **علبة بريد** وعامل تصفية **MailboxContent** .

- يمكن أن يحتوي كل مكون من عناصر قائمة عوامل التصفية على بناء جملة عامل تصفية معقد. على سبيل المثال، يمكن أن تحتوي عوامل تصفية علبة البريد والموقع على عوامل تصفية متعددة مفصولة **بعامل تشغيل -أو** :

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>أمثلة على إنشاء عوامل تصفية أذونات البحث

فيما يلي أمثلة على استخدام **New-ComplianceSecurityFilter** cmdlet لإنشاء عامل تصفية أذونات البحث.

يسمح هذا المثال لأعضاء مجموعة دور "مديري الاكتشاف في الولايات المتحدة" بالبحث فقط في علب البريد وحسابات OneDrive في الولايات المتحدة.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
يسمح هذا المثال للمستخدم annb@contoso.com بتنفيذ إجراءات البحث فقط لعلب البريد وحسابات OneDrive في كندا. يحتوي عامل التصفية هذا على رمز البلد الرقمي المكون من ثلاثة أرقام لكندا من ISO 3166-1.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

يسمح هذا المثال للمستخدمين donh و suaff بالبحث فقط في علب البريد وحسابات OneDrive التي تحتوي على القيمة 'Marketing' لخاصية علبة بريد CustomAttribute1.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

يسمح هذا المثال لأعضاء مجموعة دور "Fourth Coffee eDiscovery Managers" بالبحث فقط في علب البريد وحسابات OneDrive التي تحتوي على القيمة "FourthCoffee" لخاصية علبة بريد القسم. يسمح عامل التصفية أيضا لأعضاء مجموعة الأدوار بالبحث عن المستندات في موقع Fourth Coffee SharePoint.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> في المثال السابق، يجب تضمين عامل تصفية محتوى موقع إضافي (`SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`) لتمكين أعضاء مجموعة الأدوار من البحث عن المستندات في حسابات OneDrive. إذا لم يكن عامل التصفية هذا مضمنا، فسيسمح عامل التصفية لأعضاء مجموعة الأدوار فقط بالبحث عن المستندات الموجودة في `https://contoso.sharepoint.com/sites/FourthCoffee`.

يسمح هذا المثال لأعضاء مجموعة أدوار eDiscovery Manager بالبحث فقط في علب البريد وحسابات OneDrive الخاصة بأعضاء مجموعة توزيع المستخدمين البسطاء. يتم استخدام Get-DistributionGroup cmdlet في Exchange Online PowerShell للعثور على أعضاء مجموعة المستخدمين الواعين.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

يمنع هذا المثال أي مستخدم من تنفيذ إجراءات البحث على علب البريد وحسابات OneDrive لأعضاء مجموعة توزيع الفريق التنفيذي. وهذا يعني أنه يمكن للمستخدمين حذف المحتوى من علب البريد هذه. يتم استخدام Get-DistributionGroup cmdlet في Exchange Online PowerShell للعثور على أعضاء مجموعة الفريق التنفيذي.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

يسمح هذا المثال لأعضاء مجموعة الأدوار المخصصة ل OneDrive eDiscovery Managers بالبحث فقط عن المحتوى في حسابات OneDrive في المؤسسة.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
يقيد هذا المثال المستخدم بتنفيذ إجراءات البحث فقط على رسائل البريد الإلكتروني المرسلة خلال السنة التقويمية 2015.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

على غرار المثال السابق، يقيد هذا المثال المستخدم بتنفيذ إجراءات البحث فقط على المستندات التي تم تغييرها آخر مرة في السنة التقويمية 2015.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

يمنع هذا المثال أعضاء مجموعة أدوار "مديرو اكتشاف OneDrive" من تنفيذ إجراءات البحث على أي علبة بريد في المؤسسة.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

يمنع هذا المثال أي شخص في المؤسسة من تنفيذ إجراءات البحث على رسائل البريد الإلكتروني التي تم إرسالها أو تلقيها من قبل جانت أو مارد.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

يستخدم هذا المثال قائمة عوامل تصفية لدمج عوامل تصفية علبة البريد والموقع. في هذا المثال، عامل تصفية علبة البريد هو عامل تصفية موقع محتوى وعامل تصفية الموقع هو عامل تصفية محتوى.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

يتم استخدام **Get-ComplianceSecurityFilter** لإرجاع قائمة بعوامل تصفية أذونات البحث. استخدم المعلمة  _FilterName_ لإرجاع معلومات لعامل تصفية بحث معين.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

يتم استخدام **Set-ComplianceSecurityFilter** لتعديل عامل تصفية أذونات بحث موجود. تصف الأقسام التالية معلمات أمر cmdlet هذا. المعلمة المطلوبة الوحيدة هي  _FilterName_.
  
### <a name="filtername"></a>*اسم عامل التصفية*

تحدد المعلمة  _FilterName_ اسم عامل تصفية الأذونات.

### <a name="users"></a>*المستخدمون*

تحدد معلمة  _"المستخدمون_ " المستخدمين الذين تم تطبيق عامل التصفية هذا على عمليات البحث الخاصة بهم. نظرا إلى أن هذه خاصية متعددة القيم، فحدد مستخدما أو مجموعة من المستخدمين الذين لديهم هذه المعلمة، ثم قم بالكتابة فوق قائمة المستخدمين الموجودة. راجع الأمثلة التالية لبناء الجملة لإضافة المستخدمين المحددين وإزالتها.

يمكنك أيضا استخدام معلمة  _المستخدمين_ لتحديد مجموعة دور مدخل التوافق. يتيح لك ذلك إنشاء مجموعة أدوار مخصصة ثم تعيين عامل تصفية أذونات البحث لمجموعة الأدوار هذه. على سبيل المثال، لنفترض أن لديك مجموعة أدوار مخصصة لمديري eDiscovery للشركة الفرعية الأمريكية لشركة متعددة الجنسيات. يمكنك استخدام المعلمة  _"المستخدمون_ " لتحديد مجموعة الأدوار هذه (باستخدام خاصية "الاسم" لمجموعة الأدوار) ثم استخدام المعلمة  _"تصفية_ " للسماح بالبحث في علب البريد في الولايات المتحدة فقط. لا يمكنك تحديد مجموعات التوزيع باستخدام هذه المعلمة.

### <a name="filters"></a>*عوامل التصفيه*

تحدد  _معلمة عوامل التصفية_ معايير البحث لعامل تصفية أمان التوافق. يمكنك إنشاء ثلاثة أنواع مختلفة من عوامل التصفية:

- **تصفية علبة البريد وOneDrive:** يحدد هذا النوع من عوامل التصفية علب البريد وحسابات OneDrive التي يمكن للمستخدمين المعينين (المحددين بواسطة معلمة  _المستخدمين_ ) البحث فيها. بناء الجملة لهذا النوع من عوامل التصفية هو **Mailbox_** _MailboxPropertyName_، حيث يحدد  _MailboxPropertyName_ خاصية علبة البريد المستخدمة لتحديد نطاق علب البريد التي يمكن البحث فيها. على سبيل المثال، قد يسمح عامل تصفية  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` علبة البريد للمستخدم بتعيين عامل التصفية هذا للبحث فقط في علب البريد التي تحتوي على القيمة "أداة المعالجة الافتراضية" في الخاصية CustomAttribute10.  يمكن استخدام أي خاصية مستلم معتمدة قابلة للتصفية للخاصية  _MailboxPropertyName_ . للحصول على قائمة بالخصائص المعتمدة، راجع [الخصائص القابلة للتصفية للمعلمة -RecipientFilter](/powershell/exchange/recipientfilter-properties).

- **تصفية محتوى علبة البريد:** يتم تطبيق هذا النوع من عوامل التصفية على المحتوى الذي يمكن البحث فيه. وهو يحدد محتوى علبة البريد التي يمكن للمستخدمين المعينين البحث عنها. بناء الجملة لهذا النوع من عوامل التصفية هو **MailboxContent_**_SearchablePropertyName_، حيث يحدد  _SearchablePropertyName_ خاصية لغة استعلام الكلمات الأساسية (KQL) التي يمكن تحديدها في عملية بحث. على سبيل المثال، يسمح عامل تصفية `"MailboxContent_Recipients  -like 'contoso.com'"` محتوى علبة البريد للمستخدم بتعيين عامل التصفية هذا للبحث فقط عن الرسائل المرسلة إلى المستلمين في مجال contoso.com.  للحصول على قائمة بخصائص البريد الإلكتروني القابلة للبحث، راجع [استعلامات الكلمات الأساسية وشروط البحث في eDiscovery](keyword-queries-and-search-conditions.md).

- **تصفية محتوى الموقع والموقع:** هناك عاملا تصفية ل SharePoint وعوامل تصفية OneDrive for Business متعلقة بالموقع يمكنك استخدامهما لتحديد محتوى الموقع أو الموقع الذي يمكن للمستخدمين المعينين البحث فيه:

  - **Site_** *SearchableSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  يمكن تبادل عاملي التصفية هذين. على سبيل المثال،  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` وإرجاع  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` نفس النتائج. للحصول على قائمة بخصائص الموقع القابلة للبحث، راجع [نظرة عامة على الخصائص التي تم تتبع ارتباطاتها والخصائص المدارة في SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). يمكن استخدام الخصائص التي تم وضع علامة **"نعم** " عليها في العمود **"قابل للاستعلام** " لإنشاء عامل تصفية محتوى موقع أو موقع.

### <a name="examples-of-changing-search-permissions-filters"></a>أمثلة لتغيير عوامل تصفية أذونات البحث

توضح هذه الأمثلة كيفية استخدام **الأمرين Get-ComplianceSecurityFilter** و **Set-ComplianceSecurityFilter** cmdlets لإضافة مستخدم أو إزالته إلى قائمة المستخدمين الموجودة التي تم تعيين عامل التصفية إليها. عند إضافة مستخدمين أو إزالتهم من عامل تصفية، حدد المستخدم باستخدام عنوان SMTP الخاص بهم.
  
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

يتم استخدام **Remove-ComplianceSecurityFilter** لحذف عامل تصفية بحث. استخدم معلمة  _FilterName_ لتحديد عامل التصفية الذي تريد حذفه.
  
## <a name="more-information"></a>معلومات إضافية

- **كيف تعمل تصفية أذونات البحث؟** يتم إلحاق عامل تصفية الأذونات باستعلام البحث عند تشغيل عملية بحث. يتم ربط عامل تصفية الأذونات باستعلام البحث بواسطة عامل التشغيل **AND** المنطقي. سيبدو منطق الاستعلام لاستعلام البحث وعامل تصفية الأذونات كما يلي:

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  على سبيل المثال، لديك عامل تصفية أذونات يسمح ل Bob بتنفيذ كافة إجراءات البحث على علب البريد الخاصة بأعضاء مجموعة توزيع "العمال". ثم يقوم Bob بتشغيل بحث على كافة علب البريد في المؤسسة باستخدام استعلام  `sender:jerry@adatum.com`البحث. نظرا لأنه يتم دمج عامل تصفية الأذونات واستعلام البحث منطقيا بواسطة عامل تشغيل **AND** ، يقوم البحث بإرجاع أي رسالة تم إرسالها بواسطة jerry@adatum.com إلى أي عضو في مجموعة توزيع "العمال". 

- **ماذا يحدث إذا كان لديك عوامل تصفية متعددة لأذونات البحث؟** في استعلام البحث، يتم دمج عوامل تصفية الأذونات المتعددة بواسطة عوامل التشغيل **المنطقية OR** . لذلك سيتم إرجاع النتائج إذا كان أي من عوامل التصفية صحيحا. في عملية البحث، يتم دمج كافة عوامل التصفية (المجمعة بواسطة عوامل تشغيل **OR** ) مع استعلام البحث بواسطة عامل التشغيل **AND** .

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  لنأخذ المثال السابق، حيث يسمح عامل تصفية البحث ل Bob بالبحث فقط في علب البريد الخاصة بأعضاء مجموعة توزيع العمال. ثم نقوم بإنشاء عامل تصفية آخر يمنع Bob من البحث في علبة بريد Phil ("Mailbox_Alias -ne 'Phil'"). ولنفترض أيضا أن فيل عضو في مجموعة العمال. عندما يقوم Bob بتشغيل عملية بحث (من المثال السابق) على جميع علب البريد في المؤسسة، يتم إرجاع نتائج البحث لعلبة بريد Phil على الرغم من تطبيق عامل التصفية لمنع Bob من البحث في علبة بريد Phil. وذلك لأن عامل التصفية الأول، الذي يسمح ل Bob بالبحث في مجموعة العمال، صحيح. ولأن Phil هو عضو في مجموعة العمال، يمكن ل Bob البحث في علبة بريد Phil.

- **هل تعمل تصفية أذونات البحث لعلب البريد غير النشطة؟** نعم، يمكنك استخدام عوامل تصفية محتوى علبة البريد وعلب البريد لتحديد الأشخاص الذين يمكنهم البحث في علب البريد غير النشطة في مؤسستك. مثل علبة البريد العادية، يجب تكوين علبة بريد غير نشطة مع خاصية المستلم المستخدمة لإنشاء عامل تصفية أذونات. إذا لزم الأمر، يمكنك استخدام الأمر **Get-Mailbox -ActiveMailboxOnly** لعرض خصائص علب البريد غير النشطة. لمزيد من المعلومات، راجع [إنشاء علب البريد غير النشطة وإدارتها](create-and-manage-inactive-mailboxes.md).
  
- **هل تعمل تصفية أذونات البحث للمجلدات العامة؟** لا. كما هو موضح سابقا، لا يمكن استخدام تصفية أذونات البحث للحد من الأشخاص الذين يمكنهم البحث في المجلدات العامة في Exchange. على سبيل المثال، لا يمكن استبعاد العناصر الموجودة في مواقع المجلدات العامة من نتائج البحث بواسطة عامل تصفية الأذونات.

- **هل يؤدي السماح للمستخدم بالبحث في كافة مواقع المحتوى في خدمة معينة أيضا إلى منعه من البحث في مواقع المحتوى في خدمة مختلفة؟** لا. كما هو موضح سابقا، يجب عليك إنشاء عامل تصفية أذونات بحث لمنع المستخدمين بشكل صريح من البحث في مواقع المحتوى في خدمة معينة (مثل منع مستخدم من البحث في أي علبة بريد Exchange أو أي موقع SharePoint). بمعنى آخر، لا يمنع إنشاء عامل تصفية أذونات البحث الذي يسمح للمستخدم بالبحث في كافة مواقع SharePoint في المؤسسة هذا المستخدم من البحث في علب البريد. على سبيل المثال، للسماح لمسؤولي SharePoint بالبحث في مواقع SharePoint فقط، يجب عليك إنشاء عامل تصفية يمنعهم من البحث في علب البريد. وبالمثل، للسماح لمسؤولي Exchange بالبحث في علب البريد فقط، يجب إنشاء عامل تصفية يمنعهم من البحث في المواقع.

- **هل تحسب عوامل تصفية أذونات البحث مقابل حدود أحرف استعلام البحث؟** نعم. يتم حساب عوامل تصفية أذونات البحث مقابل حد الأحرف الخاص بالاستعلامات البحث. لمزيد من المعلومات، راجع ["حدود" في eDiscovery (Premium).](limits-ediscovery20.md)

**ما هو الحد الأقصى لعدد عوامل تصفية أذونات البحث التي يمكن إنشاؤها في مؤسسة؟**
  
لا يوجد حد لعدد عوامل تصفية أذونات البحث التي يمكن إنشاؤها في مؤسسة. ومع ذلك، يمكن أن يحتوي استعلام البحث على 100 شرط كحد أقصى. في هذه الحالة، يتم تعريف الشرط على أنه شيء متصل بالاستعلام بواسطة عامل تشغيل منطقي (مثل **AND** **وOR** و **NEAR**). يتضمن حد عدد الشروط استعلام البحث نفسه بالإضافة إلى كافة عوامل تصفية أذونات البحث التي يتم تطبيقها على المستخدم الذي يقوم بتشغيل البحث. لذلك، كلما زادت عوامل تصفية أذونات البحث لديك (خاصة إذا تم تطبيق عوامل التصفية هذه على نفس المستخدم أو مجموعة المستخدمين)، كانت فرصة تجاوز الحد الأقصى لعدد الشروط للبحث أفضل.

لفهم كيفية عمل هذا الحد، تحتاج إلى فهم أن عامل تصفية أذونات البحث يتم إلحاقه باستعلام البحث عند تشغيل عملية بحث. يتم ربط عامل تصفية أذونات البحث باستعلام البحث بواسطة عامل التشغيل **AND** المنطقي. قد يبدو منطق الاستعلام لاستعلام البحث وعامل تصفية أذونات بحث واحد كما يلي:

```text
<SearchQuery> AND <PermissionsFilter>
```

يتم دمج عوامل تصفية أذونات البحث المتعددة معا بواسطة عامل التشغيل **OR** المنطقي، ثم يتم توصيل هذه الشروط باستعلام البحث بواسطة عامل التشغيل **AND** .

قد يبدو منطق الاستعلام لاستعلام البحث وعوامل تصفية أذونات البحث المتعددة كما يلي:

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

من المحتمل أن يتكون استعلام البحث نفسه من شروط متعددة متصلة بواسطة عوامل التشغيل المنطقية. سيتم حساب كل شرط في استعلام البحث أيضا مقابل حد 100 شرط.

بالإضافة إلى ذلك، يعتمد عدد عوامل تصفية أذونات البحث الملحقة باستعلام على المستخدم الذي يقوم بتشغيل البحث. عندما يقوم مستخدم معين بتشغيل عملية بحث، يتم إلحاق عوامل تصفية أذونات البحث التي يتم تطبيقها على المستخدم (التي تم تعريفها بواسطة معلمة *المستخدمين* في عامل التصفية) بالاستعلام. قد يكون لدى مؤسستك مئات عوامل تصفية أذونات البحث، ولكن إذا تم تطبيق أكثر من 100 عامل تصفية على نفس المستخدمين، فمن المحتمل أن يتم تجاوز حد 100 شرط عند تشغيل هؤلاء المستخدمين لعمليات البحث.

هناك شيء آخر يجب أن تضعه في الاعتبار حول حد الشرط. كما يتم حساب عدد مواقع SharePoint المحددة المضمنة في استعلام البحث أو عوامل تصفية أذونات البحث مقابل هذا الحد. 

لمنع مؤسستك من الوصول إلى الحد الأقصى للشروط، احتفظ بعدد عوامل تصفية أذونات البحث في مؤسستك إلى أقل عدد ممكن لتلبية متطلبات عملك.