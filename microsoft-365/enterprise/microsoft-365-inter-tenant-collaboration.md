---
title: Microsoft 365 التعاون بين المستأجرين
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على Microsoft 365 التعاون بين المستأجرين والمستأجرين، مما يسمح لمختلف المؤسسات بالعمل معا بأمان.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9cb91b6bcaac212eeaf0ef4051f466751d8dbbd9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568775"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Microsoft 365 التعاون بين المستأجرين

لنفترض أن هناك اثنتين من الشركتين، Fabrikam و Contoso، كل منهما لديها مستأجر Microsoft 365 للأعمال وتريدان العمل معا على عدة مشاريع، بعضها يعمل لفترة محدودة والبعض الآخر مستمر. كيف يمكن ل Fabrikam و Contoso تمكين الأشخاص والفرق الخاصة بهم من التعاون بفعالية أكبر عبر المستأجرين Microsoft 365 بطريقة آمنة؟ Microsoft 365، بالإضافة إلى التعاون في Azure Active Directory (Azure AD) B2B، خيارات متعددة. تصف هذه المقالة العديد من السيناريوهات الأساسية التي يمكن أن تفكر فيها شركة Fabrikam و Contoso.

Microsoft 365 خيارات التعاون بين المستأجرين استخدام موقع مركزي للملفات والمحادثات ومشاركة التقويمات واستخدام المراسلة الفورية ومكالمات الصوت/الفيديو للاتصال وتأمين الوصول إلى الموارد والتطبيقات. استخدم الجداول التالية لتحديد الحلول ومعرفة المزيد.

## <a name="exchange-online-collaboration-options"></a>Exchange Online التعاون

