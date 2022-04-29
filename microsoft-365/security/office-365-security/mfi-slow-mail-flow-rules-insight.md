---
title: إصلاح نظرة ثاقبة لقواعد تدفق البريد البطيئة
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤولين معرفة كيفية استخدام نظرة ثاقبة لقواعد تدفق البريد البطيئة في Security & Compliance Center لتحديد قواعد تدفق البريد غير الفعالة أو المقطوعة وإصلاحها (المعروفة أيضا بقواعد النقل) في المؤسسة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 650389529f2a5d811f71b7c3f755d93e7e734d81
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128729"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>إصلاح نظرة ثاقبة لقواعد تدفق البريد البطيئة في مركز توافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكن أن تؤدي قواعد تدفق البريد غير الفعالة (المعروفة أيضا بقواعد النقل) إلى حدوث تأخيرات في تدفق البريد لمؤسستك. تقوم هذه التحليلات بالإبلاغ عن قواعد تدفق البريد التي تؤثر على تدفق البريد الخاص بالمؤسسة. تتضمن الأمثلة على هذه الأنواع من القواعد ما يلي:

- الشروط التي تستخدم **هي عضو في** المجموعات الكبيرة.
- الشروط التي تستخدم مطابقة نمط التعبير العادي المعقد (regex).
- الشروط التي تستخدم إيداع المحتوى في المرفقات.

تعلمك **نتيجة تحليلات قواعد تدفق البريد البطيئة** في المنطقة **"مستحسن"** في [لوحة معلومات تدفق البريد](mail-flow-insights-v2.md) في [مركز التوافق & الأمان](https://protection.office.com) عندما تستغرق قاعدة تدفق البريد وقتا طويلا لإكمالها.

تظهر هذه الرؤى فقط بعد الكشف عن الشرط (إذا لم يكن لديك أي حلقات بريد، فلن ترى نتيجة التحليلات).

يمكنك استخدام هذا الإعلام لمساعدتك على تحديد قواعد تدفق البريد وضبطها للمساعدة في تقليل تأخيرات تدفق البريد.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules.png" alt-text="نظرة ثاقبة لقواعد تدفق البريد البطيئة في المنطقة &quot;مستحسن&quot; في لوحة معلومات تدفق البريد" lightbox="../../media/mfi-fix-slow-mail-flow-rules.png":::

عند النقر فوق **"عرض التفاصيل** " على عنصر واجهة المستخدم، تظهر قائمة منبثقة مع مزيد من المعلومات:

- **القاعدة**: يمكنك المرور فوق الملخص للاطلاع على جميع الشروط والاستثناءات والإجراءات الخاصة بالقاعدة. يمكنك النقر فوق الملخص لتحرير القاعدة في مركز إدارة Exchange (EAC) في <https://admin.exchange.microsoft.com/#/transportrules>.
- **عدد الرسائل التي تم تقييمها**: يمكنك النقر فوق **"عرض نماذج الرسائل** " لرؤية نتائج [تتبع الرسائل](message-trace-scc.md) لعينة من الرسائل التي تأثرت بالقاعدة.
- **متوسط الوقت المستغرق في كل رسالة**
- **متوسط الوقت المنقضي في رسالة**: القيمة الوسطى التي تفصل النصف العلوي عن النصف السفلي من البيانات.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules-details.png" alt-text="القائمة المنبثقة &quot;تفاصيل&quot; التي تظهر بعد النقر فوق &quot;عرض التفاصيل&quot; على نتيجة تحليلات قواعد تدفق البريد البطيئة &quot;إصلاح&quot;" lightbox="../../media/mfi-fix-slow-mail-flow-rules-details.png":::

لمزيد من المعلومات حول الشروط والاستثناءات في قواعد تدفق البريد، راجع [شروط قاعدة تدفق البريد والاستثناءات (دالات التقييم) في Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول نتائج التحليلات الأخرى في لوحة معلومات تدفق البريد، راجع [رؤى تدفق البريد في مركز التوافق & الأمان](mail-flow-insights-v2.md).
