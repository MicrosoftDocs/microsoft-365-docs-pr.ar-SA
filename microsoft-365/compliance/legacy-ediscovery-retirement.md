---
title: تم إيقاف أدوات eDiscovery القديمة
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: سيتم إيقاف In-Place eDiscovery و In-Place e Hold (وPowerShell cmdlets المقابلة) في Exchange Online في النصف الأول من عام 2020. يتم أيضا إيقاف Search-Mailbox cmdlet وMicrosoft Purview eDiscovery (Premium) الإصدار 1.0 خلال نفس الفترة الزمنية.
ms.openlocfilehash: 228827ec405165bf8308d89fba350eb2192f6723
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936588"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>تقاعد أدوات eDiscovery القديمة

> [!IMPORTANT]
> تمت إزالة وظائف أدوات eDiscovery القديمة الموضحة في هذه المقالة إما من خدمة Microsoft 365 أو لا تزال متوفرة، ولكن لم تعد معتمدة. يمكن إزالة أي وظيفة لا تزال متوفرة دون إشعار. إذا كنت لا تزال تستخدم أيا من هذه الأدوات القديمة، ففكر في الترحيل إلى أدوات eDiscovery في مدخل توافق Microsoft Purview أو أحد البدائل الموضحة في هذه المقالة.

على مر السنين، قدمت Microsoft أدوات eDiscovery التي تتيح لك البحث عن محتوى البريد الإلكتروني ومعاينته وتصديره من Exchange Online. ومع ذلك، لم تعد هذه الأدوات توفر طريقة فعالة للبحث عن محتوى غير Exchange في خدمات Microsoft 365 أخرى، مثل SharePoint Online و مجموعات Microsoft 365. لمعالجة هذا الأمر، تقدم Microsoft أدوات eDiscovery أخرى تساعدك في البحث عن مجموعة متنوعة من محتوى Microsoft 365. وقد عملنا بجد لدمج وظائف eDiscovery الأحدث والأقوى في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق</a>. يسمح هذا للمؤسسات بالاستجابة لطلبات المستندات القانونية والداخلية وغيرها من طلبات المستندات للمحتوى عبر العديد من خدمات Microsoft 365، بما في ذلك Exchange Online.

نتيجة لوظيفة eDiscovery الجديدة والمحسنة هذه في مدخل التوافق، نقوم بحذف الميزات والوظائف التالية المتعلقة ب eDiscovery المتعلقة بالبحث عن محتوى البريد الإلكتروني في Exchange Online Microsoft 365:

- [قوائم احتجاز في مكان eDiscovery](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) وفي [مكانها](/exchange/security-and-compliance/create-or-remove-in-place-holds) في مركز إدارة Exchange.

- أوامر cmdlets Exchange Online PowerShell التي تدعم In-Place eDiscovery و"In-Place Holds" (يتم تعريف أوامر cmdlets هذه بشكل جماعي على أنها أوامر cmdlets **-MailboxSearch*). يتضمن ذلك أوامر cmdlets التالية:

  - [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch)

  - [بدء البحث في علبة البريد](/powershell/module/exchange/start-mailboxsearch)

  - [إيقاف علب البريد](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > ستتوفر أوامر [cmdlets Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) وDes-MailboxSearch بعد إيقاف cmdlets الأخرى ***-MailboxSearch*** حتى تتمكن من استخدامها للمساعدة في الانتقال إلى أدوات eDiscovery والاحتفاظ الأخرى.[](/powershell/module/exchange/remove-mailboxsearch) ومع ذلك، بعد تاريخ معين (مذكور أدناه) لن يدعم دعم Microsoft هذين cmdlets.

- أمر cmdlet [الخاص ب Search-Mailbox](/powershell/module/exchange/search-mailbox) في Exchange Online PowerShell.

- العمليات التالية في واجهة برمجة تطبيقات Exchange Web Services:

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Microsoft Purview eDiscovery (Premium) الإصدار 1.0](./overview-ediscovery-20.md)، وهو الإصدار الأول من eDiscovery (Premium) الذي يتم الوصول إليه من خلال حالة Microsoft Purview eDiscovery (Standard) في مدخل التوافق. لا يؤثر إيقاف eDiscovery (Premium) الإصدار 1.0 على قدرتك على إنشاء حالات eDiscovery (القياسية) وإدارتها.

