---
title: استخدم PowerShell لإجراء ترحيل كلي إلى Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تعرف على كيفية استخدام PowerShell لنقل المحتويات من نظام بريد إلكتروني مصدر مرة واحدة عن طريق إجراء ترحيل كلي إلى Microsoft 365.
ms.openlocfilehash: ede2dfc25897012c5cb7e5469abea49e6db4292e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078680"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>استخدم PowerShell لإجراء ترحيل كلي إلى Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك ترحيل محتويات علب بريد المستخدمين من نظام بريد إلكتروني مصدر إلى Microsoft 365 كلها مرة واحدة باستخدام الترحيل الكلي. ترشدك هذه المقالة خلال المهام الخاصة بترحيل البريد الإلكتروني الكلي باستخدام Exchange Online PowerShell.

من خلال مراجعة الموضوع، [ما تحتاج إلى معرفته حول الترحيل الكلي للبريد الإلكتروني إلى Microsoft 365](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)، يمكنك الحصول على نظرة عامة على عملية الترحيل. عندما تتعرف على محتويات هذه المقالة، استخدم هذه المقالة لبدء ترحيل علب البريد من نظام بريد إلكتروني إلى آخر.

> [!NOTE]
> يمكنك أيضا استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> لإجراء ترحيل كلي. راجع [إجراء ترحيل كلي للبريد الإلكتروني إلى Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

الوقت المقدر لإكمال هذه المهمة: 2-5 دقائق لإنشاء دفعة ترحيل. بعد بدء دفعة الترحيل، ستختلف مدة الترحيل استنادا إلى عدد علب البريد في الدفعة وحجم كل علبة بريد وسعة الشبكة المتوفرة. للحصول على معلومات حول العوامل الأخرى التي تؤثر على المدة التي يستغرقها ترحيل علب البريد إلى Microsoft 365، راجع ["أداء الترحيل](/Exchange/mailbox-migration/office-365-migration-best-practices)".

يجب تعيين أذونات لك قبل أن تتمكن من تنفيذ هذا الإجراء أو الإجراءات. للاطلاع على الأذونات التي تحتاجها، راجع إدخال "الترحيل" في جدول في موضوع ["أذونات المستلمين](/exchange/recipients-permissions-exchange-2013-help) ".

لاستخدام Exchange Online PowerShell cmdlets، تحتاج إلى تسجيل الدخول واستيراد أوامر cmdlets إلى جلسة Windows PowerShell المحلية. راجع [الاتصال Exchange Online باستخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على الإرشادات.

للحصول على قائمة كاملة بأوامر الترحيل، راجع [أوامر cmdlets للتنقل والترحيل](/powershell/exchange/).

## <a name="migration-steps"></a>خطوات الترحيل

### <a name="step-1-prepare-for-a-cutover-migration"></a>الخطوة 1: الاستعداد لانتقال كلي
<a name="BK_Step1"> </a>

- **أضف مؤسستك Exchange المحلية كمجال مقبول لمؤسستك Microsoft 365.** تستخدم خدمة الترحيل عنوان SMTP لعلب البريد المحلية لإنشاء معرف مستخدم Microsoft Online Services وعنوان البريد الإلكتروني لعلب بريد Microsoft 365 الجديدة. سيفشل الترحيل إذا لم يكن مجالك Exchange مجالا مقبولا أو المجال الأساسي لمؤسستك Microsoft 365. لمزيد من المعلومات، راجع [التحقق من مجالك](../admin/setup/add-domain.md).

- **تكوين Outlook في أي مكان على خادم Exchange المحلي.** تستخدم خدمة ترحيل البريد الإلكتروني RPC عبر HTTP أو Outlook في أي مكان للاتصال بخادم Exchange المحلي. للحصول على معلومات حول كيفية إعداد Outlook في أي مكان ل Exchange 2010 Exchange 2007 Exchange 2003، راجع ما يلي:

  - [Exchange 2010: تمكين Outlook في أي مكان](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))

  - [Exchange 2007: كيفية تمكين Outlook في أي مكان](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

  - [Exchange 2003: سيناريوهات النشر ل RPC عبر HTTP](/previous-versions/tn-archive/bb124876(v=exchg.65))

  - [كيفية تكوين Outlook في أي مكان باستخدام Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

    > [!IMPORTANT]
    > يجب تكوين تكوين Outlook في أي مكان باستخدام شهادة صادرة عن مرجع مصدق موثوق به (CA). لا يمكن تكوينه بشهادة موقعة ذاتيا. لمزيد من المعلومات، راجع [كيفية تكوين SSL Outlook في أي مكان](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

- **تحقق من إمكانية الاتصال بمؤسستك Exchange باستخدام Outlook في أي مكان.** جرب أحد هذه الأساليب لاختبار إعدادات الاتصال:

  - استخدم Microsoft Outlook من خارج شبكة الشركة للاتصال بعلبة بريد Exchange المحلية.

  - استخدم Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) لاختبار إعدادات الاتصال. استخدم اختبارات Outlook في أي مكان (RPC عبر HTTP) أو Outlook Autodiscover.

  - تشغيل الأوامر التالية في Exchange Online PowerShell.

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **قم بتعيين الأذونات اللازمة لحساب مستخدم محلي للوصول إلى علب البريد في مؤسستك Exchange.** يجب أن يكون لحساب المستخدم المحلي الذي تستخدمه للاتصال بمؤسسة Exchange المحلية (التي تسمى أيضا مسؤول الترحيل) الأذونات اللازمة للوصول إلى علب البريد المحلية التي تريد ترحيلها إلى Microsoft 365. يتم استخدام حساب المستخدم هذا لإنشاء نقطة نهاية ترحيل إلى مؤسستك المحلية.

    تعرض القائمة التالية الامتيازات الإدارية المطلوبة بترحيل علب البريد باستخدام الترحيل الكلي. هناك ثلاثة خيارات ممكنة.

  - يجب أن يكون مسؤول الترحيل عضوا في مجموعة **"مسؤولي المجال** " في Active Directory في المؤسسة المحلية.

    او

  - يجب تعيين إذن **FullAccess** لمسؤول الترحيل لكل علبة بريد محلية.

    او

  - يجب تعيين إذن **"تلقي باسم** " لمسؤول الترحيل على قاعدة بيانات علبة البريد المحلية التي تخزن علب بريد المستخدمين.

- **تعطيل المراسلة الموحدة.** إذا تم تمكين علب البريد المحلية التي تقوم بترحيلها للمراسلة الموحدة (UM)، يجب تعطيل المراسلة الموحدة على علب البريد قبل ترحيلها. يمكنك بعد ذلك تمكين المراسلة الموحدة على علب البريد بعد اكتمال الترحيل.

- **مجموعات الأمان والمفوضون** يتعذر على خدمة ترحيل البريد الإلكتروني اكتشاف ما إذا كانت مجموعات Active Directory محلي مجموعات أمان أم لا، لذلك لا يمكنها توفير أي مجموعات تم ترحيلها كالمجموعات الأمنية في Microsoft 365. إذا كنت تريد أن يكون لديك مجموعات أمان في مستأجر Microsoft 365، فيجب أولا توفير مجموعة أمان فارغة ممكنة للبريد في مستأجر Microsoft 365 قبل بدء الترحيل الكلي. بالإضافة إلى ذلك، يؤدي أسلوب الترحيل هذا إلى نقل علب البريد ومستخدمي البريد وجهات اتصال البريد والمجموعات الممكنة للبريد فقط. إذا تم تعيين أي كائن Active Directory آخر، مثل المستخدم الذي لم يتم ترحيله إلى Microsoft 365، كمدير أو مفوض إلى كائن يتم ترحيله، فيجب إزالته من الكائن قبل الترحيل.

### <a name="step-2-create-a-migration-endpoint"></a>الخطوة 2: إنشاء نقطة نهاية ترحيل
<a name="BK_Step2"> </a>

لنقل البريد الإلكتروني بنجاح، يحتاج Microsoft 365 إلى الاتصال بنظام البريد الإلكتروني المصدر والتواصل معه. للقيام بذلك، يستخدم Microsoft 365 نقطة نهاية الترحيل. لإنشاء نقطة نهاية ترحيل Outlook في أي مكان للتهحيل الكلي، [اتصل أولا Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

للحصول على قائمة كاملة بأوامر الترحيل، راجع [أوامر cmdlets للتنقل والترحيل](/powershell/exchange/).

تشغيل الأوامر التالية في Exchange Online PowerShell:

```powershell
$Credentials = Get-Credential
```

يستخدم المثال [cmdlet Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) للحصول على إعدادات الاتصال إلى خادم Exchange المحلي واختبارها، ثم يستخدم إعدادات الاتصال هذه لإنشاء نقطة نهاية الترحيل المسماة "CutoverEndpoint".

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> يمكن استخدام **New-MigrationEndpoint** cmdlet لتحديد قاعدة بيانات للخدمة لاستخدامها باستخدام خيار **-TargetDatabase** . وإلا، يتم تعيين قاعدة بيانات عشوائيا من موقع خدمات الأمان المشترك لـ Active Directory (AD FS) 2.0 حيث توجد علبة بريد الإدارة.

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

في Exchange Online PowerShell، قم بتشغيل الأمر التالي لعرض معلومات حول نقطة نهاية الترحيل "CutoverEndpoint":

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>الخطوة 3: إنشاء دفعة الترحيل الكلي
<a name="BK_Step3"> </a>

يمكنك استخدام **New-MigrationBatch** cmdlet في Exchange Online PowerShell لإنشاء دفعة ترحيل لانتقال كلي. يمكنك إنشاء دفعة ترحيل وبدء تشغيلها تلقائيا عن طريق تضمين المعلمة _AutoStart_ . بدلا من ذلك، يمكنك إنشاء دفعة الترحيل ثم بدء تشغيلها يدويا بعد ذلك باستخدام **Start-MigrationBatch** cmdlet. ينشئ هذا المثال دفعة ترحيل تسمى "CutoverBatch" ويستخدم نقطة نهاية الترحيل التي تم إنشاؤها في الخطوة السابقة.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

ينشئ هذا المثال أيضا دفعة ترحيل تسمى "CutoverBatch" ويستخدم نقطة نهاية الترحيل التي تم إنشاؤها في الخطوة السابقة. نظرا لعدم تضمين معلمة  _AutoStart_ ، يجب بدء دفعة الترحيل يدويا على لوحة معلومات الترحيل أو باستخدام **Start-MigrationBatch** cmdlet. كما ذكر سابقا، يمكن أن توجد دفعة ترحيل كلي واحدة فقط في كل مرة.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

للتحقق من إنشاء دفعة ترحيل بنجاح لانتقال كلي، قم بتشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول دفعة الترحيل الجديدة:

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>الخطوة 4: بدء دفعة الترحيل الكلي

لبدء دفعة الترحيل في Exchange Online PowerShell، قم بتشغيل الأمر التالي. سيؤدي ذلك إلى إنشاء دفعة ترحيل تسمى "CutoverBatch".

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

إذا تم بدء دفعة ترحيل بنجاح، يتم تحديد حالتها على لوحة معلومات الترحيل كمزامنة. للتحقق من أنك بدأت دفعة ترحيل بنجاح باستخدام Exchange Online PowerShell، قم بتشغيل الأمر التالي:

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>الخطوة 5: توجيه بريدك الإلكتروني إلى Microsoft 365

تستخدم أنظمة البريد الإلكتروني سجل DNS يسمى سجل MX لمعرفة مكان تسليم رسائل البريد الإلكتروني. أثناء عملية ترحيل البريد الإلكتروني، كان سجل MX يشير إلى نظام البريد الإلكتروني المصدر. الآن بعد اكتمال ترحيل البريد الإلكتروني إلى Microsoft 365، حان الوقت لإشارة سجل MX إلى Microsoft 365. يساعد ذلك على التأكد من تسليم البريد الإلكتروني إلى علب بريدك Microsoft 365. من خلال نقل سجل MX، يمكنك أيضا إيقاف تشغيل نظام البريد الإلكتروني القديم عندما تكون جاهزا.

بالنسبة إلى العديد من موفري DNS، هناك إرشادات محددة لتغيير سجل MX. إذا لم يكن موفر DNS الخاص بك مضمنا، أو إذا كنت تريد الحصول على فكرة عن التوجيهات العامة، يتم توفير [إرشادات سجل MX العامة](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx) أيضا.

قد يستغرق الأمر ما يصل إلى 72 ساعة حتى تتمكن أنظمة البريد الإلكتروني لعملائك وشركائك من التعرف على سجل MX الذي تم تغييره. انتظر 72 ساعة على الأقل قبل المتابعة إلى المهمة التالية: [الخطوة 6: حذف دفعة الترحيل الكلي](#step-6-delete-the-cutover-migration-batch).

### <a name="step-6-delete-the-cutover-migration-batch"></a>الخطوة 6: حذف دفعة الترحيل الكلي

بعد تغيير سجل MX والتحقق من توجيه كل رسائل البريد الإلكتروني إلى علب بريد Microsoft 365، قم بإعلام المستخدمين بأن البريد الخاص بهم سينتقل إلى Microsoft 365. بعد ذلك، يمكنك حذف دفعة الترحيل الكلي. تحقق مما يلي قبل حذف دفعة الترحيل.

- يستخدم جميع المستخدمين علب بريد Microsoft 365. بعد حذف الدفعة، لا يتم نسخ البريد المرسل إلى علب البريد في Exchange Server المحلية إلى علب بريد Microsoft 365 المقابلة.

- Microsoft 365 تمت مزامنة علب البريد مرة واحدة على الأقل بعد بدء إرسال البريد إليها مباشرة. للقيام بذلك، تأكد من أن القيمة الموجودة في المربع "وقت آخر مزامنة" دفعة الترحيل أحدث مما كانت عليه عند بدء توجيه البريد مباشرة إلى علب بريد Microsoft 365.

لحذف دفعة الترحيل "CutoverBatch" في Exchange Online PowerShell، قم بتشغيل الأمر التالي:

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>القسم 7: تعيين تراخيص المستخدمين

 **تنشيط Microsoft 365 حسابات المستخدمين للحسابات التي تم ترحيلها عن طريق تعيين التراخيص.** إذا لم تقم بتعيين ترخيص، يتم تعطيل علبة البريد عند انتهاء فترة السماح (30 يوما). لتعيين ترخيص في مركز مسؤولي Microsoft 365، راجع [تعيين تراخيص أو إلغاء تعيينها](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>الخطوة 8: إكمال مهام ما بعد الترحيل

- **إنشاء سجل DNS الكشف التلقائي حتى يتمكن المستخدمون من الوصول بسهولة إلى علب بريدهم.** بعد ترحيل كل علب البريد المحلية إلى Microsoft 365، يمكنك تكوين سجل DNS للتحقق التلقائي لمؤسسة Microsoft 365 لتمكين المستخدمين من الاتصال بسهولة بعلب بريدهم Microsoft 365 الجديدة باستخدام عملاء Outlook والأجهزة المحمولة. يجب أن يستخدم سجل DNS الجديد للتحقق التلقائي مساحة الاسم نفسها التي تستخدمها لمؤسستك Microsoft 365. على سبيل المثال، إذا كانت مساحة الاسم المستندة إلى السحابة cloud.contoso.com، يكون سجل DNS للتحقق التلقائي الذي تحتاج إلى إنشائه autodiscover.cloud.contoso.com.

    إذا احتفظت Exchange Server، فيجب أيضا التأكد من أن سجل DNS CNAME للتحقق التلقائي يجب أن يشير إلى Microsoft 365 في كل من DNS الداخلي والخارجي بعد الترحيل بحيث يتمكن عميل Outlook من الاتصال بعلبة البريد الصحيحة.

    > [!NOTE]
    >  في Exchange 2007، Exchange 2010، Exchange 2013 يجب عليك أيضا التعيين `Set-ClientAccessServer AutodiscoverInternalConnectionURI` إلى `Null`.

    يستخدم Microsoft 365 سجل CNAME لتنفيذ خدمة الكشف التلقائي لعملاء Outlook والأجهزة المحمولة. يجب أن يحتوي سجل CNAME للتحقق التلقائي على المعلومات التالية:

  - **الاسم المستعار:** الكشف التلقائي

  - **الهدف:** autodiscover.outlook.com

    لمزيد من المعلومات، راجع [إضافة سجلات DNS لتوصيل مجالك](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **إيقاف تشغيل خوادم Exchange المحلية.** بعد التحقق من توجيه جميع رسائل البريد الإلكتروني مباشرة إلى علب بريد Microsoft 365، ولم تعد بحاجة إلى الاحتفاظ بمؤسسة البريد الإلكتروني المحلية أو عدم التخطيط لتنفيذ حل تسجيل الدخول الأحادي، يمكنك إزالة تثبيت Exchange من الخوادم وإزالة مؤسستك Exchange المحلية.

    لمزيد من المعلومات، راجع ما يلي:

  - [تعديل Exchange 2010 أو إزالته](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [كيفية إزالة مؤسسة Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [كيفية إلغاء تثبيت Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))