---
title: إعداد خزينة المرفقات في Microsoft Defender Office 365
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
description: تعرف على كيفية تعريف خزينة المرفقات لحماية مؤسستك من الملفات الضارة في البريد الإلكتروني.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4cc0f2e3e87c288383880ba5b69f3b6b5d303c40
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63570542"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>إعداد خزينة المرفقات في Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> هذه المقالة مخصصة لعملاء الأعمال الذين لديهم [Microsoft Defender Office 365](whats-new-in-defender-for-office-365.md). إذا كنت مستخدما منزليا تبحث عن معلومات حول فحص المرفقات في Outlook، فاطلع على الأمان [المتقدم Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

خزينة المرفقات هي ميزة في [Microsoft Defender ل Office 365](whats-new-in-defender-for-office-365.md) تستخدم بيئة ظاهرية للتحقق من المرفقات في رسائل البريد الإلكتروني الواردة بعد فحصها ضوئيا بواسطة الحماية من البرامج الضارة في [Exchange Online Protection (EOP)،](anti-malware-protection.md) ولكن قبل تسليمها إلى المستلمين. لمزيد من المعلومات، [راجع خزينة المرفقات في Microsoft Defender Office 365](safe-attachments.md).

على الرغم من عدم وجود نهج خزينة مرفقات افتراضي، إلا أن نهج الأمان  المضمن للحماية المسبقة يوفر خزينة حماية المرفقات لجميع المستلمين (المستخدمون غير المحددين في نهج مرفقات خزينة المخصصة). لمزيد من المعلومات، راجع [سياسات الأمان التي تم الإعداد المسبق لها في EOP و Microsoft Defender Office 365](preset-security-policies.md). يمكنك أيضا استخدام الإجراءات في هذه المقالة لإنشاء خزينة المرفقات التي تنطبق على مستخدمين معينين أو مجموعة أو مجالات معينة.

يمكنك تكوين خزينة سياسات المرفقات في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell لمنظمات Microsoft 365 المؤهلة التي لها علب بريد في Exchange Online؛ EOP PowerShell مستقل ل المؤسسات التي ليس لها Exchange Online علب البريد، ولكن باستخدام Defender Office 365 الإضافية).

العناصر الأساسية لنمص خزينة المرفقات هي:

- نهج المرفق **الآمن: يحدد** إجراءات عمليات الكشف عن البرامج الضارة غير المعروفة، وما إذا كنت تريد إرسال الرسائل التي بها مرفقات البرامج الضارة إلى عنوان بريد إلكتروني محدد، وما إذا كنت تريد تسليم الرسائل إذا خزينة لا يمكن إكمال فحص المرفقات.
- **قاعدة المرفق الآمن**: تحدد عوامل تصفية الأولوية والمستلم (الشخص الذي ينطبق عليه النهج).

لا يكون الفرق بين هذين العنصرين واضحا عند إدارة خزينة المرفقات في مدخل Microsoft 365 Defender:

- عند إنشاء نهج خزينة المرفقات، تقوم في الواقع بإنشاء قاعدة مرفقات آمنة ونهاية المرفقات الآمنة المقترنة في الوقت نفسه باستخدام نفس الاسم لكليهما.
- عند تعديل نهج خزينة المرفقات، تقوم الإعدادات المرتبطة بالاسم والأولوية والممكن أو المعطل وتصفية المستلم بتعديل قاعدة المرفقات الآمنة. تقوم كل الإعدادات الأخرى بتعديل نهج المرفق الآمن المقترن.
- عند إزالة نهج خزينة المرفقات، تتم إزالة قاعدة المرفقات الآمنة ون نهج المرفقات الآمنة المقترن بها.

في Exchange Online PowerShell أو EOP PowerShell مستقل، يمكنك إدارة النهج والقاعدة بشكل منفصل. لمزيد من المعلومات، راجع المقطع استخدام Exchange Online [PowerShell أو EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) مستقل لتكوين خزينة المرفقات لاحقا في هذه المقالة.

