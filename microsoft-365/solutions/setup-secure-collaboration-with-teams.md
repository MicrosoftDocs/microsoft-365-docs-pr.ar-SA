---
title: إعداد مشاركة الملفات والمستندات الآمنة والتعاون مع Teams في Microsoft 365
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
description: تعرف على أفضل الممارسات لإعداد التعاون الآمن في الملفات ومشاركتها في Teams لحماية البيانات استنادا إلى حساسيتها.
ms.openlocfilehash: db1ad7d6d5c62775c696da89c3d771114d48e67e
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/22/2022
ms.locfileid: "63714942"
---
# <a name="set-up-secure-file-sharing-and-collaboration-with-microsoft-teams"></a>إعداد مشاركة الملفات الآمنة والتعاون باستخدام Microsoft Teams

إن القدرة على مشاركة الملفات والمستندات بسهولة مع الأشخاص المناسبين مع منع المشاركة بشكل أكبر هي مفتاح نجاح المؤسسة. يشمل ذلك القدرة على مشاركة البيانات السرية أو الحساسة الأخرى بأمان مع الأشخاص الذين يجب أن يكون لديهم حق الوصول إليها فقط. استنادا إلى المشروع، قد يتضمن ذلك مشاركة البيانات الحساسة مع أشخاص من خارج مؤسستك.

تتضمن إرشادات حل التعاون هذه مكونين لمساعدتك:

- نشر Teams مع مستوى الحماية المناسب لكل مشروع
- تكوين المشاركة الخارجية باستخدام إعدادات الأمان المناسبة لكل مشروع

![نشر Teams مع الحماية المناسبة وتكوين المشاركة الخارجية باستخدام إعدادات الأمان المناسبة.](..\media\solutions-architecture-center\secure-collaboration-overview.png)

إذا لم تتوفر أدوات التعاون في الملفات متعددة الاستخدام وسهلة الاستخدام، فإن المستخدمين سيتعاونون غالبا عبر إرسال مستندات بالبريد الإلكتروني. هذه طريقة تعاون مملة ومعرضة للأخطاء، ويمكن أن تزيد من خطر المشاركة غير المناسبة للمعلومات. إذا كان الأشخاص يجدون أن مشاركة الملفات صعبة للغاية، فقد يعودون إلى استخدام منتجات المستهلكين التي لا تخضع لحكم IT. وقد يشكل ذلك خطرا أكبر.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxMmL?autoplay=false]

باستخدام Microsoft 365، يمكنك نشر Teams باستخدام مجموعة متنوعة من التكوينات التي تساعد:

- حماية الملكية الفكرية
- تمكين التعاون السهل مع المستندات والملفات الأخرى
- إنشاء توازن بين الأمان وإمكانية الاستخدام التي تزيد من مستوى رضا المستخدم وتقلل من مخاطر ظل معلومات المعلومات

تملك معظم المؤسسات مجموعة متنوعة من المعلومات، مع درجات مختلفة من الحساسية ودرجات مختلفة من تأثير الأعمال إذا تمت مشاركة المعلومات بشكل غير مناسب. استنادا إلى حساسية جزء معين من المعلومات، قد ترغب في السماح بالمشاركة باستخدام:

- أي شخص (غير مفوه)
- الأشخاص داخل المؤسسة
- أشخاص معينون داخل المؤسسة
- أشخاص معينون داخل المؤسسة وخارجها

تهدف المعلومات مثل منشورات التسويق الموجزة إلى المشاركة على نطاق واسع خارج المؤسسة. لا تهدف المعلومات مثل قوائم الكافيتريا إلى المشاركة الخارجية، ولكن لن يكون لها أي تأثير أعمال إذا تمت مشاركتها خارجيا. تحتاج هذه الأنواع من المعلومات إلى القليل من الحماية أو لا تحتاج إلى حماية.

قد يتم مشاركة هذه المنشورات الموجزة التسويقية نفسها، أثناء تطويرها، داخل المؤسسة فقط. في هذه الحالة، قد تكون إعدادات المشاركة الافتراضية في Teams كافية.

