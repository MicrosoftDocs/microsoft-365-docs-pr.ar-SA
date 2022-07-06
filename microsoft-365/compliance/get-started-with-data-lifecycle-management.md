---
title: بدء استخدام إدارة دورة حياة البيانات
f1.keywords:
- NOCSH
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
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: هل أنت مستعد لبدء التحكم في بيانات مؤسستك، ولكن لست متأكدا من أين تبدأ؟ اقرأ بعض الإرشادات الإرشادية للبدء.
ms.openlocfilehash: 97890f7d873cf19ddc1050cc77f20aa2408c18af
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629652"
---
# <a name="get-started-with-data-lifecycle-management"></a>بدء استخدام إدارة دورة حياة البيانات

>*[إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

هل أنت جاهز لبدء التحكم في بيانات مؤسستك من خلال الاحتفاظ بالمحتوى الذي تحتاج إلى الاحتفاظ به، وحذف المحتوى الذي لا تريده؟ للبدء، استخدم الإرشادات التالية إدارة دورة البيانات في Microsoft Purview (المعروف سابقا ب Microsoft Information Governance):

1. **فهم كيفية عمل الاستبقاء والحذف** في Microsoft 365، ثم تحديد أحمال العمل التي تحتاج إلى نهج استبقاء وما إذا كنت بحاجة إلى إنشاء تسميات استبقاء للاستثناءات: [تعرف على الاستبقاء](retention.md)
    
    > [!NOTE]
    > إذا كنت بحاجة إلى إدارة العناصر عالية القيمة لمتطلبات حفظ السجلات التجارية أو القانونية أو التنظيمية: استخدم تسميات الاستبقاء مع [إدارة السجلات](records-management.md) بدلا من إدارة دورة حياة البيانات.

2. **إنشاء نهج استبقاء** لأحمال العمل التي حددتها، مع تحديد إعدادات الاستبقاء والإجراءات المطلوبة من قبل نهج المؤسسة أو اللوائح الصناعية: [إنشاء نهج الاستبقاء](create-retention-policies.md)
    
    إذا لزم الأمر، [قم بإنشاء تسميات الاستبقاء وتطبيقها للاستثناءات الخاصة بك](create-retention-labels-information-governance.md).

3. **تمكين أرشفة علبة البريد** لتزويد المستخدمين بمساحة تخزين إضافية لعلب البريد: [تمكين علب بريد الأرشيف في مدخل التوافق في Microsoft Purview](enable-archive-mailboxes.md)
    
    إذا لزم الأمر لدعم علب بريد الأرشيف:
    
    - [تمكين التوسيع التلقائي لأرشفة](enable-autoexpanding-archiving.md) علب البريد التي تحتاج إلى مساحة تخزين تزيد عن 100 غيغابايت.
    
    - استخدم [علامات الاستبقاء مع نهج استبقاء من إدارة سجلات المراسلة (MRM)](set-up-an-archive-and-deletion-policy-for-mailboxes.md) إذا كنت بحاجة إلى تخصيص كيفية نقل رسائل البريد الإلكتروني تلقائيا من علبة البريد الأساسية للمستخدم إلى علبة بريد الأرشيف الخاصة به، أو إذا كنت بحاجة إلى تحديد إعدادات الاستبقاء والحذف لمجلدات معينة بدلا من علبة البريد بأكملها.

4. **فهم علب البريد غير النشطة** التي تحتفظ بمحتوى علبة البريد وإدارتها بعد مغادرة الموظفين للمؤسسة: [تعرف على علب البريد غير النشطة](inactive-mailboxes-in-office-365.md)

5. إذا كانت لديك ملفات PST تحتوي على بيانات تريد التحكم فيها: **قم باستيراد ملفات PST إلى علب البريد عبر الإنترنت** باستخدام تحميل الشبكة أو شحن محرك الأقراص: [تعرف على كيفية استيراد ملفات PST الخاصة بالمؤسسة](importing-pst-files-to-office-365.md)

## <a name="subscription-and-licensing-requirements"></a>متطلبات الاشتراك والترخيص

يدعم عدد من الاشتراكات المختلفة قدرات إدارة دورة حياة البيانات.

للاطلاع على خيارات ترخيص المستخدمين للاستفادة من ميزات Microsoft Purview، راجع [إرشادات ترخيص Microsoft 365 للأمان & التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). للحصول على الميزات المدرجة في هذه الصفحة، راجع قسم [إدارة دورة البيانات في Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management) [وتنزيل PDF](https://go.microsoft.com/fwlink/?linkid=2139145) ذي الصلة لمتطلبات الترخيص على مستوى الميزات.

## <a name="permissions"></a>الأذونات

راجع القسم التالي للحصول على معلومات حول الأدوار ومجموعات الأدوار لإدارة استبقاء Microsoft 365.

للحصول على أذونات لإدارة علب البريد للأرشفة وعلب البريد غير النشطة والاستيراد، تتطلب هذه الأذونات عادة أذونات Exchange، مثل دور مستلمي البريد. بشكل افتراضي، يتم تعيين هذا الدور إلى مجموعات دور إدارة المستلمين وإدارة المؤسسة. للحصول على متطلبات الأذونات الدقيقة لكل مهمة إدارة، راجع الوثائق التي تقترن بتعليمات المسؤول.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>أذونات لنهج الاستبقاء وتسميات الاستبقاء

يحتاج أعضاء فريق التوافق الذين سينشئون نهج الاستبقاء وتسميات الاستبقاء ويديرونها إلى أذونات <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a>. بشكل افتراضي، يمكن لمسؤول المستأجر (المسؤول العام) الوصول إلى هذا الموقع ويمكنه منح مسؤولي الامتثال والأشخاص الآخرين حق الوصول دون منحهم جميع أذونات مسؤول المستأجر. لمنح أذونات لهذه الإدارة المحدودة، نوصي بإضافة مستخدمين إلى مجموعة دور مسؤول **مسؤول التوافق** .

بدلا من استخدام هذا الدور الافتراضي، يمكنك إنشاء مجموعة دور جديدة وإضافة دور **إدارة الاستبقاء** إلى هذه المجموعة. للحصول على دور للقراءة فقط، استخدم **View-Only Retention Management**. 

للحصول على إرشادات لإضافة مستخدمين إلى الأدوار الافتراضية أو إنشاء مجموعات الأدوار الخاصة بك، راجع [الأذونات في مدخل التوافق في Microsoft Purview](microsoft-365-compliance-center-permissions.md).

هذه الأذونات مطلوبة فقط لإنشاء نهج الاستبقاء وتسميات الاستبقاء وتكوينها وتطبيقها. لا يتطلب الشخص الذي يقوم بتكوين هذه النهج والتسميات الوصول إلى المحتوى.

## <a name="common-scenarios"></a>السيناريوهات الشائعة

استخدم الجدول التالي لمساعدتك على تعيين متطلبات عملك إلى السيناريوهات الأكثر شيوعا لإدارة دورة حياة البيانات.

|أريد...|الوثائق|
|----------------|---------------|
|الاحتفاظ بالبيانات لخدمات Microsoft 365 أو حذفها بكفاءة: <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- مجموعات Microsoft 365 <br />- Teams <br />- Yammer <br />- Skype for Business |[إنشاء نهج الاستبقاء وتكوينها](create-retention-policies.md)|
|تزويد المستخدمين بتخزين إضافي لعلب البريد |[تمكين علب بريد الأرشيف في مدخل التوافق في Microsoft Purview](enable-archive-mailboxes.md)|
|الاحتفاظ ببيانات علبة البريد بعد مغادرة الموظفين للمؤسسة |[إنشاء علب بريد غير نشطة وإدارتها](create-and-manage-inactive-mailboxes.md)|
|تحميل بيانات علبة البريد من ملفات PST |[استخدام تحميل الشبكة لاستيراد ملفات PST](use-network-upload-to-import-pst-files.md)|


إذا كان لديك سيناريو يتطلب إدارة بيانات العناصر الفردية، فراجع [السيناريوهات الشائعة لإدارة السجلات](get-started-with-records-management.md#common-scenarios). 

## <a name="end-user-documentation"></a>وثائق المستخدم النهائي

راجع القسم التالي للحصول على معلومات حول وثائق المستخدم النهائي لدعم استبقاء Microsoft 365.

لا تتطلب قدرات إدارة دورة حياة البيانات لعلب البريد غير النشطة واستيراد ملفات PST وثائق المستخدم النهائي لأنها عمليات المسؤول فقط. لمساعدة المستخدمين على فهم علب بريد الأرشيف والتفاعل معها في Outlook بعد تمكين هذه الإمكانية، راجع [إدارة تخزين البريد الإلكتروني باستخدام علب بريد الأرشيف عبر الإنترنت](https://support.microsoft.com/office/manage-email-storage-with-online-archive-mailboxes-1cae7d17-7813-4fe8-8ca2-9a5494e9a721).

### <a name="end-user-documentation-for-retention-and-deletion"></a>وثائق المستخدم النهائي للاستبقاء والحذف

تعمل معظم نهج الاستبقاء بشكل غير مزعج في الخلفية دون تفاعل المستخدم، وبالتالي تحتاج إلى القليل من الوثائق للمستخدمين. تعلم نهج الاستبقاء ل Teams المستخدمين عند حذف رسائلهم بارتباط إلى [رسائل Teams حول نهج الاستبقاء](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

ومع ذلك، إذا قمت بتكملة نهج الاستبقاء بتسميات الاستبقاء، فإن هذه التسميات لها وجود واجهة مستخدم في تطبيقات Microsoft 365. قبل نشر هذه التسميات على شبكة الإنتاج الخاصة بك، تأكد من توفير معلومات وإرشادات للمستخدمين النهائيين ومكتب المساعدة. لمساعدة المستخدمين على تطبيق تسميات الاستبقاء في SharePoint وOneDrive، راجع [تطبيق تسميات الاستبقاء على الملفات في SharePoint أو OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

ستكون وثائق المستخدم النهائي الأكثر فعالية دائما إرشادات وتعليمات مخصصة توفرها لأسماء تسميات الاستبقاء والتكوينات التي تختارها. راجع الصفحة التالية والتنزيلات التي يمكنك استخدامها للمساعدة في تدريب المستخدمين: [تدريب المستخدم النهائي على تسميات الاستبقاء](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

