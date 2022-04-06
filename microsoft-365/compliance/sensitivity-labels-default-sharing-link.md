---
title: استخدم تسميات الحساسية لتكوين نوع ارتباط المشاركة الافتراضي للمواقع والمستندات في SharePoint OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: استخدم تسميات الحساسية لتكوين نوع ارتباط المشاركة الافتراضي للمواقع والمستندات في SharePoint OneDrive.
ms.openlocfilehash: 122a8846893b97146dc74d3a9d30ccbfe050525b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704713"
---
# <a name="use-sensitivity-labels-to-configure-the-default-sharing-link-type-for-sites-and-documents-in-sharepoint-and-onedrive"></a>استخدم تسميات الحساسية لتكوين نوع ارتباط المشاركة الافتراضي للمواقع والمستندات في SharePoint OneDrive

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

يمكنك استخدام هذه التسميات لتكوين إعدادات الإعدادات التي تراها في مركز التوافق في Microsoft 365 لتسميات [](sensitivity-labels.md)الحساسية، لتكوين إعدادات نوع ارتباط المشاركة الافتراضي لموقع SharePoint أو حساب OneDrive والمستندات الفردية. يتم تحديد هذه الإعدادات تلقائيا، ولكنها غير مرئية بشكل كبير للمستخدمين عند تحديد الزر مشاركة في تطبيقاتهم  Office الخاصة بهم. على سبيل المثال:

![مثال لمربع الحوار ارتباط مشاركة افتراضي.](../media/default-sharing-link-example.png)

يقوم نوع ارتباط المشاركة الافتراضي بتعيين النطاق (من) والأذونات (العرض أو التحرير) التي يتم تحديدها تلقائيا عند مشاركة المستخدمين للملفات والمجلدات. على الرغم من أن المستخدمين يمكنهم دائما تجاوز هذه الإعدادات الافتراضية قبل إرسال ارتباط المشاركة، إلا أن الإعدادات التي تختارها توفر أساس آمن. عادة، لا يقوم المستخدمون بتغيير الإعدادات قبل المشاركة.

على مستوى الموقع (SharePoint موقع ويب أو حساب OneDrive)، توفر تسميات الحساسية بديلا مناسبا لإعداد نوع ارتباط المشاركة الافتراضي الذي يمكن تكوينه لموقع في SharePoint مركز الإدارة. لمزيد من المعلومات، راجع تغيير نوع الارتباط الافتراضي [لموقع](/sharepoint/change-default-sharing-link) من SharePoint البيانات.

يعمل هذا التكوين على مستوى الموقع بشكل جيد SharePoint المواقع التي لديها مستندات بنفس مستوى الحساسية. ولكن إذا كانت المواقع تحتوي على بعض المستندات ذات مستوى أعلى من الحساسية التي تتطلب إعدادات أكثر تقييدا، يمكنك تكوين تسمية حساسية بإعدادات مختلفة لنوع ارتباط المشاركة الافتراضي، ثم تطبيق هذه التسمية على المستندات.

في هذا السيناريو حيث يحتوي الموقع على إعدادات افتراضية لنوع ارتباط المشاركة، وكان المستند في هذا الموقع يحتوي على إعدادات مختلفة لنوع الارتباط الافتراضي، سيتم تطبيق إعدادات النطاق الأكثر تقييدا في الوقت الذي يحدد فيه المستخدم خيار المشاركة للمستند. على سبيل المثال:

- يتم تحديد نطاق نوع ارتباط المشاركة الافتراضي للموقع لأي شخص في مؤسستك. تم تسمية مستند في هذا الموقع بنوع ارتباط المشاركة الافتراضي المعين إلى أشخاص معينين. عندما يشارك مستخدم هذا المستند، سيتم تحديد نوع ارتباط المشاركة الافتراضي المحدد إلى أشخاص معينين.

- يتم تحديد نطاق نوع ارتباط المشاركة الافتراضي للموقع مع أشخاص معينين، مع أذونات التحرير. تم تسمية مستند في هذا الموقع بنوع ارتباط المشاركة الافتراضي الذي تم تعيينه إلى أي شخص في المؤسسة، مع أذونات العرض. عندما يشارك مستخدم هذا المستند، سيتم تحديد نوع ارتباط المشاركة الافتراضي المحدد إلى أشخاص معينين من ذوي أذونات التحرير.

قد يكون تكوين نوع الارتباط الافتراضي للمستندات مناسبا أيضا بدون إعداد على مستوى الموقع. على سبيل المثال SharePoint على الرغم من أن المواقع SharePoint عادة ما يتم تنظيمها لاستضافة نوع المستندات نفسه، إلا أن ذلك لا ينطبق على OneDrive الحسابات. يحفظ المستخدمون عادة مجموعة واسعة من الملفات OneDrive، بما في ذلك في أغلب الأحيان خليط من المستندات الشخصية ومستندات الأعمال. قد لا يكون تعيين نوع ارتباط افتراضي لكل مستندات حساب المستخدم OneDrive عملية، ولكن يمكن للمستندات الفردية الاستفادة من هذه الإعدادات. على سبيل المثال:

- المستندات الموصى بها **بسرية** عالية لها نوع ارتباط مشاركة افتراضي يقيد المشاركة على أشخاص معينين بدلا من أي شخص في المؤسسة.
- المستندات التي تسمى **عام** لها نوع ارتباط مشاركة افتراضي يقيد المشاركة للأشخاص في مؤسستك.
- المستندات ذات التسمية **شخصي** لديها نوع ارتباط مشاركة افتراضي يسمح بالمشاركة لأي شخص لديه الارتباط.

## <a name="prerequisites"></a>المتطلبات الأساسية

