---
title: إدارة دورة حياة بيانات Microsoft Purview & Microsoft Purview Records Management
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
description: تنفيذ قدرات من Microsoft Purview Data Lifecycle Management & Microsoft Purview Records Management للتحكم في بياناتك للتوافق أو المتطلبات التنظيمية.
ms.openlocfilehash: c807d2359c9a8c9cb17955b1ad4bf121cab57918
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286957"
---
# <a name="govern-your-data-with-microsoft-purview"></a>تحكم في بياناتك باستخدام Microsoft Purview

>*[Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

استخدم القدرات من **Microsoft Purview Data Lifecycle Management** (المعروف سابقا ب Microsoft Information Governance) **وMicrosoft Purview Records Management** للتحكم في بياناتك من أجل التوافق أو المتطلبات التنظيمية.

> [!TIP]
> هل تبحث عن تعيين بياناتك وإدارتها عبر ممتلكات بياناتك بأكملها، بما في ذلك السحابة المتعددة والبرامج كخدمة (SaaS)؟ استخدم [Microsoft Purview Data Map وMicrosoft Purview كتالوج البيانات وMicrosoft Purview Data Estate Insights](/azure/purview/overview).

من [منظور الترخيص](#licensing-requirements)، يمكن أن يكون هناك تداخل كبير بين إدارة دورة حياة البيانات وإدارة السجلات. يدعم كلا الحلين الاحتفاظ بالبيانات وحذفها لتطبيقات وخدمات Microsoft 365.

استخدم الرسم التالي لمساعدتك في تحديد المكونات الرئيسية القابلة للتكوين لهذه الحلول التي يكون لكل منها منطقة تكوين خاصة بها في مدخل توافق Microsoft Purview:

![المكونات الرئيسية لتكوين البيانات واستخدامها للتحكم في بياناتك باستخدام Microsoft Purview.](../media/govern-your-data.png)

هل تبحث عن حماية بياناتك؟ راجع [حماية بياناتك باستخدام Microsoft Purview](information-protection.md).

## <a name="microsoft-purview-data-lifecycle-management"></a>إدارة دورة حياة بيانات Microsoft Purview

للاحتفاظ بما تحتاج إليه وحذف ما لا تحتاج إليه:
 
|القدره|ما هي المشاكل التي تحلها؟|
|:------|:------------|:----------------|
|[نهج الاستبقاء لأحمال العمل Microsoft 365، مع تسميات الاستبقاء للاستثناءات](retention.md) | يتيح لك الاحتفاظ بالمحتوى أو حذفه باستخدام إدارة النهج للبريد الإلكتروني والمستندات Teams والرسائل Yammer. |
|[علب البريد غير النشطة](inactive-mailboxes-in-office-365.md)| يتيح لك الاحتفاظ بمحتوى علبة البريد بعد مغادرة الموظفين للمؤسسة بحيث يظل هذا المحتوى متاحا للمسؤولين ومسؤولي التوافق ومديري السجلات. |
|[أرشفة علب البريد](archive-mailboxes.md)| يوفر مساحة تخزين إضافية لعلب البريد للمستخدمين.|
|[استيراد الخدمة لملفات PST](importing-pst-files-to-office-365.md)| يدعم الاستيراد المجمع لملفات PST إلى علب بريد Exchange Online للاحتفاظ برسائل البريد الإلكتروني والبحث فيها بحثا عن التوافق أو المتطلبات التنظيمية. |

هل تريد معرفة المزيد؟ راجع [التعرف على إدارة دورة حياة البيانات](data-lifecycle-management.md).

هل أنت جاهز لبدء استخدام بعض هذه القدرات أو كلها؟ راجع [بدء استخدام إدارة دورة حياة البيانات](get-started-with-data-lifecycle-management.md).


## <a name="microsoft-purview-records-management"></a>إدارة سجلات Microsoft Purview

إدارة العناصر عالية القيمة لمتطلبات حفظ السجلات التجارية أو القانونية أو التنظيمية:

|القدره|ما هي المشاكل التي تحلها؟|
|:---------|:---------------------------|
|[خطة الملف](file-plan-manager.md)| يتيح لك إنشاء تسميات استبقاء بشكل تفاعلي أو الاستيراد بشكل مجمع، والتصدير للتحليل. تدعم التسميات معلومات إدارية إضافية (اختيارية) لمساعدتك في تحديد المتطلبات التجارية أو التنظيمية وتتبعها. |
|[تسميات الاستبقاء للعناصر الفردية، ونهج الاستبقاء إذا لزم الأمر لاستبقاء الأساس](retention.md)| تدعم التسميات جداول الاستبقاء والحذف المرنة التي يمكن تطبيقها يدويا أو تلقائيا، مع إعلان السجلات عند الحاجة. |
|[مراجعة الترتيب وإثبات التصرف](disposition.md)| المراجعة اليدوية للمحتوى قبل حذفه نهائيا، مع إثبات التخلص من السجلات.|

هل تريد معرفة المزيد؟ راجع [التعرف على إدارة السجلات](records-management.md).

هل أنت جاهز لبدء استخدام بعض هذه القدرات أو كلها؟ راجع [بدء استخدام إدارة السجلات](get-started-with-records-management.md).


## <a name="licensing-requirements"></a>متطلبات الترخيص

لفهم متطلبات الترخيص وخياراته، راجع الأقسام التالية من [وثائق الترخيص Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [إدارة دورة حياة بيانات Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management)
- [إدارة سجلات Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management)

سيتم تضمين أي متطلبات ترخيص إضافية في إرشادات الوثائق. على سبيل المثال، قد يتطلب الترخيص الخاص بإدارة علب البريد تراخيص من Exchange Online.