---
title: نُهج أمان مُعدّة مسبقاً
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: يمكن للمسؤولين معرفة كيفية تطبيق إعدادات النهج القياسية والضيقة عبر ميزات الحماية Exchange Online Protection (EOP) Microsoft Defender لـ Office 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd5fd696a9e22f0e30d18b3b785761847166a5b3
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67085236"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>نهج الأمان التي تم تعيينها مسبقا في EOP و Microsoft Defender لـ Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

توفر نهج الأمان المعينة مسبقا موقعا مركزيا لتطبيق كل نهج البريد العشوائي والبرامج الضارة والتصيد الاحتيالي الموصى بها على المستخدمين في وقت واحد. إعدادات النهج غير قابلة للتكوين. بدلا من ذلك، يتم تعيينها من قبلنا وتستند إلى ملاحظاتنا وتجاربنا في مراكز البيانات لتحقيق التوازن بين الحفاظ على المحتوى الضار بعيدا عن المستخدمين وتجنب الاضطرابات غير الضرورية.

تصف بقية هذه المقالة نهج الأمان التي تم تعيينها مسبقا وكيفية تكوينها.

## <a name="what-preset-security-policies-are-made-of"></a>ما هي نهج الأمان التي تم إعدادها مسبقا من

تتكون نهج الأمان التي تم تعيينها مسبقا من العناصر التالية:

- ملفات تعريف
- السياسات
- إعدادات النهج

بالإضافة إلى ذلك، يكون ترتيب الأسبقية مهما إذا تم تطبيق نهج أمان متعددة مسبقة الإعداد ونهج أخرى على نفس الشخص.

### <a name="profiles-in-preset-security-policies"></a>ملفات التعريف في نهج الأمان التي تم تعيينها مسبقا

يحدد ملف التعريف مستوى الحماية. تتوفر ملفات التعريف التالية:

- **الحماية القياسية**: ملف تعريف حماية أساسي مناسب لمعظم المستخدمين.
- **حماية صارمة**: ملف تعريف حماية أكثر صرامة للمستخدمين المحددين (أهداف ذات قيمة عالية أو المستخدمين ذات الأولوية).

  **للحماية القياسية** **والحماية الصارمة**، يمكنك استخدام القواعد مع الشروط والاستثناءات لتحديد المستلمين الداخليين الذين ينطبق عليها النهج (شروط المستلمين).

  الشروط والاستثناءات المتوفرة هي:

  - **المستخدمون**: علب البريد أو مستخدمو البريد أو جهات اتصال البريد المحددة.
  - **المجموعات**:
    - أعضاء مجموعات التوزيع المحددة أو مجموعات الأمان الممكنة للبريد.
    - مجموعات Microsoft 365 المحددة.
  - **المجالات**: كافة المستلمين في [المجالات المقبولة المحددة](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) في مؤسستك.

  يمكنك استخدام شرط أو استثناء مرة واحدة فقط، ولكن يمكنك تحديد قيم متعددة للشرط أو الاستثناء. تستخدم قيم متعددة لنفس الشرط أو منطق الاستثناء منطق OR (على سبيل المثال، _\<recipient1\>_ أو _\<recipient2\>_). تستخدم الشروط أو الاستثناءات المختلفة منطق AND (على سبيل المثال، _\<recipient1\>_ و _\<member of group 1\>_).

  > [!IMPORTANT]
  > لا توجد أنواع مختلفة متعددة من الشروط أو الاستثناءات الإضافية؛ إنها شاملة. يتم تطبيق نهج الأمان المعين مسبقا _فقط_ على المستلمين الذين يتطابقون مع _كافة_ عوامل تصفية المستلمين المحددة. على سبيل المثال، يمكنك تكوين شرط عامل تصفية مستلم في النهج بالقيم التالية:
  >
  > - المستلم هو: romain@contoso.com
  > - المستلم هو عضو في: المديرين التنفيذيين
  >
  > يتم تطبيق النهج على romain@contoso.com _فقط_ إذا كان أيضا عضوا في مجموعة المديرين التنفيذيين. إذا لم يكن عضوا في المجموعة، فلن يتم تطبيق النهج عليه.
  >
  > وبالمثل، إذا كنت تستخدم عامل تصفية المستلم نفسه استثناء للنهج، فلن يتم تطبيق النهج على romain@contoso.com _فقط_ إذا كان أيضا عضوا في مجموعة المديرين التنفيذيين. إذا لم يكن عضوا في المجموعة، فإن النهج لا يزال ينطبق عليه.

- **الحماية المضمنة** (Defender لـ Office 365 فقط): ملف تعريف يمكن الارتباطات الآمنة وحماية المرفقات الآمنة فقط. يوفر ملف التعريف هذا بشكل فعال نهج افتراضية للارتباطات الآمنة والمرفقات الآمنة، والتي لم يكن لها نهج افتراضية.

  > [!NOTE]
  > يتم نشر نهج الأمان المعين مسبقا للحماية المضمنة، وقد لا يكون متوفرا في مؤسستك.

  بالنسبة إلى **الحماية المضمنة**، يتم تشغيل نهج الأمان المحدد مسبقا بشكل افتراضي لجميع العملاء Defender لـ Office 365. على الرغم من أننا لا نوصي بذلك، يمكنك أيضا تكوين استثناءات استنادا إلى **المستخدمين** **والمجموعات** **والمجالات** بحيث لا يتم تطبيق الحماية على مستخدمين محددين.

حتى تقوم بتعيين النهج للمستخدمين، يتم تعيين نهج الأمان المحددة مسبقا **القياسية** **والضيقة** إلى أي شخص. في المقابل، يتم تعيين نهج الأمان المعين مسبقا **للحماية المضمنة** إلى كافة المستلمين بشكل افتراضي، ولكن يمكنك تكوين الاستثناءات.

### <a name="policies-in-preset-security-policies"></a>النهج في نهج الأمان التي تم تعيينها مسبقا

