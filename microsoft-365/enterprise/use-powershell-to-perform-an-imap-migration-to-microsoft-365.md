---
title: استخدم PowerShell لإجراء ترحيل IMAP إلى Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: تعرف على كيفية استخدام PowerShell لإجراء ترحيل بروتوكول الوصول إلى بريد إنترنت (IMAP) إلى Microsoft 365.
ms.openlocfilehash: e3375af79ce4332ebf8f44e88181d7d8dc0e430f
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128778"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>استخدم PowerShell لإجراء ترحيل IMAP إلى Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

كجزء من عملية نشر Microsoft 365، يمكنك اختيار ترحيل محتويات علب بريد المستخدمين من خدمة البريد الإلكتروني لبروتوكول الوصول إلى بريد الإنترنت (IMAP) إلى Microsoft 365. ترشدك هذه المقالة خلال مهام ترحيل IMAP بالبريد الإلكتروني باستخدام Exchange Online PowerShell.

> [!NOTE]
> يمكنك أيضا استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> لإجراء ترحيل IMAP. راجع [ترحيل علب بريد IMAP](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

الوقت المقدر لإكمال هذه المهمة: 2-5 دقائق لإنشاء دفعة ترحيل. بعد بدء دفعة الترحيل، ستختلف مدة الترحيل استنادا إلى عدد علب البريد في الدفعة وحجم كل علبة بريد وسعة الشبكة المتوفرة. للحصول على معلومات حول العوامل الأخرى التي تؤثر على المدة التي يستغرقها ترحيل علب البريد إلى Microsoft 365، راجع ["أداء الترحيل](/Exchange/mailbox-migration/office-365-migration-best-practices)".

يجب تعيين أذونات لك قبل أن تتمكن من تنفيذ هذا الإجراء أو الإجراءات. للاطلاع على الأذونات التي تحتاجها، راجع إدخال "الترحيل" في جدول في موضوع ["أذونات المستلمين](/exchange/recipients-permissions-exchange-2013-help) ".

لاستخدام Exchange Online PowerShell cmdlets، تحتاج إلى تسجيل الدخول واستيراد أوامر cmdlets إلى جلسة Windows PowerShell المحلية. راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على الإرشادات.

للحصول على قائمة كاملة بأوامر الترحيل، راجع [أوامر cmdlets للتنقل والترحيل](/powershell/exchange/).

تنطبق القيود التالية على عمليات ترحيل IMAP:

- يمكن ترحيل العناصر الموجودة في علبة الوارد الخاصة بالمستخدم أو مجلدات البريد الأخرى فقط. لا يمكنك ترحيل جهات الاتصال أو عناصر التقويم أو المهام.

- يمكن ترحيل 500000 عنصر كحد أقصى من علبة بريد المستخدم.

- الحد الأقصى لحجم الرسالة الذي يمكن ترحيله هو 35 ميغابايت.

## <a name="migration-steps"></a>خطوات الترحيل

### <a name="step-1-prepare-for-an-imap-migration"></a>الخطوة 1: الاستعداد لإدارة IMAP
<a name="BK_Step1"> </a>

- **إذا كان لديك مجال لمؤسسة IMAP، فستضيفه كمجال مقبول لمؤسستك Microsoft 365.** إذا كنت تريد استخدام المجال نفسه الذي تملكه بالفعل لعلب بريدك Microsoft 365، يجب أولا إضافته كمجال مقبول إلى Microsoft 365. بعد إضافته، يمكنك إنشاء المستخدمين في Microsoft 365. لمزيد من المعلومات، راجع[التحقق من مجالك](../admin/setup/add-domain.md).

- **أضف كل مستخدم إلى Microsoft 365 بحيث يكون لديه علبة بريد.** للحصول على الإرشادات، راجع[إضافة مستخدمين إلى Microsoft 365 للأعمال](../admin/add-users/add-users.md).

- **الحصول على FQDN لخادم IMAP**. تحتاج إلى توفير اسم المجال المؤهل بالكامل (FQDN) (يسمى أيضا اسم الكمبيوتر الكامل) لخادم IMAP الذي ستقوم بترحيل بيانات علبة البريد منه عند إنشاء نقطة نهاية ترحيل IMAP. استخدم عميل IMAP أو أمر PING للتحقق من إمكانية استخدام FQDN للاتصال بخادم IMAP عبر الإنترنت.

- **تكوين جدار الحماية للسماح باتصالات IMAP**. قد تحتاج إلى فتح المنافذ في جدار حماية المؤسسة التي تستضيف خادم IMAP بحيث يسمح بنسبة استخدام الشبكة التي تنشأ من مركز بيانات Microsoft أثناء الترحيل بإدخال المؤسسة التي تستضيف خادم IMAP. للحصول على قائمة بعناوين IP التي تستخدمها مراكز بيانات Microsoft، راجع [Exchange Online عناوين URL ونطاقات عناوين IP](./urls-and-ip-address-ranges.md).

- **تعيين أذونات حساب المسؤول للوصول إلى علب البريد في مؤسسة IMAP**. في حال استخدام بيانات اعتماد المسؤول في ملف CSV، يجب أن يكون للحساب الذي تستخدمه الأذونات اللازمة للوصول إلى علب البريد المحلية. يتم تحديد الأذونات المطلوبة للوصول إلى علب بريد المستخدمين بواسطة خادم IMAP معين.

- **لاستخدام أوامر powerShell cmdlets Exchange Online**، تحتاج إلى تسجيل الدخول واستيراد أوامر cmdlets إلى جلسة عمل Windows PowerShell المحلية. راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على الإرشادات.

    للحصول على قائمة كاملة بأوامر الترحيل، راجع [أوامر cmdlets للتنقل والترحيل](/powershell/exchange/).

- **تحقق من إمكانية الاتصال بخادم IMAP**. قم بتشغيل الأمر التالي في Exchange Online PowerShell لاختبار إعدادات الاتصال بخادم IMAP.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    بالنسبة إلى قيمة معلمة **المنفذ** ، من المعتاد استخدام 143 للاتصالات غير المشفرة أو اتصالات أمان طبقة النقل (TLS) واستخدام 993 لاتصالات SSL.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>الخطوة 2: إنشاء ملف CSV دفعة ترحيل IMAP

حدد مجموعة المستخدمين الذين تريد ترحيل علب بريدهم في دفعة ترحيل IMAP. يحتوي كل صف في ملف CSV على معلومات ضرورية للاتصال بعلبة بريد في نظام مراسلة IMAP.

في ما يلي السمات المطلوبة لكل مستخدم:

- يحدد **EmailAddress** معرف المستخدم لعل بريد Microsoft 365 الخاص بالمستخدم.

- يحدد **UserName** اسم تسجيل الدخول للحساب الذي يجب استخدامه للوصول إلى علبة البريد على خادم IMAP.

- تحدد **كلمة المرور** كلمة المرور للحساب في عمود **UserName**.

في ما يلي مثال على تنسيق ملف CSV. في هذا المثال، يتم ترحيل ثلاث علب بريد:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

بالنسبة للسمة **UserName** ، بالإضافة إلى اسم المستخدم، يمكنك استخدام بيانات اعتماد حساب تم تعيين الأذونات اللازمة له للوصول إلى علب البريد على خادم IMAP، فيما يلي بعض التنسيقات المحددة المستخدمة لبعض خوادم IMAP:

 **Microsoft Exchange:**

إذا كنت تقوم بترحيل البريد الإلكتروني من تطبيق IMAP ل Microsoft Exchange، فاستخدم تنسيق **Domain/Admin_UserName/User_UserName** **للسمة UserName** في ملف CSV. لنفترض أنك تقوم بترحيل البريد الإلكتروني من Exchange ل Terry Adams وAnn Beebe و Paul Cannon. لديك حساب مسؤول البريد، حيث يكون اسم المستخدم **mailadmin** وكلمة المرور هي **P\@ssw0rd**. إليك الشكل الذي سيبدو عليه ملف CSV:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**

بالنسبة لخوادم IMAP التي تدعم طبقة الأمان والمصادقة البسيطة (SASL)، مثل خادم Dovecot IMAP، استخدم التنسيق **User_UserName*Admin_UserName**، حيث تكون العلامة النجمية ( * ) حرف فاصل قابل للتكوين. لنفترض أنك تقوم بترحيل البريد الإلكتروني للمستخدمين نفسه من خادم Dovecot IMAP باستخدام بيانات اعتماد المسؤول **mailadmin** **وP\@ssw0rd**. إليك الشكل الذي سيبدو عليه ملف CSV:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**

إذا كنت تقوم بترحيل البريد الإلكتروني من خادم رسائل Mirapoint، فاستخدم التنسيق **#user\@المجال#Admin_UserName#** لبيانات اعتماد المسؤول. ترحيل البريد الإلكتروني من Mirapoint باستخدام **mailadmin** لبيانات اعتماد المسؤول **وP\@ssw0rd**، سيبدو ملف CSV كما يلي:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**

لا تدعم بعض أنظمة البريد الإلكتروني المصدر، مثل Courier IMAP، استخدام بيانات اعتماد مسؤول علبة البريد بترحيل علب البريد إلى Microsoft 365. بدلا من ذلك، يمكنك إعداد نظام البريد الإلكتروني المصدر لاستخدام المجلدات المشتركة الظاهرية. باستخدام المجلدات المشتركة الظاهرية، يمكنك استخدام بيانات اعتماد مسؤول علبة البريد للوصول إلى علب بريد المستخدمين على نظام البريد الإلكتروني المصدر. لمزيد من المعلومات حول كيفية تكوين المجلدات المشتركة الظاهرية ل Courier IMAP، راجع ["المجلدات المشتركة](https://go.microsoft.com/fwlink/p/?LinkId=398870)".

بترحيل علب البريد بعد إعداد المجلدات المشتركة الظاهرية على نظام البريد الإلكتروني المصدر، يجب تضمين السمة الاختيارية **UserRoot** في ملف الترحيل. تحدد هذه السمة موقع علبة بريد كل مستخدم في بنية المجلد المشترك الظاهري على نظام البريد الإلكتروني المصدر. على سبيل المثال، المسار إلى علبة بريد Terry هو /users/terry.adams.

فيما يلي مثال على ملف CSV الذي يحتوي على سمة **UserRoot** :

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>الخطوة 3: إنشاء نقطة نهاية ترحيل IMAP

لنقل البريد الإلكتروني بنجاح، يحتاج Microsoft 365 إلى الاتصال بنظام البريد الإلكتروني المصدر والتواصل معه. للقيام بذلك، يستخدم Microsoft 365 نقطة نهاية الترحيل. تحدد نقطة نهاية الترحيل أيضا عدد علب البريد المراد ترحيلها في وقت واحد وعدد علب البريد المراد مزامنتها في وقت واحد أثناء المزامنة التزايدية، والتي تحدث مرة واحدة كل 24 ساعة. لإنشاء نقطة نهاية ترحيل ل IMAP، [اتصل أولا Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

للحصول على قائمة كاملة بأوامر الترحيل، راجع [أوامر cmdlets للتنقل والترحيل](/powershell/exchange/).

لإنشاء نقطة نهاية ترحيل IMAP تسمى "IMAPEndpoint" في Exchange Online PowerShell، قم بتشغيل الأمر التالي:

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

يمكنك أيضا إضافة معلمات لتحديد عمليات الترحيل المتزامنة والترحيلات التزايدية المتزامنة والمنفذ المطلوب استخدامه. يقوم الأمر Exchange Online PowerShell التالي بإنشاء نقطة نهاية ترحيل IMAP تسمى "IMAPEndpoint" التي تدعم 50 عملية ترحيل متزامنة وما يصل إلى 25 مزامنة تزايدية متزامنة. كما أنه يقوم بتكوين نقطة النهاية لاستخدام المنفذ 143 لتشفير TLS.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

لمزيد من المعلومات حول **New-MigrationEndpoint** cmdlet، راجع [New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

قم بتشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول "IMAPEndpoint":

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>الخطوة 4: إنشاء دفعة ترحيل IMAP وبدء تشغيلها

يمكنك استخدام [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) cmdlet لإنشاء دفعة ترحيل لإدارة ترحيل IMAP. يمكنك إنشاء دفعة ترحيل وبدء تشغيلها تلقائيا عن طريق تضمين المعلمة _AutoStart_ . بدلا من ذلك، يمكنك إنشاء دفعة الترحيل ثم بدء تشغيلها بعد ذلك باستخدام[Start-MigrationBatch](/powershell/module/exchange/start-migrationbatch) cmdlet.

سيبدأ أمر PowerShell Exchange Online التالي دفعة الترحيل المسماة "IMAPBatch1" تلقائيا باستخدام نقطة نهاية IMAP التي تسمى "IMAPEndpoint":

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

قم بتشغيل [الأمر cmdlet Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch) لعرض معلومات حول "IMAPBatch1":

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

يمكنك أيضا التحقق من أن الدفعة قد بدأت عن طريق تشغيل الأمر التالي:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>الخطوة 5: توجيه بريدك الإلكتروني إلى Microsoft 365

تستخدم أنظمة البريد الإلكتروني سجل DNS يسمى سجل MX لمعرفة مكان تسليم رسائل البريد الإلكتروني. أثناء عملية ترحيل البريد الإلكتروني، كان سجل MX يشير إلى نظام البريد الإلكتروني المصدر. الآن بعد اكتمال ترحيل البريد الإلكتروني إلى Microsoft 365، حان الوقت لإشارة سجل MX إلى Microsoft 365. يساعد ذلك على التأكد من تسليم البريد الإلكتروني إلى علب بريدك Microsoft 365. من خلال نقل سجل MX، يمكنك أيضا إيقاف تشغيل نظام البريد الإلكتروني القديم عندما تكون جاهزا.

بالنسبة إلى العديد من موفري DNS، هناك إرشادات محددة لتغيير سجل MX. إذا لم يكن موفر DNS الخاص بك مضمنا، أو إذا كنت تريد الحصول على فكرة عن التوجيهات العامة، يتم توفير [إرشادات سجل MX العامة](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide#add-an-mx-record-for-email-outlook-exchange-online) أيضا.

قد يستغرق الأمر ما يصل إلى 72 ساعة حتى تتمكن أنظمة البريد الإلكتروني لعملائك وشركائك من التعرف على سجل MX الذي تم تغييره. انتظر 72 ساعة على الأقل قبل المتابعة إلى المهمة التالية: الخطوة 6: حذف دفعة ترحيل IMAP.

### <a name="step-6-delete-imap-migration-batch"></a>الخطوة 6: حذف دفعة ترحيل IMAP

بعد تغيير سجل MX والتحقق من توجيه كل رسائل البريد الإلكتروني إلى علب بريد Microsoft 365، قم بإعلام المستخدمين بأن البريد الخاص بهم سينتقل إلى Microsoft 365. بعد ذلك، يمكنك حذف دفعة ترحيل IMAP. تحقق مما يلي قبل حذف دفعة الترحيل.

- يستخدم جميع المستخدمين علب بريد Microsoft 365. بعد حذف الدفعة، لا يتم نسخ البريد المرسل إلى علب البريد في Exchange Server المحلية إلى علب بريد Microsoft 365 المقابلة.

- Microsoft 365 تمت مزامنة علب البريد مرة واحدة على الأقل بعد بدء إرسال البريد إليها مباشرة. للقيام بذلك، تأكد من أن القيمة الموجودة في المربع "وقت آخر مزامنة" دفعة الترحيل أحدث مما كانت عليه عند بدء توجيه البريد مباشرة إلى علب بريد Microsoft 365.

لحذف دفعة الترحيل "IMAPBatch1" من Exchange Online PowerShell، قم بتشغيل الأمر التالي:

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

لمزيد من المعلومات حول **Remove-MigrationBatch** cmdlet، راجع [Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

قم بتشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول "IMAPBatch1":

```powershell
Get-MigrationBatch IMAPBatch1"
```

سيرجع الأمر إما دفعة الترحيل بحالة **إزالة**، أو سيرجع خطأ يفيد بتعذر العثور على دفعة الترحيل، مع التحقق من حذف الدفعة.

لمزيد من المعلومات حول **Get-MigrationBatch** cmdlet، راجع [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>راجع أيضًا

[مستكشف أخطاء ترحيل IMAP ومصلحها](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)
