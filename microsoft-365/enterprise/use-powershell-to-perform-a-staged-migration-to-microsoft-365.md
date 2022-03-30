---
title: استخدم PowerShell لتنفيذ عملية ترحيل مرحلي Microsoft 365
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
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: تعرف على كيفية استخدام PowerShell لنقل المحتوى من نظام البريد الإلكتروني المصدر مع مرور الوقت باستخدام الترحيل Microsoft 365.
ms.openlocfilehash: 562dcb8f32a0cd2b8452f2145dcb608dac353e2f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63576904"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>استخدم PowerShell لتنفيذ عملية ترحيل مرحلي Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك ترحيل محتويات علب بريد المستخدمين من نظام البريد الإلكتروني المصدر Microsoft 365 مع مرور الوقت باستخدام الترحيل المرحلة.

تريك هذه المقالة المهام المتدخلة في عملية ترحيل البريد الإلكتروني على مراحل باستخدام Exchange Online PowerShell. يقدم لك الموضوع [، ما تحتاج إلى معرفته حول](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration) الترحيل المراحلي للبريد الإلكتروني، نظرة عامة حول عملية الترحيل. عندما ترتاح في استخدام محتويات هذه المقالة، استخدم هذه المقالة لبدء عملية تهجر علب البريد من نظام بريد إلكتروني إلى آخر.

> [!NOTE]
> يمكنك أيضا استخدام مركز إدارة Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">لتنفيذ</a> الترحيل المراحلي. راجع [تنفيذ عملية ترحيل مرحلي للبريد الإلكتروني Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

الوقت المقدر لإكمال هذه المهمة: 2-5 دقائق لإنشاء دفعة ترحيل. بعد بدء دفعة الترحيل، ستختلف مدة الترحيل استنادا إلى عدد علب البريد في الدفعة وحجم كل علبة بريد و سعة الشبكة المتوفرة. للحصول على معلومات حول عوامل أخرى تؤثر على الوقت المستغرق لترحيل علب البريد Microsoft 365، راجع [أداء الترحيل](/Exchange/mailbox-migration/office-365-migration-best-practices).

يجب تعيين أذونات لك قبل تنفيذ هذا الإجراء أو الإجراءات. لمعرفة الأذونات التي تحتاج إليها، راجع إدخال "الترحيل" في الموضوع [أذونات المستلمين](/exchange/recipients-permissions-exchange-2013-help) .

