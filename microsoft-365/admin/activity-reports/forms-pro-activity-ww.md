---
title: تقارير النشاط الصوتي للعملاء في Microsoft Dynamics 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: تعرف على كيفية الحصول على تقرير نشاط Microsoft Dynamics 365 Customer Voice باستخدام لوحة معلومات التقارير ومعرفة كيفية تعاون المستخدمين المرخصين.
ms.openlocfilehash: d31b290e9409e7d0e9a49013e0397578b5829697
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/07/2022
ms.locfileid: "66663009"
---
# <a name="microsoft-365-reports-in-the-admin-center---dynamics-365-customer-voice-activity"></a>تقارير Microsoft 365 في مركز الإدارة - نشاط Dynamics 365 Customer Voice

تعرض لك لوحة معلومات تقارير Microsoft 365 نظرة عامة على النشاط عبر المنتجات في مؤسستك. يتيح لك التنقل إلى تقارير مستوى المنتج الفردية لمنحك نظرة ثاقبة أكثر دقة حول الأنشطة داخل كل منتج. اطلع [على موضوع نظرة عامة على التقارير](activity-reports.md).
  
على سبيل المثال، يمكنك فهم نشاط كل مستخدم مرخص لاستخدام Microsoft Dynamics 365 Customer Voice من خلال النظر في تفاعلاتهم مع Dynamics 365 Customer Voice. كما يساعدك على فهم مستوى التعاون الجاري من خلال النظر في عدد استطلاعات Pro التي تم إنشاؤها والاستطلاعات الاحترافية التي استجاب لها المستخدمون. 
  
## <a name="how-to-get-to-the-dynamics-365-customer-voice-activity-report"></a>كيفية الوصول إلى تقرير نشاط Dynamics 365 Customer Voice

1. في مركز الإدارة، انتقل إلى **"التقارير**"، ثم حدد **"الاستخدام**". 
2. من الصفحة الرئيسية للوحة المعلومات، انقر فوق الزر **"عرض المزيد** " على بطاقة Dynamics 365 Customer Voice.
  
## <a name="interpret-the-dynamics-365-customer-voice-activity-report"></a>تفسير تقرير نشاط Dynamics 365 Customer Voice

يمكنك عرض الأنشطة في تقرير Dynamics 365 Customer Voice عن طريق اختيار علامة التبويب **"نشاط** ".

![تقارير Microsoft 365 - تقرير نشاط Microsoft Dynamics 365 Customer Voice.](../../media/a7e57d18-1ac8-4d4b-bd70-83361505dc3e.png)

حدد **"اختيار أعمدة** " لإضافة أعمدة أو إزالتها من التقرير.  <br/> ![تقرير نشاط Dynamics 365 Customer Voice - اختر الأعمدة.](../../media/5ab66f4b-32eb-4c9b-9683-1157ae9e2c0a.png)

يمكنك أيضا تصدير بيانات التقرير إلى ملف Excel .csv عن طريق تحديد الارتباط **"تصدير** ". يؤدي ذلك إلى تصدير بيانات جميع المستخدمين وتمكينك من إجراء فرز وتصفية بسيطين لمزيد من التحليل.

يمكن عرض تقرير **نشاط Dynamics 365 Customer Voice** للاتجاهات على مدار آخر 7 أيام أو 30 يوما أو 90 يوما أو 180 يوما. ومع ذلك، إذا حددت يوما معينا في التقرير، فسيعرض الجدول البيانات لمدة تصل إلى 28 يوما من التاريخ الحالي (وليس من تاريخ إنشاء التقرير).
  
|البند|الوصف|
|:-----|:-----|
|متري|تعريف|
|المستخدم  |عنوان البريد الإلكتروني للمستخدم الذي قام بتنفيذ النشاط على Microsoft Forms. |
|تاريخ النشاط الأخير (UTC)  |التاريخ الأخير الذي تم فيه تنفيذ نشاط نموذج من قبل المستخدم لنطاق التاريخ المحدد. لمشاهدة النشاط الذي حدث في تاريخ معين، حدد التاريخ مباشرة في المخطط.<br/>سيؤدي ذلك إلى تصفية الجدول لعرض بيانات نشاط الملف فقط للمستخدمين الذين نفذوا النشاط في ذلك اليوم المحدد.  |
|عدد الاستطلاعات التي تم إنشاؤها  |عدد الاستطلاعات التي أنشأها المستخدم.   |
|عدد استجابات الاستطلاع  |عدد الاستجابات من المستجيبين الذين تم توزيع الاستطلاع عليهم.|
