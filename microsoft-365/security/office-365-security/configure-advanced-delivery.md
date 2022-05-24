---
title: تكوين تسليم عمليات محاكاة التصيد الاحتيالي التابعة لجهات خارجية للمستخدمين والرسائل التي لم تتم تصفتها إلى علب بريد SecOps
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
description: يمكن للمسؤولين معرفة كيفية استخدام نهج التسليم المتقدم في Exchange Online Protection (EOP) لتحديد الرسائل التي لا يجب تصفيتها في سيناريوهات معينة مدعومة (محاكاة التصيد الاحتيالي من جهة خارجية والرسائل التي يتم تسليمها إلى علب بريد عمليات الأمان (SecOps).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d9a959e70408af80567d1daed140e0642870b975
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647788"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>تكوين تسليم عمليات محاكاة التصيد الاحتيالي التابعة لجهات خارجية للمستخدمين والرسائل التي لم تتم تصفتها إلى علب بريد SecOps

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

للحفاظ على أمان مؤسستك [بشكل افتراضي](secure-by-default.md)، لا يسمح Exchange Online Protection (EOP) بتجاوز القوائم الآمنة أو التصفية للرسائل التي تم تعريفها على أنها برامج ضارة أو تصيد احتيالي عالي الثقة. ولكن، هناك سيناريوهات محددة تتطلب تسليم الرسائل غير التصفية. على سبيل المثال:

- **محاكاة التصيد الاحتيالي لجهات خارجية**: يمكن أن تساعدك هجمات المحاكاة في تحديد المستخدمين المعرضين للخطر قبل أن يؤثر هجوم حقيقي على مؤسستك.
- **علب بريد عمليات الأمان (SecOps):** علب البريد المخصصة التي تستخدمها فرق الأمان لجمع الرسائل التي لم تتم تصفتها وتحليلها (سواء كانت جيدة أو سيئة).

يمكنك استخدام _نهج التسليم المتقدم_ في Microsoft 365 لمنع تصفية الرسائل الواردة _في هذه السيناريوهات المحددة_.<sup>\*</sup> يضمن نهج التسليم المتقدم أن الرسائل في هذه السيناريوهات تحقق النتائج التالية:

- لا تتخذ عوامل التصفية في EOP Microsoft Defender لـ Office 365 أي إجراء بشأن هذه الرسائل.<sup>\*</sup>
- لا تتخذ [عملية الإزالة بدون ساعة (ZAP)](zero-hour-auto-purge.md) للبريد العشوائي والتصيد الاحتيالي أي إجراء على هذه الرسائل.<sup>\*\*</sup>
- لا يتم تشغيل [تنبيهات النظام الافتراضية](/microsoft-365/compliance/alert-policies#default-alert-policies) لهذه السيناريوهات.
- يتجاهل [AIR والتجموع في Defender لـ Office 365](office-365-air.md) هذه الرسائل.
- خصيصا لمحاكاة التصيد الاحتيالي من جهة خارجية:
  - [تنشئ عمليات الإرسال مسؤول](admin-submission.md) استجابة تلقائية تفيد بأن الرسالة جزء من حملة محاكاة التصيد الاحتيالي ولا تشكل تهديدا حقيقيا. لن يتم تشغيل التنبيهات و AIR. ستظهر تجربة عمليات إرسال المسؤول هذه الرسائل كتهديد محاكاة.
  - عندما يبلغ المستخدم عن رسالة محاكاة تصيد احتيالي باستخدام [الوظيفة الإضافية "رسالة التقرير" أو "الإبلاغ عن التصيد الاحتيالي](enable-the-report-message-add-in.md)"، لن ينشئ النظام تنبيها أو تحقيقا أو حادثا. لن يتم حذف الارتباطات أو الملفات، ولكن ستظهر الرسالة أيضا على علامة تبويب **الرسائل التي أبلغ عنها المستخدم** في صفحة **عمليات الإرسال** .
  - [لا تحظر الارتباطات خزينة في Defender لـ Office 365](safe-links.md) عناوين URL المحددة في هذه الرسائل أو تحجبها في وقت النقر. لا تزال عناوين URL ملتفة، ولكن لم يتم حظرها.
  - [خزينة المرفقات في Defender لـ Office 365](safe-attachments.md) لا تخلط المرفقات في هذه الرسائل.

<sup>\*</sup> لا يمكنك تجاوز تصفية البرامج الضارة.

<sup>\*\*</sup> يمكنك تجاوز ZAP للبرامج الضارة عن طريق إنشاء نهج مكافحة البرامج الضارة لعلب بريد SecOps حيث يتم إيقاف تشغيل ZAP للبرامج الضارة. للحصول على الإرشادات، راجع [تكوين نهج مكافحة البرامج الضارة في EOP](configure-anti-malware-policies.md).

الرسائل التي يتم تحديدها بواسطة نهج التسليم المتقدم ليست تهديدات أمنية، لذلك يتم وضع علامة على الرسائل بتجاوزات النظام. ستظهر تجارب مسؤول هذه الرسائل إما بسبب تجاوز نظام **محاكاة التصيد الاحتيالي** أو تجاوز نظام **علبة بريد SecOps**. يمكن للمسؤولين التصفية والتحليل على تجاوزات النظام هذه في التجارب التالية:

- [اكتشافات مستكشف التهديدات/الوقت الحقيقي في Defender لـ Office 365 الخطة 2](threat-explorer.md): يمكن مسؤول التصفية حسب **مصدر تجاوز النظام** وتحديد **إما محاكاة التصيد الاحتيالي** أو **علبة بريد SecOps**.
- [صفحة كيان البريد الإلكتروني في اكتشافات مستكشف المخاطر/الوقت الحقيقي](mdo-email-entity-page.md): يمكن مسؤول عرض رسالة تم السماح بها بواسطة نهج المؤسسة إما بواسطة **علبة بريد SecOps** أو **محاكاة التصيد الاحتيالي** ضمن **تجاوز المستأجر** في قسم **(التجاوزات**).
- [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report): يمكن مسؤول التصفية عن طريق **عرض البيانات حسب تجاوز النظام** في القائمة المنسدلة وتحديد رؤية الرسائل المسموح بها بسبب تجاوز نظام محاكاة التصيد الاحتيالي. للاطلاع على الرسائل المسموح بها بواسطة تجاوز علبة بريد SecOps، يمكنك تحديد **تصنيف تفصيلي للمخطط حسب موقع التسليم** في **تصنيف المخطط التفصيلي حسب** القائمة المنسدلة للسبب.
- [التتبع المتقدم في Microsoft Defender لنقطة النهاية](../defender-endpoint/advanced-hunting-overview.md): ستظهر محاكاة التصيد الاحتيالي وتجاوزات نظام علبة بريد SecOps كخيارات داخل OrgLevelPolicy في EmailEvents.
- [طرق عرض الحملة](campaigns.md): يمكن مسؤول التصفية حسب **مصدر تجاوز النظام** وتحديد **إما محاكاة التصيد الاحتيالي** أو **علبة بريد SecOps**.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **التسليم المتقدم** ، افتح <https://security.microsoft.com/advanceddelivery>.

- للاتصال ب PowerShell ل Security & Compliance Center، راجع [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

- يجب تعيين أذونات لك قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - لإنشاء الإعدادات المكونة أو تعديلها أو إزالتها في نهج التسليم المتقدم، يجب أن تكون عضوا في مجموعة دور **مسؤول الأمان** في **مدخل Microsoft 365 Defender** وعضوا في مجموعة دور **إدارة المؤسسة** في **Exchange Online**.
  - للوصول للقراءة فقط إلى نهج التسليم المتقدم، يجب أن تكون عضوا في مجموعات دور **القارئ العمومي** أو **قارئ الأمان** .

  لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md) [والأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > إضافة مستخدمين إلى دور Azure Active Directory المقابل يمنح المستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender _والأذونات_ للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>استخدم مدخل Microsoft 365 Defender لتكوين علب بريد SecOps في نهج التسليم المتقدم

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **نهج التعاون** \> & البريد الإلكتروني & **التسليم المتقدم** **لنهج** \> مخاطر **القواعد** \> في قسم **القواعد**. للانتقال مباشرة إلى صفحة **التسليم المتقدم** ، استخدم <https://security.microsoft.com/advanceddelivery>.

2. في صفحة **التسليم المتقدم** ، تحقق من تحديد علامة تبويب **علبة بريد SecOps** ، ثم نفذ إحدى الخطوات التالية:
   - انقر فوق ![أيقونة "تحرير".](../../media/m365-cc-sc-edit-icon.png) **تحرير**.
   - إذا لم تكن هناك عمليات محاكاة للتصيد الاحتيالي المكونة، فانقر فوق **"إضافة**".

3. في القائمة المنبثقة **"تحرير علب بريد SecOps**" التي يتم فتحها، أدخل علبة بريد Exchange Online موجودة تريد تعيينها كعلبة بريد SecOps عن طريق تنفيذ إحدى الخطوات التالية:
   - انقر في المربع، ودع قائمة علب البريد تحل، ثم حدد علبة البريد.
   - انقر في المربع لبدء كتابة معرف لعل البريد (الاسم واسم العرض والاسم المستعار وعنوان البريد الإلكتروني واسم الحساب وما إلى ذلك)، وحدد علبة البريد (اسم العرض) من النتائج.

     كرر هذه الخطوة عدة مرات حسب الضرورة. مجموعات التوزيع غير مسموح بها.

     لإزالة قيمة موجودة، انقر فوق "إزالة" ![الأيقونة "إزالة".](../../media/m365-cc-sc-remove-selection-icon.png) بجوار القيمة.

4. عند الانتهاء، انقر فوق **حفظ**.

يتم عرض إدخالات علبة بريد SecOps التي قمت بتكوينها على علامة تبويب **علبة بريد SecOps** . لإجراء تغييرات، انقر فوق ![أيقونة "تحرير".](../../media/m365-cc-sc-edit-icon.png) **تحرير** على علامة التبويب.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>استخدام مدخل Microsoft 365 Defender لتكوين محاكاة التصيد الاحتيالي لجهة خارجية في نهج التسليم المتقدم

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **نهج التعاون** \> & البريد الإلكتروني & **التسليم المتقدم** **لنهج** \> مخاطر **القواعد** \> في قسم **القواعد**. للانتقال مباشرة إلى صفحة **التسليم المتقدم** ، استخدم <https://security.microsoft.com/advanceddelivery>.

2. في صفحة **التسليم المتقدم** ، حدد علامة **تبويب محاكاة التصيد الاحتيالي** ، ثم نفذ إحدى الخطوات التالية:
   - انقر فوق ![أيقونة "تحرير".](../../media/m365-cc-sc-edit-icon.png) **تحرير**.
   - إذا لم تكن هناك عمليات محاكاة للتصيد الاحتيالي المكونة، فانقر فوق **"إضافة**".

3. في القائمة المنبثقة **"تحرير محاكاة التصيد الاحتيالي لجهة خارجية** " التي يتم فتحها، قم بتكوين الإعدادات التالية:

   - **المجال**: قم بتوسيع هذا الإعداد وأدخل مجال عنوان بريد إلكتروني واحد على الأقل (على سبيل المثال، contoso.com) بالنقر فوق المربع وإدخال قيمة ثم الضغط على مفتاح الإدخال Enter أو تحديد القيمة المعروضة أسفل المربع. كرر هذه الخطوة عدة مرات حسب الضرورة. يمكنك إضافة ما يصل إلى 20 إدخالا.

     > [!NOTE]
     > استخدم المجال من `5321.MailFrom` العنوان (المعروف أيضا بعنوان **MAIL FROM** أو مرسل P1 أو مرسل المغلفات) المستخدم في إرسال SMTP للرسالة **أو** مجال DomainKeys Identified Mail (DKIM) كما هو محدد من قبل مورد محاكاة التصيد الاحتيالي. 

   - **إرسال IP**: قم بتوسيع هذا الإعداد وأدخل عنوان IPv4 صالحا واحدا على الأقل بالنقر فوق المربع وإدخال قيمة ثم الضغط على مفتاح الإدخال Enter أو تحديد القيمة المعروضة أسفل المربع. كرر هذه الخطوة عدة مرات حسب الضرورة. يمكنك إضافة ما يصل إلى 10 إدخالات. القيم الصحيحة هي:
     - عنوان IP واحد: على سبيل المثال، 192.168.1.1.
     - نطاق IP: على سبيل المثال، 192.168.0.1-192.168.0.254.
     - CIDR IP: على سبيل المثال، 192.168.0.1/25.
   - **عناوين URL للمحاكاة للسماح** بها: قم بتوسيع هذا الإعداد وأدخل بشكل اختياري عناوين URL معينة تشكل جزءا من حملة محاكاة التصيد الاحتيالي التي لا يجب حظرها أو معالجتها بالنقر في المربع وإدخال قيمة ثم الضغط على مفتاح الإدخال Enter أو تحديد القيمة المعروضة أسفل المربع. يمكنك إضافة ما يصل إلى 10 إدخالات. للحصول على تنسيق جملة URL، راجع [بناء جملة URL لقائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list). يتم تضمين عناوين URL هذه في وقت النقر، ولكن لا يتم حظرها.

   لإزالة قيمة موجودة، انقر فوق "إزالة" ![الأيقونة "إزالة".](../../media/m365-cc-sc-remove-selection-icon.png) بجوار القيمة.

   > [!NOTE]
   > لتكوين محاكاة تصيد احتيالي لجهة خارجية في التسليم المتقدم، تحتاج إلى تهيئة المعلومات التالية:
   > 
   > - **مجال** واحد على الأقل من أي من المصادر التالية:
   >   - `5321.MailFrom` العنوان (المعروف أيضا بعنوان MAIL FROM أو مرسل P1 أو مرسل المغلف).
   >   - مجال DKIM.
   > - **عنوان IP** واحد على الأقل.
   > 
   > يمكنك بشكل اختياري تضمين **عناوين URL المحاكاة للسماح** بالتأكد من عدم حظر عناوين URL في رسائل المحاكاة.
   > يمكنك تحديد ما يصل إلى 10 إدخالات لكل حقل.
   > يجب أن يكون هناك تطابق على **مجال** واحد على الأقل **وIP واحد يتم إرساله**، ولكن لا يتم الاحتفاظ بأي اقتران بين القيم.

4. عند الانتهاء، نفذ إحدى الخطوات التالية:
   - **المرة الأولى**: انقر فوق **"إضافة**"، ثم انقر فوق **"إغلاق**".
   - **تحرير الموجود**: انقر فوق **"حفظ"** ثم فوق **"إغلاق**".

يتم عرض إدخالات محاكاة التصيد الاحتيالي التابعة لجهة خارجية التي قمت بتكوينها على علامة تبويب **محاكاة التصيد الاحتيالي** . لإجراء تغييرات، انقر فوق ![أيقونة "تحرير".](../../media/m365-cc-sc-edit-icon.png) **تحرير** على علامة التبويب.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>سيناريوهات إضافية تتطلب تجاوز التصفية

بالإضافة إلى السيناريوهين اللذين يمكن أن يساعدك نهج التسليم المتقدم فيهما، هناك سيناريوهات أخرى قد تتطلب منك تجاوز التصفية:

- **عوامل التصفية التابعة لجهة خارجية**: إذا *لم* يشير سجل MX لمجالك إلى Office 365 (يتم توجيه الرسائل في مكان آخر أولا)، *فلن يتوفر* [الأمان بشكل افتراضي](secure-by-default.md). إذا كنت ترغب في إضافة حماية، فستحتاج إلى تمكين التصفية المحسنة للموصلات (المعروفة أيضا باسم *قائمة التخطي*). لمزيد من المعلومات، راجع [إدارة تدفق البريد باستخدام خدمة سحابية تابعة لجهة خارجية مع Exchange Online](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud). إذا كنت لا تريد التصفية المحسنة للموصلات، فاستخدم قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) لتجاوز تصفية Microsoft للرسائل التي تم تقييمها بالفعل بواسطة تصفية الجهات الخارجية. لمزيد من المعلومات، راجع [استخدام قواعد تدفق البريد لتعيين SCL في الرسائل](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- **الإيجابيات الخاطئة قيد المراجعة**: قد ترغب في السماح مؤقتا لرسائل معينة لا تزال تقوم Microsoft بتحليلها عبر [عمليات إرسال المسؤول](admin-submission.md) للإبلاغ عن الرسائل الجيدة المعروفة التي يتم وضع علامة عليها بشكل غير صحيح على أنها سيئة ل Microsoft (إيجابيات خاطئة). وكما هو الحال مع جميع عمليات التجاوز، **_نوصي بشدة_** بأن تكون هذه البدلات مؤقتة.

## <a name="security--compliance-center-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>إجراءات Security & Compliance Center PowerShell لعلب بريد SecOps في نهج التسليم المتقدم

في Security & Compliance Center PowerShell، فإن العناصر الأساسية لعلب بريد SecOps في نهج التسليم المتقدم هي:

- **نهج تجاوز SecOps**: يتم التحكم فيه بواسطة **\*أوامر cmdlets -SecOpsOverridePolicy** .
- **قاعدة التجاوز SecOps**: التي يتم التحكم فيها بواسطة **\*cmdlets -SecOpsOverrideRule** .

يحتوي هذا السلوك على النتائج التالية:

- يمكنك إنشاء النهج أولا، ثم إنشاء القاعدة التي تحدد النهج الذي تنطبق عليه القاعدة.
- عند إزالة نهج من PowerShell، تتم أيضا إزالة القاعدة المقابلة.
- عند إزالة قاعدة من PowerShell، لا تتم إزالة النهج المقابل. تحتاج إلى إزالة النهج المقابل يدويا.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>استخدام PowerShell لتكوين علب بريد SecOps

تكوين علبة بريد SecOps في نهج التسليم المتقدم في PowerShell هو عملية من خطوتين:

1. إنشاء نهج تجاوز SecOps.
2. إنشاء قاعدة تجاوز SecOps التي تحدد النهج الذي تنطبق عليه القاعدة.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>الخطوة 1: استخدام PowerShell لإنشاء نهج تجاوز SecOps

لإنشاء نهج تجاوز SecOps، استخدم بناء الجملة التالي:

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> بغض النظر عن قيمة الاسم التي تحددها، سيكون اسم النهج _SecOpsOverridePolicy_، لذلك يمكنك أيضا استخدام هذه القيمة.

ينشئ هذا المثال نهج علبة بريد SecOps.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>الخطوة 2: استخدام PowerShell لإنشاء قاعدة تجاوز SecOps

ينشئ هذا المثال قاعدة علبة بريد SecOps مع الإعدادات المحددة.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> بغض النظر عن قيمة الاسم التي تحددها، سيكون اسم القاعدة _SecOpsOverrideRule_\<GUID\> حيث \<GUID\> تكون قيمة GUID فريدة (على سبيل المثال، 6fed4b63-3563-495d-a481-b24a311f8329).

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>استخدام PowerShell لعرض نهج تجاوز SecOps

يقوم هذا المثال بإرجاع معلومات مفصلة حول نهج علبة بريد SecOps واحد فقط.

```powershell
Get-SecOpsOverridePolicy
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>استخدام PowerShell لعرض قواعد تجاوز SecOps

يرجع هذا المثال معلومات مفصلة حول قواعد تجاوز SecOps.

```powershell
Get-SecOpsOverrideRule
```

على الرغم من أن الأمر السابق يجب أن يرجع قاعدة واحدة فقط، قد يتم أيضا تضمين أي قواعد معلقة الحذف في النتائج.

يحدد هذا المثال القاعدة الصحيحة (واحدة) وأي قواعد غير صالحة.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

بعد تحديد القواعد غير الصالحة، يمكنك إزالتها باستخدام **Cmdlet Remove-SecOpsOverrideRule** كما هو موضح [لاحقا في هذه المقالة](#use-powershell-to-remove-secops-override-rules).

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>استخدام PowerShell لتعديل نهج تجاوز SecOps

لتعديل نهج تجاوز SecOps، استخدم بناء الجملة التالي:

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

يضيف `secops2@contoso.com` هذا المثال إلى نهج تجاوز SecOps.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> إذا كانت قاعدة تجاوز SecOps المقترنة صالحة، فسيتم أيضا تحديث عناوين البريد الإلكتروني في القاعدة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>استخدام PowerShell لتعديل قاعدة تجاوز SecOps

لا يقوم **Set-SecOpsOverrideRule** cmdlet بتعديل عناوين البريد الإلكتروني في قاعدة تجاوز SecOps. لتعديل عناوين البريد الإلكتروني في قاعدة تجاوز SecOps، استخدم **Set-SecOpsOverridePolicy** cmdlet.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>استخدام PowerShell لإزالة نهج تجاوز SecOps

يزيل هذا المثال نهج علبة بريد SecOps والقاعدة المقابلة.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>استخدام PowerShell لإزالة قواعد تجاوز SecOps

لإزالة قاعدة تجاوز SecOps، استخدم بناء الجملة التالي:

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

يزيل هذا المثال قاعدة تجاوز SecOps المحددة.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-center-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>إجراءات Security & Compliance Center PowerShell لمحاكاة التصيد الاحتيالي لجهات خارجية في نهج التسليم المتقدم

في Security & Compliance Center PowerShell، فإن العناصر الأساسية لمحاكاة التصيد الاحتيالي لجهة خارجية في نهج التسليم المتقدم هي:

- نهج **تجاوز محاكاة التصيد الاحتيالي**: يتحكم به **\*الأمر -PhishSimOverridePolicy** cmdlets.
- **قاعدة تجاوز محاكاة التصيد الاحتيالي**: يتم التحكم فيها بواسطة **\*-PhishSimOverrideRule** cmdlets.
- عناوين **URL لمحاكاة التصيد الاحتيالي المسموح بها (غير مقفلة**): يتم التحكم فيها بواسطة **\*cmdlets -TenantAllowBlockListItems**.

يحتوي هذا السلوك على النتائج التالية:

- يمكنك إنشاء النهج أولا، ثم إنشاء القاعدة التي تحدد النهج الذي تنطبق عليه القاعدة.
- يمكنك تعديل الإعدادات في النهج والقاعدة بشكل منفصل.
- عند إزالة نهج من PowerShell، تتم أيضا إزالة القاعدة المقابلة.
- عند إزالة قاعدة من PowerShell، لا تتم إزالة النهج المقابل. تحتاج إلى إزالة النهج المقابل يدويا.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>استخدام PowerShell لتكوين عمليات محاكاة التصيد الاحتيالي لجهات خارجية

تكوين محاكاة التصيد الاحتيالي لجهة خارجية في PowerShell هو عملية متعددة الخطوات:

1. إنشاء نهج تجاوز محاكاة التصيد الاحتيالي.
2. إنشاء قاعدة تجاوز محاكاة التصيد الاحتيالي التي تحدد:
   - النهج الذي تنطبق عليه القاعدة.
   - عنوان IP المصدر لرسائل محاكاة التصيد الاحتيالي.
3. اختياريا، حدد عناوين URL لمحاكاة التصيد الاحتيالي التي يجب السماح بها (أي لا يتم حظرها أو مسحها ضوئيا).

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>الخطوة 1: استخدام PowerShell لإنشاء نهج تجاوز محاكاة التصيد الاحتيالي

ينشئ هذا المثال نهج تجاوز محاكاة التصيد الاحتيالي.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**ملاحظة**: بغض النظر عن قيمة الاسم التي تحددها، سيكون اسم النهج _هو PhishSimOverridePolicy_، لذلك يمكنك أيضا استخدام هذه القيمة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>الخطوة 2: استخدام PowerShell لإنشاء قاعدة تجاوز محاكاة التصيد الاحتيالي

استخدم بناء الجملة التالي:

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

بغض النظر عن قيمة الاسم التي تحددها، سيكون اسم القاعدة _PhishSimOverrideRule_\<GUID\> حيث \<GUID\> تكون قيمة GUID فريدة (على سبيل المثال، a0eae53e-d755-4a42-9320-b9c6b55c5011).

إدخال عنوان IP صالح هو إحدى القيم التالية:

- عنوان IP واحد: على سبيل المثال، 192.168.1.1.
- نطاق IP: على سبيل المثال، 192.168.0.1-192.168.0.254.
- CIDR IP: على سبيل المثال، 192.168.0.1/25.

ينشئ هذا المثال قاعدة تجاوز محاكاة التصيد الاحتيالي مع الإعدادات المحددة.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>الخطوة 3: (اختياري) استخدم PowerShell لتحديد عناوين URL لمحاكاة التصيد الاحتيالي للسماح

استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

للحصول على تفاصيل حول بناء جملة URL، راجع [بناء جملة URL لقائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list).

يضيف هذا المثال عنوان URL يسمح بإدخال محدد موقع المعلومات (URL) لمحاكاة التصيد الاحتيالي المحدد من جهة خارجية دون انتهاء الصلاحية.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>استخدام PowerShell لعرض نهج تجاوز محاكاة التصيد الاحتيالي

يرجع هذا المثال معلومات مفصلة حول نهج تجاوز محاكاة التصيد الاحتيالي واحد فقط.

```powershell
Get-PhishSimOverridePolicy
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>استخدام PowerShell لعرض قواعد تجاوز محاكاة التصيد الاحتيالي

يرجع هذا المثال معلومات مفصلة حول قواعد تجاوز محاكاة التصيد الاحتيالي.

```powershell
Get-PhishSimOverrideRule
```

على الرغم من أن الأمر السابق يجب أن يرجع قاعدة واحدة فقط، قد يتم أيضا تضمين أي قواعد معلقة الحذف في النتائج.

يحدد هذا المثال القاعدة الصحيحة (واحدة) وأي قواعد غير صالحة.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

بعد تحديد القواعد غير الصالحة، يمكنك إزالتها باستخدام **Cmdlet Remove-PhishSimOverrideRule** كما هو موضح [لاحقا في هذه المقالة](#use-powershell-to-remove-phishing-simulation-override-rules).

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>استخدام PowerShell لعرض إدخالات عنوان URL لمحاكاة التصيد الاحتيالي المسموح بها

لعرض عناوين URL لمحاكاة التصيد الاحتيالي المسموح بها، قم بتشغيل الأمر التالي:

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>استخدام PowerShell لتعديل نهج تجاوز محاكاة التصيد الاحتيالي

لتعديل نهج تجاوز محاكاة التصيد الاحتيالي، استخدم بناء الجملة التالي:

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

يعطل هذا المثال نهج تجاوز محاكاة التصيد الاحتيالي.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>استخدام PowerShell لتعديل قواعد تجاوز محاكاة التصيد الاحتيالي

لتعديل قاعدة تجاوز محاكاة التصيد الاحتيالي، استخدم بناء الجملة التالي:

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

يعدل هذا المثال قاعدة تجاوز محاكاة التصيد الاحتيالي المحددة بالإعدادات التالية:

- إضافة blueyonderairlines.com إدخال المجال.
- إزالة إدخال عنوان IP 192.168.1.55.

لاحظ أن هذه التغييرات لا تؤثر على الإدخالات الموجودة.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>استخدام PowerShell لتعديل إدخالات عنوان URL لمحاكاة التصيد الاحتيالي المسموح بها

لا يمكنك تعديل قيم URL مباشرة. يمكنك [إزالة إدخالات URL الموجودة](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) [وإضافة إدخالات URL جديدة](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow) كما هو موضح في هذه المقالة.

لتعديل خصائص أخرى لإدخال محدد موقع معلومات محاكاة التصيد الاحتيالي المسموح به (على سبيل المثال، تاريخ انتهاء الصلاحية أو التعليقات)، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

يمكنك تحديد الإدخال المراد تعديله بواسطة قيم URL الخاصة به (معلمة _الإدخالات_ ) أو قيمة الهوية من إخراج **Cmdlet Get-TenantAllowBlockListItems** (معلمة _المعرف_ ).

قام هذا المثال بتعديل تاريخ انتهاء صلاحية الإدخال المحدد.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>استخدام PowerShell لإزالة نهج تجاوز محاكاة التصيد الاحتيالي

يزيل هذا المثال نهج تجاوز محاكاة التصيد الاحتيالي والقاعدة المقابلة.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>استخدام PowerShell لإزالة قواعد تجاوز محاكاة التصيد الاحتيالي

لإزالة قاعدة تجاوز محاكاة التصيد الاحتيالي، استخدم بناء الجملة التالي:

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

يزيل هذا المثال قاعدة تجاوز محاكاة التصيد الاحتيالي المحددة.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>استخدام PowerShell لإزالة إدخالات عنوان URL لمحاكاة التصيد الاحتيالي المسموح بها

لإزالة إدخال URL لمحاكاة التصيد الاحتيالي، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

يمكنك تحديد الإدخال المراد تعديله بواسطة قيم URL الخاصة به (معلمة _الإدخالات_ ) أو قيمة الهوية من إخراج **Cmdlet Get-TenantAllowBlockListItems** (معلمة _المعرف_ ).

قام هذا المثال بتعديل تاريخ انتهاء صلاحية الإدخال المحدد.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
