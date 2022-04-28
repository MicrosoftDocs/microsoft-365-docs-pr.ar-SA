---
title: ضبط أداء Exchange Online
ms.author: krowley
author: tracyp
manager: scotv
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: تحتوي هذه المقالة على تلميحات وارتباطات عامة إلى موارد أخرى تعلمك بكيفية تحسين أداء Exchange Online.
ms.openlocfilehash: 3b048db5e3ea5090ce5ed2391269f8167c459538
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092018"
---
# <a name="tune-exchange-online-performance"></a>ضبط أداء Exchange Online

تحتوي هذه المقالة على تلميحات وارتباطات عامة إلى موارد أخرى تعلمك بكيفية تحسين أداء Exchange Online، لا سيما أمام الترحيل. تشكل هذه المقالة جزءا من [تخطيط الشبكة وضبط الأداء لمشروع Office 365](./network-planning-and-performance.md).
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>الأمور التي يجب مراعاتها لتحسين الأداء Exchange Online

لتحسين سرعة الترحيل وتقليل قيود النطاق الترددي لمؤسستك Exchange Online، ضع في اعتبارك ما يلي:
  
- **تقليل أحجام علب البريد.** يعمل حجم علبة البريد الأصغر على تحسين سرعة الترحيل. 
    
- **استخدم قدرات نقل علبة البريد مع توزيع مختلط Exchange.** مع نشر مختلط Exchange، البريد غير المتصل (في شكل . لا تتطلب ملفات OST إعادة التنزيل عند الترحيل إلى Exchange Online. وهذا يقلل بشكل كبير من متطلبات النطاق الترددي للتنزيل. 
    
- **جدولة عمليات نقل علبة البريد بحيث تحدث أثناء فترات انخفاض نسبة استخدام الإنترنت وانخفاض Exchange الاستخدام المحلي.** عند جدولة عمليات النقل، يتم إرسال طلبات الترحيل إلى وكيل النسخ المتماثل لعلبة البريد وقد لا تتم على الفور. 
    
- **استخدم النوافذ المنبثقة المرنة Outlook على ويب.** توفر النوافذ المنبثقة المرنة إصدارات أصغر وأقل استخداما للذاكرة لبعض رسائل البريد الإلكتروني في Microsoft Edge أو Internet Explorer من خلال عرض بعض المكونات على الخادم. لمزيد من المعلومات، راجع [استخدام النوافذ المنبثقة المرنة لتقليل الذاكرة المستخدمة عند قراءة رسائل البريد](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>نصيحة عامة

- تأكد من أن البحث عن DNS outlook.office.com يدخل مركز بيانات MS في موقع إدخال منطقي لموقعك.

- البحث في التخزين المؤقت لعلب البريد واختيار الخيارات المناسبة (re. فترة التخزين المؤقت، التخزين المؤقت لعلب البريد المشتركة، وما إلى ذلك).

- منع بيانات Outlook من المرور عبر اتصالات VPN (إلى مكتب مركزي) قبل أن تنتقل عبر الإنترنت.

- تأكد من أن بيانات علبة البريد تلتزم بالحدود المفروضة على الكميات من المجلد والعنصر.
    
لمزيد من المعلومات حول Exchange أداء الترحيل، راجع [Office 365 أداء الترحيل وأفضل الممارسات](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
