---
title: إعدادات البريد الإلكتروني التي أبلغ عنها المستخدم للبريد العشوائي والتصيد الاحتيالي كبرميل ضار
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 07/19/2022
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: يمكن للمسؤولين التعرف على كيفية تحديد علبة بريد مخصصة (تعرف أيضا باسم علبة بريد عمليات إرسال المستخدم) لجمع رسائل البريد العشوائي والتصيد الاحتيالي التي يتم الإبلاغ عنها من قبل المستخدمين. تكمل الإعدادات الأخرى تجربة إعداد التقارير للمستخدمين عند الإبلاغ عن الرسائل.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c32d4ff27d44600ebe182f0764cb47c638a354c7
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051657"
---
# <a name="user-reported-message-settings"></a>إعدادات الرسائل التي أبلغ عنها المستخدم

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في مؤسسات Microsoft 365 التي تحتوي على علب بريد Exchange Online، يمكنك توجيه البريد إلى علبة بريد مخصصة (تعرف أيضا _بعلبة بريد عمليات إرسال المستخدم_) عندما يبلغ المستخدمون عن رسائل ضارة أو غير ضارة. عندما يقوم المستخدمون بالإبلاغ عن رسائل البريد الإلكتروني باستخدام خيارات التقارير المعتمدة، يمكن للمسؤولين تكوين إعدادات الرسائل التي أبلغ عنها المستخدم في مؤسستهم لإرسال الرسائل المبلغ عنها إلى علبة بريد عمليات إرسال المستخدم. يمكنك تكوين علبة بريد عمليات إرسال المستخدم لاعتراض الرسائل التي أبلغ عنها المستخدم (إرسال إلى علبة بريد عمليات إرسال المستخدم فقط) أو تلقي نسخ من الرسائل التي أبلغ عنها المستخدم عندما يقوم المستخدمون بالإبلاغ عن الرسائل إلى Microsoft. كانت هذه الإعدادات تعرف سابقا باسم _نهج عمليات إرسال المستخدم_.

تعمل إعدادات الرسالة التي أبلغ عنها المستخدم وعلبة بريد عمليات إرسال المستخدم مع خيارات إعداد التقارير عن الرسائل التالية:

