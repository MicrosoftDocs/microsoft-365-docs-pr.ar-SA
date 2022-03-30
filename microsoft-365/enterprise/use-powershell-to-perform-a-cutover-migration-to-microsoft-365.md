---
title: استخدم PowerShell لتنفيذ عملية ترحيل كلي Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: تعرف على كيفية استخدام PowerShell لنقل المحتويات من نظام البريد الإلكتروني المصدر في الوقت نفسه من خلال تنفيذ عملية ترحيل كلي Microsoft 365.
ms.openlocfilehash: 65f48d95a73742a0ba4e5225361ecfb0fbf66c40
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63576889"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>استخدم PowerShell لتنفيذ عملية ترحيل كلي Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك ترحيل محتويات علب بريد المستخدمين من نظام البريد الإلكتروني المصدر Microsoft 365 مرة واحدة باستخدام الترحيل كلي. تريك هذه المقالة تنفيذ المهام المتعلقة با الترحيل كلي للبريد الإلكتروني باستخدام Exchange Online PowerShell.

من خلال مراجعة الموضوع، ما [](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)تحتاج إلى معرفته حول الترحيل الشامل للبريد الإلكتروني إلى Microsoft 365، يمكنك الحصول على نظرة عامة حول عملية الترحيل. عندما ترتاح في استخدام محتويات هذه المقالة، استخدم هذه المقالة لبدء عملية تهجر علب البريد من نظام بريد إلكتروني إلى آخر.

> [!NOTE]
> يمكنك أيضا <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">استخدام مركز إدارة</a> Exchange لتنفيذ عملية ترحيل كلي. راجع [تنفيذ عملية ترحيل كلي للبريد الإلكتروني Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

الوقت المقدر لإكمال هذه المهمة: 2-5 دقائق لإنشاء دفعة ترحيل. بعد بدء دفعة الترحيل، ستختلف مدة الترحيل استنادا إلى عدد علب البريد في الدفعة وحجم كل علبة بريد و سعة الشبكة المتوفرة. للحصول على معلومات حول عوامل أخرى تؤثر على الوقت المستغرق لترحيل علب البريد Microsoft 365، راجع [أداء الترحيل](/Exchange/mailbox-migration/office-365-migration-best-practices).

يجب تعيين أذونات لك قبل تنفيذ هذا الإجراء أو الإجراءات. لمعرفة الأذونات التي تحتاج إليها، راجع إدخال "الترحيل" في جدول في الموضوع [أذونات المستلمين](/exchange/recipients-permissions-exchange-2013-help) .

