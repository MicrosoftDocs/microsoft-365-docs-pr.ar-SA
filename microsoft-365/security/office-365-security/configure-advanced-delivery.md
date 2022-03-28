---
title: تكوين تسليم عمليات محاكاة التصيد الاحتيالي من جهة خارجية إلى المستخدمين والرسائل التي لم يتم فصلها إلى علب بريد SecOps
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: يمكن للمسؤولين التعرف على كيفية استخدام نهج التسليم المتقدم في Exchange Online Protection (EOP) لتحديد الرسائل التي لا يجب تصفيتها في سيناريوهات محددة معتمدة (عمليات محاكاة التصيد الاحتيالي من جهة خارجية والرسائل التي يتم تسليمها إلى علب بريد عمليات الأمان (SecOps).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1abb2c1710d1a7bd101801110e3c44f3b8e2ae65
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775863"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>تكوين تسليم عمليات محاكاة التصيد الاحتيالي من جهة خارجية إلى المستخدمين والرسائل التي لم يتم فصلها إلى علب بريد SecOps

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

للحفاظ على أمان مؤسستك [](secure-by-default.md)بشكل افتراضي، Exchange Online Protection (EOP) القوائم الآمنة أو تجاوز التصفية للرسائل التي يتم تعريفها كبرامج ضارة أو تصيد احتيالي عالي الثقة. ولكن، هناك سيناريوهات معينة تتطلب تسليم الرسائل التي لم يتم تحديدها. على سبيل المثال:

- **عمليات محاكاة التصيد** الاحتيالي التي تقوم بها جهة خارجية: يمكن أن تساعدك الهجمات المحاكاة على تحديد المستخدمين الضعاف قبل أن يؤثر هجوم حقيقي على مؤسستك.
- **علب بريد عمليات الأمان (SecOps**): علب البريد المخصصة التي تستخدمها فرق الأمان لتجميع الرسائل التي لم يتم ترتيبها وتحليلها (سواء كانت جيدة أو سيئة).

يمكنك استخدام _نهج التسليم المتقدم_ في Microsoft 365 لمنع تصفية الرسائل الواردة في هذه السيناريوهات  المحددة.<sup>\*</sup> يضمن نهج التسليم المتقدم أن الرسائل في هذه السيناريوهات تحقق النتائج التالية:

- لا تتخذ عوامل التصفية في EOP و Microsoft Defender Office 365 أي إجراء على هذه الرسائل.<sup>\*</sup>
- لا تتخذ عملية "إزالة البريد العشوائي والتصيد الاحتيالي[" (ZAP)](zero-hour-auto-purge.md) لمدة ساعة الصفر أي إجراء على هذه الرسائل.<sup>\*</sup>
- [لا يتم تشغيل](/microsoft-365/compliance/alert-policies#default-alert-policies) تنبيهات النظام الافتراضية لهذه السيناريوهات.
- [يتجاهل AIR والتجمع في Defender for Office 365](office-365-air.md) هذه الرسائل.
- عمليات محاكاة التصيد الاحتيالي التي تقوم بها جهة خارجية تحديدا:
  - [تنشئ عمليات إرسال](admin-submission.md) المسؤول ردا تلقائيا يشير إلى أن الرسالة تشكل جزءا من حملة محاكاة التصيد الاحتيالي ولا تشكل خطرا حقيقيا. لن يتم تشغيل التنبيهات و AIR. سوف تظهر تجربة إرسالات المسؤول هذه الرسائل كخطر محاكاة.
  - عندما يقوم مستخدم ب الإبلاغ عن رسالة محاكاة تصيد احتيالي [](enable-the-report-message-add-in.md)باستخدام "رسالة التقرير" أو الوظائف الإضافية "الإبلاغ عن التصيد الاحتيالي"، لن يقوم النظام بإنشاء تنبيه أو تحقيق أو حادث. لن يتم نقل الارتباطات أو الملفات، ولكن سوف تظهر الرسالة أيضا على علامة تبويب الرسائل  التي تم إعداد تقرير عنها من **قبل المستخدم في** صفحة "الواجبات المرسلة".
  - [خزينة الارتباطات في Defender for Office 365](safe-links.md) حظر عناوين URL المحددة أو إرساءها في هذه الرسائل في وقت النقر. ما زالت عناوين URL ملتفة، ولكن لا يتم حظرها.
  - [خزينة المرفقات في Defender for Office 365](safe-attachments.md) إلى عدم إقحام المرفقات في هذه الرسائل.

<sup>\*</sup> لا يمكنك تجاوز تصفية البرامج الضارة أو ZAP للبرامج الضارة.

لا تشكل الرسائل التي تم تعريفها بواسطة نهج التسليم المتقدم تهديدات أمنية، لذلك يتم وضع علامة على الرسائل بتجاوز النظام. سوف تظهر تجارب المسؤول هذه الرسائل على أنها إما بسبب تجاوز  نظام محاكاة التصيد الاحتيالي أو تجاوز نظام علبة بريد **SecOps**. يمكن للمسؤولين التصفية والتحليل على تجاوزات النظام هذه في التجارب التالية:

- الكشف عن "مستكشف التهديدات"/في الوقت الحقيقي [في خطة Office 365 ل Defender ل 2](threat-explorer.md): يمكن للمسؤول التصفية على مصدر تجاوز النظام وتحديد محاكاة التصيد الاحتيالي أو **علبة بريد SecOps**. 
- صفحة كيان البريد الإلكتروني في الكشف عن Threat [Explorer/](mdo-email-entity-page.md)في الوقت الحقيقي: يمكن للمسؤول عرض رسالة تم السماح بها بواسطة نهج المؤسسة بواسطة علبة **بريد SecOps** أو محاكاة التصيد الاحتيالي ضمن  تجاوز المستأجر في المقطع **تجاوز (** التجاوزات).
- تقرير [حالة](view-email-security-reports.md#threat-protection-status-report) الحماية من المخاطر: يمكن للمسؤول التصفية  حسب عرض البيانات حسب تجاوز النظام في القائمة المنسدلة وتحديد لرؤية الرسائل المسموح بها بسبب تجاوز نظام محاكاة التصيد الاحتيالي. لرؤية الرسائل التي يسمح بها تجاوز علبة بريد SecOps، يمكنك تحديد تصنيف المخطط حسب موقع  التسليم في القائمة المنسدلة تصنيف  المخطط حسب السبب.
- [الصيد المتقدم في Microsoft Defender لنقطة](../defender-endpoint/advanced-hunting-overview.md) النهاية: سيتم عرض محاكاة التصيد الاحتيالي وتجاوز نظام علب بريد SecOps كالخيارات ضمن OrgLevelPolicy في EmailEvents.
- [طرق عرض الحملة](campaigns.md): يمكن للمسؤول التصفية على **مصدر** تجاوز النظام وتحديد محاكاة التصيد الاحتيالي **أو** **علبة بريد SecOps**.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى **صفحة التسليم** المتقدم، افتح <https://security.microsoft.com/advanceddelivery>.

- للاتصال بمركز التوافق & PowerShell، راجع الاتصال [إلى مركز التوافق & PowerShell](/powershell/exchange/connect-to-scc-powershell).

- يجب تعيين أذونات لك قبل أن تتمكن من تنفيذ الإجراءات في هذه المقالة:
  - لإنشاء إعدادات مكونة أو تعديلها أو إزالتها في نهج التسليم المتقدم، يجب أن تكون عضوا في مجموعة دور مسؤول الأمان في مدخل  **Microsoft 365 Defender** وعضوا في مجموعة دور إدارة المؤسسة **في Exchange Online**.
  - للوصول للقراءة فقط إلى نهج التسليم المتقدم، يجب أن تكون عضوا في مجموعات دور القارئ العام أو قارئ  الأمان.

  لمزيد من المعلومات، راجع الأذونات في [Microsoft 365 Defender والأذونات](permissions-microsoft-365-security-center.md) [في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر للمستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender والأذونات للميزات الأخرى  في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>استخدام مدخل Microsoft 365 Defender لتكوين علب بريد SecOps في نهج التسليم المتقدم

1. في مدخل Microsoft 365 Defender،    <https://security.microsoft.com>انتقل إلى البريد الإلكتروني **&** \> \> \> سياسات التعاون & قواعد المخاطر المتقدمة التسليم المتقدم في **القسم القواعد**. الانتقال مباشرة إلى **صفحة التسليم** المتقدم، استخدم <https://security.microsoft.com/advanceddelivery>.

2. في صفحة **التسليم المتقدم** ، تحقق من تحديد علامة التبويب **علبة بريد SecOps** ، ثم قم بوا إحدى الخطوات التالية:
   - انقر فوق ![أيقونة تحرير.](../../media/m365-cc-sc-edit-icon.png) **تحرير**.
   - إذا لم تكن هناك عمليات محاكاة تصيد احتيالي مكونة، انقر فوق **إضافة**.

3. في القائمة المنفتحة لتحرير علب بريد SecOps، أدخل علبة بريد موجودة Exchange Online تريد تعيينها كع البريد **SecOps** من خلال القيام بوا إحدى الخطوات التالية:
   - انقر في المربع، واترك قائمة علب البريد تحل، ثم حدد علبة البريد.
   - انقر في المربع ابدأ بكتابة معرف لعلبة البريد (الاسم واسم العرض والاسم المستعار وعنوان البريد الإلكتروني واسم الحساب وغير ذلك)، وحدد علبة البريد (اسم العرض) من النتائج.

     كرر هذه الخطوة قدر ما يلزم. مجموعات التوزيع غير مسموح بها.

     لإزالة قيمة موجودة، انقر فوق إزالة ![أيقونة إزالة.](../../media/m365-cc-sc-remove-selection-icon.png) بجانب القيمة.

4. عند الانتهاء، انقر فوق **حفظ**.

يتم عرض إدخالات علبة بريد SecOps التي قمت بتكوينها على علامة التبويب **علبة بريد SecOps** . بإجراء تغييرات، انقر فوق أيقونة ![تحرير.](../../media/m365-cc-sc-edit-icon.png) **تحرير** على علامة التبويب.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>استخدام مدخل Microsoft 365 Defender لتكوين عمليات محاكاة التصيد الاحتيالي لجهة خارجية في نهج التسليم المتقدم

1. في مدخل Microsoft 365 Defender،    <https://security.microsoft.com>انتقل إلى البريد الإلكتروني **&** \> \> \> سياسات التعاون & قواعد المخاطر المتقدمة التسليم المتقدم في **القسم القواعد**. الانتقال مباشرة إلى **صفحة التسليم** المتقدم، استخدم <https://security.microsoft.com/advanceddelivery>.

2. في صفحة **التسليم المتقدم** ، **حدد علامة التبويب** محاكاة التصيد الاحتيالي، ثم قم بوا إحدى الخطوات التالية:
   - انقر فوق ![أيقونة تحرير.](../../media/m365-cc-sc-edit-icon.png) **تحرير**.
   - إذا لم تكن هناك عمليات محاكاة تصيد احتيالي مكونة، انقر فوق **إضافة**.

3. في **قائمة تحرير محاكاة** التصيد الاحتيالي من جهة خارجية التي تفتح، قم بتكوين الإعدادات التالية:

   - **المجال**: قم بتوسيع هذا الإعداد وأدخل مجال عنوان بريد إلكتروني واحد على الأقل (على سبيل المثال، contoso.com) بالنقر في المربع، ثم إدخال قيمة، ثم الضغط على Enter أو تحديد القيمة المعروضة أسفل المربع. كرر هذه الخطوة قدر ما يلزم. يمكنك إضافة ما يصل إلى 20 إدخالا.

     > [!NOTE]
     > استخدم المجال من العنوان (المعروف أيضا باسم عنوان **MAIL FROM** أو مرسل P1 أو مرسل المغلف) المستخدم في إرسال SMTP للرسالة أو المجال DomainKeys Identified Mail  (DKIM) كما هو محدد بواسطة مورد محاكاة التصيد الاحتيالي.`5321.MailFrom` 

   - إرسال **IP**: قم بتوسيع هذا الإعداد وأدخل عنوان IPv4 صالحا واحدا على الأقل بالنقر في المربع، ثم إدخال قيمة، ثم الضغط على Enter أو تحديد القيمة المعروضة أسفل المربع. كرر هذه الخطوة قدر ما يلزم. يمكنك إضافة ما يصل إلى 10 إدخالات. القيم الصالحة هي:
     - IP واحد: على سبيل المثال، 192.168.1.1.
     - نطاق IP: على سبيل المثال، 192.168.0.1-192.168.0.254.
     - CIDR IP: على سبيل المثال، 192.168.0.1/25.
   - **عناوين URL** المحاكاة للسماح بما يلي: قم بتوسيع هذا الإعداد وأدخل عناوين URL معينة بشكل اختياري التي تكون جزءا من حملة محاكاة التصيد الاحتيالي التي يجب ألا يتم حظرها أو إعاقتها بالنقر في المربع، أو إدخال قيمة، ثم الضغط على Enter أو تحديد القيمة المعروضة أسفل المربع. يمكنك إضافة ما يصل إلى 10 إدخالات. للحصول على تنسيق بناء جملة URL، راجع بناء جملة [URL لقائمة السماح/الحظر](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list) للمستأجر. تكون عناوين URL هذه ملتفة في وقت النقر، ولكن لا يتم حظرها.

   لإزالة قيمة موجودة، انقر فوق إزالة ![أيقونة إزالة.](../../media/m365-cc-sc-remove-selection-icon.png) بجانب القيمة.

   > [!NOTE]
   > لتكوين محاكاة التصيد الاحتيالي لجهة خارجية في التسليم المتقدم، ستحتاج إلى توفير المعلومات التالية:
   > 
   > - مجال واحد **على** الأقل من أي من المصادر التالية:
   >   - العنوان `5321.MailFrom` (المعروف أيضا باسم عنوان MAIL FROM أو مرسل P1 أو مرسل المغلف).
   >   - مجال DKIM.
   > - إرسال IP واحد **على الأقل**.
   > 
   > قد تقوم بشكل اختياري بتضمين **عناوين URL للمحاكاة للسماح** لك بضمان عدم حظر عناوين URL في رسائل المحاكاة.
   > يمكنك تحديد ما يصل إلى 10 إدخالات لكل حقل.
   > يجب أن يكون هناك تطابق على مجال واحد على  الأقل ومجال **واحد لإرسال IP**، ولكن لا يتم الاحتفاظ بالاقتران بين القيم.

4. عند الانتهاء، يمكنك القيام بوا إحدى الخطوات التالية:
   - **المرة الأولى**: **انقر فوق إضافة**، ثم انقر فوق **إغلاق**.
   - **تحرير موجود**: انقر فوق **حفظ** ثم فوق **إغلاق**.

يتم عرض إدخالات محاكاة التصيد الاحتيالي التي قمت بتكوينها من جهة خارجية على علامة التبويب **محاكاة التصيد** الاحتيالي. بإجراء تغييرات، انقر فوق أيقونة ![تحرير.](../../media/m365-cc-sc-edit-icon.png) **تحرير** على علامة التبويب.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>سيناريوهات إضافية تتطلب تجاوز التصفية

بالإضافة إلى السيناريوهين الذين يمكن أن يساعدك نهج التسليم المتقدم في العمل عليه، هناك سيناريوهات أخرى قد تتطلب منك تجاوز التصفية:

- **عوامل التصفية** التي توفرها جهة خارجية: إذا لم يشير سجل MX  لمجالك إلى Office 365 (يتم توجيه الرسائل إلى مكان آخر أولا)، فلا يتوفر الأمان [](secure-by-default.md) *بشكل افتراضي*. إذا كنت تريد إضافة حماية، ستحتاج إلى تمكين التصفية المحسنة للموصلات (المعروفة أيضا *بتخطي البيانات*). لمزيد من المعلومات، راجع [إدارة تدفق البريد باستخدام خدمة](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud) سحابية من جهة خارجية Exchange Online. إذا كنت لا تريد تصفية محسنة للموصلات، فاستخدم قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) لتجاوز تصفية Microsoft للرسائل التي تم تقييمها مسبقا بواسطة تصفية جهة خارجية. لمزيد من المعلومات، راجع [استخدام قواعد تدفق البريد لتعيين SCL في الرسائل](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- **الإيجابيات** الخاطئة قيد المراجعة: قد ترغب في السماح مؤقتا لبعض الرسائل التي لا تزال يتم تحليلها بواسطة Microsoft عبر إرسالات [](admin-submission.md) المسؤول بلتقارير عن الرسائل الجيدة المعروفة التي تم وضع علامة سيئة عليها بشكل غير صحيح من قبل Microsoft (إيجابية خاطئة). وكما هو الأمر مع جميع التجاوزات، **** نوصي بشدة بأن تكون هذه البدلات مؤقتة.

## <a name="security--compliance-center-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>إجراءات & مركز التوافق PowerShell لعلب بريد SecOps في نهج التسليم المتقدم

في Security & Compliance Center PowerShell، العناصر الأساسية لعلب بريد SecOps في نهج التسليم المتقدم هي:

- **نهج تجاوز SecOps**: يتم التحكم فيه بواسطة **\*-SecOpsOverridePolicy** cmdlets.
- **قاعدة تجاوز SecOps**: يتم التحكم فيها بواسطة **\*-SecOpsOverrideRule** cmdlets.

يؤدي هذا السلوك إلى النتائج التالية:

- تقوم بإنشاء النهج أولا، ثم تقوم بإنشاء القاعدة التي تحدد النهج الذي تنطبق عليه القاعدة.
- عند إزالة نهج من PowerShell، تتم أيضا إزالة القاعدة المطابقة.
- عند إزالة قاعدة من PowerShell، لن تتم إزالة النهج المقابل. تحتاج إلى إزالة النهج المناظر يدويا.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>استخدام PowerShell لتكوين علب بريد SecOps

تكوين علبة بريد SecOps في نهج التسليم المتقدم في PowerShell هو عملية مكونة من خطوتين:

1. إنشاء نهج تجاوز SecOps.
2. إنشاء قاعدة تجاوز SecOps التي تحدد النهج الذي تنطبق عليه القاعدة.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>الخطوة 1: استخدام PowerShell لإنشاء نهج تجاوز SecOps

لإنشاء نهج تجاوز SecOps، استخدم بناء الجملة التالي:

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> بغض النظر عن قيمة الاسم التي تحددها، سيكون اسم النهج _SecOpsOverridePolicy_، لذا يمكنك أيضا استخدام هذه القيمة.

ينشئ هذا المثال نهج علبة بريد SecOps.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>الخطوة 2: استخدام PowerShell لإنشاء قاعدة تجاوز SecOps

ينشئ هذا المثال قاعدة علبة بريد SecOps مع الإعدادات المحددة.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> بغض النظر عن قيمة الاسم التي تحددها، سيكون اسم القاعدة _SecOpsOverrideRule_\<GUID\> \<GUID\> حيث تكون قيمة GUID فريدة (على سبيل المثال، 6fed4b63-3563-495d-a481-b24a311f8329).

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>استخدام PowerShell لعرض نهج تجاوز SecOps

يرجع هذا المثال معلومات مفصلة حول نهج علبة بريد SecOps واحد فقط.

```powershell
Get-SecOpsOverridePolicy
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>استخدام PowerShell لعرض قواعد تجاوز SecOps

يرجع هذا المثال معلومات مفصلة حول قواعد تجاوز SecOps.

```powershell
Get-SecOpsOverrideRule
```

على الرغم من أنه يجب أن يؤدي الأمر السابق إلى إرجاع قاعدة واحدة فقط، إلا أنه قد يتم أيضا تضمين أي قواعد معلقة في النتائج.

يحدد هذا المثال القاعدة الصالحة (واحدة) وأي قواعد غير صالحة.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

بعد تحديد القواعد غير الصالحة، يمكنك إزالتها باستخدام **الأمر cmdlet Remove-SecOpsOverrideRule** كما هو موضح لاحقا [في هذه المقالة](#use-powershell-to-remove-secops-override-rules).

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>استخدام PowerShell لتعديل نهج تجاوز SecOps

لتعديل نهج تجاوز SecOps، استخدم بناء الجملة التالي:

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

يضيف هذا المثال `secops2@contoso.com` إلى نهج تجاوز SecOps.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> إذا كانت هناك قاعدة تجاوز SecOps صالحة مقترنة، سيتم أيضا تحديث عناوين البريد الإلكتروني في القاعدة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>استخدام PowerShell لتعديل قاعدة تجاوز SecOps

لا **يعدل الأمر Cmdlet Set-SecOpsOverrideRule** عناوين البريد الإلكتروني في قاعدة تجاوز SecOps. لتعديل عناوين البريد الإلكتروني في قاعدة تجاوز SecOps، استخدم **الأمر cmdlet Set-SecOpsOverridePolicy** .

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>استخدام PowerShell لإزالة نهج تجاوز SecOps

يزيل هذا المثال نهج علبة بريد SecOps والقاعدة المطابقة.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>استخدام PowerShell لإزالة قواعد تجاوز SecOps

لإزالة قاعدة تجاوز SecOps، استخدم بناء الجملة التالي:

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

يزيل هذا المثال قاعدة تجاوز SecOps المحددة.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-center-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>إجراءات & مركز التوافق PowerShell لمحاكاة التصيد الاحتيالي لجهة خارجية في نهج التسليم المتقدم

في الأمان & مركز التوافق PowerShell، العناصر الأساسية لمحاكاة التصيد الاحتيالي لجهة خارجية في نهج التسليم المتقدم هي:

- **نهج تجاوز محاكاة التصيد الاحتيالي**: يتم **\*التحكم فيه بواسطة cmdlets -PhishSimOverridePolicy** .
- **تجاوز قاعدة تجاوز محاكاة التصيد الاحتيالي**: يتم التحكم بها بواسطة **\*cmdlets -PhishSimOverrideRule** .
- عناوين URL لمحاكاة التصيد الاحتيالي **المسموح بها (** إلغاء حظرها): **\*يتم التحكم بها بواسطة cmdlets -TenantAllowBlockListItems**.

يؤدي هذا السلوك إلى النتائج التالية:

- تقوم بإنشاء النهج أولا، ثم تقوم بإنشاء القاعدة التي تحدد النهج الذي تنطبق عليه القاعدة.
- يمكنك تعديل الإعدادات في النهج والقاعدة بشكل منفصل.
- عند إزالة نهج من PowerShell، تتم أيضا إزالة القاعدة المطابقة.
- عند إزالة قاعدة من PowerShell، لن تتم إزالة النهج المقابل. تحتاج إلى إزالة النهج المناظر يدويا.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>استخدام PowerShell لتكوين عمليات محاكاة التصيد الاحتيالي لجهة خارجية

تكوين محاكاة التصيد الاحتيالي لجهة خارجية في PowerShell عملية متعددة الخطوات:

1. إنشاء نهج تجاوز محاكاة التصيد الاحتيالي.
2. إنشاء قاعدة تجاوز محاكاة التصيد الاحتيالي التي تحدد:
   - النهج الذي تنطبق عليه القاعدة.
   - عنوان IP المصدر لرسائل محاكاة التصيد الاحتيالي.
3. بشكل اختياري، يتم تحديد عناوين URL لمحاكاة التصيد الاحتيالي التي يجب السماح بها (أي، لا يتم حظرها أو فحصها).

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>الخطوة 1: استخدام PowerShell لإنشاء نهج تجاوز محاكاة التصيد الاحتيالي

ينشئ هذا المثال نهج تجاوز محاكاة التصيد الاحتيالي.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**ملاحظة**: بغض النظر عن قيمة الاسم التي تحددها، سيكون اسم النهج _PhishSimOverridePolicy_، لذا يمكنك أيضا استخدام هذه القيمة.

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>الخطوة 2: استخدام PowerShell لإنشاء قاعدة تجاوز محاكاة التصيد الاحتيالي

استخدم بناء الجملة التالي:

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

بغض النظر عن قيمة الاسم التي تحددها، سيكون اسم القاعدة _PhishSimOverrideRule_\<GUID\> \<GUID\> حيث تكون قيمة GUID فريدة (على سبيل المثال، a0eae53e-d755-4a42-9320-b9c6b55c5011).

إدخال عنوان IP صالح هو إحدى القيم التالية:

- IP واحد: على سبيل المثال، 192.168.1.1.
- نطاق IP: على سبيل المثال، 192.168.0.1-192.168.0.254.
- CIDR IP: على سبيل المثال، 192.168.0.1/25.

ينشئ هذا المثال قاعدة تجاوز محاكاة التصيد الاحتيالي باستخدام الإعدادات المحددة.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

للحصول على بناء جملة تفصيلي ومعلومات المعلمة، راجع [New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>الخطوة 3: (اختياري) استخدم PowerShell لتحديد عناوين URL محاكاة التصيد الاحتيالي للسماح

استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

للحصول على تفاصيل حول بناء جملة URL، راجع بناء جملة [URL لقائمة السماح/الحظر](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list) للمستأجر.

يضيف هذا المثال إدخال السماح ل URL ل URL محاكاة التصيد الاحتيالي المحدد لجهة خارجية بدون انتهاء الصلاحية.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>استخدام PowerShell لعرض نهج تجاوز محاكاة التصيد الاحتيالي

يرجع هذا المثال معلومات مفصلة حول نهج تجاوز محاكاة التصيد الاحتيالي واحد فقط.

```powershell
Get-PhishSimOverridePolicy
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>استخدام PowerShell لعرض قواعد تجاوز محاكاة التصيد الاحتيالي

يرجع هذا المثال معلومات مفصلة حول قواعد تجاوز محاكاة التصيد الاحتيالي.

```powershell
Get-PhishSimOverrideRule
```

على الرغم من أنه يجب أن يؤدي الأمر السابق إلى إرجاع قاعدة واحدة فقط، إلا أنه قد يتم أيضا تضمين أي قواعد معلقة في النتائج.

يحدد هذا المثال القاعدة الصالحة (واحدة) وأي قواعد غير صالحة.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

بعد تحديد القواعد غير الصالحة، يمكنك إزالتها باستخدام **الأمر cmdlet Remove-PhishSimOverrideRule** كما هو موضح لاحقا [في هذه المقالة](#use-powershell-to-remove-phishing-simulation-override-rules).

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>استخدام PowerShell لعرض إدخالات URL لمحاكاة التصيد الاحتيالي المسموح بها

لعرض عناوين URL لمحاكاة التصيد الاحتيالي المسموح بها، يمكنك تشغيل الأمر التالي:

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>استخدام PowerShell لتعديل نهج تجاوز محاكاة التصيد الاحتيالي

لتعديل نهج تجاوز محاكاة التصيد الاحتيالي، استخدم بناء الجملة التالي:

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

يعطل هذا المثال نهج تجاوز محاكاة التصيد الاحتيالي.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>استخدام PowerShell لتعديل قواعد تجاوز محاكاة التصيد الاحتيالي

لتعديل قاعدة تجاوز محاكاة التصيد الاحتيالي، استخدم بناء الجملة التالي:

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

يعدل هذا المثال قاعدة تجاوز محاكاة التصيد الاحتيالي المحددة باستخدام الإعدادات التالية:

- أضف إدخال المجال blueyonderairlines.com.
- إزالة إدخال عنوان IP 192.168.1.55.

لاحظ أن هذه التغييرات لا تؤثر على الإدخالات الموجودة.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

للحصول على بناء جملة تفصيلي ومعلومات المعلمة، راجع [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>استخدام PowerShell لتعديل إدخالات URL لمحاكاة التصيد الاحتيالي المسموح بها

لا يمكنك تعديل قيم URL مباشرة. يمكنك إزالة [إدخالات URL الموجودة](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) [وإضافة إدخالات URL جديدة](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow) كما هو موضح في هذه المقالة.

لتعديل خصائص أخرى من إدخال URL لمحاكاة التصيد الاحتيالي المسموح به (على سبيل المثال، تاريخ انتهاء الصلاحية أو التعليقات)، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

يمكنك تحديد الإدخال الذي يجب تعديله حسب قيم URL الخاصة به (المعلمة _الإدخالات_ ) أو قيمة الهوية من إخراج **Cmdlet Get-TenantAllowBlockListItems** (المعلمة _Ids_ ).

عدل هذا المثال تاريخ انتهاء صلاحية الإدخال المحدد.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>استخدام PowerShell لإزالة نهج تجاوز محاكاة التصيد الاحتيالي

يزيل هذا المثال نهج تجاوز محاكاة التصيد الاحتيالي والقاعدة المقابلة.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>استخدام PowerShell لإزالة قواعد تجاوز محاكاة التصيد الاحتيالي

لإزالة قاعدة تجاوز محاكاة التصيد الاحتيالي، استخدم بناء الجملة التالي:

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

يزيل هذا المثال قاعدة تجاوز محاكاة التصيد الاحتيالي المحددة.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>استخدام PowerShell لإزالة إدخالات URL لمحاكاة التصيد الاحتيالي المسموح بها

لإزالة إدخال URL محاكاة التصيد الاحتيالي الموجود، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

يمكنك تحديد الإدخال الذي يجب تعديله حسب قيم URL الخاصة به (المعلمة _الإدخالات_ ) أو قيمة الهوية من إخراج **Cmdlet Get-TenantAllowBlockListItems** (المعلمة _Ids_ ).

عدل هذا المثال تاريخ انتهاء صلاحية الإدخال المحدد.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

للحصول على بناء جملة تفصيلي ومعلومات المعلمة، راجع [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
