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
description: تعريف السجلات باستخدام تسميات الاستبقاء.
ms.openlocfilehash: 93e51698109819f4743dd4b5b45f5a5177739a2a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569372"
---
# <a name="declare-records-by-using-retention-labels"></a>تعريف السجلات باستخدام تسميات الاستبقاء

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

لإعلان المستندات ورسائل البريد [الإلكتروني كسجلات](records-management.md#records)، يمكنك استخدام تسميات استبقاء تقوم بعلامة المحتوى **كسجل أو** [](retention.md#retention-labels) **سجل تنظيمي**.

إذا لم تكن متأكدا مما إذا كنت تريد استخدام سجل أو سجل تنظيمي، فشاهد مقارنة القيود على الإجراءات المسموح بها [أو المحظورة](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked). إذا كنت بحاجة إلى استخدام السجلات التنظيمية، فيجب أولا تشغيل أمر PowerShell، كما هو موضح في المقطع التالي.

يمكنك بعد ذلك نشر هذه التسميات في نهج تسمية استبقاء بحيث يمكن للمستخدمين والمسؤولين تطبيقها على المحتوى، أو بالنسبة إلى التسميات التي تقوم بعلامة العناصر كسجلات (ولكن ليس سجلات تنظيمية)، قم بتطبيق هذه التسميات بشكل تلقائي على المحتوى الذي تريد إعلان سجل عنه.

## <a name="how-to-display-the-option-to-mark-content-as-a-regulatory-record"></a>كيفية عرض خيار وضع علامة على المحتوى كسجل تنظيمي

> [!NOTE]
> الإجراء التالي هو إجراء قابل للتدقيق، تسجيل خيار  السجل التنظيمي التمكيني لتسميات الاستبقاء في القسم [](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities) نهج الاستبقاء وأنشطة تسمية الاستبقاء في سجل التدقيق.

بشكل افتراضي، لا يتم عرض خيار تسمية الاستبقاء لعلامة المحتوى كسجل تنظيمي في معالج تسمية الاستبقاء. لعرض هذا الخيار، يجب أولا تشغيل أمر PowerShell:

1. [الاتصال إلى Office 365 الأمان & مركز التوافق PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. تشغيل cmdlet التالي:

    ```powershell
    Set-RegulatoryComplianceUI -Enabled $true
    ````

    لا توجد مطالبة لتأكيد الإعداد وسيأخذ الإعداد حيز التنفيذ على الفور.

إذا غيرت رأيك بشأن رؤية هذا الخيار في معالج تسمية الاستبقاء، يمكنك إخفائه مرة أخرى عن طريق تشغيل الأمر cmdlet نفسه مع **القيمة الخاطئة** : `Set-RegulatoryComplianceUI -Enabled $false`

## <a name="configuring-retention-labels-to-declare-records"></a>تكوين تسميات الاستبقاء لإعلان السجلات

عند إنشاء تسمية استبقاء من حل  إدارة السجلات في مركز التوافق في Microsoft 365، يكون لديك خيار وضع علامة على العناصر كسجل. إذا قمت بركض الأمر PowerShell من المقطع السابق، يمكنك بدلا من ذلك وضع علامة على العناصر كسجل تنظيمي.

على سبيل المثال:

![تكوين تسمية استبقاء لتسمية المحتوى كسجل أو تنظيمي.](../media/recordversioning6.png)

باستخدام تسمية الاستبقاء هذه، يمكنك الآن تطبيقها على SharePoint أو OneDrive المستندات Exchange البريد الإلكتروني، حسب الحاجة.

للحصول على الإرشادات الكاملة:

- [إنشاء تسميات استبقاء وتطبيقها في التطبيقات](create-apply-retention-labels.md)

- [تطبيق تسمية استبقاء على المحتوى تلقائيا](apply-retention-labels-automatically.md) (غير معتمد للسجلات التنظيمية)

## <a name="tenant-setting-for-editing-record-properties"></a>إعداد المستأجر لتحرير خصائص السجل

إذا كنت تستخدم تسميات استبقاء لإعلان العناصر كسجلات (بدلا من السجلات التنظيمية) في SharePoint و OneDrive، فضع في اعتبارك ما إذا كنت بحاجة إلى تغيير إعداد المستأجر الافتراضي الذي يسمح للمستخدمين بتحرير خصائص سجل مؤمن عندما تكون الملفات أكبر من 0 [](record-versioning.md) بايت.

لتغيير هذا الإعداد الافتراضي، انتقل إلى [مركز التوافق في Microsoft 365](https://compliance.microsoft.com/) >  **إدارةRecords** >  >  >  إعدادات الإدارةاحتواء تسمياتالتحرير لخصائص السجل ثم إيقاف تشغيل الإعداد السماح للمستخدمين بتحرير خصائص **السجل**.

## <a name="applying-the-configured-retention-label-to-content"></a>تطبيق تسمية الاستبقاء المكونة على المحتوى

عند توفر تسميات الاستبقاء التي تعمل على وضع علامة على العناصر كسجل أو سجل تنظيمي للمستخدمين لتطبيقها في التطبيقات:

- بالنسبة Exchange، يمكن لأي مستخدم يمكنه الوصول للكتابة إلى علبة البريد تطبيق هذه التسميات.
- بالنسبة SharePoint OneDrive، يمكن لأي مستخدم في مجموعة الأعضاء الافتراضية (مستوى الأذونات مساهمة) تطبيق هذه التسميات.

مثال لمستند تم وضع علامة عليه كسجل باستخدام تسمية استبقاء:

![جزء التفاصيل للمستند الذي تم وضع علامة عليه كسجل.](../media/recordversioning7.png)

## <a name="searching-the-audit-log-for-labeled-items-that-were-declared-records"></a>البحث في سجل التدقيق عن العناصر الملصقات التي تم الإعلان عنها كسجلات

يتم تسجيل إجراءات التسمية لإعلان العناصر كسجلات في سجل التدقيق.

بالنسبة SharePoint العناصر:
- من **أنشطة الملف والصفحة**، حدد **تسمية الاستبقاء التي تم تغييرها لملف**. حدث التدقيق هذا هو لتسميات الاستبقاء التي تم وضع علامة على العناصر كسجلات أو سجلات تنظيمية أو تلك تسميات استبقاء قياسية.

بالنسبة Exchange العناصر:
- من **Exchange علبة البريد،** حدد **رسالة سمي كسجل**. حدث التدقيق هذا هو لتسميات الاستبقاء التي تم وضع علامة على العناصر كسجلات أو سجلات تنظيمية.

لمزيد من المعلومات حول البحث عن هذه الأحداث، راجع البحث في سجل [التدقيق في مركز التوافق & الأمان](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>الخطوات التالية

تعرف على كيفية استخدام [إصدار السجلات لتحديث السجلات المخزنة في SharePoint أو OneDrive](record-versioning.md).