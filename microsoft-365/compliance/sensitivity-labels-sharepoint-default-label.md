---
title: تكوين وصف حساسية افتراضي لمكتبة مستندات SharePoint
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: تكوين وصف حساسية افتراضي لمكتبة مستندات SharePoint للمستندات الجديدة وغير المسماة.
ms.openlocfilehash: cbe3dab1ff70b55f85727649883beab0d2fdc456
ms.sourcegitcommit: 61df6377a6185a8b55e668cfb81adbd8462a9cce
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/29/2022
ms.locfileid: "67171405"
---
# <a name="configure-a-default-sensitivity-label-for-a-sharepoint-document-library"></a>تكوين وصف حساسية افتراضي لمكتبة مستندات SharePoint

>*[إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> يتم نشر هذه الميزة تدريجيا في المعاينة وتخضع للتغيير. كما أنها ميزة متميزة مع تفاصيل الترخيص التي سيتم توفيرها عندما تصبح الميزة متاحة بشكل عام (GA).
> 
> لقراءة إعلان المعاينة، راجع [منشور Yammer](https://www.yammer.com/askipteam/threads/1846702701985792).

عند تمكين SharePoint [لأوصاف الحساسية](sensitivity-labels-sharepoint-onedrive-files.md)، يمكنك تكوين تسمية افتراضية لمكتبات المستندات. بعد ذلك، سيتم تطبيق هذه التسمية على أي ملفات جديدة تم تحميلها إلى تلك المكتبة، أو الملفات الموجودة التي تم تحريرها في المكتبة إذا لم يكن لها بالفعل وصف حساسية، أو إذا كانت لها تسمية حساسية ولكن [مع أولوية أقل](sensitivity-labels.md#label-priority-order-matters).

على سبيل المثال، يمكنك تكوين التسمية **السرية** كتسمية الحساسية الافتراضية لمكتبة المستندات. يحفظ المستخدم الذي لديه **"عام** " كتسمية افتراضية للنهج ملفا جديدا في تلك المكتبة. سيقوم SharePoint بتسمية هذا الملف على أنه **سري** بسبب الأولوية الأعلى لتلك التسمية. للحصول على ملخص سريع للنتائج المحتملة، راجع ["هل سيتم تجاوز تسمية موجودة](#will-an-existing-label-be-overridden) " على هذه الصفحة.

توفر التسمية الافتراضية مستوى أساسيا من الحماية ونموذجا للتسمية التلقائية دون فحص المحتوى. لمساعدتك على التمييز بين التسمية الافتراضية لهذه الميزة والتسمية الافتراضية في نهج التسمية:

- **وصف الحساسية الافتراضي لمكتبة مستندات**: التسمية المستندة إلى الموقع، تنطبق فقط على SharePoint. تجاوز تسمية ذات أولوية أقل ما لم يتم تطبيقها يدويا.
- **وصف الحساسية الافتراضي من نهج**: قابل للتطبيق دائما على جميع المواقع. لا تتجاوز تسمية موجودة أبدا.

عند استخدام Office على الويب لإنشاء ملف أو تحريره، يمكن تطبيق وصف الحساسية الافتراضي لمكتبة المستندات دون تأخير. ومع ذلك، لا تكون التسمية فورية إذا قمت بتحميل ملف أو إنشائه باستخدام Microsoft 365 Apps على Windows أو macOS أو iOS أو Android، ثم حفظه في SharePoint:

- تحميل الملف: قد يستغرق تطبيق التسمية بضع دقائق.
- Microsoft 365 Apps: يتم تطبيق التسمية بعد إغلاق التطبيق.

## <a name="will-an-existing-label-be-overridden"></a>هل سيتم تجاوز تسمية موجودة؟

ملخص النتائج:

|تسمية موجودة |تجاوز باستخدام التسمية الافتراضية للمكتبة |
|:-----|:-----|:-----|
|مطبق يدويا، أي أولوية| لا |
|مطبق تلقائيا، أولوية أقل | نعم |
|مطبق تلقائيا، أولوية أعلى | لا |
|التسمية الافتراضية من النهج، أولوية أقل | نعم |
|التسمية الافتراضية من النهج، أولوية أعلى | لا |

## <a name="requirements"></a>المتطلبات

- لقد قمت [بتمكين تسميات الحساسية لملفات Office في SharePoint وOneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

- [لم يتم تمكين إدارة حقوق استخدام معلومات SharePoint (IRM) للمكتبة](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists). هذه التقنية القديمة غير متوافقة مع استخدام وصف حساسية افتراضي لمكتبة مستندات SharePoint. إذا تم تمكين مكتبة ل IRM، فلن تتمكن من تحديد تسمية حساسية افتراضية.

## <a name="limitations"></a>القيود

- لا ينطبق على الملفات الموجودة الثابتة في SharePoint.

- إلا إذا قمت [بتمكين التأليف المشترك للملفات المشفرة بتسميات الحساسية](sensitivity-labels-coauthoring.md)، فسترى تأخيرا في تطبيق وصف الحساسية الافتراضي لمكتبة المستندات عندما يحدد المستخدمون الخيار **"حفظ** **الملف**\>".

- كما هو الحال مع تسميات الحساسية Office على الويب، فإن بعض [تكوينات التسميات التي تطبق التشفير](encryption-sensitivity-labels.md#configure-encryption-settings) غير مناسبة ل SharePoint، وبالتالي لا تدعم تسمية حساسية افتراضية لمكتبة مستندات SharePoint:
    - **اسمح للمستخدمين بتعيين الأذونات عند تطبيق التسمية** وعلبة الاختيار **في Word وPowerPoint وExcel، مطالبة المستخدمين بتحديد الأذونات المحددة** . يشار إلى هذا الإعداد أحيانا باسم "الأذونات المعرفة من قبل المستخدم".
    - **يتم تعيين صلاحية وصول المستخدم إلى المحتوى** إلى قيمة أخرى غير **Never**.
    - تم تحديد **تشفير المفتاح المزدوج**.

## <a name="how-to-configure-a-default-sensitivity-label-for-a-sharepoint-document-library"></a>كيفية تكوين وصف حساسية افتراضي لمكتبة مستندات SharePoint

لمكتبة مستندات موجودة:

1. في SharePoint، انتقل إلى مكتبة المستندات > **الإعدادات**.

2. من الجزء المنبثق **لإعدادات المكتبة** ، حدد **تسميات الحساسية الافتراضية**، ثم حدد تسمية من مربع القائمة المنسدلة. على سبيل المثال:
    
    ![لقطة شاشة تعرض تكوين وصف حساسية افتراضي لمكتبة SharePoint.](../media/default-sensitivity-label-spo2.png)
    
    على الرغم من أنك ترى دعم الإشارات إلى الإعدادات لملفات PDF، فإن نوع الملف هذا غير معتمد حاليا لهذا السيناريو.

إذا كنت تقوم بإنشاء مكتبة مستندات جديدة، يمكنك تكوين نفس إعداد **تسميات الحساسية الافتراضية** من جزء القائمة **المنبثقة "إنشاء مكتبة مستندات** ".

> [!NOTE]
> يتم نشر هذه الإعدادات الجديدة تدريجيا للمستأجرين. إذا لم تتمكن من رؤيتها، فحاول مرة أخرى بعد بضعة أيام.

## <a name="monitoring-application-of-library-default-sensitivity-labels"></a>مراقبة تطبيق تسميات الحساسية الافتراضية للمكتبة

استخدم العمود " **حساسية** SharePoint" لمشاهدة أسماء تسميات الحساسية المطبقة على الملفات. عند تطبيق التسمية بواسطة هذه الميزات، يعرض تعريف الأدوات لاسم التسمية **هذا الملف تلقائيا**. ومع ذلك، فإن تعريف الأدوات هذا ليس حصريا لتسمية الحساسية الافتراضية لمكتبة المستندات. كما يعرض عند تطبيق أوصاف الحساسية باستخدام نهج التسمية التلقائية أو كنتيجة للتسمية الافتراضية للمستخدم من نهج تسمية الحساسية.

لتحديد وقت تطبيق التسمية على وجه التحديد بسبب تسمية الحساسية الافتراضية للمكتبة، استخدم [سجل التدقيق في مدخل التوافق](search-the-audit-log-in-security-and-compliance.md) وحدث تدقيق **ملف وصف الحساسية المطبقة** من مجموعة **أنشطة وصف الحساسية** . ثم:
1. حدد إدخالا لعرض التفاصيل في جزء القائمة المنبثقة.

2. من جزء التفاصيل، قم بالتمرير إلى **قسم SensitivityLabelEventData**، وحدد قيمة **ActionScourceDetails**.

3. يتم استخدام قيمة **6** عند تطبيق التسمية بسبب وصف الحساسية الافتراضي لمكتبة المستندات.

لتدقيق إعداد التكوين لهذه الميزة، استخدم حدث تدقيق **القائمة المحدثة** من مجموعة **أنشطة قائمة SharePoint** . في جزء القائمة المنبثقة للتفاصيل لمكتبة المستندات، قم بالتمرير إلى قسم **SensitivityLabelEventData** حيث يمكن أن يعكس **OldSensitivityLabeld** و **SensitivityLabelId** ثلاثة تغييرات في الحالات:

- تم تطبيق وصف الحساسية
- تم تغيير تسمية الحساسية من تسمية إلى أخرى
- تمت إزالة تسمية الحساسية

لتعيين معرفات GUID لتسمية الحساسية إلى أسماء التسميات، استخدم [Get-Label](/powershell/module/exchange/get-label) cmdlet:

1. أولا، [اتصل Office 365 Security & Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. ثم قم بتشغيل الأمر التالي، حيث يمكنك تحديد GUID:

    ```powershell
    Get-Label -Identity "<GUID>" | Name

## Next steps

Default labeling ensures a minimum level of protection but doesn't take into account the file contents that might require a higher level of protection. Consider supplementing this labeling method with [automatic labeling](apply-sensitivity-label-automatically.md) that uses content inspection, and encourage [manual labeling](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) for users to replace the default label when needed.