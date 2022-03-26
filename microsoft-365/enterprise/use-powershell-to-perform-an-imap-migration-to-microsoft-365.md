---
title: استخدم PowerShell لتنفيذ عملية ترحيل IMAP Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية استخدام PowerShell لتنفيذ ترحيل بروتوكول الوصول إلى البريد عبر الإنترنت (IMAP) Microsoft 365.
ms.openlocfilehash: 0c546782e81a399f092c8c7878b52c419adee799
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63569608"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>استخدم PowerShell لتنفيذ عملية ترحيل IMAP Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

كجزء من عملية نشر Microsoft 365، يمكنك اختيار ترحيل محتويات علب بريد المستخدمين من خدمة البريد الإلكتروني لبروتوكول الوصول إلى البريد عبر الإنترنت (IMAP) إلى Microsoft 365. تريك هذه المقالة المهام المتعلقة بترزيل IMAP عبر البريد الإلكتروني باستخدام Exchange Online PowerShell.

> [!NOTE]
> يمكنك أيضا استخدام مركز إدارة Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">لتنفيذ</a> ترحيل IMAP. راجع [ترحيل علب بريد IMAP](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

الوقت المقدر لإكمال هذه المهمة: 2-5 دقائق لإنشاء دفعة ترحيل. بعد بدء دفعة الترحيل، ستختلف مدة الترحيل استنادا إلى عدد علب البريد في الدفعة وحجم كل علبة بريد و سعة الشبكة المتوفرة. للحصول على معلومات حول عوامل أخرى تؤثر على الوقت المستغرق لترحيل علب البريد Microsoft 365، راجع [أداء الترحيل](/Exchange/mailbox-migration/office-365-migration-best-practices).

يجب تعيين أذونات لك قبل تنفيذ هذا الإجراء أو الإجراءات. لمعرفة الأذونات التي تحتاج إليها، راجع إدخال "الترحيل" في جدول في الموضوع [أذونات المستلمين](/exchange/recipients-permissions-exchange-2013-help) .

