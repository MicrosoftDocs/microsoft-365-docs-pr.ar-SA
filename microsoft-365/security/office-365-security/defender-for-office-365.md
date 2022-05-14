---
title: Microsoft Defender لـ Office 365 - CSH
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
description: تتضمن Microsoft Defender لـ Office 365 خزينة المرفقات وارتباطات خزينة وأدوات مكافحة التصيد الاحتيالي المتقدمة وأدوات إعداد التقارير وقدرات التحليل الذكي للمخاطر.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9be72102f9813394cb2d9eab1e4d163c6d87bd4b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417809"
---
# <a name="microsoft-defender-for-office-365"></a>Microsoft Defender لـ Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> هذه المقالة مخصصة لعملاء الأعمال الذين لديهم [Microsoft Defender لـ Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). إذا كنت تستخدم Outlook.com أو Microsoft 365 Family أو Microsoft 365 Personal، وكنت تبحث عن معلومات حول ارتباطات خزينة أو مرفقات خزينة في Outlook، فراجع [الأمان المتقدم Outlook.com للحصول على Microsoft 365 المشتركين](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Microsoft Defender لـ Office 365 تحمي مؤسستك من التهديدات الضارة التي تشكلها رسائل البريد الإلكتروني والارتباطات (عناوين URL) وأدوات التعاون. تتضمن Defender لـ Office 365 ما يلي:

- **[نهج الحماية من التهديدات](#configure-microsoft-defender-for-office-365-policies)**: حدد نهج الحماية من التهديدات لتعيين المستوى المناسب من الحماية لمؤسستك.

- **[التقارير](#view-microsoft-defender-for-office-365-reports)**: عرض التقارير في الوقت الحقيقي لمراقبة أداء Defender لـ Office 365 في مؤسستك.

- **[قدرات التحقيق في التهديدات والاستجابة](#use-threat-investigation-and-response-capabilities)** لها: استخدم أدوات الحافة الرائدة للتحقيق في التهديدات وفهمها ومحاكاتها ومنعها.

- **[قدرات التحقيق والاستجابة التلقائية](office-365-air.md)**: توفير الوقت والجهد في التحقيق في التهديدات والتخفيف من حدتها.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>دليل تفاعلي Microsoft Defender لـ Office 365

في هذا الدليل التفاعلي، ستتعلم كيفية حماية مؤسستك باستخدام Microsoft Defender لـ Office 365. سترى كيف يمكن Defender لـ Office 365 مساعدتك في تحديد نهج الحماية وتحليل التهديدات التي تتعرض لها مؤسستك والاستجابة للهجمات.

[اطلع على الدليل التفاعلي](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>الشروع

إذا كنت جديدا على Microsoft Defender لـ Office 365 أو تعلمت بشكل أفضل من خلال *القيام بذلك*، فقد تستفيد من تقسيم تكوين Defender لـ Office 365 الأولي إلى مجموعات، والتحقيق في التقارير وعرضها باستخدام هذه المقالة كمرجع. فيما يلي مجموعات التكوين المبكر المنطقية:

- تكوين كل شيء مع '*anti*' في الاسم.
  - مكافحة البرامج الضارة
  - مكافحة التصيد الاحتيالي
  - مكافحة البريد العشوائي
- قم بإعداد كل شيء باستخدام "*safe*" في الاسم.
  - الارتباطات الآمنة
  - مرفقات خزينة
- الدفاع عن أحمال العمل (على سبيل المثال. SharePoint Online و OneDrive و Teams)
- الحماية باستخدام الإزالة التلقائية بدون ساعة (ZAP).

للتعلم من خلال القيام بذلك، [انقر فوق هذا الارتباط](protect-against-threats.md).

> [!NOTE]
> تأتي Microsoft Defender لـ Office 365 في نوعين مختلفين من الخطط. يمكنك معرفة ما إذا كان لديك **الخطة 1** إذا كان لديك "الكشف في الوقت الحقيقي"، والخطة **2**، إذا كان لديك مستكشف المخاطر. تؤثر الخطة التي لديك على الأدوات التي ستراها، لذا تأكد من أنك على دراية بخطتك أثناء تعلمك.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender لـ Office 365 الخطة 1 والخطة 2

يلخص الجدول التالي ما هو مضمن في كل خطة.

|Microsoft Defender للخطة 1 من Office 365|Microsoft Defender للخطة 2 من Office 365|
|---|---|
|إمكانيات التكوين، والحماية، والكشف: <ul><li>[مرفقات آمنة](safe-attachments.md)</li><li>[الارتباطات الآمنة](safe-links.md)</li><li>[المرفقات الآمنة لـ SharePoint وOneDrive وMicrosoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[الحماية من التصيد الاحتيالي في Defender لـ Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[عمليات الكشف في الوقت الحقيقي](threat-explorer.md)</li></ul>|قدرات Microsoft Defender للخطة 1 من Office 365 <p> Plus <p> المستخدمون المحميون بالأتمتة والاستقصاء والمعالجة والتعلقدرات الأتمتة والتحقيق والمعالجة والتعليم: <ul><li>[متعقب المخاطر](threat-trackers.md)</li><li>[مستكشف المخاطر](threat-explorer.md)</li><li>[التحقيق التلقائي والاستجابة (AIR)](office-365-air.md)</li><li>[أتمتة المحاكاة في التدريب على محاكاة الهجوم](attack-simulation-training.md)</li><li>[البحث عن التهديدات بشكل استباقي باستخدام الصيد المتقدم في Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[التحقيق في الحوادث في Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[التحقيق في التنبيهات في Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- تم تضمين Microsoft Defender لـ Office 365 (الخطة 2) في Office 365 E5 وOffice 365 A5 وMicrosoft 365 E5.

- تم تضمين Microsoft Defender لـ Office 365 (الخطة 1) في Microsoft 365 Business Premium.

- يتوفر كل من Microsoft Defender لـ Office 365 (الخطة 1) وDefender لـ Office 365 (الخطة 2) كإضافة لبعض الاشتراكات. لمعرفة المزيد، يوجد ارتباط آخر [متوفر عبر خطط Microsoft Defender لـ Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- ميزة [المستندات الآمنة](safe-docs.md) متاحة فقط للمستخدمين الذين لديهم تراخيص أمان Microsoft 365 E5 أو Microsoft 365 E5 (غير مضمنة في خطط Microsoft Defender لـ Office 365).

- إذا كان اشتراكك الحالي لا يتضمن Microsoft Defender لـ Office 365 وتريده، [فاتصل بالمبيعات لبدء نسخة تجريبية](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html)، واكتشف كيف يمكن أن يعمل Microsoft Defender لـ Office 365 في مؤسستك.

- يتمتع عملاء Microsoft Defender for Office 365 P2 بإمكانية الوصول إلى **تكامل Microsoft 365 Defender** لاكتشاف الحوادث والتنبيهات ومراجعتها والرد عليها بكفاءة. 

شاهد هذا الفيديو القصير لمعرفة المزيد حول قدرات Microsoft Defender لـ Office 365 P2 التي انتقلت إلى مدخل Microsoft 365 Defender.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfx]


## <a name="configure-microsoft-defender-for-office-365-policies"></a>تكوين نهج Microsoft Defender لـ Office 365

باستخدام Microsoft Defender لـ Office 365، يمكن لفريق الأمان في مؤسستك تكوين الحماية من خلال تحديد النهج في مدخل Microsoft 365 Defender في <https://security.microsoft.com> نهج التعاون \> **& البريد الإلكتروني** **& قواعد نهج** \> **التهديد**. أو يمكنك الانتقال مباشرة إلى صفحة **نهج التهديد** باستخدام <https://security.microsoft.com/threatpolicy>.

تعرف على المزيد من خلال مشاهدة [هذا الفيديو](https://www.youtube.com/watch?v=vivvTmWJ_3c).

> [!TIP]
> للحصول على قائمة سريعة من النهج التي يجب تعريفها، راجع [الحماية من التهديدات](protect-against-threats.md).

## <a name="defender-for-office-365-policies"></a>نهج Defender لـ Office 365

تحدد النهج المحددة لمؤسستك مستوى السلوك والحماية للتهديدات المعرفة مسبقا. خيارات النهج مرنة للغاية. على سبيل المثال، يمكن لفريق الأمان في مؤسستك تعيين حماية دقيقة من التهديدات على مستوى المستخدم والمؤسسة والمستلم والمجال. من المهم مراجعة سياساتك بانتظام لأن التهديدات والتحديات الجديدة تظهر يوميا.

- **[خزينة المرفقات](safe-attachments.md)**: يوفر حماية لمدة صفر يوم لحماية نظام المراسلة، من خلال التحقق من مرفقات البريد الإلكتروني بحثا عن محتوى ضار. يقوم بتوجيه جميع الرسائل والمرفقات التي لا تحتوي على توقيع فيروس/برامج ضارة إلى بيئة خاصة، ثم يستخدم تقنيات التعلم الآلي والتحليل للكشف عن الأهداف الضارة. إذا لم يتم العثور على أي نشاط مريب، تتم إعادة توجيه الرسالة إلى علبة البريد. لمعرفة المزيد، راجع [إعداد نهج المرفقات خزينة](set-up-safe-attachments-policies.md).

- **[ارتباطات خزينة](safe-links.md)**: توفر التحقق من وقت النقر لعناوين URL، على سبيل المثال، في رسائل البريد الإلكتروني وملفات Office. الحماية مستمرة ويتم تطبيقها عبر المراسلة وبيئة Office. يتم مسح الارتباطات ضوئيا لكل نقرة: تظل الارتباطات الآمنة قابلة للوصول ويتم حظر الارتباطات الضارة ديناميكيا. لمعرفة المزيد، راجع [إعداد نهج الارتباطات خزينة](set-up-safe-links-policies.md).

- **[خزينة المرفقات SharePoint OneDrive Microsoft Teams](mdo-for-spo-odb-and-teams.md)**: يحمي مؤسستك عند تعاون المستخدمين ومشاركة الملفات، من خلال تحديد الملفات الضارة ومنعها في مواقع الفريق ومكتبات المستندات. لمعرفة المزيد، راجع [تشغيل Defender لـ Office 365 SharePoint OneDrive Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

- **[الحماية من التصيد الاحتيالي في Defender لـ Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)**: الكشف عن محاولات انتحال هوية المستخدمين والمجالات الداخلية أو المخصصة. وهو يطبق نماذج التعلم الآلي والخوارزميات المتقدمة للكشف عن الانتحال لتجنب هجمات التصيد الاحتيالي. لمعرفة المزيد، راجع [تكوين نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>عرض تقارير Microsoft Defender لـ Office 365

تتضمن Microsoft Defender لـ Office 365 [تقارير](view-reports-for-mdo.md) لمراقبة Defender لـ Office 365. يمكنك الوصول إلى التقارير في مدخل Microsoft 365 Defender في <https://security.microsoft.com> **تقارير** \> **التعاون** \> & **البريد الإلكتروني & البريد الإلكتروني**. أو يمكنك الانتقال مباشرة إلى صفحة **تقارير البريد الإلكتروني والتعاون** باستخدام <https://security.microsoft.com/securityreports>.

يتم تحديث التقارير في الوقت الحقيقي، مما يوفر لك أحدث النتائج المعرفية. كما تقدم هذه التقارير توصيات وتنبهك إلى التهديدات الداهمة. تتضمن التقارير المعرفة مسبقا ما يلي:

- [مستكشف التهديدات (أو عمليات الكشف في الوقت الحقيقي)](threat-explorer.md)
- [تقرير حالة الحماية من التهديدات](view-reports-for-mdo.md#threat-protection-status-report)
- ... والمزيد.

## <a name="use-threat-investigation-and-response-capabilities"></a>استخدام قدرات التحقيق في التهديدات والاستجابة لها

تتضمن Microsoft Defender لـ Office 365 الخطة 2 أفضل [أدوات التحقيق في التهديدات والاستجابة](office-365-ti.md) لها التي تمكن فريق الأمان في مؤسستك من توقع الهجمات الضارة وفهمها ومنعها.

- توفر **[أدوات تعقب التهديدات](threat-trackers.md)** أحدث المعلومات حول مشكلات الأمن السيبراني السائدة. على سبيل المثال، يمكنك عرض معلومات حول أحدث البرامج الضارة، واتخاذ تدابير عكسية قبل أن تصبح تهديدا فعليا لمؤسستك. تتضمن أدوات [التعقب المتوفرة أدوات تعقب جديرة بالملاحظة](threat-trackers.md#noteworthy-trackers) [ومتعقبات الاتجاهات](threat-trackers.md#trending-trackers) [والاستعلامات المتعقبة](threat-trackers.md#tracked-queries) [والاستعلامات المحفوظة](threat-trackers.md#saved-queries).

- **[مستكشف التهديدات (أو عمليات الكشف في الوقت الحقيقي)](threat-explorer.md)** (يشار إليها أيضا باسم Explorer) هو تقرير في الوقت الحقيقي يسمح لك بتحديد وتحليل التهديدات الأخيرة. يمكنك تكوين Explorer لإظهار البيانات لفترات مخصصة.

- يسمح لك **[التدريب على محاكاة الهجوم](attack-simulation-training.md)** بتشغيل سيناريوهات هجوم واقعية في مؤسستك لتحديد الثغرات الأمنية. تتوفر عمليات محاكاة لأنواع الهجمات الحالية، بما في ذلك جمع بيانات اعتماد التصيد الاحتيالي الرمح وهجمات المرفقات، وهجمات كلمات المرور وهجمات كلمة مرور القوة الغاشمة.

## <a name="save-time-with-automated-investigation-and-response"></a>توفير الوقت مع التحقيق التلقائي والاستجابة

(**جديد!**) عندما تحقق في هجوم إلكتروني محتمل، يكون الوقت في جوهره. كلما أسرعت في تحديد التهديدات والتخفيف من حدتها، كانت مؤسستك أفضل. تتضمن قدرات [التحقيق والاستجابة التلقائية](office-365-air.md) (AIR) مجموعة من أدلة مبادئ الأمان التي يمكن تشغيلها تلقائيا، مثل عند تشغيل تنبيه، أو يدويا، مثل من طريقة عرض في المستكشف. يمكن ل AIR توفير الوقت والجهد لفريق عمليات الأمان في التخفيف من التهديدات بفعالية وكفاءة. لمعرفة المزيد، راجع [AIR في Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>الأذونات المطلوبة لاستخدام ميزات Microsoft Defender لـ Office 365

للوصول إلى ميزات Microsoft Defender لـ Office 365، يجب تعيين دور مناسب لك. يتضمن الجدول التالي بعض الأمثلة:

|الدور أو مجموعة الأدوار|الموارد لمعرفة المزيد|
|---|---|
|المسؤول العام (إدارة المؤسسة)|يمكنك تعيين هذا الدور في Azure Active Directory أو في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|مسؤول الأمان|يمكنك تعيين هذا الدور في Azure Active Directory أو في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|إدارة المؤسسة في Exchange Online|[الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo) <p> [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)|
|البحث والإزالة|يتوفر هذا الدور فقط في مدخل Microsoft 365 Defender أو مدخل التوافق في Microsoft Purview. لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md) [والأذونات في مدخل التوافق في Microsoft Purview](../../compliance/microsoft-365-compliance-center-permissions.md).|
|||

## <a name="get-microsoft-defender-for-office-365"></a>الحصول على Microsoft Defender لـ Office 365

يتم تضمين Microsoft Defender لـ Office 365 في اشتراكات معينة، مثل Microsoft 365 E5 Office 365 E5 Office 365 A5 Microsoft 365 Business Premium. إذا لم يتضمن اشتراكك Defender لـ Office 365، يمكنك شراء Defender لـ Office 365 الخطة 1 أو Defender لـ Office 365 الخطة 2 كوظيفة إضافية لاشتراكات معينة. لمعرفة المزيد، راجع الموارد التالية:

- [Microsoft Defender لـ Office 365 توفر](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) قائمة الاشتراكات التي تتضمن خطط Defender لـ Office 365.

- [توفر الميزات عبر خطط Microsoft Defender لـ Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) لقائمة الميزات المضمنة في الخطة 1 و2.

- [احصل على Microsoft Defender لـ Office 365 المناسبة](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content) لمقارنة الخطط والشراء Defender لـ Office 365.

- [بدء تجربة مجانية](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>ميزات جديدة في Microsoft Defender لـ Office 365

تتم إضافة ميزات جديدة إلى Microsoft Defender لـ Office 365 باستمرار. لمعرفة المزيد، راجع الموارد التالية:

- يوفر [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365) قائمة بالميزات الجديدة في التطوير والطرح.

- يصف [وصف الخدمة Microsoft Defender لـ Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) الميزات والتوفر عبر خطط Defender لـ Office 365.

## <a name="see-also"></a>راجع أيضًا

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [التحقيق التلقائي والاستجابة (AIR) في Microsoft 365 Defender](../defender/m365d-autoir.md)