> [!NOTE]
> في منطقة الإعدادات العامة خزينة إعدادات المرفقات، يمكنك تكوين الميزات التي لا تعتمد على خزينة المرفقات. للحصول على الإرشادات، راجع تشغيل [خزينة](turn-on-mdo-for-spo-odb-and-teams.md) المرفقات SharePoint OneDrive والمستندات Microsoft Teams خزينة والمستندات [Microsoft 365 E5.](safe-docs.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع الاتصال [Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- تحتاج إلى أذونات قبل أن تتمكن من تنفيذ الإجراءات في هذه المقالة:
  - لإنشاء سياسات المرفقات خزينة وتعديلها وحذفها، يجب أن تكون عضوا في مجموعات دور مسؤول إدارة المؤسسة أو مسؤول الأمان  في مدخل Microsoft 365 Defender  وعضوا في مجموعة دور إدارة المؤسسة في Exchange Online. 
  - للوصول للقراءة فقط إلى خزينة المرفقات، يجب أن تكون عضوا في مجموعات دور القارئ العام أو قارئ الأمان في Microsoft 365 Defender  المدخل.

  لمزيد من المعلومات، راجع الأذونات في [Microsoft 365 Defender والأذونات](permissions-microsoft-365-security-center.md) [في Exchange Online](/exchange/permissions-exo/permissions-exo).

  **ملاحظات**:

  - توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 للمستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender والأذونات للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  - توفر **أيضا مجموعة دور "** إدارة [المؤسسات Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) طريقة العرض فقط" إمكانية الوصول للقراءة فقط إلى الميزة.

- للحصول على الإعدادات المستحسنة خزينة المرفقات، راجع خزينة [المرفقات](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- السماح بتطبيق نهج جديد أو محدث لمدة تصل إلى 30 دقيقة.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>استخدام مدخل Microsoft 365 Defender لإنشاء خزينة المرفقات

يؤدي إنشاء نهج خزينة المرفقات في مدخل Microsoft 365 Defender إلى إنشاء قاعدة المرفقات الآمنة ون نهج المرفقات الآمنة المقترنة به في الوقت نفسه باستخدام نفس الاسم لكل منهما.

1. في مدخل Microsoft 365 Defender،  \>  \>  \> <https://security.microsoft.com>انتقل إلى & البريد الإلكتروني ونهج التعاون & القواعد خزينة **المرفقات** في **القسم** "سياسات". الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، انقر فوق ![إنشاء أيقونة.](../../media/m365-cc-sc-create-icon.png) **إنشاء**.

3. يتم فتح معالج النهج. في صفحة **تسمية النهج** ، قم بتكوين الإعدادات التالية:
   - **الاسم**: أدخل اسما فريدا ووصفيا النهج.
   - **الوصف**: أدخل وصفا اختياريا النهج.

   عند الانتهاء، انقر فوق **التالي**.

4. في **صفحة المستخدمون والمجالات** التي تظهر، حدد المستلمين الداخليين الذين ينطبق النهج علىهم (شروط المستلمين):
   - **المستخدمون**: علب البريد المحددة أو مستخدمي البريد أو جهات اتصال البريد المحددة في مؤسستك.
   - **المجموعات**: مجموعات التوزيع المحددة أو مجموعات الأمان التي تم تمكين البريد Microsoft 365 في مؤسستك.
   - **المجالات**: جميع المستلمين في المجالات المقبولة [المحددة](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) في مؤسستك.

   انقر في المربع المناسب، وابدأ بكتابة قيمة، وحدد القيمة التي تريدها من النتائج. كرر هذه العملية قدر ما يلزم. لإزالة قيمة موجودة، انقر فوق إزالة ![أيقونة إزالة.](../../media/m365-cc-sc-remove-selection-icon.png) بجانب القيمة.

   بالنسبة للمستخدمين أو المجموعات، يمكنك استخدام معظم المعرف (الاسم واسم العرض واسم المستعار وعنوان البريد الإلكتروني واسم الحساب وغير ذلك)، ولكن يظهر اسم العرض المقابل في النتائج. بالنسبة للمستخدمين، أدخل النجمة (\*) بمفردها لرؤية كل القيم المتوفرة.

   تستخدم القيم المتعددة في نفس الشرط منطق OR (على سبيل المثال _\<recipient1\>_ ، أو _\<recipient2\>_). تستخدم الشروط المختلفة منطق AND (على سبيل المثال _\<recipient1\>_ ، و _\<member of group 1\>_).

   - **استبعاد هؤلاء المستخدمين** والمجموعات والمجالات: لإضافة استثناءات للمستلمين الداخليين الذين يطبقهم النهج على (استثناءات غير موجودة)، حدد هذا الخيار وتكوين الاستثناءات. تشبه الإعدادات والسلوك الشروط تماما.

   عند الانتهاء، انقر فوق **التالي**.

5. على الصفحة **الإعدادات**، قم بتكوين الإعدادات التالية:

   - **خزينة البرامج الضارة غير المعروفة للمرفقات**: حدد إحدى القيم التالية:
     - **إيقاف** التشغيل: عادة، لا نوصي بهذه القيمة.
     - **جهاز العرض**
     - **الحظر**: هذه هي القيمة الافتراضية، والقيمة الموصى بها في سياسات الأمان القياسية والمتقيدة [مسبقا.](preset-security-policies.md)
     - **استبدال**
     - **التسليم الديناميكي (ميزة المعاينة)**

     يتم شرح هذه القيم [في خزينة نهج المرفقات](safe-attachments.md#safe-attachments-policy-settings).

   - **نهج الفحص**: حدد نهج الفحص الذي ينطبق على الرسائل التي تم فحصها بواسطة مرفقات خزينة (**الحظر** أو استبدال أو **التسليم الديناميكي**).  تحدد سياسات الفحص ما يمكن للمستخدمين القيام به للرسائل المعزولة، وما إذا كان المستخدمون يتلقون إعلامات الفحص أم لا. لمزيد من المعلومات، راجع [سياسات الفحص](quarantine-policies.md).

     تعني القيمة الفارغة استخدام نهج الفحص الافتراضي (AdminOnlyAccessPolicy للكشف عن البريد الإلكتروني بواسطة خزينة المرفقات). عند تحرير نهج المرفقات خزينة لاحقا أو عرض الإعدادات، يظهر اسم نهج الفحص الافتراضي.

   - إعادة توجيه الرسائل التي تحتوي على مرفقات تم الكشف **عنها: إذا** حددت تمكين إعادة التوجيه، يمكنك تحديد عنوان بريد  إلكتروني في المربع إرسال الرسائل التي تحتوي على مرفقات تم حظرها أو مراقبتها أو استبدالها إلى عنوان البريد الإلكتروني المحدد لإرسال الرسائل التي تحتوي على مرفقات البرامج الضارة لتحليلها والتحري عنها.

     إن التوصية بإعدادات النهج القياسية والتقيدية هي تمكين إعادة التوجيه. لمزيد من المعلومات، [راجع خزينة المرفقات](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

   - تطبيق **استجابة الكشف** عن خزينة المرفقات إذا لم يكن المسح الضوئي مكتملا (المهيأ أو الأخطاء): يتم اتخاذ الإجراء المحدد بواسطة استجابة البرامج الضارة غير المعروفة لمرفقات **خزينة** على الرسائل حتى عندما لا يمكن إكمال فحص المرفقات في خزينة. إذا حددت هذا الخيار، فحدد دائما **تمكين إعادة التوجيه** وحدد عنوان بريد إلكتروني لإرسال الرسائل التي تحتوي على مرفقات البرامج الضارة. وإلا، فقد يتم فقدان الرسائل.

   عند الانتهاء، انقر فوق **التالي**.

6. على الصفحة **مراجعة** التي تظهر، راجع الإعدادات. يمكنك تحديد **تحرير** في كل مقطع لتعديل الإعدادات ضمن المقطع. أو يمكنك النقر فوق **الخلف** أو تحديد الصفحة المحددة في المعالج.

   عند الانتهاء، انقر فوق **إرسال**.

7. على صفحة التأكيد التي تظهر، انقر فوق **تم**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>استخدام مدخل Microsoft 365 Defender لعرض خزينة المرفقات

1. في مدخل Microsoft 365 Defender،  \>  \>  \> <https://security.microsoft.com>انتقل إلى & البريد الإلكتروني ونهج التعاون & القواعد خزينة **المرفقات** في **القسم** "سياسات". الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة** المرفقات، يتم عرض الخصائص التالية في قائمة السياسات:
   - **الاسم**
   - **الحالة**
   - **الأولوية**

3. عند تحديد نهج بالنقر فوق الاسم، يتم عرض إعدادات النهج في قائمة منسقة.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>استخدام مدخل Microsoft 365 Defender لتعديل خزينة المرفقات

1. IIn the Microsoft 365 Defender in <https://security.microsoft.com>, go to **email & Collaboration** \> **policies & Rules** \> **threat policies** \> خزينة **المرفقات** في **القسم "** سياسات". الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة** المرفقات، حدد نهج من القائمة بالنقر فوق الاسم.

3. في قائمة تفاصيل النهج التي تظهر، حدد **تحرير** في كل مقطع لتعديل الإعدادات ضمن المقطع. لمزيد من المعلومات حول الإعدادات، راجع المقطع استخدام مدخل Microsoft 365 Defender لإنشاء [خزينة](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) المرفقات الواردة سابقا في هذه المقالة.

لتمكين نهج أو تعطيله أو تعيين ترتيب أولوية النهج، راجع المقاطع التالية.

### <a name="enable-or-disable-safe-attachments-policies"></a>تمكين سياسات المرفقات خزينة أو تعطيلها

1. في مدخل Microsoft 365 Defender،  \>  \>  \> <https://security.microsoft.com>انتقل إلى & البريد الإلكتروني ونهج التعاون & القواعد خزينة **المرفقات** في **القسم** "سياسات". الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة** المرفقات، حدد نهج من القائمة بالنقر فوق الاسم.

3. في أعلى قائمة تفاصيل النهج التي تظهر، سترى إحدى القيم التالية:
   - **إيقاف تشغيل النهج**: ل تشغيل النهج، انقر فوق أيقونة ![تشغيل.](../../media/m365-cc-sc-turn-on-off-icon.png) **قم تشغيل** .
   - **تشغيل النهج**: إيقاف تشغيل النهج، انقر فوق ![أيقونة إيقاف التشغيل.](../../media/m365-cc-sc-turn-on-off-icon.png) **إيقاف التشغيل**.

4. في مربع حوار التأكيد الذي يظهر، انقر فوق **تشغيل** أو **إيقاف تشغيل**.

5. انقر **فوق** إغلاق في مناصة تفاصيل النهج.

عند العودة إلى صفحة النهج الرئيسية، ستكون  قيمة حالة النهج في **وضع التشغيل** أو **إيقاف التشغيل**.

### <a name="set-the-priority-of-safe-attachments-policies"></a>تعيين أولوية خزينة المرفقات

بشكل افتراضي خزينة يتم منح خزينة المرفقات أولوية تستند إلى الترتيب الذي تم إنشاؤها به (تكون السياسات الجديدة ذات أولوية أقل من تلك التي يتم تعيينها إلى نهج قديمة). يشير رقم الأولوية الأدنى إلى أولوية أعلى بالنسبة إلى النهج (0 هو الأعلى)، كما تتم معالجة النهج وفقا ترتيب الأولوية (تتم معالجة نهج الأولوية العليا قبل النهج ذات الأولوية الدنيا). لا يمكن أن تكون الأولوية نفسها لنهجين، وتتوقف معالجة النهج بعد تطبيق النهج الأول.

لمزيد من المعلومات حول ترتيب الأسبقية وكيفية تقييم عدة سياسات وتطبيقها، راجع ترتيب [حماية البريد الإلكتروني وأسبقيته](how-policies-and-protections-are-combined.md).

خزينة يتم عرض نهج المرفقات بالترتيب الذي تتم معالجته (النهج الأول له القيمة **الأولوية** 0).

**ملاحظة**: في Microsoft 365 Defender، يمكنك فقط تغيير أولوية نهج المرفقات خزينة بعد إنشائها. في PowerShell، يمكنك تجاوز الأولوية الافتراضية عند إنشاء قاعدة المرفق الآمن (التي يمكن أن تؤثر على أولوية القواعد الموجودة).

لتغيير أولوية النهج، انقر فوق زيادة الأولوية أو إنقاص الأولوية في  خصائص النهج (لا يمكنك تعديل رقم الأولوية مباشرة في مدخل Microsoft 365 Defender).  لا يكون تغيير أولوية النهج منطقيا إلا إذا كان لديك نهج متعددة.

1. في مدخل Microsoft 365 Defender،  \>  \> انتقل إلى & البريد الإلكتروني ونهج التعاون & القواعد **خزينة** \> **المرفقات** في **القسم "سياسات**".

2. في صفحة **خزينة** المرفقات، حدد نهج من القائمة بالنقر فوق الاسم.

3. في أعلى القائمة العلوية التفاصيل الخاصة بالتفاصيل التي تظهر، سترى زيادة الأولوية أو إنقاص  الأولوية استنادا إلى  قيمة الأولوية الحالية وعدد النهج:
   - يتوفر النهج الذي به **القيمة الأولوية** **0** فقط خيار **إنقاص** الأولوية.
   - يتوفر النهج الذي به أقل قيمة **أولوية** (على سبيل المثال **، 3**) خيار **زيادة** الأولوية فقط.
   - إذا كان لديك ثلاثة سياسات أو أكثر، فإن الخيارات المتوفرة بين القيم ذات الأولوية الأعلى والأدنى هي الخيارات "زيادة  الأولوية" و"إنقاص الأولوية".

   انقر ![فوق زيادة أيقونة الأولوية.](../../media/m365-cc-sc-increase-icon.png) **زيادة الأولوية** أو ![أيقونة إنقاص الأولوية](../../media/m365-cc-sc-decrease-icon.png) **إنقاص** الأولوية لتغيير **قيمة الأولوية** .

4. عند الانتهاء، انقر فوق **إغلاق** في منتهى تفاصيل النهج.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>استخدام مدخل Microsoft 365 Defender لإزالة خزينة المرفقات

1. في مدخل Microsoft 365 Defender،  \>  \>  \> <https://security.microsoft.com>انتقل إلى & البريد الإلكتروني ونهج التعاون & القواعد خزينة **المرفقات** في **القسم** "سياسات". الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة** المرفقات، حدد نهج مخصص من القائمة بالنقر فوق اسم النهج.

3. في أعلى قائمة تفاصيل النهج التي تظهر، انقر فوق أيقونة ![المزيد من الإجراءات.](../../media/m365-cc-sc-more-actions-icon.png) **المزيد من الإجراءات** \> ![أيقونة حذف النهج](../../media/m365-cc-sc-delete-icon.png) **حذف النهج**.

4. في مربع حوار التأكيد الذي يظهر، انقر فوق **نعم**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>استخدام Exchange Online PowerShell أو EOP PowerShell مستقل لتكوين خزينة المرفقات

كما هو موضح مسبقا، يتكون خزينة المرفقات من نهج مرفق آمن ومن قاعدة مرفقات آمنة.

في PowerShell، يظهر الفرق بين سياسات المرفقات الآمنة وقواعد المرفقات الآمنة. يمكنك إدارة سياسات المرفقات الآمنة باستخدام **الأمر -SafeAttachmentPolicy cmdlets، كما يمكنك إدارة قواعد المرفقات الآمنة باستخدام الأمرين -SafeAttachmentRule cmdlets.\*** **\***

- في PowerShell، يمكنك أولا إنشاء نهج المرفق الآمن، ثم إنشاء قاعدة المرفق الآمن التي تحدد النهج الذي تنطبق عليه القاعدة.
- في PowerShell، يمكنك تعديل الإعدادات في نهج المرفق الآمن و قاعدة المرفق الآمن بشكل منفصل.
- عند إزالة نهج مرفق آمن من PowerShell، لا تتم إزالة قاعدة المرفقات الآمنة المقابلة تلقائيا، والعكس صحيح.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>استخدام PowerShell لإنشاء خزينة المرفقات

إن إنشاء خزينة المرفقات في PowerShell عملية من خطوتين:

1. إنشاء نهج المرفق الآمن.
2. أنشئ قاعدة المرفق الآمن التي تحدد نهج المرفق الآمن الذي تنطبق عليه القاعدة.

 **ملاحظات**:

- يمكنك إنشاء قاعدة مرفقات آمنة جديدة وتعيين نهج مرفق آمن موجود وغير مفروق لها. لا يمكن تقترن قاعدة مرفقات آمنة بأكثر من نهج مرفق آمن واحد.

- يمكنك تكوين الإعدادات التالية على نهج المرفقات الآمنة الجديدة في PowerShell غير المتوفرة في مدخل Microsoft 365 Defender إلا بعد إنشاء النهج:
  - قم بإنشاء النهج الجديد كما تم تعطيله (_ممكن_ `$false` على **cmdlet New-SafeAttachmentRule** ).
  - تعيين أولوية النهج أثناء الإنشاء (_الأولوية_ _\<Number\>_) على **cmdlet New-SafeAttachmentRule** ).

- لن يكون نهج المرفق الآمن الجديد الذي تقوم بإنشاءه في PowerShell مرئيا في مدخل Microsoft 365 Defender حتى تقوم بتعيين النهج إلى قاعدة مرفقات آمنة.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>الخطوة 1: استخدام PowerShell لإنشاء نهج مرفق آمن

لإنشاء نهج مرفق آمن، استخدم بناء الجملة هذا:

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

ينشئ هذا المثال نهج مرفق آمن باسم Contoso All مع القيم التالية:

- حظر الرسائل التي يتم العثور عليها لتحتوي على برامج ضارة خزينة فحص المستندات (لا نستخدم معلمة الإجراء، والقيمة  الافتراضية هي `Block`).
- يتم استخدام [نهج الفحص الافتراضي](quarantine-policies.md) (AdminOnlyAccessPolicy)، لأننا لا نستخدم المعلمة _QuarantineTag_ .
- يتم تمكين إعادة التوجيه، وترسل الرسائل التي يتم العثور عليها لتحتوي على برامج ضارة إلى sec-ops@contoso.com للتحليل والتحري.
- إذا خزينة فحص المرفقات غير متوفر أو واجه أخطاء، فلا تسلم الرسالة (لا نستخدم المعلمة _ActionOnError_، والقيمة الافتراضية هي `$true`).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

للحصول على بناء جملة تفصيلي ومعلومات المعلمة، راجع [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> للحصول على إرشادات مفصلة لتحديد نهج [](quarantine-policies.md) الفحص لاستخدامه في نهج مرفق آمن، راجع استخدام [PowerShell لتحديد نهج](quarantine-policies.md#safe-attachments-policies-in-powershell) الفحص في خزينة المرفقات.

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>الخطوة 2: استخدام PowerShell لإنشاء قاعدة مرفقات آمنة

لإنشاء قاعدة مرفقات آمنة، استخدم بناء الجملة هذا:

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

ينشئ هذا المثال قاعدة مرفقات آمنة تسمى Contoso All بالشروط التالية:

- تقترن القاعدة ب نهج المرفق الآمن المسمى Contoso All.
- تنطبق القاعدة على كل المستلمين في contoso.com المجال.
- نظرا لأننا لا نستخدم معلمة _الأولوية_ ، يتم استخدام الأولوية الافتراضية.
- يتم تمكين القاعدة (لا نستخدم المعلمة _Enabled_ ، والقيمة الافتراضية هي `$true`).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>استخدام PowerShell لعرض سياسات المرفقات الآمنة

لعرض سياسات المرفقات الآمنة الموجودة، استخدم بناء الجملة التالي:

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

يرجع هذا المثال قائمة ملخصة بكل سياسات المرفقات الآمنة.

```PowerShell
Get-SafeAttachmentPolicy
```

يرجع هذا المثال معلومات مفصلة حول نهج المرفق الآمن المسمى مديرو Contoso التنفيذيون.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>استخدام PowerShell لعرض قواعد المرفقات الآمنة

لعرض قواعد المرفقات الآمنة الموجودة، استخدم بناء الجملة التالي:

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

يرجع هذا المثال قائمة موجزة بكل قواعد المرفقات الآمنة.

```PowerShell
Get-SafeAttachmentRule
```

لتصفية القائمة حسب القواعد التي تم تمكينها أو تعطيلها، يمكنك تشغيل الأوامر التالية:

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

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>استخدام PowerShell لتعديل سياسات المرفقات الآمنة

لا يمكنك إعادة تسمية نهج مرفق آمن في PowerShell (لا يوجد في الأمر **Set-SafeAttachmentPolicy** cmdlet _معلمة_ الاسم). عند إعادة تسمية نهج خزينة المرفقات في Microsoft 365 Defender، تقوم بإعادة تسمية قاعدة المرفقات _الآمنة فقط_.

بخلاف ذلك، تتوفر الإعدادات نفسها عند إنشاء نهج مرفق آمن كما هو موضح في الخطوة [1: استخدام PowerShell](#step-1-use-powershell-to-create-a-safe-attachment-policy) لإنشاء مقطع نهج مرفق آمن سابقا في هذه المقالة.

لتعديل نهج مرفق آمن، استخدم بناء الجملة هذا:

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> للحصول على إرشادات مفصلة لتحديد نهج [](quarantine-policies.md) الفحص لاستخدامه في نهج مرفق آمن، راجع استخدام [PowerShell لتحديد نهج](quarantine-policies.md#safe-attachments-policies-in-powershell) الفحص في خزينة المرفقات.

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>استخدام PowerShell لتعديل قواعد المرفقات الآمنة

الإعداد الوحيد الذي لا يتوفر عند تعديل قاعدة مرفق آمن في PowerShell هو المعلمة _Enabled_ التي تسمح لك بإنشاء قاعدة معطلة. لتمكين قواعد المرفقات الآمنة الموجودة أو تعطيلها، راجع المقطع التالي.

بخلاف ذلك، تتوفر الإعدادات نفسها عند إنشاء قاعدة كما هو موضح في الخطوة [2: استخدام PowerShell](#step-2-use-powershell-to-create-a-safe-attachment-rule) لإنشاء مقطع قاعدة مرفقات آمنة سابقا في هذه المقالة.

لتعديل قاعدة مرفق آمنة، استخدم بناء الجملة هذا:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>استخدام PowerShell لتمكين قواعد المرفقات الآمنة أو تعطيلها

يؤدي تمكين قاعدة مرفقات آمنة أو تعطيلها في PowerShell إلى تمكين نهج مرفقات خزينة بالكامل أو تعطيلها (قاعدة المرفقات الآمنة ونمط المرفق الآمن المعين).

لتمكين قاعدة مرفقات آمنة أو تعطيلها في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

يعطل هذا المثال قاعدة المرفقات الآمنة المسماة قسم التسويق.

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

يمكن هذا المثال القاعدة نفسها.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Enable-SafeAttachmentRule](/powershell/module/exchange/enable-safeattachmentrule) و [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>استخدام PowerShell لتعيين أولوية قواعد المرفقات الآمنة

إن أعلى قيمة أولوية يمكنك تعيينها على قاعدة هي 0. تعتمد أقل قيمة يمكنك تعيينها على عدد القواعد. على سبيل المثال، إذا كان لديك خمس قواعد، يمكنك استخدام قيم الأولوية من 0 إلى 4. قد يكون لتغيير أولوية قاعدة موجودة تأثير تتالي على قواعد أخرى. على سبيل المثال، إذا كان لديك خمس قواعد مخصصة (الأولويات من 0 إلى 4)، ثم قمت بتغيير أولوية القاعدة إلى 2، يتم تغيير القاعدة الموجودة ذات الأولوية 2 إلى الأولوية 3، وتتغير القاعدة ذات الأولوية 3 إلى الأولوية 4.

لتعيين أولوية قاعدة مرفقات آمنة في PowerShell، استخدم بناء الجملة التالي:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

يحدد هذا المثال أولوية القاعدة المسماة قسم التسويق إلى 2. يتم تقليل كل القواعد الموجودة التي لها أولوية أقل من أو تساوي 2 بمقدار 1 (يتم زيادة أرقام أولوياتها بمقدار 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**ملاحظة**: لتعيين أولوية قاعدة جديدة عند إنشائها، استخدم المعلمة _Priority_ على **الأمر cmdlet New-SafeAttachmentRule** بدلا من ذلك.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>استخدام PowerShell لإزالة سياسات المرفقات الآمنة

عند استخدام PowerShell لإزالة نهج مرفق آمن، لن تتم إزالة قاعدة المرفقات الآمنة المقابلة.

لإزالة نهج مرفق آمن في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

يزيل هذا المثال نهج المرفق الآمن المسمى قسم التسويق.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>استخدام PowerShell لإزالة قواعد المرفقات الآمنة

عند استخدام PowerShell لإزالة قاعدة مرفقات آمنة، لن تتم إزالة نهج المرفق الآمن المناظر.

لإزالة قاعدة مرفقات آمنة في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

يزيل هذا المثال قاعدة المرفقات الآمنة المسماة قسم التسويق.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>كيف يمكنك معرفة كيفية عمل هذه الإجراءات؟

للتحقق من نجاح إنشاء أو تعديل أو إزالة خزينة المرفقات، قم بأي من الخطوات التالية:

- في صفحة **خزينة** <https://security.microsoft.com/safeattachmentv2>المرفقات في Microsoft 365 Defender في ، تحقق من قائمة السياسات وقيم الحالة **وقيم الأولوية** الخاصة بها. لعرض المزيد من التفاصيل، حدد النهج من القائمة بالنقر فوق الاسم، وانظر التفاصيل في القائمة المطيرة.

- في Exchange Online PowerShell أو Exchange Online Protection PowerShell\<Name\>، استبدل باسم النهج أو القاعدة، ثم ادير الأمر التالي وتحقق من الإعدادات:

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

للتحقق من أن خزينة "المرفقات" تمسح الرسائل ضوئيا، تحقق من "Defender" Office 365 المتوفرة. لمزيد من المعلومات، راجع [عرض تقارير ل Defender for Office 365](view-reports-for-mdo.md) [واستخدام المستكشف في Microsoft 365 Defender المدخل](threat-explorer.md).
