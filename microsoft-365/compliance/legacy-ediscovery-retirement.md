---
title: تقاعد أدوات eDiscovery القديمة
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
description: In-Place eDiscovery In-Place Hold (و PowerShell cmdlets المطابقة) في Exchange Online في النصف الأول من عام 2020. يتم Search-Mailbox cmdlet Advanced eDiscovery v1.0 أيضا خلال الفترة الزمنية نفسها.
ms.openlocfilehash: f778a31580bb908205c707c1f613f49bd6a576d1
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/04/2021
ms.locfileid: "63566586"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>تقاعد أدوات eDiscovery القديمة

> [!IMPORTANT]
> تمت إزالة وظائف أدوات eDiscovery القديمة الموضحة في هذه المقالة من خدمة Microsoft 365 أو ما زالت متوفرة، ولكن لم تعد معتمدة. قد تتم إزالة أي وظائف لا تزال متوفرة دون إشعار. إذا كنت لا تزال تستخدم أي من هذه الأدوات القديمة، فنظر في عملية البحث عن أدوات eDiscovery في مركز التوافق في Microsoft 365 أو أحد البدائل الموضحة في هذه المقالة.

على مر السنين، وفرت Microsoft أدوات eDiscovery التي تسمح لك بالبحث عن محتوى البريد الإلكتروني ومعاينته وتصديره من Exchange Online. ومع ذلك، لم تعد هذه الأدوات توفر طريقة فعالة للبحث عن محتوى غير Exchange في خدمات Microsoft 365 أخرى، مثل SharePoint عبر الإنترنت Microsoft 365 المجموعات. لمعالجة هذا الأمر، تقدم Microsoft أدوات eDiscovery أخرى تساعدك في البحث عن مجموعة واسعة من Microsoft 365 المحتويات. وقد كنا نعمل بجد لتضمين وظائف eDiscovery الأكثر اتنانا وقوي في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365.</a> يسمح هذا الأمر ل المؤسسات بالاستجابة لطلبات المستندات القانونية والداخلية والمستندات الأخرى للمحتوى عبر العديد من Microsoft 365، بما في ذلك Exchange Online.

نتيجة لوظائف eDiscovery الجديدة والمحسنة هذه في مركز التوافق في Microsoft 365، نقوم بالتقاعد عن الميزات والوظائف التالية ذات الصلة ب eDiscovery المرتبطة بالبحث عن محتوى البريد الإلكتروني في Exchange Online Microsoft 365:

- [يتم وضع eDiscovery و](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)"[](/exchange/security-and-compliance/create-or-remove-in-place-holds)في مكان" في Exchange الإدارة.

