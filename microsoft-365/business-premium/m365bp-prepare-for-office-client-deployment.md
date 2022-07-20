---
title: التحضير لنشر عميل Office باستخدام Microsoft 365 Business Premium
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
ROBOTS: NO INDEX, NO FOLLOW
description: تعرف على كيفية تثبيت تطبيقات Office 32 بت تلقائيا على أجهزة كمبيوتر Windows وإبقائها محدثة في Microsoft 365 Business Premium.
ms.openlocfilehash: a8bdede91b0b7e5114f38ac8f555d43913ff22dd
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893890"
---
# <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>التحضير لتثبيت تطبيقات Office تلقائيا على أجهزة الكمبيوتر العميلة

استخدم Microsoft 365 Business Premium لتثبيت تطبيقات Office 32 بت تلقائيا على أجهزة كمبيوتر Windows وإبقائها محدثة بالتحديثات.
  
يعمل التثبيت التلقائي بشكل أفضل إذا كان الكمبيوتر: 

- على Windows for Business.
  
- لا يحتوي على تطبيقات Office لسطح المكتب الموجودة (Word وExcel وPowerPoint وOutlook وOneNote وPublisher وAccess وOneDrive) أو لديه إصدار موجود من التشغيل الفوري ل Office مثبت.

لتحديد ما إذا كان لديك إصدار التشغيل الفوري من Office، في أي تطبيق Office، انتقل إلى **"حساب** **الملف**\>" (**حساب Office** في Outlook). إذا رأيت **Office التحديثات** كما هو موضح في الشكل التالي، فقد تم التثبيت باستخدام التشغيل الفوري.
  
![لقطة شاشة لتحديثات Office في حساب تطبيق Office.](./../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
## <a name="requirements-for-using-this-feature"></a>متطلبات استخدام هذه الميزة
  
يعمل مع:
  
- مستخدم لديه ترخيص مستخدم Windows Business، وترخيص Microsoft 365 for Business نشط، تحديث المبدعين لـ Windows 10، ومنضم إلى Azure Active Directory.

لا يعمل مع: 

- تطبيقات Office 64 بت (على سبيل المثال: Word وExcel وPowerPoint). إذا كانت تطبيقات Office بالإصدار 64 بت مطلوبة، فإن هذه الميزة ليست مناسبة لأنه لا يوجد دعم لتشغيل إصدار التشغيل الفوري 2016 64 بت من Office من وحدة تحكم مسؤول Microsoft 365 للأعمال.

- أي تطبيقات مستقلة ل Windows Installer (MSI) 2016 (على سبيل المثال، Visio أو Project). يقوم Microsoft 365 للأعمال بترقية Office إلى إصدار التشغيل الفوري من Office 2016، ولا يعمل ذلك مع تطبيقات Office 2016 MSI المستقلة.

يوضح الجدول التالي الإجراء الذي قد يحتاج المستخدمون أو المسؤولون إلى اتخاذه، استنادا إلى حالة البداية الخاصة بهم، للحصول على إصدار ناجح من "التشغيل الفوري" من Office بالإصدار 32 بت من وحدة تحكم مسؤول Microsoft 365 للأعمال.<br/>


|بدء حالة تثبيت Office|الإجراء الذي يجب اتخاذه قبل تثبيت Microsoft 365 للأعمال Office|حالة الانتهاء|
|:-----|:-----|:-----|
|لم يتم تثبيت مجموعة Office  |None  |تم تثبيت الإصدار 32 بت من Office 2016 باستخدام التشغيل الفوري  |
|إصدار التشغيل الفوري 32 بت الحالي من Office (2016 أو إصدار سابق) ولا توجد تطبيقات مستقلة  |None  |تمت الترقية إلى أحدث إصدار من التشغيل الفوري للإصدار 32 بت من Office 2016، حسب الحاجة **\*** |
|إصدار التشغيل الفوري 32 بت الحالي من Office وتطبيقات Office المستقلة للتشغيل الفوري 32 بت أو 64 بت (على سبيل المثال، Visio وProject)  |None  |لا تتأثر التطبيقات المستقلة. تمت ترقية المجموعة إلى إصدار التشغيل الفوري 32 بت من Office 2016  |
|إصدار التشغيل الفوري 32 بت الحالي من Office وأي تطبيقات Office مستقلة 32 بت أو 64 بت (باستثناء 2016) MSI  |None  |لا تتأثر التطبيقات المستقلة. تمت ترقية المجموعة إلى إصدار التشغيل الفوري 32 بت من Office 2016  |
|أي إصدار من Office من إصدار التشغيل الفوري 64 بت  |إلغاء تثبيت تطبيقات Office 64 بت، إذا كان من المقبول استبدالها بتطبيقات Office 32 بت  |إذا تمت إزالة تطبيقات Office 64 بت، يتم تثبيت إصدار التشغيل الفوري 32 بت من Office 2016  |
|تثبيت MSI موجود ل Office 2016 مع تطبيقات مستقلة أو بدونها  |إلغاء تثبيت MSI Office 2016.  |تم تثبيت إصدار التشغيل الفوري 32 بت من Office 2016. لا يوجد تغيير في التطبيقات المستقلة  |
|تثبيت MSI الحالي لتطبيقات Office 2013 (أو إصدار سابق) و/أو تطبيقات Office المستقلة  |None  |إصدار التشغيل الفوري 32 بت من Office 2016 مع تثبيت MSI Office الموجود مسبقا (والتطبيقات المستقلة) موجود جنبا إلى جنب  |

 **(\*) ملاحظة:** لا تتم الترقية إلى إصدار التشغيل الفوري 32 بت من Office 2016 بسبب خطأ معروف. هناك تصحيح قيد التقدم. 

## <a name="next-objective"></a>الهدف التالي

[إنشاء إعدادات حماية التطبيق](m365bp-protection-settings-for-windows-10-devices.md)
  