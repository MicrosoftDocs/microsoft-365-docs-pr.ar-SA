---
title: إدارة علب Exchange Online البريد في بيئة متعددة الجغرافيا
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-mar2020
ms.localizationpriority: medium
description: تعرف على كيفية إدارة Exchange Online الجغرافيا المتعددة في Microsoft 365 باستخدام PowerShell.
ms.openlocfilehash: 2e4be2fd506f89579866c61bbf4a8a41aadc0d03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569960"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>إدارة علب Exchange Online البريد في بيئة متعددة الجغرافيا

Exchange Online PowerShell لعرض الخصائص الجغرافية المتعددة وتكوينها في Microsoft 365 البيئة. للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

تحتاج إلى [Microsoft Azure Active Directory النمطية ل PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 أو أي وقت لاحق في v1.x لرؤية الخاصية **المفضلةDataLocation** على كائنات المستخدم. لا يمكن تعديل قيمة **المفضلةDataLocation** AAD (دليل Azure النشط) الاتصال عبر AAD (دليل Azure النشط) المستخدم مباشرة عبر AAD (دليل Azure النشط) PowerShell. يمكن تعديل كائنات المستخدم السحابية فقط عبر AAD (دليل Azure النشط) PowerShell. للاتصال ب Azure AD PowerShell، راجع الاتصال [PowerShell](connect-to-microsoft-365-powershell.md).

في Exchange Online متعددة البيئات الجغرافية، لن تحتاج إلى القيام بأي خطوات يدوية لإضافة جيو إلى المستأجر. بعد تلقي منشور مركز الرسائل الذي يقول أن الموقع الجغرافي المتعدد جاهز Exchange Online، ستكون كل الجغرافيا الأرضية المتوفرة جاهزة ومجهزة لاستخدامها.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>الاتصال مباشرة إلى موقع جغرافي باستخدام Exchange Online PowerShell

عادة، Exchange Online PowerShell إلى الموقع الجغرافي المركزي. ولكن يمكنك أيضا الاتصال مباشرة بالمواقع الجغرافية للأقمار الصناعية. نظرا لتحسينات الأداء، نوصي بالاتصال مباشرة بموقع الأقمار الصناعية الجغرافي عند إدارة المستخدمين في ذلك الموقع فقط.

يتم وصف متطلبات تثبيت الوحدة النمطية EXO V2 واستخدامها في [تثبيت وحدة EXO V2 النمطية والمحافظة عليها](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

لتوصيل Exchange Online PowerShell بموقع جغرافي معين، تختلف معلمة *ConnectionUri* عن إرشادات الاتصال العادية. أما باقي الأوامر والقيم، فبقية الأوامر والقيم هي نفسها.

بشكل خاص، تحتاج إلى إضافة `?email=<emailaddress>` القيمة إلى نهاية _قيمة ConnectionUri_ . `<emailaddress>` هو عنوان البريد الإلكتروني **لأي علبة** بريد في الموقع الجغرافي الهدف. لا تكون الأذونات الخاصة بك إلى علبة البريد هذه أو العلاقة مع بيانات الاعتماد الخاصة بك من العوامل؛ يخبرك عنوان البريد الإلكتروني Exchange Online PowerShell بمكان الاتصال.

Microsoft 365 أو Microsoft 365 سحابة القطاع الحكومي يحتاج العملاء عادة إلى استخدام المعلمة _ConnectionUri_ للاتصال Exchange Online PowerShell. ولكن للاتصال بموقع جغرافي معين، ستحتاج إلى استخدام معلمة _ConnectionUri_ `?email=<emailaddress>` حتى تتمكن من استخدامها في القيمة.

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>الاتصال إلى موقع جغرافي في Exchange Online PowerShell

تعمل إرشادات الاتصال التالية مع الحسابات التي تم تكوينها أو لم يتم تكوينها للمصادقة متعددة العوامل (MFA).

1. في نافذة Windows PowerShell، قم بتحميل الوحدة النمطية EXO V2 عن طريق تشغيل الأمر التالي:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. في المثال التالي، admin@contoso.onmicrosoft.com هو حساب المسؤول، وموقع الموقع الجغرافي الهدف هو المكان الذي olga@contoso.onmicrosoft.com علبة البريد.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. أدخل كلمة المرور الخاصة admin@contoso.onmicrosoft.com في المطالبة التي تظهر. إذا تم تكوين الحساب ل MFA، ستحتاج أيضا إلى إدخال رمز الأمان.

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>عرض المواقع الجغرافية المتوفرة التي تم تكوينها في Exchange Online الخاصة بك

لرؤية قائمة المواقع الجغرافية التي تم تكوينها في Microsoft 365 الجغرافيا المتعددة، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>عرض الموقع الجغرافي المركزي لمنظمتك Exchange Online

لعرض الموقع الجغرافي المركزي للمستأجر، يمكنك تشغيل الأمر التالي في Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>البحث عن الموقع الجغرافي لعلبة بريد

يعرض **cmdlet الخاص ب Get-Mailbox** في Exchange Online PowerShell الخصائص التالية ذات الصلة بالمتعددة الجغرافيا على علب البريد:

- **قاعدة** البيانات: تتوافق الأحرف 3 الأولى من اسم قاعدة البيانات مع الرمز الجغرافي، الذي يخبرك بمكان وجود علبة البريد حاليا. بالنسبة إلى علب بريد الأرشيف عبر الإنترنت، يجب استخدام الخاصية **ArchiveDatabase** .

- **علبة البريد**: يحدد رمز الموقع الجغرافي الذي تم تعيينه بواسطة المسؤول (متزامن من **المفضلةDataLocation** في Azure AD).

- **MailboxRegionLastUpdateTime**: يشير إلى وقت التحديث الأخير ل MailboxRegion (إما تلقائيا أو يدويا).

لرؤية هذه الخصائص لعلبة بريد، استخدم بناء الجملة التالي:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

على سبيل المثال، لرؤية معلومات الموقع الجغرافي لعلبة البريد chris@contoso.onmicrosoft.com، يمكنك تشغيل الأمر التالي:

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

يبدو إخراج الأمر كما يلي:

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> [!NOTE]
> إذا لم يكن رمز الموقع الجغرافي في اسم قاعدة البيانات متطابقا مع قيمة **MailboxRegion**، سيتم وضع علبة البريد تلقائيا في قائمة انتظار إعادة النقل ونقلها إلى الموقع الجغرافي المحدد بواسطة قيمة **MailboxRegion** (تبحث Exchange Online عن عدم تطابق بين قيم الخاصية هذه).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>نقل علبة بريد موجودة على السحابة فقط إلى موقع جغرافي معين

المستخدم السحابي فقط هو مستخدم لا يتم مزامنته مع المستأجر عبر AAD (دليل Azure النشط) الاتصال. تم إنشاء هذا المستخدم مباشرة في Azure AD. استخدم **الأمرين Cmdlets Get-MsolUser** وS **set-MsolUser** في وحدة Azure AD النمطية ل Windows PowerShell لعرض الموقع الجغرافي أو تحديده حيث سيتم تخزين علبة بريد مستخدم في السحابة فقط.

لعرض القيمة **المفضلةDataLocation** للمستخدم، استخدم بناء الجملة هذا في Azure AD PowerShell:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

على سبيل المثال، لرؤية القيمة **المفضلةDataLocation** للمستخدم michelle@contoso.onmicrosoft.com، ادير الأمر التالي:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

لتعديل القيمة **المفضلةDataLocation** لكائن مستخدم في السحابة فقط، استخدم بناء الجملة التالي في Azure AD PowerShell:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

على سبيل المثال، لتعيين القيمة **المفضلةDataLocation** إلى الموقع الجغرافي للاتحاد الأوروبي (EUR) michelle@contoso.onmicrosoft.com، قم بتشغيل الأمر التالي:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - كما ذكرنا سابقا، لا يمكنك استخدام هذا الإجراء  لكائنات المستخدم المتزامنة من Active Directory الداخلي. يجب تغيير القيمة **المفضلةDataLocation** في Active Directory ومزامنتها باستخدام AAD (دليل Azure النشط) الاتصال. لمزيد من المعلومات، راجع مزامنة [Azure Active Directory الاتصال: تكوين موقع البيانات المفضل Microsoft 365 الموارد](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - تعتمد المدة التي يستغرقها تغيير موقع علبة البريد إلى موقع جغرافي جديد على عدة عوامل:
>
>   - حجم علبة البريد ونوعها.
>   - عدد علب البريد التي يتم نقلها.
>   - توفر موارد نقل.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>نقل علبة بريد غير نشطة إلى جغرافي معين

لا يمكنك نقل علب البريد غير النشطة التي يتم الاحتفاظ بها لأغراض التوافق (على سبيل المثال، علب البريد في الاحتجاز بسبب الدعاوى القضائية) عن طريق تغيير القيمة **المفضلةDataLocation** الخاصة بها. لنقل علبة بريد غير نشطة إلى جغرافي آخر، يمكنك القيام بالخطوات التالية:

1. استرداد علبة البريد غير النشطة. للحصول على الإرشادات، راجع [استرداد علبة بريد غير نشطة](../compliance/recover-an-inactive-mailbox.md).

2. منع مساعد المجلد \<MailboxIdentity\> المدار من معالجة علبة البريد المستردة من خلال استبدال اسم علبة البريد أو الاسم المستعار أو الحساب أو عنوان البريد الإلكتروني وتشغيل الأمر التالي [في Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. قم بتعيين **Exchange Online الخطة 2** لعلبة البريد المستردة. هذه الخطوة مطلوبة لعودة علبة البريد إلى وضع الاحتجاز بسبب الدعاوى القضائية. للحصول على الإرشادات، راجع [تعيين تراخيص للمستخدمين](../admin/manage/assign-licenses-to-users.md).

4. تكوين القيمة **المفضلةDataLocation** على علبة البريد كما هو موضح في المقطع السابق.

5. بعد التأكيد على نقل علبة البريد إلى الموقع الجغرافي الجديد، ضع علبة البريد المستردة مرة أخرى في الاحتجاز بسبب الدعاوى القضائية. للحصول على الإرشادات، راجع [وضع علبة بريد في وضع الاحتجاز بسبب الدعاوى القضائية](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. \<MailboxIdentity\> بعد التحقق من وجود الاحتجاز بسبب الدعاوى القضائية، اسمح لمساعد المجلد المدار بمعالجة علبة البريد مرة أخرى من خلال استبدال اسم علبة البريد أو الاسم المستعار أو الحساب أو عنوان البريد الإلكتروني وتشغيل الأمر التالي [في Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. اجعل علبة البريد غير نشطة مرة أخرى عن طريق إزالة حساب المستخدم المقترن علبة البريد. للحصول على الإرشادات، [راجع حذف مستخدم من مؤسستك](../admin/add-users/delete-a-user.md). تصدر هذه الخطوة أيضا Exchange Online الخطة 2 الاستخدامات الأخرى.

**ملاحظة**: عند نقل علبة بريد غير نشطة إلى موقع جغرافي آخر، قد تؤثر على نتائج البحث في المحتوى أو القدرة على البحث في علبة البريد من الموقع الجغرافي السابق. لمزيد من المعلومات، راجع البحث عن [المحتوى وتصديره في بيئات متعددة الجغرافيا](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>إنشاء علب بريد سحابة جديدة في موقع جغرافي معين

لإنشاء علبة بريد جديدة في موقع جغرافي معين، يجب عليك القيام بأي من هذه الخطوات:

- تكوين القيمة **المفضلةDataLocation** كما هو موضح في السابق نقل علبة بريد موجودة [](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location) في السحابة فقط إلى مقطع موقع جغرافي معين قبل إنشاء علبة البريد في  Exchange Online. على سبيل المثال، قم بتكوين **القيمة المفضلةDataLocation** على مستخدم قبل تعيين ترخيص.

- قم بتعيين ترخيص في الوقت نفسه الذي قمت فيه بتعيين **القيمة المفضلةDataLocation** .

لإنشاء مستخدم جديد مرخص للسحابة فقط (AAD (دليل Azure النشط) الاتصال مزامنته) في موقع جغرافي معين، استخدم بناء الجملة التالي في Azure AD PowerShell:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

ينشئ هذا المثال حساب مستخدم جديد لإليزابيث برونر مع القيم التالية:

- اسم المستخدم الأساسي: ebrunner@contoso.onmicrosoft.com
- الاسم الأول: إليزابيث
- اسم العائلة: برونر
- اسم العرض: إليزابيث برونر
- كلمة المرور: يتم إنشاؤها عشوائيا وإظهرها في نتائج الأمر (لأننا لا نستخدم معلمة *كلمة* المرور)
- الترخيص: `contoso:ENTERPRISEPREMIUM` (E5)
- الموقع: أستراليا (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

للحصول على مزيد من المعلومات حول إنشاء حسابات مستخدمين جديدة ونجد قيم LicenseAssignment في Azure AD PowerShell، راجع إنشاء حسابات المستخدمين باستخدام [تراخيص PowerShell](create-user-accounts-with-microsoft-365-powershell.md) وعرض الخدمات باستخدام [PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> إذا كنت تستخدم Exchange Online PowerShell لتمكين علبة بريد وتحتاج إلى إنشاء علبة البريد مباشرة في الموقع الجغرافي المحدد في **PreferredDataLocation**، يجب استخدام cmdlet Exchange Online مثل **Enable-Mailbox** أو **New-Mailbox** مباشرة مقابل الخدمة السحابية. إذا كنت تستخدم **الأمر Cmdlet Enable-RemoteMailbox** في موقع powerShell Exchange، سيتم إنشاء علبة البريد في الموقع الجغرافي المركزي.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>حفظ علب البريد المحلية الموجودة في موقع جغرافي معين

يمكنك استخدام أدوات وعمليات الحاق القياسية لترحيل علبة بريد من مؤسسة Exchange المحلية إلى Exchange Online، بما في ذلك لوحة معلومات الترحيل في [EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)، و [cmdlet New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) في Exchange Online PowerShell.

الخطوة الأولى هي التحقق من وجود كائن مستخدم لكل علبة بريد للتهيئة، والتحقق من تكوين **القيمة المفضلةDataLocation** الصحيحة في Azure AD. ستحترم أدوات التزيين القيمة **المفضلةDataLocation** وست ترحيل علب البريد مباشرة إلى الموقع الجغرافي المحدد.

أو، يمكنك استخدام الخطوات التالية لتكريس علب البريد مباشرة في موقع جغرافي معين باستخدام [الأمر cmdlet New-MoveRequest](/powershell/module/exchange/new-moverequest) في Exchange Online PowerShell.

1. تحقق من وجود كائن المستخدم لكل علبة بريد لكي يتم إعدادها ومن تعيين **PreferredDataLocation** إلى القيمة المطلوبة في Azure AD. سيتم مزامنة **قيمة المفضلةDataLocation** مع السمة **MailboxRegion** لكائن مستخدم البريد المقابل في Exchange Online.

2. الاتصال مباشرة إلى موقع القمر الصناعي الجغرافي المحدد باستخدام إرشادات الاتصال الواردة سابقا في هذا الموضوع.

3. في Exchange Online PowerShell، قم بتخزين بيانات اعتماد المسؤول المحلية المستخدمة لتنفيذ ترحيل علبة بريد في متغير عن طريق تشغيل الأمر التالي:

   ```powershell
   $RC = Get-Credential
   ```

4. في Exchange Online PowerShell، أنشئ **New-MoveRequest** جديدا مماثلا للمثال التالي:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. كرر الخطوة رقم 4 لكل علبة بريد تحتاج إلى ترحيلها من موقع Exchange إلى الموقع الجغرافي للأقمار الصناعية المتصل بها حاليا.

6. إذا كنت بحاجة إلى ترحيل علب بريد إضافية إلى مواقع جغرافية أقمار صناعية مختلفة، كرر الخطوات من 2 إلى 4 لكل موقع محدد.

## <a name="multi-geo-reporting"></a>إعداد تقارير متعددة الجغرافيا

**تعرض تقارير الاستخدام** متعددة الجغرافيا في مركز مسؤولي Microsoft 365 عدد المستخدمين حسب الموقع الجغرافي. يعرض التقرير توزيع المستخدم للشهر الحالي ويوفر بيانات تاريخية للشهور الستة الماضية.

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)