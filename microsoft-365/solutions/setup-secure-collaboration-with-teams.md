---
title: إعداد مشاركة الملفات والمستندات والتعاون بشكل آمن مع Teams في Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-securecollab
- m365solution-overview
ms.custom:
- M365solutions
- seo-marvel-jun2020
f1.keywords: NOCSH
recommendations: false
description: تعرف على أفضل الممارسات لإعداد التعاون الآمن للملفات ومشاركتها في Teams لحماية بياناتك استنادا إلى حساسيتها.
ms.openlocfilehash: aadc2bf092713ffde68cd8fb9824d837c2f14acf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935402"
---
# <a name="set-up-secure-file-sharing-and-collaboration-with-microsoft-teams"></a>إعداد مشاركة الملفات الآمنة والتعاون في العمل باستخدام Microsoft Teams

إن القدرة على مشاركة الملفات والمستندات بسهولة مع الأشخاص المناسبين مع منع المشاركة الزائدة أمر أساسي لنجاح المؤسسة. ويشمل ذلك القدرة على مشاركة البيانات السرية أو الحساسة الأخرى بأمان مع الأشخاص الذين يجب أن يكون لديهم حق الوصول إليها فقط. اعتمادا على المشروع، قد يشمل ذلك مشاركة البيانات الحساسة مع أشخاص من خارج مؤسستك.

تتضمن إرشادات حل التعاون هذه مكونين لمساعدتك:

- نشر Teams بمستوى الحماية المناسب لكل مشروع
- تكوين المشاركة الخارجية مع إعدادات الأمان المناسبة لكل مشروع

![نشر Teams مع الحماية المناسبة وتكوين المشاركة الخارجية مع إعدادات الأمان المناسبة.](..\media\solutions-architecture-center\secure-collaboration-overview.png)

إذا لم تكن أدوات التعاون في الملفات متعددة الاستخدامات وسهلة الاستخدام متوفرة، فسيتعاون المستخدمون غالبا عن طريق إرسال المستندات عبر البريد الإلكتروني. هذه طريقة مملة وعرضة للخطأ للتعاون، ويمكن أن تزيد من خطر المشاركة غير المناسبة للمعلومات. إذا وجد الأشخاص أن مشاركة الملفات صعبة جدا، فقد يعودون إلى استخدام منتجات المستهلكين التي لا تخضع لتحكم تكنولوجيا المعلومات. ويمكن أن يشكل ذلك خطرا أكبر.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxMmL?autoplay=false]

باستخدام Microsoft 365، يمكنك نشر Teams مع مجموعة متنوعة من التكوينات التي تساعد:

- حماية الملكية الفكرية
- تمكين التعاون السهل مع المستندات والملفات الأخرى
- إنشاء توازن بين الأمان وقابلية الاستخدام التي تزيد من رضا المستخدم وتقلل من مخاطر ظل تكنولوجيا المعلومات

لدى معظم المؤسسات مجموعة متنوعة من المعلومات، بدرجات متفاوتة من الحساسية ودرجات متفاوتة من تأثير الأعمال إذا كانت المعلومات مشتركة بشكل غير مناسب. اعتمادا على حساسية جزء معين من المعلومات، قد تحتاج إلى السماح بالمشاركة مع:

- أي شخص (غير مصادق عليه)
- الأشخاص داخل المؤسسة
- أشخاص محددون داخل المؤسسة
- أشخاص محددون داخل المؤسسة وخارجها

تهدف المعلومات مثل الأبحاث الموجزة التسويقية إلى المشاركة على نطاق واسع خارج المؤسسة. المعلومات مثل قوائم cafeteria ليست مخصصة للمشاركة الخارجية، ولكن لن يكون لها تأثير تجاري إذا تمت مشاركتها خارجيا. تحتاج هذه الأنواع من المعلومات إلى حماية قليلة أو معدومة.

وقد لا تتم مشاركة هذه المنشورات الموجزة التسويقية نفسها، في أثناء تطويرها، إلا داخل المؤسسة. في هذه الحالة، قد تكون إعدادات المشاركة الافتراضية في Teams كافية.

