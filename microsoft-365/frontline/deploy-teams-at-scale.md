---
title: توزيع الفرق على نطاق واسع للعاملين في الخطوط الأمامية في Microsoft Teams
author: LanaChin
ms.author: v-lanachin
ms.reviewer: rahuldey
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على كيفية نشر الفرق على نطاق واسع للعاملين في الخطوط الأمامية في مؤسستك.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 28232f888b925b6a0f930d464b1dcdfca00b2c3b
ms.sourcegitcommit: af6c13d7ab1fe440dd45ce8cd3940774cdda66ef
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/25/2022
ms.locfileid: "67004225"
---
# <a name="deploy-teams-at-scale-for-frontline-workers-in-microsoft-teams"></a>توزيع الفرق على نطاق واسع للعاملين في الخطوط الأمامية في Microsoft Teams

> [!NOTE]
> هذه الميزة قيد المعاينة العامة حاليا. إذا كنت ترغب في المشاركة، فتواصل معنا في [dscale@microsoft.com](mailto:dscale@microsoft.com).

## <a name="overview"></a>نظرة عامة
 
قد يكون لدى مؤسستك الكثير من الفرق التي تستخدمها لدفع التواصل والتعاون بين القوى العاملة في الواجهة الأمامية، والتي تنتشر عبر متاجر ومواقع وأدوار مختلفة. حاليا، لا يوجد حل سهل لنشر هذه الفرق والمستخدمين وإعدادهم وإدارتهم على نطاق واسع.

نحن نبني حلا لتمكين المسؤولين من نشر الفرق وإدارتها على نطاق واسع.

فيما يلي نظرة عامة على القدرات المتاحة اليوم لإنشاء وإدارة أعداد كبيرة من الفرق في كل مرة وما نخطط له في المستقبل القريب.

||متوفر اليوم |لاحقا في عام 2022  |
|---------|---------|---------|
|**عدد الفرق التي يمكنك إنشاؤها لكل دفعة**|حتى 100 |حتى 500|
|**عدد المستخدمين الذين يمكنك إضافتهم لكل فريق**|حتى 25|حتى 25|

يتيح لك نشر الفرق على نطاق واسع ما يلي:

- إنشاء فرق باستخدام قوالب تم إنشاؤها مسبقا أو قوالب مخصصة خاصة بك.
- إضافة مستخدمين إلى الفرق كملاك أو أعضاء.
- إدارة الفرق على نطاق واسع عن طريق إضافة مستخدمين أو إزالتهم من الفرق الموجودة.
- ابق على إعلامك عبر البريد الإلكتروني، بما في ذلك الإكمال والحالة والأخطاء (إن وجدت). يمكنك اختيار إعلام ما يصل إلى خمسة أشخاص بحالة كل دفعة من الفرق التي تنشرها. يتم إعلام مالكي الفريق وأعضاء الفريق تلقائيا عند إضافتهم إلى فريق.

## <a name="how-to-deploy-teams-at-scale"></a>كيفية نشر الفرق على نطاق واسع

> [!NOTE]
> قبل نشر فرقك، تأكد من أن جميع مالكي الفرق لديهم ترخيص Teams.

اتبع هذه الخطوات لنشر عدد كبير من الفرق في كل مرة.

### <a name="step-1-prepare-your-csv-files"></a>الخطوة 1: إعداد ملفات CSV

ستحتاج إلى إنشاء ملفي CSV لكل دفعة من الفرق التي تقوم بنشرها:

- **ملف CSV الذي يحدد الفرق التي تقوم بإنشائه**. يجب أن يحتوي هذا الملف على هذه الأعمدة المطلوبة، بالترتيب التالي، بدءا من العمود الأول:

    |اسم العمود  |الوصف  |
    |---------|---------|
    |**اسم الفريق**|اسم الفريق.|
    |**معرف الفريق الموجود**|إذا كنت تقوم بإضافة مستخدمين أو إزالتهم من فريق موجود، فحدد معرف الفريق الخاص بالفريق.|
    |**الرؤيه**|سواء كان الفريق عاما (يمكن لأي شخص في مؤسستك الانضمام إليه) أو خاصا (يحتاج المستخدمون إلى موافقة مالكي الفريق للانضمام). الخيارات **عامة** **وخاصة.**|
    |**معرف قالب الفريق**|إذا كنت تقوم بإنشاء فريق من قالب مخصص أو تم إنشاؤه مسبقا، فحدد معرف قالب الفريق. راجع [بدء استخدام قوالب الفريق في مركز إدارة Teams](/microsoftteams/get-started-with-teams-templates-in-the-admin-console) للحصول على قائمة بقوالب الفريق ومعرفه التي تم إنشاؤها مسبقا. إذا كنت تريد استخدام قالب الفريق الافتراضي القياسي، فاتركه فارغا.|

- **ملف CSV يعين المستخدمين الذين تضيفهم إلى كل فريق**. يجب أن يحتوي هذا الملف على هذه الأعمدة المطلوبة، بالترتيب التالي، بدءا من العمود الأول:

    |اسم العمود  |الوصف  |
    |---------|---------|
    |**اسم المستخدم الكامل**|اسم العرض للمستخدم.|
    |**المستخدم UPN أو المعرف**|اسم المستخدم الأساسي (UPN) أو معرف المستخدم. على سبيل المثال، averyh@contoso.com.|
    |**اسم الفريق**|اسم الفريق.|
    |**نوع الإجراء**|سواء كنت تقوم بإضافة المستخدم أو إزالته من الفريق. الخيارات هي **AddMember** و **RemoveMember**.|
    |**المالك أو العضو**|سواء كان المستخدم مالك فريق أو عضوا في الفريق. الخيارات هي **المالك** **والفرد**.|

#### <a name="examples"></a>أمثلة

استخدم الأمثلة التالية لمساعدتك في إنشاء ملفات CSV. هنا، قمنا بتسمية الملفات، Teams.csv Users.csv.

**Teams.csv**

|اسم الفريق|معرف الفريق الموجود|الرؤيه|معرف قالب الفريق|
|---------|---------|---------|---------|
|متجر Contoso 1||العامه|com.microsoft.teams.template.retailStore|
|متجر Contoso 2||العامه|com.microsoft.teams.template.retailStore|
|متجر Contoso 3||العامه|com.microsoft.teams.template.retailStore|
|متجر Contoso 4||العامه|com.microsoft.teams.template.retailStore|
|متجر Contoso 5||العامه|com.microsoft.teams.template.ManageAProject|
|متجر Contoso 6||العامه|com.microsoft.teams.template.ManageAProject|
|متجر Contoso 7||العامه||
|متجر Contoso 8||الخاصه|com.microsoft.teams.template.OnboardEmployees|
|متجر Contoso 9||الخاصه|com.microsoft.teams.template.OnboardEmployees|
|متجر Contoso 10||الخاصه|com.microsoft.teams.template.OnboardEmployees|

**Users.csv**

|اسم المستخدم الكامل |المستخدم UPN أو المعرف|اسم الفريق|نوع الإجراء|المالك أو العضو|
|---------|---------|---------|---------|---------|
|Avery هوارد|averyh@contoso.com|متجر Contoso 1|AddMember|مالك|
|Casey Jensen|caseyj@contoso.com|متجر Contoso 2|AddMember|مالك|
|Jessie Irwin|jessiei@contoso.com|متجر Contoso 3|AddMember|مالك|
|Manjeet Bhatia|manjeetb@contoso.com|متجر Contoso 4|AddMember|مالك|
|Mikaela Lee|mikaelal@contoso.com|متجر Contoso 5|AddMember|مالك|
|Morgan Conners|morganc@contoso.com|متجر Contoso 6|AddMember|الاعضاء|
|جناح الجناح|oscarw@contoso.com|متجر Contoso 7|AddMember|الاعضاء|
|Rene Pelletier|renep@contoso.com|متجر Contoso 8|AddMember|الاعضاء|
|سيدني ماتوس|sydneym@contoso.com|متجر Contoso 9|AddMember|الاعضاء|
|Violet Martinez|violetm@contoso.com|متجر Contoso 10|AddMember|الاعضاء|

