---
title: تكوين مستأجر Microsoft 365 لزيادة الأمان
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 04/06/2022
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
description: يرشدك هذا الموضوع خلال التكوين الموصى به للإعدادات على مستوى المستأجر التي تؤثر على أمان بيئة Microsoft 365 الخاصة بك.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 30b46bd541f233430506766eabc2d667fad52c22
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097283"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>تكوين مستأجر Microsoft 365 لزيادة الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يرشدك هذا الموضوع خلال التكوين الموصى به للإعدادات على مستوى المستأجر التي تؤثر على أمان بيئة Microsoft 365 الخاصة بك. قد تتطلب احتياجات الأمان الخاصة بك أمانا أكثر أو أقل. استخدم هذه التوصيات كنقطة بداية.

## <a name="check-office-365-secure-score"></a>التحقق من Office 365 درجة الأمان

Office 365 تقوم درجة الأمان بتحليل أمان مؤسستك استنادا إلى الأنشطة العادية وإعدادات الأمان وتعيين درجة. ابدأ بتدوين درجاتك الحالية. سيؤدي ضبط بعض الإعدادات على مستوى المستأجر إلى زيادة درجاتك. الهدف ليس تحقيق أقصى درجة، ولكن أن تكون على دراية بالفرص لحماية بيئتك التي لا تؤثر سلبا على إنتاجية المستخدمين. راجع [نقاط أمان Microsoft](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>ضبط نهج إدارة التهديدات في مدخل Microsoft 365 Defender

يتضمن مدخل Microsoft 365 Defender القدرات التي تحمي البيئة الخاصة بك. كما يتضمن التقارير ولوحات المعلومات التي يمكنك استخدامها لمراقبة واتخاذ إجراء. تأتي بعض المناطق مع تكوينات النهج الافتراضية. لا تتضمن بعض المناطق نهج أو قواعد افتراضية. تفضل بزيارة هذه النهج ضمن نهج التعاون \> **& البريد الإلكتروني** **& قواعد نهج** \> **التهديد** لضبط إعدادات إدارة التهديدات لبيئة أكثر أمانا.

|منطقه|النهج الافتراضي؟|توصية|
|---|---|---|
|**مكافحة التصيد الاحتيالي**|نعم|تكوين نهج مكافحة التصيد الاحتيالي الافتراضي كما هو موضح هنا: [تكوين إعدادات الحماية من التصيد الاحتيالي في EOP Defender لـ Office 365](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365). <p> مزيد من المعلومات: <ul><li>[نهج مكافحة التصيد الاحتيالي في Microsoft 365](set-up-anti-phishing-policies.md)</li><li>[إعدادات نهج مكافحة التصيد الاحتيالي الموصى بها في Microsoft Defender لـ Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [نظرة ثاقبة حول انتحال الهوية](impersonation-insight.md)</li><li>[تزييف التحليل الذكي في EOP](learn-about-spoof-intelligence.md)</li><li>[إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md).</li></ul>|
|**محرك مكافحة البرامج الضارة**|نعم|تكوين نهج مكافحة البرامج الضارة الافتراضي كما هو موضح هنا: [تكوين إعدادات الحماية من البرامج الضارة في EOP](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> مزيد من المعلومات: <ul><li>[الحماية من البرامج الضارة](anti-malware-protection.md)</li><li>[إعدادات نهج مكافحة البرامج الضارة الموصى بها](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[تكوين نهج مكافحة البرامج الضارة](configure-anti-malware-policies.md)</li></ul>|
|**المرفقات الآمنة في Defender لـ Office 365**|لا|تكوين الإعدادات العمومية لمرفقات خزينة وإنشاء نهج مرفقات خزينة كما هو موضح هنا: [تكوين إعدادات المرفقات خزينة في Microsoft Defender لـ Office 365](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> مزيد من المعلومات: <ul><li>[إعدادات المرفقات خزينة المستحسنة](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[خزينة المرفقات في Microsoft Defender لـ Office 365](safe-attachments.md)</li><li>[إعداد نهج المرفقات خزينة](set-up-safe-attachments-policies.md)</li><li>[المرفقات الآمنة لـ SharePoint وOneDrive وMicrosoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[أمان المستندات في Microsoft 365 E5](safe-docs.md)</li></ul>|
|**ارتباطات خزينة في Microsoft Defender لـ Office 365**|لا|تكوين الإعدادات العمومية للارتباطات خزينة وإنشاء نهج ارتباطات خزينة كما هو موضح هنا: [تكوين إعدادات الارتباطات خزينة في Microsoft Defender لـ Office 365](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> مزيد من المعلومات: <ul><li>[إعدادات ارتباطات خزينة الموصى بها](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[إعداد نهج ارتباطات خزينة](set-up-safe-links-policies.md)</li><li>[ارتباطات خزينة في Microsoft Defender لـ Office 365](safe-links.md)</li><li>[تكوين الإعدادات العمومية للارتباطات خزينة في Microsoft Defender لـ Office 365](configure-global-settings-for-safe-links.md)</li></ul>|
|**مكافحة البريد العشوائي (تصفية البريد)**|نعم|تكوين نهج مكافحة البريد العشوائي الافتراضي كما هو موضح هنا: [تكوين إعدادات الحماية من البريد العشوائي في EOP](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> مزيد من المعلومات: <ul><li>[إعدادات نهج مكافحة البريد العشوائي الموصى بها](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[الحماية من البريد العشوائي في EOP](anti-spam-protection.md)</li><li>[تكوين نهج مكافحة البريد العشوائي في EOP](configure-your-spam-filter-policies.md)</li></ul>|
|***مصادقة البريد الإلكتروني***|نعم|تستخدم مصادقة البريد الإلكتروني سجلات DNS لإضافة معلومات يمكن التحقق منها إلى رسائل البريد الإلكتروني حول مصدر الرسالة والمرسل. Microsoft 365 تكوين مصادقة البريد الإلكتروني لمجالها الافتراضي تلقائيا (onmicrosoft.com)، ولكن يمكن لمسؤولي Microsoft 365 أيضا تكوين مصادقة البريد الإلكتروني للمجالات المخصصة. يتم استخدام ثلاثة أساليب مصادقة: <ul><li>إطار نهج المرسل (أو SPF).</li><ul><li>للإعداد، راجع [إعداد SPF في Microsoft 365 للمساعدة في منع الانتحال](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>راجع [استخدام DKIM للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك المخصص](use-dkim-to-validate-outbound-email.md).</li><li>بعد تكوين DKIM، قم بتمكينه في مدخل Microsoft 365 Defender.</li></ul><li>مصادقة الرسائل وإعداد التقارير والمطابقة المستندة إلى المجال (DMARC).</li><ul><li>لإعداد DMARC[، استخدم DMARC للتحقق من صحة البريد الإلكتروني في Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|

> [!NOTE]
> بالنسبة إلى عمليات النشر غير القياسية ل SPF، والنشرات المختلطة، واستكشاف الأخطاء وإصلاحها: [كيف تستخدم Microsoft 365 إطار نهج المرسل (SPF) لمنع الانتحال](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>عرض لوحات المعلومات والتقارير في مدخل Microsoft 365 Defender

تفضل بزيارة هذه التقارير ولوحات المعلومات لمعرفة المزيد حول صحة بيئتك. ستصبح البيانات الواردة في هذه التقارير أكثر ثراء حيث تستخدم مؤسستك خدمات Office 365. في الوقت الحالي، كن على دراية بما يمكنك مراقبته واتخاذ إجراء عليه.

|لوحه القياده|الوصف|
|---|---|
|تقارير أمان البريد الإلكتروني|تتوفر هذه التقارير في Exchange Online Protection. لمزيد من المعلومات، راجع [عرض تقارير أمان البريد الإلكتروني في مدخل Microsoft 365 Defender](view-email-security-reports.md).|
|تقارير Defender لـ Office 365|تتوفر التقارير فقط في Defender لـ Office 365. لمزيد من المعلومات، راجع [عرض تقارير Defender لـ Office 365 في مدخل Microsoft 365 Defender](view-reports-for-mdo.md).|
|تقارير تدفق البريد ونتائج التحليلات|تتوفر هذه التقارير والرؤى في مركز إدارة Exchange (EAC). لمزيد من المعلومات، راجع [تقارير تدفق البريد](/exchange/monitoring/mail-flow-reports/mail-flow-reports) ونتائج [تحليلات تدفق البريد](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[مستكشف التهديدات (أو عمليات الكشف في الوقت الحقيقي)](threat-explorer.md)|إذا كنت تحقق من هجوم ضد المستأجر أو تواجهه، فاستخدم المستكشف (أو عمليات الكشف في الوقت الحقيقي) لتحليل التهديدات. يعرض لك المستكشف (وتقرير عمليات الكشف في الوقت الحقيقي) حجم الهجمات بمرور الوقت، ويمكنك تحليل هذه البيانات حسب مجموعات التهديد والبنية الأساسية للمهاجمين والمزيد. يمكنك أيضا وضع علامة على أي بريد إلكتروني مريب لقائمة الحوادث.|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>تكوين إعدادات إضافية Exchange Online على مستوى المستأجر

فيما يلي بعض الإعدادات الإضافية الموصى بها.

|منطقه|توصية|
|---|---|
|**قواعد تدفق البريد** (المعروفة أيضا بقواعد النقل)|أضف قاعدة تدفق بريد للمساعدة في الحماية من برامج الفدية الضارة عن طريق حظر أنواع الملفات القابلة للتنفيذ وأنواع الملفات Office التي تحتوي على وحدات ماكرو. لمزيد من المعلومات، راجع [استخدام قواعد تدفق البريد لفحص مرفقات الرسائل في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> راجع هذه المواضيع الإضافية: <ul><li>[الحماية من برامج الفدية الضارة](../../admin/security-and-compliance/secure-your-business-data.md)</li><li>[البرامج الضارة والحماية من برامج الفدية الضارة في Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[التعافي من هجوم برامج الفدية الضارة في Office 365](recover-from-ransomware.md)</li></ul> <p> إنشاء قاعدة تدفق بريد لمنع إعادة التوجيه التلقائي للبريد الإلكتروني إلى المجالات الخارجية. لمزيد من المعلومات، راجع [تخفيف قواعد إعادة التوجيه الخارجي للعميل باستخدام درجة الأمان](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score). <p> مزيد من المعلومات: [قواعد تدفق البريد (قواعد النقل) في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**المصادقة الحديثة**|المصادقة الحديثة هي شرط أساسي لاستخدام المصادقة متعددة العوامل (MFA). يوصى باستخدام المصادقة متعددة العوامل لتأمين الوصول إلى موارد السحابة، بما في ذلك البريد الإلكتروني. <p> اطلع على هذه المواضيع: <ul><li>[تمكين المصادقة الحديثة أو تعطيلها في Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype for Business Online: تمكين المستأجر للمصادقة الحديثة](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> يتم تمكين المصادقة الحديثة بشكل افتراضي لعملاء Office 2016 SharePoint Online و OneDrive for Business. <p> مزيد من المعلومات: [كيفية عمل المصادقة الحديثة لتطبيقات عميل Office 2013 و Office 2016](../../enterprise/modern-auth-for-office-2013-and-2016.md)|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>تكوين نهج المشاركة على مستوى المستأجر في مركز إدارة SharePoint

توصيات Microsoft لتكوين مواقع فريق SharePoint بمستويات حماية متزايدة، بدءا من حماية الأساس. لمزيد من المعلومات، راجع [توصيات النهج لتأمين مواقع وملفات SharePoint](sharepoint-file-access-policies.md).

تسمح SharePoint مواقع الفرق التي تم تكوينها على مستوى الأساس بمشاركة الملفات مع مستخدمين خارجيين باستخدام ارتباطات الوصول المجهولة. يوصى بهذا الأسلوب بدلا من إرسال الملفات بالبريد الإلكتروني.

لدعم أهداف حماية الأساس، قم بتكوين نهج المشاركة على مستوى المستأجر كما هو موصى به هنا. يمكن أن تكون إعدادات المشاركة للمواقع الفردية أكثر تقييدا من هذا النهج على مستوى المستأجر، ولكنها ليست أكثر تساهلا.

|منطقه|يتضمن نهجا افتراضيا|توصية|
|---|---|---|
|**المشاركة** (SharePoint Online و OneDrive for Business)|نعم|يتم تمكين المشاركة الخارجية بشكل افتراضي. يوصى باستخدام هذه الإعدادات: <ul><li>السماح بالمشاركة للمستخدمين الخارجيين المصادق عليهم واستخدام ارتباطات الوصول المجهولة (الإعداد الافتراضي).</li><li>تنتهي صلاحية ارتباطات الوصول المجهولة في عدة أيام. أدخل رقما، إذا رغبت في ذلك، مثل 30 يوما.</li><li>نوع الارتباط الافتراضي — حدد داخلي (الأشخاص في المؤسسة فقط). يجب على المستخدمين الذين يرغبون في المشاركة باستخدام ارتباطات مجهولة اختيار هذا الخيار من قائمة المشاركة.</li></ul> <p> مزيد من المعلومات: [نظرة عامة على المشاركة الخارجية](/sharepoint/external-sharing-overview)|

يتضمن SharePoint مركز الإدارة ومركز إدارة OneDrive for Business الإعدادات نفسها. تنطبق الإعدادات في أي من مركزي الإدارة على كليهما.

## <a name="configure-settings-in-azure-active-directory"></a>تكوين الإعدادات في Azure Active Directory

تأكد من زيارة هاتين المنطقتين في Azure Active Directory لإكمال الإعداد على مستوى المستأجر لبيئات أكثر أمانا.

### <a name="configure-named-locations-under-conditional-access"></a>تكوين المواقع المسماة (ضمن الوصول المشروط)

إذا كانت مؤسستك تتضمن مكاتب ذات وصول آمن إلى الشبكة، فإضافة نطاقات عناوين IP الموثوق بها إلى Azure Active Directory كمواقع مسماة. تساعد هذه الميزة على تقليل عدد الإيجابيات الخاطئة المبلغ عنها لأحداث مخاطر تسجيل الدخول.

راجع: [المواقع المسماة في Azure Active Directory](/azure/active-directory/active-directory-named-locations)

### <a name="block-apps-that-dont-support-modern-authentication"></a>حظر التطبيقات التي لا تدعم المصادقة الحديثة

تتطلب المصادقة متعددة العوامل تطبيقات تدعم المصادقة الحديثة. لا يمكن حظر التطبيقات التي لا تدعم المصادقة الحديثة باستخدام قواعد الوصول المشروط.

بالنسبة إلى البيئات الآمنة، تأكد من تعطيل المصادقة للتطبيقات التي لا تدعم المصادقة الحديثة. يمكنك القيام بذلك في Azure Active Directory باستخدام عنصر تحكم قريبا.

في هذه الأثناء، استخدم أحد الأساليب التالية لإنجاز ذلك من أجل SharePoint Online و OneDrive for Business:

- استخدم PowerShell، راجع [تطبيقات الحظر التي لا تستخدم المصادقة الحديثة](/mem/intune/protect/app-modern-authentication-block).
- قم بتكوين هذا في <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">مركز إدارة SharePoint</a> على صفحة "الوصول إلى الجهاز" — "التحكم في الوصول من التطبيقات التي لا تستخدم المصادقة الحديثة". اختر "كتلة".

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>بدء استخدام Defender for Cloud Apps أو أمان التطبيقات على السحابة لـ Office 365

استخدم أمان التطبيقات على السحابة لـ Office 365 لتقييم المخاطر، وللتنبيه إلى النشاط المشبوه، واتخاذ إجراء تلقائيا. يتطلب خطة Office 365 E5.

أو استخدم Microsoft Defender for Cloud Apps للحصول على رؤية أعمق حتى بعد منح حق الوصول وعناصر التحكم الشاملة والحماية المحسنة لجميع تطبيقات السحابة، بما في ذلك Office 365.

نظرا لأن هذا الحل يوصي بخطة EMS E5، نوصي بالبدء ب Defender for Cloud Apps حتى تتمكن من استخدام هذا مع تطبيقات SaaS الأخرى في بيئتك. ابدأ بالنهج والإعدادات الافتراضية.

مزيد من المعلومات:

- [توزيع Defender لتطبيقات السحابة](/cloud-app-security/getting-started-with-cloud-app-security)
- [مزيد من المعلومات حول Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [ما هو Defender for Cloud Apps؟](/cloud-app-security/what-is-cloud-app-security)

:::image type="content" source="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png" alt-text="لوحة معلومات Defender for Cloud Apps" lightbox="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png":::

## <a name="additional-resources"></a>موارد إضافية

توفر هذه المقالات والدلائل معلومات توجيهية إضافية لتأمين بيئة Microsoft 365 الخاصة بك:

- [إرشادات أمان Microsoft للحملات السياسية والمؤسسات غير الربحية وغيرها من المؤسسات السريعة](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) (يمكنك استخدام هذه التوصية في أي بيئة، خاصة البيئات السحابية فقط)

- [نهج الأمان والتكوينات الموصى بها للهويات والأجهزة](microsoft-365-policies-configurations.md) (تتضمن هذه التوصيات المساعدة لبيئات AD FS)
