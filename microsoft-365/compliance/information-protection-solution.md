---
title: نشر حل حماية المعلومات باستخدام Microsoft Purview
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
description: إرشادات توجيهية لنشر حماية البيانات Microsoft Purview لمؤسستك.
ms.openlocfilehash: 28d0af5bba237a9f2d120f67eb1e79dd74a69f2a
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65284877"
---
# <a name="deploy-an-information-protection-solution-with-microsoft-purview"></a>نشر حل حماية المعلومات باستخدام Microsoft Purview

>*[ترخيص توافق & الأمان Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تعتمد استراتيجية حماية المعلومات الخاصة بك على احتياجات عملك. يجب على العديد من المؤسسات الامتثال للوائح والقوانين وممارسات الأعمال. بالإضافة إلى ذلك، تحتاج المؤسسات إلى حماية المعلومات الخاصة، مثل بيانات مشاريع معينة.

يوفر Microsoft Purview حماية البيانات (سابقا حماية البيانات في Microsoft) إطار عمل وعملية وإمكانيات يمكنك استخدامها لتحقيق أهداف عملك المحددة. 

## <a name="microsoft-purview-information-protection-framework"></a>إطار عمل Microsoft Purview حماية البيانات

استخدم microsoft Purview حماية البيانات لمساعدتك في اكتشاف المعلومات الحساسة وتصنيفها وحمايتها وإدارتها أينما كانت أو تنتقل.

![نظرة عامة على حل Microsoft Purview حماية البيانات](../media/mip-solution-overview-extended.png)

شاهد جلسة Ignite التالية لمعرفة كيفية دعم هذه القدرات والبناء على بعضها: [تعرف على بياناتك، وقم بحماية بياناتك، ومنع فقدان البيانات باستخدام حماية البيانات في Microsoft](https://myignite.microsoft.com/archives/IG20-OD273).

للحصول على معلومات حول التحكم في بياناتك، راجع [إدارة بياناتك باستخدام Microsoft Purview](manage-Information-governance.md).

## <a name="licensing"></a>الترخيص

يتم تضمين قدرات حماية البيانات Microsoft Purview مع Microsoft Purview. يمكن أن تختلف متطلبات الترخيص حتى داخل القدرات، اعتمادا على خيارات التكوين. لتحديد متطلبات الترخيص وخياراته، راجع [إرشادات Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="know-your-data"></a>تعرّف على بياناتك

![تعرف على بياناتك لنظرة عامة على حل Microsoft Purview حماية البيانات](../media/knowyourdata-mipsolution.png)

غالبا ما تكون معرفة مكان وجود بياناتك الحساسة أكبر تحد للعديد من المؤسسات. يساعدك تصنيف بيانات Microsoft Purview حماية البيانات على اكتشاف كميات متزايدة من البيانات التي تنشئها مؤسستك وتصنيفها بدقة. تساعدك التمثيلات الرسومية على الحصول على رؤى حول هذه البيانات حتى تتمكن من إعداد النهج ومراقبتها لحمايتها وإدارتها.


|خطوه|الوصف|معلومات إضافية|
|:---|:----------|:---------------|
|1| وصف فئات المعلومات الحساسة التي تريد حمايتها. <br /><br /> لديك بالفعل فكرة عن أنواع المعلومات الأكثر قيمة لمؤسستك والأنواع التي ليست موجودة. اعمل مع أصحاب المصلحة لوصف هذه الفئات لأن هذه هي نقطة البداية الخاصة بك. | [التعرّف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md) <p> [تعرّف على المزيد حول مصنفات قابلة للتدريب](classifier-learn-about.md)|
|2| اكتشاف البيانات الحساسة وتصنيفها. <br /><br /> يمكن العثور على البيانات الحساسة في العناصر باستخدام العديد من الأساليب المختلفة التي تتضمن نهج DLP الافتراضية والتسمية اليدوية من قبل المستخدمين والتعرف التلقائي على الأنماط باستخدام أنواع المعلومات الحساسة أو التعلم الآلي. | [التعرّف على تصنيف البيانات](data-classification-overview.md) <p> [فيديو: تصنيف البيانات في مركز الامتثال](https://www.microsoft.com/videoplayer/embed/RE4vx8x)|
|3| عرض العناصر الحساسة.  <br /><br /> استخدم مستكشف المحتوى ومستكشف النشاط لإجراء تحليل أعمق للعناصر الحساسة والإجراءات التي يتخذها المستخدمون بشأن هذه العناصر.| [بدء استخدام مستكشف المحتوى](data-classification-content-explorer.md) <p> [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)|

## <a name="protect-your-data"></a>حماية بياناتك

![حماية بياناتك لنظرة عامة على حل Microsoft Purview حماية البيانات](../media/protect-mipsolution.png)

استخدم المعلومات من معرفة مكان وجود بياناتك الحساسة لمساعدتك على حمايتها بفعالية أكبر. ولكن لا داعي للانتظار— يمكنك البدء في حماية بياناتك على الفور باستخدام مجموعة من التسميات اليدوية والإفتراضية والتلقائية. ثم استخدم [مستكشف المحتوى](data-classification-content-explorer.md) [ومستكشف النشاط](data-classification-activity-explorer.md) من القسم السابق لتأكيد العناصر التي تم وصفها وكيفية استخدام التسميات.

|خطوه|الوصف|معلومات إضافية|
|:---|-----------|:---------------|
| 1|حدد [أوصاف الحساسية](sensitivity-labels.md) والنهج التي ستحمي بيانات مؤسستك. <br /><br />بالإضافة إلى تحديد حساسية المحتوى، يمكن لهذه التسميات تطبيق إجراءات الحماية، مثل الرؤوس والتذييلات والعلامات المائية والتشفير. | [بدء استخدام تسميات الحساسية](get-started-with-sensitivity-labels.md) <br /><br /> [إنشاء وتكوين تسميات الحساسية ونهجها](create-sensitivity-labels.md) <br /><br /> [تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](encryption-sensitivity-labels.md) |
| 2|تسمية العناصر وحمايتها لتطبيقات وخدمات Microsoft 365. <br /><br />يتم دعم أوصاف الحساسية Microsoft 365 Word Excel PowerPoint Outlook والحاويات التي تتضمن مواقع SharePoint OneDrive ومجموعات Microsoft 365. استخدم مجموعة من أساليب التسمية مثل التسمية اليدوية والتسمية التلقائية والتسمية الافتراضية والتسمية الإلزامية.| [إدارة تسميات الحساسية في تطبيقات Office](sensitivity-labels-office-apps.md) <br /><br /> [تمكين تسميات الحساسية لملفات Office في SharePoint وOneDrive](sensitivity-labels-sharepoint-onedrive-files.md) <br /><br /> [تمكين التأليف المشترك للملفات المشفرة بتسميات الحساسية](sensitivity-labels-coauthoring.md) <br /><br /> [تطبيق تسمية حساسية على المحتوى تلقائياً](apply-sensitivity-label-automatically.md) <br /><br /> [استخدام تسميات الحساسية مع Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint](sensitivity-labels-teams-groups-sites.md) <br /><br /> [استخدم تسميات الحساسية لتعيين ارتباط المشاركة الافتراضي للمواقع والمستندات في SharePoint OneDrive](sensitivity-labels-default-sharing-link.md) <br /><br /> [تطبيق وصف الحساسية على نموذج في Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) <br /><br /> [أوصاف الحساسية في Power BI](/power-bi/admin/service-security-sensitivity-label-overview) |
|3|اكتشف العناصر الحساسة الموجودة في مخازن البيانات في السحابة وقم بتسميتها وحمايتها باستخدام [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) مع تسميات الحساسية الخاصة بك.| [اكتشاف البيانات المنظمة والحساسة المخزنة في السحابة وتصنيفها وتسميتها وحمايتها](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|4|اكتشف العناصر الحساسة الموجودة في مخازن البيانات في أماكن العمل وقم بتسميتها وحمايتها من خلال توزيع [الماسح الضوئي الموحد للوصف في Azure حماية البيانات](/azure/information-protection/deploy-aip-scanner) مع تسميات الحساسية الخاصة بك.| [تكوين الماسح الضوئي الموحد للوصف حماية البيانات Azure وتثبيته](/azure/information-protection/deploy-aip-scanner-configure-install)|
|5|قم بتوسيع تسميات الحساسية الخاصة بك إلى Azure باستخدام [Microsoft Purview Data Map](/azure/purview/overview)، لاكتشاف العناصر وتسميتها ل Azure Blob Storage وملفات Azure Azure Data Lake Storage Gen1 Azure Data Lake Storage Gen12. | [التسمية في Microsoft Purview Data Map](/azure/purview/create-sensitivity-label)|

إذا كنت مطورا يريد توسيع أوصاف الحساسية إلى تطبيقات خط العمل أو تطبيقات SaaS التابعة لجهة خارجية، فراجع [إعداد وتكوين حماية البيانات في Microsoft (MIP) SDK](/information-protection/develop/setup-configure-mip). 

### <a name="additional-protection-capabilities"></a>قدرات حماية إضافية

يتضمن Microsoft Purview قدرات إضافية للمساعدة في حماية البيانات. لا يحتاج كل عميل إلى هذه القدرات، وقد يحل الإصدارات الأحدث محل بعضها.

استخدم صفحة [حماية بياناتك باستخدام Microsoft Purview](information-protection.md) للحصول على القائمة الكاملة لقدرات الحماية.

## <a name="prevent-data-loss"></a>منع فقدان البيانات

![منع فقدان البيانات لنظرة عامة على حل Microsoft Purview حماية البيانات](../media/dlp-mipsolution.png)

نشر نهج Microsoft Purview Data Loss Prevention (DLP) للتحكم ومنع مشاركة البيانات الحساسة أو نقلها أو استخدامها بشكل غير مناسب عبر التطبيقات والخدمات. تساعد هذه النهج المستخدمين على اتخاذ القرارات الصحيحة واتخاذ الإجراءات الصحيحة عند استخدامهم للبيانات الحساسة.

|خطوه|الوصف|معلومات إضافية|
|:---|:----------|:---------------|
|1|تعرف على DLP. <br /><br /> تمتلك المؤسسات معلومات حساسة تحت سيطرتها، مثل البيانات المالية أو البيانات الخاصة أو أرقام بطاقات الائتمان أو السجلات الصحية أو أرقام الضمان الاجتماعي. للمساعدة في حماية هذه البيانات الحساسة وتقليل المخاطر، فإنها تحتاج إلى طريقة لمنع مستخدميها من مشاركتها بشكل غير مناسب مع أشخاص لا ينبغي أن تكون لديهم. تسمى هذه الممارسة منع فقدان البيانات (DLP).| [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)|
|2|تخطيط تنفيذ DLP الخاص بك. <br /><br /> ستخطط كل مؤسسة لمنع فقدان البيانات (DLP) وتنفذه بشكل مختلف، لأن احتياجات كل مؤسسة التجارية وأهدافها ومواردها وحالتها فريدة بالنسبة إليها. ومع ذلك، هناك عناصر شائعة لجميع عمليات تنفيذ DLP الناجحة. | [التخطيط لتفادي فقدان البيانات](dlp-overview-plan-for-dlp.md)|
|3|تصميم نهج DLP وإنشاءه. <br /><br /> يعد إنشاء نهج منع فقدان البيانات (DLP) سريعا وسهلا، ولكن الحصول على نهج لتحقيق النتائج المقصودة يمكن أن يستغرق وقتا طويلا إذا كان عليك القيام بالكثير من الضبط. سيؤدي تخصيص الوقت اللازم لتصميم نهج قبل تنفيذه إلى الحصول على النتائج المرجوة بشكل أسرع، وبمشكلات أقل غير مقصودة، مقارنة بالضبط عن طريق التجربة والخطأ فقط.| [تصميم نهج DLP](dlp-policy-design.md) <p> [مرجع نهج DLP](dlp-policy-reference.md) <p>[إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)|
|4|ضبط نهج DLP الخاصة بك. <br /><br /> بعد نشر نهج DLP، سترى مدى تلبيته للغرض المقصود. استخدم هذه المعلومات لضبط إعدادات النهج للحصول على أداء أفضل. | [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)|


## <a name="training-resources"></a>موارد التدريب

Learning الوحدات النمطية للمستشارين والمسؤولين:

- [مقدمة حول حماية المعلومات والحوكمة في Microsoft 365](/learn/modules/m365-compliance-information-governance)
- [تصنيف البيانات للحماية والحوكمة](/learn/modules/m365-compliance-information-classify-data)
- [حماية المعلومات في Microsoft 365](/learn/modules/m365-compliance-information-protect-information)
- [منع فقدان البيانات في Microsoft 365](/learn/modules/m365-compliance-information-prevent-data-loss)

للمساعدة في تدريب المستخدمين على تطبيق واستخدام تسميات الحساسية التي تقوم بتكوينها لهم، راجع [وثائق المستخدم النهائي لأوصاف الحساسية](get-started-with-sensitivity-labels.md#end-user-documentation-for-sensitivity-labels).

عند نشر نهج منع فقدان البيانات Teams، قد تجد إرشادات المستخدم النهائي التالية مفيدة كمقدمة لهذه التقنية مع بعض الرسائل المحتملة التي قد يرونها: [Teams الرسائل حول منع فقدان البيانات (DLP) ونهج التوافق مع الاتصالات](https://support.microsoft.com/office/teams-messages-about-data-loss-prevention-dlp-and-communication-compliance-policies-c5631c3f-f61b-4306-a6ac-6603d9fc5ff0).
