---
title: حاول تقييم Defender لـ Office 365
description: تعرف على كيفية تقييم قدرات Microsoft Defender لـ Office 365 وتجربتها دون التأثير على تدفق البريد الموجود.
keywords: ''
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ROBOTS: ''
ms.openlocfilehash: ad8c15ef0b5dc56d2df8455341f8bf5e4e6efd94
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857464"
---
# <a name="try-microsoft-defender-for-office-365"></a>جرب Microsoft Defender لـ Office 365

يوفر مدخل **الإصدارات التجريبية** الموحدة في مدخل Microsoft 365 Defender نقطة إدخال واحدة لتجارب الإصدار التجريبي والتقييم المنفصلة سابقا Microsoft Defender لـ Office 365. الهدف هو السماح لك بتجربة ميزات Defender لـ Office 365 الخطة 2 لمدة 90 يوما قبل الالتزام بها بالكامل. ولكن، هناك اختلافات في تجارب التقييم استنادا إلى طبيعة مؤسسة Microsoft 365:

- لديك بالفعل علب بريد Microsoft 365، ولكنك تستخدم حاليا خدمة أو جهازا تابعا لجهة خارجية لحماية البريد الإلكتروني. يتدفق البريد من الإنترنت عبر خدمة الحماية قبل التسليم إلى مؤسسة Microsoft 365. حماية Microsoft 365 منخفضة قدر الإمكان (لا يتم إيقاف تشغيلها تماما؛ على سبيل المثال، يتم دائما فرض الحماية من البرامج الضارة).

  ![يتدفق البريد من الإنترنت عبر خدمة الحماية أو الجهاز التابع لجهة خارجية قبل التسليم إلى Microsoft 365.](../../media/mdo-migration-before.png)

  في هذه البيئات، يمكنك فقط محاولة Defender لـ Office 365 في وضع *التدقيق*. لا تحتاج إلى تغيير تدفق البريد (سجلات MX) لتجربة Defender لـ Office 365.

- لديك بالفعل مؤسسة Microsoft 365. يتدفق البريد من الإنترنت مباشرة إلى Microsoft 365، ولكن لا يحتوي اشتراكك الحالي إلا [على Exchange Online Protection (EOP)](exchange-online-protection-overview.md) أو [Defender لـ Office 365 الخطة 1](overview.md#microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

  ![يتدفق البريد من الإنترنت إلى Microsoft 365، مع حماية من EOP و/أو Defender لـ Office 365 الخطة 1.](../../media/mdo-trial-mail-flow.png)

  في هذه البيئات، يمكنك تجربة Defender لـ Office 365 في وضع *التدقيق* أو في *وضع الحظر*.

أنت مدعو لبدء الإصدار التجريبي في مواقع ميزات Defender لـ Office 365 مختلفة في مدخل Microsoft 365 Defender في <https://security.microsoft.com>. الموقع المركزي لبدء الإصدار التجريبي الخاص بك موجود على صفحة **Trials** في <https://security.microsoft.com/atpEvaluation>.

شاهد هذا الفيديو القصير لمعرفة المزيد حول كيفية إنجاز المزيد من المهام في وقت أقل باستخدام Microsoft Defender لـ Office 365.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWMmIe]

تشرح بقية هذه المقالة الفرق بين وضع حظر وضع التدقيق وكيفية تكوين التقييمات وتفاصيل أخرى.

للحصول على دليل مصاحب حول كيفية استخدام الإصدار التجريبي، راجع [دليل المبادئ التجريبي: Microsoft Defender لـ Office 365](trial-playbook-defender-for-office-365.md).

## <a name="overview-of-defender-for-office-365"></a>نظرة عامة على Defender لـ Office 365

يساعد Defender لـ Office 365 المؤسسات على تأمين مؤسستها من خلال تقديم مجموعة شاملة من القدرات. لمزيد من المعلومات، راجع [Microsoft Defender لـ Office 365](defender-for-office-365.md).

