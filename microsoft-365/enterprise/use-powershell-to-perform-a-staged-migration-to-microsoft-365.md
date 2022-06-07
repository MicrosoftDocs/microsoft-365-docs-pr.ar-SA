---
title: استخدم PowerShell لإجراء ترحيل مرحلي إلى Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/07/2022
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
description: تعرف على كيفية استخدام PowerShell لنقل المحتوى من نظام بريد إلكتروني مصدر بمرور الوقت باستخدام ترحيل مرحلي إلى Microsoft 365.
ms.openlocfilehash: 361bf6e2bdfc58ea79f73c3596622ae96b420648
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930736"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>استخدم PowerShell لإجراء ترحيل مرحلي إلى Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise وOffice 365 Enterprise.*

يمكنك ترحيل محتويات علب بريد المستخدمين من نظام بريد إلكتروني مصدر إلى Microsoft 365 بمرور الوقت باستخدام ترحيل مرحلي.

ترشدك هذه المقالة عبر المهام المضمنة في ترحيل البريد الإلكتروني المرحلي باستخدام Exchange Online PowerShell. يوفر لك الموضوع، [الذي تحتاج إلى معرفته حول الترحيل المرحلي للبريد الإلكتروني](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration)، نظرة عامة على عملية الترحيل. عندما تتعرف على محتويات هذه المقالة، استخدم هذه المقالة لبدء ترحيل علب البريد من نظام بريد إلكتروني إلى آخر.

