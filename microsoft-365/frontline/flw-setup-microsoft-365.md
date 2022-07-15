---
title: إعداد Microsoft 365 للعاملين في الخطوط الأمامية
author: samanro
ms.author: samanro
ms.reviewer: samanro
manager: pamgreen
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على كيفية إعداد Microsoft 365 مع الخدمات والميزات التي تحتاجها للعاملين في الخطوط الأمامية.
ms.localizationpriority: high
ms.collection:
- m365-frontline
- m365solution-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 25f33208cd52520d810efbb9d48643595c955f3e
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823637"
---
# <a name="set-up-microsoft-365-for-frontline-workers"></a>إعداد Microsoft 365 للعاملين في الخطوط الأمامية

لإعداد Microsoft 365 للعاملين في الخطوط الأمامية، اتبع هذه العملية الشاملة:

1. **[تحديد السيناريوهات الخاصة بك](#step-1-identify-your-scenarios)**: ما هي السيناريوهات التي تريد تنفيذها للعاملين في الخطوط الأمامية؟ بعد تحديد السيناريوهات التي تريدها، استخدم الجدول أدناه لتحديد التطبيقات والخدمات المطلوبة لكل سيناريو تريد تنفيذه.
1. **[إعداد بيئتك وMicrosoft 365 الأساسي](#step-2-set-up-your-environment-and-core-microsoft-365)**: اتبع إرشادات الإعداد في مركز مسؤولي Microsoft 365 لإعداد Microsoft 365. تابع القراءة لمعرفة كيفية الوصول إلى هذه الإرشادات.
1. **[إعداد Microsoft Teams](#step-3-set-up-microsoft-teams)**: استخدم إما معالج الإلحاق أو عملية توزيع الفرق على نطاق واسع لتكوين الخدمة وإنشاء فرقك.
1. **[قم بإعداد أي خدمات أخرى مطلوبة للسيناريو الخاص بك](#step-4-set-up-other-services)**: اتبع الإرشادات الواردة في الأقسام أدناه لإعداد هذه الخدمات.
1. **[تكوين التطبيقات](#step-5-configure-apps-for-your-scenario)**: بعد إعداد كل شيء وتكوينه في مركز الإدارة، يمكنك اتباع الإرشادات الخاصة بسيناريوهاتك لتكوين التطبيقات التي تحتاجها لكل سيناريو.
1. **[الأجهزة](#step-6-set-up-devices)**: قم بإعداد الأجهزة المشتركة والشخصية للعمل مع Microsoft 365 وMicrosoft Teams والسماح للعاملين في الخطوط الأمامية بالاتصال بشكل أكثر أمانا داخل مؤسستك.

:::image type="content" source="media/m365-frontline-setup-steps.png" alt-text="خطوات إعداد Microsoft 365 للعاملين في الخطوط الأمامية." lightbox="media/m365-frontline-setup-steps.png":::

## <a name="step-1-identify-your-scenarios"></a>الخطوة 1: تحديد سيناريوهاتك

يسرد الجدول التالي سيناريوهات العاملين في الخطوط الأمامية. يمكنك قراءة ملخص لكل سيناريو في [اختيار السيناريوهات الخاصة بك](flw-choose-scenarios.md)، ومعرفة بالضبط ما تحتاج إلى تكوينه باتباع الارتباطات لكل سيناريو ولكل تطبيق أو خدمة مطلوبة.

| السيناريو | الخدمات المطلوبة |
|  ------- | -------  |
| [التواصل والتعاون بين الفرق](flw-team-collaboration.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[البريد الإلكتروني مع Exchange Online](#set-up-email-with-exchange-online) |
| [اتصالات الشركة](flw-corp-comms.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Viva Connections](#set-up-viva-connections) <br>[Yammer](#set-up-your-organizations-social-network-with-yammer) |
| [المواعيد الظاهرية](virtual-appointments.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) |
| [إشراك الموظفين والتركيز على ترقية الموظفين](flw-wellbeing-engagement.md)| [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Viva Connections](#set-up-viva-connections) <br>[Yammer](#set-up-your-organizations-social-network-with-yammer) |
| [جدولة فريقك باستخدام الورديات](shifts-for-teams-landing-page.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) |
| [إلحاق الموظفين الجدد](/sharepoint/onboard-employees)| [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Viva Connections](#set-up-viva-connections) <br>[Viva Learning](#set-up-viva-learning)|
| [التدريب المستمر](flw-onboarding-training.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[Viva Learning](#set-up-viva-learning) |
| [تبسيط العمليات التجارية](simplify-business-processes.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[Power Apps وPower Automate وPower BI](#set-up-power-apps-power-automate-and-power-bi) |

يتم تضمين بعض الخدمات فقط مع تراخيص F3، مثل البريد الإلكتروني وPower Platform. اطلع على [فهم أنواع المستخدمين في الخطوط الأمامية والترخيص](flw-licensing-options.md) لتحديد نوع التراخيص التي ستحتاجها للمستخدمين.

## <a name="step-2-set-up-your-environment-and-core-microsoft-365"></a>الخطوة 2: إعداد البيئة والنواة Microsoft 365

يحتوي مركز مسؤولي Microsoft 365 على مجموعة من [إرشادات الإعداد](/microsoft-365/enterprise/setup-guides-for-microsoft-365) التي ترشدك عبر الخطوات اللازمة لإعداد المنتجات وميزات الأمان وأدوات التعاون في Microsoft 365. يمكن الوصول إلى إرشادات الإعداد من [صفحة إرشادات الإعداد](https://aka.ms/setupguidance) في مركز مسؤولي Microsoft 365.

1. استخدم دليل [إعداد البيئة](https://aka.ms/prepareyourenvironment) لإعداد بيئة مؤسستك لخدمات Microsoft 365 Office 365.
1. استخدم دليل [إعداد Microsoft 365](https://aka.ms/microsoft365setupguide) لإعداد أدوات الإنتاجية ونهج الأمان وقدرات إدارة الأجهزة. يمكنك أيضا استخدام هذا المستشار لإعداد أجهزة مؤسستك وتكوينها.

## <a name="step-3-set-up-microsoft-teams"></a>الخطوة 3: إعداد Microsoft Teams

بالنسبة لمشروع تجريبي، يمكنك استخدام معالج إلحاق عامل Frontline لإعداد فريق واحد، تم تكوينه للعاملين في الخطوط الأمامية. للحصول على إرشادات خطوة بخطوة، راجع [معالج إعداد Frontline Worker للحصول على القوى العاملة الأمامية وتشغيلها](flw-onboarding-wizard.md).

لعمليات النشر الكاملة، اتبع الإرشادات الواردة في [نشر الفرق على نطاق واسع للعاملين في الخطوط الأمامية](deploy-teams-at-scale.md).

## <a name="step-4-set-up-other-services"></a>الخطوة 4: إعداد خدمات أخرى

### <a name="set-up-email-with-exchange-online"></a>إعداد البريد الإلكتروني باستخدام Exchange Online

إذا كنت تريد أن يكون لمديري الخطوط الأمامية والعاملين لديك حق الوصول إلى البريد الإلكتروني، فأنت بحاجة إلى إعداد البريد الإلكتروني في Microsoft 365. يجب أن يكون لدى المستخدمين ترخيص F3 للوصول إلى البريد الإلكتروني. اتبع [دليل إعداد البريد الإلكتروني](https://aka.ms/office365setup) لإعداده.

تجدر الإشارة إلى أنه يمكن للمستخدمين أيضا تثبيت تطبيق Outlook لاستخدامه للبريد الإلكتروني الخاص بهم، لذا ستحتاج إلى التأكد من مشاركة مكان تنزيل تطبيق Outlook معهم.

### <a name="set-up-sites-with-sharepoint-in-microsoft-365"></a>إعداد المواقع باستخدام SharePoint في Microsoft 365

يتيح لك [SharePoint](/sharepoint/sharepoint-online) مشاركة المستندات وإنشاء مواقع. استخدم [دليل إعداد SharePoint](https://aka.ms/spoguidance) في مركز مسؤولي Microsoft 365 لإعداده.

### <a name="set-up-employee-experiences-with-viva-modules"></a>إعداد تجارب الموظفين باستخدام الوحدات النمطية ل Viva

تساعد [Microsoft Viva](/viva/microsoft-viva-overview) على ربط الموظفين بتجربة متكاملة للموظفين تجمع بين الاتصالات والمعرفة والتعلم والموارد والرؤى في تدفق العمل. لدى Microsoft Viva العديد من الوحدات النمطية التي يمكن استخدامها مع Microsoft Teams لإنشاء تجارب الموظفين.

#### <a name="set-up-viva-connections"></a>إعداد Viva Connections

استخدم [Viva Connections](/viva/connections/viva-connections-overview) لإنشاء لوحة معلومات تساعد على إشراك العاملين في الخطوط الأمامية وإعلامهم بذلك. Viva Connections هو تطبيق قابل للتخصيص في Microsoft Teams يمنح الجميع وجهة مخصصة لاكتشاف الأخبار والمحادثات والأدوات ذات الصلة التي يحتاجونها للنجاح. 

اتبع [دليل إعداد إعداد تجربة الموظف](https://aka.ms/EmployeeExperienceDashboard) لإعداده. تعرف على المزيد حول [إعداد Viva Connections](/viva/connections/guide-to-setting-up-viva-connections).

#### <a name="set-up-viva-learning"></a>إعداد Viva Learning

[Viva Learning](/viva/learning/) هو تطبيق في Microsoft Teams يمكن الموظفين من جعل التعلم جزءا طبيعيا من اليوم من خلال إدخال التعلم في تدفق العمل داخل الأدوات والأنظمة الأساسية التي يستخدمونها بالفعل. راجع [إعداد Microsoft Viva Learning في مركز إدارة Teams](/viva/learning/set-up-viva-learning) لمعرفة كيفية إعداد Viva Learning.

### <a name="set-up-your-organizations-social-network-with-yammer"></a>إعداد الشبكة الاجتماعية لمؤسستك باستخدام Yammer

يساعد [Yammer](/yammer) في توصيل القوى العاملة عبر شركتك. استخدم [مستشار نشر Yammer](https://aka.ms/yammerdeploymentguide) لإعداده.

### <a name="set-up-power-apps-power-automate-and-power-bi"></a>إعداد Power Apps وPower Automate وPower BI

يمكنك استخدام كل هذه التطبيقات داخل Microsoft Teams. لمزيد من المعلومات حول كيفية إعدادها، راجع:

- [تكامل Power Apps وMicrosoft Teams](/powerapps/teams/overview)
- [Power Automate - استخدام التدفقات في Microsoft Teams](/power-automate/teams/overview)
- [التعاون في Microsoft Teams باستخدام Power BI](/power-bi/collaborate-share/service-collaborate-microsoft-teams)
- [تطبيق Power Virtual Agents في Microsoft Teams](/power-virtual-agents/teams/fundamentals-what-is-power-virtual-agents-teams)
- [تطبيقات الطاقة](/microsoftteams/manage-power-platform-apps)

## <a name="step-5-configure-apps-for-your-scenario"></a>الخطوة 5: تكوين التطبيقات للسيناريو الخاص بك

بعد إعداد كل شيء وتكوينه في مركز الإدارة، يمكنك اتباع الإرشادات الخاصة بسيناريوهاتك لتكوين التطبيقات التي تحتاجها لكل سيناريو.

السيناريوهات والتطبيقات

| السيناريو | الموافقات | الحجوزات | قوائم | الثناء | التحولات | المهام | التحديثات |
| :---- | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| [التواصل والتعاون بين الفرق](flw-team-collaboration.md) | &#x2705; | &nbsp; | &#x2705; | &#x2705; | &nbsp; | &#x2705; | &#x2705; |
| [اتصالات الشركة](flw-corp-comms.md) |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |
| [المواعيد الظاهرية مع Microsoft Teams وتطبيق Bookings](bookings-virtual-visits.md) |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp;|  &nbsp; |
| تفاوض & الويب |  &nbsp; |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; |
| [جدولة فريقك باستخدام الورديات](shifts-for-teams-landing-page.md) |  &nbsp; | &nbsp; | &#x2705; |  &nbsp; | &#x2705; | &#x2705; | &#x2705; |
| [تدريب: إلحاق الموظفين الجدد](/sharepoint/onboard-employees) |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| التدريب المستمر |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| [تبسيط العمليات التجارية](simplify-business-processes.md) | &#x2705; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| إدارة المواقع والمتاجر والمشاريع | &#x2705; |  &nbsp; | &#x2705; |  &nbsp; | &nbsp; | &#x2705; | &#x2705; |

## <a name="step-6-set-up-devices"></a>الخطوة 6: إعداد الأجهزة

لإعداد الأجهزة المشتركة والشخصية للعمل مع Microsoft 365 وMicrosoft Teams والسماح للعاملين في الخطوط الأمامية بالاتصال بشكل أكثر أمانا داخل مؤسستك، راجع [إدارة الأجهزة المحمولة للعاملين في الخطوط الأمامية](flw-devices.md).
