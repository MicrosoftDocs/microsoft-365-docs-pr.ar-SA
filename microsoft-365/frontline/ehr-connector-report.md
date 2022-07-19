---
title: تقرير المواعيد الظاهرية موصل Microsoft Teams EHR
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: conceptual
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
- m365solution-scenario
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: ''
description: تعرف على كيفية استخدام تقرير المواعيد الظاهرية موصل Teams EHR في مركز إدارة Microsoft Teams للحصول على نظرة عامة حول استخدام المواعيد الظاهرية المتكاملة من EHR في مؤسستك.
ms.openlocfilehash: 6ec3423df4b6cd094bd2cab07e44c06923ec58bf
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66858071"
---
# <a name="microsoft-teams-ehr-connector-virtual-appointments-report"></a>تقرير المواعيد الظاهرية موصل Microsoft Teams EHR

يوفر لك موصل Microsoft Teams Electronic Health Record (EHR) تقرير المواعيد الظاهرية في مركز إدارة Microsoft Teams طريقة سريعة وسهلة لعرض استخدام المواعيد الظاهرية المتكاملة ل Teams EHR في مؤسستك.

لعرض التقرير، يجب أن تكون مسؤولا عاما أو مسؤول Teams أو قارئا عموميا أو قارئ تقارير.

## <a name="view-the-report"></a>عرض التقرير

هناك طريقتان للوصول إلى التقرير وعرضه في مركز إدارة Teams.

- من خلال [بطاقة استخدام موصل EHR](#the-ehr-connector-usage-card) في لوحة المعلومات
- مباشرة عن طريق اختيار [**المواعيد الظاهرية موصل EHR**](#the-teams-ehr-connector-virtual-appointments-report) في **تقارير التحليلات & تقارير** > **الاستخدام**

### <a name="the-ehr-connector-usage-card"></a>بطاقة استخدام موصل EHR

في جزء التنقل الأيمن لمركز إدارة Microsoft Teams، اختر **لوحة المعلومات**، ثم انتقل إلى بطاقة **المواعيد الظاهرية موصل EHR**.

هنا، يمكنك الحصول على عرض سريع لنشاط الموعد الظاهري المتكامل في Teams EHR حسب الشهر، بما في ذلك المواعيد المكتملة والتخصيص المتبقي وما إذا كنت قد تجاوزت الحد الشهري (اعتمادا على الترخيص الذي تملكه).

:::image type="content" source="media/ehr-connector-report-card.png" alt-text="لقطة شاشة لبطاقة استخدام موصل EHR في لوحة معلومات مركز إدارة Teams." lightbox="media/ehr-connector-report-card.png":::

اختر **"عرض التفاصيل** " للاطلاع على تفاصيل التقرير. لشراء المزيد من التراخيص، اختر **"شراء المزيد**".

### <a name="the-teams-ehr-connector-virtual-appointments-report"></a>تقرير المواعيد الظاهرية موصل Teams EHR

1. في جزء التنقل الأيمن لمركز إدارة Teams، انتقل إلى **Analytics & تقارير** > **الاستخدام**.
1. في علامة التبويب **"عرض التقارير**"، اختر **موصل EHR المواعيد الظاهرية** ونطاق تاريخ. ثم حدد **"تشغيل التقرير**".

    :::image type="content" source="media/ehr-connector-report.png" alt-text="لقطة شاشة لتقرير المواعيد الظاهرية موصل Teams EHR في مركز إدارة Teams." lightbox="media/ehr-connector-report.png":::

#### <a name="interpret-the-report"></a>تفسير التقرير

|شرح |الوصف  |
|--------|-------------|
|**1**   |يعرض كل تقرير تاريخ إنشاء التقرير ونطاق التاريخ الذي اخترته.|
|**2**   |يوفر لك الجدول معلومات مفصلة حول كل موعد تم خلال نطاق التاريخ المحدد. ضع في اعتبارك أنك لن ترى إدخالات للمواعيد التي لم ينضم فيها أحد أعضاء فريق العمل أو المريض. <ul><li>**وقت البدء (UTC)** هو التاريخ والوقت الذي يكون فيه كل من عضو فريق العمل والمشارك في الموعد.  </li> <li>**المدة** هي الفرق الزمني بين وقت البدء ووقت مغادرة آخر شخص للموعد.</li> <li>**الأساسي** هو اسم منظم الاجتماع. <li>**البريد الإلكتروني الأساسي** هو عنوان البريد الإلكتروني لمنظم الاجتماع.</li> <li> **القسم** هو معلومات القسم للموعد. إذا لم يتم عرض المعلومات بشكل صحيح، فاتصل بفريق دعم EHR. للتكامل مع Epic، تأكد من أنه ```&departmentId=%PERFDEPID;;; ; ;;NONE;%``` جزء من سجل تكامل الموفر. </li></li> <li>**إن الردود** هي العدد الإجمالي لأعضاء فريق العمل والمشاركين في الموعد.</li> <li>**يشير ضمن الحد** إلى ما إذا كان الموعد ضمن حد التخصيص. </li> </ul> |
|**3**   |يمكنك تصدير التقرير إلى ملف CSV للتحليل دون اتصال. حدد **"تصدير إلى Excel** " لتنزيل التقرير. |
|**4**   |حدد **عامل التصفية** لتصفية طريقة عرض تفاصيل التقرير. |
|**5**   |حدد " **ملء الشاشة** " لعرض التقرير في وضع ملء الشاشة. |
|**6**   |تحديد **"تحرير الأعمدة** " لإضافة أعمدة أو إزالتها في الجدول |

> [!NOTE]
> لمزيد من التحليلات حول المواعيد الظاهرية المتكاملة ل Teams EHR، راجع [تقرير استخدام الزيارات الظاهرية](virtual-visits-usage-report.md). باستخدام تقرير استخدام الزيارات الظاهرية، يمكنك عرض المقاييس الرئيسية مثل إجمالي المواعيد ووقت انتظار ساحة الانتظار ومدة الموعد وعدم وجود عروض. استخدم هذه المعلومات للحصول على نظرة ثاقبة على اتجاهات الاستخدام لمساعدتك على تحسين المواعيد الظاهرية لتقديم نتائج أعمال أفضل.

## <a name="related-articles"></a>المقالات ذات الصلة

- [المواعيد الظاهرية مع Teams - التكامل في Cerner EHR](ehr-admin-cerner.md)
- [المواعيد الظاهرية مع Teams - التكامل في Epic EHR](ehr-admin-epic.md) 
