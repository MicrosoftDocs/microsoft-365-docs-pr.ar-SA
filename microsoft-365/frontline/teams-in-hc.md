---
title: بدء استخدام Microsoft 365 لمؤسسات الرعاية الصحية
author: samanro
ms.author: samanro
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365solution-healthcare
- m365solution-overview
- m365-frontline
- m365solution-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: ''
description: تعرف على ميزات التطبيب عن بعد في Microsoft 365 وMicrosoft Teams وكيف يمكنك تنفيذها في مؤسسة الرعاية الصحية.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 01bd5b5c9386869e78b23da81d6e7cc48ecc16c8
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823649"
---
# <a name="get-started-with-microsoft-365-for-healthcare-organizations"></a>بدء استخدام Microsoft 365 لمؤسسات الرعاية الصحية

يقدم Microsoft 365 وMicrosoft Teams عددا من ميزات التطبيب عن بعد المفيدة للمستشفيات وغيرها من مؤسسات الرعاية الصحية. يتم تطوير ميزات Teams لمساعدة المستشفيات في:

- المواعيد الظاهرية وتكامل سجل الرعاية الصحية الإلكتروني (EHR)
- حزم نهج Teams
- المراسلة الآمنة
- قوالب Teams
- تنسيق الرعاية والتعاون

> [!NOTE]
> هذه الوظيفة هي أيضا جزء من Microsoft Cloud للرعاية الصحية. تعرف على المزيد حول استخدام هذا الحل، الذي يجمع بين القدرات من Azure و Dynamics 365 وMicrosoft 365 في [Microsoft Cloud for Healthcare](/industry/healthcare).

شاهد الفيديو التالي لمعرفة المزيد حول استخدام مجموعة الرعاية الصحية لتعزيز تعاون فريق الرعاية الصحية في Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hqan]

للاستفادة إلى أقصى استفادة من مؤسسة الرعاية الصحية، يمكنك أولا اختيار السيناريوهات التي يمكن أن يساعدك فيها Microsoft 365 وMicrosoft Teams في أنشطتك اليومية، ثم تأكد من إعداد بيئة Teams الخاصة بك بالأساسيات والفرق والتطبيقات المناسبة لدعم هذه السيناريوهات.

