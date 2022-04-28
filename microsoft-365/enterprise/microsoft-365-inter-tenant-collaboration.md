---
title: Microsoft 365 التعاون بين المستأجرين
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: تعرف على كيفية عمل التعاون Microsoft 365 عبر المستأجرين والمؤسسات، مما يسمح للمؤسسات المختلفة بالعمل معا بشكل آمن.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 517e015a463a501ad7b9a295a80531595c650454
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100468"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Microsoft 365 التعاون بين المستأجرين

لنفترض أن اثنتين من المؤسسات، Fabrikam وContoso، لكل منهما Microsoft 365 لمستأجر الأعمال وتريدان العمل معا على عدة مشاريع؛ بعضها يعمل لفترة محدودة وبعضها مستمر. كيف يمكن لشركة Fabrikam وContoso تمكين أفرادها وفرقها من التعاون بشكل أكثر فعالية عبر المستأجرين Microsoft 365 المختلفين بطريقة آمنة؟ يوفر Microsoft 365، بالتزامن مع تعاون Azure Active Directory (Azure AD) B2B، العديد من الخيارات. تصف هذه المقالة العديد من السيناريوهات الرئيسية التي يمكن أن تأخذها Fabrikam وContoso في الاعتبار.

تتضمن Microsoft 365 خيارات التعاون بين المستأجرين استخدام موقع مركزي للملفات والمحادثات ومشاركة التقويمات واستخدام المراسلة الفورية ومكالمات الصوت/الفيديو للاتصال وتأمين الوصول إلى الموارد والتطبيقات. استخدم الجداول التالية لتحديد الحلول ومعرفة المزيد.

## <a name="exchange-online-collaboration-options"></a>خيارات التعاون Exchange Online

