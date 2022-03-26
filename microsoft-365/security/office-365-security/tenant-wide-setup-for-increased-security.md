---
title: تكوين مستأجر Microsoft 365 المستأجر لزيادة الأمان
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 10/11/2018
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: 8d274fe3-db51-4107-ba64-865e7155b355
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: يهيأ لك هذا الموضوع من خلال التكوين الموصى به لإعدادات نطاق المستأجر التي تؤثر على أمان بيئة Microsoft 365 الخاصة بك.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 82e96b4b35d5095a6844618125ee49f1dba6ffd6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567184"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>تكوين مستأجر Microsoft 365 المستأجر لزيادة الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يهيأ لك هذا الموضوع من خلال التكوين الموصى به لإعدادات نطاق المستأجر التي تؤثر على أمان بيئة Microsoft 365 الخاصة بك. قد تتطلب احتياجات الأمان الخاصة بك المزيد أو أقل من الأمان. استخدم هذه التوصيات كنقطة بداية.

## <a name="check-office-365-secure-score"></a>التحقق Office 365 نقاط آمنة

Office 365 تقوم Secure Score بتحليل أمان مؤسستك استنادا إلى الأنشطة العادية وإعدادات الأمان وتعيين درجة. ابدأ بتبشير نقاطك الحالية. سيزيد ضبط بعض الإعدادات على مستوى المستأجر من نقاطك. الهدف ليس تحقيق الحد الأقصى من النقاط، ولكن أن تكون على دراية بالفرص المتاحة لحماية بيئتك التي لا تؤثر سلبا على إنتاجية المستخدمين. راجع [Microsoft Secure Score](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>ضبط سياسات إدارة المخاطر في مدخل Microsoft 365 Defender

يتضمن Microsoft 365 Defender المدخل قدرات تحمي بيئتك. كما يتضمن أيضا التقارير لوحات المعلومات التي يمكنك استخدامها لمراقبة واتخاذ إجراء. تأتي بعض المناطق مع تكوينات النهج الافتراضية. لا تتضمن بعض المناطق سياسات أو قواعد افتراضية. تفضل بزيارة  هذه &  \> \> البريد الإلكتروني & ونهج التهديدات للقواعد لضبط إعدادات إدارة المخاطر لبيئة أكثر أمانا.

<br>

****

|المنطقة|النهج الافتراضي؟|توصية|
|---|---|---|
|**مكافحة التصيد الاحتيالي**|نعم|قم بتكوين نهج مكافحة التصيد الاحتيالي الافتراضي كما هو موضح هنا: تكوين إعدادات الحماية من التصيد الاحتيالي في [EOP](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365) و Defender Office 365. <p> مزيد من المعلومات: <ul><li>[سياسات مكافحة التصيد الاحتيالي في Microsoft 365](set-up-anti-phishing-policies.md)</li><li>[إعدادات نهج مكافحة التصيد الاحتيالي المستحسنة في Microsoft Defender Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [نظرة ثاقبة حول انتحال](impersonation-insight.md)</li><li>[المعلومات الاستخبارية المنتحلة في EOP](learn-about-spoof-intelligence.md)</li><li>[إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md).</li></ul>|
|**مشغل مكافحة البرامج الضارة**|نعم|قم بتكوين نهج الحماية من البرامج الضارة الافتراضي كما هو موضح هنا: تكوين إعدادات الحماية من البرامج الضارة [في EOP](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> مزيد من المعلومات: <ul><li>[الحماية من البرامج الضارة](anti-malware-protection.md)</li><li>[إعدادات نهج مكافحة البرامج الضارة الموصى بها](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[تكوين سياسات مكافحة البرامج الضارة](configure-anti-malware-policies.md)</li></ul>|
|**خزينة المرفقات في Defender for Office 365**|لا|قم بتكوين الإعدادات العامة خزينة المرفقات وإنشاء نهج مرفقات خزينة كما هو موضح هنا: تكوين خزينة المرفقات في [Microsoft Defender Office 365](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> مزيد من المعلومات: <ul><li>[إعدادات المرفقات خزينة المستحسنة](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[خزينة المرفقات في Microsoft Defender Office 365](safe-attachments.md)</li><li>[إعداد خزينة المرفقات](set-up-safe-attachments-policies.md)</li><li>[خزينة المرفقات SharePoint OneDrive و Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[أمان المستندات في Microsoft 365 E5](safe-docs.md)</li></ul>|
|**خزينة ارتباطات في Microsoft Defender Office 365**|لا|قم بتكوين الإعدادات العامة خزينة الارتباطات وإنشاء نهج ارتباطات خزينة كما هو موضح هنا: تكوين إعدادات خزينة الارتباطات في [Microsoft Defender Office 365](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> مزيد من المعلومات: <ul><li>[إعدادات الارتباطات خزينة المستحسنة](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[إعداد خزينة الارتباطات](set-up-safe-links-policies.md)</li><li>[خزينة ارتباطات في Microsoft Defender Office 365](safe-links.md)</li><li>[تكوين الإعدادات خزينة ارتباطات في Microsoft Defender Office 365](configure-global-settings-for-safe-links.md)</li></ul>|
|**مكافحة البريد العشوائي (تصفية البريد)**|نعم|تكوين نهج مكافحة البريد العشوائي الافتراضي كما هو موضح هنا: تكوين إعدادات الحماية من البريد العشوائي [في EOP](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> مزيد من المعلومات: <ul><li>[إعدادات نهج مكافحة البريد العشوائي الموصى بها](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[الحماية من البريد العشوائي في EOP](anti-spam-protection.md)</li><li>[تكوين سياسات مكافحة البريد العشوائي في EOP](configure-your-spam-filter-policies.md)</li></ul>|
|***مصادقة البريد الإلكتروني***|نعم|تستخدم مصادقة البريد الإلكتروني سجلات DNS لإضافة معلومات يمكن التحقق منها إلى رسائل البريد الإلكتروني حول مصدر الرسالة والمرسل. Microsoft 365 تلقائيا مصادقة البريد الإلكتروني لمجالها الافتراضي (onmicrosoft.com)، ولكن Microsoft 365 يمكن لمسؤولي البريد الإلكتروني أيضا تكوين مصادقة البريد الإلكتروني للمجالات المخصصة. يتم استخدام ثلاث طرق مصادقة: <ul><li>إطار نهج المرسل (أو SPF).</li><ul><li>للحصول على الإعداد، راجع [إعداد SPF في Microsoft 365 للمساعدة في منع التهزاء](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>راجع [استخدام DKIM للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك المخصص](use-dkim-to-validate-outbound-email.md).</li><li>بعد تكوين DKIM، قم بتمكينه في Microsoft 365 Defender.</li></ul><li>مصادقة الرسائل وإعداد التقارير والتوافق (DMARC) المستندة إلى المجال.</li><ul><li>لإعداد DMARC[، استخدم DMARC للتحقق من صحة البريد الإلكتروني في Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|
|

> [!NOTE]
> بالنسبة إلى عمليات النشر غير القياسية ل SPF، والنشرات المختلطة، استكشاف الأخطاء وإصلاحها: كيفية استخدام Microsoft 365 نهج المرسل [(SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) لمنع الانتحال.

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>عرض لوحات المعلومات والتقارير في مدخل Microsoft 365 Defender

تفضل بزيارة هذه التقارير لوحات المعلومات للتعرف على المزيد حول حماية بيئتك. ستصبح البيانات الموجودة في هذه التقارير أغنى عندما تستخدم مؤسستك Office 365 أخرى. في الوقت الحالي، تعرف على ما يمكنك مراقبته واتخاذ إجراء بشأنه.

<br>

****

|لوحة المعلومات|الوصف|
|---|---|
|تقارير أمان البريد الإلكتروني|تتوفر هذه التقارير في Exchange Online Protection. لمزيد من المعلومات، راجع [عرض تقارير أمان البريد الإلكتروني في Microsoft 365 Defender الإلكتروني](view-email-security-reports.md).|
|Defender for Office 365 التقارير|تتوفر التقارير فقط في Defender for Office 365. لمزيد من المعلومات، راجع [عرض Defender Office 365 التقارير في Microsoft 365 Defender المدخل](view-reports-for-mdo.md).|
|تقارير تدفق البريد وإحصاءاته|تتوفر هذه التقارير والأفكار في مركز إدارة Exchange (EAC). لمزيد من المعلومات، راجع [تقارير تدفق البريد](/exchange/monitoring/mail-flow-reports/mail-flow-reports) ورؤى [تدفق البريد](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[مستكشف التهديدات (أو الكشف في الوقت الحقيقي)](threat-explorer.md)|إذا كنت تقوم بالتحري عن هجوم على المستأجر أو تواجهه، فاستخدم المستكشف (أو الكشف في الوقت الحقيقي) لتحليل التهديدات. يعرض المستكشف (تقرير الكشف في الوقت الحقيقي) حجم الهجمات مع مرور الوقت، كما يمكنك تحليل هذه البيانات حسب التهديدات التي تواجهها العائلات والبنية الأساسية للمهاجمين والمزيد. يمكنك أيضا وضع علامة على أي بريد إلكتروني مريب لقائمة "الأحداث".|
|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>تكوين إعدادات إضافية Exchange Online نطاق المستأجر

فيما يلي بعض الإعدادات الإضافية المستحسنة.

<br>

****

|المنطقة|توصية|
|---|---|
|**قواعد تدفق البريد** (المعروفة أيضا بقواعد النقل)|أضف قاعدة تدفق البريد للمساعدة في الحماية من برامج الفدية الضارة من خلال حظر أنواع الملفات القابلة للتنفيذ Office أنواع الملفات التي تحتوي على وحدات ماكرو. لمزيد من المعلومات، راجع [استخدام قواعد تدفق البريد لفحص](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments) مرفقات الرسائل في Exchange Online. <p> راجع المواضيع الإضافية التالية: <ul><li>[الحماية من برامج الفدية الضارة](../../admin/security-and-compliance/secure-your-business-data.md#5-protect-against-ransomware)</li><li>[الحماية من البرامج الضارة والفدية الضارة في Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[استرداد من هجوم برامج الفدية الضارة في Office 365](recover-from-ransomware.md)</li></ul> <p> إنشاء قاعدة تدفق البريد لمنع إعادة توجيه البريد الإلكتروني إلى مجالات خارجية بشكل تلقائي. لمزيد من المعلومات، راجع تخفيف قواعد إعادة توجيه العميل [الخارجية باستخدام نقاط آمنة](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score). <p> مزيد من المعلومات: [قواعد تدفق البريد (قواعد النقل) في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**المصادقة الحديثة**|المصادقة الحديثة هي أحد المتطلبات الأساسية لاستخدام المصادقة متعددة العوامل (MFA). يوصى باستخدام MFA لتأمين الوصول إلى موارد السحابة، بما في ذلك البريد الإلكتروني. <p> راجع المواضيع التالية: <ul><li>[تمكين المصادقة الحديثة أو تعطيلها في Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype for Business عبر الإنترنت: تمكين المستأجر للمصادقة الحديثة](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> يتم تمكين المصادقة الحديثة بشكل افتراضي Office عملاء 2016 SharePoint عبر الإنترنت OneDrive for Business. <p> مزيد من المعلومات: [كيفية عمل المصادقة الحديثة Office 2013 Office عميل 2016](../../enterprise/modern-auth-for-office-2013-and-2016.md)|
|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>تكوين سياسات المشاركة على مستوى المستأجر في SharePoint إدارة

توصيات Microsoft لتكوين مواقع SharePoint في مستويات حماية متزايدة، بدءا من حماية الأساس. لمزيد من المعلومات، راجع توصيات النهج [لتأمين SharePoint والملفات](sharepoint-file-access-policies.md).

SharePoint مواقع الفريق التي تم تكوينها على مستوى الأساس مشاركة الملفات مع مستخدمين خارجيين باستخدام ارتباطات الوصول المجهولة. يوصى باستخدام هذه الطريقة بدلا من إرسال الملفات بالبريد الإلكتروني.

لدعم أهداف حماية الأساس، قم بتكوين سياسات المشاركة على مستوى المستأجر كما هو مستحسن هنا. قد تكون إعدادات المشاركة للمواقع الفردية أكثر تقييدا من هذا النهج على نطاق المستأجر، ولكنها لا تكون أكثر اتساما بذاتها.

<br>

****

|المنطقة|يتضمن نهج افتراضي|توصية|
|---|---|---|
|**المشاركة** (SharePoint عبر الإنترنت OneDrive for Business)|نعم|يتم تمكين المشاركة الخارجية بشكل افتراضي. من المستحسن هذه الإعدادات: <ul><li>السماح بالمشاركة لمستخدمين خارجيين مصدقين واستخدام ارتباطات وصول مجهولة (إعداد افتراضي).</li><li>تنتهي صلاحية ارتباطات الوصول المجهولة في هذا العدد من الأيام. أدخل رقما، إذا أردت، مثل 30 يوما.</li><li>نوع الارتباط الافتراضي — حدد داخلي (الأشخاص في المؤسسة فقط). يجب على المستخدمين الذين يرغبون في المشاركة باستخدام الارتباطات المجهولة اختيار هذا الخيار من قائمة المشاركة.</li></ul> <p> مزيد من المعلومات: [نظرة عامة حول المشاركة الخارجية](/sharepoint/external-sharing-overview)|
|

SharePoint مركز إدارة OneDrive for Business الإدارة على الإعدادات نفسها. تنطبق الإعدادات في أي من مركزي الإدارة على كليهما.

## <a name="configure-settings-in-azure-active-directory"></a>تكوين الإعدادات في Azure Active Directory

تأكد من زيارة هاتين المنطقتين في Azure Active Directory لإكمال الإعداد على مستوى المستأجر لبيئات أكثر أمانا.

### <a name="configure-named-locations-under-conditional-access"></a>تكوين المواقع المسماة (ضمن الوصول الشرطي)

إذا كانت مؤسستك تتضمن مكاتب ذات وصول آمن إلى الشبكة، ف أضف نطاقات عناوين IP الموثوق بها إلى Azure Active Directory كمواد مسماة. تساعد هذه الميزة على تقليل عدد الإيجابيات الخاطئة التي تم تسجيلها في أحداث مخاطر تسجيل الدخول.

راجع: [المواقع المسماة في Azure Active Directory](/azure/active-directory/active-directory-named-locations)

### <a name="block-apps-that-dont-support-modern-authentication"></a>حظر التطبيقات التي لا تدعم المصادقة الحديثة

تتطلب المصادقة متعددة العوامل التطبيقات التي تدعم المصادقة الحديثة. لا يمكن حظر التطبيقات التي لا تدعم المصادقة الحديثة باستخدام قواعد الوصول الشرطي.

بالنسبة للبيئات الآمنة، تأكد من تعطيل المصادقة للتطبيقات التي لا تدعم المصادقة الحديثة. يمكنك القيام بذلك في Azure Active Directory باستخدام عنصر تحكم قادم قريبا.

في هذه الأثناء، استخدم أحد الأساليب التالية لتنفيذ هذا SharePoint عبر الإنترنت OneDrive for Business:

- استخدم PowerShell، راجع [حظر التطبيقات التي لا تستخدم المصادقة الحديثة](/mem/intune/protect/app-modern-authentication-block).
- قم بتكوين ذلك في مركز إدارة SharePoint <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">على</a> صفحة "الوصول إلى الجهاز" — "التحكم في الوصول من التطبيقات التي لا تستخدم المصادقة الحديثة". اختر حظر.

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>بدء استخدام Defender for Cloud Apps أو أمان التطبيقات على السحابة لـ Office 365

استخدم أمان التطبيقات على السحابة لـ Office 365 لتقييم المخاطر، والتنبيه إلى نشاط مريب، واتخاذ إجراء تلقائيا. يتطلب Office 365 E5 خطة.

أو استخدم Microsoft Defender لتطبيقات السحابة للحصول على رؤية أكثر عمقا حتى بعد منح حق الوصول، والتحكم الشامل، والحماية المحسنة لجميع تطبيقات السحابة، بما في ذلك التطبيقات Office 365.

نظرا لأن هذا الحل يوصي لخطة EMS E5، نوصيك بالبدء باستخدام Defender for Cloud Apps حتى تتمكن من استخدام هذا مع تطبيقات SaaS الأخرى في بيئتك. ابدأ باستخدام الإعدادات والسياسات الافتراضية.

مزيد من المعلومات:

- [نشر Defender لتطبيقات السحابة](/cloud-app-security/getting-started-with-cloud-app-security)
- [مزيد من المعلومات حول Microsoft Defender لتطبيقات السحابة](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [ما هو Defender for Cloud Apps؟](/cloud-app-security/what-is-cloud-app-security)

![لوحة معلومات Defender for Cloud Apps.](../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png)

## <a name="additional-resources"></a>موارد إضافية

توفر هذه المقالات و الدليل معلومات وصفية إضافية لتأمين بيئة Microsoft 365 الخاصة بك:

- [إرشادات أمان Microsoft للحملات](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) السياسية و المؤسسات غير الربحية وغيرها من مؤسسات agile (يمكنك استخدام هذه التوصيات في أي بيئة، ولا سيما البيئات السحابية فقط)

- [سياسات الأمان الموصى](microsoft-365-policies-configurations.md) بها وتكوينات الهويات والأجهزة (تتضمن هذه التوصيات تعليمات لبيئات AD FS)
