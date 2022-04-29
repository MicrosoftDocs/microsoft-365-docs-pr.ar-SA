---
title: دعم التحقق من صحة الرسائل الموقعة للبريد المعرف لمفاتيح المجال (DKIM)
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
description: تعرف على التحقق من صحة الرسائل الموقعة من DKIM في Exchange Online Protection Exchange Online
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dcdd251ba1266033671ac524426d1ac3d2f56a10
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130703"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>دعم التحقق من صحة الرسائل الموقعة من DKIM

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يدعم كل من Exchange Online Protection (EOP) وكلاهما Exchange Online التحقق الوارد من صحة رسائل البريد المعرف لمفاتيح المجال ([DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt)).

يتحقق DKIM من أن رسالة بريد إلكتروني لم يتم *تزييفها* من قبل شخص آخر، وتم إرسالها من المجال الذي *تقول* إنها جاءت منه. وهي تربط رسالة بريد إلكتروني بالمؤسسة التي أرسلتها. يتم استخدام التحقق من DKIM تلقائيا لجميع الرسائل المرسلة باستخدام IPv6. يدعم Microsoft 365 أيضا DKIM عند إرسال البريد عبر IPv4. (لمزيد من المعلومات حول دعم IPv6، راجع [دعم رسائل البريد الإلكتروني الواردة المجهولة عبر IPv6](support-for-anonymous-inbound-email-messages-over-ipv6.md).)

يتحقق DKIM من صحة رسالة موقعة رقميا تظهر في رأس DKIM-Signature لرؤوس الرسائل. يتم طابع نتائج التحقق من صحة DKIM-Signature في رأس Authentication-Results. يظهر نص رأس الرسالة مشابها للنص التالي (حيث contoso.com هو المرسل):

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> لمزيد من المعلومات حول رأس Authentication-Results، راجع RFC 7001 ([حقل رأس الرسالة للإشارة إلى حالة مصادقة الرسالة](https://www.rfc-editor.org/rfc/rfc7001.txt). يتوافق تنفيذ DKIM من Microsoft مع RFC هذا.

يمكن للمسؤولين إنشاء [قواعد تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) Exchange (المعروفة أيضا بقواعد النقل) على نتائج التحقق من صحة DKIM. ستسمح قواعد تدفق البريد هذه للمسؤولين بتصفية الرسائل أو توجيهها حسب الحاجة.
