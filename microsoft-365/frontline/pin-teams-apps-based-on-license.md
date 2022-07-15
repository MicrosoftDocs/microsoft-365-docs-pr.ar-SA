---
title: تخصيص تطبيقات Teams للعاملين في الخطوط الأمامية
author: LanaChin
ms.author: v-lanachin
ms.reviewer: aaglick
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على تجربة التطبيق المخصصة للعاملين في الخطوط الأمامية في Microsoft Teams.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 24393b11abc9bb7ba4c6736daca4dfa5969f94b8
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823694"
---
# <a name="tailor-teams-apps-for-your-frontline-workers"></a>تخصيص تطبيقات Teams للعاملين في الخطوط الأمامية

> [!NOTE]
> يتم حاليا طرح هذه الميزة وقد لا تكون متوفرة في مؤسستك بعد. للبقاء على اطلاع على ميزات Teams القادمة، اطلع على [مخطط Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=microsoft%2Cteams).

## <a name="overview"></a>نظرة عامة

يقوم Teams بتثبيت التطبيقات استنادا إلى الترخيص لمنح العاملين في الخطوط الأمامية تجربة غير مضمنة في Teams مصممة خصيصا لاحتياجاتهم. 

من خلال تجربة تطبيق الخطوط الأمامية المخصصة، يحصل عمال الخطوط الأمامية على التطبيقات الأكثر صلة في Teams دون الحاجة إلى أي إجراء من المسؤول.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4VuCH]

## <a name="tailored-frontline-app-experience"></a>تجربة تطبيق الخطوط الأمامية المخصصة

يتم تثبيت التطبيقات على شريط التطبيقات، وهو الشريط الموجود أسفل عملاء Teams للأجهزة المحمولة (iOS وAndroid) وعلى جانب عميل Teams لسطح المكتب. يتم تثبيت التطبيقات التالية للمستخدمين الذين لديهم [ترخيص F](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt):