> [!NOTE]
> تنطبق وظيفة eDiscovery التي يتم إيقافها فقط على الإصدارات المستندة إلى السحابة من Microsoft 365 Office 365. ستظل وظائف eDiscovery في الإصدارات المحلية من Exchange SharePoint مدعومة حتى إشعار آخر.

توفر الأقسام التالية في هذه المقالة إرشادات حول إيقاف كل ميزة. تتضمن هذه المعلومات المخططات الزمنية والأدوات البديلة التي يمكنك استخدامها بدلا من الأداة التي تم إيقافها.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place eDiscovery و"In-Place Holds" في مركز إدارة Exchange 

وفقا للإعلان الأصلي في 1 يوليو 2017، يتم إيقاف وظيفة In-Place eDiscovery & Hold في مركز إدارة Exchange (EAC). سمحت لك صفحة & & eDiscovery In-Place في EAC بالبحث عن المحتوى من Exchange Online والاحتفاظ به وتصديره. يتيح لك In-Place eDiscovery أيضا نسخ نتائج البحث إلى علبة بريد اكتشاف حتى تتمكن أنت أو مديرو eDiscovery الآخرون من مراجعة المحتوى وإتاحته للطلبات القانونية والتنظيمية والعامة.

نظرا لأن كل هذه الإمكانات (باستثناء نسخ نتائج البحث إلى علبة بريد اكتشاف) متوفرة الآن في أدوات البحث في المحتوى، وأدوات eDiscovery وeDiscovery (Premium) في [مدخل التوافق](./microsoft-365-compliance-center.md) (مع تحسين الوظائف والموثوقية والدعم لمجموعة واسعة من خدمات Microsoft 365)، نوصي بالبدء في استخدام هذه الأدوات في أقرب وقت ممكن. لمساعدتك في الانتقال إلى أدوات eDiscovery الأخرى هذه، يسرد الجدول أدناه الأدوات التي يمكنك استخدامها بدلا من In-Place eDiscovery و In-Place e Hold.

### <a name="scope-of-affected-organizations"></a>نطاق المنظمات المتأثرة

- المؤسسات Office 365 Microsoft 365 Enterprise

- المؤسسات Office 365 Microsoft 365 Education

- Office 365 والمنظمات الحكومية Microsoft 365؛ يشمل ذلك سحابة القطاع الحكومي سحابة القطاع الحكومي High و DoD

- Office 365 ألمانيا

### <a name="timeline-for-retirement"></a>مخطط زمني للتقاعد

- 1 يوليو 2020: لن تتمكن من إنشاء عمليات بحث وعمليات احتجاز جديدة، ولكن لا يزال بإمكانك تشغيل عمليات البحث الموجودة وتحريرها وحذفها على مسؤوليتك الخاصة. لن In-Place دعم Microsoft بعد الآن & eDiscovery في EAC.

- 1 أكتوبر 2020: سيتم وضع وظيفة & eDiscovery & In-Place في EAC في وضع القراءة فقط. وهذا يعني أنك ستتمكن فقط من إزالة عمليات البحث و قوائم الاحتجاز الموجودة.

### <a name="alternative-tools"></a>أدوات بديلة

يصف الجدول التالي الأدوات الأخرى التي يمكنك استخدامها لاستبدال الوظائف الموجودة التي يتم إيقافها.

