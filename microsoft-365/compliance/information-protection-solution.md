---
title: نشر حل حماية البيانات في Microsoft
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-overview
- m365solution-mip
- m365initiative-compliance
description: إرشادات وصفية لنشر حماية البيانات في Microsoft (MIP) لمنظمتك.
ms.openlocfilehash: d70f7356909b0aa0ec663a641e1bc76926db72f0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63580018"
---
# <a name="deploy-a-microsoft-information-protection-solution"></a>نشر حل حماية البيانات في Microsoft

>*[ترخيص Microsoft 365 الأمان & التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

إن استراتيجية حماية المعلومات لديك مدفوعة باحتياجات أعمالك. يتعين على العديد من المؤسسات الامتثال للأنظمة والقوانين والممارسات التجارية. بالإضافة إلى ذلك، تحتاج المؤسسات إلى حماية المعلومات الخاصة، مثل بيانات مشاريع معينة.

حماية البيانات في Microsoft (MIP) إطار عمل وعملية وإمكانيات يمكنك استخدامها لتحقيق أهداف أعمالك المحددة. 

## <a name="microsoft-information-protection-framework"></a>حماية البيانات في Microsoft العمل

استخدم حماية البيانات في Microsoft لمساعدتك على اكتشاف المعلومات الحساسة وتصنيفها وحمايتها وتحكمها أينما كانت أو تتنقل.

![نظرة عامة حول حل MIP](../media/mip-solution-overview-extended.png)

شاهد جلسة الاشعال التالية لمعرفة كيفية دعم هذه الإمكانات للدعم والبنية على [بعضها البعض:](https://myignite.microsoft.com/archives/IG20-OD273) تعرف على بياناتك، وحمي بياناتك، ومنع فقدان البيانات باستخدام حماية البيانات في Microsoft.

للحصول على معلومات حول إدارة بياناتك، راجع [إدارة معلومات Microsoft في](manage-Information-governance.md) Microsoft 365.

## <a name="licensing"></a>الترخيص

يتم تضمين قدرات MIP مع Microsoft 365 التوافق. يمكن أن تختلف متطلبات الترخيص حتى ضمن الإمكانات، استنادا إلى خيارات التكوين. لتحديد متطلبات وخيارات الترخيص، راجع Microsoft 365 [إرشادات الأمان & التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="know-your-data"></a>معرفة بياناتك

![تعرف على بياناتك للحصول على نظرة عامة حول حل MIP](../media/knowyourdata-mipsolution.png)

غالبا ما تكون معرفة مكان وجود بياناتك الحساسة هي التحدي الأكبر للعديد من المؤسسات. يساعدك تصنيف بيانات MIP على اكتشاف كميات البيانات التي تنشئها مؤسستك وتصنيفها بشكل دقيق. تساعدك التمثيلات الرسومية في الحصول على معلومات متعمقة حول هذه البيانات حتى تتمكن من إعداد السياسات ومراقبتها لحمايتها وتحكمها.


|الخطوة|الوصف|معلومات إضافية|
|:---|:----------|:---------------|
|1| وصف فئات المعلومات الحساسة التي تريد حمايتها. <br /><br /> لديك بالفعل فكرة عن أنواع المعلومات الأكثر قيمة لم المؤسسة والأنواع التي لا تكون كذلك. اعمل مع المساهمين لوصف هذه الفئات لأنها مكان البداية. | [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md) <p> [التعرف على المصنفات القابلة للتدريب](classifier-learn-about.md)|
|2| اكتشاف البيانات الحساسة وتصنيفها. <br /><br /> يمكن العثور على البيانات الحساسة في العناصر باستخدام العديد من الأساليب المختلفة التي تتضمن سياسات DLP الافتراضية والتسميات اليدوية من قبل المستخدمين، بالإضافة إلى التعرف التلقائي على الأنماط باستخدام أنواع المعلومات الحساسة أو التعلم الآلي. | [التعرف على تصنيف البيانات](data-classification-overview.md) <p> [فيديو: تصنيف البيانات في مركز التوافق](https://www.microsoft.com/videoplayer/embed/RE4vx8x)|
|3| عرض العناصر الحساسة.  <br /><br /> استخدم مستكشف المحتوى ومستكشف النشاط لتحليل العناصر الحساسة والإجراءات التي يقوم المستخدمون بها بشكل أعمق.| [بدء استخدام مستكشف المحتوى](data-classification-content-explorer.md) <p> [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)|

## <a name="protect-your-data"></a>حماية البيانات

![حماية البيانات للحصول على نظرة عامة حول حل MIP](../media/protect-mipsolution.png)

استخدم المعلومات من معرفة مكان وجود بياناتك الحساسة لمساعدتك على حمايتها بفعالية أكبر. ولكن لا حاجة للانتظار— يمكنك البدء في حماية بياناتك على الفور باستخدام تركيبة من التسميات اليدوية والافتراضية والتلقائية. بعد [ذلك،](data-classification-content-explorer.md) استخدم مستكشف المحتوى ومستكشف النشاط من المقطع السابق لتأكيد العناصر التي تم تسميتها وكيفية استخدام التسميات.[](data-classification-activity-explorer.md)

|الخطوة|الوصف|معلومات إضافية|
|:---|-----------|:---------------|
| 1|حدد [تسميات الحساسية والسياسات](sensitivity-labels.md) التي ستحمي بيانات مؤسستك. <br /><br />بالإضافة إلى تحديد حساسية المحتوى، يمكن لهذه التسميات تطبيق إجراءات الحماية، مثل رؤوس وتسميات تاشير وعلامة مائية وتشفير. | [بدء استخدام تسميات الحساسية](get-started-with-sensitivity-labels.md) <br /><br /> [إنشاء تسميات الحساسية ونهجها وتكوينها](create-sensitivity-labels.md) <br /><br /> [تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](encryption-sensitivity-labels.md) |
| 2|تسمية العناصر وحمايتها Microsoft 365 والخدمات. <br /><br />يتم دعم تسميات الحساسية Microsoft 365 Word و Excel و PowerPoint و Outlook والحاويات التي تتضمن مواقع SharePoint OneDrive و Microsoft 365 أخرى. استخدم مجموعة من أساليب التسمية مثل التسمية اليدوية والتسميات التلقائية والتسمية الافتراضية والتسمية الإلزامية.| [إدارة تسميات الحساسية في تطبيقات Office](sensitivity-labels-office-apps.md) <br /><br /> [تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) <br /><br /> [تمكين التأليف المشترك للملفات المشفرة باستخدام تسميات الحساسية](sensitivity-labels-coauthoring.md) <br /><br /> [تطبيق تسمية حساسية على المحتوى تلقائيا](apply-sensitivity-label-automatically.md) <br /><br /> [استخدام تسميات الحساسية مع Microsoft Teams Microsoft 365 ومجموعات SharePoint ويب](sensitivity-labels-teams-groups-sites.md) <br /><br /> [استخدم تسميات الحساسية لتعيين ارتباط المشاركة الافتراضي للمواقع والمستندات في SharePoint OneDrive](sensitivity-labels-default-sharing-link.md) <br /><br /> [تطبيق تسمية حساسية على نموذج في Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) <br /><br /> [تسميات الحساسية في Power BI](/power-bi/admin/service-security-sensitivity-label-overview) |
|3|يمكنك اكتشاف العناصر الحساسة الموجودة في مخازن البيانات في السحابة وتسميتها وحمايتها باستخدام [Microsoft Defender لتطبيقات](/cloud-app-security/what-is-cloud-app-security) السحابة مع تسميات الحساسية.| [اكتشاف البيانات المنظمة والحساسة المخزنة في السحابة وتصنيفها وتسميتها وحمايتها](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|4|يمكنك اكتشاف العناصر الحساسة الموجودة في مخازن البيانات المحلية وتسميتها وحمايتها من خلال نشر ماسح تسميات [Azure Information Protection](/azure/information-protection/deploy-aip-scanner) الموحد مع تسميات الحساسية.| [تكوين ماسح التسمية الموحد في Azure Information Protection وتثبيته](/azure/information-protection/deploy-aip-scanner-configure-install)|
|5|يمكنك توسيع تسميات الحساسية إلى Azure باستخدام [Azure Purview](/azure/purview/overview)، لاكتشاف عناصر تخزين Azure Blob وملفات Azure وملفات Azure Data Lake Storage Gen1 و Azure Data Lake Storage Gen12. | [وضع التسميات في Azure Purview](/azure/purview/create-sensitivity-label)|

إذا كنت مطورا تريد توسيع تسميات الحساسية لتمتد إلى تطبيقات خط العمل أو تطبيقات SaaS الخاصة ب جهة خارجية، فشاهد إعداد [SDK (MIP)](/information-protection/develop/setup-configure-mip) وتكوينه حماية البيانات في Microsoft (MIP). 

### <a name="additional-protection-capabilities"></a>إمكانات حماية إضافية

Microsoft 365 إمكانات إضافية للمساعدة في حماية البيانات. لا يحتاج كل عميل إلى هذه الإمكانات، وقد يتم الا فوق بعضها بال الإصدارات الأخيرة.

استخدم حماية البيانات في Microsoft [في Microsoft 365](information-protection.md) للحصول على القائمة الكاملة لقدرات الحماية.

## <a name="prevent-data-loss"></a>منع فقدان البيانات

![منع فقدان البيانات للحصول على نظرة عامة حول حل MIP](../media/dlp-mipsolution.png)

نشر سياسات منع فقدان البيانات (DLP) لتتحكم في المشاركة غير المناسبة للبيانات الحساسة أو نقلها أو استخدامها عبر التطبيقات والخدمات ومنعها. تساعد هذه السياسات المستخدمين على اتخاذ القرارات الصحيحة واتخاذ الإجراءات الصحيحة عند استخدامهم لبيانات حساسة.

|الخطوة|الوصف|معلومات إضافية|
|:---|:----------|:---------------|
|1|تعرف على DLP. <br /><br /> تملك المؤسسات معلومات حساسة تحت سيطرتها، مثل البيانات المالية أو البيانات الخاصة أو أرقام بطاقات الائتمان أو السجلات الصحية أو أرقام الضمان الاجتماعي. للمساعدة في حماية هذه البيانات الحساسة وتقليل المخاطر، تحتاج إلى طريقة لمنع المستخدمين من مشاركتها بشكل غير مناسب مع أشخاص لا يجب أن ينتهوا منها. تسمى هذه الممارسة منع فقدان البيانات (DLP).| [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)|
|2|تخطيط تنفيذ DLP. <br /><br /> ستخطط كل مؤسسة لمنع فقدان البيانات (DLP) وتنفيذها بطريقة مختلفة، لأن احتياجات الأعمال والأهداف والموارد والوضع الخاصة بكل مؤسسة فريدة بالنسبة لها. ومع ذلك، هناك عناصر مشتركة بين جميع تنفيذات DLP الناجحة. | [التخطيط لمنع فقدان البيانات](dlp-overview-plan-for-dlp.md)|
|3|تصميم نهج DLP وإنشاءه. <br /><br /> إن إنشاء نهج منع فقدان البيانات (DLP) أمر سريع وسهل، ولكن قد يستغرق الحصول على نهج للحصول على النتائج المرجوة وقتا طويلا إذا كان عليك القيام بالكثير من الضبط. يؤدي أخذ الوقت لتصميم نهج قبل تنفيذه إلى الوصول إلى النتائج المطلوبة بشكل أسرع، وبخط أقل من المشاكل غير المقصودة، مقارنة بالضبط حسب الإصدار التجريبي والخطأ فقط.| [تصميم نهج DLP](dlp-policy-design.md) <p> [مرجع نهج DLP](dlp-policy-reference.md) <p>[إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)|
|4|اضبط سياسات DLP. <br /><br /> بعد نشر نهج DLP، ستشاهد مدى تلبية هذه النهج للهدف المقصود. استخدم هذه المعلومات لضبط إعدادات النهج للحصول على أداء أفضل. | [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)|


## <a name="training-resources"></a>موارد التدريب

Learning النمطية للمستشارين المسؤولين:

- [مقدمة حول حماية المعلومات والحوكمة في Microsoft 365](/learn/modules/m365-compliance-information-governance)
- [تصنيف البيانات للحماية والحوكمة](/learn/modules/m365-compliance-information-classify-data)
- [حماية المعلومات في Microsoft 365](/learn/modules/m365-compliance-information-protect-information)
- [منع فقدان البيانات في Microsoft 365](/learn/modules/m365-compliance-information-prevent-data-loss)

للمساعدة في تدريب المستخدمين على تطبيق تسميات الحساسية التي تقوم بتكوينها واستخدامها لهم، راجع وثائق المستخدم النهائي لتسميات [الحساسية](get-started-with-sensitivity-labels.md#end-user-documentation-for-sensitivity-labels).

عند نشر سياسات منع فقدان البيانات ل Teams، قد تجد إرشادات المستخدم النهائي التالية مفيدة كمقدمة لهذه التقنية مع بعض الرسائل المحتملة التي قد يرونها: رسائل Teams حول منع فقدان البيانات [(DLP) ](https://support.microsoft.com/office/teams-messages-about-data-loss-prevention-dlp-and-communication-compliance-policies-c5631c3f-f61b-4306-a6ac-6603d9fc5ff0)ونهج توافق الاتصالات.