قد تعتبر المعلومات حول منتج جديد قيد التطوير حساسة، حتى داخل المؤسسة. قد تكون درجة أكبر من الحماية مناسبة في هذه الحالة. يمكنك تقييد الوصول إلى هذه المعلومات لأعضاء فريق معين، على سبيل المثال. استنادا إلى المشروع، قد تحتاج إلى التعاون مع أشخاص من خارج مؤسستك، مثل مورد أو مؤسسة شريكة.

قد تتطلب المعلومات الهامة لنجاح مؤسستك، أو التي لديها متطلبات أمان أو توافق صارمة مستويات حماية أكبر.

![مقياس المخاطر من منخفض (منشور دعائي تم إصداره) إلى عال (بيانات الأعمال الحساسة).](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

بالنسبة لجميع السيناريوهات المذكورة أعلاه، يمكنك استخدام الفرق Microsoft Teams لتخزين المعلومات ومشاركتها والتعاون في العمل عليها.

لتكوين التعاون الآمن، يمكنك استخدام هذه Microsoft 365 والميزات.

|المنتج أو المكون|الإمكانية أو الميزة|الترخيص|
|---|---|---|
|Microsoft Defender Office 365|خزينة مرفقات SPO OneDrive و Teams؛ خزينة المستندات؛ خزينة ارتباطات Teams|Microsoft 365 E1 و E3 و E5|
|SharePoint|سياسات مشاركة الموقع والملفات، أذونات مشاركة الموقع، ارتباطات المشاركة، طلبات Access، إعدادات مشاركة ضيف الموقع|Microsoft 365 E1 و E3 و E5|
|Microsoft Teams|وصول الضيف والفرق الخاصة والقنوات الخاصة والقنوات المشتركة|Microsoft 365 E1 و E3 و E5|
|Microsoft 365 التوافق|تسميات الحساسية|Microsoft 365 E3 و E5|

## <a name="collaboration-governance-framework-for-teams-and-microsoft-365"></a>إطار عمل حوكمة التعاون Teams Microsoft 365

Microsoft 365 العديد من الخيارات التي تحكم حل التعاون. نوصي باستخدام محتوى النشر هذا جنبا إلى جنب مع محتوى [حوكمة](collaboration-governance-overview.md) التعاون لإنشاء أفضل حل للتعاون في مؤسستك.

### <a name="securing-teams-for-sensitive-and-highly-sensitive-data"></a>تأمين Teams البيانات الحساسة والحساسة بدرجة عالية

لإدارة الوصول إلى المعلومات بحساسيات مختلفة، قمنا بتطوير ثلاثة مستويات مختلفة من الحماية [Teams](configure-teams-three-tiers-protection.md). يمكنك تخصيص أي من هذه المستويات لتلبية الاحتياجات أو أعمالك بشكل أفضل.

![رسم لثلاثة مستويات من الحماية Teams.](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)

تزيد *هذه المستويات* تدريجيا من الحماية التي تساعد  على منع تسريب المعلومات وتسريبها بشكل كبير، كما هو موضح في الجدول التالي.

|-|مستوى الأساس|الطبقة الحساسة|الطبقة الحساسة بدرجة عالية|
|---|---|---|---|
|فريق عام أو خاص|إما|خاص|خاص|
|المشاركة غير المأكة|تم الحظر|تم الحظر|تم الحظر|
|مشاركة الملفات|مسموح به|مسموح به|يمكن لمالكي الفريق فقط المشاركة.|
|عضوية الفريق|يمكن لأي شخص الانضمام إلى الفرق العامة.<br>موافقة مالك الفريق مطلوبة للانضمام إلى الفرق الخاصة.|موافقة مالك الفريق مطلوبة للانضمام.|موافقة مالك الفريق مطلوبة للانضمام.|
|تشفير المستند|||متوفر مع تسمية الحساسية|
|مشاركة الضيف|مسموح به|يمكن السماح به أو حظره|يمكن السماح به أو حظره|
|الأجهزة غير التي يتم تدراجها|بلا قيود|الوصول إلى الويب فقط|تم الحظر|

يتضمن تكوين هذه المستويات ما يلي:

- تكوين الإعدادات في Teams وصول الضيوف والقنوات الخاصة
- تكوين الإعدادات في موقع ويب SharePoint الخاص بفريق للمشاركة الداخلية والضيفة وطلبات الوصول وروابط المشاركة
- بالنسبة *للمستويات الحساسة* والحساسة إلى حد كبير، تكوين تسميات الحساسية لتصنيف الفرق والتحكم في مشاركة الضيف والوصول إليه من الأجهزة غير المراقبة 
- بالنسبة *للطبقة عالية الحساسية* ، تكوين تسمية حساسية لتشفير المستندات التي تم تطبيقها عليها

ابدأ بمستويات الأساس، ثم أضف الفرق التي تستخدم الطبقات الحساسة والحساسة بدرجة عالية كما هو مطلوب للمساعدة في حماية المعلومات في مؤسستك.  راجع هذه الموارد للبدء:

- [تكوين الفرق باستخدام حماية الأساس](configure-teams-baseline-protection.md)
- [تكوين الفرق مع حماية البيانات الحساسة](configure-teams-sensitive-protection.md)
- [تكوين الفرق مع حماية البيانات عالية الحساسية](configure-teams-highly-sensitive-protection.md)

إذا كان لديك مشروع شديد الحساسية يتطلب حماية إضافية من المشاركة حتى داخل مؤسستك، يمكنك تكوين فريق يستخدم تسمية الحساسية الخاصة به لتشفير الملفات بحيث يمكن لأعضاء الفريق فقط قراءتها. راجع [تكوين فريق مع عزل الأمان](secure-teams-security-isolation.md) للحصول على التفاصيل.

### <a name="sharing-with-people-outside-your-organization"></a>المشاركة مع أشخاص من خارج مؤسستك

قد تحتاج إلى [مشاركة معلومات عن أي حساسية مع أشخاص من خارج مؤسستك](collaborate-with-people-outside-your-organization.md). قد يتراوح ذلك من مشاركة مستند واحد مع شخص واحد إلى التعاون في مشروع رئيسي مع مؤسسة شريكة كبيرة أو مستقلين من جميع أنحاء العالم. في Microsoft 365، يمكن القيام بهذا النطاق من المشاركة الخارجية بسهولة وبضمانات مناسبة للمساعدة في حماية معلوماتك الحساسة.

ستساعدك هذه الموارد على بدء إعداد بيئتك للتعاون مع أشخاص من خارج مؤسستك:

- [التعاون في العمل على المستندات](collaborate-on-documents.md) لمشاركة الملفات الفردية للمجلدات.
- [التعاون في موقع للتعاون](collaborate-in-site.md) مع الضيوف في SharePoint ويب.
- [التعاون في العمل كفريق](collaborate-as-team.md) للتعاون مع الضيوف في فريق.
- [التعاون مع المشاركين الخارجيين في قناة](/microsoft-365/solutions/collaborate-teams-direct-connect) للتعاون مع أشخاص من خارج المؤسسة في قناة مشتركة.

استنادا إلى حساسية المعلومات التي يتم مشاركتها، يمكنك إضافة ضمانات للمساعدة على منع المشاركة المفرطة. ستساعدك هذه الموارد على إعداد الحماية التي تحتاجها لمنظمتك:

- [أفضل الممارسات لمشاركة الملفات والمجلدات مع المستخدمين الذين لم يتم تأييدهم](best-practices-anonymous-sharing.md)
- [الحد من التعرض العرضي للملفات عند المشاركة مع أشخاص من خارج مؤسستك](share-limit-accidental-exposure.md)
- [إنشاء بيئة مشاركة ضيوف آمنة](create-secure-guest-sharing-environment.md)

إذا كان لديك مشروع رئيسي مع مؤسسة شريكة، يمكنك استخدام إما القنوات المشتركة [](/microsoft-365/solutions/collaborate-teams-direct-connect) أو [إدارة استحقاق Azure](b2b-extranet.md) لإدارة الأشخاص من خارج مؤسستك الذين تحتاج إلى التعاون معهم.

## <a name="training-for-administrators"></a>تدريب للمسؤولين

يمكن أن تساعدك الوحدات النمطية التدريبية هذه من Microsoft Learn على التعرف على ميزات التعاون والحوكمة والهوية في Teams SharePoint.

### <a name="teams"></a>الفرق

|التدريب:|إدارة تعاون الفريق مع Microsoft Teams|
|---|---|
|![Teams التدريب على التعاون.](../media/manage-team-collaboration-with-microsoft-teams.svg)|إدارة تعاون الفريق مع Microsoft Teams تعرفك على ميزات Microsoft Teams، المركز المركزي لتعاون الفريق في Microsoft 365. ستتعرف على كيفية استخدام Teams لتسهيل العمل الجماعي والتواصل داخل مؤسستك، سواء داخل المؤسسة أو خارجها، على مجموعة واسعة من الأجهزة، من أسطح المكتب إلى أجهزة الكمبيوتر اللوحية إلى الهواتف، مع الاستفادة من كل الوظائف الغنية في تطبيقات Office 365. ستفهم كيفية توفير Teams بيئة شاملة ومرنة للتعاون عبر التطبيقات والأجهزة. يمكن أن يساعدك مسار التعلم هذا على التحضير Microsoft 365 معتمد: Teams المسؤول المعاون.<p>2 ساعة و17 دقيقة - Learning مسار - 5 وحدات|

> [!div class="nextstepaction"]
> [ابدأ >](/learn/modules/m365-teams-collab-prepare-deployment/introduction/)

### <a name="sharepoint"></a>SharePoint

|التدريب:|التعاون في العمل SharePoint في Microsoft 365|
|---|---|
|![SharePoint التدريب.](../media/collaborate-with-sharepoint-in-microsoft-365.svg)|تعرفك إدارة المحتوى المشترك SharePoint Microsoft على ميزات SharePoint وكيفية عملها مع Microsoft 365. ستتعرف على الأنواع المختلفة من المواقع SharePoint، بما في ذلك مواقع الموزع، بالإضافة إلى حماية المعلومات وإعداد التقارير والمراقبة. ستتعرف أيضا على كيفية استخدام SharePoint الملفات والمجلدات لتحسين التعاون، وكيفية مشاركة الملفات خارجيا، وكيفية إدارة مواقع SharePoint في SharePoint إدارة. يمكن أن يساعدك مسار التعلم هذا على التحضير Microsoft 365 معتمد: شهادة إقران مسؤول العمل الجماعي.<p>ساعة و14 دقيقة - Learning مسار - 4 وحدات نموذجية|

> [!div class="nextstepaction"]
> [ابدأ >](/learn/modules/m365-teams-sharepoint-plan-sharepoint/introduction/)

### <a name="information-protection"></a>حماية المعلومات

|التدريب:|حماية معلومات المؤسسة باستخدام Microsoft 365|
|---|---|
|![Teams التدريب على حماية المعلومات.](../media/protect-enterprise-information-microsoft-365.svg)|إن حماية معلومات مؤسستك وتأمينها أصعب من أي وقت مضى. يناقش مسار حماية معلومات المؤسسة باستخدام Microsoft 365 كيفية حماية معلوماتك الحساسة من تضخيم أو إساءة الاستخدام العرضية، وكيفية اكتشاف البيانات وتصنيفها، وكيفية حمايتها باستخدام تسميات الحساسية، وكيفية مراقبة المعلومات الحساسة وتحليلها لحمايتها من فقدانها. يمكن أن يساعدك مسار التعلم هذا على التحضير Microsoft 365 معتمد: معتمد ومعتمد Microsoft 365 مسؤول الأمان: شهادات خبراء إدارة المؤسسة.<p>1 ساعة - Learning مسار - 5 وحدات نموذجية|

> [!div class="nextstepaction"]
> [ابدأ >](/learn/modules/m365-security-info-overview/introduction/)

### <a name="identity-and-access"></a>الهوية والوصول

|التدريب:|حماية الهوية والوصول باستخدام Azure Active Directory|
|---|---|
|![أيقونة التدريب على الهوية والوصول.](../media/protect-identity-and-access-with-microsoft-365.svg)|يتناول مسار التعلم الهوية والوصول إلى أحدث تقنيات الهوية والوصول، وأدوات تعزيز المصادقة، والإرشادات المتعلقة بحماية الهوية داخل مؤسستك. تمكنك تقنيات الوصول والهوية من Microsoft من تأمين هوية مؤسستك، سواء كانت في موقعها المحلية أو في السحابة، وتمكين المستخدمين من العمل بأمان من أي موقع. يمكن أن يساعدك مسار التعلم هذا على التحضير Microsoft 365 معتمد: معتمد ومعتمد Microsoft 365 مسؤول الأمان: شهادات خبراء إدارة المؤسسة.<p>2 ساعة و52 دقيقة - Learning مسار - 6 وحدات نموذجية|

> [!div class="nextstepaction"]
> [ابدأ >](/learn/modules/m365-identity-overview/introduction/)

## <a name="training-for-end-users"></a>تدريب للمستخدمين النهائيين

بإمكان الوحدات النمطية التدريبية هذه أن تساعد المستخدمين على استخدام Teams والمجموعات SharePoint للتعاون في Microsoft 365.

|الفرق|SharePoint|
|---|---|
|![قم بإعداد أيقونة تدريب الفريق وتخصيصها.](../media/set-up-customize-team-training.png)<br>**[إعداد فريقك وتخصيصه](https://support.microsoft.com/office/702a2977-e662-4038-bef5-bdf8ee47b17b)**|![SharePoint أيقونة التدريب على المشاركة والمزامنة](../media/sharepoint-share-sync-training.png)<br>**[المشاركة والمزامنة](https://support.microsoft.com/office/98cb2ff2-c27e-42ea-b055-c2d895f8a5de)**|
|![Teams أيقونة التدريب على تحميل الملفات والعثور عليها.](../media/smc-teams-upload-find-files-training.png)<br>**[Upload الملفات والعثور عليها](https://support.microsoft.com/office/57b669db-678e-424e-b0a0-15d19215cb12)**||
|![التعاون في الفرق والقنوات الأيقونة.](../media/teams-collaborate-channels-training.png)<br>**[التعاون في الفرق والقنوات](https://support.microsoft.com/office/c3d63c10-77d5-4204-a566-53ddcf723b46)**||

## <a name="illustrations"></a>رسومات توضيحية

ستساعدك هذه التوضيحات على فهم كيفية تفاعل المجموعات والفرق مع الخدمات الأخرى في Microsoft 365 وميزات التوافق والحوكمة المتوفرة لمساعدتك على إدارة هذه الخدمات في مؤسستك.

### <a name="groups-in-microsoft-365-for-it-architects"></a>المجموعات في Microsoft 365 ل IT Architects

ما يحتاج مهندسو هندسة المعلومات إلى معرفته حول المجموعات في Microsoft 365

|**عنصر**|**الوصف**|
|---|---|
|[![صورة مصغرة للمجموعات البيانية للمعلومات.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> تم التحديث في يونيو 2019|تفصيل هذه التوضيحات لأنواع المجموعات المختلفة، وكيفية إنشائها وإدارتها، وبضع توصيات حول الإدارة.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams وخدمات الإنتاجية ذات الصلة في Microsoft 365 لمهندسي المعلومات

البنية المنطقية لخدمات الإنتاجية في Microsoft 365، مع Microsoft Teams.

|**عنصر**|**الوصف**|
|---|---|
|[![صورة مصغرة لملصق Teams المنطقي.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>تحديث أبريل 2019|توفر Microsoft مجموعة من خدمات الإنتاجية التي تعمل معا لتوفير تجارب التعاون مع قدرات إدارة البيانات والأمان والتوافق. <p>توفر هذه السلسلة من الرسومات التوضيحية طريقة عرض في البنية المنطقية لخدمات الإنتاجية للمهندسين الهندسيين للمؤسسات، مما يؤدي إلى Microsoft Teams.|

## <a name="deploy-the-secure-collaboration-solution"></a>نشر حل التعاون الآمن

عندما تكون جاهزا لنشر هذا الحل، تابع الخطوات التالية:

1. تكوين ثلاث مستويات مختلفة من [الحماية Teams](configure-teams-three-tiers-protection.md).
2. قم بتكوين الإعدادات لمشاركة [المعلومات من أي حساسية مع أشخاص من خارج مؤسستك](collaborate-with-people-outside-your-organization.md).

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 وثائق الأمان](../security/index.yml)

[Microsoft 365 وثائق التوافق](../compliance/index.yml)

[مرحبا بك في Microsoft Teams](/MicrosoftTeams/Teams-overview)
