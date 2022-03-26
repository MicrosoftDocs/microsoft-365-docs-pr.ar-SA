---
title: بدء استخدام تسميات الحساسية
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
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: هل أنت جاهز لنشر تسميات الحساسية للمساعدة في حماية بيانات مؤسستك، ولكنك غير متأكد من مكان البدء؟ اقرأ بعض الإرشادات العملية لمساعدتك على مساعدتك في رحلة وضع التسميات.
ms.openlocfilehash: adc939d44715bcfaeb97cdbfa530f55a5aeecd4e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566815"
---
# <a name="get-started-with-sensitivity-labels"></a>بدء استخدام تسميات الحساسية

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

للحصول على معلومات حول تسميات الحساسية وكيف يمكنها مساعدتك في حماية بيانات مؤسستك، راجع [التعرف على تسميات الحساسية](sensitivity-labels.md).

إذا كان [لديك Azure Information Protection](/azure/information-protection/what-is-information-protection) ولا تزال تستخدم تسميات Azure Information Protection التي كانت مدارة من مدخل Azure، فيجب ترحيل هذه التسميات إلى النظام الأساسي الموحد [للتسمية](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform). بالنسبة Windows الكمبيوتر، [يمكنك اختيار عميل](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) التسمية الذي يجب استخدامه لتسميات الحساسية المنشورة.

عندما تكون جاهزا لبدء حماية بيانات مؤسستك باستخدام تسميات الحساسية:

1. **إنشاء التسميات.** قم بإنشاء تسميات الحساسية الخاصة بك وتسميتها وفقا لتصنيف تصنيف مؤسستك لمستويات حساسية مختلفة من المحتوى. استخدم الأسماء أو المصطلحات الشائعة التي تكون ذات معنى للمستخدمين. إذا لم يكن لديك تصنيف منشأ بالفعل، فقم ببدء أسماء التسميات مثل شخصي و عام و عام و سري و سري للغاية. يمكنك بعد ذلك استخدام التسميات الفرعية في تجميع تسميات مماثلة حسب الفئة. عند إنشاء تسمية، استخدم نص تنقيط الأداة لمساعدة المستخدمين على تحديد التسمية المناسبة.
    
    للحصول على إرشادات أكثر شمولا لتعريف تصنيف التصنيف، قم بتنزيل الورقة البيضاء، "تصنيف البيانات & تصنيف تسمية الحساسية" من [Service Trust Portal](https://aka.ms/DataClassificationWhitepaper).

2. **حدد ما يمكن لكل تسمية القيام به.** قم بتكوين إعدادات الحماية التي تريدها مقترنة بكل تسمية. على سبيل المثال، قد ترغب في تطبيق رأس أو ت السفلي على محتوى الحساسية الأقل (مثل تسمية "عام")، بينما يجب أن يكون لمحتوى الحساسية الأعلى (مثل تسمية "سري") علامة مائية وتشفير.

3. **نشر التسميات.** بعد تكوين تسميات الحساسية، قم بنشرها باستخدام نهج التسمية. تحديد المستخدمين والمجموعات التي يجب أن يكون لها التسميات وإعدادات النهج التي يجب استخدامها. يمكن إعادة استخدام تسمية واحدة— يمكنك تعريفها مرة واحدة، ثم يمكنك تضمينها في العديد من سياسات التسميات المعينة لمستخدمين مختلفين. لذلك، على سبيل المثال، يمكنك استخدام تسميات الحساسية من خلال تعيين نهج تسمية إلى عدد قليل من المستخدمين فقط. بعد ذلك، عندما تكون جاهزا ل طرح التسميات عبر مؤسستك، يمكنك إنشاء نهج تسميات جديد للتسميات وفي هذه المرة، حدد جميع المستخدمين.


> قد تكون مؤهلا لإنشاء تسميات افتراضية تلقائيا ون نهج تسمية افتراضي يعتني بالخطوات من 1 إلى 3 من أجلك. لمزيد من المعلومات، راجع [التسميات الافتراضية ونهج حماية البيانات في Microsoft](mip-easy-trials.md).

التدفق الأساسي لنشر تسميات الحساسية وتطبيقها:

![رسم تخطيطي يعرض سير العمل لتسميات الحساسية.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>متطلبات الاشتراك والترخيص لتسميات الحساسية

يدعم عدد من الاشتراكات المختلفة تسميات الحساسية وتعتمد متطلبات الترخيص للمستخدمين على الميزات التي تستخدمها.

لمعرفة خيارات ترخيص المستخدمين للاستفادة من Microsoft 365 التوافق، راجع Microsoft 365 إرشادات ترخيص الأمان & [التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). للحصول على تسميات الحساسية، راجع القسم حماية المعلومات [: تسمية](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-sensitivity-labeling) الحساسية وتنزيل [PDF](https://go.microsoft.com/fwlink/?linkid=2139145) ذي الصلة لمتطلبات الترخيص على مستوى الميزات.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>الأذونات المطلوبة لإنشاء أوصاف الحساسية وإدارتها

يحتاج أعضاء فريق التوافق الذين سينشئون تسميات الحساسية إلى أذونات مركز التوافق في Microsoft 365.

بشكل افتراضي، يمكن للمسؤولين العامين للمستأجر الوصول إلى مركز الإدارة هذا ويمكنهم منح مسؤولي التوافق و الأشخاص الآخرين حق الوصول، دون منحهم كل الأذونات من مسؤول المستأجر. بالنسبة إلى وصول المسؤول المحدود المفوض هذا، أضف مستخدمين إلى مجموعة دور مسؤول **بيانات** التوافق أو مسؤول **التوافق أو مسؤول** الأمان. 

بدلا من استخدام الأدوار الافتراضية، يمكنك إنشاء مجموعة أدوار جديدة وإضافة إما مسؤول تسمية الحساسية أو أدوار  تكوين المؤسسة إلى هذه المجموعة. للحصول على دور للقراءة فقط، استخدم **قارئ تسميات الحساسية**. 

> [!NOTE]
> الآن في المعاينة، يمكنك استخدام مجموعات الدور التالية:
> - **حماية المعلومات**
> - **مسؤولو حماية المعلومات**
> - **محللو حماية المعلومات**
> - **الباحثون عن حماية المعلومات**
> - **قراء حماية المعلومات**
>
> للحصول على شرح لكل واحد منها، والأدوار الجديدة التي تحتوي عليها، حدد مجموعة أدوار في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a> >  **الأدوار &** >  >  مركز المشاركة **،** ثم راجع الوصف في جزء القائمة المن القائمة المنير. أو، [راجع مجموعات الدور في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

للحصول على إرشادات لإضافة مستخدمين إلى مجموعة الأدوار الافتراضية أو الأدوار أو إنشاء مجموعات أدوار خاصة بك، راجع الأذونات [في](microsoft-365-compliance-center-permissions.md) مركز التوافق في Microsoft 365.

هذه الأذونات مطلوبة فقط لإنشاء تسميات الحساسية ونهج التسميات الخاصة بها وتكوينها. ولا يطلب منها تطبيق التسميات في التطبيقات أو الخدمات. إذا كانت هناك حاجة إلى أذونات إضافية لتكوينات معينة ذات صلة ملصقات الحساسية، سيتم إدراج هذه الأذونات في إرشادات الوثائق الخاصة بها.

## <a name="deployment-strategy-for-sensitivity-labels"></a>استراتيجية النشر لتسميات الحساسية
استراتيجية ناجحة لنشر تسميات الحساسية في مؤسسة ما هي إنشاء فريق ظاهري يعمل على تحديد متطلبات العمل والمتطلبات التقنية وإدارتها، وإثبات اختبار المفاهيم، ونقاط الفحص والموافقات الداخلية، والنشر النهائي لبيئة الإنتاج.

باستخدام الجدول في المقطع التالي، نوصي بتحديد سيناريو واحد أو اثنين من أهم السيناريوهات التي تحدد متطلبات العمل الأكثر تأثيرا. بعد نشر هذه السيناريوهات، ارجع إلى القائمة لتحديد الأول أو الأولويتين التاليتين للنشر.

ستجد إرشادات نشر عامة إضافية وأفضل الممارسات في دليل تسريع النشر ل حماية البيانات في Microsoft [](https://microsoft.github.io/ComplianceCxE/dag/mip-dlp/)البيانات ومنع فقدان البيانات، وهو أحد الموارد من موقع فريق تسريع العملاء [(CAT](https://microsoft.github.io/ComplianceCxE/)).

## <a name="common-scenarios-for-sensitivity-labels"></a>السيناريوهات الشائعة لتسميات الحساسية

تتطلب كل السيناريوهات إنشاء تسميات الحساسية ونهجها [وتكوينها](create-sensitivity-labels.md).

|أريد...|الوثائق|
|----------------|---------------|
|إدارة تسميات الحساسية لتطبيقات Office بحيث يتم تسمية المحتوى عند إنشائه، بما في ذلك دعم التسميات اليدوية على كل الأنظمة الأساسية |[إدارة تسميات الحساسية في تطبيقات Office](sensitivity-labels-office-apps.md)|
|توسيع التسمية إلى "مستكشف الملفات" و PowerShell، مع ميزات إضافية لتطبيقات Office على Windows (إذا لزم الأمر)|[عميل التسمية الموحد في Azure Information Protection Windows](/azure/information-protection/rms-client/aip-clientv2)|
|تشفير المستندات ورسائل البريد الإلكتروني باستخدام تسميات الحساسية وتقييد الأشخاص الذين يمكنهم الوصول إلى هذا المحتوى وكيفية استخدامه |[تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](encryption-sensitivity-labels.md)|
|تمكين تسميات الحساسية Office على الويب، مع دعم المشاركة في التسمية، و eDiscovery، ومنع فقدان البيانات، والبحث، حتى عندما تكون المستندات مشفرة | [تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|استخدام التأليف المشترك وال حفظ تلقائي في تطبيقات Office سطح المكتب عند تشفير المستندات | [تمكين التأليف المشترك للملفات المشفرة باستخدام تسميات الحساسية](sensitivity-labels-coauthoring.md)
|تطبيق تسميات الحساسية تلقائيا على المستندات ورسائل البريد الإلكتروني | [تطبيق تسمية حساسية على المحتوى تلقائيا](apply-sensitivity-label-automatically.md)|
|استخدم تسميات الحساسية لحماية المحتوى في Teams SharePoint |[استخدام تسميات الحساسية مع Microsoft Teams Microsoft 365 ومجموعات SharePoint ويب](sensitivity-labels-teams-groups-sites.md)|
|استخدم تسميات الحساسية لتكوين نوع ارتباط المشاركة الافتراضي للمواقع والمستندات الفردية في SharePoint OneDrive |[استخدم تسميات الحساسية لتعيين ارتباط المشاركة الافتراضي للمواقع والمستندات في SharePoint OneDrive](sensitivity-labels-default-sharing-link.md)|
|تطبيق تسمية حساسية على نموذج فهم المستندات، بحيث يتم تصنيف المستندات المحددة في مكتبة SharePoint تلقائيا وحمايتها |[تطبيق تسمية حساسية على نموذج في Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|منع المستخدمين من مشاركة الملفات أو رسائل البريد الإلكتروني باستخدام تسمية حساسية معينة أو تحذيرهم |[استخدام تسميات الحساسية كالشروط في سياسات DLP](dlp-sensitivity-label-as-condition.md) |
|تطبيق تسمية استبقاء للاحتفاظ بالملفات أو رسائل البريد الإلكتروني التي لها تسمية حساسية معينة أو حذفها|[تطبيق تسمية استبقاء تلقائيا للاحتفاظ بالمحتوى أو حذفه](apply-retention-labels-automatically.md) |
|اكتشاف الملفات المخزنة في مخازن البيانات المحلية وتسميتها وحمايتها |[نشر ماسح حماية المعلومات من Azure لتصنيف الملفات وحمايتها تلقائيا](/azure/information-protection/deploy-aip-scanner)|
|اكتشاف الملفات المخزنة في مخازن البيانات الموجودة في السحابة وتسميتها وحمايتها|[اكتشاف البيانات المنظمة والحساسة المخزنة في السحابة وتصنيفها وتسميتها وحمايتها](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|تطبيق التسميات وعرضها في Power BI، وحماية البيانات عند حفظها خارج الخدمة|[تسميات الحساسية في Power BI](/power-bi/admin/service-security-sensitivity-label-overview)|
|مراقبة وفهم كيفية استخدام تسميات الحساسية في المؤسسة|[التعرف على تصنيف البيانات](data-classification-overview.md)|
|توسيع تسميات الحساسية إلى تطبيقات وخدمات  الأطراف الخارجية|[حماية البيانات في Microsoft SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|توسيع تسميات الحساسية عبر المحتوى في أصول Azure Purview، مثل Azure Blob Storage و Azure Files و Azure Data Lake Storage ومصادر البيانات متعددة السحابة|[وضع التسميات في Azure Purview](/azure/purview/create-sensitivity-label) |


## <a name="end-user-documentation-for-sensitivity-labels"></a>وثائق المستخدم النهائي لتسميات الحساسية

ستكون وثائق المستخدم النهائي الأكثر فعالية هي الإرشادات والإرشادات المخصصة التي تقدمها لأسماء التسميات والتكوينات التي تختارها. يمكنك استخدام إعداد نهج التسمية **قم** بتوفير ارتباط إلى صفحة تعليمات مخصصة للمستخدمين لتحديد ارتباط داخلي لهذه الوثائق. يمكن للمستخدمين الوصول إليها بسهولة من **الزر الحساسية** :

- للتسمية المضمنة: **خيار القائمة معرفة** المزيد.
- بالنسبة إلى عميل التسمية الموحد في Azure Information Protection: **خيار** قائمة "تعليمات وملاحظات" >  الارتباط "أخبرني المزيد" في مربع الحوار Microsoft Azure Information Protection.

لمساعدتك على توفير الوثائق المخصصة، راجع الصفحة التالية والتنزيلها التي يمكنك استخدامها للمساعدة في تدريب المستخدمين: تدريب المستخدم النهائي لتسميات [الحساسية](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

يمكنك أيضا استخدام الموارد التالية للحصول على الإرشادات الأساسية:

- [تطبيق أوصاف الحساسية على ملفاتك وبريدك الإلكتروني في Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [المشاكل المعروفة مع تسميات الحساسية في Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [تطبيق أو التوصية بتسميات الحساسية تلقائيا على ملفاتك ورسائل البريد الإلكتروني في Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [المشاكل المعروفة المتعلقة بتطبيق أو التوصية بتسميات الحساسية تلقائيا](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [دليل المستخدم الموحد لتسمية Azure Information Protection](/azure/information-protection/rms-client/clientv2-user-guide)

إذا كانت تسميات الحساسية تطبق التشفير لمستندات PDF، يمكن فتح هذه المستندات باستخدام Microsoft Edge على Windows أو Mac. لمزيد من المعلومات، والقراء البديلين، راجع ما هي قراء PDF المعتمدة [لمستندات PDF المحمية؟](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
