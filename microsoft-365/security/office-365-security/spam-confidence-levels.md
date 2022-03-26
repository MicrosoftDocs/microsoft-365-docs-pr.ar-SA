---
title: مستوى الثقة في البريد العشوائي
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤولين التعرف على مستوى الثقة في البريد العشوائي (SCL) الذي تم تطبيقه على الرسائل في Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a5a7bfd34fdb23b0bef94119f53adaa9ecc0c4a1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566574"
---
# <a name="spam-confidence-level-scl-in-eop"></a>مستوى الثقة في البريد العشوائي (SCL) في EOP

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

في Microsoft 365 المؤسسات التي بها علب بريد في Exchange Online أو مؤسسات Exchange Online Protection (EOP) مستقلة بدون علب بريد Exchange Online، تمر الرسائل الواردة عبر تصفية البريد العشوائي في EOP، كما يتم تعيين درجة بريد عشوائي لها. يتم تعيين هذه الدرجة إلى مستوى الثقة الفردي للبريد العشوائي (SCL) الذي يضاف إلى الرسالة في رأس X. يشير SCL أعلى إلى أن الرسالة من المرجح أن تكون بريدا عشوائيا. يتخذ EOP إجراء استنادا إلى الرسالة استنادا إلى SCL.

يتم وصف معنى SCL والإجراءات الافتراضية التي يتم اتخاذها على الرسائل في الجدول التالي. لمزيد من المعلومات حول الإجراءات التي يمكنك اتخاذها على الرسائل استنادا إلى قرار تصفية البريد العشوائي، راجع تكوين سياسات مكافحة البريد العشوائي [في EOP](configure-your-spam-filter-policies.md).

****

|SCL|التعريف|الإجراء الافتراضي|
|:---:|---|---|
|-1|تم تخطي الرسالة لتصفية البريد العشوائي. على سبيل المثال، الرسالة من مرسل آمن، أو تم إرسالها إلى مستلم آمن، أو من خادم مصدر بريد إلكتروني في قائمة السماح ب IP. لمزيد من المعلومات، راجع [إنشاء قوائم مرسلين آمنة في EOP](create-safe-sender-lists-in-office-365.md).|تسليم الرسالة إلى علبة الوارد الخاصة المستلمين.|
|0, 1|حددت تصفية البريد العشوائي أن الرسالة لم تكن بريدا عشوائيا.|تسليم الرسالة إلى علبة الوارد الخاصة المستلمين.|
|5, 6|وضع عامل تصفية البريد العشوائي علامة على الرسالة **كرسالة عشوائية**|أرسل الرسالة إلى مجلد البريد الإلكتروني غير الهام للمستلمين.|
|9|وضعت تصفية البريد العشوائي علامة على الرسالة **كرسالة عشوائية عالية الثقة**|أرسل الرسالة إلى مجلد البريد الإلكتروني غير الهام للمستلمين.|
|

ستلاحظ أن SCL 2 و3 و4 و7 و8 لا تستخدم بواسطة تصفية البريد العشوائي.

يمكنك استخدام قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) لرسائل SCL. إذا كنت تستخدم قاعدة تدفق البريد لتعيين SCL، فإن القيم 5 أو 6 تقوم بتشغيل إجراء تصفية البريد العشوائي للبريد العشوائي، وتشغل القيم 7 أو 8 أو 9 إجراء تصفية البريد العشوائي للبريد العشوائي عالي **الثقة.** لمزيد من المعلومات، راجع استخدام قواعد تدفق البريد لتعيين مستوى الثقة في البريد [العشوائي (SCL) في الرسائل](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

على غرار SCL، يحدد مستوى الشكوى المجمعة (BCL) البريد الإلكتروني المجمع السيئ (المعروف أيضا بالبريد _الرمادي_). يشير مؤشر BCL أعلى إلى أن رسالة البريد المجمع من المرجح أن تنشئ شكاوى (وبالتالي من المرجح أن تكون بريدا عشوائيا). يمكنك تكوين عتبة BCL في سياسات مكافحة البريد العشوائي. لمزيد من المعلومات، راجع تكوين سياسات مكافحة البريد العشوائي في [EOP](configure-your-spam-filter-policies.md) ومستوى الشكوى [المجمعة (BCL) في EOP)](bulk-complaint-level-values.md) وما الفرق بين البريد الإلكتروني غير الهام والبريد الإلكتروني المجمع [؟](what-s-the-difference-between-junk-email-and-bulk-email.md).

****

![الأيقونة القصيرة ل LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **هل تريد Microsoft 365؟** اكتشف دورات تدريبية مجانية Microsoft 365 **لمسؤولي** ومهنيي المعلومات، تم إحضارها لك بواسطة LinkedIn Learning.
