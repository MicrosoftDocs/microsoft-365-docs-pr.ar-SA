---
title: إعداد نهج ارتباطات خزينة في Microsoft Defender لـ Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: bdd5372d-775e-4442-9c1b-609627b94b5d
ms.collection:
- M365-security-compliance
ms.custom: ''
description: يمكن للمسؤولين التعرف على كيفية عرض نهج ارتباطات خزينة وإعدادات ارتباطات خزينة العمومية في Microsoft Defender لـ Office 365 وإنشاءها وتعديلها وحذفها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5e66b1b079f67d6454754d056ca9fedf5fefb74f
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115774"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>إعداد نهج ارتباطات خزينة في Microsoft Defender لـ Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> هذه المقالة مخصصة لعملاء الأعمال الذين لديهم [Microsoft Defender لـ Office 365](defender-for-office-365.md). إذا كنت مستخدما منزليا تبحث عن معلومات حول الارتباطات الآمنة في Outlook، فراجع [الأمان المتقدم Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

توفر خزينة الارتباطات في [Microsoft Defender لـ Office 365](defender-for-office-365.md) مسح URL لرسائل البريد الإلكتروني الواردة في تدفق البريد، ووقت التحقق من صحة عناوين URL والارتباطات في رسائل البريد الإلكتروني وفي مواقع أخرى. لمزيد من المعلومات، راجع [الارتباطات خزينة في Microsoft Defender لـ Office 365](safe-links.md).

على الرغم من عدم وجود نهج ارتباطات خزينة افتراضي، يوفر نهج الأمان المعين مسبقا **للحماية المضمنة** حماية خزينة الارتباطات لكافة المستلمين (المستخدمين الذين لم يتم تعريفهم في نهج الارتباطات خزينة المخصصة). لمزيد من المعلومات، راجع [نهج الأمان التي تم تعيينها مسبقا في EOP Microsoft Defender لـ Office 365](preset-security-policies.md).

يمكنك أيضا استخدام الإجراءات الواردة في هذه المقالة لإنشاء نهج ارتباطات خزينة تنطبق على مستخدمين أو مجموعات أو مجالات معينة.

> [!NOTE]
>
> يمكنك تكوين الإعدادات العمومية لحماية الارتباطات خزينة **خارج** نهج الارتباطات خزينة. للحصول على الإرشادات، راجع [تكوين الإعدادات العمومية للارتباطات خزينة في Microsoft Defender لـ Office 365](configure-global-settings-for-safe-links.md).
>
> يجب على المسؤولين مراعاة إعدادات التكوين المختلفة لارتباطات خزينة. أحد الخيارات المتوفرة هو تضمين معلومات تعريف المستخدم في ارتباطات خزينة. تمكن هذه الميزة فرق عمليات الأمان (SecOps) من التحقيق في اختراق المستخدم المحتمل، واتخاذ إجراءات تصحيحية، والحد من الخروقات المكلفة.

يمكنك تكوين نهج الارتباطات خزينة في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell للمؤسسات Microsoft 365 المؤهلة مع علب بريد في Exchange Online؛ EOP PowerShell مستقل للمؤسسات دون Exchange Online علب البريد، ولكن مع اشتراكات Microsoft Defender لـ Office 365 الإضافية).

العناصر الأساسية لنهج ارتباطات خزينة هي:

- **نهج الارتباطات الآمنة**: قم بتشغيل خزينة حماية الارتباطات، وقم بتشغيل مسح URL في الوقت الحقيقي، وحدد ما إذا كنت تريد انتظار اكتمال الفحص في الوقت الحقيقي قبل تسليم الرسالة، وقم بتشغيل المسح بحثا عن الرسائل الداخلية، وحدد ما إذا كان يجب تعقب نقرات المستخدم على عناوين URL، وحدد ما إذا كان يجب السماح للمستخدمين بالنقر فوق trough إلى عنوان URL الأصلي.
- **قاعدة الارتباطات الآمنة**: تحدد الأولوية وعوامل تصفية المستلم (من ينطبق عليه النهج).

لا يكون الفرق بين هذين العنصرين واضحا عند إدارة نهج الارتباطات خزينة في مدخل Microsoft 365 Defender:

- عند إنشاء نهج ارتباطات خزينة، فإنك تقوم بالفعل بإنشاء قاعدة ارتباطات آمنة ونهج الارتباطات الآمنة المقترنة في نفس الوقت باستخدام نفس الاسم لكليهما.
- عند تعديل نهج ارتباطات خزينة، تعدل الإعدادات المتعلقة بالاسم والأولوية والممكنة أو المعطلة وعوامل تصفية المستلم قاعدة الارتباطات الآمنة. تعدل كافة الإعدادات الأخرى نهج الارتباطات الآمنة المقترنة.
- عند إزالة نهج ارتباطات خزينة، تتم إزالة قاعدة الارتباطات الآمنة ونهج الارتباطات الآمنة المقترنة.