لاستخدام Exchange Online Cmdlets في PowerShell، ستحتاج إلى تسجيل الدخول واستيراد cmdlets إلى جلسة Windows PowerShell المحلية. راجع [الاتصال Exchange Online استخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على الإرشادات.

للحصول على قائمة كاملة من أوامر الترحيل، راجع [أوامر cmdlets](/powershell/exchange/) الخاصة بالنقل وا الترحيل.

تنطبق القيود التالية على ترحيلات IMAP:

- يمكن ترحيل العناصر الموجودة في علبة الوارد الخاصة بالمستخدم أو مجلدات البريد الأخرى فقط. لا يمكنك ترحيل جهات الاتصال أو عناصر التقويم أو المهام.

- يمكن ترحيل 500000 عنصر كحد أقصى من علبة بريد المستخدم.

- الحد الأقصى لحجم الرسالة التي يمكن ترحيلها هو 35 مبايت.

## <a name="migration-steps"></a>خطوات الترحيل

### <a name="step-1-prepare-for-an-imap-migration"></a>الخطوة 1: التحضير  الترحيل IMAP
<a name="BK_Step1"> </a>

- **إذا كان لديك مجال خاص بك في مؤسسة IMAP، ف أضفه كمجال مقبول Microsoft 365 مؤسستك.** إذا كنت تريد استخدام المجال نفسه الذي تملكه بالفعل لعلب بريدك Microsoft 365، يجب أولا إضافته كمجال مقبول Microsoft 365. بعد إضافته، يمكنك إنشاء المستخدمين في Microsoft 365. لمزيد من المعلومات، راجع [التحقق من مجالك](../admin/setup/add-domain.md).

- **أضف كل مستخدم Microsoft 365 بحيث يكون لديه علبة بريد.** للحصول على الإرشادات، [راجعمعادة المستخدمين Microsoft 365 للأعمال](../admin/add-users/add-users.md).

- **احصل على FQDN من خادم IMAP**. يجب توفير اسم المجال المؤهل بالكامل (FQDN) (يسمى أيضا اسم الكمبيوتر الكامل) للخادم IMAP الذي سيتم ترحيل بيانات علبة البريد منه عند إنشاء نقطة نهاية ترحيل IMAP. استخدم عميل IMAP أو أمر PING للتحقق من إمكانية استخدام FQDN للاتصال بخادم IMAP عبر الإنترنت.

- **قم بتكوين جدار الحماية للسماح باتصالات IMAP**. قد تحتاج إلى فتح المنافذ في جدار حماية المؤسسة التي تستضيف خادم IMAP حتى يتم السماح لحركة مرور الشبكة التي تنشأ من مركز بيانات Microsoft أثناء الترحيل بإدخال المؤسسة التي تستضيف خادم IMAP. للحصول على قائمة عناوين IP المستخدمة بواسطة مراكز بيانات Microsoft، راجع Exchange Online [عناوين URL وعناوين IP النطاقات](./urls-and-ip-address-ranges.md).

- **قم بتعيين أذونات حساب المسؤول للوصول إلى علب البريد في مؤسسة IMAP**. في حال استخدام بيانات اعتماد المسؤول في ملف CSV، يجب أن يكون للحساب الذي تستخدمه الأذونات اللازمة للوصول إلى علب البريد المحلية. يتم تحديد الأذونات المطلوبة للوصول إلى علب بريد المستخدمين بواسطة خادم IMAP معين.

- **لاستخدام Exchange Online Cmdlets في PowerShell**، ستحتاج إلى تسجيل الدخول واستيراد cmdlets إلى جلسة عمل Windows PowerShell المحلية. راجع [الاتصال Exchange Online استخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على الإرشادات.

    للحصول على قائمة كاملة من أوامر الترحيل، راجع [أوامر cmdlets](/powershell/exchange/) الخاصة بالنقل وا الترحيل.

- **تحقق من أنه يمكنك الاتصال بخادم IMAP**. تشغيل الأمر التالي في Exchange Online PowerShell لاختبار إعدادات الاتصال إلى خادم IMAP.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    بالنسبة لقيمة معلمة المنفذ، من المعتاد استخدام 143 للاتصالات غير مشفرة أو اتصالات أمان طبقة النقل (TLS) واستخدام 993 لاتصالات SSL.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>الخطوة 2: إنشاء ملف CSV دفعة ترحيل IMAP

حدد مجموعة المستخدمين الذين تريد ترحيل علب بريدهم في دفعة ترحيل IMAP. يحتوي كل صف في ملف CSV على المعلومات الضرورية للاتصال علبة بريد في نظام مراسلة IMAP.

في ما يلي السمات المطلوبة لكل مستخدم:

- **يحدد EmailAddress** "عنوان تعريف المستخدم" لعلبة بريد Microsoft 365 المستخدم.

- **يحدد UserName** اسم تسجيل الدخول للحساب الذي يجب استخدامه للوصول إلى علبة البريد على خادم IMAP.

- **تحدد** كلمة المرور كلمة المرور للحساب في **العمود اسم** المستخدم.

في ما يلي مثال على تنسيق ملف CSV. في هذا المثال، يتم ترحيل ثلاث علب بريد:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

بالنسبة إلى السمة **UserName** ، بالإضافة إلى اسم المستخدم، يمكنك استخدام بيانات اعتماد حساب تم تعيين الأذونات اللازمة له للوصول إلى علب البريد على خادم IMAP، فيما يلي بعض التنسيقات المحددة المستخدمة لبعض خوادم IMAP:

 **Microsoft Exchange:**

إذا كنت تقوم بتهجر البريد الإلكتروني من تنفيذ IMAP ل Microsoft Exchange، فاستخدم التنسيق **Domain/Admin_UserName/User_UserName** ل السمة **UserName** في ملف CSV. لنقل أنك تقوم بتهريب البريد الإلكتروني من Exchange إلى تيري أدامز و"آن بيبي" و"بول كانون". لديك حساب مسؤول البريد، حيث يكون اسم المستخدم **mailadmin** وكلمة المرور **Pssw0rd\@**. إليك كيف سيبدو ملف CSV:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**

بالنسبة إلى خوادم IMAP التي تدعم المصادقة البسيطة وطبقة الأمان (SASL)، مثل خادم Dovecot IMAP، استخدم التنسيق **User_UserName*Admin_UserName**، حيث تكون النجمة ( * ) حرف فاصل قابل للتكوين. لنقل أنك تقوم بتهجر البريد الإلكتروني لنفس المستخدمين من خادم Dovecot IMAP باستخدام بيانات اعتماد المسؤول **mailadmin** و **\@Pssw0rd**. إليك كيف سيبدو ملف CSV:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**

إذا كنت تقوم بتهجر البريد الإلكتروني من خادم رسائل Mirapoint، فاستخدم التنسيق #user **البريد الإلكتروني#Admin_UserName# للحصول على بيانات اعتماد المسؤول.\@** لترحيل البريد الإلكتروني من Mirapoint باستخدام بيانات اعتماد المسؤول **mailadmin** **\@و Pssw0rd**، سيبدو ملف CSV كما يلي:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**

لا تدعم بعض أنظمة البريد الإلكتروني المصدر، مثل Courier IMAP، استخدام بيانات اعتماد مسؤول علب البريد لترحيل علب البريد إلى Microsoft 365. بدلا من ذلك، يمكنك إعداد نظام البريد الإلكتروني المصدر لاستخدام المجلدات المشتركة الظاهرية. باستخدام المجلدات المشتركة الظاهرية، يمكنك استخدام بيانات اعتماد مسؤول علبة البريد للوصول إلى علب بريد المستخدمين على نظام البريد الإلكتروني المصدر. لمزيد من المعلومات حول كيفية تكوين المجلدات المشتركة الظاهرية ل Courier IMAP، راجع [المجلدات المشتركة](https://go.microsoft.com/fwlink/p/?LinkId=398870).

لترحيل علب البريد بعد إعداد المجلدات المشتركة الظاهرية على نظام البريد الإلكتروني المصدر، يجب تضمين السمة الاختيارية **UserRoot** في ملف الترحيل. تحدد هذه السمة موقع علبة بريد كل مستخدم في بنية المجلدات المشتركة الظاهرية على نظام البريد الإلكتروني المصدر. على سبيل المثال، المسار إلى علبة بريد تيري هو /users/terry.adams.

فيما يلي مثال لملف CSV يحتوي على السمة **UserRoot** :

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>الخطوة 3: إنشاء نقطة نهاية ترحيل IMAP

لترحيل البريد الإلكتروني بنجاح، Microsoft 365 تحتاج إلى الاتصال ونظام البريد الإلكتروني المصدر والتواصل معه. للقيام بذلك، Microsoft 365 نقطة نهاية الترحيل. تعرف نقطة نهاية الترحيل أيضا عدد علب البريد التي سيتم ترحيلها في الوقت نفسه وعدد علب البريد التي تريد مزامنتها في الوقت نفسه أثناء المزامنة التزايدية، التي تحدث مرة واحدة كل 24 ساعة. لإنشاء نقطة نهاية ترحيل ل ترحيل IMAP، اتصل أولا [ب Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

للحصول على قائمة كاملة من أوامر الترحيل، راجع [أوامر cmdlets](/powershell/exchange/) الخاصة بالنقل وا الترحيل.

لإنشاء نقطة نهاية ترحيل IMAP التي تسمى "IMAPEndpoint" في Exchange Online PowerShell، قم بتشغيل الأمر التالي:

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

يمكنك أيضا إضافة معلمات لتحديد الترحيلات المتزامنة وا الترحيلات التزايدية المتزامنة والميناء الذي يجب استخدامه. ينشئ Exchange Online PowerShell نقطة نهاية ترحيل IMAP تسمى "IMAPEndpoint" تدعم 50 عملية ترحيل متزامنة وما يصل إلى 25 عملية مزامنة تزايدية متزامنة. كما تقوم أيضا بتكوين نقطة النهاية لاستخدام المنفذ 143 لتشفير TLS.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

لمزيد من المعلومات حول **الأمر cmdlet ل New-MigrationEndpoint** ، [راجعNew-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>التحقق من عملها

تشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول "IMAPEndpoint":

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>الخطوة 4: إنشاء دفعة ترحيل IMAP وبدء تشغيلها

يمكنك استخدام [الأمر cmdlet New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) لإنشاء دفعة ترحيل ترحيل IMAP. يمكنك إنشاء دفعة ترحيل وبدء تشغيلها تلقائيا من خلال بما في ذلك _معلمة التشغيل_ التلقائي. بدلا من ذلك، يمكنك إنشاء دفعة الترحيل ثم بدء تشغيلها بعد ذلك باستخدام الأمر cmdlet الخاص [بStart-MigrationBatch](/powershell/module/exchange/start-migrationbatch) .

سيبدأ Exchange Online PowerShell دفعة الترحيل التي تسمى "IMAPBatch1" تلقائيا باستخدام نقطة نهاية IMAP التي تسمى "IMAPEndpoint":

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>التحقق من عملها

تشغيل [الأمر Cmdlet Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch) لعرض معلومات حول "IMAPBatch1":

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

يمكنك أيضا التحقق من أن الدفعة قد بدأت عن طريق تشغيل الأمر التالي:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>الخطوة 5: توجيه البريد الإلكتروني إلى Microsoft 365

تستخدم أنظمة البريد الإلكتروني سجل DNS يسمى سجل MX لمعرفة مكان تسليم رسائل البريد الإلكتروني. أثناء عملية ترحيل البريد الإلكتروني، كان سجل MX يشير إلى نظام البريد الإلكتروني المصدر. الآن وقد اكتملت عملية ترحيل البريد الإلكتروني Microsoft 365، حان وقت الإشارة إلى سجل MX Microsoft 365. يساعد ذلك على التأكد من تسليم البريد الإلكتروني إلى علب بريدك Microsoft 365 البريد. من خلال نقل سجل MX، يمكنك أيضا إيقاف تشغيل نظام البريد الإلكتروني القديم عندما تكون جاهزا.

بالنسبة إلى العديد من موفري DNS، توجد إرشادات محددة لتغيير سجل MX. إذا لم يكن موفر DNS مضمنا، أو إذا كنت تريد الحصول على إرشادات عامة، يتم أيضا توفير إرشادات عامة حول سجل [MX](https://go.microsoft.com/fwlink/?LinkId=397449) .

قد يستغرق الأمر ما يصل إلى 72 ساعة لكي تتعرف أنظمة البريد الإلكتروني لعملائك وشركائك على سجل MX الذي تم تغييره. انتظر 72 ساعة على الأقل قبل المتابعة إلى المهمة التالية: الخطوة 6: حذف دفعة ترحيل IMAP.

### <a name="step-6-delete-imap-migration-batch"></a>الخطوة 6: حذف دفعة ترحيل IMAP

بعد تغيير سجل MX والتحقق من توجيه كل رسائل البريد الإلكتروني Microsoft 365 علب البريد، قم بإعلام المستخدمين بأن بريدهم سيتم Microsoft 365. بعد ذلك، يمكنك حذف دفعة ترحيل IMAP. تحقق مما يلي قبل حذف دفعة الترحيل.

- يستخدم جميع المستخدمين علب Microsoft 365 البريد. بعد حذف الدفعة، لا يتم نسخ البريد المرسل إلى علب البريد على Exchange Server المحلية إلى علب البريد Microsoft 365 المقابلة.

- Microsoft 365 علب البريد مرة واحدة على الأقل بعد بدء إرسال البريد إليها مباشرة. للقيام بذلك، تأكد من أن القيمة في المربع آخر وقت متزامن بدفعة الترحيل أحدث من تلك التي كانت عند بدء توجيه البريد مباشرة إلى علب البريد Microsoft 365 البريد.

لحذف دفعة الترحيل "IMAPBatch1" من Exchange Online PowerShell، قم بتشغيل الأمر التالي:

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

لمزيد من المعلومات حول **الأمر cmdlet Remove-MigrationBatch** ، [راجعRemove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>التحقق من عملها

تشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول "IMAPBatch1":

```powershell
Get-MigrationBatch IMAPBatch1"
```

سيرجع الأمر إما دفعة الترحيل التي لها حالة إزالة، أو سيرجع رسالة خطأ تفيد بأنه لا يمكن العثور على دفعة الترحيل، مع التحقق من حذف الدفعة.

لمزيد من المعلومات حول **الأمر cmdlet Get-MigrationBatch** ، [راجعGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>راجع أيضًا

[م استكشاف مشاكل ترحيل IMAP ومشكلاتها](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)