| هدف المشاركة | إجراء إداري | معلومات حول كيفية استخدام |
|:-----|:-----|:-----|
|مشاركة التقويمات مع مؤسسة Microsoft 365 أخرى |يمكن للمسؤولين إعداد مستويات مختلفة من الوصول إلى التقويم في Exchange Online للسماح للشركات بالتعاون مع الشركات الأخرى والسماح للمستخدمين بمشاركة الجداول الزمنية (معلومات الشغل/الشغل) مع الآخرين. | <ul><li>[المشاركة](/exchange/sharing/sharing) </li><li> [علاقات المؤسسات](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [إنشاء علاقة مؤسسة](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [تعديل علاقة مؤسسة](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [إزالة علاقة مؤسسة](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [مشاركة التقويمات مع مستخدمين خارجيين](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|التحكم في كيفية مشاركة المستخدمين تقويماتهم مع أشخاص من خارج مؤسستك | يقوم المسؤولون بتطبيق سياسات المشاركة على علب بريد المستخدمين للتحكم في الأشخاص الذين يمكن مشاركتها معهم ومستوى الوصول الممنوح لهم |  <ul><li> [سياسات المشاركة](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [إنشاء نهج مشاركة](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [تطبيق نهج مشاركة على علب البريد](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [تعديل نهج مشاركة أو تعطيله أو إزالته](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|تكوين قنوات البريد الإلكتروني الآمنة والتحكم في تدفق البريد مع المؤسسات الشريكة | ينشئ المسؤولون موصلات لتطبيق الأمان على تبادلات البريد مع مؤسسة شريكة أو موفر خدمة. تفرض الموصلات التشفير عبر أمان طبقة النقل (TLS) بالإضافة إلى السماح بالقيود على أسماء المجالات أو نطاقات عناوين IP التي يرسل منها الشركاء بريدا إلكترونيا. |  <ul><li> [كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [تكوين تدفق البريد باستخدام الموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [المجالات البعيدة](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [إعداد الموصل لتدفق البريد الآمن مع مؤسسة شريكة](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [أفضل ممارسات تدفق البريد (نظرة عامة)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint عبر الإنترنت OneDrive for Business التعاون

| أهداف المشاركة | إجراء إداري | معلومات حول كيفية استخدام |
|:-----|:-----|:-----|
|مشاركة المواقع والمستندات مع مستخدمين خارجيين | يقوم المسؤولون بتكوين المشاركة على مستوى المستأجر أو مجموعة المواقع الخاصة لحساب Microsoft المصادقة أو حساب العمل أو المؤسسة الدراسية أو حسابات الضيوف |  <ul><li> [إدارة المشاركة الخارجية لبيئة SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [تقييد مشاركة SharePoint OneDrive حسب المجال](/sharepoint/restricted-domains-sharing) </li><li> [استخدام SharePoint Online كحل إكسترانت للأعمال (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|تعقب المشاركة الخارجية للمستخدمين والتحكم بها | OneDrive for Business مالكي الملفات SharePoint المستخدمين النهائيين عبر الإنترنت تكوين مشاركة الموقع والمستندات وإنشاء إعلامات لتعقب المشاركة |  <ul><li> [تكوين الإعلامات للمشاركة الخارجية OneDrive for Business](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [مشاركة SharePoint أو مجلدات](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>Skype for Business خيارات التعاون

| هدف المشاركة | إجراء إداري | معلومات حول كيفية استخدام |
|:-----|:-----|:-----|
|Skype for Business عبر الإنترنت - المراسلة الفورية والمكالمات والحضور مع المستخدمين Skype for Business الآخرين | يمكن للمسؤولين تمكين المستخدمين Skype for Business عبر الإنترنت من المراسلة الفورية، وأجروا مكالمات صوت/فيديو، وشاهدوا حالة الحضور مع المستخدمين في Microsoft 365 مستأجر آخر. | [السماح للمستخدمين بالاتصال بمستخدمين Skype for Business خارجيين](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype for Business عبر الإنترنت - المراسلة الفورية والمكالمات والحضور مع Skype (المستهلكين) | يمكن للمسؤولين تمكين المستخدمين Skype for Business عبر الإنترنت من المراسلة الفورية، إجراء المكالمات، ورؤية الحضور مع Skype المستخدمين (المستهلكين). | [السماح Skype for Business المستخدمين بإضافة Skype اتصال](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>خيارات التعاون في Azure AD B2B

| هدف المشاركة | إجراء إداري | معلومات حول كيفية استخدام |
|:-----|:-----|:-----|
|التعاون في Azure AD B2B - مشاركة المحتوى عن طريق إضافة مستخدمين خارجيين إلى مجموعة في دليل المؤسسة | بإمكان **مسؤول Azure AD DC** أو مسؤول الأمان أو مسؤول المستخدم أو مسؤول تطبيق السحابة أو  المسؤول العام لمستأجر Microsoft 365 واحد دعوة الأشخاص في مستأجر Microsoft 365 آخر للانضمام إلى الدليل وإضافة هؤلاء المستخدمين الخارجيين إلى مجموعة ومنح حق الوصول إلى المحتوى، مثل مواقع SharePoint ومكتبات المجموعة.  |  <ul><li> [ما هي معاينة التعاون في Azure AD B2B؟](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B: تجعل التحديثات الجديدة من السهل إنشاء مجمع عبر الأعمال](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [المشاركة الخارجية والتعاون في Azure Active Directory B2B](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [API للتخصيص والتعاون في Azure Active Directory B2B](/azure/active-directory/active-directory-b2b-api) </li><li> [عرض Azure AD والهوية: التعاون في Azure AD B2B (Business to Business)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>Microsoft 365 التعاون

| هدف المشاركة | إجراء إداري | معلومات حول كيفية استخدام |
|:-----|:-----|:-----|
|Microsoft 365 المجموعات - البريد الإلكتروني والتقويم OneNote الملفات والملفات المشتركة في مكان مركزي | يتم دعم المجموعات في خطط Business Essentials و Business Premium والتعليم و Enterprise E1 و E3 و E5. يمكن للأشخاص في Microsoft 365 المستأجر إنشاء مجموعة ودعوة الأشخاص في Microsoft 365 المستأجر كمستخدمين ضيوف. ينطبق على Dynamics CRM أيضا. |  <ul><li> [التعرف على Microsoft 365 المجموعات](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [وصول الضيف في Microsoft 365 المجموعات](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [نشر Microsoft 365 المجموعات](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>Yammer التعاون

| هدف المشاركة | إجراء إداري | معلومات حول كيفية استخدام |
|:-----|:-----|:-----|
|Yammer - التعاون من خلال وسط اجتماعي للمؤسسة | ما لم يتم تعطيل القدرة على إنشاء مجموعات خارجية من قبل مسؤول Yammer، يمكن للمستخدمين إنشاء مجموعات خارجية للتعاون في Yammer من خلال المحادثات، والقدرة على متابعة المنشورات ومشاركة الملفات والدردشة عبر الإنترنت. | [إنشاء مجموعات خارجية وإدارتها في Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>Teams التعاون

|هدف المشاركة|إجراء إداري|معلومات حول كيفية استخدام|
|:-----|:-----|:-----|
|التعاون في Teams مع مستخدمين من خارج المؤسسة | يحتاج **مسؤول المستخدم** أو المسؤول  العام Microsoft 365 المستأجر إلى تمكين التعاون الخارجي في Teams. سيتمكن المسؤولون العامون ومالاك الفريق الآن من دعوة أي شخص باستخدام عنوان بريد إلكتروني للتعاون في Teams.  <br/> يمكن للمسؤولين أيضا إدارة الضيوف حاضرين بالفعل في المستأجر وتحريرهم. |  <ul><li> [تخويل وصول الضيف](/microsoftteams/teams-dependencies) </li><li> [تشغيل وصول الضيف أو إيقاف تشغيله في Teams](/microsoftteams/set-up-guests) </li><li> [استخدام PowerShell للتحكم في وصول الضيف](/microsoftteams/guest-access-powershell) </li><li> [قائمة اختيار وصول الضيف](/microsoftteams/guest-access-checklist) </li><li> [عرض المستخدمين الضيوف](/microsoftteams/view-guests) </li><li> [تحرير معلومات المستخدم الضيف](/microsoftteams/edit-guests-information) </li></ul> |
|يمكن لمالكي الفريق دعوة وإدارة كيفية تعاون الضيوف داخل فرقهم.  |يتوفر لمالكي الفريق عناصر تحكم إضافية حول ما يمكن للضيوف القيام به داخل فرقهم. |  <ul><li> [إضافة ضيوف](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [إضافة ضيف إلى فريق](/microsoftteams/add-guests) </li><li> [إدارة وصول الضيف في Teams](/microsoftteams/manage-guests) </li><li> [معرفة من هو أعضاء الفريق أو في قناة](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|يمكن للضيوف من المستأجرين الآخرين عرض المحتويات في Teams والتعاون مع الأعضاء الآخرين | بلا. | [تجربة وصول الضيف](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>خيارات التعاون في Power BI

| هدف المشاركة | إجراء إداري | معلومات حول كيفية استخدام |
|:-----|:-----|:-----|
|يمكن Power BI المستخدمين الضيوف الخارجيين من استخدام المحتوى الذي تمت مشاركته لهم من خلال الارتباطات. يمكن ذلك المستخدمين في المؤسسة من توزيع المحتوى بطريقة آمنة عبر المؤسسات.<br/> | يمكن لمسؤول Power BI التحكم في ما إذا كان يمكن للمستخدمين الخارجيين دعوة مستخدمين خارجيين لعرض المحتوى داخل المؤسسة.| [توزيع محتوى Power BI للمستخدمين الضيوف الخارجيين باستخدام Azure AD B2B](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>النقاط التي يجب الانتباه Microsoft 365 التعاون بين المستأجرين

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>مشاركة حسابات المستخدمين والتراخيص والاشتراكات والتخزين

تحافظ كل مؤسسة على حسابات المستخدمين وهوياتها ومجموعات الأمان والاشتراكات والتراخيص والتخزين الخاصة بها. يستخدم الأشخاص ميزات التعاون في Microsoft 365 مع سياسات المشاركة وإعدادات الأمان لتوفير الوصول إلى المعلومات المطلوبة مع الحفاظ على التحكم في أصول الشركة.

- **حسابات المستخدمين:** لا يمكن مشاركة الحسابات أو تكرارها بين المستأجرين أو الأقسام في خدمات مجال Active Directory المحلية.

- **&amp;** تراخيص الاشتراكات: في Microsoft 365، تمنح التراخيص من خطط الترخيص (تسمى أيضا خطط Microsoft 365) المستخدمين حق الوصول إلى خدمات Microsoft 365 المعرفة لهذه الخطط.

- **مساحة التخزين:** في Microsoft 365 الترخيص، تدار حدود البرنامج وحدوده SharePoint Online بشكل منفصل عن حدود تخزين علب البريد. يتم إعداد حدود تخزين علب البريد وإدارتها باستخدام Exchange Online. في كلا السيناريوهين، لا يمكن مشاركة مساحة التخزين عبر المستأجرين.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>هل يمكننا مشاركة مساحات أسماء المجالات عبر Microsoft 365 المستأجرين؟

لا. يمكن إقترن أسماء مجالات المؤسسة، fabrikam.com أو tailspintoys.com، بمستأجر واحد فقط Microsoft 365 نطاق واحد. يجب أن يكون لكل مستأجر مساحة اسم خاصة به. لا يمكن مشاركة مساحات أسماء UPN وSTP وSIP عبر المستأجرين.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>ماذا عن المكونات المختلطة Microsoft 365 التعاون بين المستأجرين؟

لا يمكن تقسيم المكونات المختلطة Exchange، مثل Exchange و Azure AD الاتصال عبر مستأجرين متعددين.
