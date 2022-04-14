---
title: إعداد نهج المرفقات خزينة في Microsoft Defender لـ Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 078eb946-819a-4e13-8673-fe0c0ad3a775
ms.collection:
- M365-security-compliance
description: تعرف على كيفية تعريف نهج المرفقات خزينة لحماية مؤسستك من الملفات الضارة في البريد الإلكتروني.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 811730ce12af80b2ac8df7db068b63b96b856bbd
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847060"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>إعداد نهج المرفقات خزينة في Microsoft Defender لـ Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 1 والخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> هذه المقالة مخصصة لعملاء الأعمال الذين لديهم [Microsoft Defender لـ Office 365](whats-new-in-defender-for-office-365.md). إذا كنت مستخدما منزليا تبحث عن معلومات حول مسح المرفقات في Outlook، فراجع [الأمان المتقدم Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

خزينة المرفقات هي ميزة في [Microsoft Defender لـ Office 365](whats-new-in-defender-for-office-365.md) تستخدم بيئة ظاهرية للتحقق من المرفقات في رسائل البريد الإلكتروني الواردة بعد مسحها ضوئيا بواسطة [الحماية من البرامج الضارة في Exchange Online Protection (EOP)،](anti-malware-protection.md) ولكن قبل تسليمها إلى المستلمين. لمزيد من المعلومات، راجع [خزينة المرفقات في Microsoft Defender لـ Office 365](safe-attachments.md).

على الرغم من عدم وجود نهج افتراضي خزينة المرفقات، يوفر نهج الأمان المعين مسبقا **للحماية المضمنة** حماية المرفقات خزينة لكافة المستلمين (المستخدمون الذين لم يتم تعريفهم في نهج المرفقات خزينة المخصصة). لمزيد من المعلومات، راجع [نهج الأمان التي تم تعيينها مسبقا في EOP Microsoft Defender لـ Office 365](preset-security-policies.md). يمكنك أيضا استخدام الإجراءات الواردة في هذه المقالة لإنشاء نهج مرفقات خزينة تنطبق على مستخدمين أو مجموعات أو مجالات معينة.

يمكنك تكوين نهج المرفقات خزينة في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell للمؤسسات Microsoft 365 المؤهلة التي لها علب بريد في Exchange Online؛ وEOP PowerShell مستقل للمؤسسات بدون Exchange Online علب البريد، ولكن مع اشتراكات Defender لـ Office 365 الإضافية).

العناصر الأساسية لنهج المرفقات خزينة هي:

- **نهج المرفقات الآمن**: يحدد الإجراءات الخاصة بالكشف عن البرامج الضارة غير المعروفة، وما إذا كنت تريد إرسال الرسائل التي تحتوي على مرفقات برامج ضارة إلى عنوان بريد إلكتروني محدد، وما إذا كنت تريد تسليم الرسائل إذا تعذر إكمال مسح المرفقات خزينة.
- **قاعدة المرفقات الآمنة**: تحدد الأولوية وعوامل تصفية المستلم (من ينطبق عليه النهج).

لا يكون الفرق بين هذين العنصرين واضحا عند إدارة نهج المرفقات خزينة في مدخل Microsoft 365 Defender:

- عند إنشاء نهج مرفقات خزينة، فأنت تقوم بالفعل بإنشاء قاعدة مرفقات آمنة ونهج المرفقات الآمنة المقترن في نفس الوقت باستخدام نفس الاسم لكليهما.
- عند تعديل نهج خزينة المرفقات، تقوم الإعدادات المتعلقة بالاسم والأولوية والممكن أو المعطل وعوامل تصفية المستلم بتعديل قاعدة المرفقات الآمنة. تعدل كافة الإعدادات الأخرى نهج المرفقات الآمنة المقترن.
- عند إزالة نهج مرفقات خزينة، تتم إزالة قاعدة المرفقات الآمنة ونهج المرفقات الآمنة المقترنة.

في Exchange Online PowerShell أو EOP PowerShell المستقل، يمكنك إدارة النهج والقاعدة بشكل منفصل. لمزيد من المعلومات، راجع [استخدام Exchange Online PowerShell أو EOP PowerShell المستقل لتكوين قسم نهج المرفقات خزينة](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) لاحقا في هذه المقالة.