> [!NOTE]
> يمكنك أيضا استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> لإجراء الترحيل المرحلي. راجع [إجراء ترحيل مرحلي للبريد الإلكتروني إلى Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

الوقت المقدر لإكمال هذه المهمة: 2-5 دقائق لإنشاء دفعة ترحيل. بعد بدء دفعة الترحيل، ستختلف مدة الترحيل استنادا إلى عدد علب البريد في الدفعة وحجم كل علبة بريد وسعة الشبكة المتوفرة. للحصول على معلومات حول العوامل الأخرى التي تؤثر على المدة التي يستغرقها ترحيل علب البريد إلى Microsoft 365، راجع ["أداء الترحيل](/Exchange/mailbox-migration/office-365-migration-best-practices)".

يجب تعيين أذونات لك قبل أن تتمكن من تنفيذ هذا الإجراء أو الإجراءات. للاطلاع على الأذونات التي تحتاجها، راجع إدخال "الترحيل" في موضوع ["أذونات المستلمين](/exchange/recipients-permissions-exchange-2013-help) ".

لاستخدام أوامر Cmdlets PowerShell في Exchange Online، تحتاج إلى تسجيل الدخول واستيراد أوامر cmdlets إلى جلسة عمل Windows PowerShell المحلية. راجع [الاتصال ب Exchange Online باستخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على الإرشادات.

للحصول على قائمة كاملة بأوامر الترحيل، راجع [أوامر cmdlets للتنقل والترحيل](/powershell/exchange/).

## <a name="migration-steps"></a>خطوات الترحيل

### <a name="step-1-prepare-for-a-staged-migration"></a>الخطوة 1: الاستعداد لل ترحيل مرحلي

قبل ترحيل علب البريد إلى Microsoft 365 باستخدام ترحيل مرحلي، يجب إجراء بعض التغييرات على بيئة Exchange.

 **تكوين Outlook في أي مكان على Exchange Server المحلي** تستخدم خدمة ترحيل البريد الإلكتروني Outlook في أي مكان (المعروف أيضا باسم RPC عبر HTTP)، للاتصال ب Exchange Server المحلي. للحصول على معلومات حول كيفية إعداد Outlook في أي مكان ل Exchange Server 2007 وExchange 2003، راجع ما يلي:

- [Exchange 2007: كيفية تمكين Outlook في أي مكان](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [كيفية تكوين Outlook في أي مكان باستخدام Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> يجب استخدام شهادة صادرة عن مرجع مصدق موثوق به (CA) مع تكوين Outlook Anywhere. يتعذر تكوين Outlook Anywhere باستخدام شهادة موقعة ذاتيا. لمزيد من المعلومات، راجع [كيفية تكوين SSL ل Outlook في أي مكان](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **اختياري: تحقق من إمكانية الاتصال بمؤسسة Exchange باستخدام Outlook في أي مكان** جرب أحد الأساليب التالية لاختبار إعدادات الاتصال.

- استخدم Outlook من خارج شبكة الشركة للاتصال بعلبة بريد Exchange المحلية.

- استخدم [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) لاختبار إعدادات الاتصال. استخدم اختباري Outlook Anywhere (RPC عبر HTTP) أو Outlook Autodiscover.

- تشغيل الأوامر التالية في Exchange Online PowerShell:

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **تعيين الأذونات** يجب أن يكون لحساب المستخدم المحلي الذي تستخدمه للاتصال بمؤسسة Exchange المحلية (التي تسمى أيضا مسؤول الترحيل) الأذونات اللازمة للوصول إلى علب البريد المحلية التي تريد ترحيلها إلى Microsoft 365. يتم استخدام حساب المستخدم هذا عند الاتصال بنظام البريد الإلكتروني الخاص بك عن طريق إنشاء نقطة نهاية ترحيل لاحقا في هذا الإجراء [الخطوة 3: إنشاء نقطة نهاية ترحيل](#step-3-create-a-migration-endpoint).

بترحيل علب البريد، يجب أن يكون لدى المسؤول إحدى مجموعات الأذونات التالية:

- كن عضوا في مجموعة **"مسؤولي المجال** " في Active Directory في المؤسسة المحلية.

    او

- يجب تعيين إذن **FullAccess** لكل علبة بريد محلية وإذن **WriteProperty** لتعديل **الخاصية TargetAddress** على حسابات المستخدمين المحلية.

    او

- يجب تعيين إذن **"تلقي باسم** " على قاعدة بيانات علبة البريد المحلية التي تخزن علب بريد المستخدمين وإذن **WriteProperty** لتعديل **الخاصية TargetAddress** على حسابات المستخدمين المحلية.

للحصول على إرشادات حول كيفية تعيين هذه الأذونات، راجع [تعيين أذونات ترحيل علب البريد إلى Microsoft 365](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **تعطيل المراسلة الموحدة (UM)** إذا كانت المراسلة الموحدة قيد التشغيل لعلب البريد المحلية التي تقوم بترحيلها، فقم بإيقاف تشغيل المراسلة الموحدة قبل الترحيل. قم بتشغيل المراسلة الموحدة لعلب البريد بعد اكتمال الترحيل. للحصول على خطوات إرشادية، راجع[تعطيل المراسلة الموحدة](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **استخدم مزامنة الدليل لإنشاء مستخدمين جدد في Microsoft 365.** يمكنك استخدام مزامنة الدليل لإنشاء جميع المستخدمين المحليين في مؤسسة Microsoft 365.

تحتاج إلى ترخيص المستخدمين بعد إنشائهم. لديك 30 يوما لإضافة تراخيص بعد إنشاء المستخدمين. للحصول على خطوات لإضافة تراخيص، راجع [الخطوة 8: إكمال مهام ما بعد الترحيل](#step-8-complete-post-migration-tasks).

 يمكنك استخدام أداة مزامنة Microsoft Azure Active Directory (Azure AD) أو Microsoft Azure AD Sync Services لمزامنة المستخدمين المحليين وإنشاءهم في Microsoft 365. بعد ترحيل علب البريد إلى Microsoft 365، يمكنك إدارة حسابات المستخدمين في مؤسستك المحلية، وتتم مزامنتها مع مؤسسة Microsoft 365. لمزيد من المعلومات، راجع[تكامل الدليل](/previous-versions/azure/azure-services/jj573653(v=azure.100)) .

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>الخطوة 2: إنشاء ملف CSV دفعة ترحيل مرحلي

بعد تحديد المستخدمين الذين تريد ترحيل علب البريد المحلية الخاصة بهم إلى Microsoft 365، يمكنك استخدام ملف قيمة مفصولة بفواصل (CSV) لإنشاء دفعة ترحيل. يحتوي كل صف في ملف CSV، الذي يستخدمه Microsoft 365 لتشغيل الترحيل، على معلومات حول علبة بريد محلية.

> [!NOTE]
> لا يوجد حد لعدد علب البريد التي يمكنك ترحيلها إلى Microsoft 365 باستخدام ترحيل مرحلي. يمكن أن يحتوي ملف CSV دفعة ترحيل على 2000 صف كحد أقصى. لنقل أكثر من 2000 علبة بريد، قم بإنشاء ملفات CSV إضافية واستخدم كل ملف لإنشاء دفعة ترحيل جديدة.

 **السمات المدعومة**

يدعم ملف CSV لل ترحيل مرحلي السمات الثلاث التالية. يتوافق كل صف في ملف CSV مع علبة بريد ويجب أن يحتوي على قيمة لكل من هذه السمات.

|**السمه**|**الوصف**|**مطلوب؟**|
|:-----|:-----|:-----|
|Emailaddress  <br/> |تحديد عنوان البريد الإلكتروني SMTP الأساسي، على سبيل المثال، pilarp@contoso.com، لعلب البريد المحلية.  <br/> استخدم عنوان SMTP الأساسي لعلب البريد المحلية وليس معرفات المستخدمين من Microsoft 365. على سبيل المثال، إذا تمت تسمية المجال المحلي contoso.com ولكن تمت تسمية مجال البريد الإلكتروني Microsoft 365 service.contoso.com، يمكنك استخدام اسم المجال contoso.com لعناوين البريد الإلكتروني في ملف CSV.  <br/> |مطلوب  <br/> |
|كلمه المرور  <br/> |كلمة المرور التي سيتم تعيينها لعل بريد Microsoft 365 الجديد. تنطبق أيضا أي قيود على كلمة المرور يتم تطبيقها على مؤسسة Microsoft 365 على كلمات المرور المضمنة في ملف CSV.  <br/> |اختياري  <br/> |
|ForceChangePassword  <br/> |تحديد ما إذا كان يجب على المستخدم تغيير كلمة المرور في المرة الأولى التي يسجل فيها الدخول إلى علبة بريد Microsoft 365 الجديدة. استخدم **True** أو **False** لقيمة هذه المعلمة. <br/> > [!NOTE]> إذا قمت بتنفيذ حل تسجيل الدخول الأحادي (SSO) عن طريق نشر خدمات الأمان المشترك ل Active Directory (AD FS) أو أكبر في مؤسستك المحلية، يجب استخدام **False** لقيمة سمة **ForceChangePassword** .          |اختياري  <br/> |

 **تنسيق الملف CSV**

في ما يلي مثال على تنسيق ملف CSV. في هذا المثال، يتم ترحيل ثلاث علب بريد محلية إلى Microsoft 365.

يسرد الصف الأول أو صف الرأس، من ملف CSV أسماء السمات أو الحقول المحددة في الصفوف التالية. يتم الفصل بين كل اسم من أسماء السمات بفاصلة.

```powershell
EmailAddress,Password,ForceChangePassword
pilarp@contoso.com,Pa$$w0rd,False
tobyn@contoso.com,Pa$$w0rd,False
briant@contoso.com,Pa$$w0rd,False
```

يمثل كل صف أسفل صف الرأس مستخدما واحدا ويقدم المعلومات التي سيتم استخدامها في ترحيل علبة بريد المستخدم. يجب أن تكون قيم السمات في كل صف بنفس ترتيب أسماء السمات في صف الرأس.

استخدم أي محرر نص أو تطبيق مثل Excel لإنشاء ملف CSV. احفظ الملف كملف .csv أو .txt.

> [!NOTE]
> إذا كان الملف CSV يحتوي على أحرف غير ASCII أو أحرف خاصة، فقم بحفظ ملف CSV بترميز UTF-8 أو بترميز Unicode آخر. اعتمادا على التطبيق، يمكن أن يكون حفظ ملف CSV مع ترميز UTF-8 أو ترميز Unicode آخر أسهل عندما تتطابق الإعدادات المحلية للنظام للكمبيوتر مع اللغة المستخدمة في ملف CSV.

### <a name="step-3-create-a-migration-endpoint"></a>الخطوة 3: إنشاء نقطة نهاية ترحيل

للانتقال إلى البريد الإلكتروني بنجاح، يحتاج Microsoft 365 إلى الاتصال بنظام البريد الإلكتروني المصدر والتواصل معه. للقيام بذلك، يستخدم Microsoft 365 نقطة نهاية ترحيل. لإنشاء نقطة نهاية ترحيل Outlook في أي مكان باستخدام PowerShell، لل ترحيل مرحلي، اتصل أولا [ب Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

للحصول على قائمة كاملة بأوامر الترحيل، راجع [أوامر cmdlets للتنقل والترحيل](/powershell/exchange/).

لإنشاء نقطة نهاية ترحيل Outlook في أي مكان تسمى "StagedEndpoint" في Exchange Online PowerShell، قم بتشغيل الأوامر التالية:

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

لمزيد من المعلومات حول **New-MigrationEndpoint** cmdlet، راجع [New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> يمكن استخدام **New-MigrationEndpoint** cmdlet لتحديد قاعدة بيانات للخدمة لاستخدامها باستخدام خيار **-TargetDatabase** . وإلا، يتم تعيين قاعدة بيانات عشوائيا من موقع خدمات الأمان المشترك ل Active Directory (AD FS) 2.0 حيث توجد علبة بريد الإدارة.

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

في Exchange Online PowerShell، قم بتشغيل الأمر التالي لعرض معلومات حول نقطة نهاية الترحيل "StagedEndpoint":

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>الخطوة 4: إنشاء دفعة ترحيل مرحلة وبدء تشغيلها

يمكنك استخدام **New-MigrationBatch** cmdlet في Exchange Online PowerShell لإنشاء دفعة ترحيل لانتقال كلي. يمكنك إنشاء دفعة ترحيل وبدء تشغيلها تلقائيا عن طريق تضمين المعلمة _AutoStart_ . بدلا من ذلك، يمكنك إنشاء دفعة الترحيل ثم بدء تشغيلها يدويا بعد ذلك باستخدام **Start-MigrationBatch** cmdlet. ينشئ هذا المثال دفعة ترحيل تسمى "StagedBatch1" ويستخدم نقطة نهاية الترحيل التي تم إنشاؤها في الخطوة السابقة.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

ينشئ هذا المثال أيضا دفعة ترحيل تسمى "StagedBatch1" ويستخدم نقطة نهاية الترحيل التي تم إنشاؤها في الخطوة السابقة. نظرا لعدم تضمين معلمة _AutoStart_ ، يجب بدء دفعة الترحيل يدويا على لوحة معلومات الترحيل أو باستخدام **Start-MigrationBatch** cmdlet. كما ذكر سابقا، يمكن أن توجد دفعة ترحيل كلي واحدة فقط في كل مرة.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

قم بتشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول "StagedBatch1":

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

يمكنك أيضا التحقق من أن الدفعة قد بدأت عن طريق تشغيل الأمر التالي:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

لمزيد من المعلومات حول **Get-MigrationBatch** cmdlet، راجع [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>الخطوة 5: تحويل علب البريد المحلية إلى مستخدمين ممكنين للبريد

بعد ترحيل دفعة من علب البريد بنجاح، تحتاج إلى طريقة ما للسماح للمستخدمين بلانتقال إلى بريدهم. لدى المستخدم الذي تم ترحيل علبة بريده الآن علبة بريد محلية وأخرى في Microsoft 365. سيتوقف المستخدمون الذين لديهم علبة بريد في Microsoft 365 عن تلقي بريد جديد في علبة البريد المحلية الخاصة بهم.

نظرا لعدم الانتهاء من عمليات الترحيل، فأنت لست جاهزا بعد لتوجيه جميع المستخدمين إلى Microsoft 365 للبريد الإلكتروني الخاص بهم. فماذا تفعل لهؤلاء الأشخاص الذين لديهم كليهما؟ ما يمكنك القيام به هو تغيير علب البريد المحلية التي قمت بترحيلها بالفعل إلى المستخدمين الممكنين للبريد. عند التغيير من علبة بريد إلى مستخدم ممكن للبريد، يمكنك توجيه المستخدم إلى Microsoft 365 للبريد الإلكتروني بدلا من الانتقال إلى علبة البريد المحلية الخاصة به.

هناك سبب مهم آخر لتحويل علب البريد المحلية إلى مستخدمين ممكنين للبريد وهو الاحتفاظ بعناوين الوكيل من علب بريد Microsoft 365 عن طريق نسخ عناوين الوكيل إلى المستخدمين الممكنين للبريد. يتيح لك ذلك إدارة المستخدمين المستندين إلى السحابة من مؤسستك المحلية باستخدام Active Directory. علاوة على ذلك، إذا قررت إيقاف تشغيل مؤسسة Exchange Server المحلية بعد ترحيل كل علب البريد إلى Microsoft 365، فستبقى عناوين الوكيل التي نسختها إلى المستخدمين الممكنين للبريد في Active Directory المحلي.

### <a name="step-6-delete-a-staged-migration-batch"></a>الخطوة 6: حذف دفعة ترحيل مرحلي

 بعد ترحيل كل علب البريد الموجودة في دفعة ترحيل بنجاح، وتحويل علب البريد المحلية في الدفعة إلى مستخدمين ممكنين للبريد، تصبح جاهزا لحذف دفعة ترحيل مرحلي. تأكد من إعادة توجيه البريد إلى علب بريد Microsoft 365 في دفعة الترحيل. عند حذف دفعة ترحيل مرحلي، تقوم خدمة الترحيل بتنظيف أي سجلات ذات صلة دفعة الترحيل وحذف دفعة الترحيل.

لحذف دفعة الترحيل "StagedBatch1" في Exchange Online PowerShell، قم بتشغيل الأمر التالي.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

لمزيد من المعلومات حول **Remove-MigrationBatch** cmdlet، راجع [Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>تحقق من أنه يعمل

قم بتشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات حول "IMAPBatch1":

```powershell
Get-MigrationBatch StagedBatch1
```

سيرجع الأمر إما دفعة الترحيل بحالة **إزالة**، أو سيرجع خطأ يفيد بتعذر العثور على دفعة الترحيل، مع التحقق من حذف الدفعة.

لمزيد من المعلومات حول **Get-MigrationBatch** cmdlet، راجع [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>الخطوة 7: تعيين تراخيص لمستخدمي Microsoft 365

تنشيط حسابات مستخدمي Microsoft 365 للحسابات التي تم ترحيلها عن طريق تعيين التراخيص. إذا لم تقم بتعيين ترخيص، يتم تعطيل علبة البريد عند انتهاء فترة السماح (30 يوما). لتعيين ترخيص في مركز إدارة Microsoft 365، راجع [تعيين تراخيص أو إلغاء تعيينها](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>الخطوة 8: إكمال مهام ما بعد الترحيل

- **إنشاء سجل DNS الكشف التلقائي حتى يتمكن المستخدمون من الوصول بسهولة إلى علب بريدهم.** بعد ترحيل كل علب البريد المحلية إلى Microsoft 365، يمكنك تكوين سجل DNS للتحقق التلقائي لمؤسسة Microsoft 365 لتمكين المستخدمين من الاتصال بسهولة بعلب بريد Microsoft 365 الجديدة باستخدام عملاء Outlook والأجهزة المحمولة. يجب أن يستخدم سجل DNS الجديد للتحقق التلقائي مساحة الاسم نفسها التي تستخدمها لمؤسسة Microsoft 365. على سبيل المثال، إذا كانت مساحة الاسم المستندة إلى السحابة cloud.contoso.com، يكون سجل DNS للتحقق التلقائي الذي تحتاج إلى إنشائه autodiscover.cloud.contoso.com.

    يستخدم Microsoft 365 سجل CNAME لتنفيذ خدمة الكشف التلقائي لعملاء Outlook والأجهزة المحمولة. يجب أن يحتوي سجل CNAME للتحقق التلقائي على المعلومات التالية:

  - **الاسم المستعار:** الكشف التلقائي

  - **الهدف:** autodiscover.outlook.com

    لمزيد من المعلومات، راجع [إضافة سجلات DNS لتوصيل مجالك](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **إيقاف تشغيل خوادم Exchange المحلية.** بعد التحقق من توجيه كل رسائل البريد الإلكتروني مباشرة إلى علب بريد Microsoft 365، ولم تعد بحاجة إلى الحفاظ على مؤسسة البريد الإلكتروني المحلية أو عدم التخطيط لتنفيذ حل SSO، يمكنك إلغاء تثبيت Exchange من خوادمك وإزالة مؤسسة Exchange المحلية.

> [!NOTE]
> يمكن أن يؤدي إيقاف تشغيل Exchange إلى عواقب غير مقصودة. قبل إيقاف تشغيل مؤسسة Exchange المحلية، نوصي بالاتصال بدعم Microsoft.

لمزيد من المعلومات، راجع ما يلي:

- [تعديل Exchange 2010 أو إزالته](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

- [كيفية إزالة مؤسسة Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

- [كيفية إلغاء تثبيت Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
