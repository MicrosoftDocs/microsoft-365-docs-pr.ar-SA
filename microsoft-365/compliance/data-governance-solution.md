---
title: توزيع حل إدارة البيانات
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365solution-overview
- m365solution-mig
- m365initiative-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: إرشادات توجيهية لنشر Microsoft Purview لمؤسستك للتحكم في بياناتك للتوافق أو المتطلبات التنظيمية.
ms.openlocfilehash: 90832541bf202f062b44c1ec375fb20d3db654c3
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67106000"
---
# <a name="deploy-a-data-governance-solution-with-microsoft-purview"></a>نشر حل حوكمة البيانات باستخدام Microsoft Purview

>*[إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

استخدم **إدارة دورة البيانات في Microsoft Purview** (المعروف سابقا ب Microsoft Information Governance) **إدارة سجلات Microsoft Purview** للتحكم في بيانات Microsoft 365 للتوافق أو المتطلبات التنظيمية.

![نظرة عامة على خطوات نشر حل حوكمة البيانات باستخدام Microsoft Purview](../media/data-governance-solution-overview.png)

لإدارة البيانات التي تعين البيانات وتديرها عبر ممتلكات بياناتك، بما في ذلك السحابة المتعددة والبرمجيات كخدمة (SaaS)، استخدم [Microsoft Purview Data Map وMicrosoft Purview كتالوج البيانات وMicrosoft Purview Data Estate Insights](/azure/purview/overview).

للحصول على حل حماية البيانات، راجع [نشر حل حماية المعلومات باستخدام Microsoft Purview](information-protection-solution.md).

## <a name="licensing"></a>الترخيص

لفهم متطلبات الترخيص وخياراته، راجع المعلومات الواردة في إرشادات Microsoft 365 للامتثال & الأمان، [إدارة دورة البيانات في Microsoft Purview & إدارة سجلات Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management--microsoft-purview-records-management) قسم متطلبات الترخيص على مستوى الميزات.

## <a name="keep-what-you-need-and-delete-what-you-dont"></a>احتفظ بما تحتاج إليه واحذف ما لا تريده

![خطوات لحل إدارة دورة حياة البيانات](../media/data-lifecycle-management-solution.png)

استخدم **إدارة دورة البيانات في Microsoft Purview** (المعروف سابقا ب Microsoft Information Governance) للاحتفاظ بما تحتاج إليه وحذف ما لا تحتاج إليه.

|درج|الوصف|معلومات إضافية|
|:---|:----------|:---------------|
|1| فهم كيفية عمل الاستبقاء والحذف لخدمات Microsoft 365. <br /><br /> بعد أن تفهم كيف يمكنك استخدام نهج الاستبقاء وتسميات الاستبقاء، حدد أحمال العمل التي تحتاج إلى نهج استبقاء وما إذا كنت بحاجة إلى إنشاء تسميات استبقاء للاستثناءات. | [التعرف على نهج الاستبقاء وتسميات الاستبقاء](retention.md)|
|2| إنشاء نهج الاستبقاء، وإذا لزم الأمر، تسميات الاستبقاء للاستثناءات. <br /><br /> نهج الاستبقاء الأكثر استخداما هي ل Exchange وSharePoint وTeams مجموعات Microsoft 365 وYamer. يمكنك تكوين استثناءات للمستندات ورسائل البريد الإلكتروني. | [إنشاء نهج استبقاء](create-retention-policies.md) <p> [إنشاء تسميات الاستبقاء وتطبيقها على الاستثناءات الخاصة بك](create-retention-labels-information-governance.md)|
|3| إدارة علب البريد. <br /><br /> قم بتمكين علب البريد لأرشفة الأرشفة وتوسيعها تلقائيا، وفكر فيما إذا كنت بحاجة إلى التخصيص عند نقل رسائل البريد الإلكتروني إلى علبة بريد الأرشيف، وجعل علب البريد غير نشطة عند مغادرة المستخدمين للمؤسسة.| [تمكين علب بريد الأرشيف](enable-archive-mailboxes.md) <p> [تمكين أرشفة التوسع التلقائي](enable-autoexpanding-archiving.md) <p> [إنشاء علب بريد غير نشطة وإدارتها](create-and-manage-inactive-mailboxes.md)|
|4| استيراد ملفات PST إلى علب البريد عبر الإنترنت.  <br /><br /> إذا كانت لديك ملفات PST تحتوي على البيانات التي تريد التحكم فيها، يمكنك استيرادها باستخدام تحميل الشبكة أو شحن محرك الأقراص.| [استخدام تحميل الشبكة لاستيراد ملفات PST الخاصة بالمؤسسة](use-network-upload-to-import-pst-files.md) <p> [استخدام شحن محرك الأقراص لاستيراد ملفات PST لمؤسستك](use-drive-shipping-to-import-pst-files-to-office-365.md)|

لمعرفة المزيد حول القدرات من هذا الحل، راجع [التعرف على إدارة دورة حياة البيانات](information-governance.md).

## <a name="manage-high-value-items"></a>إدارة العناصر عالية القيمة

![خطوات لحل إدارة السجلات](../media/records-management-solution.png)

استخدم **إدارة سجلات Microsoft Purview** لإدارة العناصر عالية القيمة لمؤسستك لمتطلبات حفظ السجلات التجارية أو القانونية أو التنظيمية.

|درج|الوصف|معلومات إضافية|
|:---|:----------|:---------------|
|1| فهم حل إدارة السجلات. <br /><br /> استخدم تسميات الاستبقاء مع خيارات تكوين أكثر مرونة وعند الحاجة، قم بتعريف العناصر كسجلات. | [تعرّف على إدارة السجلات](records-management.md)|
|2| استخدم خطة الملف لإدارة جداول الاستبقاء. <br /><br /> تتيح لك خطة الملفات إنشاء تسميات استبقاء بشكل تفاعلي أو الاستيراد بشكل مجمع، والتصدير للتحليل. تدعم التسميات التي تقوم بإنشائها باستخدام خطة الملفات معلومات إدارية إضافية لمساعدتك في تحديد متطلبات العمل أو المتطلبات التنظيمية وتتبعها. | [استخدام خطة الملف لإنشاء تسميات الاستبقاء وإدارتها](file-plan-manager.md)|
|3| تطبيق تسميات الاستبقاء الخاصة بك. <br /><br /> يمكن نشر تسميات الاستبقاء وتطبيقها يدويا أو تلقائيا في التطبيقات، أو تطبيقها تلقائيا استنادا إلى المعلومات الحساسة أو الكلمات الأساسية أو الخصائص القابلة للبحث أو المصنفات القابلة للتدريب أو مرفقات السحابة. |[نشر تسميات الاستبقاء وتطبيقها في التطبيقات](create-apply-retention-labels.md) <p> [تطبيق تسمية استبقاء على المحتوى تلقائيا](apply-retention-labels-automatically.md)|
|4| إدارة الحذف الدائم للبيانات. <br /><br /> تعرف باسم التخلص من البيانات، يمكنك طلب مراجعة يدوية للمحتوى قبل حذفه نهائيا، وتوفير إثبات التصرف للسجلات. |[إدارة ترتيب المحتوى](disposition.md)|

> [!TIP]
> تحقق من قائمة [السيناريوهات الشائعة](get-started-with-records-management.md#common-scenarios) للتكوينات الإضافية التي تدعمها إدارة السجلات.

لمعرفة المزيد حول القدرات من هذا الحل، راجع ["تعرف على إدارة السجلات](records-management.md)".

## <a name="training-resources"></a>موارد التدريب

وحدات التعلم للمستشارين والمسؤولين:

- [مقدمة حول حماية المعلومات وإدارة دورة حياة البيانات في Microsoft Purview](/learn/modules/m365-compliance-information-governance)
- [إدارة دورة حياة البيانات في Microsoft Purview](/learn/modules/m365-compliance-information-govern-information/)
- [إدارة السجلات في Microsoft Purview](/learn/modules/m365-compliance-information-manage-records/)

للحصول على وثائق لدعم المستخدمين عند نشر هذه الحلول، راجع أقسام وثائق المستخدم النهائي [لإدارة دورة حياة البيانات](get-started-with-information-governance.md#end-user-documentation) [وإدارة السجلات](get-started-with-records-management.md#end-user-documentation).