> [!NOTE]
> في منطقة الإعدادات العمومية لإعدادات خزينة المرفقات، يمكنك تكوين الميزات التي لا تعتمد على نهج خزينة المرفقات. للحصول على الإرشادات[، راجع "تشغيل مرفقات خزينة للمستندات SharePoint OneDrive Microsoft Teams والمستندات](turn-on-mdo-for-spo-odb-and-teams.md) [خزينة في Microsoft 365 E5](safe-docs.md)".

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

- للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع [الاتصال إلى Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- تحتاج إلى أذونات قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - لإنشاء نهج المرفقات وتعديلها وحذفها خزينة، يجب أن تكون عضوا في مجموعات دور مسؤول **الأمان** أو **إدارة المؤسسة** **في مدخل Microsoft 365 Defender** وعضوا في مجموعة دور **إدارة المؤسسة** في Exchange Online.
  - للوصول للقراءة فقط إلى نهج المرفقات خزينة، يجب أن تكون عضوا في مجموعات دور **القارئ العمومي** أو **قارئ الأمان** في مدخل Microsoft 365 Defender.

  لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md) [والأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  **الملاحظات**:

  - إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender _والأذونات_ للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع ["حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md)".
  - كما توفر مجموعة دور **إدارة المؤسسة للعرض فقط** في [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) إمكانية الوصول للقراءة فقط إلى الميزة.

- للحصول على الإعدادات الموصى بها لنهج المرفقات خزينة، راجع [إعدادات المرفقات خزينة](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- السماح بما يصل إلى 30 دقيقة لتطبيق نهج جديد أو محدث.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>استخدام مدخل Microsoft 365 Defender لإنشاء نهج المرفقات خزينة

يؤدي إنشاء نهج مرفقات خزينة مخصص في مدخل Microsoft 365 Defender إلى إنشاء قاعدة المرفقات الآمنة ونهج المرفقات الآمنة المقترنة في نفس الوقت باستخدام نفس الاسم لكليهما.

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "قواعد** \> \> **التهديد**" **خزينة المرفقات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، انقر فوق !["إنشاء أيقونة".](../../media/m365-cc-sc-create-icon.png) **إنشاء**.

3. يفتح معالج النهج. في صفحة **"الاسم" في النهج** ، قم بتكوين الإعدادات التالية:
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

   - **استبعاد هؤلاء المستخدمين والمجموعات والمجالات**: لإضافة استثناءات للمستلمين الداخليين الذين ينطبق عليهم النهج (استثناءات recpient)، حدد هذا الخيار وقم بتكوين الاستثناءات. الإعدادات والسلوك تشبه تماما الشروط.

   عند الانتهاء، انقر فوق **"التالي**".

5. في صفحة **الإعدادات**، قم بتكوين الإعدادات التالية:

   - **خزينة استجابة البرامج الضارة غير المعروفة للمرفقات**: حدد إحدى القيم التالية:
     - **إيقاف التشغيل**: عادة، لا نوصي بهذه القيمة.
     - **رصد**
     - **الكتلة**: هذه هي القيمة الافتراضية والقيمة الموصى بها في [نهج الأمان القياسية والضيقة المحددة مسبقا](preset-security-policies.md).
     - **استبدال**
     - **التسليم الديناميكي (ميزة المعاينة)**

     يتم شرح هذه القيم في [إعدادات نهج المرفقات خزينة](safe-attachments.md#safe-attachments-policy-settings).

   - **نهج العزل**: حدد نهج العزل الذي ينطبق على الرسائل التي تم عزلها بواسطة مرفقات خزينة (**حظر** أو **استبدال** أو **تسليم ديناميكي**). تحدد نهج العزل ما يمكن للمستخدمين القيام به للرسائل المعزولة، وما إذا كان المستخدمون يتلقون إعلامات العزل. لمزيد من المعلومات، راجع [نهج العزل](quarantine-policies.md).

     تعني القيمة الفارغة أنه يتم استخدام نهج العزل الافتراضي (AdminOnlyAccessPolicy للكشف عن البريد الإلكتروني بواسطة خزينة المرفقات). عندما تقوم لاحقا بتحرير نهج خزينة المرفقات أو عرض الإعدادات، يظهر اسم نهج العزل الافتراضي.

   - **إعادة توجيه الرسائل التي تحتوي على مرفقات تم الكشف عنها**: إذا حددت **"تمكين إعادة التوجيه**"، يمكنك تحديد عنوان بريد إلكتروني في **"إرسال الرسائل" يحتوي على مرفقات محظورة أو مراقبة أو تم استبدالها إلى مربع عنوان البريد الإلكتروني المحدد** لإرسال الرسائل التي تحتوي على مرفقات البرامج الضارة للتحليل والتحقيق.

     التوصية بإعدادات النهج القياسية والضيقة هي تمكين إعادة التوجيه. لمزيد من المعلومات، راجع [خزينة إعدادات المرفقات](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

   - **تطبيق استجابة الكشف عن المرفقات خزينة إذا تعذر إكمال الفحص (المهلة أو الأخطاء):** يتم اتخاذ الإجراء المحدد بواسطة **خزينة استجابة البرامج الضارة غير المعروفة للمرفقات** على الرسائل حتى عندما يتعذر إكمال مسح المرفقات خزينة. إذا حددت هذا الخيار، فحدد دائما **تمكين إعادة التوجيه** وحدد عنوان بريد إلكتروني لإرسال الرسائل التي تحتوي على مرفقات البرامج الضارة. وإلا، فقد يتم فقدان الرسائل.

   عند الانتهاء، انقر فوق **"التالي**".

6. في صفحة **المراجعة** التي تظهر، راجع الإعدادات. يمكنك تحديد **"تحرير"** في كل مقطع لتعديل الإعدادات داخل المقطع. أو يمكنك النقر فوق **"الخلف"** أو تحديد الصفحة المحددة في المعالج.

   عند الانتهاء، انقر فوق **"إرسال**".

7. في صفحة التأكيد التي تظهر، انقر فوق **"تم**".

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>استخدام مدخل Microsoft 365 Defender لعرض نهج المرفقات خزينة

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "قواعد** \> \> **التهديد**" **خزينة المرفقات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، يتم عرض الخصائص التالية في قائمة النهج:
   - **الاسم**
   - **حاله**
   - **الاولويه**

3. عند تحديد نهج بالنقر فوق الاسم، يتم عرض إعدادات النهج في قائمة منبثقة.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>استخدام مدخل Microsoft 365 Defender لتعديل نهج المرفقات خزينة

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "قواعد** \> \> **التهديد**" **خزينة المرفقات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، حدد نهجا من القائمة بالنقر فوق الاسم.

3. في القائمة المنبثقة لتفاصيل النهج التي تظهر، حدد **"تحرير"** في كل مقطع لتعديل الإعدادات داخل المقطع. لمزيد من المعلومات حول الإعدادات، راجع [مدخل Microsoft 365 Defender لإنشاء قسم نهج المرفقات خزينة](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) سابقا في هذه المقالة.

لتمكين نهج أو تعطيله أو تعيين ترتيب أولوية النهج، راجع الأقسام التالية.

### <a name="enable-or-disable-safe-attachments-policies"></a>تمكين نهج المرفقات خزينة أو تعطيلها

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "قواعد** \> \> **التهديد**" **خزينة المرفقات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، حدد نهجا من القائمة بالنقر فوق الاسم.

3. في أعلى القائمة المنبثقة لتفاصيل النهج التي تظهر، سترى إحدى القيم التالية:
   - **إيقاف تشغيل النهج**: لتشغيل النهج، انقر فوق !["تشغيل الأيقونة".](../../media/m365-cc-sc-turn-on-off-icon.png) **تشغيل** .
   - **تم تشغيل النهج**: لإيقاف تشغيل النهج، انقر فوق !["إيقاف تشغيل الأيقونة".](../../media/m365-cc-sc-turn-on-off-icon.png) **إيقاف التشغيل**.

4. في مربع حوار التأكيد الذي يظهر، انقر فوق **"تشغيل** " أو **"إيقاف تشغيل**".

5. انقر فوق **"إغلاق** " في القائمة المنبثقة لتفاصيل النهج.

بالعودة إلى صفحة النهج الرئيسية، ستكون قيمة **الحالة** للنهج **قيد التشغيل** أو **متوقفة عن التشغيل**.

### <a name="set-the-priority-of-safe-attachments-policies"></a>تعيين أولوية نهج المرفقات خزينة

بشكل افتراضي، يتم إعطاء نهج المرفقات خزينة أولوية تستند إلى الترتيب الذي تم إنشاؤها فيه (النهج الأحدث هي أولوية أقل من النهج الأقدم). يشير رقم الأولوية الأقل إلى أولوية أعلى للنهج (0 هو الأعلى)، وتتم معالجة النهج بترتيب الأولوية (تتم معالجة نهج الأولوية الأعلى قبل نهج الأولوية الدنيا). لا يمكن أن يكون لأي نهجين نفس الأولوية، وتتوقف معالجة النهج بعد تطبيق النهج الأول.

لمزيد من المعلومات حول ترتيب الأسبقية وكيفية تقييم نهج متعددة وتطبيقها، راجع [ترتيب حماية البريد الإلكتروني وأسبقيته](how-policies-and-protections-are-combined.md).

خزينة يتم عرض نهج المرفقات بالترتيب الذي تتم معالجتها به (النهج الأول له قيمة **الأولوية** 0).

**ملاحظة**: في مدخل Microsoft 365 Defender، يمكنك تغيير أولوية نهج المرفقات خزينة فقط بعد إنشائه. في PowerShell، يمكنك تجاوز الأولوية الافتراضية عند إنشاء قاعدة المرفق الآمن (والتي يمكن أن تؤثر على أولوية القواعد الموجودة).

لتغيير أولوية النهج، انقر فوق **"زيادة الأولوية**" أو **"إنقاص الأولوية**" في خصائص النهج (لا يمكنك تعديل رقم **"الأولوية**" مباشرة في مدخل Microsoft 365 Defender). تغيير أولوية النهج أمر منطقي فقط إذا كان لديك نهج متعددة.

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج التعاون** \> & البريد الإلكتروني **" & "قواعد** \> \> **التهديد"** **خزينة المرفقات** في قسم **"النهج**".

2. في صفحة **خزينة المرفقات**، حدد نهجا من القائمة بالنقر فوق الاسم.

3. في أعلى القائمة المنبثقة لتفاصيل النهج التي تظهر، سترى **زيادة الأولوية** أو **إنقاص الأولوية** استنادا إلى قيمة الأولوية الحالية وعدد النهج:
   - يحتوي النهج الذي يحتوي على قيمة **الأولوية** **0** على الخيار **"إنقاص الأولوية** " المتاح فقط.
   - يحتوي النهج الذي يحتوي على أقل قيمة **أولوية** (على سبيل المثال، **3**) على الخيار **"زيادة الأولوية** " المتاح فقط.
   - إذا كان لديك ثلاثة نهج أو أكثر، فإن النهج بين القيم ذات الأولوية الأعلى والدنيا تحتوي على كل من خيارات **"زيادة الأولوية** " و" **إنقاص الأولوية** " المتوفرة.

   انقر فوق ![أيقونة "زيادة الأولوية".](../../media/m365-cc-sc-increase-icon.png) **زيادة الأولوية** أو ![أيقونة](../../media/m365-cc-sc-decrease-icon.png) **"إنقاص الأولوية" "إنقاص الأولوية** " لتغيير قيمة **"الأولوية** ".

4. عند الانتهاء، انقر فوق **"إغلاق** " في القائمة المنبثقة لتفاصيل النهج.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>استخدام مدخل Microsoft 365 Defender لإزالة نهج المرفقات خزينة

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "قواعد** \> \> **التهديد**" **خزينة المرفقات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، حدد نهجا مخصصا من القائمة بالنقر فوق اسم النهج.

3. في أعلى القائمة المنبثقة لتفاصيل النهج التي تظهر، انقر فوق ![أيقونة المزيد من الإجراءات.](../../media/m365-cc-sc-more-actions-icon.png) **المزيد من الإجراءات** \> ![حذف أيقونة](../../media/m365-cc-sc-delete-icon.png) نهج **حذف النهج**.

4. في مربع حوار التأكيد الذي يظهر، انقر فوق **"نعم**".

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>استخدام Exchange Online PowerShell أو EOP PowerShell المستقل لتكوين نهج المرفقات خزينة

كما هو موضح سابقا، يتكون نهج المرفقات خزينة من نهج مرفق آمن وقاعدة مرفق آمنة.

في PowerShell، يكون الفرق بين نهج المرفقات الآمنة وقواعد المرفقات الآمنة واضحا. يمكنك إدارة نهج المرفقات الآمنة باستخدام **\*cmdlets -SafeAttachmentPolicy** ، وتدير قواعد المرفقات الآمنة باستخدام **\*cmdlets -SafeAttachmentRule** .

- في PowerShell، يمكنك إنشاء نهج المرفق الآمن أولا، ثم إنشاء قاعدة المرفق الآمنة التي تحدد النهج الذي تنطبق عليه القاعدة.
- في PowerShell، يمكنك تعديل الإعدادات في نهج المرفق الآمن وقاعدة المرفقات الآمنة بشكل منفصل.
- عند إزالة نهج مرفق آمن من PowerShell، لا تتم إزالة قاعدة المرفقات الآمنة المقابلة تلقائيا، والعكس بالعكس.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>استخدام PowerShell لإنشاء نهج المرفقات خزينة

إنشاء نهج مرفقات خزينة في PowerShell هو عملية من خطوتين:

1. إنشاء نهج المرفق الآمن.
2. إنشاء قاعدة المرفقات الآمنة التي تحدد نهج المرفق الآمن الذي تنطبق عليه القاعدة.

 **الملاحظات**:

- يمكنك إنشاء قاعدة مرفق آمنة جديدة وتعيين نهج مرفق آمن موجود غير مقترن إليها. لا يمكن إقران قاعدة المرفقات الآمنة بأكثر من نهج مرفق آمن واحد.

- يمكنك تكوين الإعدادات التالية على نهج المرفقات الآمنة الجديدة في PowerShell غير المتوفرة في مدخل Microsoft 365 Defender حتى بعد إنشاء النهج:
  - إنشاء النهج الجديد كتعطيل (_ممكن_ `$false` على **New-SafeAttachmentRule** cmdlet).
  - تعيين أولوية النهج أثناء الإنشاء (_الأولوية__\<Number\>_) على **New-SafeAttachmentRule** cmdlet).

- لا يظهر نهج مرفق آمن جديد تقوم بإنشائه في PowerShell في مدخل Microsoft 365 Defender حتى تقوم بتعيين النهج إلى قاعدة مرفق آمنة.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>الخطوة 1: استخدام PowerShell لإنشاء نهج مرفق آمن

لإنشاء نهج مرفق آمن، استخدم بناء الجملة هذا:

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

ينشئ هذا المثال نهج مرفق آمن يسمى Contoso All بالقيم التالية:

- حظر الرسائل التي تم العثور عليها لتحتوي على برامج ضارة عن طريق مسح المستندات خزينة (نحن لا نستخدم معلمة _الإجراء_، والقيمة الافتراضية هي `Block`).
- يتم استخدام [نهج العزل](quarantine-policies.md) الافتراضي (AdminOnlyAccessPolicy)، لأننا لا نستخدم معلمة _QuarantineTag_ .
- يتم تمكين إعادة التوجيه، ويتم إرسال الرسائل التي وجدت أنها تحتوي على برامج ضارة إلى sec-ops@contoso.com للتحليل والتحقيق.
- إذا لم يكن مسح المرفقات خزينة متوفرا أو واجه أخطاء، فلا تقم بتسليم الرسالة (نحن لا نستخدم المعلمة _ActionOnError_، والقيمة الافتراضية هي `$true`).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> للحصول على إرشادات مفصلة لتحديد [نهج العزل](quarantine-policies.md) لاستخدامه في نهج مرفق آمن، راجع [استخدام PowerShell لتحديد نهج العزل في نهج المرفقات خزينة](quarantine-policies.md#safe-attachments-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>الخطوة 2: استخدام PowerShell لإنشاء قاعدة مرفق آمنة

لإنشاء قاعدة مرفق آمنة، استخدم بناء الجملة هذا:

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

ينشئ هذا المثال قاعدة مرفق آمنة تسمى Contoso All مع الشروط التالية:

- تقترن القاعدة بنهج المرفق الآمن المسمى Contoso All.
- تنطبق القاعدة على كافة المستلمين في مجال contoso.com.
- نظرا لأننا لا نستخدم معلمة _الأولوية_ ، يتم استخدام الأولوية الافتراضية.
- يتم تمكين القاعدة (نحن لا نستخدم المعلمة _الممكنة_ ، والقيمة الافتراضية هي `$true`).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>استخدام PowerShell لعرض نهج المرفقات الآمنة

لعرض نهج المرفقات الآمنة الموجودة، استخدم بناء الجملة التالي:

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

يقوم هذا المثال بإرجاع قائمة ملخصة لكافة نهج المرفقات الآمنة.

```PowerShell
Get-SafeAttachmentPolicy
```

يرجع هذا المثال معلومات مفصلة لنهج المرفق الآمن المسمى Contoso Executives.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>استخدام PowerShell لعرض قواعد المرفقات الآمنة

لعرض قواعد المرفقات الآمنة الموجودة، استخدم بناء الجملة التالي:

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

يقوم هذا المثال بإرجاع قائمة ملخصة لكافة قواعد المرفقات الآمنة.

```PowerShell
Get-SafeAttachmentRule
```

لتصفية القائمة حسب القواعد الممكنة أو المعطلة، قم بتشغيل الأوامر التالية:

```PowerShell
Get-SafeAttachmentRule -State Disabled
```

```PowerShell
Get-SafeAttachmentRule -State Enabled
```

يرجع هذا المثال معلومات مفصلة لقاعدة المرفقات الآمنة المسماة Contoso Executives.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>استخدام PowerShell لتعديل نهج المرفقات الآمنة

لا يمكنك إعادة تسمية نهج مرفق آمن في PowerShell (لا يحتوي **Cmdlet Set-SafeAttachmentPolicy** على معلمة _اسم_ ). عند إعادة تسمية نهج مرفقات خزينة في مدخل Microsoft 365 Defender، فأنت تعيد تسمية _قاعدة_ المرفقات الآمنة فقط.

بخلاف ذلك، تتوفر نفس الإعدادات عند إنشاء نهج مرفق آمن كما هو موضح في [الخطوة 1: استخدم PowerShell لإنشاء مقطع نهج مرفق آمن](#step-1-use-powershell-to-create-a-safe-attachment-policy) سابقا في هذه المقالة.

لتعديل نهج مرفق آمن، استخدم بناء الجملة هذا:

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> للحصول على إرشادات مفصلة لتحديد [نهج العزل](quarantine-policies.md) لاستخدامه في نهج مرفق آمن، راجع [استخدام PowerShell لتحديد نهج العزل في نهج المرفقات خزينة](quarantine-policies.md#safe-attachments-policies-in-powershell).

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>استخدام PowerShell لتعديل قواعد المرفقات الآمنة

الإعداد الوحيد غير المتوفر عند تعديل قاعدة مرفق آمنة في PowerShell هو المعلمة _الممكنة_ التي تسمح لك بإنشاء قاعدة معطلة. لتمكين قواعد المرفقات الآمنة الموجودة أو تعطيلها، راجع القسم التالي.

بخلاف ذلك، تتوفر نفس الإعدادات عند إنشاء قاعدة كما هو موضح في [الخطوة 2: استخدم PowerShell لإنشاء مقطع قاعدة مرفق آمن](#step-2-use-powershell-to-create-a-safe-attachment-rule) سابقا في هذه المقالة.

لتعديل قاعدة مرفق آمنة، استخدم بناء الجملة هذا:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>استخدام PowerShell لتمكين قواعد المرفقات الآمنة أو تعطيلها

يؤدي تمكين قاعدة مرفق آمنة أو تعطيلها في PowerShell إلى تمكين نهج المرفقات خزينة بأكمله أو تعطيله (قاعدة المرفقات الآمنة ونهج المرفقات الآمنة المعين).

لتمكين قاعدة مرفق آمنة أو تعطيلها في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

يقوم هذا المثال بتعطيل قاعدة المرفقات الآمنة المسماة "قسم التسويق".

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

يمكن هذا المثال القاعدة نفسها.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Enable-SafeAttachmentRule](/powershell/module/exchange/enable-safeattachmentrule) و [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>استخدام PowerShell لتعيين أولوية قواعد المرفقات الآمنة

أعلى قيمة أولوية يمكنك تعيينها على قاعدة هي 0. تعتمد أقل قيمة يمكنك تعيينها على عدد القواعد. على سبيل المثال، إذا كان لديك خمس قواعد، يمكنك استخدام قيم الأولوية من 0 إلى 4. يمكن أن يكون لتغيير أولوية قاعدة موجودة تأثير متتالي على قواعد أخرى. على سبيل المثال، إذا كان لديك خمس قواعد مخصصة (الأولويات من 0 إلى 4)، وقمت بتغيير أولوية قاعدة إلى 2، يتم تغيير القاعدة الموجودة ذات الأولوية 2 إلى الأولوية 3، ويتم تغيير القاعدة ذات الأولوية 3 إلى الأولوية 4.

لتعيين أولوية قاعدة مرفق آمنة في PowerShell، استخدم بناء الجملة التالي:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

يعين هذا المثال أولوية القاعدة المسماة "قسم التسويق" إلى 2. يتم تقليل كافة القواعد الموجودة التي لها أولوية أقل من أو تساوي 2 بمقدار 1 (يتم زيادة أرقام الأولوية الخاصة بها بمقدار 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**ملاحظة**: لتعيين أولوية قاعدة جديدة عند إنشائها، استخدم معلمة _الأولوية_ على **New-SafeAttachmentRule** cmdlet بدلا من ذلك.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>استخدام PowerShell لإزالة نهج المرفقات الآمنة

عند استخدام PowerShell لإزالة نهج مرفق آمن، لا تتم إزالة قاعدة المرفقات الآمنة المقابلة.

لإزالة نهج مرفق آمن في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

يزيل هذا المثال نهج المرفق الآمن المسمى "قسم التسويق".

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>استخدام PowerShell لإزالة قواعد المرفقات الآمنة

عند استخدام PowerShell لإزالة قاعدة مرفق آمنة، لا تتم إزالة نهج المرفق الآمن المقابل.

لإزالة قاعدة مرفق آمنة في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

يزيل هذا المثال قاعدة المرفقات الآمنة المسماة "قسم التسويق".

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>كيف تعرف أن هذه الإجراءات تعمل؟

للتحقق من إنشاء نهج المرفقات أو تعديلها أو إزالتها بنجاح خزينة، قم بأي من الخطوات التالية:

- في صفحة **خزينة المرفقات** في مدخل Microsoft 365 Defender في <https://security.microsoft.com/safeattachmentv2>، تحقق من قائمة النهج وقيم **الحالة** وقيم **الأولوية** الخاصة بها. لعرض مزيد من التفاصيل، حدد النهج من القائمة بالنقر فوق الاسم، وعرض التفاصيل في القائمة المنبثقة.

- في Exchange Online PowerShell أو Exchange Online Protection PowerShell، استبدل \<Name\> باسم النهج أو القاعدة، وقم بتشغيل الأمر التالي، وتحقق من الإعدادات:

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

للتحقق من أن خزينة المرفقات تقوم بمسح الرسائل ضوئيا، تحقق من تقارير Defender لـ Office 365 المتوفرة. لمزيد من المعلومات، راجع [عرض تقارير Defender لـ Office 365](view-reports-for-mdo.md) و["استخدام المستكشف" في مدخل Microsoft 365 Defender](threat-explorer.md).