تستخدم نهج الأمان التي تم تعيينها مسبقا النهج المقابلة من ميزات الحماية المختلفة في EOP Microsoft Defender لـ Office 365. يتم إنشاء هذه النهج _بعد_ تعيين نهج الأمان المعينة مسبقا **للحماية القياسية** أو **الحماية الصارمة** للمستخدمين. لا يمكنك تعديل الإعدادات في هذه النهج.

- **نهج Exchange Online Protection (EOP):** هذه النهج موجودة في جميع مؤسسات Microsoft 365 التي تحتوي على علب بريد Exchange Online والمؤسسات المستقلة EOP بدون علب بريد Exchange Online:

  - [نهج مكافحة البريد العشوائي](configure-your-spam-filter-policies.md) **المسماة "نهج أمان قياسي مسبق الإعداد** " و **"نهج أمان مقيد مسبقا**".
  - [نهج مكافحة البرامج الضارة](configure-anti-malware-policies.md) **المسماة Standard Preset Security Policy** **ونهج أمان مقيد مسبق الإعداد**.
  - [نهج مكافحة التصيد الاحتيالي (حماية الانتحال)](set-up-anti-phishing-policies.md#spoof-settings) **المسماة Standard Preset Security Policy** و **Strict Preset Security Policy** (sof settings).

  > [!NOTE]
  > نهج البريد العشوائي الصادرة ليست جزءا من نهج الأمان التي تم إعدادها مسبقا. يحمي نهج البريد العشوائي الصادر الافتراضي تلقائيا أعضاء نهج الأمان التي تم تعيينها مسبقا. أو يمكنك إنشاء نهج بريد عشوائي صادر مخصصة لتخصيص الحماية لأعضاء نهج الأمان التي تم تعيينها مسبقا. لمزيد من المعلومات، راجع [تكوين تصفية البريد العشوائي الصادر في EOP](configure-the-outbound-spam-policy.md).

- **نهج Microsoft Defender لـ Office 365**: هذه النهج موجودة في المؤسسات التي لها اشتراكات Microsoft 365 E5 أو Defender لـ Office 365 الوظائف الإضافية:
  - نهج مكافحة التصيد الاحتيالي في Defender لـ Office 365 **المسماة Standard Preset Security Policy** و **Strict Preset Security Policy**، والتي تتضمن:
    - نفس [إعدادات الانتحال](set-up-anti-phishing-policies.md#spoof-settings) المتوفرة في نهج مكافحة التصيد الاحتيالي EOP.
    - [إعدادات الانتحال](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [حدود التصيد الاحتيالي المتقدمة](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [نهج الارتباطات الآمنة](set-up-safe-links-policies.md) **المسماة نهج الأمان القياسي المحدد مسبقا** **ونهج الأمان المحدد مسبقا** الصارم **ونهج الحماية المضمن**.
  - [نهج المرفقات الآمنة](set-up-safe-attachments-policies.md) **المسماة "نهج أمان قياسي مسبق الإعداد**" و **"نهج أمان مقيد مسبقا**" و" **نهج حماية مضمن**".

يمكنك تطبيق حماية EOP على مستخدمين مختلفين عن Defender لـ Office 365 الحماية، أو يمكنك تطبيق EOP Defender لـ Office 365 على نفس المستلمين.

### <a name="policy-settings-in-preset-security-policies"></a>إعدادات النهج في نهج الأمان التي تم تعيينها مسبقا

لا يمكنك تعديل إعدادات النهج في ملفات تعريف الحماية. يتم وصف قيم إعداد نهج الحماية **القياسية** **والضيقة** **والمضمنة** في [الإعدادات المستحسنة ل EOP والأمان Microsoft Defender لـ Office 365](recommended-settings-for-eop-and-office365.md).

> [!NOTE]
> في Defender لـ Office 365 الحماية، تحتاج إلى تحديد المرسلين [لحماية انتحال المستخدم](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) والمجالات الداخلية أو الخارجية [لحماية انتحال المجال](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).
>
> تتلقى جميع المجالات التي تملكها ([المجالات المقبولة](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) تلقائيا حماية انتحال المجال في نهج الأمان المعينة مسبقا.
>
> يتلقى جميع المستلمين تلقائيا حماية انتحال من [ذكاء علبة البريد](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) في نهج الأمان التي تم تعيينها مسبقا.

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>ترتيب الأسبقية لنهج الأمان المسبقة والنهج الأخرى

عند تطبيق نهج متعددة على مستخدم، يتم تطبيق الترتيب التالي من الأولوية القصوى إلى الأولوية الدنيا:

1. نهج أمان مقيد مسبقا.
2. نهج أمان قياسي مسبق الإعداد.
3. النهج المخصصة. يتم تطبيق النهج المخصصة استنادا إلى قيمة الأولوية للنهج.
4. نهج أمان مسبق الإعداد للحماية المضمنة للارتباطات الآمنة والمرفقات الآمنة؛ النهج الافتراضية لمكافحة البرامج الضارة، ومكافحة البريد العشوائي، ومكافحة التصيد الاحتيالي.

بمعنى آخر، تتجاوز إعدادات نهج الأمان المضمن **مسبقا إعدادات** نهج الأمان **القياسي** الذي تم تعيينه مسبقا، والذي يتجاوز الإعدادات من أي نهج مخصصة، والتي تتجاوز إعدادات نهج الأمان **المضمن** الذي تم تعيينه مسبقا للارتباطات الآمنة والمرفقات الآمنة، والنهج الافتراضية لمكافحة البريد العشوائي ومكافحة البرامج الضارة والتصيد الاحتيالي.

على سبيل المثال، يوجد إعداد أمان في **الحماية القياسية** ويحدد المسؤول مستخدما **للحماية القياسية**. يتم تطبيق إعداد **الحماية القياسي** على المستخدم بدلا من ما تم تكوينه لهذا الإعداد في نهج مخصص أو في النهج الافتراضي لنفس المستخدم.

قد تحتاج إلى تطبيق نهج الأمان **القياسية** أو **الصارمة** المعينة مسبقا على مجموعة فرعية من المستخدمين، وتطبيق نهج مخصصة على مستخدمين آخرين في مؤسستك لتلبية احتياجات محددة. لتلبية هذا المطلب، قم بالخطوات التالية:

- تكوين المستخدمين الذين يجب أن يحصلوا على إعدادات نهج الأمان **القياسي** الذي تم تعيينه مسبقا والنهج المخصصة كاستثناءات في نهج الأمان المضمن **مسبقا.**
- تكوين المستخدمين الذين يجب أن يحصلوا على إعدادات النهج المخصصة كاستثناءات في نهج الأمان **القياسي** الذي تم تعيينه مسبقا.

لا تؤثر **الحماية المضمنة** على المستلمين في نهج الارتباطات الآمنة أو المرفقات الآمنة الموجودة. إذا قمت بالفعل بتكوين نهج **الحماية القياسية** أو **الحماية الصارمة** أو الارتباطات الآمنة المخصصة أو المرفقات الآمنة، يتم تطبيق هذه النهج _دائما_ _قبل_ **الحماية المضمنة**، لذلك لا يوجد أي تأثير على المستلمين الذين تم تعريفهم بالفعل في تلك النهج المخصصة أو المعينة مسبقا الموجودة.

## <a name="assign-preset-security-policies-to-users"></a>تعيين نهج الأمان المعينة مسبقا للمستخدمين

### <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **نهج الأمان التي تم تعيينها مسبقا** ، استخدم <https://security.microsoft.com/presetSecurityPolicies>.

- للاتصال Exchange Online PowerShell، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- يجب تعيين أذونات لك في **Exchange Online** قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - لتكوين نهج الأمان المحددة مسبقا، يجب أن تكون عضوا في مجموعات دور مسؤول **الأمان** أو **إدارة المؤسسة**.
  - للوصول للقراءة فقط إلى نهج الأمان المحددة مسبقا، يجب أن تكون عضوا في مجموعة دور **القارئ العمومي** .

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  **ملاحظة**: إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات _والأذونات_ المطلوبة للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>استخدام مدخل Microsoft 365 Defender لتعيين نهج أمان محددة مسبقا وقياسية للمستخدمين

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **"نهج التعاون** \> & البريد الإلكتروني **" & نهج** \> **المخاطر** "قواعد\>" **التي تم تعيينها مسبقا لنهج الأمان** في قسم **"نهج القوالب**". للانتقال مباشرة إلى صفحة **نهج الأمان التي تم تعيينها مسبقا** ، استخدم <https://security.microsoft.com/presetSecurityPolicies>.

2. في صفحة **نهج الأمان المحددة مسبقا** ، انقر فوق **"إدارة** " في قسمي " **الحماية القياسية** " أو **"الحماية الصارمة** ".

3. يبدأ معالج **تطبيق الحماية القياسية** أو **تطبيق الحماية الصارمة** في قائمة منبثقة.

   في الصفحة **"تطبيق Exchange Online Protection**"، حدد المستلمين الداخليين الذين تنطبق [حماية EOP](#policies-in-preset-security-policies) على (شروط المستلمين):
   - **كافة المستلمين**
   - **مستلمون محددون**:
     - **المستخدمون**
     - **المجموعات**
     - **المجالات**

     انقر في المربع المناسب، وابدأ بكتابة قيمة، وحدد القيمة التي تريدها من النتائج. كرر هذه العملية عدة مرات حسب الضرورة. لإزالة قيمة موجودة، انقر فوق "إزالة" ![الأيقونة "إزالة".](../../media/m365-cc-sc-remove-selection-icon.png) بجوار القيمة.

     بالنسبة للمستخدمين أو المجموعات، يمكنك استخدام معظم المعرفات (الاسم واسم العرض والاسم المستعار وعنوان البريد الإلكتروني واسم الحساب وما إلى ذلك)، ولكن يظهر اسم العرض المقابل في النتائج. بالنسبة للمستخدمين، أدخل علامة نجمية (\*) بحد ذاتها لمشاهدة كافة القيم المتوفرة.

   - **None**

   - **استبعاد هؤلاء المستلمين**: لإضافة استثناءات للمستلمين الداخليين الذين ينطبق عليها النهج (استثناءات المستلمين)، حدد هذا الخيار وقم بتكوين الاستثناءات. الإعدادات والسلوك تشبه تماما الشروط.

   عند الانتهاء، انقر فوق **"التالي**".

   > [!NOTE]
   > في المؤسسات التي لا تحتوي على Defender لـ Office 365، يؤدي النقر فوق **"التالي**" إلى أخذك إلى صفحة **"مراجعة**". تتوفر الخطوات/الصفحات المتبقية قبل صفحة **المراجعة** فقط في المؤسسات ذات Defender لـ Office 365.

4. في صفحة **"تطبيق حماية Defender لـ Office 365**"، حدد المستلمين الداخليين الذين تنطبق Defender لـ Office 365 [الحماية](#policies-in-preset-security-policies) على (شروط المستلمين).

   تشبه الإعدادات والسلوك تماما **حماية EOP التي تنطبق على** الصفحة في الخطوة السابقة.

   يمكنك أيضا تحديد **المستلمين المحددين مسبقا** لاستخدام نفس المستلمين الذين حددتهم لحماية EOP على الصفحة السابقة.

   عند الانتهاء، انقر فوق **"التالي**".

5. في صفحة **حماية انتحال الهوية** ، انقر فوق **"التالي**".

6. في صفحة **"إضافة عناوين البريد الإلكتروني" لوضع علامة عليها عند انتحالها بواسطة المهاجمين** ، أضف المرسلين الداخليين والخارجيين المحميين [بحماية انتحال المستخدم](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   > [!NOTE]
   > يتلقى جميع المستلمين تلقائيا حماية انتحال من [ذكاء علبة البريد](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) في نهج الأمان التي تم تعيينها مسبقا.

   يتكون كل إدخال من اسم عرض وعنوان بريد إلكتروني. أدخل كل قيمة في المربعات ثم انقر فوق **"إضافة**". كرر هذه الخطوة عدة مرات حسب الضرورة.

   يمكنك تحديد 350 مستخدما كحد أقصى، ولا يمكنك تحديد نفس المستخدم في إعدادات حماية انتحال المستخدم في نهج متعددة.

   لإزالة إدخال موجود من القائمة، انقر فوق ![إزالة المستخدم من أيقونة حماية الانتحال.](../../media/m365-cc-sc-remove.png).

   عند الانتهاء، انقر فوق **"التالي**".

7. في صفحة **"إضافة مجالات" لوضع علامة عليها عند انتحالها بواسطة المهاجمين** ، أضف المجالات الداخلية والخارجية المحمية [بحماية انتحال المجال](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   > [!NOTE]
   > تتلقى جميع المجالات التي تملكها ([المجالات المقبولة](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) تلقائيا حماية انتحال المجال في نهج الأمان المعينة مسبقا.

   جميع المرسلين في المجالات المحددة محميون بحماية انتحال المجال.

   أدخل المجال في المربع، ثم انقر فوق **"إضافة**". كرر هذه الخطوة عدة مرات حسب الضرورة.

   لإزالة إدخال موجود من القائمة، حدد الإدخال، ثم انقر فوق ![إزالة المجال من أيقونة حماية الانتحال.](../../media/m365-cc-sc-remove.png).

   الحد الأقصى لعدد المجالات التي يمكنك تحديدها لحماية انتحال المجال في جميع نهج مكافحة التصيد الاحتيالي هو 50.

   عند الانتهاء، انقر فوق **"التالي**".

8. في " **إضافة عناوين البريد الإلكتروني والمجالات الموثوق بها لعدم وضع علامة كصفحة انتحال** "، أدخل عناوين البريد الإلكتروني والمجالات المرسلة التي تريد استبعادها من حماية الانتحال. لن يتم وضع علامة على الرسائل الواردة من هؤلاء المرسلين على أنها هجوم انتحال، ولكن لا يزال المرسلون عرضة للمسح الضوئي من قبل عوامل التصفية الأخرى في EOP Defender لـ Office 365.

   أدخل عنوان البريد الإلكتروني أو المجال في المربع، ثم انقر فوق **"إضافة**". كرر هذه الخطوة عدة مرات حسب الضرورة.

   لإزالة إدخال موجود من القائمة، حدد الإدخال، ثم انقر فوق ![إزالة الاستثناءات لأيقونة حماية انتحال الهوية.](../../media/m365-cc-sc-remove.png).

   عند الانتهاء، انقر فوق **"التالي**".

9. في صفحة **المراجعة والتأكيد على هذا النهج** ، تحقق من التحديدات، ثم انقر فوق **"تأكيد**".

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>استخدم مدخل Microsoft 365 Defender لتعديل تعيينات نهج الأمان القياسية والضيقة المحددة مسبقا

خطوات تعديل تعيين نهج الأمان المعين مسبقا **للحماية القياسية** أو **الحماية الصارمة** هي نفسها التي تم [تعيينها في البداية لنهج الأمان المعينة مسبقا للمستخدمين](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

لتعطيل نهج الأمان التي تم تعيينها مسبقا **للحماية القياسية** أو **الحماية الصارمة** مع الحفاظ على الشروط والاستثناءات الحالية، قم بتمديد التبديل إلى **"إيقاف التشغيل المعطل**![".](../../media/scc-toggle-off.png) لتمكين النهج، قم بتحريك التبديل إلى **"تمكين** ![التشغيل](../../media/scc-toggle-on.png)".

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>استخدم مدخل Microsoft 365 Defender لتعديل تعيينات نهج الأمان المضمن الذي تم تعيينه مسبقا للحماية

تذكر أنه يتم تعيين نهج الأمان المعين مسبقا **للحماية المضمنة** لجميع المستلمين، ولا يؤثر على المستلمين الذين تم تعريفهم في نهج الأمان المعينة مسبقا **للحماية القياسية** أو **الحماية الصارمة** أو الارتباطات الآمنة المخصصة أو نهج المرفقات الآمنة.

لذلك، عادة لا نوصي باستثناءات لنهج الأمان المعين مسبقا **للحماية المضمنة** .

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **"نهج التعاون** \> & البريد الإلكتروني **" & نهج** \> **المخاطر** "قواعد\>" **التي تم تعيينها مسبقا لنهج الأمان** في قسم **"نهج القوالب**". للانتقال مباشرة إلى صفحة **نهج الأمان التي تم تعيينها مسبقا** ، استخدم <https://security.microsoft.com/presetSecurityPolicies>.

2. في صفحة **نهج الأمان المحددة مسبقا** ، حدد **"إضافة استثناءات" (غير مستحسن)** في قسم **الحماية المضمنة** .

3. في القائمة المنبثقة " **استبعاد من الحماية المضمنة** " التي تظهر، حدد المستلمين الداخليين المستبعدين من "الارتباطات الآمنة" المضمنة وحماية المرفقات الآمنة:
   - **المستخدمون**
   - **المجموعات**
   - **المجالات**

   انقر في المربع المناسب، وابدأ بكتابة قيمة، وحدد القيمة التي تريدها من النتائج. كرر هذه العملية عدة مرات حسب الضرورة. لإزالة قيمة موجودة، انقر فوق "إزالة" ![إزالة الاستثناءات من أيقونة الحماية المضمنة.](../../media/m365-cc-sc-remove-selection-icon.png) بجوار القيمة.

   بالنسبة للمستخدمين أو المجموعات، يمكنك استخدام معظم المعرفات (الاسم واسم العرض والاسم المستعار وعنوان البريد الإلكتروني واسم الحساب وما إلى ذلك)، ولكن يظهر اسم العرض المقابل في النتائج. بالنسبة للمستخدمين، أدخل علامة نجمية (\*) بحد ذاتها لمشاهدة كافة القيم المتوفرة.

   عند الانتهاء، انقر فوق **حفظ**.

### <a name="how-do-you-know-these-procedures-worked"></a>كيف تعرف أن هذه الإجراءات تعمل؟

للتحقق من أنك قمت بتعيين نهج أمان **الحماية القياسية** أو **الحماية الصارمة** إلى مستخدم بنجاح، استخدم إعداد حماية حيث تكون القيمة الافتراضية مختلفة عن إعداد **الحماية القياسية** ، والذي يختلف عن إعداد **الحماية الصارمة** .

على سبيل المثال، بالنسبة للبريد الإلكتروني الذي تم اكتشافه كبريد عشوائي (ليس بريدا عشوائيا عالي الدقة) تحقق من تسليم الرسالة إلى مجلد "البريد الإلكتروني غير الهام" لمستخدمي **الحماية القياسية** ، ويتم عزلها لمستخدمي **الحماية الصارمة** .

أو، [للبريد المجمع](bulk-complaint-level-values.md)، تحقق من أن قيمة BCL 6 أو أعلى تقوم بتسليم الرسالة إلى مجلد البريد الإلكتروني غير الهام لمستخدمي **الحماية القياسية** ، وتعزل قيمة BCL 4 أو أعلى الرسالة لمستخدمي **الحماية الصارمة** .

## <a name="preset-security-policies-in-exchange-online-powershell"></a>نهج الأمان المسبقة في Exchange Online PowerShell

في PowerShell، تتكون نهج الأمان التي تم تعيينها مسبقا من العناصر التالية:

- **نهج الأمان الفردية**: على سبيل المثال، نهج مكافحة البرامج الضارة ونهج مكافحة البريد العشوائي ونهج مكافحة التصيد الاحتيالي ونهج الارتباطات الآمنة ونهج المرفقات الآمنة.

  > [!WARNING]
  > لا تحاول إنشاء نهج الأمان الفردية المقترنة بنهج الأمان المعينة مسبقا أو تعديلها أو إزالتها. الطريقة الوحيدة المدعومة لإنشاء نهج الأمان الفردية لنهج الأمان القياسية أو الصارمة المعينة مسبقا هي تشغيل نهج الأمان المعين مسبقا في مدخل Microsoft 365 Defender للمرة الأولى.

- **القواعد**: تحدد القواعد المنفصلة لنهج الأمان القياسي المعين مسبقا، ونهج الأمان المحدد مسبقا الصارم، ونهج الأمان المضمن المعين مسبقا للحماية شروط المستلم والاستثناءات للنهج (تحديد المستلمين الذين تنطبق حماية النهج علىهم).

  بالنسبة إلى نهج الأمان القياسية والضيقة المعينة مسبقا، يتم إنشاء هذه القواعد في المرة الأولى التي تقوم فيها بتشغيل نهج الأمان المعين مسبقا في مدخل Microsoft 365 Defender. إذا لم تقم بتشغيل نهج الأمان المعين مسبقا، فإن القواعد المقترنة غير موجودة. بعد ذلك، لا يؤدي إيقاف تشغيل نهج الأمان المعين مسبقا إلى حذف القواعد المقترنة.

  يحتوي نهج الأمان الذي تم إعداده مسبقا للحماية المضمنة على قاعدة واحدة تتحكم في استثناءات للارتباطات الآمنة الافتراضية وحماية المرفقات الآمنة للنهج.

  تتضمن نهج الأمان القياسية والضيقة التي تم تعيينها مسبقا القواعد التالية:

  - **قواعد حماية Exchange Online Protection (EOP):** تتحكم قاعدة نهج الأمان القياسي المحدد مسبقا والقاعدة الخاصة بنهج الأمان المحدد مسبقا الصارم في الأشخاص الذين تطبقهم حماية EOP في النهج (مكافحة البرامج الضارة والبريد العشوائي والتصيد الاحتيالي) على (شروط المستلمين واستثناءات حماية EOP).
  - **قواعد الحماية Defender لـ Office 365**: تتحكم قاعدة نهج الأمان القياسي المحدد مسبقا وقاعدة نهج الأمان المحدد مسبقا الصارم في الأشخاص الذين تنطبق Defender لـ Office 365 الحماية في النهج (الارتباطات الآمنة والمرفقات الآمنة) على (شروط المستلمين واستثناءاتهم Defender لـ Office 365 الحماية).

  تسمح لك قواعد نهج الأمان القياسية والضيقة المعينة مسبقا أيضا بتشغيل نهج الأمان المعين مسبقا أو تشغيله عن طريق تمكين القواعد المقترنة بالنهج أو تعطيلها.

  لا تتوفر قواعد نهج الأمان المحددة مسبقا ل cmdlets القاعدة العادية التي تعمل مع نهج الأمان الفردية (على سبيل المثال، **Get-AntiPhishRule**). بدلا من ذلك، تكون أوامر cmdlets التالية مطلوبة:

  - نهج أمان الحماية المضمنة مسبقا: **\*-ATPBuiltInProtectionRule** cmdlets.
  - نهج الأمان القياسية والصارمة المحددة مسبقا: **\*-EOPProtectionPolicyRule** **و-ATPProtectionPolicyRule\*** cmdlets.

تصف الأقسام التالية كيفية استخدام أوامر cmdlets هذه في **السيناريوهات المدعومة**.

للاتصال Exchange Online PowerShell، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="use-powershell-to-view-individual-security-policies-for-preset-security-policies"></a>استخدام PowerShell لعرض نهج الأمان الفردية لنهج الأمان التي تم تعيينها مسبقا

تذكر، إذا لم تقم بتشغيل نهج الأمان القياسي المعين مسبقا أو نهج الأمان المحدد مسبقا الصارم في مدخل Microsoft 365 Defender، فإن نهج الأمان المقترنة لنهج الأمان المعين مسبقا غير موجودة.

> [!WARNING]
> لا تحاول إنشاء نهج الأمان الفردية المقترنة بنهج الأمان المعينة مسبقا أو تعديلها أو إزالتها. الطريقة الوحيدة المدعومة لإنشاء نهج الأمان الفردية لنهج الأمان القياسية أو الصارمة المعينة مسبقا هي تشغيل نهج الأمان المعين مسبقا في مدخل Microsoft 365 Defender للمرة الأولى.

- **نهج الأمان المعين مسبقا للحماية المضمنة**: تسمى النهج المقترنة Built-In نهج الحماية. قيمة الخاصية IsBuiltInProtection هي True لهذه النهج.

  لعرض نهج الأمان الفردية لنهج الأمان المضمن الذي تم تعيينه مسبقا للحماية، قم بتشغيل الأمر التالي:

  ```powershell
  Write-Output -InputObject ("`r`n"*3),"Built-in protection Safe Attachments policy",("-"*79);Get-SafeAttachmentPolicy -Identity "Built-In Protection Policy" | Format-List; Write-Output -InputObject ("`r`n"*3),"Built-in protection Safe Links policy",("-"*79);Get-SafeLinksPolicy -Identity "Built-In Protection Policy" | Format-List
  ```

- **نهج الأمان القياسي المعين مسبقا**: تتم تسمية `Standard Preset Security Policy<13-digit number>`النهج المقترنة. على سبيل المثال، `Standard Preset Security Policy1622650008019`. قيمة خاصية RecommendPolicyType هي Standard.

  - **المؤسسات التي لا تحتوي على Defender ل Microsoft 365**:

    لعرض نهج الأمان الفردية لنهج الأمان القياسي الذي تم تعيينه مسبقا في المؤسسات دون Defender ل Microsoft 365، قم بتشغيل الأمر التالي:

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"Standard anti-malware policy",("-"*79);Get-MalwareFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard anti-spam policy",("-"*79);Get-HostedContentFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"
    ```

  - **المؤسسات التي تستخدم Defender ل Microsoft 365**:

    لعرض نهج الأمان الفردية لنهج الأمان القياسي الذي تم تعيينه مسبقا في المؤسسات باستخدام Defender ل Microsoft 365، قم بتشغيل الأمر التالي:

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"Standard anti-malware policy",("-"*79);Get-MalwareFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard anti-spam policy",("-"*79);Get-HostedContentFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard Safe Attachments policy",("-"*79);Get-SafeAttachmentPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard Safe Links policy",("-"*79);Get-SafeLinksPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"
    ```

- **نهج أمان مقيد مسبقا**: تتم تسمية النهج المقترنة.`Strict Preset Security Policy<13-digit number>` على سبيل المثال، `Strict Preset Security Policy1642034872546`. قيمة الخاصية RecommendPolicyType مقيدة.

  - **المؤسسات التي لا تحتوي على Defender ل Microsoft 365**:

    - لعرض نهج الأمان الفردية لنهج الأمان المضمن مسبقا في المؤسسات دون Defender ل Microsoft 365، قم بتشغيل الأمر التالي:

      ```powershell
      Write-Output -InputObject ("`r`n"*3),"Strict anti-malware policy",("-"*79);Get-MalwareFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict anti-spam policy",("-"*79);Get-HostedContentFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"
      ```

  - **المؤسسات التي تستخدم Defender ل Microsoft 365**:

    - لعرض نهج الأمان الفردية لنهج الأمان المضمن مسبقا في المؤسسات التي تستخدم Defender for Microsoft 365، قم بتشغيل الأمر التالي:

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"Strict anti-malware policy",("-"*79);Get-MalwareFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict anti-spam policy",("-"*79);Get-HostedContentFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict Safe Attachments policy",("-"*79);Get-SafeAttachmentPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict Safe Links policy",("-"*79);Get-SafeLinksPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"
    ```

### <a name="use-powershell-to-view-rules-for-preset-security-policies"></a>استخدام PowerShell لعرض قواعد نهج الأمان التي تم تعيينها مسبقا

تذكر، إذا لم تقم بتشغيل نهج الأمان القياسي المعين مسبقا أو نهج الأمان المحدد مسبقا في مدخل Microsoft 365 Defender، فلن تكون القواعد المقترنة بهذه النهج موجودة.

- **نهج الأمان المعين مسبقا للحماية المضمنة**: تسمى القاعدة المقترنة ب ATP Built-In Protection Rule.

  لعرض القاعدة المقترنة بنهج الأمان المعين مسبقا للحماية المضمنة، قم بتشغيل الأمر التالي:

  ```powershell
  Get-ATPBuiltInProtectionRule
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-ATPBuiltInProtectionRule](/powershell/module/exchange/get-atpbuiltinprotectionrule).

- **نهج الأمان القياسي المعين مسبقا**: تسمى القواعد المقترنة بنهج الأمان القياسي المعين مسبقا.

  استخدم الأوامر التالية لعرض القواعد المقترنة بنهج الأمان القياسي المعين مسبقا:

  - لعرض القاعدة المقترنة بحمايات EOP في نهج الأمان القياسي المعين مسبقا، قم بتشغيل الأمر التالي:

    ```powershell
    Get-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"
    ```

  - لعرض القاعدة المقترنة بالحماية Defender لـ Office 365 في نهج الأمان القياسي المعين مسبقا، قم بتشغيل الأمر التالي:

    ```powershell
    Get-ATPProtectionPolicyRule -Identity "Standard Preset Security Policy"
    ```

  - لعرض كلتا القواعد في الوقت نفسه، قم بتشغيل الأمر التالي:

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"EOP rule - Standard preset security policy",("-"*79);Get-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"; Write-Output -InputObject ("`r`n"*3),"Defender for Office 365 rule - Standard preset security policy",("-"*79);Get-ATPProtectionPolicyRule -Identity "Standard Preset Security Policy"
    ```

- **نهج أمان مقيد مسبقا**: تسمى القواعد المقترنة "نهج أمان مقيد مسبق الإعداد".

  استخدم الأوامر التالية لعرض القواعد المقترنة بنهج الأمان المحدد مسبقا الصارم:

  - لعرض القاعدة المقترنة بحمايات EOP في نهج الأمان المحدد مسبقا الصارم، قم بتشغيل الأمر التالي:

    ```powershell
    Get-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"
    ```

  - لعرض القاعدة المقترنة بالحماية Defender لـ Office 365 في نهج الأمان المحدد مسبقا، قم بتشغيل الأمر التالي:

    ```powershell
    Get-ATPProtectionPolicyRule -Identity "Strict Preset Security Policy"
    ```

  - لعرض كلتا القواعد في الوقت نفسه، قم بتشغيل الأمر التالي:

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"EOP rule - Strict preset security policy",("-"*79);Get-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"; Write-Output -InputObject ("`r`n"*3),"Defender for Office 365 rule - Strict preset security policy",("-"*79);Get-ATPProtectionPolicyRule -Identity "Strict Preset Security Policy"
    ```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-EOPProtectionPolicyRule](/powershell/module/exchange/get-eopprotectionpolicyrule) و [Get-ATPProtectionPolicyRule](/powershell/module/exchange/get-atpprotectionpolicyrule).

### <a name="use-powershell-to-turn-on-or-turn-off-preset-security-policies"></a>استخدام PowerShell لتشغيل نهج الأمان المحددة مسبقا أو إيقاف تشغيلها

كما هو موضح سابقا، لتشغيل نهج الأمان القياسية أو التقييدية المعينة مسبقا أو إيقاف تشغيلها، يمكنك تمكين القواعد المقترنة بالنهج أو تعطيلها. تظهر قيمة خاصية الحالة للقاعدة ما إذا كانت القاعدة ممكنة أو معطلة.

اعتمادا على ما إذا كان لدى مؤسستك Defender لـ Office 365، قد تحتاج إلى تمكين قاعدة واحدة أو تعطيلها (قاعدة حماية EOP) أو قاعدتين (قاعدة واحدة لحماية EOP، وقاعدة واحدة لحماية Defender لـ Office 365) لتشغيل نهج الأمان المحدد مسبقا أو إيقاف تشغيله.

- **نهج الأمان القياسي المسبق الإعداد**:

  - **المؤسسات التي لا Defender لـ Office 365**:

    - في المؤسسات التي لا تحتوي على Defender لـ Office 365، قم بتشغيل الأمر التالي لتحديد ما إذا كانت القاعدة الخاصة بنهج الإعداد المسبق القياسي ممكنة أو معطلة حاليا:

      ```powershell
      Get-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy" | Format-Table Name,State
      ```

    - قم بتشغيل الأمر التالي لإيقاف تشغيل نهج الأمان القياسي المحدد مسبقا إذا كان قيد التشغيل:

      ```powershell
      Disable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"
      ```

    - قم بتشغيل الأمر التالي لتشغيل نهج الأمان القياسي المحدد مسبقا إذا تم إيقاف تشغيله:

      ```powershell
      Enable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"
      ```

  - **المؤسسات ذات Defender لـ Office 365**:

    - في المؤسسات ذات Defender لـ Office 365، قم بتشغيل الأمر التالي لتحديد ما إذا كانت قواعد نهج الإعداد المسبق القياسي ممكنة أو معطلة حاليا:

      ```powershell
      Write-Output -InputObject ("`r`n"*3),"EOP rule - Standard preset security policy",("-"*63);Get-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy" | Format-Table Name,State; Write-Output -InputObject `r`n,"Defender for Office 365 rule - Standard preset security policy",("-"*63);Get-ATPProtectionPolicyRule -Identity "Standard Preset Security Policy" | Format-Table Name,State
      ```

    - قم بتشغيل الأمر التالي لإيقاف تشغيل نهج الأمان القياسي المحدد مسبقا إذا كان قيد التشغيل:

      ```powershell
      Disable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"; Disable-ATPProtectionPolicyRule -Identity "Standard Preset Security Policy"
      ```

    - قم بتشغيل الأمر التالي لتشغيل نهج الأمان القياسي المحدد مسبقا إذا تم إيقاف تشغيله:

      ```powershell
      Enable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"; Enable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"
      ```

- **نهج أمان مقيد مسبقا**:

  - **المؤسسات التي لا Defender لـ Office 365**:

    - في المؤسسات ذات Defender لـ Office 365، قم بتشغيل الأمر التالي لتحديد ما إذا كانت قاعدة نهج الإعداد المسبق الصارم ممكنة أو معطلة حاليا:

      ```powershell
      Get-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy" | Format-Table Name,State
      ```

    - قم بتشغيل الأمر التالي لإيقاف تشغيل نهج الأمان المحدد مسبقا الصارم إذا كان قيد التشغيل:

      ```powershell
      Disable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"
      ```

    - قم بتشغيل الأمر التالي لتشغيل نهج الأمان المحدد مسبقا الصارم إذا تم إيقاف تشغيله:

      ```powershell
      Enable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"
      ```

  - **المؤسسات ذات Defender لـ Office 365**:

    - في المؤسسات ذات Defender لـ Office 365، قم بتشغيل الأمر التالي لتحديد ما إذا كانت قواعد نهج الإعداد المسبق الصارم ممكنة أو معطلة حاليا:

      ```powershell
      Write-Output -InputObject ("`r`n"*3),"EOP rule - Strict preset security policy",("-"*63);Get-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy" | Format-Table Name,State; Write-Output -InputObject `r`n,"Defender for Office 365 rule - Strict preset security policy",("-"*63);Get-ATPProtectionPolicyRule -Identity "Strict Preset Security Policy" | Format-Table Name,State
      ```

    - قم بتشغيل الأمر التالي لإيقاف تشغيل نهج الأمان المحدد مسبقا الصارم إذا كان قيد التشغيل:

      ```powershell
      Disable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"; Disable-ATPProtectionPolicyRule -Identity "Strict Preset Security Policy"
      ```

    - قم بتشغيل الأمر التالي لتشغيل نهج الأمان المحدد مسبقا الصارم إذا تم إيقاف تشغيله:

      ```powershell
      Enable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"; Enable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"
      ```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Enable-EOPProtectionPolicyRule](/powershell/module/exchange/enable-eopprotectionpolicyrule) و [Enable-ATPProtectionPolicyRule](/powershell/module/exchange/enable-atpprotectionpolicyrule) و [Disable-EOPProtectionPolicyRule](/powershell/module/exchange/disable-eopprotectionpolicyrule) و [Disable-ATPProtectionPolicyRule](/powershell/module/exchange/disable-atpprotectionpolicyrule).

### <a name="use-powershell-to-specify-recipient-conditions-and-exceptions-for-preset-security-policies"></a>استخدام PowerShell لتحديد شروط المستلم واستثناءاته لنهج الأمان التي تم تعيينها مسبقا

> [!IMPORTANT]
  > لا توجد أنواع مختلفة متعددة من الشروط أو الاستثناءات الإضافية؛ إنها شاملة. يتم تطبيق نهج الأمان المعين مسبقا _فقط_ على المستلمين الذين يتطابقون مع _كافة_ عوامل تصفية المستلمين المحددة. على سبيل المثال، يمكنك تكوين شرط عامل تصفية مستلم في النهج بالقيم التالية:
  >
  > - المستلم هو: romain@contoso.com
  > - المستلم هو عضو في: المديرين التنفيذيين
  >
  > يتم تطبيق النهج على romain@contoso.com _فقط_ إذا كان أيضا عضوا في مجموعة المديرين التنفيذيين. إذا لم يكن عضوا في المجموعة، فلن يتم تطبيق النهج عليه.
  >
  > وبالمثل، إذا كنت تستخدم عامل تصفية المستلم نفسه استثناء للنهج، فلن يتم تطبيق النهج على romain@contoso.com _فقط_ إذا كان أيضا عضوا في مجموعة المديرين التنفيذيين. إذا لم يكن عضوا في المجموعة، فإن النهج لا يزال ينطبق عليه.

بالنسبة إلى نهج الأمان المضمن الذي تم تعيينه مسبقا للحماية، يمكنك تحديد استثناءات المستلمين فقط. إذا كانت كافة قيم معلمات الاستثناء فارغة (`$null`)، فلا توجد استثناءات للنهج.

بالنسبة إلى نهج الأمان القياسية والضيقة التي تم تعيينها مسبقا، يمكنك تحديد شروط المستلم واستثناءاته لحماية EOP وحمايات Defender لـ Office 365. إذا كانت كافة الشروط وقيم معلمات الاستثناء فارغة (`$null`)، فلا توجد شروط مستلم أو استثناءات لنهج الأمان القياسية أو الصارمة المحددة مسبقا.

حتى إذا لم يتم تطبيق شروط المستلمين أو استثناءاتهم على نهج أمان معين مسبقا، فإن ما إذا كان النهج مطبقا على كافة المستلمين يعتمد على [ترتيب الأسبقية للنهج](#order-of-precedence-for-preset-security-policies-and-other-policies) كما هو موضح سابقا في هذه المقالة.

- **نهج الأمان الذي تم إعداده مسبقا للحماية المضمنة**:

  استخدم بناء الجملة التالي:

  ```powershell
  Set-ATPBuiltInProtectionRule -Identity "ATP Built-In Protection Rule" -ExceptIfRecipientDomainIs <"domain1","domain2",... | $null> -ExceptIfSentTo <"user1","user2",... | $null> -ExceptIfSentToMemberOf <"group1","group2",... | $null>
  ```

  يزيل هذا المثال كافة استثناءات المستلمين من نهج الأمان المضمن الذي تم تعيينه مسبقا للحماية.

  ```powershell
  Set-ATPBuiltInProtectionRule -Identity "ATP Built-In Protection Rule" -ExceptIfRecipientDomainIs $null -ExceptIfSentTo $null -ExceptIfSentToMemberOf $null
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-ATPBuiltInProtectionRule](/powershell/module/exchange/set-atpbuiltinprotectionrule).

- **نهج أمان محددة مسبقا قياسية أو مقيدة**

  استخدم بناء الجملة التالي:

  ```powershell
  <Set-EOPProtectionPolicyRule | SetAtpProtectionPolicyRule> -Identity "<Standard Preset Security Policy | Strict Preset Security Policy>" -SentTo <"user1","user2",... | $null> -ExceptIfSentTo <"user1","user2",... | $null> -SentToMemberOf <"group1","group2",... | $null> -ExceptIfSentToMemberOf <"group1","group2",... | $null> -RecipientDomainIs <"domain1","domain2",... | $null> -ExceptIfRecipientDomainIs <"domain1","domain2",... | $null>
  ```

  يقوم هذا المثال بتكوين استثناءات من حماية EOP في نهج الأمان القياسي المحدد مسبقا لأعضاء مجموعة التوزيع المسماة "المديرون التنفيذيون".

  ```powershell
  Set-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy" -ExceptIfSentToMemberOf Executives
  ```

  يقوم هذا المثال بتكوين استثناءات من الحماية Defender لـ Office 365 في الأمان المعين مسبقا الصارم لعلب بريد عمليات الأمان المحددة (SecOps).

  ```powershell
  Set-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy" -ExceptIfSentTo "SecOps1","SecOps2"
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-EOPProtectionPolicyRule](/powershell/module/exchange/set-eopprotectionpolicyrule) و [Set-ATPProtectionPolicyRule](/powershell/module/exchange/Set-atpprotectionpolicyrule).
