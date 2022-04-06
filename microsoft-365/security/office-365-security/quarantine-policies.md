---
title: سياسات الفحص
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: يمكن للمسؤولين معرفة كيفية استخدام سياسات الفحص للتحكم في ما يمكن للمستخدمين القيام به للرسائل المعزولة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5133b98609c29e54361b8fe108e8810858f0d8c8
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467104"
---
# <a name="quarantine-policies"></a>سياسات الفحص

تسمح سياسات الفحص (المعروفة سابقا باسم علامات _الفحص) في_ Exchange Online Protection (EOP) و Microsoft Defender لـ Office 365 للمسؤولين بالتحكم في ما يمكن للمستخدمين القيام به للرسائل المعزولة استنادا إلى سبب عزل الرسالة.

بشكل تقليدي، يتم السماح للمستخدمين أو رفض مستويات التفاعل لرسائل الفحص استنادا إلى سبب عزل الرسالة. على سبيل المثال، يمكن للمستخدمين عرض الرسائل التي تم فحصها بواسطة تصفية مكافحة البريد العشوائي كبريد عشوائي أو مجمع، ولكن لا يمكنهم عرض الرسائل التي تم فحصها أو إصدارها على أنها تصيد احتيالي أو برامج ضارة عالية الثقة.

بالنسبة [لمميزات](#step-2-assign-a-quarantine-policy-to-supported-features) الحماية المعتمدة، تحدد سياسات الفحص ما يسمح للمستخدمين القيام به بالرسائل الخاصة بهم (الرسائل التي تكون مستلما) في الفحص وفي إعلامات _الفحص_. [إعلامات الفحص](use-spam-notifications-to-release-and-report-quarantined-messages.md) هي البديل عن إعلامات البريد العشوائي للمستخدم النهائي. يتم الآن التحكم في هذه الإعلامات بواسطة نهج الفحص، وتحتوي على معلومات حول الرسائل المعزولة لكل ميزات الحماية المعتمدة (وليس فقط نهج مكافحة البريد العشوائي وحكم نهج مكافحة التصيد الاحتيالي).

يتم تلقائيا تعيين سياسات الفحص الافتراضية التي تفرض قدرات المستخدم التاريخية إلى الإجراءات في ميزات الحماية المعتمدة التي تقوم بعزل الرسائل. أو، يمكنك إنشاء سياسات عزل مخصصة وتعيينها إلى ميزات الحماية المعتمدة للسماح للمستخدمين أو منعهم من تنفيذ إجراءات معينة على هذه الأنواع من الرسائل المعزولة.

يتم دمج أذونات نهج الفحص الفردية في مجموعات الأذونات التالية التي تم الإعداد المسبق لها:

- لا يمكن الوصول
- وصول محدود
- الوصول الكامل

يتم وصف أذونات نهج الفحص الفردية المضمنة في مجموعات الأذونات المحددة مسبقا في الجدول التالي:

|الإذن|لا يمكن الوصول|وصول محدود|الوصول الكامل|
|---|:---:|:---:|:---:|
|**حظر المرسل** (_PermissionToBlockSender_)||![علامة الاختيار.](../../media/checkmark.png)|![علامة الاختيار.](../../media/checkmark.png)|
|**حذف** (_PermissionToDelete_)||![علامة الاختيار.](../../media/checkmark.png)|![علامة الاختيار.](../../media/checkmark.png)|
|**معاينة** (_PermissionToPreview_)||![علامة الاختيار.](../../media/checkmark.png)|![علامة الاختيار.](../../media/checkmark.png)|
|**السماح للمستلمين بإطلاق رسالة من الفحص** (_PermissionToRelease_)|||![علامة الاختيار.](../../media/checkmark.png)|
|**السماح للمستلمين بطلب إصدار** رسالة من الفحص (_PermissionToRequestRelease_)||![علامة الاختيار](../../media/checkmark.png)||

يتم وصف سياسات الفحص الافتراضية ومجموعات الأذونات المقترنة بها وما إذا كانت إعلامات الفحص تم تمكينها في الجدول التالي:

|نهج الفحص الافتراضي|مجموعة الأذونات المستخدمة|هل تم تمكين إعلامات الفحص؟|
|---|---|---|
|AdminOnlyAccessPolicy|لا يمكن الوصول|لا|
|DefaultFullAccessPolicy|الوصول الكامل|لا|
|NotificationEnabledPolicy<sup>\*</sup>|الوصول الكامل|نعم|

إذا لم تعثر على الأذونات الافتراضية في مجموعات الأذونات التي تم تعيينها مسبقا، أو إذا كنت تريد تمكين إعلامات الفحص، قم بإنشاء سياسات الفحص المخصصة واستخدامها. لمزيد من المعلومات حول ما يقوم به كل إذن، [راجع القسم تفاصيل](#quarantine-policy-permission-details) أذونات نهج الفحص لاحقا في هذه المقالة.

يمكنك إنشاء سياسات الفحص وتعيينها في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell ل Microsoft 365 المؤسسات التي بها علب بريد Exchange Online؛ EOP PowerShell مستقل في مؤسسات EOP بدون Exchange Online علب البريد).

> [!NOTE]
> يتم التحكم بالمهة التي يتم فيها الاحتفاظ بالرسائل المعزولة في الفحص قبل انتهاء صلاحيتها بواسطة الاحتفاظ بالبريد العشوائي في الفحص لعدة **أيام (**_QuarantineRetentionPeriod_) في سياسات مكافحة البريد العشوائي. لمزيد من المعلومات، راجع [تكوين سياسات مكافحة البريد العشوائي في EOP](configure-your-spam-filter-policies.md).
>
> إذا قمت بتغيير نهج الفحص المعين إلى ميزة حماية معتمدة، يؤثر التغيير على الرسائل التي يتم فحصها بعد إجراء التغيير. لا تتأثر الرسائل التي تم فحصها مسبقا بواسطة ميزة الحماية هذه بإعدادات تعيين نهج الفحص الجديد.

## <a name="full-access-permissions-and-quarantine-notifications"></a>أذونات الوصول الكامل وإخطارات الفحص

<sup>\*</sup> نهج الفحص المسمى NotificationEnabledPolicy غير موجود في كل البيئات. سيكون لديك نهج الفحص NotificationEnabledPolicy إذا كانت مؤسستك تلبي كلا من المتطلبات التالية:

- كانت مؤسستك موجودة قبل تشغيل ميزة نهج الفحص (في أواخر يوليو/أوائل أغسطس 2021).
- كان لديك نهج واحد أو أكثر لمكافحة البريد [العشوائي (نهج](configure-your-spam-filter-policies.md) مكافحة البريد العشوائي الافتراضي أو نهج مكافحة البريد العشوائي المخصصة) حيث تم تشغيل إعداد تمكين  إعلامات البريد العشوائي للمستخدم النهائي.

كما هو موضح سابقا، تحل إعلامات الفحص في سياسات الفحص محل إعلامات البريد العشوائي للمستخدم النهائي التي استخدمتها في تشغيل أو إيقاف تشغيل سياسات مكافحة البريد العشوائي. يؤدي نهج الفحص المضمن المسمى DefaultFullAccessPolicy إلى تكرار الأذونات  التاريخية للرسائل المعزولة، ولكن  لا يتم تشغيل إعلامات الفحص في نهج الفحص. ونظرا لعدم إمكانية تعديل النهج المضمن، لا يمكنك تشغيل إعلامات الفحص في DefaultFullAccessPolicy.

لتوفير أذونات DefaultFullAccessPolicy ولكن مع تشغيل إعلامات الفحص، قمنا بإنشاء النهج المسمى NotificationEnabledPolicy لاستخدامه مكان DefaultFullAccessPolicy لتلك المؤسسات التي كانت بحاجة إليه (المؤسسات التي تم تشغيل إعلامات البريد العشوائي للمستخدم النهائي فيها).

بالنسبة إلى المؤسسات الجديدة أو المؤسسات القديمة التي لم يتم تمكين إعلامات البريد العشوائي للمستخدم النهائي في نهج مكافحة البريد العشوائي، لن يكون لديك نهج الفحص المسمى NotificationEnabledPolicy. الطريقة التي يمكنك بها تشغيل إعلامات الفحص هي إنشاء سياسات الفحص المخصصة واستخدامها حيث يتم تشغيل إعلامات الفحص.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة **"سياسات** الفحص"، استخدم <https://security.microsoft.com/quarantinePolicies>.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع الاتصال [Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- لعرض سياسات الفحص أو إنشائها أو تعديلها أو إزالتها، يجب أن تكون عضوا في أدوار مسؤول إدارة المؤسسة أو مسؤول الأمان أو مسؤول الفحص  في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>الخطوة 1: إنشاء سياسات الفحص في مدخل Microsoft 365 Defender

1. في مدخل [Microsoft 365 Defender،](https://security.microsoft.com) \>  \>  \> انتقل إلى & البريد الإلكتروني ونهج التعاون في & القواعد ونهج الفحص في **القسم القواعد**.

2. في صفحة **نهج الفحص** ، انقر فوق ![إضافة أيقونة نهج مخصص.](../../media/m365-cc-sc-create-icon.png) **إضافة نهج مخصص**.

3. يتم **فتح معالج النهج** الجديد. في صفحة **اسم النهج** ، أدخل اسما مختصرا ولكن فريدا في **المربع اسم** النهج. ستحتاج إلى تحديد نهج الفحص وتحديده حسب الاسم في الخطوات القادمة. عند الانتهاء، انقر فوق **التالي**.

4. في صفحة **الوصول إلى رسالة المستلم** ، حدد إحدى القيم التالية:
   - **الوصول المحدود**: تم وصف الأذونات الفردية المضمنة في مجموعة الأذونات هذه سابقا في هذه المقالة.
   - **تعيين وصول معين (متقدم)**: استخدم هذه القيمة لتحديد أذونات مخصصة. تكوين الإعدادات التالية التي تظهر:
     - **حدد تفضيلات إجراء الإصدار**: حدد إحدى القيم التالية:
       - فارغ: هذه هي القيمة الافتراضية.
       - **السماح للمستلمين بإطلاق رسالة من الفحص**
       - **السماح للمستلمين بطلب إصدار رسالة من الفحص**
     - **حدد إجراءات إضافية يمكن للمستلمين اتخاذها على الرسائل المعزولة**: حدد بعض القيم التالية أو كلها أو لا شيء منها:
       - **حذف**
       - **معاينة**
       - **حظر المرسل**

   يتم وصف هذه الأذونات وتأثيرها على الرسائل المعزولة وفي إعلامات الفحص في المقطع [تفاصيل](#quarantine-policy-permission-details) أذونات نهج الفحص لاحقا في هذه المقالة.

   عند الانتهاء، انقر فوق **التالي**.

5. في صفحة **إعلام البريد العشوائي للمستخدم** النهائي، حدد **تمكين** لتمكين إعلامات الفحص (المعروفة سابقا بإعلامات البريد العشوائي للمستخدم النهائي). عند الانتهاء، انقر فوق **التالي**.

   > [!NOTE]
   > كما هو موضح سابقا، لا يتم تشغيل الإعلامات المعزولة (AdminOnlyAccessPolicy أو DefaultFullAccessPolicy) ولا يمكنك تعديلها.

6. في صفحة **مراجعة النهج** ، راجع الإعدادات. يمكنك تحديد **تحرير** في كل مقطع لتعديل الإعدادات ضمن المقطع. أو يمكنك النقر فوق **الخلف** أو تحديد الصفحة المحددة في المعالج.

   عند الانتهاء، انقر فوق **إرسال**.

7. على صفحة التأكيد التي تظهر، انقر فوق **تم**.

أنت الآن جاهز لتعيين نهج الفحص إلى ميزة الفحص كما هو موضح في [القسم الخطوة 2](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>إنشاء سياسات الفحص في PowerShell

إذا كنت تفضل استخدام PowerShell لإنشاء سياسات الفحص، فاتصل Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدام أمر cmdlet **جديد-QuarantinePolicy**.

> [!NOTE]
> إذا لم تستخدم المعلمة _ESNEnabled_ `$true`والقيمة ، يتم إيقاف تشغيل إعلامات الفحص.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>استخدام المعلمة EndUserQuarantinePermissionsValue

لإنشاء نهج عزل باستخدام _المعلمة EndUserQuarantinePermissionsValue_ ، استخدم بناء الجملة التالي:

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

تستخدم _المعلمة EndUserQuarantinePermissionsValue_ قيمة عشرية يتم تحويلها من قيمة ثنائية. تتوافق القيمة الثنائية مع أذونات الفحص المتوفرة للمستخدم النهائي في ترتيب معين. لكل إذن، تساوي القيمة 1 True والقيمة 0 تساوي False.

يتم وصف الترتيب والقيم المطلوبة لكل إذن فردي في الجدول التالي:

|الإذن|القيمة العشرية|قيمة ثنائية|
|---|:---:|:---:|
|PermissionToViewHeader<sup>\*</sup>|128|10000000|
|PermissionToDownload<sup>\*\*</sup>|64|01000000|
|PermissionToAllowSender<sup>\*\*</sup>|32|00100000|
|PermissionToBlockSender|16|00010000|
|PermissionToRequestRelease<sup>\*\*\*</sup>|8|00001000|
|PermissionToRelease<sup>\*\*\*</sup>|4|00000100|
|PermissionToPreview|2|00000010|
|PermissionToDelete|1|00000001|

<sup>\*</sup>لا تخفي القيمة 0 الزر عرض رأس الرسالة في  تفاصيل الرسالة المعزولة (الزر متوفر دائما).

<sup>\*\*</sup> لا يتم استخدام هذا الإعداد (لا تقوم القيمة 0 أو 1 بأي شيء).

<sup>\*\*\*</sup> لا تضع كلتا القيمتين على 1. قم بتعيين واحد إلى 1 والآخر إلى 0، أو قم بتعيين كليهما إلى 0.

بالنسبة إلى أذونات الوصول المحدودة، القيم المطلوبة هي:

|الإذن|وصول محدود|
|---|:--:|
|PermissionToViewHeader|0|
|PermissionToDownload|0|
|PermissionToAllowSender|0|
|PermissionToBlockSender|1|
|PermissionToRequestRelease|1|
|PermissionToRelease|0|
|PermissionToPreview|1|
|PermissionToDelete|1|
|قيمة ثنائية|00011011|
|قيمة عشرية لاستخدامها|27|

ينشئ هذا المثال نهج عزل جديد يسمى LimitedAccess مع تشغيل إعلامات الفحص التي تقوم بتعيين أذونات الوصول المحدود كما هو موضح في الجدول السابق.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

للأذونات المخصصة، استخدم الجدول السابق للحصول على القيمة الثنائية التي تتوافق مع الأذونات التي تريدها. تحويل القيمة الثنائية إلى قيمة عشرية واستخدام القيمة العشرية للمعلمة _EndUserQuarantinePermissionsValue_ . لا تستخدم القيمة الثنائية لقيمة المعلمة.

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>الخطوة 2: تعيين نهج عزل للميزات المعتمدة

في _ميزات_ الحماية المعتمدة التي تقوم بعزل رسائل البريد الإلكتروني، يمكنك تعيين نهج الفحص إلى إجراءات الفحص المتوفرة. الميزات التي يتم وصفها لرسائل الفحص وتوفر سياسات الفحص في الجدول التالي:

|الميزة|هل تم دعم سياسات الفحص؟|سياسات الفحص الافتراضية المستخدمة|
|---|:---:|---|
|[سياسات مكافحة البريد العشوائي](configure-your-spam-filter-policies.md): <ul><li>**البريد العشوائي** (_SpamAction_)</li><li>**بريد عشوائي عالي الثقة** (_HighConfidenceSpamAction_)</li><li>**التصيد الاحتيالي** (_PhishSpamAction_)</li><li>**التصيد الاحتيالي عالي الثقة** (_HighConfidencePhishAction_)</li><li>**مجمع** (_BulkSpamAction_)</li></ul>|نعم|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>AdminOnlyAccessPolicy (بلا وصول)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li></ul>|
|سياسات مكافحة التصيد الاحتيالي: <ul><li>[الحماية من المعلومات المنتحلة](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[حماية انتحال في Defender لـ Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<ul><li>**إذا تم اكتشاف الرسالة كمستخدم منتحل** (_TargetedUserProtectionAction_)</li><li>**إذا تم اكتشاف الرسالة كمجال منتحل** (_TargetedDomainProtectionAction_)</li><li>**إذا كشف الذكاء في علبة البريد عن مستخدم منتحل** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|نعم|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>حماية انتحال:<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li></ul></li></ul>|
|[سياسات مكافحة البرامج الضارة](configure-anti-malware-policies.md): يتم دائما فحص كل الرسائل التي تم الكشف عنها.|نعم|AdminOnlyAccessPolicy (بلا وصول)|
|[خزينة المرفقات](safe-attachments.md): <ul><li>رسائل البريد الإلكتروني التي بها مرفقات تم فحصها كبرامج ضارة خزينة المرفقات (_تمكين_ و _إجراء_)</li><li>الملفات التي تم فحصها [كبرامج ضارة خزينة مرفقات SharePoint OneDrive و Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li></ul>|<ul><li>نعم</li><li>لا</li></ul>|<ul><li>AdminOnlyAccessPolicy (بلا وصول)</li><li>n/a</li></ul>|
|[قواعد تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (المعروفة أيضا بقواعد النقل) مع الإجراء: تسليم **الرسالة** إلى الفحص المستضاف (_الفحص_).|لا|n/a|

<sup>\*</sup> كما [هو موضح سابقا في هذه المقالة](#full-access-permissions-and-quarantine-notifications)، قد تستخدم مؤسستك الإعلاماتالبوليسية بدلا من DefaultFullAccessPolicy. والفرق الوحيد بين هذين الخيارين المعزولين هو أن إعلامات الفحص قيد التشغيل في NotificationEnabledPolicy ويتم إيقاف تشغيلها في DefaultFullAccessPolicy.

يتم وصف سياسات الفحص الافتراضية ومجموعات الأذونات التي تم تعيينها مسبقا والأذونات في بداية [هذه](#quarantine-policies) المقالة وفي [وقت لاحق في هذه المقالة](#preset-permissions-groups).

> [!NOTE]
> إذا كنت راضيا عن أذونات المستخدم الافتراضية وإخطارات الفحص التي تم توفيرها (أو لم يتم توفيرها) بواسطة سياسات الفحص الافتراضية، فلا تحتاج إلى القيام بأي شيء. إذا كنت تريد إضافة إمكانات المستخدم النهائي (الأزرار المتوفرة) أو إزالتها للرسائل المعزولة للمستخدم، أو تمكين إعلامات الفحص وإضافة القدرات نفسها أو إزالتها في إعلامات الفحص، يمكنك تعيين نهج عزل مختلف إلى إجراء الفحص.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>تعيين سياسات الفحص في سياسات معتمدة في مدخل Microsoft 365 Defender

### <a name="anti-spam-policies"></a>سياسات مكافحة البريد العشوائي

1. في مدخل [Microsoft 365 Defender،](https://security.microsoft.com) \>  \>  \> انتقل إلى البريد & البريد الإلكتروني ونهج التعاون & قواعد الحماية من البريد العشوائي في القسم **"** سياسات".

   أو، انتقل مباشرة إلى صفحة سياسات البريد العشوائي في **Ant** ، استخدم <https://security.microsoft.com/antispam>.

2. على الصفحة **"سياسات مكافحة البريد** العشوائي"، يمكنك تنفيذ إحدى الخطوات التالية:
   - ابحث عن نهج موجود لمكافحة البريد العشوائي **الوارد** وحدده.
   - إنشاء نهج جديد **لمكافحة** البريد العشوائي الوارد.

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير الموجود**: حدد النهج بالنقر فوق اسم النهج. في الجزء منتحل تفاصيل النهج، انتقل إلى المقطع **إجراءات** ثم انقر فوق **تحرير الإجراءات**.
   - **إنشاء جديد**: في معالج النهج الجديد، يمكنك الوصول إلى **صفحة الإجراءات** .

4. في صفحة **الإجراءات**، سيكون لكل قرار يحتوي على إجراء رسالة **الفحص** أيضا المربع تحديد نهج الفحص  لكي تحدد نهج عزل مقابل.

   **ملاحظة**: عند إنشاء نهج جديد، تشير قيمة نهج تحديد  الفحص الفارغة إلى استخدام نهج الفحص الافتراضي لهذا القرار. عند تحرير النهج لاحقا، يتم استبدال القيم الفارغة بأسماء نهج الفحص الافتراضي الفعلي كما هو موضح في الجدول السابق.

   :::image type="content" source="../../media/quarantine-tags-in-anti-spam-policies.png" alt-text="تحديدات نهج الفحص في نهج مكافحة البريد العشوائي" lightbox="../../media/quarantine-tags-in-anti-spam-policies.png":::

يتم وصف الإرشادات الكاملة لإنشاء سياسات مكافحة البريد العشوائي وتعديلها في تكوين سياسات مكافحة البريد العشوائي [في EOP](configure-your-spam-filter-policies.md).

#### <a name="anti-spam-policies-in-powershell"></a>سياسات مكافحة البريد العشوائي في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين سياسات الفحص في سياسات مكافحة البريد العشوائي، فتواصل مع Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدام بناء الجملة التالي:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**ملاحظات**:

- القيمة الافتراضية لمعلمتي _PhishSpamAction_ و _HighConfidencePhishAction_ هي "الفحص"، لذلك لن تحتاج إلى استخدام هذه المعلمات عند إنشاء سياسات جديدة لتصفية البريد العشوائي في PowerShell. بالنسبة لمعلمات _SpamAction_ و _HighConfidenceSpamAction_ _وSpamAction_ المجمعة في نهج مكافحة البريد العشوائي الجديدة أو الموجودة، يكون نهج الفحص فعالا فقط إذا كانت القيمة هي "الفحص".

  لرؤية قيم المعلمات المهمة في سياسات مكافحة البريد العشوائي الموجودة، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  للحصول على معلومات حول قيم الإجراءات الافتراضية وقيم الإجراءات الموصى بها للقيم القياسية والمتقيدة، راجع إعدادات نهج مكافحة البريد العشوائي [في EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- عند إنشاء نهج جديدة لمكافحة البريد العشوائي، فإن قرار تصفية البريد العشوائي بدون معلمة نهج الفحص المقابلة يعني استخدام نهج الفحص [](#step-2-assign-a-quarantine-policy-to-supported-features) الافتراضي لهذا القرار.

  تحتاج إلى استبدال نهج الفحص الافتراضي ونهاية الفحص المخصصة فقط إذا كنت تريد تغيير قدرات المستخدم النهائي الافتراضية على الرسائل المعزولة للحصول على قرار تصفية البريد العشوائي هذا.

- يتطلب نهج جديد لمكافحة البريد العشوائي في PowerShell نهج تصفية البريد العشوائي (الإعدادات) باستخدام الأمر **cmdlet New-HostedContentFilterPolicy** ولقاعدة تصفية البريد العشوائي الحصرية (عوامل تصفية المستلمين) باستخدام الأمر **cmdlet New-HostedContentFilterRule** . للحصول على الإرشادات، راجع [استخدام PowerShell لإنشاء سياسات مكافحة البريد العشوائي](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

ينشئ هذا المثال نهج تصفية بريد عشوائي جديد يسمى قسم الأبحاث مع الإعدادات التالية:

- تم تعيين الإجراء لكل الأحكام الخاصة بتصفية البريد العشوائي إلى "الفحص".
- يحل نهج الفحص المخصص المسمى NoAccess الذي يعين أذونات **"** بلا وصول" محل أي نهج عزل افتراضية لم يتم تعيين أذونات الوصول إليها  بشكل افتراضي.

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

يعدل هذا المثال نهج عامل تصفية البريد العشوائي الحالي المسمى الموارد البشرية. يتم تعيين الإجراء الخاص بحكم عزل البريد العشوائي إلى "الفحص"، كما يتم تعيين نهج الفحص المخصص المسمى NoAccesss.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>سياسات مكافحة التصيد الاحتيالي

تتوفر المعلومات المنتحلة في EOP Defender لـ Office 365. تتوفر حماية انتحال المستخدم والحماية من انتحال المجال وذكاء علبة البريد فقط في Defender لـ Office 365. لمزيد من المعلومات، راجع [سياسات مكافحة التصيد](set-up-anti-phishing-policies.md) الاحتيالي في Microsoft 365.

1. في مدخل [Microsoft 365 Defender،](https://security.microsoft.com) \>  \>  \> انتقل إلى & البريد الإلكتروني ونهج التعاون & قواعد الحماية من التصيد الاحتيالي في **القسم** "سياسات".

   أو، انتقل مباشرة إلى صفحة سياسات البريد العشوائي في **Ant** ، استخدم <https://security.microsoft.com/antiphishing>.

2. في صفحة **مكافحة التصيد** الاحتيالي، يمكنك القيام بوا إحدى الخطوات التالية:
   - ابحث عن نهج مكافحة التصيد الاحتيالي الموجود وحدده.
   - إنشاء نهج جديد لمكافحة التصيد الاحتيالي.

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير الموجود**: حدد النهج بالنقر فوق اسم النهج. في قائمة تفاصيل النهج، انتقل إلى المقطع **إعدادات الحماية** ثم انقر فوق **تحرير إعدادات الحماية**.
   - **إنشاء جديد**: في معالج النهج الجديد، يمكنك الوصول إلى **صفحة الإجراءات** .

4. في **صفحة إعدادات الحماية** ، تحقق من تشغيل الإعدادات التالية وتكوينها كما تقتضي الحاجة:
   - **المستخدمون الذين تم تمكينهم من الحماية**: تحديد المستخدمين.
   - **المجالات التي تم تمكينها لحمايتها**: حدد **تضمين المجالات التي** أملكها و **/أو تضمين** مجالات مخصصة وحدد المجالات.
   - **تمكين المعلومات الاستخبارية لعلبة البريد**
   - **تمكين المعلومات الاستخبارية للحماية من انتحال الشخصية**
   - **تمكين المعلومات المنتحلة**

5. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير موجود**: في القائمة من القائمة المناصة التفاصيل الخاصة ب النهج، انتقل إلى المقطع **إجراءات** ، ثم انقر فوق **تحرير الإجراءات**.
   - **إنشاء جديد**: في معالج النهج الجديد، يمكنك الوصول إلى **صفحة الإجراءات** .

6. في صفحة **الإجراءات**، سيكون لكل قرار يحتوي على إجراء  "الفحص" في الرسالة أيضا المربع تطبيق  نهج الفحص لكي تحدد نهج عزل مقابل.

   **ملاحظة**: عند إنشاء نهج جديد، تشير القيمة الفارغة لتطبيق نهج الفحص إلى استخدام نهج الفحص الافتراضي لهذا الإجراء. عند تحرير النهج لاحقا، يتم استبدال القيم الفارغة بأسماء نهج الفحص الافتراضي الفعلي كما هو موضح في الجدول السابق.

   :::image type="content" source="../../media/quarantine-tags-in-anti-phishing-policies.png" alt-text="تحديدات نهج الفحص في نهج مكافحة التصيد الاحتيالي" lightbox="../../media/quarantine-tags-in-anti-phishing-policies.png":::

تتوفر الإرشادات الكاملة لإنشاء سياسات مكافحة التصيد الاحتيالي وتعديلها في المواضيع التالية:

- [تكوين سياسات مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md)
- [تكوين سياسات مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>سياسات مكافحة التصيد الاحتيالي في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين سياسات الفحص في سياسات مكافحة التصيد الاحتيالي، فاتصل ب PowerShell Exchange Online PowerShell أو Exchange Online Protection PowerShell، ثم استخدم بناء الجملة التالي:

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**ملاحظات**:

- إن _المعلمات\*_ Enable مطلوبة ل تشغيل ميزات الحماية المحددة. القيمة الافتراضية لمعلمتي _EnableMailboxIntellgence_ و _EnableSpoofIntellgence_ هي $true، لذلك لن تحتاج إلى استخدام هذه المعلمات عند إنشاء سياسات جديدة لمكافحة التصيد الاحتيالي في PowerShell. تحتاج كافة _معلمات\*_ التمكين الأخرى إلى تعيين $true بحيث يمكنك تعيين القيمة "_\*_ عزل" في معلمات الإجراء المقابلة لتعيين نهج عزل. لا تملك أي معلمة من معلمات _*\Action_ القيمة الافتراضية "الفحص".

  لرؤية قيم المعلمات المهمة في سياسات مكافحة التصيد الاحتيالي الموجودة، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  للحصول على معلومات حول قيم الإجراءات الافتراضية وقيم الإجراءات الموصى بها ل Standard and Strict، راجع إعدادات نهج مكافحة التصيد الاحتيالي وإعدادات انتحال [EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) في نهج مكافحة التصيد الاحتيالي في [Microsoft Defender لـ Office 365.](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)

- عندما تنشئ نهج مكافحة التصيد الاحتيالي، فإن إجراء مكافحة التصيد الاحتيالي بدون معلمة نهج الفحص المقابلة يعني استخدام [](#step-2-assign-a-quarantine-policy-to-supported-features) نهج الفحص الافتراضي لهذا القرار.

  تحتاج إلى استبدال نهج عزل افتراضي ونهاية عزل مخصصة فقط إذا كنت تريد تغيير قدرات المستخدم الافتراضي على الرسائل المعزولة لهذا القرار.

- يتطلب نهج جديد لمكافحة التصيد الاحتيالي في PowerShell نهج مكافحة التصيد الاحتيالي (إعدادات) باستخدام الأمر **cmdlet الجديد AntiPhishPolicy** ولقاعدة حصرية لمكافحة التصيد الاحتيالي (عوامل تصفية المستلمين) باستخدام الأمر **cmdlet الجديد AntiPhishRule** . للحصول على الإرشادات، راجع المواضيع التالية:
  - [استخدام PowerShell لتكوين سياسات مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [استخدام Exchange Online PowerShell لتكوين سياسات مكافحة التصيد الاحتيالي](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

ينشئ هذا المثال نهج جديد لمكافحة التصيد الاحتيالي يسمى قسم الأبحاث مع الإعدادات التالية:

- تم تعيين الإجراء لكل الأحكام الخاصة بتصفية البريد العشوائي إلى "الفحص".
- يحل نهج الفحص المخصص المسمى NoAccess الذي يعين أذونات **"** بلا وصول" محل أي نهج عزل افتراضية لم يتم تعيين أذونات الوصول إليها  بشكل افتراضي.

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

يعدل هذا المثال نهج مكافحة التصيد الاحتيالي الحالي المسمى الموارد البشرية. يتم تعيين الإجراء الخاص بالرسائل التي تم اكتشافها بواسطة انتحال المستخدم و انتحال المجال إلى "الفحص"، كما يتم تعيين نهج الفحص المخصص المسمى NoAccesss.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-AntiPhishPolicy](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>سياسات مكافحة البرامج الضارة

1.  في مدخل [Microsoft 365 Defender،](https://security.microsoft.com) انتقل إلى البريد الإلكتروني **&** \>  \> \> سياسات التعاون & قواعد الحماية من البرامج الضارة في **القسم** "سياسات".

   أو، انتقل مباشرة إلى صفحة **مكافحة البرامج** الضارة، استخدم <https://security.microsoft.com/antimalwarev2>.

2. في صفحة **مكافحة البرامج** الضارة، يمكنك القيام بوا إحدى الخطوات التالية:
   - ابحث عن نهج مكافحة البرامج الضارة الموجود وحدده.
   - إنشاء نهج جديد لمكافحة البرامج الضارة.

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير الموجود**: حدد النهج بالنقر فوق اسم النهج. في قائمة تفاصيل النهج، انتقل إلى المقطع **إعدادات الحماية** ثم انقر فوق **تحرير إعدادات الحماية**.
   - **إنشاء جديد**: في معالج النهج الجديد، يمكنك الوصول إلى **صفحة الإجراءات** .

4. في الصفحة **إعدادات الحماية** ، حدد نهج عزل في المربع **نهج الفحص** .

   **ملاحظة**: عند إنشاء نهج جديد، تشير قيمة نهج الفحص  الفارغة إلى نهج الفحص الافتراضي لذلك المستخدم. عند تحرير النهج لاحقا، يتم استبدال القيمة الفارغة باسم نهج الفحص الافتراضي الفعلي كما هو موضح في الجدول السابق.

#### <a name="anti-malware-policies-in-powershell"></a>سياسات مكافحة البرامج الضارة في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين سياسات الفحص في سياسات مكافحة البرامج الضارة، فاتصل ب Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدام بناء الجملة التالي:

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**ملاحظات**:

- عند إنشاء نهج جديدة لمكافحة البرامج الضارة دون استخدام المعلمة QuarantineTag عند إنشاء نهج جديد لمكافحة البرامج الضارة، يتم استخدام نهج الفحص الافتراضي للكشف عن البرامج الضارة (AdminOnlyAccessPolicy).

  تحتاج إلى استبدال نهج الفحص الافتراضي ون نهج الفحص المخصص فقط إذا كنت تريد تغيير قدرات المستخدم الافتراضي على الرسائل التي تم فحصها كبرامج ضارة.

  لرؤية قيم المعلمات المهمة في سياسات مكافحة التصيد الاحتيالي الموجودة، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- يتطلب نهج جديد لمكافحة البرامج الضارة في PowerShell نهج تصفية البرامج الضارة (الإعدادات) باستخدام **الأمر cmdlet New-MalwareFilterPolicy** ولقاعدة تصفية البرامج الضارة الحصرية (عوامل تصفية المستلمين) باستخدام **cmdlet New-MalwareFilterRule** . للحصول على الإرشادات، راجع [استخدام Exchange Online PowerShell أو EOP PowerShell](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies) مستقل لتكوين سياسات مكافحة البرامج الضارة.

ينشئ هذا المثال نهج تصفية البرامج الضارة المسمى قسم الأبحاث الذي يستخدم نهج الفحص المخصص المسمى NoAccess الذي يعين أذونات  الوصول إلى الرسائل المعزولة.

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

يعدل هذا المثال نهج تصفية البرامج الضارة الموجود المسمى الموارد البشرية بتعيين نهج الفحص المخصص المسمى NoAccess الذي يعين أذونات الوصول إلى  الرسائل المعزولة.

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>خزينة المرفقات في Defender لـ Office 365

1. في مدخل [Microsoft 365 Defender،](https://security.microsoft.com) \>  \>  \> انتقل إلى البريد & البريد الإلكتروني ونهج التعاون & قواعد المخاطر خزينة **المرفقات** في **المقطع** "سياسات".

   أو، انتقل مباشرة **إلى صفحة** المرفقات خزينة المرفقات، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، يمكنك القيام بوا إحدى الخطوات التالية:
   - ابحث عن نهج مرفقات خزينة وحدده.
   - إنشاء نهج جديد خزينة المرفقات.

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير الموجود**: حدد النهج بالنقر فوق اسم النهج. في قائمة تفاصيل النهج، انتقل **إلى المقطع الإعدادات** ثم انقر فوق **تحرير الإعدادات**.
   - **إنشاء جديد**: في معالج النهج الجديد، يمكنك الوصول إلى **الإعدادات** الجديدة.

4. على صفحة **الإعدادات**، يمكنك القيام بالخطوات التالية:
   1. **خزينة البرامج الضارة غير المعروفة للمرفقات**: حدد **حظر** أو **استبدال** أو **تسليم ديناميكي**.
   2. حدد نهج عزل في المربع **نهج الفحص** .

   **ملاحظة**: عند إنشاء نهج جديد، تشير قيمة نهج الفحص  الفارغة إلى استخدام نهج الفحص الافتراضي. عند تحرير النهج لاحقا، يتم استبدال القيمة الفارغة باسم نهج الفحص الافتراضي الفعلي كما هو موضح في الجدول السابق.

يتم وصف الإرشادات الكاملة لإنشاء خزينة المرفقات وتعديلها في إعداد [خزينة المرفقات في Microsoft Defender لـ Office 365](set-up-safe-attachments-policies.md).

#### <a name="safe-attachments-policies-in-powershell"></a>خزينة المرفقات في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين سياسات الفحص في خزينة المرفقات، فاتصل ب Exchange Online PowerShell Exchange Online Protection PowerShell واستخدام بناء الجملة التالي:

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**ملاحظات**:

- يمكن _أن ينتج_ عن قيم معلمة الإجراء حظر أو استبدال أو DynamicDelivery رسائل معزولة (القيمة السماح لا تعزل الرسائل). قيمة المعلمة _Action_ في ذات معنى فقط عندما تكون قيمة المعلمة _Enable_ هي `$true`.

- عند إنشاء نهج خزينة مرفقات جديدة بدون استخدام المعلمة QuarantineTag، يتم استخدام نهج الفحص الافتراضي للكشف عن مرفقات خزينة في البريد الإلكتروني (AdminOnlyAccessPolicy).

  يجب استبدال نهج الفحص الافتراضي ونهج الفحص المخصص فقط إذا كنت تريد تغيير قدرات المستخدم الافتراضي على رسائل البريد الإلكتروني التي تم فحصها بواسطة نهج خزينة المرفقات.

  لرؤية قيم المعلمات المهمة، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- يتطلب نهج مرفقات خزينة الجديد في PowerShell نهج مرفق آمن (إعدادات) باستخدام **الأمر cmdlet New-SafeAttachmentPolicy** ولقاعدة مرفقات آمنة حصرية (عوامل تصفية المستلمين) باستخدام الأمر **cmdlet New-SafeAttachmentRule**. للحصول على الإرشادات، راجع [استخدام Exchange Online PowerShell أو EOP PowerShell](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) مستقل لتكوين خزينة المرفقات.

ينشئ هذا المثال نهج مرفق آمن يسمى قسم الأبحاث يمنع الرسائل التي تم الكشف عنها ويستخدم نهج الفحص المخصص المسمى NoAccess الذي يعين أذونات الوصول إلى  الرسائل التي تم فحصها.

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

يعدل هذا المثال نهج المرفقات الآمنة الموجودة المسمى الموارد البشرية بتعيين نهج الفحص المخصص المسمى NoAccess الذي يعين أذونات **الوصول** بلا.

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>تكوين إعدادات إعلامات الفحص العام في مدخل Microsoft 365 Defender

تسمح لك الإعدادات العامة لنهج الفحص بتخصيص إعلامات الفحص التي يتم إرسالها إلى مستلمي الرسائل المعزولة إذا تم تشغيل إعلامات الفحص في نهج الفحص. لمزيد من المعلومات حول هذه الإعلامات، راجع [إعلامات الفحص](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. في مدخل Microsoft 365 Defender، انتقل إلى البريد & البريد الإلكتروني ونهج التعاون **&** \>  \>  \> سياسات المخاطر في **القسم القواعد**.

2. في صفحة **نهج الفحص** ، حدد **الإعدادات العامة**.

3. في قائمة **إعدادات الإعلامات** المعزولة التي تفتح، قم بتكوين بعض الإعدادات التالية أو كلها:

   - **اسم العرض**: تخصيص اسم عرض المرسل المستخدم في إعلامات الفحص.

     لكل لغة أضفتها، حدد اللغة في مربع اللغة الثاني (لا تنقر فوق X) وأدخل القيمة النصية التي تريدها في **المربع اسم** العرض.

     تعرض لقطة الشاشة التالية اسم العرض المخصص في إعلام الفحص:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-display-name.png" alt-text="اسم عرض مرسل مخصص في إعلام الفحص" lightbox="../../media/quarantine-tags-esn-customization-display-name.png":::

   - **إخلاء المسؤولية**: أضف إخلاء إخلاء المسؤولية المخصص إلى أسفل إعلامات الفحص. النص المكتوب، إخلاء المسؤولية من **مؤسستك:** يتم تضمينه أولا دائما، متبوع بالنص الذي تحدده.

     لكل لغة أضفتها، حدد اللغة في مربع اللغة الثاني (لا تنقر فوق X) وأدخل القيمة النصية التي تريدها في مربع **إخلاء المسؤولية.**

     تعرض لقطة الشاشة التالية إخلاء المسؤولية المخصص في إعلام الفحص:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-disclaimer.png" alt-text="إخلاء المسؤولية المخصص في أسفل إعلام الفحص" lightbox="../../media/quarantine-tags-esn-customization-disclaimer.png":::

   - **اختر اللغة**: تكون إعلامات الفحص معروبة بالفعل استنادا إلى إعدادات لغة المستلم. يمكنك تحديد نص مخصص بلغات مختلفة **لقيم** "اسم العرض" و" **إخلاء** المسؤولية".

     حدد لغة واحدة على الأقل من مربع اللغة الأولى، ثم انقر فوق **إضافة**. يمكنك تحديد لغات متعددة بالنقر فوق **إضافة** بعد كل لغة. يعرض مربع لغة المقطع كل اللغات التي حددتها:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-selected-languages.png" alt-text="اللغات المحددة في مربع اللغة الثانية في إعدادات الإعلامات المعزولة العامة لنهج الفحص" lightbox="../../media/quarantine-tags-esn-customization-selected-languages.png":::

   - **استخدام شعار شركتي**: حدد هذا الخيار لاستبدال شعار Microsoft الافتراضي المستخدم في أعلى إعلامات الفحص. قبل القيام بذلك، ستحتاج إلى اتباع الإرشادات الواردة في [تخصيص](../../admin/setup/customize-your-organization-theme.md) Microsoft 365 لمنظمتك لتحميل شعارك المخصص.

     تعرض لقطة الشاشة التالية شعارا مخصصا في إعلام الفحص:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-logo.png" alt-text="شعار مخصص في إعلام الفحص" lightbox="../../media/quarantine-tags-esn-customization-logo.png":::

   - **إرسال إعلام بالبريد العشوائي للمستخدم النهائي كل (أيام)**: حدد تكرار إعلامات الفحص.

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>عرض سياسات الفحص في مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، انتقل إلى البريد & البريد الإلكتروني ونهج التعاون **&** \>  \>  \> سياسات المخاطر في **القسم القواعد**.

2. تعرض **صفحة نهج الفحص** قائمة النهج حسب **الاسم** **وتاريخ التحديث** الأخير.

3. لعرض إعدادات نهج الفحص المضمنة أو المخصصة، حدد نهج الفحص من القائمة بالنقر فوق الاسم.

4. لعرض الإعدادات العالمية، انقر فوق **الإعدادات العالمية**

### <a name="view-quarantine-policies-in-powershell"></a>عرض سياسات الفحص في PowerShell

إذا كنت تفضل استخدام PowerShell لعرض سياسات الفحص، فتابع تنفيذ أي من الخطوات التالية:

- لعرض قائمة ملخصة بكل النهج المضمنة أو المخصصة، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- لعرض إعدادات نهج \<QuarantinePolicyName\> الفحص المضمنة أو المخصصة، استبدل باسم نهج الفحص، ثم ادير الأمر التالي:

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- لعرض الإعدادات العامة الخاصة بإشعارات الفحص، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>تعديل سياسات الفحص في مدخل Microsoft 365 Defender

لا يمكنك تعديل سياسات الفحص المضمنة المسماة AdminOnlyAccessPolicy أو DefaultFullAccessPolicy. يمكنك تعديل النهج المضمن المسمى NotificationEnabledPolicy ([إذا](#full-access-permissions-and-quarantine-notifications) كان لديك) ونهج الفحص المخصصة.

1. في مدخل Microsoft 365 Defender، انتقل إلى البريد & البريد الإلكتروني ونهج التعاون **&** \>  \>  \> سياسات المخاطر في **القسم القواعد**.

2. في الصفحة **نهج الفحص** ، حدد النهج بالنقر فوق الاسم.

3. بعد تحديد النهج، انقر فوق الأيقونة ![تحرير النهج.](../../media/m365-cc-sc-edit-icon.png) **أيقونة تحرير** النهج التي تظهر.

4. يكون **معالج تحرير النهج** الذي يتم فتحه مماثلا تقريبا لمعالج  النهج الجديد كما هو موضح في المقطع إنشاء [](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) نهج الفحص في Microsoft 365 Defender المدخل السابق في هذه المقالة.

   الفرق الرئيسي هو: لا يمكنك إعادة تسمية نهج موجود.

5. عند الانتهاء من تعديل النهج، انتقل إلى صفحة **الملخص** وانقر فوق **إرسال**.

### <a name="modify-quarantine-policies-in-powershell"></a>تعديل سياسات الفحص في PowerShell

إذا كنت تفضل استخدام PowerShell \<QuarantinePolicyName\> لتعديل نهج عزل مخصص، فاستبدله باسم نهج الفحص، ثم استخدم بناء الجملة التالي:

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

الإعدادات المتوفرة هي نفس الإعدادات الموضحة لإنشاء سياسات الفحص المذكورة سابقا في هذه المقالة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>إزالة سياسات الفحص في مدخل Microsoft 365 Defender

**ملاحظات**:

- لا يمكنك إزالة سياسات الفحص المضمنة المسماة AdminOnlyAccessPolicy أو DefaultFullAccessPolicy. يمكنك إزالة النهج المضمن المسمى NotificationEnabledPolicy ([إذا](#full-access-permissions-and-quarantine-notifications) كان لديك) ونهج الفحص المخصصة.
- قبل إزالة نهج الفحص، تحقق من عدم استخدامه. على سبيل المثال، تشغيل الأمر التالي في PowerShell:

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  إذا كان يتم استخدام نهج الفحص، فاستبدل نهج [الفحص المعين](#step-2-assign-a-quarantine-policy-to-supported-features) قبل إزالته.

1. في مدخل Microsoft 365 Defender، انتقل إلى البريد & البريد الإلكتروني ونهج التعاون **&** \>  \>  \> سياسات المخاطر في **القسم القواعد**.

2. في صفحة **نهج الفحص** ، حدد نهج الفحص المخصص الذي تريد إزالته بالنقر فوق الاسم.

3. بعد تحديد النهج، انقر فوق الأيقونة ![حذف نهج.](../../media/m365-cc-sc-delete-icon.png) **أيقونة حذف** النهج التي تظهر.

4. انقر **فوق إزالة النهج** في مربع حوار التأكيد الذي يظهر.

### <a name="remove-quarantine-policies-in-powershell"></a>إزالة سياسات الفحص في PowerShell

إذا كنت تفضل استخدام PowerShell \<QuarantinePolicyName\> لإزالة نهج عزل مخصص، فاستبدله باسم نهج الفحص، ثم قم بتشغيل الأمر التالي:

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>تنبيهات النظام لطلبات إصدار الفحص

بشكل افتراضي، ينشئ نهج التنبيه الافتراضي المسمى المستخدم الذي طلب إصدار رسالة معزولة تنبيها إعلاميا تلقائيا ويرسل رسائل إعلام إلى أعضاء مجموعات الدور التالية عندما يطلب المستخدم إصدار رسالة معزولة:

- مسؤول الفحص
- مسؤول الأمان
- إدارة المؤسسة (المسؤول العام)

يمكن للمسؤولين تخصيص مستلمي إعلامات البريد الإلكتروني أو إنشاء نهج تنبيه مخصص لمزيد من الخيارات.

لمزيد من المعلومات حول سياسات التنبيه، راجع [تنبيهات في Microsoft 365](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>تفاصيل أذونات نهج الفحص

تصف الأقسام التالية تأثيرات مجموعات الأذونات المحددة مسبقا والأذونات الفردية في تفاصيل الرسائل المعزولة وفي إعلامات الفحص.

### <a name="preset-permissions-groups"></a>مجموعات الأذونات التي تم الإعداد المسبق لها

يتم سرد الأذونات الفردية المضمنة في مجموعات الأذونات المحددة مسبقا في الجدول في بداية هذه المقالة.

#### <a name="no-access"></a>لا يمكن الوصول

إذا كان نهج الفحص يعين أذونات **الوصول** بلا (وصول المسؤول فقط)، لن يتمكن المستخدمون من رؤية الرسائل التي تم فحصها:

- **تفاصيل الرسالة المعزولة**: لن تظهر أي رسائل في طريقة عرض المستخدم النهائي.
- **إعلامات الفحص**: لن يتم إرسال أي إعلامات لتلك الرسائل.

#### <a name="limited-access"></a>وصول محدود

إذا كان نهج الفحص يعين **أذونات الوصول** المحدود، يحصل المستخدمون على الإمكانات التالية:

- **تفاصيل الرسالة المعزولة**: تتوفر الأزرار التالية:
  - **طلب إصدار**
  - **عرض رؤوس الرسائل**
  - **معاينة الرسالة**
  - **إزالة من الفحص**
  - **حظر المرسل**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-limited-access.png" alt-text="الأزرار المتوفرة في تفاصيل الرسالة المعزولة إذا كان نهج الفحص يمنح المستخدم أذونات وصول محدودة" lightbox="../../media/quarantine-tags-quarantined-message-details-limited-access.png":::

- **إعلامات الفحص**: تتوفر الأزرار التالية:
  - **حظر المرسل**
  - **طلب إصدار**
  - **مراجعة**

  :::image type="content" source="../../media/quarantine-tags-esn-limited-access.png" alt-text="الأزرار المتوفرة في إعلام الفحص إذا كان نهج الفحص يمنح المستخدم أذونات وصول محدودة" lightbox="../../media/quarantine-tags-esn-limited-access.png":::

#### <a name="full-access"></a>الوصول الكامل

إذا كان نهج الفحص يعين أذونات **الوصول** الكامل (كل الأذونات المتوفرة)، يحصل المستخدمون على الإمكانات التالية:

- **تفاصيل الرسالة المعزولة**: تتوفر الأزرار التالية:
  - **رسالة الإصدار**
  - **عرض رؤوس الرسائل**
  - **معاينة الرسالة**
  - **إزالة من الفحص**
  - **حظر المرسل**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-full-access.png" alt-text="تفاصيل الأزرار المتوفرة في الرسالة المعزولة إذا كان نهج الفحص يمنح المستخدم أذونات الوصول الكامل" lightbox="../../media/quarantine-tags-quarantined-message-details-full-access.png":::

- **إعلامات الفحص**: تتوفر الأزرار التالية:
  - **حظر المرسل**
  - **Release**
  - **مراجعة**

  :::image type="content" source="../../media/quarantine-tags-esn-full-access.png" alt-text="الأزرار المتوفرة في إعلام الفحص إذا كان نهج الفحص يمنح المستخدم أذونات الوصول الكامل" lightbox="../../media/quarantine-tags-esn-full-access.png":::

### <a name="individual-permissions"></a>الأذونات الفردية

#### <a name="block-sender-permission"></a>حظر إذن المرسل

يتحكم **إذن** حظر المرسل (_PermissionToBlockSender_) في الوصول إلى الزر الذي يسمح للمستخدمين بإضافة مرسل الرسالة المعزولة إلى قائمة المرسلين المحظورين بشكل ملائم.

- **تفاصيل الرسالة المعزولة**:
  - **تم تمكين إذن** حظر المرسل: **يتوفر** الزر حظر المرسل.
  - **حظر إذن المرسل** معطل: **الزر حظر** المرسل غير متوفر.

- **إعلامات الفحص**:
  - **تم تمكين إذن** حظر المرسل: **يتوفر** الزر حظر المرسل.
  - **حظر إذن المرسل** معطل: **الزر حظر** المرسل غير متوفر.

لمزيد من المعلومات حول قائمة المرسلون المحظورون، راجع حظر [](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) الرسائل من شخص ما [واستخدام Exchange Online PowerShell](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox) لتكوين مجموعة القوائم الآمنة على علبة بريد.

#### <a name="delete-permission"></a>حذف الإذن

يتحكم **إذن** الحذف (_PermissionToDelete_) في قدرة المستخدمين على حذف رسائلهم (الرسائل التي يكون المستخدم مستلما فيها) من الفحص.

- **تفاصيل الرسالة المعزولة**:
  - **تم** تمكين إذن الحذف: **يتوفر** الزر إزالة من الفحص.
  - **تم** تعطيل الإذن حذف: الزر إزالة **من** الفحص غير متوفر.

- **إعلامات الفحص**: لا تأثير.

#### <a name="preview-permission"></a>إذن المعاينة

يتحكم **إذن** المعاينة (_PermissionToPreview_) في قدرة المستخدمين على معاينة رسائلهم في الفحص.

- **تفاصيل الرسالة المعزولة**:
  - **إذن** المعاينة تم تمكينه: يتوفر الزر **معاينة** الرسالة.
  - **تم** تعطيل إذن المعاينة: الزر **معاينة** الرسالة غير متوفر.

- **إعلامات الفحص**: لا تأثير.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>السماح للمستلمين بإطلاق رسالة من إذن الفحص

يتحكم **السماح للمستلمين** بإطلاق رسالة من إذن الفحص (_PermissionToRelease_) في قدرة المستخدمين على إصدار رسائلهم المعزولة مباشرة وبدون موافقة المسؤول.

- **تفاصيل الرسالة المعزولة**:
  - الإذن الذي تم تمكينه **: يتوفر زر** رسالة الإصدار.
  - تم تعطيل الإذن: الزر **"إصدار الرسالة** " غير متوفر.

- **إعلامات الفحص**:
  - تم تمكين الإذن **: يتوفر الزر** "إصدار".
  - تم تعطيل الإذن: الزر **"** إصدار" غير متوفر.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>السماح للمستلمين بطلب إصدار رسالة من إذن الفحص

يتحكم **السماح للمستلمين** بطلب إصدار رسالة من إذن الفحص (_PermissionToRequestRelease_) في قدرة المستخدمين على طلب إصدار الرسائل التي تم فحصها. يتم إصدار الرسالة فقط بعد موافقة المسؤول على الطلب.

- **تفاصيل الرسالة المعزولة**:
  - تم تمكين الإذن: **يتوفر الزر طلب** الإصدار.
  - تم تعطيل الإذن: **الزر طلب** الإصدار غير متوفر.

- **إعلامات الفحص**:
  - تم تمكين الإذن: **يتوفر الزر طلب** الإصدار.
  - تم تعطيل الإذن: **الزر طلب** الإصدار غير متوفر.