| مشاركة الهدف | إجراء إداري | معلومات إرشادية |
|:-----|:-----|:-----|
|مشاركة التقويمات مع مؤسسة Microsoft 365 أخرى |يمكن للمسؤولين إعداد مستويات مختلفة من الوصول إلى التقويم في Exchange Online للسماح للشركات بالتعاون مع الشركات الأخرى والسماح للمستخدمين بمشاركة الجداول (معلومات التوفر/الانشغال) مع الآخرين. | <ul><li>[تقاسم](/exchange/sharing/sharing) </li><li> [علاقات المؤسسات](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [إنشاء علاقة مؤسسة](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [تعديل علاقة مؤسسة](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [إزالة علاقة مؤسسة](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [مشاركة التقويمات مع مستخدمين خارجيين](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|التحكم في كيفية مشاركة المستخدمين لتقويماتهم مع أشخاص من خارج مؤسستك | يطبق المسؤولون نهج المشاركة على علب بريد المستخدمين للتحكم في الأشخاص الذين يمكن مشاركتها معهم ومستوى الوصول الممنوح |  <ul><li> [نهج المشاركة](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [إنشاء نهج مشاركة](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [تطبيق نهج مشاركة على علب البريد](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [تعديل نهج مشاركة أو تعطيله أو إزالته](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|تكوين قنوات بريد إلكتروني آمنة والتحكم في تدفق البريد مع المؤسسات الشريكة | يقوم المسؤولون بإنشاء موصلات لتطبيق الأمان على عمليات تبادل البريد مع مؤسسة شريكة أو موفر خدمة. تفرض الموصلات التشفير عبر أمان طبقة النقل (TLS) بالإضافة إلى السماح بالقيود على أسماء المجالات أو نطاقات عناوين IP التي يرسل منها الشركاء بريدا إلكترونيا. |  <ul><li> [كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [تكوين تدفق البريد باستخدام الموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [المجالات البعيدة](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [إعداد موصل لتدفق بريد آمن مع مؤسسة شريكة](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [أفضل ممارسات تدفق البريد (نظرة عامة)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint خيارات التعاون عبر الإنترنت OneDrive for Business

| مشاركة الأهداف | إجراء إداري | معلومات إرشادية |
|:-----|:-----|:-----|
|مشاركة المواقع والمستندات مع مستخدمين خارجيين | يقوم المسؤولون بتكوين المشاركة على مستوى المستأجر أو مجموعة المواقع المشتركة لحساب Microsoft المصادق عليه أو حساب العمل أو المؤسسة التعليمية المصادق عليه أو حسابات الضيوف |  <ul><li> [إدارة المشاركة الخارجية لبيئة SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [تقييد مشاركة SharePoint والمحتوى OneDrive حسب المجال](/sharepoint/restricted-domains-sharing) </li><li> [استخدام SharePoint Online كحل إكسترانت للشركات (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|تعقب المشاركة الخارجية للمستخدمين النهائيين والتحكم فيها | OneDrive for Business مالكي الملفات والمستخدمين النهائيين SharePoint Online على تكوين مشاركة الموقع والمستند وإنشاء إعلامات لتعقب المشاركة |  <ul><li> [تكوين إعلامات للمشاركة الخارجية OneDrive for Business](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [مشاركة ملفات أو مجلدات SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>خيارات التعاون Skype for Business

| مشاركة الهدف | إجراء إداري | معلومات إرشادية |
|:-----|:-----|:-----|
|Skype for Business Online - المراسلة الفورية والمكالمات والحضور مع مستخدمين آخرين Skype for Business | يمكن للمسؤولين تمكين مستخدمي Skype for Business Online من المراسلة الفورية وإجراء مكالمات الصوت/الفيديو ورؤية حالة الحضور مع المستخدمين في مستأجر Microsoft 365 آخر. | [السماح للمستخدمين بالاتصال بمستخدمي Skype for Business الخارجيين](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype for Business Online - المراسلة الفورية والمكالمات والحضور مع مستخدمي Skype (المستهلكين) | يمكن للمسؤولين تمكين مستخدمي Skype for Business عبر الإنترنت من المراسلة الفورية وإجراء المكالمات ورؤية حالة الحضور مع مستخدمي Skype (المستهلكين). | [السماح للمستخدمين Skype for Business بإضافة جهات اتصال Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>خيارات تعاون B2B Azure AD

| مشاركة الهدف | إجراء إداري | معلومات إرشادية |
|:-----|:-----|:-----|
|تعاون Azure AD B2B - مشاركة المحتوى عن طريق إضافة مستخدمين خارجيين إلى مجموعة في دليل المؤسسة | يمكن **لمسؤول AZURE AD DC** أو **مسؤول الأمان** أو **مسؤول المستخدم** أو **مسؤول تطبيق السحابة** أو **المسؤول العام** لمستأجر Microsoft 365 دعوة أشخاص في مستأجر Microsoft 365 آخر للانضمام إلى دليلهم وإضافة هؤلاء المستخدمين الخارجيين إلى مجموعة ومنح حق الوصول إلى المحتوى، مثل مواقع SharePoint والمكتبات الخاصة بالمجموعة. |  <ul><li> [ما هي معاينة تعاون Azure AD B2B؟](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B: التحديثات الجديدة تسهل عملية تجميع الأعمال](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [المشاركة الخارجية والتعاون في Azure Active Directory B2B](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [واجهة برمجة تطبيقات التعاون في Azure Active Directory B2B والتخصيص](/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD و Identity Show: تعاون B2B Azure AD (Business to Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>خيارات التعاون Microsoft 365

| مشاركة الهدف | إجراء إداري | معلومات إرشادية |
|:-----|:-----|:-----|
|مجموعات Microsoft 365 - البريد الإلكتروني والتقويم OneNote والملفات المشتركة في مكان مركزي | يتم دعم المجموعات في أساسيات الأعمال Premium الأعمال والتعليم وخطط Enterprise E1 وE3 وE5. يمكن للأشخاص في مستأجر Microsoft 365 واحد إنشاء مجموعة ودعوة أشخاص في مستأجر Microsoft 365 آخر كمستخدمين ضيوف. ينطبق على Dynamics CRM أيضا. |  <ul><li> [التعرف على مجموعات Microsoft 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [وصول الضيف في مجموعات Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [نشر مجموعات Microsoft 365](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>خيارات التعاون Yammer

| مشاركة الهدف | إجراء إداري | معلومات إرشادية |
|:-----|:-----|:-----|
|Yammer - التعاون من خلال وسيلة اجتماعية للمؤسسة | ما لم يتم تعطيل القدرة على إنشاء مجموعات خارجية من قبل مسؤول Yammer، يمكن للمستخدمين إنشاء مجموعات خارجية للتعاون في Yammer من خلال المحادثات، والقدرة على تسجيل الإعجاب بالمنشورات ومتابعتها ومشاركة الملفات والدردشة عبر الإنترنت. | [إنشاء مجموعات خارجية وإدارتها في Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>خيارات التعاون Teams

|مشاركة الهدف|إجراء إداري|معلومات إرشادية|
|:-----|:-----|:-----|
|التعاون في Teams مع مستخدمين من خارج المؤسسة | يحتاج **مسؤول المستخدم** أو **المسؤول العام** لمستأجر Microsoft 365 الدعوة إلى تمكين التعاون الخارجي في Teams. سيتمكن المسؤولون العموميون ومالكو الفرق الآن من دعوة أي شخص لديه عنوان بريد إلكتروني للتعاون في Teams.  <br/> يمكن للمسؤولين أيضا إدارة الضيوف ضيوف موجودين بالفعل في المستأجر وتحريرهم. |  <ul><li> [تخويل وصول الضيف](/microsoftteams/teams-dependencies) </li><li> [تشغيل وصول الضيف أو إيقاف تشغيله في Teams](/microsoftteams/set-up-guests) </li><li> [استخدام PowerShell للتحكم في Guest Access](/microsoftteams/guest-access-powershell) </li><li> [قائمة اختيار وصول الضيف](/microsoftteams/guest-access-checklist) </li><li> [عرض المستخدمين الضيوف](/microsoftteams/view-guests) </li><li> [تحرير معلومات المستخدم الضيف](/microsoftteams/edit-guests-information) </li></ul> |
|يمكن لمالكي الفريق دعوة وإدارة كيفية تعاون الضيوف داخل فرقهم.  |يمتلك مالكو الفريق عناصر تحكم إضافية حول ما يمكن للضيوف القيام به داخل فرقهم. |  <ul><li> [إضافة ضيوف](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [إضافة ضيف إلى فريق](/microsoftteams/add-guests) </li><li> [إدارة وصول الضيف في Teams](/microsoftteams/manage-guests) </li><li> [معرفة الأشخاص الموجودين في فريق أو في قناة](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|يمكن للضيوف من المستأجرين الآخرين عرض المحتويات في Teams والتعاون مع الأعضاء الآخرين | اي. | [تجربة وصول الضيف](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>خيارات التعاون في Power BI

| مشاركة الهدف | إجراء إداري | معلومات إرشادية |
|:-----|:-----|:-----|
|يتيح Power BI للمستخدمين الضيوف الخارجيين استهلاك المحتوى المشترك معهم من خلال الارتباطات. وهذا يمكن المستخدمين في المؤسسة من توزيع المحتوى بطريقة آمنة عبر المؤسسات.<br/> | يمكن لمسؤول Power BI التحكم فيما إذا كان يمكن للمستخدمين دعوة مستخدمين خارجيين لعرض المحتوى داخل المؤسسة.| [توزيع محتوى Power BI على المستخدمين الضيوف الخارجيين باستخدام Azure AD B2B](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>النقاط التي يجب أن تكون على علم بها حول التعاون بين المستأجرين Microsoft 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>مشاركة حسابات المستخدمين والتراخيص والاشتراكات والتخزين

تحتفظ كل مؤسسة بحسابات المستخدمين والهويات ومجموعات الأمان والاشتراكات والتراخيص والتخزين الخاصة بها. يستخدم الأشخاص ميزات التعاون في Microsoft 365 مع نهج المشاركة وإعدادات الأمان لتوفير الوصول إلى المعلومات المطلوبة مع الحفاظ على التحكم في أصول الشركة.

- **حسابات المستخدمين:** لا يمكن مشاركة الحسابات أو تكرارها بين المستأجرين أو الأقسام في Active Directory محلي Domain Services.

- **اشتراكات التراخيص&amp;:** في Microsoft 365، تمنح التراخيص من خطط الترخيص (تسمى أيضا وحدات SKU أو خطط Microsoft 365) للمستخدمين إمكانية الوصول إلى خدمات Microsoft 365 المحددة لتلك الخطط.

- **تخزين:** في خطط الترخيص Microsoft 365، تتم إدارة حدود البرامج وحدودها SharePoint Online بشكل منفصل عن حدود تخزين علبة البريد. يتم إعداد حدود تخزين علبة البريد وإدارتها باستخدام Exchange Online. في كلا السيناريوهين، لا يمكن مشاركة التخزين عبر المستأجرين.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>هل يمكننا مشاركة مساحات أسماء المجالات عبر المستأجرين Microsoft 365؟

لا. يمكن اقتران أسماء مجالات المؤسسة، مثل fabrikam.com أو tailspintoys.com، واستخدامها مع مستأجر Microsoft 365 واحد فقط. يجب أن يكون لكل مستأجر مساحة الاسم الخاصة به. لا يمكن مشاركة مساحات أسماء UPN وSMTP وSIP عبر المستأجرين.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>ماذا عن المكونات المختلطة والتعاون بين المستأجرين Microsoft 365؟

لا يمكن تقسيم المكونات المختلطة المحلية، مثل مؤسسة Exchange الاتصال Azure AD، عبر مستأجرين متعددين.
