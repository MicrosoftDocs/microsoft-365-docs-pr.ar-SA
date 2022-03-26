---
title: إدارة معلومات Microsoft في Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
recommendations: false
description: تنفيذ قدرات Microsoft Information Governance لتحكم بياناتك من أجل التوافق أو المتطلبات التنظيمية.
ms.openlocfilehash: b99d073817dc0ef899f448fb6a21619b08806759
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/27/2022
ms.locfileid: "63566145"
---
# <a name="microsoft-information-governance-in-microsoft-365"></a>إدارة معلومات Microsoft في Microsoft 365

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

استخدم قدرات Microsoft Information Governance (اختصارا في بعض الأحيان إلى MIG) لإدارة بياناتك للتوافق أو المتطلبات التنظيمية.

من منظور [الترخيص،](#licensing-requirements) يمكن أن يكون هناك تداخل كبير بين إدارة المعلومات وإدارة السجلات وموصلات البيانات. تدعم المناطق الثلاث كلها الاحتفاظ بالبيانات وحذفها في Microsoft 365. يتم استخدام الموصلات بواسطة حلول التوافق غير إدارة المعلومات والسجلات. 

استخدم الرسم التالي لمساعدتك على تحديد المكونات الرئيسية القابلة للتكوين لهذه الحلول الثلاثة المختلفة التي تحتوي كل منها على عقدة خاصة بها في مركز التوافق:

![المكونات الرئيسية التي يجب إدارتها ل Microsoft Information Goevernance.](../media/information-governance-components.png)

هل تبحث عن حماية بياناتك؟ راجع [حماية البيانات في Microsoft في Microsoft 365](information-protection.md).

## <a name="information-governance"></a>إدارة المعلومات

لإبقاء ما تحتاج إليه وحذف ما لا تحتاج إليه:
 
|الإمكانية|ما هي المشاكل التي يحلها؟|بدء العمل|
|:------|:------------|:--------------------|:-----------------------------|
|[سياسات الاستبقاء Microsoft 365 العمل، مع تسميات استبقاء الاستثناءات](retention.md) | الاحتفاظ بالمحتوى أو حذفه باستخدام إدارة النهج للبريد الإلكتروني والمستندات Teams Yammer البريد الإلكتروني | [إنشاء سياسات استبقاء وتكوينها](create-retention-policies.md) <br /><br /> [إنشاء تسميات استبقاء لاستثناءات لنهج الاستبقاء](create-retention-labels-information-governance.md)|
|[أرشفة علب البريد](archive-mailboxes.md)| توفير مساحة تخزين إضافية لعلبة البريد للمستخدمين | [تمكين علب بريد الأرشيف](enable-archive-mailboxes.md) |
|[علب البريد غير النشطة](inactive-mailboxes-in-office-365.md)| الاحتفاظ بمحتوى علبة البريد بعد مغادرة الموظفين المؤسسة بحيث يظل هذا المحتوى متاحا للمسؤولين وموظفي التوافق ومديري السجلات | [إنشاء علب بريد غير نشطة وإدارتها](create-and-manage-inactive-mailboxes.md)|
|[استيراد خدمة لملفات PST](importing-pst-files-to-office-365.md)| استيراد ملفات PST مجمعة Exchange Online علب البريد للاحتفاظ بالرسائل والبحث فيها بحثا عن التوافق أو المتطلبات التنظيمية | [استخدم تحميل الشبكة لاستيراد ملفات PST الخاصة مؤسستك Microsoft 365](use-network-upload-to-import-pst-files.md)|

## <a name="records-management"></a>إدارة السجلات

إدارة دورة حياة العناصر ذات القيمة العالية للالتزامات القانونية أو التجارية أو التنظيمية:

|الإمكانية|ما هي المشاكل التي يحلها؟|بدء العمل|
|:------|:------------|---------------------|:----------------------------|
|[إدارة السجلات](records-management.md)| حل واحد للبريد الإلكتروني والمستندات يتضمن جداول استبقاء وحذف مرنة ومتطلبات لدعم دورة حياة المحتوى بالكامل مع إعلان السجلات والتصرف الذي يمكن الدفاع عنه عند الحاجة |[بدء العمل باستخدام إدارة السجلات](get-started-with-records-management.md) |

## <a name="connectors-for-third-party-data"></a>موصلات لبيانات جهة خارجية

توسيع أدوات التوافق الخاصة بك لتمتد إلى بيانات  الأطراف الخارجية المستوردة والمرشفة من الأنظمة الأساسية لل الوسائط الاجتماعية، و الأنظمة الأساسية للمراسلة الفورية، و الأنظمة الأساسية للتعاون في العمل على المستندات:

|الإمكانية|ما هي المشاكل التي يحلها؟|بدء العمل|
|:------|:------------|:--------------------|:-----------------------------|
|[موصلات البيانات](archiving-third-party-data.md)| استيراد حلول التوافق وأرشفتها وتطبيقها على بيانات  الأطراف الخارجية من الأنظمة الأساسية لل الوسائط الاجتماعية و الأنظمة الأساسية للمراسلة الفورية و الأنظمة الأساسية للتعاون في العمل على المستندات| [موصلات  جهة خارجية](archiving-third-party-data.md#third-party-data-connectors)|

## <a name="licensing-requirements"></a>متطلبات الترخيص

تعتمد متطلبات الترخيص لإدارة معلومات Microsoft على السيناريوهات والميزات التي تستخدمها، بدلا من تعيين متطلبات الترخيص لكل إمكانية مدرجة في هذه الصفحة. لفهم متطلبات وخيارات الترخيص، راجع الأقسام التالية من Microsoft 365 [الترخيص:](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) 
- [إدارة المعلومات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) 
- [إدارة التسجيلات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) 
- [موصلات البيانات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-connectors)

سيتم تضمين أي متطلبات ترخيص إضافية في إرشادات الوثائق. على سبيل المثال، قد يتطلب الترخيص الخاص بإدارة علب البريد تراخيص من Exchange Online.

