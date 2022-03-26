---
title: تقارير نشاط عملاء Microsoft Dynamics 365 الصوتية
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
description: تعرف على كيفية الحصول على تقرير نشاط عميل Microsoft Dynamics 365 باستخدام لوحة معلومات Microsoft 365 تقارير العملاء في مركز مسؤولي Microsoft 365.
ms.openlocfilehash: fb3f631db84dbd974123863956d5505f02c382d6
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63570120"
---
# <a name="microsoft-365-reports-in-the-admin-center---dynamics-365-customer-voice-activity"></a>Microsoft 365 التقارير في مركز الإدارة - نشاط "صوت العميل" في Dynamics 365

تعرض Microsoft 365 "التقارير" نظرة عامة حول النشاط عبر المنتجات في مؤسستك. يتيح لك التنقل في تقارير مستوى المنتج الفردية لتعطيك معرفة أكثر تعمقا حول الأنشطة داخل كل منتج. اطلع على [موضوع نظرة عامة حول التقارير](activity-reports.md).
  
على سبيل المثال، يمكنك فهم نشاط كل مستخدم مرخص له استخدام Microsoft Dynamics 365 Customer Voice بالنظر إلى تفاعلاتهم مع Dynamics 365 Customer Voice. كما يساعدك أيضا على فهم مستوى التعاون المستمر بالنظر إلى عدد استطلاعات Pro التي تم إنشاؤها Pro الاستطلاعات التي استجاب لها المستخدمون. 
  
## <a name="how-to-get-to-the-dynamics-365-customer-voice-activity-report"></a>كيفية الوصول إلى تقرير نشاط Dynamics 365 Customer Voice

1. في مركز الإدارة، انتقل إلى **صفحة استخدام** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">التقارير.</a> 
2. من الصفحة الرئيسية للوحة المعلومات، انقر فوق الزر **عرض المزيد على** بطاقة صوت العميل Dynamics 365.
  
## <a name="interpret-the-dynamics-365-customer-voice-activity-report"></a>تفسير تقرير نشاط "صوت العميل" في Dynamics 365

يمكنك عرض الأنشطة في تقرير Dynamics 365 Customer Voice باختيار **علامة التبويب** نشاط.<br/>![Microsoft 365 تقارير - تقرير نشاط عميل Microsoft Dynamics 365.](../../media/a7e57d18-1ac8-4d4b-bd70-83361505dc3e.png)

حدد **اختيار أعمدة** لإضافة أعمدة أو إزالتها من التقرير.  <br/> ![تقرير نشاط عملاء Dynamics 365 Voice - اختر أعمدة.](../../media/5ab66f4b-32eb-4c9b-9683-1157ae9e2c0a.png)

يمكنك أيضا تصدير بيانات التقرير إلى ملف Excel .csv عن طريق تحديد **الارتباط تصدير**. يقوم هذا الأمر بتصدير بيانات جميع المستخدمين، كما يمكنك من إجراء فرز وتصفية بسيطين لمزيد من التحليل. إذا كان لديك أقل من 2000 مستخدم، يمكنك الفرز والتصفية داخل الجدول في التقرير نفسه. إذا كان لديك أكثر من 2000 مستخدم، لكي تتمكن من التصفية والفرز، ستحتاج إلى تصدير البيانات. 

يمكن عرض تقرير نشاط Customer **Voice في Dynamics 365** للحصول على الاتجاهات على مدار آخر 7 أيام أو 30 يوما أو 90 يوما أو 180 يوما. ومع ذلك، إذا حددت يوما معينا في التقرير، سيعرض الجدول بيانات لمدة تصل إلى 28 يوما من التاريخ الحالي (وليس من تاريخ إنشاء التقرير).
  
|عنصر|الوصف|
|:-----|:-----|
|**متري**|**التعريف**|
|اسم المستخدم  <br/> |عنوان البريد الإلكتروني للمستخدم الذي قام بتنفيذ النشاط على Microsoft Forms.  <br/> |
|تاريخ النشاط الأخير (UTC)  <br/> |آخر تاريخ تم فيه إجراء نشاط نموذج بواسطة المستخدم لنطاق التاريخ المحدد. لرؤية النشاط الذي حدث في تاريخ معين، حدد التاريخ مباشرة في المخطط.<br/>يؤدي ذلك إلى تصفية الجدول لعرض بيانات نشاط الملف فقط للمستخدمين الذين ينفذون النشاط في ذلك اليوم المحدد.  <br/> |
|عدد الاستطلاعات التي تم إنشاؤها  <br/> |عدد الاستطلاعات التي أنشأها المستخدم.   <br/> |
|عدد استجابات الاستطلاعات  <br/> |عدد الاستجابات من المجيبين الذين تم توزيع الاستطلاع معهم.|
|||