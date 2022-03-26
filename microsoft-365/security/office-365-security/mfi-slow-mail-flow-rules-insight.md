---
title: إصلاح تحليلات قواعد تدفق البريد البطيئة
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤولين التعرف على كيفية استخدام معلومات إصلاح قواعد تدفق البريد البطيئة في مركز التوافق & الأمان لتحديد قواعد تدفق البريد غير الفعالة أو المعطلة (المعروفة أيضا بقواعد النقل) وإصلاحها في مؤسساتهم.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9866761e683e15d34d81b8ea0962d974b0b474da
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63566749"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>إصلاح بطء معرفة قواعد تدفق البريد في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

قد تؤدي قواعد تدفق البريد غير الفعالة (المعروفة أيضا بقواعد النقل) إلى حدوث تأخيرات في تدفق البريد لمنظمتك. تقدم هذه النظرة المتعمقة تقارير حول قواعد تدفق البريد التي تؤثر على تدفق البريد في مؤسستك. تتضمن أمثلة هذه الأنواع من القواعد ما يلي:

- الشروط التي تستخدم **هي عضو في** للمجموعات الكبيرة.
- الشروط التي تستخدم نمط تعبير (regex) معقد متطابق.
- الشروط التي تستخدم تدقيق المحتوى في المرفقات.

تقوم **معلومات** إصلاح قواعد تدفق البريد البطيئة  في المنطقة الموصى بها لك في [](mail-flow-insights-v2.md) لوحة معلومات تدفق البريد في مركز التوافق ل [&](https://protection.office.com) الأمان بتعريفك عندما تطول عملية إكمال قاعدة تدفق البريد.

تظهر هذه المعرفة فقط بعد الكشف عن الشرط (إذا لم يكن لديك أي تكرارات بريد، فلن ترى هذه المعرفة).

يمكنك استخدام هذا الإعلام لمساعدتك على تحديد قواعد تدفق البريد وضبطها للمساعدة في تقليل تأخيرات تدفق البريد.

![إصلاح بطء معرفة قواعد تدفق البريد في المنطقة المستحسنة من لوحة معلومات تدفق البريد.](../../media/mfi-fix-slow-mail-flow-rules.png)

عندما **تنقر فوق عرض التفاصيل على** عنصر واجهة المستخدم، تظهر عنصر منقط مع مزيد من المعلومات:

- **القاعدة**: يمكنك مرر فوق الملخص لرؤية كل الشروط والاستثناءات والإجراءات الخاصة بالقاعدة. يمكنك النقر فوق الملخص لتحرير القاعدة في Exchange إدارة (EAC) في <https://admin.exchange.microsoft.com/#/transportrules>.
- **عدد الرسائل التي تم تقييمها**: يمكنك النقر  فوق عرض رسائل نموذجية للاطلاع على [](message-trace-scc.md) نتائج تتبع الرسائل لعينة من الرسائل التي تأثرت بالقاعدة.
- **متوسط الوقت المنفق على كل رسالة**
- **الوقت الوسطي المنقضي على رسالة**: القيمة المتوسطة التي تفصل النصف العلوي عن النصف السفلي من بيانات الوقت.

![القائمة من خلال القائمة من القائمة المنافقة لالتفاصيل التي تظهر بعد النقر فوق عرض التفاصيل في تصحيح بطء تدفق البريد.](../../media/mfi-fix-slow-mail-flow-rules-details.png)

لمزيد من المعلومات حول الشروط والاستثناءات في قواعد تدفق البريد، راجع شروط قاعدة [تدفق البريد والاستثناءات (الشروط](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)) في Exchange Online.

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).