قد تعتبر المعلومات حول منتج جديد قيد التطوير حساسة، حتى داخل المؤسسة. قد تكون درجة أكبر من الحماية مناسبة في هذه الحالة. يمكنك تقييد الوصول إلى هذه المعلومات لأعضاء فريق معين، على سبيل المثال. استنادا إلى المشروع، قد تحتاج إلى التعاون مع أشخاص من خارج مؤسستك، مثل مورد أو مؤسسة شريكة.

قد تتطلب المعلومات المهمة لنجاح مؤسستك، أو التي لها متطلبات أمان أو امتثال صارمة، مستويات حماية أكبر.

![مقياس المخاطر من منخفض (منشور موجز) إلى عالي (بيانات الأعمال الحساسة).](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

بالنسبة إلى جميع السيناريوهات المذكورة أعلاه، يمكنك استخدام الفرق في Microsoft Teams لتخزين المعلومات ومشاركتها والتعاون في العمل عليها.

لتكوين تعاون آمن، يمكنك استخدام هذه الإمكانات والميزات Microsoft 365.

|المنتج أو المكون|القدرة أو الميزة|الترخيص|
|---|---|---|
|Microsoft Defender لـ Office 365|مرفقات خزينة ل SPO OneDrive Teams; مستندات خزينة; ارتباطات خزينة Teams|Microsoft 365 E1 وE3 وE5|
|SharePoint|نهج مشاركة الموقع والملفات، وأذونات مشاركة الموقع، وارتباطات المشاركة، وطلبات Access، وإعدادات مشاركة ضيف الموقع|Microsoft 365 E1 وE3 وE5|
|Microsoft Teams|وصول الضيوف، والفرق الخاصة، والقنوات الخاصة، والقنوات المشتركة|Microsoft 365 E1 وE3 وE5|
|Microsoft Purview|تسميات الحساسية|Microsoft 365 E3 وE5|

## <a name="collaboration-governance-framework-for-teams-and-microsoft-365"></a>إطار عمل حوكمة التعاون Teams Microsoft 365

يوفر Microsoft 365 العديد من الخيارات للتحكم في حل التعاون الخاص بك. نوصي باستخدام محتوى النشر هذا إلى جانب [محتوى حوكمة التعاون](collaboration-governance-overview.md) لإنشاء أفضل حل للتعاون لمؤسستك.

### <a name="securing-teams-for-sensitive-and-highly-sensitive-data"></a>تأمين Teams للبيانات الحساسة والحساسة للغاية

لإدارة الوصول إلى المعلومات ذات الحساسية المختلفة، قمنا بتطوير [ثلاثة مستويات مختلفة من الحماية Teams](configure-teams-three-tiers-protection.md). يمكنك تخصيص أي من هذه المستويات لتلبية الاحتياجات أو عملك بشكل أفضل.

![رسم لثلاثة مستويات من الحماية Teams.](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)

تزيد هذه المستويات - *الأساسية* *والحساسة* *والحساسة للغاية* - تدريجيا من الحماية التي تساعد على منع المشاركة الزائدة وتسرب المعلومات المحتمل، كما هو موضح في الجدول التالي.

|-|المستوى الأساسي|طبقة حساسة|مستوى حساس للغاية|
|---|---|---|---|
|فريق عام أو خاص|اما|الخاصه|الخاصه|
|مشاركة غير مصدق عليها|حظر|حظر|حظر|
|مشاركة الملفات|يسمح|يسمح|يمكن لمالكي الفريق فقط المشاركة.|
|عضوية الفريق|يمكن لأي شخص الانضمام إلى الفرق العامة.<br>موافقة مالك الفريق مطلوبة للانضمام إلى الفرق الخاصة.|موافقة مالك الفريق مطلوبة للانضمام.|موافقة مالك الفريق مطلوبة للانضمام.|
|تشفير المستند|||متوفر مع وصف الحساسية|
|مشاركة الضيف|يسمح|يمكن السماح به أو حظره|يمكن السماح به أو حظره|
|الأجهزة غير المدارة|بلا قيود|الوصول إلى ويب فقط|حظر|

يتضمن تكوين هذه المستويات ما يلي:

- تكوين الإعدادات في Teams للوصول إلى الضيف والقنوات الخاصة
- تكوين الإعدادات في موقع SharePoint المقترن بفريق ما لمشاركة الضيوف والداخلية وطلبات الوصول وارتباطات المشاركة
- بالنسبة للمستويات *الحساسة* *والحساسة للغاية* ، قم بتكوين تسميات الحساسية لتصنيف الفرق، والتحكم في مشاركة الضيف والوصول من الأجهزة غير المدارة
- بالنسبة إلى المستوى *الحساس للغاية* ، قم بتكوين تسمية حساسية لتشفير المستندات التي يتم تطبيقها عليها

ابدأ بمستوى الأساس، ثم أضف فرقا تستخدم المستويات *الحساسة* *والحساسة للغاية* حسب الحاجة للمساعدة في حماية المعلومات في مؤسستك. راجع هذه الموارد للبدء:

- [تكوين الفرق باستخدام الحماية الأساسية](configure-teams-baseline-protection.md)
- [تكوين الفرق مع حماية البيانات الحساسة](configure-teams-sensitive-protection.md)
- [تكوين الفرق مع حماية البيانات شديدة الحساسية](configure-teams-highly-sensitive-protection.md)

إذا كان لديك مشروع حساس للغاية يتطلب حماية إضافية من المشاركة حتى داخل مؤسستك، يمكنك تكوين فريق يستخدم وصف الحساسية الخاص به لتشفير الملفات بحيث يمكن لأعضاء الفريق فقط قراءتها. راجع [تكوين فريق مع عزل الأمان](secure-teams-security-isolation.md) للحصول على التفاصيل.

### <a name="sharing-with-people-outside-your-organization"></a>المشاركة مع أشخاص من خارج مؤسستك

قد تحتاج إلى [مشاركة معلومات عن أي حساسية مع أشخاص من خارج مؤسستك](collaborate-with-people-outside-your-organization.md). قد يتراوح هذا من مشاركة مستند واحد مع شخص واحد إلى التعاون في مشروع رئيسي مع مؤسسة شريكة كبيرة أو مساعدين من جميع أنحاء العالم. في Microsoft 365، يمكن إجراء هذا النطاق من المشاركة الخارجية بسهولة وباستخدام الضمانات المناسبة للمساعدة في حماية معلوماتك الحساسة.

ستساعدك هذه الموارد على البدء في إعداد بيئتك للتعاون مع أشخاص من خارج مؤسستك:

- [التعاون في العمل على المستندات](collaborate-on-documents.md) لمشاركة ملفات فردية من المجلدات.
- [التعاون في العمل في موقع](collaborate-in-site.md) للتعاون مع الضيوف في موقع SharePoint.
- [تعاون في العمل كفريق](collaborate-as-team.md) للتعاون مع الضيوف في فريق.
- [التعاون مع المشاركين الخارجيين في قناة](/microsoft-365/solutions/collaborate-teams-direct-connect) للتعاون مع أشخاص من خارج المؤسسة في قناة مشتركة.

اعتمادا على حساسية المعلومات التي تتم مشاركتها، يمكنك إضافة ضمانات للمساعدة في منع المشاركة الزائدة. ستساعدك هذه الموارد على إعداد الحماية التي تحتاجها لمؤسستك:

- [أفضل الممارسات لمشاركة الملفات والمجلدات مع مستخدمين غير مصادقين](best-practices-anonymous-sharing.md)
- [الحد من التعرض العرضي للملفات عند المشاركة مع أشخاص من خارج مؤسستك](share-limit-accidental-exposure.md)
- [إنشاء بيئة مشاركة ضيف آمنة](create-secure-guest-sharing-environment.md)

إذا كان لديك مشروع رئيسي مع مؤسسة شريكة، يمكنك استخدام [القنوات المشتركة](/microsoft-365/solutions/collaborate-teams-direct-connect) أو [Azure Entitlement Management](b2b-extranet.md) لإدارة الأشخاص من خارج مؤسستك الذين تحتاج إلى التعاون معهم.

## <a name="training-for-administrators"></a>تدريب للمسؤولين

يمكن أن تساعدك وحدات التدريب هذه من Microsoft Learn على تعلم ميزات التعاون والحوكمة والهوية في Teams SharePoint.

### <a name="teams"></a>الفرق

|التدريب:|إدارة تعاون الفريق باستخدام Microsoft Teams|
|---|---|
|![Teams أيقونة التدريب على التعاون.](../media/manage-team-collaboration-with-microsoft-teams.svg)|إدارة تعاون الفريق مع Microsoft Teams تعرفك على ميزات وإمكانيات Microsoft Teams، المركز المركزي لتعاون الفريق في Microsoft 365. ستتعلم كيف يمكنك استخدام Teams لتسهيل العمل الجماعي والتواصل داخل مؤسستك، سواء في أماكن العمل أو خارجها، على مجموعة واسعة من الأجهزة - من أجهزة سطح المكتب إلى أجهزة الكمبيوتر اللوحية إلى الهواتف - مع الاستفادة من جميع الوظائف الغنية لتطبيقات Office 365. ستفهم كيف يوفر Teams بيئة شاملة ومرنة للتعاون عبر التطبيقات والأجهزة. يمكن أن يساعدك مسار التعلم هذا على الاستعداد Microsoft 365 المعتمد: شهادة شريك مسؤول Teams.<p>2 ساعة و17 دقيقة - مسار Learning - 5 وحدات نمطية|

> [!div class="nextstepaction"]
> [بدء >](/learn/modules/m365-teams-collab-prepare-deployment/introduction/)

### <a name="sharepoint"></a>SharePoint

|التدريب:|التعاون في العمل مع SharePoint في Microsoft 365|
|---|---|
|![SharePoint أيقونة التدريب.](../media/collaborate-with-sharepoint-in-microsoft-365.svg)|تعرفك إدارة المحتوى المشترك مع Microsoft SharePoint على ميزات وإمكانيات SharePoint وكيفية عملها مع Microsoft 365. ستتعرف على الأنواع المختلفة لمواقع SharePoint، بما في ذلك مواقع المركز، بالإضافة إلى حماية المعلومات وإعداد التقارير والمراقبة. ستتعلم أيضا كيفية استخدام مشاركة الملفات والمجلدات SharePoint لتحسين التعاون، وكيفية مشاركة الملفات خارجيا، وكيفية إدارة مواقع SharePoint في مركز إدارة SharePoint. يمكن أن يساعدك مسار التعلم هذا على الاستعداد للحصول على شهادة "Microsoft 365 Certified: Teamwork Administrator Associate".<p>1 ساعة و14 دقيقة - مسار Learning - 4 وحدات نمطية|

> [!div class="nextstepaction"]
> [بدء >](/learn/modules/m365-teams-sharepoint-plan-sharepoint/introduction/)

### <a name="information-protection"></a>حماية المعلومات

|التدريب:|حماية معلومات المؤسسة باستخدام Microsoft 365|
|---|---|
|![Teams أيقونة التدريب على حماية المعلومات.](../media/protect-enterprise-information-microsoft-365.svg)|تعد حماية معلومات مؤسستك وتأمينها أكثر تحديا من أي وقت مضى. يناقش مسار التعلم "حماية معلومات المؤسسة Microsoft 365" كيفية حماية معلوماتك الحساسة من المشاركة العرضية أو إساءة الاستخدام، وكيفية اكتشاف البيانات وتصنيفها، وكيفية حمايتها باستخدام أوصاف الحساسية، وكيفية مراقبة المعلومات الحساسة وتحليلها للحماية من فقدانها. يمكن أن يساعدك مسار التعلم هذا على الاستعداد Microsoft 365 المعتمد: مساعد مسؤول الأمان وشهادات Microsoft 365 المعتمدة: شهادات خبراء إدارة المؤسسة.<p>1 ساعة - مسار Learning - 5 وحدات نمطية|

> [!div class="nextstepaction"]
> [بدء >](/learn/modules/m365-security-info-overview/introduction/)

### <a name="identity-and-access"></a>الهوية والوصول

|التدريب:|حماية الهوية والوصول باستخدام Azure Active Directory|
|---|---|
|![أيقونة التدريب على الهوية والوصول.](../media/protect-identity-and-access-with-microsoft-365.svg)|يغطي مسار تعلم الهوية والوصول أحدث تقنيات الهوية والوصول وأدوات تعزيز المصادقة والتوجيه حول حماية الهوية داخل مؤسستك. تمكنك تقنيات الوصول والهوية من Microsoft من تأمين هوية مؤسستك، سواء كانت داخلية أو في السحابة، وتمكين المستخدمين من العمل بأمان من أي موقع. يمكن أن يساعدك مسار التعلم هذا على الاستعداد Microsoft 365 المعتمد: مساعد مسؤول الأمان وشهادات Microsoft 365 المعتمدة: شهادات خبراء إدارة المؤسسة.<p>2 ساعة و52 دقيقة - مسار Learning - 6 وحدات نمطية|

> [!div class="nextstepaction"]
> [بدء >](/learn/modules/m365-identity-overview/introduction/)

## <a name="training-for-end-users"></a>تدريب للمستخدمين النهائيين

يمكن أن تساعد وحدات التدريب هذه المستخدمين على استخدام Teams والمجموعات SharePoint للتعاون في Microsoft 365.

|الفرق|SharePoint|
|---|---|
|![إعداد أيقونة تدريب فريقك وتخصيصها.](../media/set-up-customize-team-training.png)<br>**[إعداد فريقك وتخصيصه](https://support.microsoft.com/office/702a2977-e662-4038-bef5-bdf8ee47b17b)**|![SharePoint مشاركة أيقونة التدريب ومزامنتها](../media/sharepoint-share-sync-training.png)<br>**[المشاركة والمزامنة](https://support.microsoft.com/office/98cb2ff2-c27e-42ea-b055-c2d895f8a5de)**|
|![Teams تحميل أيقونة تدريب الملفات والعثور عليها.](../media/smc-teams-upload-find-files-training.png)<br>**[Upload والعثور على الملفات](https://support.microsoft.com/office/57b669db-678e-424e-b0a0-15d19215cb12)**||
|![التعاون في العمل في أيقونة الفرق والقنوات.](../media/teams-collaborate-channels-training.png)<br>**[التعاون في الفرق والقنوات](https://support.microsoft.com/office/c3d63c10-77d5-4204-a566-53ddcf723b46)**||

## <a name="illustrations"></a>الرسوم التوضيحيه

ستساعدك هذه الرسوم التوضيحية على فهم كيفية تفاعل المجموعات والفرق مع الخدمات الأخرى في Microsoft 365 وميزات الحوكمة والتوافق المتوفرة لمساعدتك على إدارة هذه الخدمات في مؤسستك.

### <a name="groups-in-microsoft-365-for-it-architects"></a>المجموعات في Microsoft 365 لمهندسي تكنولوجيا المعلومات

ما يحتاج مهندسو تكنولوجيا المعلومات إلى معرفته حول المجموعات في Microsoft 365

|**البند**|**الوصف**|
|---|---|
|[![صورة مصغرة للملف البياني للمعلومات للمجموعات.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> تم التحديث في يونيو 2019|توضح هذه الرسوم التوضيحية بالتفصيل الأنواع المختلفة من المجموعات، وكيفية إنشاء هذه المجموعات وإدارتها، وبعض توصيات الحوكمة.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams وخدمات الإنتاجية ذات الصلة في Microsoft 365 لمهندسي تكنولوجيا المعلومات

البنية المنطقية لخدمات الإنتاجية في Microsoft 365، الرائدة مع Microsoft Teams.

|**البند**|**الوصف**|
|---|---|
|[![صورة إبهام لملصق البنية المنطقية Teams.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>تم التحديث في أبريل 2019|توفر Microsoft مجموعة من خدمات الإنتاجية التي تعمل معا لتوفير تجارب التعاون مع قدرات حوكمة البيانات والأمان والتوافق. <p>توفر هذه السلسلة من الرسوم التوضيحية عرضا للبنية المنطقية لخدمات الإنتاجية لمهندسي المؤسسات، ما يؤدي إلى Microsoft Teams.|

## <a name="deploy-the-secure-collaboration-solution"></a>نشر حل التعاون الآمن

عندما تكون مستعدا لنشر هذا الحل، تابع الخطوات التالية:

1. تكوين [ثلاثة مستويات مختلفة من الحماية Teams](configure-teams-three-tiers-protection.md).
2. تكوين إعدادات [لمشاركة معلومات عن أي حساسية مع أشخاص من خارج مؤسستك](collaborate-with-people-outside-your-organization.md).

## <a name="see-also"></a>راجع أيضًا

[وثائق الأمان Microsoft 365](../security/index.yml)

[وثائق Microsoft Purview](../compliance/index.yml)

[مرحبا بك في Microsoft Teams](/MicrosoftTeams/Teams-overview)
