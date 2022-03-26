---
title: حماية البيانات في Microsoft في Microsoft 365
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
description: يمكنك حماية البيانات في Microsoft (MIP) لمساعدتك على حماية المعلومات الحساسة أينما كانت أو تتنقل.
ms.openlocfilehash: 2fccdafa662bfdf8390a53ac535c571f52f673de
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63568916"
---
# <a name="microsoft-information-protection-in-microsoft-365"></a>حماية البيانات في Microsoft في Microsoft 365

>*[ترخيص Microsoft 365 الأمان & التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

يمكنك تنفيذ قدرات حماية البيانات في Microsoft (MIP) لمساعدتك على اكتشاف المعلومات الحساسة وتصنيفها وحمايتها أينما كانت أو تتنقل.

يتم تضمين قدرات MIP مع Microsoft 365 والتوافق، كما تمنحك الأدوات اللازمة لمعرفة بياناتك[](#know-your-data)، وحماية البيانات، [](#protect-your-data)[ومنع فقدان البيانات](#prevent-data-loss).

![صورة كيف يساعدك MIP على اكتشاف البيانات الحساسة وتصنيفها وحمايتها.](../media/powered-by-intelligent-platform.png)

للحصول على إرشادات وصفية لنشر حل MIP لمنظمتك، راجع [نشر حل حماية البيانات في Microsoft.](information-protection-solution.md)

للحصول على معلومات حول إدارة بياناتك، راجع [إدارة معلومات Microsoft في](manage-Information-governance.md) Microsoft 365.

## <a name="know-your-data"></a>معرفة بياناتك

لفهم البيانات الأفقية وتحديد البيانات الحساسة عبر بيئتك المختلطة، استخدم الإمكانات التالية:

|الإمكانية|ما هي المشاكل التي يحلها؟|بدء العمل|
|:------|:------------|:--------------------|
|[أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md)| تعرف البيانات الحساسة باستخدام تعبيرات عادية مضمنة أو مخصصة أو دالة. تتضمن الدلائل المعززة الكلمات الأساسية ومستويات الثقة والتقارب.| [تخصيص نوع معلومات حساسة مضمن](customize-a-built-in-sensitive-information-type.md)|
|[المصنفات القابلة للتدريب](classifier-learn-about.md)| تعرف البيانات الحساسة باستخدام أمثلة عن البيانات التي تريدها بدلا من تحديد العناصر في العنصر (مطابقة النمط). يمكنك استخدام المصنفات المضمنة أو تدريب المصنف باستخدام المحتوى الخاص بك.| [بدء العمل باستخدام المصنفات القابلة للتدريب](classifier-get-started-with.md) |
|[تصنيف البيانات](data-classification-overview.md) | تحديد رسومي للعناصر في مؤسستك التي تحتوي على تسمية حساسية أو تسمية استبقاء أو تم تصنيفها. يمكنك أيضا استخدام هذه المعلومات للحصول على معلومات متعمقة حول الإجراءات التي يقوم المستخدمون باتخاذها على هذه العناصر. | [بدء استخدام مستكشف المحتوى](data-classification-content-explorer.md) <p> [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>حماية البيانات

لتطبيق إجراءات الحماية المرنة التي تتضمن التشفير وقيود الوصول والعلامات المرئية، استخدم الإمكانات التالية:

|الإمكانية|ما هي المشاكل التي يحلها؟|بدء العمل|
|:------|:------------|---------------------|
|[تسميات الحساسية](sensitivity-labels.md)| حل واحد عبر التطبيقات والخدمات والأجهزة لتسمية البيانات وحمايتها أثناء تنقلها داخل مؤسستك وخارجها. <br /><br /> أمثلة على السيناريوهات: <br />- [إدارة تسميات الحساسية لتطبيقات Office](sensitivity-labels-office-apps.md) <br />- [تشفير المستندات ورسائل البريد الإلكتروني](encryption-sensitivity-labels.md) <br />-  [تطبيق التسميات وعرضها في Power BI](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> للحصول على قائمة شاملة بسيناريوهات تسميات الحساسية، راجع وثائق بدء استخدام.|[بدء استخدام تسميات الحساسية](get-started-with-sensitivity-labels.md) |
|[عميل التسمية الموحد في Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2)| بالنسبة Windows الكمبيوتر، يتم توسيع التسمية إلى "مستكشف الملفات" و PowerShell، مع ميزات إضافية لتطبيقات Office إذا لزم الأمر| [دليل مسؤول عميل التسمية الموحد ل Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[تشفير المفتاح المزدوج](double-key-encryption.md)| في جميع الحالات، يمكن لمنظمتك فقط فك تشفير المحتوى المحمي أو للمتطلبات التنظيمية، يجب أن تحمل مفاتيح التشفير ضمن حد جغرافي. | [نشر تشفير المفتاح المزدوج](double-key-encryption.md#deploy-dke)|
|[تشفير الرسائل من Office 365 (OME)](ome.md)| تشفير رسائل البريد الإلكتروني والمستندات المرفقة التي يتم إرسالها إلى أي مستخدم على أي جهاز، بحيث يمكن للمستلمين المخولا فقط قراءة المعلومات المرسلة عبر البريد الإلكتروني. <br /><br />  سيناريو المثال: [إبطال البريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدمة](revoke-ome-encrypted-mail.md) | [إعداد قدرات تشفير الرسائل الجديدة](set-up-new-message-encryption-capabilities.md)|
|[تشفير الخدمة باستخدام "مفتاح العميل"](customer-key-overview.md) | يحمي من عرض البيانات بواسطة أنظمة أو موظفين غير مصرح لهم، ويكمل تشفير القرص BitLocker في مراكز بيانات Microsoft. | [إعداد مفتاح العميل Office 365](customer-key-set-up.md)|
|[SharePoint إدارة حقوق استخدام المعلومات (IRM)](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|يحمي SharePoint مكتبات وقوائم المستخدمين بحيث يكون الملف الذي تم تنزيله محميا عندما يفحصه المستخدم، بحيث يمكن للأشخاص المخولا فقط عرض الملف واستخدامه وفقا لنهج تحددها. | [إعداد إدارة حقوق استخدام المعلومات (IRM) في SharePoint إدارة](set-up-irm-in-sp-admin-center.md)|
[موصل إدارة الحقوق](/azure/information-protection/deploy-rms-connector) |الحماية فقط للنشرات المحلية الموجودة التي تستخدم Exchange أو SharePoint Server أو خوادم الملفات التي تعمل Windows الخادم والبنية الأساسية لتصنيف الملفات (FCI). | [خطوات لنشر موصل RMS](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[ماسح التسمية الموحد في Azure Information Protection](/azure/information-protection/deploy-aip-scanner)| اكتشاف المعلومات الحساسة الموجودة في مخازن البيانات المحلية وتسميتها وحمايتها. | [تكوين ماسح التسمية الموحد في Azure Information Protection وتثبيته](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Microsoft Defender لتطبيقات السحابة](/cloud-app-security/what-is-cloud-app-security)| اكتشاف المعلومات الحساسة الموجودة في مخازن البيانات الموجودة في السحابة وتسمياتها وحمايتها. | [اكتشاف البيانات المنظمة والحساسة المخزنة في السحابة وتصنيفها وتسميتها وحمايتها](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Azure Purview](/azure/purview/overview) |تحديد البيانات الحساسة وطبق التسمية التلقائية على المحتوى في أصول Azure Purview. وتتضمن هذه الملفات في مساحة التخزين مثل Azure Data Lake وملفات Azure، وبيانات مكياسية مثل الأعمدة في Azure SQL DB وDDB منأوكوس. |[وضع التسميات في Azure Purview](/azure/purview/create-sensitivity-label) |
|[حماية البيانات في Microsoft SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|توسيع تسميات الحساسية لتشمل تطبيقات وخدمات  الأطراف الخارجية. <br /><br />  سيناريو المثال: [تعيين تسمية حساسية (C++) والحصول عليها](/information-protection/develop/quick-file-set-get-label-cpp) |[إعداد عدة تطوير برامج حماية البيانات في Microsoft (MIP) وتكوينها](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>منع فقدان البيانات

للمساعدة في منع  زائدة عن طريق الخطأ للمعلومات الحساسة، استخدم الإمكانات التالية:


|الإمكانية|ما هي المشاكل التي يحلها؟|بدء العمل|
|:------|:------------|:---------------------|
|[منع فقدان البيانات](dlp-learn-about-dlp.md)| يساعد على منع المشاركة غير المقصودة للعناصر الحساسة. | [بدء استخدام نهج DLP الافتراضي](get-started-with-the-default-dlp-policy.md)|
|[منع فقدان البيانات في نقطة النهاية](endpoint-dlp-learn-about.md)| توسيع قدرات DLP للعناصر المستخدمة والمشتركة على أجهزة الكمبيوتر Windows 10 الكمبيوتر. | [بدء استخدام منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md)|
|[ملحق التوافق من Microsoft](dlp-chrome-learn-about.md) | توسيع قدرات DLP إلى مستعرض Chrome | [بدء العمل باستخدام ملحق التوافق من Microsoft](dlp-chrome-get-started.md)|
|[Microsoft 365 فقدان البيانات المحلي (معاينة)](dlp-on-premises-scanner-learn.md)|توسيع مراقبة DLP لأنشطة الملفات والإجراءات الحماية لتلك الملفات إلى عمليات مشاركة الملفات SharePoint ومكتبات المستندات.|[بدء استخدام Microsoft 365 فقدان البيانات المحلي (معاينة)](dlp-on-premises-scanner-get-started.md)|
|[حماية المعلومات الحساسة في Microsoft Teams رسائل الدردشة والقنوات](dlp-microsoft-teams.md) | توسيع بعض وظائف DLP Teams رسائل الدردشة والقناة | [تعرف على نهج منع فقدان البيانات الافتراضي في Microsoft Teams (معاينة)](dlp-teams-default-policy.md)|

## <a name="licensing-requirements"></a>متطلبات الترخيص

تعتمد متطلبات الترخيص ل MIP على السيناريوهات والميزات التي تستخدمها، بدلا من تعيين متطلبات الترخيص لكل إمكانية مدرجة في هذه الصفحة. لفهم متطلبات الترخيص وخيارات MIP، راجع أقسام حماية المعلومات من [إرشادات Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) لتوافق الأمان & وتنزيل [PDF](https://go.microsoft.com/fwlink/?linkid=2139145) ذي الصلة لمتطلبات الترخيص على مستوى الميزات.