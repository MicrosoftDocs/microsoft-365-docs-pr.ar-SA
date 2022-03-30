---
title: سياسات الفحص
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: يمكن للمسؤولين معرفة كيفية استخدام سياسات الفحص للتحكم في ما يمكن للمستخدمين فعله بالرسائل المعزولة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 96dc1e2158787457884ca6a3c6f27bf76e83a369
ms.sourcegitcommit: b3c4816b55657b87ed4a5f6a4abe3d505392218e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/04/2021
ms.locfileid: "63577043"
---
# <a name="quarantine-policies"></a>سياسات الفحص

> [!NOTE]
> الميزات الموضحة في هذه المقالة متوفرة حاليا في معاينة، ولا تتوفر للجميع، وهي عرضة للتغيير.

تسمح سياسات الفحص (المعروفة سابقا باسم علامات الفحص) في Exchange Online Protection (EOP) للمسؤولين بالتحكم في ما يمكن للمستخدمين فعله بالرسائل المعزولة استنادا إلى كيفية وصول الرسالة في الفحص.

يسمح EOP عادة أو يمنع مستويات معينة من التفاعل للرسائل في الفحص وفي إعلامات [](find-and-release-quarantined-messages-as-a-user.md) البريد العشوائي [للمستخدم النهائي](use-spam-notifications-to-release-and-report-quarantined-messages.md). على سبيل المثال، يمكن للمستخدمين عرض الرسائل التي تم فحصها بواسطة تصفية مكافحة البريد العشوائي كبريد عشوائي أو مجمع، ولكن لا يمكنهم عرض الرسائل التي تم فحصها أو إصدارها على أنها تصيد احتيالي عالي الثقة (يمكن للمسؤولين فقط القيام بذلك).