1. [اختر السيناريوهات التي](#scenarios-for-healthcare) تريد تنفيذها.
2. [إعداد Microsoft 365](flw-setup-microsoft-365.md) - إعداد العناصر الأساسية ل Microsoft 365 وMicrosoft Teams وأي خدمات أخرى تحتاج إليها.
3. [تكوين الخدمات والتطبيقات](flw-setup-microsoft-365.md#step-5-configure-apps-for-your-scenario) - استخدم قوالب الفريق لإعداد الفرق التي تحتاجها بسرعة، بما في ذلك القنوات والتطبيقات التي تحتاجها لعملك. أضف تطبيقات أخرى من Microsoft حسب الحاجة لدعم سيناريوهاتك.

## <a name="scenarios-for-healthcare"></a>سيناريوهات الرعاية الصحية

تتوفر السيناريوهات التالية لمؤسسات الرعاية الصحية:

| السيناريو | الوصف | الاحتياجات |
| -------- | -------- | -------- |
| [المواعيد الظاهرية مع تكامل سجل الرعاية الصحية الإلكتروني (EHR)](#virtual-appointments-and-electronic-healthcare-record-ehr-integration) | جدولة المواعيد الظاهرية وإدارتها وإجراءها مع المرضى. يربط هذا السيناريو Teams والنظام الأساسي Cerner أو Epic لدعم المواعيد الظاهرية. | اشتراك نشط في Microsoft Cloud for Healthcare أو اشتراك في عرض Microsoft Teams EHR المستقل للموصل. <br> يجب أن يكون لدى المستخدمين ترخيص Microsoft 365 أو Office 365 مناسب يتضمن اجتماعات Teams*. <br> يجب أن يكون لدى المؤسسات إصدار Cerner نوفمبر 2018 أو إصدار أحدث أو Epic من نوفمبر 2018 أو إصدار أحدث. <br>تفاصيل متطلبات [Cerner EHR](ehr-admin-cerner.md#before-you-begin) و [Epic EHR](ehr-admin-epic.md#before-you-begin) |
| [المواعيد الظاهرية مع Microsoft Bookings وتطبيق Bookings](#virtual-appointments-and-electronic-healthcare-record-ehr-integration) | جدولة المواعيد الظاهرية وإدارتها وإجراءها مع المرضى. يعتمد هذا السيناريو على Microsoft Bookings لدعم المواعيد الظاهرية. | يجب تشغيل Microsoft Bookings للمؤسسة. <br> يجب أن يكون لدى جميع مستخدمي تطبيق Bookings وجميع الموظفين المشاركين في الاجتماعات ترخيص يدعم جدولة اجتماع Teams*. <br>[تفاصيل متطلبات Bookings](/microsoftteams/bookings-app-admin#prerequisites-to-use-the-bookings-app-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)|
| [تنسيق الرعاية والتعاون](#care-coordination-and-collaboration) | يمكن للأطباء والموظفين التعاون داخليا على الجداول والمستندات والمهام وما إلى ذلك.| يجب أن يكون لدى المستخدمين ترخيص مناسب*. |

*Office 365 A3 و A5 وE3 وE5 وF1 وF3 Microsoft 365 A3 و A5 وE3 وE5، يتم دعم Business Standard. لمزيد من المعلومات حول ترخيص Teams العام، راجع [إدارة وصول المستخدم إلى Teams](/microsoftteams/user-access).

أو اختر من [بين سيناريوهات](flw-choose-scenarios.md) أخرى ل Microsoft 365 للعاملين في الخطوط الأمامية، مثل [اتصالات الشركة](flw-corp-comms.md) أو [بيئة العمل والمشاركة](flw-wellbeing-engagement.md).

واستفد من هذه الميزات التي تساعد Microsoft Teams على العمل في مؤسسة الرعاية الصحية:

| ميزه | الوصف | الاحتياجات |
| -------- | -------- | -------- |
| [حزم نهج Teams](#teams-policy-packages)| تأكد من أن العاملين الطبيين والعاملين في مجال المعلومات وأجهزة غرف المرضى لديهم حق الوصول المناسب إلى وظائف Teams.| يجب أن يكون لدى المستخدمين ترخيص مناسب*. |
| [المراسلة الآمنة](#secure-messaging) | اجذب انتباها أسرع إلى الرسائل العاجلة وكن واثقا من تلقي الرسالة وقراءتها. | يجب أن يكون لدى المستخدمين ترخيص مناسب*.  |
| [قوالب Teams](#teams-templates-for-healthcare-organizations) | أنشئ فرقا تتضمن قالبا معرفا مسبقا من الإعدادات والقنوات والتطبيقات المثبتة مسبقا للاتصال والتعاون داخل عنبر أو حجيرة أو قسم، أو بين أقسام وحاويات وأقسام متعددة داخل المستشفى. | يجب أن يكون لدى المستخدمين ترخيص مناسب*.  |

## <a name="virtual-appointments-and-electronic-healthcare-record-ehr-integration"></a>المواعيد الظاهرية وتكامل سجل الرعاية الصحية الإلكتروني (EHR)

استخدم النظام الأساسي للاجتماعات الكامل في Teams لجدولة المواعيد الظاهرية وإدارتها وإجراءها مع المرضى.

- إذا كانت مؤسستك تستخدم سجلات الحماية الإلكترونية أو EHR، يمكنك دمج Teams للحصول على تجربة أكثر سلاسة. يجعل موصل Teams Electronic Health Record (EHR) من السهل على الأطباء بدء موعد أو استشارة المريض الظاهري مع موفر آخر في Teams مباشرة من نظام EHR. لمعرفة المزيد، راجع [المواعيد الظاهرية مع Teams - التكامل في Cerner EHR](ehr-admin-cerner.md) [والمواعيد الظاهرية مع Teams - التكامل في Epic EHR](ehr-admin-epic.md).
- إذا كنت لا تستخدم EHR معتمدا، يمكنك استخدام Microsoft Bookings وتطبيق Bookings في Teams. لمعرفة المزيد، راجع [المواعيد الظاهرية باستخدام Teams وتطبيق Bookings](bookings-virtual-visits.md).

![المواعيد الظاهرية مع Microsoft Teams.](media/virtual-visits-teams.png)

## <a name="teams-policy-packages"></a>حزم نهج Teams

تطبيق حزم نهج Teams لتحديد الأدوار المختلفة التي يمكن أن تقوم بها في Teams. على سبيل المثال، حدد نهج ل:

- يحاسب العاملون الطبيون، مثل الممرضات المسجلات والممرضات والأطباء والعاملين الاجتماعيين، حتى يتمكنوا من الوصول الكامل إلى الدردشة والمكالمات وإدارة الورديات والاجتماعات.
- يمكن للعاملين في مجال المعلومات في مؤسسة الرعاية الصحية، مثل موظفي تكنولوجيا المعلومات، وموظفي المعلومات، والموظفين الماليين، ومسؤولي الامتثال، الوصول الكامل إلى الدردشة والمكالمات والاجتماعات.
- غرف المرضى، للتحكم في إعدادات أجهزة غرف المرضى.

لمعرفة المزيد، راجع [حزم نهج Teams للرعاية الصحية](/microsoftteams/policy-packages-healthcare?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

## <a name="secure-messaging"></a>المراسلة الآمنة

تدعم المراسلة الآمنة التعاون داخل الفرق الصحية، بما في ذلك العديد من الميزات الجديدة:

- يمكن لمرسل الرسالة تعيين أولوية خاصة لرسالته، بحيث يتم إعلام المستلم بشكل متكرر حتى يقرأ الرسالة.
- يمكن لمرسل الرسالة طلب إيصال بالقراءة، بحيث يتم إعلامه عند قراءة الرسالة التي أرسلها بواسطة مستلم الرسالة.

تسمح هذه الميزات معا بالانتباه بشكل أسرع إلى الرسائل العاجلة والثقة في تلقي الرسالة وقراءتها. يمكن إنشاء فرق صحية جديدة تستخدم هذه الميزات على أساس كل مريض. تستند هذه الميزات إلى النهج، ويمكن تعيينها إلى الأفراد أو الفرق بأكملها.

لمعرفة المزيد، راجع [بدء استخدام نهج المراسلة الآمنة لمؤسسات الرعاية الصحية](messaging-policies-hc.md).

تتعلق أيضا بالمراسلة الآمنة بالقدرة على أن يكون المستأجرون الآخرون موحدين من قبل مؤسسات الرعاية الصحية، ما يسمح بالاتصالات الثرية بين المستأجرين. (راجع [إدارة الاجتماعات الخارجية والدردشة في Microsoft Teams](/microsoftteams/manage-external-access)).

## <a name="teams-templates-for-healthcare-organizations"></a>قوالب Teams لمؤسسات الرعاية الصحية

تتضمن الفرق قوالب مصممة خصيصا لمؤسسات الرعاية الصحية، ما يسهل إنشاء فرق للموظفين للتواصل والتعاون في رعاية المرضى أو الاحتياجات التشغيلية. لمعرفة المزيد، راجع [استخدام قوالب فريق الرعاية الصحية](/microsoftteams/expand-teams-across-your-org/healthcare/healthcare-templates-admin-console?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

## <a name="care-coordination-and-collaboration"></a>تنسيق الرعاية والتعاون

اجمع فريق الرعاية الصحية معا لتنسيق الرعاية والتعاون مع Teams.

![الرعاية الصحية: تعاون مع فريقك الصحي في Teams.](media/teams-healthcare-collaborate-in-teams.png)

تمكن الفرق الأطباء والأطباء والممرضات والموظفين الآخرين من التعاون بكفاءة مع ميزات التعاون المضمنة في Teams، مثل:

- إعداد الفرق والقنوات لفرق الرعاية الصحية والعاملين في مجال المعلومات. استخدم القنوات التي تحتوي على علامات تبويب كطريقة لتنظيم عملها، مع تعليمات إضافية من علامات التبويب التي يمكنهم تثبيت مصادر المعلومات عليها.
- الدردشة ونشر الرسائل والتواصل. يمكن لفريقك إجراء محادثات مستمرة حول المرضى المختلفين الذين يحتاجون إلى الانتباه.
- اتصل بأعضاء الفريق الصحي واجتماع معهم. يمكنك إعداد اجتماعات فردية أو استخدام اجتماعات القناة لإدارة الاجتماعات اليومية، سواء باستخدام ميزات الصوت والفيديو ومشاركة الشاشة والتسجيل والنسخ في Teams.
- تخزين الملفات والمستندات ومشاركتها. فريق الحماية الخاص بك هو جزء من فريق ظاهري واحد يعمل ويتعاون على مستندات Office.

بالإضافة إلى ذلك، يمكن لفريقك استخدام التطبيقات في Teams من أجل:

- مشاركة القوائم وتعقب المعلومات باستخدام تطبيق القوائم
- تعقب المهام ومراقبتها باستخدام تطبيق المهام
- تبسيط الموافقات باستخدام تطبيق "الموافقات"
- إنشاء جداول زمنية وإدارتها ومشاركتها باستخدام تطبيق Shifts

### <a name="share-lists-and-track-information-with-the-lists-app"></a>مشاركة القوائم وتعقب المعلومات باستخدام تطبيق القوائم

يساعد تطبيق القوائم في Teams الفرق على تعقب المعلومات وتنظيم العمل. تم تثبيت التطبيق مسبقا لجميع مستخدمي Teams وهو متوفر كعلامة تبويب في كل فريق وقناة. يمكن إنشاء القوائم من البداية أو من قوالب معرفة مسبقا أو عن طريق استيراد البيانات إلى Excel.

يمكن لفرق الصحة استخدام قالب المرضى للبدء. يمكنهم إنشاء قوائم لتعقب احتياجات المرضى وحالته. يمكن إحضار بيانات المرضى الموجودة على جداول بيانات Excel لإنشاء قائمة في Teams. يمكن استخدام هذه القوائم لسيناريوهات مثل الجولات ومراقبة المرضى لتنسيق الرعاية.

على سبيل المثال، تنشئ الممرضة المسؤولة قائمة بالمرضى في فريق يتضمن جميع أعضاء الفريق الصحي. في أثناء الجولات، يصل فريق الصحة إلى Teams على أجهزته المحمولة ويحدث معلومات المرضى في القائمة، والتي يمكن لجميع أعضاء الفريق عرضها للبقاء في وضع المزامنة. في جلسات التقريب حيث يجتمع فريق الصحة لمناقشة وتقييم مقاييس الأداء الصحي الرئيسية لضمان وصول المريض إلى المسار الصحيح للتصريف، يمكنه مشاركة هذه المعلومات باستخدام Teams على شاشة عرض كبيرة. يمكن لأعضاء الفريق الصحي غير الموجودين في الموقع الانضمام عن بعد.

فيما يلي قائمة أمثلة تم إعدادها لتقريب المرضى.

:::image type="content" source="media/lists-patients-example.png" alt-text="Screenshot of example list for patient rounding.":::

لمعرفة المزيد، راجع [إدارة تطبيق القوائم لمؤسستك في Teams](/microsoftteams/manage-lists-app?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

### <a name="track-and-monitor-tasks-with-the-tasks-app"></a>تعقب المهام ومراقبتها باستخدام تطبيق المهام

استخدم [المهام](https://support.microsoft.com/office/use-the-tasks-app-in-teams-e32639f3-2e07-4b62-9a8c-fd706c12c070) في Teams لتعقب تنفيذ العناصر لفريق الرعاية الصحية بأكمله. يمكن لفريق الحماية إنشاء المهام وتعيينها وجدولتها وتصنيفها وتحديث الحالة في أي وقت، من أي جهاز يقوم بتشغيل Teams. يمكن لمحترفي تكنولوجيا المعلومات والمسؤولين أيضا نشر المهام إلى فرق معينة لمؤسستك. على سبيل المثال، يمكنك نشر مجموعة من المهام لبروتوكولات السلامة الجديدة أو خطوة جديدة لاستخدامها عبر المستشفى.

لمعرفة المزيد، راجع [إدارة تطبيق المهام لمؤسستك في Microsoft Teams](/microsoftteams/manage-tasks-app?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)

### <a name="streamline-approvals-with-the-approvals-app"></a>تبسيط الموافقات باستخدام تطبيق "الموافقات"

استخدم [الموافقات](https://support.microsoft.com/office/what-is-approvals-a9a01c95-e0bf-4d20-9ada-f7be3fc283d3) لتبسيط جميع طلباتك وعملياتك مع فريقك. إنشاء الموافقات وإدارتها ومشاركتها مباشرة من مركزك للعمل الجماعي. ابدأ تدفق الموافقة من نفس المكان الذي ترسل فيه دردشة أو في محادثة قناة أو من تطبيق الموافقات نفسه. ما عليك سوى تحديد نوع الموافقة وإضافة التفاصيل وإرفاق الملفات واختيار الموافقين. بمجرد الإرسال، يتم إعلام الموافقين ويمكنهم مراجعة الطلب والعمل عليه.

يمكنك السماح بتطبيق الموافقات لمؤسستك وإضافته إلى فرقك. لمعرفة المزيد، راجع [إدارة تطبيق الموافقات](/microsoftteams/approval-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

### <a name="create-manage-and-share-schedules-with-the-shifts-app-and-frontline-worker-integration"></a>إنشاء جداول زمنية وإدارتها ومشاركتها باستخدام تطبيق Shifts وتكامل Frontline Worker

يتكامل Teams مع تطبيق Shifts و Frontline Worker، والتي يمكن استخدامها لتنسيق ميزات التوظيف في الوردية والمزيد. على سبيل المثال، في الورديات، يمكن لمديري الممرضات إعداد الجداول الزمنية وتنسيقها لموظفيهم، ويمكن للممرضات التحقق من الجداول الزمنية وتبديل الورديات.

لمعرفة المزيد، راجع [إدارة تطبيق الورديات لمؤسستك في Microsoft Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

## <a name="help-your-clinical-and-information-workers-get-going-with-teams"></a>مساعدة العاملين في مجال الخدمات الطبية والمعلومات على استخدام Teams

تتوفر العديد من الموارد لمساعدة جميع المستخدمين في مؤسستك على التأقلم مع استخدام Teams:

- تفضل بزيارة [مركز اعتماد Teams](https://adoption.microsoft.com/microsoft-teams/) للحصول على المشورة حول نشر Teams إذا كنت قد بدأت للتو رحلة مؤسستك مع Teams، أو توسيع Teams إلى المزيد من المناطق في مؤسستك.
- ضع في اعتبارك إعداد [مسارات تعلم](https://adoption.microsoft.com/microsoft-365-learning-pathways/) مخصصة للمستخدمين لتغطية المهام التي يحتاجون إلى القيام بها فقط.
- احصل على تعليمات وتدريبات للمستخدمين حول كيفية تنفيذ المهام الأساسية في Teams على [موقع دعم Teams](https://support.microsoft.com/teams)، بما في ذلك [مقاطع الفيديو التدريبية السريعة](https://support.microsoft.com/office/microsoft-teams-video-training-4f108e54-240b-4351-8084-b1089f0d21d7). يحتوي هذا الموقع أيضا على تعليمات وتدريبات لتطبيقات Teams، بما في ذلك [القوائم](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db) [والمهام](https://support.microsoft.com/office/use-the-tasks-app-in-teams-e32639f3-2e07-4b62-9a8c-fd706c12c070) [والموافقات](https://support.microsoft.com/office/what-is-approvals-a9a01c95-e0bf-4d20-9ada-f7be3fc283d3) [والحجوزات](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5) [والورديات](https://support.microsoft.com/office/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821).