<table>
<thead>
<tr class="header">
<th>وظيفه</th>
<th>أداة بديلة</th>
<th>تعليقات</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>البحث والتصدير باستمرار لأغراض قانونية</td>
<td>حالات eDiscovery (قياسي) في مدخل التوافق </td>
<td><p>يوفر استخدام قدرات حالات eDiscovery الأساسية التماثل الوظيفي In-Place eDiscovery و In-Place e Holds. يتضمن ذلك ما يلي:</p>
<ul>
<li>
<p>توسيع نطاق البحث لملايين المواقع</p>
</li>
<li>
<p>موثوقية أعلى للبحث عن المحتوى وتصديره ووضعه قيد الاحتجاز</p>
</li>
<li>
<p>البحث عن محتوى في Exchange Online أو SharePoint Online أو OneDrive for Business أو Skype for Business أو Microsoft Teams أو مجموعات Yammer أو مجموعات Microsoft 365 ، ومحتوى آخر مخزن في تطبيقات Office 365</p></li></ul>
</td>
</tr>
<tr class="even">
<td>الاحتجاز لأغراض الاستبقاء</td>
<td>نهج الاستبقاء في مدخل التوافق</td>
<td><p>يمكنك استخدام نهج الاستبقاء للاحتفاظ بالمحتوى، وإذا رغبت في ذلك، فاحذفه بعد انتهاء فترة الاستبقاء. وتشمل القدرات الأخرى ما يلي:</p>
<ul>
<li>
<p>تطبيق النهج على مؤسستك بأكملها </p>
</li><li>
<p>تطبيق النهج على مواقع محتوى معينة مثل مجموعات Exchange Online و SharePoint Online و OneDrive for Business و Skype for Business و Microsoft Teams و Office 365</p></li>
<li>
<p>تطبيق النهج على مستخدمين محددين</p></li></ul>
<p>لمزيد من المعلومات، راجع <a href="/microsoft-365/compliance/retention-policies"> التعرف على نهج الاستبقاء وتسميات الاستبقاء</a>.</td>
</tr>
<tr class="odd">
<td>نسخ نتائج البحث في البريد الإلكتروني إلى علبة بريد اكتشاف لمراجعتها</td><td>مجموعات المراجعة في eDiscovery (Premium) v2.0</td>
<td><p>لم تكن مراجعة المحتوى في Microsoft 365 أسهل من أي وقت مضى. مجموعات المراجعة لديها العديد من القدرات الرائعة للمساعدة في تقليل مقدار الوقت والبيانات اللازمة للمراجعة، بما في ذلك:</p>
<ul>
<li><p>تنفيذ استعلامات البحث السريعة وتصفية المحتوى في مجموعة مراجعة</p></li>
<li><p>تحليل المحتوى في مجموعة مراجعة؛ وهذا يشمل مؤشر ترابط البريد الإلكتروني، والكشف شبه المتكرر، وتحليل النسق، والترميز التنبؤي</p></li>
<li><p>وضع علامة على المستندات في مجموعة مراجعة</p></li>
<li><p>اقتراحات وضع العلامات للمساعدة في تحديد محتوى امتياز العميل للمحامي</p></li></ul>
<p>لمزيد من المعلومات، راجع <a href="/microsoft-365/compliance/overview-ediscovery-20">نظرة عامة على حل eDiscovery (Premium) في Microsoft 365</a>.</p>
<p>
<p>بدلا من ذلك، يمكنك تصدير نتائج البحث إلى ملفات PST ثم استخدام Microsoft 365 Import service لاستيراد PSTs إلى علبة بريد اكتشاف. للحصول على إرشادات مفصلة خطوة بخطوة، راجع <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">استخدام تحميل الشبكة لاستيراد ملفات PST إلى Office 365</a>.
</tr>
<tr class=even>
  <td>نسخ الرسائل من علبة بريد واحدة إلى علبة بريد أخرى</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">تعيين أذونات إلى علبة بريد</a></td>
  <td>لمنح شخص حق الوصول إلى البريد الإلكتروني لمستخدم آخر (على سبيل المثال، عندما يغادر موظف مؤسستك وتحتاج إلى منح شخص آخر حق الوصول إلى البريد الإلكتروني للموظف السابق)، نوصي بتعيين أذونات هذا الشخص للوصول إلى علبة بريد الموظف السابق. لذا بدلا من نسخ عناصر علبة البريد إلى علبة بريد مستخدم أخرى أو علبة بريد مشتركة، ما عليك سوى تعيين الأذونات اللازمة للوصول إلى علبة البريد المصدر.</td>
  
  </tr>
<tr class="odd">
<td>استعادة العناصر من مجلد العناصر القابلة للاسترداد</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>يمكنك استعادة العناصر المحذوفة بشكل دائم (المعروفة أيضا بالعناصر <i>المحذوفة مبدئيا</i> ) في علب البريد، طالما أن فترة الاحتفاظ بالعنصر المحذوفة لعنصر ما لم تنته صلاحيتها. لمزيد من المعلومات، راجع <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">مجلد العناصر القابلة للاسترداد في Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>الأسئلة المتداولة حول In-Place eDiscovery و In-Place e Holds