لاستخدام Exchange Online Cmdlets في PowerShell، ستحتاج إلى تسجيل الدخول واستيراد cmdlets إلى جلسة Windows PowerShell المحلية. راجع [الاتصال Exchange Online استخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على الإرشادات.

للحصول على قائمة كاملة من أوامر الترحيل، راجع [أوامر cmdlets](/powershell/exchange/) الخاصة بالنقل وا الترحيل.

## <a name="migration-steps"></a>خطوات الترحيل

### <a name="step-1-prepare-for-a-staged-migration"></a>الخطوة 1: التحضير لهجرة مرحلية

قبل ترحيل علب البريد إلى Microsoft 365 الترحيل المراحلي، يجب إدخال بعض التغييرات على بيئة Exchange الخاصة بك.

 **تكوين Outlook في** أي مكان على موقعك المحلي Exchange Server تستخدم خدمة ترحيل البريد الإلكتروني Outlook من أي مكان (المعروف أيضا باسم RPC عبر HTTP)، للاتصال ببريدك المحلي Exchange Server. للحصول على معلومات حول كيفية إعداد Outlook أي مكان Exchange Server 2007، Exchange 2003، راجع ما يلي:

- [Exchange 2007: كيفية تمكين Outlook أي مكان](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [كيفية تكوين Outlook أي مكان باستخدام Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> يجب عليك استخدام شهادة صادرة عن مرجع ممصادقة موثوق به (CA) مع تكوين Outlook أي مكان. Outlook في أي مكان باستخدام شهادة موقعة ذاتيا. لمزيد من المعلومات، [راجع كيفية تكوين SSL Outlook أي مكان](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **اختياري: تحقق من أنه** يمكنك الاتصال Exchange باستخدام Outlook في أي مكان جرب أحد الأساليب التالية لاختبار إعدادات الاتصال.

- استخدم Outlook من خارج شبكة الشركة للاتصال لعلبة بريدك المحلية Exchange البريد.

- استخدم [محلل الاتصال عن بعد من Microsoft](https://https://testconnectivity.microsoft.com/) لاختبار إعدادات الاتصال. استخدم Outlook أي مكان (RPC عبر HTTP) أو Outlook الاكتشاف التلقائي.

- تشغيل الأوامر التالية في Exchange Online PowerShell:

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **تعيين الأذونات** يجب أن يكون لحساب المستخدم المحلي الذي تستخدمه للاتصال بمنظمة Exchange المحلية (تسمى أيضا مسؤول الترحيل) الأذونات اللازمة للوصول إلى علب البريد المحلية التي تريد ترحيلها إلى Microsoft 365. يتم استخدام حساب المستخدم هذا عند الاتصال لنظام البريد الإلكتروني الخاص بك عن طريق إنشاء نقطة نهاية ترحيل لاحقا في هذا الإجراء الخطوة [3: إنشاء نقطة نهاية ترحيل](#step-3-create-a-migration-endpoint).

لترحيل علب البريد، يجب أن يكون لدى المسؤول إحدى مجموعات الأذونات التالية:

- كن عضوا في مجموعة **"مسؤولو المجالات** " في Active Directory في المؤسسة المحلي.

    أو

- أن يتم تعيين إذن **FullAccess لكل** علبة بريد في الموقع وإذن **WriteProperty** لتعديل الخاصية **TargetAddress** على حسابات المستخدمين في الموقع.

    أو

- تعيين الإذن **"** تلقي ك" في قاعدة بيانات علبة البريد المحلية التي تخزن علب بريد المستخدمين والإذن **WriteProperty** لتعديل الخاصية **TargetAddress** على حسابات المستخدمين المحلية.

للحصول على إرشادات حول كيفية تعيين هذه الأذونات، راجع تعيين أذونات لترحيل علب البريد [إلى Microsoft 365](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **تعطيل المراسلة الموحدة (UM)** إذا تم تشغيل UM لعلب البريد المحلية التي تقوم ب ترحيلها، ف قم إيقاف تشغيل UM قبل الترحيل. قم تشغيل UM لعلب البريد بعد اكتمال الترحيل. للحصول على خطوات حول كيفية القيام بذلك، يمكنك الاطلاع على المراسلة [الموحدة القابلة للانعقاد](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **استخدم مزامنة الدليل لإنشاء مستخدمين جدد في Microsoft 365.** يمكنك استخدام مزامنة الدليل لإنشاء جميع المستخدمين في مؤسستك Microsoft 365.

ستحتاج إلى ترخيص المستخدمين بعد إنشائهم. لديك 30 يوما لإضافة التراخيص بعد إنشاء المستخدمين. للحصول على خطوات لإضافة التراخيص، راجع [الخطوة 8: إكمال مهام ما بعد الترحيل](#step-8-complete-post-migration-tasks).

 يمكنك استخدام أداة Microsoft Azure Active Directory (Azure AD) أو Microsoft Azure AD Sync Services لمزامنة المستخدمين المحليين وإنشاءهم في Microsoft 365. بعد ترحيل علب البريد إلى Microsoft 365، يمكنك إدارة حسابات المستخدمين في مؤسستك المحلية، ومزامنتها مع Microsoft 365 الخاصة بك. لمزيد من المعلومات، راجع [تكامل البيانات](/previous-versions/azure/azure-services/jj573653(v=azure.100)) .

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>الخطوة 2: إنشاء ملف CSV دفعة ترحيل مرحلة

بعد تحديد المستخدمين الذين تريد ترحيل علب بريدهم المحلية إلى Microsoft 365، يمكنك استخدام ملف قيم مفصولة بفصول (CSV) لإنشاء دفعة ترحيل. يحتوي كل صف في ملف CSV Microsoft 365 يستخدمه المستخدم لتشغيل الترحيل، على معلومات حول علبة بريد في الموقع.

> [!NOTE]
> لا يوجد حد لعدد علب البريد التي يمكنك ترحيلها إلى Microsoft 365 الترحيل المرحلة. يمكن أن يحتوي ملف CSV الخاص بدفعة ترحيل على 2000 صف كحد أقصى. لترحيل أكثر من 2000 علبة بريد، قم بإنشاء ملفات CSV إضافية واستخدام كل ملف لإنشاء دفعة ترحيل جديدة.

 **السمات المعتمدة**

يدعم ملف CSV ل الترحيل المراحلي السمات الثلاث التالية. يتوافق كل صف في ملف CSV مع علبة بريد ويجب أن يحتوي على قيمة لكل سمة من هذه السمات.

|**السمة**|**الوصف**|**مطلوب؟**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |يحدد عنوان البريد الإلكتروني SMTP الأساسي، على سبيل pilarp@contoso.com، لعلب البريد المحلية.  <br/> استخدم عنوان SMTP الأساسي لعلب البريد المحلية وليس لم تعريفات المستخدمين من Microsoft 365. على سبيل المثال، إذا كان المجال المسمى contoso.com ولكن مجال البريد الإلكتروني في Microsoft 365 يسمى service.contoso.com، يمكنك استخدام اسم مجال contoso.com عناوين البريد الإلكتروني في ملف CSV.  <br/> |مطلوب  <br/> |
|كلمة المرور  <br/> |كلمة المرور التي سيتم تعيينها لعلبة بريد Microsoft 365 الجديدة. تنطبق أيضا أي قيود كلمات مرور يتم تطبيقها على Microsoft 365 المؤسسة على كلمات المرور المضمنة في ملف CSV.  <br/> |اختياري  <br/> |
|ForceChangePassword  <br/> |يحدد ما إذا كان يجب على المستخدم تغيير كلمة المرور في المرة الأولى التي يقوم فيها تسجيل الدخول إلى علبة بريده الجديدة Microsoft 365 البريد. استخدم **True** أو **False** لقيمة هذه المعلمة. <br/> > [!NOTE]> إذا قمت بتنفيذ حل تسجيل الدخول الفردي (SSO) من خلال نشر خدمات اتحاد Active Directory (AD FS) أو أكثر في مؤسستك المحلية، فيجب استخدام **False** لقيمة السمة **ForceChangePassword** .          |اختياري  <br/> |

 **تنسيق الملف CSV**

في ما يلي مثال على تنسيق ملف CSV. في هذا المثال، يتم ترحيل ثلاث علب بريد المحلية إلى Microsoft 365.

يسرد الصف الأول أو صف الرأس، من ملف CSV أسماء السمات أو الحقول المحددة في الصفوف التالية. يتم الفصل بين كل اسم من أسماء السمات بفاصلة.

```powershell
EmailAddress,Password,ForceChangePassword
pilarp@contoso.com,Pa$$w0rd,False
tobyn@contoso.com,Pa$$w0rd,False
briant@contoso.com,Pa$$w0rd,False
```

يمثل كل صف أسفل صف الرأس مستخدما واحدا ويزوده بالمعلومات التي سيتم استخدامها لترحيل علبة بريد المستخدم. يجب أن تكون قيم السمات في كل صف بنفس ترتيب أسماء السمات في صف الرأس.

استخدم أي محرر نص أو تطبيق مثل Excel ، لإنشاء ملف CSV. احفظ الملف كملف .csv أو .txt.

> [!NOTE]
> إذا كان الملف CSV يحتوي على أحرف غير ASCII أو أحرف خاصة، فقم بحفظ ملف CSV بترميز UTF-8 أو بترميز Unicode آخر. استنادا إلى التطبيق، قد يكون حفظ ملف CSV باستخدام ترميز UTF-8 أو ترميز Unicode آخر أسهل عندما تطابق لغات النظام المحلية للكمبيوتر اللغة المستخدمة في ملف CSV.

### <a name="step-3-create-a-migration-endpoint"></a>الخطوة 3: إنشاء نقطة نهاية ترحيل

لترحيل البريد الإلكتروني بنجاح، Microsoft 365 تحتاج إلى الاتصال ونظام البريد الإلكتروني المصدر والتواصل معه. للقيام بذلك، Microsoft 365 نقطة نهاية الترحيل. لإنشاء نقطة نهاية ترحيل Outlook أي مكان باستخدام PowerShell، ل الترحيل المراحلي، اتصل أولا [Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

للحصول على قائمة كاملة من أوامر الترحيل، راجع [أوامر cmdlets](/powershell/exchange/) الخاصة بالنقل وا الترحيل.

لإنشاء نقطة نهاية ترحيل Outlook أي مكان تسمى "StagedEndpoint" في Exchange Online PowerShell، قم بتشغيل الأوامر التالية:

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

لمزيد من المعلومات حول **الأمر cmdlet ل New-MigrationEndpoint** ، [راجعNew-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> يمكن **استخدام الأمر cmdlet New-MigrationEndpoint** لتحديد قاعدة بيانات للخدمة لاستخدامها باستخدام **الخيار -TargetDatabase** . بخلاف ذلك، يتم تعيين قاعدة بيانات عشوائيا من موقع خدمات Active Directory Federation Services (AD FS) 2.0 حيث توجد علبة بريد الإدارة.

#### <a name="verify-it-worked"></a>التحقق من عملها

في Exchange Online PowerShell، تشغيل الأمر التالي لعرض معلومات حول نقطة نهاية الترحيل "StagedEndpoint":

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>الخطوة 4: إنشاء دفعة ترحيل مرحلة وبدء تشغيلها

يمكنك استخدام **الأمر cmdlet New-MigrationBatch** في Exchange Online PowerShell لإنشاء دفعة ترحيل ل الترحيل كلي. يمكنك إنشاء دفعة ترحيل وبدء تشغيلها تلقائيا من خلال بما في ذلك _معلمة التشغيل_ التلقائي. بدلا من ذلك، يمكنك إنشاء دفعة الترحيل ثم بدء تشغيلها يدويا بعد ذلك باستخدام **الأمر cmdlet Start-MigrationBatch** . ينشئ هذا المثال دفعة ترحيل تسمى "StagedBatch1" ويستخدم نقطة نهاية الترحيل التي تم إنشاؤها في الخطوة السابقة.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

ينشئ هذا المثال أيضا دفعة ترحيل تسمى "StagedBatch1" ويستخدم نقطة نهاية الترحيل التي تم إنشاؤها في الخطوة السابقة. نظرا لعدم  _تضمين_ معلمة التشغيل التلقائي، يجب بدء دفعة الترحيل يدويا على لوحة معلومات الترحيل أو باستخدام **الأمر cmdlet Start-MigrationBatch** . كما ذكر سابقا، يمكن أن توجد دفعة ترحيل كلي واحدة فقط في كل مرة.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>التحقق من عملها

تشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول "StagedBatch1":

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

يمكنك أيضا التحقق من أن الدفعة قد بدأت عن طريق تشغيل الأمر التالي:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

لمزيد من المعلومات حول **الأمر cmdlet Get-MigrationBatch** ، [راجعGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>الخطوة 5: تحويل علب البريد المحلية إلى مستخدمين لتمكين البريد

بعد ترحيل دفعة من علب البريد بنجاح، ستحتاج إلى طريقة تسمح للمستخدمين ب الوصول إلى بريدهم. لدى المستخدم الذي تم ترحيل علبة بريده الآن علبة بريد في الموقع و علبة بريد في Microsoft 365. سيتوقف المستخدمون الذين لديهم علبة بريد في Microsoft 365 تلقي بريد جديد في علبة البريد الخاصة بهم.

نظرا لعدم انتهائك من الترحيلات، لست جاهزا بعد لتوجيه جميع المستخدمين Microsoft 365 بريدهم الإلكتروني. فماذا تفعل لهؤلاء الأشخاص الذين لديهم الاثنين؟ ما يمكنك فعله هو تغيير علب البريد المحلية التي قمت بترحيلها بالفعل إلى المستخدمين الممكنين للبريد. عند التغيير من علبة بريد إلى مستخدم يقوم بتمكين البريد، يمكنك توجيه المستخدم Microsoft 365 بريده الإلكتروني بدلا من الذهاب إلى علبة البريد الخاصة به في الموقع.

هناك سبب آخر مهم لتحويل علب البريد المحلية إلى مستخدمين تم تمكين البريد له وهو الاحتفاظ عناوين الوكيل من علب بريد Microsoft 365 عن طريق نسخ عناوين الوكيل إلى المستخدمين الذين تم تمكين البريد لديهم. يتيح لك ذلك إدارة المستخدمين المستندين إلى السحابة من مؤسستك في الموقع باستخدام Active Directory. بالإضافة إلى ذلك، إذا قررت إلغاء تشغيل مؤسسة Exchange Server المحلية بعد ترحيل كل علب البريد إلى Microsoft 365، فإن عناوين الوكيل التي نسختها إلى المستخدمين الذين تم تمكينهم للبريد ستبقى في Active Directory الداخلي.

### <a name="step-6-delete-a-staged-migration-batch"></a>الخطوة 6: حذف دفعة ترحيل مرحلي

 بعد نجاح ترحيل كل علب البريد في دفعة ترحيل، وتحويل علب البريد المحلية في الدفعة إلى مستخدمين تم تمكينهم للبريد، تكون جاهزا لحذف دفعة ترحيل مرحلي. تأكد من التحقق من إعادة توجيه البريد إلى Microsoft 365 البريد في دفعة الترحيل. عند حذف دفعة ترحيل مرحلي، تقوم خدمة الترحيل بتنظيف أي سجلات مرتبطة بدفعة الترحيل وحذف دفعة الترحيل.

لحذف دفعة الترحيل "StagedBatch1" Exchange Online PowerShell، قم بتشغيل الأمر التالي.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

لمزيد من المعلومات حول **الأمر cmdlet Remove-MigrationBatch** ، [راجعRemove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>التحقق من عملها

تشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول "IMAPBatch1":

```powershell
Get-MigrationBatch StagedBatch1
```

سيرجع الأمر إما دفعة الترحيل التي لها حالة إزالة، أو سيرجع رسالة خطأ تفيد بأنه لا يمكن العثور على دفعة الترحيل، مع التحقق من حذف الدفعة.

لمزيد من المعلومات حول **الأمر cmdlet Get-MigrationBatch** ، [راجعGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>الخطوة 7: تعيين التراخيص Microsoft 365 المستخدمين

تنشيط Microsoft 365 حسابات المستخدمين للحسابات التي تم ترحيلها من خلال تعيين التراخيص. إذا لم يتم تعيين ترخيص، يتم تعطيل علبة البريد عند انتهاء فترة السماح (30 يوما). لتعيين ترخيص في مركز مسؤولي Microsoft 365، راجع تعيين تراخيص أو [عدم تعيينها](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>الخطوة 8: إكمال مهام ما بعد الترحيل

- **قم بإنشاء سجل DNS ل Autodiscover حتى يمكن للمستخدمين الوصول بسهولة إلى علب البريد الخاصة بهم.** بعد ترحيل كل علب البريد المحلية إلى Microsoft 365، يمكنك تكوين سجل DNS الاكتشاف التلقائي لمنظمتك في Microsoft 365 لتمكين المستخدمين من الاتصال بسهولة لعلب بريد Microsoft 365 الجديدة مع عملاء Outlook والأجهزة المحمولة. يجب أن يستخدم سجل DNS ل Autodiscover الجديد مساحة الاسم نفسها التي تستخدمها Microsoft 365 مؤسستك. على سبيل المثال، إذا كانت مساحة الاسم المستندة إلى السحابة cloud.contoso.com، يكون سجل DNS الذي تريد إنشاؤه في الاكتشاف التلقائي autodiscover.cloud.contoso.com.

    Microsoft 365 سجل CNAME لتطبيق خدمة الاكتشاف التلقائي للعملاء Outlook الجوال. يجب أن يحتوي سجل CNAME ل Autodiscover على المعلومات التالية:

  - **الاسم المستعار:** autodiscover

  - **الهدف: autodiscover.outlook.com**

    لمزيد من المعلومات، راجع [إضافة سجلات DNS لتوصيل مجالك](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **اسحب الخوادم Exchange في الموقع.** بعد التحقق من توجيه كل رسائل البريد الإلكتروني مباشرة إلى علب بريد Microsoft 365، ولم تعد بحاجة إلى الاحتفاظ بمنظمتك المحلية للبريد الإلكتروني أو عدم التخطيط لتطبيق حل SSO، يمكنك إزالة تثبيت Exchange من الخوادم وإزالة مؤسسة Exchange المحلية.

    لمزيد من المعلومات، راجع ما يلي:

  - [تعديل أو Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [كيفية إزالة Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [كيفية إلغاء تثبيت Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
