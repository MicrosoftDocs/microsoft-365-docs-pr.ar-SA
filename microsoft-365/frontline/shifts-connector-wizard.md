---
title: استخدم معالج موصل Shifts لتوصيل الورديات ب Blue Yonder Workforce Management
author: lanachin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على كيفية استخدام معالج موصل Shifts لدمج Shifts في Teams مع Workforce Management Blue Yonder.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 8c4aa1036af00eaaf7d776c267648141bf4db733
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823667"
---
# <a name="use-the-shifts-connector-wizard-to-connect-shifts-to-blue-yonder-workforce-management"></a>استخدم معالج موصل Shifts لتوصيل الورديات ب Blue Yonder Workforce Management

## <a name="overview"></a>نظرة عامة

يمكنك معالج موصل Shifts في مركز مسؤولي Microsoft 365 من دمج تطبيق Shifts في Microsoft Teams مع نظام إدارة القوى العاملة (WFM). بعد إعداد اتصال، يمكن للعاملين في الخطوط الأمامية عرض جداولهم وإدارتها بسلاسة في نظام WFM من داخل الورديات.

يقوم المعالج بتكوين موصل Shifts، وإنشاء اتصال بنظام WFM، وتطبيق إعدادات المزامنة وتعيينات الفريق التي تختارها. تحدد إعدادات المزامنة معلومات الجدولة التي تتم مزامنتها بين نظام WFM والورديات. تحدد تعيينات الفريق علاقة المزامنة بين مثيلات WFM والفرق في Teams. يمكنك التعيين إلى الفرق الموجودة والفرق الجديدة.

يمكنك إعداد اتصالات متعددة، لكل منهما إعدادات مزامنة مختلفة. على سبيل المثال، إذا كانت مؤسستك تحتوي على مواقع متعددة ذات متطلبات جدولة مختلفة، قم بإنشاء اتصال بإعدادات مزامنة فريدة لكل موقع. ضع في اعتبارك أنه لا يمكن تعيين مثيل WFM إلا لفريق واحد في أي وقت. إذا تم تعيين مثيل WFM بالفعل إلى فريق، فلا يمكن تعيينه إلى فريق آخر.

باستخدام نظام WFM كنظام سجل، يمكن للعاملين في الخطوط الأمامية رؤية الورديات وتبديلها، وإدارة توفرهم، وطلب الإجازة في الورديات على أجهزتهم. يمكن لمديري الخطوط الأمامية الاستمرار في استخدام نظام WFM لإعداد الجداول.

## <a name="integrate-shifts-with-blue-yonder-workforce-management"></a>دمج الورديات مع Workforce Management Yonder الأزرق

حاليا، يدعم المعالج [موصل Microsoft Teams Shifts ل Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder). يمكنك هذا الموصل من دمج Shifts مع Workforce Management Blue Yonder (WFM Blue Yonder) لإدارة جداولك وإبقائها محدثة. في هذه المقالة، نرشدك إلى كيفية تشغيل المعالج لإعداد اتصال ب Blue Yonder WFM من خلال الموصل.

> [!NOTE]
> يمكنك أيضا استخدام PowerShell لدمج Shifts مع WFM Blue Yonder. لمعرفة المزيد، راجع [استخدام PowerShell لتوصيل Shifts ب Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md).

## <a name="before-you-begin"></a>قبل البدء

يجب أن تكون مسؤولا عموميا في Microsoft 365 لتشغيل المعالج.

### <a name="prerequisites"></a>المتطلبات الأساسية
<a name="prerequisites"> </a>
[!INCLUDE [shifts-connector-prerequisites](includes/shifts-connector-prerequisites.md)]