لتطبيق نوع ارتباط المشاركة الافتراضي للمواقع، يجب تمكين تسميات الحساسية والحاويات. إذا لم يتم تمكين هذه الإمكانية للمستأجر بعد، ف راجع كيفية تمكين تسميات الحساسية والحاويات [ومزامنة التسميات](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels).

لتطبيق نوع ارتباط المشاركة الافتراضي للمستندات في SharePoint OneDrive، يجب تمكين تسميات الحساسية لهذه الخدمات. إذا لم يتم تمكين هذه الإمكانية للمستأجر بعد، ف راجع كيفية تمكين تسميات الحساسية SharePoint OneDrive [(الاشتراك)](sensitivity-labels-sharepoint-onedrive-files.md#how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in).

في جلسة PowerShell، يجب الاتصال Office 365 [الأمان & مركز التوافق PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) لتكوين الإعدادات لنوع ارتباط المشاركة الافتراضي.

> [!NOTE]
> على الرغم من أنه ليس مطلوبا، فمن الأسهل إنشاء [](create-sensitivity-labels.md)تسميات الحساسية وتكوينها أولا في مركز التوافق في Microsoft 365، ثم تعديل هذه التسميات باستخدام الإعدادات التي تقوم بتكوين نوع ارتباط المشاركة الافتراضي.

## <a name="how-to-configure-settings-for-the-default-sharing-link-type"></a>كيفية تكوين الإعدادات لنوع ارتباط المشاركة الافتراضي

تستخدم إعدادات التكوين لنوع ارتباط المشاركة الافتراضي المعلمة PowerShell *AdvancedSettings* مع cmdlets [Set-Label](/powershell/module/exchange/set-label) و [New-Label](/powershell/module/exchange/new-labelpolicy) من [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell):

- **DefaultSharingScope**: القيم المتوفرة هي:
    - **SpecificPeople**: تعيين ارتباط المشاركة الافتراضي للموقع إلى الارتباط "أشخاص محددون"
    - **المؤسسة**: تعيين ارتباط المشاركة الافتراضي للموقع إلى ارتباط "المؤسسة" أو ارتباط الشركة القابل للمشاركة
    - **أي** شخص: تعيين ارتباط المشاركة الافتراضي للموقع إلى ارتباط وصول مجهول أو أي شخص

- **DefaultShareLinkPermission**: القيم المتوفرة هي:
    - **طريقة** العرض: تعيين إذن الارتباط الافتراضي للموقع إلى أذونات "العرض"
    - **تحرير**: تعيين إذن الارتباط الافتراضي للموقع لأذونات "التحرير"

يكافئ هذان الإعدادان والقيم المعلمتين *DefaultSharingScope* و *DefaultShareLinkPermission* من [الأمر cmdlet Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) .

أمثلة PowerShell، حيث تكون تسمية الحساسية GUID **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

- لتعيين نوع ارتباط المشاركة الافتراضي إلى SpecificPeople:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope="SpecificPeople"}
    ````

- لتعيين أذونات نوع ارتباط المشاركة الافتراضي إلى تحرير:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultShareLinkPermission="Edit"}
    ````

لتكوين إعدادات نوع ارتباط المشاركة الافتراضي لموقع، يجب أن يتضمن نطاق تسمية الحساسية المجموعات & المواقع [](sensitivity-labels.md#label-scopes) عند إنشاء تسمية الحساسية في مركز التوافق في Microsoft 365. بعد إنشائه، سترى ذلك معروضا على أنه موقع، و **UnifiedGroup** في العمود النطاق على  صفحة التسميات،  ويعرض إعداد PowerShell *ContentType* هذه القيمة نفسها أيضا. بالنسبة للمستندات، يجب أن يتضمن النطاق ملفات **& البريد الإلكتروني**، التي يتم عرضها **كملف، بريد إلكتروني**. ثم:

- عندما يتضمن النطاق مجموعات **& المواقع**، يمكنك تطبيق التسمية على موقع، مما يحدد نوع ارتباط المشاركة الافتراضي لهذا الموقع. للحصول على معلومات حول كيفية تطبيق تسمية حساسية على موقع، راجع [كيفية تطبيق تسميات الحساسية على الحاويات](sensitivity-labels-teams-groups-sites.md#how-to-apply-sensitivity-labels-to-containers).

- عندما يتضمن نطاق تسمية الحساسية ملفات & البريد الإلكتروني، يمكنك تطبيق التسمية على المستندات، مما يحدد نوع ارتباط المشاركة الافتراضي لهذا المستند. يمكن تطبيق التسمية [يدويا](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) [أو تلقائيا](apply-sensitivity-label-automatically.md).

> [!TIP]
> يمكنك أيضا تحديد أن التسمية هي تسمية الحساسية الافتراضية التي يجب تطبيقها على المواقع الجديدة أو المستندات الجديدة، كم إعداد [نهج تسمية](sensitivity-labels.md#what-label-policies-can-do).

### <a name="powershell-tips-for-specifying-the-advanced-settings"></a>تلميحات PowerShell لتحديد الإعدادات المتقدمة

على الرغم من أنه يمكنك تحديد تسمية الحساسية حسب اسمها، إلا أننا نوصي باستخدام التسمية GUID لتجنب الإرباك المحتمل حول تحديد اسم التسمية أو اسم العرض. للعثور على GUID وتأكيد نطاق التسمية:

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid, ContentType
````

لإزالة أي من هذه الإعدادات المتقدمة من تسمية الحساسية، استخدم بناء جملة المعلمة AdvancedSettings نفسه، ولكن حدد قيمة سلسلة فارغة. على سبيل المثال:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope=""}
````