### <a name="step-2-deploy-your-teams"></a>الخطوة 2: نشر فرقك

الآن بعد أن قمت بإنشاء ملفات CSV الخاصة بك، فأنت مستعد لإعداد بيئتك ونشر فرقك.

يمكنك استخدام ```New-CsBatchTeamsDeployment``` cmdlet لإرسال دفعة من الفرق لإنشائها. يتم إنشاء معرف تزامن لكل دفعة. يمكنك بعد ذلك استخدام ```Get-CsBatchTeamsDeployment``` cmdlet لتعقب تقدم كل دفعة وحالتها.

1. تثبيت الإصدار 7 من PowerShell أو إصدار أحدث. للحصول على إرشادات خطوة بخطوة، راجع [تثبيت PowerShell على Windows](/powershell/scripting/install/installing-powershell-on-windows).
1. تشغيل PowerShell في وضع المسؤول.
1. قم بتشغيل ما يلي لإلغاء تثبيت أي وحدة نمطية مثبتة مسبقا في Teams PowerShell.

    ```powershell
    Uninstall-module -Name MicrosoftTeams -Force -Allversions
    ```

    إذا تلقيت رسالة خطأ، فأنت معين بالفعل. انتقل إلى الخطوة التالية.
1. قم بتنزيل [أحدث إصدار معاينة من الوحدة النمطية Teams PowerShell](https://www.powershellgallery.com/packages/MicrosoftTeams) وتثبيته. يجب تشغيل الإصدار 4.3.1 (معاينة) أو إصدار معاينة أحدث.  

1. قم بتشغيل ما يلي للاتصال ب Teams.

    ```powershell
    Connect-MicrosoftTeams
    ```

    عند مطالبتك، سجل الدخول باستخدام بيانات اعتماد المسؤول.

1. قم بتشغيل ما يلي للحصول على قائمة بالأوامر في الوحدة النمطية Teams PowerShell.

    ```powershell
    Get-Command -Module MicrosoftTeams
    ```

    تحقق من ذلك ```New-CsBatchTeamsDeployment``` ومن ```Get-CsBatchTeamsDeployment``` إدراجه.

1. قم بتشغيل ما يلي لنشر دفعة من الفرق. في هذا الأمر، يمكنك تحديد المسار إلى ملفات CSV وعناوين البريد الإلكتروني لما يصل إلى خمسة مستلمين لإعلامهم بهذا النشر.

    ```powershell
    New-CsBatchTeamsDeployment -TeamsFilePath "Your CSV file path" -UsersFilePath "Your CSV file path" -UsersToNotify "Email addresses" 
    ```

    على سبيل المثال:

    ```powershell
    New-CsBatchTeamsDeployment -TeamsFilePath "C:\dscale\Teams.csv" -UsersFilePath "C:\dscale\Users.csv" -UsersToNotify "adminteams@contoso.com,adelev@contoso.com"
    ```

    سيتلقى المستلمون إعلامات بالبريد الإلكتروني حول حالة النشر. يحتوي البريد الإلكتروني على معرف التزامن للدفعة التي أرسلتها وأي أخطاء قد تكون حدثت.

1. قم بتشغيل ما يلي للتحقق من حالة الدفعة التي أرسلتها.

    ```powershell
    Get-CsBatchTeamsDeploymentStatus -OrchestrationId "OrchestrationId"
    ```

## <a name="send-us-feedback"></a>إرسال ملاحظات إلينا

نحن نقدر ملاحظاتك. قابلية الاستخدام والموثوقية والأداء&mdash;نرحب بها جميعا!

[dscale@microsoft.com](mailto:dscale@microsoft.com) البريد الإلكتروني وقم بتضمين معرف التزامن وملف الخطأ، إذا كان لديك.

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة على Teams PowerShell](/microsoftteams/teams-powershell-overview)