لاستخدام Exchange Online Cmdlets في PowerShell، ستحتاج إلى تسجيل الدخول واستيراد cmdlets إلى جلسة Windows PowerShell المحلية. راجع [الاتصال Exchange Online استخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على الإرشادات.

للحصول على قائمة كاملة من أوامر الترحيل، راجع [أوامر cmdlets](/powershell/exchange/) الخاصة بالنقل وا الترحيل.

## <a name="migration-steps"></a>خطوات الترحيل

### <a name="step-1-prepare-for-a-cutover-migration"></a>الخطوة 1: التحضير ل الترحيل كلي
<a name="BK_Step1"> </a>

- **أضف مؤسستك Exchange كمجال مقبول لمنظمتك Microsoft 365.** تستخدم خدمة الترحيل عنوان SMTP لعلب البريد المحلية لإنشاء عنوان البريد الإلكتروني ومستخدم Microsoft Online Services لعلب بريد Microsoft 365 الجديدة. ستفشل عملية الترحيل إذا لم Exchange مجالك مجالا مقبولا أو مجالا أساسيا لمجالك Microsoft 365 المؤسسة. لمزيد من المعلومات، راجع [التحقق من مجالك](../admin/setup/add-domain.md).

- **قم بتكوين Outlook أي مكان على الخادم Exchange الموقع.** تستخدم خدمة ترحيل البريد الإلكتروني RPC عبر HTTP أو Outlook أي مكان، للاتصال بخادم البريد Exchange الموقع. للحصول على معلومات حول كيفية إعداد Outlook أي مكان ل Exchange 2010 و Exchange 2007 و Exchange 2003، راجع ما يلي:

  - [Exchange 2010: تمكين Outlook أي مكان](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))

  - [Exchange 2007: كيفية تمكين Outlook أي مكان](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

  - [Exchange 2003: سيناريوهات النشر ل RPC عبر HTTP](/previous-versions/tn-archive/bb124876(v=exchg.65))

  - [كيفية تكوين Outlook أي مكان باستخدام Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

    > [!IMPORTANT]
    > يجب Outlook تكوين من أي مكان بواسطة شهادة صادرة عن مرجع ممصادقة موثوق به (CA). لا يمكن تكوينه باستخدام شهادة موقعة ذاتيا. لمزيد من المعلومات، [راجع كيفية تكوين SSL Outlook أي مكان](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

- **تحقق من أنه يمكنك الاتصال Exchange مؤسستك باستخدام Outlook أي مكان.** جرب أحد هذه الأساليب لاختبار إعدادات الاتصال:

  - استخدم Microsoft Outlook من خارج شبكة الشركة للاتصال لعلبة بريدك المحلية Exchange البريد.

  - استخدم Microsoft Exchange ["محلل الاتصال](https://www.testexchangeconnectivity.com/) عن بعد" لاختبار إعدادات الاتصال. استخدم Outlook أي مكان (RPC عبر HTTP) أو Outlook الاكتشاف التلقائي.

  - تشغيل الأوامر التالية في Exchange Online PowerShell.

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **قم بتعيين الأذونات اللازمة لحساب مستخدم Exchange مؤسستك.** يجب أن يكون لحساب المستخدم المحلي الذي تستخدمه للاتصال بمنظمة Exchange المحلية (تسمى أيضا مسؤول الترحيل) الأذونات اللازمة للوصول إلى علب البريد المحلية التي تريد ترحيلها إلى Microsoft 365. يتم استخدام حساب المستخدم هذا لإنشاء نقطة نهاية ترحيل إلى مؤسستك الداخلية.

    تعرض القائمة التالية الامتيازات الإدارية المطلوبة لترحيل علب البريد باستخدام الترحيل كلي. هناك ثلاثة خيارات محتملة.

  - يجب أن يكون مسؤول الترحيل عضوا في مجموعة **مسؤولي** المجالات في Active Directory في المؤسسة المحلي.

    أو

  - يجب أن يتم تعيين إذن **FullAccess إلى** مسؤول الترحيل لكل علبة بريد في الموقع.

    أو

  - يجب أن يتم تعيين إذن **"** تلقي باسم" لمسؤول الترحيل على قاعدة بيانات علبة البريد المحلية التي تخزن علب بريد المستخدمين.

- **تعطيل المراسلة الموحدة.** إذا تم تمكين علب البريد المحلية التي تقوم بترحيلها للمراسلة الموحدة (UM)، يجب تعطيل المراسلة الموحدة على علب البريد قبل ترحيلها. يمكنك بعد ذلك تمكين UM على علب البريد بعد اكتمال عملية الترحيل.

- **مجموعات الأمان والمفوضون** يتعذر على خدمة ترحيل البريد الإلكتروني الكشف عما إذا كانت مجموعات Active Directory المحلية هي مجموعات أمان أم لا، وبالتالي لا يمكنها توفير أي مجموعات تم ترحيلها كم مجموعات أمان في Microsoft 365. إذا كنت تريد أن يكون لديك مجموعات أمان في مستأجر Microsoft 365، فيجب أولا توفير مجموعة أمان فارغة لتمكين البريد في مستأجر Microsoft 365 قبل بدء الترحيل كلي. بالإضافة إلى ذلك، لا ينقل أسلوب الترحيل هذا سوى علب البريد ومستخدمي البريد وجهات اتصال البريد والمجموعات التي تم تمكينها للبريد. إذا تم تعيين أي كائن Active Directory آخر، مثل المستخدم الذي لم يتم ترحيله إلى Microsoft 365، كمدير أو مفوض لكائن يتم ترحيله، فيجب إزالته من الكائن قبل الترحيل.

### <a name="step-2-create-a-migration-endpoint"></a>الخطوة 2: إنشاء نقطة نهاية ترحيل
<a name="BK_Step2"> </a>

لترحيل البريد الإلكتروني بنجاح، Microsoft 365 تحتاج إلى الاتصال ونظام البريد الإلكتروني المصدر والتواصل معه. للقيام بذلك، Microsoft 365 نقطة نهاية الترحيل. لإنشاء نقطة نهاية ترحيل Outlook أي مكان ل الترحيل كلي، اتصل أولا [Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

للحصول على قائمة كاملة من أوامر الترحيل، راجع [أوامر cmdlets](/powershell/exchange/) الخاصة بالنقل وا الترحيل.

تشغيل الأوامر التالية في Exchange Online PowerShell:

```powershell
$Credentials = Get-Credential
```

يستخدم المثال [الأمر cmdlet Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) للحصول على إعدادات الاتصال إلى خادم Exchange في الموقع واختبارها، ثم يستخدم إعدادات الاتصال هذه لإنشاء نقطة نهاية الترحيل التي تسمى "CutoverEndpoint".

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> يمكن **استخدام الأمر cmdlet New-MigrationEndpoint** لتحديد قاعدة بيانات للخدمة لاستخدامها باستخدام **الخيار -TargetDatabase** . بخلاف ذلك، يتم تعيين قاعدة بيانات عشوائيا من موقع خدمات Active Directory Federation Services (AD FS) 2.0 حيث توجد علبة بريد الإدارة.

#### <a name="verify-it-worked"></a>التحقق من عملها

في Exchange Online PowerShell، تشغيل الأمر التالي لعرض معلومات حول نقطة نهاية الترحيل "CutoverEndpoint":

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>الخطوة 3: إنشاء دفعة الترحيل كلي
<a name="BK_Step3"> </a>

يمكنك استخدام **الأمر cmdlet New-MigrationBatch** في Exchange Online PowerShell لإنشاء دفعة ترحيل ل الترحيل كلي. يمكنك إنشاء دفعة ترحيل وبدء تشغيلها تلقائيا من خلال بما في ذلك _معلمة التشغيل_ التلقائي. بدلا من ذلك، يمكنك إنشاء دفعة الترحيل ثم بدء تشغيلها يدويا بعد ذلك باستخدام **الأمر cmdlet Start-MigrationBatch** . ينشئ هذا المثال دفعة ترحيل تسمى "CutoverBatch" ويستخدم نقطة نهاية الترحيل التي تم إنشاؤها في الخطوة السابقة.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

ينشئ هذا المثال أيضا دفعة ترحيل تسمى "CutoverBatch" ويستخدم نقطة نهاية الترحيل التي تم إنشاؤها في الخطوة السابقة. نظرا لعدم  _تضمين_ معلمة التشغيل التلقائي، يجب بدء دفعة الترحيل يدويا على لوحة معلومات الترحيل أو باستخدام **الأمر cmdlet Start-MigrationBatch** . كما ذكر سابقا، يمكن أن توجد دفعة ترحيل كلي واحدة فقط في كل مرة.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>التحقق من عملها

للتحقق من أنك قمت بإنشاء دفعة ترحيل بنجاح ل الترحيل كلي، قم بتشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول دفعة الترحيل الجديدة:

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>الخطوة 4: بدء دفعة الترحيل كلي

لبدء دفعة الترحيل في Exchange Online PowerShell، يمكنك تشغيل الأمر التالي. سينشئ هذا دفعة ترحيل تسمى "CutoverBatch".

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>التحقق من عملها

إذا تم بدء دفعة ترحيل بنجاح، يتم تحديد الحالة على لوحة معلومات الترحيل كمزامنة. للتحقق من أنك قد بدأت دفعة ترحيل بنجاح باستخدام Exchange Online PowerShell، ادير الأمر التالي:

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>الخطوة 5: توجيه البريد الإلكتروني إلى Microsoft 365

تستخدم أنظمة البريد الإلكتروني سجل DNS يسمى سجل MX لمعرفة مكان تسليم رسائل البريد الإلكتروني. أثناء عملية ترحيل البريد الإلكتروني، كان سجل MX يشير إلى نظام البريد الإلكتروني المصدر. الآن وقد اكتملت عملية ترحيل البريد الإلكتروني Microsoft 365، حان وقت الإشارة إلى سجل MX Microsoft 365. يساعد ذلك على التأكد من تسليم البريد الإلكتروني إلى علب بريدك Microsoft 365 البريد. من خلال نقل سجل MX، يمكنك أيضا إيقاف تشغيل نظام البريد الإلكتروني القديم عندما تكون جاهزا.

بالنسبة إلى العديد من موفري DNS، توجد إرشادات محددة لتغيير سجل MX. إذا لم يكن موفر DNS مضمنا، أو إذا كنت تريد الحصول على إرشادات عامة، يتم أيضا توفير إرشادات عامة حول سجل [MX](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx) .

قد يستغرق الأمر ما يصل إلى 72 ساعة لكي تتعرف أنظمة البريد الإلكتروني لعملائك وشركائك على سجل MX الذي تم تغييره. انتظر 72 ساعة على الأقل قبل المتابعة إلى المهمة التالية: الخطوة [6: حذف دفعة الترحيل كلي](#step-6-delete-the-cutover-migration-batch).

### <a name="step-6-delete-the-cutover-migration-batch"></a>الخطوة 6: حذف دفعة الترحيل كلي

بعد تغيير سجل MX والتحقق من توجيه كل رسائل البريد الإلكتروني Microsoft 365 علب البريد، قم بإعلام المستخدمين بأن بريدهم سيتم Microsoft 365. بعد ذلك، يمكنك حذف دفعة الترحيل كلي. تحقق مما يلي قبل حذف دفعة الترحيل.

- يستخدم جميع المستخدمين علب Microsoft 365 البريد. بعد حذف الدفعة، لا يتم نسخ البريد المرسل إلى علب البريد على Exchange Server المحلية إلى علب البريد Microsoft 365 المقابلة.

- Microsoft 365 علب البريد مرة واحدة على الأقل بعد بدء إرسال البريد إليها مباشرة. للقيام بذلك، تأكد من أن القيمة في المربع آخر وقت متزامن بدفعة الترحيل أحدث من تلك التي كانت عند بدء توجيه البريد مباشرة إلى علب البريد Microsoft 365 البريد.

لحذف دفعة الترحيل "CutoverBatch" Exchange Online PowerShell، قم بتشغيل الأمر التالي:

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>القسم 7: تعيين تراخيص المستخدمين

 **تنشيط Microsoft 365 حسابات المستخدمين للحسابات التي تم ترحيلها من خلال تعيين التراخيص.** إذا لم يتم تعيين ترخيص، يتم تعطيل علبة البريد عند انتهاء فترة السماح (30 يوما). لتعيين ترخيص في مركز مسؤولي Microsoft 365، راجع تعيين تراخيص أو [عدم تعيينها](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>الخطوة 8: إكمال مهام ما بعد الترحيل

- **قم بإنشاء سجل DNS ل Autodiscover حتى يمكن للمستخدمين الوصول بسهولة إلى علب البريد الخاصة بهم.** بعد ترحيل كل علب البريد المحلية إلى Microsoft 365، يمكنك تكوين سجل DNS الاكتشاف التلقائي لمنظمتك في Microsoft 365 لتمكين المستخدمين من الاتصال بسهولة لعلب بريد Microsoft 365 الجديدة مع عملاء Outlook والأجهزة المحمولة. يجب أن يستخدم سجل DNS ل Autodiscover الجديد مساحة الاسم نفسها التي تستخدمها Microsoft 365 مؤسستك. على سبيل المثال، إذا كانت مساحة الاسم المستندة إلى السحابة cloud.contoso.com، يكون سجل DNS الذي تريد إنشاؤه في الاكتشاف التلقائي autodiscover.cloud.contoso.com.

    إذا احتفظت ب Exchange Server، يجب أيضا التأكد من أن سجل DNS CNAME ل الاكتشاف التلقائي يجب أن يشير إلى Microsoft 365 في كل من DNS الداخلي والخارجي بعد الترحيل بحيث يتصل عميل Outlook لعلبة البريد الصحيحة.

    > [!NOTE]
    >  في Exchange 2007 Exchange 2010 Exchange 2013، يجب أيضا تعيين إلى `Set-ClientAccessServer AutodiscoverInternalConnectionURI` `Null`.

    Microsoft 365 سجل CNAME لتطبيق خدمة الاكتشاف التلقائي للعملاء Outlook الجوال. يجب أن يحتوي سجل CNAME ل Autodiscover على المعلومات التالية:

  - **الاسم المستعار:** autodiscover

  - **الهدف: autodiscover.outlook.com**

    لمزيد من المعلومات، راجع [إضافة سجلات DNS لتوصيل مجالك](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **اسحب الخوادم Exchange في الموقع.** بعد التحقق من توجيه كل رسائل البريد الإلكتروني مباشرة إلى علب بريد Microsoft 365، ولم تعد بحاجة إلى الاحتفاظ بمنظمتك المحلية للبريد الإلكتروني أو عدم التخطيط لتنفيذ حل تسجيل الدخول الفردي (SSO)، يمكنك إلغاء تثبيت Exchange من الخوادم وإزالة حساب بريدك Exchange المحلي.

    لمزيد من المعلومات، راجع ما يلي:

  - [تعديل أو Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [كيفية إزالة Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [كيفية إلغاء تثبيت Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))