---
title: تعريف السجلات باستخدام تسميات الاستبقاء
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
search.appverid:
- MOE150
- MET150
description: الإعلان عن السجلات باستخدام تسميات الاستبقاء.
ms.openlocfilehash: 0e8453bee843131a5781318f7adde8d19bb04d92
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016801"
---
# <a name="declare-records-by-using-retention-labels"></a>تعريف السجلات باستخدام تسميات الاستبقاء

>*[Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

للإعلان عن المستندات ورسائل البريد الإلكتروني [كسجلات](records-management.md#records)، يمكنك استخدام [تسميات الاستبقاء](retention.md#retention-labels) التي تضع علامة على المحتوى **كسجل** أو **سجل تنظيمي**.

إذا لم تكن متأكدا مما إذا كنت تريد استخدام سجل أو سجل تنظيمي، فراجع ["مقارنة القيود" للإجراءات المسموح بها أو المحظورة](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked). إذا كنت بحاجة إلى استخدام السجلات التنظيمية، يجب أولا تشغيل أمر PowerShell، كما هو موضح في القسم التالي.

يمكنك بعد ذلك نشر هذه التسميات في نهج تسمية استبقاء بحيث يمكن للمستخدمين والمسؤولين تطبيقها على المحتوى، أو للتسميات التي تضع علامة على العناصر كسجلات (ولكن ليس كسجلات تنظيمية)، قم بتطبيق هذه التسميات تلقائيا على المحتوى الذي تريد الإعلان عن سجل له.

## <a name="how-to-display-the-option-to-mark-content-as-a-regulatory-record"></a>كيفية عرض خيار وضع علامة على المحتوى كسجل تنظيمي

> [!NOTE]
> الإجراء التالي هو إجراء قابل للتدقيق، **وهو خيار السجل التنظيمي الممكن لتسجيل تسميات الاستبقاء** في [قسم أنشطة سياسة الاستبقاء وتسمية الاستبقاء](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities) في سجل التدقيق.

بشكل افتراضي، لا يتم عرض خيار تسمية الاستبقاء لوضع علامة على المحتوى كسجل تنظيمي في معالج تسمية الاستبقاء. لعرض هذا الخيار، يجب أولا تشغيل أمر PowerShell:

1. [الاتصال إلى Office 365 Security & Compliance PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. تشغيل cmdlet التالي:

    ```powershell
    Set-RegulatoryComplianceUI -Enabled $true
    ````

    لا توجد مطالبة للتأكيد ويدخل الإعداد حيز التنفيذ على الفور.

إذا غيرت رأيك بشأن رؤية هذا الخيار في معالج تسمية الاستبقاء، يمكنك إخفاؤه مرة أخرى عن طريق تشغيل cmdlet نفسه بالقيمة **الخطأ** : `Set-RegulatoryComplianceUI -Enabled $false`

## <a name="configuring-retention-labels-to-declare-records"></a>تكوين تسميات الاستبقاء للإعلان عن السجلات

عند إنشاء تسمية استبقاء من حل **إدارة السجلات** في مدخل توافق Microsoft Purview، يكون لديك خيار وضع علامة على العناصر كسجل. إذا قمت بتشغيل أمر PowerShell من القسم السابق، يمكنك بدلا من ذلك وضع علامة على العناصر كسجل تنظيمي.

على سبيل المثال:

![تكوين تسمية استبقاء لوضع علامة على المحتوى كسجل أو تنظيمي.](../media/declare-records.png)

باستخدام تسمية الاستبقاء هذه، يمكنك الآن تطبيقها على SharePoint أو OneDrive المستندات ورسائل البريد الإلكتروني Exchange، حسب الحاجة.

للحصول على الإرشادات الكاملة:

- [نشر تسميات الاستبقاء وتطبيقها في التطبيقات](create-apply-retention-labels.md)

- [تطبيق تسمية استبقاء على المحتوى تلقائيا](apply-retention-labels-automatically.md) (غير معتمد للسجلات التنظيمية)

## <a name="tenant-setting-for-editing-record-properties"></a>إعداد المستأجر لتحرير خصائص السجل

إذا كنت ستستخدم تسميات الاستبقاء للإعلان عن العناصر كسجلات (بدلا من السجلات التنظيمية) في SharePoint OneDrive، ففكر فيما إذا كنت بحاجة إلى تغيير إعداد المستأجر الافتراضي الذي يسمح للمستخدمين بتحرير خصائص [سجل مؤمن](record-versioning.md) عندما تكون الملفات أكبر من 0 بايت.

لتغيير هذا الإعداد الافتراضي، انتقل إلى **إعدادات استبقاء** >  إعدادات  >  إدارة سجلات [Microsoft Purview لمدخل](https://compliance.microsoft.com/) >  >  التوافق، ثم **قم** بإيقاف تشغيل الإعداد **"السماح للمستخدمين بتحرير خصائص السجل**".

## <a name="applying-the-configured-retention-label-to-content"></a>تطبيق تسمية الاستبقاء المكونة على المحتوى

عند إتاحة تسميات الاستبقاء التي تضع علامة على العناصر كسجل أو سجل تنظيمي للمستخدمين لتطبيقها في التطبيقات:

- بالنسبة Exchange، يمكن لأي مستخدم لديه حق الوصول للكتابة إلى علبة البريد تطبيق هذه التسميات.
- بالنسبة SharePoint OneDrive، يمكن لأي مستخدم في مجموعة الأعضاء الافتراضية (مستوى أذونات المساهمة) تطبيق هذه التسميات.

مثال لمستند تم وضع علامة عليه كسجل باستخدام تسمية استبقاء:

![جزء التفاصيل للمستند الذي تم وضع علامة عليه كسجل.](../media/recordversioning7.png)

## <a name="searching-the-audit-log-for-labeled-items-that-were-declared-records"></a>البحث في سجل التدقيق عن العناصر المسماة التي تم الإعلان عنها كسجلات

يتم تسجيل إجراءات التسمية للإعلان عن العناصر كسجلات في سجل التدقيق.

للعناصر SharePoint:
- من **أنشطة الملف والصفحة**، حدد **تسمية الاستبقاء التي تم تغييرها لملف**. حدث التدقيق هذا هو لتسميات الاستبقاء التي تضع علامة على العناصر كسجلات أو سجلات تنظيمية أو تسميات استبقاء قياسية.

للعناصر Exchange:
- من **Exchange أنشطة علبة البريد**، حدد **الرسالة المسماة كسجل**. حدث التدقيق هذا هو لتسميات الاستبقاء التي تضع علامة على العناصر كسجلات أو سجلات تنظيمية.

لمزيد من المعلومات حول البحث عن هذه الأحداث، راجع [البحث في سجل التدقيق في مركز التوافق & الأمان](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>الخطوات التالية

فهم كيفية استخدام [تعيين إصدار السجل لتحديث السجلات المخزنة في SharePoint أو OneDrive](record-versioning.md).
