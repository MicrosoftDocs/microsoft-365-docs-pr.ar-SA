---
title: اختر حماية البيانات في Microsoft (MIP) المضمنة لتطبيقات Office عبر الوظائف الإضافية Azure Information Protection (AIP)
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: عند استخدام عميل التسمية الموحد لحماية معلومات Azure (AIP)، يمكنك فهم فوائد استخدام التسميات المضمنة لتطبيقات Office بدلا من الوظائف الإضافية AIP.
ms.openlocfilehash: 88849422d295cc7caf2eb39837f7f1bb82b7a378
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704723"
---
# <a name="why-choose-mip-built-in-labeling-over-the-aip-add-in-for-office-apps"></a>لماذا اختر تسمية MIP المضمنة عبر الوظائف الإضافية AIP لتطبيقات Office

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

عند استخدام تسميات الحساسية في Microsoft 365 Apps على أجهزة كمبيوتر Windows، يكون لديك خيار استخدام التسميات المضمنة في تطبيقات Office، أو إضافة إضافية من عميل التسمية الموحد لحماية معلومات [Azure (AIP](/azure/information-protection/rms-client/aip-clientv2)).[](sensitivity-labels.md) 

تشكل التسميات المضمنة حجر الزاوية لنشر [حماية البيانات في Microsoft (MIP)](information-protection-solution.md) لأن تقنية التسمية هذه تمتد عبر الأنظمة الأساسية (Windows و macOS و iOS و Android و الويب)، بالإضافة إلى تطبيقات وخدمات Microsoft وغيرها. تم أيضا تصميم التسميات المضمنة للعمل مع إمكانات MIP الأخرى، مثل تصنيف البيانات ومنع فقدان البيانات (DLP).

نظرا لأن التسميات المضمنة لا تستخدم Office الإضافية، فإنها تستفيد من المزيد من الثبات والأداء الأفضل. كما تدعم أيضا أحدث ميزات MIP، مثل المصنفات المتقدمة.

بشكل افتراضي، يتم إيقاف تشغيل التسميات المضمنة في Office لتطبيقات Windows عند تثبيت عميل AIP. يمكنك تغيير هذا السلوك الافتراضي باستخدام الإرشادات الموجودة في المقطع التالي، كيفية تعطيل الوظائف الإضافية [AIP](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps) لاستخدام التسميات المضمنة لتطبيقات Office التطبيقات.

عند الاحتفاظ ب عميل AIP مثبتا ولكن معطلا في تطبيقات Office، تبقى الإمكانات الأخرى الخاصة ب عميل AIP معتمدة:

- خيارات النقر بضغطة زر الماوس الأيمن في "مستكشف الملفات" للمستخدمين لتطبيق التسميات على كل أنواع الملفات.

- عارض لعرض الملفات المشفرة للنص أو الصور أو مستندات PDF.

- وحدة PowerShell النمطية لاكتشاف المعلومات الحساسة في الملفات في الموقع، وتطبيق التسميات والتشفير من هذه الملفات أو إزالتها منها.

- ماسح ضوئي لاكتشاف المعلومات الحساسة المخزنة في مخازن البيانات المحلية، ثم تسمية هذا المحتوى اختياريا.

لمزيد من المعلومات حول هذه الإمكانات التي تتجاوز Office التطبيقات، راجع دليل مسؤول تسمية عميل [Azure](/azure/information-protection/rms-client/clientv2-admin-guide) الموحد لحماية المعلومات من وثائق AIP.

بشكل مستقل عن التسميات، يمكنك الاستمرار في استخدام وحدة [AIPService](/powershell/module/aipservice) PowerShell النمطية لإدارة خدمة التشفير على مستوى المستأجر. على سبيل المثال، قم بتكوين وصول مستخدم فائق عندما تحتاج إلى إزالة التشفير لاسترداد البيانات، وتعقب المستندات التي تم فتحها بواسطة عميل AIP وإبطالها، وتكوين فترة صلاحية استخدام الترخيص للوصول دون اتصال. لمزيد من المعلومات، راجع [إدارة الحماية من حماية معلومات Azure باستخدام PowerShell](/azure/information-protection/administer-powershell).

