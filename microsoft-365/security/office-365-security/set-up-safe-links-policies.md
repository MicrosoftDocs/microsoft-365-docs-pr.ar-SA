---
title: إعداد خزينة الارتباطات في Microsoft Defender Office 365
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
description: يمكن للمسؤولين معرفة كيفية عرض خزينة الارتباطات وإعدادات الارتباطات العامة خزينة في Microsoft Defender Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7d4cbaccab3eca371114eec92fe1bf89b2c0e353
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63573865"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>إعداد خزينة الارتباطات في Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> هذه المقالة مخصصة لعملاء الأعمال الذين لديهم [Microsoft Defender Office 365](defender-for-office-365.md). إذا كنت مستخدما منزليا تبحث عن معلومات حول الارتباطات الآمنة في Outlook، فاطلع على [أمان Outlook.com المتقدم](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

خزينة الارتباطات في [Microsoft Defender for Office 365](defender-for-office-365.md) فحص URL لرسائل البريد الإلكتروني الواردة في تدفق البريد، والوقت الذي يتم فيه النقر فوق التحقق من عناوين URL والارتباطات في رسائل البريد الإلكتروني وفي مواقع أخرى. لمزيد من المعلومات، راجع خزينة [ارتباطات في Microsoft Defender Office 365](safe-links.md).

على الرغم من عدم وجود نهج خزينة ارتباطات افتراضي، إلا أن  نهج الأمان المضمن للحماية المسبقة يوفر حماية ارتباطات خزينة لكل المستلمين (المستخدمون غير المحددين في نهج ارتباطات خزينة المخصصة). لمزيد من المعلومات، راجع [سياسات الأمان التي تم الإعداد المسبق لها في EOP و Microsoft Defender Office 365](preset-security-policies.md).

يمكنك أيضا استخدام الإجراءات في هذه المقالة لإنشاء خزينة الارتباطات التي تنطبق على مستخدمين معينين أو مجموعة أو مجالات معينة.

> [!NOTE]
>
> يمكنك تكوين الإعدادات العامة لحماية خزينة الارتباطات **خارج** خزينة الارتباطات. للحصول على الإرشادات، راجع تكوين [الإعدادات خزينة ارتباطات في Microsoft Defender Office 365](configure-global-settings-for-safe-links.md).
>
> يجب على المسؤولين التفكير في إعدادات التكوين المختلفة خزينة الارتباطات. أحد الخيارات المتوفرة هو تضمين معلومات تعريف المستخدم في خزينة الارتباطات. تمكن هذه الميزة *فرق "عمليات* الأمان" من التحقق من اختراق المستخدم المحتمل، واتخاذ إجراء تصحيحي، والحد من الخروقات مكلفة.

يمكنك تكوين سياسات ارتباطات خزينة في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell لمنظمات Microsoft 365 المؤهلة التي بها علب بريد في Exchange Online؛ EOP PowerShell مستقل ل المؤسسات التي لا يمكنها Exchange Online علب البريد، ولكن باستخدام Microsoft Defender Office 365 اشتراكات الوظائف الإضافية).

إن العناصر الأساسية لن نهج ارتباطات خزينة هي:

- نهج الارتباطات **الآمنة: قم** تشغيل حماية ارتباطات خزينة، و تشغيل مسح URL في الوقت الحقيقي، وحدد ما إذا كنت تريد الانتظار حتى اكتمال الفحص في الوقت الحقيقي قبل تسليم الرسالة، و تشغيل الفحص بحثا عن الرسائل الداخلية، وتحديد ما إذا كنت تريد تعقب نقرات المستخدم على عناوين URL، وتحديد ما إذا كنت تريد السماح للمستخدمين بالنقر فوق Trough إلى عنوان URL الأصلي.
- **قاعدة الارتباطات الآمنة**: تحدد عوامل تصفية الأولوية والمستلم (الشخص الذي ينطبق عليه النهج).

لا يكون الفرق بين هذين العنصرين واضحا عند إدارة خزينة الارتباطات في مدخل Microsoft 365 Defender:

- عند إنشاء نهج ارتباطات خزينة، تقوم في الواقع بإنشاء قاعدة ارتباطات آمنة ون نهج الارتباطات الآمنة المقترنة به في الوقت نفسه باستخدام نفس الاسم لكل منهما.
- عند تعديل نهج ارتباطات خزينة، تقوم الإعدادات المرتبطة بالاسم والأولوية والممكن أو المعطل وتصفية المستلم بتعديل قاعدة الارتباطات الآمنة. تقوم كل الإعدادات الأخرى بتعديل نهج الارتباطات الآمنة المقترنة.
- عند إزالة نهج ارتباطات خزينة، تتم إزالة قاعدة الارتباطات الآمنة ون نهج الارتباطات الآمنة المقترنة.

في Exchange Online PowerShell أو EOP PowerShell مستقل، يمكنك إدارة النهج والقاعدة بشكل منفصل. لمزيد من المعلومات، راجع القسم استخدام [Exchange Online PowerShell أو EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) مستقل لتكوين خزينة الارتباطات لاحقا في هذه المقالة.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة ارتباطات خزينة **،** استخدم <https://security.microsoft.com/safelinksv2>.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع الاتصال [Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- يجب تعيين أذونات لك قبل أن تتمكن من تنفيذ الإجراءات في هذه المقالة:
  - لإنشاء سياسات ارتباطات خزينة وتعديلها وحذفها، يجب أن تكون عضوا في مجموعات دور مسؤول إدارة المؤسسة أو مسؤول  الأمان في مدخل  Microsoft 365 Defender وعضوا في مجموعة دور إدارة المؤسسة في Exchange Online. 
  - للوصول للقراءة فقط إلى خزينة الارتباطات، يجب أن تكون عضوا في مجموعات دور قارئ الشاشة العام أو قارئ الأمان.

  لمزيد من المعلومات، راجع الأذونات في [Microsoft 365 Defender والأذونات](permissions-microsoft-365-security-center.md) [في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 للمستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender والأذونات للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  . - توفر **مجموعة دور** "إدارة [المؤسسات"](/Exchange/permissions-exo/permissions-exo#role-groups) Exchange Online طريقة العرض فقط حق الوصول للقراءة فقط إلى الميزة.

- للحصول على الإعدادات المستحسنة خزينة الارتباطات، راجع خزينة [نهج الارتباطات](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- السماح بتطبيق نهج جديد أو محدث لمدة تصل إلى 6 ساعات.

- [يتم باستمرار إضافة الميزات الجديدة إلى Microsoft Defender Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). عند إضافة ميزات جديدة، قد تحتاج إلى إجراء تعديلات على سياسات الارتباطات خزينة الموجودة.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>استخدام مدخل Microsoft 365 Defender لإنشاء خزينة الارتباطات

يؤدي إنشاء نهج ارتباطات خزينة مخصص في مدخل Microsoft 365 Defender إلى إنشاء قاعدة الارتباطات الآمنة ون نهج الارتباطات الآمنة المقترنة في الوقت نفسه باستخدام الاسم نفسه لكليهما.

1. في Microsoft 365 Defender على <https://security.microsoft.com>، انتقل إلى  البريد الإلكتروني **&** \>  \> \> سياسات التعاون & قواعد خزينة **الارتباطات** في **القسم "سياسات**". الانتقال مباشرة إلى صفحة ارتباطات خزينة **،** استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **خزينة الارتباطات**، انقر فوق إنشاء ![أيقونة.](../../media/m365-cc-sc-create-icon.png) **إنشاء**.

3. يتم **فتح معالج خزينة ارتباطات** جديدة. في صفحة **تسمية النهج** ، قم بتكوين الإعدادات التالية:

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

   - **استبعاد هؤلاء المستخدمين** والمجموعات والمجالات: لإضافة استثناءات للمستلمين الداخليين التي ينطبق عليها النهج (استثناءات المستلمين)، حدد هذا الخيار وتكوين الاستثناءات. تشبه الإعدادات والسلوك الشروط تماما.

   عند الانتهاء، انقر فوق **التالي**.

5. في **الصفحة إعدادات الحماية** التي تظهر، قم بتكوين الإعدادات التالية:
   - **حدد الإجراء الخاص عناوين URL** غير المعروفة التي من المحتمل أن تكون ضارة في الرسائل: حدد على لتمكين خزينة الارتباطات للربطات في رسائل البريد الإلكتروني. إذا قمت ب تشغيل هذا الإعداد، تتوفر الإعدادات التالية:
     - **تطبيق مسح عناوين URL** في الوقت الحقيقي للربطات المريبة والربطات التي تشير إلى الملفات: حدد هذا الخيار لتمكين مسح الارتباطات في الوقت الحقيقي في رسائل البريد الإلكتروني. إذا قمت ب تشغيل هذا الإعداد على الإعداد التالي فهو متوفر:
       - **انتظر حتى تكتمل** عملية مسح URL قبل تسليم الرسالة: حدد هذا الخيار لانتظار اكتمال فحص URL في الوقت الحقيقي قبل تسليم الرسالة.
     - **تطبيق خزينة ارتباطات** إلى رسائل البريد الإلكتروني المرسلة داخل المؤسسة: حدد هذا الخيار لتطبيق نهج ارتباطات خزينة على الرسائل بين المرسلين الداخليين والمستلمين الداخليين.
   - **حدد الإجراء URL** غير معروف أو يحتمل أن يكون ضارا ضمن Microsoft Teams: حدد على لتمكين خزينة  الارتباطات للربطات في Teams. تجدر الإشارة إلى أن هذا الإعداد قد يستغرق ما يصل إلى 24 ساعة حتى يتم تطبيق هذا الإعداد.
   - **عدم تعقب نقرات المستخدم**: اترك هذا الإعداد غير محدد لتمكين المستخدم المتعقب ينقر فوق عناوين URL في رسائل البريد الإلكتروني.
   - **لا تسمح للمستخدمين** بالنقر فوق عنوان URL الأصلي: حدد هذا الخيار لمنع المستخدمين من النقر فوق عنوان URL الأصلي في [صفحات التحذير](safe-links.md#warning-pages-from-safe-links).
   - **لا تعيد كتابة عناوين URL** التالية: تسمح بالوصول إلى عناوين URL المحددة التي كانت ستحظرها خزينة الارتباطات.

     في المربع، اكتب عنوان URL أو القيمة التي تريدها، ثم انقر فوق **إضافة**. كرر هذه الخطوة قدر ما يلزم.

     لإزالة إدخال موجود، انقر فوق ![أيقونة إزالة.](../../media/m365-cc-sc-remove-selection-icon.png) بجانب الإدخال.

     للحصول على بناء جملة الإدخال، راجع بناء جملة الإدخال [للقائمة "](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list)عدم إعادة كتابة عناوين URL التالية".

   للحصول على معلومات مفصلة حول هذه الإعدادات، راجع خزينة [الارتباطات](safe-links.md#safe-links-settings-for-email-messages) لرسائل البريد الإلكتروني [وإعدادات خزينة الارتباطات Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).

   لمزيد من القيم الموصى بها لإعدادات النهج القياسية والتقيدية، راجع خزينة [نهج الارتباطات](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   عند الانتهاء، انقر فوق **التالي**.

6. في صفحة **الإعلام** التي تظهر، حدد إحدى القيم التالية حول كيف تريد إعلام **المستخدمين؟**:
   - **استخدام نص الإعلام الافتراضي**
   - **استخدام نص إعلام مخصص**: إذا حددت هذه القيمة (لا يمكن أن يتجاوز الطول 200 حرف)، تظهر الإعدادات التالية:
     - **استخدام المترجم من Microsoft الترجمة التلقائية**
     - **نص إعلام مخصص**: أدخل نص الإعلام المخصص في هذا المربع.

   عند الانتهاء، انقر فوق **التالي**.

7. على الصفحة **مراجعة** التي تظهر، راجع الإعدادات. يمكنك تحديد **تحرير** في كل مقطع لتعديل الإعدادات ضمن المقطع. أو يمكنك النقر فوق **الخلف** أو تحديد الصفحة المحددة في المعالج.

   عند الانتهاء، انقر فوق **إرسال**.

8. على صفحة التأكيد التي تظهر، انقر فوق **تم**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>استخدام مدخل Microsoft 365 Defender لعرض خزينة الارتباطات

1. في Microsoft 365 Defender على <https://security.microsoft.com>، انتقل إلى  البريد الإلكتروني **&** \>  \> \> سياسات التعاون & قواعد خزينة **الارتباطات** في **القسم "سياسات**". الانتقال مباشرة إلى صفحة ارتباطات خزينة **،** استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **خزينة الارتباطات**، يتم عرض الخصائص التالية في قائمة خزينة الارتباطات:
   - **الاسم**
   - **الحالة**
   - **الأولوية**

3. عند تحديد نهج بالنقر فوق الاسم، يتم عرض إعدادات النهج في قائمة منسقة.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>استخدام مدخل Microsoft 365 Defender لتعديل خزينة الارتباطات

1. في مدخل Microsoft 365 Defender،  \>  \>  \> انتقل إلى قسم & "سياسات التهديدات" خزينة **الارتباطات**.

2. في صفحة **خزينة الارتباطات**، حدد نهج من القائمة بالنقر فوق الاسم.

3. في قائمة تفاصيل النهج التي تظهر، حدد **تحرير** في كل مقطع لتعديل الإعدادات ضمن المقطع. لمزيد من المعلومات حول الإعدادات، راجع المقطع السابق استخدام مدخل Microsoft 365 Defender لإنشاء [خزينة الارتباطات](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) في هذه المقالة.

لتمكين نهج أو تعطيله أو تعيين ترتيب أولوية النهج، راجع المقاطع التالية.

### <a name="enable-or-disable-safe-links-policies"></a>تمكين سياسات الارتباطات خزينة أو تعطيلها

1. في Microsoft 365 Defender على <https://security.microsoft.com>، انتقل إلى  البريد الإلكتروني **&** \>  \> \> سياسات التعاون & قواعد خزينة **الارتباطات** في **القسم "سياسات**". الانتقال مباشرة إلى صفحة ارتباطات خزينة **،** استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **خزينة الارتباطات**، حدد نهج من القائمة بالنقر فوق الاسم.

3. في أعلى قائمة تفاصيل النهج التي تظهر، سترى إحدى القيم التالية:
   - **إيقاف تشغيل النهج**: ل تشغيل النهج، انقر فوق أيقونة ![تشغيل.](../../media/m365-cc-sc-turn-on-off-icon.png) **قم تشغيل** .
   - **تشغيل النهج**: إيقاف تشغيل النهج، انقر فوق ![أيقونة إيقاف التشغيل.](../../media/m365-cc-sc-turn-on-off-icon.png) **إيقاف التشغيل**.

4. في مربع حوار التأكيد الذي يظهر، انقر فوق **تشغيل** أو **إيقاف تشغيل**.

5. انقر **فوق** إغلاق في مناصة تفاصيل النهج.

عند العودة إلى صفحة النهج الرئيسية، ستكون  قيمة حالة النهج في **وضع التشغيل** أو **إيقاف التشغيل**.

### <a name="set-the-priority-of-safe-links-policies"></a>تعيين أولوية خزينة الارتباطات

بشكل افتراضي، خزينة الارتباطات ذات الأولوية التي تستند إلى الترتيب الذي تم إنشاؤها به (تكون السياسات الجديدة ذات أولوية أقل من تلك التي يتم تعيينها إلى سياسات قديمة). يشير رقم الأولوية الأدنى إلى أولوية أعلى بالنسبة إلى النهج (0 هو الأعلى)، كما تتم معالجة النهج وفقا ترتيب الأولوية (تتم معالجة نهج الأولوية العليا قبل النهج ذات الأولوية الدنيا). لا يمكن أن تكون الأولوية نفسها لنهجين، وتتوقف معالجة النهج بعد تطبيق النهج الأول.

لتغيير أولوية النهج، انقر فوق زيادة الأولوية أو إنقاص الأولوية في  خصائص النهج (لا يمكنك تعديل رقم الأولوية مباشرة في مدخل Microsoft 365 Defender).  لا يكون تغيير أولوية النهج منطقيا إلا إذا كان لديك نهج متعددة.

**ملاحظة**:

- في Microsoft 365 Defender، يمكنك فقط تغيير أولوية نهج الارتباطات خزينة بعد إنشائها. في PowerShell، يمكنك تجاوز الأولوية الافتراضية عند إنشاء قاعدة الارتباطات الآمنة (التي يمكن أن تؤثر على أولوية القواعد الموجودة).
- خزينة معالجة نهج الارتباطات بالترتيب الذي يتم عرضه فيه (النهج الأول له القيمة **الأولوية** 0). لمزيد من المعلومات حول ترتيب الأسبقية وكيفية تقييم عدة سياسات وتطبيقها، راجع ترتيب [حماية البريد الإلكتروني وأسبقيته](how-policies-and-protections-are-combined.md).

1. في Microsoft 365 Defender على <https://security.microsoft.com>، انتقل إلى  البريد الإلكتروني **&** \>  \> \> سياسات التعاون & قواعد خزينة **الارتباطات** في **القسم "سياسات**". الانتقال مباشرة إلى صفحة ارتباطات خزينة **،** استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **خزينة الارتباطات**، حدد نهج من القائمة بالنقر فوق الاسم.

3. في أعلى القائمة العلوية التفاصيل الخاصة ب النهج التي تظهر، سترى زيادة الأولوية أو إنقاص  الأولوية استنادا إلى  قيمة الأولوية الحالية وعدد النهج المخصصة:
   - يتوفر النهج الذي به **القيمة الأولوية** **0** فقط خيار **إنقاص** الأولوية.
   - يتوفر النهج الذي به أقل قيمة **أولوية** (على سبيل المثال **، 3**) خيار **زيادة** الأولوية فقط.
   - إذا كان لديك ثلاثة سياسات أو أكثر، فإن الخيارات المتوفرة بين القيم ذات الأولوية الأعلى والأدنى هي الخيارات "زيادة  الأولوية" و"إنقاص الأولوية".

   انقر ![فوق زيادة أيقونة الأولوية.](../../media/m365-cc-sc-increase-icon.png) **زيادة الأولوية** أو ![أيقونة إنقاص الأولوية](../../media/m365-cc-sc-decrease-icon.png) **إنقاص** الأولوية لتغيير **قيمة الأولوية** .

4. عند الانتهاء، انقر فوق **إغلاق** في منتهى تفاصيل النهج.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>استخدام مدخل Microsoft 365 Defender لإزالة خزينة الارتباطات

1. في مدخل Microsoft 365 Defender،  \>  \>  \> انتقل إلى & البريد الإلكتروني ونهج التعاون & القواعد خزينة **الارتباطات** في **المقطع** "سياسات".

2. في صفحة **خزينة الارتباطات**، حدد نهج من القائمة بالنقر فوق الاسم. في أعلى قائمة تفاصيل النهج التي تظهر، انقر فوق أيقونة ![المزيد من الإجراءات.](../../media/m365-cc-sc-more-actions-icon.png) **المزيد من الإجراءات** \> ![أيقونة حذف النهج](../../media/m365-cc-sc-delete-icon.png) **حذف النهج**.

3. في مربع حوار التأكيد الذي يظهر، انقر فوق **نعم**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>استخدام Exchange Online PowerShell أو EOP PowerShell مستقل لتكوين خزينة الارتباطات

كما هو موضح مسبقا، يتكون خزينة ارتباطات الأمان من نهج ارتباطات آمنة ومن قاعدة ارتباطات آمنة.

في PowerShell، يظهر الفرق بين سياسات الارتباطات الآمنة وقواعد الارتباطات الآمنة. يمكنك إدارة سياسات **\*الارتباطات الآمنة باستخدام الأمرين -SafeLinksPolicy cmdlets****\*، وإدارة قواعد الارتباطات الآمنة باستخدام الأمرين -SafeLinksRule** cmdlets.

- في PowerShell، يمكنك إنشاء نهج الارتباطات الآمنة أولا، ثم إنشاء قاعدة الارتباطات الآمنة التي تحدد النهج الذي تنطبق عليه القاعدة.
- في PowerShell، يمكنك تعديل الإعدادات في نهج الارتباطات الآمنة مع قاعدة الارتباطات الآمنة بشكل منفصل.
- عند إزالة نهج ارتباطات آمنة من PowerShell، لا تتم إزالة قاعدة الارتباطات الآمنة المقابلة تلقائيا، والعكس صحيح.

### <a name="use-powershell-to-create-safe-links-policies"></a>استخدام PowerShell لإنشاء خزينة الارتباطات

إن إنشاء خزينة الارتباطات في PowerShell عملية من خطوتين:

1. إنشاء نهج الارتباطات الآمنة.
2. أنشئ قاعدة الارتباطات الآمنة التي تحدد نهج الارتباطات الآمنة الذي تنطبق عليه القاعدة.

> [!NOTE]
>
> - يمكنك إنشاء قاعدة ارتباطات آمنة جديدة وتعيين نهج ارتباطات آمنة موجود وغير مفروق لها. لا يمكن تقترن قاعدة الارتباطات الآمنة بأكثر من نهج ارتباطات آمنة واحد.
>
> - يمكنك تكوين الإعدادات التالية على نهج الارتباطات الآمنة الجديدة في PowerShell غير المتوفرة في مدخل Microsoft 365 Defender إلا بعد إنشاء النهج:
>   - إنشاء النهج الجديد ك معطل (_ممكن_ `$false` على **cmdlet New-SafeLinksRule** ).
>   - تعيين أولوية النهج أثناء الإنشاء (_الأولوية_ _\<Number\>_) على **cmdlet New-SafeLinksRule** ).
>
> - لن يكون نهج الارتباطات الآمنة الجديد الذي تقوم بإنشاءه في PowerShell مرئيا في مدخل Microsoft 365 Defender حتى تقوم بتعيين النهج إلى قاعدة ارتباطات آمنة.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>الخطوة 1: استخدام PowerShell لإنشاء نهج ارتباطات آمنة

لإنشاء نهج ارتباطات آمنة، استخدم بناء الجملة هذا:

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-IsEnabled <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-DoNotAllowClickThrough <$true | $false>] [-DoNotTrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - للحصول على تفاصيل حول بناء جملة الإدخال الذي يجب استخدامه لمعلمة _DoNotRewriteUrls_ ، راجع بناء جملة الإدخال لقائمة "عدم إعادة كتابة عناوين [URL التالية](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list)".
>
> - للحصول على بناء جملة إضافي يمكنك استخدامه لمعلمة _DoNotRewriteUrls_ عند تعديل سياسات الارتباطات الآمنة الموجودة باستخدام الأمر **cmdlet Set-SafeLinksPolicy** ، راجع المقطع استخدام [PowerShell](#use-powershell-to-modify-safe-links-policies) لتعديل سياسات الارتباطات الآمنة لاحقا في هذه المقالة.

ينشئ هذا المثال نهج ارتباطات آمنة يسمى Contoso All مع القيم التالية:

- تشغيل مسح URL وإعادة كتابته في رسائل البريد الإلكتروني.
- تشغيل مسح URL في Teams.
- قم تشغيل المسح الضوئي في الوقت الحقيقي من عناوين URL التي تم النقر فوقها، بما في ذلك الارتباطات التي تم النقر فوقها والتي تشير إلى الملفات.
- انتظر حتى تكتمل عملية فحص عنوان URL قبل تسليم الرسالة.
- تشغيل مسح URL وإعادة كتابته للرسائل الداخلية.
- تعقب نقرات المستخدم المتعلقة خزينة الارتباطات (لا نستخدم معلمة _DoNotTrackUserClicks_، والقيمة الافتراضية $false، مما يعني أنه يتم تعقب نقرات المستخدم).
- لا تسمح للمستخدمين بالنقر فوق عنوان URL الأصلي.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -IsEnabled $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -DoNotAllowClickThrough $true
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>الخطوة 2: استخدام PowerShell لإنشاء قاعدة ارتباطات آمنة

لإنشاء قاعدة ارتباطات آمنة، استخدم بناء الجملة هذا:

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

ينشئ هذا المثال قاعدة ارتباطات آمنة باسم Contoso All بالشروط التالية:

- تقترن القاعدة ب نهج الارتباطات الآمنة المسمى Contoso All.
- تنطبق القاعدة على كل المستلمين في contoso.com المجال.
- نظرا لأننا لا نستخدم معلمة _الأولوية_ ، يتم استخدام الأولوية الافتراضية.
- يتم تمكين القاعدة (لا نستخدم المعلمة _Enabled_ ، والقيمة الافتراضية هي `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>استخدام PowerShell لعرض سياسات الارتباطات الآمنة

لعرض سياسات الارتباطات الآمنة الموجودة، استخدم بناء الجملة التالي:

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

يرجع هذا المثال قائمة ملخصة بكل سياسات الارتباطات الآمنة.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

يرجع هذا المثال معلومات مفصلة حول نهج الارتباطات الآمنة المسمى مديرو Contoso التنفيذيون.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>استخدام PowerShell لعرض قواعد الارتباطات الآمنة

لعرض قواعد الارتباطات الآمنة الموجودة، استخدم بناء الجملة التالي:

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

يرجع هذا المثال قائمة موجزة بكل قواعد الارتباطات الآمنة.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

لتصفية القائمة حسب القواعد التي تم تمكينها أو تعطيلها، يمكنك تشغيل الأوامر التالية:

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

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>استخدام PowerShell لتعديل سياسات الارتباطات الآمنة

لا يمكنك إعادة تسمية نهج ارتباطات آمنة في PowerShell (لا يوجد في **الأمر Set-SafeLinksPolicy** cmdlet _معلمة_ الاسم). عند إعادة تسمية نهج ارتباطات خزينة في مدخل Microsoft 365 Defender، تقوم بإعادة تسمية قاعدة الارتباطات _الآمنة فقط_.

إن الاعتبار الإضافي الوحيد لتعديل سياسات الارتباطات الآمنة في PowerShell هو بناء الجملة المتوفر لمعلمة _DoNotRewriteUrls_ (القائمة "عدم إعادة كتابة عناوين [URL التالية"](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)):

- لإضافة قيم ستحل محل أي إدخالات موجودة، استخدم بناء الجملة التالي: `"Entry1","Entry2,..."EntryN"`.
- لإضافة قيم أو إزالتها دون التأثير على الإدخالات الأخرى الموجودة، استخدم بناء الجملة التالي: `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

بخلاف ذلك، تتوفر الإعدادات نفسها عند إنشاء نهج ارتباطات آمنة كما هو موضح في الخطوة [1: استخدام PowerShell](#step-1-use-powershell-to-create-a-safe-links-policy) لإنشاء قسم نهج الارتباطات الآمنة السابق في هذه المقالة.

لتعديل نهج الارتباطات الآمنة، استخدم بناء الجملة هذا:

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>استخدام PowerShell لتعديل قواعد الارتباطات الآمنة

الإعداد الوحيد الذي لا يتوفر عند تعديل قاعدة ارتباطات آمنة في PowerShell هو المعلمة _Enabled_ التي تسمح لك بإنشاء قاعدة معطلة. لتمكين قواعد الارتباطات الآمنة الموجودة أو تعطيلها، راجع المقطع التالي.

بخلاف ذلك، تتوفر الإعدادات نفسها عند إنشاء قاعدة كما هو موضح في الخطوة [2: استخدام PowerShell](#step-2-use-powershell-to-create-a-safe-links-rule) لإنشاء مقطع قاعدة ارتباطات آمنة سابقا في هذه المقالة.

لتعديل قاعدة ارتباطات آمنة، استخدم بناء الجملة هذا:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>استخدام PowerShell لتمكين قواعد الارتباطات الآمنة أو تعطيلها

يؤدي تمكين قاعدة ارتباطات آمنة أو تعطيلها في PowerShell إلى تمكين نهج ارتباطات خزينة بالكامل أو تعطيله (قاعدة الارتباطات الآمنة ونمط الارتباطات الآمنة المعين).

لتمكين قاعدة ارتباطات آمنة أو تعطيلها في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

يعطل هذا المثال قاعدة الارتباطات الآمنة المسماة قسم التسويق.

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

يمكن هذا المثال القاعدة نفسها.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Enable-SafeLinksRule](/powershell/module/exchange/enable-safelinksrule) و [Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>استخدام PowerShell لتعيين أولوية قواعد الارتباطات الآمنة

إن أعلى قيمة أولوية يمكنك تعيينها على قاعدة هي 0. تعتمد أقل قيمة يمكنك تعيينها على عدد القواعد. على سبيل المثال، إذا كان لديك خمس قواعد، يمكنك استخدام قيم الأولوية من 0 إلى 4. قد يكون لتغيير أولوية قاعدة موجودة تأثير تتالي على قواعد أخرى. على سبيل المثال، إذا كان لديك خمس قواعد مخصصة (الأولويات من 0 إلى 4)، ثم قمت بتغيير أولوية القاعدة إلى 2، يتم تغيير القاعدة الموجودة ذات الأولوية 2 إلى الأولوية 3، وتتغير القاعدة ذات الأولوية 3 إلى الأولوية 4.

لتعيين أولوية قاعدة الارتباطات الآمنة في PowerShell، استخدم بناء الجملة التالي:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

يحدد هذا المثال أولوية القاعدة المسماة قسم التسويق إلى 2. يتم تقليل كل القواعد الموجودة التي لها أولوية أقل من أو تساوي 2 بمقدار 1 (يتم زيادة أرقام أولوياتها بمقدار 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> لتعيين أولوية قاعدة جديدة عند إنشائها، استخدم المعلمة _Priority_ على **cmdlet New-SafeLinksRule** بدلا من ذلك.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>استخدام PowerShell لإزالة سياسات الارتباطات الآمنة

عند استخدام PowerShell لإزالة نهج ارتباطات آمنة، لا تتم إزالة قاعدة الارتباطات الآمنة المقابلة.

لإزالة نهج ارتباطات آمنة في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

يزيل هذا المثال نهج الارتباطات الآمنة المسمى قسم التسويق.

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>استخدام PowerShell لإزالة قواعد الارتباطات الآمنة

عند استخدام PowerShell لإزالة قاعدة ارتباطات آمنة، لن تتم إزالة نهج الارتباطات الآمنة المقابل.

لإزالة قاعدة ارتباطات آمنة في PowerShell، استخدم بناء الجملة هذا:

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

يزيل هذا المثال قاعدة الارتباطات الآمنة المسماة قسم التسويق.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

للتحقق من أن خزينة الارتباطات تقوم بالمسح الضوئي للرسائل، تحقق من Microsoft Defender المتوفر Office 365 التقارير. لمزيد من المعلومات، راجع [عرض تقارير ل Defender for Office 365](view-reports-for-mdo.md) [واستخدام المستكشف في Microsoft 365 Defender المدخل](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>كيف يمكنك معرفة كيفية عمل هذه الإجراءات؟

للتحقق من نجاح إنشاء أو تعديل أو إزالة خزينة الارتباطات، قم بأي من الخطوات التالية:

- في صفحة **خزينة الارتباطات** في Microsoft 365 Defender <https://security.microsoft.com/safelinksv2>في ، تحقق من قائمة السياسات وقيم الحالة **وقيم الأولوية** الخاصة بها. لعرض المزيد من التفاصيل، حدد النهج من القائمة، وانظر التفاصيل في القائمة المطيرة.

- في Exchange Online PowerShell أو Exchange Online Protection PowerShell\<Name\>، استبدل باسم النهج أو القاعدة، ثم ادير الأمر التالي وتحقق من الإعدادات:

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
