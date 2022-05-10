---
title: اختر تسمية مضمنة ل Microsoft Purview حماية البيانات لتطبيقات Office عبر الوظيفة الإضافية حماية البيانات Azure (AIP)
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
description: عند استخدام عميل التسمية الموحد ل Azure حماية البيانات (AIP)، فهم مزايا استخدام التسمية المضمنة لتطبيقات Office بدلا من الوظيفة الإضافية AIP.
ms.openlocfilehash: 161f05c1f9c27723ff4940087c715e0556484b79
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287123"
---
# <a name="why-choose-built-in-labeling-over-the-aip-add-in-for-office-apps"></a>لماذا اختر تسمية مضمنة عبر الوظيفة الإضافية AIP لتطبيقات Office

>*[Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

عند استخدام [تسميات الحساسية](sensitivity-labels.md) في Microsoft 365 Apps على أجهزة الكمبيوتر Windows، لديك خيار استخدام التسمية المضمنة في تطبيقات Office، أو وظيفة إضافية من [عميل التسمية الموحدة ل Azure حماية البيانات (AIP](/azure/information-protection/rms-client/aip-clientv2)). 

تشكل التسمية المضمنة حجر الزاوية [لنشر حماية معلومات Microsoft Purview](information-protection-solution.md) لأن تقنية التسمية هذه تمتد عبر الأنظمة الأساسية (Windows وmacOS وiOS وAndroid والويب)، وكذلك عبر تطبيقات Microsoft وخدماتها وما بعدها. كما تم تصميم التسمية المضمنة للعمل مع قدرات Microsoft Purview الأخرى، مثل تصنيف البيانات ومنع فقدان بيانات Microsoft Purview (DLP).

نظرا لأن التسميات المضمنة لا تستخدم وظيفة إضافية Office، فإنها تستفيد من المزيد من الاستقرار والأداء الأفضل. كما أنها تدعم أحدث ميزات Microsoft Purview، مثل المصنفات المتقدمة.

بشكل افتراضي، يتم إيقاف تشغيل التسمية المضمنة في Office لتطبيقات Windows عند تثبيت عميل AIP. يمكنك تغيير هذا السلوك الافتراضي باستخدام الإرشادات الموجودة في القسم التالي، [كيفية تعطيل الوظيفة الإضافية AIP لاستخدام التسمية المضمنة لتطبيقات Office](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps).

عند الاحتفاظ بعميل AIP مثبتا ولكن معطلا في تطبيقات Office، تظل الإمكانات الأخرى لعميل AIP مدعومة:

- خيارات النقر بزر الماوس الأيمن في مستكشف الملفات للمستخدمين لتطبيق التسميات على كافة أنواع الملفات.

- عارض لعرض الملفات المشفرة للنص أو الصور أو مستندات PDF.

- وحدة PowerShell لاكتشاف المعلومات الحساسة في الملفات المحلية، وتطبيق أو إزالة التسميات والتشفير من هذه الملفات.

- ماسح ضوئي لاكتشاف المعلومات الحساسة المخزنة في مخازن البيانات المحلية، ثم بشكل اختياري، قم بتسمية هذا المحتوى.

لمزيد من المعلومات حول هذه الإمكانات التي توسع التسمية إلى ما هو أبعد من تطبيقات Office، راجع [دليل مسؤول عميل التسمية الموحد في Azure حماية البيانات](/azure/information-protection/rms-client/clientv2-admin-guide) من وثائق AIP.

بشكل مستقل عن التسمية، يمكنك الاستمرار في استخدام الوحدة النمطية [AIPService](/powershell/module/aipservice) PowerShell لإدارة على مستوى المستأجر لخدمة التشفير. على سبيل المثال، قم بتكوين وصول المستخدم الفائق عندما تحتاج إلى إزالة التشفير لاسترداد البيانات، وتعقب المستندات التي تم فتحها بواسطة عميل AIP وإبطالها، وتكوين فترة صلاحية ترخيص الاستخدام للوصول دون اتصال. لمزيد من المعلومات، راجع [إدارة الحماية من Azure حماية البيانات باستخدام PowerShell](/azure/information-protection/administer-powershell).

## <a name="decide-whether-to-use-built-in-labeling-for-office-apps-or-the-aip-add-in"></a>تحديد ما إذا كنت تريد استخدام التسمية المضمنة لتطبيقات Office أو الوظيفة الإضافية AIP

الآن بعد أن أصبح عميل AIP في [وضع الصيانة](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613)، لا نوصي باستخدام الوظيفة الإضافية AIP لتطبيقات Office للأسباب التالية:

- لن يتم دعم أي ميزات تسمية جديدة.
- الوظائف الإضافية أقل استقرارا لأنها قد تتعارض مع الوظائف الإضافية الأخرى التي يمكن أن تؤدي إلى تعليق Office التطبيقات أو تعطلها أو تعطيلها تلقائيا.
- كوظيفة إضافية، يتم تشغيلها ببطء أكبر، ويمكن للمستخدمين تعطيلها لتجاوز متطلبات التسمية.
- تتطلب أي إصلاحات أخطاء إعادة تثبيت عميل azure حماية البيانات.
- تختلف تجربة التسمية للمستخدمين قليلا عن التسميات المضمنة التي يمتلكها المستخدمون على أجهزتهم الأخرى (macOS وiOS وAndroid) وعند استخدامهم Office على الويب. يمكن أن يزيد هذا الاختلاف من تكاليف التدريب والدعم.
- هناك بالفعل ميزات تسمية Office جديدة تم [إصدارها والتي يتم دعمها فقط بواسطة التسمية المضمنة](#features-supported-only-by-built-in-labeling-for-office-apps)، وتزداد القائمة طوال الوقت.

استخدم الوظيفة الإضافية AIP لتطبيقات Windows Office فقط إذا كنت قد قمت بالفعل بنشرها للمستخدمين وتحتاج إلى وقت ترحيلها إلى التسمية المضمنة. أو يحتاج المستخدمون إلى ميزة غير معتمدة بواسطة التسمية المضمنة. استخدم [معلومات تماثل الميزات](#feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps) في هذه الصفحة لمساعدتك على تحديد هذه الميزات.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>الميزات المدعومة فقط من خلال التسمية المضمنة لتطبيقات Office

> [!NOTE]
> توجد العديد من ميزات التسمية الجديدة في التخطيط أو التطوير، لذا توقع أن تنمو القائمة الموجودة في هذا القسم بمرور الوقت.

يتم دعم بعض الميزات فقط من خلال التسمية المضمنة لتطبيقات Office، ولن تكون مدعومة من قبل الوظيفة الإضافية AIP. وتشمل هذه الخطوات ما يلي:

- للتسمية التلقائية والموصى بها:
    - الوصول إلى خدمات التصنيف الذكية التي تتضمن [مصنفات قابلة للتدريب](classifier-learn-about.md) [ومطابقة البيانات الدقيقة (EDM)](sit-learn-about-exact-data-match-based-sits.md) [والكيانات المسماة](named-entities-learn.md)
    - الكشف عن المعلومات الحساسة أثناء كتابة المستخدمين
    - في Word، يمكن للمستخدمين مراجعة المحتوى الحساس المحدد وإزالته
- بالنسبة للتسميات التي تسمح للمستخدمين بتعيين الأذونات، يمكن منح أذونات مختلفة (قراءة أو تغيير) للمستخدمين أو المجموعات
- Encrypt-Only لرسائل البريد الإلكتروني
- رؤية التسميات على شريط المعلومات
- دعم تبديل الحساب
- لا يمكن للمستخدمين تعطيل التسمية

مثال يوضح كيف يمكن للمستخدمين مراجعة المحتوى الحساس المعرف في Word وإزالته اختياريا:

![أرقام بطاقات الائتمان المحددة للمستخدمين على أنها محتوى حساسية مع خيار لإزالته.](../media/detect-sensitive-content.png)

للبقاء على اطلاع عندما تصبح قدرات التسمية الجديدة متوفرة للتسمية المضمنة، راجع [الميزات الجديدة في قسمي وصف الحساسية وMicrosoft Purview](whats-new.md).

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>كيفية تعطيل الوظيفة الإضافية AIP لاستخدام التسمية المضمنة لتطبيقات Office

عند تثبيت عميل AIP لتوسيع التسمية إلى ما هو أبعد من تطبيقات Office ولكنك تريد منع تحميل الوظيفة الإضافية للعميل في تطبيقات Office، استخدم قائمة الإعدادات نهج المجموعة **للوظائف الإضافية المدارة** كما هو موثق في ["لا توجد وظائف إضافية" تم تحميلها بسبب إعدادات نهج المجموعة لبرامج Office 2013 و Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

بالنسبة لتطبيقات Windows Office التي تدعم التسمية المضمنة، استخدم التكوين Microsoft Word 2016، Excel 2016، PowerPoint 2016، Outlook 2016، وحدد المعرفات البرمجية التالية (ProgID) لعميل AIP، وعين الخيار إلى **0: الوظيفة الإضافية معطلة دائما (محظورة)**

|Application  |Progid  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

نشر هذا الإعداد باستخدام نهج المجموعة، أو باستخدام [خدمة نهج السحابة Office](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> إذا كنت تستخدم إعداد نهج المجموعة **، فاستخدم ميزة الحساسية في Office لتطبيق أوصاف الحساسية وعرضها** وقمت بتعيينها إلى **1**، فهناك بعض الحالات التي قد لا تزال فيها الوظيفة الإضافية AIP محملة في تطبيقات Office. يؤدي حظر تحميل الوظيفة الإضافية في كل تطبيق إلى منع حدوث ذلك.

بدلا من ذلك، يمكنك تعطيل **وظيفة Microsoft Azure حماية البيانات Office الإضافية** أو إزالتها بشكل تفاعلي من Word Excel PowerPoint Outlook. هذا الأسلوب مناسب لجهاز كمبيوتر واحد، واختبار مخصص. للحصول على الإرشادات، راجع [عرض الوظائف الإضافية وإدارتها وتثبيتها في برامج Office](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d).

أيا كانت الطريقة التي تختارها، فستدخل التغييرات حيز التنفيذ عند إعادة تشغيل تطبيقات Office.

> [!NOTE]
> تتطلب التسميات المضمنة إصدار اشتراك من تطبيقات Office. إذا كان لديك إصدارات مستقلة من Office، تسمى أحيانا "Office الدائمة"، نوصي بالترقية إلى Microsoft 365 Apps ل Enterprise للاستفادة من [أحدث قدرات التسمية](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

تذكر أنه عند استخدام هذا الأسلوب لتعطيل الوظيفة الإضافية AIP، لا يزال بإمكانك استخدام عميل AIP لتوسيع التسمية إلى ما هو أبعد من تطبيقات Office.

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>تماثل الميزات للتسمية المضمنة والوظيفة الإضافية AIP لتطبيقات Office

يتم الآن دعم العديد من ميزات التسمية المدعومة من قبل الوظيفة الإضافية AIP بواسطة التسمية المضمنة. للحصول على قائمة أكثر تفصيلا من القدرات، والحد الأدنى للإصدارات التي قد تكون مطلوبة، ومعلومات التكوين، راجع [إدارة تسميات الحساسية في تطبيقات Office](sensitivity-labels-office-apps.md).

يتم التخطيط لمزيد من الميزات وفي مرحلة التطوير. إذا كانت هناك ميزة معينة تهمك، فتحقق من [مخطط Microsoft 365](https://aka.ms/MIPC/Roadmap) وفكر [في الانضمام إلى حماية البيانات في Microsoft في Office المعاينة الخاصة](https://aka.ms/MIP/PreviewRing).

استخدم المعلومات التالية لمساعدتك في تحديد ما إذا كنت تستخدم ميزة من الوظيفة الإضافية AIP غير معتمدة بعد بواسطة التسمية المضمنة:

|ميزة وظيفة AIP الإضافية أو إمكانيتها|التسمية المضمنة |
|:-------------------------------|:----------------:|
|**الفئة: عام** ||
|إعداد التقارير والتدقيق المركزي|![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|سحابة حكومية|![دعم.](../media/yes-icon.png)|
|يمكن للمسؤول تعطيل التسمية <br> - جميع التطبيقات|  ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-office-apps.md#if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows)|
|يمكن للمسؤول تعطيل التسمية <br> - لكل تطبيق|  في التخطيط أو التطوير|
|**الفئة: تجربة المستخدم** ||
|الزر "تسمية" على الشريط|![دعم.](../media/yes-icon.png)|
|دعم اللغات المتعددة لأسماء التسميات وتلميحات الأدوات| ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|ألوان التسمية| في التخطيط أو التطوير |
|رؤية التسميات على شريط الأدوات| في التخطيط أو التطوير |
|**الفئة: إجراءات التسمية** ||
|التسمية اليدوية |  ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|التسمية الإلزامية | ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels.md#what-label-policies-can-do)|
|التسمية الافتراضية <br> - العناصر الجديدة والموجودة <br> - إعدادات منفصلة للبريد الإلكتروني|  ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels.md#what-label-policies-can-do) |
|مستحسن أو تلقائي |![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|ضبط التدرج التنازلي |  ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels.md#what-label-policies-can-do)|
| **الفئة: علامات مرئية** | |
|الرؤوس والتذييلات والعلامة المائية| ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels.md#what-label-policies-can-do)|
|العلامات الديناميكية| ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|وضع علامة مرئية لكل تطبيق| ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **الفئة: التشفير** | |
|الأذونات المعرفة من قبل المسؤول | ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](encryption-sensitivity-labels.md#assign-permissions-now) |
|الأذونات المعرفة من قبل المستخدم <br> - عدم إعادة التوجيه Outlook <br> - الأذونات المخصصة للمستخدم والمجموعة ل Word، Excel، PowerPoint| ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|الأذونات المعرفة من قبل المستخدم <br> - أذونات مخصصة على مستوى المؤسسة عن طريق تحديد مجالات ل Word أو Excel أو PowerPoint | في التخطيط أو التطوير |
|التأليف المشترك والحفظ التلقائي | ![دعم.](../media/yes-icon.png) <br>[معرفة المزيد](sensitivity-labels-coauthoring.md) |
|تشفير المفتاح المزدوج | في التخطيط أو التطوير |
|إبطال المستند للمستخدمين | قيد المراجعة |
| | |

### <a name="support-for-powershell-advanced-settings"></a>دعم إعدادات PowerShell المتقدمة

يدعم عميل AIP العديد من التخصيصات باستخدام [إعدادات PowerShell المتقدمة](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell). بعض هذه الإعدادات المتقدمة مدعومة الآن بواسطة التسمية المضمنة، كما هو موثق في [New-Label](/powershell/module/exchange/new-label) أو [Set-Label](/powershell/module/exchange/set-label) و [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) أو [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy).

ومع ذلك، قد تجد أنك لا تحتاج إلى استخدام PowerShell لتكوين الإعدادات المدعومة لأنها مضمنة في التكوين القياسي من مدخل توافق Microsoft Purview. على سبيل المثال، القدرة على إيقاف تشغيل التسمية الإلزامية Outlook وتعيين تسمية افتراضية مختلفة.

التكوينات التالية من الوظيفة الإضافية AIP غير معتمدة بعد بواسطة التسمية المضمنة وتشمل:

- [توريث التسمية من مرفقات البريد الإلكتروني](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [S/MIME ل Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
- [المشاركة الزائدة في الرسائل المنبثقة Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [تسمية فرعية افتراضية لتسمية أصل](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [إزالة علامات المحتوى الخارجي](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>الميزات غير المخطط دعمها بواسطة التسمية المضمنة لتطبيقات Office

على الرغم من أنه تتم إضافة قدرات جديدة للتسمية المضمنة طوال الوقت، تدعم الوظيفة الإضافية AIP Office الإمكانات التالية غير المخطط أن تكون متوفرة في الإصدارات المستقبلية للتسمية المضمنة:

- تطبيق التسميات على تنسيقات Microsoft Office 97-2003، مثل ملفات .doc
- أجهزة كمبيوتر غير متصلة بشكل دائم
- الإصدارات المستقلة من Office (تسمى أحيانا "Office الدائمة") بدلا من الإصدارات المستندة إلى الاشتراك

## <a name="next-steps"></a>الخطوات التالية

للحصول على إرشادات لإنشاء وتكوين قدرات التسمية هذه، راجع [إنشاء وتكوين تسميات الحساسية ونهجها](create-sensitivity-labels.md).

> [!TIP]
> إذا كان لديك بالفعل تسميات الحساسية في مدخل توافق Microsoft Purview، فلن تكون مؤهلا للإنشاء التلقائي للتسميات الافتراضية. ومع ذلك، قد لا تزال تجد أنه من المفيد الإشارة إلى تكوينها: [تسميات الحساسية الافتراضية](mip-easy-trials.md#default-sensitivity-labels). 