- [Activity](https://support.microsoft.com/office/explore-the-activity-feed-in-teams-91c635a1-644a-4c60-9c98-233db3e13a56)
- [الدردشة](https://support.microsoft.com/office/get-started-with-chat-0b506ce2-eb6d-4fca-9668-e56980ba755e)
- [الفرق](https://support.microsoft.com/office/teams-and-channels-in-microsoft-teams-c6d0e61d-a61e-44a6-a972-04f2a8fa4155)
- [اسلكي](https://support.microsoft.com/office/get-started-with-teams-walkie-talkie-25bdc3d5-bbb2-41b7-89bf-650fae0c8e0c)
- [المهام](https://support.microsoft.com/office/use-the-tasks-app-in-teams-e32639f3-2e07-4b62-9a8c-fd706c12c070)
- [التحولات](https://support.microsoft.com/office/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821)
- [الموافقات](https://support.microsoft.com/office/what-is-approvals-a9a01c95-e0bf-4d20-9ada-f7be3fc283d3)

**Teams للأجهزة المحمولة**

:::image type="content" source="media/tailored-teams-apps-mobile.png" alt-text="تجربة تطبيق الخطوط الأمامية المخصصة على Teams للأجهزة المحمولة" lightbox="media/tailored-teams-apps-mobile.png"::: 

**Teams لسطح المكتب**

:::image type="content" source="media/tailored-teams-apps-desktop.png" alt-text="تجربة تطبيق الخطوط الأمامية المخصصة على Teams لسطح المكتب" lightbox="media/tailored-teams-apps-desktop.png"::: 

## <a name="admin-controls"></a>عناصر تحكم مسؤول

> [!NOTE]
> يجب تشغيل إعداد **تثبيت المستخدم** في [نهج إعداد التطبيق](/microsoftteams/teams-app-setup-policies) العمومي (الافتراضي على مستوى المؤسسة) حتى تصبح هذه الميزة سارية المفعول.

يتم التحكم في تجربة تطبيق الواجهة الأمامية المخصصة من خلال إعداد التطبيق **"إظهار التطبيقات المخصصة** على مستوى المؤسسة" على صفحة ["إدارة التطبيقات](/microsoftteams/manage-apps#manage-org-wide-app-settings) " في مركز إدارة Teams. إذا كانت الميزة قيد التشغيل، فسيحصل جميع المستخدمين في مؤسستك الذين لديهم ترخيص F على تجربة تطبيق مخصصة.

ضع في اعتبارك أن أي [نهج إعداد تطبيق](/microsoftteams/teams-app-setup-policies) مخصصة معينة للمستخدمين لها الأسبقية. وهذا يعني أنه إذا كان لدى المستخدم بالفعل نهج إعداد تطبيق مخصص معين له، يحصل المستخدم على التكوين المحدد في نهج إعداد التطبيق المخصص. لمعرفة المزيد حول كيفية عمل الميزة مع نهج تطبيق Teams، بما في ذلك نهج إعداد التطبيق العمومي، راجع قسم ["السيناريوهات"](#scenarios) لاحقا في هذه المقالة.

هذه الميزة قيد التشغيل بشكل افتراضي. ومع ذلك، إذا كنت لا تريد تجربة تطبيق الخطوط الأمامية المخصصة التي توفرها Microsoft، يمكنك إيقاف تشغيل الميزة. لإيقاف تشغيل الميزة أو تشغيلها:

1. في جزء التنقل الأيمن لمركز إدارة Microsoft Teams، انتقل إلى **تطبيقات** >  Teams **"إدارة التطبيقات**"، ثم حدد **إعدادات التطبيق على مستوى المؤسسة**.
2. ضمن **التطبيقات المخصصة**، قم بتبديل تبديل **"إظهار التطبيقات المخصصة** " إلى **"إيقاف تشغيل** " أو **"تشغيل**".

    :::image type="content" source="media/tailored-teams-apps-admin-center.png" alt-text="لقطة شاشة لإعداد &quot;إظهار التطبيقات المخصصة&quot; على صفحة &quot;إدارة التطبيقات&quot; في مركز إدارة Teams" lightbox="media/tailored-teams-apps-admin-center.png":::

## <a name="scenarios"></a>سيناريوهات

### <a name="how-does-the-tailored-frontline-app-experience-affect-my-global-app-setup-policy"></a>كيف تؤثر تجربة تطبيق الواجهة الأمامية المخصصة على نهج إعداد التطبيق العمومي؟

تعرف على كيفية عمل تجربة تطبيق الواجهة الأمامية المخصصة مع نهج إعداد التطبيق العمومي. تنطبق السيناريوهات الموجودة في هذا الجدول على العاملين في الخطوط الأمامية الذين لديهم ترخيص F ونهج إعداد التطبيق العمومي، مع تشغيل **تثبيت المستخدم** .

|اذا... |ثم... |
|---------|---------|
|لدى عامل الواجهة الأمامية نهج إعداد التطبيق العمومي والميزة متوقفة عن التشغيل. |يحصل عامل الواجهة الأمامية على التطبيقات المحددة في نهج إعداد التطبيق العمومي.|
|لدى عامل الواجهة الأمامية نهج إعداد التطبيق العمومي والميزة قيد التشغيل.     | يحصل عامل الخطوط الأمامية على تجربة تطبيق الخطوط الأمامية المخصصة. يتم تثبيت التطبيقات المحددة في نهج إعداد التطبيق العمومي أسفل التطبيقات المخصصة.      |
|يمكنك تحديث نهج إعداد التطبيق العمومي والميزة قيد التشغيل.     |يحصل عامل الواجهة الأمامية على تجربة تطبيق الواجهة الأمامية المخصصة ويتم تثبيت التطبيقات المحددة في نهج إعداد التطبيق العمومي أسفل التطبيقات المخصصة.         |
|لدى عامل الواجهة الأمامية نهج إعداد التطبيق العمومي ويتم إيقاف تشغيل **تثبيت المستخدم** . |يحصل عامل الواجهة الأمامية على التطبيقات المحددة في نهج إعداد التطبيق العمومي.|
|لدى عامل الواجهة الأمامية نهج إعداد التطبيق العمومي، ويتم تغيير نهج إعداد التطبيق العمومي لتضمين تطبيق خط العمل (LOB) في الموضع الثاني في قائمة التطبيقات. |يتم تثبيت تطبيق LOB أسفل التطبيقات المخصصة. يمكن لعامل الواجهة الأمامية تغيير ترتيب التطبيق إذا كان **تثبيت المستخدم** قيد التشغيل.         |
|لدى عامل الخطوط الأمامية نهج الإعداد العمومي ويتم تغيير نهج إعداد التطبيق العمومي لتضمين Shifts في الموضع الأول.  |يتم تثبيت الورديات في الموضع السادس، كما هو محدد من خلال تجربة تطبيق الخطوط الأمامية المخصصة. يمكن لعامل الواجهة الأمامية تغيير ترتيب التطبيق إذا كان **تثبيت المستخدم** قيد التشغيل.          |

### <a name="how-does-the-tailored-frontline-app-experience-work-with-other-teams-app-policies"></a>كيف تعمل تجربة تطبيق الواجهة الأمامية المخصصة مع نهج تطبيقات Teams الأخرى؟

تعرف على كيفية عمل تجربة تطبيق الواجهة الأمامية المخصصة مع نهج تطبيقات Teams الأخرى.

|اذا...  |ثم... |
|---------|---------|
الميزة متوقفة عن التشغيل.   | يحصل عامل الواجهة الأمامية على التطبيقات المحددة في نهج إعداد التطبيق العمومي أو نهج إعداد التطبيق المخصص المعين له.          |
|لدى عامل الواجهة الأمامية نهج إعداد تطبيق مخصص والميزة قيد التشغيل.    |يحصل عامل الواجهة الأمامية على التطبيقات المحددة في نهج إعداد التطبيق المخصص.          |
|يتم حظر تطبيق في تجربة تطبيق الواجهة الأمامية المخصصة لمستخدم أو لمؤسستك.      |تحترم تجربة تطبيق الواجهة الأمامية المخصصة [نهج أذونات التطبيق](/microsoftteams/teams-app-permission-policies). إذا تم حظر تطبيق، فلن يرى عامل الواجهة الأمامية التطبيق المحظور.           |
|تم تعريف تطبيق في تجربة تطبيق الواجهة الأمامية المخصصة بالفعل في نهج إعداد التطبيق والميزة قيد التشغيل. |يتم تثبيت التطبيق استنادا إلى الترتيب المحدد من قبل قائمة التطبيقات المخصصة.        |
|لدى المستخدم ترخيص E أو A أو G والميزة قيد التشغيل.   | لا يحصل المستخدم على تجربة تطبيق الخطوط الأمامية المخصصة. حاليا، تنطبق التجربة فقط على المستخدمين الذين لديهم ترخيص F.        |

> [!NOTE]
> لا يمكنك تغيير التطبيقات أو ترتيب التطبيقات في تجربة تطبيق الواجهة الأمامية المخصصة. في الوقت الحالي، إذا كنت تريد إجراء تغييرات، يمكنك إعداد تجربتك المخصصة. للقيام بذلك، قم أولا بإيقاف تشغيل الميزة. ثم [قم بإنشاء نهج إعداد تطبيق مخصص](/microsoftteams/teams-app-setup-policies)، [وتعيينه للمستخدمين أو المجموعات](/microsoftteams/assign-policies-users-and-groups).

## <a name="related-articles"></a>المقالات ذات الصلة

- [إدارة تطبيق التواصل الصوتي في Teams](/microsoftteams/walkie-talkie?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [إدارة تطبيق المهام في Teams](/microsoftteams/manage-tasks-app?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [إدارة تطبيق الورديات في Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [إدارة تطبيق الموافقات في Teams](/microsoftteams/approval-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [إدارة نهج إعداد التطبيق في Teams](/microsoftteams/teams-app-setup-policies)
- [إدارة نهج أذونات التطبيق في Teams](/microsoftteams/teams-app-permission-policies)