**استخدم وظيفة نسخ نتائج البحث في In-Place eDiscovery &"Holds" في EAC لنسخ نتائج البحث إلى علبة بريد اكتشاف لمراجعتها من قبل الوكلاء. ما هي الخيارات المتوفرة لدي الآن؟**

هناك طريقتان لنسخ هذه الوظيفة اليوم. الأول هو استخدام [مجموعات المراجعة في eDiscovery (Premium) v2.0](./view-documents-in-review-set.md). تتمتع مجموعات المراجعة بالعديد من الإمكانات نفسها التي تراها في أداة مراجعة تقليدية مثل البحث السريع عن المستندات ووضع العلامات ومؤشرات ترابط البريد الإلكتروني والتجميع شبه المكرر وتحليل النسق والترميز التنبؤي. إذا كنت لا تزال ترغب في استخدام علب بريد الاكتشاف للمراجعة، فإن الخيار الثاني هو تصدير نتائج البحث إلى ملفات PST ثم استيراد ملفات PST إلى علبة بريد اكتشاف باستخدام [ميزة استيراد PST](use-network-upload-to-import-pst-files.md) في مركز توافق Microsoft.

**كيف أعمل التحكم في مواقع المحتويات (مثل علب البريد أو المواقع) التي يمكن لمدير eDiscovery البحث فيها باستخدام الأدوات الجديدة؟**

يستخدم مدخل التوافق أيضا [حدود التوافق](set-up-compliance-boundaries.md) للتحكم في مواقع المحتوى التي يمكن لمدير eDiscovery البحث فيها. حدود الامتثال مفيدة في الكيانات الحكومية التي تحتاج إلى البقاء داخل حدود الوكالات أو الشركات متعددة الجنسيات المطلوبة لاحترام الجهات المحلية الجغرافية.

**كيف يمكنني نقل عمليات البحث والحتفظ الحالية إلى مدخل توافق Microsoft Purview؟**

من الممكن ترحيل In-Place eDiscovery عمليات البحث والحمل من EAC باستخدام PowerShell. للحصول على الإرشادات، راجع [ترحيل عمليات البحث وأوامر الاحتجاز من EAC إلى مدخل التوافق](./migrate-legacy-ediscovery-searches-and-holds.md).

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch cmdlets

وفقا للإشعار الأصلي الذي تم الإعلان عنه في 1 يوليو 2017 في مركز إدارة Exchange، يتم إيقاف وظيفة In-Place eDiscovery & Hold وcmdlets **-MailboxSearch المطابقة\***. توفر أوامر cmdlets هذه للمستخدمين القدرة على البحث عن محتوى علبة البريد باستمرار وتصديره للطلبات القانونية والتنظيمية والعامة.