- لا تتوفر للفرق التي تريد تعيينها أي جداول. إذا كان لدى الفريق جدول زمني موجود، [فقم بإزالة الجدول من الفريق](#remove-schedules-from-teams-you-want-to-map) قبل تعيين مثيل WFM أزرق له. وإلا، فسترى ورديات مكررة.

## <a name="remove-schedules-from-teams-you-want-to-map"></a>إزالة الجداول الزمنية من الفرق التي تريد تعيينها
<a name="remove_schedules"> </a>

> [!NOTE]
> أكمل هذه الخطوة إذا كنت تقوم بتعيين مثيلات Blue Yonder WFM إلى الفرق الموجودة التي لديها جداول. إذا كنت تقوم بتعيين فرق لا تحتوي على أي جداول أو إذا كنت تقوم بإنشاء فرق جديدة لتعيينها، يمكنك تخطي هذه الخطوة.

استخدم PowerShell لإزالة الجداول من الفرق.

1. أولا، ستحتاج إلى تثبيت وحدات PowerShell والحصول على إعداد. اتبع الخطوات [لإعداد بيئتك](shifts-connector-powershell-manage.md#set-up-your-environment).
1. قم بتنفيذ الأمر التالي:

    ```powershell
    Remove-CsTeamsShiftsScheduleRecord -TeamId <Teams team ID> -DateRangeStartDate <start time> -DateRangeEndDate <end time> -ClearSchedulingGroup:$false -EntityType <the scenario entities that you want to remove, the format is @(scenario1, scenario2, ...)> -DesignatedActorId <Teams team owner ID>
    ```

    للحصول على قائمة بسيناريوهات المعلمة `EntityType` ، قم بتشغيل [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector). ستتم إزالة بيانات الجدولة لنطاق التاريخ والوقت الذي تحدده.

لمعرفة المزيد، راجع [Remove-CsTeamsShiftsScheduleRecord](/powershell/module/teams/remove-csteamsshiftsschedulerecord).

## <a name="run-the-wizard"></a>تشغيل المعالج

### <a name="get-started"></a>بدء الاستخدام

1. في جزء التنقل الأيمن [من مركز مسؤولي Microsoft 365](https://admin.microsoft.com/)، اختر **"إعداد**"، ثم انتقل إلى قسم **التطبيقات والبريد الإلكتروني**.
1. حدد **توصيل نظام إدارة القوى العاملة.** هنا، يمكنك معرفة المزيد حول موصلات Shifts وتجربة عامل الخط الأمامي والمدير عند توصيل الورديات بنظام WFM.
    :::image type="content" source="media/shifts-connector-wizard-get-started.png" alt-text="لقطة شاشة لصفحة التفاصيل لمعالج موصل Shifts في مركز مسؤولي Microsoft 365." lightbox="media/shifts-connector-wizard-get-started.png":::
1. عندما تصبح جاهزا، حدد **"بدء الاستخدام**".
1. حدد **"التالي**" لإنشاء اتصال WFM أزرق.

### <a name="enter-connection-details"></a>أدخل تفاصيل الاتصال
<a name="connection_details"> </a>

1. في صفحة تفاصيل الاتصال، أدخل اسما فريدا لاتصالك. لا يمكن أن يزيد طولها عن 128 حرفا أو أن تحتوي على أي أحرف خاصة.
    :::image type="content" source="media/shifts-connector-wizard-connection-details.png" alt-text="لقطة شاشة لصفحة تفاصيل الاتصال للمعالج، تعرض إعدادات الاتصال." lightbox="media/shifts-connector-wizard-connection-details.png":::
1. أدخل اسم حساب خدمة WFM الأزرق وكلمة المرور وعناوين URL للخدمة.
1. عند الانتهاء، حدد **"التالي** " لاختبار الاتصال بالإعدادات التي أدخلتها.

### <a name="choose-sync-settings"></a>اختيار إعدادات المزامنة
<a name="sync"> </a>

في صفحة إعدادات المزامنة، يمكنك اختيار المعلومات التي تريد مزامنتها من WFM Blue Yonder إلى Shifts وتكرار المزامنة وما إذا كان بإمكان مستخدمي Shifts إجراء تغييرات على البيانات.

1. أدخل حساب نظام Microsoft 365.
    :::image type="content" source="media/shifts-connector-wizard-sync-settings.png" alt-text="لقطة شاشة لصفحة إعدادات المزامنة للمعالج، تعرض إعدادات المزامنة." lightbox="media/shifts-connector-wizard-sync-settings.png":::
<a name="email"> </a>
1. ضمن **مستلمي إعلامات البريد الإلكتروني**، اختر من يتلقى إعلامات البريد الإلكتروني حول هذا الاتصال. يمكنك إضافة مستخدمين ومجموعات فردية. تحتوي إعلامات البريد الإلكتروني على معلومات حول حالة إعداد الاتصال وأي مشاكل أو أخطاء قد تحدث بعد إعداد الاتصال.
1. اختر إعدادات المزامنة:
    1. ضمن **الجدول والورديات**، اختر بيانات WFM Blue Yonder التي يمكن للمستخدمين الاطلاع عليها أو تغييرها، ثم قم بتعيين تكرار المزامنة.
    2. ضمن **"الطلبات"**، اختر أنواع الطلبات التي يمكن للمستخدمين الورديات رؤيتها وإنشائها.

    > [!IMPORTANT]
    > إذا اخترت أيا من الخيارات التالية لتعطيل الورديات المفتوحة أو طلبات الوردية المفتوحة أو طلبات التبديل أو طلبات الإجازة، فهناك خطوة أخرى تحتاج إلى القيام بها لإخفاء الإمكانية في الورديات.
    >
    > - الورديات المفتوحة: **لن يرى المستخدمون الورديات بيانات WFM Blue Yonder**
    > - طلبات التبديل: **تم تعطيل الميزة لكافة المستخدمين**
    > - طلبات الإجازة: **تم تعطيل الميزة لكافة المستخدمين**
    >
    > بعد تشغيل المعالج، تأكد من اتباع الخطوات الواردة في قسم [تعطيل الورديات المفتوحة وفتح طلبات الورديات وطلبات التبديل وطلبات الإجازة](#disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests) لاحقا في هذه المقالة.
 
1. عند الانتهاء من اختيار الإعدادات، حدد **"إنشاء اتصال**".

### <a name="map-blue-yonder-workforce-management-instances-to-teams"></a>تعيين مثيلات Workforce Management أزرق إلى الفرق
<a name="sites"> </a>

اختر المثيلات WFM الزرقاء التي تريد الاتصال بها، ثم قم بتعيين كل مثيل إلى فريق في Teams. يمكنك تعيين ما يصل إلى 100 مثيل. هناك طريقتان يمكنك من خلالهما القيام بذلك:

- [تعيين المثيلات يدويا إلى الفرق](#manually-map-instances-to-teams)
- [إعداد ملف CSV الذي يحدد تعييناتك وتحميله](#use-a-csv-file-to-map-instances-to-teams)

#### <a name="manually-map-instances-to-teams"></a>تعيين المثيلات يدويا إلى الفرق

حدد المثيلات التي تريد تعيينها.

:::image type="content" source="media/shifts-connector-wizard-sites.png" alt-text="لقطة شاشة للمعالج، تعرض قائمة مثيلات WFM Blue Yonder." lightbox="media/shifts-connector-wizard-sites.png":::
<a name="mapping"> </a>
<a name="search_teams"> </a> ثم قم بتعيين كل مثيل إلى فريق في Teams. يمكنك تعيين مثيل لفريق موجود أو يمكنك إنشاء فريق جديد.
:::image type="content" source="media/shifts-connector-wizard-search-team.png" alt-text="لقطة شاشة للجزء الذي يعرض خيار فريق البحث وإنشاء خيار فريق جديد." lightbox="media/shifts-connector-wizard-search-team.png":::

##### <a name="to-map-an-instance-to-an-existing-team"></a>لتعيين مثيل إلى فريق موجود

1. حدد اسم المثيل.
2. في الجزء، ابحث عن الفريق، ثم حدده. ضع في اعتبارك أن الفرق التي تم تعيينها بالفعل إلى مثيل في هذا الاتصال لا تظهر في البحث.
3. اختر المنطقة الزمنية وأقرب مدينة.
4. حدد **"حفظ"**، ثم حدد **"التالي**".

##### <a name="to-map-an-instance-to-a-new-team"></a>لتعيين مثيل لفريق جديد

1. حدد اسم المثيل.
2. في الجزء، اختر **"إنشاء فريق جديد**". سيتم نقلك إلى علامة تبويب جديدة في المستعرض حيث يمكنك إنشاء فريق جديد في مركز مسؤولي Microsoft 365.
    1. أدخل اسما ووصفا اختياريا للفريق.
    1. إضافة مالك فريق واحد أو أكثر. تأكد من إضافة حساب نظام Microsoft 365 كمالك.
    1. إضافة أعضاء الفريق.
    1. أضف عنوان بريد إلكتروني للفريق واختر إعداد خصوصية.
    1. راجع الإعدادات، ثم اختر **"إضافة فريق**". عند إنشاء فريقك، اختر **"إغلاق**".
3. ارجع إلى المعالج وابحث عن الفريق الجديد الذي أنشأته ثم حدده.
4. اختر المنطقة الزمنية وأقرب مدينة.
5. حدد **"حفظ"**، ثم حدد **"التالي**".

#### <a name="use-a-csv-file-to-map-instances-to-teams"></a>استخدام ملف CSV لتعيين المثيلات إلى الفرق

1. حدد **التبديل إلى الوضع المجمع**.
1. حدد **تنزيل ملف قالب** لتنزيل قالب تعيين يمكنك استخدامه لتعريف التعيينات.

    :::image type="content" source="media/shifts-connector-wizard-mapping-file.png" alt-text="لقطة شاشة لصفحة ملف تحميل التعيين للمعالج." lightbox="media/shifts-connector-wizard-mapping-file.png":::

1. استخدم القالب لإنشاء ملف التعيين. يحتوي على هذه الأعمدة، بالترتيب التالي، بدءا من العمود الأول. تشير العلامة النجمية (*) إلى عمود مطلوب.

    |اسم العمود  |الوصف  |
    |---------|---------|
    |**معرف مثيل Yonder أزرق*** |معرف مثيل WFM الأزرق.|
    |**اسم مثيل Yonder أزرق**|اسم مثيل WFM الأزرق.|
    |**معرف الفريق*** |معرف الفريق.|
    |**اسم الفريق**|اسم الفريق.|
    |**المنطقة الزمنية*** |المنطقة الزمنية بتنسيق قاعدة بيانات tz. على سبيل المثال، أوروبا/لندن.|

    > [!NOTE]
    > تحتاج فقط إلى تعبئة الأعمدة المطلوبة (معرف مثيل Yonder الأزرق، معرف الفريق، المنطقة الزمنية) لتعيين المثيلات إلى الفرق.

    فيما يلي مثال على الشكل الذي يبدو عليه ملف التعيين.

    |معرف مثيل Yonder أزرق|اسم مثيل Yonder أزرق|معرف الفريق|اسم الفريق|المنطقة الزمنية|
    |---------|---------|---------|---------|---------|
    |2111|فريق Contoso الأمريكي|3a4d78a-2261|فريق الولايات المتحدة|أمريكا/Los_Angeles|
    |3212|فريق Contoso UK|2d1f6c2e-5272|فريق المملكة المتحدة|أوروبا/لندن|
    |4865||bfa6o89e-1328||أمريكا/تورونتو|

1. عند إنشاء ملف التعيين، حدد **"استعراض** " لتحميله. يقوم المعالج بالتحقق من صحة الملف. إذا عثر على أخطاء، فسترى قائمة بالأخطاء، ورسالة تطلب منك تصحيحها. وإلا، فسترى رسالة للمتابعة إلى الخطوة التالية.  
1. حدد **التالي**.

### <a name="review-and-finish"></a>المراجعة والانتهاء

راجع الإعدادات. إذا كنت بحاجة إلى إجراء تغييرات على أي تعيينات للفريق، فاختر **"تحرير"** للقيام بذلك. عندما تصبح جاهزا، حدد **"إنهاء**".

:::image type="content" source="media/shifts-connector-wizard-review.png" alt-text="Screenshot of the Review page of the wizard, showing mappings." lightbox="media/shifts-connector-wizard-review.png":::

سترى رسالة لتأكيد تلقينا طلبك مع معرف العملية. دون ملاحظة لمعرف العملية. ستحتاج إليها للتحقق من حالة إعداد الاتصال.

:::image type="content" source="media/shifts-connector-wizard-operation-id.png" alt-text="لقطة شاشة لصفحة المعالج، تظهر رسالة التأكيد ومعرف العملية." lightbox="media/shifts-connector-wizard-operation-id.png":::

يبدأ المعالج العملية لإعداد الاتصال وتعيين المثيلات إلى الفرق التي حددتها. قد تستغرق هذه العملية بعض الوقت لإكمالها. سيتلقى المستلمون الذين اخترتهم إعلامات بالبريد الإلكتروني حول حالة الإعداد.

حدد **"تم** " لإنهاء المعالج.

أنت في طريقك ولكنك لم تنتهي بعد! تأكد من التحقق من بريدك الإلكتروني. ستتلقى تأكيدا أننا تلقينا طلبك مع [ارتباط](shifts-connector-powershell-manage.md#check-connection-setup-status) إلى كيفية التحقق من حالة الإعداد.

> [!NOTE]
> إذا حدثت مشكلة أو خطأ في اتصال بعد إعداده، فسيتم إعلامك بالبريد الإلكتروني. اتبع الإرشادات الواردة في البريد الإلكتروني لاستكشاف المشكلة وإصلاحها.

## <a name="disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests"></a>تعطيل الورديات المفتوحة وطلبات الورديات المفتوحة وطلبات التبديل وطلبات الإجازة

> [!IMPORTANT]
> اتبع هذه الخطوات فقط إذا اخترت أيا من الخيارات التالية لتعطيل الورديات المفتوحة أو طلبات الوردية المفتوحة أو طلبات التبديل أو طلبات الإجازة في المعالج. يؤدي إكمال هذه الخطوة إلى إخفاء الإمكانية في Shifts.
>
> - الورديات المفتوحة: **لن يرى المستخدمون الورديات بيانات WFM Blue Yonder**
> - طلبات التبديل: **تم تعطيل الميزة لكافة المستخدمين**
> - طلبات الإجازة: **تم تعطيل الميزة لكافة المستخدمين**
>
> بدون هذه الخطوة الثانية، سيظل المستخدمون يرون الإمكانية في Shifts، وسيحصلون على رسالة خطأ "عملية غير معتمدة" إذا حاولوا استخدامها.

لإخفاء الورديات المفتوحة وطلبات التبديل وطلبات الإجازة في الورديات، استخدم [نوع مورد جدولة](/graph/api/resources/schedule) واجهة برمجة التطبيقات Graph لتعيين المعلمات ```false``` التالية لكل فريق قمت بتعيينه إلى مثيل WFM أزرق:

- الورديات المفتوحة: ```openShiftsEnabled```
- طلبات التبديل:  ```swapShiftsRequestsEnabled```
- طلبات الإجازة: ```timeOffRequestsEnabled```

لإخفاء طلبات الورديات المفتوحة في الورديات، انتقل إلى **الإعدادات** في الورديات، ثم أوقف تشغيل إعداد **"الورديات المفتوحة** ".

## <a name="if-you-need-to-make-changes-to-a-connection"></a>إذا كنت بحاجة إلى إجراء تغييرات على اتصال
<a name="update_connection"> </a>

بعد إعداد اتصال، يمكنك استخدام PowerShell لإجراء تغييرات عليه. على سبيل المثال، يمكنك تحديث إعدادات المزامنة وتعيينات الفريق وتعطيل المزامنة للاتصال. للحصول على إرشادات مفصلة خطوة بخطوة، راجع [استخدام PowerShell لإدارة اتصال Shifts ب Blue Yonder Workforce Management](shifts-connector-powershell-manage.md).

## <a name="related-articles"></a>المقالات ذات الصلة

- [موصلات الورديات](shifts-connectors.md)
- [استخدم PowerShell لإدارة اتصال الورديات ب Blue Yonder Workforce Management](shifts-connector-powershell-manage.md)
- [إدارة تطبيق الورديات في Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
