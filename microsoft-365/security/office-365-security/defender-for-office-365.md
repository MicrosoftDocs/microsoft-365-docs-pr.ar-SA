---
title: Microsoft Defender Office 365 - CSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.assetid: e100fe7c-f2a1-4b7d-9e08-622330b83653
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- intro-overview
description: يتضمن Microsoft Defender for Office 365 مرفقات خزينة، خزينة ارتباطات، وأدوات متقدمة لمكافحة التصيد الاحتيالي، وأدوات إعداد التقارير، وإمكانيات المعلومات المتعلقة بالخطر.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b8041962ca1a696146f9a5828c66b1a6800c4b01
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683724"
---
# <a name="microsoft-defender-for-office-365"></a>Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> هذه المقالة مخصصة لعملاء الأعمال الذين لديهم [Microsoft Defender Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). إذا كنت تستخدم Outlook.com أو Microsoft 365 Family أو Microsoft 365 Personal، وتبحث عن معلومات حول ارتباطات خزينة أو مرفقات خزينة في Outlook، فاطلع على أمان [Outlook.com المتقدم ل Microsoft 365 المشتركين](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

يحمي Microsoft Defender Office 365 مؤسستك من التهديدات الضارة التي تفرضها رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون. يتضمن defender for Office 365:

- **[سياسات الحماية من المخاطر](#configure-microsoft-defender-for-office-365-policies)**: حدد سياسات الحماية من المخاطر لتعيين مستوى الحماية المناسب لمنظمتك.

- **[التقارير](#view-microsoft-defender-for-office-365-reports)**: يمكنك عرض التقارير في الوقت الحقيقي لمراقبة أداء Defender Office 365 في مؤسستك.

- **[قدرات الاستقصاء عن المخاطر والاستجابة](#use-threat-investigation-and-response-capabilities)** لها: استخدم الأدوات الرائدة للتحقق من التهديدات وفهمها ومحاكاةها ومنعها.

- **[قدرات الاستجابة والتحري التلقائي](office-365-air.md)**: وفر الوقت والجهد في التحقق من التهديدات وتخفيفها.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>دليل تفاعلي إلى Microsoft Defender Office 365

في هذا الدليل التفاعلي، ستتعرف على كيفية حماية مؤسستك باستخدام Microsoft Defender Office 365. ستشاهد كيف يمكن أن يساعدك Office 365 Defender for Office 365 في تحديد سياسات الحماية وتحليل التهديدات التي تواجهها مؤسستك والاستجابة للهجمات.

[الاطلاع على الدليل التفاعلي](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>بدء العمل

إذا كنت مستخدما جديدا ل Microsoft Defender ل Office 365 أو تعرفت على أفضل طريقة من خلال القيام بذلك، فقد تستفيد من تقسيم تكوين Defender الأولي ل Office 365 إلى أجزاء، والتحري، وعرض التقارير باستخدام هذه المقالة كمرجع. فيما يلي أجزاء تكوين منطقية مبكرة:

- قم بتكوين كل شيء *باستخدام 'anti*' في الاسم.
  - مكافحة البرامج الضارة
  - مكافحة التصيد الاحتيالي
  - مكافحة البريد العشوائي
- قم بإعداد كل شيء *باستخدام "آمن*" في الاسم.
  - الارتباطات الآمنة
  - خزينة المرفقات
- ادافع عن أحمال العمل (على بعض الحالات. SharePoint عبر الإنترنت OneDrive و Teams)
- الحماية باستخدام إزالة تلقائية لمدة ساعة (ZAP).

للتعرف من خلال القيام بذلك، [انقر فوق هذا الارتباط](protect-against-threats.md).

> [!NOTE]
> يأتي Microsoft Defender Office 365 في نوعين مختلفين من الخطط. يمكنك معرفة ما إذا كان لديك **الخطة 1** إذا كان لديك "الكشف في الوقت الحقيقي"، الخطة **2**، إذا كان لديك "مستكشف التهديدات". تؤثر الخطة التي تملكها على الأدوات التي ستشاهدها، لذا كن على يقين من أنك على علم بهذه الخطة عندما تتعلم.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender Office 365 الخطة 1 الخطة 2

يلخص الجدول التالي ما هو مضمن في كل خطة.

|Defender for Office 365 1|Defender for Office 365 2|
|---|---|
|قدرات التكوين والحماية والكشف: <ul><li>[خزينة المرفقات](safe-attachments.md)</li><li>[الارتباطات الآمنة](safe-links.md)</li><li>[خزينة المرفقات SharePoint OneDrive و Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[الحماية من التصيد الاحتيالي في Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[الكشف في الوقت الحقيقي](threat-explorer.md)</li></ul>|Defender for Office 365 الخطة 1 <p> --- بالإضافة إلى --- <p> إمكانات التنفيذ التلقائي، والتحري، والوساطة، والتعليم: <ul><li>[متعقبات التهديدات](threat-trackers.md)</li><li>[مستكشف التهديدات](threat-explorer.md)</li><li>[إجراء عمليات التحقيق والاستجابة التلقائية](office-365-air.md)</li><li>[التدريب على محاكاة الهجمات](attack-simulation-training.md)</li><li>[البحث الاستباقي عن التهديدات باستخدام الصيد المتقدم في Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[التحقق من الأحداث في Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[التحقق من التنبيهات في Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Microsoft Defender Office 365 الخطة 2 مضمنة في Office 365 E5 Office 365 A5 Microsoft 365 E5.

- Microsoft Defender Office 365 الخطة 1 مضمنة في Microsoft 365 Business Premium.

- يتوفر كل من Microsoft Defender Office 365 1 و Defender Office 365 الخطة 2 كل منهما كعناية إضافية لاشتراكات معينة. لمعرفة المزيد، إليك ارتباط آخر توفر ميزة [عبر Microsoft Defender Office 365 الجديدة](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- تتوفر [خزينة المستندات](safe-docs.md) فقط للمستخدمين الذين لديهم تراخيص Microsoft 365 E5 أو الأمان في Microsoft 365 E5 (غير مضمنة في Microsoft Defender لخطط Office 365).

- إذا لم يتضمن اشتراكك الحالي Microsoft Defender for Office 365 وتريده، فاتصل بالمبيعات لبدء تشغيل [](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html)الإصدار التجريبي، واكتشف كيف يمكن أن يعمل Microsoft Defender Office 365 في مؤسستك.

- يمكن لعملاء Microsoft Defender Office 365 P2 الوصول إلى تكامل Microsoft 365 Defender للكشف  عن الأحداث والتنبيهات ومراجعتها والاستجابة لها بفعالية.

## <a name="configure-microsoft-defender-for-office-365-policies"></a>تكوين Microsoft Defender Office 365 الجديدة

باستخدام Microsoft Defender Office 365، يمكن لفريق الأمان في مؤسستك تكوين الحماية من خلال تحديد سياسات <https://security.microsoft.com> في مدخل Microsoft 365 Defender في البريد الإلكتروني **&** \>  \> منهج التعاون & قواعد **المخاطر.** أو، يمكنك الانتقال مباشرة إلى صفحة **سياسات التهديدات باستخدام** <https://security.microsoft.com/threatpolicy>.

تعرف على المزيد من خلال [مشاهدة هذا الفيديو](https://www.youtube.com/watch?v=vivvTmWJ_3c).

> [!TIP]
> للحصول على قائمة سريعة من السياسات لتحديدها، راجع [الحماية من التهديدات](protect-against-threats.md).

## <a name="defender-for-office-365-policies"></a>Defender for Office 365 الجديدة

تحدد السياسات المعرفة لمنظمتك مستوى الحماية والسلوك للتهديدات المعرفة مسبقا. تتسم خيارات النهج بالمرونة القصوى. على سبيل المثال، يمكن لفريق الأمان في مؤسستك تعيين الحماية من المخاطر الدقيقة على مستوى المستخدم والمستلم والمستلم والمجال. من المهم مراجعة سياساتك بشكل منتظم بسبب ظهور تهديدات وتحديات جديدة يوميا.

- **[خزينة المرفقات](safe-attachments.md)**: توفير حماية لمدة يوم واحد لحماية نظام المراسلة، من خلال التحقق من مرفقات البريد الإلكتروني للمحتوى الضار. فهو يسلك كل الرسائل والمرفقات التي لا تملك توقيع فيروس/برنامج ضار إلى بيئة خاصة، ثم يستخدم تقنيات التعلم والتحليل الآلي للكشف عن النوايا الضارة. إذا لم يتم العثور على أي نشاط مريب، يتم إعادة توجيه الرسالة إلى علبة البريد. لمعرفة المزيد، راجع [إعداد خزينة المرفقات](set-up-safe-attachments-policies.md).

- **[خزينة الارتباطات](safe-links.md)**: يوفر التحقق من وقت النقر فوق عناوين URL، على سبيل المثال، في رسائل البريد الإلكتروني Office الملفات. الحماية مستمرة وتنطبق على المراسلة Office البيئة. يتم مسح الارتباطات ضوئيا لكل نقرة: تظل الارتباطات الآمنة قابلة للوصول إليها، كما يتم حظر الارتباطات الضارة ديناميكيا. لمعرفة المزيد، راجع [إعداد خزينة الارتباطات.](set-up-safe-links-policies.md)

- **[خزينة](mdo-for-spo-odb-and-teams.md)** المرفقات ل SharePoint و OneDrive و Microsoft Teams: تحمي مؤسستك عندما يتعاون المستخدمون مع الآخرين ويتشاركون الملفات، عن طريق تحديد الملفات الضارة وحظرها في مواقع الفريق ومكتبات المستندات. لمعرفة المزيد، راجع تشغيل [Defender Office 365 SharePoint OneDrive Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

- **[الحماية من التصيد الاحتيالي في Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)**: الكشف عن محاولات انتحال هوية المستخدمين والمجالات الداخلية أو المخصصة. وهو يطبق نماذج التعلم الآلي والخوارزميات المتقدمة للكشف عن التصيد الاحتيالي لتجنب هجمات التصيد الاحتيالي. لمعرفة المزيد، راجع تكوين سياسات مكافحة التصيد الاحتيالي [في Microsoft Defender Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>عرض Microsoft Defender لتقارير Office 365

يتضمن Microsoft Defender Office 365 [تقارير](view-reports-for-mdo.md) لمراقبة Defender Office 365. يمكنك الوصول إلى التقارير في مدخلMicrosoft 365 Defender <https://security.microsoft.com> في **تقارير** \> البريد الإلكتروني & **البريد** \> الإلكتروني & **التعاون**. أو، يمكنك الانتقال مباشرة إلى **صفحة البريد الإلكتروني تقارير التعاون** باستخدام <https://security.microsoft.com/securityreports>.

يتم تحديث التقارير في الوقت الحقيقي، مما يوفر لك أحدث الرؤى. توفر هذه التقارير أيضا توصيات وتتنبهك إلى تهديدات وشيكة الحدوث. تتضمن التقارير المحددة مسبقا ما يلي:

- [مستكشف التهديدات (أو الكشف في الوقت الحقيقي)](threat-explorer.md)
- [تقرير حالة الحماية من المخاطر](view-reports-for-mdo.md#threat-protection-status-report)
- ... والمزيد.

## <a name="use-threat-investigation-and-response-capabilities"></a>استخدام قدرات الاستجابة والتحري عن المخاطر

يتضمن Microsoft Defender Office 365 الخطة 2 أفضل أدوات الاستجابة والتحري عن المخاطر التي تمكن [](office-365-ti.md) فريق الأمان في مؤسستك من توقع الهجمات الضارة وفهمها ومنعها.

- **[توفر متعقبات](threat-trackers.md)** المخاطر أحدث المعلومات حول مشاكل الأمن الإلكتروني السائدة. على سبيل المثال، يمكنك عرض معلومات حول البرامج الضارة الأخيرة، واتخاذ تدابير مقابلة قبل أن تصبح خطرا فعليا على مؤسستك. تتضمن متعقبات التعقب المتوفرة المتعقبات الجديرة [بالملاحظة](threat-trackers.md#noteworthy-trackers) ومتعقبات الاتجاهات [والاستعلامات](threat-trackers.md#tracked-queries) المتعقبة [والاستعلامات المحفوظة](threat-trackers.md#saved-queries). [](threat-trackers.md#trending-trackers)

- **[إن "مستكشف](threat-explorer.md)** التهديدات" (أو الكشف في الوقت الحقيقي) (يشار إليه أيضا باسم "المستكشف") هو تقرير في الوقت الحقيقي يسمح لك بتحديد التهديدات الأخيرة وتحليلها. يمكنك تكوين المستكشف لإظهار البيانات لفترات مخصصة.

- **[يسمح لك التدريب على محاكاة](attack-simulation-training.md)** الهجمات بتشغيل سيناريوهات هجوم واقعية في مؤسستك لتحديد نقاط الضعف. تتوفر عمليات محاكاة للأنواع الحالية من الهجمات، بما في ذلك عمليات تجميع بيانات اعتماد التصيد الاحتيالي وهجمات المرفقات وهجمات استخدام كلمات المرور وهجمات القوة الغاشمة بكلمات المرور.

## <a name="save-time-with-automated-investigation-and-response"></a>توفير الوقت باستخدام الاستجابة والتحري التلقائي

(**جديد!**) عندما تقوم بالتحري عن هجوم إلكتروني محتمل، يكون الوقت في جوهره. كلما أسرعت في تحديد التهديدات وتخفيفها، كانت مؤسستك أفضل. تتضمن [إمكانات](office-365-air.md) الاستجابة والتحريك التلقائية (AIR) مجموعة من دفاتر تشغيل الأمان التي يمكن تشغيلها تلقائيا، مثل عند تشغيل تنبيه، أو يدويا، مثل من طريقة عرض في المستكشف. يمكن أن توفر AIR وقت فريق عمليات الأمان وجهدها في التخفيف من المخاطر بفعالية وفعالية. لمعرفة المزيد، راجع [AIR في Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>الأذونات المطلوبة لاستخدام Microsoft Defender Office 365 الميزات

للوصول إلى Microsoft Defender Office 365 الميزات، يجب أن يتم تعيين دور مناسب لك. يتضمن الجدول التالي بعض الأمثلة:

|مجموعة الدور أو الدور|الموارد لمعرفة المزيد|
|---|---|
|المسؤول العام (إدارة المؤسسة)|يمكنك تعيين هذا الدور في Azure Active Directory أو في Microsoft 365 Defender الإلكتروني. لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).|
|مسؤول الأمان|يمكنك تعيين هذا الدور في Azure Active Directory أو في Microsoft 365 Defender الإلكتروني. لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).|
|إدارة المؤسسة في Exchange Online|[الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo) <p> [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)|
|البحث و الازدحام|يتوفر هذا الدور فقط في مدخل Microsoft 365 Defender أو مركز التوافق في Microsoft 365. لمزيد من المعلومات، راجع الأذونات في Microsoft 365 Defender [والأذونات في مركز التوافق في Microsoft 365](../../compliance/microsoft-365-compliance-center-permissions.md).[](permissions-microsoft-365-security-center.md)|
|||

## <a name="get-microsoft-defender-for-office-365"></a>الحصول على Microsoft Defender Office 365

يتم تضمين Microsoft Defender Office 365 في اشتراكات معينة، مثل Microsoft 365 E5 و Office 365 E5 و Office 365 A5 و Microsoft 365 Business Premium. إذا لم يتضمن اشتراكك Defender for Office 365، يمكنك شراء Defender for Office 365 الخطة 1 أو Defender for Office 365 الخطة 2 كعينة أخرى لاشتراكات معينة. لمعرفة المزيد، راجع الموارد التالية:

- [يوفر Microsoft Defender Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) قائمة الاشتراكات التي تتضمن Defender Office 365 الجديدة.

- [توفر الميزات عبر Microsoft Defender Office 365 للحصول](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) على قائمة بالميزات المضمنة في الخطة 1 و2.

- [احصل على Microsoft Defender المناسب Office 365](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content) لمقارنة الخطط وشراء Defender Office 365.

- [بدء تجربة مجانية](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>الميزات الجديدة في Microsoft Defender Office 365

تضاف الميزات الجديدة إلى Microsoft Defender Office 365 باستمرار. لمعرفة المزيد، راجع الموارد التالية:

- [Microsoft 365 خريطة](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365) الطريق قائمة بالميزات الجديدة في التطوير وال طرحها.

- [يصف Microsoft Defender Office 365 وصف](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) الخدمة الميزات والتوفر عبر Defender Office 365 الإضافية.

## <a name="see-also"></a>راجع أيضًا

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [إجراء عمليات التحقيق والاستجابة التلقائية (AIR) في Microsoft 365 Defender](../defender/m365d-autoir.md)