- يتم Exchange Online Cmdlets في PowerShell التي تدعم In-Place eDiscovery وeDiscovery In-Place (يتم تعريف هذه cmdlets بشكل جماعي على أنها cmdlets **-MailboxSearch*). يشمل ذلك cmdlets التالية:

  - [البحث عن علبة بريد جديدة](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > سيتم توفير الأمرين Cmdlets [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) و [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) بعد ***-MailboxSearch**** cmdlets الأخرى بحيث يمكنك استخدامها للمساعدة في الانتقال إلى أدوات eDiscovery أخرى مع الاستمرار. ومع ذلك، بعد تاريخ معين (مرد أدناه) لن يدعم دعم Microsoft الأمرين cmdlets.

- الأمر [cmdlet "البحث في علبة](/powershell/module/exchange/search-mailbox) البريد" Exchange Online PowerShell.

- العمليات التالية في Exchange API لخدمات الويب:

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [eDiscovery المتقدم في Office 365 الإصدار 1.0](./overview-ediscovery-20.md)، وهو الإصدار الأول من Advanced eDiscovery التي يمكن الوصول إليها من خلال حالة eDiscovery الأساسية في مركز التوافق في Microsoft 365. لا يؤثر Advanced eDiscovery v1.0 على قدرتك على إنشاء حالات eDiscovery الأساسية وإدارتها.

> [!NOTE]
> تنطبق وظيفة eDiscovery التي يتم سحبها فقط على الإصدارات المستندة إلى السحابة من Microsoft 365 Office 365. ستبقى وظائف eDiscovery في الإصدارات Exchange و SharePoint معتمدة حتى إشعار آخر.

توفر الأقسام التالية في هذه المقالة إرشادات حول كل ميزة يتم اقالتها. تتضمن هذه المعلومات المخططات الزمنية والأدوات البديلة التي يمكنك استخدامها بدلا من الأداة المعتزلة.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place eDiscovery In-Place في مركز إدارة Exchange 

وفقا للإعلان الأصلي في 1 يوليو 2017، يتم الآن In-Place eDiscovery & وظيفة الاستمرار في مركز إدارة Exchange (EAC). تتيح In-Place eDiscovery & في EAC البحث عن المحتوى من Exchange Online مع الاستمرار وتصديره. In-Place eDiscovery أيضا نسخ نتائج البحث إلى علبة بريد اكتشاف بحيث يمكنك أنت أو مدراء eDiscovery الآخرين مراجعة المحتوى وجعله متوفرا للطلبات القانونية والتنظيمية والعامة.

نظرا لأن كل هذه الإمكانات (باستثناء نسخ نتائج البحث إلى علبة بريد اكتشاف) متوفرة الآن في أدوات البحث في المحتوى و eDiscovery و Advanced eDiscovery في [مركز التوافق في Microsoft 365](./microsoft-365-compliance-center.md) (مع وظائف ووثوقية ودعم محسنة لمجموعة واسعة من Microsoft 365  الخدمات)، نوصيك ببدء استخدام هذه الأدوات في أسرع وقت ممكن. لمساعدتك في الانتقال إلى أدوات eDiscovery الأخرى هذه، يسرد الجدول أدناه الأدوات التي يمكنك استخدامها بدلا من In-Place eDiscovery In-Place Hold.

### <a name="scope-of-affected-organizations"></a>نطاق المؤسسات المتأثرة

- Office 365 Microsoft 365 Enterprise المؤسسات

- Office 365 Microsoft 365 Education المؤسسات

- Office 365 Microsoft 365 الحكومية؛ يشمل ذلك سحابة القطاع الحكومي وd doD سحابة القطاع الحكومي وD DOD

- Office 365 ألمانيا

### <a name="timeline-for-retirement"></a>مخطط زمني للتقاعد

- 1 يوليو 2020: لن تتمكن من إنشاء عمليات بحث وعمليات حفظ جديدة، ولكن لا يزال بإمكانك تشغيل عمليات البحث الموجودة وتحريرها وحذفها على حسابك الخاص. لن يعود دعم Microsoft In-Place eDiscovery & في EAC.

- 1 أكتوبر 2020: سيتم وضع وظيفة In-Place eDiscovery & Holds في EAC في وضع القراءة فقط. وهذا يعني أنك لن تتمكن إلا من إزالة عمليات البحث والمواضع المحتجزة الموجودة.

### <a name="alternative-tools"></a>الأدوات البديلة

يصف الجدول التالي الأدوات الأخرى التي يمكنك استخدامها لاستبدال الوظائف الموجودة التي يتم إعفاها.

<table>
<thead>
<tr class="header">
<th>الوظائف</th>
<th>أداة بديلة</th>
<th>التعليقات</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>البحث والتصدير والمسك لأغراض قانونية</td>
<td>حالات eDiscovery الأساسية في مركز التوافق في Microsoft 365 </td>
<td><p>يوفر استخدام قدرات حالات eDiscovery الأساسية الاتقاء الوظيفي In-Place eDiscovery In-Place المواقد. يشمل ذلك ما يلي:</p>
<ul>
<li>
<p>مقياس البحث لملايين المواقع</p>
</li>
<li>
<p>وثوقية أعلى للبحث عن المحتوى وتصديره ووضعه في وضع الانتظار</p>
</li>
<li>
<p>البحث عن محتوى في Exchange Online أو SharePoint عبر الإنترنت أو OneDrive for Business أو Skype for Business أو Microsoft Teams أو Yammer أو Microsoft 365  المجموعات والمحتوى الآخر المخزن في تطبيقات Office 365</p></li></ul>
</td>
</tr>
<tr class="even">
<td>الاستمرار لأغراض الاستبقاء</td>
<td>سياسات الاستبقاء في مركز التوافق في Microsoft 365</td>
<td><p>يمكنك استخدام سياسات الاستبقاء للاحتفاظ بالمحتوى، وحذفه بعد انتهاء فترة الاستبقاء، إذا أردت ذلك. تتضمن الإمكانات الأخرى:</p>
<ul>
<li>
<p>تطبيق سياسات على مؤسستك بكاملها </p>
</li><li>
<p>تطبيق سياسات على مواقع محتوى محددة مثل Exchange Online و SharePoint عبر الإنترنت و OneDrive for Business و Skype for Business و Microsoft Teams و Office 365 المجموعات</p></li>
<li>
<p>تطبيق سياسات على مستخدمين محددين</p></li></ul>
<p>لمزيد من المعلومات، راجع <a href="/microsoft-365/compliance/retention-policies"> التعرف على سياسات الاستبقاء وتسميات الاستبقاء</a>.</td>
</tr>
<tr class="odd">
<td>نسخ نتائج البحث في البريد الإلكتروني إلى علبة بريد الاكتشاف لمراجعتها</td><td>مراجعة المجموعات في Advanced eDiscovery v2.0</td>
<td><p>لم تكن مراجعة المحتوى Microsoft 365 أسهل من أي وقت. تتضمن مجموعات المراجعة العديد من الإمكانات الكبيرة للمساعدة على تقليل مقدار الوقت والبيانات المطلوبة للمراجعة، بما في ذلك:</p>
<ul>
<li><p>تنفيذ استعلامات بحث سريعة وتصفية المحتوى في مجموعة مراجعة</p></li>
<li><p>تحليل المحتوى في مجموعة مراجعة؛ يشمل ذلك ترابط البريد الإلكتروني، والاكتشاف شبه المتكرر، وتحليل المحتوى، والترميز التنبؤي</p></li>
<li><p>وضع علامة على المستندات في مجموعة مراجعة</p></li>
<li><p>اقتراحات وضع العلامات للمساعدة في تحديد محتوى امتياز عميل المحامي</p></li></ul>
<p>لمزيد من المعلومات، راجع نظرة عامة <a href="/microsoft-365/compliance/overview-ediscovery-20">على Advanced eDiscovery في Microsoft 365</a>.</p>
<p>
<p>بدلا من ذلك، يمكنك تصدير نتائج البحث إلى ملفات PST ثم Microsoft 365 استيراد الخدمة لاستيراد PSTs إلى علبة بريد اكتشاف. للحصول على الإرشادات خطوة بخطوة، راجع <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">استخدام تحميل الشبكة لاستيراد ملفات PST Office 365</a>.
</tr>
<tr class=even>
  <td>نسخ الرسائل من علبة بريد واحدة إلى علبة بريد أخرى</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">تعيين أذونات إلى علبة بريد</a></td>
  <td>لإعطاء شخص حق الوصول إلى البريد الإلكتروني الخاص بمستخدم آخر (على النحو الذي يحدث عند مغادرة موظف لمنظمتك وأنت بحاجة إلى منح شخص آخر حق الوصول إلى البريد الإلكتروني الخاص بالموظف السابق)، نوصي بتعيين أذونات لهذا الشخص للوصول إلى علبة بريد الموظف السابق. لذا بدلا من نسخ عناصر علبة البريد إلى علبة بريد مستخدم أخرى أو علبة بريد مشتركة، ما عليك سوى تعيين الأذونات اللازمة للمستخدم للوصول إلى علبة البريد المصدر.</td>
  
  </tr>
<tr class="odd">
<td>استعادة العناصر من مجلد "العناصر القابلة لاستردادها"</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>يمكنك استعادة العناصر المحذوفة بشكل دائم (المعروفة أيضا بالعناصر <i></i> المحذوفة بشكل تلقائي) في علب البريد، طالما أن فترة استبقاء العنصر المحذوفة لم تنته بعد. لمزيد من المعلومات، راجع <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">مجلد العناصر القابلة للاسترداد في Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>الأسئلة والأسئلة In-Place eDiscovery In-Place المواعيد

**استخدم وظيفة نتائج البحث In-Place eDiscovery & في EAC لنسخ نتائج البحث إلى علبة بريد الاكتشاف لمراجعتها من قبل المحاميين. ما هي الخيارات المتوفرة لدي الآن؟**

هناك طريقتان لتكرار هذه الوظيفة اليوم. الأول هو استخدام [مجموعات المراجعة في Advanced eDiscovery v2.0](./view-documents-in-review-set.md). مجموعات المراجعة لديها العديد من القدرات نفسها التي تراها في أداة مراجعة تقليدية مثل البحث السريع للمستندات ووضع العلامات وترابط البريد الإلكتروني والت تجميع مكرر تقريبا وتحليل المحتوى والترميز المتوقع. إذا كنت لا تزال تريد استخدام علب بريد الاكتشاف للمراجعة، فالخيار الثاني هو تصدير نتائج البحث إلى ملفات PST ثم استيراد ملفات PST إلى علبة بريد اكتشاف باستخدام ميزة استيراد [PST](use-network-upload-to-import-pst-files.md) في مركز التوافق من Microsoft.

**كيف يمكنني التحكم في مواقع المحتوى (مثل علب البريد أو المواقع) التي يمكن لمدير eDiscovery البحث فيها باستخدام الأدوات الجديدة؟**

تستخدم [مركز التوافق في Microsoft 365 أيضا حدود](set-up-compliance-boundaries.md) التوافق للتحكم في مواقع المحتوى التي يمكن لمدير eDiscovery البحث فيها. إن حدود التوافق مفيدة في الكيانات الحكومية التي تحتاج إلى البقاء ضمن حدود الوكالة أو الشركات المتعددة الجنسيات المطلوبة لاحترام الحدود الجغرافية.

**كيف يمكنني نقل عمليات البحث الحالية والتنقل إلى مركز التوافق في Microsoft 365؟**

من الممكن ترحيل عمليات In-Place eDiscovery وعمليات التحميل من EAC باستخدام PowerShell. للحصول على الإرشادات، راجع [ترحيل عمليات البحث والتحمل من EAC إلى مركز التوافق في Microsoft 365](./migrate-legacy-ediscovery-searches-and-holds.md).

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch cmdlets

وفقا للملاحظة الأصلية التي تم الإعلان عنها في 1 يوليو 2017 في مركز إدارة Exchange، يتم حاليا ازاله وظيفة In-Place eDiscovery & Hold و Cmdlets المطابقة ل -**MailboxSearch.\*** توفر هذه cmdlets للمستخدمين إمكانية البحث عن محتوى علبة البريد أو الاحتفاظ به وتصديره للحصول على طلبات قانونية وتنظيمية وعلنية.

ونظرا لتوفر هذه الإمكانات الآن في [<span class="underline"></span>](./microsoft-365-compliance-center.md) مركز التوافق في Microsoft 365 Office 365 الأمان & مركز التوافق PowerShell مع تحسين الأداء وقابلية التوسع، يجب استخدام cmdlets المحسنة هذه. تتضمن هذه cmdlets [<span class="underline">\*-ComplianceCase</span>](/powershell/module/exchange/get-compliancecase) [<span class="underline">و-ComplianceSearch\*</span>](/powershell/module/exchange/get-compliancesearch) [<span class="underline">و-CaseHoldPolicy\*</span>](/powershell/module/exchange/get-caseholdpolicy) [<span class="underline">و-CaseHoldRule\*</span>](/powershell/module/exchange/get-caseholdrule) [<span class="underline">و-ComplianceSearchAction\*</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>نطاق المؤسسات المتأثرة

- Office 365 Microsoft 365 Enterprise المؤسسات

- Office 365 Microsoft 365 Education المؤسسات

- Office 365 Microsoft 365 الحكومية؛ يشمل ذلك سحابة القطاع الحكومي وd doD سحابة القطاع الحكومي وD DOD

- Office 365 ألمانيا

### <a name="timeline"></a>المخطط الزمني

- 1 يوليو 2020: لن تتمكن من استخدام **البحث** الجديد لعلب البريد لإنشاء عمليات بحث eDiscovery جديدة في In-Place وعمليات حفظ In-Place، ولكن لا يزال بإمكانك استخدام cmdlets لتشغيل عمليات البحث والمواعيد الموجودة وتحريرها وحذفها على حسابك الخاص. لن يوفر دعم Microsoft المساعدة بعد الآن لهذه الأنواع من عمليات البحث والتحمل.

- 1 أكتوبر 2020: كما ذكر سابقا، سيتم وضع وظيفة In-Place eDiscovery & Holds في EAC في وضع القراءة فقط. وهذا يعني أيضا أنك لن تتمكن من استخدام cmdlets البحث في علبة البريد الجديدة أو البحث في **Start-Mailbox أو** **Set-MailboxSearch**. لن تتمكن إلا من الحصول على عمليات البحث والمواضع المواضع الموجودة وإزالتها.

### <a name="alternative-tools"></a>الأدوات البديلة

يصف الجدول التالي الأدوات الأخرى التي يمكنك استخدامها لاستبدال الوظائف الموجودة التي يتم إعفاها.

<table>
<thead>
<tr class="header">
<th>الوظائف</th>
<th>الأدوات البديلة</th>
<th>التعليقات</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>البحث والتصدير</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>تعمل كل من Cmdlets ComplianceSearchAction و ComplianceSearchAction معا لمساعدتك في البحث عن المحتوى وتصديره. يمكنك إنشاء بحث جديد وعرض تقدير البحث باستخدام <strong>الأمرين cmdlets البحث</strong> عن جديد <strong></strong>والحصول على وبدء التوافق<strong></strong>. بعد ذلك، يمكنك استخدام <strong>الأمر cmdlet New-ComplianceSearchAction</strong> لتصدير نتائج البحث. سيبقى عليك استخدام أداة eDiscovery الأساسية في مركز التوافق في Microsoft 365 لتنزيل نتائج البحث هذه إلى الكمبيوتر المحلي.</p>
<p>
<p><strong>ملاحظة:</strong> إذا كنت تستخدم cmdlets هذه لإنشاء عمليات بحث غير مقترنة بأحجية eDiscovery أساسية، سيتم تحديد موقع عمليات البحث هذه على صفحة البحث <strong></strong> في المحتوى في مركز التوافق في Microsoft 365.</p></td>
</tr>
<tr class="even">
<td>الاحتفاظ بالمحتوى في علبة بريد</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>يجب إقترن مركز التوافق في Microsoft 365 في الرصيد ب ComplianceCase. أولا، قم بإنشاء حالة التوافق، ثم قم بإنشاء CaseHoldPolicy و CaseHoldRule.</p>
<p><strong>ملاحظة:</strong> يؤدي إنشاء CaseHoldPolicy بدون إنشاء CaseHoldRule إلى عرض وضع الانتظار غير قابل للتطبيق حتى يتم إنشاء CaseHoldRule وإقترن ب CaseHoldPolicy. راجع وثائق cmdlet للحصول على مزيد من المعلومات.</p></td>
</tr>
<tr class="odd">
<td>نسخ نتائج البحث إلى علبة بريد اكتشاف</td>
<td>بلا</td>
<td>لا يوجد بديل مباشر لهذه الوظيفة لأنها لا توفر إمكانية الوصول إلى جميع Microsoft 365 الخدمات. راجع الأسئلة الشائعة التالية أدناه للحصول على حلول بديلة.</td>
</tr>
  <tr class=even>
  <td>نسخ الرسائل من علبة بريد واحدة إلى علبة بريد أخرى</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">تعيين أذونات إلى علبة بريد</a></td>
  <td>لإعطاء شخص حق الوصول إلى البريد الإلكتروني الخاص بمستخدم آخر (على النحو الذي يحدث عند مغادرة موظف لمنظمتك وأنت بحاجة إلى منح شخص آخر حق الوصول إلى البريد الإلكتروني الخاص بالموظف السابق)، نوصي بتعيين أذونات لهذا الشخص للوصول إلى علبة بريد الموظف السابق. لذا بدلا من نسخ عناصر علبة البريد إلى علبة بريد مستخدم أخرى أو علبة بريد مشتركة، ما عليك سوى تعيين أذونات مستخدم للوصول إلى علبة البريد المصدر.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>الأسئلة المسئلة حول **cmdlets *-MailboxSearch**

**نحن نستخدم "نسخ البحث" لتصدير رسائل البريد الإلكتروني أو الرسائل الفورية لأغراض خاصة ب eDiscovery والاستعراضات القانونية الأخرى. ما هي الخيارات الأخرى المتوفرة لدينا بعد أن يتم ازاله هذه cmdlets؟**

توفر [<span class="underline">واجهات Graph</span>](https://developer.microsoft.com/en-us/graph) **\*** برمجة تطبيقات Microsoft عددا من الأساليب لاستخراج البيانات لتحليلها وأغراض أخرى أكثر مرونة وقابلية للتدرج من استخدام cmdlets -MailboxSearch.

**كيف يمكنني ترحيل عمليات البحث والترحيل إلى مركز التوافق في Microsoft 365؟**

من الممكن ترحيل عمليات In-Place eDiscovery وعمليات البحث من مركز إدارة Exchange باستخدام برنامج PowerShell النصي. للحصول على مزيد من المعلومات، راجع [ترحيل عمليات البحث القديمة في eDiscovery وتحملها إلى مركز التوافق في Microsoft 365](migrate-legacy-eDiscovery-searches-and-holds.md).

**بعد أن يتم التخلص من cmdlets، هل ما زلت قادرا على إزالة عمليات البحث أو استردادها؟**

نعم، على الرغم من أننا نقوم بإزالة القدرة على إنشاء عمليات البحث وتعديلها، إلا أنه سيبقى بإمكانك استخدام **Get-MailboxSearch** و **Remove-MailboxSearch** حتى إشعار آخر. ومع ذلك، فإن استخدام هذه cmdlets سيكون على طريقتك الخاصة بعد تواريخ التقاعد ولن يتمكن دعم Microsoft من تقديم المساعدة بعد ذلك.

## <a name="search-mailbox-cmdlet"></a>Search-Mailbox cmdlet

يتم **الآن** Exchange Online أمر cmdlet "البحث في علبة البريد" في PowerShell كما تم الإعلان عنه في البداية في تحذير في إخراج cmdlet بدءا من عام 2018. تم **استخدام الأمر cmdlet** "البحث في علبة البريد" في الأصل للبحث في علبة بريد المستخدم و إزالة المحتوى الضار. نوصيك ببدء استخدام **Cmdlets New-ComplianceSearch** و **New-ComplianceSearchAction** cmdlets في Office 365 Security & Compliance Center PowerShell للبحث عن المحتوى وحذفه. للحصول على تجربة أمان مضمنة، توفر [<span class="underline"></span>](../security/index.yml) ميزات الأمان Microsoft 365 حماية قوية من المخاطر للبريد الإلكتروني والعديد من خدمات Microsoft.

### <a name="scope-of-affected-organizations"></a>نطاق المؤسسات المتأثرة

- Office 365 Microsoft 365 Enterprise المؤسسات

- Office 365 Microsoft 365 Education المؤسسات

- Office 365 Microsoft 365 الحكومية؛ يشمل ذلك سحابة القطاع الحكومي وd doD سحابة القطاع الحكومي وD DOD

- Office 365 ألمانيا

### <a name="timeline"></a>المخطط الزمني

-  1 يوليو 2020: لن يعود **الأمر cmdlet** "البحث في علبة البريد" متوفرا ولن يقدم دعم Microsoft المساعدة بعد الآن.

### <a name="alternative-tools"></a>الأدوات البديلة

يصف الجدول التالي الأدوات الأخرى التي يمكنك استخدامها لاستبدال الوظائف الموجودة التي يتم إعفاها.

<table>
<thead>
<tr class="header">
<th>الوظائف</th>
<th>الأدوات البديلة</th>
<th>التعليقات</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>البحث في علبة بريد</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>تعمل كل من Cmdlets ComplianceSearchAction و ComplianceSearchAction معا لمساعدتك في البحث عن المحتوى وتصديره. يمكنك إنشاء بحث جديد وعرض تقدير البحث باستخدام <strong>الأمرين cmdlets البحث</strong> عن جديد <strong></strong>والحصول على وبدء التوافق<strong></strong>. بعد ذلك، يمكنك استخدام <strong>الأمر New-ComplianceSearchAction -Export</strong> لتصدير نتائج البحث. سيبقى عليك استخدام أداة eDiscovery الأساسية في مركز التوافق في Microsoft 365 لتنزيل نتائج البحث هذه إلى الكمبيوتر المحلي.</p></p>
</td>
</tr>
<tr class="even">
<td>حذف البريد الإلكتروني المجمع من علبة بريد</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">إعداد نهج أرشفة وحذف لعلب البريد</span></a></p>
<p></p></td>
<td><p>يمكن للمسؤولين إنشاء نهج أرشفة وحذف ينقل العناصر تلقائيا إلى علبة بريد الأرشيف الخاصة بالمستخدم ويحذف العناصر تلقائيا من علبة البريد.</p>
</td>
</tr>
<tr class="even">
<td>نسخ نتائج البحث إلى علبة بريد اكتشاف</td>
<td> </td>
<td>لا يوجد بديل مباشر لهذه الوظيفة لأنها لا توفر إمكانية الوصول إلى جميع Microsoft 365 الخدمات. راجع الأسئلة الواردة في <strong>القسم cmdlets *-MailboxSearch</strong> للحصول على حلول بديلة. </td>
</tr>
<tr class=odd>
  <td>نسخ الرسائل من علبة بريد واحدة إلى علبة بريد أخرى</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">تعيين أذونات إلى علبة بريد</a></td>
  <td>لإعطاء شخص حق الوصول إلى البريد الإلكتروني الخاص بمستخدم آخر (على النحو الذي يحدث عند مغادرة موظف لمنظمتك وأنت بحاجة إلى منح شخص آخر حق الوصول إلى البريد الإلكتروني الخاص بالموظف السابق)، نوصي بتعيين أذونات لهذا الشخص للوصول إلى علبة بريد الموظف السابق. لذا بدلا من نسخ عناصر علبة البريد إلى علبة بريد مستخدم أخرى أو علبة بريد مشتركة، ما عليك سوى تعيين إذن مستخدم للوصول إلى علبة البريد المصدر.</td>
</tr>
<tr class=even>
  <td>إزالة الرسائل من علبة بريد</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>يعمل كل من ComplianceSearch و ComplianceSearchAction cmdlets معا لمساعدتك على البحث عن المحتوى وحذفه. يمكنك إنشاء بحث وتشغيله باستخدام <strong>أوامر cmdlets ل البحث في New-ComplianceSearch</strong> و <strong>New-ComplianceSearch</strong> ، ثم يمكنك إزالة المحتوى باستخدام <strong>الأمر New-ComplianceSearchAction -Purge -PurgeType</strong> . لمزيد من المعلومات، راجع <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">البحث عن الرسائل وحذفها</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>إزالة الرسائل من علبة بريد</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">تعيين أذونات إلى علبة بريد</a></td>
<td>ل إزالة الرسائل من علبة بريد، قم بتعيين أذونات المسؤول للوصول إلى علبة بريد الموظف. يمكن حذف الرسائل وإعادة تدويرها حسب الحاجة للاستفادة من إمكانيات البحث والعرض المضمنة في Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Exchange API لخدمات الويب

يتم استخدام هذه العمليات في Exchange Web Services API بواسطة ميزة In-Place eDiscovery & eDiscovery & في مركز إدارة Exchange **\*** و cmdlets المطابقة ل -MailboxSearch في Exchange Online PowerShell. سيتم أيضا إزالتها كجزء من عملية إعزال أدوات eDiscovery القديمة الأخرى.

### <a name="scope-of-affected-organizations"></a>نطاق المؤسسات المتأثرة

- Office 365 Microsoft 365 Enterprise المؤسسات

- Office 365 Microsoft 365 Education المؤسسات

- Office 365 Microsoft 365 الحكومية؛ يشمل ذلك سحابة القطاع الحكومي وd doD سحابة القطاع الحكومي وD DOD

- Office 365 ألمانيا

### <a name="timeline"></a>المخطط الزمني

- 1 يوليو 2020: لن تتوفر عمليات GetSearchableMailboxes و SearchMailboxes و SetHoldOnMailboxes و GetHoldOnMailboxes، ولن يقدم دعم Microsoft المساعدة بعد الآن.

## <a name="advanced-ediscovery-v10"></a>Advanced eDiscovery 1.0

Advanced eDiscovery الإصدار 1.0، وهو إصدار Advanced eDiscovery المتوفر في حالة eDiscovery الأساسية بالنقر فوق التبديل إلى Advanced eDiscovery، يتم إيقافه. تم استبدال وظائفه بحلول Advanced eDiscovery [الجديد](./ediscovery.md) في مركز التوافق في Microsoft 365.

لتحديد ما إذا كانت مؤسستك تستخدم Advanced eDiscovery 1.0:

1. انتقل إلى مركز التوافق في Microsoft 365، وحدد **eDiscoveryCore** > ، وافتح حالة eDiscovery أساسية.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

1. إذا رأيت زر التبديل **إلى** Advanced eDiscovery، فإن النقر فوقه سيأخذك إلى الإصدار 1.0 من Advanced eDiscovery، الذي يتم إيقافه. لن تتأثر القدرة على إنشاء الحالات وإدارتها في Core eDiscovery. يتم إيقاف القدرة على إضافة بيانات حالة Advanced eDiscovery في v1.0 (بالنقر فوق التبديل إلى **Advanced eDiscovery) فقط**.

يوفر حل Advanced eDiscovery الجديد في Microsoft 365 (المعروف أيضا ب *Advanced eDiscovery v2.0*) كل إمكانات الحل الأصلي، ولكنه يتضمن الآن نهجا مستندا إلى المحتوى لتعريف المحتوى في Microsoft 365  الخدمات، وجمع هذا المحتوى، ثم إضافته إلى مجموعة مراجعة حيث يمكن للمراجعين الاستفادة من استعلامات البحث السريع، ووضع العلامات، وميزات التحليلات للمساعدة في العثور على المستندات ذات الصلة. Advanced eDiscovery تتضمن الآن المعالجة المحسنة والعارضين الأصليين لكل من أنواع الملفات من Microsoft وغير Microsoft، توجد قائمة كاملة بأنواع الملفات هنا، كما توجد حقول [](./supported-filetypes-ediscovery20.md) بيانات التعريف [المعتمدة هنا](./document-metadata-fields-in-advanced-ediscovery.md). بالإضافة إلى ذلك، يوفر Advanced eDiscovery الجديد ميزة إدارة احتجاز حامل قوية تتيح لك تطبيق الاحتجازات على المحتوى في خدمات مختلفة وإعلام المستخدمين باحتواك المحتوى وتعقب الاستجابات الضمية، كل ذلك ضمن Advanced eDiscovery أخرى.

للوصول إلى Advanced eDiscovery v2.0:

انتقل إلى مركز التوافق في Microsoft 365، وحدد **eDiscoveryAdvanced** > ، وافتح حالة eDiscovery الأساسية.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

في هذا الوقت، نوصي ببدء نقل سير عمل eDiscovery إلى وظيفة Advanced eDiscovery الجديدة. إذا لزم الأمر، يمكنك أرشفة Advanced eDiscovery 1.0 من خلال تصدير المحتوى وتخزينه دون اتصال. على الرغم من أنه سيبقى بإمكانك الوصول إلى Advanced eDiscovery 1.0 في الحالات الموجودة حتى 31 ديسمبر 2020، إلا أن دعم Microsoft لن يوفر الدعم بعد 1 أكتوبر 2020. راجع المخطط الزمني التالي للحصول على مزيد من التفاصيل.

### <a name="scope-of-affected-organizations"></a>نطاق المؤسسات المتأثرة

- Office 365 Microsoft 365 Enterprise المؤسسات

- Office 365 Microsoft 365 Education المؤسسات

- Office 365 Microsoft 365 الحكومية؛ يشمل ذلك سحابة القطاع الحكومي وd doD سحابة القطاع الحكومي وD DOD

- Office 365 ألمانيا

### <a name="timeline"></a>المخطط الزمني

- 1 يوليو 2020: لن تتمكن من إنشاء حالات Advanced eDiscovery v1.0.

- 1 أكتوبر 2020: لن تتمكن من إضافة بيانات جديدة (إعداد نتائج البحث Advanced eDiscovery) إلى أي حالة. سوف تتمكن من متابعة العمل على البيانات في الحالات الموجودة على المخاطر الخاصة بك. لن يقدم دعم Microsoft المساعدة بعد الآن. 

- 31 ديسمبر 2020: لن تتمكن من الوصول إلى Advanced eDiscovery v1.0.

### <a name="alternative-tools"></a>الأدوات البديلة

الحل [Advanced eDiscovery في](./overview-ediscovery-20.md) مركز التوافق في Microsoft 365.