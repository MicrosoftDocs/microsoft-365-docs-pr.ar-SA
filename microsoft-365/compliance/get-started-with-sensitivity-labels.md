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
description: هل أنت مستعد لنشر أوصاف الحساسية للمساعدة في حماية بيانات مؤسستك، ولكن لست متأكدا من مكان البدء؟ اقرأ بعض الإرشادات العملية لمساعدتك في رحلة التسمية.
ms.openlocfilehash: f27f1a475f5880058db40894015dabdec9038be1
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286023"
---
# <a name="get-started-with-sensitivity-labels"></a>بدء استخدام تسميات الحساسية

>*[Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

للحصول على معلومات حول تسميات الحساسية وكيف يمكن أن تساعدك على حماية بيانات مؤسستك، راجع [التعرف على تسميات الحساسية](sensitivity-labels.md).

إذا كان لديك [Azure حماية البيانات](/azure/information-protection/what-is-information-protection) ولا تزال تستخدم تسميات Azure حماية البيانات التي تمت إدارتها من مدخل Microsoft Azure، يجب ترحيل هذه التسميات إلى [النظام الأساسي الموحد للتسميات](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform). بالنسبة لأجهزة الكمبيوتر Windows، يمكنك [بعد ذلك اختيار عميل التسمية الذي يجب استخدامه](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) لتسميات الحساسية المنشورة.

عندما تكون مستعدا لبدء حماية بيانات مؤسستك باستخدام أوصاف الحساسية:

1. **إنشاء التسميات.** قم بإنشاء تسميات الحساسية الخاصة بك وتسميتها وفقا لتصنيف تصنيف مؤسستك لمستويات حساسية مختلفة من المحتوى. استخدم الأسماء أو المصطلحات الشائعة المنطقية للمستخدمين. إذا لم يكن لديك تصنيف ثابت بالفعل، ففكر في البدء بأسماء التسميات مثل "شخصي" و"عام" و"عام" و"سري" و"سري للغاية". يمكنك بعد ذلك استخدام الأوصاف الفرعية لتجميع تسميات مشابهة حسب الفئة. عند إنشاء تسمية، استخدم نص تعريف الأدوات لمساعدة المستخدمين على تحديد التسمية المناسبة.
    
    للحصول على إرشادات أكثر شمولا لتحديد تصنيف التصنيف، قم بتنزيل الورقة البيضاء، "تصنيف البيانات & تصنيف وصف الحساسية" من [Service Trust Portal](https://aka.ms/DataClassificationWhitepaper).

2. **حدد ما يمكن أن تفعله كل تسمية.** تكوين إعدادات الحماية التي تريد إقرانها بكل تسمية. على سبيل المثال، قد ترغب في تطبيق محتوى حساسية أقل (مثل تسمية "عام") على رأس أو تذييل فقط، بينما يجب أن يحتوي محتوى الحساسية الأعلى (مثل التسمية "سري") على علامة مائية وتشفير.

3. **نشر التسميات.** بعد تكوين تسميات الحساسية الخاصة بك، انشرها باستخدام نهج التسمية. حدد المستخدمين والمجموعات التي يجب أن تحتوي على التسميات وإعدادات النهج التي يجب استخدامها. التسمية الواحدة قابلة لإعادة الاستخدام— يمكنك تعريفها مرة واحدة، ثم يمكنك تضمينها في العديد من نهج التسمية المعينة لمستخدمين مختلفين. لذلك على سبيل المثال، يمكنك تجربة تسميات الحساسية الخاصة بك عن طريق تعيين نهج تسمية لعدد قليل من المستخدمين. ثم عندما تكون جاهزا لنشر التسميات عبر مؤسستك، يمكنك إنشاء نهج تسميات جديد للتسميات الخاصة بك وهذه المرة، حدد جميع المستخدمين.


> قد تكون مؤهلا للإنشاء التلقائي للتسميات الافتراضية ونهج التسميات الافتراضي الذي يعتني بالخطوات من 1 إلى 3 لك. لمزيد من المعلومات، راجع [التسميات والنهج الافتراضية ل Microsoft Purview حماية البيانات](mip-easy-trials.md).

التدفق الأساسي لنشر أوصاف الحساسية وتطبيقها:

![رسم تخطيطي يوضح سير العمل لأوصاف الحساسية.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>متطلبات الاشتراك والترخيص لأوصاف الحساسية

يعتمد عدد من الاشتراكات المختلفة تسميات الحساسية ومتطلبات الترخيص للمستخدمين على الميزات التي تستخدمها.

للاطلاع على خيارات ترخيص المستخدمين للاستفادة من ميزات Microsoft Purview، راجع [إرشادات ترخيص Microsoft 365 للأمان & التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). للحصول على تسميات الحساسية، راجع [حماية البيانات Microsoft Purview: قسم وصف الحساسية](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-information-protection-sensitivity-labeling) [وتنزيل PDF](https://go.microsoft.com/fwlink/?linkid=2139145) ذي الصلة لمتطلبات الترخيص على مستوى الميزات.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>الأذونات المطلوبة لإنشاء أوصاف الحساسية وإدارتها

يحتاج أعضاء فريق الامتثال الذين سينشئون تسميات الحساسية إلى أذونات لمدخل الامتثال ل Microsoft Purview.

بشكل افتراضي، يمكن للمسؤولين العموميين للمستأجر الوصول إلى مركز الإدارة هذا ويمكنهم منح مسؤولي الامتثال والأشخاص الآخرين حق الوصول، دون منحهم جميع أذونات مسؤول المستأجر. للحصول على وصول مسؤول محدود مفوض، أضف مستخدمين إلى مجموعة دور **مسؤول بيانات التوافق** أو **مسؤول التوافق** أو **مسؤول الأمان** . 

بدلا من استخدام الأدوار الافتراضية، يمكنك إنشاء مجموعة أدوار جديدة وإضافة أدوار مسؤول **وصف الحساسية** أو **تكوين المؤسسة** إلى هذه المجموعة. للحصول على دور للقراءة فقط، استخدم **قارئ وصف الحساسية**. 

> [!NOTE]
> الآن في المعاينة، يمكنك استخدام مجموعات الأدوار التالية:
> - **حماية البيانات**
> - **مسؤولو حماية البيانات**
> - **حماية البيانات المحللين**
> - **المحققون حماية البيانات**
> - **قارئات حماية البيانات**
>
> للحصول على شرح لكل منها، والأدوار الجديدة التي تحتوي عليها، حدد مجموعة أدوار في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل توافق</a> >  Microsoft Purview **& roleCompliance** >  **centerRoles** > ، ثم راجع الوصف في جزء القائمة المنبثقة. أو راجع [مجموعات الأدوار في Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

للحصول على إرشادات لإضافة مستخدمين إلى مجموعة الأدوار الافتراضية أو الأدوار أو إنشاء مجموعات الأدوار الخاصة بك، راجع [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md).

هذه الأذونات مطلوبة فقط لإنشاء وتكوين تسميات الحساسية ونهج التسميات الخاصة بها. وهي غير مطلوبة لتطبيق التسميات في التطبيقات أو الخدمات. إذا كانت هناك حاجة إلى أذونات إضافية لتكوينات معينة تتعلق بتسميات الحساسية، فسيتم سرد هذه الأذونات في تعليمات الوثائق الخاصة بها.

## <a name="deployment-strategy-for-sensitivity-labels"></a>استراتيجية التوزيع لأوصاف الحساسية
تتمثل الاستراتيجية الناجحة لنشر تسميات الحساسية للمؤسسة في إنشاء فريق ظاهري عامل يحدد ويدير متطلبات الأعمال والمتطلبات التقنية، وإثبات اختبار المفهوم، ونقاط التحقق الداخلية والموافقات، والنشر النهائي لبيئة الإنتاج.

باستخدام الجدول في القسم التالي، نوصي بتحديد أفضل سيناريو أو سيناريوهين يحددان متطلبات عملك الأكثر تأثيرا. بعد نشر هذه السيناريوهات، ارجع إلى القائمة لتحديد أولويات النشر التالية أو أولوياتها.

## <a name="common-scenarios-for-sensitivity-labels"></a>السيناريوهات الشائعة لأوصاف الحساسية

تتطلب منك جميع السيناريوهات [إنشاء وتكوين تسميات الحساسية ونهجها](create-sensitivity-labels.md).

|أريد...|الوثائق|
|----------------|---------------|
|إدارة أوصاف الحساسية لتطبيقات Office بحيث يتم تسمية المحتوى عند إنشائه— بما في ذلك دعم التسمية اليدوية على جميع الأنظمة الأساسية |[إدارة تسميات الحساسية في تطبيقات Office](sensitivity-labels-office-apps.md)|
|توسيع التسمية إلى مستكشف الملفات وPowerShell، مع ميزات إضافية لتطبيقات Office على Windows (إذا لزم الأمر)|[عميل تسمية موحد حماية البيانات Azure Windows](/azure/information-protection/rms-client/aip-clientv2)|
|تشفير المستندات ورسائل البريد الإلكتروني باستخدام تسميات الحساسية وتقييد الأشخاص الذين يمكنهم الوصول إلى هذا المحتوى وكيفية استخدامه |[تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](encryption-sensitivity-labels.md)|
|تمكين أوصاف الحساسية Office على الويب، مع دعم التأليف المشترك، eDiscovery، منع فقدان البيانات، البحث - حتى عندما يتم تشفير المستندات | [تمكين تسميات الحساسية لملفات Office في SharePoint وOneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|استخدام التأليف المشترك والحفظ التلقائي في تطبيقات سطح المكتب Office عند تشفير المستندات | [تمكين التأليف المشترك للملفات المشفرة بتسميات الحساسية](sensitivity-labels-coauthoring.md)
|تطبيق أوصاف الحساسية تلقائيا على المستندات ورسائل البريد الإلكتروني | [تطبيق تسمية حساسية على المحتوى تلقائياً](apply-sensitivity-label-automatically.md)|
|استخدام تسميات الحساسية لحماية المحتوى في Teams SharePoint |[استخدام تسميات الحساسية مع Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint](sensitivity-labels-teams-groups-sites.md)|
|استخدم تسميات الحساسية لتكوين نوع ارتباط المشاركة الافتراضي للمواقع والمستندات الفردية في SharePoint OneDrive |[استخدم تسميات الحساسية لتعيين ارتباط المشاركة الافتراضي للمواقع والمستندات في SharePoint OneDrive](sensitivity-labels-default-sharing-link.md)|
|تطبيق وصف الحساسية على نموذج فهم المستندات، بحيث يتم تصنيف المستندات المحددة في مكتبة SharePoint وحمايتها تلقائيا |[تطبيق وصف الحساسية على نموذج في Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|منع المستخدمين من مشاركة الملفات أو رسائل البريد الإلكتروني أو تحذيرهم باستخدام وصف حساسية معين |[استخدام تسميات الحساسية كشروط في نهج DLP](dlp-sensitivity-label-as-condition.md) |
|تطبيق وصف الحساسية على ملف عندما أتلقى تنبيها بأن المحتوى الذي يحتوي على بيانات شخصية تتم مشاركته ويحتاج إلى الحماية| [التحقيق في التنبيهات ومعالجتها في إدارة مخاطر الخصوصية](/privacy/priva/risk-management-alerts)|
|تطبيق تسمية استبقاء للاحتفاظ بالملفات أو رسائل البريد الإلكتروني التي تحتوي على وصف حساسية معين أو حذفها|[تطبيق تسمية استبقاء تلقائيا للاحتفاظ بالمحتوى أو حذفه](apply-retention-labels-automatically.md) |
|اكتشاف الملفات المخزنة في مخازن البيانات المحلية وتسميتها وحمايتها |[نشر الماسح الضوئي ل Azure حماية البيانات لتصنيف الملفات وحمايتها تلقائيا](/azure/information-protection/deploy-aip-scanner)|
|اكتشاف الملفات المخزنة في مخازن البيانات الموجودة في السحابة وتسميتها وحمايتها|[اكتشاف البيانات المنظمة والحساسة المخزنة في السحابة وتصنيفها وتسميتها وحمايتها](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|تسمية SQL أعمدة قاعدة البيانات باستخدام نفس تسميات الحساسية المستخدمة للملفات ورسائل البريد الإلكتروني بحيث يكون لدى المؤسسة حل تسمية موحد يمكنه الاستمرار في حماية هذه البيانات المنظمة عند تصديرها |[Data Discovery & Classification for Azure SQL Database وAzure SQL Managed Instance وAzure Synapse Analytics](/azure/azure-sql/database/data-discovery-and-classification-overview) <br /><br /> [SQL اكتشاف البيانات وتصنيفها SQL Server المحلي](/sql/relational-databases/security/sql-data-discovery-and-classification)|
|تطبيق التسميات وعرضها في Power BI، وحماية البيانات عند حفظها خارج الخدمة|[أوصاف الحساسية في Power BI](/power-bi/admin/service-security-sensitivity-label-overview)|
|مراقبة وفهم كيفية استخدام أوصاف الحساسية في مؤسستي|[التعرّف على تصنيف البيانات](data-classification-overview.md)|
|توسيع أوصاف الحساسية لتشمل تطبيقات وخدمات الجهات الخارجية|[حماية البيانات في Microsoft SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|توسيع تسميات الحساسية عبر المحتوى في أصول Microsoft Purview Data Map، مثل Azure Blob Storage وAzure Files Azure Data Lake Storage ومصادر البيانات متعددة السحابة|[التسمية في Microsoft Purview Data Map](/azure/purview/create-sensitivity-label) |

## <a name="end-user-documentation-for-sensitivity-labels"></a>وثائق المستخدم النهائي لأوصاف الحساسية

ستكون وثائق المستخدم النهائي الأكثر فعالية إرشادات وتعليمات مخصصة توفرها لأسماء التسميات والتكوينات التي تختارها. يمكنك استخدام إعداد نهج التسمية **لتزويد المستخدمين بارتباط إلى صفحة تعليمات مخصصة** لتحديد ارتباط داخلي لهذه الوثائق. يمكن للمستخدمين بعد ذلك الوصول إليها بسهولة من زر **الحساسية** :

- للتسمية المضمنة: خيار القائمة **"معرفة المزيد** ".
- بالنسبة لعميل التسمية الموحد ل Azure حماية البيانات: خيار قائمة **التعليمات والملاحظات** > ارتباط **"أخبرني المزيد"** في مربع الحوار "microsoft Azure حماية البيانات".

لمساعدتك على توفير الوثائق المخصصة، راجع الصفحة التالية والتنزيلات التي يمكنك استخدامها للمساعدة في تدريب المستخدمين: [التدريب على المستخدم النهائي لأوصاف الحساسية](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

يمكنك أيضا استخدام الموارد التالية للحصول على التعليمات الأساسية:

- [تطبيق أوصاف الحساسية على ملفاتك وبريدك الإلكتروني في Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [المشاكل المعروفة المتعلقة بتسميات الحساسية في Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [تطبيق تسميات الحساسية أو التوصية بها تلقائيا على ملفاتك ورسائل البريد الإلكتروني في Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [المشاكل المعروفة المتعلقة بتطبيق أوصاف الحساسية أو التوصية بها تلقائيا](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [دليل مستخدم التسمية الموحد ل Azure حماية البيانات](/azure/information-protection/rms-client/clientv2-user-guide)

إذا كانت تسميات الحساسية تطبق التشفير على مستندات PDF، يمكن فتح هذه المستندات باستخدام Microsoft Edge على Windows أو Mac. لمزيد من المعلومات، والقراء البديلين، راجع [ما هي برامج قراءة PDF المعتمدة لملفات PDF المحمية؟](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