في Exchange Online PowerShell أو EOP PowerShell المستقل، يمكنك إدارة النهج والقاعدة بشكل منفصل. لمزيد من المعلومات، راجع [استخدام Exchange Online PowerShell أو EOP PowerShell المستقل لتكوين قسم نهج خزينة الارتباطات](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) لاحقا في هذه المقالة.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **ارتباطات خزينة**، استخدم <https://security.microsoft.com/safelinksv2>.

- للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع [الاتصال إلى Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- يجب تعيين أذونات لك قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - لإنشاء نهج ارتباطات خزينة وتعديلها وحذفها، يجب أن تكون عضوا في مجموعات دور **مسؤول الأمان** أو **إدارة المؤسسة** **في مدخل Microsoft 365 Defender** وعضوا في مجموعة دور **إدارة المؤسسة** في Exchange Online.
  - للوصول للقراءة فقط إلى نهج الارتباطات خزينة، يجب أن تكون عضوا في مجموعات أدوار **القارئ العمومي** أو **قارئ الأمان**.

  لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md) [والأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender _والأذونات_ للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  . - تمنح مجموعة دور **إدارة المؤسسة للعرض فقط** في [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) أيضا حق الوصول للقراءة فقط إلى الميزة.

- للحصول على الإعدادات الموصى بها لنهج الارتباطات خزينة، راجع [إعدادات نهج الارتباطات خزينة](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- السماح بما يصل إلى 6 ساعات لتطبيق نهج جديد أو محدث.

- [تتم إضافة ميزات جديدة باستمرار إلى Microsoft Defender لـ Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). عند إضافة ميزات جديدة، قد تحتاج إلى إجراء تعديلات على نهج الارتباطات خزينة الموجودة.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>استخدام مدخل Microsoft 365 Defender لإنشاء نهج ارتباطات خزينة

يؤدي إنشاء نهج ارتباطات خزينة مخصص في مدخل Microsoft 365 Defender إلى إنشاء قاعدة الارتباطات الآمنة ونهج الارتباطات الآمنة المقترنة في نفس الوقت باستخدام نفس الاسم لكليهما.

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "نهج** \> **مخاطر** القواعد \> **" خزينة الارتباطات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **ارتباطات خزينة**، استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **"ارتباطات خزينة**"، انقر فوق "![إنشاء أيقونة".](../../media/m365-cc-sc-create-icon.png) **إنشاء**.

3. يفتح معالج **نهج الارتباطات خزينة الجديدة**. في صفحة **"الاسم" في النهج** ، قم بتكوين الإعدادات التالية:

   - **الاسم**: أدخل اسما وصفيا فريدا للنهج.
   - **الوصف**: أدخل وصفا اختياريا للنهج.

   عند الانتهاء، انقر فوق **"التالي**".

4. في صفحة **المستخدمين والمجالات** التي تظهر، حدد المستلمين الداخليين الذين ينطبق عليهم النهج (شروط المستلمين):
   - **المستخدمون**: علب البريد أو مستخدمو البريد أو جهات اتصال البريد المحددة.
   - **المجموعات**:
     - أعضاء مجموعات التوزيع المحددة أو مجموعات الأمان الممكنة للبريد.
     - مجموعات Microsoft 365 المحددة.
   - **المجالات**: كافة المستلمين في [المجالات المقبولة المحددة](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) في مؤسستك.

   انقر في المربع المناسب، وابدأ بكتابة قيمة، وحدد القيمة التي تريدها من النتائج. كرر هذه العملية عدة مرات حسب الضرورة. لإزالة قيمة موجودة، انقر فوق "إزالة" ![الأيقونة "إزالة".](../../media/m365-cc-sc-remove-selection-icon.png) بجوار القيمة.

   بالنسبة للمستخدمين أو المجموعات، يمكنك استخدام معظم المعرفات (الاسم واسم العرض والاسم المستعار وعنوان البريد الإلكتروني واسم الحساب وما إلى ذلك)، ولكن يظهر اسم العرض المقابل في النتائج. بالنسبة للمستخدمين، أدخل علامة نجمية (\*) بحد ذاتها لمشاهدة كافة القيم المتوفرة.

   تستخدم القيم المتعددة في نفس الشرط منطق OR (على سبيل المثال، _\<recipient1\>_ أو _\<recipient2\>_). تستخدم الشروط المختلفة منطق AND (على سبيل المثال، _\<recipient1\>_ و _\<member of group 1\>_).

   - **استبعاد هؤلاء المستخدمين والمجموعات والمجالات**: لإضافة استثناءات للمستلمين الداخليين الذين ينطبق عليهم النهج (استثناءات المستلمين)، حدد هذا الخيار وقم بتكوين الاستثناءات. الإعدادات والسلوك تشبه تماما الشروط.

   > [!IMPORTANT]
   > لا تعد الشروط أو الاستثناءات المختلفة المتعددة مضافة؛ إنها شاملة. يتم تطبيق النهج _فقط_ على المستلمين الذين يتطابقون مع _كافة_ عوامل تصفية المستلمين المحددة. على سبيل المثال، يمكنك تكوين شرط عامل تصفية مستلم في النهج بالقيم التالية:
   >
   > - المستلم هو: romain@contoso.com
   > - المستلم هو عضو في: المديرين التنفيذيين
   >
   > يتم تطبيق النهج على romain@contoso.com _فقط_ إذا كان أيضا عضوا في مجموعات المديرين التنفيذيين. إذا لم يكن عضوا في المجموعة، فلن يتم تطبيق النهج عليه.
   >
   > وبالمثل، إذا كنت تستخدم عامل تصفية المستلم نفسه استثناء للنهج، فلن يتم تطبيق النهج على romain@contoso.com _فقط_ إذا كان أيضا عضوا في مجموعات المديرين التنفيذيين. إذا لم يكن عضوا في المجموعة، فإن النهج لا يزال ينطبق عليه.

   عند الانتهاء، انقر فوق **"التالي**".

5. في صفحة **إعدادات الحماية** التي تظهر، قم بتكوين الإعدادات التالية:
   - **حدد الإجراء الخاص بعناوين URL غير المعروفة التي يحتمل أن تكون ضارة في الرسائل**: حدد "**تشغيل**" لتمكين حماية الارتباطات خزينة للارتباطات في رسائل البريد الإلكتروني. إذا قمت بتشغيل هذا الإعداد، تتوفر الإعدادات التالية:
     - **تطبيق فحص URL في الوقت الحقيقي للارتباطات والارتباطات المشبوهة التي تشير إلى الملفات**: حدد هذا الخيار لتمكين المسح في الوقت الحقيقي للارتباطات في رسائل البريد الإلكتروني. إذا قمت بتشغيل هذا الإعداد، فهذا الإعداد متوفر:
       - **انتظر حتى يكتمل مسح URL قبل تسليم الرسالة**: حدد هذا الخيار لانتظار اكتمال مسح URL في الوقت الحقيقي قبل تسليم الرسالة.
     - **تطبيق ارتباطات خزينة إلى رسائل البريد الإلكتروني المرسلة داخل المؤسسة**: حدد هذا الخيار لتطبيق نهج الارتباطات خزينة على الرسائل بين المرسلين الداخليين والمستلمين الداخليين.
   - **حدد الإجراء الخاص بعناوين URL غير المعروفة أو التي يحتمل أن تكون ضارة داخل Microsoft Teams**: حدد "**تشغيل**" لتمكين حماية الارتباطات خزينة للارتباطات في Teams. لاحظ أن هذا الإعداد قد يستغرق ما يصل إلى 24 ساعة حتى يدخل حيز التنفيذ.

     > [!NOTE]
     > حاليا، لا تتوفر حماية الارتباطات خزينة Microsoft Teams في Microsoft 365 سحابة القطاع الحكومي High أو Microsoft 365 DoD.

   - **تعقب نقرات المستخدم**: اترك هذا الخيار محددا لتمكين نقرات المستخدم المتعقبة على عناوين URL في رسائل البريد الإلكتروني.
   - **اسمح للمستخدمين بالنقر فوق عنوان URL الأصلي**: قم بإلغاء تحديد هذا الخيار لمنع المستخدمين من النقر فوق عنوان URL الأصلي في [صفحات التحذير](safe-links.md#warning-pages-from-safe-links).
   - **لا تقم بإعادة كتابة عناوين URL التالية**: تسمح بالوصول إلى عناوين URL المحددة التي قد يتم حظرها بواسطة ارتباطات خزينة.

     في المربع، اكتب عنوان URL أو القيمة التي تريدها، ثم انقر فوق **"إضافة**". كرر هذه الخطوة عدة مرات حسب الضرورة.

     لإزالة إدخال موجود، انقر فوق ![الأيقونة "إزالة".](../../media/m365-cc-sc-remove-selection-icon.png) بجوار الإدخال.

     للحصول على بناء جملة الإدخال، راجع [بناء جملة الإدخال لقائمة "عدم إعادة كتابة عناوين URL التالية".](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list)

   للحصول على معلومات مفصلة حول هذه الإعدادات، راجع [خزينة إعدادات الارتباطات لرسائل البريد الإلكتروني](safe-links.md#safe-links-settings-for-email-messages) [وإعدادات ارتباطات خزينة Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).

   لمزيد من القيم الموصى بها لإعدادات النهج القياسية والضيقة، راجع [خزينة إعدادات نهج الارتباطات](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   عند الانتهاء، انقر فوق **"التالي**".

6. في صفحة **الإعلام** التي تظهر، حدد إحدى القيم التالية **لكيفية إعلام المستخدمين؟**:
   - **استخدام نص الإعلام الافتراضي**
   - **استخدم نص الإعلام المخصص**: إذا حددت هذه القيمة (لا يمكن أن يتجاوز الطول 200 حرف)، فستظهر الإعدادات التالية:
     - **استخدام المترجم من Microsoft للترجمة التلقائية**
     - **نص الإعلام المخصص**: أدخل نص الإعلام المخصص في هذا المربع.

   عند الانتهاء، انقر فوق **"التالي**".

7. في صفحة **المراجعة** التي تظهر، راجع الإعدادات. يمكنك تحديد **"تحرير"** في كل مقطع لتعديل الإعدادات داخل المقطع. أو يمكنك النقر فوق **"الخلف"** أو تحديد الصفحة المحددة في المعالج.

   عند الانتهاء، انقر فوق **"إرسال**".

8. في صفحة التأكيد التي تظهر، انقر فوق **"تم**".

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>استخدام مدخل Microsoft 365 Defender لعرض نهج الارتباطات خزينة

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "نهج** \> **مخاطر** القواعد \> **" خزينة الارتباطات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **ارتباطات خزينة**، استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **ارتباطات خزينة**، يتم عرض الخصائص التالية في قائمة نهج الارتباطات خزينة:
   - **الاسم**
   - **حاله**
   - **الاولويه**

3. عند تحديد نهج بالنقر فوق الاسم، يتم عرض إعدادات النهج في قائمة منبثقة.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>استخدام مدخل Microsoft 365 Defender لتعديل نهج ارتباطات خزينة

1. في مدخل Microsoft 365 Defender، انتقل **إلى قسم** \> نهج نهج **المخاطر** \> **& النهج** \> **خزينة الارتباطات**.

2. في صفحة **الارتباطات خزينة**، حدد نهجا من القائمة بالنقر فوق الاسم.

3. في القائمة المنبثقة لتفاصيل النهج التي تظهر، حدد **"تحرير"** في كل مقطع لتعديل الإعدادات داخل المقطع. لمزيد من المعلومات حول الإعدادات، راجع مدخل Microsoft 365 Defender السابق [لإنشاء قسم نهج الارتباطات خزينة](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) في هذه المقالة.

لتمكين نهج أو تعطيله أو تعيين ترتيب أولوية النهج، راجع الأقسام التالية.

### <a name="enable-or-disable-safe-links-policies"></a>تمكين نهج ارتباطات خزينة أو تعطيلها

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "نهج** \> **مخاطر** القواعد \> **" خزينة الارتباطات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **ارتباطات خزينة**، استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **الارتباطات خزينة**، حدد نهجا من القائمة بالنقر فوق الاسم.

3. في أعلى القائمة المنبثقة لتفاصيل النهج التي تظهر، سترى إحدى القيم التالية:
   - **إيقاف تشغيل النهج**: لتشغيل النهج، انقر فوق !["تشغيل الأيقونة".](../../media/m365-cc-sc-turn-on-off-icon.png) **تشغيل** .
   - **تم تشغيل النهج**: لإيقاف تشغيل النهج، انقر فوق !["إيقاف تشغيل الأيقونة".](../../media/m365-cc-sc-turn-on-off-icon.png) **إيقاف التشغيل**.

4. في مربع حوار التأكيد الذي يظهر، انقر فوق **"تشغيل** " أو **"إيقاف تشغيل**".

5. انقر فوق **"إغلاق** " في القائمة المنبثقة لتفاصيل النهج.

بالعودة إلى صفحة النهج الرئيسية، ستكون قيمة **الحالة** للنهج **قيد التشغيل** أو **متوقفة عن التشغيل**.

### <a name="set-the-priority-of-safe-links-policies"></a>تعيين أولوية نهج ارتباطات خزينة

بشكل افتراضي، يتم إعطاء الارتباطات خزينة أولوية تستند إلى الترتيب الذي تم إنشاؤها فيه (النهج الأحدث أقل أولوية من النهج الأقدم). يشير رقم الأولوية الأقل إلى أولوية أعلى للنهج (0 هو الأعلى)، وتتم معالجة النهج بترتيب الأولوية (تتم معالجة نهج الأولوية الأعلى قبل نهج الأولوية الدنيا). لا يمكن أن يكون لأي نهجين نفس الأولوية، وتتوقف معالجة النهج بعد تطبيق النهج الأول.

لتغيير أولوية النهج، انقر فوق **"زيادة الأولوية**" أو **"إنقاص الأولوية**" في خصائص النهج (لا يمكنك تعديل رقم **"الأولوية**" مباشرة في مدخل Microsoft 365 Defender). تغيير أولوية النهج أمر منطقي فقط إذا كان لديك نهج متعددة.

**ملاحظة**:

- في مدخل Microsoft 365 Defender، يمكنك تغيير أولوية نهج الارتباطات خزينة فقط بعد إنشائه. في PowerShell، يمكنك تجاوز الأولوية الافتراضية عند إنشاء قاعدة الارتباطات الآمنة (والتي يمكن أن تؤثر على أولوية القواعد الموجودة).
- تتم معالجة نهج الارتباطات خزينة بالترتيب الذي يتم عرضه به (النهج الأول له قيمة **الأولوية** 0). لمزيد من المعلومات حول ترتيب الأسبقية وكيفية تقييم نهج متعددة وتطبيقها، راجع [ترتيب حماية البريد الإلكتروني وأسبقيته](how-policies-and-protections-are-combined.md).

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "نهج** \> **مخاطر** القواعد \> **" خزينة الارتباطات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **ارتباطات خزينة**، استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **الارتباطات خزينة**، حدد نهجا من القائمة بالنقر فوق الاسم.

3. في أعلى القائمة المنبثقة لتفاصيل النهج التي تظهر، سترى **زيادة الأولوية** أو **إنقاص الأولوية** استنادا إلى قيمة الأولوية الحالية وعدد النهج المخصصة:
   - يحتوي النهج الذي يحتوي على قيمة **الأولوية** **0** على الخيار **"إنقاص الأولوية** " المتاح فقط.
   - يحتوي النهج الذي يحتوي على أقل قيمة **أولوية** (على سبيل المثال، **3**) على الخيار **"زيادة الأولوية** " المتاح فقط.
   - إذا كان لديك ثلاثة نهج أو أكثر، فإن النهج بين القيم ذات الأولوية الأعلى والدنيا تحتوي على كل من خيارات **"زيادة الأولوية** " و" **إنقاص الأولوية** " المتوفرة.

   انقر فوق ![أيقونة "زيادة الأولوية".](../../media/m365-cc-sc-increase-icon.png) **زيادة الأولوية** أو ![أيقونة](../../media/m365-cc-sc-decrease-icon.png) **"إنقاص الأولوية" "إنقاص الأولوية** " لتغيير قيمة **"الأولوية** ".

4. عند الانتهاء، انقر فوق **"إغلاق** " في القائمة المنبثقة لتفاصيل النهج.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>استخدام مدخل Microsoft 365 Defender لإزالة نهج الارتباطات خزينة

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "قواعد** \> \> **التهديد**" **خزينة الارتباطات** في قسم **"النهج**".

2. في صفحة **الارتباطات خزينة**، حدد نهجا من القائمة بالنقر فوق الاسم. في أعلى القائمة المنبثقة لتفاصيل النهج التي تظهر، انقر فوق ![أيقونة المزيد من الإجراءات.](../../media/m365-cc-sc-more-actions-icon.png) **المزيد من الإجراءات** \> ![حذف أيقونة](../../media/m365-cc-sc-delete-icon.png) نهج **حذف النهج**.

3. في مربع حوار التأكيد الذي يظهر، انقر فوق **"نعم**".

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>استخدام Exchange Online PowerShell أو EOP PowerShell المستقل لتكوين نهج ارتباطات خزينة

كما هو موضح سابقا، يتكون نهج الارتباطات خزينة من نهج ارتباطات آمنة وقاعدة ارتباطات آمنة.

في PowerShell، يظهر الفرق بين نهج الارتباطات الآمنة وقواعد الارتباطات الآمنة. يمكنك إدارة نهج الارتباطات الآمنة باستخدام **\*cmdlets -SafeLinksPolicy** ، ويمكنك إدارة قواعد الارتباطات الآمنة باستخدام **\*cmdlets -SafeLinksRule** .

- في PowerShell، يمكنك إنشاء نهج الارتباطات الآمنة أولا، ثم إنشاء قاعدة الارتباطات الآمنة التي تحدد النهج الذي تنطبق عليه القاعدة.
- في PowerShell، يمكنك تعديل الإعدادات في نهج الارتباطات الآمنة وقاعدة الارتباطات الآمنة بشكل منفصل.
- عند إزالة نهج ارتباطات آمنة من PowerShell، لا تتم إزالة قاعدة الارتباطات الآمنة المقابلة تلقائيا، والعكس بالعكس.

### <a name="use-powershell-to-create-safe-links-policies"></a>استخدام PowerShell لإنشاء نهج ارتباطات خزينة

إنشاء نهج ارتباطات خزينة في PowerShell هو عملية مكونة من خطوتين:

1. إنشاء نهج الارتباطات الآمنة.
2. إنشاء قاعدة الارتباطات الآمنة التي تحدد نهج الارتباطات الآمنة التي تنطبق عليها القاعدة.

> [!NOTE]
>
> - يمكنك إنشاء قاعدة ارتباطات آمنة جديدة وتعيين نهج ارتباطات آمنة موجودة وغير مقترنة إليها. لا يمكن إقران قاعدة الارتباطات الآمنة بأكثر من نهج ارتباطات آمنة واحد.
>
> - يمكنك تكوين الإعدادات التالية على نهج الارتباطات الآمنة الجديدة في PowerShell غير المتوفرة في مدخل Microsoft 365 Defender حتى بعد إنشاء النهج:
>   - إنشاء النهج الجديد كتعطيل (_ممكن_ `$false` على **New-SafeLinksRule** cmdlet).
>   - تعيين أولوية النهج أثناء الإنشاء (_الأولوية__\<Number\>_) على **New-SafeLinksRule** cmdlet).
>
> - لا يظهر نهج ارتباطات آمنة جديد تقوم بإنشائه في PowerShell في مدخل Microsoft 365 Defender حتى تقوم بتعيين النهج إلى قاعدة ارتباطات آمنة.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>الخطوة 1: استخدام PowerShell لإنشاء نهج ارتباطات آمنة

لإنشاء نهج ارتباطات آمنة، استخدم بناء الجملة هذا:

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSafeLinksForEmail <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-AllowClickThrough <$true | $false>] [-TrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - للحصول على تفاصيل حول بناء جملة الإدخال لاستخدامها للمعلمة _DoNotRewriteUrls_، راجع [بناء جملة الإدخال لقائمة "عدم إعادة كتابة عناوين URL التالية".](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list)
>
> - للحصول على بناء جملة إضافي يمكنك استخدامه للمعلمة _DoNotRewriteUrls_ عند تعديل نهج الارتباطات الآمنة الموجودة باستخدام **Cmdlet Set-SafeLinksPolicy** ، راجع القسم ["استخدام PowerShell" لتعديل نهج الارتباطات الآمنة](#use-powershell-to-modify-safe-links-policies) لاحقا في هذه المقالة.

ينشئ هذا المثال نهج ارتباطات آمنة يسمى Contoso All بالقيم التالية:

- تشغيل مسح URL وإعادة كتابته في رسائل البريد الإلكتروني.
- تشغيل مسح URL في Teams.
- قم بتشغيل المسح الضوئي في الوقت الحقيقي لعناوين URL التي تم النقر فوقها، بما في ذلك الارتباطات التي تم النقر فوقها والتي تشير إلى الملفات.
- انتظر حتى يكتمل مسح URL قبل تسليم الرسالة.
- تشغيل مسح URL وإعادة الكتابة للرسائل الداخلية.
- تعقب نقرات المستخدم المتعلقة بحماية الارتباطات خزينة (نحن لا نستخدم المعلمة _TrackUserClicks_، والقيمة الافتراضية هي $true).
- لا تسمح للمستخدمين بالنقر فوق عنوان URL الأصلي.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -EnableSafeLinksForEmail $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -AllowClickThrough $false
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>الخطوة 2: استخدام PowerShell لإنشاء قاعدة ارتباطات آمنة

لإنشاء قاعدة ارتباطات آمنة، استخدم بناء الجملة هذا:

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

ينشئ هذا المثال قاعدة ارتباطات آمنة تسمى Contoso All مع الشروط التالية:

- تقترن القاعدة بنهج الارتباطات الآمنة المسمى Contoso All.
- تنطبق القاعدة على كافة المستلمين في مجال contoso.com.
- نظرا لأننا لا نستخدم معلمة _الأولوية_ ، يتم استخدام الأولوية الافتراضية.
- يتم تمكين القاعدة (نحن لا نستخدم المعلمة _الممكنة_ ، والقيمة الافتراضية هي `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

ينشئ هذا المثال قاعدة ارتباطات آمنة مشابهة للمثال السابق، ولكن في هذا المثال، تنطبق القاعدة على المستلمين في كافة المجالات المقبولة في المؤسسة.

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs (Get-AcceptedDomain).Name
```

ينشئ هذا المثال قاعدة ارتباطات آمنة مشابهة بالأمثلة السابقة، ولكن في هذا المثال، تنطبق القاعدة على المستلمين في المجالات المحددة في ملف .csv.

```powershell
$Data = Import-Csv -Path "C:\Data\SafeLinksDomains.csv"
$SLDomains = $Data.Domains
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs $SLDomains
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>استخدام PowerShell لعرض نهج الارتباطات الآمنة

لعرض نهج الارتباطات الآمنة الموجودة، استخدم بناء الجملة التالي:

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

يقوم هذا المثال بإرجاع قائمة ملخصة لكافة نهج الارتباطات الآمنة.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

يرجع هذا المثال معلومات مفصلة لنهج الارتباطات الآمنة المسمى Contoso Executives.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>استخدام PowerShell لعرض قواعد الارتباطات الآمنة

لعرض قواعد الارتباطات الآمنة الموجودة، استخدم بناء الجملة التالي:

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

يقوم هذا المثال بإرجاع قائمة ملخصة لكافة قواعد الارتباطات الآمنة.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

لتصفية القائمة حسب القواعد الممكنة أو المعطلة، قم بتشغيل الأوامر التالية:

```PowerShell
Get-SafeLinksRule -State Disabled
```

```PowerShell
Get-SafeLinksRule -State Enabled
```

يرجع هذا المثال معلومات مفصلة لقاعدة الارتباطات الآمنة المسماة Contoso Executives.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>استخدام PowerShell لتعديل نهج الارتباطات الآمنة

لا يمكنك إعادة تسمية نهج ارتباطات آمنة في PowerShell (لا يحتوي **Cmdlet Set-SafeLinksPolicy** على معلمة _اسم_ ). عند إعادة تسمية نهج ارتباطات خزينة في مدخل Microsoft 365 Defender، فأنت تعيد تسمية _قاعدة_ الارتباطات الآمنة فقط.

الاعتبار الإضافي الوحيد لتعديل نهج الارتباطات الآمنة في PowerShell هو بناء الجملة المتوفر لمعلمة _DoNotRewriteUrls_ ( [القائمة "عدم إعادة كتابة عناوين URL التالية"](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)):

- لإضافة قيم ستحل محل أي إدخالات موجودة، استخدم بناء الجملة التالي: `"Entry1","Entry2,..."EntryN"`.
- لإضافة قيم أو إزالتها دون التأثير على إدخالات موجودة أخرى، استخدم بناء الجملة التالي: `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

وإلا، تتوفر نفس الإعدادات عند إنشاء نهج ارتباطات آمنة كما هو موضح في [الخطوة 1: استخدم PowerShell لإنشاء قسم نهج ارتباطات آمنة](#step-1-use-powershell-to-create-a-safe-links-policy) سابقا في هذه المقالة.

لتعديل نهج ارتباطات آمنة، استخدم بناء الجملة هذا:

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>استخدام PowerShell لتعديل قواعد الارتباطات الآمنة

الإعداد الوحيد غير المتوفر عند تعديل قاعدة ارتباطات آمنة في PowerShell هو المعلمة _الممكنة_ التي تسمح لك بإنشاء قاعدة معطلة. لتمكين قواعد الارتباطات الآمنة الموجودة أو تعطيلها، راجع القسم التالي.

وإلا، تتوفر نفس الإعدادات عند إنشاء قاعدة كما هو موضح في [الخطوة 2: استخدم PowerShell لإنشاء مقطع قاعدة ارتباطات آمنة](#step-2-use-powershell-to-create-a-safe-links-rule) سابقا في هذه المقالة.

لتعديل قاعدة ارتباطات آمنة، استخدم بناء الجملة هذا:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

يضيف هذا المثال كافة المجالات المقبولة في المؤسسة كشرط لقاعدة الارتباطات الآمنة المسماة Contoso All.

```powershell
Set-SafeLinksRule -Identity "Contoso All" -RecipientDomainIs (Get-AcceptedDomain).Name
```

يضيف هذا المثال المجالات من .csv المحددة كشرط إلى قاعدة الارتباطات الآمنة المسماة Contoso All.

```powershell
$Data = Import-Csv -Path "C:\Data\SafeLinksDomains.csv"
$SLDomains = $Data.Domains
Set-SafeLinksRule -Identity "Contoso All" -RecipientDomainIs $SLDomains
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>استخدام PowerShell لتمكين قواعد الارتباطات الآمنة أو تعطيلها

يؤدي تمكين قاعدة ارتباطات آمنة أو تعطيلها في PowerShell إلى تمكين نهج الارتباطات خزينة بأكمله أو تعطيله (قاعدة الارتباطات الآمنة ونهج الارتباطات الآمنة المعين).

لتمكين قاعدة ارتباطات آمنة أو تعطيلها في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

يعطل هذا المثال قاعدة الارتباطات الآمنة المسماة "قسم التسويق".

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

يمكن هذا المثال القاعدة نفسها.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Enable-SafeLinksRule](/powershell/module/exchange/enable-safelinksrule) و [Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>استخدام PowerShell لتعيين أولوية قواعد الارتباطات الآمنة

أعلى قيمة أولوية يمكنك تعيينها على قاعدة هي 0. تعتمد أقل قيمة يمكنك تعيينها على عدد القواعد. على سبيل المثال، إذا كان لديك خمس قواعد، يمكنك استخدام قيم الأولوية من 0 إلى 4. يمكن أن يكون لتغيير أولوية قاعدة موجودة تأثير متتالي على قواعد أخرى. على سبيل المثال، إذا كان لديك خمس قواعد مخصصة (الأولويات من 0 إلى 4)، وقمت بتغيير أولوية قاعدة إلى 2، يتم تغيير القاعدة الموجودة ذات الأولوية 2 إلى الأولوية 3، ويتم تغيير القاعدة ذات الأولوية 3 إلى الأولوية 4.

لتعيين أولوية قاعدة ارتباطات آمنة في PowerShell، استخدم بناء الجملة التالي:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

يعين هذا المثال أولوية القاعدة المسماة "قسم التسويق" إلى 2. يتم تقليل كافة القواعد الموجودة التي لها أولوية أقل من أو تساوي 2 بمقدار 1 (يتم زيادة أرقام الأولوية الخاصة بها بمقدار 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> لتعيين أولوية قاعدة جديدة عند إنشائها، استخدم المعلمة _Priority_ على **New-SafeLinksRule** cmdlet بدلا من ذلك.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>استخدام PowerShell لإزالة نهج الارتباطات الآمنة

عند استخدام PowerShell لإزالة نهج ارتباطات آمنة، لا تتم إزالة قاعدة الارتباطات الآمنة المقابلة.

لإزالة نهج ارتباطات آمنة في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

يزيل هذا المثال نهج الارتباطات الآمنة المسمى "قسم التسويق".

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>استخدام PowerShell لإزالة قواعد الارتباطات الآمنة

عند استخدام PowerShell لإزالة قاعدة ارتباطات آمنة، لا تتم إزالة نهج الارتباطات الآمنة المقابلة.

لإزالة قاعدة ارتباطات آمنة في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

يزيل هذا المثال قاعدة الارتباطات الآمنة المسماة "قسم التسويق".

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

للتحقق من أن الارتباطات خزينة تقوم بمسح الرسائل ضوئيا، تحقق من تقارير Microsoft Defender لـ Office 365 المتوفرة. لمزيد من المعلومات، راجع [عرض تقارير Defender لـ Office 365](view-reports-for-mdo.md) و["استخدام المستكشف" في مدخل Microsoft 365 Defender](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>كيف تعرف أن هذه الإجراءات تعمل؟

للتحقق من إنشاء نهج ارتباطات خزينة أو تعديلها أو إزالتها بنجاح، قم بأي من الخطوات التالية:

- في صفحة **الارتباطات خزينة** في مدخل Microsoft 365 Defender في <https://security.microsoft.com/safelinksv2>، تحقق من قائمة النهج وقيم **الحالة** وقيم **الأولوية** الخاصة بها. لعرض المزيد من التفاصيل، حدد النهج من القائمة، واعرض التفاصيل في القائمة المنبثقة.

- في Exchange Online PowerShell أو Exchange Online Protection PowerShell، استبدل \<Name\> باسم النهج أو القاعدة، وقم بتشغيل الأمر التالي، وتحقق من الإعدادات:

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
