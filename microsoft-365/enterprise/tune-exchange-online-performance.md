---
title: ضبط Exchange Online الأداء
ms.author: krowley
author: tracyp
manager: laurawi
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
description: تحتوي هذه المقالة على تلميحات عامة وروابط إلى موارد أخرى تعلمك بكيفية تحسين أداء Exchange Online.
ms.openlocfilehash: 5feb704a1da83ef93ebc3bbe72fb12c7f0c54574
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575327"
---
# <a name="tune-exchange-online-performance"></a>ضبط Exchange Online الأداء

تحتوي هذه المقالة على تلميحات عامة وروابط إلى موارد أخرى تعلمك بكيفية تحسين أداء Exchange Online، لا سيما قبل الترحيل. هذه المقالة هي جزء من تخطيط الشبكة وضبط الأداء [Office 365](./network-planning-and-performance.md) المشروع.
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>الأمور التي يجب وضعها في الاعتبار لتحسين Exchange Online الأداء

لتحسين سرعة الترحيل وتقليل قيود النطاق الترددي لمنظمتك Exchange Online، فكر في ما يلي:
  
- **تقليل أحجام علب البريد.** يحسن حجم علبة البريد الأصغر سرعة الترحيل. 
    
- **استخدم قدرات نقل علبة البريد مع Exchange مختلط.** باستخدام Exchange المختلط، البريد غير المتصل (على شكل . لا تتطلب ملفات OST إعادة التنزيل عند إجراء عملية Exchange Online. هذا يقلل بشكل ملحوظ من متطلبات النطاق الترددي للتنزيل. 
    
- **جدولة عمليات نقل علب البريد التي تحدث أثناء فترات انخفاض نسبة استخدام الإنترنت وانخفاض مستوى Exchange الاستخدام.** عند جدولة الانتقالات، يتم إرسال طلبات الترحيل إلى وكيل النسخ المتماثل لعلبة البريد وقد لا تتم على الفور. 
    
- **استخدم النوافذ المنبثقة المائلة Outlook على ويب.** توفر النوافذ المنبثقة المائلة إصدارات أصغر وأقل استخداما للذاكرة من بعض رسائل البريد الإلكتروني في Microsoft Edge أو Internet Explorer من خلال عرض بعض المكونات على الخادم. لمزيد من المعلومات، راجع استخدام النوافذ المنبثقة [المائلة لتقليل الذاكرة المستخدمة عند قراءة رسائل البريد](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>نصيحة عامة

- تأكد من أن البحث عن outlook.office.com DNS يدخل مركز بيانات MS في موقع إدخال منطقي لموقعك.

- قم بالبحث عن التخزين المؤقت لعلبة البريد واختر الخيارات المناسبة (إعادة). فترة التخزين المؤقت، التخزين المؤقت لعلبة البريد المشتركة، وما إلى ذلك).

- حافظ على Outlook البيانات من المرور عبر اتصالات VPN (إلى مكتب مركزي) قبل مرورها عبر الإنترنت.

- تأكد من أن بيانات علبة البريد تلتزم بالقيود المفروضة على المجلد والعناصر والمبالغ.
    
لمزيد من المعلومات حول Exchange الترحيل، راجع Office 365 [الترحيل وأفضل الممارسات](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
