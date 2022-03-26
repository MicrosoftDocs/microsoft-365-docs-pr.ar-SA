---
title: دعم التحقق من صحة الرسائل الموقعة على "البريد المعرف لمفاتيح المجال" (DKIM)
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a4c95148-a00c-4d12-85ed-88520b547d97
ms.collection:
- M365-security-compliance
description: تعرف على التحقق من صحة الرسائل الموقعة على DKIM Exchange Online Protection Exchange Online
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a5ea98add5ebe860f756d645909366a1f5502832
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566350"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>دعم التحقق من صحة الرسائل الموقعة على DKIM

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) Exchange Online التحقق من الصحة الوارد لرسائل البريد المعرف لمفاتيح المجال ([DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt)).

تتحقق DKIM من أن رسالة بريد إلكتروني لم يتم اتهابها من قبل شخص آخر، وقد تم إرسالها من المجال الذي تقول  إنها تأتي منه. وهو يربط رسالة بريد إلكتروني إلى المؤسسة التي أرسلتها. يتم استخدام التحقق من صحة DKIM تلقائيا لكل الرسائل المرسلة باستخدام IPv6. Microsoft 365 أيضا DKIM عند إرسال البريد عبر IPv4. (لمزيد من المعلومات حول دعم IPv6، راجع دعم رسائل البريد الإلكتروني الواردة المجهولة [عبر IPv6](support-for-anonymous-inbound-email-messages-over-ipv6.md).)

تتحقق DKIM من صحة رسالة موقع عليها رقميا تظهر في DKIM-Signature رأس الرسالة. يتم ختم نتائج DKIM-Signature التحقق من الصحة في Authentication-Results البيانات. يظهر نص رأس الرسالة مماثلا للنص التالي (contoso.com يكون المرسل):

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> لمزيد من المعلومات حول Authentication-Results، راجع RFC 7001 (حقل رأس الرسالة [للإشارة إلى حالة مصادقة الرسالة](https://www.rfc-editor.org/rfc/rfc7001.txt)). يتوافق تنفيذ DKIM من Microsoft مع RFC هذا.

يمكن للمسؤولين Exchange [قواعد تدفق](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) البريد الإلكتروني (المعروفة أيضا بقواعد النقل) على نتائج التحقق من صحة DKIM. ستسمح قواعد تدفق البريد هذه للمسؤولين بتصفية الرسائل أو توجيهها حسب الحاجة.