يمكنك أيضا معرفة المزيد حول Defender لـ Office 365 في هذا [الدليل التفاعلي](https://aka.ms/MS365D.InteractiveGuide).

![رسم تخطيطي تصوري Microsoft Defender لـ Office 365.](../../media/microsoft-defender-for-office-365.png)

## <a name="policies-in-blocking-mode-or-audit-mode"></a>النهج في وضع الحظر أو وضع التدقيق

عند تقييم Defender لـ Office 365، تكون النهج التي تتحكم في ميزات الحماية في Microsoft 365 موجودة:

- **Exchange Online Protection (EOP):** لا يتم إنشاء نهج جديدة أو خاصة. يمكن لنهج EOP الموجودة العمل على الرسائل (على سبيل المثال، إرسال رسائل إلى مجلد البريد الإلكتروني غير الهام أو العزل):

  - [نهج مكافحة البرامج الضارة](anti-malware-protection.md)
  - [الحماية الواردة من البريد العشوائي](anti-spam-protection.md)
  - [الحماية من الانتحال في نهج مكافحة التصيد الاحتيالي](set-up-anti-phishing-policies.md#spoof-settings)

  تكون النهج الافتراضية لهذه الميزات قيد التشغيل دائما، وتنطبق على جميع المستلمين، ويتم تطبيقها دائما في النهاية (بعد أي نهج مخصصة).

- **Defender لـ Office 365**: يتم إنشاء النهج الحصرية Defender لـ Office 365 لتقييم Defender لـ Office 365:

  - [حماية الانتحال في نهج مكافحة التصيد الاحتيالي](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [مرفقات آمنة لرسائل البريد الإلكتروني](safe-attachments.md)
  - [ارتباطات آمنة لرسائل البريد الإلكتروني وMicrosoft Teams](safe-links.md)

  ولكن، تختلف طبيعة هذه النهج في وضع الحظر ووضع التدقيق:

  - **وضع التدقيق**: يتم إنشاء نهج منتظمة، ولكن يتم تكوين النهج فقط *للكشف عن* التهديدات. Defender لـ Office 365 بالكشف عن الرسائل الضارة لإعداد التقارير، ولكن لا يتم التعامل مع الرسائل (على سبيل المثال، لا يتم عزل الرسائل المكتشفة).

  - **وضع الحظر**: يتم إنشاء النهج باستخدام القالب القياسي [لنهج الأمان التي تم تعيينها مسبقا](preset-security-policies.md). Defender لـ Office 365 *الكشف عن* الرسائل الضارة *وتنفيذ إجراءات بشأنها* (على سبيل المثال، يتم عزل الرسائل المكتشفة).

  التحديد الافتراضي والموصى به هو تحديد نطاق نهج Defender لـ Office 365 هذه لجميع المستخدمين في المؤسسة. ولكن أثناء الإعداد أو بعده، يمكنك تغيير تعيين النهج إلى مستخدمين أو مجموعات أو مجالات بريد إلكتروني معينة.

**الملاحظات**:

- ستؤدي الارتباطات الآمنة إلى تهيئة عناوين URL في تدفق البريد. لمنع معالجة عناوين URL معينة، استخدم قائمة السماح/الحظر للمستأجر. لمزيد من المعلومات، راجع [إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md).
- لا تقوم الارتباطات الآمنة بتغليف ارتباطات URL في نصوص رسائل البريد الإلكتروني.
- يتم وصف إعدادات نهج التقييم في قسم [إعدادات نهج التقييم](#evaluation-policy-settings) لاحقا في هذه المقالة.

## <a name="set-up-an-evaluation-in-audit-mode"></a>إعداد تقييم في وضع التدقيق

1. انقر فوق **"بدء التقييم**".

2. في مربع الحوار **"تشغيل الحماية** "، حدد **"لا"، أريد فقط إعداد التقارير**، ثم انقر فوق **"متابعة**".

3. في مربع الحوار **"تحديد المستخدمين الذين تريد تضمينهم** "، قم بتكوين الإعدادات التالية:

   - **كافة المستخدمين**: هذا هو الخيار الافتراضي والموصى به.
   - **حدد المستخدمين**: إذا حددت هذا الخيار، فستحتاج إلى تحديد المستلمين الداخليين الذين ينطبق عليهم التقييم:
     - **المستخدمون**: علب البريد أو مستخدمو البريد أو جهات اتصال البريد المحددة.
     - **المجموعات**:
       - أعضاء مجموعات التوزيع المحددة أو مجموعات الأمان الممكنة للبريد.
       - مجموعات Microsoft 365 المحددة.
       - **المجالات**: كافة المستلمين في [المجالات المقبولة المحددة](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) في مؤسستك.

     انقر في المربع المناسب، وابدأ بكتابة قيمة، وحدد القيمة التي تريدها من النتائج. كرر هذه العملية عدة مرات حسب الضرورة. لإزالة قيمة موجودة، انقر فوق "إزالة" ![الأيقونة "إزالة".](../../media/m365-cc-sc-remove-selection-icon.png) بجوار القيمة.

     بالنسبة للمستخدمين أو المجموعات، يمكنك استخدام معظم المعرفات (الاسم واسم العرض والاسم المستعار وعنوان البريد الإلكتروني واسم الحساب وما إلى ذلك)، ولكن يظهر اسم العرض المقابل في النتائج. بالنسبة للمستخدمين، أدخل علامة نجمية (\*) بحد ذاتها لمشاهدة كافة القيم المتوفرة.

   > [!NOTE]
   > يمكنك تغيير هذه التحديدات بعد الانتهاء من إعداد التقييم.

   عند الانتهاء، انقر فوق **"متابعة**".

4. في مربع الحوار **"ساعدنا على فهم تدفق البريد** "، قم بتكوين الخيارات التالية:

   - **مشاركة البيانات مع Microsoft**: يتم تحديد هذا الخيار بشكل افتراضي، ولكن يمكنك إلغاء تحديد خانة الاختيار إذا أردت ذلك.

   - يتم تحديد أحد الخيارات التالية تلقائيا استنادا إلى اكتشافنا لسجل MX لمجالك:

     - **إنني أستخدم موفر خدمة تابع لجهة خارجية و/أو محلي**: يشير سجل MX لمجالك إلى مكان آخر غير Microsoft 365. يتطلب هذا التحديد الإعدادات الإضافية التالية بعد النقر فوق **"التالي"**:

       1. في مربع حوار **الإعدادات المحلية أو الجهة الخارجية** ، قم بتكوين الإعدادات التالية:

          - **حدد موفر خدمة تابع لجهة خارجية**: حدد إحدى القيم التالية:
            - **البركوده**
            - **منفذ حديدي**
            - **Mimecast**
            - **نقطة تدقيق**
            - **سوفوس**
            - **سيمانتيك**
            - **Trend Micro**
            - **الاخري**

          - **الموصل الذي يجب تطبيق هذا التقييم عليه**: حدد الموصل المستخدم لتدفق البريد إلى Microsoft 365.

            يتم تكوين [التصفية المحسنة للموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (المعروفة أيضا باسم *قائمة التخطي*) تلقائيا على الموصل الذي تحدده.

            عند وجود خدمة أو جهاز تابع لجهة خارجية أمام Microsoft 365، تحدد التصفية المحسنة للموصلات بشكل صحيح مصدر رسائل الإنترنت وتعمل على تحسين دقة مكدس تصفية Microsoft بشكل كبير (خاصة [التحليل الذكي للانتحال](anti-spoofing-protection.md)، بالإضافة إلى قدرات ما بعد الاختراق في [مستكشف المخاطر](threat-explorer.md) والتحقيق [التلقائي & الاستجابة (AIR)](automated-investigation-response-office.md)).

          - **سرد كل عنوان IP للبوابة التي تمر بها رسائلك**: يتوفر هذا الإعداد فقط إذا قمت بتحديد **"آخر** " **لتحديد موفر خدمة تابع لجهة خارجية**. أدخل قائمة مفصولة بفواصل لعناوين IP التي تستخدمها خدمة الحماية أو الجهاز التابع لجهة خارجية لإرسال البريد إلى Microsoft 365.

          عند الانتهاء، انقر فوق **"التالي**".

       2. في مربع الحوار **"قواعد تدفق بريد Exchange**"، حدد ما إذا كنت بحاجة إلى قاعدة تدفق بريد Exchange Online (تعرف أيضا باسم قاعدة النقل) التي تتخطى تصفية البريد العشوائي للرسائل الواردة من خدمة الحماية أو الجهاز التابع لجهة خارجية.

          من المحتمل أن يكون لديك بالفعل قاعدة تدفق بريد SCL=-1 في Exchange Online تسمح لجميع البريد الوارد من خدمة الحماية بتجاوز تصفية Microsoft 365 (معظم). تشجع العديد من خدمات الحماية أسلوب قاعدة تدفق البريد (SCL) لمستوى الثقة في البريد العشوائي هذا لعملاء Microsoft 365 الذين يستخدمون خدماتهم.

          كما هو موضح في الخطوة السابقة، يتم تكوين التصفية المحسنة للموصلات تلقائيا على الموصل الذي تحدده كمصدر للبريد من خدمة الحماية.

          سيؤدي تشغيل التصفية المحسنة للموصلات بدون قاعدة SCL=-1 للبريد الوارد من خدمة الحماية إلى تحسين قدرات الكشف عن ميزات حماية EOP مثل [التحليل الذكي للانتحال](anti-spoofing-protection.md)، ويمكن أن يؤثر على تسليم تلك الرسائل التي تم الكشف عنها حديثا (على سبيل المثال، الانتقال إلى مجلد البريد الإلكتروني غير الهام أو العزل). يقتصر هذا التأثير على نهج EOP؛ كما هو موضح سابقا، يتم إنشاء نهج Defender لـ Office 365 في وضع التدقيق.

          لإنشاء قاعدة تدفق بريد SCL=-1 أو لمراجعة القواعد الموجودة، انقر فوق الزر **"الانتقال إلى مركز إدارة Exchange** " على الصفحة. لمزيد من المعلومات، راجع [استخدام قواعد تدفق البريد لتعيين مستوى الثقة بالبريد العشوائي (SCL) في الرسائل في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

          عند الانتهاء، انقر فوق **"إنهاء**".

     - **إنني أستخدم Microsoft Exchange Online فقط**: تشير سجلات MX لمجالك إلى Microsoft 365. لم يتبقى شيء لتكوينه، لذلك انقر فوق **"إنهاء**".

5. يظهر مربع حوار تقدم أثناء إعداد التقييم. عند اكتمال الإعداد، انقر فوق **"تم**".

## <a name="set-up-an-evaluation-in-blocking-mode"></a>إعداد تقييم في وضع الحظر

1. انقر فوق **"بدء التقييم**".

2. في مربع الحوار **"تشغيل الحماية** "، حدد **"نعم"، وقم بحماية مؤسستي عن طريق حظر التهديدات**، ثم انقر فوق **"متابعة**".

3. في مربع الحوار **"تحديد المستخدمين الذين تريد تضمينهم** "، قم بتكوين الإعدادات التالية:

   - **كافة المستخدمين**: هذا هو الخيار الافتراضي والموصى به.
   - **حدد المستخدمين**: إذا حددت هذا الخيار، فستحتاج إلى تحديد المستلمين الداخليين الذين ينطبق عليهم التقييم:
     - **المستخدمون**: علب البريد أو مستخدمو البريد أو جهات اتصال البريد المحددة.
     - **المجموعات**:
       - أعضاء مجموعات التوزيع المحددة أو مجموعات الأمان الممكنة للبريد.
       - مجموعات Microsoft 365 المحددة.
     - **المجالات**: كافة المستلمين في [المجالات المقبولة المحددة](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) في مؤسستك.

     انقر في المربع المناسب، وابدأ بكتابة قيمة، وحدد القيمة التي تريدها من النتائج. كرر هذه العملية عدة مرات حسب الضرورة. لإزالة قيمة موجودة، انقر فوق "إزالة" ![الأيقونة "إزالة".](../../media/m365-cc-sc-remove-selection-icon.png) بجوار القيمة.

     بالنسبة للمستخدمين أو المجموعات، يمكنك استخدام معظم المعرفات (الاسم واسم العرض والاسم المستعار وعنوان البريد الإلكتروني واسم الحساب وما إلى ذلك)، ولكن يظهر اسم العرض المقابل في النتائج. بالنسبة للمستخدمين، أدخل علامة نجمية (\*) بحد ذاتها لمشاهدة كافة القيم المتوفرة.

   > [!NOTE]
   > يمكنك تغيير هذه التحديدات بعد الانتهاء من إعداد التقييم.

   عند الانتهاء، انقر فوق **"متابعة**".

4. يظهر مربع حوار تقدم أثناء إعداد التقييم. عند اكتمال الإعداد، انقر فوق **"تم**".

## <a name="reporting-in-audit-mode"></a>إعداد التقارير في وضع التدقيق

- يعرض [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report) عمليات الكشف حسب Defender لـ Office 365 في طرق العرض التالية:
  - [عرض البيانات حسب البرامج الضارة للبريد الإلكتروني \> وتفصيل المخطط حسب تقنية الكشف](view-email-security-reports.md#view-data-by-email--malware-and-chart-breakdown-by-detection-technology)
  - [عرض البيانات حسب التصيد الاحتيالي للبريد الإلكتروني \> وتفصيل المخطط حسب تقنية الكشف](view-email-security-reports.md#view-data-by-email--phish-and-chart-breakdown-by-detection-technology)

- في [مستكشف المخاطر](threat-explorer.md)، تظهر الرسائل التي تم الكشف عنها بواسطة تقييم Defender لـ Office 365 الشعار التالي في تفاصيل الإدخال:

  ![شعار الإعلام في تفاصيل الرسالة أن تقييم Defender لـ Office 365 كشف عن رسالة بريد إلكتروني ضارة.](../../media/evalv2-detection-banner.png)

<!--- This stuff is likely not applicable for V2 reporting --->

تدمج صفحة **التقييم Microsoft Defender لـ Office 365** في <https://security.microsoft.com/atpEvaluation> إعداد التقارير عن النهج في التقييم:

- حماية الانتحال في نهج مكافحة التصيد الاحتيالي
- الارتباطات الآمنة
- مرفقات آمنة

بشكل افتراضي، تعرض المخططات بيانات لآخر 30 يوما، ولكن يمكنك تصفية نطاق التاريخ بالنقر فوق أيقونة !["التقويم".](../../media/m365-cc-sc-add-internal-icon.png) **30 يوما** وتحديد من القيم الإضافية التالية التي تقل عن 30 يوما:

- 24 ساعة
- 7 أيام
- 14 يوماً
- نطاق التاريخ المخصص

يمكنك النقر فوق ![أيقونة "تنزيل".](../../media/m365-cc-sc-download-icon.png) **تنزيل** لتنزيل بيانات المخطط إلى ملف .csv.

## <a name="required-permissions"></a>الأذونات المطلوبة

يتم وصف الأذونات المطلوبة في **Azure AD** لإعداد تقييم Defender ل Microsoft 365 في القائمة التالية:

- **إنشاء تقييم أو تعديله أو حذفه**: مسؤول الأمان أو المسؤول العام.
- **عرض نهج التقييم والتقارير**: مسؤول الأمان أو قارئ الأمان.

لمزيد من المعلومات حول أذونات Azure AD في مدخل Microsoft 365 Defender، راجع [الأدوار Azure AD في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md#azure-ad-roles-in-the-microsoft-365-defender-portal)

## <a name="evaluation-policy-settings"></a>إعدادات نهج التقييم

يتم وصف الإعدادات في Defender لـ Office 365 التي تم إنشاؤها خصيصا للتقييم في الجداول التالية:

**إعدادات نهج تقييم مكافحة التصيد الاحتيالي**:

|اعداد|قيمه|
|---|---|
|AdminDisplayName|نهج التقييم|
|AuthenticationFailAction|MoveToJmf|
|تمكين|صحيح|
|EnableFirstContactSafetyTips|كاذبه|
|EnableMailboxIntelligence|صحيح|
|EnableMailboxIntelligenceProtection|صحيح|
|EnableOrganizationDomainsProtection|كاذبه|
|EnableSimilarDomainsSafetyTips|كاذبه|
|EnableSimilarUsersSafetyTips|كاذبه|
|EnableSpoofIntelligence|صحيح|
|EnableSuspiciousSafetyTip|كاذبه|
|EnableTargetedDomainsProtection|كاذبه|
|EnableTargetedUserProtection|كاذبه|
|EnableUnauthenticatedSender|صحيح|
|EnableUnusualCharactersSafetyTips|كاذبه|
|EnableViaTag|صحيح|
|Guid|قيمة GUID|
|انتحال الحمايةState|دليل|
|IsDefault|كاذبه|
|MailboxIntelligenceProtectionAction|NoAction|
|MailboxIntelligenceProtectionActionRecipients|{}|
|MailboxIntelligenceQuarantineTag|DefaultFullAccessPolicy|
|الاسم|نهج التقييم|
|PhishThresholdLevel|1|
|RecommendedPolicyType|التقييم|
|SpoofQuarantineTag|DefaultFullAccessPolicy|
|TargetedDomainActionRecipients|{}|
|TargetedDomainProtectionAction|NoAction|
|TargetedDomainQuarantineTag|DefaultFullAccessPolicy|
|TargetedUserActionRecipients|{}|
|TargetedUserProtectionAction|NoAction|
|TargetedUserQuarantineTag|DefaultFullAccessPolicy|
|||
|AntiPhishPolicyLevelDataList|فارغه|
|AntiSpoofEnforcementType|عاليه|
|AuthenticationSafetyTipText|فارغه|
|AuthenticationSoftPassSafetyTipText|فارغه|
|EnableAuthenticationSafetyTip|كاذبه|
|EnableAuthenticationSoftPassSafetyTip|كاذبه|
|علامة تعريف النهج|فارغه|
|SimilarUsersSafetyTipsCustomText|فارغه|
|TreatSoftPassAsAuthenticated|صحيح|
|غير عاديCharactersSafetyTipsCustomText|فارغه|
|||
|ExcludedDomains|{}|
|الendenders المستثناة|{}|
|TargetedDomainsToProtect|{}|
|TargetedUsersToProtect|{}|

**إعدادات نهج تقييم المرفقات الآمنة**:

|اعداد|قيمه|
|---|---|
|العمل|سماح|
|ActionOnError|صحيح|
|AdminDisplayName|نهج التقييم|
|ConfidenceLevelThreshold|80|
|تمكين|صحيح|
|EnableOrganizationBranding|كاذبه|
|Guid|قيمة GUID|
|IsBuiltInProtection|كاذبه|
|IsDefault|كاذبه|
|الاسم|نهج التقييم|
|OperationMode|تاخير|
|علامة الفحص|AdminOnlyAccessPolicy|
|RecommendedPolicyType|التقييم|
|اعاده توجيه|كاذبه|
|عنوان إعادة التوجيه|{}|
|المسح الضوئي|30|

**إعدادات نهج تقييم الارتباطات الآمنة**:

|اعداد|قيمه|
|---|---|
|AdminDisplayName|نهج التقييم|
|AllowClickThrough|كاذبه|
|نص التعليق المخصص|فارغه|
|DeliverMessageAfterScan|صحيح|
|DisableUrlRewrite|صحيح|
|عناوين Url DoNotRewrite|{}|
|EnableForInternalSenders|كاذبه|
|EnableOrganizationBranding|كاذبه|
|EnableSafeLinksForTeams|صحيح|
|Guid|قيمة GUID|
|IsBuiltInProtection|كاذبه|
|IsDefault|كاذبه|
|IsEnabled|صحيح|
|LocalizedNotificationTextList|{}|
|الاسم|"EvaluationPolicy"|
|RecommendedPolicyType|التقييم|
|فحوصات ضوئية|صحيح|
|TrackClicks|صحيح|
|||
|DoNotAllowClickThrough|فارغه|
|DoNotTrackUserClicks|كاذبه|
|EnableSafeLinksForEmail|صحيح|
|EnableSafeLinksForOffice|صحيح|
|عناوين Url المستبعدة|{}|
|عناوين Url ل WhiteListed|فارغه|