- [الوظيفة الإضافية "رسالة التقرير"](enable-the-report-message-add-in.md)
- [الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي"](enable-the-report-phish-add-in.md)
- [أدوات إعداد التقارير لجهة خارجية](#third-party-reporting-tools-options)

يسمح تسليم الرسائل التي أبلغ عنها المستخدم إلى علبة بريد عمليات إرسال المستخدم بدلا من إرسالها مباشرة إلى Microsoft للمسؤولين بالإبلاغ عن الرسائل بشكل انتقائي ويدوي إلى Microsoft على صفحة **عمليات الإرسال** في <https://security.microsoft.com/reportsubmission>. لمزيد من المعلومات، راجع [مسؤول الإرسال](admin-submission.md).

  > [!NOTE]
  > إذا تم تعطيل إعداد التقارير [في Outlook على ويب](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web)، فسيؤدي تمكين الرسائل التي أبلغ عنها المستخدم هنا إلى تجاوز هذا الإعداد والسماح للمستخدمين بالإبلاغ عن الرسائل في Outlook على ويب مرة أخرى.

## <a name="configuration-requirements-for-the-user-submissions-mailbox"></a>متطلبات التكوين لعلبة بريد عمليات إرسال المستخدم

قبل البدء، تحتاج yu إلى تكوين Exchange Online Protection Defender لـ Office 365 بحيث يتم تسليم الرسائل التي أبلغ عنها المستخدم إلى علبة بريد عمليات إرسال المستخدم دون تصفيتها كما هو موضح في الخطوات التالية:

- حدد علبة بريد عمليات إرسال المستخدم كعلبة بريد SecOps. للحصول على الإرشادات، راجع [استخدام مدخل Microsoft 365 Defender لتكوين علب بريد SecOps في نهج التسليم المتقدم](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

- إنشاء نهج مخصص لمكافحة البرامج الضارة لعل بريد عمليات إرسال المستخدم مع الإعدادات التالية:

  - إيقاف تشغيل الإزالة التلقائية بدون ساعة (ZAP) للبرامج الضارة (قسم \>**إعدادات الحماية** لم يتم تحديد عملية **الإزالة التلقائية بدون ساعة للبرامج الضارة** أو `-ZapEnabled $false` في PowerShell).

  - إيقاف تشغيل تصفية المرفقات الشائعة (قسم \>**إعدادات الحماية**، لم يتم تحديد **عامل تصفية المرفقات الشائع** أو `EnableFileFilter $false` في PowerShell).
  
  للحصول على الإرشادات، راجع [إنشاء نهج مكافحة البرامج الضارة](configure-anti-malware-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-malware-policies).

- تحقق من أن علبة بريد عمليات إرسال المستخدم غير مضمنة في نهج الأمان **القياسية** أو **الصارمة** التي تم تعيينها مسبقا. للحصول على الإرشادات، راجع [نهج الأمان التي تم تعيينها مسبقا](preset-security-policies.md).

- **Defender لـ Office 365**: تكوين الإعدادات الإضافية التالية:

  - استبعاد علبة بريد عمليات إرسال المستخدم من نهج الأمان **المضمن** الذي تم تعيينه مسبقا. للحصول على الإرشادات، راجع [نهج الأمان التي تم تعيينها مسبقا](preset-security-policies.md).

  - إنشاء نهج "المرفقات الآمنة" لعلب بريد عمليات إرسال المستخدم حيث يتم إيقاف تشغيل المسح الضوئي للمرفقات الآمنة، بما في ذلك التسليم الديناميكي، **(قسم** \> **الاستجابة للبرامج الضارة غير المعروفة في "المرفقات الآمنة** **للإعدادات**\>" أو `-Enable $false` في PowerShell). للحصول على الإرشادات، راجع [إعداد نهج المرفقات الآمنة في Microsoft Defender لـ Office 365](set-up-safe-attachments-policies.md).

  - إنشاء نهج ارتباطات آمنة لعلب بريد عمليات إرسال المستخدم حيث يتم إيقاف تشغيل المسح الضوئي للارتباطات الآمنة في البريد الإلكتروني (**URL & النقر فوق إعدادات الحماية** **قيد التشغيل: تتحقق الارتباطات الآمنة من قائمة الارتباطات الضارة المعروفة عندما ينقر المستخدمون فوق ارتباطات في البريد الإلكتروني** غير محددة أو `EnableSafeLinksForEmail $false` في PowerShell).\> للحصول على الإرشادات، راجع [إعداد نهج الارتباطات الآمنة في Microsoft Defender لـ Office 365](set-up-safe-links-policies.md).

بعد التحقق من أن علبة البريد تفي بهذه المتطلبات، استخدم الإرشادات المتبقية في هذه المقالة لتحديد علبة بريد عمليات إرسال المستخدم وإعدادات الرسائل التي أبلغ عنها المستخدم الآخر.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **عمليات إرسال المستخدم** ، استخدم <https://security.microsoft.com/userSubmissionsReportMessage>.

- للاتصال Exchange Online PowerShell، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- لتعديل التكوين الخاص بإرسالات المستخدم، يجب أن تكون عضوا في إحدى مجموعات الأدوار التالية:

  - **إدارة المؤسسة** أو **مسؤول الأمان** في [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- تحتاج إلى الوصول إلى Exchange Online PowerShell. إذا لم يكن للحساب الذي تحاول استخدامه حق الوصول إلى Exchange Online PowerShell، فستتلقى رسالة خطأ تبدو مماثلة لما يلي عند تحديد علبة بريد عمليات الإرسال:

  > تحديد عنوان بريد إلكتروني في مجالك

  لمزيد من المعلومات حول تمكين الوصول إلى Exchange Online PowerShell أو تعطيله، راجع المواضيع التالية:

  - [تمكين الوصول إلى Exchange Online PowerShell أو تعطيله](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [قواعد وصول العميل في Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox-for-email"></a>استخدام مدخل Microsoft 365 Defender لتكوين علبة بريد عمليات إرسال المستخدم للبريد الإلكتروني

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **نهج & قواعد نهج** \> \> **التهديد** **التي أبلغ المستخدم عن إعدادات الرسالة** في قسم **"الآخرين**". للانتقال مباشرة إلى صفحة **عمليات إرسال المستخدم** ، استخدم <https://security.microsoft.com/userSubmissionsReportMessage>.

2. في صفحة **عمليات إرسال المستخدم** ، يتم تحديد ما تراه إلى حد كبير بواسطة **الزر "رسالة تقرير Microsoft Outlook** " للتبديل:

   - **في** ![ تشغيل.](../../media/scc-toggle-on.png): يمكنك استخدام تجربة إعداد التقارير المتكاملة من Microsoft، والتي تتضمن الوظيفة الإضافية "رسالة التقرير" أو الوظيفة الإضافية "تصيد التقرير" أو التقارير المضمنة في Outlook على ويب.

     يسمح هذا الإعداد أيضا للمستخدمين بالإبلاغ عن رسائل إيجابية خاطئة من مدخل العزل.

   - **قباله** ![ التبديل.](../../media/scc-toggle-off.png): يمكنك استخدام أدوات إعداد تقارير الرسائل التابعة لجهة خارجية بدلا من تجربة إعداد التقارير المتكاملة من Microsoft.

يتم وصف خيارات التكوين ذات الصلة في الأقسام التالية.

### <a name="microsoft-integrated-reporting-experience-options"></a>خيارات تجربة التقارير المتكاملة من Microsoft

عندما يكون **الزر "رسالة تقرير Microsoft Outlook**" قيد  ![التشغيل.](../../media/scc-toggle-on.png) تتوفر الإعدادات التالية في صفحة **عمليات إرسال المستخدم**:

- **إرسال الرسائل التي تم الإبلاغ عنها إلى** المقطع: حدد أحد الخيارات التالية:

  - **Microsoft**: لا يتم استخدام علبة بريد عمليات إرسال المستخدم (تنتقل كل الرسائل التي تم الإبلاغ عنها إلى Microsoft للتحليل).

  - **علبة بريد Microsoft وعلبة بريد مؤسستي**: في المربع الذي يظهر، أدخل عنوان البريد الإلكتروني لعل بريد Exchange Online موجود لاستخدامها كعلبة بريد عمليات إرسال للمستخدم. مجموعات التوزيع غير مسموح بها. تنتقل عمليات إرسال المستخدم إلى Microsoft للتحليل وإلى علبة بريد عمليات إرسال المستخدم للمسؤول أو فريق عمليات الأمان لتحليلها.

  - **علبة بريد مؤسستي**: في المربع الذي يظهر، أدخل عنوان البريد الإلكتروني لعل بريد Exchange Online موجود. مجموعات التوزيع غير مسموح بها. تنتقل عمليات إرسال المستخدم فقط إلى علبة بريد عمليات إرسال المستخدم لمسؤول أو فريق عمليات الأمان لتحليلها. لا تنتقل الرسائل إلى Microsoft للتحليل إلا إذا أرسل المسؤول الرسائل يدويا.

  > [!IMPORTANT]
  > في المؤسسات الحكومية الأمريكية (GCC و GCC High و DoD)، يكون التحديد الوحيد المتاح في المقطع **"إرسال الرسائل المبلغ عنها"** هو **علبة بريد مؤسستي**. الخياران الآخران باللون الرمادي.
  >
  > إذا استخدمت [نهج علبة بريد Outlook على ويب](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/configure-outlook-web-app-mailbox-policy-properties) لتعطيل إرسال تقارير البريد الإلكتروني غير الهام في Outlook على ويب، ولكنك حددت **Microsoft** أو **Microsoft وعلبة بريد مؤسستي**، فسيتمكن المستخدمون من الإبلاغ عن الرسائل إلى Microsoft في Outlook على ويب باستخدام الوظيفة الإضافية "رسالة التقرير" أو الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي".
  >
  > إذا قمت بتحديد **علبة بريد المؤسسة الخاصة بي**، فستظهر الرسائل المبلغ عنها في علامة التبويب **"المستخدم" في علامة التبويب "رسائل تم الإبلاغ عنها** " في صفحة **"عمليات الإرسال** " في <https://security.microsoft.com/reportsubmission>. ولكن ستكون قيمة **النتيجة** لهذه الرسائل فارغة دائما، لأنه لم يتم إعادة إرسال الرسائل.
  >
  > إذا كنت تستخدم [تدريب محاكاة الهجوم](attack-simulation-training-get-started.md) أو منتج تابع لجهة خارجية لإجراء عمليات محاكاة التصيد الاحتيالي، فيجب تكوين علبة بريد عمليات إرسال المستخدم كعلبة بريد SecOps كما هو موضح سابقا في [متطلبات التكوين لقسم علبة بريد عمليات إرسال المستخدم](#configuration-requirements-for-the-user-submissions-mailbox) المذكورة سابقا في هذه المقالة. إذا لم تفعل ذلك، فقد يقوم المستخدم الذي يبلغ عن رسالة بتشغيل مهمة تدريب في منتج محاكاة التصيد الاحتيالي.

  بغض النظر عن التحديد، تتوفر الإعدادات التالية أيضا في المقطع **"إرسال الرسائل التي تم الإبلاغ عنها"** :

  - **اسمح للمستخدمين باختيار ما إذا كانوا يريدون الإبلاغ**: يتحكم هذا الإعداد في الخيارات المتوفرة في **خيارات تحديد التقارير المتوفرة للمستخدمين** :

    - **اسمح للمستخدمين باختيار ما إذا كانوا يرغبون في إعداد تقرير** محدد: يمكنك تحديد بعض الإعدادات الموجودة في القسم **"تحديد التقارير" المتوفرة للمستخدمين** أو كلها أو عدم تحديد أي منها.
    - **اسمح للمستخدمين باختيار ما إذا كانوا يريدون عدم تحديد التقرير** : يمكنك تحديد إعداد واحد فقط في **خيارات تحديد التقارير المتوفرة للمستخدمين** .

    - **حدد خيارات التقارير المتوفرة لقسم المستخدمين** :
      - **اسألني قبل إرسال الرسالة**
      - **الإبلاغ دائما عن الرسالة**
      - **عدم الإبلاغ عن الرسالة مطلقا**

- قسم **تجربة تقارير المستخدم**: تتوفر الإعدادات التالية:

  كما هو موضح على الصفحة، إذا حددت خيارا يرسل الرسائل المبلغ عنها إلى Microsoft، يضاف النص التالي أيضا إلى الإعلام:

  > سيتم إرسال بريدك الإلكتروني كما هو إلى Microsoft للتحليل. قد تحتوي بعض رسائل البريد الإلكتروني على معلومات شخصية أو حساسة.

  - قبل علامة التبويب **"تقرير**": في مربعي النص الأساسي **للعنوان** **والرسالة**، أدخل النص الوصفي الذي يراه المستخدمون قبل الإبلاغ عن رسالة باستخدام الوظيفة الإضافية "رسالة التقرير" أو الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي". يمكنك استخدام المتغير لتضمين `%type%` نوع الإرسال (غير الهام، وليس غير الهام، والتصيد الاحتيالي، وما إلى ذلك).
  - **بعد** علامة تبويب التقرير: في مربعي رسالة **العنوان** **والتأكيد** ، أدخل النص الوصفي الذي يراه المستخدمون بعد الإبلاغ عن رسالة باستخدام الوظيفة الإضافية "رسالة التقرير" أو الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي". يمكنك استخدام المتغير `%type%` لتضمين نوع الإرسال.

  - **العرض فقط عندما يقوم المستخدم بالإبلاغ عن التصيد الاحتيالي**: حدد هذا الخيار لعرض الإعلامات **"قبل إعداد التقارير** " و" **بعد الإبلاغ"** فقط عندما يقوم المستخدمون بالإبلاغ عن الرسائل على أنها تصيد احتيالي. وإلا، يتم عرض الإعلامات لكافة الرسائل التي تم الإبلاغ عنها.

- **إعلامات البريد الإلكتروني لقسم نتائج مراجعة المسؤول** : تتوفر الإعدادات التالية:

  - **حدد عنوان البريد الإلكتروني Office 365 لاستخدامه كمرسل**: حدد هذا الإعداد وأدخل عنوان البريد الإلكتروني في المربع الذي يظهر.
  
  - **تخصيص الإعلامات**: انقر فوق هذا الارتباط لتخصيص إعلام البريد الإلكتروني الذي يتم إرساله بعد مراجعات المسؤول ووضع علامة على الرسائل التي تم الإبلاغ عنها.

    في القائمة المنبثقة **لرسالة التأكيد "تخصيص** " التي تظهر، قم بتكوين الإعدادات التالية:

    - تم العثور على علامات **تصيد احتيالي** أو **غير هام** **أو أي تهديدات**: في **نص نتائج المراجعة** على بعض علامات التبويب أو بلا علامات تبويب أو كلها، أدخل النص المخصص الذي تريد استخدامه.
    - علامة **تذييل** الصفحة: تتوفر الخيارات التالية:
      - **نص التذييل**: أدخل نص تذييل الرسالة المخصص لاستخدامه.
      - **عرض شعار الشركة**: قبل تحديد هذا الخيار، تحتاج إلى اتباع الإرشادات في [تخصيص نسق Microsoft 365 لمؤسستك](../../admin/setup/customize-your-organization-theme.md) لتحميل الشعار المخصص.

  عند الانتهاء من القائمة المنبثقة **لرسالة التأكيد "تخصيص** "، انقر فوق **"تأكيد**".

- **تخصيص تجربة مؤسستك عند الإبلاغ عن التهديدات المحتملة في قسم العزل** :

  **زر رسالة تقرير العزل**: تحقق **من تشغيل** ![تشغيل هذا الإعداد.](../../media/scc-toggle-on.png) للسماح للمستخدمين بالإبلاغ عن الرسائل من العزل. وإلا، **فقم بإيقاف** ![تشغيل هذا الإعداد.](../../media/scc-toggle-off.png)

عند الانتهاء من صفحة **عمليات إرسال المستخدم** ، انقر فوق **"حفظ**". لاستعادة الإعدادات إلى قيمها السابقة مباشرة، انقر فوق **"استعادة**".

### <a name="third-party-reporting-tools-options"></a>خيارات أدوات إعداد التقارير لجهة خارجية

يمكنك إيقاف تشغيل تجربة إعداد التقارير المتكاملة من Microsoft لاستخدام أدوات إعداد تقارير الرسائل من جهة خارجية لإرسال الرسائل التي تم الإبلاغ عنها إلى علبة بريد عمليات إرسال المستخدم.

المتطلب الوحيد هو تضمين الرسائل الأصلية كغير مضغوطة. EML أو . مرفقات MSG في الرسائل التي يتم إرسالها إلى علبة بريد عمليات إرسال المستخدم. بمعنى آخر، لا تقم فقط بإعادة توجيه الرسائل الأصلية إلى علبة بريد عمليات إرسال المستخدم.

> [!NOTE]
> إذا كانت هناك مرفقات بريد إلكتروني متعددة في الرسالة، فسيتم تجاهل الإرسال. نحن ندعم الرسالة التي تحتوي على مرفق بريد إلكتروني واحد فقط.

يتم وصف متطلبات تنسيق الرسالة في القسم التالي. التنسيق اختياري، ولكن الرسائل المبلغ عنها لا تتبع التنسيق المحدد، ويتم دائما تعريف الرسائل المبلغ عنها على أنها تصيد احتيالي.

عندما يكون **الزر "رسالة تقرير Microsoft Outlook****" متوقفا عن** ![التشغيل.](../../media/scc-toggle-off.png) تتوفر الإعدادات التالية في صفحة **عمليات إرسال المستخدم** :

- **علبة بريد Microsoft وعلبة بريد مؤسستي**: في المربع الذي يظهر، أدخل عنوان البريد الإلكتروني لعل بريد Exchange Online موجود لاستخدامها كعلبة بريد عمليات إرسال للمستخدم. مجموعات التوزيع غير مسموح بها.

- **تخصيص تجربة مؤسستك عند الإبلاغ عن التهديدات المحتملة في قسم العزل** :

  **زر رسالة تقرير العزل**: تحقق **من تشغيل** ![تشغيل هذا الإعداد.](../../media/scc-toggle-on.png) للسماح للمستخدمين بالإبلاغ عن الرسائل من العزل. وإلا، **فقم بإيقاف** ![تشغيل هذا الإعداد.](../../media/scc-toggle-off.png)

عند الانتهاء من صفحة **عمليات إرسال المستخدم** ، انقر فوق **"حفظ**". لاستعادة الإعدادات إلى قيمها السابقة مباشرة، انقر فوق **"استعادة**".

#### <a name="message-submission-format"></a>تنسيق إرسال الرسالة

لتعريف الرسائل المرفقة الأصلية بشكل صحيح، تتطلب الرسائل المرسلة إلى علبة البريد المخصصة تنسيقا محددا. إذا لم تستخدم الرسائل هذا التنسيق، يتم دائما تعريف الرسائل المرفقة الأصلية على أنها تصيد احتيالي.

لتحديد سبب الإبلاغ عن الرسائل المرفقة الأصلية، يجب أن تفي الرسائل المرسلة إلى علبة بريد عمليات إرسال المستخدم بالمعايير التالية:

- مرفق الرسالة الأصلي غير معدل.
- يجب أن يبدأ سطر الموضوع (عنوان المغلف) للرسائل المرسلة إلى علبة بريد عمليات إرسال المستخدم بإحدى قيم البادئة التالية:
  - `1|` أو `Junk:`.
  - `2|` أو `Not junk:`.
  - `3|` أو `Phishing:`.

  على سبيل المثال:

  - `3|This text in the Subject line is ignored by the system`
  - `Not Junk:This text in the Subject line is also ignored by the system`

  لن يتم عرض الرسائل التي لا تتبع هذا التنسيق بشكل صحيح في صفحة **عمليات الإرسال** في <https://security.microsoft.com/reportsubmission>.

## <a name="use-exchange-online-powershell-to-configure-the-user-submissions-mailbox-for-email"></a>استخدام Exchange Online PowerShell لتكوين علبة بريد عمليات إرسال المستخدم للبريد الإلكتروني

بعد [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)، يمكنك استخدام **\*-ReportSubmissionPolicy** **و-ReportSubmissionRule\*** cmdlets لإدارة وتكوين علبة بريد عمليات إرسال المستخدم والإعدادات ذات الصلة.

في Exchange Online PowerShell، تكون العناصر الأساسية لإعدادات علبة بريد عمليات إرسال المستخدم هي:

- **نهج إرسال التقرير**: تشغيل تجربة إعداد التقارير المتكاملة من Microsoft أو إيقاف تشغيلها، وتشغيل إرسال الرسائل التي تم الإبلاغ عنها إلى Microsoft أو إيقاف تشغيلها، وتشغيل إرسال الرسائل المبلغ عنها إلى علبة بريد عمليات إرسال المستخدم أو إيقاف تشغيلها، ومعظم الإعدادات الأخرى.
- **قاعدة إرسال التقرير**: تحدد عنوان البريد الإلكتروني الخاص بعلبة بريد عمليات الإرسال الخاصة بالمستخدم أو قيمة فارغة عندما لا يتم استخدام علبة بريد عمليات الإرسال الخاصة بالمستخدم (إرسال رسائل التقرير إلى Microsoft فقط).

الفرق بين هذين العنصرين غير واضح عند إدارة إعدادات علبة بريد عمليات إرسال المستخدم في مدخل Microsoft 365 Defender:

- هناك فقط نهج إرسال التقرير المسمى DefaultReportSubmissionPolicy وقاعدة إرسال تقرير واحدة تسمى DefaultReportSubmissionRule بشكل افتراضي.

  إذا لم يسبق لك الذهاب إلى <https://security.microsoft.com/userSubmissionsReportMessage>، فلا يوجد نهج إرسال التقرير أو قاعدة إرسال التقرير (لا ترجع Get-ReportSubmissionPolicy و cmdlets Get-ReportSubmissionRule شيئا).

  بمجرد زيارة <https://security.microsoft.com/userSubmissionsReportMessage> وحتى قبل تكوين أي إعدادات، يتم إنشاء نهج إرسال التقرير بالقيم الافتراضية ويكون مرئيا في PowerShell.

  كما هو الحال بعد تكوين الإعدادات وحفظها <https://security.microsoft.com/userSubmissionsReportMessage> لتحديد علبة بريد عمليات إرسال المستخدم (تجربة التقارير المتكاملة من Microsoft أو أدوات الجهات الخارجية)، يتم تلقائيا إنشاء قاعدة إرسال التقرير المسماة DefaultReportSubmissionRule. لاحظ أن الأمر يستغرق عدة ثوان قبل أن تكون القاعدة مرئية في PowerShell.

- يمكنك حذف قاعدة إرسال التقرير وإعادة إنشائها باسم مختلف، ولكن القاعدة تقترن دائما بنهج إرسال التقرير الذي لا يمكنك تغيير اسمه. لذلك، نوصي بتسمية القاعدة DefaultReportSubmissionRule كلما قمت بإنشاء القاعدة أو إعادة إنشائها.

- عند تحديد عنوان البريد الإلكتروني لعل بريد المستخدم المرسل في مدخل Microsoft 365 Defender، يتم تعيين هذه القيمة بشكل أساسي في قاعدة إرسال التقرير، ولكن يتم أيضا نسخ القيمة إلى الخصائص ذات الصلة في نهج إرسال التقرير. في PowerShell، عند تعيين عنوان البريد الإلكتروني في القاعدة، لا يتم نسخ القيمة إلى الخصائص ذات الصلة في النهج. للاتساق مع مدخل Microsoft 365 Defender وللوضوح، نوصي بإضافة عنوان البريد الإلكتروني أو تحديثه في النهج والقاعدة.

### <a name="use-powershell-to-view-the-report-submission-policy-and-the-report-submission-rule"></a>استخدام PowerShell لعرض نهج إرسال التقرير وقاعدة إرسال التقرير

لعرض نهج إرسال التقرير، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```powershell
Get-ReportSubmissionPolicy
```

لعرض قاعدة إرسال التقرير، قم بتشغيل الأمر التالي:

```powershell
Get-ReportSubmissionRule
```

لعرض كل من النهج والقاعدة في الوقت نفسه، قم بتشغيل الأوامر التالية:

```powershell
Write-Output -InputObject `r`n,"Report Submission Policy","-------------------------------------------------------------------------------------"; Get-ReportSubmissionPolicy; Write-Output -InputObject `r`n,"Report Submission Rule","-------------------------------------------------------------------------------------"; Get-ReportSubmissionRule
```

تذكر، إذا لم تكن قد انتقلت إلى <https://security.microsoft.com/userSubmissionsReportMessage> نهج إرسال التقرير أو قاعدة إرسال التقرير في PowerShell أو أنشأته يدويا، فلا يوجد نهج إرسال التقرير أو قاعدة إرسال التقرير، لذلك لا ترجع **أوامر Get-ReportSubmissionPolicy** و **Get-ReportSubmissionRule** cmdlets شيئا.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-ReportSubmissionPolicy](/powershell/module/exchange/get-reportsubmissionpolicy) و [Get-ReportSubmissionRule](/powershell/module/exchange/get-reportsubmissionrule).

### <a name="use-powershell-to-create-the-report-submission-policy-and-the-report-submission-rule"></a>استخدام PowerShell لإنشاء نهج إرسال التقرير وقاعدة إرسال التقرير

إذا كانت **أوامر Get-ReportSubmissionPolicy** و **Get-ReportSubmissionRule** cmdlets لا ترجع أي إخراج، يمكنك إنشاء نهج إرسال التقرير وقاعدة إرسال التقرير. إذا حاولت إنشاؤها عندما تكون موجودة بالفعل، فستحصل على خطأ.

قم دائما بإنشاء نهج إرسال التقرير أولا، لأنك تحدد نهج إرسال التقرير في قاعدة إرسال التقرير.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-ReportSubmissionPolicy](/powershell/module/exchange/new-reportsubmissionpolicy) و [New-ReportSubmissionRule](/powershell/module/exchange/new-reportsubmissionrule).

#### <a name="use-powershell-to-enable-the-microsoft-integrated-reporting-experience-with-report-to-microsoft-only"></a>استخدام PowerShell لتمكين تجربة إعداد التقارير المتكاملة من Microsoft مع إرسال تقرير إلى Microsoft فقط

ينشئ هذا المثال نهج إرسال التقرير مع الإعدادات الافتراضية (نفس الإعدادات التي كانت عند زيارة <https://security.microsoft.com/userSubmissionsReportMessage>لأول مرة، ولكن قبل تكوين أي إعدادات أو حفظها):

- تم تشغيل تجربة إعداد التقارير المتكاملة من Microsoft: **زر "رسالة تقرير Microsoft Outlook**": **تشغيل** ![التشغيل.](../../media/scc-toggle-on.png)

- إرسال الرسائل التي تم الإبلاغ عنها إلى Microsoft فقط: **إرسال الرسائل التي تم الإبلاغ عنها إلى** \> **Microsoft**.

- لا توجد حاجة إلى علبة بريد عمليات إرسال المستخدم أو تحديدها، لذلك لم يتم إنشاء قاعدة إرسال التقرير.

```powershell
New-ReportSubmissionPolicy
```

#### <a name="use-powershell-for-the-microsoft-integrated-reporting-experience-with-report-to-microsoft-and-the-user-submissions-mailbox"></a>استخدام PowerShell لتجربة التقارير المتكاملة من Microsoft مع إرسال تقرير إلى Microsoft وعلبة بريد عمليات إرسال المستخدم

ينشئ هذا المثال نهج إرسال التقرير وقاعدة إرسال التقرير بالإعدادات التالية:

- تم تشغيل تجربة إعداد التقارير المتكاملة من Microsoft: **زر "رسالة تقرير Microsoft Outlook**": **تشغيل** ![التشغيل.](../../media/scc-toggle-on.png) في **New-ReportSubmissionPolicy** cmdlet، تكون القيمة الافتراضية لمعلمة _EnableReportToMicrosoft_ هي `$true` والقيمة الافتراضية لمعلمة `$false`_EnableThirdPartyAddress_، لذلك لا تحتاج إلى استخدامها.

- إرسال الرسائل التي تم الإبلاغ عنها إلى Microsoft وعلبة بريد عمليات إرسال المستخدم: **إرسال الرسائل التي تم الإبلاغ عنها إلى** \> **Microsoft وعلبة بريد مؤسستي**:

  - **New-ReportSubmissionPolicy**: `-ReportJunkToCustomizedAddress $true -ReportJunkAddresses <emailaddress> -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses <emailaddress> -ReportPhishToCustomizedAddress $true -ReportPhishAddresses <emailaddress>`.
  - **Set-ReportSubmissionRule**: `SentTo <emailaddress>`.

  في هذا المثال، يتم reportedmessages@contoso.com عنوان البريد الإلكتروني لعل بريد عمليات إرسال المستخدم في Exchange Online (لا يمكنك تحديد عنوان بريد إلكتروني خارجي).

  > [!NOTE]
  > يجب استخدام نفس قيمة عنوان البريد الإلكتروني في كافة المعلمات التي تحدد علبة بريد عمليات إرسال المستخدم.

المعلمات المتبقية مطلوبة لإنشاء نهج إرسال التقرير. في هذا المثال، يتم استخدام القيم الافتراضية. إذا لم تحدد القيم الافتراضية كما هو موضح في هذا المثال، فقد تكون المعلمات والإعدادات الإضافية مطلوبة:

- **اسمح للمستخدمين باختيار ما إذا كانوا يرغبون في الإبلاغ عن** تحديد (`-DisableUserSubmissionOptions $false`) ولا يتم تحديد **خيارات تحديد التقارير المتوفرة لخيارات المستخدمين** (يتم استخدام قيمة `0` معلمة _UserSubmissionOptions_ الافتراضية).
- قسم **تجربة تقارير المستخدم**:
  - لا يتم إدخال أي شيء في مربعي **النص الأساسي للعنوان** **والرسالة** في علامتي التبويب **"قبل إعداد التقارير** " أو **"بعد إعداد التقارير** " (`-EnableCustomizedMsg $false`).
  - **يتم العرض فقط عندما يقوم المستخدم بالإبلاغ عن التصيد الاحتيالي** المحدد (`-OnlyShowPhishingDisclaimer $true`).
- **إعلامات البريد الإلكتروني لقسم نتائج مراجعة المسؤول** :
  - **حدد عنوان البريد الإلكتروني Office 365 لاستخدامه كمرسل** غير محدد (`-EnableCustomNotificationSender $false`).
  - تخصيص ارتباط \> **الإعلامات** تخصيص علامة **تذييل** قائمة **التأكيد** المنبثقة\>: لم يتم تحديد **شعار شركة العرض** (`-EnableOrganizationBranding $false`).
- **تخصيص تجربة مؤسستك عند الإبلاغ عن التهديدات المحتملة في قسم العزل** :

  **زر رسالة تقرير العزل** قيد التبديل: **تشغيل** ![التشغيل.](../../media/scc-toggle-on.png) (`-DisableQuarantineReportingOption $false`).

```powershell
$usersub = "reportedmessages@contoso.com"

New-ReportSubmissionPolicy -ReportJunkToCustomizedAddress $true -ReportJunkAddresses $usersub -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses $usersub -ReportPhishToCustomizedAddress $true -ReportPhishAddresses $usersub -DisableUserSubmissionOptions $false -EnableCustomizedMsg $false -OnlyShowPhishingDisclaimer $true -EnableCustomNotificationSender $false -EnableOrganizationBranding $false -DisableQuarantineReportingOption $false

New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
```

#### <a name="use-powershell-for-the-microsoft-integrated-reporting-experience-with-report-to-the-user-submissions-mailbox-only"></a>استخدام PowerShell لتجربة التقارير المتكاملة من Microsoft مع إرسال تقرير إلى علبة بريد عمليات إرسال المستخدم فقط

ينشئ هذا المثال نهج إرسال التقرير وقاعدة إرسال التقرير بالإعدادات التالية:

- تم تشغيل تجربة إعداد التقارير المتكاملة من Microsoft: **زر "رسالة تقرير Microsoft Outlook**": **تشغيل** ![التشغيل.](../../media/scc-toggle-on.png) في **New-ReportSubmissionPolicy** cmdlet: `-EnableReportToMicrosoft $false`. القيمة الافتراضية للمعلمة _EnableThirdPartyAddress_ هي `$false`، لذلك لا تحتاج إلى استخدامها.

- إرسال الرسائل التي تم الإبلاغ عنها إلى علبة بريد عمليات إرسال المستخدم فقط: **إرسال الرسائل التي تم الإبلاغ عنها إلى** \> **علبة بريد المؤسسات**:

  - **New-ReportSubmissionPolicy**: `-ReportJunkToCustomizedAddress $true -ReportJunkAddresses <emailaddress> -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses <emailaddress> -ReportPhishToCustomizedAddress $true -ReportPhishAddresses <emailaddress>`.
  - **Set-ReportSubmissionRule**: `SentTo <emailaddress>`.

  في هذا المثال، يتم userreportedmessages@fabrikam.com عنوان البريد الإلكتروني لعل بريد عمليات إرسال المستخدم في Exchange Online (لا يمكنك تحديد عنوان بريد إلكتروني خارجي).

  > [!NOTE]
  > يجب استخدام نفس قيمة عنوان البريد الإلكتروني في كافة المعلمات التي تحدد علبة بريد عمليات إرسال المستخدم.

كما هو الحال في المثال السابق، تكون نفس المعلمات المتبقية مطلوبة لإنشاء نهج إرسال التقرير. كما هو الحال في المثال السابق، يتم أيضا استخدام القيم الافتراضية لهذه المعلمات:

```powershell
$usersub = "userreportedmessages@fabrikam.com"

New-ReportSubmissionPolicy -EnableReportToMicrosoft $false -ReportJunkToCustomizedAddress $true -ReportJunkAddresses $usersub -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses $usersub -ReportPhishToCustomizedAddress $true -ReportPhishAddresses $usersub -DisableUserSubmissionOptions $false -EnableCustomizedMsg $false -OnlyShowPhishingDisclaimer $true -EnableCustomNotificationSender $false -EnableOrganizationBranding $false -DisableQuarantineReportingOption $false

New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
```

#### <a name="use-powershell-for-third-party-reporting-tools"></a>استخدام PowerShell لأدوات إعداد التقارير لجهات خارجية

ينشئ هذا المثال نهج إرسال التقرير وقاعدة إرسال التقرير بالإعدادات التالية:

- تم إيقاف تشغيل تجربة إعداد التقارير المتكاملة من Microsoft: **زر "رسالة تقرير Microsoft Outlook**": **إيقاف** ![التشغيل.](../../media/scc-toggle-off.png) في **New-ReportSubmissionPolicy** cmdlet: `-EnableReportToMicrosoft $false -EnableThirdPartyAddress $true`.

- استخدم المعلمات التالية لتحديد عنوان البريد الإلكتروني لعل بريد المستخدم المرسل:

  - **New-ReportSubmissionPolicy**: `-ThirdPartyReportAddresses <emailaddress>`
  - **Set-ReportSubmissionRule**: `SentTo <emailaddress>`.

  في هذا المثال، يتم thirdpartyreporting@wingtiptoys.com عنوان البريد الإلكتروني لعل بريد عمليات إرسال المستخدم في Exchange Online (لا يمكنك تحديد عنوان بريد إلكتروني خارجي

  > [!NOTE]
  > يجب استخدام نفس قيمة عنوان البريد الإلكتروني في كافة المعلمات التي تحدد علبة بريد عمليات إرسال المستخدم.

المعلمات المتبقية مطلوبة لإنشاء نهج إرسال التقرير بنجاح. في هذا المثال، يتم استخدام القيم الافتراضية. لا تتوفر خيارات أخرى في نهج إرسال التقرير عند إيقاف تشغيل تجربة إعداد التقارير المتكاملة من Microsoft:

- **تخصيص تجربة مؤسستك عند الإبلاغ عن التهديدات المحتملة في قسم العزل** :

  **زر رسالة تقرير العزل** قيد التبديل: **تشغيل** ![التشغيل.](../../media/scc-toggle-on.png) (`-DisableQuarantineReportingOption $false`).

```powershell
$usersub = "thirdpartyreporting@wingtiptoys.com"

New-ReportSubmissionPolicy -EnableReportToMicrosoft $false -EnableThirdPartyAddress $true -ThirdPartyReportAddresses $usersub -DisableQuarantineReportingOption $false

New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
```

### <a name="use-powershell-to-modify-the-report-submission-policy-and-the-report-submission-rule"></a>استخدام PowerShell لتعديل نهج إرسال التقرير وقاعدة إرسال التقرير

تتوفر نفس الإعدادات عند تعديل نهج إرسال التقرير في PowerShell كما هو الحال عند إنشاء النهج كما هو موضح في [القسم السابق](#use-powershell-to-create-the-report-submission-policy-and-the-report-submission-rule). الفرق الرئيسي هو: المعلمات الإضافية المطلوبة لإنشاء النهج (على سبيل المثال، _DisableQuarantineReportingOption) ليست مطلوبة_ لفترة طويلة. ولكن، قد تحتاج إلى التراجع عن بعض الإعدادات المهمة التي قمت بتكوينها أو لم تقم بتكوينها مسبقا أو إلغاءها. وقد تحتاج إلى إنشاء قاعدة إرسال التقرير أو حذفها للسماح بالإبلاغ إلى علبة بريد عمليات إرسال المستخدم أو منعها.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-ReportSubmissionPolicy](/powershell/module/exchange/set-reportsubmissionpolicy).

توضح الأمثلة التالية كيفية تغيير تجربة إعداد تقارير المستخدم دون القلق بشأن الإعدادات أو القيم الموجودة:

- التغيير إلى **تقرير تجربة \> التقارير المتكاملة من Microsoft إلى Microsoft فقط**:

  ```powershell
   Set-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy -EnableReportToMicrosoft $true -EnableThirdPartyAddress $false -ThirdPartyReportAddresses $null -ReportJunkToCustomizedAddress $false -ReportJunkAddresses $null -ReportNotJunkToCustomizedAddress $false -ReportNotJunkAddresses $null -ReportPhishToCustomizedAddress $false -ReportPhishAddresses $null

  Get-ReportSubmissionRule | Remove-ReportSubmissionRule
  ```

- تغيير **تقرير تجربة \> التقارير المتكاملة من Microsoft إلى Microsoft وعلبة بريد عمليات إرسال المستخدم** (على سبيل المثال، reportedmessages@contoso.com):

  ```powershell
  $usersub = "reportedmessages@contoso.com"

  Set-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy -EnableReportToMicrosoft $true -EnableThirdPartyAddress $false -ThirdPartyReportAddresses $null -ReportJunkToCustomizedAddress $true -ReportJunkAddresses $usersub -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses $usersub -ReportPhishToCustomizedAddress $true -ReportPhishAddresses $usersub
  ```

  الأمر التالي مطلوب فقط إذا لم يكن لديك قاعدة إرسال التقرير بالفعل:

  ```powershell
  New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
  ```

- التغيير إلى **تقرير تجربة \> التقارير المتكاملة من Microsoft إلى علبة بريد عمليات إرسال المستخدم فقط** (على سبيل المثال، userreportedmessages@fabrikam.com):

  ```powershell
  $usersub = "userreportedmessages@fabrikam.com"

  Set-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy -EnableReportToMicrosoft $false -EnableThirdPartyAddress $false -ThirdPartyReportAddresses $null -ReportJunkToCustomizedAddress $true -ReportJunkAddresses $usersub -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses $usersub -ReportPhishToCustomizedAddress $true -ReportPhishAddresses $usersub
  ```

  الأمر التالي مطلوب فقط إذا لم يكن لديك قاعدة إرسال التقرير بالفعل:

  ```powershell
  New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
  ```

- تغيير إلى **أدوات إعداد التقارير التابعة لجهة خارجية** (على سبيل المثال، thirdpartyreporting@wingtiptoys.com):

  ```powershell
  $usersub = "thirdpartyreporting@wingtiptoys.com"

  Set-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy -EnableReportToMicrosoft $false -EnableThirdPartyAddress $true -ThirdPartyReportAddresses $usersub -ReportJunkToCustomizedAddress $false -ReportJunkAddresses $null -ReportNotJunkToCustomizedAddress $false -ReportNotJunkAddresses $null -ReportPhishToCustomizedAddress $false -ReportPhishAddresses $null
  ```

  الأمر التالي مطلوب فقط إذا لم يكن لديك قاعدة إرسال التقرير بالفعل:

  ```powershell
  New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
  ```

الإعداد الوحيد ذي المعنى الذي يمكنك تعديله في قاعدة إرسال التقرير هو عنوان البريد الإلكتروني لعلبة بريد عمليات إرسال المستخدم (قيمة المعلمة _SentTo_ ). على سبيل المثال:

```powershell
Get-ReportSubmissionRule | Set-ReportSubmissionRule -SentTo newemailaddress@contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-ReportSubmissionRule](/powershell/module/exchange/set-reportsubmissionrule).

لتعطيل إرسال رسائل البريد الإلكتروني مؤقتا إلى علبة بريد عمليات إرسال المستخدم (تجربة إعداد التقارير المتكاملة من Microsoft أو أدوات الجهات الخارجية) دون إدخال قاعدة إرسال التقرير، استخدم [Disable-ReportSubmissionRule](/powershell/module/exchange/disable-reportsubmissionrule). على سبيل المثال:

```powershell
Get-ReportSubmissionRule | Disable-ReportSubmissionRule -Confirm:$false
```

لتمكين قاعدة إرسال التقرير مرة أخرى، استخدم [Enable-ReportSubmissionRule](/powershell/module/exchange/enable-reportsubmissionrule). على سبيل المثال:

```powershell
Get-ReportSubmissionRule | Disable-ReportSubmissionRule -Confirm:$false
```

### <a name="use-powershell-to-remove-the-report-submission-policy-and-the-report-submission-rule"></a>استخدام PowerShell لإزالة نهج إرسال التقرير وقاعدة إرسال التقرير

للبدء من جديد بالإعدادات الافتراضية لنهج إرسال التقرير، يمكنك حذفه وإعادة إنشائه. لا تؤدي إزالة نهج إرسال التقرير إلى إزالة قاعدة إرسال التقرير، والعكس بالعكس.

لإزالة نهج إرسال التقرير، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```powershell
Remove-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy
```

لإزالة قاعدة إرسال التقرير، قم بتشغيل الأمر التالي:

```powershell
Get-ReportSubmissionRule | Remove-ReportSubmissionRule
```

لإزالة كل من نهج إرسال التقرير وقاعدة إرسال التقرير في الأمر نفسه دون مطالبات، قم بتشغيل الأمر التالي:

```powershell
Remove-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy; Get-ReportSubmissionRule | Remove-ReportSubmissionRule -Confirm:$false
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-ReportSubmissionPolicy](/powershell/module/exchange/remove-reportsubmissionpolicy) و [Remove-ReportSubmissionRule](/powershell/module/exchange/remove-reportsubmissionrule).