بالنسبة [لمميزات](#step-2-assign-a-quarantine-policy-to-supported-features) الحماية المعتمدة، تحدد سياسات الفحص ما يسمح للمستخدمين القيام به في رسائل إعلام البريد العشوائي للمستخدم النهائي وفي رسائلهم المعزولة في الفحص (الرسائل التي يكون فيها المستخدم مستلما). يتم تعيين سياسات الفحص الافتراضية تلقائيا لفرض الإمكانات التاريخية للمستخدمين على الرسائل المعزولة. أو، يمكنك إنشاء سياسات عزل مخصصة وتعيينها للسماح للمستخدمين النهائيين أو منعهم من تنفيذ إجراءات معينة على الرسائل المعزولة.

يتم دمج الأذونات الفردية في مجموعات الأذونات التالية التي تم الإعداد المسبق لها:

- لا يمكن الوصول
- وصول محدود
- الوصول الكامل

يتم وصف الأذونات الفردية المتوفرة وما هو مضمن أو غير مضمن في مجموعات الأذونات التي تم الإعداد المسبق لها في الجدول التالي:

<br>

****

|الإذن|لا يمكن الوصول|وصول محدود|الوصول الكامل|
|---|:---:|:---:|:---:|
|**السماح للمرسل** (_PermissionToAllowSender_)|||![علامة الاختيار](../../media/checkmark.png)|
|**حظر المرسل** (_PermissionToBlockSender_)||![علامة الاختيار](../../media/checkmark.png)|![علامة الاختيار](../../media/checkmark.png)|
|**حذف** (_PermissionToDelete_)||![علامة الاختيار](../../media/checkmark.png)|![علامة الاختيار](../../media/checkmark.png)|
|**معاينة** (_PermissionToPreview_)||![علامة الاختيار](../../media/checkmark.png)|![علامة الاختيار](../../media/checkmark.png)|
|**السماح للمستلمين بإطلاق رسالة من الفحص** (_PermissionToRelease_)|||![علامة الاختيار](../../media/checkmark.png)|
|**السماح للمستلمين بطلب إصدار** رسالة من الفحص (_PermissionToRequestRelease_)||![علامة الاختيار](../../media/checkmark.png)||
|

إذا لم تعثر على الأذونات الافتراضية في مجموعات الأذونات التي تم تعيينها مسبقا، يمكنك استخدام أذونات مخصصة عند إنشاء أو تعديل سياسات عزل مخصصة. لمزيد من المعلومات حول ما يقوم به كل إذن، [راجع القسم تفاصيل](#quarantine-policy-permission-details) أذونات نهج الفحص لاحقا في هذه المقالة.

يمكنك إنشاء سياسات الفحص وتعيينها في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell ل Microsoft 365 المؤسسات التي بها علب بريد Exchange Online؛ EOP PowerShell مستقل في مؤسسات EOP بدون Exchange Online علب البريد).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. أو الانتقال مباشرة إلى صفحة **"سياسات** الفحص"، افتح <https://security.microsoft.com/quarantineTags>.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع الاتصال [Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- لعرض سياسات الفحص أو إنشائها أو تعديلها أو إزالتها، يجب أن تكون عضوا في أدوار "إدارة  المؤسسة" أو  "مسؤول الأمان" في Microsoft 365 Defender المدخل. لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>الخطوة 1: إنشاء سياسات الفحص في مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، انتقل إلى **البريد** \> \> الإلكتروني & قواعد سياسات **التعاون في** \> العمل على الفحص ثم حدد **سياسات الفحص**.

2. في صفحة **نهج الفحص** ، انقر فوق ![إضافة أيقونة نهج مخصص](../../media/m365-cc-sc-create-icon.png) **إضافة نهج مخصص**.

3. يتم **فتح معالج النهج** الجديد. في صفحة **اسم النهج** ، أدخل اسما مختصرا ولكن فريدا في **المربع اسم** النهج. ستحتاج إلى تحديد نهج الفحص وتحديده حسب الاسم في الخطوات القادمة. عند الانتهاء، انقر فوق **التالي**.

4. في صفحة **الوصول إلى رسالة المستلم** ، حدد إحدى القيم التالية:
   - **لا يمكن الوصول**
   - **وصول محدود**
   - **الوصول الكامل**

   تم وصف الأذونات الفردية المضمنة في مجموعات الأذونات هذه سابقا في هذه المقالة.

   لتحديد أذونات مخصصة، حدد **تعيين وصول معين (** خيارات متقدمة) وتكوين الإعدادات التالية التي تظهر:

     - **حدد تفضيلات إجراء الإصدار**: حدد إحدى القيم التالية:
       - **لا يوجد إجراء إصدار**: هذه هي القيمة الافتراضية.
       - **السماح للمستلمين بإطلاق رسالة من الفحص**
       - **السماح للمستلمين بطلب إصدار رسالة من الفحص**
     - **حدد إجراءات إضافية يمكن للمستلمين اتخاذها على الرسائل المعزولة**: حدد بعض القيم التالية أو كلها أو لا شيء منها:
       - **حذف**
       - **معاينة**
       - **حظر المرسل**

   يتم وصف هذه الأذونات وتأثيرها على الرسائل المعزولة وفي إعلامات البريد العشوائي للمستخدم النهائي في المقطع تفاصيل [](#quarantine-policy-permission-details) أذونات نهج الفحص لاحقا في هذه المقالة.

   عند الانتهاء، انقر فوق **التالي**.

5. في صفحة **مراجعة النهج** التي تظهر، راجع الإعدادات. يمكنك تحديد **تحرير** في كل مقطع لتعديل الإعدادات ضمن المقطع. أو يمكنك النقر فوق **الخلف** أو تحديد الصفحة المحددة في المعالج.

   عند الانتهاء، انقر فوق **إرسال**.

6. على صفحة التأكيد التي تظهر، انقر فوق **تم**.

أنت الآن جاهز لتعيين نهج الفحص إلى ميزة الفحص كما هو موضح في [القسم الخطوة 2](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>إنشاء سياسات الفحص في PowerShell

إذا كنت تفضل استخدام PowerShell لإنشاء سياسات الفحص، فاتصل Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدام الأمر **cmdlet New-QuarantineTag**. لديك طريقتان مختلفتان للاختيار من بينها:

- استخدم _المعلمة EndUserQuarantinePermissionsValue_ .
- استخدم _المعلمة EndUserQuarantinePermissions_ .

يتم وصف هذه الأساليب في المقاطع التالية.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>استخدام المعلمة EndUserQuarantinePermissionsValue

لإنشاء نهج عزل باستخدام _المعلمة EndUserQuarantinePermissionsValue_ ، استخدم بناء الجملة التالي:

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236>
```

تستخدم _المعلمة EndUserQuarantinePermissionsValue_ قيمة عشرية يتم تحويلها من قيمة ثنائية. تتوافق القيمة الثنائية مع أذونات الفحص المتوفرة للمستخدم النهائي في ترتيب معين. لكل إذن، تساوي القيمة 1 True والقيمة 0 تساوي False.

يتم وصف الترتيب والقيم المطلوبة لكل إذن فردي في مجموعات الأذونات المحددة مسبقا في الجدول التالي:

<br>

****

|الإذن|لا يمكن الوصول|وصول محدود|الوصول الكامل|
|---|:---:|:---:|:---:|
|PermissionToAllowSender|0|0|1|
|PermissionToBlockSender|0|1|1|
|PermissionToDelete|0|1|1|
|PermissionToDownload<sup>\*</sup>|0|0|0|
|PermissionToPreview|0|1|1|
|PermissionToRelease<sup>\*\*</sup>|0|0|1|
|PermissionToRequestRelease<sup>\*\*</sup>|0|1|0|
|PermissionToViewHeader<sup>\*</sup>|0|0|0|
|قيمة ثنائية|00000000|01101010|11101100|
|قيمة عشرية لاستخدامها|0|106|236|
|

<sup>\*</sup> حاليا، هذه القيمة دائما 0. بالنسبة إلى PermissionToViewHeader، لا تخفي القيمة 0 الزر عرض رأس الرسالة  في تفاصيل الرسالة المعزولة (الزر متوفر دائما).

<sup>\*\*</sup> لا تضع كلتا القيمتين على 1. قم بتعيين واحد إلى 1 والآخر إلى 0، أو قم بتعيين كليهما إلى 0.

ينشئ هذا المثال اسم نهج الفحص الجديد NoAccess الذي يعين أذونات "بلا وصول" كما هو موضح في الجدول السابق.

```powershell
New-QuarantineTag -Name NoAccess -EndUserQuarantinePermissionsValue 0
```

لأذونات الوصول المحدود، استخدم القيمة 106. لأذونات الوصول الكامل، استخدم القيمة 236.

للأذونات المخصصة، استخدم الجدول السابق للحصول على القيمة الثنائية التي تتوافق مع الأذونات التي تريدها. تحويل القيمة الثنائية إلى قيمة عشرية واستخدام القيمة العشرية للمعلمة _EndUserQuarantinePermissionsValue_ .

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-QuarantineTag](/powershell/module/exchange/new-quarantinetag).

#### <a name="use-the-enduserquarantinepermissions-parameter"></a>استخدام المعلمة EndUserQuarantinePermissions

لإنشاء نهج عزل باستخدام _المعلمة EndUserQuarantinePermissionsValue_ ، قم بالخطوات التالية:

A. تخزين كائن أذونات الفحص في متغير باستخدام **أمر cmdlet جديد-QuarantinePermissions** .

<p>

B. استخدم المتغير _كقيمة EndUserQuarantinePermissions_ في **الأمر New-QuarantineTag** .

##### <a name="step-a-store-a-quarantine-permissions-object-in-a-variable"></a>الخطوة A: تخزين كائن أذونات الفحص في متغير

استخدم بناء الجملة التالي:

```powershell
$<VariableName> = New-QuarantinePermissions [-PermissionToAllowSender <$true | $False>] [-PermissionToBlockSender <$true | $False>] [-PermissionToDelete <$true | $False>] [-PermissionToPreview <$true | $False>] [-PermissionToRelease <$true | $False>] [-PermissionToRequestRelease <$true | $False>]
```

القيمة الافتراضية لأي `$false`معلمات غير مستخدمة هي ، لذلك تحتاج فقط إلى استخدام المعلمات حيث تريد تعيين القيمة إلى `$true`.

تظهر الأمثلة التالية كيفية إنشاء كائنات الأذونات التي تتوافق مع مجموعات الأذونات التي تم ضبطها مسبقا:

- **لا يمكن الوصول**:

  ```powershell
  $NoAccess = New-QuarantinePermissions
  ```

- **وصول محدود**:

  ```powershell
  $LimitedAccess = New-QuarantinePermissions -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRequestRelease $true
  ```

- **الوصول الكامل**:

  ```powershell
  $FullAccess = New-QuarantinePermissions -PermissionToAllowSender $true -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRelease $true
  ```

لرؤية القيم التي قمت بتعيينها، قم بتشغيل اسم المتغير ك أمر (على سبيل المثال، قم بتشغيل الأمر `$NoAccess`).

بالنسبة إلى الأذونات المخصصة، لا يتم تعيين كل من _المعلمتين PermissionToRelease_ _وأذوناتToRequestRelease_ إلى `$true`. قم بتعيين أحدهما `$true` إلى وترك الآخر ك `$false`، أو اترك كليهما ك `$false`.

يمكنك أيضا تعديل متغير كائن أذونات موجود بعد إنشائه ولكن قبل استخدامه باستخدام **الأمر cmdlet Set-QuarantinePermissions** .

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-QuarantinePermissions](/powershell/module/exchange/new-quarantinepermissions) و [Set-QuarantinePermissions](/powershell/module/exchange/set-quarantinepermissions).

##### <a name="step-b-use-the-variable-in-the-new-quarantinetag-command"></a>الخطوة ب: استخدام المتغير في الأمر New-QuarantineTag

بعد إنشاء كائن الأذونات وتخزينه في متغير، استخدم المتغير لقيمة المعلمة _EndUserQuarantinePermission_ في الأمر **New-QuarantineTag** التالي:

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissions $<VariableName>
```

ينشئ هذا المثال نهج عزل جديد يسمى LimitedAccess باستخدام `$LimitedAccess` كائن الأذونات الذي تم وصفه وإنشاءه في الخطوة السابقة.

```powershell
New-QuarantineTag -Name LimitedAccess -EndUserQuarantinePermissions $LimitedAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-QuarantineTag](/powershell/module/exchange/new-quarantinetag).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>الخطوة 2: تعيين نهج عزل للميزات المعتمدة

في _ميزات_ الحماية المعتمدة التي تقوم بعزل الرسائل أو الملفات (تلقائيا أو ك إجراء قابل للتكوين)، يمكنك تعيين نهج عزل إلى إجراءات الفحص المتوفرة. الميزات التي يتم وصفها لرسائل الفحص وتوفر سياسات الفحص في الجدول التالي:

<br>

****

|الميزة|هل تم دعم سياسات الفحص؟|سياسات الفحص الافتراضية المستخدمة|
|---|:---:|---|
|[سياسات مكافحة البريد العشوائي](configure-your-spam-filter-policies.md): <ul><li>**البريد العشوائي** (_SpamAction_)</li><li>**بريد عشوائي عالي الثقة** (_HighConfidenceSpamAction_)</li><li>**التصيد الاحتيالي** (_PhishSpamAction_)</li><li>**التصيد الاحتيالي عالي الثقة** (_HighConfidencePhishAction_)</li><li>**مجمع** (_BulkSpamAction_)</li></ul>|نعم|<ul><li>DefaultSpamTag (الوصول الكامل)</li><li>DefaultHighConfSpamTag (الوصول الكامل)</li><li>DefaultPhishTag (الوصول الكامل)</li><li>DefaultHighConfPhishTag (بلا وصول)</li><li>DefaultBulkTag (الوصول الكامل)</li></ul>
|سياسات مكافحة التصيد الاحتيالي: <ul><li>[الحماية من المعلومات المنتحلة](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[حماية انتحال:](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)<sup>\*</sup> <ul><li>**إذا تم اكتشاف الرسالة كمستخدم منتحل** (_TargetedUserProtectionAction_)</li><li>**إذا تم اكتشاف الرسالة كمجال منتحل** (_TargetedDomainProtectionAction_)</li><li>**إذا كشف الذكاء في علبة البريد عن مستخدم منتحل** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul></ul>|لا|n/a|
|[سياسات مكافحة البرامج الضارة](configure-anti-malware-policies.md): يتم دائما فحص كل الرسائل التي تم الكشف عنها.|لا|n/a|
|[خزينة المرفقات SharePoint OneDrive و Microsoft Teams](mdo-for-spo-odb-and-teams.md)|لا|n/a|
|[قواعد تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (المعروفة أيضا بقواعد النقل) مع الإجراء: تسليم **الرسالة** إلى الفحص المستضاف (_الفحص_).|لا|n/a|
|

<sup>\*</sup>تتوفر إعدادات الحماية من التصيد الاحتيالي فقط في سياسات مكافحة التصيد الاحتيالي في Microsoft Defender Office 365.

إذا كنت راضيا عن أذونات المستخدم النهائي التي توفرها سياسات الفحص الافتراضية، فلا تحتاج إلى القيام بأي شيء. إذا كنت تريد تخصيص قدرات المستخدم النهائي (الأزرار المتوفرة) في إعلامات البريد العشوائي للمستخدم النهائي أو في تفاصيل الرسائل المعزولة، يمكنك تعيين نهج عزل مخصص.

### <a name="assign-quarantine-policies-in-anti-spam-policies-in-the-microsoft-365-defender-portal"></a>تعيين سياسات الفحص في سياسات مكافحة البريد العشوائي في مدخل Microsoft 365 Defender

يتم وصف الإرشادات الكاملة لإنشاء سياسات مكافحة البريد العشوائي وتعديلها في تكوين سياسات مكافحة البريد العشوائي [في EOP](configure-your-spam-filter-policies.md).

1. في مدخل Microsoft 365 Defender، انتقل إلى **البريد** \>  \> الإلكتروني & سياسات التعاون & قواعد البريد الإلكتروني  في \> **قسم مكافحة البريد العشوائي**. أو، افتح <https://security.microsoft.com/antispam>.

2. على الصفحة **"سياسات مكافحة البريد** العشوائي"، يمكنك تنفيذ إحدى الخطوات التالية:
   - ابحث عن نهج موجود لمكافحة البريد العشوائي **الوارد** وحدده.
   - إنشاء نهج جديد **لمكافحة** البريد العشوائي الوارد.

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير نهج مكافحة** البريد العشوائي الموجود: في القائمة من القائمة المن القائمة التفاصيل الخاصة ب النهج، انتقل  إلى المقطع إجراءات، ثم انقر فوق **تحرير الإجراءات**.
   - **إنشاء نهج جديد لمكافحة البريد العشوائي**: في معالج النهج الجديد، انتقل إلى **صفحة الإجراءات** .

4. في صفحة **الإجراءات** . سيكون لكل قرار يحتوي على إجراء **رسالة "** الفحص" أيضا مربع  نهج تحديد الفحص لكي تحدد نهج الفحص المقابل.

   **ملاحظة**: عند إنشاء نهج جديد، تشير قيمة نهج تحديد  الفحص الفارغة إلى استخدام نهج الفحص الافتراضي لهذا القرار. عند تحرير النهج لاحقا، يتم استبدال القيم الفارغة بأسماء نهج الفحص الافتراضي الفعلي كما هو موضح في الجدول السابق.

   ![تحديدات نهج الفحص في نهج مكافحة البريد العشوائي](../../media/quarantine-tags-in-anti-spam-policies.png)

5. عند الانتهاء، انقر فوق **حفظ**.

#### <a name="assign-quarantine-policies-in-anti-spam-policies-in-powershell"></a>تعيين سياسات الفحص في سياسات مكافحة البريد العشوائي في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين سياسات الفحص في سياسات مكافحة البريد العشوائي، فتواصل مع Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدام بناء الجملة التالي:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>">  [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**ملاحظات**:

- القيمة الافتراضية لمعلمة _HighConfidencePhishAction_ هي "الفحص"، لذلك لست بحاجة إلى تعيين الإجراء "الفحص" للكشف عن التصيد الاحتيالي عالي الثقة في سياسات مكافحة البريد العشوائي الجديدة. بالنسبة إلى كل الأحكام الأخرى المتعلقة بتصفية البريد العشوائي في نهج مكافحة البريد العشوائي الجديدة أو الموجودة، يكون نهج الفحص فعالا فقط إذا كانت قيمة الإجراء هي "الفحص". لرؤية قيم الإجراءات في سياسات مكافحة البريد العشوائي الموجودة، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-HostedContentFilterPolicy | Format-Table Name,*SpamAction,HighConfidencePhishAction
  ```

  للحصول على معلومات حول قيم الإجراءات الافتراضية وقيم الإجراءات الموصى بها للقيم القياسية والمتقيدة، راجع إعدادات نهج مكافحة البريد العشوائي [في EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- يعني قرار تصفية البريد العشوائي بدون معلمة نهج الفحص المقابلة استخدام نهج [الفحص الافتراضي](#step-2-assign-a-quarantine-policy-to-supported-features) لهذا القرار.

  ستحتاج فقط إلى استبدال نهج عزل افتراضي ونمح عزل مخصص إذا كنت تريد تغيير قدرات المستخدم الافتراضي على الرسائل المعزولة.

- يتطلب نهج جديد لمكافحة البريد العشوائي في PowerShell نهج تصفية البريد العشوائي (الإعدادات) باستخدام الأمر **cmdlet New-HostedContentFilterPolicy** ولقاعدة جديدة لتصفية البريد العشوائي (عوامل تصفية المستلمين) باستخدام الأمر **cmdlet New-HostedContentFilterRule** . للحصول على الإرشادات، راجع [استخدام PowerShell لإنشاء سياسات مكافحة البريد العشوائي](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

ينشئ هذا المثال نهج تصفية بريد عشوائي جديد يسمى قسم الأبحاث مع الإعدادات التالية:

- تم تعيين الإجراء لكل الأحكام الخاصة بتصفية البريد العشوائي إلى "الفحص".
- يحل نهج الفحص المخصص المسمى NoAccess الذي يعين أذونات **"** بلا وصول" محل أي نهج عزل افتراضية لم يتم تعيين أذونات الوصول إليها  بشكل افتراضي.

```powershell
New-HostedContentFilterPolicy -Name Research Department -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

يعدل هذا المثال نهج عامل تصفية البريد العشوائي الحالي المسمى الموارد البشرية. يتم تعيين الإجراء الخاص بحكم عزل البريد العشوائي إلى "الفحص"، كما يتم تعيين نهج الفحص المخصص المسمى NoAccesss.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>تكوين إعدادات إعلامات الفحص العام في مدخل Microsoft 365 Defender

تسمح لك الإعدادات العامة لنهج الفحص بتخصيص إعلامات البريد العشوائي للمستخدم النهائي التي يتم إرسالها إلى مستلمي الرسائل التي تم فحصها. لمزيد من المعلومات حول هذه الإعلامات، راجع [إعلامات البريد العشوائي للمستخدم النهائي](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. في مدخل Microsoft 365 Defender، انتقل إلى **البريد** \> \> الإلكتروني & قواعد سياسات **التعاون في** \> العمل على الفحص ثم حدد **سياسات الفحص**.

2. في صفحة **نهج الفحص** ، حدد **الإعدادات العامة**.

3. في قائمة **إعدادات الإعلامات** المعزولة التي تفتح، قم بتكوين بعض الإعدادات التالية أو كلها:

   - **اسم العرض**: تخصيص اسم عرض المرسل المستخدم في إعلامات البريد العشوائي للمستخدم النهائي.

     لكل لغة أضفتها، حدد اللغة في مربع اللغة الثاني (لا تنقر فوق X) وأدخل القيمة النصية التي تريدها في **المربع اسم** العرض.

     تعرض لقطة الشاشة التالية اسم العرض المخصص في إعلام البريد العشوائي للمستخدم النهائي:

     ![اسم عرض مرسل مخصص في إعلام البريد العشوائي للمستخدم النهائي](../../media/quarantine-tags-esn-customization-display-name.png)

   - **إخلاء المسؤولية**: أضف إخلاء إخلاء المسؤولية المخصص إلى أسفل إعلامات البريد العشوائي للمستخدم النهائي. النص المكتوب، إخلاء المسؤولية من **مؤسستك:** يتم تضمينه أولا دائما، متبوع بالنص الذي تحدده.

     لكل لغة أضفتها، حدد اللغة في مربع اللغة الثاني (لا تنقر فوق X) وأدخل القيمة النصية التي تريدها في مربع **إخلاء المسؤولية.**

     تعرض لقطة الشاشة التالية إخلاء المسؤولية المخصص في إعلام البريد العشوائي للمستخدم النهائي:

     ![إخلاء المسؤولية المخصص في أسفل إعلام البريد العشوائي للمستخدم النهائي](../../media/quarantine-tags-esn-customization-disclaimer.png)

   - **اختر اللغة**: يتم بالفعل تعريف إعلامات البريد العشوائي للمستخدم النهائي استنادا إلى إعدادات لغة المستلم. يمكنك تحديد نص مخصص بلغات مختلفة **لقيم** "اسم العرض" و" **إخلاء** المسؤولية".

     حدد لغة واحدة على الأقل من مربع اللغة الأولى، ثم انقر فوق **إضافة**. يمكنك تحديد لغات متعددة بالنقر فوق **إضافة** بعد كل لغة. يعرض مربع لغة المقطع كل اللغات التي حددتها:

     ![اللغات المحددة في مربع اللغة الثانية في إعدادات إعلامات الفحص العام لنهج الفحص](../../media/quarantine-tags-esn-customization-selected-languages.png)

   - **استخدام شعار شركتي**: حدد هذا الخيار لاستبدال شعار Microsoft الافتراضي الذي يتم استخدامه في أعلى إعلامات البريد العشوائي للمستخدم النهائي. قبل القيام بذلك، ستحتاج إلى اتباع الإرشادات الواردة في [تخصيص](../../admin/setup/customize-your-organization-theme.md) Microsoft 365 لمنظمتك لتحميل شعارك المخصص.

     تعرض لقطة الشاشة التالية شعارا مخصصا في إعلام البريد العشوائي للمستخدم النهائي:

     ![شعار مخصص في إعلام البريد العشوائي للمستخدم النهائي](../../media/quarantine-tags-esn-customization-logo.png)

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>عرض سياسات الفحص في مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، انتقل إلى **البريد** \> \> الإلكتروني & قواعد سياسات **التعاون في** \> العمل على الفحص ثم حدد **سياسات الفحص**.

2. تعرض **صفحة نهج الفحص** قائمة النهج حسب **الاسم** **وتاريخ التحديث** الأخير.

3. لعرض إعدادات نهج الفحص المضمنة أو المخصصة، حدد نهج الفحص من القائمة بالنقر فوق الاسم.

4. لعرض الإعدادات العالمية، انقر فوق **الإعدادات العالمية**

### <a name="view-quarantine-policies-in-powershell"></a>عرض سياسات الفحص في PowerShell

إذا كنت تفضل استخدام PowerShell لعرض سياسات الفحص، فتابع تنفيذ أي من الخطوات التالية:

- لعرض قائمة ملخصة بكل النهج المضمنة أو المخصصة، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-QuarantineTag | Format-Table Name
  ```

- لعرض إعدادات نهج \<QuarantinePolicyName\> الفحص المضمنة أو المخصصة، استبدل باسم نهج الفحص، ثم ادير الأمر التالي:

  ```powershell
  Get-QuarantineTag -Identity "<QuarantinePolicyName>"
  ```

- لعرض الإعدادات العامة، تشغيل الأمر التالي:

  ```powershell
  Get-QuarantineTag -QuarantineTagType GlobalQuarantineTag
  ```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>تعديل سياسات الفحص في مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، انتقل إلى **البريد** \> \> الإلكتروني & قواعد سياسات **التعاون في** \> العمل على الفحص ثم حدد **سياسات الفحص**.

2. في الصفحة **نهج الفحص** ، حدد النهج بالنقر فوق الاسم.

3. بعد تحديد النهج، انقر فوق الأيقونة ![تحرير النهج **أيقونة**](../../media/m365-cc-sc-edit-icon.png) تحرير النهج التي تظهر.

4. يكون **معالج تحرير النهج** الذي يتم فتحه مماثلا تقريبا لمعالج  النهج الجديد كما هو موضح في المقطع إنشاء [](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) نهج الفحص في Microsoft 365 Defender المدخل السابق في هذه المقالة.

   الفرق الرئيسي هو: لا يمكنك إعادة تسمية نهج موجود.

5. عند الانتهاء من تعديل النهج، انتقل إلى صفحة **الملخص** وانقر فوق **إرسال**.

### <a name="modify-quarantine-policies-in-powershell"></a>تعديل سياسات الفحص في PowerShell

إذا كنت تفضل استخدام PowerShell \<QuarantinePolicyName\> لتعديل نهج عزل مخصص، فاستبدله باسم نهج الفحص، ثم استخدم بناء الجملة التالي:

```powershell
Set-QuarantineTag -Identity "<QuarantinePolicyName>" [Settings]
```

الإعدادات المتوفرة هي نفس الإعدادات الموضحة لإنشاء سياسات الفحص المذكورة سابقا في هذه المقالة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-QuarantineTag](/powershell/module/exchange/set-quarantinetag).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>إزالة سياسات الفحص في مدخل Microsoft 365 Defender

**ملاحظات**:

- لا يمكنك إزالة سياسات الفحص المضمنة.
- قبل إزالة نهج الفحص المخصص، تحقق من عدم استخدامه. على سبيل المثال، تشغيل الأمر التالي في PowerShell:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag
  ```

  إذا كان يتم استخدام نهج الفحص، فاستبدل نهج [الفحص المعين](#step-2-assign-a-quarantine-policy-to-supported-features) قبل إزالته.

1. في مدخل Microsoft 365 Defender، انتقل إلى **البريد** \> \> الإلكتروني & قواعد سياسات **التعاون في** \> العمل على الفحص ثم حدد **سياسات الفحص**.

2. في صفحة **نهج الفحص** ، حدد نهج الفحص المخصص الذي تريد إزالته بالنقر فوق الاسم.

3. بعد تحديد النهج، انقر فوق أيقونة ![حذف النهج **أيقونة**](../../media/m365-cc-sc-delete-icon.png) حذف النهج التي تظهر.

4. انقر **فوق إزالة النهج** في مربع حوار التأكيد الذي يظهر.

### <a name="remove-quarantine-policies-in-powershell"></a>إزالة سياسات الفحص في PowerShell

إذا كنت تفضل استخدام PowerShell \<QuarantinePolicyName\> لإزالة نهج عزل مخصص، فاستبدله باسم نهج الفحص، ثم قم بتشغيل الأمر التالي:

```powershell
Remove-QuarantineTag -Identity "<QuarantinePolicyName>"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-QuarantineTag](/powershell/module/exchange/remove-quarantinetag).

## <a name="quarantine-policy-permission-details"></a>تفاصيل أذونات نهج الفحص

تصف الأقسام التالية تأثيرات مجموعات الأذونات المحددة مسبقا والأذونات الفردية في تفاصيل الرسائل المعزولة وفي إعلامات البريد العشوائي للمستخدم النهائي.

### <a name="preset-permissions-groups"></a>مجموعات الأذونات التي تم الإعداد المسبق لها

يتم سرد الأذونات الفردية المضمنة في مجموعات الأذونات المحددة مسبقا في الجدول في بداية هذه المقالة.

#### <a name="no-access"></a>لا يمكن الوصول

إذا كان نهج الفحص يعين أذونات **"** بلا وصول" (بدون أذونات)، فلا يزال المستخدمون لديهم بعض إمكانات الأساس:

- **تفاصيل الرسالة المعزولة****: الزر عرض** رأس الرسالة متوفر دائما.

  ![الأزرار المتوفرة في تفاصيل الرسالة المعزولة إذا كان نهج الفحص لا يمنح المستخدم أذونات الوصول](../../media/quarantine-tags-quarantined-message-details-no-access.png)

- **إعلامات البريد العشوائي للمستخدم** النهائي: يكون الزر **مراجعة** الذي يأخذ المستخدم إلى الرسالة في الفحص متوفرا دائما.

  ![الأزرار المتوفرة في إعلام البريد العشوائي للمستخدم النهائي إذا كان نهج الفحص لا يمنح المستخدم أذونات الوصول](../../media/quarantine-tags-esn-no-access.png)

#### <a name="limited-access"></a>وصول محدود

إذا كان نهج الفحص يعين **أذونات الوصول** المحدود، يحصل المستخدمون على الإمكانات التالية:

- **تفاصيل الرسالة المعزولة**: تتوفر الأزرار التالية:
  - **طلب إصدار**
  - **عرض رأس الرسالة**
  - **معاينة الرسالة**
  - **حظر المرسل**
  - **إزالة من الفحص**

  ![الأزرار المتوفرة في تفاصيل الرسالة المعزولة إذا كان نهج الفحص يمنح المستخدم أذونات وصول محدودة](../../media/quarantine-tags-quarantined-message-details-limited-access.png)

- **إعلامات البريد العشوائي للمستخدم** النهائي: تتوفر الأزرار التالية:
  - **حظر المرسل**
  - **مراجعة**

  ![الأزرار المتوفرة في إعلام البريد العشوائي للمستخدم النهائي إذا كان نهج الفحص يمنح المستخدم أذونات وصول محدودة](../../media/quarantine-tags-esn-limited-access.png)

#### <a name="full-access"></a>الوصول الكامل

إذا كان نهج الفحص يعين أذونات **الوصول** الكامل (كل الأذونات المتوفرة)، يحصل المستخدمون على الإمكانات التالية:

- **تفاصيل الرسالة المعزولة**: تتوفر الأزرار التالية:
  - **رسالة الإصدار**
  - **عرض رأس الرسالة**
  - **معاينة الرسالة**
  - **حظر المرسل**
  - **السماح للمرسل**
  - **إزالة من الفحص**

  ![الأزرار المتوفرة في تفاصيل الرسالة المعزولة إذا كان نهج الفحص يمنح المستخدم أذونات الوصول الكامل](../../media/quarantine-tags-quarantined-message-details-full-access.png)

- **إعلامات البريد العشوائي للمستخدم** النهائي: تتوفر الأزرار التالية:
  - **حظر المرسل**
  - **Release**
  - **مراجعة**

  ![الأزرار المتوفرة في إعلام البريد العشوائي للمستخدم النهائي إذا كان نهج الفحص يمنح المستخدم أذونات الوصول الكامل](../../media/quarantine-tags-esn-full-access.png)

### <a name="individual-permissions"></a>الأذونات الفردية

> [!NOTE]
> تذكر أن المستخدمين دائما ما يوصون بالأزرار الموضحة في [القسم "بلا وصول](#no-access) ". لا يتم تضمين هذه الأزرار في أوصاف الأذونات الفردية.

#### <a name="allow-sender-permission"></a>السماح بإذن المرسل

يتحكم **إذن** السماح بالمرسل (_PermissionToAllowSender_) بالوصول إلى الزر الذي يسمح للمستخدمين بإضافة مرسل الرسالة المعزولة إلى قائمة المرسلين المعزولين خزينة المرسلين.

- **تفاصيل الرسالة المعزولة**:
  - **السماح بتمكين إذن** المرسل **: يتوفر الزر** السماح للمرسل.
  - **السماح بتعطيل** إذن المرسل **: الزر السماح** بالمرسل غير متوفر.

- **إعلامات البريد العشوائي للمستخدم** النهائي: لا تأثير.

لمزيد من المعلومات حول خزينة المرسلين، راجع منع حظر المرسلين الموثوق [](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379666) بهم واستخدام [Exchange Online PowerShell](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox) لتكوين مجموعة القوائم الآمنة في علبة بريد.

#### <a name="block-sender-permission"></a>حظر إذن المرسل

يتحكم **إذن** حظر المرسل (_PermissionToBlockSender_) في الوصول إلى الزر الذي يسمح للمستخدمين بإضافة مرسل الرسالة المعزولة إلى قائمة المرسلين المحظورين بشكل ملائم.

- **تفاصيل الرسالة المعزولة**:
  - **تم تمكين إذن** حظر المرسل: **يتوفر** الزر حظر المرسل.
  - **حظر إذن المرسل** معطل: **الزر حظر** المرسل غير متوفر.

- **إعلامات البريد العشوائي للمستخدم النهائي**:
  - **حظر إذن المرسل** معطل: **الزر حظر** المرسل غير متوفر.
  - **تم تمكين إذن** حظر المرسل: **يتوفر** الزر حظر المرسل.

لمزيد من المعلومات حول قائمة المرسلون المحظورون، راجع حظر [](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) الرسائل من شخص ما [واستخدام Exchange Online PowerShell](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox) لتكوين مجموعة القوائم الآمنة على علبة بريد.

#### <a name="delete-permission"></a>حذف الإذن

يتحكم **إذن** الحذف (_PermissionToDelete_) في قدرة المستخدمين على حذف رسائلهم (الرسائل التي يكون المستخدم مستلما فيها) من الفحص.

- **تفاصيل الرسالة المعزولة**:
  - **تم** تمكين إذن الحذف: **يتوفر** الزر إزالة من الفحص.
  - **تم** تعطيل الإذن حذف: الزر إزالة **من** الفحص غير متوفر.

- **إعلامات البريد العشوائي للمستخدم** النهائي: لا تأثير.

#### <a name="preview-permission"></a>إذن المعاينة

يتحكم **إذن** المعاينة (_PermissionToPreview_) في قدرة المستخدمين على معاينة رسائلهم في الفحص.

- **تفاصيل الرسالة المعزولة**:
  - **إذن** المعاينة تم تمكينه: يتوفر الزر **معاينة** الرسالة.
  - **تم** تعطيل إذن المعاينة: الزر **معاينة** الرسالة غير متوفر.

- **إعلامات البريد العشوائي للمستخدم** النهائي: لا تأثير.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>السماح للمستلمين بإطلاق رسالة من إذن الفحص

يتحكم **السماح للمستلمين** بإطلاق رسالة من إذن الفحص (_PermissionToRelease_) في قدرة المستخدمين على إصدار رسائلهم المعزولة مباشرة وبدون موافقة المسؤول.

- **تفاصيل الرسالة المعزولة**:
  - الإذن الذي تم تمكينه **: يتوفر زر** رسالة الإصدار.
  - تم تعطيل الإذن: الزر **"إصدار الرسالة** " غير متوفر.

- **إعلامات البريد العشوائي للمستخدم النهائي**:
  - تم تمكين الإذن **: يتوفر الزر** "إصدار".
  - تم تعطيل الإذن: الزر **"** إصدار" غير متوفر.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>السماح للمستلمين بطلب إصدار رسالة من إذن الفحص

يتحكم **السماح للمستلمين** بطلب إصدار رسالة من إذن الفحص (_PermissionToRequestRelease_) في قدرة المستخدمين على طلب إصدار الرسائل التي تم فحصها. يتم إصدار الرسالة فقط بعد موافقة المسؤول على الطلب.

- **تفاصيل الرسالة المعزولة**:
  - تم تمكين الإذن: **يتوفر الزر طلب** الإصدار.
  - تم تعطيل الإذن: **الزر طلب** الإصدار غير متوفر.

- **إعلامات البريد العشوائي للمستخدم** النهائي: الزر **"إصدار** " غير متوفر.
