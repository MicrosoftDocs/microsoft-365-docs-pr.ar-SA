---
title: إدارة علب بريد Exchange Online في بيئة متعددة الجغرافيا
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
description: تعرف على كيفية إدارة الإعدادات Exchange Online متعددة المناطق الجغرافية في بيئة Microsoft 365 باستخدام PowerShell.
ms.openlocfilehash: 4b0b02fa9ea974784ec93efe83520faed5fd05bd
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130856"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>إدارة علب بريد Exchange Online في بيئة متعددة الجغرافيا

Exchange Online PowerShell مطلوب لعرض وتكوين خصائص جغرافية متعددة في بيئة Microsoft 365 الخاصة بك. للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

تحتاج [إلى Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 أو أحدث في v1.x لمشاهدة خاصية **PreferredDataLocation** على كائنات المستخدم. لا يمكن لعناصر المستخدم التي تمت مزامنتها عبر AAD (دليل Azure النشط) الاتصال إلى AAD (دليل Azure النشط) تعديل قيمة **PreferredDataLocation** مباشرة عبر AAD (دليل Azure النشط) PowerShell. يمكن تعديل كائنات المستخدم السحابية فقط عبر AAD (دليل Azure النشط) PowerShell. للاتصال Azure AD PowerShell، راجع [الاتصال إلى PowerShell](connect-to-microsoft-365-powershell.md).

في Exchange Online بيئات متعددة المناطق الجغرافية، لا تحتاج إلى القيام بأي خطوات يدوية لإضافة مناطق جغرافية إلى المستأجر الخاص بك. بعد تلقي منشور مركز الرسائل الذي يشير إلى أن المناطق الجغرافية المتعددة جاهزة Exchange Online، ستكون جميع المناطق الجغرافية المتوفرة جاهزة ومكونة لاستخدامها.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>الاتصال مباشرة إلى موقع جغرافي باستخدام Exchange Online PowerShell

عادة ما يتصل Exchange Online PowerShell بالموقع الجغرافي المركزي. ولكن، يمكنك أيضا الاتصال مباشرة بالمواقع الجغرافية للأقمار الصناعية. بسبب تحسينات الأداء، نوصي بالاتصال مباشرة بالموقع الجغرافي للأقمار الصناعية عندما تدير المستخدمين فقط في هذا الموقع.

يتم وصف متطلبات التثبيت واستخدام الوحدة النمطية EXO V2 في [تثبيت وحدة EXO V2 وصيانتها](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

لتوصيل Exchange Online PowerShell بموقع جغرافي محدد، تختلف معلمة *ConnectionUri* عن إرشادات الاتصال العادية. باقي الأوامر والقيم هي نفسها.

على وجه التحديد، تحتاج إلى إضافة `?email=<emailaddress>` القيمة إلى نهاية قيمة _ConnectionUri_ . `<emailaddress>` هو عنوان البريد الإلكتروني **لأي** علبة بريد في الموقع الجغرافي المستهدف. لا تعد الأذونات الخاصة بك إلى علبة البريد هذه أو العلاقة ببيانات الاعتماد عاملا؛ يخبر عنوان البريد الإلكتروني ببساطة Exchange Online PowerShell بمكان الاتصال.

لا يحتاج العملاء Microsoft 365 أو Microsoft 365 سحابة القطاع الحكومي عادة إلى استخدام معلمة _ConnectionUri_ للاتصال Exchange Online PowerShell. ولكن، للاتصال بموقع جغرافي محدد، تحتاج إلى استخدام معلمة _ConnectionUri_ حتى تتمكن من استخدامها `?email=<emailaddress>` في القيمة.

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>الاتصال إلى موقع جغرافي في Exchange Online PowerShell

تعمل إرشادات الاتصال التالية للحسابات التي تم تكوينها أو لم يتم تكوينها للمصادقة متعددة العوامل (MFA).

1. في نافذة Windows PowerShell، قم بتحميل الوحدة النمطية EXO V2 عن طريق تشغيل الأمر التالي:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. في المثال التالي، admin@contoso.onmicrosoft.com هو حساب المسؤول، والموقع الجغرافي الهدف هو المكان الذي توجد فيه علبة البريد olga@contoso.onmicrosoft.com.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. أدخل كلمة مرور admin@contoso.onmicrosoft.com في المطالبة التي تظهر. إذا تم تكوين الحساب ل MFA، فستحتاج أيضا إلى إدخال رمز الأمان.

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>عرض المواقع الجغرافية المتوفرة التي تم تكوينها في مؤسستك Exchange Online

لمشاهدة قائمة المواقع الجغرافية المكونة في Microsoft 365 Multi-Geo، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>عرض الموقع الجغرافي المركزي لمؤسستك Exchange Online

لعرض الموقع الجغرافي المركزي للمستأجر، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>البحث عن الموقع الجغرافي لعل البريد

يعرض **الأمر get-Mailbox** cmdlet في Exchange Online PowerShell الخصائص التالية ذات الصلة متعددة المناطق الجغرافية على علب البريد:

- **قاعدة البيانات**: تتوافق الأحرف ال 3 الأولى من اسم قاعدة البيانات مع التعليمات البرمجية الجغرافية، والتي تخبرك بمكان علبة البريد حاليا. بالنسبة إلى علب بريد الأرشيف عبر الإنترنت، يجب استخدام **الخاصية ArchiveDatabase** .

- **MailboxRegion**: يحدد رمز الموقع الجغرافي الذي تم تعيينه من قبل المسؤول (تمت مزامنته من **PreferredDataLocation** في Azure AD).

- **MailboxRegionLastUpdateTime**: يشير إلى تاريخ آخر تحديث ل MailboxRegion (إما تلقائيا أو يدويا).

لمشاهدة هذه الخصائص لعل بريد، استخدم بناء الجملة التالي:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

على سبيل المثال، للاطلاع على معلومات الموقع الجغرافي لعل chris@contoso.onmicrosoft.com علبة البريد، قم بتشغيل الأمر التالي:

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
> إذا لم يتطابق رمز الموقع الجغرافي في اسم قاعدة البيانات مع قيمة **MailboxRegion**، فسيتم وضع علبة البريد تلقائيا في قائمة انتظار نقل ونقلها إلى الموقع الجغرافي المحدد بواسطة قيمة **MailboxRegion** (Exchange Online تبحث عن عدم تطابق بين قيم الخصائص هذه).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>نقل علبة بريد موجودة على السحابة فقط إلى موقع جغرافي محدد

المستخدم السحابي فقط هو مستخدم لا تتم مزامنته مع المستأجر عبر AAD (دليل Azure النشط) الاتصال. تم إنشاء هذا المستخدم مباشرة في Azure AD. استخدم **الأمرين Get-MsolUser** و **Set-MsolUser** cmdlets في الوحدة النمطية Azure AD Windows PowerShell لعرض أو تحديد الموقع الجغرافي حيث سيتم تخزين علبة بريد مستخدم السحابة فقط.

لعرض قيمة **PreferredDataLocation** لمستخدم، استخدم بناء الجملة هذا في Azure AD PowerShell:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

على سبيل المثال، لمشاهدة قيمة **PreferredDataLocation** للمستخدم michelle@contoso.onmicrosoft.com، قم بتشغيل الأمر التالي:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

لتعديل قيمة **PreferredDataLocation** لكائن مستخدم السحابة فقط، استخدم بناء الجملة التالي في Azure AD PowerShell:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

على سبيل المثال، لتعيين قيمة **PreferredDataLocation** إلى الموقع الجغرافي للاتحاد الأوروبي (اليورو) للمستخدم michelle@contoso.onmicrosoft.com، قم بتشغيل الأمر التالي:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - كما ذكر سابقا، لا يمكنك استخدام هذا الإجراء لكائنات المستخدم المتزامنة من Active Directory محلي. تحتاج إلى تغيير قيمة **PreferredDataLocation** في Active Directory ومزامنتها باستخدام AAD (دليل Azure النشط) الاتصال. لمزيد من المعلومات، راجع [Azure Active Directory الاتصال المزامنة: تكوين موقع البيانات المفضل لموارد Microsoft 365](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - تعتمد المدة التي يستغرقها نقل علبة البريد إلى موقع جغرافي جديد على عدة عوامل:
>
>   - حجم علبة البريد ونوعها.
>   - عدد علب البريد التي يتم نقلها.
>   - توفر موارد النقل.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>نقل علبة بريد غير نشطة إلى جغرافيا معين

لا يمكنك نقل علب البريد غير النشطة التي يتم الاحتفاظ بها لأغراض التوافق (على سبيل المثال، علب البريد في احتجاز التقاضي) عن طريق تغيير قيمة **PreferredDataLocation الخاصة بها** . لنقل علبة بريد غير نشطة إلى جغرافيا آخر، قم بالخطوات التالية:

1. استرداد علبة البريد غير النشطة. للحصول على الإرشادات، راجع [استرداد علبة بريد غير نشطة](../compliance/recover-an-inactive-mailbox.md).

2. منع مساعد المجلد المدار من معالجة علبة البريد المستردة عن طريق استبدالها \<MailboxIdentity\> باسم علبة البريد أو الاسم المستعار أو الحساب أو عنوان البريد الإلكتروني وتشغيل الأمر التالي في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. تعيين ترخيص **Exchange Online الخطة 2** إلى علبة البريد المستردة. هذه الخطوة مطلوبة لوضع علبة البريد مرة أخرى على احتجاز التقاضي. للحصول على الإرشادات، راجع [تعيين التراخيص للمستخدمين](../admin/manage/assign-licenses-to-users.md).

4. تكوين قيمة **PreferredDataLocation** على علبة البريد كما هو موضح في القسم السابق.

5. بعد التأكد من نقل علبة البريد إلى الموقع الجغرافي الجديد، ضع علبة البريد المستردة مرة أخرى في "احتجاز التقاضي". للحصول على الإرشادات، راجع [وضع علبة بريد في احتجاز التقاضي](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. بعد التحقق من وجود احتجاز التقاضي، اسمح لمساعد المجلد المدار بمعالجة علبة البريد مرة أخرى عن طريق استبداله \<MailboxIdentity\> باسم علبة البريد أو الاسم المستعار أو الحساب أو عنوان البريد الإلكتروني وتشغيل الأمر التالي في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. اجعل علبة البريد غير نشطة مرة أخرى عن طريق إزالة حساب المستخدم المقترن بعلبة البريد. للحصول على الإرشادات، راجع [حذف مستخدم من مؤسستك](../admin/add-users/delete-a-user.md). تصدر هذه الخطوة أيضا ترخيص Exchange Online الخطة 2 للاستخدامات الأخرى.

**ملاحظة**: عند نقل علبة بريد غير نشطة إلى موقع جغرافي مختلف، قد تؤثر على نتائج البحث في المحتوى أو القدرة على البحث في علبة البريد من الموقع الجغرافي السابق. لمزيد من المعلومات، راجع [البحث عن المحتوى وتصديره في بيئات متعددة المناطق الجغرافية](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>إنشاء علب بريد سحابية جديدة في موقع جغرافي محدد

لإنشاء علبة بريد جديدة في موقع جغرافي محدد، تحتاج إلى القيام بأي من الخطوات التالية:

- تكوين قيمة **PreferredDataLocation** كما هو موضح في السابق [نقل علبة بريد موجودة في السحابة فقط إلى مقطع موقع جغرافي معين](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location) *قبل* إنشاء علبة البريد في Exchange Online. على سبيل المثال، قم بتكوين قيمة **PreferredDataLocation** على مستخدم قبل تعيين ترخيص.

- قم بتعيين ترخيص في نفس الوقت الذي تقوم فيه بتعيين قيمة **PreferredDataLocation** .

لإنشاء مستخدم مرخص سحابي جديد (وليس AAD (دليل Azure النشط) الاتصال متزامنا) في موقع جغرافي محدد، استخدم بناء الجملة التالي في Azure AD PowerShell:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

ينشئ هذا المثال حساب مستخدم جديد ل "بروناغرايث" بالقيم التالية:

- اسم المستخدم الأساسي: ebrunner@contoso.onmicrosoft.com
- الاسم الأول: أنزابيت
- اسم العائلة: برونانر
- اسم العرض: برونانر اليزابيث
- كلمة المرور: تم إنشاؤها عشوائيا وعرضها في نتائج الأمر (لأننا لا نستخدم معلمة *كلمة المرور* )
- الترخيص: `contoso:ENTERPRISEPREMIUM` (E5)
- الموقع: أستراليا (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

لمزيد من المعلومات حول إنشاء حسابات مستخدمين جديدة والبحث عن قيم LicenseAssignment في Azure AD PowerShell، راجع [إنشاء حسابات المستخدمين باستخدام PowerShell](create-user-accounts-with-microsoft-365-powershell.md) [وعرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> إذا كنت تستخدم Exchange Online PowerShell لتمكين علبة بريد وتحتاج إلى إنشاء علبة البريد مباشرة في الموقع الجغرافي المحدد في **PreferredDataLocation**، فستحتاج إلى استخدام أمر cmdlet Exchange Online مثل **Enable-Mailbox** أو **New-Mailbox** مباشرة مقابل خدمة السحابة. إذا كنت تستخدم **Enable-RemoteMailbox** cmdlet في Exchange PowerShell المحلية، فسيتم إنشاء علبة البريد في الموقع الجغرافي المركزي.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>إلحاق علب البريد المحلية الموجودة في موقع جغرافي محدد

يمكنك استخدام أدوات وعمليات الإلحاق القياسية بترحيل علبة بريد من مؤسسة Exchange محلية إلى Exchange Online، بما [في ذلك لوحة معلومات الترحيل في EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)، و [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) cmdlet في Exchange Online PowerShell.

الخطوة الأولى هي التحقق من وجود كائن مستخدم لكل علبة بريد لإلحاقها، والتحقق من تكوين قيمة **PreferredDataLocation** الصحيحة في Azure AD. ستحترم أدوات الإلحاق قيمة **PreferredDataLocation** وسترحل علب البريد مباشرة إلى الموقع الجغرافي المحدد.

أو يمكنك استخدام الخطوات التالية لإلحاق علب البريد مباشرة في موقع جغرافي معين باستخدام [New-MoveRequest](/powershell/module/exchange/new-moverequest) cmdlet في Exchange Online PowerShell.

1. تحقق من وجود كائن المستخدم لكل علبة بريد ليتم إلحاقها ومن تعيين **PreferredDataLocation** إلى القيمة المطلوبة في Azure AD. ستتم مزامنة قيمة **PreferredDataLocation** مع سمة **MailboxRegion** لكائن مستخدم البريد المطابق في Exchange Online.

2. الاتصال مباشرة إلى الموقع الجغرافي للأقمار الصناعية المحددة باستخدام إرشادات الاتصال الواردة سابقا في هذا الموضوع.

3. في Exchange Online PowerShell، قم بتخزين بيانات اعتماد المسؤول المحلي المستخدمة لتنفيذ ترحيل علبة بريد في متغير عن طريق تشغيل الأمر التالي:

   ```powershell
   $RC = Get-Credential
   ```

4. في Exchange Online PowerShell، قم بإنشاء **New-MoveRequest** جديد مشابه للمثال التالي:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. كرر الخطوة رقم 4 لكل علبة بريد تحتاج إلى ترحيلها من Exchange المحلية إلى الموقع الجغرافي للقمر الصناعي الذي تتصل به حاليا.

6. إذا كنت بحاجة إلى ترحيل علب بريد إضافية إلى مواقع جغرافية تابعة مختلفة، فكرر الخطوات من 2 إلى 4 لكل موقع محدد.

## <a name="multi-geo-reporting"></a>إعداد التقارير متعددة المناطق الجغرافية

> [!NOTE]
> ميزة إعداد التقارير متعددة المناطق الجغرافية موجودة حاليا في المعاينة، وهي غير متوفرة في جميع المؤسسات، وهي عرضة للتغيير.

تعرض **تقارير الاستخدام الجغرافي المتعدد** في مركز مسؤولي Microsoft 365 عدد المستخدمين حسب الموقع الجغرافي. يعرض التقرير توزيع المستخدم للشهر الحالي ويوفر بيانات تاريخية للأشهر الستة الماضية.

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