## <a name="decide-whether-to-use-built-in-labeling-for-office-apps-or-the-aip-add-in"></a>تحديد ما إذا كنت تريد استخدام التسميات المضمنة لتطبيقات Office أو الوظائف الإضافية AIP

الآن وبعد أن أصبح عميل AIP في [](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613)وضع الصيانة، لا نوصي باستخدام الوظائف الإضافية AIP لتطبيقات Office للأسباب التالية:

- لن يتم دعم أي ميزات تسمية جديدة.
- الوظائف الإضافية أقل استقرارا لأنها قد تتضارب مع الوظائف الإضافية الأخرى التي قد تؤدي إلى تعليق Office أو تعطلها أو تعطيلها تلقائيا.
- وكواد إضافية، يتم تشغيلها ببطء أكبر، ويمكن تعطيلها من قبل المستخدمين لتجاوز متطلبات التسمية.
- تتطلب أي إصلاحات أخطاء إعادة تثبيت عميل Azure Information Protection.
- تختلف تجربة وضع التسميات للمستخدمين قليلا عن التسميات المضمنة التي لدى المستخدمين على أجهزتهم الأخرى (macOS و iOS و Android) وعند استخدامهم Office على الويب. يمكن أن يزيد هذا الفرق تكاليف التدريب والدعم.
- هناك ميزات جديدة Office التي تم إصدارها ولا يتم دعمها إلا بواسطة التسميات المضمنة، وتنمو القائمة في كل الأوقات.[](#features-supported-only-by-built-in-labeling-for-office-apps)

استخدم الوظائف الإضافية AIP لتطبيقات Windows Office فقط إذا كنت قد نشرتها بالفعل للمستخدمين واحتاجت إلى وقت لترحيلها إلى تسميات مضمنة. أو يحتاج المستخدمون إلى ميزة غير معتمدة بواسطة التسميات المضمنة. استخدم [معلومات اتقاء الميزات](#feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps) في هذه الصفحة لمساعدتك على تحديد هذه الميزات.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>الميزات المعتمدة فقط بواسطة التسميات المضمنة لتطبيقات Office

> [!NOTE]
> هناك العديد من ميزات التسمية الجديدة في التخطيط أو التطوير، لذا تتوقع أن تنمو القائمة في هذا القسم مع مرور الوقت.

يتم دعم بعض الميزات فقط بواسطة التسميات المضمنة لتطبيقات Office، ولن يتم دعمها بواسطة الوظائف الإضافية AIP. وتتضمن هذه الخيارات:

- للتسمية التلقائية والموصى بها:
    - الوصول إلى خدمات التصنيف الذكية التي تتضمن [تصنيفات](classifier-learn-about.md) قابلة للتدريب ومطابقة البيانات الدقيقة [(EDM)](sit-learn-about-exact-data-match-based-sits.md) [والكيانات المسماة](named-entities-learn.md)
    - الكشف عن المعلومات الحساسة مع كتابة المستخدمين
    - في Word، يمكن للمستخدمين مراجعة المحتوى الحساس المعرف وإزالته
- بالنسبة إلى التسميات التي تسمح للمستخدمين بتعيين أذونات، يمكن منح أذونات مختلفة (قراءة أو تغيير) للمستخدمين أو المجموعات
- Encrypt-Only رسائل البريد الإلكتروني
- رؤية التسميات على شريط المعلومات
- دعم تبديل الحساب
- لا يمكن للمستخدمين تعطيل التسمية

مثال يوضح كيف يمكن للمستخدمين مراجعة المحتوى الحساس المعرف وإزالته بشكل اختياري في Word:

![أرقام بطاقات الائتمان المحددة للمستخدمين كمحتوى حساسية مع خيار لإزالتها.](../media/detect-sensitive-content.png)

لمعرفة متى تصبح إمكانيات التسمية الجديدة متوفرة للتسميات المضمنة، راجع ما الجديد في [](whats-new.md) Microsoft 365 ومقسمات تسميات الحساسية.

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>كيفية تعطيل الوظائف الإضافية AIP لاستخدام التسميات المضمنة لتطبيقات Office

عند تثبيت عميل AIP لتوسيع التسميات إلى ما هو أبعد من تطبيقات Office ولكنك تريد منع تحميل الوظائف الإضافية للعميل في تطبيقات Office، استخدم قائمة إعداد نهج المجموعة ل الوظائف الإضافية المدارة كما هو موثق في عدم تحميل  الوظائف الإضافية بسبب إعدادات نهج المجموعة لبرامج [Office 2013 و Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

بالنسبة لتطبيقات Windows Office التي تدعم التسميات المضمنة، استخدم تكوين Microsoft Word 2016 و Excel 2016 و PowerPoint 2016 و Outlook 2016، وحدد المعرف البرنامجي التالي (ProgID) للعميل AIP **، ثم قم بتعيين الخيار إلى 0: تكون الوظائف الإضافية معطلة دائما (تم حظرها)**

|Application  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

نشر هذا الإعداد باستخدام "نهج المجموعة"، أو باستخدام خدمة Office [السحابية](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> إذا كنت تستخدم إعداد نهج المجموعة استخدم ميزة الحساسية في **Office** لتطبيق تسميات الحساسية وعرضها ثم قم بتعيينها إلى **1**، فهناك بعض الحالات التي قد لا تزال فيها الوظائف الإضافية AIP تحمل في تطبيقات Office. منع تحميل الوظائف الإضافية في كل تطبيق يمنع حدوث ذلك.

بدلا من ذلك، يمكنك تعطيل أو إزالة ميزة الحماية من المعلومات من **Microsoft Azure** Office من Word Excel و PowerPoint و Outlook. هذا الأسلوب مناسب لكمبيوتر واحد، واختبار مخصص. للحصول على الإرشادات، راجع عرض الوظائف الإضافية وإدارتها وتثبيتها [في Office البرامج](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d).

أيا كان الأسلوب الذي تختاره، يتم تطبيق التغييرات عند Office تشغيل التطبيقات.

> [!NOTE]
> تتطلب التسميات المضمنة إصدار اشتراك Office التطبيقات. إذا كان لديك إصدارات مستقلة من Office، تسمى أحيانا "Office الدائم"، نوصي بالترقية إلى Microsoft 365 Apps للمؤسسات للاستفادة من أحدث إمكانات [التسمية](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

تذكر أنه عند استخدام هذا الأسلوب لتعطيل الوظائف الإضافية AIP، لا يزال بإمكانك استخدام عميل AIP لتوسيع التسميات إلى Office التطبيقات.

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>اتقاء الميزات للتسمية المضمنة وا الإضافية AIP لتطبيقات Office

يتم الآن دعم العديد من ميزات التسمية المعتمدة بواسطة الوظائف الإضافية AIP بواسطة التسميات المضمنة. للحصول على قائمة أكثر تفصيلا للإمكانات والحد الأدنى للإصدارات التي قد تكون مطلوبة ومعلومات التكوين، راجع إدارة تسميات الحساسية [في Office التطبيقات](sensitivity-labels-office-apps.md).

يتم التخطيط لمزيد من الميزات وفي وضع التطوير. إذا كانت هناك ميزة معينة تهمك، فتحقق من Microsoft 365 وحدد الانضمام إلى حماية البيانات في Microsoft [](https://aka.ms/MIPC/Roadmap) في [Office خاص](https://aka.ms/MIP/PreviewRing).

استخدم المعلومات التالية لمساعدتك على تحديد ما إذا كنت تستخدم ميزة من الوظائف الإضافية AIP غير المعتمدة بعد بواسطة التسميات المضمنة:

|ميزة أو إمكانية الوظائف الإضافية ل AIP|تسمية مضمنة |
|:-------------------------------|:----------------:|
|**الفئة: عام** ||
|إعداد التقارير والتدقيق المركزي|![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|Government Cloud|![معتمد.](../media/yes-icon.png)|
|يمكن للمسؤول تعطيل التسمية <br> - جميع التطبيقات|  ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-office-apps.md#office-built-in-labeling-client-and-other-labeling-solutions)|
|يمكن للمسؤول تعطيل التسمية <br> - لكل تطبيق|  في التخطيط أو التطوير|
|**الفئة: تجربة المستخدم** ||
|الزر "تسمية" على الشريط|![معتمد.](../media/yes-icon.png)|
|دعم متعدد اللغات لأسماء التسميات وأصابع الأدوات| ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|ألوان التسمية| في التخطيط أو التطوير |
|رؤية التسميات على شريط الأدوات| في التخطيط أو التطوير |
|**الفئة: إجراءات التسمية** ||
|التسمية اليدوية |  ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|التسمية الإلزامية | ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels.md#what-label-policies-can-do)|
|التسمية الافتراضية <br> - العناصر الجديدة والموجودة <br> - فصل الإعدادات للبريد الإلكتروني|  ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels.md#what-label-policies-can-do) |
|مستحسن أو تلقائي |![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|تخفيض درجة التبرير |  ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels.md#what-label-policies-can-do)|
| **الفئة: العلامات المرئية** | |
|رؤوس وتواسير وعلامة مائية| ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels.md#what-label-policies-can-do)|
|علامات ديناميكية| ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|وضع علامات مرئية لكل تطبيق| ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **الفئة: التشفير** | |
|الأذونات المعرفة من قبل المسؤول | ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](encryption-sensitivity-labels.md#assign-permissions-now) |
|الأذونات المعرفة من قبل المستخدم <br> - عدم إعادة توجيه Outlook <br> - أذونات مخصصة للمستخدم والمجموعة ل Word، Excel، PowerPoint| ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|الأذونات المعرفة من قبل المستخدم <br> - الأذونات المخصصة على مستوى المؤسسة من خلال تحديد مجالات ل Word Excel PowerPoint | في التخطيط أو التطوير |
|التأليف المشترك وال حفظ تلقائي | ![معتمد.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-coauthoring.md) |
|تشفير المفتاح المزدوج | في التخطيط أو التطوير |
|إلغاء المستند للمستخدمين | قيد المراجعة |
| | |

### <a name="support-for-powershell-advanced-settings"></a>دعم الإعدادات المتقدمة في PowerShell

يدعم عميل AIP العديد من التخصيصات باستخدام [الإعدادات المتقدمة في PowerShell](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell). يتم الآن دعم بعض هذه الإعدادات المتقدمة بواسطة التسميات المضمنة، كما هو موثق في [New-Label](/powershell/module/exchange/new-label) أو [Set-Label](/powershell/module/exchange/set-label) و [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) أو [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy).

ومع ذلك، قد تجد أنك لست بحاجة إلى استخدام PowerShell لتكوين الإعدادات المعتمدة لأنها مضمنة في التكوين القياسي من مركز التوافق في Microsoft 365. على سبيل المثال، القدرة على إيقاف تشغيل التسميات الإلزامية Outlook تعيين تسمية افتراضية مختلفة.

التكوينات التالية من الوظائف الإضافية AIP غير معتمدة بعد بواسطة التسميات المضمنة تتضمن:

- [توريث التسمية من مرفقات البريد الإلكتروني](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [S/MIME Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
- [إرسال رسائل منبثقة إلى Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [تسمية فرعية افتراضية لتسمية أصل](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [إزالة علامات المحتوى الخارجي](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>الميزات غير المخطط دعمها بواسطة التسميات المضمنة لتطبيقات Office

على الرغم من أنه يتم إضافة قدرات جديدة للتسميات المضمنة في كل الأوقات، إلا أن الوظائف الإضافية AIP Office تدعم الإمكانات التالية التي لم يتم التخطيط لتوفرها في الإصدارات المستقبلية للتسميات المضمنة:

- تطبيق التسميات Microsoft Office 97-2003، مثل .doc الملفات
- أجهزة كمبيوتر غير منقطعة الاتصال بشكل دائم
- إصدارات مستقلة من Office (تسمى أحيانا "Office الدائمة") بدلا من الإصدارات المستندة إلى الاشتراك

## <a name="next-steps"></a>الخطوات التالية

للحصول على إرشادات لإنشاء قدرات التسمية هذه وتكوينها، راجع إنشاء تسميات الحساسية ونهجها [وتكوينها](create-sensitivity-labels.md).

> [!TIP]
> إذا كان لديك بالفعل تسميات الحساسية في مركز التوافق في Microsoft 365، فلن تكون مؤهلا لإنشاء التسميات الافتراضية تلقائيا. ومع ذلك، قد لا يزال من المفيد الإشارة إلى تكوينها: [تسميات الحساسية الافتراضية](mip-easy-trials.md#default-sensitivity-labels). 
