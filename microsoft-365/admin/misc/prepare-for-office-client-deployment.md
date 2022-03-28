---
title: التحضير لنشر Office حسب Microsoft 365 للأعمال
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
ms.date: 02/25/2022
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: M365-subscription-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: ed34fff3-2881-4ed4-9906-1ba6bb8dd804
description: تعرف على كيفية تثبيت الإصدار 32 بت Office تلقائيا على Windows 10 الكمبيوتر وتحديثها باستمرار.
ms.openlocfilehash: aa14aa9407f7115e31f01a8e20ea1324a23452ec
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575639"
---
# <a name="prepare-for-office-client-deployment-by-microsoft-365-for-business"></a>التحضير لنشر Office حسب Microsoft 365 للأعمال

تنطبق هذه المقالة على Microsoft 365 Business Premium.

> [!NOTE]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>التحضير لتثبيت تطبيقات Office تلقائيا على أجهزة الكمبيوتر العميلة

يمكنك استخدام Microsoft 365 Business Premium لتثبيت تطبيقات Office 32 بت تلقائيا على Windows 10 الكمبيوتر وتحديثها باستمرار.
  
يعمل التثبيت التلقائي بشكل أفضل إذا كان كمبيوتر المستخدم على Windows 10 Business و:
  
- لا توجد تطبيقات سطح المكتب Office (Word و Excel و PowerPoint و Outlook و OneNote و Publisher و Access و OneDrive).
    
    أو
    
- تم تثبيت إصدار موجود من "التشغيل Office".
    
لتحديد ما إذا  \> كان لديك إصدار التشغيل Office، في أي تطبيق Office انتقل إلى حساب **الملف (Office** **حساب** في Outlook). إذا رأيت Office **التحديثات** كما هو موضح في الشكل التالي، تم التثبيت باستخدام التشغيل التلقائي. 
  
![لقطة شاشة Office التحديثات في تطبيق Office الحساب.](../../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
 **روبوت Who مزايا الحصول على هذه الميزة**
  
المستخدم الذي يقوم جهاز الكمبيوتر الخاص به:
  
- **لديه** Windows 10 Business مستخدم، Microsoft 365 نشط للأعمال، تحديث المبدعين لـ Windows 10، ومنضم إلى Azure Active Directory. 
    
- **لا تتضمن تطبيقات** 64 بت Office (على سبيل المثال: Word، Excel، PowerPoint). إذا كانت تطبيقات Office بالإصدار 64 بت مطلوبة، فهذا يعني أن هذه الميزة غير ملائمة نظرا لعدم وجود دعم لتشغيل إصدار التشغيل التلقائي 2016 64 بت من Office من وحدة تحكم مسؤول Microsoft 365 للأعمال. 
    
- **لا تتضمن أي** تطبيقات مستقلة Windows 2016 (MSI) (على سبيل المثال، Visio أو Project). Microsoft 365 ترقية Office إلى إصدار التشغيل Office 2016 الذي لا يعمل مع تطبيقات MSI Office 2016. 
    
يوضح الجدول التالي الإجراء الذي قد يحتاج المستخدمون/المسؤولون إلى اتخاذه، استنادا إلى حالة البداية، للحصول على إصدار التشغيل السريع الناجح من Office 32 بت من وحدة تحكم مسؤول Microsoft 365 للأعمال.<br/>


|حالة Office التثبيت|الإجراء الذي يجب اتخاذه Microsoft 365 تثبيت Office للأعمال|حالة الانتهاء|
|:-----|:-----|:-----|
|لم يتم Office مجموعة مثبتة  <br/> |بلا  <br/> |Office 2016 32 بت باستخدام التشغيل  <br/> |
|إصدار التشغيل الحالي 32 بت من Office (2016 أو إصدار سابق) بدون تطبيقات مستقلة  <br/> |بلا  <br/> |تمت الترقية إلى أحدث إصدار من إصدار 32 بت من التشغيل Office 2016، حسب الحاجة **\*** <br/> |
|إصدار التشغيل الحالي 32 بت من Office و"التشغيل التشغيلي" 32 بت أو 64 بت تطبيقات Office مستقلة (على سبيل المثال، Visio Project)  <br/> |بلا  <br/> |لا تتأثر التطبيقات مستقلة. تمت ترقية المجموعة إلى إصدار التشغيل 32 بت من Office 2016  <br/> |
|إصدار التشغيل الحالي 32 بت من Office وأي تطبيقات مستقلة للإصدار 32 بت أو 64 بت (Office باستثناء 2016) MSI  <br/> |بلا  <br/> |لا تتأثر التطبيقات مستقلة. تمت ترقية المجموعة إلى إصدار التشغيل 32 بت من Office 2016  <br/> |
|أي إصدار موجود للتشغيل 64 بت من Office  <br/> |إلغاء تثبيت تطبيقات Office 64 بت، إذا كان لا بأس في استبدالها Office 32 بت  <br/> |إذا Office إزالة تطبيقات 64 بت، يتم تثبيت إصدار التشغيل 32 بت من Office 2016  <br/> |
|تثبيت MSI موجود Office 2016 مع تطبيقات مستقلة أو بدونها  <br/> |إلغاء تثبيت MSI Office 2016.  <br/> |تم تثبيت إصدار التشغيل 32 بت من Office 2016. لا يوجد تغيير في التطبيقات مستقلة  <br/> |
|تثبيت MSI Office 2013 (أو أي وقت سابق) و/أو تطبيقات Office مستقلة  <br/> |بلا  <br/> |إصدار التشغيل التشغيل 32 بت من Office 2016 مع تثبيت MSI Office الموجود مسبقا (والتطبيقات مستقلة) موجود جنبا إلى جنب  <br/> |
||||
   
 **(\*) ملاحظة:** لا يقوم بالترقية إلى إصدار التشغيل 32 بت من Office 2016 بسبب خطأ معروف. تصحيح ما هو في تقدم. 
  