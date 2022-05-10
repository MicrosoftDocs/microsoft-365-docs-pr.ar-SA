---
title: Microsoft Purview حماية البيانات
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-mip
- m365initiative-compliance
recommendations: false
description: تنفيذ قدرات Microsoft Purview حماية البيانات لمساعدتك على حماية المعلومات الحساسة أينما كانت تعيش أو تنتقل.
ms.openlocfilehash: 97f5172479d889ec1914cfc46102a58a83165269
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285467"
---
# <a name="protect-your-sensitive-data-with-microsoft-purview"></a>حماية بياناتك الحساسة باستخدام Microsoft Purview

>*[ترخيص توافق & الأمان Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!TIP]
> *هل تعلم أنه يمكنك تجربة الإصدارات المتميزة من جميع حلول Microsoft Purview التسعة مجانا؟* استخدم تجربة حلول Purview لمدة 90 يوما لاستكشاف مدى قدرة قدرات Purview القوية على مساعدة مؤسستك على تلبية احتياجات التوافق الخاصة بها. يمكن للعملاء Microsoft 365 E3 Office 365 E3 البدء الآن في [مركز تجارب مدخل الامتثال ل Microsoft Purview](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). تعرف على تفاصيل حول [الأشخاص الذين يمكنهم التسجيل وشروط الإصدار التجريبي](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تنفيذ قدرات **من Microsoft Purview حماية البيانات** (سابقا حماية البيانات في Microsoft) لمساعدتك على اكتشاف المعلومات الحساسة وتصنيفها وحمايتها أينما كانت تعيش أو تنتقل.

تمنحك قدرات حماية المعلومات هذه الأدوات [اللازمة للتعرف](#know-your-data) على بياناتك [، وحماية بياناتك](#protect-your-data)، [ومنع فقدان البيانات](#prevent-data-loss).

![صورة لكيفية مساعدة Microsoft Purview حماية البيانات في اكتشاف البيانات الحساسة وتصنيفها وحمايتها.](../media/powered-by-intelligent-platform.png)

للحصول على إرشادات توجيهية لنشر حل microsoft Purview حماية البيانات لمؤسستك، راجع [نشر حل حماية المعلومات باستخدام Microsoft Purview](information-protection-solution.md).

للحصول على معلومات حول التحكم في بياناتك، راجع [إدارة بياناتك باستخدام Microsoft Purview](manage-Information-governance.md).

## <a name="know-your-data"></a>تعرّف على بياناتك

لفهم مشهد البيانات وتحديد البيانات الحساسة عبر بيئتك المختلطة، استخدم القدرات التالية:

|القدره|ما هي المشاكل التي تحلها؟|بدء الاستخدام|
|:------|:------------|:--------------------|
|[أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md)| تحديد البيانات الحساسة باستخدام تعبيرات عادية مضمنة أو مخصصة أو دالة. تتضمن الأدلة المتوافقة الكلمات الأساسية ومستويات الثقة والتقارب.| [تخصيص نوع معلومات حساسة مضمن](customize-a-built-in-sensitive-information-type.md)|
|[مصنفات قابلة للتدريب](classifier-learn-about.md)| تحديد البيانات الحساسة باستخدام أمثلة على البيانات التي تهتم بها بدلا من تحديد العناصر في العنصر (مطابقة النمط). يمكنك استخدام المصنفات المضمنة أو تدريب مصنف باستخدام المحتوى الخاص بك.| [بدء استخدام المصنفات القابلة للتدريب](classifier-get-started-with.md) |
|[تصنيف البيانات](data-classification-overview.md) | تعريف رسومي للعناصر في مؤسستك التي تحتوي على وصف حساسية أو تسمية استبقاء أو تم تصنيفها. يمكنك أيضا استخدام هذه المعلومات للحصول على رؤى حول الإجراءات التي يتخذها المستخدمون على هذه العناصر. | [بدء استخدام مستكشف المحتوى](data-classification-content-explorer.md) <p> [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>حماية بياناتك

لتطبيق إجراءات الحماية المرنة التي تتضمن التشفير وقيود الوصول والعلامات المرئية، استخدم القدرات التالية:

|القدره|ما هي المشاكل التي تحلها؟|بدء الاستخدام|
|:------|:------------|---------------------|
|[تسميات الحساسية](sensitivity-labels.md)| حل واحد عبر التطبيقات والخدمات والأجهزة لتسمية بياناتك وحمايتها أثناء انتقالها داخل مؤسستك وخارجها. <br /><br /> أمثلة على السيناريوهات: <br />- [إدارة أوصاف الحساسية لتطبيقات Office](sensitivity-labels-office-apps.md) <br />- [تشفير المستندات ورسائل البريد الإلكتروني](encryption-sensitivity-labels.md) <br />-  [تطبيق التسميات وعرضها في Power BI](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> للحصول على قائمة شاملة بسيناريوهات تسميات الحساسية، راجع وثائق بدء الاستخدام.|[بدء استخدام تسميات الحساسية](get-started-with-sensitivity-labels.md) |
|[عميل تسمية موحد حماية البيانات Azure](/azure/information-protection/rms-client/aip-clientv2)| بالنسبة لأجهزة الكمبيوتر Windows، يتم توسيع التسمية إلى مستكشف الملفات وPowerShell، مع ميزات إضافية لتطبيقات Office إذا لزم الأمر| [دليل مسؤول عميل التسمية الموحد ل Azure حماية البيانات](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[تشفير المفتاح المزدوج](double-key-encryption.md)| في جميع الظروف، يمكن لمؤسستك فقط فك تشفير المحتوى المحمي أو للمتطلبات التنظيمية، يجب أن تحمل مفاتيح التشفير داخل حدود جغرافية. | [توزيع تشفير المفتاح المزدوج](double-key-encryption.md#deploy-dke)|
|[تشفير رسائل Office 365 (OME)](ome.md)| تشفير رسائل البريد الإلكتروني والمستندات المرفقة التي يتم إرسالها إلى أي مستخدم على أي جهاز، بحيث يمكن للمستلمين المعتمدين فقط قراءة المعلومات المرسلة بالبريد الإلكتروني. <br /><br />  سيناريو المثال: [إبطال البريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدم](revoke-ome-encrypted-mail.md) | [إعداد قدرات جديدة لتشفير الرسائل](set-up-new-message-encryption-capabilities.md)|
|[تشفير الخدمة باستخدام مفتاح العميل](customer-key-overview.md) | يحمي من عرض البيانات من قبل الأنظمة أو الموظفين غير المصرح لهم، ويكمل تشفير قرص BitLocker في مراكز بيانات Microsoft. | [إعداد مفتاح العميل Office 365](customer-key-set-up.md)|
|[SharePoint إدارة حقوق استخدام المعلومات (IRM)](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|يحمي SharePoint القوائم والمكتبات بحيث يكون الملف الذي تم تنزيله محميا عندما يقوم المستخدم بسحب مستند حتى يتمكن الأشخاص المخولون فقط من عرض الملف واستخدامه وفقا للنهج التي تحددها. | [إعداد إدارة حقوق المعلومات (IRM) في مركز إدارة SharePoint](set-up-irm-in-sp-admin-center.md)|
[موصل إدارة الحقوق](/azure/information-protection/deploy-rms-connector) |الحماية فقط لعمليات النشر المحلية الحالية التي تستخدم خادم Exchange أو SharePoint، أو خوادم الملفات التي تعمل Windows الخادم والبنية الأساسية لتصنيف الملفات (FCI). | [خطوات لنشر موصل RMS](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[الماسح الضوئي الموحد للوصف حماية البيانات Azure](/azure/information-protection/deploy-aip-scanner)| اكتشاف المعلومات الحساسة الموجودة في مخازن البيانات المحلية وتسمياتها وحمايتها. | [تكوين الماسح الضوئي الموحد للوصف حماية البيانات Azure وتثبيته](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)| اكتشاف المعلومات الحساسة الموجودة في مخازن البيانات الموجودة في السحابة وتسمياتها وحمايتها. | [اكتشاف البيانات المنظمة والحساسة المخزنة في السحابة وتصنيفها وتسميتها وحمايتها](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Microsoft Purview Data Map](/azure/purview/overview) |تحديد البيانات الحساسة وتطبيق التسمية التلقائية على المحتوى في أصول Microsoft Purview Data Map. وتشمل هذه الملفات في التخزين مثل Azure Data Lake وAzure Files والبيانات المخططة مثل الأعمدة في Azure SQL DB وCosmos DB. |[التسمية في Microsoft Purview Data Map](/azure/purview/create-sensitivity-label) |
|[حماية البيانات في Microsoft SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|توسيع تسميات الحساسية لتشمل تطبيقات وخدمات الجهات الخارجية. <br /><br />  مثال على السيناريو: [تعيين تسمية الحساسية والحصول عليها (C++)](/information-protection/develop/quick-file-set-get-label-cpp) |[إعداد عدة تطوير برامج حماية البيانات في Microsoft (MIP) وتكوينها](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>منع فقدان البيانات

للمساعدة في منع الإفراط في المشاركة العرضية للمعلومات الحساسة، استخدم القدرات التالية:


|القدره|ما هي المشاكل التي تحلها؟|بدء الاستخدام|
|:------|:------------|:---------------------|
|[منع فقدان بيانات Microsoft Purview](dlp-learn-about-dlp.md)| يساعد على منع المشاركة غير المقصودة للعناصر الحساسة. | [بدء استخدام نهج DLP الافتراضي](get-started-with-the-default-dlp-policy.md)|
|[منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)| توسيع قدرات DLP إلى العناصر المستخدمة والمشتركة على أجهزة الكمبيوتر Windows 10. | [للحصول على متطلبات إضافية لنشر Endpoint DLP، راجع البدء في تفادي فقدان البيانات على الأجهزة.](endpoint-dlp-getting-started.md)|
|[ملحق الامتثال ل Microsoft](dlp-chrome-learn-about.md) | توسيع قدرات DLP إلى مستعرض Chrome | [بدء العمل باستخدام ملحق التوافق من Microsoft](dlp-chrome-get-started.md)|
|[الماسح الضوئي المحلي لمنع فقدان بيانات Microsoft Purview (معاينة)](dlp-on-premises-scanner-learn.md)|توسيع مراقبة DLP لأنشطة الملفات وإجراءات الحماية لتلك الملفات إلى مشاركات الملفات المحلية ومجلدات SharePoint ومكتبات المستندات.|[بدء استخدام الماسح الضوئي المحلي لمنع فقدان بيانات Microsoft Purview (معاينة)](dlp-on-premises-scanner-get-started.md)|
|[حماية المعلومات الحساسة في Microsoft Teams رسائل الدردشة والقنوات](dlp-microsoft-teams.md) | توسيع بعض وظائف DLP إلى Teams رسائل الدردشة والقنوات | [تعرّف على نهج منع فقدان البيانات الافتراضي في Microsoft Teams (معاينة)](dlp-teams-default-policy.md)|

## <a name="licensing-requirements"></a>متطلبات الترخيص

تعتمد متطلبات الترخيص ل Microsoft Purview حماية البيانات على السيناريوهات والميزات التي تستخدمها، بدلا من تعيين متطلبات الترخيص لكل قدرة مدرجة في هذه الصفحة. لفهم متطلبات الترخيص وخياراته ل Microsoft Purview حماية البيانات، راجع أقسام **حماية البيانات** من [إرشادات Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) [وتنزيل PDF](https://go.microsoft.com/fwlink/?linkid=2139145) ذي الصلة لمتطلبات الترخيص على مستوى الميزات.
