---
title: إصلاح التبصر المحتمل لحلقة البريد
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: cb801985-3c89-4979-9c18-17829a4cb563
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤولين معرفة كيفية استخدام تصحيح معلومات حلقة البريد المحتملة في لوحة معلومات تدفق البريد في مركز التوافق & الأمان لتحديد حلقيات البريد وإصلاحها في المؤسسة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a80555f438ceb9431638e727ff0b84c3268ac1c1
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679687"
---
# <a name="fix-possible-mail-loop-insight-in-the-security--compliance-center"></a>إصلاح إمكانية معرفة حلقة البريد في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تكون تكرارات البريد سيئة بسبب:

- إنها تهدر موارد النظام.
- فهي تستهلك الحصة النسبية لحجم البريد في مؤسستك.
- فهي ترسل تقارير بعدم التسليم مربكة (تعرف أيضا بالتقارير بعدم التسليم أو رسائل البريد المرتد) إلى مرسلي الرسائل النصية الأصلية.

تقوم **لوحة معلومات** إصلاح حلقة البريد المحتملة في  المنطقة الموصى بها لك في [لوحة](https://protection.office.com) معلومات تدفق البريد في مركز التوافق & الأمان، بالكشف عن تكرار تكراري للبريد في مؤسستك.[](mail-flow-insights-v2.md)

تظهر هذه المعرفة فقط بعد الكشف عن الشرط (إذا لم يكن لديك أي تكرارات بريد، فلن ترى هذه المعرفة).

![إصلاح بطء معرفة قواعد تدفق البريد في المنطقة المستحسنة من لوحة معلومات تدفق البريد.](../../media/mfi-fix-possible-mail-loop.png)

عندما **تنقر فوق عرض التفاصيل على** عنصر واجهة المستخدم، تظهر عنصر منقط مع مزيد من المعلومات:

- **المجال**
- **عدد الرسائل**: يمكنك **النقر فوق عرض** الرسائل العينة للاطلاع على نتائج [](message-trace-scc.md) تتبع الرسائل لعينة من الرسائل التي تأثرت بهذه الحلقة.
- **نوع المجال**" على سبيل المثال، موثوق أو غير موثوق.
- **سجل MX**: قيم الأولوية والمضيف (**خادم** البريد) لسجل MX للمجال.
- **السبب الحلقي** **وكيفية الإصلاح**: سنحدد السيناريوهات الأكثر شيوعا لحلقة البريد ونوفر الإجراءات الموصى بها لإصلاح التكرار الحلقي.

![القائمة من القائمة من القائمة flyout لالتفاصيل التي تظهر بعد النقر فوق عرض التفاصيل في تصحيح رؤى حلقة البريد المحتملة.](../../media/mfi-fix-possible-mail-loop-details.png)

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).