نظرا لأن هذه الإمكانات متوفرة الآن في [<span class="underline">مدخل التوافق</span>](./microsoft-365-compliance-center.md) Office 365 Security & Compliance Center PowerShell مع تحسين الأداء وقابلية التوسع، يجب عليك استخدام أوامر cmdlet المحسنة هذه. تتضمن [<span class="underline">\*</span>](/powershell/module/exchange/get-compliancecase)أوامر cmdlets هذه -ComplianceCase [<span class="underline">و-ComplianceSearch\*</span>](/powershell/module/exchange/get-compliancesearch) [<span class="underline">و-CaseHoldPolicy\*</span>](/powershell/module/exchange/get-caseholdpolicy) [<span class="underline">و-CaseHoldRule\*</span>](/powershell/module/exchange/get-caseholdrule) [<span class="underline">و-ComplianceSearchAction\*</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>نطاق المنظمات المتأثرة

- المؤسسات Office 365 Microsoft 365 Enterprise

- المؤسسات Office 365 Microsoft 365 Education

- Office 365 والمنظمات الحكومية Microsoft 365؛ يشمل ذلك سحابة القطاع الحكومي سحابة القطاع الحكومي High و DoD

- Office 365 ألمانيا

### <a name="timeline"></a>المخطط الزمني

- 1 يوليو 2020: لن تتمكن من استخدام **New-MailboxSearch** لإنشاء عمليات بحث جديدة In-Place eDiscovery وعمليات In-Place Holds، ولكن لا يزال بإمكانك استخدام أوامر cmdlets لتشغيل عمليات البحث والملاحظات الموجودة وتحريرها وحذفها على مسؤوليتك الخاصة. لن يقدم دعم Microsoft بعد الآن المساعدة لهذه الأنواع من عمليات البحث وقوائم الاحتجاز.

- 1 أكتوبر 2020: كما ذكر سابقا، سيتم وضع وظيفة In-Place eDiscovery & Holds في EAC في وضع القراءة فقط. وهذا يعني أيضا أنك لن تتمكن من استخدام **New-MailboxSearch** أو **Start-MailboxSearch** أو **Set-MailboxSearch** cmdlets. ستتمكن فقط من الحصول على عمليات البحث وعمليات الاحتجاز الموجودة وإزالتها.

### <a name="alternative-tools"></a>أدوات بديلة

يصف الجدول التالي الأدوات الأخرى التي يمكنك استخدامها لاستبدال الوظائف الموجودة التي يتم إيقافها.

<table>
<thead>
<tr class="header">
<th>وظيفه</th>
<th>أدوات بديلة</th>
<th>تعليقات</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>البحث والتصدير</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>تعمل cmdlets ComplianceSearch و ComplianceSearchAction معا لمساعدتك في البحث عن المحتوى وتصديره. يمكنك إنشاء بحث جديد وعرض تقدير البحث باستخدام أوامر cmdlets <strong>New-</strong>, <strong>Get-</strong>, and <strong>Start-ComplianceSearch</strong> . ثم يمكنك استخدام <strong>New-ComplianceSearchAction</strong> cmdlet لتصدير نتائج البحث. سيظل عليك استخدام أداة eDiscovery الأساسية في مدخل التوافق لتنزيل نتائج البحث هذه إلى الكمبيوتر المحلي.</p>
<p>
<p><strong>ملاحظه:</strong> إذا كنت تستخدم أوامر cmdlet لإنشاء عمليات بحث غير مقترنة بحالة eDiscovery أساسية، فسيتم وضع عمليات البحث هذه على صفحة <strong>البحث في المحتوى</strong> في مدخل التوافق.</p></td>
</tr>
<tr class="even">
<td>الاحتفاظ بالمحتوى في علبة بريد</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>يجب أن تكون قوائم الاحتجاز في مدخل التوافق مقترنة ب ComplianceCase. أولا، أنشئ حالة الامتثال، ثم أنشئ CaseHoldPolicy و CaseHoldRule.</p>
<p><strong>ملاحظه:</strong> سيؤدي إنشاء CaseHoldPolicy دون إنشاء CaseHoldRule إلى جعل قائمة الاحتجاز غير قابلة للتشغيل حتى يتم إنشاء CaseHoldRule وإقرانه ب CaseHoldPolicy. راجع وثائق cmdlet لمزيد من المعلومات.</p></td>
</tr>
<tr class="odd">
<td>نسخ نتائج البحث إلى علبة بريد اكتشاف</td>
<td>None</td>
<td>لا يوجد استبدال مباشر لهذه الوظيفة لأنها لا توفر الوصول إلى جميع خدمات Microsoft 365. راجع الأسئلة المتداولة التالية أدناه للحصول على حلول بديلة.</td>
</tr>
  <tr class=even>
  <td>نسخ الرسائل من علبة بريد واحدة إلى علبة بريد أخرى</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">تعيين أذونات إلى علبة بريد</a></td>
  <td>لمنح شخص حق الوصول إلى البريد الإلكتروني لمستخدم آخر (على سبيل المثال، عندما يغادر موظف مؤسستك وتحتاج إلى منح شخص آخر حق الوصول إلى البريد الإلكتروني للموظف السابق)، نوصي بتعيين أذونات هذا الشخص للوصول إلى علبة بريد الموظف السابق. لذا بدلا من نسخ عناصر علبة البريد إلى علبة بريد مستخدم أخرى أو علبة بريد مشتركة، ما عليك سوى تعيين أذونات المستخدم للوصول إلى علبة البريد المصدر.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>الأسئلة المتداولة حول ***-MailboxSearch** cmdlets

**نستخدم "نسخ البحث" لتصدير رسائل البريد الإلكتروني أو الرسائل الفورية لأغراض تتعلق ب eDiscovery والتحقيقات القانونية الأخرى. ما هي الخيارات الأخرى التي لدينا بعد إيقاف أوامر cmdlets هذه؟**

توفر [<span class="underline">واجهات برمجة تطبيقات Microsoft Graph</span>](https://developer.microsoft.com/en-us/graph) عددا من الأساليب لاستخراج البيانات للتحليل وأغراض أخرى أكثر مرونة وقابلية للتطوير من استخدام **\*cmdlets -MailboxSearch**.

**كيف يمكنني ترحيل عمليات البحث و قوائم الاحتجاز إلى مدخل التوافق؟**

من الممكن ترحيل In-Place eDiscovery عمليات البحث و الاحتجاز من مركز إدارة Exchange باستخدام برنامج نصي PowerShell. لمزيد من المعلومات، راجع [ترحيل عمليات بحث eDiscovery القديمة وحتفظ بها في مدخل التوافق](migrate-legacy-eDiscovery-searches-and-holds.md).

**بعد إيقاف أوامر cmdlets، هل سأظل قادرا على إزالة عمليات البحث أو استردادها؟**

نعم، على الرغم من أننا نزيل القدرة على إنشاء عمليات البحث وتعديلها، ستظل قادرا **على استخدام Get-MailboxSearch** و **Remove-MailboxSearch** حتى إشعار آخر. ومع ذلك، سيكون استخدام أوامر cmdlets هذه على مسؤوليتك الخاصة بعد تواريخ التقاعد ولن يتمكن دعم Microsoft من تقديم المساعدة.

## <a name="search-mailbox-cmdlet"></a>Search-Mailbox cmdlet

يتم إيقاف أمر cmdlet **الخاص ب Search-Mailbox** في Exchange Online PowerShell كما تم الإعلان عنه في الأصل في تحذير في إخراج cmdlet بدءا من عام 2018. تم استخدام أمر cmdlet الخاص **ب Search-Mailbox** في الأصل للبحث في علبة بريد المستخدم وإزالة المحتوى الضار. نوصي بالبدء في استخدام **New-ComplianceSearch** و **New-ComplianceSearchAction** cmdlets في Office 365 Security & Compliance Center PowerShell للبحث عن المحتوى وإزالة المحتوى. للحصول على تجربة أمان مضمنة، توفر [<span class="underline">ميزات الأمان Microsoft 365</span>](../security/index.yml) حماية قوية من التهديدات للبريد الإلكتروني والعديد من خدمات Microsoft الأخرى.

### <a name="scope-of-affected-organizations"></a>نطاق المنظمات المتأثرة

- المؤسسات Office 365 Microsoft 365 Enterprise

- المؤسسات Office 365 Microsoft 365 Education

- Office 365 والمنظمات الحكومية Microsoft 365؛ يشمل ذلك سحابة القطاع الحكومي سحابة القطاع الحكومي High و DoD

- Office 365 ألمانيا

### <a name="timeline"></a>المخطط الزمني

-  1 يوليو 2020: لن يعود أمر cmdlet الخاص **بعلبة بريد البحث** متوفرا ولن يقدم دعم Microsoft المساعدة بعد الآن.

### <a name="alternative-tools"></a>أدوات بديلة

يصف الجدول التالي الأدوات الأخرى التي يمكنك استخدامها لاستبدال الوظائف الموجودة التي يتم إيقافها.

<table>
<thead>
<tr class="header">
<th>وظيفه</th>
<th>أدوات بديلة</th>
<th>تعليقات</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>البحث في علبة بريد</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>تعمل cmdlets ComplianceSearch و ComplianceSearchAction معا لمساعدتك في البحث عن المحتوى وتصديره. يمكنك إنشاء بحث جديد وعرض تقدير البحث باستخدام أوامر cmdlets <strong>New-</strong>, <strong>Get-</strong>, and <strong>Start-ComplianceSearch</strong> . ثم يمكنك استخدام الأمر <strong>New-ComplianceSearchAction -Export</strong> لتصدير نتائج البحث. سيظل عليك استخدام أداة eDiscovery الأساسية في مدخل التوافق لتنزيل نتائج البحث هذه إلى الكمبيوتر المحلي.</p></p>
</td>
</tr>
<tr class="even">
<td>حذف البريد الإلكتروني المجمع من علبة بريد</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">إعداد نهج الأرشفة والحذف لعلب البريد</span></a></p>
<p></p></td>
<td><p>يمكن للمسؤولين إنشاء نهج أرشفة وحذف ينقل العناصر تلقائيا إلى علبة بريد الأرشيف الخاصة بالمستخدم ويحذف العناصر تلقائيا من علبة البريد.</p>
</td>
</tr>
<tr class="even">
<td>نسخ نتائج البحث إلى علبة بريد اكتشاف</td>
<td> </td>
<td>لا يوجد استبدال مباشر لهذه الوظيفة لأنها لا توفر الوصول إلى جميع خدمات Microsoft 365. راجع الأسئلة المتداولة في القسم <strong>*-MailboxSearch cmdlets</strong> للحصول على حلول بديلة. </td>
</tr>
<tr class=odd>
  <td>نسخ الرسائل من علبة بريد واحدة إلى علبة بريد أخرى</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">تعيين أذونات إلى علبة بريد</a></td>
  <td>لمنح شخص حق الوصول إلى البريد الإلكتروني لمستخدم آخر (على سبيل المثال، عندما يغادر موظف مؤسستك وتحتاج إلى منح شخص آخر حق الوصول إلى البريد الإلكتروني للموظف السابق)، نوصي بتعيين أذونات هذا الشخص للوصول إلى علبة بريد الموظف السابق. لذا بدلا من نسخ عناصر علبة البريد إلى علبة بريد مستخدم أخرى أو علبة بريد مشتركة، ما عليك سوى تعيين إذن مستخدم للوصول إلى علبة البريد المصدر.</td>
</tr>
<tr class=even>
  <td>إزالة الرسائل من علبة بريد</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>تعمل cmdlets ComplianceSearch و ComplianceSearchAction معا لمساعدتك في البحث عن المحتوى وإزالة المحتوى. يمكنك إنشاء بحث وتشغيله باستخدام <strong>New-ComplianceSearch</strong> و <strong>New-ComplianceSearch</strong> cmdlets، ثم يمكنك إزالة المحتوى باستخدام الأمر <strong>New-ComplianceSearchAction -Purge -PurgeType</strong> . لمزيد من المعلومات، راجع <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">البحث عن الرسائل وحذفها</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>إزالة الرسائل من علبة بريد</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">تعيين أذونات إلى علبة بريد</a></td>
<td>لإزالة الرسائل من علبة بريد، قم بتعيين أذونات المسؤول للوصول إلى علبة بريد الموظف. يمكن حذف الرسائل وإعادة تدويرها حسب الحاجة للاستفادة من إمكانيات البحث وعرض المضمنة في Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>عمليات واجهة برمجة تطبيقات Exchange Web Services

يتم استخدام هذه العمليات في واجهة برمجة تطبيقات Exchange Web Services بواسطة ميزة & eDiscovery In-Place في مركز إدارة Exchange وcmdlets **-MailboxSearch المطابقة\*** في Exchange Online PowerShell. كما سيتم إيقافها كجزء من إيقاف أدوات eDiscovery القديمة الأخرى.

### <a name="scope-of-affected-organizations"></a>نطاق المنظمات المتأثرة

- المؤسسات Office 365 Microsoft 365 Enterprise

- المؤسسات Office 365 Microsoft 365 Education

- Office 365 والمنظمات الحكومية Microsoft 365؛ يشمل ذلك سحابة القطاع الحكومي سحابة القطاع الحكومي High و DoD

- Office 365 ألمانيا

### <a name="timeline"></a>المخطط الزمني

- 1 يوليو 2020: لن تكون عمليات GetSearchableMailboxes و SearchMailboxes و SetHoldOnMailboxes و GetHoldOnMailboxes متوفرة بعد الآن، ولن يقدم دعم Microsoft المساعدة بعد الآن.

## <a name="ediscovery-premium-v10"></a>eDiscovery (Premium) الإصدار 1.0

eDiscovery (Premium) v1.0, which is the version of eDiscovery (Premium) available in a core eDiscovery case by clicking **Switch to eDiscovery (Premium)**, is being retired. تم استبدال وظائفه بحل [eDiscovery الجديد (Premium)](./ediscovery.md) في مدخل التوافق.

لتحديد ما إذا كانت مؤسستك تستخدم eDiscovery (Premium) الإصدار 1.0:

1. انتقل إلى مدخل التوافق، وحدد **eDiscoveryCore** > ، وافتح حالة eDiscovery (قياسي).<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

1. إذا رأيت زر **التبديل إلى eDiscovery (Premium**)، فسينقلك النقر فوقه إلى الإصدار 1.0 من eDiscovery (Premium)، الذي يتم إيقافه. لن تتأثر القدرة على إنشاء الحالات وإدارتها في eDiscovery (قياسي). يتم إيقاف القدرة على إضافة بيانات الحالة وتحليلها فقط في eDiscovery (Premium) الإصدار 1.0 (بالنقر فوق **التبديل إلى eDiscovery (Premium)**).

يوفر حل eDiscovery الجديد (Premium) في Microsoft 365 (المعروف أيضا باسم *eDiscovery (Premium) الإصدار 2.0*) جميع إمكانيات الحل الأصلي، ولكنه يتضمن الآن نهجا يستند إلى الوصي لتحديد المحتوى في Microsoft 365 أخرى  الخدمات، وجمع هذا المحتوى، ثم إضافته إلى مجموعة مراجعة حيث يمكن للمراجعين الاستفادة من استعلامات البحث السريعة ووضع العلامات وميزات التحليلات للمساعدة في احصاء المستندات ذات الصلة. يتضمن eDiscovery (Premium) الآن المعالجة المحسنة والعارضين الأصليين لكل من أنواع الملفات من Microsoft وغير التابعة ل Microsoft، وقائمة كاملة بأنواع الملفات [موجودة هنا](./supported-filetypes-ediscovery20.md) وحقول بيانات التعريف المعتمدة [موجودة هنا](./document-metadata-fields-in-advanced-ediscovery.md). بالإضافة إلى ذلك، يوفر حل eDiscovery الجديد (Premium) ميزة إدارة احتجاز الوصي القوية التي تتيح لك تطبيق قوائم الاحتجاز على المحتوى في خدمات مختلفة، وإعلام المستخدمين بالموقوفين، وتتبع استجابات الوصي، كل ذلك ضمن حالة eDiscovery (Premium).

للوصول إلى eDiscovery (Premium) v2.0:

انتقل إلى مدخل التوافق، وحدد **eDiscoveryAdvanced** > ، <a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank">**وافتح**</a> حالة eDiscovery (قياسي).

في هذا الوقت، نوصي بالبدء في نقل سير عمل eDiscovery إلى وظيفة eDiscovery الجديدة (Premium). إذا لزم الأمر، يمكنك أرشفة eDiscovery (Premium) 1.0 حالة عن طريق تصدير المحتوى وتخزينه دون اتصال. على الرغم من أنه سيظل بإمكانك الوصول إلى الإصدار 1.0 من eDiscovery (Premium) في الحالات الحالية حتى 31 ديسمبر 2020، إلا أن دعم Microsoft لن يوفر الدعم بعد 1 أكتوبر 2020. راجع المخطط الزمني التالي للحصول على مزيد من التفاصيل.

### <a name="scope-of-affected-organizations"></a>نطاق المنظمات المتأثرة

- المؤسسات Office 365 Microsoft 365 Enterprise

- المؤسسات Office 365 Microsoft 365 Education

- Office 365 والمنظمات الحكومية Microsoft 365؛ يشمل ذلك سحابة القطاع الحكومي سحابة القطاع الحكومي High و DoD

- Office 365 ألمانيا

### <a name="timeline"></a>المخطط الزمني

- 1 يوليو 2020: لن تتمكن من إنشاء حالات eDiscovery جديدة (Premium) الإصدار 1.0.

- 1 أكتوبر 2020: لن تتمكن من إضافة بيانات جديدة (إعداد نتائج البحث ل eDiscovery (Premium)) إلى أي حالات. ستتمكن من متابعة العمل مع البيانات في الحالات الحالية على مسؤوليتك الخاصة. لن يقدم دعم Microsoft المساعدة بعد الآن. 

- 31 ديسمبر 2020: لن تتمكن من الوصول إلى حالات eDiscovery (Premium) الإصدار 1.0.

### <a name="alternative-tools"></a>أدوات بديلة

[حل eDiscovery (Premium)](./overview-ediscovery-20.md) في مدخل التوافق.
