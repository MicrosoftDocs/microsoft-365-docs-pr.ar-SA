---
title: سياسات العزل
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
description: يمكن للمسؤولين معرفة كيفية استخدام نهج العزل للتحكم في ما يمكن للمستخدمين القيام به للرسائل المعزولة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a3d50debf31f53f75177e7c8cf8c7116ae3789b6
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128844"
---
# <a name="quarantine-policies"></a>سياسات العزل

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على:**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تسمح نهج العزل (المعروفة سابقا باسم _علامات العزل_) في Exchange Online Protection (EOP) والمسؤولين Microsoft Defender لـ Office 365 بالتحكم في ما يمكن للمستخدمين القيام به للرسائل المعزولة استنادا إلى سبب عزل الرسالة.

تقليديا، تم السماح للمستخدمين أو رفض مستويات التفاعل لرسائل العزل بناء على سبب عزل الرسالة. على سبيل المثال، يمكن للمستخدمين عرض الرسائل التي تم عزلها من قبل تصفية مكافحة البريد العشوائي أو كرسائل غير هامة أو مجمعة وإصدارها، ولكن لا يمكنهم عرض الرسائل التي تم عزلها على أنها تصيد احتيالي عالي الثقة أو برامج ضارة.

بالنسبة [لميزات الحماية المدعومة](#step-2-assign-a-quarantine-policy-to-supported-features)، تحدد نهج العزل ما يسمح للمستخدمين بالقيام به لرسائلهم الخاصة (الرسائل حيث هم مستلمون) في العزل وفي _إعلامات العزل_. [إعلامات العزل](use-spam-notifications-to-release-and-report-quarantined-messages.md) هي البديل لإعلامات البريد العشوائي للمستخدم النهائي. يتم الآن التحكم في هذه الإعلامات بواسطة نهج العزل، وتحتوي على معلومات حول الرسائل المعزولة لجميع ميزات الحماية المدعومة (وليس فقط سياسة مكافحة البريد العشوائي وأحكام نهج مكافحة التصيد الاحتيالي).

يتم تعيين نهج العزل الافتراضية التي تفرض قدرات المستخدم التاريخية تلقائيا إلى الإجراءات في ميزات الحماية المدعومة التي تقوم بعزل الرسائل. أو، يمكنك إنشاء نهج عزل مخصصة وتعيينها إلى ميزات الحماية المعتمدة للسماح للمستخدمين بتنفيذ إجراءات معينة على هذه الأنواع من الرسائل المعزولة أو منعهم منها.

يتم دمج أذونات نهج العزل الفردية في مجموعات الأذونات التي تم تعيينها مسبقا التالية:

- لا يوجد وصول
- وصول محدود
- الوصول الكامل

يتم وصف أذونات نهج العزل الفردية الموجودة في مجموعات الأذونات المعينة مسبقا في الجدول التالي:

|اذن|لا يوجد وصول|وصول محدود|الوصول الكامل|
|---|:---:|:---:|:---:|
|**مرسل الحظر** (_PermissionToBlockSender_)||![علامة الاختيار.](../../media/checkmark.png)|![علامة الاختيار.](../../media/checkmark.png)|
|**حذف** (_PermissionToDelete_)||![علامة الاختيار.](../../media/checkmark.png)|![علامة الاختيار.](../../media/checkmark.png)|
|**معاينة** (_PermissionToPreview_)||![علامة الاختيار.](../../media/checkmark.png)|![علامة الاختيار.](../../media/checkmark.png)|
|**السماح للمستلمين بتحرير رسالة من العزل** (_PermissionToRelease_)|||![علامة الاختيار.](../../media/checkmark.png)|
|**السماح للمستلمين بطلب إصدار رسالة من العزل** (_PermissionToRequestRelease_)||![علامة اختيار](../../media/checkmark.png)||

يتم وصف نهج العزل الافتراضية ومجموعات الأذونات المقترنة بها وما إذا كانت إعلامات العزل ممكنة في الجدول التالي:

|نهج العزل الافتراضي|مجموعة الأذونات المستخدمة|هل تم تمكين إعلامات العزل؟|
|---|:---:|:---:|
|AdminOnlyAccessPolicy|لا يوجد وصول|لا|
|DefaultFullAccessPolicy|الوصول الكامل|لا|
|NotificationEnabledPolicy<sup>\*</sup>|الوصول الكامل|نعم|

إذا لم تعجبك الأذونات الافتراضية في مجموعات الأذونات التي تم تعيينها مسبقا، أو إذا كنت تريد تمكين إعلامات العزل، فتنشئ نهج العزل المخصصة وتستخدمها. لمزيد من المعلومات حول ما يفعله كل إذن، راجع قسم [تفاصيل أذونات نهج العزل](#quarantine-policy-permission-details) لاحقا في هذه المقالة.

يمكنك إنشاء نهج العزل وتعيينها في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell للمؤسسات Microsoft 365 مع علب بريد Exchange Online؛ EOP PowerShell مستقل في مؤسسات EOP دون Exchange Online علب البريد).

> [!NOTE]
> يتم التحكم في مدة الاحتفاظ بالرسائل المعزولة قبل انتهاء صلاحيتها بواسطة الاحتفاظ بالبريد **العشوائي في العزل لعدة أيام** (_QuarantineRetentionPeriod_) في نهج مكافحة البريد العشوائي. لمزيد من المعلومات، راجع [تكوين نهج مكافحة البريد العشوائي في EOP](configure-your-spam-filter-policies.md).
>
> إذا قمت بتغيير نهج العزل الذي تم تعيينه إلى ميزة حماية معتمدة، يؤثر التغيير على الرسائل التي يتم عزلها _بعد_ إجراء التغيير. لا تتأثر الرسائل التي تم عزلها مسبقا بواسطة ميزة الحماية هذه بإعدادات تعيين نهج العزل الجديد.

## <a name="full-access-permissions-and-quarantine-notifications"></a>أذونات الوصول الكامل وإعلامات العزل

<sup>\*</sup> نهج العزل المسمى NotificationEnabledPolicy غير موجود في جميع البيئات. سيكون لديك نهج العزل NotificationEnabledPolicy إذا كانت مؤسستك تلبي كلا المتطلبات التالية:

- كانت مؤسستك موجودة قبل تشغيل ميزة نهج العزل (في أواخر يوليو/أوائل أغسطس 2021).
- كان لديك نهج واحد أو أكثر [لمكافحة البريد العشوائي](configure-your-spam-filter-policies.md) (نهج مكافحة البريد العشوائي الافتراضي أو نهج مكافحة البريد العشوائي المخصصة) حيث تم تشغيل إعداد **تمكين إعلامات البريد العشوائي للمستخدم** النهائي.

كما هو موضح سابقا، تحل إعلامات العزل في نهج العزل محل إعلامات البريد العشوائي للمستخدم النهائي التي استخدمتها لتشغيل نهج مكافحة البريد العشوائي أو إيقاف تشغيلها. يكرر نهج العزل المضمن المسمى DefaultFullAccessPolicy _الأذونات_ التاريخية للرسائل المعزولة، ولكن _إعلامات العزل_ غير قيد التشغيل في نهج العزل. ولأنه لا يمكنك تعديل النهج المضمن، لا يمكنك تشغيل إعلامات العزل في DefaultFullAccessPolicy.

لتوفير أذونات DefaultFullAccessPolicy ولكن مع تشغيل إعلامات العزل، أنشأنا النهج المسمى NotificationEnabledPolicy لاستخدامه بدلا من DefaultFullAccessPolicy للمؤسسات التي تحتاج إليه (المؤسسات التي تم فيها تشغيل إعلامات البريد العشوائي للمستخدم النهائي).

بالنسبة للمؤسسات الجديدة أو المؤسسات القديمة التي لم يتم تمكين إعلامات البريد العشوائي للمستخدم النهائي في نهج مكافحة البريد العشوائي، لن يكون لديك نهج العزل المسمى NotificationEnabledPolicy. الطريقة التي يمكنك من خلالها تشغيل إعلامات العزل هي إنشاء نهج العزل المخصصة واستخدامها حيث يتم تشغيل إعلامات العزل.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **نهج العزل** ، استخدم <https://security.microsoft.com/quarantinePolicies>.

- للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع [الاتصال إلى Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- لعرض نهج العزل أو إنشائها أو تعديلها أو إزالتها، يجب أن تكون عضوا في أدوار **إدارة المؤسسة** أو **مسؤول الأمان** أو **مسؤول العزل** في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>الخطوة 1: إنشاء نهج العزل في مدخل Microsoft 365 Defender

1. في [مدخل Microsoft 365 Defender](https://security.microsoft.com)، انتقل إلى **نهج التعاون** \> & البريد الإلكتروني **&** \> نهج **"قواعد التهديد** \> **" في** قسم **"القواعد**". أو للانتقال مباشرة إلى صفحة **نهج العزل** ، استخدم <https://security.microsoft.com/quarantinePolicies>.

2. في صفحة **نهج العزل** ، انقر فوق ![أيقونة "إضافة نهج مخصص".](../../media/m365-cc-sc-create-icon.png) **إضافة نهج مخصص**.

3. يفتح معالج **النهج الجديد** . في صفحة **اسم النهج** ، أدخل اسما موجزا ولكنه فريد في مربع **اسم النهج** . ستحتاج إلى تحديد نهج العزل وتحديده بالاسم في الخطوات القادمة. عند الانتهاء، انقر فوق **"التالي**".

4. في صفحة **الوصول إلى رسالة المستلم** ، حدد إحدى القيم التالية:
   - **وصول محدود**: تم وصف الأذونات الفردية المضمنة في مجموعة الأذونات هذه مسبقا في هذه المقالة.
   - **تعيين وصول معين (متقدم)**: استخدم هذه القيمة لتحديد أذونات مخصصة. تكوين الإعدادات التالية التي تظهر:
     - **تحديد تفضيل إجراء الإصدار**: حدد إحدى القيم التالية:
       - فارغ: هذه هي القيمة الافتراضية.
       - **السماح للمستلمين بتحرير رسالة من العزل**
       - **السماح للمستلمين بطلب إصدار رسالة من العزل**
     - **حدد إجراءات إضافية يمكن للمستلمين اتخاذها في الرسائل المعزولة**: حدد بعض القيم التالية أو كلها أو لا شيء منها:
       - **حذف**
       - **معاينه**
       - **حظر المرسل**

   يتم وصف هذه الأذونات وتأثيرها على الرسائل المعزولة وفي إعلامات العزل في قسم [تفاصيل أذونات نهج العزل](#quarantine-policy-permission-details) لاحقا في هذه المقالة.

   عند الانتهاء، انقر فوق **"التالي**".

5. في صفحة **إعلام البريد العشوائي للمستخدم النهائي** ، حدد **"تمكين** " لتمكين إعلامات العزل (المعروفة سابقا باسم إعلامات البريد العشوائي للمستخدم النهائي). عند الانتهاء، انقر فوق **"التالي**".

   > [!NOTE]
   > كما هو موضح سابقا، لا تحتوي النهج المضمنة (AdminOnlyAccessPolicy أو DefaultFullAccessPolicy) على إعلامات تم عزلها قيد التشغيل، ولا يمكنك تعديل النهج.

6. في صفحة **مراجعة النهج** ، راجع الإعدادات. يمكنك تحديد **"تحرير"** في كل مقطع لتعديل الإعدادات داخل المقطع. أو يمكنك النقر فوق **"الخلف"** أو تحديد الصفحة المحددة في المعالج.

   عند الانتهاء، انقر فوق **"إرسال**".

7. في صفحة التأكيد التي تظهر، انقر فوق **"تم**".

الآن أنت مستعد لتعيين نهج العزل إلى ميزة العزل كما هو موضح في قسم [الخطوة 2](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>إنشاء نهج العزل في PowerShell

إذا كنت تفضل استخدام PowerShell لإنشاء نهج العزل، فتواصل مع Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدم **New-QuarantinePolicy** cmdlet.

> [!NOTE]
> إذا لم تستخدم المعلمة _ESNEnabled_ والقيمة `$true`، فسيتم إيقاف تشغيل إعلامات العزل.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>استخدام المعلمة EndUserQuarantinePermissionsValue

لإنشاء نهج عزل باستخدام المعلمة _EndUserQuarantinePermissionsValue_ ، استخدم بناء الجملة التالي:

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

تستخدم المعلمة _EndUserQuarantinePermissionsValue_ قيمة عشرية يتم تحويلها من قيمة ثنائية. تتوافق القيمة الثنائية مع أذونات العزل المتوفرة للمستخدم النهائي بترتيب معين. لكل إذن، القيمة 1 تساوي True والقيمة 0 تساوي False.

يتم وصف الترتيب والقيم المطلوبة لكل إذن فردي في الجدول التالي:

|اذن|قيمة عشرية|قيمة ثنائية|
|---|:---:|:---:|
|PermissionToViewHeader<sup>\*</sup>|128|10000000|
|PermissionToDownload<sup>\*\*</sup>|64|01000000|
|PermissionToAllowSender<sup>\*\*</sup>|32|00100000|
|PermissionToBlockSender|16|00010000|
|PermissionToRequestRelease<sup>\*\*\*</sup>|8|00001000|
|PermissionToRelease<sup>\*\*\*</sup>|4|00000100|
|PermissionToPreview|2|00000010|
|PermissionToDelete|1|00000001|

<sup>\*</sup> لا تخفي القيمة 0 الزر **"عرض رأس الرسالة** " في تفاصيل الرسالة المعزولة (الزر متوفر دائما).

<sup>\*\*</sup> لا يتم استخدام هذا الإعداد (القيمة 0 أو 1 لا تفعل شيئا).

<sup>\*\*\*</sup> لا تقم بتعيين كلتا القيمتين إلى 1. تعيين واحد إلى 1 والآخر إلى 0، أو تعيين كليهما إلى 0.

بالنسبة لأذونات الوصول المحدود، تكون القيم المطلوبة هي:

|اذن|وصول محدود|
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
|القيمة العشرية المطلوب استخدامها|27|

ينشئ هذا المثال نهج عزل جديد يسمى LimitedAccess مع تشغيل إعلامات العزل التي تعين أذونات الوصول المحدود كما هو موضح في الجدول السابق.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

للحصول على أذونات مخصصة، استخدم الجدول السابق للحصول على القيمة الثنائية التي تتوافق مع الأذونات التي تريدها. قم بتحويل القيمة الثنائية إلى قيمة عشرية واستخدم القيمة العشرية للمعلمة _EndUserQuarantinePermissionsValue_ . لا تستخدم القيمة الثنائية لقيمة المعلمة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>الخطوة 2: تعيين نهج العزل إلى الميزات المدعومة

في ميزات الحماية _المدعومة_ التي تقوم بعزل رسائل البريد الإلكتروني، يمكنك تعيين نهج عزل إلى إجراءات العزل المتوفرة. يتم وصف الميزات التي تقوم بعزل الرسائل وتوفر نهج العزل في الجدول التالي:

|ميزه|هل سياسات العزل مدعومة؟|نهج العزل الافتراضية المستخدمة|
|---|:---:|---|
|[نهج مكافحة البريد العشوائي](configure-your-spam-filter-policies.md): <ul><li>**البريد العشوائي** (_SpamAction_)</li><li>**البريد العشوائي عالي الثقة** (_HighConfidenceSpamAction_)</li><li>**التصيد الاحتيالي** (_PhishSpamAction_)</li><li>**التصيد الاحتيالي عالي الثقة** (_HighConfidencePhishAction_)</li><li>**Bulk** (_BulkSpamAction_)</li></ul>|نعم|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>AdminOnlyAccessPolicy (بدون وصول)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li></ul>|
|نهج مكافحة التصيد الاحتيالي: <ul><li>[Spoof intelligence protection](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[حماية انتحال الهوية في Defender لـ Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<ul><li>**إذا تم الكشف عن الرسالة كمستخدم منتحل** (_TargetedUserProtectionAction_)</li><li>**إذا تم الكشف عن الرسالة كمجال منتحل** (_TargetedDomainProtectionAction_)</li><li>**إذا كشف تحليل معلومات علبة البريد عن مستخدم منتحل** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|نعم|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>حماية الانتحال:<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (الوصول الكامل)</li></ul></li></ul>|
|[نهج مكافحة البرامج الضارة](configure-anti-malware-policies.md): يتم عزل جميع الرسائل المكتشفة دائما.|نعم|AdminOnlyAccessPolicy (بدون وصول)|
|[حماية المرفقات خزينة](safe-attachments.md): <ul><li>رسائل البريد الإلكتروني التي تحتوي على مرفقات تم عزلها كبرود ضار بواسطة نهج المرفقات خزينة (_تمكين_ _وإجراء)_</li><li>الملفات التي تم عزلها كالبرمجيات الضارة بواسطة [مرفقات خزينة SharePoint OneDrive Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li></ul>|<ul><li>نعم</li><li>لا</li></ul>|<ul><li>AdminOnlyAccessPolicy (بدون وصول)</li><li>n/a</li></ul>|
|[قواعد تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (المعروفة أيضا باسم قواعد النقل) مع الإجراء: **تسليم الرسالة إلى العزل المستضاف** (_العزل_).|لا|n/a|

<sup>\*</sup> كما [هو موضح سابقا في هذه المقالة](#full-access-permissions-and-quarantine-notifications)، قد تستخدم مؤسستك NotificationEnabledPolicy بدلا من DefaultFullAccessPolicy. الفرق الوحيد بين نهجي العزل هذين هو تشغيل إعلامات العزل في NotificationEnabledPolicy وإيقاف تشغيلها في DefaultFullAccessPolicy.

يتم وصف نهج العزل الافتراضية ومجموعات الأذونات التي تم تعيينها مسبقا والأذونات في [بداية هذه المقالة](#quarantine-policies) [وأحدث في هذه المقالة](#preset-permissions-groups).

> [!NOTE]
> إذا كنت راضيا عن أذونات المستخدم النهائي الافتراضية وإعلامات العزل التي يتم توفيرها (أو لم يتم توفيرها) من قبل نهج العزل الافتراضية، فلن تحتاج إلى القيام بأي شيء. إذا كنت تريد إضافة قدرات المستخدم النهائي (الأزرار المتوفرة) أو إزالتها للرسائل المعزولة للمستخدم، أو تمكين إعلامات العزل وإضافة نفس الإمكانات أو إزالتها في إعلامات العزل، يمكنك تعيين نهج عزل مختلف لإجراء العزل.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>تعيين نهج العزل في النهج المعتمدة في مدخل Microsoft 365 Defender

> [!NOTE]
> لا يمكن للمستخدمين إصدار رسائلهم الخاصة التي تم عزلها على أنها برامج ضارة (نهج مكافحة البرامج الضارة) أو التصيد الاحتيالي عالي الثقة (نهج مكافحة البريد العشوائي)، بغض النظر عن كيفية تكوين نهج العزل. في أفضل الأحوال، يمكن للمسؤولين تكوين نهج العزل حتى يتمكن المستخدمون من طلب إصدار البرامج الضارة المعزولة أو رسائل التصيد الاحتيالي عالية الثقة.

### <a name="anti-spam-policies"></a>نهج مكافحة البريد العشوائي

1. في [مدخل Microsoft 365 Defender](https://security.microsoft.com)، انتقل إلى **نهج التعاون** \> في & البريد الإلكتروني **& قواعد** \> **نهج** \> التهديدات **لمكافحة البريد العشوائي** في قسم **النهج**.

   أو للانتقال مباشرة إلى صفحة **نهج Ant-spam** ، استخدم <https://security.microsoft.com/antispam>.

2. في صفحة **نهج مكافحة البريد العشوائي** ، نفذ إحدى الخطوات التالية:
   - ابحث عن نهج مكافحة البريد العشوائي **الوارد** الموجود وحدده.
   - إنشاء نهج جديد لمكافحة البريد العشوائي **الوارد** .

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير الموجود**: حدد النهج بالنقر فوق اسم النهج. في القائمة المنبثقة لتفاصيل النهج، انتقل إلى قسم **الإجراءات** ثم انقر فوق **"تحرير الإجراءات**".
   - **إنشاء جديد**: في معالج النهج الجديد، الوصول إلى صفحة **الإجراءات** .

4. في صفحة **«Actions»** ، سيكون لكل حكم يحتوي على إجراء **رسالة العزل** أيضا مربع **«Select quarantine policy** » لتحديد نهج عزل مقابل.

   **ملاحظة**: عند إنشاء نهج جديد، تشير قيمة **نهج تحديد العزل** الفارغة إلى استخدام نهج العزل الافتراضي لهذا الحكم. عند تحرير النهج لاحقا، يتم استبدال القيم الفارغة بأسماء نهج العزل الافتراضية الفعلية كما هو موضح في الجدول السابق.

   :::image type="content" source="../../media/quarantine-tags-in-anti-spam-policies.png" alt-text="تحديدات نهج العزل في نهج مكافحة البريد العشوائي" lightbox="../../media/quarantine-tags-in-anti-spam-policies.png":::

يتم وصف الإرشادات الكاملة لإنشاء نهج مكافحة البريد العشوائي وتعديلها في [تكوين نهج مكافحة البريد العشوائي في EOP](configure-your-spam-filter-policies.md).

#### <a name="anti-spam-policies-in-powershell"></a>نهج مكافحة البريد العشوائي في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين نهج العزل في نهج مكافحة البريد العشوائي، فتواصل مع Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدم بناء الجملة التالي:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**الملاحظات**:

- القيمة الافتراضية لمعلمات _PhishSpamAction_ و _HighConfidencePhishAction_ هي Quarantine، لذلك لا تحتاج إلى استخدام هذه المعلمات عند إنشاء نهج تصفية بريد عشوائي جديدة في PowerShell. بالنسبة إلى معلمات _SpamAction_ و _HighConfidenceSpamAction_ و _BulkSpamAction_ في نهج مكافحة البريد العشوائي الجديدة أو الموجودة، يكون نهج العزل فعالا فقط إذا كانت القيمة العزل.

  للاطلاع على قيم المعلمات المهمة في نهج مكافحة البريد العشوائي الموجودة، قم بتشغيل الأمر التالي:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  للحصول على معلومات حول قيم الإجراء الافتراضية وقيم الإجراء الموصى بها للمقاييس والمقاييس الصارمة، راجع [إعدادات نهج مكافحة البريد العشوائي EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- عند إنشاء نهج جديدة لمكافحة البريد العشوائي، يعني قرار تصفية البريد العشوائي دون معلمة سياسة العزل المقابلة [استخدام نهج العزل الافتراضي](#step-2-assign-a-quarantine-policy-to-supported-features) لهذا الحكم.

  تحتاج إلى استبدال نهج العزل الافتراضي بنهج عزل مخصص فقط إذا كنت تريد تغيير قدرات المستخدم النهائي الافتراضية على الرسائل المعزولة لحكم تصفية البريد العشوائي المحدد هذا.

- يتطلب نهج مكافحة البريد العشوائي الجديد في PowerShell نهج تصفية البريد العشوائي (الإعدادات) باستخدام **New-HostedContentFilterPolicy** cmdlet وقاعدة تصفية البريد العشوائي الحصري (عوامل تصفية المستلمين) باستخدام **New-HostedContentFilterRule** cmdlet. للحصول على الإرشادات، راجع [استخدام PowerShell لإنشاء نهج مكافحة البريد العشوائي](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

ينشئ هذا المثال نهج عامل تصفية بريد عشوائي جديد يسمى "قسم الأبحاث" بالإعدادات التالية:

- يتم تعيين الإجراء الخاص بجميع أحكام تصفية البريد العشوائي إلى العزل.
- يحل نهج العزل المخصص المسمى NoAccess الذي يعين أذونات **عدم الوصول** محل أي نهج عزل افتراضية لا تعين أذونات **عدم الوصول** بشكل افتراضي.

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

يعدل هذا المثال نهج عامل تصفية البريد العشوائي الحالي المسمى الموارد البشرية. يتم تعيين الإجراء الخاص بحكم عزل البريد العشوائي إلى العزل، ويتم تعيين نهج العزل المخصص المسمى NoAccess.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>نُهج مكافحة التصيد الاحتيالي

يتوفر التحليل الذكي للانتحال في EOP Defender لـ Office 365. لا تتوفر حماية انتحال المستخدم وحماية انتحال المجال وتحليل معلومات علبة البريد إلا في Defender لـ Office 365. لمزيد من المعلومات، راجع [نهج مكافحة التصيد الاحتيالي في Microsoft 365](set-up-anti-phishing-policies.md).

1. في [مدخل Microsoft 365 Defender](https://security.microsoft.com)، انتقل إلى **"نهج التعاون** \> & البريد الإلكتروني **" & قواعد** \> "**نهج** \> التهديد **" لمكافحة التصيد الاحتيالي** في قسم **"النهج**".

   أو للانتقال مباشرة إلى صفحة **نهج Ant-spam** ، استخدم <https://security.microsoft.com/antiphishing>.

2. في صفحة **مكافحة التصيد الاحتيالي** ، نفذ إحدى الخطوات التالية:
   - البحث عن نهج حالي لمكافحة التصيد الاحتيالي وتحديده.
   - إنشاء نهج جديد لمكافحة التصيد الاحتيالي.

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير الموجود**: حدد النهج بالنقر فوق اسم النهج. في القائمة المنبثقة لتفاصيل النهج، انتقل إلى قسم **إعدادات الحماية** ثم انقر فوق **"تحرير إعدادات الحماية**".
   - **إنشاء جديد**: في معالج النهج الجديد، الوصول إلى صفحة **الإجراءات** .

4. في صفحة **إعدادات الحماية** ، تحقق من تشغيل الإعدادات التالية وتكوينها كما هو مطلوب:
   - **المستخدمون الممكنون للحماية**: حدد المستخدمين.
   - **المجالات الممكن حمايتها**: حدد **تضمين المجالات التي أملكها** و/أو **قم بتضمين المجالات المخصصة** وحدد المجالات.
   - **تمكين تحليل معلومات علبة البريد**
   - **تمكين التحليل الذكي لحماية الانتحال**
   - **تمكين التحليل الذكي للانتحال**

5. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير موجود**: في القائمة المنبثقة لتفاصيل النهج، انتقل إلى قسم **الإجراءات** ثم انقر فوق **"تحرير الإجراءات**".
   - **إنشاء جديد**: في معالج النهج الجديد، الوصول إلى صفحة **الإجراءات** .

6. في صفحة **الإجراءات** ، سيكون لكل حكم يحتوي على **العزل إجراء الرسالة** أيضا مربع **تطبيق نهج العزل** لك لتحديد نهج عزل مقابل.

   **ملاحظة**: عند إنشاء نهج جديد، تشير قيمة **نهج تطبيق العزل** الفارغة إلى استخدام نهج العزل الافتراضي لهذا الإجراء. عند تحرير النهج لاحقا، يتم استبدال القيم الفارغة بأسماء نهج العزل الافتراضية الفعلية كما هو موضح في الجدول السابق.

   :::image type="content" source="../../media/quarantine-tags-in-anti-phishing-policies.png" alt-text="تحديدات نهج العزل في نهج مكافحة التصيد الاحتيالي" lightbox="../../media/quarantine-tags-in-anti-phishing-policies.png":::

تتوفر إرشادات كاملة لإنشاء نهج مكافحة التصيد الاحتيالي وتعديلها في المواضيع التالية:

- [تكوين نهج مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md)
- [تكوين نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>نهج مكافحة التصيد الاحتيالي في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين نهج العزل في نهج مكافحة التصيد الاحتيالي، فتواصل مع Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدم بناء الجملة التالي:

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**الملاحظات**:

- المعلمات _Enable\*_ مطلوبة لتشغيل ميزات الحماية المحددة. القيمة الافتراضية لمعلمات _EnableMailboxIntelligence_ و _EnableSpoofIntelligence_ هي $true، لذلك لا تحتاج إلى استخدام هذه المعلمات عند إنشاء نهج جديدة لمكافحة التصيد الاحتيالي في PowerShell. يجب أن تحتوي جميع معلمات _التمكين\*_ الأخرى على القيمة $true حتى تتمكن من تعيين القيمة Quarantine في معلمات الإجراء المقابلة _\*_ لتعيين نهج العزل بعد ذلك. لا تحتوي أي من معلمات _*\Action_ على القيمة الافتراضية Quarantine.

  للاطلاع على قيم المعلمات المهمة في نهج مكافحة التصيد الاحتيالي الموجودة، قم بتشغيل الأمر التالي:

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  للحصول على معلومات حول قيم الإجراء الافتراضية وقيم الإجراءات الموصى بها للمقاييس والمقاييس الصارمة، راجع [إعدادات نهج مكافحة التصيد الاحتيالي وإعدادات انتحال EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) [في نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- عند إنشاء نهج مكافحة التصيد الاحتيالي، فإن إجراء مكافحة التصيد الاحتيالي دون معلمة نهج عزل مقابلة يعني استخدام [نهج العزل الافتراضي](#step-2-assign-a-quarantine-policy-to-supported-features) لهذا الحكم.

  تحتاج إلى استبدال نهج العزل الافتراضي بنهج عزل مخصص فقط إذا كنت تريد تغيير قدرات المستخدم النهائي الافتراضية على الرسائل المعزولة لهذا الحكم المحدد.

- يتطلب نهج مكافحة التصيد الاحتيالي الجديد في PowerShell نهج (إعدادات) مكافحة التصيد الاحتيالي باستخدام **New-AntiPhishPolicy** cmdlet وقاعدة حصرية لمكافحة التصيد الاحتيالي (عوامل تصفية المستلمين) باستخدام **New-AntiPhishRule** cmdlet. للحصول على الإرشادات، راجع المواضيع التالية:
  - [استخدام PowerShell لتكوين نهج مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [استخدام Exchange Online PowerShell لتكوين نهج مكافحة التصيد الاحتيالي](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

ينشئ هذا المثال نهجا جديدا لمكافحة التصيد الاحتيالي يسمى "قسم الأبحاث" بالإعدادات التالية:

- يتم تعيين الإجراء الخاص بجميع أحكام تصفية البريد العشوائي إلى العزل.
- يحل نهج العزل المخصص المسمى NoAccess الذي يعين أذونات **عدم الوصول** محل أي نهج عزل افتراضية لا تعين أذونات **عدم الوصول** بشكل افتراضي.

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

يعدل هذا المثال نهج مكافحة التصيد الاحتيالي الحالي المسمى الموارد البشرية. يتم تعيين الإجراء الخاص بالرسائل التي تم الكشف عنها بواسطة انتحال المستخدم وانتحال المجال إلى العزل، ويتم تعيين نهج العزل المخصص المسمى NoAccess.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-AntiPhishPolicy](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>نهج مكافحة البرامج الضارة

1. في [مدخل Microsoft 365 Defender](https://security.microsoft.com)، انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & قواعد** \> "**نهج** \> التهديد **" لمكافحة البرامج الضارة** في قسم **"النهج**".

   أو للانتقال مباشرة إلى صفحة **مكافحة البرامج الضارة** ، استخدم <https://security.microsoft.com/antimalwarev2>.

2. في صفحة **مكافحة البرامج الضارة** ، نفذ إحدى الخطوات التالية:
   - ابحث عن نهج حالي لمكافحة البرامج الضارة وحدده.
   - إنشاء نهج جديد لمكافحة البرامج الضارة.

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير الموجود**: حدد النهج بالنقر فوق اسم النهج. في القائمة المنبثقة لتفاصيل النهج، انتقل إلى قسم **إعدادات الحماية** ثم انقر فوق **"تحرير إعدادات الحماية**".
   - **إنشاء جديد**: في معالج النهج الجديد، الوصول إلى صفحة **الإجراءات** .

4. في صفحة **إعدادات الحماية** ، حدد نهج عزل في مربع **نهج العزل** .

   **ملاحظة**: عند إنشاء نهج جديد، تشير قيمة **نهج العزل** الفارغة إلى استخدام نهج العزل الافتراضي لذلك. عند تحرير النهج لاحقا، يتم استبدال القيمة الفارغة باسم نهج العزل الافتراضي الفعلي كما هو موضح في الجدول السابق.

#### <a name="anti-malware-policies-in-powershell"></a>نهج مكافحة البرامج الضارة في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين نهج العزل في نهج مكافحة البرامج الضارة، فتواصل مع Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدم بناء الجملة التالي:

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**الملاحظات**:

- عند إنشاء نهج جديدة لمكافحة البرامج الضارة دون استخدام معلمة QuarantineTag عند إنشاء نهج جديد لمكافحة البرامج الضارة، يتم استخدام نهج العزل الافتراضي للكشف عن البرامج الضارة (AdminOnlyAccessPolicy).

  تحتاج إلى استبدال نهج العزل الافتراضي بنهج عزل مخصص فقط إذا كنت تريد تغيير قدرات المستخدم النهائي الافتراضية على الرسائل التي يتم عزلها كالبرمجيات الضارة.

  للاطلاع على قيم المعلمات المهمة في نهج مكافحة التصيد الاحتيالي الموجودة، قم بتشغيل الأمر التالي:

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- يتطلب نهج مكافحة البرامج الضارة الجديد في PowerShell نهج تصفية البرامج الضارة (الإعدادات) باستخدام **New-MalwareFilterPolicy** cmdlet وقاعدة تصفية البرامج الضارة الحصرية (عوامل تصفية المستلمين) باستخدام **New-MalwareFilterRule** cmdlet. للحصول على الإرشادات، راجع [استخدام Exchange Online PowerShell أو EOP PowerShell المستقل لتكوين نهج مكافحة البرامج الضارة](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies).

ينشئ هذا المثال نهج عامل تصفية البرامج الضارة المسمى "قسم الأبحاث" الذي يستخدم نهج العزل المخصص المسمى NoAccess الذي يعين أذونات **عدم الوصول** إلى الرسائل المعزولة.

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

يعدل هذا المثال نهج عامل تصفية البرامج الضارة الحالي المسمى Human Resources عن طريق تعيين نهج العزل المخصص المسمى NoAccess الذي يعين أذونات **عدم الوصول** إلى الرسائل المعزولة.

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>نهج المرفقات خزينة في Defender لـ Office 365

1. في [مدخل Microsoft 365 Defender](https://security.microsoft.com)، انتقل إلى نهج **التعاون** \> & البريد الإلكتروني **& قواعد** \> **نهج التهديد** \> **خزينة المرفقات** في قسم **"النهج**".

   أو للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **"مرفقات خزينة**"، نفذ إحدى الخطوات التالية:
   - ابحث عن نهج مرفقات خزينة موجود وحدده.
   - إنشاء نهج مرفقات خزينة جديد.

3. قم بتنفيذ أحد الخطوتين التاليين:
   - **تحرير الموجود**: حدد النهج بالنقر فوق اسم النهج. في القائمة المنبثقة لتفاصيل النهج، انتقل إلى قسم **الإعدادات** ثم انقر فوق **"تحرير الإعدادات**".
   - **إنشاء جديد**: في معالج النهج الجديد، الوصول إلى صفحة **الإعدادات**.

4. في صفحة **الإعدادات**، قم بالخطوات التالية:
   1. **خزينة استجابة البرامج الضارة غير المعروفة في المرفقات**: حدد **Block** أو **Replace** أو **Dynamic Delivery**.
   2. حدد نهج عزل في مربع **نهج العزل** .

   **ملاحظة**: عند إنشاء نهج جديد، تشير قيمة **نهج العزل** الفارغة إلى استخدام نهج العزل الافتراضي. عند تحرير النهج لاحقا، يتم استبدال القيمة الفارغة باسم نهج العزل الافتراضي الفعلي كما هو موضح في الجدول السابق.

يتم وصف الإرشادات الكاملة لإنشاء نهج المرفقات خزينة وتعديلها في [إعداد نهج المرفقات خزينة في Microsoft Defender لـ Office 365](set-up-safe-attachments-policies.md).

#### <a name="safe-attachments-policies-in-powershell"></a>نهج المرفقات خزينة في PowerShell

إذا كنت تفضل استخدام PowerShell لتعيين نهج العزل في نهج المرفقات خزينة، فتواصل مع Exchange Online PowerShell أو Exchange Online Protection PowerShell واستخدم بناء الجملة التالي:

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**الملاحظات**:

- يمكن أن ينتج عن قيم معلمة _الإجراء_ Block أو Replace أو DynamicDelivery رسائل معزولة (لا تقوم القيمة Allow بعزل الرسائل). قيمة معلمة _الإجراء_ ذات المعنى فقط عندما تكون `$true`قيمة المعلمة _Enable_ .

- عند إنشاء نهج مرفقات خزينة جديدة دون استخدام معلمة QuarantineTag، يتم استخدام نهج العزل الافتراضي لاكتشافات المرفقات خزينة في البريد الإلكتروني (AdminOnlyAccessPolicy).

  تحتاج إلى استبدال نهج العزل الافتراضي بنهج عزل مخصص فقط إذا كنت تريد تغيير قدرات المستخدم النهائي الافتراضية على رسائل البريد الإلكتروني التي تم عزلها بواسطة نهج المرفقات خزينة.

  لمشاهدة قيم المعلمات المهمة، قم بتشغيل الأمر التالي:

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- يتطلب نهج مرفقات خزينة جديد في PowerShell نهج مرفق آمن (إعدادات) باستخدام **New-SafeAttachmentPolicy** cmdlet وقاعدة مرفقات آمنة حصرية (عوامل تصفية المستلمين) باستخدام **New-SafeAttachmentRule** cmdlet. للحصول على الإرشادات، راجع [استخدام Exchange Online PowerShell أو EOP PowerShell المستقل لتكوين نهج المرفقات خزينة](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies).

ينشئ هذا المثال نهج مرفق آمن يسمى "قسم الأبحاث" يحظر الرسائل المكتشفة ويستخدم نهج العزل المخصص المسمى NoAccess الذي يعين **"بلا أذونات وصول"** إلى الرسائل المعزولة.

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

يعدل هذا المثال نهج المرفقات الآمنة الحالي المسمى Human Resources عن طريق تعيين نهج العزل المخصص المسمى NoAccess الذي يعين أذونات **عدم الوصول** .

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>تكوين إعدادات إعلام العزل العمومي في مدخل Microsoft 365 Defender

تسمح لك الإعدادات العمومية لنهج العزل بتخصيص إعلامات العزل التي يتم إرسالها إلى مستلمي الرسائل المعزولة إذا تم تشغيل إعلامات العزل في نهج العزل. لمزيد من المعلومات حول هذه الإعلامات، راجع [إعلامات العزل](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. في مدخل Microsoft 365 Defender، انتقل إلى **نهج التعاون** \> & البريد الإلكتروني **& نهج** \> **عزل** **نهج** \> التهديد في قسم **"القواعد**". أو للانتقال مباشرة إلى صفحة **نهج العزل** ، استخدم <https://security.microsoft.com/quarantinePolicies>.

2. في صفحة **نهج العزل** ، حدد **الإعدادات العمومية**.

3. في القائمة المنبثقة **لإعدادات إعلام العزل** التي يتم فتحها، قم بتكوين الإعدادات التالية:

   - تخصيص إعلامات العزل استنادا إلى لغة المستلم:

     - **اسم العرض** للمرسل المستخدم في إعلامات العزل كما هو موضح في لقطة الشاشة التالية.

       :::image type="content" source="../../media/quarantine-tags-esn-customization-display-name.png" alt-text="اسم عرض مرسل مخصص في إعلام العزل." lightbox="../../media/quarantine-tags-esn-customization-display-name.png":::

     - نص **إخلاء المسؤولية** الذي تمت إضافته إلى أسفل إعلامات العزل. النص المترجم، **إخلاء المسؤولية من مؤسستك:** يتم تضمينه دائما أولا، متبوعا بالنص الذي تحدده كما هو موضح في لقطة الشاشة التالية:

       :::image type="content" source="../../media/quarantine-tags-esn-customization-disclaimer.png" alt-text="إخلاء مسؤولية مخصص في أسفل إعلام العزل." lightbox="../../media/quarantine-tags-esn-customization-disclaimer.png":::

     - معرف اللغة **لاسم العرض** وقيم **إخلاء المسؤولية** . يتم ترجمة إعلامات العزل بالفعل استنادا إلى إعدادات اللغة الخاصة بالمستلم. يتم استخدام **قيم الاسم المعروض** **وإخلاء المسؤولية** في إعلامات العزل التي تنطبق على لغة المستلم.

       حدد اللغة في المربع **"اختيار اللغة**" _قبل_ إدخال القيم في مربعي **"الاسم المعروض****" و"إخلاء المسؤولية**". عند تغيير القيمة في مربع **"اختيار اللغة** "، يتم إفراغ القيم الموجودة في **مربعي "اسم العرض** " و **"إخلاء المسؤولية** ".

     اتبع هذه الخطوات لتخصيص إعلامات العزل استنادا إلى لغة المستلم:

     1. حدد اللغة من المربع **"اختيار اللغة** ". القيمة الافتراضية هي **الافتراضية**، ما يعني اللغة الإنجليزية.
     2. أدخل **قيما لاسم العرض** **وإخلاء المسؤولية**. يجب أن تكون القيم فريدة لكل لغة. إذا حاولت إعادة استخدام **اسم عرض** أو قيمة **إخلاء مسؤولية** للغات متعددة، فستتلقى رسالة خطأ عند النقر فوق **"حفظ**".
     3. انقر فوق الزر **"إضافة** ".
     4. كرر الخطوات السابقة لإنشاء ثلاثة إعلامات عزل مخصصة كحد أقصى استنادا إلى لغة المستلم. يعرض المربع غير المسمى اللغات التي قمت بتكوينها:

        :::image type="content" source="../../media/quarantine-tags-esn-customization-selected-languages.png" alt-text="اللغات المحددة في إعدادات إعلام العزل العمومي لنهج العزل." lightbox="../../media/quarantine-tags-esn-customization-selected-languages.png":::

   - **استخدم شعار شركتي**: حدد هذا الخيار لاستبدال شعار Microsoft الافتراضي المستخدم في أعلى إعلامات العزل. قبل تنفيذ هذه الخطوة، تحتاج إلى اتباع الإرشادات الواردة في [تخصيص نسق Microsoft 365 لمؤسستك](../../admin/setup/customize-your-organization-theme.md) لتحميل الشعار المخصص.

     تظهر لقطة الشاشة التالية شعارا مخصصا في إعلام العزل:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-logo.png" alt-text="شعار مخصص في إعلام العزل" lightbox="../../media/quarantine-tags-esn-customization-logo.png":::

   - **إرسال إعلام بالبريد العشوائي للمستخدم النهائي كل (أيام):** حدد معدل تكرار إعلامات العزل. القيمة الافتراضية هي 3 أيام، ولكن يمكنك تحديد من يوم إلى 15 يوما.

4. عند الانتهاء، انقر فوق **حفظ**.

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>عرض نهج العزل في مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، انتقل إلى **نهج التعاون** \> & البريد الإلكتروني **& نهج** \> **عزل** **نهج** \> التهديد في قسم **"القواعد**". أو للانتقال مباشرة إلى صفحة **نهج العزل** ، استخدم <https://security.microsoft.com/quarantinePolicies>.

2. تعرض صفحة **نهج العزل** قائمة النهج حسب **الاسم** وتاريخ **التحديث الأخير** .

3. لعرض إعدادات نهج العزل المضمنة أو المخصصة، حدد نهج العزل من القائمة بالنقر فوق الاسم.

4. لعرض الإعدادات العمومية، انقر فوق **الإعدادات العمومية**

### <a name="view-quarantine-policies-in-powershell"></a>عرض نهج العزل في PowerShell

إذا كنت تفضل استخدام PowerShell لعرض نهج العزل، فقم بأي من الخطوات التالية:

- لعرض قائمة ملخصة لكافة النهج المضمنة أو المخصصة، قم بتشغيل الأمر التالي:

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- لعرض إعدادات نهج العزل المضمنة أو المخصصة، استبدلها \<QuarantinePolicyName\> باسم نهج العزل، ثم قم بتشغيل الأمر التالي:

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- لعرض الإعدادات العمومية لإعلامات العزل، قم بتشغيل الأمر التالي:

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>تعديل نهج العزل في مدخل Microsoft 365 Defender

لا يمكنك تعديل نهج العزل المضمنة المسماة AdminOnlyAccessPolicy أو DefaultFullAccessPolicy. يمكنك تعديل النهج المضمن المسمى NotificationEnabledPolicy ([إذا كان لديك](#full-access-permissions-and-quarantine-notifications)) ونهج العزل المخصصة.

1. في مدخل Microsoft 365 Defender، انتقل إلى **نهج التعاون** \> & البريد الإلكتروني **& نهج** \> **عزل** **نهج** \> التهديد في قسم **"القواعد**". أو للانتقال مباشرة إلى صفحة **نهج العزل** ، استخدم <https://security.microsoft.com/quarantinePolicies>.

2. في صفحة **نهج العزل** ، حدد النهج بالنقر فوق الاسم.

3. بعد تحديد النهج، انقر فوق أيقونة ![تحرير النهج.](../../media/m365-cc-sc-edit-icon.png) **أيقونة تحرير النهج** التي تظهر.

4. معالج **تحرير النهج** الذي يتم فتحه مطابق تقريبا لمعالج **النهج الجديد** كما هو موضح في "[إنشاء نهج العزل" في قسم مدخل Microsoft 365 Defender](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) سابقا في هذه المقالة.

   الفرق الرئيسي هو: لا يمكنك إعادة تسمية نهج موجود.

5. عند الانتهاء من تعديل النهج، انتقل إلى صفحة **الملخص** وانقر فوق **"إرسال**".

### <a name="modify-quarantine-policies-in-powershell"></a>تعديل نهج العزل في PowerShell

إذا كنت تفضل استخدام PowerShell لتعديل نهج عزل مخصص، استبدله \<QuarantinePolicyName\> باسم نهج العزل، واستخدم بناء الجملة التالي:

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

الإعدادات المتوفرة هي نفسها الموضحة لإنشاء نهج العزل سابقا في هذه المقالة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>إزالة نهج العزل في مدخل Microsoft 365 Defender

**الملاحظات**:

- لا يمكنك إزالة نهج العزل المضمنة المسماة AdminOnlyAccessPolicy أو DefaultFullAccessPolicy. يمكنك إزالة النهج المضمن المسمى NotificationEnabledPolicy ([إذا كان لديك](#full-access-permissions-and-quarantine-notifications)) ونهج العزل المخصصة.
- قبل إزالة نهج العزل، تحقق من عدم استخدامه. على سبيل المثال، قم بتشغيل الأمر التالي في PowerShell:

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  إذا كان نهج العزل قيد الاستخدام، [فقم باستبدال نهج العزل المعين](#step-2-assign-a-quarantine-policy-to-supported-features) قبل إزالته.

1. في مدخل Microsoft 365 Defender، انتقل إلى **نهج التعاون** \> & البريد الإلكتروني **& نهج** \> **عزل** **نهج** \> التهديد في قسم **"القواعد**". أو للانتقال مباشرة إلى صفحة **نهج العزل** ، استخدم <https://security.microsoft.com/quarantinePolicies>.

2. في صفحة **نهج العزل** ، حدد نهج العزل المخصص الذي تريد إزالته بالنقر فوق الاسم.

3. بعد تحديد النهج، انقر فوق أيقونة ![حذف النهج.](../../media/m365-cc-sc-delete-icon.png) **أيقونة "حذف النهج** " التي تظهر.

4. انقر فوق **"إزالة النهج** " في مربع حوار التأكيد الذي يظهر.

### <a name="remove-quarantine-policies-in-powershell"></a>إزالة نهج العزل في PowerShell

إذا كنت تفضل استخدام PowerShell لإزالة نهج عزل مخصص، استبدله \<QuarantinePolicyName\> باسم نهج العزل، وقم بتشغيل الأمر التالي:

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>تنبيهات النظام لطلبات إصدار العزل

بشكل افتراضي، يقوم نهج التنبيه الافتراضي **المسمى User الذي طلب إصدار رسالة معزولة** بإنشاء تنبيه إعلامي تلقائيا وإرسال رسائل إعلام إلى أعضاء مجموعات الأدوار التالية كلما طلب المستخدم إصدار رسالة معزولة:

- مسؤول العزل
- مسؤول الأمان
- إدارة المؤسسة (المسؤول العام)

يمكن للمسؤولين تخصيص مستلمي إعلامات البريد الإلكتروني أو إنشاء نهج تنبيه مخصص لمزيد من الخيارات.

لمزيد من المعلومات حول نهج التنبيه، راجع [نهج التنبيه في Microsoft 365](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>تفاصيل إذن نهج العزل

تصف الأقسام التالية تأثيرات مجموعات الأذونات المعدة مسبقا والأذونات الفردية في تفاصيل الرسائل المعزولة وفي إعلامات العزل.

### <a name="preset-permissions-groups"></a>مجموعات الأذونات التي تم تعيينها مسبقا

يتم سرد الأذونات الفردية المضمنة في مجموعات الأذونات المعينة مسبقا في الجدول في بداية هذه المقالة.

#### <a name="no-access"></a>لا يوجد وصول

إذا قام نهج العزل بتعيين أذونات **عدم الوصول** (وصول المسؤول فقط)، فلن يتمكن المستخدمون من رؤية الرسائل التي تم عزلها:

- **تفاصيل الرسالة المعزولة**: لن تظهر أي رسائل في طريقة عرض المستخدم النهائي.
- **إعلامات العزل**: لن يتم إرسال أي إعلامات لهذه الرسائل.

#### <a name="limited-access"></a>وصول محدود

إذا كان نهج العزل يعين أذونات **الوصول المحدود** ، يحصل المستخدمون على الإمكانات التالية:

- **تفاصيل الرسالة المعزولة**: تتوفر الأزرار التالية:
  - **إصدار الطلب**
  - **عرض رؤوس الرسائل**
  - **معاينة الرسالة**
  - **إزالة من العزل**
  - **حظر المرسل**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-limited-access.png" alt-text="الأزرار المتوفرة في تفاصيل الرسالة المعزولة إذا كان نهج العزل يمنح المستخدم أذونات وصول محدودة" lightbox="../../media/quarantine-tags-quarantined-message-details-limited-access.png":::

- **إعلامات العزل**: تتوفر الأزرار التالية:
  - **حظر المرسل**
  - **إصدار الطلب**
  - **مراجعة**

  :::image type="content" source="../../media/quarantine-tags-esn-limited-access.png" alt-text="الأزرار المتوفرة في إعلام العزل إذا كان نهج العزل يمنح المستخدم أذونات وصول محدودة" lightbox="../../media/quarantine-tags-esn-limited-access.png":::

#### <a name="full-access"></a>الوصول الكامل

إذا كان نهج العزل يعين أذونات **الوصول الكامل** (كافة الأذونات المتوفرة)، يحصل المستخدمون على الإمكانات التالية:

- **تفاصيل الرسالة المعزولة**: تتوفر الأزرار التالية:
  - **رسالة الإصدار**
  - **عرض رؤوس الرسائل**
  - **معاينة الرسالة**
  - **إزالة من العزل**
  - **حظر المرسل**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-full-access.png" alt-text="الأزرار المتوفرة في تفاصيل الرسالة المعزولة إذا كان نهج العزل يمنح المستخدم أذونات الوصول الكامل" lightbox="../../media/quarantine-tags-quarantined-message-details-full-access.png":::

- **إعلامات العزل**: تتوفر الأزرار التالية:
  - **حظر المرسل**
  - **Release**
  - **مراجعة**

  :::image type="content" source="../../media/quarantine-tags-esn-full-access.png" alt-text="الأزرار المتوفرة في إعلام العزل إذا كان نهج العزل يمنح المستخدم أذونات الوصول الكامل" lightbox="../../media/quarantine-tags-esn-full-access.png":::

> [!NOTE]
> كما هو موضح سابقا، يتم تعطيل إعلامات العزل في نهج العزل الافتراضي المسمى DefaultFullAccessPolicy، على الرغم من تعيين مجموعة أذونات **الوصول الكامل** لنهج العزل هذا. تتوفر إعلامات العزل فقط في نهج العزل المخصصة التي تقوم بإنشائها أو في نهج الوصول إلى العزل الافتراضي المسمى NotificationEnabledPolicy ([إذا كان هذا النهج متوفرا في مؤسستك](#full-access-permissions-and-quarantine-notifications)).

### <a name="individual-permissions"></a>أذونات فردية

#### <a name="block-sender-permission"></a>حظر إذن المرسل

يتحكم إذن **مرسل الحظر** (_PermissionToBlockSender_) في الوصول إلى الزر الذي يسمح للمستخدمين بإضافة مرسل الرسائل المعزولة إلى قائمة المرسلين المحظورين الخاصة بهم بشكل ملائم.

- **تفاصيل الرسالة المعزولة**:
  - تم تمكين إذن **"حظر المرسل**": يتوفر الزر **"حظر المرسل**".
  - تم تعطيل إذن **"حظر المرسل**": الزر "**حظر المرسل**" غير متوفر.

- **إعلامات العزل**:
  - تم تمكين إذن **"حظر المرسل**": يتوفر الزر **"حظر المرسل**".
  - تم تعطيل إذن **"حظر المرسل**": الزر "**حظر المرسل**" غير متوفر.

لمزيد من المعلومات حول قائمة "المرسلون المحظورون"، راجع [رسائل الحظر الواردة من شخص ما](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) [واستخدام Exchange Online PowerShell لتكوين مجموعة القائمة الآمنة على علبة بريد](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="delete-permission"></a>حذف الإذن

يتحكم إذن **الحذف** (_PermissionToDelete_) في قدرة المستخدمين على حذف رسائلهم (الرسائل التي يكون فيها المستخدم مستلما) من العزل.

- **تفاصيل الرسالة المعزولة**:
  - تم تمكين إذن **الحذف**: يتوفر الزر **"إزالة من العزل**".
  - تم تعطيل إذن **الحذف**: الزر **"إزالة من العزل**" غير متوفر.

- **إعلامات العزل**: لا يوجد أي تأثير.

#### <a name="preview-permission"></a>إذن المعاينة

يتحكم إذن **المعاينة** (_PermissionToPreview_) في قدرة المستخدمين على معاينة رسائلهم في العزل.

- **تفاصيل الرسالة المعزولة**:
  - تم تمكين إذن **المعاينة**: يتوفر زر **رسالة المعاينة**.
  - إذن **المعاينة** معطل: زر **رسالة المعاينة** غير متوفر.

- **إعلامات العزل**: لا يوجد أي تأثير.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>السماح للمستلمين بتحرير رسالة من إذن العزل

يتحكم **السماح للمستلمين بتحرير رسالة من إذن العزل** (_PermissionToRelease_) في قدرة المستخدمين على تحرير رسائلهم المعزولة مباشرة ودون موافقة المسؤول.

- **تفاصيل الرسالة المعزولة**:
  - تم تمكين الإذن: يتوفر زر **رسالة الإصدار** .
  - تم تعطيل الإذن: زر **رسالة الإصدار** غير متوفر.

- **إعلامات العزل**:
  - تم تمكين الإذن: يتوفر الزر **"إصدار** ".
  - تم تعطيل الإذن: الزر **"إصدار"** غير متوفر.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>السماح للمستلمين بطلب إصدار رسالة من إذن العزل

يتحكم **السماح للمستلمين بطلب إصدار رسالة من إذن العزل** (_PermissionToRequestRelease_) في قدرة المستخدمين على _طلب_ إصدار رسائل العزل الخاصة بهم. يتم إصدار الرسالة فقط بعد موافقة المسؤول على الطلب.

- **تفاصيل الرسالة المعزولة**:
  - تم تمكين الإذن: يتوفر الزر **"طلب الإصدار** ".
  - تم تعطيل الإذن: الزر **"طلب إصدار"** غير متوفر.

- **إعلامات العزل**:
  - تم تمكين الإذن: يتوفر الزر **"طلب الإصدار** ".
  - تم تعطيل الإذن: الزر **"طلب إصدار"** غير متوفر.
